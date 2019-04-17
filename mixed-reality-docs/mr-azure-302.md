---
title: El Sr. y Azure 302 - Computer vision
description: Realice este curso para aprender a reconocer contenido visual dentro de una imagen proporcionada, con Azure Computer Vision en una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidad mixta, Azure, academy, unity, tutorial, api, visión de equipo, hololens, envolventes, vr
ms.openlocfilehash: 9d5288904dd6cae08a995ae40a31b00fea655776
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597888"
---
>[!NOTE]
><span data-ttu-id="ab19c-104">Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.</span><span class="sxs-lookup"><span data-stu-id="ab19c-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="ab19c-105">Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="ab19c-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="ab19c-106">Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.</span><span class="sxs-lookup"><span data-stu-id="ab19c-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="ab19c-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="ab19c-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="ab19c-108">Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ab19c-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="ab19c-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.</span><span class="sxs-lookup"><span data-stu-id="ab19c-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302-computer-vision"></a><span data-ttu-id="ab19c-110">El Sr. y 302 de Azure: Visión de equipo</span><span class="sxs-lookup"><span data-stu-id="ab19c-110">MR and Azure 302: Computer vision</span></span>

<span data-ttu-id="ab19c-111">En este curso, obtendrá información sobre cómo reconocer contenido visual dentro de una imagen proporcionada, con funcionalidades de Azure Computer Vision en una aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="ab19c-111">In this course, you will learn how to recognize visual content within a provided image, using Azure Computer Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="ab19c-112">Resultados de reconocimiento se mostrará como etiquetas descriptivas.</span><span class="sxs-lookup"><span data-stu-id="ab19c-112">Recognition results will be displayed as descriptive tags.</span></span> <span data-ttu-id="ab19c-113">Puede usar este servicio sin necesidad de para entrenar un modelo de aprendizaje automático.</span><span class="sxs-lookup"><span data-stu-id="ab19c-113">You can use this service without needing to train a machine learning model.</span></span> <span data-ttu-id="ab19c-114">Si su implementación requiere entrenar un modelo de aprendizaje automático, vea [MR y Azure 302b](mr-azure-302b.md).</span><span class="sxs-lookup"><span data-stu-id="ab19c-114">If your implementation requires training a machine learning model, see [MR and Azure 302b](mr-azure-302b.md).</span></span>

![Resultado de laboratorio](images/AzureLabs-Lab2-000.png)

