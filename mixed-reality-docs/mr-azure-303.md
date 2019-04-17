---
title: El Sr. y Azure 303 - lenguaje Natural descripción (LUIS)
description: Realice este curso para obtener información sobre cómo implementar Azure Language Understanding Intelligence Service (LUIS) dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidad mixta, Azure, academy, unity, tutorial, api, servicio de lenguaje de descripción inteligencia, luis, vr envolventes, hololens,
ms.openlocfilehash: fb00fe9079e49a7ada507e7407ef45fa7eeb0d7e
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605321"
---
>[!NOTE]
><span data-ttu-id="c68fd-104">Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.</span><span class="sxs-lookup"><span data-stu-id="c68fd-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c68fd-105">Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="c68fd-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="c68fd-106">Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.</span><span class="sxs-lookup"><span data-stu-id="c68fd-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="c68fd-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="c68fd-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c68fd-108">Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c68fd-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="c68fd-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.</span><span class="sxs-lookup"><span data-stu-id="c68fd-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-303-natural-language-understanding-luis"></a><span data-ttu-id="c68fd-110">El Sr. y Azure 303: Comprensión del lenguaje natural (LUIS)</span><span class="sxs-lookup"><span data-stu-id="c68fd-110">MR and Azure 303: Natural language understanding (LUIS)</span></span>

<span data-ttu-id="c68fd-111">En este curso, obtendrá información sobre cómo integrar la comprensión del lenguaje en una aplicación de realidad mixta con Azure Cognitive Services, con la API de lenguaje de descripción.</span><span class="sxs-lookup"><span data-stu-id="c68fd-111">In this course, you will learn how to integrate Language Understanding into a mixed reality application using Azure Cognitive Services, with the Language Understanding API.</span></span>

![Resultado de laboratorio](images/AzureLabs-Lab3-000.png)

