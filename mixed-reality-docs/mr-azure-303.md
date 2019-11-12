---
title: 'MR y Azure 303: comprensión del lenguaje natural (LUIS)'
description: Complete este curso para aprender a implementar Azure Language Understanding Intelligence Service (LUIS) en una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, tutorial, API, Language Understanding Intelligence Service, Luis, hololens, envolventes, VR
ms.openlocfilehash: 9b3e4f081dc8a054d783246554f904a38f43f26c
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926803"
---
>[!NOTE]
><span data-ttu-id="31799-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="31799-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="31799-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="31799-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="31799-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="31799-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="31799-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="31799-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="31799-108">Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="31799-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="31799-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.</span><span class="sxs-lookup"><span data-stu-id="31799-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a><span data-ttu-id="31799-110">MR y Azure 303: comprensión del lenguaje natural (LUIS)</span><span class="sxs-lookup"><span data-stu-id="31799-110">MR and Azure 303: Natural language understanding (LUIS)</span></span>

<span data-ttu-id="31799-111">En este curso, aprenderá a integrar Language Understanding en una aplicación de realidad mixta con Azure Cognitive Services, con la Language Understanding API.</span><span class="sxs-lookup"><span data-stu-id="31799-111">In this course, you will learn how to integrate Language Understanding into a mixed reality application using Azure Cognitive Services, with the Language Understanding API.</span></span>

![resultado de laboratorio](images/AzureLabs-Lab3-000.png)

