---
title: El Sr. y Azure 302b - visión personalizada
description: Complete este curso para obtener información sobre cómo entrenar un modelo de aprendizaje automático y, a continuación, use el modelo entrenado para reconocer objetos similares dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/03/2018
ms.topic: article
keywords: realidad mixta, Azure, academy, unity, tutorial, api, visión personalizada, hololens, envolventes, vr
ms.openlocfilehash: e6e9782a8d559af660dc4765556f1e926c5360b1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599998"
---
>[!NOTE]
><span data-ttu-id="99afd-104">Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.</span><span class="sxs-lookup"><span data-stu-id="99afd-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="99afd-105">Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="99afd-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="99afd-106">Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.</span><span class="sxs-lookup"><span data-stu-id="99afd-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="99afd-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="99afd-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="99afd-108">Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="99afd-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="99afd-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.</span><span class="sxs-lookup"><span data-stu-id="99afd-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-302b-custom-vision"></a><span data-ttu-id="99afd-110">El Sr. y 302b Azure: Visión personalizada</span><span class="sxs-lookup"><span data-stu-id="99afd-110">MR and Azure 302b: Custom vision</span></span>

<span data-ttu-id="99afd-111">En este curso, obtendrá información sobre cómo reconocer contenido visual personalizado dentro de una imagen proporcionada, con las funciones de visión personalizada de Azure en una aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="99afd-111">In this course, you will learn how to recognize custom visual content within a provided image, using Azure Custom Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="99afd-112">Este servicio, podrá entrenar un modelo de aprendizaje automático mediante imágenes de objeto.</span><span class="sxs-lookup"><span data-stu-id="99afd-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="99afd-113">A continuación, usará el modelo entrenado para reconocer objetos similares, tal como lo proporciona la captura de cámara de Microsoft HoloLens o una cámara conectada a su equipo para inmersivos (VR).</span><span class="sxs-lookup"><span data-stu-id="99afd-113">You will then use the trained model to recognize similar objects, as provided by the camera capture of Microsoft HoloLens or a camera connected to your PC for immersive (VR) headsets.</span></span>

![resultado del curso](images/AzureLabs-Lab302b-00.png)

<span data-ttu-id="99afd-115">Azure Custom Vision es un servicio de Microsoft Cognitive que permite a los desarrolladores crear clasificadores de imagen personalizada.</span><span class="sxs-lookup"><span data-stu-id="99afd-115">Azure Custom Vision is a Microsoft Cognitive Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="99afd-116">A continuación, pueden utilizarse con las nuevas imágenes para reconocer estos clasificadores o clasificación objetos dentro de esa imagen.</span><span class="sxs-lookup"><span data-stu-id="99afd-116">These classifiers can then be used with new images to recognize, or classify, objects within that new image.</span></span> <span data-ttu-id="99afd-117">El servicio proporciona un portal fácil de usar, sencillo y en línea para agilizar el proceso.</span><span class="sxs-lookup"><span data-stu-id="99afd-117">The Service provides a simple, easy to use, online portal to streamline the process.</span></span> <span data-ttu-id="99afd-118">Para obtener más información, visite la [página Azure Custom Vision Service](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span><span class="sxs-lookup"><span data-stu-id="99afd-118">For more information, visit the [Azure Custom Vision Service page](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span></span>

<span data-ttu-id="99afd-119">Tras la finalización de este curso, tendrá una aplicación de realidad mixta que podrá trabajar en dos modos:</span><span class="sxs-lookup"><span data-stu-id="99afd-119">Upon completion of this course, you will have a mixed reality application which will be able to work in two modes:</span></span>

-   <span data-ttu-id="99afd-120">**Modo de análisis**: configuración de Custom Vision Service manualmente mediante la carga de imágenes, crear etiquetas y el servicio de entrenamiento para reconocer objetos diferentes (en este caso mouse y teclado).</span><span class="sxs-lookup"><span data-stu-id="99afd-120">**Analysis Mode**: setting up the Custom Vision Service manually by uploading images, creating tags, and training the Service to recognize different objects (in this case mouse and keyboard).</span></span> <span data-ttu-id="99afd-121">A continuación, creará una aplicación de HoloLens que se captura de imágenes con la cámara e intenta reconocer esos objetos en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="99afd-121">You will then create a HoloLens app that will capture images using the camera, and try to recognize those objects in the real world.</span></span>

-   <span data-ttu-id="99afd-122">**Modo de formación**: implementará código que le permitirán un "modo de aprendizaje" en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="99afd-122">**Training Mode**: you will implement code that will enable a "Training Mode" in your app.</span></span> <span data-ttu-id="99afd-123">El modo de formación, podrá capturar imágenes con la cámara de HoloLens, cargar las imágenes capturadas en el servicio y entrenar el modelo de visión personalizada.</span><span class="sxs-lookup"><span data-stu-id="99afd-123">The training mode will allow you to capture images using the HoloLens' camera, upload the captured images to the Service, and train the custom vision model.</span></span>

<span data-ttu-id="99afd-124">Este curso le mostrará cómo obtener los resultados de Custom Vision Service en una aplicación de ejemplo basada en Unity.</span><span class="sxs-lookup"><span data-stu-id="99afd-124">This course will teach you how to get the results from the Custom Vision Service into a Unity-based sample application.</span></span> <span data-ttu-id="99afd-125">Será quien decide estos conceptos se aplican a una aplicación personalizada puede que esté creando.</span><span class="sxs-lookup"><span data-stu-id="99afd-125">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="99afd-126">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="99afd-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="99afd-127">Curso</span><span class="sxs-lookup"><span data-stu-id="99afd-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="99afd-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="99afd-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="99afd-129"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="99afd-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="99afd-130">El Sr. y 302b Azure: Visión personalizada</span><span class="sxs-lookup"><span data-stu-id="99afd-130">MR and Azure 302b: Custom vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="99afd-131">✔️</span><span class="sxs-lookup"><span data-stu-id="99afd-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="99afd-132">✔️</span><span class="sxs-lookup"><span data-stu-id="99afd-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="99afd-133">Aunque este curso se centra principalmente en HoloLens, también puede aplicar lo aprendido en este curso a inmersivos (VR) Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="99afd-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="99afd-134">Dado que inmersivos (VR) no tienen cámaras accesible, necesitará una cámara externa conectada a su PC.</span><span class="sxs-lookup"><span data-stu-id="99afd-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="99afd-135">Como seguir el curso, verá las notas de la de los cambios que deberá emplear para admitir inmersivos (VR).</span><span class="sxs-lookup"><span data-stu-id="99afd-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="99afd-136">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="99afd-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="99afd-137">Este tutorial está diseñado para los desarrolladores con experiencia básica con Unity y C#.</span><span class="sxs-lookup"><span data-stu-id="99afd-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="99afd-138">También Ten en cuenta que los requisitos previos y las instrucciones escritas en este documento representan lo que se ha probado y comprobado en el momento de redactar (julio de 2018).</span><span class="sxs-lookup"><span data-stu-id="99afd-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="99afd-139">Es libre de usar el software más reciente, como se muestra en el [instalar las herramientas de](install-the-tools.md) artículo, aunque no se debe suponer que la información de este curso perfectamente coincida con lo que encontrará en el software más reciente que se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="99afd-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="99afd-140">Se recomiendan el siguiente hardware y software para este curso:</span><span class="sxs-lookup"><span data-stu-id="99afd-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="99afd-141">Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desarrollo de auriculares envolvente (VR)</span><span class="sxs-lookup"><span data-stu-id="99afd-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="99afd-142">Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="99afd-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="99afd-143">El SDK más reciente de Windows 10</span><span class="sxs-lookup"><span data-stu-id="99afd-143">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="99afd-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="99afd-144">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="99afd-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="99afd-145">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="99afd-146">Un [auriculares de Windows Mixed Reality envolventes (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="99afd-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="99afd-147">Una cámara conectada a su equipo (para el desarrollo de amplias auriculares)</span><span class="sxs-lookup"><span data-stu-id="99afd-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="99afd-148">Acceso a Internet para el programa de instalación de Azure y la recuperación de Custom Vision API</span><span class="sxs-lookup"><span data-stu-id="99afd-148">Internet access for Azure setup and Custom Vision API retrieval</span></span>
- <span data-ttu-id="99afd-149">Una serie de imágenes de al menos cinco (5) (¡diez (10) recomienda) para cada objeto que le gustaría Custom Vision Service para que reconozca.</span><span class="sxs-lookup"><span data-stu-id="99afd-149">A series of at least five (5) images (ten (10) recommended) for each object that you would like the Custom Vision Service to recognize.</span></span> <span data-ttu-id="99afd-150">Si lo desea, puede usar [las imágenes que ya se proporciona con este curso (un mouse y teclado) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span><span class="sxs-lookup"><span data-stu-id="99afd-150">If you wish, you can use [the images already provided with this course (a computer mouse and a keyboard) ](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="99afd-151">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="99afd-151">Before you start</span></span>

1.  <span data-ttu-id="99afd-152">Para evitar problemas de creación de este proyecto, se recomienda encarecidamente que cree el proyecto se ha mencionado en este tutorial en una carpeta raíz o cerca de la raíz (rutas de acceso de carpeta largo pueden causar problemas en tiempo de compilación).</span><span class="sxs-lookup"><span data-stu-id="99afd-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="99afd-153">Configurar y probar su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="99afd-153">Set up and test your HoloLens.</span></span> <span data-ttu-id="99afd-154">Si necesita admite la configuración de su HoloLens, [Asegúrese de visitar el artículo del programa de instalación de HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="99afd-154">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="99afd-155">Es una buena idea para realizar la calibración y optimización Sensor cuando comienza a desarrollar una nueva aplicación de HoloLens (a veces puede ayudar a realizar dichas tareas para cada usuario).</span><span class="sxs-lookup"><span data-stu-id="99afd-155">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="99afd-156">Para obtener ayuda sobre la calibración, siga este [vínculo al artículo de calibración de HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="99afd-156">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="99afd-157">Para obtener ayuda sobre optimización Sensor, siga este [vínculo al artículo optimización Sensor de HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="99afd-157">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-service-portal"></a><span data-ttu-id="99afd-158">Capítulo 1: Custom Vision Service Portal</span><span class="sxs-lookup"><span data-stu-id="99afd-158">Chapter 1 - The Custom Vision Service Portal</span></span>

<span data-ttu-id="99afd-159">Para usar el *Custom Vision Service* en Azure, deberá configurar una instancia del servicio esté disponible para su aplicación.</span><span class="sxs-lookup"><span data-stu-id="99afd-159">To use the *Custom Vision Service* in Azure, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="99afd-160">Primero, [vaya a la *Custom Vision Service* página principal](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span><span class="sxs-lookup"><span data-stu-id="99afd-160">First, [navigate to the *Custom Vision Service* main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="99afd-161">Haga clic en el **comenzar** botón.</span><span class="sxs-lookup"><span data-stu-id="99afd-161">Click on the **Get Started** button.</span></span>

    ![](images/AzureLabs-Lab302b-01.png)

3.  <span data-ttu-id="99afd-162">Inicie sesión en el *Custom Vision Service* Portal.</span><span class="sxs-lookup"><span data-stu-id="99afd-162">Sign in to the *Custom Vision Service* Portal.</span></span>

    ![](images/AzureLabs-Lab302b-02.png)

    > [!NOTE]
    > <span data-ttu-id="99afd-163">Si no dispone de una cuenta de Azure, deberá crear uno.</span><span class="sxs-lookup"><span data-stu-id="99afd-163">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="99afd-164">Si está siguiendo este tutorial en una situación de aula o laboratorio, pida el instructor o uno de los a los supervisores de ayuda para instalar la nueva cuenta.</span><span class="sxs-lookup"><span data-stu-id="99afd-164">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

4.  <span data-ttu-id="99afd-165">Una vez que haya iniciado sesión por primera vez, se le pedirá con el *condiciones del servicio* panel.</span><span class="sxs-lookup"><span data-stu-id="99afd-165">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="99afd-166">Haga clic en la casilla de verificación para aceptar los términos.</span><span class="sxs-lookup"><span data-stu-id="99afd-166">Click on the checkbox to agree to the terms.</span></span> <span data-ttu-id="99afd-167">A continuación, haga clic en **acepto**.</span><span class="sxs-lookup"><span data-stu-id="99afd-167">Then click on **I agree**.</span></span>

    ![](images/AzureLabs-Lab302b-03.png)

5.  <span data-ttu-id="99afd-168">Tener aceptado los términos, se abrirá el *proyectos* sección del Portal.</span><span class="sxs-lookup"><span data-stu-id="99afd-168">Having agreed to the Terms, you will be navigated to the *Projects* section of the Portal.</span></span> <span data-ttu-id="99afd-169">Haga clic en **nuevo proyecto**.</span><span class="sxs-lookup"><span data-stu-id="99afd-169">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab302b-04.png)

6.  <span data-ttu-id="99afd-170">Aparecerá una ficha en el lado derecho, que le solicitará que especifique algunos campos para el proyecto.</span><span class="sxs-lookup"><span data-stu-id="99afd-170">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="99afd-171">Insertar un *nombre* para el proyecto.</span><span class="sxs-lookup"><span data-stu-id="99afd-171">Insert a *Name* for your project.</span></span>

    2.  <span data-ttu-id="99afd-172">Insertar un *descripción* para el proyecto (*opcional*).</span><span class="sxs-lookup"><span data-stu-id="99afd-172">Insert a *Description* for your project (*optional*).</span></span>

    3.  <span data-ttu-id="99afd-173">Elija un *grupo de recursos* o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="99afd-173">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="99afd-174">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="99afd-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="99afd-175">Se recomienda que todos los servicios de Azure asociados con un único proyecto (por ejemplo, como estos cursos) en un grupo de recursos comunes).</span><span class="sxs-lookup"><span data-stu-id="99afd-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

    4. <span data-ttu-id="99afd-176">Establecer el *tipos de proyecto* a **clasificación**</span><span class="sxs-lookup"><span data-stu-id="99afd-176">Set the *Project Types* to **Classification**</span></span>
    
    5. <span data-ttu-id="99afd-177">Establecer el *dominios* como **General**.</span><span class="sxs-lookup"><span data-stu-id="99afd-177">Set the *Domains* as **General**.</span></span>

        ![](images/AzureLabs-Lab302b-05.png)

        > <span data-ttu-id="99afd-178">Si desea leer más acerca de los grupos de recursos de Azure, inicie [visite el artículo del grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="99afd-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

7.  <span data-ttu-id="99afd-179">Una vez haya terminado, haga clic en **crear un proyecto**, se le redirigirá a Custom Vision Service, página del proyecto.</span><span class="sxs-lookup"><span data-stu-id="99afd-179">Once you are finished, click on **Create project**, you will be redirected to the Custom Vision Service, project page.</span></span>

## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="99afd-180">Capítulo 2: el proyecto de Custom Vision de entrenamiento</span><span class="sxs-lookup"><span data-stu-id="99afd-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="99afd-181">Una vez en el portal de Custom Vision, su principal objetivo es entrenar su proyecto para reconocer objetos específicos en las imágenes.</span><span class="sxs-lookup"><span data-stu-id="99afd-181">Once in the Custom Vision portal, your primary objective is to train your project to recognize specific objects in images.</span></span> <span data-ttu-id="99afd-182">Necesita al menos cinco (5) las imágenes, aunque diez (10) se prefiere, para cada objeto que desea que la aplicación reconozca.</span><span class="sxs-lookup"><span data-stu-id="99afd-182">You need at least five (5) images, though ten (10) is preferred, for each object that you would like your application to recognize.</span></span> <span data-ttu-id="99afd-183">[Puede usar las imágenes proporcionadas con este curso (un mouse y teclado)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span><span class="sxs-lookup"><span data-stu-id="99afd-183">[You can use the images provided with this course (a computer mouse and a keyboard)](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/ComputerVision_Images.zip).</span></span> 

<span data-ttu-id="99afd-184">Para entrenar el proyecto de Custom Vision Service:</span><span class="sxs-lookup"><span data-stu-id="99afd-184">To train your Custom Vision Service project:</span></span>

1.  <span data-ttu-id="99afd-185">Haga clic en el **+** situado junto a **etiquetas.**</span><span class="sxs-lookup"><span data-stu-id="99afd-185">Click on the **+** button next to **Tags.**</span></span>

    ![](images/AzureLabs-Lab302b-06.png)

2.  <span data-ttu-id="99afd-186">Agregar el **nombre** del objeto que desea reconocer.</span><span class="sxs-lookup"><span data-stu-id="99afd-186">Add the **name** of the object you would like to recognize.</span></span> <span data-ttu-id="99afd-187">Haga clic en **guardar**.</span><span class="sxs-lookup"><span data-stu-id="99afd-187">Click on **Save**.</span></span>

    ![](images/AzureLabs-Lab302b-07.png)

3.  <span data-ttu-id="99afd-188">Observará el **etiqueta** se ha agregado (es posible que deba volver a cargar la página para que aparezca).</span><span class="sxs-lookup"><span data-stu-id="99afd-188">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> <span data-ttu-id="99afd-189">Haga clic en la casilla de verificación junto a la nueva etiqueta, si ya no está seleccionada.</span><span class="sxs-lookup"><span data-stu-id="99afd-189">Click the checkbox alongside your new tag, if it is not already checked.</span></span>

    ![](images/AzureLabs-Lab302b-08.png)

4.  <span data-ttu-id="99afd-190">Haga clic en **agregar imágenes** en el centro de la página.</span><span class="sxs-lookup"><span data-stu-id="99afd-190">Click on **Add Images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab302b-09.png)

5.  <span data-ttu-id="99afd-191">Haga clic en **examinar archivos locales**y de búsqueda, a continuación, seleccione las imágenes que desea cargar, siendo el mínimo cinco (5).</span><span class="sxs-lookup"><span data-stu-id="99afd-191">Click on **Browse local files**, and search, then select, the images you would like to upload, with the minimum being five (5).</span></span> <span data-ttu-id="99afd-192">Recuerde que todas estas imágenes deben contener el objeto que está enseñando.</span><span class="sxs-lookup"><span data-stu-id="99afd-192">Remember all of these images should contain the object which you are training.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="99afd-193">Puede seleccionar varias imágenes a la vez, para cargar.</span><span class="sxs-lookup"><span data-stu-id="99afd-193">You can select several images at a time, to upload.</span></span>

6.  <span data-ttu-id="99afd-194">Una vez que se puede ver las imágenes en la ficha, seleccione la etiqueta correspondiente en el **Mis etiquetas** cuadro.</span><span class="sxs-lookup"><span data-stu-id="99afd-194">Once you can see the images in the tab, select the appropriate tag in the **My Tags** box.</span></span>

    ![](images/AzureLabs-Lab302b-10.png)

7.  <span data-ttu-id="99afd-195">Haga clic en **cargar archivos**.</span><span class="sxs-lookup"><span data-stu-id="99afd-195">Click on **Upload files**.</span></span> <span data-ttu-id="99afd-196">Los archivos cargarán.</span><span class="sxs-lookup"><span data-stu-id="99afd-196">The files will begin uploading.</span></span> <span data-ttu-id="99afd-197">Una vez que la confirmación de la carga, haga clic en **realiza**.</span><span class="sxs-lookup"><span data-stu-id="99afd-197">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab302b-11.png)

8.  <span data-ttu-id="99afd-198">Repita el mismo proceso para crear un nuevo **etiqueta** denominado **teclado** y cargue las fotos adecuadas para él.</span><span class="sxs-lookup"><span data-stu-id="99afd-198">Repeat the same process to create a new **Tag** named **Keyboard** and upload the appropriate photos for it.</span></span> <span data-ttu-id="99afd-199">No olvide **desactive** *Mouse* después de crear las nuevas etiquetas, por lo que para mostrar el *agregar imágenes* ventana.</span><span class="sxs-lookup"><span data-stu-id="99afd-199">Make sure to **uncheck** *Mouse* once you have created the new tags, so to show the *Add images* window.</span></span>

9.  <span data-ttu-id="99afd-200">Una vez que tenga dos etiquetas configurar, haga clic en **Train**, y la primera iteración de entrenamiento se iniciará la creación.</span><span class="sxs-lookup"><span data-stu-id="99afd-200">Once you have both Tags set up, click on **Train**, and the first training iteration will start building.</span></span>

    ![](images/AzureLabs-Lab302b-12.png)

10. <span data-ttu-id="99afd-201">Una vez compilada, podrá ver dos botones denominados **Predeterminar** y **predicción URL**.</span><span class="sxs-lookup"><span data-stu-id="99afd-201">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="99afd-202">Haga clic en **Predeterminar** en primer lugar, a continuación, haga clic en **predicción URL**.</span><span class="sxs-lookup"><span data-stu-id="99afd-202">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab302b-13.png)

    > [!NOTE] 
    > <span data-ttu-id="99afd-203">La dirección URL del extremo que se proporciona con esto, se establece en lo que ocurra *iteración* está marcada como predeterminada.</span><span class="sxs-lookup"><span data-stu-id="99afd-203">The endpoint URL which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="99afd-204">Como tal, si posteriormente realiza una nueva *iteración* y actualizarlo como valor predeterminado, no necesitará cambiar el código.</span><span class="sxs-lookup"><span data-stu-id="99afd-204">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

11. <span data-ttu-id="99afd-205">Una vez que ha hecho clic *dirección URL de la predicción*, abra *el Bloc de notas*y copie y pegue el **URL** y el **predicción clave**, para que pueda recuperarlo cuando necesite más adelante en el código.</span><span class="sxs-lookup"><span data-stu-id="99afd-205">Once you have clicked on *Prediction URL*, open *Notepad*, and copy and paste the **URL** and the **Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab302b-14.png)

12. <span data-ttu-id="99afd-206">Haga clic en el **engranaje** en la parte superior derecha de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="99afd-206">Click on the **Cog** at the top right of the screen.</span></span>

    ![](images/AzureLabs-Lab302b-15.png)

13. <span data-ttu-id="99afd-207">Copia el **clave entrenamiento** y péguelo en un *el Bloc de notas*, para su uso posterior.</span><span class="sxs-lookup"><span data-stu-id="99afd-207">Copy the **Training Key** and paste it into a *Notepad*, for later use.</span></span>

    ![](images/AzureLabs-Lab302b-16.png)

14. <span data-ttu-id="99afd-208">Copie también el **Id. de proyecto**y péguela también en su *el Bloc de notas* archivo para su uso posterior.</span><span class="sxs-lookup"><span data-stu-id="99afd-208">Also copy your **Project Id**, and also paste it into your *Notepad* file, for later use.</span></span>

    ![](images/AzureLabs-Lab302b-16a.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="99afd-209">Capítulo 3: configurar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="99afd-209">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="99afd-210">El siguiente es un conjunto típico de para el desarrollo con la realidad mixta y por lo tanto, es una buena plantilla para otros proyectos.</span><span class="sxs-lookup"><span data-stu-id="99afd-210">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="99afd-211">Abra *Unity* y haga clic en **New**.</span><span class="sxs-lookup"><span data-stu-id="99afd-211">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab302b-17.png)

2.  <span data-ttu-id="99afd-212">Ahora deberá proporcionar un nombre de proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="99afd-212">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="99afd-213">Insertar **AzureCustomVision.**</span><span class="sxs-lookup"><span data-stu-id="99afd-213">Insert **AzureCustomVision.**</span></span> <span data-ttu-id="99afd-214">Asegúrese de que la plantilla de proyecto se establece en **3D**.</span><span class="sxs-lookup"><span data-stu-id="99afd-214">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="99afd-215">Establecer el **ubicación** a algún lugar adecuado para usted (Recuerde, es mejor cuanto más se acerque a los directorios raíz).</span><span class="sxs-lookup"><span data-stu-id="99afd-215">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="99afd-216">A continuación, haga clic en **crear un proyecto**.</span><span class="sxs-lookup"><span data-stu-id="99afd-216">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab302b-18.png)

3.  <span data-ttu-id="99afd-217">Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="99afd-217">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="99afd-218">Vaya a **editar* > *preferencias** y, a continuación, en la ventana nueva, vaya a **herramientas externas**.</span><span class="sxs-lookup"><span data-stu-id="99afd-218">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="99afd-219">Cambio **External Script Editor** a **de Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="99afd-219">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="99afd-220">Cerrar la **preferencias** ventana.</span><span class="sxs-lookup"><span data-stu-id="99afd-220">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab302b-19.png)

