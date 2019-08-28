---
title: MR y Azure 302-Computer Vision
description: Complete este curso para aprender a reconocer contenido visual dentro de una imagen proporcionada, con Azure Computer Vision en una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, tutorial, API, Computer Vision, hololens, envolventes, VR
ms.openlocfilehash: 9cc526afdc36b8056afd61948fea5cf98015bb35
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047194"
---
>[!NOTE]
><span data-ttu-id="ea360-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="ea360-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="ea360-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="ea360-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="ea360-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ea360-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="ea360-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="ea360-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="ea360-108">Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ea360-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="ea360-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.</span><span class="sxs-lookup"><span data-stu-id="ea360-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302-computer-vision"></a><span data-ttu-id="ea360-110">MR y Azure 302: Computer Vision</span><span class="sxs-lookup"><span data-stu-id="ea360-110">MR and Azure 302: Computer vision</span></span>

<span data-ttu-id="ea360-111">En este curso, aprenderá a reconocer el contenido visual dentro de una imagen proporcionada, con las funcionalidades de Azure Computer Vision en una aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="ea360-111">In this course, you will learn how to recognize visual content within a provided image, using Azure Computer Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="ea360-112">Los resultados del reconocimiento se mostrarán como etiquetas descriptivas.</span><span class="sxs-lookup"><span data-stu-id="ea360-112">Recognition results will be displayed as descriptive tags.</span></span> <span data-ttu-id="ea360-113">Puede usar este servicio sin necesidad de entrenar un modelo de aprendizaje automático.</span><span class="sxs-lookup"><span data-stu-id="ea360-113">You can use this service without needing to train a machine learning model.</span></span> <span data-ttu-id="ea360-114">Si su implementación requiere entrenar un modelo de aprendizaje automático, consulte [Mr y Azure 302B](mr-azure-302b.md).</span><span class="sxs-lookup"><span data-stu-id="ea360-114">If your implementation requires training a machine learning model, see [MR and Azure 302b](mr-azure-302b.md).</span></span>

![resultado de laboratorio](images/AzureLabs-Lab2-000.png)