<span data-ttu-id="c68fd-113">*Language Understanding (LUIS)* es un servicio de Microsoft Azure, que proporciona a las aplicaciones la capacidad para realizar el significado fuera de la entrada del usuario, como a través de extracción de lo que una persona es posible que desee en sus propias palabras.</span><span class="sxs-lookup"><span data-stu-id="c68fd-113">*Language Understanding (LUIS)* is a Microsoft Azure service, which provides applications with the ability to make meaning out of user input, such as through extracting what a person might want, in their own words.</span></span> <span data-ttu-id="c68fd-114">Esto se logra a través de machine learning, que comprende y aprende la información de entrada y, a continuación, puede responder con información detallada relevante.</span><span class="sxs-lookup"><span data-stu-id="c68fd-114">This is achieved through machine learning, which understands and learns the input information, and then can reply with detailed, relevant, information.</span></span> <span data-ttu-id="c68fd-115">Para obtener más información, visite la [página Azure Language Understanding (LUIS)](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span><span class="sxs-lookup"><span data-stu-id="c68fd-115">For more information, visit the [Azure Language Understanding (LUIS) page](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span></span>

<span data-ttu-id="c68fd-116">Una vez completado este curso, tendrá una aplicación de envolventes auriculares de realidad mixta que podrá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="c68fd-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="c68fd-117">Captura de voz de entrada de usuario, con el micrófono conectado a los auriculares envolventes.</span><span class="sxs-lookup"><span data-stu-id="c68fd-117">Capture user input speech, using the Microphone attached to the immersive headset.</span></span> 
2.  <span data-ttu-id="c68fd-118">Enviar el dictado capturado la *Azure Language Understanding Intelligent Service* (*LUIS*).</span><span class="sxs-lookup"><span data-stu-id="c68fd-118">Send the captured dictation the *Azure Language Understanding Intelligent Service* (*LUIS*).</span></span> 
3.  <span data-ttu-id="c68fd-119">Tienen extracción LUIS lo que significa que en la información de envío que se va a analizar e intenta determinar que la intención de la solicitud del usuario se realizará.</span><span class="sxs-lookup"><span data-stu-id="c68fd-119">Have LUIS extract meaning from the send information, which will be analyzed, and attempt to determine the intent of the user’s request will be made.</span></span>

<span data-ttu-id="c68fd-120">Desarrollo incluirá la creación de una aplicación donde el usuario podrá usar voz o que mirar para cambiar el tamaño y el color de los objetos de la escena.</span><span class="sxs-lookup"><span data-stu-id="c68fd-120">Development will include the creation of an app where the user will be able to use voice and/or gaze to change the size and the color of the objects in the scene.</span></span> <span data-ttu-id="c68fd-121">No se tratará el uso de los controladores de movimiento.</span><span class="sxs-lookup"><span data-stu-id="c68fd-121">The use of motion controllers will not be covered.</span></span>

<span data-ttu-id="c68fd-122">En la aplicación, es depende de usted sobre cómo se integrará los resultados con el diseño.</span><span class="sxs-lookup"><span data-stu-id="c68fd-122">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="c68fd-123">Este curso está diseñado para mostrarle cómo integrar un servicio de Azure con el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="c68fd-123">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="c68fd-124">Es su trabajo consiste en usar los conocimientos que obtendrá de este curso para mejorar las aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="c68fd-124">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="c68fd-125">Prepárese para entrenar LUIS varias veces, lo que se trata en [capítulo 12](#chapter-12--improving-your-luis-service).</span><span class="sxs-lookup"><span data-stu-id="c68fd-125">Be prepared to Train LUIS several times, which is covered in [Chapter 12](#chapter-12--improving-your-luis-service).</span></span> <span data-ttu-id="c68fd-126">Obtendrá mejores resultados más veces que se ha entrenado LUIS.</span><span class="sxs-lookup"><span data-stu-id="c68fd-126">You will get better results the more times LUIS has been trained.</span></span>

## <a name="device-support"></a><span data-ttu-id="c68fd-127">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="c68fd-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c68fd-128">Curso</span><span class="sxs-lookup"><span data-stu-id="c68fd-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c68fd-129"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c68fd-129"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c68fd-130"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="c68fd-130"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="c68fd-131">El Sr. y Azure 303: Comprensión del lenguaje natural (LUIS)</span><span class="sxs-lookup"><span data-stu-id="c68fd-131">MR and Azure 303: Natural language understanding (LUIS)</span></span></td><td style="text-align: center;"> <span data-ttu-id="c68fd-132">✔️</span><span class="sxs-lookup"><span data-stu-id="c68fd-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="c68fd-133">✔️</span><span class="sxs-lookup"><span data-stu-id="c68fd-133">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="c68fd-134">Aunque este curso se centra principalmente en inmersivos (VR) Windows Mixed Reality, también puede aplicar lo aprendido en este curso de Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c68fd-134">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="c68fd-135">Como seguir el curso, verá notas en cualquier cambio que deberá emplear para admitir HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c68fd-135">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="c68fd-136">Al usar HoloLens, es posible que observe algunos eco durante la captura de voz.</span><span class="sxs-lookup"><span data-stu-id="c68fd-136">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c68fd-137">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="c68fd-137">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="c68fd-138">Este tutorial está diseñado para los desarrolladores con experiencia básica con Unity y C#.</span><span class="sxs-lookup"><span data-stu-id="c68fd-138">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="c68fd-139">También Ten en cuenta que los requisitos previos y las instrucciones escritas en este documento representan lo que se ha probado y comprobado en el momento de redactar (mayo de 2018).</span><span class="sxs-lookup"><span data-stu-id="c68fd-139">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="c68fd-140">Es libre de usar el software más reciente, como se muestra en el [instalar las herramientas de](install-the-tools.md) artículo, aunque no se debe suponer que la información de este curso perfectamente coincida con lo que encontrará en el software más reciente que se indica a continuación .</span><span class="sxs-lookup"><span data-stu-id="c68fd-140">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="c68fd-141">Se recomiendan el siguiente hardware y software para este curso:</span><span class="sxs-lookup"><span data-stu-id="c68fd-141">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="c68fd-142">Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desarrollo de auriculares envolvente (VR)</span><span class="sxs-lookup"><span data-stu-id="c68fd-142">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="c68fd-143">Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="c68fd-143">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="c68fd-144">El SDK más reciente de Windows 10</span><span class="sxs-lookup"><span data-stu-id="c68fd-144">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="c68fd-145">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="c68fd-145">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="c68fd-146">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c68fd-146">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="c68fd-147">Un [auriculares de Windows Mixed Reality envolventes (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="c68fd-147">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="c68fd-148">Un conjunto de auriculares con micrófono integrado (si no tienen los auriculares altavoces y un micrófono integrado)</span><span class="sxs-lookup"><span data-stu-id="c68fd-148">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="c68fd-149">Acceso a Internet para el programa de instalación de Azure y la recuperación de LUIS</span><span class="sxs-lookup"><span data-stu-id="c68fd-149">Internet access for Azure setup and LUIS retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="c68fd-150">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="c68fd-150">Before you start</span></span>

1.  <span data-ttu-id="c68fd-151">Para evitar problemas de creación de este proyecto, se recomienda encarecidamente que cree el proyecto se ha mencionado en este tutorial en una carpeta raíz o cerca de la raíz (rutas de acceso de carpeta largo pueden causar problemas en tiempo de compilación).</span><span class="sxs-lookup"><span data-stu-id="c68fd-151">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 
2.  <span data-ttu-id="c68fd-152">Para permitir que la máquina para permitir dictado, vaya a **Windows Configuración > privacidad > voz de tinta & escribir** y pulse en el botón **activar servicios de voz y escritura sugerencias**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-152">To allow your machine to enable Dictation, go to **Windows Settings > Privacy > Speech, Inking & Typing** and press on the button **Turn On speech services and typing suggestions**.</span></span>
3.  <span data-ttu-id="c68fd-153">El código de este tutorial le permitirá grabar desde el **dispositivo de micrófono predeterminado** establecida en el equipo.</span><span class="sxs-lookup"><span data-stu-id="c68fd-153">The code in this tutorial will allow you to record from the **Default Microphone Device** set on your machine.</span></span> <span data-ttu-id="c68fd-154">Asegúrese de que el dispositivo de micrófono predeterminado se establece como el que desea usar para capturar la voz.</span><span class="sxs-lookup"><span data-stu-id="c68fd-154">Make sure the Default Microphone Device is set as the one you wish to use to capture your voice.</span></span>
4.  <span data-ttu-id="c68fd-155">Si los auriculares tienen un micrófono integrado, asegúrese de que la opción *"Cuando wear mi auriculares, vaya a auriculares con micrófono"* está activado en el *Portal de realidad mixta* configuración.</span><span class="sxs-lookup"><span data-stu-id="c68fd-155">If your headset has a built-in microphone, make sure the option *“When I wear my headset, switch to headset mic”* is turned on in the *Mixed Reality Portal* settings.</span></span>

    ![Configuración de auriculares envolventes](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a><span data-ttu-id="c68fd-157">Capítulo 1: configurar el Portal de Azure</span><span class="sxs-lookup"><span data-stu-id="c68fd-157">Chapter 1 – Setup Azure Portal</span></span>

<span data-ttu-id="c68fd-158">Para usar el *Language Understanding* service en Azure, deberá configurar una instancia del servicio esté disponible para su aplicación.</span><span class="sxs-lookup"><span data-stu-id="c68fd-158">To use the *Language Understanding* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="c68fd-159">Inicie sesión en el [Portal Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="c68fd-159">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="c68fd-160">Si no dispone de una cuenta de Azure, deberá crear uno.</span><span class="sxs-lookup"><span data-stu-id="c68fd-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="c68fd-161">Si está siguiendo este tutorial en una situación de aula o laboratorio, pida el instructor o uno de los a los supervisores de ayuda para instalar la nueva cuenta.</span><span class="sxs-lookup"><span data-stu-id="c68fd-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="c68fd-162">Una vez que haya iniciado sesión, haga clic en **New** en la esquina superior izquierda esquina y busque *Language Understanding*y haga clic en **ENTRAR**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-162">Once you are logged in, click on **New** in the top left corner, and search for *Language Understanding*, and click **Enter**.</span></span> 

    ![Crear recurso de LUIS](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > <span data-ttu-id="c68fd-164">La palabra **New** se han reemplazado con **crear un recurso**, en los portales más reciente.</span><span class="sxs-lookup"><span data-stu-id="c68fd-164">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="c68fd-165">La nueva página a la derecha proporcionará una descripción del servicio en la comprensión del lenguaje.</span><span class="sxs-lookup"><span data-stu-id="c68fd-165">The new page to the right will provide a description of the Language Understanding service.</span></span> <span data-ttu-id="c68fd-166">En la parte inferior izquierda de esta página, seleccione el **crear** botón para crear una instancia de este servicio.</span><span class="sxs-lookup"><span data-stu-id="c68fd-166">At the bottom left of this page, select the **Create** button, to create an instance of this service.</span></span>

    ![Creación del servicio LUIS - aviso legal](images/AzureLabs-Lab3-02.png)
 
4.  <span data-ttu-id="c68fd-168">Una vez que ha hecho clic en crear:</span><span class="sxs-lookup"><span data-stu-id="c68fd-168">Once you have clicked on Create:</span></span>

    1. <span data-ttu-id="c68fd-169">Insertar el elemento **nombre** para esta instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="c68fd-169">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="c68fd-170">Seleccione un **suscripción**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-170">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="c68fd-171">Seleccione el **tarifa** adecuado para usted, si ésta es la primera tiempo creando una *LUIS Service*, un nivel gratuito (denominado F0) debe estar disponible para usted.</span><span class="sxs-lookup"><span data-stu-id="c68fd-171">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *LUIS Service*, a free tier (named F0) should be available to you.</span></span> <span data-ttu-id="c68fd-172">La asignación gratuita debe ser más que suficiente para este curso.</span><span class="sxs-lookup"><span data-stu-id="c68fd-172">The free allocation should be more than sufficient for this course.</span></span>
    4. <span data-ttu-id="c68fd-173">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="c68fd-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="c68fd-174">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="c68fd-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="c68fd-175">Se recomienda mantener todos los servicios de Azure asociados a un proyecto único (por ejemplo, por ejemplo, estos cursos) en un grupo de recursos comunes).</span><span class="sxs-lookup"><span data-stu-id="c68fd-175">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span> 

        > <span data-ttu-id="c68fd-176">Si desea leer más acerca de los grupos de recursos de Azure, inicie [visite el artículo del grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="c68fd-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="c68fd-177">Determinar la **ubicación** para el grupo de recursos (si está creando un nuevo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="c68fd-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="c68fd-178">La ubicación sería lo ideal es que en la región donde desea ejecutar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c68fd-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="c68fd-179">Algunos recursos de Azure solo están disponibles en determinadas regiones.</span><span class="sxs-lookup"><span data-stu-id="c68fd-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="c68fd-180">También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.</span><span class="sxs-lookup"><span data-stu-id="c68fd-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="c68fd-181">Selecciona **Crear**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-181">Select **Create**.</span></span>

        ![Crear servicio LUIS - proporcionados por el usuario](images/AzureLabs-Lab3-03.png)
 
5.  <span data-ttu-id="c68fd-183">Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="c68fd-183">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="c68fd-184">Una vez creada la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="c68fd-184">A notification will appear in the portal once the Service instance is created.</span></span> 
 
    ![Nueva imagen de la notificación de Azure](images/AzureLabs-Lab3-04.png)

7.  <span data-ttu-id="c68fd-186">Haga clic en la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="c68fd-186">Click on the notification to explore your new Service instance.</span></span>

    ![Notificación de creación de recurso correcta](images/AzureLabs-Lab3-05.png)
 
8.  <span data-ttu-id="c68fd-188">Haga clic en el **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="c68fd-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="c68fd-189">Se le llevará a la nueva instancia del servicio LUIS.</span><span class="sxs-lookup"><span data-stu-id="c68fd-189">You will be taken to your new LUIS service instance.</span></span> 
 
    ![Acceso a las claves de LUIS](images/AzureLabs-Lab3-06.png)

9.  <span data-ttu-id="c68fd-191">En este tutorial, la aplicación necesitará realizar llamadas al servicio, que se realiza a través del uso clave del servicio en la de suscripción.</span><span class="sxs-lookup"><span data-stu-id="c68fd-191">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="c68fd-192">Desde el *inicio rápido* página, de su *LUIS API* de servicio, navegue hasta el primer paso, *obtener las claves*y haga clic en **claves** (también puede lograr esto, haga clic en el hipervínculo azul claves, ubicado en el menú de navegación de servicios, indicado por el icono de llave).</span><span class="sxs-lookup"><span data-stu-id="c68fd-192">From the *Quick start* page, of your *LUIS API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="c68fd-193">Esto revelará su servicio *claves*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-193">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="c68fd-194">Realice una copia de una de las claves de muestra, ya que lo necesitará más adelante en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="c68fd-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 
12. <span data-ttu-id="c68fd-195">En el *servicio* página, haga clic en *Portal de Language Understanding* se redirijan a la página Web que usará para crear su nuevo servicio en la App LUIS.</span><span class="sxs-lookup"><span data-stu-id="c68fd-195">In the *Service* page, click on *Language Understanding Portal* to be redirected to the webpage which you will use to create your new Service, within the LUIS App.</span></span> 

## <a name="chapter-2--the-language-understanding-portal"></a><span data-ttu-id="c68fd-196">Capítulo 2: Portal de Language Understanding</span><span class="sxs-lookup"><span data-stu-id="c68fd-196">Chapter 2 – The Language Understanding Portal</span></span>

<span data-ttu-id="c68fd-197">En esta sección obtendrá información sobre cómo hacer una App LUIS en el Portal de LUIS.</span><span class="sxs-lookup"><span data-stu-id="c68fd-197">In this section you will learn how to make a LUIS App on the LUIS Portal.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="c68fd-198">Tenga en cuenta que la configuración de la *entidades*, *intenciones*, y *grabaciones de voz* dentro de este capítulo es sólo el primer paso para crear el servicio LUIS: también deberá reciclar el servicio, varias veces, por lo que para que sea más precisa.</span><span class="sxs-lookup"><span data-stu-id="c68fd-198">Please be aware, that setting up the *Entities*, *Intents*, and *Utterances* within this chapter is only the first step in building your LUIS service: you will also need to retrain the service, several times, so to make it more accurate.</span></span> <span data-ttu-id="c68fd-199">Reciclaje del servicio se trata en el [último capítulo](#chapter-12--improving-your-luis-service) de este curso, así que asegúrese de que lo complete.</span><span class="sxs-lookup"><span data-stu-id="c68fd-199">Retraining your service is covered in the [last Chapter](#chapter-12--improving-your-luis-service) of this course, so ensure that you complete it.</span></span>

1.  <span data-ttu-id="c68fd-200">Cuando se alcanza el *Portal de Language Understanding*, es posible que deba iniciar sesión, si no está ya, con las mismas credenciales que el portal de Azure.</span><span class="sxs-lookup"><span data-stu-id="c68fd-200">Upon reaching the *Language Understanding Portal*, you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> 

    ![Página de inicio de sesión de LUIS](images/AzureLabs-Lab3-07.png)
 
2.  <span data-ttu-id="c68fd-202">Si se trata de la primera vez que usa LUIS, deberá desplazarse hacia abajo hasta la parte inferior de la página de bienvenida, para buscar y haga clic en el **aplicación LUIS crear** botón.</span><span class="sxs-lookup"><span data-stu-id="c68fd-202">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the **Create LUIS app** button.</span></span>

    ![Crear página de aplicación de LUIS](images/AzureLabs-Lab3-08.png)
 
3.  <span data-ttu-id="c68fd-204">Una vez iniciada la sesión, haga clic en **mis aplicaciones** (si no estás en esa sección actualmente).</span><span class="sxs-lookup"><span data-stu-id="c68fd-204">Once logged in, click **My apps** (if you are not in that section currently).</span></span> <span data-ttu-id="c68fd-205">A continuación, puede hacer clic en **crear nueva aplicación**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-205">You can then click on **Create new app**.</span></span>

    ![LUIS - mi imagen de aplicaciones](images/AzureLabs-Lab3-09.png)
 
4.  <span data-ttu-id="c68fd-207">Asigne a la aplicación un *nombre*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-207">Give your app a *Name*.</span></span>
5.  <span data-ttu-id="c68fd-208">Si se supone que la aplicación para entender un idioma distinto del inglés, debe cambiar la *referencia cultural* para el idioma adecuado.</span><span class="sxs-lookup"><span data-stu-id="c68fd-208">If your app is supposed to understand a language different from English, you should change the *Culture* to the appropriate language.</span></span>
6.  <span data-ttu-id="c68fd-209">Aquí también puede agregar un *descripción* de la nueva aplicación de LUIS.</span><span class="sxs-lookup"><span data-stu-id="c68fd-209">Here you can also add a *Description* of your new LUIS app.</span></span>

    ![LUIS - crear una nueva aplicación](images/AzureLabs-Lab3-10.png)

7.  <span data-ttu-id="c68fd-211">Una vez que presione **realiza**, que va a escribir el *compilar* página de la nueva *LUIS* aplicación.</span><span class="sxs-lookup"><span data-stu-id="c68fd-211">Once you press **Done**, you will enter the *Build* page of your new *LUIS* application.</span></span>
8.  <span data-ttu-id="c68fd-212">Hay algunos conceptos importantes para comprender aquí:</span><span class="sxs-lookup"><span data-stu-id="c68fd-212">There are a few important concepts to understand here:</span></span>

    -   <span data-ttu-id="c68fd-213">*Intención*, representa el método que se llama después de una consulta desde el usuario.</span><span class="sxs-lookup"><span data-stu-id="c68fd-213">*Intent*, represents the method that will be called following a query from the user.</span></span> <span data-ttu-id="c68fd-214">Un *intención* puede tener uno o varios *entidades*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-214">An *INTENT* may have one or more *ENTITIES*.</span></span>
    -   <span data-ttu-id="c68fd-215">*Entidad*, es un componente de la consulta que describe la información relevante para el *intención*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-215">*Entity*, is a component of the query that describes information relevant to the *INTENT*.</span></span>
    -   <span data-ttu-id="c68fd-216">*Grabaciones de voz*, son ejemplos de consultas proporcionado por el desarrollador, se usará ese LUIS para entrenar a sí mismo.</span><span class="sxs-lookup"><span data-stu-id="c68fd-216">*Utterances*, are examples of queries provided by the developer, that LUIS will use to train itself.</span></span>

<span data-ttu-id="c68fd-217">Si estos conceptos no son perfectamente borrar, no se preocupe, como este curso aclarar ellos aún más en este capítulo.</span><span class="sxs-lookup"><span data-stu-id="c68fd-217">If these concepts are not perfectly clear, do not worry, as this course will clarify them further in this chapter.</span></span>

<span data-ttu-id="c68fd-218">Comenzará creando la *entidades* necesarios para compilar este curso.</span><span class="sxs-lookup"><span data-stu-id="c68fd-218">You will begin by creating the *Entities* needed to build this course.</span></span>

9.  <span data-ttu-id="c68fd-219">En el lado izquierdo de la página, haga clic en *entidades*, a continuación, haga clic en **crear nueva entidad**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-219">On the left side of the page, click on *Entities*, then click on **Create new entity**.</span></span>

    ![Crear nueva entidad](images/AzureLabs-Lab3-11.png)

10. <span data-ttu-id="c68fd-221">Llame a la nueva entidad *color*, establezca su tipo en *Simple*, a continuación, presione **realiza**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-221">Call the new Entity *color*, set its type to *Simple*, then press **Done**.</span></span>

    ![Crear entidad simple - color](images/AzureLabs-Lab3-12.png)
 
11. <span data-ttu-id="c68fd-223">Repita este proceso para crear tres (3) más Simple entidades denominadas:</span><span class="sxs-lookup"><span data-stu-id="c68fd-223">Repeat this process to create three (3) more Simple Entities named:</span></span>

    -   <span data-ttu-id="c68fd-224">*upsize*</span><span class="sxs-lookup"><span data-stu-id="c68fd-224">*upsize*</span></span>
    -   <span data-ttu-id="c68fd-225">*downsize*</span><span class="sxs-lookup"><span data-stu-id="c68fd-225">*downsize*</span></span>
    -   <span data-ttu-id="c68fd-226">*target*</span><span class="sxs-lookup"><span data-stu-id="c68fd-226">*target*</span></span>

<span data-ttu-id="c68fd-227">El resultado debería ser similar a la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="c68fd-227">The result should look like the image below:</span></span>

![Resultado de la creación de la entidad](images/AzureLabs-Lab3-13.png)
 
<span data-ttu-id="c68fd-229">En este momento puede comenzar a crear *intenciones*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-229">At this point you can begin creating *Intents*.</span></span> 

> [!WARNING]
> <span data-ttu-id="c68fd-230">No elimine el **ninguno** intención.</span><span class="sxs-lookup"><span data-stu-id="c68fd-230">Do not delete the **None** intent.</span></span>

12. <span data-ttu-id="c68fd-231">En el lado izquierdo de la página, haga clic en **intenciones**, a continuación, haga clic en **crear nuevo intento**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-231">On the left side of the page, click on **Intents**, then click on **Create new intent**.</span></span>

    ![Crear nuevas plataformas intents](images/AzureLabs-Lab3-14.png)

13. <span data-ttu-id="c68fd-233">Llame al nuevo *intención* **ChangeObjectColor**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-233">Call the new *Intent* **ChangeObjectColor**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="c68fd-234">Esto *intención* nombre se usa dentro del código más adelante en este curso, así que para obtener mejores resultados, use este nombre tal y como se proporciona.</span><span class="sxs-lookup"><span data-stu-id="c68fd-234">This *Intent* name is used within the code later in this course, so for best results, use this name exactly as provided.</span></span>

<span data-ttu-id="c68fd-235">Una vez que confirme el nombre que se le dirigirá a la página de intenciones.</span><span class="sxs-lookup"><span data-stu-id="c68fd-235">Once you confirm the name you will be directed to the Intents Page.</span></span>

![LUIS - página de intenciones](images/AzureLabs-Lab3-15.png)

<span data-ttu-id="c68fd-237">Observará que hay un cuadro de texto que le pide al tipo de 5 o más diferente *grabaciones de voz*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-237">You will notice that there is a textbox asking you to type 5 or more different *Utterances*.</span></span>

> [!NOTE]
> <span data-ttu-id="c68fd-238">LUIS convierte todas las grabaciones de voz a minúsculas.</span><span class="sxs-lookup"><span data-stu-id="c68fd-238">LUIS converts all Utterances to lower case.</span></span>

14. <span data-ttu-id="c68fd-239">Inserte el siguiente *Utterance* en el cuadro de texto superior (actualmente con el texto *tipo alrededor de 5 ejemplos...*</span><span class="sxs-lookup"><span data-stu-id="c68fd-239">Insert the following *Utterance* in the top textbox (currently with the text *Type about 5 examples…*</span></span> <span data-ttu-id="c68fd-240">) y presione **ENTRAR**:</span><span class="sxs-lookup"><span data-stu-id="c68fd-240">), and press **Enter**:</span></span>

```
The color of the cylinder must be red
```

<span data-ttu-id="c68fd-241">Observará que el nuevo *Utterance* aparecerán en una lista debajo.</span><span class="sxs-lookup"><span data-stu-id="c68fd-241">You will notice that the new *Utterance* will appear in a list underneath.</span></span>

<span data-ttu-id="c68fd-242">Siguiendo el mismo proceso, inserte las siguientes declaraciones para seis (6):</span><span class="sxs-lookup"><span data-stu-id="c68fd-242">Following the same process, insert the following six (6) Utterances:</span></span>

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

<span data-ttu-id="c68fd-243">Para cada declaración que ha creado, debe identificar las palabras que se deben usar Luis como entidades.</span><span class="sxs-lookup"><span data-stu-id="c68fd-243">For each Utterance you have created, you must identify which words should be used by LUIS as Entities.</span></span> <span data-ttu-id="c68fd-244">En este ejemplo necesita etiquetar todos los colores como un *color* entidad y todos los posibles referencia de un destino como un *destino* entidad.</span><span class="sxs-lookup"><span data-stu-id="c68fd-244">In this example you need to label all the colors as a *color* Entity, and all the possible reference to a target as a *target* Entity.</span></span>

15. <span data-ttu-id="c68fd-245">Para ello, intente hacer clic en la palabra *cilindro* en el primer utterance (dictado) y seleccione *destino*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-245">To do so, try clicking on the word *cylinder* in the first Utterance and select *target*.</span></span>

    ![Identificar objetivos utterance (dictado)](images/AzureLabs-Lab3-16.png)
 
16. <span data-ttu-id="c68fd-247">Ahora, haga clic en la palabra *rojo* en el primer utterance (dictado) y seleccione *color*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-247">Now click on the word *red* in the first Utterance and select *color*.</span></span>

    ![Identificación de las entidades utterance (dictado)](images/AzureLabs-Lab3-17.png)
 
17. <span data-ttu-id="c68fd-249">Además, la siguiente línea de etiqueta donde *cubo* debe ser un *destino*, y *negro* debe ser un *color*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-249">Label the next line also, where *cube* should be a *target*, and *black* should be a *color*.</span></span> <span data-ttu-id="c68fd-250">Observe también el uso de las palabras *'this'*, *'it'*, y *'este objeto'*, lo que ofrecemos, por lo que tener también tipos no específico de destino disponibles.</span><span class="sxs-lookup"><span data-stu-id="c68fd-250">Notice also the use of the words *‘this’*, *‘it’*, and *‘this object’*, which we are providing, so to have non-specific target types available also.</span></span> 

18. <span data-ttu-id="c68fd-251">Repita el proceso anterior hasta que todas las palabras pronunciadas tienen las entidades etiquetadas como.</span><span class="sxs-lookup"><span data-stu-id="c68fd-251">Repeat the process above until all the Utterances have the Entities labelled.</span></span> <span data-ttu-id="c68fd-252">Vea la siguiente imagen, si necesita ayuda.</span><span class="sxs-lookup"><span data-stu-id="c68fd-252">See the below image if you need help.</span></span>

    > [!TIP]
    > <span data-ttu-id="c68fd-253">Al seleccionar las palabras que desea etiquetarlos como entidades:</span><span class="sxs-lookup"><span data-stu-id="c68fd-253">When selecting words to label them as entities:</span></span>
    > - <span data-ttu-id="c68fd-254">Para las palabras individuales simplemente haga clic en ellos.</span><span class="sxs-lookup"><span data-stu-id="c68fd-254">For single words just click them.</span></span>
    > - <span data-ttu-id="c68fd-255">Para un conjunto de dos o más palabras, haga clic al principio y, a continuación, al final del conjunto.</span><span class="sxs-lookup"><span data-stu-id="c68fd-255">For a set of two or more words, click at the beginning and then at the end of the set.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c68fd-256">Puede usar el *Tokens vista* botón de alternancia para cambiar entre **entidades / Tokens View**!</span><span class="sxs-lookup"><span data-stu-id="c68fd-256">You can use the *Tokens View* toggle button to switch between **Entities / Tokens View**!</span></span>

19. <span data-ttu-id="c68fd-257">Los resultados deben ser como se muestra en las imágenes, a continuación, que muestra la **entidades / Tokens View**:</span><span class="sxs-lookup"><span data-stu-id="c68fd-257">The results should be as seen in the images below, showing the **Entities / Tokens View**:</span></span>

    ![Las vistas de las entidades y los tokens](images/AzureLabs-Lab3-18.png)
  
20. <span data-ttu-id="c68fd-259">En este momento se presione el **Train** situado en la parte superior derecha de la página y espere el pequeño indicador redondear en él para cambiar a verde.</span><span class="sxs-lookup"><span data-stu-id="c68fd-259">At this point press the **Train** button at the top-right of the page and wait for the small round indicator on it to turn green.</span></span> <span data-ttu-id="c68fd-260">Esto indica que se ha entrenado LUIS correctamente para que reconozca esta intención.</span><span class="sxs-lookup"><span data-stu-id="c68fd-260">This indicates that LUIS has been successfully trained to recognize this Intent.</span></span>

    ![LUIS "Train"](images/AzureLabs-Lab3-19.png)
 
21. <span data-ttu-id="c68fd-262">Como ejercicio para usted, cree un nuevo intento llamado **ChangeObjectSize**, con las entidades *destino*, *convertir*, y *reducir el tamaño de*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-262">As an exercise for you, create a new Intent called **ChangeObjectSize**, using the Entities *target*, *upsize*, and *downsize*.</span></span>
22. <span data-ttu-id="c68fd-263">Siguiendo el mismo proceso que la intención anterior, inserte las siguientes declaraciones para ocho (8) para *tamaño* cambiar:</span><span class="sxs-lookup"><span data-stu-id="c68fd-263">Following the same process as the previous Intent, insert the following eight (8) Utterances for *Size* change:</span></span>

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

23. <span data-ttu-id="c68fd-264">El resultado debería ser como el de la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="c68fd-264">The result should be like the one in the image below:</span></span>

    ![Configurar los Tokens ChangeObjectSize / entidades](images/AzureLabs-Lab3-20.png) 

24. <span data-ttu-id="c68fd-266">Una vez tanto intenciones **ChangeObjectColor** y **ChangeObjectSize**, se han creado y entrenado, haga clic en el **publicar** botón encima de la página.</span><span class="sxs-lookup"><span data-stu-id="c68fd-266">Once both Intents, **ChangeObjectColor** and **ChangeObjectSize**, have been created and trained, click on the **PUBLISH** button on top of the page.</span></span>

    ![Publicar servicio LUIS](images/AzureLabs-Lab3-21.png)

25. <span data-ttu-id="c68fd-268">En el *publicar* página se finalizar y publicar su App LUIS para que el código puede tener acceso a.</span><span class="sxs-lookup"><span data-stu-id="c68fd-268">On the *Publish* page you will finalize and publish your LUIS App so that it can be accessed by your code.</span></span>

    1. <span data-ttu-id="c68fd-269">Establecer la lista *Publish To* como **producción**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-269">Set the drop down *Publish To* as **Production**.</span></span>
    2. <span data-ttu-id="c68fd-270">Establecer el *Timezone* a su zona horaria.</span><span class="sxs-lookup"><span data-stu-id="c68fd-270">Set the *Timezone* to your time zone.</span></span>
    3. <span data-ttu-id="c68fd-271">Active la casilla de verificación **incluir todas las puntuaciones intención puede predecir**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-271">Check the box **Include all predicted intent scores**.</span></span>
    4. <span data-ttu-id="c68fd-272">Haga clic en **publicar en la ranura de producción**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-272">Click on **Publish to Production Slot**.</span></span>

        ![Configuración de publicación](images/AzureLabs-Lab3-22.png)

26. <span data-ttu-id="c68fd-274">En la sección *recursos y las claves*:</span><span class="sxs-lookup"><span data-stu-id="c68fd-274">In the section *Resources and Keys*:</span></span>

    1.  <span data-ttu-id="c68fd-275">Seleccione la región que se configuró para la instancia de servicio en el Portal de Azure.</span><span class="sxs-lookup"><span data-stu-id="c68fd-275">Select the region you set for service instance in the Azure Portal.</span></span>
    2.  <span data-ttu-id="c68fd-276">Observará un **Starter_Key** elemento a continuación, pasar por alto.</span><span class="sxs-lookup"><span data-stu-id="c68fd-276">You will notice a **Starter_Key** element below, ignore it.</span></span>
    3.  <span data-ttu-id="c68fd-277">Haga clic en **Agregar clave** e inserte el *clave* que obtuvo en el Portal de Azure al crear la instancia del servicio.</span><span class="sxs-lookup"><span data-stu-id="c68fd-277">Click on **Add Key** and insert the *Key* that you obtained in the Azure Portal when you created your Service instance.</span></span> <span data-ttu-id="c68fd-278">Si se registran los de Azure y el portal de LUIS en el mismo usuario, se le proporcionará los menús desplegables para *nombredeinquilino*, *nombre de la suscripción*y el *clave* que desea usar () tendrá el mismo nombre que proporcionó anteriormente en el Portal de Azure.</span><span class="sxs-lookup"><span data-stu-id="c68fd-278">If your Azure and the LUIS portal are logged into the same user, you will be provided drop-down menus for *Tenant name*, *Subscription Name*, and the *Key* you wish to use (will have the same name as you provided previously in the Azure Portal.</span></span>

    > [!IMPORTANT] 
    > <span data-ttu-id="c68fd-279">Debajo de la directiva *extremo*, realice una copia del punto de conexión correspondiente a la clave ha insertado, pronto podrá utilizarla en el código.</span><span class="sxs-lookup"><span data-stu-id="c68fd-279">Underneath *Endpoint*, take a copy of the endpoint corresponding to the Key you have inserted, you will soon use it in your code.</span></span>
 
## <a name="chapter-3--set-up-the-unity-project"></a><span data-ttu-id="c68fd-280">Capítulo 3: configurar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="c68fd-280">Chapter 3 – Set up the Unity project</span></span>

<span data-ttu-id="c68fd-281">El siguiente es un conjunto típico de para el desarrollo con la realidad mixta y por lo tanto, es una buena plantilla para otros proyectos.</span><span class="sxs-lookup"><span data-stu-id="c68fd-281">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="c68fd-282">Abra *Unity* y haga clic en **New**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-282">Open *Unity* and click **New**.</span></span> 

    ![Inicie el nuevo proyecto de Unity.](images/AzureLabs-Lab3-24.png)

2.  <span data-ttu-id="c68fd-284">Ahora deberá proporcionar un nombre de proyecto de Unity, insertar **MR_LUIS**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-284">You will now need to provide a Unity Project name, insert **MR_LUIS**.</span></span> <span data-ttu-id="c68fd-285">Asegúrese de que el tipo de proyecto se establece en **3D**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-285">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="c68fd-286">Establecer el **ubicación** a algún lugar adecuado para usted (Recuerde, es mejor cuanto más se acerque a los directorios raíz).</span><span class="sxs-lookup"><span data-stu-id="c68fd-286">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="c68fd-287">A continuación, haga clic en **crear un proyecto**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-287">Then, click **Create project**.</span></span>

    ![Se proporcionan detalles para el nuevo proyecto de Unity.](images/AzureLabs-Lab3-25.png)
 
3.  <span data-ttu-id="c68fd-289">Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-289">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="c68fd-290">Vaya a Editar > Preferencias y, a continuación, en la ventana nueva, vaya a **herramientas externas**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-290">Go to Edit > Preferences and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="c68fd-291">Cambio **External Script Editor** a **de Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-291">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="c68fd-292">Cerrar la **preferencias** ventana.</span><span class="sxs-lookup"><span data-stu-id="c68fd-292">Close the **Preferences** window.</span></span>

    ![Actualizar las preferencias del editor de secuencia de comandos.](images/AzureLabs-Lab3-26.png)
 
4.  <span data-ttu-id="c68fd-294">A continuación, vaya a **archivo > configuración de compilación** y cambiar la plataforma a **Universal Windows Platform**, haciendo clic en el **Cambiar plataforma** botón.</span><span class="sxs-lookup"><span data-stu-id="c68fd-294">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Crear ventana de configuración de la plataforma del conmutador para UWP.](images/AzureLabs-Lab3-27.png)
 
5.  <span data-ttu-id="c68fd-296">Vaya a **archivo > configuración de compilación** y asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="c68fd-296">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="c68fd-297">**Dispositivo de destino** está establecido en **cualquier dispositivo**</span><span class="sxs-lookup"><span data-stu-id="c68fd-297">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="c68fd-298">Para el Microsoft HoloLens, establezca **dispositivo de destino** a *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-298">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="c68fd-299">**Tipo de compilación** está establecido en **D3D**</span><span class="sxs-lookup"><span data-stu-id="c68fd-299">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="c68fd-300">**SDK** está establecido en **instalada más reciente**</span><span class="sxs-lookup"><span data-stu-id="c68fd-300">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="c68fd-301">**Versión de Visual Studio** está establecido en **instalada más reciente**</span><span class="sxs-lookup"><span data-stu-id="c68fd-301">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="c68fd-302">**Compilar y ejecutar** está establecido en **máquina Local**</span><span class="sxs-lookup"><span data-stu-id="c68fd-302">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="c68fd-303">Guarde la escena y agregarlo a la compilación.</span><span class="sxs-lookup"><span data-stu-id="c68fd-303">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="c68fd-304">Hacer esto seleccionando **agregar escenas abierto**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-304">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="c68fd-305">Aparecerá el guardado de la ventana.</span><span class="sxs-lookup"><span data-stu-id="c68fd-305">A save window will appear.</span></span>
        
            ![Haga clic en Agregar botón de escenas abierto](images/AzureLabs-Lab3-28.png)

        2. <span data-ttu-id="c68fd-307">Cree una nueva carpeta de esto y cualquier futuro, escena, a continuación, seleccione el **nueva carpeta** botón para crear una nueva carpeta y asígnele el nombre **escenas**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-307">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Crear nueva carpeta de scripts](images/AzureLabs-Lab3-29.png)

        3. <span data-ttu-id="c68fd-309">Abra el recién creado **escenas** carpeta y, a continuación, en el *nombre de archivo*: campo de texto, escriba **MR_LuisScene**, a continuación, presione **guardar**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-309">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_LuisScene**, then press **Save**.</span></span>

            ![Asigne un nombre de nueva escena.](images/AzureLabs-Lab3-30.png)

    7. <span data-ttu-id="c68fd-311">El resto de la configuración, en *configuración de compilación*, debe dejarse como predeterminada por ahora.</span><span class="sxs-lookup"><span data-stu-id="c68fd-311">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="c68fd-312">En el *configuración de compilación* ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el *Inspector* se encuentra.</span><span class="sxs-lookup"><span data-stu-id="c68fd-312">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Abra Configuración del Reproductor.](images/AzureLabs-Lab3-31.png) 
 
7. <span data-ttu-id="c68fd-314">En este panel, es necesario comprobar algunas opciones de configuración:</span><span class="sxs-lookup"><span data-stu-id="c68fd-314">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="c68fd-315">En el **otra configuración** pestaña:</span><span class="sxs-lookup"><span data-stu-id="c68fd-315">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="c68fd-316">**Versión en tiempo de ejecución de secuencias de comandos** debe ser **estable** (.NET 3.5 equivalente).</span><span class="sxs-lookup"><span data-stu-id="c68fd-316">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="c68fd-317">**Scripting de back-end** debe ser **.NET**</span><span class="sxs-lookup"><span data-stu-id="c68fd-317">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="c68fd-318">**Nivel de compatibilidad de API** debe ser **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="c68fd-318">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Actualizar la configuración de otros.](images/AzureLabs-Lab3-32.png)
      
    2. <span data-ttu-id="c68fd-320">Dentro de la **configuración de publicación** ficha **capacidades**, consulte:</span><span class="sxs-lookup"><span data-stu-id="c68fd-320">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="c68fd-321">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="c68fd-321">**InternetClient**</span></span>
        2. <span data-ttu-id="c68fd-322">**Micrófono**</span><span class="sxs-lookup"><span data-stu-id="c68fd-322">**Microphone**</span></span>

            ![Actualizando la configuración de publicación.](images/AzureLabs-Lab3-33.png)

    3. <span data-ttu-id="c68fd-324">Más abajo el panel, en **XR configuración** (bajo **configuración de publicación**), graduación **admite la realidad Virtual**, asegúrese de que el **SDK de Windows Mixed Reality**  se agrega.</span><span class="sxs-lookup"><span data-stu-id="c68fd-324">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Actualice la configuración de R de X.](images/AzureLabs-Lab3-34.png)

8.  <span data-ttu-id="c68fd-326">En *configuración de compilación* _Unity C#_  proyectos ya no está atenuada; Marque la casilla situada junto a esto.</span><span class="sxs-lookup"><span data-stu-id="c68fd-326">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="c68fd-327">Cierre la ventana de configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="c68fd-327">Close the Build Settings window.</span></span>
10. <span data-ttu-id="c68fd-328">Guarde la escena y el proyecto (**archivo > Guardar ESCENA / archivo > Guardar proyecto**).</span><span class="sxs-lookup"><span data-stu-id="c68fd-328">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4--create-the-scene"></a><span data-ttu-id="c68fd-329">Capítulo 4: crear la escena</span><span class="sxs-lookup"><span data-stu-id="c68fd-329">Chapter 4 – Create the scene</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c68fd-330">Si desea omitir la *configurar Unity* componente de este curso y continuar directamente en código, no dude en descargar este [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), importarlo en el proyecto como un [paquete personalizado ](https://docs.unity3d.com/Manual/AssetPackages.html)y, a continuación, continuar desde [capítulo 5](#chapter-5--create-the-microphonemanager-class).</span><span class="sxs-lookup"><span data-stu-id="c68fd-330">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-microphonemanager-class).</span></span> 

1.  <span data-ttu-id="c68fd-331">Haga clic en un área vacía de la *jerarquía Panel*, en **objeto 3D**, agregue un **plano**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-331">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Plane**.</span></span>

    ![Crear un plano.](images/AzureLabs-Lab3-35.png)

2.  <span data-ttu-id="c68fd-333">Tenga en cuenta que cuando haga doble clic en el *jerarquía* nuevo para crear más objetos, si sigue teniendo el último objeto seleccionado, el objeto seleccionado será el elemento primario del objeto nuevo.</span><span class="sxs-lookup"><span data-stu-id="c68fd-333">Be aware that when you right-click within the *Hierarchy* again to create more objects, if you still have the last object selected, the selected object will be the parent of your new object.</span></span> <span data-ttu-id="c68fd-334">Evitar esto, hace clic en un espacio vacío dentro de la jerarquía y, a continuación, haciendo clic en.</span><span class="sxs-lookup"><span data-stu-id="c68fd-334">Avoid this left-clicking in an empty space within the Hierarchy, and then right-clicking.</span></span>

3.  <span data-ttu-id="c68fd-335">Repita el procedimiento anterior para agregar los siguientes objetos:</span><span class="sxs-lookup"><span data-stu-id="c68fd-335">Repeat the above procedure to add the following objects:</span></span>

    1. <span data-ttu-id="c68fd-336">*Sphere*</span><span class="sxs-lookup"><span data-stu-id="c68fd-336">*Sphere*</span></span>
    2. <span data-ttu-id="c68fd-337">*Cilindro*</span><span class="sxs-lookup"><span data-stu-id="c68fd-337">*Cylinder*</span></span>
    3. <span data-ttu-id="c68fd-338">*Cubo*</span><span class="sxs-lookup"><span data-stu-id="c68fd-338">*Cube*</span></span>
    4. <span data-ttu-id="c68fd-339">*Texto 3D*</span><span class="sxs-lookup"><span data-stu-id="c68fd-339">*3D Text*</span></span>

4.  <span data-ttu-id="c68fd-340">La escena resultante *jerarquía* debe ser como el de la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="c68fd-340">The resulting scene *Hierarchy* should be like the one in the image below:</span></span>

    ![Configuración de la jerarquía escena.](images/AzureLabs-Lab3-36.png)
 
5.  <span data-ttu-id="c68fd-342">Haga clic en el **cámara principal** para seleccionarlo, examine el *Panel Inspector* , verá el objeto de cámara con todos los sus componentes.</span><span class="sxs-lookup"><span data-stu-id="c68fd-342">Left click on the **Main Camera** to select it, look at the *Inspector Panel* you will see the Camera object with all the its components.</span></span>
6.  <span data-ttu-id="c68fd-343">Haga clic en el **Agregar componente** situado en la parte inferior de la *Panel Inspector*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-343">Click on the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span>

    ![Agregar origen de Audio](images/AzureLabs-Lab3-37.png)
 
7.  <span data-ttu-id="c68fd-345">Busque el componente denominado *origen Audio*, como se indicó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c68fd-345">Search for the component called *Audio Source*, as shown above.</span></span>
8.  <span data-ttu-id="c68fd-346">Además, asegúrese de que el *transformar* componente de la cámara principal se establece en (0,0,0), esto puede hacerse presionando el **engranaje** icono situado junto a la cámara *transformar* componente y seleccione **restablecer**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-346">Also make sure that the *Transform* component of the Main Camera is set to (0,0,0), this can be done by pressing the **Gear** icon next to the Camera’s *Transform* component and selecting **Reset**.</span></span> <span data-ttu-id="c68fd-347">El *transformar* componente debería entonces el aspecto siguiente:</span><span class="sxs-lookup"><span data-stu-id="c68fd-347">The *Transform* component should then look like:</span></span>

    1.  <span data-ttu-id="c68fd-348">*Posición* está establecido en **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-348">*Position* is set to **0, 0, 0**.</span></span>
    2.  <span data-ttu-id="c68fd-349">*Rotación* está establecido en **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-349">*Rotation* is set to **0, 0, 0**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="c68fd-350">Para el Microsoft HoloLens, deberá cambiar también los siguientes valores, que forman parte de la **cámara** componente, que se encuentra en su **cámara principal**:</span><span class="sxs-lookup"><span data-stu-id="c68fd-350">For the Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component, which is on your **Main Camera**:</span></span>
    > - <span data-ttu-id="c68fd-351">**Borrar las marcas de:** Color sólido.</span><span class="sxs-lookup"><span data-stu-id="c68fd-351">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="c68fd-352">**En segundo plano** ' negro, alfa 0': código de color hexadecimal: #00000000.</span><span class="sxs-lookup"><span data-stu-id="c68fd-352">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

9.  <span data-ttu-id="c68fd-353">Haga clic en el **plano** para seleccionarlo.</span><span class="sxs-lookup"><span data-stu-id="c68fd-353">Left click on the **Plane** to select it.</span></span> <span data-ttu-id="c68fd-354">En el *Panel Inspector* establecer el *transformar* componente con los valores siguientes:</span><span class="sxs-lookup"><span data-stu-id="c68fd-354">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="c68fd-355">Transformar - *posición*</span><span class="sxs-lookup"><span data-stu-id="c68fd-355">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="c68fd-356">**X**</span><span class="sxs-lookup"><span data-stu-id="c68fd-356">**X**</span></span> | <span data-ttu-id="c68fd-357">**Y**</span><span class="sxs-lookup"><span data-stu-id="c68fd-357">**Y**</span></span>                  | <span data-ttu-id="c68fd-358">**Z**</span><span class="sxs-lookup"><span data-stu-id="c68fd-358">**Z**</span></span> |
    | <span data-ttu-id="c68fd-359">0</span><span class="sxs-lookup"><span data-stu-id="c68fd-359">0</span></span>     | <span data-ttu-id="c68fd-360">-1</span><span class="sxs-lookup"><span data-stu-id="c68fd-360">-1</span></span>                     | <span data-ttu-id="c68fd-361">0</span><span class="sxs-lookup"><span data-stu-id="c68fd-361">0</span></span>     |


10. <span data-ttu-id="c68fd-362">Haga clic en el **esfera** para seleccionarlo.</span><span class="sxs-lookup"><span data-stu-id="c68fd-362">Left click on the **Sphere** to select it.</span></span> <span data-ttu-id="c68fd-363">En el *Panel Inspector* establecer el *transformar* componente con los valores siguientes:</span><span class="sxs-lookup"><span data-stu-id="c68fd-363">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="c68fd-364">Transformar - *posición*</span><span class="sxs-lookup"><span data-stu-id="c68fd-364">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="c68fd-365">**X**</span><span class="sxs-lookup"><span data-stu-id="c68fd-365">**X**</span></span> | <span data-ttu-id="c68fd-366">**Y**</span><span class="sxs-lookup"><span data-stu-id="c68fd-366">**Y**</span></span>                  | <span data-ttu-id="c68fd-367">**Z**</span><span class="sxs-lookup"><span data-stu-id="c68fd-367">**Z**</span></span> |
    | <span data-ttu-id="c68fd-368">2</span><span class="sxs-lookup"><span data-stu-id="c68fd-368">2</span></span>     | <span data-ttu-id="c68fd-369">1</span><span class="sxs-lookup"><span data-stu-id="c68fd-369">1</span></span>                      | <span data-ttu-id="c68fd-370">2</span><span class="sxs-lookup"><span data-stu-id="c68fd-370">2</span></span>     |

11. <span data-ttu-id="c68fd-371">Haga clic en el **cilindro** para seleccionarlo.</span><span class="sxs-lookup"><span data-stu-id="c68fd-371">Left click on the **Cylinder** to select it.</span></span> <span data-ttu-id="c68fd-372">En el *Panel Inspector* establecer el *transformar* componente con los valores siguientes:</span><span class="sxs-lookup"><span data-stu-id="c68fd-372">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="c68fd-373">Transformar - *posición*</span><span class="sxs-lookup"><span data-stu-id="c68fd-373">Transform - *Position*</span></span> |       |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="c68fd-374">**X**</span><span class="sxs-lookup"><span data-stu-id="c68fd-374">**X**</span></span> | <span data-ttu-id="c68fd-375">**Y**</span><span class="sxs-lookup"><span data-stu-id="c68fd-375">**Y**</span></span>                  | <span data-ttu-id="c68fd-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="c68fd-376">**Z**</span></span> |
    | <span data-ttu-id="c68fd-377">-2</span><span class="sxs-lookup"><span data-stu-id="c68fd-377">-2</span></span>    | <span data-ttu-id="c68fd-378">1</span><span class="sxs-lookup"><span data-stu-id="c68fd-378">1</span></span>                      | <span data-ttu-id="c68fd-379">2</span><span class="sxs-lookup"><span data-stu-id="c68fd-379">2</span></span>     |

12. <span data-ttu-id="c68fd-380">Haga clic en el **cubo** para seleccionarlo.</span><span class="sxs-lookup"><span data-stu-id="c68fd-380">Left click on the **Cube** to select it.</span></span> <span data-ttu-id="c68fd-381">En el *Panel Inspector* establecer el *transformar* componente con los valores siguientes:</span><span class="sxs-lookup"><span data-stu-id="c68fd-381">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |        | <span data-ttu-id="c68fd-382">Transformar - *posición*</span><span class="sxs-lookup"><span data-stu-id="c68fd-382">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="c68fd-383">Transformar - *rotación*</span><span class="sxs-lookup"><span data-stu-id="c68fd-383">Transform - *Rotation*</span></span> |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="c68fd-384">**X**</span><span class="sxs-lookup"><span data-stu-id="c68fd-384">**X**</span></span> | <span data-ttu-id="c68fd-385">**Y**</span><span class="sxs-lookup"><span data-stu-id="c68fd-385">**Y**</span></span>                   | <span data-ttu-id="c68fd-386">**Z**</span><span class="sxs-lookup"><span data-stu-id="c68fd-386">**Z**</span></span> |  \| | <span data-ttu-id="c68fd-387">**X**</span><span class="sxs-lookup"><span data-stu-id="c68fd-387">**X**</span></span> | <span data-ttu-id="c68fd-388">**Y**</span><span class="sxs-lookup"><span data-stu-id="c68fd-388">**Y**</span></span>                  | <span data-ttu-id="c68fd-389">**Z**</span><span class="sxs-lookup"><span data-stu-id="c68fd-389">**Z**</span></span> |
    | <span data-ttu-id="c68fd-390">0</span><span class="sxs-lookup"><span data-stu-id="c68fd-390">0</span></span>     | <span data-ttu-id="c68fd-391">1</span><span class="sxs-lookup"><span data-stu-id="c68fd-391">1</span></span>                       | <span data-ttu-id="c68fd-392">4</span><span class="sxs-lookup"><span data-stu-id="c68fd-392">4</span></span>     |  \| | <span data-ttu-id="c68fd-393">45</span><span class="sxs-lookup"><span data-stu-id="c68fd-393">45</span></span>    | <span data-ttu-id="c68fd-394">45</span><span class="sxs-lookup"><span data-stu-id="c68fd-394">45</span></span>                     | <span data-ttu-id="c68fd-395">0</span><span class="sxs-lookup"><span data-stu-id="c68fd-395">0</span></span>     | 

13. <span data-ttu-id="c68fd-396">Haga clic en el **nuevo texto** objeto para seleccionarlo.</span><span class="sxs-lookup"><span data-stu-id="c68fd-396">Left click on the **New Text** object to select it.</span></span> <span data-ttu-id="c68fd-397">En el *Panel Inspector* establecer el *transformar* componente con los valores siguientes:</span><span class="sxs-lookup"><span data-stu-id="c68fd-397">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="c68fd-398">Transformar - *posición*</span><span class="sxs-lookup"><span data-stu-id="c68fd-398">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="c68fd-399">Transformar - *escala*</span><span class="sxs-lookup"><span data-stu-id="c68fd-399">Transform - *Scale*</span></span> |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | <span data-ttu-id="c68fd-400">**X**</span><span class="sxs-lookup"><span data-stu-id="c68fd-400">**X**</span></span> | <span data-ttu-id="c68fd-401">**Y**</span><span class="sxs-lookup"><span data-stu-id="c68fd-401">**Y**</span></span>                  | <span data-ttu-id="c68fd-402">**Z**</span><span class="sxs-lookup"><span data-stu-id="c68fd-402">**Z**</span></span> |  \| | <span data-ttu-id="c68fd-403">**X**</span><span class="sxs-lookup"><span data-stu-id="c68fd-403">**X**</span></span> | <span data-ttu-id="c68fd-404">**Y**</span><span class="sxs-lookup"><span data-stu-id="c68fd-404">**Y**</span></span>               | <span data-ttu-id="c68fd-405">**Z**</span><span class="sxs-lookup"><span data-stu-id="c68fd-405">**Z**</span></span> |
    | <span data-ttu-id="c68fd-406">-2</span><span class="sxs-lookup"><span data-stu-id="c68fd-406">-2</span></span>    | <span data-ttu-id="c68fd-407">6</span><span class="sxs-lookup"><span data-stu-id="c68fd-407">6</span></span>                      | <span data-ttu-id="c68fd-408">9</span><span class="sxs-lookup"><span data-stu-id="c68fd-408">9</span></span>     |  \| | <span data-ttu-id="c68fd-409">0.1</span><span class="sxs-lookup"><span data-stu-id="c68fd-409">0.1</span></span>   | <span data-ttu-id="c68fd-410">0.1</span><span class="sxs-lookup"><span data-stu-id="c68fd-410">0.1</span></span>                 | <span data-ttu-id="c68fd-411">0.1</span><span class="sxs-lookup"><span data-stu-id="c68fd-411">0.1</span></span>   | 

14. <span data-ttu-id="c68fd-412">Cambio **Font Size** en el **texto de la malla** al **50**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-412">Change **Font Size** in the **Text Mesh** component to **50**.</span></span>
15. <span data-ttu-id="c68fd-413">Cambiar el *nombre* de la **texto de la malla** objeto **texto dictado**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-413">Change the *name* of the **Text Mesh** object to **Dictation Text**.</span></span>

    ![Crear objeto de texto 3D](images/AzureLabs-Lab3-38.png)
 
16. <span data-ttu-id="c68fd-415">La estructura del Panel de la jerarquía debe ser ahora similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="c68fd-415">Your Hierarchy Panel structure should now look like this:</span></span>

    ![texto de la malla en la vista de escena](images/AzureLabs-Lab3-38b.png)


17. <span data-ttu-id="c68fd-417">La escena final debe parecerse a la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="c68fd-417">The final scene should look like the image below:</span></span>

    ![La vista de escena.](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a><span data-ttu-id="c68fd-419">Capítulo 5: crear la clase MicrophoneManager</span><span class="sxs-lookup"><span data-stu-id="c68fd-419">Chapter 5 – Create the MicrophoneManager class</span></span>

<span data-ttu-id="c68fd-420">Es el primer Script que se va a crear el *MicrophoneManager* clase.</span><span class="sxs-lookup"><span data-stu-id="c68fd-420">The first Script you are going to create is the *MicrophoneManager* class.</span></span> <span data-ttu-id="c68fd-421">De este modo, creará el *LuisManager*, el *comportamientos* (clase), por último, el *que mirar* clase (si quiere, puede crear todos estos ahora, aunque se tratarán como llegar a cada capítulo).</span><span class="sxs-lookup"><span data-stu-id="c68fd-421">Following this, you will create the *LuisManager*, the *Behaviours* class, and lastly the *Gaze* class (feel free to create all these now, though it will be covered as you reach each Chapter).</span></span>

<span data-ttu-id="c68fd-422">El *MicrophoneManager* clase es responsable de:</span><span class="sxs-lookup"><span data-stu-id="c68fd-422">The *MicrophoneManager* class is responsible for:</span></span>

-   <span data-ttu-id="c68fd-423">Detectar el dispositivo de grabación conectado al equipo (lo que sea el valor predeterminado) o auriculares.</span><span class="sxs-lookup"><span data-stu-id="c68fd-423">Detecting the recording device attached to the headset or machine (whichever is the default one).</span></span>
-   <span data-ttu-id="c68fd-424">Captura de audio (voces) y use el dictado para almacenarla como una cadena.</span><span class="sxs-lookup"><span data-stu-id="c68fd-424">Capture the audio (voice) and use dictation to store it as a string.</span></span>
-   <span data-ttu-id="c68fd-425">Una vez que se ha pausado la voz, enviar el dictado a la *LuisManager* clase.</span><span class="sxs-lookup"><span data-stu-id="c68fd-425">Once the voice has paused, submit the dictation to the *LuisManager* class.</span></span> 

<span data-ttu-id="c68fd-426">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="c68fd-426">To create this class:</span></span> 

1.  <span data-ttu-id="c68fd-427">Haga clic en el *Panel del proyecto*, **crear > carpeta**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-427">Right-click in the *Project Panel*, **Create > Folder**.</span></span> <span data-ttu-id="c68fd-428">Llame a la carpeta **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-428">Call the folder **Scripts**.</span></span> 

    ![Crear carpeta de Scripts.](images/AzureLabs-Lab3-40.png)
 
2.  <span data-ttu-id="c68fd-430">Con el **Scripts** carpeta creada, haga doble clic en él para abrirlo.</span><span class="sxs-lookup"><span data-stu-id="c68fd-430">With the **Scripts** folder created, double click it, to open.</span></span> <span data-ttu-id="c68fd-431">A continuación, dentro de esa carpeta, con el botón secundario, **crear > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-431">Then, within that folder, right-click, **Create > C# Script**.</span></span> <span data-ttu-id="c68fd-432">Nombre de la secuencia de comandos *MicrophoneManager*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-432">Name the script *MicrophoneManager*.</span></span> 

3.  <span data-ttu-id="c68fd-433">Haga doble clic en *MicrophoneManager* para abrirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-433">Double click on *MicrophoneManager* to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="c68fd-434">Agregue los siguientes espacios de nombres en la parte superior del archivo:</span><span class="sxs-lookup"><span data-stu-id="c68fd-434">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="c68fd-435">A continuación, agregue las siguientes variables dentro de la *MicrophoneManager* clase:</span><span class="sxs-lookup"><span data-stu-id="c68fd-435">Then add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  <span data-ttu-id="c68fd-436">El código para *Awake()* y *Start()* métodos ahora debe agregarse.</span><span class="sxs-lookup"><span data-stu-id="c68fd-436">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="c68fd-437">Estos se llamará cuando se inicializa la clase:</span><span class="sxs-lookup"><span data-stu-id="c68fd-437">These will be called when the class initializes:</span></span>

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
 
7.  <span data-ttu-id="c68fd-438">Ahora tiene el método que usa la aplicación para iniciar y detener la captura de voz y pasarlo a la *LuisManager* (clase), que se compila en breve.</span><span class="sxs-lookup"><span data-stu-id="c68fd-438">Now you need the method that the App uses to start and stop the voice capture, and pass it to the *LuisManager* class, that you will build soon.</span></span> 

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

8.  <span data-ttu-id="c68fd-439">Agregar un *controlador dictado* que se invocará cuando se detiene la voz.</span><span class="sxs-lookup"><span data-stu-id="c68fd-439">Add a *Dictation Handler* that will be invoked when the voice pauses.</span></span> <span data-ttu-id="c68fd-440">Este método pasará el texto dictado a la *LuisManager* clase.</span><span class="sxs-lookup"><span data-stu-id="c68fd-440">This method will pass the dictation text to the *LuisManager* class.</span></span>

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
    > <span data-ttu-id="c68fd-441">Eliminar el *Update()* método puesto que esta clase no lo usará.</span><span class="sxs-lookup"><span data-stu-id="c68fd-441">Delete the *Update()* method since this class will not use it.</span></span>

9.  <span data-ttu-id="c68fd-442">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-442">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c68fd-443">En este momento aparece un error que aparecen en la *Panel de consola del Editor de Unity*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-443">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="c68fd-444">Esto es porque el código hace referencia a la *LuisManager* clase que se creará en el próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="c68fd-444">This is because the code references the *LuisManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-6--create-the-luismanager-class"></a><span data-ttu-id="c68fd-445">Capítulo 6: crear la clase LUISManager</span><span class="sxs-lookup"><span data-stu-id="c68fd-445">Chapter 6 – Create the LUISManager class</span></span>

<span data-ttu-id="c68fd-446">Es el momento de crear el *LuisManager* (clase), lo que hará que la llamada al servicio Azure LUIS.</span><span class="sxs-lookup"><span data-stu-id="c68fd-446">It is time for you to create the *LuisManager* class, which will make the call to the Azure LUIS service.</span></span> 

<span data-ttu-id="c68fd-447">El propósito de esta clase se va a recibir el texto dictado el *MicrophoneManager* clase y enviarlo a la *Azure Language Understanding API* para analizarlos.</span><span class="sxs-lookup"><span data-stu-id="c68fd-447">The purpose of this class is to receive the dictation text from the *MicrophoneManager* class and send it to the *Azure Language Understanding API* to be analyzed.</span></span>

<span data-ttu-id="c68fd-448">Esta clase se deserializará la *JSON* respuesta y llamar a los métodos adecuados de la *comportamientos* clase para desencadenar una acción.</span><span class="sxs-lookup"><span data-stu-id="c68fd-448">This class will deserialize the *JSON* response and call the appropriate methods of the *Behaviours* class to trigger an action.</span></span>

<span data-ttu-id="c68fd-449">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="c68fd-449">To create this class:</span></span> 

1.  <span data-ttu-id="c68fd-450">Haga doble clic en el **Scripts** carpeta para abrirla.</span><span class="sxs-lookup"><span data-stu-id="c68fd-450">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="c68fd-451">Haga clic en el **Scripts** carpeta, haga clic en **crear > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-451">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="c68fd-452">Nombre de la secuencia de comandos *LuisManager*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-452">Name the script *LuisManager*.</span></span> 
3.  <span data-ttu-id="c68fd-453">Haga doble clic en el script para abrirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c68fd-453">Double click on the script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="c68fd-454">Agregue los siguientes espacios de nombres en la parte superior del archivo:</span><span class="sxs-lookup"><span data-stu-id="c68fd-454">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="c68fd-455">Se iniciará mediante la creación de tres clases **dentro de** el *LuisManager* clase (dentro del mismo archivo de script, por encima del *Start()* método) que representará deserializado Respuesta JSON de Azure.</span><span class="sxs-lookup"><span data-stu-id="c68fd-455">You will begin by creating three classes **inside** the *LuisManager* class (within the same script file, above the *Start()* method) that will represent the deserialized JSON response from Azure.</span></span>

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

6.  <span data-ttu-id="c68fd-456">A continuación, agregue las siguientes variables dentro de la *LuisManager* clase:</span><span class="sxs-lookup"><span data-stu-id="c68fd-456">Next, add the following variables inside the *LuisManager* class:</span></span>
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  <span data-ttu-id="c68fd-457">Asegúrese de que va a colocar el punto de conexión de LUIS en ahora (que tendrá desde el portal de LUIS).</span><span class="sxs-lookup"><span data-stu-id="c68fd-457">Make sure to place your LUIS endpoint in now (which you will have from your LUIS portal).</span></span>

8.  <span data-ttu-id="c68fd-458">El código para el *Awake()* método ahora debe agregarse.</span><span class="sxs-lookup"><span data-stu-id="c68fd-458">Code for the *Awake()* method now needs to be added.</span></span> <span data-ttu-id="c68fd-459">Este método se llamará cuando se inicializa la clase:</span><span class="sxs-lookup"><span data-stu-id="c68fd-459">This method will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  <span data-ttu-id="c68fd-460">Ahora tiene los métodos de esta aplicación se usa para enviar el dictado recibido desde el *MicrophoneManager* clase *LUIS*y, a continuación, recibir y deserializar la respuesta.</span><span class="sxs-lookup"><span data-stu-id="c68fd-460">Now you need the methods this application uses to send the dictation received from the *MicrophoneManager* class to *LUIS*, and then receive and deserialize the response.</span></span> 
10. <span data-ttu-id="c68fd-461">Una vez determinado el valor de la intención y las entidades asociadas, se pasan a la instancia de la *comportamientos* clase para desencadenar la acción deseada.</span><span class="sxs-lookup"><span data-stu-id="c68fd-461">Once the value of the Intent, and associated Entities, have been determined, they are passed to the instance of the *Behaviours* class to trigger the intended action.</span></span>

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
 
11. <span data-ttu-id="c68fd-462">Crear un nuevo método denominado *AnalyseResponseElements()* que leerá resultante *AnalysedQuery* y determinar las entidades.</span><span class="sxs-lookup"><span data-stu-id="c68fd-462">Create a new method called *AnalyseResponseElements()* that will read the resulting *AnalysedQuery* and determine the Entities.</span></span> <span data-ttu-id="c68fd-463">Una vez que se determinan las entidades, se pasará a la instancia de la *comportamientos* clase que se utiliza en las acciones.</span><span class="sxs-lookup"><span data-stu-id="c68fd-463">Once those Entities are determined, they will be passed to the instance of the *Behaviours* class to use in the actions.</span></span>

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

            // Depending on the topmost recognised intent, read the entities name
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
    > <span data-ttu-id="c68fd-464">Eliminar el *Start()* y *Update()* métodos, ya que esta clase no los utilizará.</span><span class="sxs-lookup"><span data-stu-id="c68fd-464">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

12. <span data-ttu-id="c68fd-465">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-465">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

> [!NOTE]
> <span data-ttu-id="c68fd-466">En este punto se dará cuenta de varios errores que aparecen en la *Panel de consola del Editor de Unity*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-466">At this point you will notice several errors appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="c68fd-467">Esto es porque el código hace referencia a la *comportamientos* clase que se creará en el próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="c68fd-467">This is because the code references the *Behaviours* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--create-the-behaviours-class"></a><span data-ttu-id="c68fd-468">Capítulo 7: crear la clase de comportamientos</span><span class="sxs-lookup"><span data-stu-id="c68fd-468">Chapter 7 – Create the Behaviours class</span></span>

<span data-ttu-id="c68fd-469">El *comportamientos* clase desencadenará las acciones con las entidades proporcionadas por el *LuisManager* clase.</span><span class="sxs-lookup"><span data-stu-id="c68fd-469">The *Behaviours* class will trigger the actions using the Entities provided by the *LuisManager* class.</span></span>

<span data-ttu-id="c68fd-470">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="c68fd-470">To create this class:</span></span> 

1.  <span data-ttu-id="c68fd-471">Haga doble clic en el **Scripts** carpeta para abrirla.</span><span class="sxs-lookup"><span data-stu-id="c68fd-471">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="c68fd-472">Haga clic en el **Scripts** carpeta, haga clic en **crear > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-472">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="c68fd-473">Nombre de la secuencia de comandos *comportamientos*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-473">Name the script *Behaviours*.</span></span> 
3.  <span data-ttu-id="c68fd-474">Haga doble clic en el script para abrirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-474">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="c68fd-475">A continuación, agregue las siguientes variables dentro de la *comportamientos* clase:</span><span class="sxs-lookup"><span data-stu-id="c68fd-475">Then add the following variables inside the *Behaviours* class:</span></span>

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  <span data-ttu-id="c68fd-476">Agregar el *Awake()* código del método.</span><span class="sxs-lookup"><span data-stu-id="c68fd-476">Add the *Awake()* method code.</span></span> <span data-ttu-id="c68fd-477">Este método se llamará cuando se inicializa la clase:</span><span class="sxs-lookup"><span data-stu-id="c68fd-477">This method will be called when the class initializes:</span></span>

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  <span data-ttu-id="c68fd-478">Los siguientes métodos son invocados por la *LuisManager* clase (que ha creado anteriormente) para determinar qué objeto es el destino de la consulta y, a continuación, desencadenar la acción apropiada.</span><span class="sxs-lookup"><span data-stu-id="c68fd-478">The following methods are called by the *LuisManager* class (which you have created previously) to determine which object is the target of the query and then trigger the appropriate action.</span></span>

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
 
7.  <span data-ttu-id="c68fd-479">Agregar el *FindTarget()* método para determinar cuál de los *GameObjects* es el destino de la intención de actual.</span><span class="sxs-lookup"><span data-stu-id="c68fd-479">Add the *FindTarget()* method to determine which of the *GameObjects* is the target of the current Intent.</span></span> <span data-ttu-id="c68fd-480">Este método el valor predeterminado es el destino de la *GameObject* que se va a "gazed" Si no se define ningún destino explícita en las entidades.</span><span class="sxs-lookup"><span data-stu-id="c68fd-480">This method defaults the target to the *GameObject* being “gazed” if no explicit target is defined in the Entities.</span></span>

    ```csharp
        /// <summary>
        /// Determines which obejct reference is the target GameObject by providing its name
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
    > <span data-ttu-id="c68fd-481">Eliminar el *Start()* y *Update()* métodos, ya que esta clase no los utilizará.</span><span class="sxs-lookup"><span data-stu-id="c68fd-481">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

8.  <span data-ttu-id="c68fd-482">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-482">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--create-the-gaze-class"></a><span data-ttu-id="c68fd-483">Capítulo 8: crear la clase de mirada</span><span class="sxs-lookup"><span data-stu-id="c68fd-483">Chapter 8 – Create the Gaze Class</span></span>

<span data-ttu-id="c68fd-484">La clase último que necesitará para completar esta aplicación es el *que mirar* clase.</span><span class="sxs-lookup"><span data-stu-id="c68fd-484">The last class that you will need to complete this app is the *Gaze* class.</span></span> <span data-ttu-id="c68fd-485">Esta clase actualiza la referencia a la *GameObject* actualmente en foco visuales del usuario.</span><span class="sxs-lookup"><span data-stu-id="c68fd-485">This class updates the reference to the *GameObject* currently in the user’s visual focus.</span></span>

<span data-ttu-id="c68fd-486">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="c68fd-486">To create this Class:</span></span> 

1.  <span data-ttu-id="c68fd-487">Haga doble clic en el **Scripts** carpeta para abrirla.</span><span class="sxs-lookup"><span data-stu-id="c68fd-487">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="c68fd-488">Haga clic en el **Scripts** carpeta, haga clic en **crear > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-488">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="c68fd-489">Nombre de la secuencia de comandos *que mirar*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-489">Name the script *Gaze*.</span></span> 
3.  <span data-ttu-id="c68fd-490">Haga doble clic en el script para abrirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-490">Double click on the script to open it with *Visual Studio*.</span></span>
4.  <span data-ttu-id="c68fd-491">Inserte el siguiente código para esta clase:</span><span class="sxs-lookup"><span data-stu-id="c68fd-491">Insert the following code for this class:</span></span>

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
 
5.  <span data-ttu-id="c68fd-492">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-492">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--completing-the-scene-setup"></a><span data-ttu-id="c68fd-493">Capítulo 9: finalización de la configuración de la escena</span><span class="sxs-lookup"><span data-stu-id="c68fd-493">Chapter 9 – Completing the scene setup</span></span>

1.  <span data-ttu-id="c68fd-494">Para completar la instalación de la escena, arrastre cada script que ha creado desde la carpeta Scripts para la **cámara principal** objeto en el *jerarquía Panel*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-494">To complete the setup of the scene, drag each script that you have created from the Scripts Folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="c68fd-495">Seleccione el **cámara principal** y examine el *Panel Inspector*, podrá ver cada script que se ha conectado y observará que hay parámetros en cada secuencia de comandos que todavía han de establecerse.</span><span class="sxs-lookup"><span data-stu-id="c68fd-495">Select the **Main Camera** and look at the *Inspector Panel*, you should be able to see each script that you have attached, and you will notice that there are parameters on each script that are yet to be set.</span></span>

    ![Establecer los destinos de referencia de la cámara.](images/AzureLabs-Lab3-41.png)

3.  <span data-ttu-id="c68fd-497">Para establecer estos parámetros correctamente, siga estas instrucciones:</span><span class="sxs-lookup"><span data-stu-id="c68fd-497">To set these parameters correctly, follow these instructions:</span></span>

    1. <span data-ttu-id="c68fd-498">*MicrophoneManager*:</span><span class="sxs-lookup"><span data-stu-id="c68fd-498">*MicrophoneManager*:</span></span>

        - <span data-ttu-id="c68fd-499">Desde el *jerarquía Panel*, arrastre el **texto dictado** objeto en el **texto dictado** cuadro del valor de parámetro.</span><span class="sxs-lookup"><span data-stu-id="c68fd-499">From the *Hierarchy Panel*, drag the **Dictation Text** object into the **Dictation Text** parameter value box.</span></span>

    2. <span data-ttu-id="c68fd-500">*Comportamientos*, desde el *jerarquía Panel*:</span><span class="sxs-lookup"><span data-stu-id="c68fd-500">*Behaviours*, from the *Hierarchy Panel*:</span></span>

        - <span data-ttu-id="c68fd-501">Arrastre el **esfera** objeto en el *esfera* cuadro del destino de referencia.</span><span class="sxs-lookup"><span data-stu-id="c68fd-501">Drag the **Sphere** object into the *Sphere* reference target box.</span></span>
        - <span data-ttu-id="c68fd-502">Arrastre el **cilindro** en el *cilindro* cuadro del destino de referencia.</span><span class="sxs-lookup"><span data-stu-id="c68fd-502">Drag the **Cylinder** into the *Cylinder* reference target box.</span></span>
        - <span data-ttu-id="c68fd-503">Arrastre el **cubo** en el *cubo* cuadro del destino de referencia.</span><span class="sxs-lookup"><span data-stu-id="c68fd-503">Drag the **Cube** into the *Cube* reference target box.</span></span>

    3. <span data-ttu-id="c68fd-504">*Gaze*:</span><span class="sxs-lookup"><span data-stu-id="c68fd-504">*Gaze*:</span></span>

        - <span data-ttu-id="c68fd-505">Establecer el *que mirar Max distancia* a **300** (si aún no está).</span><span class="sxs-lookup"><span data-stu-id="c68fd-505">Set the *Gaze Max Distance* to **300** (if it is not already).</span></span> 

4.  <span data-ttu-id="c68fd-506">El resultado debería ser similar a la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="c68fd-506">The result should look like the image below:</span></span>

    ![Ahora que muestra los destinos de referencia de la cámara, establecer.](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a><span data-ttu-id="c68fd-508">Capítulo 10: prueba en el Editor de Unity</span><span class="sxs-lookup"><span data-stu-id="c68fd-508">Chapter 10 – Test in the Unity Editor</span></span>

<span data-ttu-id="c68fd-509">Prueba que se ha implementado correctamente la configuración de la escena.</span><span class="sxs-lookup"><span data-stu-id="c68fd-509">Test that the Scene setup is properly implemented.</span></span>

<span data-ttu-id="c68fd-510">Asegúrate de lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="c68fd-510">Ensure that:</span></span>

-   <span data-ttu-id="c68fd-511">Todos los scripts están conectados a la **cámara principal** objeto.</span><span class="sxs-lookup"><span data-stu-id="c68fd-511">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="c68fd-512">Todos los campos de la *Panel de Inspector de cámara principal* se asignan correctamente.</span><span class="sxs-lookup"><span data-stu-id="c68fd-512">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>

1.  <span data-ttu-id="c68fd-513">Presione el **reproducir** situado en la *Editor de Unity*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-513">Press the **Play** button in the *Unity Editor*.</span></span> <span data-ttu-id="c68fd-514">La aplicación debe estar ejecutándose dentro de los auriculares envolventes adjunto.</span><span class="sxs-lookup"><span data-stu-id="c68fd-514">The App should be running within the attached immersive headset.</span></span>

2.  <span data-ttu-id="c68fd-515">Pruebe algunas declaraciones, como:</span><span class="sxs-lookup"><span data-stu-id="c68fd-515">Try a few utterances, such as:</span></span>

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > <span data-ttu-id="c68fd-516">Si ve un error en la consola de Unity sobre el dispositivo de audio predeterminado cambia, la escena podría no funcionar según lo previsto.</span><span class="sxs-lookup"><span data-stu-id="c68fd-516">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="c68fd-517">Esto es debido al modo en que el portal de realidad mixta se ocupa de los micrófonos integrados para auriculares que disponen de ella.</span><span class="sxs-lookup"><span data-stu-id="c68fd-517">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="c68fd-518">Si ve este error, basta con detener la escena y vuelva a iniciarlo y todo debería funcionar como se esperaba.</span><span class="sxs-lookup"><span data-stu-id="c68fd-518">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a><span data-ttu-id="c68fd-519">Capítulo 11: generar y transferir localmente la solución de UWP</span><span class="sxs-lookup"><span data-stu-id="c68fd-519">Chapter 11 – Build and sideload the UWP Solution</span></span>

<span data-ttu-id="c68fd-520">Una vez que se ha asegurado de que la aplicación funciona en el Editor de Unity, está listo para compilar e implementar.</span><span class="sxs-lookup"><span data-stu-id="c68fd-520">Once you have ensured that the application is working in the Unity Editor, you are ready to Build and Deploy.</span></span>

<span data-ttu-id="c68fd-521">Para compilar:</span><span class="sxs-lookup"><span data-stu-id="c68fd-521">To Build:</span></span>

1.  <span data-ttu-id="c68fd-522">Guarde la escena actual haciendo clic en **archivo > Guardar**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-522">Save the current scene by clicking on **File > Save**.</span></span>
2.  <span data-ttu-id="c68fd-523">Vaya a **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-523">Go to **File > Build Settings**.</span></span>
3.  <span data-ttu-id="c68fd-524">Marque la casilla llamada **Unity C# proyectos** (útil para ver y depurar el código una vez creado el proyecto de UWP.</span><span class="sxs-lookup"><span data-stu-id="c68fd-524">Tick the box called **Unity C# Projects** (useful for seeing and debugging your code once the UWP project is created.</span></span>
4.  <span data-ttu-id="c68fd-525">Haga clic en **agregar escenas abierto**, a continuación, haga clic en **compilar**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-525">Click on **Add Open Scenes**, then click **Build**.</span></span>

    ![Ventana de configuración de la compilación](images/AzureLabs-Lab3-43.png)

4.  <span data-ttu-id="c68fd-527">Se le pedirá que seleccione la carpeta donde desea compilar la solución.</span><span class="sxs-lookup"><span data-stu-id="c68fd-527">You will be prompted to select the folder where you want to build the Solution.</span></span> 

5.  <span data-ttu-id="c68fd-528">Crear un *compilaciones* carpeta y dentro de esa carpeta, cree otra carpeta con un nombre adecuado de su elección.</span><span class="sxs-lookup"><span data-stu-id="c68fd-528">Create a *BUILDS* folder and within that folder create another folder with an appropriate name of your choice.</span></span> 
6.  <span data-ttu-id="c68fd-529">Haga clic en **Seleccionar carpeta** para iniciar la compilación en esa ubicación.</span><span class="sxs-lookup"><span data-stu-id="c68fd-529">Click **Select Folder** to begin the build at that location.</span></span>
 
    <span data-ttu-id="c68fd-530">![Crear carpeta compilaciones](images/AzureLabs-Lab3-44.png)
    ![Seleccionar carpeta de compilaciones](images/AzureLabs-Lab3-45.png)</span><span class="sxs-lookup"><span data-stu-id="c68fd-530">![Create Builds Folder](images/AzureLabs-Lab3-44.png)
![Select Builds Folder](images/AzureLabs-Lab3-45.png)</span></span>
 
7.  <span data-ttu-id="c68fd-531">Una vez Unity ha finalizado la compilación (puede tardar algún tiempo), debería abrir un **Explorador de archivos** ventana en la ubicación de la compilación.</span><span class="sxs-lookup"><span data-stu-id="c68fd-531">Once Unity has finished building (it might take some time), it should open a **File Explorer** window at the location of your build.</span></span>

<span data-ttu-id="c68fd-532">Para implementar en el equipo Local:</span><span class="sxs-lookup"><span data-stu-id="c68fd-532">To Deploy on Local Machine:</span></span>

1.  <span data-ttu-id="c68fd-533">En *Visual Studio*, abra el archivo de solución que se ha creado en el [capítulo anterior](#chapter-10--test-in-the-unity-editor).</span><span class="sxs-lookup"><span data-stu-id="c68fd-533">In *Visual Studio*, open the solution file that has been created in the [previous Chapter](#chapter-10--test-in-the-unity-editor).</span></span>
2.  <span data-ttu-id="c68fd-534">En el **plataforma de solución**, seleccione **x86**, **máquina Local**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-534">In the **Solution Platform**, select **x86**, **Local Machine**.</span></span>
3.  <span data-ttu-id="c68fd-535">En el **configuración de la solución** seleccione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-535">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="c68fd-536">Para el Microsoft HoloLens, quizá le resulte más fácil establecer esto en *máquina remota*, de modo que no están atados a su equipo.</span><span class="sxs-lookup"><span data-stu-id="c68fd-536">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="c68fd-537">Sin embargo, necesitará también hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="c68fd-537">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="c68fd-538">Conocer el **dirección IP** de su HoloLens, que se encuentra dentro de la *configuración > red e Internet > Wi-Fi > Opciones avanzadas*; IPv4 es la dirección que debe usar.</span><span class="sxs-lookup"><span data-stu-id="c68fd-538">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="c68fd-539">Asegúrese de **modo de programador** es **en**; se encuentra en *configuración > actualización y seguridad > para los desarrolladores*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-539">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Implementación de aplicación](images/AzureLabs-Lab3-46.png)
 
4.  <span data-ttu-id="c68fd-541">Vaya a la **menú compilar** y haga clic en **implementar solución** para transferir localmente la aplicación en el equipo.</span><span class="sxs-lookup"><span data-stu-id="c68fd-541">Go to the **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>
5.  <span data-ttu-id="c68fd-542">La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas, listos para iniciarse.</span><span class="sxs-lookup"><span data-stu-id="c68fd-542">Your App should now appear in the list of installed apps, ready to be launched!</span></span>
6.  <span data-ttu-id="c68fd-543">Una vez iniciado, la aplicación le pedirá que autorice el acceso a la _micrófono_.</span><span class="sxs-lookup"><span data-stu-id="c68fd-543">Once launched, the App will prompt you to authorize access to the _Microphone_.</span></span> <span data-ttu-id="c68fd-544">Use la *controladores de movimiento*, o *entrada de voz*, o el *teclado* presionar el **Sí** botón.</span><span class="sxs-lookup"><span data-stu-id="c68fd-544">Use the *Motion Controllers*, or *Voice Input*, or the *Keyboard* to press the **YES** button.</span></span> 

## <a name="chapter-12--improving-your-luis-service"></a><span data-ttu-id="c68fd-545">Capítulo 12: mejorar el servicio LUIS</span><span class="sxs-lookup"><span data-stu-id="c68fd-545">Chapter 12 – Improving your LUIS service</span></span>

>[!IMPORTANT] 
> <span data-ttu-id="c68fd-546">Este capítulo es muy importante y es posible que deba realizar una tras varias veces, le ayudará a mejorar la precisión del servicio LUIS: asegúrese de completar esta.</span><span class="sxs-lookup"><span data-stu-id="c68fd-546">This chapter is incredibly important, and may need to be interated upon several times, as it will help improve the accuracy of your LUIS service: ensure you complete this.</span></span>

<span data-ttu-id="c68fd-547">Para mejorar el grado de conocimiento proporciona LUIS deberá capturar grabaciones de voz nueva y usarlos para volver a entrenar su App LUIS.</span><span class="sxs-lookup"><span data-stu-id="c68fd-547">To improve the level of understanding provided by LUIS you need to capture new utterances and use them to re-train your LUIS App.</span></span>

<span data-ttu-id="c68fd-548">Por ejemplo, es posible que haya entrenado LUIS a comprender "Aumentar" y "Convertir", pero no quiere que su aplicación para poder comprender también palabras como "Ampliar"?</span><span class="sxs-lookup"><span data-stu-id="c68fd-548">For example, you might have trained LUIS to understand “Increase” and “Upsize”, but wouldn’t you want your app to also understand words like “Enlarge”?</span></span>

<span data-ttu-id="c68fd-549">Una vez que ha usado la aplicación varias veces, todo lo que dicen será recopilados Luis y está disponible en el PORTAL de LUIS.</span><span class="sxs-lookup"><span data-stu-id="c68fd-549">Once you have used your application a few times, everything you have said will be collected by LUIS and available in the LUIS PORTAL.</span></span>

1.  <span data-ttu-id="c68fd-550">Vaya a la aplicación de portal siguiente esto [vínculo](https://www.luis.ai/home)y en el registro.</span><span class="sxs-lookup"><span data-stu-id="c68fd-550">Go to your portal application following this [LINK](https://www.luis.ai/home), and Log In.</span></span>
2.  <span data-ttu-id="c68fd-551">Una vez haya iniciado sesión con sus Credentials MS, haga clic en su *nombre de la aplicación*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-551">Once you are logged in with your MS Credentials, click on your *App name*.</span></span>
3.  <span data-ttu-id="c68fd-552">Haga clic en el **revisar grabaciones de voz de punto de conexión** botón a la izquierda de la página.</span><span class="sxs-lookup"><span data-stu-id="c68fd-552">Click the **Review endpoint utterances** button on the left of the page.</span></span>

    ![Revisar grabaciones de voz](images/AzureLabs-Lab3-47.png)
 
4.  <span data-ttu-id="c68fd-554">Se mostrará una lista de las palabras pronunciadas que se han enviado a LUIS por su aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="c68fd-554">You will be shown a list of the Utterances that have been sent to LUIS by your mixed reality Application.</span></span>

    ![Lista de declaraciones](images/AzureLabs-Lab3-48.png)
 
<span data-ttu-id="c68fd-556">Observará algunos resaltado *entidades*.</span><span class="sxs-lookup"><span data-stu-id="c68fd-556">You will notice some highlighted *Entities*.</span></span> 

<span data-ttu-id="c68fd-557">Mantenga el puntero sobre cada palabra resaltada, puede revisar las declaraciones y determinar qué entidad ha sido reconocida correctamente, lo que las entidades son erróneas y cuáles se pierden las entidades.</span><span class="sxs-lookup"><span data-stu-id="c68fd-557">By hovering over each highlighted word, you can review each Utterance and determine which Entity has been recognized correctly, which Entities are wrong and which Entities are missed.</span></span>

<span data-ttu-id="c68fd-558">En el ejemplo anterior, se encontró que la palabra "spear" tenía ha resaltado como destino, por lo tanto, es necesario corregir el error, que se realiza mediante el mouse sobre la palabra con el mouse y haga clic en **Quitar etiqueta**.</span><span class="sxs-lookup"><span data-stu-id="c68fd-558">In the example above, it was found that the word “spear” had been highlighted as a target, so it necessary to correct the mistake, which is done by hovering over the word with the mouse and clicking **Remove Label**.</span></span>

<span data-ttu-id="c68fd-559">![Compruebe las grabaciones de voz](images/AzureLabs-Lab3-49.png)
![Quitar etiqueta de imagen](images/AzureLabs-Lab3-50.png)</span><span class="sxs-lookup"><span data-stu-id="c68fd-559">![Check utterances](images/AzureLabs-Lab3-49.png)
![Remove Label Image](images/AzureLabs-Lab3-50.png)</span></span>
 
5.  <span data-ttu-id="c68fd-560">Si encuentra declaraciones que están completamente equivocados, puede eliminarlos mediante la **eliminar** situado a la derecha de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="c68fd-560">If you find Utterances that are completely wrong, you can delete them using the **Delete** button on the right side of the screen.</span></span>

    ![Eliminar grabaciones de voz incorrectos](images/AzureLabs-Lab3-51.png)

6.  <span data-ttu-id="c68fd-562">O si se siente que LUIS interpreta correctamente la declaración, puede validar su descripción mediante el **agregar a la intención alineado** botón.</span><span class="sxs-lookup"><span data-stu-id="c68fd-562">Or if you feel that LUIS has interpreted the Utterance correctly, you can validate its understanding by using the **Add To Aligned Intent** button.</span></span>

    ![Agregar a la intención alineada](images/AzureLabs-Lab3-52.png)

7.  <span data-ttu-id="c68fd-564">Una vez que haya ordenado todas las palabras pronunciadas mostradas, pruebe y vuelva a cargar la página para ver si hay disponibles más.</span><span class="sxs-lookup"><span data-stu-id="c68fd-564">Once you have sorted all the displayed Utterances, try and reload the page to see if more are available.</span></span>
8.  <span data-ttu-id="c68fd-565">Es muy importante que repetir este proceso tantas veces como sea posible mejorar la comprensión de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c68fd-565">It is very important to repeat this process as many times as possible to improve your application understanding.</span></span> 

<span data-ttu-id="c68fd-566">**¡Que te diviertas!**</span><span class="sxs-lookup"><span data-stu-id="c68fd-566">**Have fun!**</span></span>

## <a name="your-finished-luis-integrated-application"></a><span data-ttu-id="c68fd-567">La aplicación LUIS integrado finalizada</span><span class="sxs-lookup"><span data-stu-id="c68fd-567">Your finished LUIS Integrated application</span></span>

<span data-ttu-id="c68fd-568">Enhorabuena, compila una aplicación de realidad mixta que aprovecha Azure Language Understanding Intelligence Service, para entender lo que dice un usuario y actuar en esa información.</span><span class="sxs-lookup"><span data-stu-id="c68fd-568">Congratulations, you built a mixed reality app that leverages the Azure Language Understanding Intelligence Service, to understand what a user says, and act on that information.</span></span>

![Resultado de laboratorio](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="c68fd-570">Ejercicios de bonificación</span><span class="sxs-lookup"><span data-stu-id="c68fd-570">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="c68fd-571">Ejercicio 1</span><span class="sxs-lookup"><span data-stu-id="c68fd-571">Exercise 1</span></span>

<span data-ttu-id="c68fd-572">Al usar esta aplicación, puede que observe que si mire el objeto Floor y pida que cambie su color, lo hará.</span><span class="sxs-lookup"><span data-stu-id="c68fd-572">While using this application you might notice that if you gaze at the Floor object and ask to change its color, it will do so.</span></span> <span data-ttu-id="c68fd-573">¿Puede averiguar cómo detener la aplicación si cambia el color de suelo?</span><span class="sxs-lookup"><span data-stu-id="c68fd-573">Can you work out how to stop your application from changing the Floor color?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="c68fd-574">Ejercicio 2</span><span class="sxs-lookup"><span data-stu-id="c68fd-574">Exercise 2</span></span>

<span data-ttu-id="c68fd-575">Intentar extender las capacidades de LUIS y aplicación, agregar funcionalidad adicional para los objetos en la escena; Por ejemplo, crear nuevos objetos en la mirada punto de posicionamiento, dependiendo de cuál es el usuario dice y, a continuación, podrá usar esos objetos junto con los objetos de escena actual, con los comandos existentes.</span><span class="sxs-lookup"><span data-stu-id="c68fd-575">Try extending the LUIS and App capabilities, adding additional functionality for objects in scene; as an example, create new objects at the Gaze hit point, depending on what the user says, and then be able to use those objects alongside current scene objects, with the existing commands.</span></span> 