4.  <span data-ttu-id="99afd-221">A continuación, vaya a **archivo > configuración de compilación** y seleccione **Universal Windows Platform**, a continuación, haga clic en el **Cambiar plataforma** botón para aplicar la selección.</span><span class="sxs-lookup"><span data-stu-id="99afd-221">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab302b-20.png)

5.  <span data-ttu-id="99afd-222">Mientras sigue en **archivo > configuración de compilación** y asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="99afd-222">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="99afd-223">**Dispositivo de destino** está establecido en **Hololens**</span><span class="sxs-lookup"><span data-stu-id="99afd-223">**Target Device** is set to **Hololens**</span></span>

        > <span data-ttu-id="99afd-224">Establezca el inmersivos, **dispositivo de destino** a *cualquier dispositivo*.</span><span class="sxs-lookup"><span data-stu-id="99afd-224">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>
        
    2.  <span data-ttu-id="99afd-225">**Tipo de compilación** está establecido en **D3D**</span><span class="sxs-lookup"><span data-stu-id="99afd-225">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="99afd-226">**SDK** está establecido en **instalada más reciente**</span><span class="sxs-lookup"><span data-stu-id="99afd-226">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="99afd-227">**Versión de Visual Studio** está establecido en **instalada más reciente**</span><span class="sxs-lookup"><span data-stu-id="99afd-227">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="99afd-228">**Compilar y ejecutar** está establecido en **máquina Local**</span><span class="sxs-lookup"><span data-stu-id="99afd-228">**Build and Run** is set to **Local Machine**</span></span>
    6.  <span data-ttu-id="99afd-229">Guarde la escena y agregarlo a la compilación.</span><span class="sxs-lookup"><span data-stu-id="99afd-229">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="99afd-230">Hacer esto seleccionando **agregar escenas abierto**.</span><span class="sxs-lookup"><span data-stu-id="99afd-230">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="99afd-231">Aparecerá el guardado de la ventana.</span><span class="sxs-lookup"><span data-stu-id="99afd-231">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab302b-21.png)

        2. <span data-ttu-id="99afd-232">Cree una nueva carpeta de esto y cualquier futuro, escena, a continuación, seleccione el **nueva carpeta** botón para crear una nueva carpeta y asígnele el nombre **escenas**.</span><span class="sxs-lookup"><span data-stu-id="99afd-232">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab302b-22.png)

        3. <span data-ttu-id="99afd-233">Abra su recién creado **escenas** carpeta y, a continuación, en el *nombre de archivo:* campo de texto, escriba **CustomVisionScene**, a continuación, haga clic en **guardar**.</span><span class="sxs-lookup"><span data-stu-id="99afd-233">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **CustomVisionScene**, then click on **Save**.</span></span>

            ![](images/AzureLabs-Lab302b-23.png)

            > <span data-ttu-id="99afd-234">Tenga en cuenta, debe guardar sus escenas de Unity dentro de la *activos* carpeta, ya que deben estar asociados al proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="99afd-234">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="99afd-235">Creación de la carpeta de segundo plano (y otras carpetas similares) es una forma habitual de estructurar un proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="99afd-235">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>
            
    7.  <span data-ttu-id="99afd-236">El resto de la configuración, en *configuración de compilación*, debe dejarse como predeterminada por ahora.</span><span class="sxs-lookup"><span data-stu-id="99afd-236">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab302b-24.png)