<span data-ttu-id="ea360-116">Microsoft Computer Vision es un conjunto de API diseñadas para ofrecer a los desarrolladores el procesamiento y el análisis de imágenes (con información de retorno), mediante algoritmos avanzados, todo desde la nube.</span><span class="sxs-lookup"><span data-stu-id="ea360-116">The Microsoft Computer Vision is a set of APIs designed to provide developers with image processing and analysis (with return information), using advanced algorithms, all from the cloud.</span></span> <span data-ttu-id="ea360-117">Los desarrolladores cargan una imagen o una dirección URL de imagen, y los algoritmos de Microsoft Computer Vision API analizan el contenido visual, en función de las entradas elegidas para el usuario, que pueden devolver información, incluido, identificar el tipo y la calidad de una imagen, detectar caras humanas ( devolver sus coordenadas) y etiquetar o clasificar las imágenes.</span><span class="sxs-lookup"><span data-stu-id="ea360-117">Developers upload an image or image URL, and the Microsoft Computer Vision API algorithms analyze the visual content, based upon inputs chosen the user, which then can return information, including, identifying the type and quality of an image, detect human faces (returning their coordinates), and tagging, or categorizing images.</span></span> <span data-ttu-id="ea360-118">Para obtener más información, visite la [Página de Computer Vision API de Azure](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span><span class="sxs-lookup"><span data-stu-id="ea360-118">For more information, visit the [Azure Computer Vision API page](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span></span>

<span data-ttu-id="ea360-119">Una vez completado este curso, tendrá una aplicación de realidad HoloLens mixta, que podrá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="ea360-119">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="ea360-120">Con el gesto de TAP, la cámara de HoloLens capturará una imagen.</span><span class="sxs-lookup"><span data-stu-id="ea360-120">Using the Tap gesture, the camera of the HoloLens will capture an image.</span></span>
2.  <span data-ttu-id="ea360-121">La imagen se enviará al servicio Azure Computer Vision API.</span><span class="sxs-lookup"><span data-stu-id="ea360-121">The image will be sent to the Azure Computer Vision API Service.</span></span> 
3.  <span data-ttu-id="ea360-122">Los objetos reconocidos se enumerarán en un grupo de interfaz de usuario simple situado en la escena de Unity.</span><span class="sxs-lookup"><span data-stu-id="ea360-122">The objects recognized will be listed in a simple UI group positioned in the Unity Scene.</span></span>

<span data-ttu-id="ea360-123">En su aplicación, depende del modo en que va a integrar los resultados con el diseño.</span><span class="sxs-lookup"><span data-stu-id="ea360-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="ea360-124">Este curso está diseñado para enseñarle a integrar un servicio de Azure con su proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="ea360-124">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="ea360-125">Es su trabajo usar el conocimiento que obtiene de este curso para mejorar su aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="ea360-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="ea360-126">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="ea360-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="ea360-127">Recurso</span><span class="sxs-lookup"><span data-stu-id="ea360-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="ea360-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ea360-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ea360-129"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="ea360-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="ea360-130">MR y Azure 302: Computer Vision</span><span class="sxs-lookup"><span data-stu-id="ea360-130">MR and Azure 302: Computer vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="ea360-131">✔️</span><span class="sxs-lookup"><span data-stu-id="ea360-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="ea360-132">✔️</span><span class="sxs-lookup"><span data-stu-id="ea360-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="ea360-133">Aunque este curso se centra principalmente en HoloLens, también puede aplicar lo que aprenda en este curso a los auriculares con Windows Mixed Reality inmersivo (VR).</span><span class="sxs-lookup"><span data-stu-id="ea360-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="ea360-134">Dado que los auriculares envolventes (VR) no tienen cámaras accesibles, necesitará una cámara externa conectada al equipo.</span><span class="sxs-lookup"><span data-stu-id="ea360-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="ea360-135">A medida que siga con el curso, verá notas sobre cualquier cambio que deba usar para admitir auriculares envolventes (VR).</span><span class="sxs-lookup"><span data-stu-id="ea360-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ea360-136">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="ea360-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="ea360-137">Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#.</span><span class="sxs-lookup"><span data-stu-id="ea360-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="ea360-138">Tenga en cuenta también que los requisitos previos y las instrucciones escritas dentro de este documento representan lo que se ha probado y comprobado en el momento de la escritura (2018 de mayo).</span><span class="sxs-lookup"><span data-stu-id="ea360-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="ea360-139">Puede usar el software más reciente, como se indica en el artículo [instalar las herramientas](install-the-tools.md) , aunque no se debe suponer que la información de este curso se ajusta perfectamente a lo que encontrará en el software más reciente que el que se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="ea360-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="ea360-140">Se recomienda el siguiente hardware y software para este curso:</span><span class="sxs-lookup"><span data-stu-id="ea360-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="ea360-141">Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de auriculares envolvente (VR)</span><span class="sxs-lookup"><span data-stu-id="ea360-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="ea360-142">Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="ea360-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ea360-143">El SDK de Windows 10 más reciente</span><span class="sxs-lookup"><span data-stu-id="ea360-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ea360-144">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="ea360-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ea360-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ea360-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="ea360-146">Un [auricular de Windows Mixed Reality inmersivo (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="ea360-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="ea360-147">Una cámara conectada al equipo (para el desarrollo de auriculares envolvente)</span><span class="sxs-lookup"><span data-stu-id="ea360-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="ea360-148">Acceso a Internet para la configuración y recuperación de Computer Vision API de Azure</span><span class="sxs-lookup"><span data-stu-id="ea360-148">Internet access for Azure setup and Computer Vision API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="ea360-149">Antes de comenzar</span><span class="sxs-lookup"><span data-stu-id="ea360-149">Before you start</span></span>

1.  <span data-ttu-id="ea360-150">Para evitar que se produzcan problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cerca de la raíz (las rutas de acceso de carpeta largas pueden producir problemas en tiempo de compilación).</span><span class="sxs-lookup"><span data-stu-id="ea360-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="ea360-151">Configure y pruebe su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ea360-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="ea360-152">Si necesita ayuda para configurar HoloLens, asegúrese [de visitar el artículo de configuración de hololens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="ea360-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="ea360-153">Es una buena idea realizar la calibración y el ajuste del sensor al empezar a desarrollar una nueva aplicación de HoloLens (a veces puede ayudar a realizar esas tareas para cada usuario).</span><span class="sxs-lookup"><span data-stu-id="ea360-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="ea360-154">Para obtener ayuda sobre la calibración, siga este [vínculo al artículo sobre la calibración de HoloLens](calibration.md#hololens-2).</span><span class="sxs-lookup"><span data-stu-id="ea360-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="ea360-155">Para obtener ayuda sobre la optimización de sensores, siga este [vínculo al artículo sobre la optimización del sensor de HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="ea360-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="ea360-156">Capítulo 1: Azure portal</span><span class="sxs-lookup"><span data-stu-id="ea360-156">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="ea360-157">Para usar el servicio de *Computer Vision API* en Azure, tendrá que configurar una instancia del servicio para que esté disponible para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ea360-157">To use the *Computer Vision API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="ea360-158">En primer lugar, inicie sesión en [Azure portal](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="ea360-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="ea360-159">Si aún no tiene una cuenta de Azure, tendrá que crear una.</span><span class="sxs-lookup"><span data-stu-id="ea360-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="ea360-160">Si sigue este tutorial en una situación de aula o de laboratorio, pregunte al instructor o a uno de los Proctors para obtener ayuda para configurar la nueva cuenta.</span><span class="sxs-lookup"><span data-stu-id="ea360-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="ea360-161">Una vez que haya iniciado sesión, haga clic en **nuevo** en la esquina superior izquierda y busque *Computer Vision API*y haga clic en **entrar**.</span><span class="sxs-lookup"><span data-stu-id="ea360-161">Once you are logged in, click on **New** in the top left corner, and search for *Computer Vision API*, and click **Enter**.</span></span>

    ![Creación de un nuevo recurso en Azure](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > <span data-ttu-id="ea360-163">Es posible que la palabra **nuevo** se haya reemplazado por **crear un recurso**, en portales más recientes.</span><span class="sxs-lookup"><span data-stu-id="ea360-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="ea360-164">La nueva página proporcionará una descripción del servicio *Computer Vision API* .</span><span class="sxs-lookup"><span data-stu-id="ea360-164">The new page will provide a description of the *Computer Vision API* service.</span></span> <span data-ttu-id="ea360-165">En la parte inferior izquierda de esta página, seleccione el botón **crear** para crear una asociación con este servicio.</span><span class="sxs-lookup"><span data-stu-id="ea360-165">At the bottom left of this page, select the **Create** button, to create an association with this service.</span></span>

    ![Acerca del servicio Computer Vision API](images/AzureLabs-Lab2-01.png)
 
4.  <span data-ttu-id="ea360-167">Una vez que haya hecho clic en **crear**:</span><span class="sxs-lookup"><span data-stu-id="ea360-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="ea360-168">Inserte el **nombre** que desee para esta instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="ea360-168">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="ea360-169">Seleccione una **suscripción**.</span><span class="sxs-lookup"><span data-stu-id="ea360-169">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="ea360-170">Seleccione el **plan de tarifa** adecuado para usted; si es la primera vez que crea un servicio de *Computer Vision API* , debe tener a su disposición un nivel gratis (denominado F0).</span><span class="sxs-lookup"><span data-stu-id="ea360-170">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Computer Vision API* Service, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="ea360-171">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="ea360-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="ea360-172">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="ea360-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="ea360-173">Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común).</span><span class="sxs-lookup"><span data-stu-id="ea360-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="ea360-174">Si desea leer más información sobre los grupos de recursos de Azure, [visite el artículo sobre el grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="ea360-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="ea360-175">Determine la ubicación del grupo de recursos (si va a crear un nuevo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="ea360-175">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="ea360-176">Idealmente, la ubicación estará en la región donde se ejecutará la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ea360-176">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="ea360-177">Algunos recursos de Azure solo están disponibles en determinadas regiones.</span><span class="sxs-lookup"><span data-stu-id="ea360-177">Some Azure assets are only available in certain regions.</span></span>

    6. <span data-ttu-id="ea360-178">También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.</span><span class="sxs-lookup"><span data-stu-id="ea360-178">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="ea360-179">Haga clic en crear.</span><span class="sxs-lookup"><span data-stu-id="ea360-179">Click Create.</span></span>

        ![Información de creación del servicio](images/AzureLabs-Lab2-02.png)

5.  <span data-ttu-id="ea360-181">Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="ea360-181">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="ea360-182">Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="ea360-182">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Vea la nueva notificación del nuevo servicio](images/AzureLabs-Lab2-03.png) 
 
7.  <span data-ttu-id="ea360-184">Haga clic en la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="ea360-184">Click on the notification to explore your new Service instance.</span></span> 

    ![Seleccione el botón ir a recurso.](images/AzureLabs-Lab2-04.png)
 
8. <span data-ttu-id="ea360-186">Haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="ea360-186">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="ea360-187">Se le dirigirá a la nueva instancia de servicio de Computer Vision API.</span><span class="sxs-lookup"><span data-stu-id="ea360-187">You will be taken to your new Computer Vision API service instance.</span></span> 

    ![El nuevo servicio de Computer Vision API](images/AzureLabs-Lab2-05.png)
 
9.  <span data-ttu-id="ea360-189">En este tutorial, la aplicación necesitará realizar llamadas al servicio, lo que se realiza mediante el uso de la clave de suscripción del servicio.</span><span class="sxs-lookup"><span data-stu-id="ea360-189">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="ea360-190">En la página *Inicio rápido* , del servicio de *Computer Vision API* , navegue hasta el primer paso, *grabe sus claves*y haga clic en **claves** (también puede conseguirlo haciendo clic en las teclas de hipervínculo azul, que se encuentran en el menú de navegación servicios. indicado por el icono de clave).</span><span class="sxs-lookup"><span data-stu-id="ea360-190">From the *Quick start* page, of your *Computer Vision API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="ea360-191">Esto revelará las *claves*de servicio.</span><span class="sxs-lookup"><span data-stu-id="ea360-191">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="ea360-192">Realice una copia de una de las claves que se muestran, ya que la necesitará más adelante en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="ea360-192">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

12. <span data-ttu-id="ea360-193">Vuelva a la página *Inicio rápido* y, desde ahí, recupere el punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="ea360-193">Go back to the *Quick start* page, and from there, fetch your endpoint.</span></span> <span data-ttu-id="ea360-194">Tenga en cuenta que el suyo puede ser diferente, en función de su región (que, si es así, deberá realizar un cambio en el código más adelante).</span><span class="sxs-lookup"><span data-stu-id="ea360-194">Be aware yours may be different, depending on your region (which if it is, you will need to make a change to your code later).</span></span> <span data-ttu-id="ea360-195">Realice una copia de este punto de conexión para usarlo más adelante:</span><span class="sxs-lookup"><span data-stu-id="ea360-195">Take a copy of this endpoint for use later:</span></span>

    ![El nuevo servicio de Computer Vision API](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > <span data-ttu-id="ea360-197">Puede comprobar los distintos puntos de conexión [aquí](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span><span class="sxs-lookup"><span data-stu-id="ea360-197">You can check what the various endpoints are [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="ea360-198">Capítulo 2: configurar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="ea360-198">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="ea360-199">Lo siguiente es una configuración típica para desarrollar con la realidad mixta y, como tal, es una buena plantilla para otros proyectos.</span><span class="sxs-lookup"><span data-stu-id="ea360-199">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="ea360-200">Abra *Unity* y haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="ea360-200">Open *Unity* and click **New**.</span></span> 

    ![Inicie el nuevo proyecto de Unity.](images/AzureLabs-Lab2-06.png)

2.  <span data-ttu-id="ea360-202">Ahora tendrá que proporcionar un nombre de proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="ea360-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="ea360-203">Inserte **MR_ComputerVision**.</span><span class="sxs-lookup"><span data-stu-id="ea360-203">Insert **MR_ComputerVision**.</span></span> <span data-ttu-id="ea360-204">Asegúrese de que el tipo de proyecto está establecido en **3D**.</span><span class="sxs-lookup"><span data-stu-id="ea360-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="ea360-205">Establezca la **Ubicación** en algún lugar adecuado para usted (Recuerde que, más cerca de los directorios raíz es mejor).</span><span class="sxs-lookup"><span data-stu-id="ea360-205">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="ea360-206">A continuación, haga clic en **crear proyecto**.</span><span class="sxs-lookup"><span data-stu-id="ea360-206">Then, click **Create project**.</span></span>

    ![Proporcione los detalles del nuevo proyecto de Unity.](images/AzureLabs-Lab2-07.png)

3.  <span data-ttu-id="ea360-208">Con Unity abierto, merece la pena comprobar que el **Editor** de scripts predeterminado está establecido en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="ea360-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="ea360-209">Vaya a **editar > preferencias** y, a continuación, en la nueva ventana, vaya a **herramientas externas**.</span><span class="sxs-lookup"><span data-stu-id="ea360-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="ea360-210">Cambie el **Editor de script externo** a **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="ea360-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="ea360-211">Cierre la ventana **preferencias** .</span><span class="sxs-lookup"><span data-stu-id="ea360-211">Close the **Preferences** window.</span></span>

    ![Actualice las preferencias del editor de scripts.](images/AzureLabs-Lab2-08.png)

4.  <span data-ttu-id="ea360-213">A continuación, vaya a **archivo > configuración de compilación** y seleccione **plataforma universal de Windows**y, después, haga clic en el botón **cambiar plataforma** para aplicar la selección.</span><span class="sxs-lookup"><span data-stu-id="ea360-213">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Ventana Configuración de compilación, cambiar plataforma a UWP.](images/AzureLabs-Lab2-10.png)

5.  <span data-ttu-id="ea360-215">Mientras sigue en el **archivo > la configuración de compilación** y asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="ea360-215">While still in **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="ea360-216">El **dispositivo de destino** está establecido en **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="ea360-216">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="ea360-217">Para los auriculares envolventes, establezca el **dispositivo de destino** en *cualquier dispositivo*.</span><span class="sxs-lookup"><span data-stu-id="ea360-217">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="ea360-218">El **tipo de compilación** se establece en **D3D**</span><span class="sxs-lookup"><span data-stu-id="ea360-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="ea360-219">**SDK** está establecido en la **versión más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="ea360-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="ea360-220">La **versión de Visual Studio** está establecida en la **más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="ea360-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="ea360-221">**Compilar y ejecutar** está establecido en **equipo local**</span><span class="sxs-lookup"><span data-stu-id="ea360-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="ea360-222">Guarde la escena y agréguela a la compilación.</span><span class="sxs-lookup"><span data-stu-id="ea360-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="ea360-223">Para ello, seleccione **Agregar escenas abiertas**.</span><span class="sxs-lookup"><span data-stu-id="ea360-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="ea360-224">Aparecerá una ventana de guardar.</span><span class="sxs-lookup"><span data-stu-id="ea360-224">A save window will appear.</span></span>
        
            ![Haga clic en el botón Agregar escenas abiertas](images/AzureLabs-Lab2-11.png)

        2. <span data-ttu-id="ea360-226">Cree una nueva carpeta para este, y en cualquier momento, en el futuro, seleccione el botón **nueva carpeta** para crear una nueva carpeta, asígneleel nombre Scenes.</span><span class="sxs-lookup"><span data-stu-id="ea360-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Crear nueva carpeta de scripts](images/AzureLabs-Lab2-12.png)

        3. <span data-ttu-id="ea360-228">Abra la carpeta Scenes recién creada y, a continuación, en el campo *nombre de archivo*:, escriba **MR_ComputerVisionScene**y haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="ea360-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![Asigne un nombre a la nueva escena.](images/AzureLabs-Lab2-13.png)

            > <span data-ttu-id="ea360-230">Tenga en cuenta que debe guardar las escenas de Unity dentro de la carpeta *assets* , ya que deben estar asociadas con el proyecto Unity.</span><span class="sxs-lookup"><span data-stu-id="ea360-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="ea360-231">La creación de la carpeta Scenes (y otras carpetas similares) es una forma habitual de estructurar un proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="ea360-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="ea360-232">El resto de la configuración, en la *configuración de compilación*, debe dejarse como predeterminada por ahora.</span><span class="sxs-lookup"><span data-stu-id="ea360-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="ea360-233">En la ventana *configuración de compilación* , haga clic en el botón Configuración del **reproductor** ; se abrirá el panel relacionado en el espacio donde se encuentra el *Inspector* .</span><span class="sxs-lookup"><span data-stu-id="ea360-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Abra configuración del reproductor.](images/AzureLabs-Lab2-14.png)

7. <span data-ttu-id="ea360-235">En este panel, deben comprobarse algunas opciones de configuración:</span><span class="sxs-lookup"><span data-stu-id="ea360-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="ea360-236">En la pestaña **otros valores** :</span><span class="sxs-lookup"><span data-stu-id="ea360-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="ea360-237">La **versión de scripting en tiempo de ejecución** debe ser **estable** (.net 3,5 equivalente).</span><span class="sxs-lookup"><span data-stu-id="ea360-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="ea360-238">El **back-end** de scripting debe ser **.net**</span><span class="sxs-lookup"><span data-stu-id="ea360-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="ea360-239">El **nivel de compatibilidad de API** debe ser **.net 4,6**</span><span class="sxs-lookup"><span data-stu-id="ea360-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Actualice otras opciones de configuración.](images/AzureLabs-Lab2-15.png)
      
    2. <span data-ttu-id="ea360-241">En la pestaña **configuración de publicación** , en **capacidades**, seleccione:</span><span class="sxs-lookup"><span data-stu-id="ea360-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="ea360-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="ea360-242">**InternetClient**</span></span>
        2. <span data-ttu-id="ea360-243">**Web**</span><span class="sxs-lookup"><span data-stu-id="ea360-243">**Webcam**</span></span>

            ![Actualizando la configuración de publicación.](images/AzureLabs-Lab2-16.png)

    3. <span data-ttu-id="ea360-245">Más abajo en el panel, en la **configuración de XR** (se encuentra debajo de **configuración de publicación**), tick **Virtual Reality compatible**, asegúrese de que se agrega el **SDK de Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="ea360-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Actualice la configuración de X R.](images/AzureLabs-Lab2-17.png)

8.  <span data-ttu-id="ea360-247">De nuevo en la *configuración de compilación* , los proyectos de _Unity C#_  ya no están atenuados; Marque la casilla situada junto a este.</span><span class="sxs-lookup"><span data-stu-id="ea360-247">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="ea360-248">Cierre la ventana Configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="ea360-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="ea360-249">Guarde la escena y el proyecto (**archivo > guardar la escena o el archivo > guardar proyecto**).</span><span class="sxs-lookup"><span data-stu-id="ea360-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="ea360-250">Capítulo 3: configuración de la cámara principal</span><span class="sxs-lookup"><span data-stu-id="ea360-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ea360-251">Si desea omitir el componente *de configuración de Unity* de este curso y continuar directamente en el código, no dude en descargar este [. unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), impórtelo en el proyecto como un [paquete personalizado](https://docs.unity3d.com/Manual/AssetPackages.html)y, después, continúe con el [capítulo 5](#chapter-5--create-the-resultslabel-class).</span><span class="sxs-lookup"><span data-stu-id="ea360-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-resultslabel-class).</span></span>

1.  <span data-ttu-id="ea360-252">En el *Panel jerarquía*, seleccione la **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="ea360-252">In the *Hierarchy Panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="ea360-253">Una vez seleccionado, podrá ver todos los componentes de la **cámara principal** en el *panel del inspector*.</span><span class="sxs-lookup"><span data-stu-id="ea360-253">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="ea360-254">El **objeto de cámara** debe tener el nombre de la **cámara principal** (tenga en cuenta la ortografía).</span><span class="sxs-lookup"><span data-stu-id="ea360-254">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>
    2. <span data-ttu-id="ea360-255">La **etiqueta** de cámara principal se debe establecer en **MainCamera** (tenga en cuenta la ortografía).</span><span class="sxs-lookup"><span data-stu-id="ea360-255">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>
    3. <span data-ttu-id="ea360-256">Asegúrese de que la **posición de transformación** está establecida en **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="ea360-256">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="ea360-257">Establezca **marcas** de borrado en **color sólido** (Ignore esto para los auriculares inmersivo).</span><span class="sxs-lookup"><span data-stu-id="ea360-257">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>
    5. <span data-ttu-id="ea360-258">Establezca el color de **fondo** del componente de la cámara en **negro, alfa 0 (código hexadecimal: #00000000)** (no se tiene en cuenta para el casco inmersivo).</span><span class="sxs-lookup"><span data-stu-id="ea360-258">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

        ![Actualice los componentes de la cámara.](images/AzureLabs-Lab2-18.png)
 
3.  <span data-ttu-id="ea360-260">A continuación, tendrá que crear un objeto de "cursor" simple adjunto a la **cámara principal**, lo que le ayudará a colocar la salida del análisis de la imagen cuando la aplicación se esté ejecutando.</span><span class="sxs-lookup"><span data-stu-id="ea360-260">Next, you will have to create a simple “Cursor” object attached to the **Main Camera**, which will help you position the image analysis output when the application is running.</span></span> <span data-ttu-id="ea360-261">Este cursor determinará el punto central del foco de la cámara.</span><span class="sxs-lookup"><span data-stu-id="ea360-261">This Cursor will determine the center point of the camera focus.</span></span>

<span data-ttu-id="ea360-262">Para crear el cursor:</span><span class="sxs-lookup"><span data-stu-id="ea360-262">To create the Cursor:</span></span>

1.  <span data-ttu-id="ea360-263">En el *Panel jerarquía*, haga clic con el botón secundario en la **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="ea360-263">In the *Hierarchy Panel*, right-click on the **Main Camera**.</span></span> <span data-ttu-id="ea360-264">En **objeto 3D**, haga clic en **Sphere**.</span><span class="sxs-lookup"><span data-stu-id="ea360-264">Under **3D Object**, click on **Sphere**.</span></span>

    ![Seleccione el objeto Cursor.](images/AzureLabs-Lab2-19.png)
 
2.  <span data-ttu-id="ea360-266">Cambie el nombre de la **esfera** a **cursor** (haga doble clic en el objeto cursor o presione el botón de teclado ' F2 ' con el objeto seleccionado) y asegúrese de que se encuentra como elemento secundario de la **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="ea360-266">Rename the **Sphere** to **Cursor** (double click the Cursor object or press the ‘F2’ keyboard button with the object selected), and make sure it is located as child of the **Main Camera**.</span></span>

3.  <span data-ttu-id="ea360-267">En el *Panel jerarquía*, haga clic con el botón izquierdo en el **cursor**.</span><span class="sxs-lookup"><span data-stu-id="ea360-267">In the *Hierarchy Panel*, left click on the **Cursor**.</span></span> <span data-ttu-id="ea360-268">Con el cursor seleccionado, ajuste las siguientes variables en el *panel del inspector*:</span><span class="sxs-lookup"><span data-stu-id="ea360-268">With the Cursor selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="ea360-269">Establecer la *posición* de la transformación en **0,** 0,5</span><span class="sxs-lookup"><span data-stu-id="ea360-269">Set the *Transform Position* to **0, 0, 5**</span></span>
    2. <span data-ttu-id="ea360-270">Establezca la *escala* en **0,02, 0,02, 0,02**</span><span class="sxs-lookup"><span data-stu-id="ea360-270">Set the *Scale* to **0.02, 0.02, 0.02**</span></span>

        ![Actualice la posición y la escala de transformación.](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a><span data-ttu-id="ea360-272">Capítulo 4: configurar el sistema de etiquetas</span><span class="sxs-lookup"><span data-stu-id="ea360-272">Chapter 4 – Setup the Label system</span></span>

<span data-ttu-id="ea360-273">Una vez que haya capturado una imagen con la cámara de HoloLens, esa imagen se enviará a la instancia de servicio de *Azure Computer Vision API* para su análisis.</span><span class="sxs-lookup"><span data-stu-id="ea360-273">Once you have captured an image with the HoloLens’ camera, that image will be sent to your *Azure Computer Vision API* Service instance for analysis.</span></span> 

<span data-ttu-id="ea360-274">Los resultados de ese análisis serán una lista de objetos reconocidos denominados **etiquetas**.</span><span class="sxs-lookup"><span data-stu-id="ea360-274">The results of that analysis will be a list of recognized objects called **Tags**.</span></span> 

<span data-ttu-id="ea360-275">Usará etiquetas (como texto en 3D en el espacio universal) para mostrar estas etiquetas en la ubicación en la que se tomó la foto.</span><span class="sxs-lookup"><span data-stu-id="ea360-275">You will use Labels (as a 3D text in world space) to display these Tags at the location the photo was taken.</span></span>

<span data-ttu-id="ea360-276">En los pasos siguientes se muestra cómo configurar el objeto de **etiqueta** .</span><span class="sxs-lookup"><span data-stu-id="ea360-276">The following steps will show how to setup the **Label** object.</span></span>

1.  <span data-ttu-id="ea360-277">Haga clic con el botón secundario en cualquier lugar del panel jerarquía (la ubicación no importa en este momento), en **objeto 3D**, agregue un **texto 3D**.</span><span class="sxs-lookup"><span data-stu-id="ea360-277">Right-click anywhere in the Hierarchy Panel (the location does not matter at this point), under **3D Object**, add a **3D Text**.</span></span> <span data-ttu-id="ea360-278">Asígnele el nombre **LabelText**.</span><span class="sxs-lookup"><span data-stu-id="ea360-278">Name it **LabelText**.</span></span>

    ![Cree un objeto de texto 3D.](images/AzureLabs-Lab2-21.png)
 
2.  <span data-ttu-id="ea360-280">En el *Panel jerarquía*, haga clic con el botón izquierdo en el **LabelText**.</span><span class="sxs-lookup"><span data-stu-id="ea360-280">In the *Hierarchy Panel*, left click on the **LabelText**.</span></span> <span data-ttu-id="ea360-281">Con el **LabelText** seleccionado, ajuste las siguientes variables en el *panel del inspector*:</span><span class="sxs-lookup"><span data-stu-id="ea360-281">With the **LabelText** selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="ea360-282">Establezca la **posición** en **0, 0,0**</span><span class="sxs-lookup"><span data-stu-id="ea360-282">Set the **Position** to **0,0,0**</span></span>
    2. <span data-ttu-id="ea360-283">Establezca la **escala** en **0,01, 0,01, 0,01**</span><span class="sxs-lookup"><span data-stu-id="ea360-283">Set the **Scale** to **0.01, 0.01, 0.01**</span></span>
    3. <span data-ttu-id="ea360-284">En la **malla de texto**del componente:</span><span class="sxs-lookup"><span data-stu-id="ea360-284">In the component **Text Mesh**:</span></span>
    4. <span data-ttu-id="ea360-285">Reemplace todo el texto dentro del **texto**, con "..."</span><span class="sxs-lookup"><span data-stu-id="ea360-285">Replace all the text within **Text**, with "..."</span></span>        
    5. <span data-ttu-id="ea360-286">Establecer el **anclaje** en el **Centro central**</span><span class="sxs-lookup"><span data-stu-id="ea360-286">Set the **Anchor** to **Middle Center**</span></span>
    6. <span data-ttu-id="ea360-287">Establecer la **alineación** en **Center**</span><span class="sxs-lookup"><span data-stu-id="ea360-287">Set the **Alignment** to **Center**</span></span>
    7. <span data-ttu-id="ea360-288">Establecer el **tamaño** de tabulación en **4**</span><span class="sxs-lookup"><span data-stu-id="ea360-288">Set the **Tab Size** to **4**</span></span>
    8. <span data-ttu-id="ea360-289">Establezca el **tamaño de fuente** en **50**</span><span class="sxs-lookup"><span data-stu-id="ea360-289">Set the **Font Size** to **50**</span></span>
    9. <span data-ttu-id="ea360-290">Establezca el **color** en **#FFFFFFFF**</span><span class="sxs-lookup"><span data-stu-id="ea360-290">Set the **Color** to **#FFFFFFFF**</span></span>

    ![Componente de texto](images/AzureLabs-Lab2-21-5.png)

3.  <span data-ttu-id="ea360-292">Arrastre **LabelText** desde el *Panel jerarquía*, a la *carpeta Asset*, dentro del *panel Proyecto*.</span><span class="sxs-lookup"><span data-stu-id="ea360-292">Drag the **LabelText** from the *Hierarchy Panel*, into the *Asset Folder*, within in the *Project Panel*.</span></span> <span data-ttu-id="ea360-293">Esto hará que el **LabelText** sea recurso prefabricado, de modo que se puedan crear instancias en el código.</span><span class="sxs-lookup"><span data-stu-id="ea360-293">This will make the **LabelText** a Prefab, so that it can be instantiated in code.</span></span>

    ![Cree un recurso prefabricado del objeto LabelText.](images/AzureLabs-Lab2-22.png)
 
4.  <span data-ttu-id="ea360-295">Debe eliminar el **LabelText** del panel de *jerarquías*, de modo que no se muestre en la escena de apertura.</span><span class="sxs-lookup"><span data-stu-id="ea360-295">You should delete the **LabelText** from the *Hierarchy Panel*, so that it will not be displayed in the opening scene.</span></span> <span data-ttu-id="ea360-296">Como es ahora un recurso prefabricado, al que se llamará para las instancias individuales de la carpeta Assets, no hay necesidad de mantenerla dentro de la escena.</span><span class="sxs-lookup"><span data-stu-id="ea360-296">As it is now a prefab, which you will call on for individual instances from your Assets folder, there is no need to keep it within the scene.</span></span> 
5.  <span data-ttu-id="ea360-297">La estructura final del objeto en el *Panel jerarquía* debe ser como la que se muestra en la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="ea360-297">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![Estructura final del panel de jerarquía.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a><span data-ttu-id="ea360-299">Capítulo 5: crear la clase ResultsLabel</span><span class="sxs-lookup"><span data-stu-id="ea360-299">Chapter 5 – Create the ResultsLabel class</span></span>

<span data-ttu-id="ea360-300">El primer script que necesita crear es la clase *ResultsLabel* , que es responsable de lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="ea360-300">The first script you need to create is the *ResultsLabel* class, which is responsible for the following:</span></span> 

- <span data-ttu-id="ea360-301">Crear las etiquetas en el espacio del mundo adecuado, con respecto a la posición de la cámara.</span><span class="sxs-lookup"><span data-stu-id="ea360-301">Creating the Labels in the appropriate world space, relative to the position of the Camera.</span></span>
- <span data-ttu-id="ea360-302">Mostrar las etiquetas de la imagen ardua.</span><span class="sxs-lookup"><span data-stu-id="ea360-302">Displaying the Tags from the Image Anaysis.</span></span>

<span data-ttu-id="ea360-303">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="ea360-303">To create this class:</span></span> 

1.  <span data-ttu-id="ea360-304">Haga clic con el botón derecho en el *panel Proyecto*y, a continuación, **cree > carpeta**.</span><span class="sxs-lookup"><span data-stu-id="ea360-304">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="ea360-305">Asigne a lacarpeta el nombre scripts.</span><span class="sxs-lookup"><span data-stu-id="ea360-305">Name the folder **Scripts**.</span></span> 

    ![Crear carpeta de scripts.](images/AzureLabs-Lab2-24.png)

2.  <span data-ttu-id="ea360-307">Con la carpeta scripts creada, haga doble clic en ella para abrirla.</span><span class="sxs-lookup"><span data-stu-id="ea360-307">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="ea360-308">Después, dentro de esa carpeta, haga clic con el botón derecho y seleccione **crear >** después  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="ea360-308">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="ea360-309">Asigne al script el nombre *ResultsLabel*.</span><span class="sxs-lookup"><span data-stu-id="ea360-309">Name the script *ResultsLabel*.</span></span> 

3.  <span data-ttu-id="ea360-310">Haga doble clic en el nuevo script *ResultsLabel* para abrirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="ea360-310">Double click on the new *ResultsLabel* script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="ea360-311">Dentro de la clase, inserte el siguiente código en la clase *ResultsLabel* :</span><span class="sxs-lookup"><span data-stu-id="ea360-311">Inside the Class insert the following code in the *ResultsLabel* class:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  <span data-ttu-id="ea360-312">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="ea360-312">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
7.  <span data-ttu-id="ea360-313">De nuevo en *el editor de Unity*, haga clic y arrastre la clase *ResultsLabel* desde la carpeta **scripts** hasta el objeto **cámara principal** en el *Panel jerarquía*.</span><span class="sxs-lookup"><span data-stu-id="ea360-313">Back in the *Unity Editor*, click and drag the *ResultsLabel* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
8.  <span data-ttu-id="ea360-314">Haga clic en la **cámara principal** y mire en el *panel del inspector*.</span><span class="sxs-lookup"><span data-stu-id="ea360-314">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span>

<span data-ttu-id="ea360-315">Observará que, desde el script que acaba de arrastrar a la cámara, hay dos campos: **Cursor** y **etiqueta recurso prefabricado**.</span><span class="sxs-lookup"><span data-stu-id="ea360-315">You will notice that from the script you just dragged into the Camera, there are two fields: **Cursor** and **Label Prefab**.</span></span>

9.  <span data-ttu-id="ea360-316">Arrastre el objeto denominado **cursor** desde el *Panel jerarquía* hasta la ranura denominada **cursor**, tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="ea360-316">Drag the object called **Cursor** from the *Hierarchy Panel* to the slot named **Cursor**, as shown in the image below.</span></span>
10. <span data-ttu-id="ea360-317">Arrastre el objeto llamado **LabelText** desde la *carpeta assets* del *panel Proyecto* hasta la ranura denominada **etiqueta recurso prefabricado**, tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="ea360-317">Drag the object called **LabelText** from the *Assets Folder* in the *Project Panel* to the slot named **Label Prefab**, as shown in the image below.</span></span> 

    ![Establezca los destinos de referencia en Unity.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a><span data-ttu-id="ea360-319">Capítulo 6: crear la clase ImageCapture</span><span class="sxs-lookup"><span data-stu-id="ea360-319">Chapter 6 – Create the ImageCapture class</span></span>

<span data-ttu-id="ea360-320">La clase siguiente que va a crear es la clase *ImageCapture* .</span><span class="sxs-lookup"><span data-stu-id="ea360-320">The next class you are going to create is the *ImageCapture* class.</span></span> <span data-ttu-id="ea360-321">Esta clase es responsable de:</span><span class="sxs-lookup"><span data-stu-id="ea360-321">This class is responsible for:</span></span>

-   <span data-ttu-id="ea360-322">Captura de una imagen con la cámara de HoloLens y su almacenamiento en la carpeta de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ea360-322">Capturing an Image using the HoloLens Camera and storing it in the App Folder.</span></span>
-   <span data-ttu-id="ea360-323">Captura de gestos de TAP del usuario.</span><span class="sxs-lookup"><span data-stu-id="ea360-323">Capturing Tap gestures from the user.</span></span>

<span data-ttu-id="ea360-324">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="ea360-324">To create this class:</span></span> 

1.  <span data-ttu-id="ea360-325">Vaya a la carpeta scripts que creó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="ea360-325">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="ea360-326">Haga clic con el botón derecho dentro de la carpeta, **cree > C# script**.</span><span class="sxs-lookup"><span data-stu-id="ea360-326">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="ea360-327">Llame al script *ImageCapture*.</span><span class="sxs-lookup"><span data-stu-id="ea360-327">Call the script *ImageCapture*.</span></span> 
3.  <span data-ttu-id="ea360-328">Haga doble clic en el nuevo script *ImageCapture* para abrirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="ea360-328">Double click on the new *ImageCapture* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="ea360-329">Agregue los siguientes espacios de nombres al principio del archivo:</span><span class="sxs-lookup"><span data-stu-id="ea360-329">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="ea360-330">A continuación, agregue las siguientes variables dentro de la clase *ImageCapture* , sobre el método *Start ()* :</span><span class="sxs-lookup"><span data-stu-id="ea360-330">Then add the following variables inside the *ImageCapture* class, above the *Start()* method:</span></span>

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
<span data-ttu-id="ea360-331">La variable **tapsCount** almacenará el número de gestos de TAP capturados por el usuario.</span><span class="sxs-lookup"><span data-stu-id="ea360-331">The **tapsCount** variable will store the number of tap gestures captured from the user.</span></span> <span data-ttu-id="ea360-332">Este número se usa en el nombre de las imágenes capturadas.</span><span class="sxs-lookup"><span data-stu-id="ea360-332">This number is used in the naming of the images captured.</span></span>

6.  <span data-ttu-id="ea360-333">Ahora es necesario agregar el código para los métodos *activo ()* e *Inicio ()* .</span><span class="sxs-lookup"><span data-stu-id="ea360-333">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="ea360-334">Se llamará cuando se inicialice la clase:</span><span class="sxs-lookup"><span data-stu-id="ea360-334">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="ea360-335">Implemente un controlador que se llamará cuando se produzca un gesto de TAP.</span><span class="sxs-lookup"><span data-stu-id="ea360-335">Implement a handler that will be called when a Tap gesture occurs.</span></span> 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
<span data-ttu-id="ea360-336">El método *TapHandler ()* incrementa el número de pulsaciones capturadas por el usuario y usa la posición del cursor actual para determinar dónde se debe colocar una nueva etiqueta.</span><span class="sxs-lookup"><span data-stu-id="ea360-336">The *TapHandler()* method increments the number of taps captured from the user and uses the current Cursor position to determine where to position a new Label.</span></span>

<span data-ttu-id="ea360-337">A continuación, este método llama al método *ExecuteImageCaptureAndAnalysis ()* para comenzar la funcionalidad básica de esta aplicación.</span><span class="sxs-lookup"><span data-stu-id="ea360-337">This method then calls the *ExecuteImageCaptureAndAnalysis()* method to begin the core functionality of this application.</span></span>

8.  <span data-ttu-id="ea360-338">Una vez capturada y almacenada una imagen, se llamará a los siguientes controladores.</span><span class="sxs-lookup"><span data-stu-id="ea360-338">Once an Image has been captured and stored, the following handlers will be called.</span></span> <span data-ttu-id="ea360-339">Si el proceso se realiza correctamente, el resultado se pasa a *VisionManager* (que aún no se ha creado) para el análisis.</span><span class="sxs-lookup"><span data-stu-id="ea360-339">If the process is successful, the result is passed to the *VisionManager* (which you are yet to create) for analysis.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  <span data-ttu-id="ea360-340">A continuación, agregue el método que utiliza la aplicación para iniciar el proceso de captura de imagen y almacenar la imagen.</span><span class="sxs-lookup"><span data-stu-id="ea360-340">Then add the method that the application uses to start the Image capture process and store the image.</span></span>

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> <span data-ttu-id="ea360-341">En este punto, observará que aparece un error en el *Panel*de la consola del editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="ea360-341">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="ea360-342">Esto se debe a que el código hace referencia a la clase *VisionManager* que creará en el siguiente capítulo.</span><span class="sxs-lookup"><span data-stu-id="ea360-342">This is because the code references the *VisionManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-image-analysis"></a><span data-ttu-id="ea360-343">Capítulo 7: llamada a Azure y análisis de imágenes</span><span class="sxs-lookup"><span data-stu-id="ea360-343">Chapter 7 – Call to Azure and Image Analysis</span></span>

<span data-ttu-id="ea360-344">El último script que debe crear es la clase *VisionManager* .</span><span class="sxs-lookup"><span data-stu-id="ea360-344">The last script you need to create is the *VisionManager* class.</span></span> 

<span data-ttu-id="ea360-345">Esta clase es responsable de:</span><span class="sxs-lookup"><span data-stu-id="ea360-345">This class is responsible for:</span></span>

-   <span data-ttu-id="ea360-346">Cargar la imagen más reciente capturada como una matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="ea360-346">Loading the latest image captured as an array of bytes.</span></span>
-   <span data-ttu-id="ea360-347">Envío de la matriz de bytes a la instancia de servicio de *Azure Computer Vision API* para su análisis.</span><span class="sxs-lookup"><span data-stu-id="ea360-347">Sending the byte array to your *Azure Computer Vision API* Service instance for analysis.</span></span>
-   <span data-ttu-id="ea360-348">Recibir la respuesta como una cadena JSON.</span><span class="sxs-lookup"><span data-stu-id="ea360-348">Receiving the response as a JSON string.</span></span>
-   <span data-ttu-id="ea360-349">Deserializar la respuesta y pasar las etiquetas resultantes a la clase *ResultsLabel* .</span><span class="sxs-lookup"><span data-stu-id="ea360-349">Deserializing the response and passing the resulting Tags to the *ResultsLabel* class.</span></span>
 
<span data-ttu-id="ea360-350">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="ea360-350">To create this class:</span></span>

1.  <span data-ttu-id="ea360-351">Haga doble clic en la carpeta scripts para abrirla.</span><span class="sxs-lookup"><span data-stu-id="ea360-351">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="ea360-352">Haga clic con el botón derecho en la carpeta scripts y haga clic en **crear > C# script**.</span><span class="sxs-lookup"><span data-stu-id="ea360-352">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="ea360-353">Asigne al script el nombre *VisionManager*.</span><span class="sxs-lookup"><span data-stu-id="ea360-353">Name the script *VisionManager*.</span></span> 
3.  <span data-ttu-id="ea360-354">Haga doble clic en el nuevo script para abrirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ea360-354">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="ea360-355">Actualice los espacios de nombres para que sean los mismos que los que se indican a continuación, en la parte superior de la clase *VisionManager* :</span><span class="sxs-lookup"><span data-stu-id="ea360-355">Update the namespaces to be the same as the following, at the top of the *VisionManager* class:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  <span data-ttu-id="ea360-356">En la parte superior del script, *dentro* de la clase *VisionManager* (encima del método *Start ()* ), ahora debe crear dos *clases* que representen la respuesta JSON deserializada de Azure:</span><span class="sxs-lookup"><span data-stu-id="ea360-356">At the top of your script, *inside* the *VisionManager* class (above the *Start()* method), you now need to create two *Classes* that will represent the deserialized JSON response from Azure:</span></span>

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="ea360-357">Las clases *TagData* y *AnalysedObject* deben tener el atributo *[System. Serializable]* agregado antes de que se pueda deserializar con las bibliotecas de Unity.</span><span class="sxs-lookup"><span data-stu-id="ea360-357">The *TagData* and *AnalysedObject* classes need to have the *[System.Serializable]* attribute added before the declaration to be able to be deserialized with the Unity libraries.</span></span>

6.  <span data-ttu-id="ea360-358">En la clase VisionManager, debe agregar las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="ea360-358">In the VisionManager class, you should add the following variables:</span></span>

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > <span data-ttu-id="ea360-359">Asegúrese de insertar la **clave de autenticación** en la variable **authorizationKey** .</span><span class="sxs-lookup"><span data-stu-id="ea360-359">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span> <span data-ttu-id="ea360-360">Habrá anotado la **clave de autenticación** al principio de este curso, [capítulo 1](#chapter-1--the-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="ea360-360">You will have noted your **Auth Key** at the beginning of this course, [Chapter 1](#chapter-1--the-azure-portal).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="ea360-361">La variable **visionAnalysisEndpoint** podría diferir de la especificada en este ejemplo.</span><span class="sxs-lookup"><span data-stu-id="ea360-361">The **visionAnalysisEndpoint** variable might differ from the one specified in this example.</span></span> <span data-ttu-id="ea360-362">**West-US** hace referencia estrictamente a las instancias de servicio creadas para la región oeste de EE. UU.</span><span class="sxs-lookup"><span data-stu-id="ea360-362">The **west-us** strictly refers to Service instances created for the West US region.</span></span> <span data-ttu-id="ea360-363">Actualícelo con la [dirección URL del punto de conexión](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); Estos son algunos ejemplos de lo que podría ser similar a:</span><span class="sxs-lookup"><span data-stu-id="ea360-363">Update this with your [endpoint URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); here are some examples of what that might look like:</span></span>
    > - <span data-ttu-id="ea360-364">Europa Occidental:`https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="ea360-364">West Europe: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="ea360-365">Sudeste Asiático:`https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="ea360-365">Southeast Asia: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="ea360-366">Este de Australia:`https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="ea360-366">Australia East: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>

7.  <span data-ttu-id="ea360-367">Ahora es necesario agregar el código para activo.</span><span class="sxs-lookup"><span data-stu-id="ea360-367">Code for Awake now needs to be added.</span></span> 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  <span data-ttu-id="ea360-368">A continuación, agregue la corutina (con el método de secuencia estático debajo), que obtendrá los resultados del análisis de la imagen capturada por la clase *ImageCapture* .</span><span class="sxs-lookup"><span data-stu-id="ea360-368">Next, add the coroutine (with the static stream method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* Class.</span></span> 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  <span data-ttu-id="ea360-369">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="ea360-369">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
10. <span data-ttu-id="ea360-370">De nuevo en el editor de Unity, haga clic y arrastre las clases *VisionManager* y *ImageCapture* desde la carpeta **scripts** hasta el objeto **cámara principal** en el *Panel jerarquía*.</span><span class="sxs-lookup"><span data-stu-id="ea360-370">Back in the Unity Editor, click and drag the *VisionManager* and *ImageCapture* classes from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 

## <a name="chapter-8--before-building"></a><span data-ttu-id="ea360-371">Capítulo 8: antes de compilar</span><span class="sxs-lookup"><span data-stu-id="ea360-371">Chapter 8 – Before building</span></span>

<span data-ttu-id="ea360-372">Para realizar una prueba exhaustiva de la aplicación, debe transferirla a su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ea360-372">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="ea360-373">Antes de hacerlo, asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="ea360-373">Before you do, ensure that:</span></span>

-   <span data-ttu-id="ea360-374">Toda la configuración mencionada en el [capítulo 2](#chapter-2--set-up-the-unity-project) se establece correctamente.</span><span class="sxs-lookup"><span data-stu-id="ea360-374">All the settings mentioned in [Chapter 2](#chapter-2--set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="ea360-375">Todos los scripts se adjuntan al objeto de **cámara principal** .</span><span class="sxs-lookup"><span data-stu-id="ea360-375">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="ea360-376">Todos los campos del *panel Inspector de cámara principal* están asignados correctamente.</span><span class="sxs-lookup"><span data-stu-id="ea360-376">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
-   <span data-ttu-id="ea360-377">Asegúrese de insertar la **clave de autenticación** en la variable **authorizationKey** .</span><span class="sxs-lookup"><span data-stu-id="ea360-377">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span>
-   <span data-ttu-id="ea360-378">Asegúrese de que también ha comprobado el punto de conexión en el script de *VisionManager* y que está alineado con *su* región (este documento usa *West-US* de forma predeterminada).</span><span class="sxs-lookup"><span data-stu-id="ea360-378">Ensure that you have also checked your endpoint in your *VisionManager* script, and that it aligns to *your* region (this document uses *west-us* by default).</span></span>

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a><span data-ttu-id="ea360-379">Capítulo 9: compilar la solución UWP y transferir localmente la aplicación</span><span class="sxs-lookup"><span data-stu-id="ea360-379">Chapter 9 – Build the UWP Solution and sideload the application</span></span>
<span data-ttu-id="ea360-380">Ya se ha completado todo lo necesario para la sección Unity de este proyecto, por lo que es el momento de compilarla desde Unity.</span><span class="sxs-lookup"><span data-stu-id="ea360-380">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="ea360-381">Vaya a la *configuración* - de compilación**archivo > configuración de compilación...**</span><span class="sxs-lookup"><span data-stu-id="ea360-381">Navigate to *Build Settings* - **File > Build Settings…**</span></span>
2.  <span data-ttu-id="ea360-382">En la ventana *configuración de compilación* , haga clic en compilar.</span><span class="sxs-lookup"><span data-stu-id="ea360-382">From the *Build Settings* window, click **Build**.</span></span>

    ![Compilar la aplicación desde Unity](images/AzureLabs-Lab2-26.png)

3.  <span data-ttu-id="ea360-384">Si aún no lo está, marque los **proyectos de Unity C#** .</span><span class="sxs-lookup"><span data-stu-id="ea360-384">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="ea360-385">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="ea360-385">Click **Build**.</span></span> <span data-ttu-id="ea360-386">Unity iniciará una ventana del *Explorador de archivos* , donde tendrá que crear y seleccionar una carpeta en la que compilar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ea360-386">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="ea360-387">Cree esa carpeta ahora y asígnele el nombre *App*.</span><span class="sxs-lookup"><span data-stu-id="ea360-387">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="ea360-388">Después, con la carpeta de la *aplicación* seleccionada, presione **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="ea360-388">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="ea360-389">Unity comenzará a compilar el proyecto en la carpeta de la *aplicación* .</span><span class="sxs-lookup"><span data-stu-id="ea360-389">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="ea360-390">Una vez que Unity termine de compilar (puede tardar algún tiempo), se abrirá una ventana del *Explorador de archivos* en la ubicación de la compilación (Compruebe la barra de tareas, ya que es posible que no aparezca siempre por encima de las ventanas, pero le notificará la adición de una nueva ventana).</span><span class="sxs-lookup"><span data-stu-id="ea360-390">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-10--deploy-to-hololens"></a><span data-ttu-id="ea360-391">Capítulo 10: implementación en HoloLens</span><span class="sxs-lookup"><span data-stu-id="ea360-391">Chapter 10 – Deploy to HoloLens</span></span>

<span data-ttu-id="ea360-392">Para implementar en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="ea360-392">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="ea360-393">Necesitará la dirección IP de HoloLens (para la implementación remota) y para asegurarse de que HoloLens está en **modo de desarrollador**.</span><span class="sxs-lookup"><span data-stu-id="ea360-393">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="ea360-394">Para ello:</span><span class="sxs-lookup"><span data-stu-id="ea360-394">To do this:</span></span>

    1. <span data-ttu-id="ea360-395">Mientras se contenga HoloLens, abra la **configuración**.</span><span class="sxs-lookup"><span data-stu-id="ea360-395">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="ea360-396">Vaya a **Network & Internet > Wi-Fi > opciones avanzadas** .</span><span class="sxs-lookup"><span data-stu-id="ea360-396">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="ea360-397">Anote la dirección **IPv4** .</span><span class="sxs-lookup"><span data-stu-id="ea360-397">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="ea360-398">A continuación, vuelva a **configuración**y, a continuación, **actualice & seguridad > para desarrolladores**</span><span class="sxs-lookup"><span data-stu-id="ea360-398">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="ea360-399">Establezca el modo de Desarrollador en.</span><span class="sxs-lookup"><span data-stu-id="ea360-399">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="ea360-400">Vaya a la nueva compilación de Unity (la carpeta de la *aplicación* ) y abra el archivo de solución con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="ea360-400">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="ea360-401">En la configuración de soluciones, seleccione Depurar.</span><span class="sxs-lookup"><span data-stu-id="ea360-401">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="ea360-402">En la plataforma de la solución, seleccione **x86**, **equipo remoto**.</span><span class="sxs-lookup"><span data-stu-id="ea360-402">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![Implemente la solución desde Visual Studio.](images/AzureLabs-Lab2-27.png)
 
5.  <span data-ttu-id="ea360-404">Vaya al **menú** compilar y haga clic en **implementar solución**para transferir localmente la aplicación a HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ea360-404">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="ea360-405">La aplicación debe aparecer ahora en la lista de aplicaciones instaladas en HoloLens, lista para su lanzamiento.</span><span class="sxs-lookup"><span data-stu-id="ea360-405">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="ea360-406">Para implementar en auriculares inmersivo, establezca la **plataforma** de la solución en el *equipo local*y establezca la **configuración** en depurar, con *x86* como **plataforma**.</span><span class="sxs-lookup"><span data-stu-id="ea360-406">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="ea360-407">A continuación, implemente en el equipo local, mediante el **menú**compilar, seleccionando *implementar solución*.</span><span class="sxs-lookup"><span data-stu-id="ea360-407">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="your-finished-computer-vision-api-application"></a><span data-ttu-id="ea360-408">La aplicación Computer Vision API finalizada</span><span class="sxs-lookup"><span data-stu-id="ea360-408">Your finished Computer Vision API application</span></span>

<span data-ttu-id="ea360-409">Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha el Computer Vision API de Azure para reconocer objetos reales y mostrar la confianza de lo que se ha detectado.</span><span class="sxs-lookup"><span data-stu-id="ea360-409">Congratulations, you built a mixed reality app that leverages the Azure Computer Vision API to recognize real world objects, and display confidence of what has been seen.</span></span>

![resultado de laboratorio](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="ea360-411">Ejercicios de bonus</span><span class="sxs-lookup"><span data-stu-id="ea360-411">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="ea360-412">Ejercicio 1</span><span class="sxs-lookup"><span data-stu-id="ea360-412">Exercise 1</span></span>

<span data-ttu-id="ea360-413">Del mismo modo que ha usado el parámetro *Tags* (como se evidencia en el *punto de conexión* usado dentro del *VisionManager*), extienda la aplicación para detectar otra información; Observe a qué otros parámetros tiene acceso [aquí](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span><span class="sxs-lookup"><span data-stu-id="ea360-413">Just as you have used the *Tags* parameter (as evidenced within the *endpoint* used within the *VisionManager*), extend the app to detect other information; have a look at what other parameters you have access to [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span>

### <a name="exercise-2"></a><span data-ttu-id="ea360-414">Ejercicio 2</span><span class="sxs-lookup"><span data-stu-id="ea360-414">Exercise 2</span></span>

<span data-ttu-id="ea360-415">Muestre los datos de Azure devueltos, de forma más conversación y legibles, y quizás oculte los números.</span><span class="sxs-lookup"><span data-stu-id="ea360-415">Display the returned Azure data, in a more conversational, and readable way, perhaps hiding the numbers.</span></span> <span data-ttu-id="ea360-416">Como si un bot pudiera estar hablando al usuario.</span><span class="sxs-lookup"><span data-stu-id="ea360-416">As though a bot might be speaking to the user.</span></span>