<span data-ttu-id="31799-113">*Language Understanding (Luis)* es un servicio de Microsoft Azure, que proporciona a las aplicaciones la capacidad de ser el significado de los datos proporcionados por el usuario, como por ejemplo, al extraer lo que una persona podría querer, en sus propias palabras.</span><span class="sxs-lookup"><span data-stu-id="31799-113">*Language Understanding (LUIS)* is a Microsoft Azure service, which provides applications with the ability to make meaning out of user input, such as through extracting what a person might want, in their own words.</span></span> <span data-ttu-id="31799-114">Esto se consigue a través del aprendizaje automático, que comprende y aprende la información de entrada y, a continuación, puede responder con información detallada, relevante.</span><span class="sxs-lookup"><span data-stu-id="31799-114">This is achieved through machine learning, which understands and learns the input information, and then can reply with detailed, relevant, information.</span></span> <span data-ttu-id="31799-115">Para obtener más información, visite la [Página de Azure Language Understanding (Luis)](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span><span class="sxs-lookup"><span data-stu-id="31799-115">For more information, visit the [Azure Language Understanding (LUIS) page](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span></span>

<span data-ttu-id="31799-116">Una vez finalizado este curso, tendrá una aplicación de auriculares con un casco de realidad mixta que podrá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="31799-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="31799-117">Capture la voz de entrada del usuario con el micrófono conectado al casco envolvente.</span><span class="sxs-lookup"><span data-stu-id="31799-117">Capture user input speech, using the Microphone attached to the immersive headset.</span></span> 
2.  <span data-ttu-id="31799-118">Envíe el dictado capturado a *Azure Language Understanding Intelligent Service* (*Luis*).</span><span class="sxs-lookup"><span data-stu-id="31799-118">Send the captured dictation the *Azure Language Understanding Intelligent Service* (*LUIS*).</span></span> 
3.  <span data-ttu-id="31799-119">Tenga el significado de LUIS Extract de la información de envío, que se analizará y se realizará un intento de determinar la intención de la solicitud del usuario.</span><span class="sxs-lookup"><span data-stu-id="31799-119">Have LUIS extract meaning from the send information, which will be analyzed, and attempt to determine the intent of the user’s request will be made.</span></span>

<span data-ttu-id="31799-120">El desarrollo incluirá la creación de una aplicación en la que el usuario podrá usar la voz o la mirada para cambiar el tamaño y el color de los objetos de la escena.</span><span class="sxs-lookup"><span data-stu-id="31799-120">Development will include the creation of an app where the user will be able to use voice and/or gaze to change the size and the color of the objects in the scene.</span></span> <span data-ttu-id="31799-121">No se tratará el uso de controladores de movimiento.</span><span class="sxs-lookup"><span data-stu-id="31799-121">The use of motion controllers will not be covered.</span></span>

<span data-ttu-id="31799-122">En su aplicación, depende del modo en que va a integrar los resultados con el diseño.</span><span class="sxs-lookup"><span data-stu-id="31799-122">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="31799-123">Este curso está diseñado para enseñarle a integrar un servicio de Azure con su proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="31799-123">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="31799-124">Es su trabajo usar el conocimiento que obtiene de este curso para mejorar su aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="31799-124">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="31799-125">Esté preparado para entrenar a LUIS varias veces, que se trata en el [capítulo 12](#chapter-12--improving-your-luis-service).</span><span class="sxs-lookup"><span data-stu-id="31799-125">Be prepared to Train LUIS several times, which is covered in [Chapter 12](#chapter-12--improving-your-luis-service).</span></span> <span data-ttu-id="31799-126">Obtendrá mejores resultados cuanto más se haya entrenado a LUIS.</span><span class="sxs-lookup"><span data-stu-id="31799-126">You will get better results the more times LUIS has been trained.</span></span>

## <a name="device-support"></a><span data-ttu-id="31799-127">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="31799-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="31799-128">Recurso</span><span class="sxs-lookup"><span data-stu-id="31799-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="31799-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="31799-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="31799-130"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="31799-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="31799-131">MR y Azure 303: comprensión del lenguaje natural (LUIS)</span><span class="sxs-lookup"><span data-stu-id="31799-131">MR and Azure 303: Natural language understanding (LUIS)</span></span></td><td style="text-align: center;"> <span data-ttu-id="31799-132">✔️</span><span class="sxs-lookup"><span data-stu-id="31799-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="31799-133">✔️</span><span class="sxs-lookup"><span data-stu-id="31799-133">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="31799-134">Aunque este curso se centra principalmente en los auriculares de Windows Mixed Reality inmersivo (VR), también puede aplicar lo que aprenda en este curso a Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="31799-134">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="31799-135">A medida que siga con el curso, verá notas sobre cualquier cambio que deba usar para admitir HoloLens.</span><span class="sxs-lookup"><span data-stu-id="31799-135">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="31799-136">Al usar HoloLens, puede observar algún Eco durante la captura de voz.</span><span class="sxs-lookup"><span data-stu-id="31799-136">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="31799-137">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="31799-137">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="31799-138">Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#.</span><span class="sxs-lookup"><span data-stu-id="31799-138">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="31799-139">Tenga en cuenta también que los requisitos previos y las instrucciones escritas dentro de este documento representan lo que se ha probado y comprobado en el momento de la escritura (2018 de mayo).</span><span class="sxs-lookup"><span data-stu-id="31799-139">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="31799-140">Puede usar el software más reciente, como se indica en el artículo [instalar las herramientas](install-the-tools.md) , aunque no se debe suponer que la información de este curso se ajusta perfectamente a lo que encontrará en el software más reciente que el que se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="31799-140">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="31799-141">Se recomienda el siguiente hardware y software para este curso:</span><span class="sxs-lookup"><span data-stu-id="31799-141">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="31799-142">Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de auriculares envolvente (VR)</span><span class="sxs-lookup"><span data-stu-id="31799-142">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="31799-143">Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="31799-143">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="31799-144">El SDK de Windows 10 más reciente</span><span class="sxs-lookup"><span data-stu-id="31799-144">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="31799-145">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="31799-145">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="31799-146">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="31799-146">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="31799-147">Un [auricular de Windows Mixed Reality inmersivo (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="31799-147">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="31799-148">Un conjunto de auriculares con micrófono integrado (si el casco no tiene micrófonos y altavoces integrados)</span><span class="sxs-lookup"><span data-stu-id="31799-148">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="31799-149">Acceso a Internet para la instalación de Azure y la recuperación de LUIS</span><span class="sxs-lookup"><span data-stu-id="31799-149">Internet access for Azure setup and LUIS retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="31799-150">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="31799-150">Before you start</span></span>

1.  <span data-ttu-id="31799-151">Para evitar que se produzcan problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cerca de la raíz (las rutas de acceso de carpeta largas pueden producir problemas en tiempo de compilación).</span><span class="sxs-lookup"><span data-stu-id="31799-151">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 
2.  <span data-ttu-id="31799-152">Para permitir que el equipo habilite el dictado, vaya a **configuración de Windows > privacidad > voz, entrada manuscrita & escriba** y presione el botón **activar servicios de voz y sugerencias de escritura**.</span><span class="sxs-lookup"><span data-stu-id="31799-152">To allow your machine to enable Dictation, go to **Windows Settings > Privacy > Speech, Inking & Typing** and press on the button **Turn On speech services and typing suggestions**.</span></span>
3.  <span data-ttu-id="31799-153">El código de este tutorial le permitirá grabar desde el dispositivo de **micrófono predeterminado** del equipo.</span><span class="sxs-lookup"><span data-stu-id="31799-153">The code in this tutorial will allow you to record from the **Default Microphone Device** set on your machine.</span></span> <span data-ttu-id="31799-154">Asegúrese de que el dispositivo de micrófono predeterminado esté establecido como el que desea usar para capturar la voz.</span><span class="sxs-lookup"><span data-stu-id="31799-154">Make sure the Default Microphone Device is set as the one you wish to use to capture your voice.</span></span>
4.  <span data-ttu-id="31799-155">Si el casco tiene un micrófono integrado, asegúrese de que la opción *"al gastar el casco, cambiar al micrófono de auriculares"* está activada en la configuración del *portal de realidad mixta* .</span><span class="sxs-lookup"><span data-stu-id="31799-155">If your headset has a built-in microphone, make sure the option *“When I wear my headset, switch to headset mic”* is turned on in the *Mixed Reality Portal* settings.</span></span>

    ![Configuración de auriculares inmersivo](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a><span data-ttu-id="31799-157">Capítulo 1: configuración del portal de Azure</span><span class="sxs-lookup"><span data-stu-id="31799-157">Chapter 1 – Setup Azure Portal</span></span>

<span data-ttu-id="31799-158">Para usar el servicio de *Language Understanding* en Azure, tendrá que configurar una instancia del servicio para que esté disponible para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="31799-158">To use the *Language Understanding* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="31799-159">Inicie sesión en el [portal de Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="31799-159">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="31799-160">Si aún no tiene una cuenta de Azure, tendrá que crear una.</span><span class="sxs-lookup"><span data-stu-id="31799-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="31799-161">Si sigue este tutorial en una situación de aula o de laboratorio, pregunte al instructor o a uno de los Proctors para obtener ayuda para configurar la nueva cuenta.</span><span class="sxs-lookup"><span data-stu-id="31799-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="31799-162">Una vez que haya iniciado sesión, haga clic en **nuevo** en la esquina superior izquierda y busque *Language Understanding*y haga clic en **entrar**.</span><span class="sxs-lookup"><span data-stu-id="31799-162">Once you are logged in, click on **New** in the top left corner, and search for *Language Understanding*, and click **Enter**.</span></span> 

    ![Crear recurso LUIS](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > <span data-ttu-id="31799-164">Es posible que la palabra **nuevo** se haya reemplazado por **crear un recurso**, en portales más recientes.</span><span class="sxs-lookup"><span data-stu-id="31799-164">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="31799-165">La nueva página a la derecha proporcionará una descripción del servicio de Language Understanding.</span><span class="sxs-lookup"><span data-stu-id="31799-165">The new page to the right will provide a description of the Language Understanding service.</span></span> <span data-ttu-id="31799-166">En la parte inferior izquierda de esta página, seleccione el botón **crear** para crear una instancia de este servicio.</span><span class="sxs-lookup"><span data-stu-id="31799-166">At the bottom left of this page, select the **Create** button, to create an instance of this service.</span></span>

    ![Creación del servicio LUIS: Aviso legal](images/AzureLabs-Lab3-02.png)
 
4.  <span data-ttu-id="31799-168">Una vez que haya hecho clic en crear:</span><span class="sxs-lookup"><span data-stu-id="31799-168">Once you have clicked on Create:</span></span>

    1. <span data-ttu-id="31799-169">Inserte el **nombre** que desee para esta instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="31799-169">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="31799-170">Seleccione una **suscripción**.</span><span class="sxs-lookup"><span data-stu-id="31799-170">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="31799-171">Seleccione el **plan de tarifa** adecuado para usted; si es la primera vez que crea un *servicio Luis*, debe tener a su disposición un nivel gratis (denominado F0).</span><span class="sxs-lookup"><span data-stu-id="31799-171">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *LUIS Service*, a free tier (named F0) should be available to you.</span></span> <span data-ttu-id="31799-172">La asignación gratuita debe ser más que suficiente para este curso.</span><span class="sxs-lookup"><span data-stu-id="31799-172">The free allocation should be more than sufficient for this course.</span></span>
    4. <span data-ttu-id="31799-173">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="31799-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="31799-174">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="31799-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="31799-175">Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común).</span><span class="sxs-lookup"><span data-stu-id="31799-175">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span> 

        > <span data-ttu-id="31799-176">Si desea leer más información sobre los grupos de recursos de Azure, [visite el artículo sobre el grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="31799-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="31799-177">Determine la **Ubicación** del grupo de recursos (si va a crear un nuevo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="31799-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="31799-178">Idealmente, la ubicación estará en la región donde se ejecutará la aplicación.</span><span class="sxs-lookup"><span data-stu-id="31799-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="31799-179">Algunos recursos de Azure solo están disponibles en determinadas regiones.</span><span class="sxs-lookup"><span data-stu-id="31799-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="31799-180">También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.</span><span class="sxs-lookup"><span data-stu-id="31799-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="31799-181">Selecciona **Crear**.</span><span class="sxs-lookup"><span data-stu-id="31799-181">Select **Create**.</span></span>

        ![Crear el servicio LUIS: entrada del usuario](images/AzureLabs-Lab3-03.png)
 
5.  <span data-ttu-id="31799-183">Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="31799-183">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="31799-184">Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="31799-184">A notification will appear in the portal once the Service instance is created.</span></span> 
 
    ![Nueva imagen de notificación de Azure](images/AzureLabs-Lab3-04.png)

7.  <span data-ttu-id="31799-186">Haga clic en la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="31799-186">Click on the notification to explore your new Service instance.</span></span>

    ![Notificación de creación de recursos correcta](images/AzureLabs-Lab3-05.png)
 
8.  <span data-ttu-id="31799-188">Haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="31799-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="31799-189">Se le dirigirá a la nueva instancia de servicio de LUIS.</span><span class="sxs-lookup"><span data-stu-id="31799-189">You will be taken to your new LUIS service instance.</span></span> 
 
    ![Acceso a claves de LUIS](images/AzureLabs-Lab3-06.png)

9.  <span data-ttu-id="31799-191">En este tutorial, la aplicación necesitará realizar llamadas al servicio, lo que se realiza mediante el uso de la clave de suscripción del servicio.</span><span class="sxs-lookup"><span data-stu-id="31799-191">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="31799-192">En la página de *Inicio rápido* , del servicio de *API de Luis* , navegue hasta el primer paso, *grabe sus claves*y haga clic en **claves** (también puede conseguirlo haciendo clic en las teclas de hipervínculo azul, que se encuentran en el menú de navegación servicios, indicado por el icono de llave).</span><span class="sxs-lookup"><span data-stu-id="31799-192">From the *Quick start* page, of your *LUIS API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="31799-193">Esto revelará las *claves*de servicio.</span><span class="sxs-lookup"><span data-stu-id="31799-193">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="31799-194">Realice una copia de una de las claves que se muestran, ya que la necesitará más adelante en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="31799-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 
12. <span data-ttu-id="31799-195">En la página *servicio* , haga clic en *Language Understanding portal* para redirigirse a la página web que usará para crear el nuevo servicio, dentro de la aplicación Luis.</span><span class="sxs-lookup"><span data-stu-id="31799-195">In the *Service* page, click on *Language Understanding Portal* to be redirected to the webpage which you will use to create your new Service, within the LUIS App.</span></span> 

## <a name="chapter-2--the-language-understanding-portal"></a><span data-ttu-id="31799-196">Capítulo 2: portal de Language Understanding</span><span class="sxs-lookup"><span data-stu-id="31799-196">Chapter 2 – The Language Understanding Portal</span></span>

<span data-ttu-id="31799-197">En esta sección, aprenderá a crear una aplicación de LUIS en el portal de LUIS.</span><span class="sxs-lookup"><span data-stu-id="31799-197">In this section you will learn how to make a LUIS App on the LUIS Portal.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="31799-198">Tenga en cuenta que la configuración de las *entidades*, las *intenciones*y *grabaciones* en este capítulo es solo el primer paso para crear el servicio de Luis: también tendrá que volver a entrenar el servicio, varias veces, para que sea más preciso.</span><span class="sxs-lookup"><span data-stu-id="31799-198">Please be aware, that setting up the *Entities*, *Intents*, and *Utterances* within this chapter is only the first step in building your LUIS service: you will also need to retrain the service, several times, so to make it more accurate.</span></span> <span data-ttu-id="31799-199">El reciclaje del servicio se trata en el [último capítulo](#chapter-12--improving-your-luis-service) de este curso, por lo que debe asegurarse de que lo completa.</span><span class="sxs-lookup"><span data-stu-id="31799-199">Retraining your service is covered in the [last Chapter](#chapter-12--improving-your-luis-service) of this course, so ensure that you complete it.</span></span>

1.  <span data-ttu-id="31799-200">Al llegar al *portal de Language Understanding*, puede que tenga que iniciar sesión, si aún no lo está, con las mismas credenciales que el Azure portal.</span><span class="sxs-lookup"><span data-stu-id="31799-200">Upon reaching the *Language Understanding Portal*, you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> 

    ![Página de inicio de sesión de LUIS](images/AzureLabs-Lab3-07.png)
 
2.  <span data-ttu-id="31799-202">Si esta es la primera vez que usa LUIS, tendrá que desplazarse hacia abajo hasta la parte inferior de la Página principal, para buscar y hacer clic en el botón **crear aplicación de Luis** .</span><span class="sxs-lookup"><span data-stu-id="31799-202">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the **Create LUIS app** button.</span></span>

    ![Página crear aplicación LUIS](images/AzureLabs-Lab3-08.png)
 
3.  <span data-ttu-id="31799-204">Una vez que haya iniciado sesión, haga clic en **mis aplicaciones** (si no está en esa sección actualmente).</span><span class="sxs-lookup"><span data-stu-id="31799-204">Once logged in, click **My apps** (if you are not in that section currently).</span></span> <span data-ttu-id="31799-205">Después, puede hacer clic en **crear nueva aplicación**.</span><span class="sxs-lookup"><span data-stu-id="31799-205">You can then click on **Create new app**.</span></span>

    ![LUIS: imagen de mis aplicaciones](images/AzureLabs-Lab3-09.png)
 
4.  <span data-ttu-id="31799-207">Asigne un *nombre*a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="31799-207">Give your app a *Name*.</span></span>
5.  <span data-ttu-id="31799-208">Si se supone que la aplicación comprende un idioma distinto del inglés, debe cambiar la *referencia cultural* al idioma adecuado.</span><span class="sxs-lookup"><span data-stu-id="31799-208">If your app is supposed to understand a language different from English, you should change the *Culture* to the appropriate language.</span></span>
6.  <span data-ttu-id="31799-209">Aquí también puede Agregar una *Descripción* de la nueva aplicación Luis.</span><span class="sxs-lookup"><span data-stu-id="31799-209">Here you can also add a *Description* of your new LUIS app.</span></span>

    ![LUIS: creación de una nueva aplicación](images/AzureLabs-Lab3-10.png)

7.  <span data-ttu-id="31799-211">Una vez que presione **listo**, escribirá la página *compilación* de la nueva aplicación *Luis* .</span><span class="sxs-lookup"><span data-stu-id="31799-211">Once you press **Done**, you will enter the *Build* page of your new *LUIS* application.</span></span>
8.  <span data-ttu-id="31799-212">Hay algunos conceptos importantes que debe comprender aquí:</span><span class="sxs-lookup"><span data-stu-id="31799-212">There are a few important concepts to understand here:</span></span>

    -   <span data-ttu-id="31799-213">*Intención*, representa el método al que se llamará después de una consulta del usuario.</span><span class="sxs-lookup"><span data-stu-id="31799-213">*Intent*, represents the method that will be called following a query from the user.</span></span> <span data-ttu-id="31799-214">Un *intento* puede tener una o más *entidades*.</span><span class="sxs-lookup"><span data-stu-id="31799-214">An *INTENT* may have one or more *ENTITIES*.</span></span>
    -   <span data-ttu-id="31799-215">*Entidad*, es un componente de la consulta que describe la información relevante para la *intención*.</span><span class="sxs-lookup"><span data-stu-id="31799-215">*Entity*, is a component of the query that describes information relevant to the *INTENT*.</span></span>
    -   <span data-ttu-id="31799-216">*Grabaciones*, son ejemplos de consultas proporcionadas por el desarrollador que Luis usará para entrenarse.</span><span class="sxs-lookup"><span data-stu-id="31799-216">*Utterances*, are examples of queries provided by the developer, that LUIS will use to train itself.</span></span>

<span data-ttu-id="31799-217">Si estos conceptos no están perfectamente claros, no se preocupe, ya que este curso lo aclarará más adelante en este capítulo.</span><span class="sxs-lookup"><span data-stu-id="31799-217">If these concepts are not perfectly clear, do not worry, as this course will clarify them further in this chapter.</span></span>

<span data-ttu-id="31799-218">Comenzará creando las *entidades* necesarias para compilar este curso.</span><span class="sxs-lookup"><span data-stu-id="31799-218">You will begin by creating the *Entities* needed to build this course.</span></span>

9.  <span data-ttu-id="31799-219">En el lado izquierdo de la página, haga clic en *entidades*y, a continuación, haga clic en **crear nueva entidad**.</span><span class="sxs-lookup"><span data-stu-id="31799-219">On the left side of the page, click on *Entities*, then click on **Create new entity**.</span></span>

    ![Crear nueva entidad](images/AzureLabs-Lab3-11.png)

10. <span data-ttu-id="31799-221">Llame al nuevo *color*de entidad, establezca su tipo en *simple*y, después, haga clic en **listo**.</span><span class="sxs-lookup"><span data-stu-id="31799-221">Call the new Entity *color*, set its type to *Simple*, then press **Done**.</span></span>

    ![Crear un color de entidad simple](images/AzureLabs-Lab3-12.png)
 
11. <span data-ttu-id="31799-223">Repita este proceso para crear tres (3) entidades más simples denominadas:</span><span class="sxs-lookup"><span data-stu-id="31799-223">Repeat this process to create three (3) more Simple Entities named:</span></span>

    -   <span data-ttu-id="31799-224">*actualizar*</span><span class="sxs-lookup"><span data-stu-id="31799-224">*upsize*</span></span>
    -   <span data-ttu-id="31799-225">*reducir*</span><span class="sxs-lookup"><span data-stu-id="31799-225">*downsize*</span></span>
    -   <span data-ttu-id="31799-226">*dirigir*</span><span class="sxs-lookup"><span data-stu-id="31799-226">*target*</span></span>

<span data-ttu-id="31799-227">El resultado debería ser similar a la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="31799-227">The result should look like the image below:</span></span>

![Resultado de la creación de entidades](images/AzureLabs-Lab3-13.png)
 
<span data-ttu-id="31799-229">Llegados a este punto, puede empezar a crear *intenciones*.</span><span class="sxs-lookup"><span data-stu-id="31799-229">At this point you can begin creating *Intents*.</span></span> 

> [!WARNING]
> <span data-ttu-id="31799-230">No elimine **ningún** intento.</span><span class="sxs-lookup"><span data-stu-id="31799-230">Do not delete the **None** intent.</span></span>

12. <span data-ttu-id="31799-231">En el lado izquierdo de la página, haga clic en **intenciones y, a continuación, haga**clic en **crear nuevo intento**.</span><span class="sxs-lookup"><span data-stu-id="31799-231">On the left side of the page, click on **Intents**, then click on **Create new intent**.</span></span>

    ![Crear nuevas intenciones](images/AzureLabs-Lab3-14.png)

13. <span data-ttu-id="31799-233">Llame al nuevo *intento* **ChangeObjectColor**.</span><span class="sxs-lookup"><span data-stu-id="31799-233">Call the new *Intent* **ChangeObjectColor**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="31799-234">Este nombre de *intención* se usa en el código más adelante en este curso, por lo que para obtener los mejores resultados, use este nombre exactamente como se indica.</span><span class="sxs-lookup"><span data-stu-id="31799-234">This *Intent* name is used within the code later in this course, so for best results, use this name exactly as provided.</span></span>

<span data-ttu-id="31799-235">Una vez que confirme el nombre, se le redirigirá a la página de intents.</span><span class="sxs-lookup"><span data-stu-id="31799-235">Once you confirm the name you will be directed to the Intents Page.</span></span>

![LUIS-página de intents](images/AzureLabs-Lab3-15.png)

<span data-ttu-id="31799-237">Observará que hay un cuadro de texto que le pide que escriba 5 o más *grabaciones*diferentes.</span><span class="sxs-lookup"><span data-stu-id="31799-237">You will notice that there is a textbox asking you to type 5 or more different *Utterances*.</span></span>

> [!NOTE]
> <span data-ttu-id="31799-238">LUIS convierte todos los grabaciones a minúsculas.</span><span class="sxs-lookup"><span data-stu-id="31799-238">LUIS converts all Utterances to lower case.</span></span>

14. <span data-ttu-id="31799-239">Inserte el siguiente *utterance* en el cuadro de texto superior (actualmente con el tipo de texto *sobre 5 ejemplos...*</span><span class="sxs-lookup"><span data-stu-id="31799-239">Insert the following *Utterance* in the top textbox (currently with the text *Type about 5 examples…*</span></span> <span data-ttu-id="31799-240">) y presione **entrar**:</span><span class="sxs-lookup"><span data-stu-id="31799-240">), and press **Enter**:</span></span>

```
The color of the cylinder must be red
```

<span data-ttu-id="31799-241">Observará que el nuevo *utterance* aparecerá en una lista debajo de.</span><span class="sxs-lookup"><span data-stu-id="31799-241">You will notice that the new *Utterance* will appear in a list underneath.</span></span>

<span data-ttu-id="31799-242">Siguiendo el mismo proceso, inserte los seis (6) grabaciones siguientes:</span><span class="sxs-lookup"><span data-stu-id="31799-242">Following the same process, insert the following six (6) Utterances:</span></span>

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

<span data-ttu-id="31799-243">Para cada utterance que haya creado, debe identificar qué palabras deben usar los LUIS como entidades.</span><span class="sxs-lookup"><span data-stu-id="31799-243">For each Utterance you have created, you must identify which words should be used by LUIS as Entities.</span></span> <span data-ttu-id="31799-244">En este ejemplo, debe etiquetar todos los colores como una entidad de *color* y todas las referencias posibles a un destino como entidad de *destino* .</span><span class="sxs-lookup"><span data-stu-id="31799-244">In this example you need to label all the colors as a *color* Entity, and all the possible reference to a target as a *target* Entity.</span></span>

15. <span data-ttu-id="31799-245">Para ello, intente hacer clic en la palabra *cilindro* en el primer utterance y seleccione *destino*.</span><span class="sxs-lookup"><span data-stu-id="31799-245">To do so, try clicking on the word *cylinder* in the first Utterance and select *target*.</span></span>

    ![Identificación de los destinos de utterance](images/AzureLabs-Lab3-16.png)
 
16. <span data-ttu-id="31799-247">Ahora, haga clic en la palabra *red* del primer utterance y seleccione *color*.</span><span class="sxs-lookup"><span data-stu-id="31799-247">Now click on the word *red* in the first Utterance and select *color*.</span></span>

    ![Identificación de las entidades utterance](images/AzureLabs-Lab3-17.png)
 
17. <span data-ttu-id="31799-249">Etiquete la siguiente línea también, donde *Cube* debe ser un *destino*y el *negro* debe ser un *color*.</span><span class="sxs-lookup"><span data-stu-id="31799-249">Label the next line also, where *cube* should be a *target*, and *black* should be a *color*.</span></span> <span data-ttu-id="31799-250">Observe también el uso de las palabras *' this '* , *' it '* y *' this Object '* , que ofrecemos, por lo que para tener también disponibles tipos de destino no específicos.</span><span class="sxs-lookup"><span data-stu-id="31799-250">Notice also the use of the words *‘this’*, *‘it’*, and *‘this object’*, which we are providing, so to have non-specific target types available also.</span></span> 

18. <span data-ttu-id="31799-251">Repita el proceso anterior hasta que todos los grabaciones tengan las entidades etiquetadas.</span><span class="sxs-lookup"><span data-stu-id="31799-251">Repeat the process above until all the Utterances have the Entities labelled.</span></span> <span data-ttu-id="31799-252">Si necesita ayuda, consulte la siguiente imagen.</span><span class="sxs-lookup"><span data-stu-id="31799-252">See the below image if you need help.</span></span>

    > [!TIP]
    > <span data-ttu-id="31799-253">Al seleccionar palabras para etiquetarlas como entidades:</span><span class="sxs-lookup"><span data-stu-id="31799-253">When selecting words to label them as entities:</span></span>
    > - <span data-ttu-id="31799-254">Solo tiene que hacer clic en las palabras individuales.</span><span class="sxs-lookup"><span data-stu-id="31799-254">For single words just click them.</span></span>
    > - <span data-ttu-id="31799-255">Para un conjunto de dos o más palabras, haga clic en al principio y, a continuación, al final del conjunto.</span><span class="sxs-lookup"><span data-stu-id="31799-255">For a set of two or more words, click at the beginning and then at the end of the set.</span></span>

    > [!NOTE]
    > <span data-ttu-id="31799-256">Puede usar el botón de alternancia de la *vista tokens* para cambiar entre la **vista de entidades y tokens**.</span><span class="sxs-lookup"><span data-stu-id="31799-256">You can use the *Tokens View* toggle button to switch between **Entities / Tokens View**!</span></span>

19. <span data-ttu-id="31799-257">Los resultados deben ser tal como se muestra en las imágenes siguientes, mostrando la **vista de entidades o tokens**:</span><span class="sxs-lookup"><span data-stu-id="31799-257">The results should be as seen in the images below, showing the **Entities / Tokens View**:</span></span>

    ![Tokens & vistas de entidades](images/AzureLabs-Lab3-18.png)
  
20. <span data-ttu-id="31799-259">En este punto, presione el botón **entrenar** situado en la parte superior derecha de la página y espere a que el pequeño indicador redondo se convierta en verde.</span><span class="sxs-lookup"><span data-stu-id="31799-259">At this point press the **Train** button at the top-right of the page and wait for the small round indicator on it to turn green.</span></span> <span data-ttu-id="31799-260">Esto indica que LUIS se ha entrenado correctamente para reconocer este intento.</span><span class="sxs-lookup"><span data-stu-id="31799-260">This indicates that LUIS has been successfully trained to recognize this Intent.</span></span>

    ![Entrenar a LUIS](images/AzureLabs-Lab3-19.png)
 
21. <span data-ttu-id="31799-262">Como ejercicio, cree un nuevo intento llamado **ChangeObjectSize**con las entidades *target* *, up y* *reducir*.</span><span class="sxs-lookup"><span data-stu-id="31799-262">As an exercise for you, create a new Intent called **ChangeObjectSize**, using the Entities *target*, *upsize*, and *downsize*.</span></span>
22. <span data-ttu-id="31799-263">Siguiendo el mismo proceso que la intención anterior, inserte los ocho (8) grabaciones siguientes para el cambio de *tamaño* :</span><span class="sxs-lookup"><span data-stu-id="31799-263">Following the same process as the previous Intent, insert the following eight (8) Utterances for *Size* change:</span></span>

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. <span data-ttu-id="31799-264">El resultado debería ser como el de la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="31799-264">The result should be like the one in the image below:</span></span>

    ![Configuración de las entidades o tokens de ChangeObjectSize](images/AzureLabs-Lab3-20.png) 

24. <span data-ttu-id="31799-266">Una vez que se han creado y entrenado las opciones intents, **ChangeObjectColor** y **ChangeObjectSize**, haga clic en el botón **publicar** de la parte superior de la página.</span><span class="sxs-lookup"><span data-stu-id="31799-266">Once both Intents, **ChangeObjectColor** and **ChangeObjectSize**, have been created and trained, click on the **PUBLISH** button on top of the page.</span></span>

    ![Publicar el servicio LUIS](images/AzureLabs-Lab3-21.png)

25. <span data-ttu-id="31799-268">En la página *publicar* , finalizará y publicará la aplicación Luis para que el código pueda acceder a ella.</span><span class="sxs-lookup"><span data-stu-id="31799-268">On the *Publish* page you will finalize and publish your LUIS App so that it can be accessed by your code.</span></span>

    1. <span data-ttu-id="31799-269">Establezca la lista desplegable *publicar en* como **producción**.</span><span class="sxs-lookup"><span data-stu-id="31799-269">Set the drop down *Publish To* as **Production**.</span></span>
    2. <span data-ttu-id="31799-270">Establezca la *zona horaria en la* zona horaria.</span><span class="sxs-lookup"><span data-stu-id="31799-270">Set the *Timezone* to your time zone.</span></span>
    3. <span data-ttu-id="31799-271">Active la casilla **incluir todas las puntuaciones de intención**previstas.</span><span class="sxs-lookup"><span data-stu-id="31799-271">Check the box **Include all predicted intent scores**.</span></span>
    4. <span data-ttu-id="31799-272">Haga clic en **publicar en ranura de producción**.</span><span class="sxs-lookup"><span data-stu-id="31799-272">Click on **Publish to Production Slot**.</span></span>

        ![Configuración de publicación](images/AzureLabs-Lab3-22.png)

26. <span data-ttu-id="31799-274">En la sección *recursos y claves*:</span><span class="sxs-lookup"><span data-stu-id="31799-274">In the section *Resources and Keys*:</span></span>

    1.  <span data-ttu-id="31799-275">Seleccione la región que estableció para instancia de servicio en Azure portal.</span><span class="sxs-lookup"><span data-stu-id="31799-275">Select the region you set for service instance in the Azure Portal.</span></span>
    2.  <span data-ttu-id="31799-276">Observará un **Starter_Key** elemento siguiente y lo omitirá.</span><span class="sxs-lookup"><span data-stu-id="31799-276">You will notice a **Starter_Key** element below, ignore it.</span></span>
    3.  <span data-ttu-id="31799-277">Haga clic en **Agregar clave** e inserte la *clave* que obtuvo en Azure portal al crear la instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="31799-277">Click on **Add Key** and insert the *Key* that you obtained in the Azure Portal when you created your Service instance.</span></span> <span data-ttu-id="31799-278">Si el portal de Azure y LUIS están conectados al mismo usuario, se le proporcionarán menús desplegables para el *nombre del inquilino*, el nombre de la *suscripción*y la *clave* que quiere usar (tendrá el mismo nombre que proporcionó anteriormente en Azure portal).</span><span class="sxs-lookup"><span data-stu-id="31799-278">If your Azure and the LUIS portal are logged into the same user, you will be provided drop-down menus for *Tenant name*, *Subscription Name*, and the *Key* you wish to use (will have the same name as you provided previously in the Azure Portal.</span></span>

    > [!IMPORTANT] 
    > <span data-ttu-id="31799-279">Debajo de *punto de conexión*, realice una copia del punto de conexión correspondiente a la clave que ha insertado. lo usará pronto en el código.</span><span class="sxs-lookup"><span data-stu-id="31799-279">Underneath *Endpoint*, take a copy of the endpoint corresponding to the Key you have inserted, you will soon use it in your code.</span></span>
 
## <a name="chapter-3--set-up-the-unity-project"></a><span data-ttu-id="31799-280">Capítulo 3: configuración del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="31799-280">Chapter 3 – Set up the Unity project</span></span>

<span data-ttu-id="31799-281">Lo siguiente es una configuración típica para desarrollar con la realidad mixta y, como tal, es una buena plantilla para otros proyectos.</span><span class="sxs-lookup"><span data-stu-id="31799-281">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="31799-282">Abra *Unity* y haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="31799-282">Open *Unity* and click **New**.</span></span> 

    ![Inicie el nuevo proyecto de Unity.](images/AzureLabs-Lab3-24.png)

2.  <span data-ttu-id="31799-284">Ahora tendrá que proporcionar un nombre de proyecto de Unity, insertar **MR_LUIS**.</span><span class="sxs-lookup"><span data-stu-id="31799-284">You will now need to provide a Unity Project name, insert **MR_LUIS**.</span></span> <span data-ttu-id="31799-285">Asegúrese de que el tipo de proyecto está establecido en **3D**.</span><span class="sxs-lookup"><span data-stu-id="31799-285">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="31799-286">Establezca la **Ubicación** en algún lugar adecuado para usted (Recuerde que, más cerca de los directorios raíz es mejor).</span><span class="sxs-lookup"><span data-stu-id="31799-286">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="31799-287">A continuación, haga clic en **crear proyecto**.</span><span class="sxs-lookup"><span data-stu-id="31799-287">Then, click **Create project**.</span></span>

    ![Proporcione los detalles del nuevo proyecto de Unity.](images/AzureLabs-Lab3-25.png)
 
3.  <span data-ttu-id="31799-289">Con Unity abierto, merece la pena comprobar que el **Editor de scripts** predeterminado está establecido en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="31799-289">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="31799-290">Vaya a Editar > Preferencias y, a continuación, en la nueva ventana, vaya a **herramientas externas**.</span><span class="sxs-lookup"><span data-stu-id="31799-290">Go to Edit > Preferences and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="31799-291">Cambie el **Editor de script externo** a **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="31799-291">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="31799-292">Cierre la ventana **preferencias** .</span><span class="sxs-lookup"><span data-stu-id="31799-292">Close the **Preferences** window.</span></span>

    ![Actualice las preferencias del editor de scripts.](images/AzureLabs-Lab3-26.png)
 
4.  <span data-ttu-id="31799-294">A continuación, vaya a **archivo > configuración de compilación** y cambie la plataforma a **plataforma universal de Windows**, haciendo clic en el botón **cambiar plataforma** .</span><span class="sxs-lookup"><span data-stu-id="31799-294">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Ventana Configuración de compilación, cambiar plataforma a UWP.](images/AzureLabs-Lab3-27.png)
 
5.  <span data-ttu-id="31799-296">Vaya a **archivo > configuración de compilación** y asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="31799-296">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="31799-297">El **dispositivo de destino** se establece en **cualquier dispositivo**</span><span class="sxs-lookup"><span data-stu-id="31799-297">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="31799-298">Para Microsoft HoloLens, establezca el **dispositivo de destino** en *hololens*.</span><span class="sxs-lookup"><span data-stu-id="31799-298">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="31799-299">El **tipo de compilación** se establece en **D3D**</span><span class="sxs-lookup"><span data-stu-id="31799-299">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="31799-300">**SDK** está establecido en la **versión más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="31799-300">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="31799-301">La **versión de Visual Studio** está establecida en la **más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="31799-301">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="31799-302">**Compilar y ejecutar** está establecido en **equipo local**</span><span class="sxs-lookup"><span data-stu-id="31799-302">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="31799-303">Guarde la escena y agréguela a la compilación.</span><span class="sxs-lookup"><span data-stu-id="31799-303">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="31799-304">Para ello, seleccione **Agregar escenas abiertas**.</span><span class="sxs-lookup"><span data-stu-id="31799-304">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="31799-305">Aparecerá una ventana de guardar.</span><span class="sxs-lookup"><span data-stu-id="31799-305">A save window will appear.</span></span>
        
            ![Haga clic en el botón Agregar escenas abiertas](images/AzureLabs-Lab3-28.png)

        2. <span data-ttu-id="31799-307">Cree una nueva carpeta para este, y en cualquier momento, en el futuro, seleccione el botón **nueva carpeta** para crear una nueva carpeta, asígnele el nombre **Scenes**.</span><span class="sxs-lookup"><span data-stu-id="31799-307">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Crear nueva carpeta de scripts](images/AzureLabs-Lab3-29.png)

        3. <span data-ttu-id="31799-309">Abra la carpeta **escenas** recién creada y, a continuación, en el campo *nombre de archivo*:, escriba **MR_LuisScene**y, a continuación, presione **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="31799-309">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_LuisScene**, then press **Save**.</span></span>

            ![Asigne un nombre a la nueva escena.](images/AzureLabs-Lab3-30.png)

    7. <span data-ttu-id="31799-311">El resto de la configuración, en la *configuración de compilación*, debe dejarse como predeterminada por ahora.</span><span class="sxs-lookup"><span data-stu-id="31799-311">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="31799-312">En la ventana *configuración de compilación* , haga clic en el botón Configuración del **reproductor** ; se abrirá el panel relacionado en el espacio donde se encuentra el *Inspector* .</span><span class="sxs-lookup"><span data-stu-id="31799-312">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Abra configuración del reproductor.](images/AzureLabs-Lab3-31.png) 
 
7. <span data-ttu-id="31799-314">En este panel, deben comprobarse algunas opciones de configuración:</span><span class="sxs-lookup"><span data-stu-id="31799-314">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="31799-315">En la pestaña **otros valores** :</span><span class="sxs-lookup"><span data-stu-id="31799-315">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="31799-316">La **versión de scripting en tiempo de ejecución** debe ser **estable** (.net 3,5 equivalente).</span><span class="sxs-lookup"><span data-stu-id="31799-316">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="31799-317">El **back-end de scripting** debe ser **.net**</span><span class="sxs-lookup"><span data-stu-id="31799-317">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="31799-318">El **nivel de compatibilidad de API** debe ser **.net 4,6**</span><span class="sxs-lookup"><span data-stu-id="31799-318">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Actualice otras opciones de configuración.](images/AzureLabs-Lab3-32.png)
      
    2. <span data-ttu-id="31799-320">En la pestaña **configuración de publicación** , en **capacidades**, seleccione:</span><span class="sxs-lookup"><span data-stu-id="31799-320">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="31799-321">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="31799-321">**InternetClient**</span></span>
        2. <span data-ttu-id="31799-322">**Micrófono**</span><span class="sxs-lookup"><span data-stu-id="31799-322">**Microphone**</span></span>

            ![Actualizando la configuración de publicación.](images/AzureLabs-Lab3-33.png)

    3. <span data-ttu-id="31799-324">Más abajo en el panel, en la **configuración de XR** (se encuentra debajo de **configuración de publicación**), tick **Virtual Reality compatible**, asegúrese de que se agrega el **SDK de Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="31799-324">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Actualice la configuración de X R.](images/AzureLabs-Lab3-34.png)

8.  <span data-ttu-id="31799-326">De nuevo en la *configuración de compilación* , los proyectos de _Unity C#_  ya no están atenuados; Marque la casilla situada junto a este.</span><span class="sxs-lookup"><span data-stu-id="31799-326">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="31799-327">Cierre la ventana Configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="31799-327">Close the Build Settings window.</span></span>
10. <span data-ttu-id="31799-328">Guarde la escena y el proyecto (**archivo > guardar la escena o el archivo > guardar proyecto**).</span><span class="sxs-lookup"><span data-stu-id="31799-328">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4--create-the-scene"></a><span data-ttu-id="31799-329">Capítulo 4: creación de la escena</span><span class="sxs-lookup"><span data-stu-id="31799-329">Chapter 4 – Create the scene</span></span>

> [!IMPORTANT]
> <span data-ttu-id="31799-330">Si desea omitir el componente *de configuración de Unity* de este curso y continuar directamente en el código, no dude en descargar este [. unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), impórtelo en el proyecto como un [paquete personalizado](https://docs.unity3d.com/Manual/AssetPackages.html)y, después, continúe con el [capítulo 5](#chapter-5--create-the-microphonemanager-class).</span><span class="sxs-lookup"><span data-stu-id="31799-330">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-microphonemanager-class).</span></span> 

1.  <span data-ttu-id="31799-331">Haga clic con el botón secundario en un área vacía del *Panel de jerarquías*, en **objeto 3D**, agregar un **plano**.</span><span class="sxs-lookup"><span data-stu-id="31799-331">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Plane**.</span></span>

    ![Cree un plano.](images/AzureLabs-Lab3-35.png)

2.  <span data-ttu-id="31799-333">Tenga en cuenta que al hacer clic con el botón secundario en la *jerarquía* de nuevo para crear más objetos, si todavía tiene el último objeto seleccionado, el objeto seleccionado será el elemento primario del nuevo objeto.</span><span class="sxs-lookup"><span data-stu-id="31799-333">Be aware that when you right-click within the *Hierarchy* again to create more objects, if you still have the last object selected, the selected object will be the parent of your new object.</span></span> <span data-ttu-id="31799-334">Evite este clic con el botón secundario en un espacio vacío dentro de la jerarquía y, a continuación, haga clic con el botón derecho en.</span><span class="sxs-lookup"><span data-stu-id="31799-334">Avoid this left-clicking in an empty space within the Hierarchy, and then right-clicking.</span></span>

3.  <span data-ttu-id="31799-335">Repita el procedimiento anterior para agregar los objetos siguientes:</span><span class="sxs-lookup"><span data-stu-id="31799-335">Repeat the above procedure to add the following objects:</span></span>

    1. <span data-ttu-id="31799-336">*Compartimiento*</span><span class="sxs-lookup"><span data-stu-id="31799-336">*Sphere*</span></span>
    2. <span data-ttu-id="31799-337">*Cerradura*</span><span class="sxs-lookup"><span data-stu-id="31799-337">*Cylinder*</span></span>
    3. <span data-ttu-id="31799-338">*BD*</span><span class="sxs-lookup"><span data-stu-id="31799-338">*Cube*</span></span>
    4. <span data-ttu-id="31799-339">*Texto 3D*</span><span class="sxs-lookup"><span data-stu-id="31799-339">*3D Text*</span></span>

4.  <span data-ttu-id="31799-340">La *jerarquía* de escenas resultante debe ser similar a la de la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="31799-340">The resulting scene *Hierarchy* should be like the one in the image below:</span></span>

    ![Configuración de la jerarquía de escenas.](images/AzureLabs-Lab3-36.png)
 
5.  <span data-ttu-id="31799-342">Haga clic con el botón izquierdo en la **cámara principal** para seleccionarla y, en el *Panel de inspector* , verá el objeto de cámara con todos sus componentes.</span><span class="sxs-lookup"><span data-stu-id="31799-342">Left click on the **Main Camera** to select it, look at the *Inspector Panel* you will see the Camera object with all the its components.</span></span>
6.  <span data-ttu-id="31799-343">Haga clic en el botón **Agregar componente** situado en la parte inferior del *panel Inspector*.</span><span class="sxs-lookup"><span data-stu-id="31799-343">Click on the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span>

    ![Agregar origen de audio](images/AzureLabs-Lab3-37.png)
 
7.  <span data-ttu-id="31799-345">Busque el componente denominado *origen de audio*, como se mostró anteriormente.</span><span class="sxs-lookup"><span data-stu-id="31799-345">Search for the component called *Audio Source*, as shown above.</span></span>
8.  <span data-ttu-id="31799-346">Asegúrese también de que el componente de *transformación* de la cámara principal esté establecido en (0,0). para ello, presione el icono de **engranaje** situado junto al componente de *transformación* de la cámara y seleccione **restablecer**.</span><span class="sxs-lookup"><span data-stu-id="31799-346">Also make sure that the *Transform* component of the Main Camera is set to (0,0,0), this can be done by pressing the **Gear** icon next to the Camera’s *Transform* component and selecting **Reset**.</span></span> <span data-ttu-id="31799-347">El componente de *transformación* debería tener el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="31799-347">The *Transform* component should then look like:</span></span>

    1.  <span data-ttu-id="31799-348">La *posición* se establece en **0, 0,0**.</span><span class="sxs-lookup"><span data-stu-id="31799-348">*Position* is set to **0, 0, 0**.</span></span>
    2.  <span data-ttu-id="31799-349">La *rotación* se establece en **0,** 0,0.</span><span class="sxs-lookup"><span data-stu-id="31799-349">*Rotation* is set to **0, 0, 0**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="31799-350">En el caso de Microsoft HoloLens, también deberá cambiar lo siguiente, que forman parte del componente de **cámara** , que se encuentra en la **cámara principal**:</span><span class="sxs-lookup"><span data-stu-id="31799-350">For the Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component, which is on your **Main Camera**:</span></span>
    > - <span data-ttu-id="31799-351">**Borrar marcas:** Color sólido.</span><span class="sxs-lookup"><span data-stu-id="31799-351">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="31799-352">**Información general** ' Black, Alpha 0 ' – color Hex: #00000000.</span><span class="sxs-lookup"><span data-stu-id="31799-352">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

9.  <span data-ttu-id="31799-353">Haga clic con el botón izquierdo en el **plano** para seleccionarlo.</span><span class="sxs-lookup"><span data-stu-id="31799-353">Left click on the **Plane** to select it.</span></span> <span data-ttu-id="31799-354">En el *panel Inspector* , establezca el componente de *transformación* con los siguientes valores:</span><span class="sxs-lookup"><span data-stu-id="31799-354">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="31799-355">Transformación: *posición*</span><span class="sxs-lookup"><span data-stu-id="31799-355">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="31799-356">**X1**</span><span class="sxs-lookup"><span data-stu-id="31799-356">**X**</span></span> | <span data-ttu-id="31799-357">**Sí**</span><span class="sxs-lookup"><span data-stu-id="31799-357">**Y**</span></span>                  | <span data-ttu-id="31799-358">**Z**</span><span class="sxs-lookup"><span data-stu-id="31799-358">**Z**</span></span> |
    | <span data-ttu-id="31799-359">0</span><span class="sxs-lookup"><span data-stu-id="31799-359">0</span></span>     | <span data-ttu-id="31799-360">-1</span><span class="sxs-lookup"><span data-stu-id="31799-360">-1</span></span>                     | <span data-ttu-id="31799-361">0</span><span class="sxs-lookup"><span data-stu-id="31799-361">0</span></span>     |


10. <span data-ttu-id="31799-362">Haga clic con el botón izquierdo en la **esfera** para seleccionarlo.</span><span class="sxs-lookup"><span data-stu-id="31799-362">Left click on the **Sphere** to select it.</span></span> <span data-ttu-id="31799-363">En el *panel Inspector* , establezca el componente de *transformación* con los siguientes valores:</span><span class="sxs-lookup"><span data-stu-id="31799-363">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="31799-364">Transformación: *posición*</span><span class="sxs-lookup"><span data-stu-id="31799-364">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="31799-365">**X1**</span><span class="sxs-lookup"><span data-stu-id="31799-365">**X**</span></span> | <span data-ttu-id="31799-366">**Sí**</span><span class="sxs-lookup"><span data-stu-id="31799-366">**Y**</span></span>                  | <span data-ttu-id="31799-367">**Z**</span><span class="sxs-lookup"><span data-stu-id="31799-367">**Z**</span></span> |
    | <span data-ttu-id="31799-368">2</span><span class="sxs-lookup"><span data-stu-id="31799-368">2</span></span>     | <span data-ttu-id="31799-369">1</span><span class="sxs-lookup"><span data-stu-id="31799-369">1</span></span>                      | <span data-ttu-id="31799-370">2</span><span class="sxs-lookup"><span data-stu-id="31799-370">2</span></span>     |

11. <span data-ttu-id="31799-371">Haga clic con el botón izquierdo en el **cilindro** para seleccionarlo.</span><span class="sxs-lookup"><span data-stu-id="31799-371">Left click on the **Cylinder** to select it.</span></span> <span data-ttu-id="31799-372">En el *panel Inspector* , establezca el componente de *transformación* con los siguientes valores:</span><span class="sxs-lookup"><span data-stu-id="31799-372">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="31799-373">Transformación: *posición*</span><span class="sxs-lookup"><span data-stu-id="31799-373">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="31799-374">**X1**</span><span class="sxs-lookup"><span data-stu-id="31799-374">**X**</span></span> | <span data-ttu-id="31799-375">**Sí**</span><span class="sxs-lookup"><span data-stu-id="31799-375">**Y**</span></span>                  | <span data-ttu-id="31799-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="31799-376">**Z**</span></span> |
    | <span data-ttu-id="31799-377">-2</span><span class="sxs-lookup"><span data-stu-id="31799-377">-2</span></span>    | <span data-ttu-id="31799-378">1</span><span class="sxs-lookup"><span data-stu-id="31799-378">1</span></span>                      | <span data-ttu-id="31799-379">2</span><span class="sxs-lookup"><span data-stu-id="31799-379">2</span></span>     |

12. <span data-ttu-id="31799-380">Haga clic con el botón izquierdo en el **cubo** para seleccionarlo.</span><span class="sxs-lookup"><span data-stu-id="31799-380">Left click on the **Cube** to select it.</span></span> <span data-ttu-id="31799-381">En el *panel Inspector* , establezca el componente de *transformación* con los siguientes valores:</span><span class="sxs-lookup"><span data-stu-id="31799-381">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |        | <span data-ttu-id="31799-382">Transformación: *posición*</span><span class="sxs-lookup"><span data-stu-id="31799-382">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="31799-383">Transformación- *giro*</span><span class="sxs-lookup"><span data-stu-id="31799-383">Transform - *Rotation*</span></span> |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="31799-384">**X1**</span><span class="sxs-lookup"><span data-stu-id="31799-384">**X**</span></span> | <span data-ttu-id="31799-385">**Sí**</span><span class="sxs-lookup"><span data-stu-id="31799-385">**Y**</span></span>                   | <span data-ttu-id="31799-386">**Z**</span><span class="sxs-lookup"><span data-stu-id="31799-386">**Z**</span></span> |  \| | <span data-ttu-id="31799-387">**X1**</span><span class="sxs-lookup"><span data-stu-id="31799-387">**X**</span></span> | <span data-ttu-id="31799-388">**Sí**</span><span class="sxs-lookup"><span data-stu-id="31799-388">**Y**</span></span>                  | <span data-ttu-id="31799-389">**Z**</span><span class="sxs-lookup"><span data-stu-id="31799-389">**Z**</span></span> |
    | <span data-ttu-id="31799-390">0</span><span class="sxs-lookup"><span data-stu-id="31799-390">0</span></span>     | <span data-ttu-id="31799-391">1</span><span class="sxs-lookup"><span data-stu-id="31799-391">1</span></span>                       | <span data-ttu-id="31799-392">4</span><span class="sxs-lookup"><span data-stu-id="31799-392">4</span></span>     |  \| | <span data-ttu-id="31799-393">45</span><span class="sxs-lookup"><span data-stu-id="31799-393">45</span></span>    | <span data-ttu-id="31799-394">45</span><span class="sxs-lookup"><span data-stu-id="31799-394">45</span></span>                     | <span data-ttu-id="31799-395">0</span><span class="sxs-lookup"><span data-stu-id="31799-395">0</span></span>     | 

13. <span data-ttu-id="31799-396">Haga clic con el botón izquierdo en el nuevo objeto de **texto** para seleccionarlo.</span><span class="sxs-lookup"><span data-stu-id="31799-396">Left click on the **New Text** object to select it.</span></span> <span data-ttu-id="31799-397">En el *panel Inspector* , establezca el componente de *transformación* con los siguientes valores:</span><span class="sxs-lookup"><span data-stu-id="31799-397">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="31799-398">Transformación: *posición*</span><span class="sxs-lookup"><span data-stu-id="31799-398">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="31799-399">Transformación de *escala*</span><span class="sxs-lookup"><span data-stu-id="31799-399">Transform - *Scale*</span></span> |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | <span data-ttu-id="31799-400">**X1**</span><span class="sxs-lookup"><span data-stu-id="31799-400">**X**</span></span> | <span data-ttu-id="31799-401">**Sí**</span><span class="sxs-lookup"><span data-stu-id="31799-401">**Y**</span></span>                  | <span data-ttu-id="31799-402">**Z**</span><span class="sxs-lookup"><span data-stu-id="31799-402">**Z**</span></span> |  \| | <span data-ttu-id="31799-403">**X1**</span><span class="sxs-lookup"><span data-stu-id="31799-403">**X**</span></span> | <span data-ttu-id="31799-404">**Sí**</span><span class="sxs-lookup"><span data-stu-id="31799-404">**Y**</span></span>               | <span data-ttu-id="31799-405">**Z**</span><span class="sxs-lookup"><span data-stu-id="31799-405">**Z**</span></span> |
    | <span data-ttu-id="31799-406">-2</span><span class="sxs-lookup"><span data-stu-id="31799-406">-2</span></span>    | <span data-ttu-id="31799-407">6</span><span class="sxs-lookup"><span data-stu-id="31799-407">6</span></span>                      | <span data-ttu-id="31799-408">9</span><span class="sxs-lookup"><span data-stu-id="31799-408">9</span></span>     |  \| | <span data-ttu-id="31799-409">0,1</span><span class="sxs-lookup"><span data-stu-id="31799-409">0.1</span></span>   | <span data-ttu-id="31799-410">0,1</span><span class="sxs-lookup"><span data-stu-id="31799-410">0.1</span></span>                 | <span data-ttu-id="31799-411">0,1</span><span class="sxs-lookup"><span data-stu-id="31799-411">0.1</span></span>   | 

14. <span data-ttu-id="31799-412">Cambie el **tamaño de fuente** en el componente de malla de **texto** a **50**.</span><span class="sxs-lookup"><span data-stu-id="31799-412">Change **Font Size** in the **Text Mesh** component to **50**.</span></span>
15. <span data-ttu-id="31799-413">Cambie el *nombre* del objeto de **malla de texto** a texto de **dictado**.</span><span class="sxs-lookup"><span data-stu-id="31799-413">Change the *name* of the **Text Mesh** object to **Dictation Text**.</span></span>

    ![Crear objeto de texto 3D](images/AzureLabs-Lab3-38.png)
 
16. <span data-ttu-id="31799-415">La estructura del panel de jerarquías debería tener ahora el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="31799-415">Your Hierarchy Panel structure should now look like this:</span></span>

    ![malla de texto en la vista de escenas](images/AzureLabs-Lab3-38b.png)


17. <span data-ttu-id="31799-417">La escena final debe ser similar a la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="31799-417">The final scene should look like the image below:</span></span>

    ![Vista de la escena.](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a><span data-ttu-id="31799-419">Capítulo 5: crear la clase MicrophoneManager</span><span class="sxs-lookup"><span data-stu-id="31799-419">Chapter 5 – Create the MicrophoneManager class</span></span>

<span data-ttu-id="31799-420">El primer script que va a crear es la clase *MicrophoneManager* .</span><span class="sxs-lookup"><span data-stu-id="31799-420">The first Script you are going to create is the *MicrophoneManager* class.</span></span> <span data-ttu-id="31799-421">Después, creará el *LuisManager*, la clase de *comportamientos* y, por último, la clase de *miras* (no dude en crearlos ahora, aunque se cubrirá cuando llegue a cada capítulo).</span><span class="sxs-lookup"><span data-stu-id="31799-421">Following this, you will create the *LuisManager*, the *Behaviours* class, and lastly the *Gaze* class (feel free to create all these now, though it will be covered as you reach each Chapter).</span></span>

<span data-ttu-id="31799-422">La clase *MicrophoneManager* es responsable de:</span><span class="sxs-lookup"><span data-stu-id="31799-422">The *MicrophoneManager* class is responsible for:</span></span>

-   <span data-ttu-id="31799-423">Detección del dispositivo de grabación conectado a los auriculares o al equipo (lo que sea el predeterminado).</span><span class="sxs-lookup"><span data-stu-id="31799-423">Detecting the recording device attached to the headset or machine (whichever is the default one).</span></span>
-   <span data-ttu-id="31799-424">Capture el audio (voz) y use el dictado para almacenarlo como una cadena.</span><span class="sxs-lookup"><span data-stu-id="31799-424">Capture the audio (voice) and use dictation to store it as a string.</span></span>
-   <span data-ttu-id="31799-425">Una vez que se haya pausado la voz, envíe el dictado a la clase *LuisManager* .</span><span class="sxs-lookup"><span data-stu-id="31799-425">Once the voice has paused, submit the dictation to the *LuisManager* class.</span></span> 

<span data-ttu-id="31799-426">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="31799-426">To create this class:</span></span> 

1.  <span data-ttu-id="31799-427">Haga clic con el botón derecho en el *panel Proyecto*, **cree > carpeta**.</span><span class="sxs-lookup"><span data-stu-id="31799-427">Right-click in the *Project Panel*, **Create > Folder**.</span></span> <span data-ttu-id="31799-428">Llame a los **scripts**de la carpeta.</span><span class="sxs-lookup"><span data-stu-id="31799-428">Call the folder **Scripts**.</span></span> 

    ![Crear carpeta de scripts.](images/AzureLabs-Lab3-40.png)
 
2.  <span data-ttu-id="31799-430">Con la carpeta **scripts** creada, haga doble clic en ella para abrirla.</span><span class="sxs-lookup"><span data-stu-id="31799-430">With the **Scripts** folder created, double click it, to open.</span></span> <span data-ttu-id="31799-431">A continuación, en esa carpeta, haga clic con el botón secundario en **crear > C# script**.</span><span class="sxs-lookup"><span data-stu-id="31799-431">Then, within that folder, right-click, **Create > C# Script**.</span></span> <span data-ttu-id="31799-432">Asigne al script el nombre *MicrophoneManager*.</span><span class="sxs-lookup"><span data-stu-id="31799-432">Name the script *MicrophoneManager*.</span></span> 

3.  <span data-ttu-id="31799-433">Haga doble clic en *MicrophoneManager* para abrirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="31799-433">Double click on *MicrophoneManager* to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="31799-434">Agregue los siguientes espacios de nombres al principio del archivo:</span><span class="sxs-lookup"><span data-stu-id="31799-434">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="31799-435">A continuación, agregue las siguientes variables dentro de la clase *MicrophoneManager* :</span><span class="sxs-lookup"><span data-stu-id="31799-435">Then add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  <span data-ttu-id="31799-436">Ahora es necesario agregar el código para los métodos *activo ()* e *Inicio ()* .</span><span class="sxs-lookup"><span data-stu-id="31799-436">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="31799-437">Se llamará cuando se inicialice la clase:</span><span class="sxs-lookup"><span data-stu-id="31799-437">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  <span data-ttu-id="31799-438">Ahora necesita el método que usa la aplicación para iniciar y detener la captura de voz y pasarlo a la clase *LuisManager* , que creará pronto.</span><span class="sxs-lookup"><span data-stu-id="31799-438">Now you need the method that the App uses to start and stop the voice capture, and pass it to the *LuisManager* class, that you will build soon.</span></span> 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  <span data-ttu-id="31799-439">Agregue un *controlador de dictado* que se invocará cuando la voz se ponga en pausa.</span><span class="sxs-lookup"><span data-stu-id="31799-439">Add a *Dictation Handler* that will be invoked when the voice pauses.</span></span> <span data-ttu-id="31799-440">Este método pasará el texto de dictado a la clase *LuisManager* .</span><span class="sxs-lookup"><span data-stu-id="31799-440">This method will pass the dictation text to the *LuisManager* class.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="31799-441">Elimine el método *Update ()* , ya que esta clase no lo usará.</span><span class="sxs-lookup"><span data-stu-id="31799-441">Delete the *Update()* method since this class will not use it.</span></span>

9.  <span data-ttu-id="31799-442">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="31799-442">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

    > [!NOTE]
    > <span data-ttu-id="31799-443">En este punto, observará que aparece un error en el *Panel*de la consola del editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="31799-443">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="31799-444">Esto se debe a que el código hace referencia a la clase *LuisManager* que creará en el siguiente capítulo.</span><span class="sxs-lookup"><span data-stu-id="31799-444">This is because the code references the *LuisManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-6--create-the-luismanager-class"></a><span data-ttu-id="31799-445">Capítulo 6: crear la clase LUISManager</span><span class="sxs-lookup"><span data-stu-id="31799-445">Chapter 6 – Create the LUISManager class</span></span>

<span data-ttu-id="31799-446">Es el momento de crear la clase *LuisManager* , que realizará la llamada al servicio de Luis de Azure.</span><span class="sxs-lookup"><span data-stu-id="31799-446">It is time for you to create the *LuisManager* class, which will make the call to the Azure LUIS service.</span></span> 

<span data-ttu-id="31799-447">El propósito de esta clase es recibir el texto de dictado de la clase *MicrophoneManager* y enviarlo al *Language Understanding API de Azure* que se va a analizar.</span><span class="sxs-lookup"><span data-stu-id="31799-447">The purpose of this class is to receive the dictation text from the *MicrophoneManager* class and send it to the *Azure Language Understanding API* to be analyzed.</span></span>

<span data-ttu-id="31799-448">Esta clase deserializará la respuesta *JSON* y llamará a los métodos adecuados de la clase de *comportamientos* para desencadenar una acción.</span><span class="sxs-lookup"><span data-stu-id="31799-448">This class will deserialize the *JSON* response and call the appropriate methods of the *Behaviours* class to trigger an action.</span></span>

<span data-ttu-id="31799-449">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="31799-449">To create this class:</span></span> 

1.  <span data-ttu-id="31799-450">Haga doble clic en la carpeta **scripts** para abrirla.</span><span class="sxs-lookup"><span data-stu-id="31799-450">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="31799-451">Haga clic con el botón derecho en la carpeta **scripts** y haga clic en **crear > C# script**.</span><span class="sxs-lookup"><span data-stu-id="31799-451">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="31799-452">Asigne al script el nombre *LuisManager*.</span><span class="sxs-lookup"><span data-stu-id="31799-452">Name the script *LuisManager*.</span></span> 
3.  <span data-ttu-id="31799-453">Haga doble clic en el script para abrirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="31799-453">Double click on the script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="31799-454">Agregue los siguientes espacios de nombres al principio del archivo:</span><span class="sxs-lookup"><span data-stu-id="31799-454">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="31799-455">Comenzará creando tres clases **dentro** de la clase *LuisManager* (dentro del mismo archivo de script, encima del método *Start ()* ) que representará la respuesta JSON deserializada de Azure.</span><span class="sxs-lookup"><span data-stu-id="31799-455">You will begin by creating three classes **inside** the *LuisManager* class (within the same script file, above the *Start()* method) that will represent the deserialized JSON response from Azure.</span></span>

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  <span data-ttu-id="31799-456">A continuación, agregue las siguientes variables dentro de la clase *LuisManager* :</span><span class="sxs-lookup"><span data-stu-id="31799-456">Next, add the following variables inside the *LuisManager* class:</span></span>
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  <span data-ttu-id="31799-457">Asegúrese de colocar el punto de conexión de LUIS en este momento (que tendrá del portal de LUIS).</span><span class="sxs-lookup"><span data-stu-id="31799-457">Make sure to place your LUIS endpoint in now (which you will have from your LUIS portal).</span></span>

8.  <span data-ttu-id="31799-458">Ahora es necesario agregar el código para el método *activo ()* .</span><span class="sxs-lookup"><span data-stu-id="31799-458">Code for the *Awake()* method now needs to be added.</span></span> <span data-ttu-id="31799-459">Se llamará a este método cuando se inicialice la clase:</span><span class="sxs-lookup"><span data-stu-id="31799-459">This method will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  <span data-ttu-id="31799-460">Ahora necesita los métodos que esta aplicación usa para enviar el dictado recibido de la clase *MicrophoneManager* a *Luis*y, a continuación, recibir y deserializar la respuesta.</span><span class="sxs-lookup"><span data-stu-id="31799-460">Now you need the methods this application uses to send the dictation received from the *MicrophoneManager* class to *LUIS*, and then receive and deserialize the response.</span></span> 
10. <span data-ttu-id="31799-461">Una vez que se ha determinado el valor de la intención y las entidades asociadas, se pasan a la instancia de la clase de *comportamientos* para desencadenar la acción deseada.</span><span class="sxs-lookup"><span data-stu-id="31799-461">Once the value of the Intent, and associated Entities, have been determined, they are passed to the instance of the *Behaviours* class to trigger the intended action.</span></span>

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. <span data-ttu-id="31799-462">Cree un nuevo método llamado *AnalyseResponseElements ()* que leerá el *AnalysedQuery* resultante y determine las entidades.</span><span class="sxs-lookup"><span data-stu-id="31799-462">Create a new method called *AnalyseResponseElements()* that will read the resulting *AnalysedQuery* and determine the Entities.</span></span> <span data-ttu-id="31799-463">Una vez que se determinen esas entidades, se pasarán a la instancia de la clase de *comportamientos* que se va a usar en las acciones.</span><span class="sxs-lookup"><span data-stu-id="31799-463">Once those Entities are determined, they will be passed to the instance of the *Behaviours* class to use in the actions.</span></span>

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognized intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="31799-464">Elimine los métodos *Start ()* y *Update ()* , ya que esta clase no los usará.</span><span class="sxs-lookup"><span data-stu-id="31799-464">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

12. <span data-ttu-id="31799-465">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="31799-465">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

> [!NOTE]
> <span data-ttu-id="31799-466">En este punto, observará que aparecen varios errores en el *Panel*de la consola del editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="31799-466">At this point you will notice several errors appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="31799-467">Esto se debe a que el código hace referencia a la clase de *comportamientos* que creará en el siguiente capítulo.</span><span class="sxs-lookup"><span data-stu-id="31799-467">This is because the code references the *Behaviours* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--create-the-behaviours-class"></a><span data-ttu-id="31799-468">Capítulo 7: creación de la clase de comportamientos</span><span class="sxs-lookup"><span data-stu-id="31799-468">Chapter 7 – Create the Behaviours class</span></span>

<span data-ttu-id="31799-469">La clase de *comportamientos* desencadenará las acciones mediante las entidades proporcionadas por la clase *LuisManager* .</span><span class="sxs-lookup"><span data-stu-id="31799-469">The *Behaviours* class will trigger the actions using the Entities provided by the *LuisManager* class.</span></span>

<span data-ttu-id="31799-470">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="31799-470">To create this class:</span></span> 

1.  <span data-ttu-id="31799-471">Haga doble clic en la carpeta **scripts** para abrirla.</span><span class="sxs-lookup"><span data-stu-id="31799-471">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="31799-472">Haga clic con el botón derecho en la carpeta **scripts** y haga clic en **crear > C# script**.</span><span class="sxs-lookup"><span data-stu-id="31799-472">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="31799-473">Asigne un nombre a los *comportamientos*del script.</span><span class="sxs-lookup"><span data-stu-id="31799-473">Name the script *Behaviours*.</span></span> 
3.  <span data-ttu-id="31799-474">Haga doble clic en el script para abrirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="31799-474">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="31799-475">A continuación, agregue las siguientes variables dentro de la clase de *comportamientos* :</span><span class="sxs-lookup"><span data-stu-id="31799-475">Then add the following variables inside the *Behaviours* class:</span></span>

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  <span data-ttu-id="31799-476">Agregue el código del método *activo ()* .</span><span class="sxs-lookup"><span data-stu-id="31799-476">Add the *Awake()* method code.</span></span> <span data-ttu-id="31799-477">Se llamará a este método cuando se inicialice la clase:</span><span class="sxs-lookup"><span data-stu-id="31799-477">This method will be called when the class initializes:</span></span>

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  <span data-ttu-id="31799-478">La clase *LuisManager* (que ha creado anteriormente) llama a los métodos siguientes para determinar qué objeto es el destino de la consulta y, a continuación, desencadenar la acción adecuada.</span><span class="sxs-lookup"><span data-stu-id="31799-478">The following methods are called by the *LuisManager* class (which you have created previously) to determine which object is the target of the query and then trigger the appropriate action.</span></span>

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  <span data-ttu-id="31799-479">Agregue el método *FindTarget ()* para determinar cuál de *GameObjects* es el destino de la intención actual.</span><span class="sxs-lookup"><span data-stu-id="31799-479">Add the *FindTarget()* method to determine which of the *GameObjects* is the target of the current Intent.</span></span> <span data-ttu-id="31799-480">Este método usa de forma predeterminada el destino en el *GameObject* que se "mira" si no se define ningún destino explícito en las entidades.</span><span class="sxs-lookup"><span data-stu-id="31799-480">This method defaults the target to the *GameObject* being “gazed” if no explicit target is defined in the Entities.</span></span>

    ```csharp
        /// <summary>
        /// Determines which object reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="31799-481">Elimine los métodos *Start ()* y *Update ()* , ya que esta clase no los usará.</span><span class="sxs-lookup"><span data-stu-id="31799-481">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

8.  <span data-ttu-id="31799-482">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="31799-482">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--create-the-gaze-class"></a><span data-ttu-id="31799-483">Capítulo 8: crear la clase fijamente</span><span class="sxs-lookup"><span data-stu-id="31799-483">Chapter 8 – Create the Gaze Class</span></span>

<span data-ttu-id="31799-484">La última clase que necesitará para completar esta aplicación es la clase *fijamente* .</span><span class="sxs-lookup"><span data-stu-id="31799-484">The last class that you will need to complete this app is the *Gaze* class.</span></span> <span data-ttu-id="31799-485">Esta clase actualiza la referencia a *GameObject* actualmente en el foco visual del usuario.</span><span class="sxs-lookup"><span data-stu-id="31799-485">This class updates the reference to the *GameObject* currently in the user’s visual focus.</span></span>

<span data-ttu-id="31799-486">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="31799-486">To create this Class:</span></span> 

1.  <span data-ttu-id="31799-487">Haga doble clic en la carpeta **scripts** para abrirla.</span><span class="sxs-lookup"><span data-stu-id="31799-487">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="31799-488">Haga clic con el botón derecho en la carpeta **scripts** y haga clic en **crear > C# script**.</span><span class="sxs-lookup"><span data-stu-id="31799-488">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="31799-489">Asigne un nombre *al script.*</span><span class="sxs-lookup"><span data-stu-id="31799-489">Name the script *Gaze*.</span></span> 
3.  <span data-ttu-id="31799-490">Haga doble clic en el script para abrirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="31799-490">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="31799-491">Inserte el código siguiente para esta clase:</span><span class="sxs-lookup"><span data-stu-id="31799-491">Insert the following code for this class:</span></span>

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  <span data-ttu-id="31799-492">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="31799-492">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--completing-the-scene-setup"></a><span data-ttu-id="31799-493">Capítulo 9: completar la configuración de la escena</span><span class="sxs-lookup"><span data-stu-id="31799-493">Chapter 9 – Completing the scene setup</span></span>

1.  <span data-ttu-id="31799-494">Para completar la instalación de la escena, arrastre cada script que ha creado desde la carpeta scripts hasta el objeto **cámara principal** del *Panel jerarquía*.</span><span class="sxs-lookup"><span data-stu-id="31799-494">To complete the setup of the scene, drag each script that you have created from the Scripts Folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="31799-495">Seleccione la **cámara principal** y mire en el *panel del inspector*, podrá ver cada script que ha adjuntado y observará que hay parámetros en cada script que todavía se deben establecer.</span><span class="sxs-lookup"><span data-stu-id="31799-495">Select the **Main Camera** and look at the *Inspector Panel*, you should be able to see each script that you have attached, and you will notice that there are parameters on each script that are yet to be set.</span></span>

    ![Establecer los destinos de referencia de la cámara.](images/AzureLabs-Lab3-41.png)

3.  <span data-ttu-id="31799-497">Para establecer estos parámetros correctamente, siga estas instrucciones:</span><span class="sxs-lookup"><span data-stu-id="31799-497">To set these parameters correctly, follow these instructions:</span></span>

    1. <span data-ttu-id="31799-498">*MicrophoneManager*:</span><span class="sxs-lookup"><span data-stu-id="31799-498">*MicrophoneManager*:</span></span>

        - <span data-ttu-id="31799-499">En el *Panel jerarquía*, arrastre el objeto de **texto dictado** al cuadro valor del parámetro de **texto de dictado** .</span><span class="sxs-lookup"><span data-stu-id="31799-499">From the *Hierarchy Panel*, drag the **Dictation Text** object into the **Dictation Text** parameter value box.</span></span>

    2. <span data-ttu-id="31799-500">*Comportamientos*, en el *Panel jerarquía*:</span><span class="sxs-lookup"><span data-stu-id="31799-500">*Behaviours*, from the *Hierarchy Panel*:</span></span>

        - <span data-ttu-id="31799-501">Arrastre el objeto **Sphere** al cuadro destino de referencia *Sphere* .</span><span class="sxs-lookup"><span data-stu-id="31799-501">Drag the **Sphere** object into the *Sphere* reference target box.</span></span>
        - <span data-ttu-id="31799-502">Arrastre el **cilindro** al cuadro destino de referencia del *cilindro* .</span><span class="sxs-lookup"><span data-stu-id="31799-502">Drag the **Cylinder** into the *Cylinder* reference target box.</span></span>
        - <span data-ttu-id="31799-503">Arrastre el **cubo** al cuadro destino de referencia del *cubo* .</span><span class="sxs-lookup"><span data-stu-id="31799-503">Drag the **Cube** into the *Cube* reference target box.</span></span>

    3. <span data-ttu-id="31799-504">*Mira fijamente*:</span><span class="sxs-lookup"><span data-stu-id="31799-504">*Gaze*:</span></span>

        - <span data-ttu-id="31799-505">Establezca la *distancia máxima de miración* en **300** (si aún no lo está).</span><span class="sxs-lookup"><span data-stu-id="31799-505">Set the *Gaze Max Distance* to **300** (if it is not already).</span></span> 

4.  <span data-ttu-id="31799-506">El resultado debería ser similar a la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="31799-506">The result should look like the image below:</span></span>

    ![Que muestra los destinos de referencia de la cámara, ahora establecido.](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a><span data-ttu-id="31799-508">Capítulo 10: prueba en el editor de Unity</span><span class="sxs-lookup"><span data-stu-id="31799-508">Chapter 10 – Test in the Unity Editor</span></span>

<span data-ttu-id="31799-509">Compruebe que la configuración de la escena está implementada correctamente.</span><span class="sxs-lookup"><span data-stu-id="31799-509">Test that the Scene setup is properly implemented.</span></span>

<span data-ttu-id="31799-510">Asegúrate de lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="31799-510">Ensure that:</span></span>

-   <span data-ttu-id="31799-511">Todos los scripts se adjuntan al objeto de **cámara principal** .</span><span class="sxs-lookup"><span data-stu-id="31799-511">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="31799-512">Todos los campos del *panel Inspector de cámara principal* están asignados correctamente.</span><span class="sxs-lookup"><span data-stu-id="31799-512">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>

1.  <span data-ttu-id="31799-513">Presione el botón **reproducir** en el *Editor de Unity*.</span><span class="sxs-lookup"><span data-stu-id="31799-513">Press the **Play** button in the *Unity Editor*.</span></span> <span data-ttu-id="31799-514">La aplicación debe ejecutarse dentro de los auriculares inmersivo agregados.</span><span class="sxs-lookup"><span data-stu-id="31799-514">The App should be running within the attached immersive headset.</span></span>

2.  <span data-ttu-id="31799-515">Pruebe unos cuantos grabaciones, como:</span><span class="sxs-lookup"><span data-stu-id="31799-515">Try a few utterances, such as:</span></span>

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > <span data-ttu-id="31799-516">Si ve un error en la consola de Unity sobre el cambio del dispositivo de audio predeterminado, es posible que la escena no funcione según lo previsto.</span><span class="sxs-lookup"><span data-stu-id="31799-516">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="31799-517">Esto se debe a la forma en que el portal de realidad mixta trata los micrófonos integrados para los auriculares que los tienen.</span><span class="sxs-lookup"><span data-stu-id="31799-517">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="31799-518">Si ve este error, simplemente detenga la escena e iníciela de nuevo y las cosas deberían funcionar según lo previsto.</span><span class="sxs-lookup"><span data-stu-id="31799-518">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a><span data-ttu-id="31799-519">Capítulo 11: compilar y transferir localmente la solución de UWP</span><span class="sxs-lookup"><span data-stu-id="31799-519">Chapter 11 – Build and sideload the UWP Solution</span></span>

<span data-ttu-id="31799-520">Una vez que se ha asegurado de que la aplicación funciona en el editor de Unity, está listo para compilar e implementar.</span><span class="sxs-lookup"><span data-stu-id="31799-520">Once you have ensured that the application is working in the Unity Editor, you are ready to Build and Deploy.</span></span>

<span data-ttu-id="31799-521">Para compilar:</span><span class="sxs-lookup"><span data-stu-id="31799-521">To Build:</span></span>

1.  <span data-ttu-id="31799-522">Guarde la escena actual haciendo clic en **archivo > guardar**.</span><span class="sxs-lookup"><span data-stu-id="31799-522">Save the current scene by clicking on **File > Save**.</span></span>
2.  <span data-ttu-id="31799-523">Vaya a **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="31799-523">Go to **File > Build Settings**.</span></span>
3.  <span data-ttu-id="31799-524">Marque el cuadro denominado **proyectos C# de Unity** (útil para ver y depurar el código una vez creado el proyecto de UWP.</span><span class="sxs-lookup"><span data-stu-id="31799-524">Tick the box called **Unity C# Projects** (useful for seeing and debugging your code once the UWP project is created.</span></span>
4.  <span data-ttu-id="31799-525">Haga clic en **Agregar escenas abiertas**y luego haga clic en **compilar**.</span><span class="sxs-lookup"><span data-stu-id="31799-525">Click on **Add Open Scenes**, then click **Build**.</span></span>

    ![Ventana Configuración de compilación](images/AzureLabs-Lab3-43.png)

4.  <span data-ttu-id="31799-527">Se le pedirá que seleccione la carpeta en la que desea compilar la solución.</span><span class="sxs-lookup"><span data-stu-id="31799-527">You will be prompted to select the folder where you want to build the Solution.</span></span> 

5.  <span data-ttu-id="31799-528">Cree una carpeta *compilaciones* y, dentro de esa carpeta, cree otra carpeta con un nombre adecuado de su elección.</span><span class="sxs-lookup"><span data-stu-id="31799-528">Create a *BUILDS* folder and within that folder create another folder with an appropriate name of your choice.</span></span> 
6.  <span data-ttu-id="31799-529">Haga clic en **Seleccionar carpeta** para iniciar la compilación en esa ubicación.</span><span class="sxs-lookup"><span data-stu-id="31799-529">Click **Select Folder** to begin the build at that location.</span></span>
 
    <span data-ttu-id="31799-530">![carpeta crear compilaciones](images/AzureLabs-Lab3-44.png)
    ![seleccione la carpeta compilaciones](images/AzureLabs-Lab3-45.png)</span><span class="sxs-lookup"><span data-stu-id="31799-530">![Create Builds Folder](images/AzureLabs-Lab3-44.png)
![Select Builds Folder](images/AzureLabs-Lab3-45.png)</span></span>
 
7.  <span data-ttu-id="31799-531">Una vez que Unity termine de compilar (puede tardar algún tiempo), debe abrir una ventana del **Explorador de archivos** en la ubicación de la compilación.</span><span class="sxs-lookup"><span data-stu-id="31799-531">Once Unity has finished building (it might take some time), it should open a **File Explorer** window at the location of your build.</span></span>

<span data-ttu-id="31799-532">Para implementar en la máquina local:</span><span class="sxs-lookup"><span data-stu-id="31799-532">To Deploy on Local Machine:</span></span>

1.  <span data-ttu-id="31799-533">En *Visual Studio*, abra el archivo de solución que se creó en el [capítulo anterior](#chapter-10--test-in-the-unity-editor).</span><span class="sxs-lookup"><span data-stu-id="31799-533">In *Visual Studio*, open the solution file that has been created in the [previous Chapter](#chapter-10--test-in-the-unity-editor).</span></span>
2.  <span data-ttu-id="31799-534">En la **plataforma**de la solución, seleccione **x86**, **equipo local**.</span><span class="sxs-lookup"><span data-stu-id="31799-534">In the **Solution Platform**, select **x86**, **Local Machine**.</span></span>
3.  <span data-ttu-id="31799-535">En la **configuración de soluciones** , seleccione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="31799-535">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="31799-536">En el caso de Microsoft HoloLens, es posible que le resulte más fácil establecer esto en el *equipo remoto*, de modo que no esté anclado al equipo.</span><span class="sxs-lookup"><span data-stu-id="31799-536">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="31799-537">Sin embargo, también tendrá que hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="31799-537">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="31799-538">Conozca la **dirección IP** de HoloLens, que puede encontrarse en la *configuración > red & Internet > Wi-Fi > Opciones avanzadas*; IPv4 es la dirección que debe usar.</span><span class="sxs-lookup"><span data-stu-id="31799-538">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="31799-539">Asegurarse de que el **modo de desarrollador** está **activado**; se encuentra en *configuración > actualizar & > de seguridad para desarrolladores*.</span><span class="sxs-lookup"><span data-stu-id="31799-539">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Implementar aplicación](images/AzureLabs-Lab3-46.png)
 
4.  <span data-ttu-id="31799-541">Vaya al **menú compilar** y haga clic en **implementar solución** para transferir localmente la aplicación a la máquina.</span><span class="sxs-lookup"><span data-stu-id="31799-541">Go to the **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>
5.  <span data-ttu-id="31799-542">La aplicación debe aparecer ahora en la lista de aplicaciones instaladas, lista para su lanzamiento.</span><span class="sxs-lookup"><span data-stu-id="31799-542">Your App should now appear in the list of installed apps, ready to be launched!</span></span>
6.  <span data-ttu-id="31799-543">Una vez iniciado, la aplicación le pedirá que autorice el acceso al _micrófono_.</span><span class="sxs-lookup"><span data-stu-id="31799-543">Once launched, the App will prompt you to authorize access to the _Microphone_.</span></span> <span data-ttu-id="31799-544">Use los *controladores de movimiento*, la *entrada de voz*o el *teclado* para presionar el botón **sí** .</span><span class="sxs-lookup"><span data-stu-id="31799-544">Use the *Motion Controllers*, or *Voice Input*, or the *Keyboard* to press the **YES** button.</span></span> 

## <a name="chapter-12--improving-your-luis-service"></a><span data-ttu-id="31799-545">Capítulo 12: mejorar el servicio de LUIS</span><span class="sxs-lookup"><span data-stu-id="31799-545">Chapter 12 – Improving your LUIS service</span></span>

>[!IMPORTANT] 
> <span data-ttu-id="31799-546">Este capítulo es increíblemente importante, por lo que es posible que tenga que repetirse varias veces, ya que le ayudará a mejorar la precisión del servicio LUIS: Asegúrese de que lo completa.</span><span class="sxs-lookup"><span data-stu-id="31799-546">This chapter is incredibly important, and may need to be iterated upon several times, as it will help improve the accuracy of your LUIS service: ensure you complete this.</span></span>

<span data-ttu-id="31799-547">Para mejorar el nivel de comprensión proporcionado por LUIS, debe capturar nuevos grabaciones y usarlos para volver a entrenar su aplicación de LUIS.</span><span class="sxs-lookup"><span data-stu-id="31799-547">To improve the level of understanding provided by LUIS you need to capture new utterances and use them to re-train your LUIS App.</span></span>

<span data-ttu-id="31799-548">Por ejemplo, es posible que haya entrenado a LUIS para comprender "aumento" y "tamaño", pero no desea que la aplicación también entienda palabras como "agrandar"?</span><span class="sxs-lookup"><span data-stu-id="31799-548">For example, you might have trained LUIS to understand “Increase” and “Upsize”, but wouldn’t you want your app to also understand words like “Enlarge”?</span></span>

<span data-ttu-id="31799-549">Una vez que haya usado la aplicación varias veces, se recopilará todo lo que haya dicho en LUIS y estará disponible en el PORTAL de LUIS.</span><span class="sxs-lookup"><span data-stu-id="31799-549">Once you have used your application a few times, everything you have said will be collected by LUIS and available in the LUIS PORTAL.</span></span>

1.  <span data-ttu-id="31799-550">Vaya a la aplicación de portal que sigue a este [vínculo](https://www.luis.ai/home)e inicie sesión.</span><span class="sxs-lookup"><span data-stu-id="31799-550">Go to your portal application following this [LINK](https://www.luis.ai/home), and Log In.</span></span>
2.  <span data-ttu-id="31799-551">Una vez que haya iniciado sesión con sus credenciales de MS, haga clic en el nombre de la *aplicación*.</span><span class="sxs-lookup"><span data-stu-id="31799-551">Once you are logged in with your MS Credentials, click on your *App name*.</span></span>
3.  <span data-ttu-id="31799-552">Haga clic en el botón **revisar extremo grabaciones** situado a la izquierda de la página.</span><span class="sxs-lookup"><span data-stu-id="31799-552">Click the **Review endpoint utterances** button on the left of the page.</span></span>

    ![Revisar grabaciones](images/AzureLabs-Lab3-47.png)
 
4.  <span data-ttu-id="31799-554">Se le mostrará una lista de los grabaciones enviados a LUIS por la aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="31799-554">You will be shown a list of the Utterances that have been sent to LUIS by your mixed reality Application.</span></span>

    ![Lista de grabaciones](images/AzureLabs-Lab3-48.png)
 
<span data-ttu-id="31799-556">Observará algunas *entidades*resaltadas.</span><span class="sxs-lookup"><span data-stu-id="31799-556">You will notice some highlighted *Entities*.</span></span> 

<span data-ttu-id="31799-557">Al mantener el mouse sobre cada palabra resaltada, puede revisar cada utterance y determinar qué entidad se reconoció correctamente, qué entidades son erróneas y qué entidades se han perdido.</span><span class="sxs-lookup"><span data-stu-id="31799-557">By hovering over each highlighted word, you can review each Utterance and determine which Entity has been recognized correctly, which Entities are wrong and which Entities are missed.</span></span>

<span data-ttu-id="31799-558">En el ejemplo anterior, se encontró que la palabra "Spear" se resaltó como destino, por lo que era necesario corregir el error, lo que se realiza al mantener el mouse sobre la palabra con el mouse y hacer clic en **quitar etiqueta**.</span><span class="sxs-lookup"><span data-stu-id="31799-558">In the example above, it was found that the word “spear” had been highlighted as a target, so it necessary to correct the mistake, which is done by hovering over the word with the mouse and clicking **Remove Label**.</span></span>

<span data-ttu-id="31799-559">![comprobar grabaciones](images/AzureLabs-Lab3-49.png)
![quitar etiqueta de imagen](images/AzureLabs-Lab3-50.png)</span><span class="sxs-lookup"><span data-stu-id="31799-559">![Check utterances](images/AzureLabs-Lab3-49.png)
![Remove Label Image](images/AzureLabs-Lab3-50.png)</span></span>
 
5.  <span data-ttu-id="31799-560">Si encuentra grabaciones que son completamente incorrectas, puede eliminarlos mediante el botón **eliminar** situado en el lado derecho de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="31799-560">If you find Utterances that are completely wrong, you can delete them using the **Delete** button on the right side of the screen.</span></span>

    ![Eliminar grabaciones erróneo](images/AzureLabs-Lab3-51.png)

6.  <span data-ttu-id="31799-562">O bien, si cree que LUIS ha interpretado el utterance correctamente, puede validar su comprensión mediante el botón **Agregar a intento alineado** .</span><span class="sxs-lookup"><span data-stu-id="31799-562">Or if you feel that LUIS has interpreted the Utterance correctly, you can validate its understanding by using the **Add To Aligned Intent** button.</span></span>

    ![Agregar a intención alineada](images/AzureLabs-Lab3-52.png)

7.  <span data-ttu-id="31799-564">Una vez que haya ordenado todo el grabaciones que se muestra, intente volver a cargar la página para ver si hay más disponibles.</span><span class="sxs-lookup"><span data-stu-id="31799-564">Once you have sorted all the displayed Utterances, try and reload the page to see if more are available.</span></span>
8.  <span data-ttu-id="31799-565">Es muy importante repetir este proceso tantas veces como sea posible para mejorar la comprensión de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="31799-565">It is very important to repeat this process as many times as possible to improve your application understanding.</span></span> 

<span data-ttu-id="31799-566">**¡Que te diviertas!**</span><span class="sxs-lookup"><span data-stu-id="31799-566">**Have fun!**</span></span>

## <a name="your-finished-luis-integrated-application"></a><span data-ttu-id="31799-567">Su aplicación integrada de LUIS finalizada</span><span class="sxs-lookup"><span data-stu-id="31799-567">Your finished LUIS Integrated application</span></span>

<span data-ttu-id="31799-568">Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha el servicio de inteligencia de Language Understanding de Azure para comprender lo que un usuario dice y actuar sobre esa información.</span><span class="sxs-lookup"><span data-stu-id="31799-568">Congratulations, you built a mixed reality app that leverages the Azure Language Understanding Intelligence Service, to understand what a user says, and act on that information.</span></span>

![resultado de laboratorio](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="31799-570">Ejercicios de bonus</span><span class="sxs-lookup"><span data-stu-id="31799-570">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="31799-571">Ejercicio 1</span><span class="sxs-lookup"><span data-stu-id="31799-571">Exercise 1</span></span>

<span data-ttu-id="31799-572">Al usar esta aplicación, es posible que observe que si mira el objeto Floor y pide cambiar su color, lo hará.</span><span class="sxs-lookup"><span data-stu-id="31799-572">While using this application you might notice that if you gaze at the Floor object and ask to change its color, it will do so.</span></span> <span data-ttu-id="31799-573">¿Puede averiguar cómo evitar que la aplicación cambie el color del piso?</span><span class="sxs-lookup"><span data-stu-id="31799-573">Can you work out how to stop your application from changing the Floor color?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="31799-574">Ejercicio 2</span><span class="sxs-lookup"><span data-stu-id="31799-574">Exercise 2</span></span>

<span data-ttu-id="31799-575">Intente ampliar las funcionalidades de LUIS y App, agregando funcionalidad adicional a los objetos de la escena. por ejemplo, cree nuevos objetos en el punto de Miración de la mirada, en función de lo que indique el usuario y, a continuación, podrá usar esos objetos junto con los objetos de la escena actual con los comandos existentes.</span><span class="sxs-lookup"><span data-stu-id="31799-575">Try extending the LUIS and App capabilities, adding additional functionality for objects in scene; as an example, create new objects at the Gaze hit point, depending on what the user says, and then be able to use those objects alongside current scene objects, with the existing commands.</span></span> 