6.  <span data-ttu-id="99afd-237">En el *configuración de compilación* ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el *Inspector* se encuentra.</span><span class="sxs-lookup"><span data-stu-id="99afd-237">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

7. <span data-ttu-id="99afd-238">En este panel, es necesario comprobar algunas opciones de configuración:</span><span class="sxs-lookup"><span data-stu-id="99afd-238">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="99afd-239">En el **otra configuración** pestaña:</span><span class="sxs-lookup"><span data-stu-id="99afd-239">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="99afd-240">**Versión en tiempo de ejecución de secuencias de comandos** debe ser **Experimental (.NET 4.6 equivalente)**, lo que desencadenará una necesidad de reiniciar el Editor.</span><span class="sxs-lookup"><span data-stu-id="99afd-240">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="99afd-241">**Scripting de back-end** debe ser **.NET**</span><span class="sxs-lookup"><span data-stu-id="99afd-241">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="99afd-242">**Nivel de compatibilidad de API** debe ser **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="99afd-242">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![](images/AzureLabs-Lab302b-25.png)

    2.  <span data-ttu-id="99afd-243">Dentro de la **configuración de publicación** ficha **capacidades**, consulte:</span><span class="sxs-lookup"><span data-stu-id="99afd-243">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="99afd-244">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="99afd-244">**InternetClient**</span></span>

        2.  <span data-ttu-id="99afd-245">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="99afd-245">**Webcam**</span></span>

        3. <span data-ttu-id="99afd-246">**Micrófono**</span><span class="sxs-lookup"><span data-stu-id="99afd-246">**Microphone**</span></span>

        ![](images/AzureLabs-Lab302b-26.png)

    3.  <span data-ttu-id="99afd-247">Más abajo el panel, en **XR configuración** (bajo **configuración de publicación**), graduación **admite la realidad Virtual**, asegúrese de que el **SDK de Windows Mixed Reality**  se agrega.</span><span class="sxs-lookup"><span data-stu-id="99afd-247">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

    ![](images/AzureLabs-Lab302b-27.png)

8.  <span data-ttu-id="99afd-248">En *configuración de compilación* *Unity C\# proyectos* ya no está atenuada; Marque la casilla situada junto a esto.</span><span class="sxs-lookup"><span data-stu-id="99afd-248">Back in *Build Settings* *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="99afd-249">Cierre la ventana de configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="99afd-249">Close the Build Settings window.</span></span>

10.  <span data-ttu-id="99afd-250">Guarde la escena y el proyecto (**archivo > Guardar ESCENA / archivo > Guardar proyecto**).</span><span class="sxs-lookup"><span data-stu-id="99afd-250">Save your Scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-4---importing-the-newtonsoft-dll-in-unity"></a><span data-ttu-id="99afd-251">Capítulo 4: importar el archivo DLL de Newtonsoft en Unity</span><span class="sxs-lookup"><span data-stu-id="99afd-251">Chapter 4 - Importing the Newtonsoft DLL in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="99afd-252">Si desea omitir la *configurar Unity* componente de este curso y continuar directamente en código, no dude en descargar este [MR-Azure-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), importarlo en el proyecto como un [ **Paquete personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)y, a continuación, continuar desde [capítulo 6](#chapter-6---create-the-customvisionanalyser-class).</span><span class="sxs-lookup"><span data-stu-id="99afd-252">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-302b.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/Azure-MR-302b.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 6](#chapter-6---create-the-customvisionanalyser-class).</span></span>

<span data-ttu-id="99afd-253">Este curso requiere el uso de la **Newtonsoft** biblioteca, que puede agregar como un archivo DLL a los recursos.</span><span class="sxs-lookup"><span data-stu-id="99afd-253">This course requires the use of the **Newtonsoft** library, which you can add as a DLL to your assets.</span></span> <span data-ttu-id="99afd-254">El paquete que contiene [esta biblioteca se puede descargar desde este vínculo](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="99afd-254">The package containing [this library can be downloaded from this Link](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302b%20-%20Custom%20vision/NewtonsoftDLL.unitypackage).</span></span>
<span data-ttu-id="99afd-255">Para importar la biblioteca de Newtonsoft en el proyecto, use el paquete de Unity que acompaña a este curso.</span><span class="sxs-lookup"><span data-stu-id="99afd-255">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="99afd-256">Agregar el *.unitypackage* a Unity mediante el uso de la **activos* > *importación* *paquete*  >  *Personalizado* *paquete** opción de menú.</span><span class="sxs-lookup"><span data-stu-id="99afd-256">Add the *.unitypackage* to Unity by using the **Assets* > *Import* *Package* > *Custom* *Package** menu option.</span></span>

2.  <span data-ttu-id="99afd-257">En el **Importar paquete de Unity** cuadro que aparece hacia arriba, asegúrese de todo el contenido en (e incluido) **complementos** está seleccionada.</span><span class="sxs-lookup"><span data-stu-id="99afd-257">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab302b-28.png)

3.  <span data-ttu-id="99afd-258">Haga clic en el **importación** para agregar los elementos al proyecto.</span><span class="sxs-lookup"><span data-stu-id="99afd-258">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="99afd-259">Vaya a la **Newtonsoft** carpeta bajo **complementos** en la vista de proyecto y seleccione el *Newtonsoft.Json complemento*.</span><span class="sxs-lookup"><span data-stu-id="99afd-259">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the *Newtonsoft.Json plugin*.</span></span>

    ![](images/AzureLabs-Lab302b-29.png)

5.  <span data-ttu-id="99afd-260">Con el *Newtonsoft.Json complemento* seleccionado, asegúrese de que **cualquier plataforma** es **unchecked**, a continuación, asegúrese de que **WSAPlayer** también es **unchecked**, a continuación, haga clic en **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="99afd-260">With the *Newtonsoft.Json plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="99afd-261">Esto es solo para confirmar que los archivos están configurados correctamente.</span><span class="sxs-lookup"><span data-stu-id="99afd-261">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab302b-30.png)

    > [!NOTE]
    > <span data-ttu-id="99afd-262">Marcar estos complementos configura para su uso en el Editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="99afd-262">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="99afd-263">Hay un conjunto diferente de ellos en la carpeta WSA que se utilizará después de que el proyecto se exporta desde Unity.</span><span class="sxs-lookup"><span data-stu-id="99afd-263">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="99afd-264">A continuación, deberá abrir el **WSA** carpeta, en el **Newtonsoft** carpeta.</span><span class="sxs-lookup"><span data-stu-id="99afd-264">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="99afd-265">Verá una copia del mismo archivo que acaba de configurar.</span><span class="sxs-lookup"><span data-stu-id="99afd-265">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="99afd-266">Seleccione el archivo y, a continuación, en el inspector, asegúrese de que</span><span class="sxs-lookup"><span data-stu-id="99afd-266">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="99afd-267">**Cualquier plataforma** es **desactivada**</span><span class="sxs-lookup"><span data-stu-id="99afd-267">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="99afd-268">**solo** **WSAPlayer** es **activada**</span><span class="sxs-lookup"><span data-stu-id="99afd-268">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="99afd-269">**No procesar** es **activada**</span><span class="sxs-lookup"><span data-stu-id="99afd-269">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab302b-31.png)

## <a name="chapter-5---camera-setup"></a><span data-ttu-id="99afd-270">Capítulo 5: configuración de cámara</span><span class="sxs-lookup"><span data-stu-id="99afd-270">Chapter 5 - Camera setup</span></span>

1.  <span data-ttu-id="99afd-271">En el Panel de la jerarquía, seleccione la *cámara principal*.</span><span class="sxs-lookup"><span data-stu-id="99afd-271">In the Hierarchy Panel, select the *Main Camera*.</span></span>

2.  <span data-ttu-id="99afd-272">Una vez seleccionado, podrá ver todos los componentes de la *cámara principal* en el *Panel Inspector*.</span><span class="sxs-lookup"><span data-stu-id="99afd-272">Once selected, you will be able to see all the components of the *Main Camera* in the *Inspector Panel*.</span></span>

    1.  <span data-ttu-id="99afd-273">El *cámara* objeto debe denominarse **cámara principal** (tenga en cuenta la ortografía!)</span><span class="sxs-lookup"><span data-stu-id="99afd-273">The *camera* object must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="99afd-274">La cámara principal **etiqueta** debe establecerse en **MainCamera** (tenga en cuenta la ortografía!)</span><span class="sxs-lookup"><span data-stu-id="99afd-274">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="99afd-275">Asegúrese de que el **transformar posición** está establecido en **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="99afd-275">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="99afd-276">Establecer **borrar las marcas** a **Color sólido** (omitir esto para envolventes auriculares).</span><span class="sxs-lookup"><span data-stu-id="99afd-276">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>

    5.  <span data-ttu-id="99afd-277">Establecer el **en segundo plano** Color de la cámara al **negro, alfa de 0 (código hexadecimal: #00000000)** (omitir esto para envolventes auriculares).</span><span class="sxs-lookup"><span data-stu-id="99afd-277">Set the **Background** Color of the camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

    ![](images/AzureLabs-Lab302b-32.png)


## <a name="chapter-6---create-the-customvisionanalyser-class"></a><span data-ttu-id="99afd-278">Capítulo 6: crear la clase CustomVisionAnalyser.</span><span class="sxs-lookup"><span data-stu-id="99afd-278">Chapter 6 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="99afd-279">En este momento está listo para escribir código.</span><span class="sxs-lookup"><span data-stu-id="99afd-279">At this point you are ready to write some code.</span></span>

<span data-ttu-id="99afd-280">Se iniciará con la *CustomVisionAnalyser* clase.</span><span class="sxs-lookup"><span data-stu-id="99afd-280">You will begin with the *CustomVisionAnalyser* class.</span></span>

> [!NOTE]
> <span data-ttu-id="99afd-281">Las llamadas a la **Custom Vision Service** realizados en el código se muestra a continuación se realizan utilizando el **API de REST de Custom Vision**.</span><span class="sxs-lookup"><span data-stu-id="99afd-281">The calls to the **Custom Vision Service** made in the code shown below are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="99afd-282">A través del uso de esto, verá cómo implementar y hacer uso de esta API (útil para comprender cómo implementar algo similar en su propio).</span><span class="sxs-lookup"><span data-stu-id="99afd-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="99afd-283">Tenga en cuenta que Microsoft ofrece un **Custom Vision Service SDK** que también se puede utilizar para realizar llamadas al servicio.</span><span class="sxs-lookup"><span data-stu-id="99afd-283">Be aware, that Microsoft offers a **Custom Vision Service SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="99afd-284">Para obtener más información, visite la [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) artículo.</span><span class="sxs-lookup"><span data-stu-id="99afd-284">For more information visit the [Custom Vision Service SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/) article.</span></span>

<span data-ttu-id="99afd-285">Esta clase es responsable de:</span><span class="sxs-lookup"><span data-stu-id="99afd-285">This class is responsible for:</span></span>

-   <span data-ttu-id="99afd-286">Cargando la última imagen de captura como una matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="99afd-286">Loading the latest image captured as an array of bytes.</span></span>

-   <span data-ttu-id="99afd-287">Envío de la matriz de bytes en su Azure *Custom Vision Service* instancia para el análisis.</span><span class="sxs-lookup"><span data-stu-id="99afd-287">Sending the byte array to your Azure *Custom Vision Service* instance for analysis.</span></span>

-   <span data-ttu-id="99afd-288">Recibir la respuesta como una cadena JSON.</span><span class="sxs-lookup"><span data-stu-id="99afd-288">Receiving the response as a JSON string.</span></span>

-   <span data-ttu-id="99afd-289">Al deserializar la respuesta y el paso resultante *predicción* a la *SceneOrganiser* (clase), que se encargará de cómo se debe mostrar la respuesta.</span><span class="sxs-lookup"><span data-stu-id="99afd-289">Deserializing the response and passing the resulting *Prediction* to the *SceneOrganiser* class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="99afd-290">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="99afd-290">To create this class:</span></span>

1.  <span data-ttu-id="99afd-291">Haga clic en el *carpeta de activos* ubicado en el *Panel proyecto*, a continuación, haga clic en **crear > carpeta**.</span><span class="sxs-lookup"><span data-stu-id="99afd-291">Right-click in the *Asset Folder* located in the *Project Panel*, then click **Create > Folder**.</span></span> <span data-ttu-id="99afd-292">Llame a la carpeta **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="99afd-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab302b-33.png)

2.  <span data-ttu-id="99afd-293">Haga doble clic en la carpeta que acaba de crear para abrirlo.</span><span class="sxs-lookup"><span data-stu-id="99afd-293">Double-click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="99afd-294">Haga clic en la carpeta, a continuación, haga clic en **crear** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="99afd-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="99afd-295">Nombre de la secuencia de comandos *CustomVisionAnalyser*.</span><span class="sxs-lookup"><span data-stu-id="99afd-295">Name the script *CustomVisionAnalyser*.</span></span>

4.  <span data-ttu-id="99afd-296">Haga doble clic en el nuevo *CustomVisionAnalyser* script para abrirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="99afd-296">Double-click on the new *CustomVisionAnalyser* script to open it with **Visual Studio**.</span></span>

5.  <span data-ttu-id="99afd-297">Actualice los espacios de nombres en la parte superior del archivo para que coincida con lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="99afd-297">Update the namespaces at the top of your file to match the following:</span></span>

    ```csharp
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    using Newtonsoft.Json;
    ```

6.  <span data-ttu-id="99afd-298">En el *CustomVisionAnalyser* de clases, agregue las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="99afd-298">In the *CustomVisionAnalyser* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your Prediction Key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > <span data-ttu-id="99afd-299">Asegúrese de insertar el **clave predicción** en el **predictionKey** variable y su **punto de conexión de predicción** en el **predictionEndpoint** variable.</span><span class="sxs-lookup"><span data-stu-id="99afd-299">Make sure you insert your **Prediction Key** into the **predictionKey** variable and your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="99afd-300">Ha copiado a *el Bloc de notas* anteriormente en el curso.</span><span class="sxs-lookup"><span data-stu-id="99afd-300">You copied these to *Notepad* earlier in the course.</span></span>

7.  <span data-ttu-id="99afd-301">El código para **Awake()** ahora debe agregarse para inicializar la variable de instancia:</span><span class="sxs-lookup"><span data-stu-id="99afd-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  <span data-ttu-id="99afd-302">Elimine los métodos **Start()** y **Update()**.</span><span class="sxs-lookup"><span data-stu-id="99afd-302">Delete the methods **Start()** and **Update()**.</span></span>

9.  <span data-ttu-id="99afd-303">A continuación, agregue la corrutina (con el método estático **GetImageAsByteArray()** método debajo de él), que obtendrá los resultados del análisis de la imagen capturada por la *ImageCapture* clase.</span><span class="sxs-lookup"><span data-stu-id="99afd-303">Next, add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="99afd-304">En el **AnalyseImageCapture** corrutina, hay una llamada a la *SceneOrganiser* clase que aún está a crear.</span><span class="sxs-lookup"><span data-stu-id="99afd-304">In the **AnalyseImageCapture** coroutine, there is a call to the *SceneOrganiser* class that you are yet to create.</span></span> <span data-ttu-id="99afd-305">Por lo tanto, **las deje líneas de comentarios por ahora**.</span><span class="sxs-lookup"><span data-stu-id="99afd-305">Therefore, **leave those lines commented for now**.</span></span>

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(predictionEndpoint, webForm))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);

                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader("Prediction-Key", predictionKey);

                // The upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                // The download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return unityWebRequest.SendWebRequest();

                string jsonResponse = unityWebRequest.downloadHandler.text;

                // The response will be in JSON format, therefore it needs to be deserialized    
    
                // The following lines refers to a class that you will build in later Chapters
                // Wait until then to uncomment these lines

                //AnalysisObject analysisObject = new AnalysisObject();
                //analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
                //SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
            }
        }

        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);

            BinaryReader binaryReader = new BinaryReader(fileStream);

            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