<span data-ttu-id="ab19c-116">Microsoft Computer Vision es un conjunto de API diseñadas para ofrecer a los desarrolladores con procesamiento de imágenes y análisis (con la información de devolución), mediante algoritmos avanzados, todo ello desde la nube.</span><span class="sxs-lookup"><span data-stu-id="ab19c-116">The Microsoft Computer Vision is a set of APIs designed to provide developers with image processing and analysis (with return information), using advanced algorithms, all from the cloud.</span></span> <span data-ttu-id="ab19c-117">Los desarrolladores cargar una imagen o una dirección URL de imagen y los algoritmos de Microsoft Computer Vision API analizan el contenido visual, en función de entradas que elige el usuario, que, a continuación, puede devolver información, incluidos, que identifica el tipo y la calidad de una imagen, detectar caras humanas () devolver sus coordenadas) y etiquetado, o categorizar las imágenes.</span><span class="sxs-lookup"><span data-stu-id="ab19c-117">Developers upload an image or image URL, and the Microsoft Computer Vision API algorithms analyze the visual content, based upon inputs chosen the user, which then can return information, including, identifying the type and quality of an image, detect human faces (returning their coordinates), and tagging, or categorizing images.</span></span> <span data-ttu-id="ab19c-118">Para obtener más información, visite la [página Azure Computer Vision API](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span><span class="sxs-lookup"><span data-stu-id="ab19c-118">For more information, visit the [Azure Computer Vision API page](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span></span>

<span data-ttu-id="ab19c-119">Una vez completado este curso, tendrá una realidad mixta HoloLens aplicación, que podrá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="ab19c-119">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="ab19c-120">La cámara de la HoloLens con el gesto de pulsar, capturará una imagen.</span><span class="sxs-lookup"><span data-stu-id="ab19c-120">Using the Tap gesture, the camera of the HoloLens will capture an image.</span></span>
2.  <span data-ttu-id="ab19c-121">La imagen se enviará con el servicio de API de visión de equipos de Azure.</span><span class="sxs-lookup"><span data-stu-id="ab19c-121">The image will be sent to the Azure Computer Vision API Service.</span></span> 
3.  <span data-ttu-id="ab19c-122">Los objetos reconocidos se mostrarán en un grupo de interfaz de usuario simple que está situado en la escena de Unity.</span><span class="sxs-lookup"><span data-stu-id="ab19c-122">The objects recognized will be listed in a simple UI group positioned in the Unity Scene.</span></span>

<span data-ttu-id="ab19c-123">En la aplicación, es depende de usted sobre cómo se integrará los resultados con el diseño.</span><span class="sxs-lookup"><span data-stu-id="ab19c-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="ab19c-124">Este curso está diseñado para mostrarle cómo integrar un servicio de Azure con el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="ab19c-124">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="ab19c-125">Es su trabajo consiste en usar los conocimientos que obtendrá de este curso para mejorar las aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="ab19c-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="ab19c-126">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="ab19c-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="ab19c-127">Curso</span><span class="sxs-lookup"><span data-stu-id="ab19c-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="ab19c-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ab19c-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ab19c-129"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="ab19c-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="ab19c-130">El Sr. y 302 de Azure: Visión de equipo</span><span class="sxs-lookup"><span data-stu-id="ab19c-130">MR and Azure 302: Computer vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="ab19c-131">✔️</span><span class="sxs-lookup"><span data-stu-id="ab19c-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="ab19c-132">✔️</span><span class="sxs-lookup"><span data-stu-id="ab19c-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="ab19c-133">Aunque este curso se centra principalmente en HoloLens, también puede aplicar lo aprendido en este curso a inmersivos (VR) Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="ab19c-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="ab19c-134">Dado que inmersivos (VR) no tienen cámaras accesible, necesitará una cámara externa conectada a su PC.</span><span class="sxs-lookup"><span data-stu-id="ab19c-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="ab19c-135">Como seguir el curso, verá las notas de la de los cambios que deberá emplear para admitir inmersivos (VR).</span><span class="sxs-lookup"><span data-stu-id="ab19c-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ab19c-136">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="ab19c-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="ab19c-137">Este tutorial está diseñado para los desarrolladores con experiencia básica con Unity y C#.</span><span class="sxs-lookup"><span data-stu-id="ab19c-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="ab19c-138">También Ten en cuenta que los requisitos previos y las instrucciones escritas en este documento representan lo que se ha probado y comprobado en el momento de redactar (mayo de 2018).</span><span class="sxs-lookup"><span data-stu-id="ab19c-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="ab19c-139">Es libre de usar el software más reciente, como se muestra en el [instalar las herramientas de](install-the-tools.md) artículo, aunque no se debe suponer que la información de este curso perfectamente coincida con lo que encontrará en el software más reciente que se indica a continuación .</span><span class="sxs-lookup"><span data-stu-id="ab19c-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="ab19c-140">Se recomiendan el siguiente hardware y software para este curso:</span><span class="sxs-lookup"><span data-stu-id="ab19c-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="ab19c-141">Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desarrollo de auriculares envolvente (VR)</span><span class="sxs-lookup"><span data-stu-id="ab19c-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="ab19c-142">Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="ab19c-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ab19c-143">El SDK más reciente de Windows 10</span><span class="sxs-lookup"><span data-stu-id="ab19c-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ab19c-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="ab19c-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ab19c-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ab19c-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="ab19c-146">Un [auriculares de Windows Mixed Reality envolventes (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="ab19c-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="ab19c-147">Una cámara conectada a su equipo (para el desarrollo de amplias auriculares)</span><span class="sxs-lookup"><span data-stu-id="ab19c-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="ab19c-148">Acceso a Internet para el programa de instalación de Azure y la recuperación de Computer Vision API</span><span class="sxs-lookup"><span data-stu-id="ab19c-148">Internet access for Azure setup and Computer Vision API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="ab19c-149">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="ab19c-149">Before you start</span></span>

1.  <span data-ttu-id="ab19c-150">Para evitar problemas de creación de este proyecto, se recomienda encarecidamente que cree el proyecto se ha mencionado en este tutorial en una carpeta raíz o cerca de la raíz (rutas de acceso de carpeta largo pueden causar problemas en tiempo de compilación).</span><span class="sxs-lookup"><span data-stu-id="ab19c-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="ab19c-151">Configurar y probar su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ab19c-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="ab19c-152">Si necesita admite la configuración de su HoloLens, [Asegúrese de visitar el artículo del programa de instalación de HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="ab19c-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="ab19c-153">Es una buena idea para realizar la calibración y optimización Sensor cuando comienza a desarrollar una App HoloLens nuevo (a veces puede ayudar a realizar dichas tareas para cada usuario).</span><span class="sxs-lookup"><span data-stu-id="ab19c-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="ab19c-154">Para obtener ayuda sobre la calibración, siga este [vínculo al artículo de calibración de HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="ab19c-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="ab19c-155">Para obtener ayuda sobre optimización Sensor, siga este [vínculo al artículo optimización Sensor de HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="ab19c-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="ab19c-156">Capítulo 1: el Portal de Azure</span><span class="sxs-lookup"><span data-stu-id="ab19c-156">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="ab19c-157">Para usar el *Computer Vision API* service en Azure, deberá configurar una instancia del servicio esté disponible para su aplicación.</span><span class="sxs-lookup"><span data-stu-id="ab19c-157">To use the *Computer Vision API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="ab19c-158">En primer lugar, inicie sesión en el [Portal de Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="ab19c-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="ab19c-159">Si no dispone de una cuenta de Azure, deberá crear uno.</span><span class="sxs-lookup"><span data-stu-id="ab19c-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="ab19c-160">Si está siguiendo este tutorial en una situación de aula o laboratorio, pida el instructor o uno de los a los supervisores de ayuda para instalar la nueva cuenta.</span><span class="sxs-lookup"><span data-stu-id="ab19c-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="ab19c-161">Una vez que haya iniciado sesión, haga clic en **New** en la esquina superior izquierda esquina y busque *Computer Vision API*y haga clic en **ENTRAR**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-161">Once you are logged in, click on **New** in the top left corner, and search for *Computer Vision API*, and click **Enter**.</span></span>

    ![Crear un nuevo recurso en Azure](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > <span data-ttu-id="ab19c-163">La palabra **New** se han reemplazado con **crear un recurso**, en los portales más reciente.</span><span class="sxs-lookup"><span data-stu-id="ab19c-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="ab19c-164">La nueva página proporcionará una descripción de la *Computer Vision API* service.</span><span class="sxs-lookup"><span data-stu-id="ab19c-164">The new page will provide a description of the *Computer Vision API* service.</span></span> <span data-ttu-id="ab19c-165">En la parte inferior izquierda de esta página, seleccione el **crear** botón para crear una asociación con este servicio.</span><span class="sxs-lookup"><span data-stu-id="ab19c-165">At the bottom left of this page, select the **Create** button, to create an association with this service.</span></span>

    ![Acerca del servicio de api de visión de equipo](images/AzureLabs-Lab2-01.png)
 
4.  <span data-ttu-id="ab19c-167">Una vez que ha hecho clic **crear**:</span><span class="sxs-lookup"><span data-stu-id="ab19c-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="ab19c-168">Insertar el elemento **nombre** para esta instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="ab19c-168">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="ab19c-169">Seleccione un **suscripción**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-169">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="ab19c-170">Seleccione el **tarifa** adecuado para usted, si ésta es la primera tiempo creando una *Computer Vision API* servicio, un nivel gratuito (denominado F0) debe estar disponible para usted.</span><span class="sxs-lookup"><span data-stu-id="ab19c-170">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Computer Vision API* Service, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="ab19c-171">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="ab19c-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="ab19c-172">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="ab19c-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="ab19c-173">Se recomienda mantener todos los servicios de Azure asociados a un proyecto único (por ejemplo, por ejemplo, estos laboratorios) en un grupo de recursos comunes).</span><span class="sxs-lookup"><span data-stu-id="ab19c-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="ab19c-174">Si desea leer más acerca de los grupos de recursos de Azure, inicie [visite el artículo del grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="ab19c-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="ab19c-175">Determinar la ubicación del grupo de recursos (si está creando un nuevo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="ab19c-175">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="ab19c-176">La ubicación sería lo ideal es que en la región donde desea ejecutar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ab19c-176">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="ab19c-177">Algunos recursos de Azure solo están disponibles en determinadas regiones.</span><span class="sxs-lookup"><span data-stu-id="ab19c-177">Some Azure assets are only available in certain regions.</span></span>

    6. <span data-ttu-id="ab19c-178">También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.</span><span class="sxs-lookup"><span data-stu-id="ab19c-178">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="ab19c-179">Haga clic en crear.</span><span class="sxs-lookup"><span data-stu-id="ab19c-179">Click Create.</span></span>

        ![Información sobre la creación de servicio](images/AzureLabs-Lab2-02.png)

5.  <span data-ttu-id="ab19c-181">Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="ab19c-181">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="ab19c-182">Una vez creada la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="ab19c-182">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Vea la notificación de nuevo para su nuevo servicio](images/AzureLabs-Lab2-03.png) 
 
7.  <span data-ttu-id="ab19c-184">Haga clic en la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="ab19c-184">Click on the notification to explore your new Service instance.</span></span> 

    ![Seleccione el botón Ir a recursos.](images/AzureLabs-Lab2-04.png)
 
8. <span data-ttu-id="ab19c-186">Haga clic en el **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="ab19c-186">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="ab19c-187">Se le llevará a la nueva instancia del servicio Computer Vision API.</span><span class="sxs-lookup"><span data-stu-id="ab19c-187">You will be taken to your new Computer Vision API service instance.</span></span> 

    ![El nuevo servicio Computer Vision API](images/AzureLabs-Lab2-05.png)
 
9.  <span data-ttu-id="ab19c-189">En este tutorial, la aplicación necesitará realizar llamadas al servicio, que se realiza a través del uso clave del servicio en la de suscripción.</span><span class="sxs-lookup"><span data-stu-id="ab19c-189">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="ab19c-190">Desde el *inicio rápido* página, de su *Computer Vision API* de servicio, navegue hasta el primer paso, *obtener las claves*y haga clic en **claves** () También puede lograr esto, haga clic en el hipervínculo azul claves, ubicado en el menú de navegación de servicios, indicado por el icono de llave).</span><span class="sxs-lookup"><span data-stu-id="ab19c-190">From the *Quick start* page, of your *Computer Vision API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="ab19c-191">Esto revelará su servicio *claves*.</span><span class="sxs-lookup"><span data-stu-id="ab19c-191">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="ab19c-192">Realice una copia de una de las claves de muestra, ya que lo necesitará más adelante en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="ab19c-192">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

12. <span data-ttu-id="ab19c-193">Vuelva a la *inicio rápido* página y, a partir de ahí, capturar el punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="ab19c-193">Go back to the *Quick start* page, and from there, fetch your endpoint.</span></span> <span data-ttu-id="ab19c-194">Tenga en cuenta suya puede ser diferente, dependiendo de su región (lo que si es así, deberá realizar un cambio en el código más adelante).</span><span class="sxs-lookup"><span data-stu-id="ab19c-194">Be aware yours may be different, depending on your region (which if it is, you will need to make a change to your code later).</span></span> <span data-ttu-id="ab19c-195">Realice una copia de este punto de conexión para su uso posterior:</span><span class="sxs-lookup"><span data-stu-id="ab19c-195">Take a copy of this endpoint for use later:</span></span>

    ![El nuevo servicio Computer Vision API](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > <span data-ttu-id="ab19c-197">Puede comprobar cuáles son los diferentes extremos [aquí](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span><span class="sxs-lookup"><span data-stu-id="ab19c-197">You can check what the various endpoints are [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="ab19c-198">Capítulo 2: configurar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="ab19c-198">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="ab19c-199">El siguiente es un conjunto típico de para el desarrollo con la realidad mixta y por lo tanto, es una buena plantilla para otros proyectos.</span><span class="sxs-lookup"><span data-stu-id="ab19c-199">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="ab19c-200">Abra *Unity* y haga clic en **New**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-200">Open *Unity* and click **New**.</span></span> 

    ![Inicie el nuevo proyecto de Unity.](images/AzureLabs-Lab2-06.png)

2.  <span data-ttu-id="ab19c-202">Ahora deberá proporcionar un nombre de proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="ab19c-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="ab19c-203">Insertar **MR_ComputerVision**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-203">Insert **MR_ComputerVision**.</span></span> <span data-ttu-id="ab19c-204">Asegúrese de que el tipo de proyecto se establece en **3D**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="ab19c-205">Establecer el **ubicación** a algún lugar adecuado para usted (Recuerde, es mejor cuanto más se acerque a los directorios raíz).</span><span class="sxs-lookup"><span data-stu-id="ab19c-205">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="ab19c-206">A continuación, haga clic en **crear un proyecto**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-206">Then, click **Create project**.</span></span>

    ![Se proporcionan detalles para el nuevo proyecto de Unity.](images/AzureLabs-Lab2-07.png)

3.  <span data-ttu-id="ab19c-208">Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="ab19c-209">Vaya a **Editar > Preferencias** y, a continuación, en la ventana nueva, vaya a **herramientas externas**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="ab19c-210">Cambio **External Script Editor** a **de Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="ab19c-211">Cerrar la **preferencias** ventana.</span><span class="sxs-lookup"><span data-stu-id="ab19c-211">Close the **Preferences** window.</span></span>

    ![Actualizar las preferencias del editor de secuencia de comandos.](images/AzureLabs-Lab2-08.png)

4.  <span data-ttu-id="ab19c-213">A continuación, vaya a **archivo > configuración de compilación** y seleccione **Universal Windows Platform**, a continuación, haga clic en el **Cambiar plataforma** botón para aplicar la selección.</span><span class="sxs-lookup"><span data-stu-id="ab19c-213">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Crear ventana de configuración de la plataforma del conmutador para UWP.](images/AzureLabs-Lab2-10.png)

5.  <span data-ttu-id="ab19c-215">Mientras sigue en **archivo > configuración de compilación** y asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="ab19c-215">While still in **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="ab19c-216">**Dispositivo de destino** está establecido en **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="ab19c-216">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="ab19c-217">Establezca el inmersivos, **dispositivo de destino** a *cualquier dispositivo*.</span><span class="sxs-lookup"><span data-stu-id="ab19c-217">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="ab19c-218">**Tipo de compilación** está establecido en **D3D**</span><span class="sxs-lookup"><span data-stu-id="ab19c-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="ab19c-219">**SDK** está establecido en **instalada más reciente**</span><span class="sxs-lookup"><span data-stu-id="ab19c-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="ab19c-220">**Versión de Visual Studio** está establecido en **instalada más reciente**</span><span class="sxs-lookup"><span data-stu-id="ab19c-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="ab19c-221">**Compilar y ejecutar** está establecido en **máquina Local**</span><span class="sxs-lookup"><span data-stu-id="ab19c-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="ab19c-222">Guarde la escena y agregarlo a la compilación.</span><span class="sxs-lookup"><span data-stu-id="ab19c-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="ab19c-223">Hacer esto seleccionando **agregar escenas abierto**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="ab19c-224">Aparecerá el guardado de la ventana.</span><span class="sxs-lookup"><span data-stu-id="ab19c-224">A save window will appear.</span></span>
        
            ![Haga clic en Agregar botón de escenas abierto](images/AzureLabs-Lab2-11.png)

        2. <span data-ttu-id="ab19c-226">Cree una nueva carpeta de esto y cualquier futuro, escena, a continuación, seleccione el **nueva carpeta** botón para crear una nueva carpeta y asígnele el nombre **escenas**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Crear nueva carpeta de scripts](images/AzureLabs-Lab2-12.png)

        3. <span data-ttu-id="ab19c-228">Abra su recién creado **escenas** carpeta y, a continuación, en el *nombre de archivo*: campo de texto, escriba **MR_ComputerVisionScene**, a continuación, haga clic en **guardar** .</span><span class="sxs-lookup"><span data-stu-id="ab19c-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![Asigne un nombre de nueva escena.](images/AzureLabs-Lab2-13.png)

            > <span data-ttu-id="ab19c-230">Tenga en cuenta, debe guardar sus escenas de Unity dentro de la *activos* carpeta, ya que deben estar asociados al proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="ab19c-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="ab19c-231">Creación de la carpeta de segundo plano (y otras carpetas similares) es una forma habitual de estructurar un proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="ab19c-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="ab19c-232">El resto de la configuración, en *configuración de compilación*, debe dejarse como predeterminada por ahora.</span><span class="sxs-lookup"><span data-stu-id="ab19c-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="ab19c-233">En el *configuración de compilación* ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el *Inspector* se encuentra.</span><span class="sxs-lookup"><span data-stu-id="ab19c-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Abra Configuración del Reproductor.](images/AzureLabs-Lab2-14.png)

7. <span data-ttu-id="ab19c-235">En este panel, es necesario comprobar algunas opciones de configuración:</span><span class="sxs-lookup"><span data-stu-id="ab19c-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="ab19c-236">En el **otra configuración** pestaña:</span><span class="sxs-lookup"><span data-stu-id="ab19c-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="ab19c-237">**Versión en tiempo de ejecución de secuencias de comandos** debe ser **estable** (.NET 3.5 equivalente).</span><span class="sxs-lookup"><span data-stu-id="ab19c-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="ab19c-238">**Scripting de back-end** debe ser **.NET**</span><span class="sxs-lookup"><span data-stu-id="ab19c-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="ab19c-239">**Nivel de compatibilidad de API** debe ser **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="ab19c-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Actualizar la configuración de otros.](images/AzureLabs-Lab2-15.png)
      
    2. <span data-ttu-id="ab19c-241">Dentro de la **configuración de publicación** ficha **capacidades**, consulte:</span><span class="sxs-lookup"><span data-stu-id="ab19c-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="ab19c-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="ab19c-242">**InternetClient**</span></span>
        2. <span data-ttu-id="ab19c-243">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="ab19c-243">**Webcam**</span></span>

            ![Actualizando la configuración de publicación.](images/AzureLabs-Lab2-16.png)

    3. <span data-ttu-id="ab19c-245">Más abajo el panel, en **XR configuración** (bajo **configuración de publicación**), graduación **admite la realidad Virtual**, asegúrese de que el **SDK de Windows Mixed Reality**  se agrega.</span><span class="sxs-lookup"><span data-stu-id="ab19c-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Actualice la configuración de R de X.](images/AzureLabs-Lab2-17.png)

8.  <span data-ttu-id="ab19c-247">En *configuración de compilación* _Unity C#_  proyectos ya no está atenuada; Marque la casilla situada junto a esto.</span><span class="sxs-lookup"><span data-stu-id="ab19c-247">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="ab19c-248">Cierre la ventana de configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="ab19c-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="ab19c-249">Guarde la escena y el proyecto (**archivo > Guardar ESCENA / archivo > Guardar proyecto**).</span><span class="sxs-lookup"><span data-stu-id="ab19c-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="ab19c-250">Capítulo 3: configuración de cámara principal</span><span class="sxs-lookup"><span data-stu-id="ab19c-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ab19c-251">Si desea omitir la *configurar Unity* componente de este curso y continuar directamente en código, no dude en descargar este [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), importarlo en el proyecto como un [paquete personalizado ](https://docs.unity3d.com/Manual/AssetPackages.html)y, a continuación, continuar desde [capítulo 5](#chapter-5--create-the-resultslabel-class).</span><span class="sxs-lookup"><span data-stu-id="ab19c-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-resultslabel-class).</span></span>

1.  <span data-ttu-id="ab19c-252">En el *jerarquía Panel*, seleccione el **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-252">In the *Hierarchy Panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="ab19c-253">Una vez seleccionado, podrá ver todos los componentes de la **cámara principal** en el *Panel Inspector*.</span><span class="sxs-lookup"><span data-stu-id="ab19c-253">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="ab19c-254">El **objeto de cámara** debe denominarse **cámara principal** (tenga en cuenta la ortografía!)</span><span class="sxs-lookup"><span data-stu-id="ab19c-254">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>
    2. <span data-ttu-id="ab19c-255">La cámara principal **etiqueta** debe establecerse en **MainCamera** (tenga en cuenta la ortografía!)</span><span class="sxs-lookup"><span data-stu-id="ab19c-255">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>
    3. <span data-ttu-id="ab19c-256">Asegúrese de que el **transformar posición** está establecido en **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="ab19c-256">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="ab19c-257">Establecer **borrar las marcas** a **Color sólido** (omitir esto para envolventes auriculares).</span><span class="sxs-lookup"><span data-stu-id="ab19c-257">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>
    5. <span data-ttu-id="ab19c-258">Establecer el **en segundo plano** Color del componente de cámara para **negro, alfa de 0 (código hexadecimal: #00000000)** (omitir esto para envolventes auriculares).</span><span class="sxs-lookup"><span data-stu-id="ab19c-258">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

        ![Actualizar componentes de la cámara.](images/AzureLabs-Lab2-18.png)
 
3.  <span data-ttu-id="ab19c-260">A continuación, tendrá que crear un objeto simple "Cursor" conectado a la **cámara principal**, que ayudan a colocar el análisis de imagen generará cuando se ejecuta la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ab19c-260">Next, you will have to create a simple “Cursor” object attached to the **Main Camera**, which will help you position the image analysis output when the application is running.</span></span> <span data-ttu-id="ab19c-261">Este Cursor determinará el punto central del foco de la cámara.</span><span class="sxs-lookup"><span data-stu-id="ab19c-261">This Cursor will determine the center point of the camera focus.</span></span>

<span data-ttu-id="ab19c-262">Para crear el Cursor:</span><span class="sxs-lookup"><span data-stu-id="ab19c-262">To create the Cursor:</span></span>

1.  <span data-ttu-id="ab19c-263">En el *jerarquía Panel*, haga doble clic en el **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-263">In the *Hierarchy Panel*, right-click on the **Main Camera**.</span></span> <span data-ttu-id="ab19c-264">En **objeto 3D**, haga clic en **esfera**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-264">Under **3D Object**, click on **Sphere**.</span></span>

    ![Seleccione el objeto del Cursor.](images/AzureLabs-Lab2-19.png)
 
2.  <span data-ttu-id="ab19c-266">Cambiar el nombre de la **esfera** a **Cursor** (haga doble clic en el objeto del Cursor o presione el botón de teclado 'F2' con el objeto seleccionado) y asegúrese de que se encuentra como elemento secundario de la **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-266">Rename the **Sphere** to **Cursor** (double click the Cursor object or press the ‘F2’ keyboard button with the object selected), and make sure it is located as child of the **Main Camera**.</span></span>

3.  <span data-ttu-id="ab19c-267">En el *jerarquía Panel*, haga clic en el **Cursor**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-267">In the *Hierarchy Panel*, left click on the **Cursor**.</span></span> <span data-ttu-id="ab19c-268">Con el Cursor seleccionado, ajustar las siguientes variables en el *Panel Inspector*:</span><span class="sxs-lookup"><span data-stu-id="ab19c-268">With the Cursor selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="ab19c-269">Establecer el *transformar posición* a **0, 0, 5**</span><span class="sxs-lookup"><span data-stu-id="ab19c-269">Set the *Transform Position* to **0, 0, 5**</span></span>
    2. <span data-ttu-id="ab19c-270">Establecer el *escala* a **0,02, 0,02, 0,02**</span><span class="sxs-lookup"><span data-stu-id="ab19c-270">Set the *Scale* to **0.02, 0.02, 0.02**</span></span>

        ![Actualizar la posición de la transformación y la escala.](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a><span data-ttu-id="ab19c-272">Capítulo 4: instalación del sistema de etiqueta</span><span class="sxs-lookup"><span data-stu-id="ab19c-272">Chapter 4 – Setup the Label system</span></span>

<span data-ttu-id="ab19c-273">Una vez que ha capturado una imagen con la cámara de HoloLens, esa imagen se enviará a su *Azure Computer Vision API* instancia de servicio para el análisis.</span><span class="sxs-lookup"><span data-stu-id="ab19c-273">Once you have captured an image with the HoloLens’ camera, that image will be sent to your *Azure Computer Vision API* Service instance for analysis.</span></span> 

<span data-ttu-id="ab19c-274">Los resultados del análisis será una lista de objetos reconocidos denominados **etiquetas**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-274">The results of that analysis will be a list of recognized objects called **Tags**.</span></span> 

<span data-ttu-id="ab19c-275">Debe utilizar las etiquetas (como texto 3D en el espacio global) para mostrar estas etiquetas en la ubicación que se tomó la fotografía.</span><span class="sxs-lookup"><span data-stu-id="ab19c-275">You will use Labels (as a 3D text in world space) to display these Tags at the location the photo was taken.</span></span>

<span data-ttu-id="ab19c-276">Los pasos siguientes muestran cómo configurar el **etiqueta** objeto.</span><span class="sxs-lookup"><span data-stu-id="ab19c-276">The following steps will show how to setup the **Label** object.</span></span>

1.  <span data-ttu-id="ab19c-277">Haga doble clic en cualquier lugar en la jerarquía de Panel (la ubicación no importa en este momento), en **objeto 3D**, agregue un **texto 3D**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-277">Right-click anywhere in the Hierarchy Panel (the location does not matter at this point), under **3D Object**, add a **3D Text**.</span></span> <span data-ttu-id="ab19c-278">Asígnele el nombre **LabelText**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-278">Name it **LabelText**.</span></span>

    ![Crear objeto de texto 3D.](images/AzureLabs-Lab2-21.png)
 
2.  <span data-ttu-id="ab19c-280">En el *jerarquía Panel*, haga clic en el **LabelText**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-280">In the *Hierarchy Panel*, left click on the **LabelText**.</span></span> <span data-ttu-id="ab19c-281">Con el **LabelText** seleccionado, ajustar las siguientes variables en el *Panel Inspector*:</span><span class="sxs-lookup"><span data-stu-id="ab19c-281">With the **LabelText** selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="ab19c-282">Establecer el **posición** a **0,0,0**</span><span class="sxs-lookup"><span data-stu-id="ab19c-282">Set the **Position** to **0,0,0**</span></span>
    2. <span data-ttu-id="ab19c-283">Establecer el **escala** a **0,01, 0,01, 0,01**</span><span class="sxs-lookup"><span data-stu-id="ab19c-283">Set the **Scale** to **0.01, 0.01, 0.01**</span></span>
    3. <span data-ttu-id="ab19c-284">En el componente **texto de la malla**:</span><span class="sxs-lookup"><span data-stu-id="ab19c-284">In the component **Text Mesh**:</span></span>
    4. <span data-ttu-id="ab19c-285">Reemplace todo el texto dentro de **texto**, con "..."</span><span class="sxs-lookup"><span data-stu-id="ab19c-285">Replace all the text within **Text**, with "..."</span></span>        
    5. <span data-ttu-id="ab19c-286">Establecer el **delimitador** a **intermedio central**</span><span class="sxs-lookup"><span data-stu-id="ab19c-286">Set the **Anchor** to **Middle Center**</span></span>
    6. <span data-ttu-id="ab19c-287">Establecer el **alineación** a **Center**</span><span class="sxs-lookup"><span data-stu-id="ab19c-287">Set the **Alignment** to **Center**</span></span>
    7. <span data-ttu-id="ab19c-288">Establecer el **tamaño de tabulación** a **4**</span><span class="sxs-lookup"><span data-stu-id="ab19c-288">Set the **Tab Size** to **4**</span></span>
    8. <span data-ttu-id="ab19c-289">Establecer el **tamaño de fuente** a **50**</span><span class="sxs-lookup"><span data-stu-id="ab19c-289">Set the **Font Size** to **50**</span></span>
    9. <span data-ttu-id="ab19c-290">Establecer el **Color** a **#FFFFFFFF**</span><span class="sxs-lookup"><span data-stu-id="ab19c-290">Set the **Color** to **#FFFFFFFF**</span></span>

    ![Componente de texto](images/AzureLabs-Lab2-21-5.png)

3.  <span data-ttu-id="ab19c-292">Arrastre el **LabelText** desde el *Panel de la jerarquía*, en el *carpeta de activos*, en el *Panel del proyecto*.</span><span class="sxs-lookup"><span data-stu-id="ab19c-292">Drag the **LabelText** from the *Hierarchy Panel*, into the *Asset Folder*, within in the *Project Panel*.</span></span> <span data-ttu-id="ab19c-293">Esto hará que el **LabelText** un prefabricado, por lo que TI se puede crear instancias en el código.</span><span class="sxs-lookup"><span data-stu-id="ab19c-293">This will make the **LabelText** a Prefab, so that it can be instantiated in code.</span></span>

    ![Creación de un prefabricado del objeto LabelText.](images/AzureLabs-Lab2-22.png)
 
4.  <span data-ttu-id="ab19c-295">Debe eliminar el **LabelText** desde el *jerarquía Panel*, de modo que no se mostrará en la escena de apertura.</span><span class="sxs-lookup"><span data-stu-id="ab19c-295">You should delete the **LabelText** from the *Hierarchy Panel*, so that it will not be displayed in the opening scene.</span></span> <span data-ttu-id="ab19c-296">Ya que es ahora un prefabricado, que llamará en para las instancias individuales de la carpeta de activos, no hay ninguna necesidad para mantenerlo dentro de la escena.</span><span class="sxs-lookup"><span data-stu-id="ab19c-296">As it is now a prefab, which you will call on for individual instances from your Assets folder, there is no need to keep it within the scene.</span></span> 
5.  <span data-ttu-id="ab19c-297">La estructura del objeto final en el *jerarquía Panel* debe ser como se muestra en la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="ab19c-297">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![Estructura final del panel de la jerarquía.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a><span data-ttu-id="ab19c-299">Capítulo 5: crear la clase de etiqueta resultados</span><span class="sxs-lookup"><span data-stu-id="ab19c-299">Chapter 5 – Create the ResultsLabel class</span></span>

<span data-ttu-id="ab19c-300">Es el primer script, deberá crear el *etiqueta resultados* (clase), que es responsable de lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="ab19c-300">The first script you need to create is the *ResultsLabel* class, which is responsible for the following:</span></span> 

- <span data-ttu-id="ab19c-301">Creación de las etiquetas en el espacio adecuado del mundo, con respecto a la posición de la cámara.</span><span class="sxs-lookup"><span data-stu-id="ab19c-301">Creating the Labels in the appropriate world space, relative to the position of the Camera.</span></span>
- <span data-ttu-id="ab19c-302">Mostrar las etiquetas de la ardua de imagen.</span><span class="sxs-lookup"><span data-stu-id="ab19c-302">Displaying the Tags from the Image Anaysis.</span></span>

<span data-ttu-id="ab19c-303">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="ab19c-303">To create this class:</span></span> 

1.  <span data-ttu-id="ab19c-304">Haga clic en el *Panel del proyecto*, a continuación, **crear > carpeta**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-304">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="ab19c-305">Nombre de la carpeta **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-305">Name the folder **Scripts**.</span></span> 

    ![Crear carpeta de scripts.](images/AzureLabs-Lab2-24.png)

2.  <span data-ttu-id="ab19c-307">Con el **Scripts** carpeta crear, haga doble clic en él para abrirlo.</span><span class="sxs-lookup"><span data-stu-id="ab19c-307">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="ab19c-308">A continuación, dentro de esa carpeta, contextual y seleccione **crear >** , a continuación,  **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-308">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="ab19c-309">Nombre de la secuencia de comandos *etiqueta resultados*.</span><span class="sxs-lookup"><span data-stu-id="ab19c-309">Name the script *ResultsLabel*.</span></span> 

3.  <span data-ttu-id="ab19c-310">Haga doble clic en el nuevo *etiqueta resultados* script para abrirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-310">Double click on the new *ResultsLabel* script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="ab19c-311">Dentro de la clase, inserte el código siguiente en el *etiqueta resultados* clase:</span><span class="sxs-lookup"><span data-stu-id="ab19c-311">Inside the Class insert the following code in the *ResultsLabel* class:</span></span>

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

6.  <span data-ttu-id="ab19c-312">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="ab19c-312">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
7.  <span data-ttu-id="ab19c-313">En el *Editor de Unity*, haga clic y arrastre el *etiqueta resultados* clase desde el **Scripts** carpeta a la **cámara principal** objeto en el  *Panel de la jerarquía*.</span><span class="sxs-lookup"><span data-stu-id="ab19c-313">Back in the *Unity Editor*, click and drag the *ResultsLabel* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
8.  <span data-ttu-id="ab19c-314">Haga clic en el **cámara principal** y examine el *Panel Inspector*.</span><span class="sxs-lookup"><span data-stu-id="ab19c-314">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span>

<span data-ttu-id="ab19c-315">Observará que, desde la secuencia de comandos que acaba de arrastrar a la cámara, hay dos campos: **Cursor** y **etiquetar prefabricado**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-315">You will notice that from the script you just dragged into the Camera, there are two fields: **Cursor** and **Label Prefab**.</span></span>

9.  <span data-ttu-id="ab19c-316">Arrastre el objeto llamado **Cursor** desde el *jerarquía Panel* a la ranura denominada **Cursor**, tal y como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="ab19c-316">Drag the object called **Cursor** from the *Hierarchy Panel* to the slot named **Cursor**, as shown in the image below.</span></span>
10. <span data-ttu-id="ab19c-317">Arrastre el objeto llamado **LabelText** desde el *carpeta Assets* en el *Panel proyecto* a la ranura denominada **etiqueta prefabricado**, tal y como se muestra en el imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="ab19c-317">Drag the object called **LabelText** from the *Assets Folder* in the *Project Panel* to the slot named **Label Prefab**, as shown in the image below.</span></span> 

    ![Establecer los destinos de referencia dentro de Unity.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a><span data-ttu-id="ab19c-319">Capítulo 6: crear la clase ImageCapture</span><span class="sxs-lookup"><span data-stu-id="ab19c-319">Chapter 6 – Create the ImageCapture class</span></span>

<span data-ttu-id="ab19c-320">La siguiente clase que se va a crear es la *ImageCapture* clase.</span><span class="sxs-lookup"><span data-stu-id="ab19c-320">The next class you are going to create is the *ImageCapture* class.</span></span> <span data-ttu-id="ab19c-321">Esta clase es responsable de:</span><span class="sxs-lookup"><span data-stu-id="ab19c-321">This class is responsible for:</span></span>

-   <span data-ttu-id="ab19c-322">Capturar una imagen con la cámara de HoloLens y almacenarla en la carpeta de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ab19c-322">Capturing an Image using the HoloLens Camera and storing it in the App Folder.</span></span>
-   <span data-ttu-id="ab19c-323">Captura de derivación de gestos del usuario.</span><span class="sxs-lookup"><span data-stu-id="ab19c-323">Capturing Tap gestures from the user.</span></span>

<span data-ttu-id="ab19c-324">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="ab19c-324">To create this class:</span></span> 

1.  <span data-ttu-id="ab19c-325">Vaya a la **Scripts** carpeta que creó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="ab19c-325">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="ab19c-326">Haga clic en la carpeta, **crear > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-326">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="ab19c-327">Llame al script *ImageCapture*.</span><span class="sxs-lookup"><span data-stu-id="ab19c-327">Call the script *ImageCapture*.</span></span> 
3.  <span data-ttu-id="ab19c-328">Haga doble clic en el nuevo *ImageCapture* script para abrirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-328">Double click on the new *ImageCapture* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="ab19c-329">Agregue los siguientes espacios de nombres en la parte superior del archivo:</span><span class="sxs-lookup"><span data-stu-id="ab19c-329">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="ab19c-330">A continuación, agregue las siguientes variables dentro de la *ImageCapture* clase encima el *Start()* método:</span><span class="sxs-lookup"><span data-stu-id="ab19c-330">Then add the following variables inside the *ImageCapture* class, above the *Start()* method:</span></span>

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
<span data-ttu-id="ab19c-331">El **tapsCount** variable almacenará el número de movimientos de tap capturados desde el usuario.</span><span class="sxs-lookup"><span data-stu-id="ab19c-331">The **tapsCount** variable will store the number of tap gestures captured from the user.</span></span> <span data-ttu-id="ab19c-332">Este número se usa en la denominación de las imágenes de captura.</span><span class="sxs-lookup"><span data-stu-id="ab19c-332">This number is used in the naming of the images captured.</span></span>

6.  <span data-ttu-id="ab19c-333">El código para *Awake()* y *Start()* métodos ahora debe agregarse.</span><span class="sxs-lookup"><span data-stu-id="ab19c-333">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="ab19c-334">Estos se llamará cuando se inicializa la clase:</span><span class="sxs-lookup"><span data-stu-id="ab19c-334">These will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="ab19c-335">Implemente un controlador que se llamará cuando se produce un gesto de pulsar.</span><span class="sxs-lookup"><span data-stu-id="ab19c-335">Implement a handler that will be called when a Tap gesture occurs.</span></span> 

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
 
<span data-ttu-id="ab19c-336">El *TapHandler()* método incrementa el número de pesos capturados desde el usuario y la posición actual del Cursor se utiliza para determinar dónde colocar una etiqueta nueva.</span><span class="sxs-lookup"><span data-stu-id="ab19c-336">The *TapHandler()* method increments the number of taps captured from the user and uses the current Cursor position to determine where to position a new Label.</span></span>

<span data-ttu-id="ab19c-337">A continuación, llama a este método la *ExecuteImageCaptureAndAnalysis()* método para comenzar la funcionalidad básica de esta aplicación.</span><span class="sxs-lookup"><span data-stu-id="ab19c-337">This method then calls the *ExecuteImageCaptureAndAnalysis()* method to begin the core functionality of this application.</span></span>

8.  <span data-ttu-id="ab19c-338">Una vez capturada y almacena una imagen, se llamará los siguientes controladores.</span><span class="sxs-lookup"><span data-stu-id="ab19c-338">Once an Image has been captured and stored, the following handlers will be called.</span></span> <span data-ttu-id="ab19c-339">Si el proceso se realiza correctamente, el resultado se pasa a la *VisionManager* (que aún están crear) para el análisis.</span><span class="sxs-lookup"><span data-stu-id="ab19c-339">If the process is successful, the result is passed to the *VisionManager* (which you are yet to create) for analysis.</span></span>

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
 
9.  <span data-ttu-id="ab19c-340">A continuación, agregue el método que utiliza la aplicación para iniciar el proceso de captura de imagen y almacenar la imagen.</span><span class="sxs-lookup"><span data-stu-id="ab19c-340">Then add the method that the application uses to start the Image capture process and store the image.</span></span>

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
> <span data-ttu-id="ab19c-341">En este momento aparece un error que aparecen en la *Panel de consola del Editor de Unity*.</span><span class="sxs-lookup"><span data-stu-id="ab19c-341">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="ab19c-342">Esto es porque el código hace referencia a la *VisionManager* clase que se creará en el próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="ab19c-342">This is because the code references the *VisionManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-image-analysis"></a><span data-ttu-id="ab19c-343">Capítulo 7: llamada a Azure y análisis de imágenes</span><span class="sxs-lookup"><span data-stu-id="ab19c-343">Chapter 7 – Call to Azure and Image Analysis</span></span>

<span data-ttu-id="ab19c-344">Es el último script, deberá crear el *VisionManager* clase.</span><span class="sxs-lookup"><span data-stu-id="ab19c-344">The last script you need to create is the *VisionManager* class.</span></span> 

<span data-ttu-id="ab19c-345">Esta clase es responsable de:</span><span class="sxs-lookup"><span data-stu-id="ab19c-345">This class is responsible for:</span></span>

-   <span data-ttu-id="ab19c-346">Cargando la última imagen de captura como una matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="ab19c-346">Loading the latest image captured as an array of bytes.</span></span>
-   <span data-ttu-id="ab19c-347">Envío de la matriz de bytes para su *Azure Computer Vision API* instancia de servicio para el análisis.</span><span class="sxs-lookup"><span data-stu-id="ab19c-347">Sending the byte array to your *Azure Computer Vision API* Service instance for analysis.</span></span>
-   <span data-ttu-id="ab19c-348">Recibir la respuesta como una cadena JSON.</span><span class="sxs-lookup"><span data-stu-id="ab19c-348">Receiving the response as a JSON string.</span></span>
-   <span data-ttu-id="ab19c-349">Al deserializar la respuesta y pasar las etiquetas resultantes a la *etiqueta resultados* clase.</span><span class="sxs-lookup"><span data-stu-id="ab19c-349">Deserializing the response and passing the resulting Tags to the *ResultsLabel* class.</span></span>
 
<span data-ttu-id="ab19c-350">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="ab19c-350">To create this class:</span></span>

1.  <span data-ttu-id="ab19c-351">Haga doble clic en el **Scripts** carpeta para abrirla.</span><span class="sxs-lookup"><span data-stu-id="ab19c-351">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="ab19c-352">Haga clic en el **Scripts** carpeta, haga clic en **crear > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-352">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="ab19c-353">Nombre de la secuencia de comandos *VisionManager*.</span><span class="sxs-lookup"><span data-stu-id="ab19c-353">Name the script *VisionManager*.</span></span> 
3.  <span data-ttu-id="ab19c-354">Haga doble clic en el nuevo script para abrirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ab19c-354">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="ab19c-355">Actualice los espacios de nombres para que sea igual a lo siguiente en la parte superior de la *VisionManager* clase:</span><span class="sxs-lookup"><span data-stu-id="ab19c-355">Update the namespaces to be the same as the following, at the top of the *VisionManager* class:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  <span data-ttu-id="ab19c-356">En la parte superior de la secuencia de comandos, *dentro de* el *VisionManager* clase (anteriormente el *Start()* método), ahora debe crear dos *clases* que representa la respuesta JSON deserializada de Azure:</span><span class="sxs-lookup"><span data-stu-id="ab19c-356">At the top of your script, *inside* the *VisionManager* class (above the *Start()* method), you now need to create two *Classes* that will represent the deserialized JSON response from Azure:</span></span>

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
    > <span data-ttu-id="ab19c-357">El *TagData* y *AnalysedObject* clases deben tener la *[System.Serializable]* atributo agregado antes de la declaración se pueda deserializar con la de Unity bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="ab19c-357">The *TagData* and *AnalysedObject* classes need to have the *[System.Serializable]* attribute added before the declaration to be able to be deserialized with the Unity libraries.</span></span>

6.  <span data-ttu-id="ab19c-358">En la clase VisionManager, debe agregar las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="ab19c-358">In the VisionManager class, you should add the following variables:</span></span>

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
    > <span data-ttu-id="ab19c-359">Asegúrese de insertar el **Auth Key** en el **authorizationKey** variable.</span><span class="sxs-lookup"><span data-stu-id="ab19c-359">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span> <span data-ttu-id="ab19c-360">Habrá anotó la **Auth Key** al principio de este curso, [capítulo 1](#chapter-1--the-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="ab19c-360">You will have noted your **Auth Key** at the beginning of this course, [Chapter 1](#chapter-1--the-azure-portal).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="ab19c-361">El **visionAnalysisEndpoint** variable puede diferir de lo especificado en este ejemplo.</span><span class="sxs-lookup"><span data-stu-id="ab19c-361">The **visionAnalysisEndpoint** variable might differ from the one specified in this example.</span></span> <span data-ttu-id="ab19c-362">El **oeste-EE** estrictamente hace referencia a instancias de servicio creadas para la región Oeste de Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="ab19c-362">The **west-us** strictly refers to Service instances created for the West US region.</span></span> <span data-ttu-id="ab19c-363">Actualícelo con su [dirección URL del extremo](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); aquí son algunos ejemplos de lo que podrían ser similar a:</span><span class="sxs-lookup"><span data-stu-id="ab19c-363">Update this with your [endpoint URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); here are some examples of what that might look like:</span></span>
    > - <span data-ttu-id="ab19c-364">Europa occidental: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="ab19c-364">West Europe: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="ab19c-365">Sudeste de Asia: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="ab19c-365">Southeast Asia: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="ab19c-366">Este de Australia: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="ab19c-366">Australia East: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>

7.  <span data-ttu-id="ab19c-367">Código para Awake ahora debe agregarse.</span><span class="sxs-lookup"><span data-stu-id="ab19c-367">Code for Awake now needs to be added.</span></span> 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  <span data-ttu-id="ab19c-368">A continuación, agregue la corrutina (con el método estático secuencia debajo de él), que se va a obtener los resultados del análisis de la imagen capturada por la *ImageCapture* clase.</span><span class="sxs-lookup"><span data-stu-id="ab19c-368">Next, add the coroutine (with the static stream method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* Class.</span></span> 

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

9.  <span data-ttu-id="ab19c-369">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="ab19c-369">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
10. <span data-ttu-id="ab19c-370">En el Editor de Unity, haga clic en Atrás y arrastre el *VisionManager* y *ImageCapture* clases a partir de la **Scripts** carpeta a la **cámara principal**objeto en el *jerarquía Panel*.</span><span class="sxs-lookup"><span data-stu-id="ab19c-370">Back in the Unity Editor, click and drag the *VisionManager* and *ImageCapture* classes from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 

## <a name="chapter-8--before-building"></a><span data-ttu-id="ab19c-371">Capítulo 8 antes de compilar</span><span class="sxs-lookup"><span data-stu-id="ab19c-371">Chapter 8 – Before building</span></span>

<span data-ttu-id="ab19c-372">Para llevar a cabo una prueba completa de la aplicación se necesitará para transferir localmente en su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ab19c-372">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="ab19c-373">Antes de hacerlo, asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="ab19c-373">Before you do, ensure that:</span></span>

-   <span data-ttu-id="ab19c-374">Todas las configuraciones que se mencionan en [capítulo 2](#chapter-2--set-up-the-unity-project) están establecidas correctamente.</span><span class="sxs-lookup"><span data-stu-id="ab19c-374">All the settings mentioned in [Chapter 2](#chapter-2--set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="ab19c-375">Todos los scripts están conectados a la **cámara principal** objeto.</span><span class="sxs-lookup"><span data-stu-id="ab19c-375">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="ab19c-376">Todos los campos de la *Panel de Inspector de cámara principal* se asignan correctamente.</span><span class="sxs-lookup"><span data-stu-id="ab19c-376">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
-   <span data-ttu-id="ab19c-377">Asegúrese de insertar el **Auth Key** en el **authorizationKey** variable.</span><span class="sxs-lookup"><span data-stu-id="ab19c-377">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span>
-   <span data-ttu-id="ab19c-378">Asegúrese de que también ha comprobado el punto de conexión su *VisionManager* script y que se alinea con *su* región (este documento usa *west-nos* de forma predeterminada).</span><span class="sxs-lookup"><span data-stu-id="ab19c-378">Ensure that you have also checked your endpoint in your *VisionManager* script, and that it aligns to *your* region (this document uses *west-us* by default).</span></span>

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a><span data-ttu-id="ab19c-379">Capítulo 9: compilar la solución de UWP y transferir localmente la aplicación</span><span class="sxs-lookup"><span data-stu-id="ab19c-379">Chapter 9 – Build the UWP Solution and sideload the application</span></span>
<span data-ttu-id="ab19c-380">Todo lo necesario para la sección de Unity de este proyecto ahora se completó, por lo que es el momento de crearla desde Unity.</span><span class="sxs-lookup"><span data-stu-id="ab19c-380">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="ab19c-381">Vaya a *configuración de compilación* - **archivo > configuración de compilación...**</span><span class="sxs-lookup"><span data-stu-id="ab19c-381">Navigate to *Build Settings* - **File > Build Settings…**</span></span>
2.  <span data-ttu-id="ab19c-382">Desde el *configuración de compilación* ventana, haga clic en **compilar**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-382">From the *Build Settings* window, click **Build**.</span></span>

    ![Creación de la aplicación de Unity](images/AzureLabs-Lab2-26.png)

3.  <span data-ttu-id="ab19c-384">Si aún no marque **Unity C# proyectos**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-384">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="ab19c-385">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-385">Click **Build**.</span></span> <span data-ttu-id="ab19c-386">Unity se iniciará un *Explorador de archivos* ventana, donde se debe crear y, a continuación, seleccione una carpeta para compilar la aplicación en.</span><span class="sxs-lookup"><span data-stu-id="ab19c-386">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="ab19c-387">Crear la carpeta y asígnele el nombre *aplicación*.</span><span class="sxs-lookup"><span data-stu-id="ab19c-387">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="ab19c-388">A continuación, con el *aplicación* carpeta seleccionada, presione **seleccionar la carpeta**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-388">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="ab19c-389">Unity empezará a compilar el proyecto para el *aplicación* carpeta.</span><span class="sxs-lookup"><span data-stu-id="ab19c-389">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="ab19c-390">Una vez Unity ha finalizado la compilación (puede tardar algún tiempo), se abrirá un *Explorador de archivos* ventana en la ubicación de la compilación (comprobación de la barra de tareas, tal y como es posible que no siempre aparecen por encima de las ventanas, pero le informará de la adición de un nuevo ventana).</span><span class="sxs-lookup"><span data-stu-id="ab19c-390">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-10--deploy-to-hololens"></a><span data-ttu-id="ab19c-391">Capítulo 10: implementar en HoloLens</span><span class="sxs-lookup"><span data-stu-id="ab19c-391">Chapter 10 – Deploy to HoloLens</span></span>

<span data-ttu-id="ab19c-392">Para implementar en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="ab19c-392">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="ab19c-393">Necesitará la dirección IP de su HoloLens (para la implementación remota), y garantizar su HoloLens se encuentra en **modo de programador**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-393">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="ab19c-394">Para ello:</span><span class="sxs-lookup"><span data-stu-id="ab19c-394">To do this:</span></span>

    1. <span data-ttu-id="ab19c-395">Mientras que el exceso de su HoloLens, abra el **configuración**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-395">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="ab19c-396">Vaya a **red e Internet > Wi-Fi > Opciones avanzadas**</span><span class="sxs-lookup"><span data-stu-id="ab19c-396">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="ab19c-397">Tenga en cuenta la **IPv4** dirección.</span><span class="sxs-lookup"><span data-stu-id="ab19c-397">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="ab19c-398">A continuación, vaya a **configuración**y, a continuación, para **actualización y seguridad > para desarrolladores**</span><span class="sxs-lookup"><span data-stu-id="ab19c-398">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="ab19c-399">Activar el modo de programador.</span><span class="sxs-lookup"><span data-stu-id="ab19c-399">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="ab19c-400">Vaya a la nueva compilación de Unity (la *aplicación* carpeta) y abra el archivo de solución con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="ab19c-400">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="ab19c-401">En, seleccione la configuración de la solución **depurar**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-401">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="ab19c-402">En la plataforma de soluciones, seleccione **x86**, **máquina remota**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-402">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![Implementar la solución de Visual Studio.](images/AzureLabs-Lab2-27.png)
 
5.  <span data-ttu-id="ab19c-404">Vaya a la **menú compilar** y haga clic en **implementar solución**, para transferir localmente la aplicación a su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ab19c-404">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="ab19c-405">La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas en su HoloLens, lista para iniciarse.</span><span class="sxs-lookup"><span data-stu-id="ab19c-405">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="ab19c-406">Para implementar en los auriculares envolventes, establezca el **plataforma de solución** a *máquina Local*y establezca el **configuración** a *depurar*, con *x86* como el **plataforma**.</span><span class="sxs-lookup"><span data-stu-id="ab19c-406">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="ab19c-407">Implementar, a continuación, en el equipo local machine, utilizando el **menú compilar**, seleccionar *implementar solución*.</span><span class="sxs-lookup"><span data-stu-id="ab19c-407">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="your-finished-computer-vision-api-application"></a><span data-ttu-id="ab19c-408">La aplicación finalizada de Computer Vision API</span><span class="sxs-lookup"><span data-stu-id="ab19c-408">Your finished Computer Vision API application</span></span>

<span data-ttu-id="ab19c-409">Enhorabuena, creó una aplicación de realidad mixta que aprovecha Azure Computer Vision API para reconocer objetos del mundo real y mostrar la confianza de lo que se ha visto.</span><span class="sxs-lookup"><span data-stu-id="ab19c-409">Congratulations, you built a mixed reality app that leverages the Azure Computer Vision API to recognize real world objects, and display confidence of what has been seen.</span></span>

![Resultado de laboratorio](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="ab19c-411">Ejercicios de bonificación</span><span class="sxs-lookup"><span data-stu-id="ab19c-411">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="ab19c-412">Ejercicio 1</span><span class="sxs-lookup"><span data-stu-id="ab19c-412">Exercise 1</span></span>

<span data-ttu-id="ab19c-413">Tal como ha usado el *etiquetas* parámetro (tal como se evidencia dentro de la *extremo* utilizado dentro de la *VisionManager*), amplíe la aplicación para detectar la información de otro; Eche un vistazo a ¿Qué otros parámetros que tienen acceso a [aquí](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span><span class="sxs-lookup"><span data-stu-id="ab19c-413">Just as you have used the *Tags* parameter (as evidenced within the *endpoint* used within the *VisionManager*), extend the app to detect other information; have a look at what other parameters you have access to [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span>

### <a name="exercise-2"></a><span data-ttu-id="ab19c-414">Ejercicio 2</span><span class="sxs-lookup"><span data-stu-id="ab19c-414">Exercise 2</span></span>

<span data-ttu-id="ab19c-415">Mostrar los datos devueltos de Azure, de forma más conversacional y legible, quizás ocultando los números.</span><span class="sxs-lookup"><span data-stu-id="ab19c-415">Display the returned Azure data, in a more conversational, and readable way, perhaps hiding the numbers.</span></span> <span data-ttu-id="ab19c-416">Como si es posible que se habla un bot al usuario.</span><span class="sxs-lookup"><span data-stu-id="ab19c-416">As though a bot might be speaking to the user.</span></span>