10.  <span data-ttu-id="99afd-306">Asegúrese de guardar los cambios en **Visual Studio** antes de volver a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="99afd-306">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-customvisionobjects-class"></a><span data-ttu-id="99afd-307">Capítulo 7: crear la clase CustomVisionObjects</span><span class="sxs-lookup"><span data-stu-id="99afd-307">Chapter 7 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="99afd-308">La clase que se va a crear es ahora el *CustomVisionObjects* clase.</span><span class="sxs-lookup"><span data-stu-id="99afd-308">The class you will create now is the *CustomVisionObjects* class.</span></span>

<span data-ttu-id="99afd-309">Este script contiene un número de objetos usados por otras clases para serializar y deserializar las llamadas realizadas a la *Custom Vision Service*.</span><span class="sxs-lookup"><span data-stu-id="99afd-309">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the *Custom Vision Service*.</span></span>

> [!WARNING]
> <span data-ttu-id="99afd-310">Es importante tomar nota del punto de conexión que Custom Vision Service proporciona, como el siguiente código JSON estructura se ha configurado para trabajar con [ *Custom Vision predicción v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span><span class="sxs-lookup"><span data-stu-id="99afd-310">It is important that you take note of the endpoint that the Custom Vision Service provides you, as the below JSON structure has been set up to work with [*Custom Vision Prediction v2.0*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/450e4ba4d72542e889d93fd7b8e960de/operations/5a6264bc40d86a0ef8b2c290).</span></span> <span data-ttu-id="99afd-311">Si tiene una versión diferente, es posible que deba actualizar la siguiente estructura.</span><span class="sxs-lookup"><span data-stu-id="99afd-311">If you have a different version, you may need to update the below structure.</span></span>

<span data-ttu-id="99afd-312">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="99afd-312">To create this class:</span></span>

1.  <span data-ttu-id="99afd-313">Haga clic en el **Scripts** carpeta, a continuación, haga clic en **crear** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="99afd-313">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="99afd-314">Llame al script *CustomVisionObjects*.</span><span class="sxs-lookup"><span data-stu-id="99afd-314">Call the script *CustomVisionObjects*.</span></span>

2.  <span data-ttu-id="99afd-315">Haga doble clic en el nuevo **CustomVisionObjects** script para abrirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="99afd-315">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="99afd-316">Agregue los siguientes espacios de nombres en la parte superior del archivo:</span><span class="sxs-lookup"><span data-stu-id="99afd-316">Add the following namespaces to the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="99afd-317">Eliminar el **Start()** y **Update()** métodos dentro de la *CustomVisionObjects* clase; esta clase debe estar vacía.</span><span class="sxs-lookup"><span data-stu-id="99afd-317">Delete the **Start()** and **Update()** methods inside the *CustomVisionObjects* class; this class should now be empty.</span></span>

5.  <span data-ttu-id="99afd-318">Agregue las siguientes clases **fuera** el *CustomVisionObjects* clase.</span><span class="sxs-lookup"><span data-stu-id="99afd-318">Add the following classes **outside** the *CustomVisionObjects* class.</span></span> <span data-ttu-id="99afd-319">Estos objetos se usan por el *Newtonsoft* library para serializar y deserializar los datos de respuesta:</span><span class="sxs-lookup"><span data-stu-id="99afd-319">These objects are used by the *Newtonsoft* library to serialize and deserialize the response data:</span></span>

    ```csharp
    // The objects contained in this script represent the deserialized version
    // of the objects used by this application 

    /// <summary>
    /// Web request object for image data
    /// </summary>
    class MultipartObject : IMultipartFormSection
    {
        public string sectionName { get; set; }

        public byte[] sectionData { get; set; }

        public string fileName { get; set; }

        public string contentType { get; set; }
    }

    /// <summary>
    /// JSON of all Tags existing within the project
    /// contains the list of Tags
    /// </summary> 
    public class Tags_RootObject
    {
        public List<TagOfProject> Tags { get; set; }
        public int TotalTaggedImages { get; set; }
        public int TotalUntaggedImages { get; set; }
    }

    public class TagOfProject
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public string Description { get; set; }
        public int ImageCount { get; set; }
    }

    /// <summary>
    /// JSON of Tag to associate to an image
    /// Contains a list of hosting the tags,
    /// since multiple tags can be associated with one image
    /// </summary> 
    public class Tag_RootObject
    {
        public List<Tag> Tags { get; set; }
    }

    public class Tag
    {
        public string ImageId { get; set; }
        public string TagId { get; set; }
    }

    /// <summary>
    /// JSON of Images submitted
    /// Contains objects that host detailed information about one or more images
    /// </summary> 
    public class ImageRootObject
    {
        public bool IsBatchSuccessful { get; set; }
        public List<SubmittedImage> Images { get; set; }
    }

    public class SubmittedImage
    {
        public string SourceUrl { get; set; }
        public string Status { get; set; }
        public ImageObject Image { get; set; }
    }

    public class ImageObject
    {
        public string Id { get; set; }
        public DateTime Created { get; set; }
        public int Width { get; set; }
        public int Height { get; set; }
        public string ImageUri { get; set; }
        public string ThumbnailUri { get; set; }
    }

    /// <summary>
    /// JSON of Service Iteration
    /// </summary> 
    public class Iteration
    {
        public string Id { get; set; }
        public string Name { get; set; }
        public bool IsDefault { get; set; }
        public string Status { get; set; }
        public string Created { get; set; }
        public string LastModified { get; set; }
        public string TrainedAt { get; set; }
        public string ProjectId { get; set; }
        public bool Exportable { get; set; }
        public string DomainId { get; set; }
    }

    /// <summary>
    /// Predictions received by the Service after submitting an image for analysis
    /// </summary> 
    [Serializable]
    public class AnalysisObject
    {
        public List<Prediction> Predictions { get; set; }
    }

    [Serializable]
    public class Prediction
    {
        public string TagName { get; set; }
        public double Probability { get; set; }
    }
    ```

## <a name="chapter-8---create-the-voicerecognizer-class"></a><span data-ttu-id="99afd-320">Capítulo 8: crear la clase VoiceRecognizer</span><span class="sxs-lookup"><span data-stu-id="99afd-320">Chapter 8 - Create the VoiceRecognizer class</span></span>

<span data-ttu-id="99afd-321">Esta clase reconocerá la entrada de voz del usuario.</span><span class="sxs-lookup"><span data-stu-id="99afd-321">This class will recognize the voice input from the user.</span></span>

<span data-ttu-id="99afd-322">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="99afd-322">To create this class:</span></span>

1.  <span data-ttu-id="99afd-323">Haga clic en el **Scripts** carpeta, a continuación, haga clic en **crear** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="99afd-323">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="99afd-324">Llame al script *VoiceRecognizer*.</span><span class="sxs-lookup"><span data-stu-id="99afd-324">Call the script *VoiceRecognizer*.</span></span>

2.  <span data-ttu-id="99afd-325">Haga doble clic en el nuevo **VoiceRecognizer** script para abrirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="99afd-325">Double-click on the new **VoiceRecognizer** script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="99afd-326">Agregue los siguientes espacios de nombres anterior el *VoiceRecognizer* clase:</span><span class="sxs-lookup"><span data-stu-id="99afd-326">Add the following namespaces above the *VoiceRecognizer* class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.Windows.Speech;
    ```

4.  <span data-ttu-id="99afd-327">A continuación, agregue las siguientes variables dentro de la *VoiceRecognizer* clase encima el *Start()* método:</span><span class="sxs-lookup"><span data-stu-id="99afd-327">Then add the following variables inside the *VoiceRecognizer* class, above the *Start()* method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static VoiceRecognizer Instance;

        /// <summary>
        /// Recognizer class for voice recognition
        /// </summary>
        internal KeywordRecognizer keywordRecognizer;

        /// <summary>
        /// List of Keywords registered
        /// </summary>
        private Dictionary<string, Action> _keywords = new Dictionary<string, Action>();
    ```

5.  <span data-ttu-id="99afd-328">Agregar el **Awake()** y **Start()** métodos, que establecerá el usuario *palabras clave* para ser reconocido cuando asocia una etiqueta a una imagen:</span><span class="sxs-lookup"><span data-stu-id="99afd-328">Add the **Awake()** and **Start()** methods, the latter of which will set up the user *keywords* to be recognized when associating a tag to an image:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start ()
        {

            Array tagsArray = Enum.GetValues(typeof(CustomVisionTrainer.Tags));

            foreach (object tagWord in tagsArray)
            {
                _keywords.Add(tagWord.ToString(), () =>
                {
                    // When a word is recognized, the following line will be called
                    CustomVisionTrainer.Instance.VerifyTag(tagWord.ToString());
                });
            }

            _keywords.Add("Discard", () =>
            {
                // When a word is recognized, the following line will be called
                // The user does not want to submit the image
                // therefore ignore and discard the process
                ImageCapture.Instance.ResetImageCapture();
                keywordRecognizer.Stop();
            });

            //Create the keyword recognizer 
            keywordRecognizer = new KeywordRecognizer(_keywords.Keys.ToArray());

            // Register for the OnPhraseRecognized event 
            keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        }
    ```

6.  <span data-ttu-id="99afd-329">Eliminar el **Update()** método.</span><span class="sxs-lookup"><span data-stu-id="99afd-329">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="99afd-330">Agregue el siguiente controlador, que se llama cada vez que se reconoce la entrada de voz:</span><span class="sxs-lookup"><span data-stu-id="99afd-330">Add the following handler, which is called whenever voice input is recognized:</span></span>

    ```csharp    
        /// <summary>
        /// Handler called when a word is recognized
        /// </summary>
        private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
        {
            Action keywordAction;
            // if the keyword recognized is in our dictionary, call that Action.
            if (_keywords.TryGetValue(args.text, out keywordAction))
            {
                keywordAction.Invoke();
            }
        }
    ```

8.  <span data-ttu-id="99afd-331">Asegúrese de guardar los cambios en **Visual Studio** antes de volver a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="99afd-331">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!NOTE]
> <span data-ttu-id="99afd-332">No se preocupe código que puede aparecer un error, ya que proporciona clases más pronto, lo que solucionará estas.</span><span class="sxs-lookup"><span data-stu-id="99afd-332">Do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-9---create-the-customvisiontrainer-class"></a><span data-ttu-id="99afd-333">Capítulo 9: crear la clase CustomVisionTrainer</span><span class="sxs-lookup"><span data-stu-id="99afd-333">Chapter 9 - Create the CustomVisionTrainer class</span></span>

<span data-ttu-id="99afd-334">Esta clase encadenará una serie de llamadas de web para entrenar el *Custom Vision Service*.</span><span class="sxs-lookup"><span data-stu-id="99afd-334">This class will chain a series of web calls to train the *Custom Vision Service*.</span></span> <span data-ttu-id="99afd-335">Cada llamada se explicarán detalladamente justo encima del código.</span><span class="sxs-lookup"><span data-stu-id="99afd-335">Each call will be explained in detail right above the code.</span></span>

<span data-ttu-id="99afd-336">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="99afd-336">To create this class:</span></span>

1.  <span data-ttu-id="99afd-337">Haga clic en el **Scripts** carpeta, a continuación, haga clic en **crear** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="99afd-337">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="99afd-338">Llame al script *CustomVisionTrainer*.</span><span class="sxs-lookup"><span data-stu-id="99afd-338">Call the script *CustomVisionTrainer*.</span></span>

2.  <span data-ttu-id="99afd-339">Haga doble clic en el nuevo *CustomVisionTrainer* script para abrirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="99afd-339">Double-click on the new *CustomVisionTrainer* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="99afd-340">Agregue los siguientes espacios de nombres anterior el *CustomVisionTrainer* clase:</span><span class="sxs-lookup"><span data-stu-id="99afd-340">Add the following namespaces above the *CustomVisionTrainer* class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Collections.Generic;
    using System.IO;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="99afd-341">A continuación, agregue las siguientes variables dentro de la *CustomVisionTrainer* clase encima el **Start()** método.</span><span class="sxs-lookup"><span data-stu-id="99afd-341">Then add the following variables inside the *CustomVisionTrainer* class, above the **Start()** method.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="99afd-342">La dirección URL de entrenamiento usada aquí se proporciona en el *Custom Vision Training 1.2* documentación, y tiene una estructura de: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span><span class="sxs-lookup"><span data-stu-id="99afd-342">The training URL used here is provided within the *Custom Vision Training 1.2* documentation, and has a structure of: https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/{projectId}/</span></span>  
    > <span data-ttu-id="99afd-343">Para obtener más información, visite la [ *referencia v1.2 de Custom Vision Training API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span><span class="sxs-lookup"><span data-stu-id="99afd-343">For more information, visit the [*Custom Vision Training v1.2 reference API*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span>

    > [!WARNING]
    > <span data-ttu-id="99afd-344">Es importante tomar nota del punto de conexión que Custom Vision Service se proporciona para el modo de formación, como la estructura de JSON utilizada (dentro de la **CustomVisionObjects** clase) se ha configurado para trabajar con [  *Custom Vision Training v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span><span class="sxs-lookup"><span data-stu-id="99afd-344">It is important that you take note of the endpoint that the Custom Vision Service provides you for the training mode, as the JSON structure used (within the **CustomVisionObjects** class) has been set up to work with [*Custom Vision Training v1.2*](https://southcentralus.dev.cognitive.microsoft.com/docs/services/f2d62aa3b93843d79e948fe87fa89554/operations/5a3044ee08fa5e06b890f11f).</span></span> <span data-ttu-id="99afd-345">Si tiene una versión diferente, es posible que deba actualizar el *objetos* estructura.</span><span class="sxs-lookup"><span data-stu-id="99afd-345">If you have a different version, you may need to update the *Objects* structure.</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CustomVisionTrainer Instance;

        /// <summary>
        /// Custom Vision Service URL root
        /// </summary>
        private string url = "https://southcentralus.api.cognitive.microsoft.com/customvision/v1.2/Training/projects/";

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string trainingKey = "- Insert your key here -";

        /// <summary>
        /// Insert your Project Id here
        /// </summary>
        private string projectId = "- Insert your Project Id here -";

        /// <summary>
        /// Byte array of the image to submit for analysis
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// The Tags accepted
        /// </summary>
        internal enum Tags {Mouse, Keyboard}

        /// <summary>
        /// The UI displaying the training Chapters
        /// </summary>
        private TextMesh trainingUI_TextMesh;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="99afd-346">Asegúrese de agregar su **clave de servicio** (entrenamiento clave-valor) y **Id. de proyecto** valor que anotó anterior; estos son los valores [recopilados desde el portal anteriormente en el curso () Capítulo 2, el paso 10 y versiones posteriores)](#chapter-2---training-your-custom-vision-oroject).</span><span class="sxs-lookup"><span data-stu-id="99afd-346">Ensure that you add your **Service Key** (Training Key) value and **Project Id** value, which you noted down previous; these are the values you [collected from the portal earlier in the course (Chapter 2, step 10 onwards)](#chapter-2---training-your-custom-vision-oroject).</span></span>

5.  <span data-ttu-id="99afd-347">Agregue el siguiente **Start()** y **Awake()** métodos.</span><span class="sxs-lookup"><span data-stu-id="99afd-347">Add the following **Start()** and **Awake()** methods.</span></span> <span data-ttu-id="99afd-348">Esos métodos se llaman en la inicialización y contienen la llamada para configurar la interfaz de usuario:</span><span class="sxs-lookup"><span data-stu-id="99afd-348">Those methods are called on initialization and contain the call to set up the UI:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        private void Start()
        { 
            trainingUI_TextMesh = SceneOrganiser.Instance.CreateTrainingUI("TrainingUI", 0.04f, 0, 4, false);
        }
    ```

6.  <span data-ttu-id="99afd-349">Eliminar el **Update()** método.</span><span class="sxs-lookup"><span data-stu-id="99afd-349">Delete the **Update()** method.</span></span> <span data-ttu-id="99afd-350">Esta clase no necesitará.</span><span class="sxs-lookup"><span data-stu-id="99afd-350">This class will not need it.</span></span>

7.  <span data-ttu-id="99afd-351">Agregar el **RequestTagSelection()** método.</span><span class="sxs-lookup"><span data-stu-id="99afd-351">Add the **RequestTagSelection()** method.</span></span> <span data-ttu-id="99afd-352">Este método es la primera que se llama cuando se captura una imagen y se almacena en el dispositivo y ahora está listo para enviarse a la *Custom Vision Service*, entrenarlo.</span><span class="sxs-lookup"><span data-stu-id="99afd-352">This method is the first to be called when an image has been captured and stored in the device and is now ready to be submitted to the *Custom Vision Service*, to train it.</span></span> <span data-ttu-id="99afd-353">Este método muestra, en el entrenamiento de la interfaz de usuario, un conjunto de palabras clave que el usuario puede utilizar para etiquetar la imagen que se ha capturado.</span><span class="sxs-lookup"><span data-stu-id="99afd-353">This method displays, in the training UI, a set of keywords the user can use to tag the image that has been captured.</span></span> <span data-ttu-id="99afd-354">También le avisa la *VoiceRecognizer* clase para empezar a escuchar al usuario para la entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="99afd-354">It also alerts the *VoiceRecognizer* class to begin listening to the user for voice input.</span></span>

    ```csharp
        internal void RequestTagSelection()
        {
            trainingUI_TextMesh.gameObject.SetActive(true);
            trainingUI_TextMesh.text = $" \nUse voice command \nto choose between the following tags: \nMouse\nKeyboard \nor say Discard";

            VoiceRecognizer.Instance.keywordRecognizer.Start();
        }
    ```

8.  <span data-ttu-id="99afd-355">Agregar el **VerifyTag()** método.</span><span class="sxs-lookup"><span data-stu-id="99afd-355">Add the **VerifyTag()** method.</span></span> <span data-ttu-id="99afd-356">Este método recibe la entrada de voz reconocida por el **VoiceRecognizer** clase y comprobar su validez y, a continuación, iniciar el proceso de entrenamiento.</span><span class="sxs-lookup"><span data-stu-id="99afd-356">This method will receive the voice input recognized by the **VoiceRecognizer** class and verify its validity, and then begin the training process.</span></span>

    ```csharp
        /// <summary>
        /// Verify voice input against stored tags.
        /// If positive, it will begin the Service training process.
        /// </summary>
        internal void VerifyTag(string spokenTag)
        {
            if (spokenTag == Tags.Mouse.ToString() || spokenTag == Tags.Keyboard.ToString())
            {
                trainingUI_TextMesh.text = $"Tag chosen: {spokenTag}";
                VoiceRecognizer.Instance.keywordRecognizer.Stop();
                StartCoroutine(SubmitImageForTraining(ImageCapture.Instance.filePath, spokenTag));
            }
        }
    ```

9.  <span data-ttu-id="99afd-357">Agregar el **SubmitImageForTraining()** método.</span><span class="sxs-lookup"><span data-stu-id="99afd-357">Add the **SubmitImageForTraining()** method.</span></span> <span data-ttu-id="99afd-358">Este método comenzará el proceso de entrenamiento de Custom Vision Service.</span><span class="sxs-lookup"><span data-stu-id="99afd-358">This method will begin the Custom Vision Service training process.</span></span> <span data-ttu-id="99afd-359">El primer paso es recuperar el **Id. de etiqueta** desde el servicio que está asociado con la entrada de voz validada del usuario.</span><span class="sxs-lookup"><span data-stu-id="99afd-359">The first step is to retrieve the **Tag Id** from the Service which is associated with the validated speech input from the user.</span></span> <span data-ttu-id="99afd-360">El **Id. de etiqueta** se cargará a continuación, junto con la imagen.</span><span class="sxs-lookup"><span data-stu-id="99afd-360">The **Tag Id** will then be uploaded along with the image.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to submit the image.
        /// </summary>
        public IEnumerator SubmitImageForTraining(string imagePath, string tag)
        {
            yield return new WaitForSeconds(2);
            trainingUI_TextMesh.text = $"Submitting Image \nwith tag: {tag} \nto Custom Vision Service";
            string imageId = string.Empty;
            string tagId = string.Empty;

            // Retrieving the Tag Id relative to the voice input
            string getTagIdEndpoint = string.Format("{0}{1}/tags", url, projectId);
            using (UnityWebRequest www = UnityWebRequest.Get(getTagIdEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Tags_RootObject tagRootObject = JsonConvert.DeserializeObject<Tags_RootObject>(jsonResponse);

                foreach (TagOfProject tOP in tagRootObject.Tags)
                {
                    if (tOP.Name == tag)
                    {
                        tagId = tOP.Id;
                    }             
                }
            }

            // Creating the image object to send for training
            List<IMultipartFormSection> multipartList = new List<IMultipartFormSection>();
            MultipartObject multipartObject = new MultipartObject();
            multipartObject.contentType = "application/octet-stream";
            multipartObject.fileName = "";
            multipartObject.sectionData = GetImageAsByteArray(imagePath);
            multipartList.Add(multipartObject);

            string createImageFromDataEndpoint = string.Format("{0}{1}/images?tagIds={2}", url, projectId, tagId);

            using (UnityWebRequest www = UnityWebRequest.Post(createImageFromDataEndpoint, multipartList))
            {
                // Gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);           

                //unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                www.SetRequestHeader("Training-Key", trainingKey);

                // The upload handler will help uploading the byte array with the request
                www.uploadHandler = new UploadHandlerRaw(imageBytes);

                // The download handler will help receiving the analysis from Azure
                www.downloadHandler = new DownloadHandlerBuffer();

                // Send the request
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                ImageRootObject m = JsonConvert.DeserializeObject<ImageRootObject>(jsonResponse);
                imageId = m.Images[0].Image.Id;
            }
            trainingUI_TextMesh.text = "Image uploaded";
            StartCoroutine(TrainCustomVisionProject());
        }
    ```

10. <span data-ttu-id="99afd-361">Agregar el **TrainCustomVisionProject()** método.</span><span class="sxs-lookup"><span data-stu-id="99afd-361">Add the **TrainCustomVisionProject()** method.</span></span> <span data-ttu-id="99afd-362">Una vez que se han enviado y etiquetar la imagen, este método se llamará.</span><span class="sxs-lookup"><span data-stu-id="99afd-362">Once the image has been submitted and tagged, this method will be called.</span></span> <span data-ttu-id="99afd-363">Creará una nueva iteración que se van a entrenar con todas las imágenes anteriores y enviadas al servicio además de la imagen recién cargado.</span><span class="sxs-lookup"><span data-stu-id="99afd-363">It will create a new Iteration that will be trained with all the previous images submitted to the Service plus the image just uploaded.</span></span> <span data-ttu-id="99afd-364">Una vez que se ha completado el entrenamiento, este método llamará a un método para establecer el recién creado **iteración** como **predeterminado**, de modo que el punto de conexión que usa para el análisis es la última iteración entrenada.</span><span class="sxs-lookup"><span data-stu-id="99afd-364">Once the training has been completed, this method will call a method to set the newly created **Iteration** as **Default**, so that the endpoint you are using for analysis is the latest trained iteration.</span></span>

    ```csharp
        /// <summary>
        /// Call the Custom Vision Service to train the Service.
        /// It will generate a new Iteration in the Service
        /// </summary>
        public IEnumerator TrainCustomVisionProject()
        {
            yield return new WaitForSeconds(2);

            trainingUI_TextMesh.text = "Training Custom Vision Service";

            WWWForm webForm = new WWWForm();

            string trainProjectEndpoint = string.Format("{0}{1}/train", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Post(trainProjectEndpoint, webForm))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Training - JSON Response: {jsonResponse}");

                // A new iteration that has just been created and trained
                Iteration iteration = new Iteration();
                iteration = JsonConvert.DeserializeObject<Iteration>(jsonResponse);

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Custom Vision Trained";

                    // Since the Service has a limited number of iterations available,
                    // we need to set the last trained iteration as default
                    // and delete all the iterations you dont need anymore
                    StartCoroutine(SetDefaultIteration(iteration)); 
                }
            }
        }
    ```

11. <span data-ttu-id="99afd-365">Agregar el **SetDefaultIteration()** método.</span><span class="sxs-lookup"><span data-stu-id="99afd-365">Add the **SetDefaultIteration()** method.</span></span> <span data-ttu-id="99afd-366">Este método establece la iteración creada anteriormente y entrenada como *predeterminado*.</span><span class="sxs-lookup"><span data-stu-id="99afd-366">This method will set the previously created and trained iteration as *Default*.</span></span> <span data-ttu-id="99afd-367">Una vez completado, este método tendrá que eliminar la iteración anterior existente en el servicio.</span><span class="sxs-lookup"><span data-stu-id="99afd-367">Once completed, this method will have to delete the previous iteration existing in the Service.</span></span> <span data-ttu-id="99afd-368">En el momento de redactar este curso, hay un límite de un máximo iteraciones de diez (10) permiten al mismo tiempo en el servicio.</span><span class="sxs-lookup"><span data-stu-id="99afd-368">At the time of writing this course, there is a limit of a maximum ten (10) iterations allowed to exist at the same time in the Service.</span></span>

    ```csharp
        /// <summary>
        /// Set the newly created iteration as Default
        /// </summary>
        private IEnumerator SetDefaultIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);
            trainingUI_TextMesh.text = "Setting default iteration";

            // Set the last trained iteration to default
            iteration.IsDefault = true;

            // Convert the iteration object as JSON
            string iterationAsJson = JsonConvert.SerializeObject(iteration);
            byte[] bytes = Encoding.UTF8.GetBytes(iterationAsJson);

            string setDefaultIterationEndpoint = string.Format("{0}{1}/iterations/{2}", 
                                                            url, projectId, iteration.Id);

            using (UnityWebRequest www = UnityWebRequest.Put(setDefaultIterationEndpoint, bytes))
            {
                www.method = "PATCH";
                www.SetRequestHeader("Training-Key", trainingKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                if (www.isDone)
                {
                    trainingUI_TextMesh.text = "Default iteration is set \nDeleting Unused Iteration";
                    StartCoroutine(DeletePreviousIteration(iteration));
                }
            }
        }
    ```

12. <span data-ttu-id="99afd-369">Agregar el **DeletePreviousIteration()** método.</span><span class="sxs-lookup"><span data-stu-id="99afd-369">Add the **DeletePreviousIteration()** method.</span></span> <span data-ttu-id="99afd-370">Este método se busque y elimine la iteración no predeterminado anterior:</span><span class="sxs-lookup"><span data-stu-id="99afd-370">This method will find and delete the previous non-default iteration:</span></span>

    ```csharp
        /// <summary>
        /// Delete the previous non-default iteration.
        /// </summary>
        public IEnumerator DeletePreviousIteration(Iteration iteration)
        {
            yield return new WaitForSeconds(5);

            trainingUI_TextMesh.text = "Deleting Unused \nIteration";

            string iterationToDeleteId = string.Empty;

            string findAllIterationsEndpoint = string.Format("{0}{1}/iterations", url, projectId);

            using (UnityWebRequest www = UnityWebRequest.Get(findAllIterationsEndpoint))
            {
                www.SetRequestHeader("Training-Key", trainingKey);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();

                string jsonResponse = www.downloadHandler.text;

                // The iteration that has just been trained
                List<Iteration> iterationsList = new List<Iteration>();
                iterationsList = JsonConvert.DeserializeObject<List<Iteration>>(jsonResponse);

                foreach (Iteration i in iterationsList)
                {
                    if (i.IsDefault != true)
                    {
                        Debug.Log($"Cleaning - Deleting iteration: {i.Name}, {i.Id}");
                        iterationToDeleteId = i.Id;
                        break;
                    }
                }
            }

            string deleteEndpoint = string.Format("{0}{1}/iterations/{2}", url, projectId, iterationToDeleteId);

            using (UnityWebRequest www2 = UnityWebRequest.Delete(deleteEndpoint))
            {
                www2.SetRequestHeader("Training-Key", trainingKey);
                www2.downloadHandler = new DownloadHandlerBuffer();
                yield return www2.SendWebRequest();
                string jsonResponse = www2.downloadHandler.text;

                trainingUI_TextMesh.text = "Iteration Deleted";
                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "Ready for next \ncapture";

                yield return new WaitForSeconds(2);
                trainingUI_TextMesh.text = "";
                ImageCapture.Instance.ResetImageCapture();
            }
        }
    ```

13. <span data-ttu-id="99afd-371">El último método para agregar de esta clase es el **GetImageAsByteArray()** método que se utiliza en llamadas a la web para convertir la imagen capturada en una matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="99afd-371">The last method to add in this class is the **GetImageAsByteArray()** method, used on the web calls to convert the image captured into a byte array.</span></span>

    ```csharp
        /// <summary>
        /// Returns the contents of the specified image file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

14. <span data-ttu-id="99afd-372">Asegúrese de guardar los cambios en **Visual Studio** antes de volver a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="99afd-372">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

## <a name="chapter-10---create-the-sceneorganiser-class"></a><span data-ttu-id="99afd-373">Capítulo 10: crear la clase SceneOrganiser</span><span class="sxs-lookup"><span data-stu-id="99afd-373">Chapter 10 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="99afd-374">Esta clase hará lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="99afd-374">This class will:</span></span>

-   <span data-ttu-id="99afd-375">Crear un **Cursor** objeto va a asociar a la cámara principal.</span><span class="sxs-lookup"><span data-stu-id="99afd-375">Create a **Cursor** object to attach to the Main Camera.</span></span>

-   <span data-ttu-id="99afd-376">Crear un **etiqueta** objeto que va a aparecer cuando el servicio reconoce los objetos reales.</span><span class="sxs-lookup"><span data-stu-id="99afd-376">Create a **Label** object that will appear when the Service recognizes the real-world objects.</span></span>

-   <span data-ttu-id="99afd-377">Configuración de la cámara principal adjuntando los componentes adecuados a él.</span><span class="sxs-lookup"><span data-stu-id="99afd-377">Set up the Main Camera by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="99afd-378">Cuando se encuentra en **modo de análisis**, generar las etiquetas en tiempo de ejecución, en el espacio adecuado mundo relativo a la posición de la cámara principal y mostrar los datos recibidos de Custom Vision Service.</span><span class="sxs-lookup"><span data-stu-id="99afd-378">When in **Analysis Mode**, spawn the Labels at runtime, in the appropriate world space relative to the position of the Main Camera, and display the data received from the Custom Vision Service.</span></span>

-   <span data-ttu-id="99afd-379">Cuando se encuentra en **modo de formación**, generar la interfaz de usuario que se mostrará las distintas fases del proceso de entrenamiento.</span><span class="sxs-lookup"><span data-stu-id="99afd-379">When in **Training Mode**, spawn the UI that will display the different stages of the training process.</span></span>

<span data-ttu-id="99afd-380">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="99afd-380">To create this class:</span></span>

1.  <span data-ttu-id="99afd-381">Haga clic en el **Scripts** carpeta, a continuación, haga clic en **crear** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="99afd-381">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="99afd-382">Nombre de la secuencia de comandos *SceneOrganiser*.</span><span class="sxs-lookup"><span data-stu-id="99afd-382">Name the script *SceneOrganiser*.</span></span>

2.  <span data-ttu-id="99afd-383">Haga doble clic en el nuevo *SceneOrganiser* script para abrirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="99afd-383">Double-click on the new *SceneOrganiser* script to open it with **Visual Studio**.</span></span>

3.  <span data-ttu-id="99afd-384">Un espacio de nombres, solo tendrá que quitar las demás desde arriba la *SceneOrganiser* clase:</span><span class="sxs-lookup"><span data-stu-id="99afd-384">You will only need one namespace, remove the others from above the *SceneOrganiser* class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="99afd-385">A continuación, agregue las siguientes variables dentro de la *SceneOrganiser* clase encima el **Start()** método:</span><span class="sxs-lookup"><span data-stu-id="99afd-385">Then add the following variables inside the *SceneOrganiser* class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        internal GameObject label;

        /// <summary>
        /// Object providing the current status of the camera.
        /// </summary>
        internal TextMesh cameraStatusIndicator;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.5f;
    ```

5.  <span data-ttu-id="99afd-386">Eliminar el **Start()** y **Update()** métodos.</span><span class="sxs-lookup"><span data-stu-id="99afd-386">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="99afd-387">Justo debajo de las variables, agregue el **Awake()** método, que inicializará la clase y configuración de la escena.</span><span class="sxs-lookup"><span data-stu-id="99afd-387">Right underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this GameObject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this GameObject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionTrainer class to this GameObject
            gameObject.AddComponent<CustomVisionTrainer>();

            // Add the VoiceRecogniser class to this GameObject
            gameObject.AddComponent<VoiceRecognizer>();

            // Add the CustomVisionObjects class to this GameObject
            gameObject.AddComponent<CustomVisionObjects>();

            // Create the camera Cursor
            cursor = CreateCameraCursor();

            // Load the label prefab as reference
            label = CreateLabel();

            // Create the camera status indicator label, and place it above where predictions
            // and training UI will appear.
            cameraStatusIndicator = CreateTrainingUI("Status Indicator", 0.02f, 0.2f, 3, true);

            // Set camera status indicator to loading.
            SetCameraStatus("Loading");
        }
    ```

7.  <span data-ttu-id="99afd-388">Ahora, agregue el **CreateCameraCursor()** método que crea y coloca el cursor de la cámara principal, y el **CreateLabel()** método, que crea el **Analysis etiqueta** objeto .</span><span class="sxs-lookup"><span data-stu-id="99afd-388">Now add the **CreateCameraCursor()** method that creates and positions the Main Camera cursor, and the **CreateLabel()** method, which creates the **Analysis Label** object.</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private GameObject CreateCameraCursor()
        {
            // Create a sphere as new cursor
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Attach it to the camera
            newCursor.transform.parent = gameObject.transform;

            // Resize the new cursor
            newCursor.transform.localScale = new Vector3(0.02f, 0.02f, 0.02f);

            // Move it to the correct position
            newCursor.transform.localPosition = new Vector3(0, 0, 4);

            // Set the cursor color to red
            newCursor.GetComponent<Renderer>().material = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<Renderer>().material.color = Color.green;

            return newCursor;
        }

        /// <summary>
        /// Create the analysis label object
        /// </summary>
        private GameObject CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Resize the new cursor
            newLabel.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);

            // Creating the text of the label
            TextMesh t = newLabel.AddComponent<TextMesh>();
            t.anchor = TextAnchor.MiddleCenter;
            t.alignment = TextAlignment.Center;
            t.fontSize = 50;
            t.text = "";

            return newLabel;
        }
    ```

8. <span data-ttu-id="99afd-389">Agregar el **SetCameraStatus()** método que controlará los mensajes destinados a la malla de texto que proporciona el estado de la cámara.</span><span class="sxs-lookup"><span data-stu-id="99afd-389">Add the **SetCameraStatus()** method, which will handle messages intended for the text mesh providing the status of the camera.</span></span>

    ```csharp
        /// <summary>
        /// Set the camera status to a provided string. Will be coloured if it matches a keyword.
        /// </summary>
        /// <param name="statusText">Input string</param>
        public void SetCameraStatus(string statusText)
        {
            if (string.IsNullOrEmpty(statusText) == false)
            {
                string message = "white";

                switch (statusText.ToLower())
                {
                    case "loading":
                        message = "yellow";
                        break;

                    case "ready":
                        message = "green";
                        break;

                    case "uploading image":
                        message = "red";
                        break;

                    case "looping capture":
                        message = "yellow";
                        break;

                    case "analysis":
                        message = "red";
                        break;
                }

                cameraStatusIndicator.GetComponent<TextMesh>().text = $"Camera Status:\n<color={message}>{statusText}..</color>";
            }
        }
    ```

9. <span data-ttu-id="99afd-390">Agregar el **PlaceAnalysisLabel()** y **SetTagsToLastLabel()** métodos, generar y mostrar los datos de Custom Vision Service en la escena.</span><span class="sxs-lookup"><span data-stu-id="99afd-390">Add the **PlaceAnalysisLabel()** and **SetTagsToLastLabel()** methods, which will spawn and display the data from the Custom Vision Service into the scene.</span></span>

    ```csharp
        /// <summary>
        /// Instantiate a label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
        }

        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void SetTagsToLastLabel(AnalysisObject analysisObject)
        {
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

            if (analysisObject.Predictions != null)
            {
                foreach (Prediction p in analysisObject.Predictions)
                {
                    if (p.Probability > 0.02)
                    {
                        lastLabelPlacedText.text += $"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}";
                        Debug.Log($"Detected: {p.TagName} {p.Probability.ToString("0.00 \n")}");
                    }
                }
            }
        }
    ```

10. <span data-ttu-id="99afd-391">Por último, agregue el **CreateTrainingUI()** método, que generará la interfaz de usuario mostrar el varias fases del proceso de entrenamiento cuando la aplicación está en modo de formación.</span><span class="sxs-lookup"><span data-stu-id="99afd-391">Lastly, add the **CreateTrainingUI()** method, which will spawn the UI displaying the multiple stages of the training process when the application is in Training Mode.</span></span> <span data-ttu-id="99afd-392">También se le sacado partido a este método para crear el objeto de estado de la cámara.</span><span class="sxs-lookup"><span data-stu-id="99afd-392">This method will also be harnessed to create the camera status object.</span></span>

    ```csharp
        /// <summary>
        /// Create a 3D Text Mesh in scene, with various parameters.
        /// </summary>
        /// <param name="name">name of object</param>
        /// <param name="scale">scale of object (i.e. 0.04f)</param>
        /// <param name="yPos">height above the cursor (i.e. 0.3f</param>
        /// <param name="zPos">distance from the camera</param>
        /// <param name="setActive">whether the text mesh should be visible when it has been created</param>
        /// <returns>Returns a 3D text mesh within the scene</returns>
        internal TextMesh CreateTrainingUI(string name, float scale, float yPos, float zPos, bool setActive)
        {
            GameObject display = new GameObject(name, typeof(TextMesh));
            display.transform.parent = Camera.main.transform;
            display.transform.localPosition = new Vector3(0, yPos, zPos);
            display.SetActive(setActive);
            display.transform.localScale = new Vector3(scale, scale, scale);
            display.transform.rotation = new Quaternion();
            TextMesh textMesh = display.GetComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            return textMesh;
        }
    ```

11. <span data-ttu-id="99afd-393">Asegúrese de guardar los cambios en **Visual Studio** antes de volver a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="99afd-393">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="99afd-394">Antes de continuar, abra el **CustomVisionAnalyser** (clase) y dentro del **AnalyseLastImageCaptured()** método, *quite* las líneas siguientes:</span><span class="sxs-lookup"><span data-stu-id="99afd-394">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
>
> ```csharp
>   AnalysisObject analysisObject = new AnalysisObject();
>   analysisObject = JsonConvert.DeserializeObject<AnalysisObject>(jsonResponse);
>   SceneOrganiser.Instance.SetTagsToLastLabel(analysisObject);
> ```

## <a name="chapter-11---create-the-imagecapture-class"></a><span data-ttu-id="99afd-395">Capítulo 11: crear la clase ImageCapture</span><span class="sxs-lookup"><span data-stu-id="99afd-395">Chapter 11 - Create the ImageCapture class</span></span>

<span data-ttu-id="99afd-396">La siguiente clase que se va a crear es la *ImageCapture* clase.</span><span class="sxs-lookup"><span data-stu-id="99afd-396">The next class you are going to create is the *ImageCapture* class.</span></span>

<span data-ttu-id="99afd-397">Esta clase es responsable de:</span><span class="sxs-lookup"><span data-stu-id="99afd-397">This class is responsible for:</span></span>

-   <span data-ttu-id="99afd-398">Capturar una imagen con la cámara de HoloLens y almacenarla en la *aplicación* carpeta.</span><span class="sxs-lookup"><span data-stu-id="99afd-398">Capturing an image using the HoloLens camera and storing it in the *App* Folder.</span></span>

-   <span data-ttu-id="99afd-399">Controlar los gestos de derivación del usuario.</span><span class="sxs-lookup"><span data-stu-id="99afd-399">Handling Tap gestures from the user.</span></span>

-   <span data-ttu-id="99afd-400">Mantener la *Enum* valor que determina si la aplicación se ejecutará *Analysis* modo o *entrenamiento* modo.</span><span class="sxs-lookup"><span data-stu-id="99afd-400">Maintaining the *Enum* value that determines if the application will run in *Analysis* mode or *Training* Mode.</span></span>

<span data-ttu-id="99afd-401">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="99afd-401">To create this class:</span></span>

1.  <span data-ttu-id="99afd-402">Vaya a la **Scripts** carpeta que creó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="99afd-402">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="99afd-403">Haga clic en la carpeta, a continuación, haga clic en **crear > C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="99afd-403">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="99afd-404">Nombre de la secuencia de comandos *ImageCapture*.</span><span class="sxs-lookup"><span data-stu-id="99afd-404">Name the script *ImageCapture*.</span></span>

3.  <span data-ttu-id="99afd-405">Haga doble clic en el nuevo **ImageCapture** script para abrirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="99afd-405">Double-click on the new **ImageCapture** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="99afd-406">Reemplace los espacios de nombres en la parte superior del archivo por lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="99afd-406">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="99afd-407">A continuación, agregue las siguientes variables dentro de la *ImageCapture* clase encima el **Start()** método:</span><span class="sxs-lookup"><span data-stu-id="99afd-407">Then add the following variables inside the *ImageCapture* class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture Instance;

        /// <summary>
        /// Keep counts of the taps for image renaming
        /// </summary>
        private int captureCount = 0;

        /// <summary>
        /// Photo Capture object
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// Allows gestures recognition in HoloLens
        /// </summary>
        private GestureRecognizer recognizer;

        /// <summary>
        /// Loop timer
        /// </summary>
        private float secondsBetweenCaptures = 10f;

        /// <summary>
        /// Application main functionalities switch
        /// </summary>
        internal enum AppModes {Analysis, Training }
        
        /// <summary>
        /// Local variable for current AppMode
        /// </summary>
        internal AppModes AppMode { get; private set; }

        /// <summary>
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  <span data-ttu-id="99afd-408">El código para **Awake()** y **Start()** métodos ahora debe agregar:</span><span class="sxs-lookup"><span data-stu-id="99afd-408">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;

            // Change this flag to switch between Analysis Mode and Training Mode 
            AppMode = AppModes.Training;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Clean up the LocalState folder of this application from all photos stored
            DirectoryInfo info = new DirectoryInfo(Application.persistentDataPath);
            var fileInfo = info.GetFiles();
            foreach (var file in fileInfo)
            {
                try
                {
                    file.Delete();
                }
                catch (Exception)
                {
                    Debug.LogFormat("Cannot delete file: ", file.Name);
                }
            } 

            // Subscribing to the Hololens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();

            SceneOrganiser.Instance.SetCameraStatus("Ready");
        }
    ```

7.  <span data-ttu-id="99afd-409">Implemente un controlador que se llamará cuando se produce un gesto de pulsar.</span><span class="sxs-lookup"><span data-stu-id="99afd-409">Implement a handler that will be called when a Tap gesture occurs.</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            switch (AppMode)
            {
                case AppModes.Analysis:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;
                        
                        // Update camera status to looping capture.
                        SceneOrganiser.Instance.SetCameraStatus("Looping Capture");

                        // Begin the capture loop
                        InvokeRepeating("ExecuteImageCaptureAndAnalysis", 0, secondsBetweenCaptures);
                    }
                    else
                    {
                        // The user tapped while the app was analyzing 
                        // therefore stop the analysis process
                        ResetImageCapture();
                    }
                    break;

                case AppModes.Training:
                    if (!captureIsActive)
                    {
                        captureIsActive = true;

                        // Call the image capture
                        ExecuteImageCaptureAndAnalysis();

                        // Set the cursor color to red
                        SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                        // Update camera status to uploading image.
                        SceneOrganiser.Instance.SetCameraStatus("Uploading Image");
                    }              
                    break;
            }     
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="99afd-410">En *Analysis* modo, el **TapHandler** método actúa como un conmutador para iniciar o detener el bucle de captura de fotografías.</span><span class="sxs-lookup"><span data-stu-id="99afd-410">In *Analysis* mode, the **TapHandler** method acts as a switch to start or stop the photo capture loop.</span></span>
    >
    > <span data-ttu-id="99afd-411">En *entrenamiento* modo, capturará una imagen de la cámara.</span><span class="sxs-lookup"><span data-stu-id="99afd-411">In *Training* mode, it will capture an image from the camera.</span></span>
    >
    > <span data-ttu-id="99afd-412">Cuando el cursor está en verde, significa que la cámara está disponible para tomar la imagen.</span><span class="sxs-lookup"><span data-stu-id="99afd-412">When the cursor is green, it means the camera is available to take the image.</span></span>
    >
    > <span data-ttu-id="99afd-413">Cuando el cursor está en rojo, significa que la cámara está ocupada.</span><span class="sxs-lookup"><span data-stu-id="99afd-413">When the cursor is red, it means the camera is busy.</span></span>

8.  <span data-ttu-id="99afd-414">Agregue el método que utiliza la aplicación para iniciar el proceso de captura de imagen y almacenar la imagen.</span><span class="sxs-lookup"><span data-stu-id="99afd-414">Add the method that the application uses to start the image capture process and store the image.</span></span>

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Update camera status to analysis.
            SceneOrganiser.Instance.SetCameraStatus("Analysis");

            // Create a label in world space using the SceneOrganiser class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 0.0f,
                    cameraResolutionWidth = targetTexture.width,
                    cameraResolutionHeight = targetTexture.height,
                    pixelFormat = CapturePixelFormat.BGRA32
                };

                // Capture the image from the camera and save it in the App internal folder
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", captureCount);
                    filePath = Path.Combine(Application.persistentDataPath, filename);          
                    captureCount++;              
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);              
                });
            });   
        }
    ```

9.  <span data-ttu-id="99afd-415">Agregue los controladores que se llamará cuando se ha capturado la foto y para cuando esté listo para ser analizados.</span><span class="sxs-lookup"><span data-stu-id="99afd-415">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="99afd-416">El resultado se pasa a la *CustomVisionAnalyser* o *CustomVisionTrainer* dependiendo del modo que el código está establecido en.</span><span class="sxs-lookup"><span data-stu-id="99afd-416">The result is then passed to the *CustomVisionAnalyser* or the *CustomVisionTrainer* depending on which mode the code is set on.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }


        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            switch (AppMode)
            {
                case AppModes.Analysis:
                    // Call the image analysis
                    StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath));
                    break;

                case AppModes.Training:
                    // Call training using captured image
                    CustomVisionTrainer.Instance.RequestTagSelection();
                    break;
            }
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Update camera status to ready.
            SceneOrganiser.Instance.SetCameraStatus("Ready");

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. <span data-ttu-id="99afd-417">Asegúrese de guardar los cambios en **Visual Studio** antes de volver a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="99afd-417">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

11. <span data-ttu-id="99afd-418">Ahora que se han completado todas las secuencias de comandos, vuelva atrás en el Editor de Unity, a continuación, haga clic y arrastre el **SceneOrganiser** clase desde el **Scripts** carpeta a la **cámara principal** objeto en el *jerarquía Panel*.</span><span class="sxs-lookup"><span data-stu-id="99afd-418">Now that all the scripts have been completed, go back in the Unity Editor, then click and drag the **SceneOrganiser** class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="99afd-419">Capítulo 12 - antes de compilar</span><span class="sxs-lookup"><span data-stu-id="99afd-419">Chapter 12 - Before building</span></span>

<span data-ttu-id="99afd-420">Para llevar a cabo una prueba completa de la aplicación se necesitará para transferir localmente en su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="99afd-420">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="99afd-421">Antes de hacerlo, asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="99afd-421">Before you do, ensure that:</span></span>

- <span data-ttu-id="99afd-422">Todas las configuraciones que se mencionan en la [capítulo 2](#chapter-2---training-your-custom-vision-project) están establecidas correctamente.</span><span class="sxs-lookup"><span data-stu-id="99afd-422">All the settings mentioned in the [Chapter 2](#chapter-2---training-your-custom-vision-project) are set correctly.</span></span>

- <span data-ttu-id="99afd-423">Todos los campos de la **cámara principal**, Panel Inspector, se asignan correctamente.</span><span class="sxs-lookup"><span data-stu-id="99afd-423">All the fields in the **Main Camera**, Inspector Panel, are assigned properly.</span></span>

- <span data-ttu-id="99afd-424">La secuencia de comandos **SceneOrganiser** está asociado a la **cámara principal** objeto.</span><span class="sxs-lookup"><span data-stu-id="99afd-424">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>

- <span data-ttu-id="99afd-425">Asegúrese de insertar el **clave predicción** en el **predictionKey** variable.</span><span class="sxs-lookup"><span data-stu-id="99afd-425">Make sure you insert your **Prediction Key** into the **predictionKey** variable.</span></span>

- <span data-ttu-id="99afd-426">Ha insertado el **punto de conexión de predicción** en el **predictionEndpoint** variable.</span><span class="sxs-lookup"><span data-stu-id="99afd-426">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** variable.</span></span>

- <span data-ttu-id="99afd-427">Ha insertado su **entrenamiento clave** en el **trainingKey** variable de la *CustomVisionTrainer* clase.</span><span class="sxs-lookup"><span data-stu-id="99afd-427">You have inserted your **Training Key** into the **trainingKey** variable, of the *CustomVisionTrainer* class.</span></span>

- <span data-ttu-id="99afd-428">Ha insertado el **Id. de proyecto** en el **projectId** variable de la *CustomVisionTrainer* clase.</span><span class="sxs-lookup"><span data-stu-id="99afd-428">You have inserted your **Project ID** into the **projectId** variable, of the *CustomVisionTrainer* class.</span></span>

## <a name="chapter-13---build-and-sideload-your-application"></a><span data-ttu-id="99afd-429">Capítulo 13 - generar y transferir localmente la aplicación</span><span class="sxs-lookup"><span data-stu-id="99afd-429">Chapter 13 - Build and sideload your application</span></span>

<span data-ttu-id="99afd-430">Para comenzar la *compilar* proceso:</span><span class="sxs-lookup"><span data-stu-id="99afd-430">To begin the *Build* process:</span></span>

1.  <span data-ttu-id="99afd-431">Vaya a **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="99afd-431">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="99afd-432">Graduación **Unity C\# proyectos**.</span><span class="sxs-lookup"><span data-stu-id="99afd-432">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="99afd-433">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="99afd-433">Click **Build**.</span></span> <span data-ttu-id="99afd-434">Unity se iniciará un **Explorador de archivos** ventana, donde se debe crear y, a continuación, seleccione una carpeta para compilar la aplicación en.</span><span class="sxs-lookup"><span data-stu-id="99afd-434">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="99afd-435">Crear la carpeta y asígnele el nombre **aplicación**.</span><span class="sxs-lookup"><span data-stu-id="99afd-435">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="99afd-436">A continuación, con el **aplicación** carpeta seleccionada, haga clic en **seleccionar la carpeta**.</span><span class="sxs-lookup"><span data-stu-id="99afd-436">Then with the **App** folder selected, click on **Select Folder**.</span></span>

4.  <span data-ttu-id="99afd-437">Unity empezará a compilar el proyecto para el **aplicación** carpeta.</span><span class="sxs-lookup"><span data-stu-id="99afd-437">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="99afd-438">Una vez Unity ha finalizado la compilación (puede tardar algún tiempo), se abrirá un **Explorador de archivos** ventana en la ubicación de la compilación (comprobación de la barra de tareas, tal y como es posible que no siempre aparecen por encima de las ventanas, pero le informará de la adición de un nuevo ventana).</span><span class="sxs-lookup"><span data-stu-id="99afd-438">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

<span data-ttu-id="99afd-439">Para implementar en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="99afd-439">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="99afd-440">Necesitará la dirección IP de su HoloLens (para la implementación remota), y garantizar su HoloLens se encuentra en **modo de programador**.</span><span class="sxs-lookup"><span data-stu-id="99afd-440">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="99afd-441">Para ello:</span><span class="sxs-lookup"><span data-stu-id="99afd-441">To do this:</span></span>

    1.  <span data-ttu-id="99afd-442">Mientras que el exceso de su HoloLens, abra el **configuración**.</span><span class="sxs-lookup"><span data-stu-id="99afd-442">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="99afd-443">Vaya a **red e Internet** > **Wi-Fi** > **opciones avanzadas**</span><span class="sxs-lookup"><span data-stu-id="99afd-443">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="99afd-444">Tenga en cuenta la **IPv4** dirección.</span><span class="sxs-lookup"><span data-stu-id="99afd-444">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="99afd-445">A continuación, vaya a **configuración**y, a continuación, en **actualización y seguridad** > **para desarrolladores**</span><span class="sxs-lookup"><span data-stu-id="99afd-445">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="99afd-446">Establecer **modo de programador en**.</span><span class="sxs-lookup"><span data-stu-id="99afd-446">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="99afd-447">Vaya a la nueva compilación de Unity (la **aplicación** carpeta) y abra el archivo de solución con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="99afd-447">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="99afd-448">En el *configuración de la solución* seleccione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="99afd-448">In the *Solution Configuration* select **Debug**.</span></span>

4.  <span data-ttu-id="99afd-449">En el *plataforma de solución*, seleccione **x86, máquina remota**.</span><span class="sxs-lookup"><span data-stu-id="99afd-449">In the *Solution Platform*, select **x86, Remote Machine**.</span></span> <span data-ttu-id="99afd-450">Se le pedirá que inserte la **dirección IP** de un dispositivo remoto (el HoloLens, en este caso, lo cual observó).</span><span class="sxs-lookup"><span data-stu-id="99afd-450">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab302b-34.png)

5. <span data-ttu-id="99afd-451">Vaya a **compilar** menú y haga clic en **implementar solución** para transferir localmente la aplicación a su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="99afd-451">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6. <span data-ttu-id="99afd-452">La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas en su HoloLens, lista para iniciarse.</span><span class="sxs-lookup"><span data-stu-id="99afd-452">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="99afd-453">Para implementar en los auriculares envolventes, establezca el **plataforma de solución** a *máquina Local*y establezca el **configuración** a *depurar*, con *x86* como el **plataforma**.</span><span class="sxs-lookup"><span data-stu-id="99afd-453">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="99afd-454">Implementar, a continuación, en el equipo local machine, utilizando el **compilar** elemento de menú, seleccionar *implementar solución*.</span><span class="sxs-lookup"><span data-stu-id="99afd-454">Then deploy to the local machine, using the **Build** menu item, selecting *Deploy Solution*.</span></span> 

## <a name="to-use-the-application"></a><span data-ttu-id="99afd-455">Para usar la aplicación:</span><span class="sxs-lookup"><span data-stu-id="99afd-455">To use the application:</span></span>

<span data-ttu-id="99afd-456">Para cambiar la funcionalidad de la aplicación entre *entrenamiento* modo y *predicción* modo deberá actualizar el **AppMode** variable, que se encuentra en la **Awake()** método ubicados dentro de la *ImageCapture* clase.</span><span class="sxs-lookup"><span data-stu-id="99afd-456">To switch the app functionality between *Training* mode and *Prediction* mode you need to update the **AppMode** variable, located in the **Awake()** method located within the *ImageCapture* class.</span></span>

```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Training;
```
<span data-ttu-id="99afd-457">o bien</span><span class="sxs-lookup"><span data-stu-id="99afd-457">or</span></span>
```
        // Change this flag to switch between Analysis mode and Training mode 
        AppMode = AppModes.Analysis;
```

<span data-ttu-id="99afd-458">En *entrenamiento* modo:</span><span class="sxs-lookup"><span data-stu-id="99afd-458">In *Training* mode:</span></span>

- <span data-ttu-id="99afd-459">Examine **Mouse** o **teclado** y usar el **gesto**.</span><span class="sxs-lookup"><span data-stu-id="99afd-459">Look at **Mouse** or **Keyboard** and use the **Tap gesture**.</span></span>

- <span data-ttu-id="99afd-460">A continuación, el texto aparecerá que le pide que proporcione una etiqueta.</span><span class="sxs-lookup"><span data-stu-id="99afd-460">Next, text will appear asking you to provide a tag.</span></span>

- <span data-ttu-id="99afd-461">Indicar **Mouse** o **teclado**.</span><span class="sxs-lookup"><span data-stu-id="99afd-461">Say either **Mouse** or **Keyboard**.</span></span>


<span data-ttu-id="99afd-462">En *predicción* modo:</span><span class="sxs-lookup"><span data-stu-id="99afd-462">In *Prediction* mode:</span></span>

- <span data-ttu-id="99afd-463">Consultar un objeto y utilizar el **gesto**.</span><span class="sxs-lookup"><span data-stu-id="99afd-463">Look at an object and use the **Tap gesture**.</span></span>

- <span data-ttu-id="99afd-464">Aparecerá texto que proporciona el objeto detectado, con la probabilidad más alta (Esto se normaliza).</span><span class="sxs-lookup"><span data-stu-id="99afd-464">Text will appear providing the object detected, with the highest probability (this is normalized).</span></span>

## <a name="chapter-14---evaluate-and-improve-your-custom-vision-model"></a><span data-ttu-id="99afd-465">Capítulo 14: evaluar y mejorar su modelo de visión personalizada</span><span class="sxs-lookup"><span data-stu-id="99afd-465">Chapter 14 - Evaluate and improve your Custom Vision model</span></span>

<span data-ttu-id="99afd-466">Para hacer que el servicio más precisos, deberá continuar entrenar el modelo utilizado para la predicción.</span><span class="sxs-lookup"><span data-stu-id="99afd-466">To make your Service more accurate, you will need to continue to train the model used for prediction.</span></span> <span data-ttu-id="99afd-467">Esto se logra a través del uso de la nueva aplicación, con ambos el *entrenamiento* y *predicción* modos, con el último tener que visitar el portal, que es lo que se trata en este capítulo.</span><span class="sxs-lookup"><span data-stu-id="99afd-467">This is accomplished through using your new application, with both the *training* and *prediction* modes, with the latter requiring you to visit the portal, which is what is covered in this Chapter.</span></span> <span data-ttu-id="99afd-468">Esté preparado para volver a visitar su portal muchas veces, para mejorar continuamente el modelo.</span><span class="sxs-lookup"><span data-stu-id="99afd-468">Be prepared to revisit your portal many times, to continually improve your model.</span></span>

1. <span data-ttu-id="99afd-469">Vaya a su Portal de Azure Custom Vision nuevo y una vez que esté en el proyecto, seleccione el *predicciones* ficha (desde la parte superior central de la página):</span><span class="sxs-lookup"><span data-stu-id="99afd-469">Head to your Azure Custom Vision Portal again, and once you are in your project, select the *Predictions* tab (from the top center of the page):</span></span>

    ![](images/AzureLabs-Lab302b-35.png)

2. <span data-ttu-id="99afd-470">Verá todas las imágenes que se han enviado al servicio mientras se estaba ejecutando la aplicación.</span><span class="sxs-lookup"><span data-stu-id="99afd-470">You will see all the images which were sent to your Service whilst your application was running.</span></span> <span data-ttu-id="99afd-471">Si mantiene el puntero sobre las imágenes, le proporcionará las predicciones realizadas para la imagen:</span><span class="sxs-lookup"><span data-stu-id="99afd-471">If you hover over the images, they will provide you with the predictions that were made for that image:</span></span>

    ![](images/AzureLabs-Lab302b-36.png)

3. <span data-ttu-id="99afd-472">Seleccione una de las imágenes para abrirlo.</span><span class="sxs-lookup"><span data-stu-id="99afd-472">Select one of your images to open it.</span></span> <span data-ttu-id="99afd-473">Una vez abierto, verá las predicciones realizadas para la imagen a la derecha.</span><span class="sxs-lookup"><span data-stu-id="99afd-473">Once open, you will see the predictions made for that image to the right.</span></span> <span data-ttu-id="99afd-474">Si las predicciones fueran correctas, y que se va a agregar esta imagen al modelo de aprendizaje del servicio, haga clic en el *Mis etiquetas* cuadro de entrada y seleccione la etiqueta a la que desea asociar.</span><span class="sxs-lookup"><span data-stu-id="99afd-474">If you the predictions were correct, and you wish to add this image to your Service's training model, click the *My Tags* input box, and select the tag you wish to associate.</span></span> <span data-ttu-id="99afd-475">Cuando haya terminado, haga clic en el *guardar y cerrar* situado en la esquina inferior derecha y continúe con la siguiente imagen.</span><span class="sxs-lookup"><span data-stu-id="99afd-475">When you are finished, click the *Save and close* button to the bottom right, and continue on to the next image.</span></span>

    ![](images/AzureLabs-Lab302b-37.png)

4. <span data-ttu-id="99afd-476">Una vez que esté a la cuadrícula de imágenes, observará que las imágenes que ha agregado etiquetas a (y guardado), se quitará.</span><span class="sxs-lookup"><span data-stu-id="99afd-476">Once you are back to the grid of images, you will notice the images which you have added tags to (and saved), will be removed.</span></span> <span data-ttu-id="99afd-477">Si encuentra cualquier imagen que piensa que es necesario el elemento etiquetado dentro de ellos, puede eliminarlos, haciendo clic en el "Tick" en esa imagen (puede hacerlo para varias imágenes) y, a continuación, haga clic en *eliminar* en la esquina superior derecha de la página de cuadrícula.</span><span class="sxs-lookup"><span data-stu-id="99afd-477">If you find any images which you think do not have your tagged item within them, you can delete them, by clicking the tick on that image (can do this for several images) and then clicking *Delete* in the upper right corner of the grid page.</span></span> <span data-ttu-id="99afd-478">En la ventana emergente a continuación, puede hacer clic en cualquiera *Sí, eliminar* o *No*para confirmar la eliminación o cancelarlo, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="99afd-478">On the popup that follows, you can click either *Yes, delete* or *No*, to confirm the deletion or cancel it, respectively.</span></span> 

    ![](images/AzureLabs-Lab302b-38.png)

5. <span data-ttu-id="99afd-479">Cuando esté listo para continuar, haga clic en el verde *Train* botón en la esquina superior derecha.</span><span class="sxs-lookup"><span data-stu-id="99afd-479">When you are ready to proceed, click the green *Train* button in the top right.</span></span> <span data-ttu-id="99afd-480">Se va a entrenar un modelo de servicio con todas las imágenes que ya haya proporcionado (que le resultará más precisas).</span><span class="sxs-lookup"><span data-stu-id="99afd-480">Your Service model will be trained with all the images which you have now provided (which will make it more accurate).</span></span> <span data-ttu-id="99afd-481">Una vez completado el entrenamiento, asegúrese de hacer clic en el *Predeterminar* botón una vez más, para que su *dirección URL de la predicción* sigue usando la iteración más reciente del servicio.</span><span class="sxs-lookup"><span data-stu-id="99afd-481">Once the training is complete, make sure to click the *Make default* button once more, so that your *Prediction URL* continues to use the most up-to-date iteration of your Service.</span></span>

    <span data-ttu-id="99afd-482">![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)</span><span class="sxs-lookup"><span data-stu-id="99afd-482">![](images/AzureLabs-Lab302b-39.png) ![](images/AzureLabs-Lab302b-40.png)</span></span>

## <a name="your-finished-custom-vision-api-application"></a><span data-ttu-id="99afd-483">La aplicación finalizada de Custom Vision API</span><span class="sxs-lookup"><span data-stu-id="99afd-483">Your finished Custom Vision API application</span></span>

<span data-ttu-id="99afd-484">Enhorabuena, creó una aplicación de realidad mixta que aprovecha la API de Azure Custom Vision para reconocer objetos del mundo real, entrenar el modelo de servicio y mostrar la confianza de lo que hemos visto.</span><span class="sxs-lookup"><span data-stu-id="99afd-484">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision API to recognize real world objects, train the Service model, and display confidence of what has been seen.</span></span>

![](images/AzureLabs-Lab302b-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="99afd-485">Ejercicios de bonificación</span><span class="sxs-lookup"><span data-stu-id="99afd-485">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="99afd-486">Ejercicio 1</span><span class="sxs-lookup"><span data-stu-id="99afd-486">Exercise 1</span></span>

<span data-ttu-id="99afd-487">Entrenar su **Custom Vision Service** a reconocer más objetos.</span><span class="sxs-lookup"><span data-stu-id="99afd-487">Train your **Custom Vision Service** to recognize more objects.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="99afd-488">Ejercicio 2</span><span class="sxs-lookup"><span data-stu-id="99afd-488">Exercise 2</span></span>

<span data-ttu-id="99afd-489">Como una forma de ampliar lo que ha aprendido, completar los ejercicios siguientes:</span><span class="sxs-lookup"><span data-stu-id="99afd-489">As a way to expand on what you have learned, complete the following exercises:</span></span>

<span data-ttu-id="99afd-490">Reproducir un sonido cuando se reconoce un objeto.</span><span class="sxs-lookup"><span data-stu-id="99afd-490">Play a sound when an object is recognized.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="99afd-491">Ejercicio 3</span><span class="sxs-lookup"><span data-stu-id="99afd-491">Exercise 3</span></span>

<span data-ttu-id="99afd-492">Usar la API para volver a entrenar el servicio con las mismas imágenes que se está analizando la aplicación, por lo tanto, para que el servicio más precisos (realizar tareas de predicción y aprendizaje de forma simultánea).</span><span class="sxs-lookup"><span data-stu-id="99afd-492">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
