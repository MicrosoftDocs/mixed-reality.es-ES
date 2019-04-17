---
title: El Sr. y 310 Azure - detección de objetos
description: Complete este curso para obtener información sobre cómo entrenar un modelo de aprendizaje automático y, a continuación, use el modelo entrenado para reconocer objetos similares y su posición en el mundo real desde dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: objeto de Azure, visión personalizada, detección, mixto en realidad, academy, unity, tutorial, api, hololens
ms.openlocfilehash: 89ee79943a88de8a34c679ae33621db5770908b0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597648"
---
>[!NOTE]
><span data-ttu-id="80077-104">Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.</span><span class="sxs-lookup"><span data-stu-id="80077-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="80077-105">Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="80077-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="80077-106">Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.</span><span class="sxs-lookup"><span data-stu-id="80077-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="80077-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="80077-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="80077-108">Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="80077-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="80077-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.</span><span class="sxs-lookup"><span data-stu-id="80077-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-310-object-detection"></a><span data-ttu-id="80077-110">El Sr. y Azure 310: Detección de objetos</span><span class="sxs-lookup"><span data-stu-id="80077-110">Mr and Azure 310: Object detection</span></span>

<span data-ttu-id="80077-111">En este curso, aprenderá a reconocer contenido visual personalizado y su posición dentro de una imagen proporcionada, espacial con Azure Custom Vision capacidades "Detección de objetos" en una aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="80077-111">In this course, you will learn how to recognize custom visual content and its spatial position within a provided image, using Azure Custom Vision "Object Detection" capabilities in a mixed reality application.</span></span>

<span data-ttu-id="80077-112">Este servicio, podrá entrenar un modelo de aprendizaje automático mediante imágenes de objeto.</span><span class="sxs-lookup"><span data-stu-id="80077-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="80077-113">A continuación, usará el modelo entrenado para reconocer objetos similares y aproximarse a su ubicación en el mundo real, tal como lo proporciona la captura de cámara de Microsoft HoloLens o una cámara de conectarse a un PC para inmersivos (VR).</span><span class="sxs-lookup"><span data-stu-id="80077-113">You will then use the trained model to recognize similar objects and approximate their location in the real world, as provided by the camera capture of Microsoft HoloLens or a camera connect to a PC for immersive (VR) headsets.</span></span>

![resultado del curso](images/AzureLabs-Lab310-00.png)

<span data-ttu-id="80077-115">**Azure Custom Vision, detección de objetos** es un Service Microsoft que permite a los desarrolladores crear clasificadores de imagen personalizada.</span><span class="sxs-lookup"><span data-stu-id="80077-115">**Azure Custom Vision, Object Detection** is a Microsoft Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="80077-116">Estos clasificadores, a continuación, pueden utilizarse con las nuevas imágenes para detectar objetos dentro de esa imagen, proporcionando **los límites del cuadro** dentro de la imagen en Sí.</span><span class="sxs-lookup"><span data-stu-id="80077-116">These classifiers can then be used with new images to detect objects within that new image, by providing **Box Boundaries** within the image itself.</span></span> <span data-ttu-id="80077-117">El servicio proporciona un portal fácil de usar, sencillo y en línea para simplificar este proceso.</span><span class="sxs-lookup"><span data-stu-id="80077-117">The Service provides a simple, easy to use, online portal to streamline this process.</span></span> <span data-ttu-id="80077-118">Para obtener más información, visite los vínculos siguientes:</span><span class="sxs-lookup"><span data-stu-id="80077-118">For more information, visit the following links:</span></span>

* [<span data-ttu-id="80077-119">Página de Azure Custom Vision</span><span class="sxs-lookup"><span data-stu-id="80077-119">Azure Custom Vision page</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [<span data-ttu-id="80077-120">Límites y cuotas</span><span class="sxs-lookup"><span data-stu-id="80077-120">Limits and Quotas</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

<span data-ttu-id="80077-121">Tras la finalización de este curso, tendrá una aplicación de realidad mixta que podrá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="80077-121">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1. <span data-ttu-id="80077-122">El usuario podrá *que mirar* en un objeto que ha entrenado mediante Azure Custom Vision Service, detección de objetos.</span><span class="sxs-lookup"><span data-stu-id="80077-122">The user will be able to *gaze* at an object, which they have trained using the Azure Custom Vision Service, Object Detection.</span></span> 
2. <span data-ttu-id="80077-123">El usuario usará el *pulse* gesto para capturar una imagen de lo están mirando.</span><span class="sxs-lookup"><span data-stu-id="80077-123">The user will use the *Tap* gesture to capture an image of what they are looking at.</span></span>
3. <span data-ttu-id="80077-124">La aplicación enviará la imagen a Azure Custom Vision Service.</span><span class="sxs-lookup"><span data-stu-id="80077-124">The app will send the image to the Azure Custom Vision Service.</span></span>
4. <span data-ttu-id="80077-125">Habrá una respuesta desde el servicio que se mostrará el resultado del reconocimiento como texto de espacio global.</span><span class="sxs-lookup"><span data-stu-id="80077-125">There will be a reply from the Service which will display the result of the recognition as world-space text.</span></span> <span data-ttu-id="80077-126">Esto se logrará mediante la utilización espacial de seguimiento de la Microsoft HoloLens, como una manera de entender la posición global del objeto reconocido y, a continuación, usar el *etiqueta* asociados con lo que se detecta en la imagen, a Escriba el texto de etiqueta.</span><span class="sxs-lookup"><span data-stu-id="80077-126">This will be accomplished through utilizing the Microsoft HoloLens' Spatial Tracking, as a way of understanding the world position of the recognized object, and then using the *Tag* associated with what is detected in the image, to provide the label text.</span></span>

<span data-ttu-id="80077-127">El curso también cubrirá manualmente cargar imágenes, crear etiquetas, y el servicio, para que reconozca diferentes entrenamiento objetos (en el ejemplo proporcionado, una taza), por establecer el *cuadro de límite* dentro de la imagen que envíe.</span><span class="sxs-lookup"><span data-stu-id="80077-127">The course will also cover manually uploading images, creating tags, and training the Service, to recognize different objects (in the provided example, a cup), by setting the *Boundary Box* within the image you submit.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="80077-128">Después de la creación y uso de la aplicación, el desarrollador debe navegar hasta Azure Custom Vision Service, identificar las predicciones realizadas por el servicio y determinar si era correctas o no (a través del etiquetado nada del servicio perdió, y ajustar el *cuadros de límite*).</span><span class="sxs-lookup"><span data-stu-id="80077-128">Following the creation and use of the app, the developer should navigate back to the Azure Custom Vision Service, and identify the predictions made by the Service, and determine whether they were correct or not (through tagging anything the Service missed, and adjusting the *Bounding Boxes*).</span></span> <span data-ttu-id="80077-129">El servicio, a continuación, se puede volver a entrenar, lo que aumentará la probabilidad de que el reconocimiento de objetos del mundo real.</span><span class="sxs-lookup"><span data-stu-id="80077-129">The Service can then be re-trained, which will increase the likelihood of it recognizing real world objects.</span></span>

<span data-ttu-id="80077-130">Este curso le mostrará cómo obtener los resultados de Azure Custom Vision Service, detección de objetos, en una aplicación de ejemplo basada en Unity.</span><span class="sxs-lookup"><span data-stu-id="80077-130">This course will teach you how to get the results from the Azure Custom Vision Service, Object Detection, into a Unity-based sample application.</span></span> <span data-ttu-id="80077-131">Será quien decide estos conceptos se aplican a una aplicación personalizada puede que esté creando.</span><span class="sxs-lookup"><span data-stu-id="80077-131">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="80077-132">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="80077-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="80077-133">Curso</span><span class="sxs-lookup"><span data-stu-id="80077-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="80077-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="80077-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="80077-135"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="80077-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="80077-136">El Sr. y Azure 310: Detección de objetos</span><span class="sxs-lookup"><span data-stu-id="80077-136">MR and Azure 310: Object detection</span></span></td><td style="text-align: center;"> <span data-ttu-id="80077-137">✔️</span><span class="sxs-lookup"><span data-stu-id="80077-137">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="80077-138">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="80077-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="80077-139">Este tutorial está diseñado para los desarrolladores con experiencia básica con Unity y C#.</span><span class="sxs-lookup"><span data-stu-id="80077-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="80077-140">También Ten en cuenta que los requisitos previos y las instrucciones escritas en este documento representan lo que se ha probado y comprobado en el momento de redactar (julio de 2018).</span><span class="sxs-lookup"><span data-stu-id="80077-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="80077-141">Es libre de usar el software más reciente, como se muestra en el [instalar las herramientas de](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) artículo, aunque no se debe suponer que la información de este curso perfectamente coincida con lo que encontrará en el software más reciente que se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="80077-141">You are free to use the latest software, as listed within the [install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="80077-142">Se recomiendan el siguiente hardware y software para este curso:</span><span class="sxs-lookup"><span data-stu-id="80077-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="80077-143">Un equipo de desarrollo</span><span class="sxs-lookup"><span data-stu-id="80077-143">A development PC</span></span>
- [<span data-ttu-id="80077-144">Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="80077-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="80077-145">El SDK más reciente de Windows 10</span><span class="sxs-lookup"><span data-stu-id="80077-145">The latest Windows 10 SDK</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="80077-146">Unity 2017.4 LTS</span><span class="sxs-lookup"><span data-stu-id="80077-146">Unity 2017.4 LTS</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="80077-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="80077-147">Visual Studio 2017</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- <span data-ttu-id="80077-148">Un [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="80077-148">A [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) with Developer mode enabled</span></span>
- <span data-ttu-id="80077-149">Acceso a Internet para el programa de instalación de Azure y la recuperación de Custom Vision Service</span><span class="sxs-lookup"><span data-stu-id="80077-149">Internet access for Azure setup and Custom Vision Service retrieval</span></span>
-  <span data-ttu-id="80077-150">Se requieren una serie de imágenes al menos quince (15)) para cada objeto que desea que la visión personalizada para que reconozca.</span><span class="sxs-lookup"><span data-stu-id="80077-150">A series of at least fifteen (15) images are required) for each object that you would like the Custom Vision to recognize.</span></span> <span data-ttu-id="80077-151">Si lo desea, puede usar las imágenes que ya se proporciona con este curso, [una serie de tazas](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span><span class="sxs-lookup"><span data-stu-id="80077-151">If you wish, you can use the images already provided with this course, [a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="80077-152">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="80077-152">Before you start</span></span>

1.  <span data-ttu-id="80077-153">Para evitar problemas de creación de este proyecto, se recomienda encarecidamente que cree el proyecto se ha mencionado en este tutorial en una carpeta raíz o cerca de la raíz (rutas de acceso de carpeta largo pueden causar problemas en tiempo de compilación).</span><span class="sxs-lookup"><span data-stu-id="80077-153">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="80077-154">Configurar y probar su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="80077-154">Set up and test your HoloLens.</span></span> <span data-ttu-id="80077-155">Si necesita admite la configuración de su HoloLens, [Asegúrese de visitar el artículo del programa de instalación de HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="80077-155">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="80077-156">Es una buena idea para realizar la calibración y optimización Sensor cuando comienza a desarrollar una App HoloLens nuevo (a veces puede ayudar a realizar dichas tareas para cada usuario).</span><span class="sxs-lookup"><span data-stu-id="80077-156">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="80077-157">Para obtener ayuda sobre la calibración, siga este [vínculo al artículo de calibración de HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="80077-157">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="80077-158">Para obtener ayuda sobre optimización Sensor, siga este [vínculo al artículo optimización Sensor de HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="80077-158">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-portal"></a><span data-ttu-id="80077-159">Capítulo 1: el Portal de Custom Vision</span><span class="sxs-lookup"><span data-stu-id="80077-159">Chapter 1 - The Custom Vision Portal</span></span>

<span data-ttu-id="80077-160">Para usar el **Azure Custom Vision Service**, deberá configurar una instancia de ella esté disponible para su aplicación.</span><span class="sxs-lookup"><span data-stu-id="80077-160">To use the **Azure Custom Vision Service**, you will need to configure an instance of it to be made available to your application.</span></span>

1.  <span data-ttu-id="80077-161">Navegue [a la **Custom Vision Service** página principal](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span><span class="sxs-lookup"><span data-stu-id="80077-161">Navigate [to the **Custom Vision Service** main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="80077-162">Haga clic en **Introducción**.</span><span class="sxs-lookup"><span data-stu-id="80077-162">Click on **Getting Started**.</span></span>

    ![](images/AzureLabs-Lab310-01.png)

3.  <span data-ttu-id="80077-163">Inicie sesión en el Portal de visión personalizada.</span><span class="sxs-lookup"><span data-stu-id="80077-163">Sign in to the Custom Vision Portal.</span></span>

    ![](images/AzureLabs-Lab310-02.png)

4.  <span data-ttu-id="80077-164">Si no dispone de una cuenta de Azure, deberá crear uno.</span><span class="sxs-lookup"><span data-stu-id="80077-164">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="80077-165">Si está siguiendo este tutorial en una situación de aula o laboratorio, pida el instructor o uno de los a los supervisores de ayuda para instalar la nueva cuenta.</span><span class="sxs-lookup"><span data-stu-id="80077-165">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

5.  <span data-ttu-id="80077-166">Una vez que haya iniciado sesión por primera vez, se le pedirá con el *condiciones del servicio* panel.</span><span class="sxs-lookup"><span data-stu-id="80077-166">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="80077-167">Haga clic en la casilla de verificación *acepta los términos*.</span><span class="sxs-lookup"><span data-stu-id="80077-167">Click the checkbox to *agree to the terms*.</span></span> <span data-ttu-id="80077-168">A continuación, haga clic en **acepto**.</span><span class="sxs-lookup"><span data-stu-id="80077-168">Then click **I agree**.</span></span>

    ![](images/AzureLabs-Lab310-03.png)

6.  <span data-ttu-id="80077-169">Tener aceptado los términos, ya está en el *Mis proyectos* sección.</span><span class="sxs-lookup"><span data-stu-id="80077-169">Having agreed to the terms, you are now in the *My Projects* section.</span></span> <span data-ttu-id="80077-170">Haga clic en **nuevo proyecto**.</span><span class="sxs-lookup"><span data-stu-id="80077-170">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab310-04.png)

7.  <span data-ttu-id="80077-171">Aparecerá una ficha en el lado derecho, que le solicitará que especifique algunos campos para el proyecto.</span><span class="sxs-lookup"><span data-stu-id="80077-171">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="80077-172">Insertar un nombre para el proyecto</span><span class="sxs-lookup"><span data-stu-id="80077-172">Insert a name for your project</span></span>

    2.  <span data-ttu-id="80077-173">Insertar una descripción para el proyecto (**opcional**)</span><span class="sxs-lookup"><span data-stu-id="80077-173">Insert a description for your project (**Optional**)</span></span>

    3.  <span data-ttu-id="80077-174">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="80077-174">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="80077-175">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="80077-175">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="80077-176">Se recomienda mantener todos los servicios de Azure asociados a un proyecto único (por ejemplo, por ejemplo, estos cursos) en un grupo de recursos comunes).</span><span class="sxs-lookup"><span data-stu-id="80077-176">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > <span data-ttu-id="80077-177">Si desea [Obtenga más información acerca de los grupos de recursos de Azure, vaya a los documentos asociados](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="80077-177">If you wish to [read more about Azure Resource Groups, navigate to the associated Docs](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4.  <span data-ttu-id="80077-178">Establecer el **tipos de proyecto** como **(versión preliminar) de detección de objetos**.</span><span class="sxs-lookup"><span data-stu-id="80077-178">Set the **Project Types** as **Object Detection (preview)**.</span></span>

8.  <span data-ttu-id="80077-179">Una vez haya terminado, haga clic en **crear un proyecto**, y se le redirigirá a la página de proyectos de Custom Vision Service.</span><span class="sxs-lookup"><span data-stu-id="80077-179">Once you are finished, click on **Create project**, and you will be redirected to the Custom Vision Service project page.</span></span>


## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="80077-180">Capítulo 2: el proyecto de Custom Vision de entrenamiento</span><span class="sxs-lookup"><span data-stu-id="80077-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="80077-181">Una vez en el Portal de visión personalizada, su principal objetivo es entrenar su proyecto para reconocer objetos específicos en las imágenes.</span><span class="sxs-lookup"><span data-stu-id="80077-181">Once in the Custom Vision Portal, your primary objective is to train your project to recognize specific objects in images.</span></span>

<span data-ttu-id="80077-182">Necesita al menos quince (15) imágenes para cada objeto que desea que la aplicación reconozca.</span><span class="sxs-lookup"><span data-stu-id="80077-182">You need at least fifteen (15) images for each object that you would like your application to recognize.</span></span> <span data-ttu-id="80077-183">Puede usar las imágenes proporcionadas con este curso ([una serie de tazas](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span><span class="sxs-lookup"><span data-stu-id="80077-183">You can use the images provided with this course ([a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

<span data-ttu-id="80077-184">Para entrenar el proyecto de Custom Vision:</span><span class="sxs-lookup"><span data-stu-id="80077-184">To train your Custom Vision project:</span></span>

1.  <span data-ttu-id="80077-185">Haga clic en el **+** situado junto a **etiquetas**.</span><span class="sxs-lookup"><span data-stu-id="80077-185">Click on the **+** button next to **Tags**.</span></span>

    ![](images/AzureLabs-Lab310-06.png)

2.  <span data-ttu-id="80077-186">Agregar un **nombre** para la etiqueta que se usará para asociar las imágenes con.</span><span class="sxs-lookup"><span data-stu-id="80077-186">Add a **name** for the tag that will be used to associate your images with.</span></span> <span data-ttu-id="80077-187">En este ejemplo para el reconocimiento, por lo que ha asignado un nombre de la etiqueta para esto, usamos las imágenes de tazas **Cup**.</span><span class="sxs-lookup"><span data-stu-id="80077-187">In this example we are using images of cups for recognition, so have named the tag for this, **Cup**.</span></span> <span data-ttu-id="80077-188">Haga clic en **guardar** una vez finalizado.</span><span class="sxs-lookup"><span data-stu-id="80077-188">Click **Save** once finished.</span></span>

    ![](images/AzureLabs-Lab310-07.png)

3.  <span data-ttu-id="80077-189">Observará el **etiqueta** se ha agregado (es posible que deba volver a cargar la página para que aparezca).</span><span class="sxs-lookup"><span data-stu-id="80077-189">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> 

    ![](images/AzureLabs-Lab310-08.png)

4.  <span data-ttu-id="80077-190">Haga clic en **agregar imágenes** en el centro de la página.</span><span class="sxs-lookup"><span data-stu-id="80077-190">Click on **Add images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab310-09.png)

5.  <span data-ttu-id="80077-191">Haga clic en **examinar archivos locales**y vaya a las imágenes que desea cargar un objeto, siendo el mínimo quince (15).</span><span class="sxs-lookup"><span data-stu-id="80077-191">Click on **Browse local files**, and browse to the images you would like to upload for one object, with the minimum being fifteen (15).</span></span>

    > [!TIP]
    >  <span data-ttu-id="80077-192">Puede seleccionar varias imágenes a la vez, para cargar.</span><span class="sxs-lookup"><span data-stu-id="80077-192">You can select several images at a time, to upload.</span></span>

    ![](images/AzureLabs-Lab310-10.png)

6.  <span data-ttu-id="80077-193">Presione **cargar archivos** una vez haya seleccionado todas las imágenes que desea entrenar el proyecto con.</span><span class="sxs-lookup"><span data-stu-id="80077-193">Press **Upload files** once you have selected all the images you would like to train the project with.</span></span> <span data-ttu-id="80077-194">Los archivos cargarán.</span><span class="sxs-lookup"><span data-stu-id="80077-194">The files will begin uploading.</span></span> <span data-ttu-id="80077-195">Una vez que la confirmación de la carga, haga clic en **realiza**.</span><span class="sxs-lookup"><span data-stu-id="80077-195">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab310-11.png)

7.  <span data-ttu-id="80077-196">En este momento las imágenes se cargan, pero no etiquetadas.</span><span class="sxs-lookup"><span data-stu-id="80077-196">At this point your images are uploaded, but not tagged.</span></span>

    ![](images/AzureLabs-Lab310-12.png)

8.  <span data-ttu-id="80077-197">Para etiquetar las imágenes, use el mouse.</span><span class="sxs-lookup"><span data-stu-id="80077-197">To tag your images, use your mouse.</span></span> <span data-ttu-id="80077-198">Cuando se sitúa encima de la imagen, un área resaltada de selección le ayudará a dibujando automáticamente una selección alrededor de su objeto.</span><span class="sxs-lookup"><span data-stu-id="80077-198">As you hover over your image, a selection highlight will aid you by automatically drawing a selection around your object.</span></span> <span data-ttu-id="80077-199">Si no es preciso, puede dibujar sus propios.</span><span class="sxs-lookup"><span data-stu-id="80077-199">If it is not accurate, you can draw your own.</span></span> <span data-ttu-id="80077-200">Esto se logra manteniendo primario del mouse, y arrastrando la región de selección para abarcar el objeto.</span><span class="sxs-lookup"><span data-stu-id="80077-200">This is accomplished by holding left-click on the mouse, and dragging the selection region to encompass your object.</span></span> 

    ![](images/AzureLabs-Lab310-13.png) 

9. <span data-ttu-id="80077-201">Después de la selección del objeto dentro de la imagen, un pequeño se le preguntará si desea *Agregar etiqueta Region*.</span><span class="sxs-lookup"><span data-stu-id="80077-201">Following the selection of your object within the image, a small prompt will ask for you to *Add Region Tag*.</span></span> <span data-ttu-id="80077-202">Seleccione la etiqueta creada anteriormente (en el ejemplo anterior, "Cup"), o si va a agregar más etiquetas, que, en Escriba y haga clic en el **+ (signo más)** botón.</span><span class="sxs-lookup"><span data-stu-id="80077-202">Select your previously created tag ('Cup', in the above example), or if you are adding more tags, type that in and click the **+ (plus)** button.</span></span>

    ![](images/AzureLabs-Lab310-14.png) 

10. <span data-ttu-id="80077-203">Para etiquetar la imagen siguiente, puede haga clic en la flecha situada a la derecha de la hoja, o cierre la hoja de etiquetas (haciendo clic en el **X** en la esquina superior derecha de la hoja) y, a continuación, haga clic en la siguiente imagen.</span><span class="sxs-lookup"><span data-stu-id="80077-203">To tag the next image, you can click the arrow to the right of the blade, or close the tag blade (by clicking the **X** in the top-right corner of the blade) and then click the next image.</span></span> <span data-ttu-id="80077-204">Una vez que la imagen siguiente lista, repita el mismo procedimiento.</span><span class="sxs-lookup"><span data-stu-id="80077-204">Once you have the next image ready, repeat the same procedure.</span></span> <span data-ttu-id="80077-205">Hágalo para todas las imágenes que ha cargado, hasta que todos están etiquetados.</span><span class="sxs-lookup"><span data-stu-id="80077-205">Do this for all the images you have uploaded, until they are all tagged.</span></span> 

    > [!NOTE]
    >  <span data-ttu-id="80077-206">Puede seleccionar varios objetos en la misma imagen, al igual que la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="80077-206">You can select several objects in the same image, like the image below:</span></span> 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. <span data-ttu-id="80077-207">Una vez que haya etiquetado todas ellas, haga clic en el **etiquetadas** botón a la izquierda de la pantalla para mostrar las imágenes etiquetadas.</span><span class="sxs-lookup"><span data-stu-id="80077-207">Once you have tagged them all, click on the **tagged** button, on the left of the screen, to reveal the tagged images.</span></span> 

    ![](images/AzureLabs-Lab310-16.png)

12. <span data-ttu-id="80077-208">Ahora está listo para entrenar el servicio.</span><span class="sxs-lookup"><span data-stu-id="80077-208">You are now ready to train your Service.</span></span> <span data-ttu-id="80077-209">Haga clic en el **Train** botón y la primera iteración de entrenamiento se iniciará.</span><span class="sxs-lookup"><span data-stu-id="80077-209">Click the **Train** button, and the first training iteration will begin.</span></span>

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. <span data-ttu-id="80077-210">Una vez compilada, podrá ver dos botones denominados **Predeterminar** y **predicción URL**.</span><span class="sxs-lookup"><span data-stu-id="80077-210">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="80077-211">Haga clic en **Predeterminar** en primer lugar, a continuación, haga clic en **predicción URL**.</span><span class="sxs-lookup"><span data-stu-id="80077-211">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > <span data-ttu-id="80077-212">El punto de conexión que se proporciona con esto, se establece en lo que ocurra *iteración* está marcada como predeterminada.</span><span class="sxs-lookup"><span data-stu-id="80077-212">The endpoint which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="80077-213">Como tal, si posteriormente realiza una nueva *iteración* y actualizarlo como valor predeterminado, no necesitará cambiar el código.</span><span class="sxs-lookup"><span data-stu-id="80077-213">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

14. <span data-ttu-id="80077-214">Una vez que ha hecho clic **dirección URL de la predicción**, abra *el Bloc de notas*y copie y pegue el **URL** (también se denomina su **predicción extremo**) y el **clave de predicción de servicio**, de modo que puede recuperar cuando necesite más adelante en el código.</span><span class="sxs-lookup"><span data-stu-id="80077-214">Once you have clicked on **Prediction URL**, open *Notepad*, and copy and paste the **URL** (also called your **Prediction-Endpoint**) and the **Service Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="80077-215">Capítulo 3: configurar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="80077-215">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="80077-216">El siguiente es un conjunto típico de para el desarrollo con la realidad mixta y por lo tanto, es una buena plantilla para otros proyectos.</span><span class="sxs-lookup"><span data-stu-id="80077-216">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="80077-217">Abra **Unity** y haga clic en **New**.</span><span class="sxs-lookup"><span data-stu-id="80077-217">Open **Unity** and click **New**.</span></span>

    ![](images/AzureLabs-Lab310-21.png)

2.  <span data-ttu-id="80077-218">Ahora deberá proporcionar un nombre de proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="80077-218">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="80077-219">Insertar **CustomVisionObjDetection**.</span><span class="sxs-lookup"><span data-stu-id="80077-219">Insert **CustomVisionObjDetection**.</span></span> <span data-ttu-id="80077-220">Asegúrese de que el tipo de proyecto se establece en **3D**y establezca el **ubicación** a algún lugar adecuado para usted (Recuerde, es mejor cuanto más se acerque a los directorios raíz).</span><span class="sxs-lookup"><span data-stu-id="80077-220">Make sure the project type is set to **3D**, and set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="80077-221">A continuación, haga clic en **crear un proyecto**.</span><span class="sxs-lookup"><span data-stu-id="80077-221">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab310-22.png)

3.  <span data-ttu-id="80077-222">Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="80077-222">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="80077-223">Vaya a **editar* > *preferencias** y, a continuación, en la ventana nueva, vaya a **herramientas externas**.</span><span class="sxs-lookup"><span data-stu-id="80077-223">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="80077-224">Cambio **External Script Editor** a **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="80077-224">Change **External Script Editor** to **Visual Studio**.</span></span> <span data-ttu-id="80077-225">Cerrar la **preferencias** ventana.</span><span class="sxs-lookup"><span data-stu-id="80077-225">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab310-23.png)

4.  <span data-ttu-id="80077-226">A continuación, vaya a **archivo > configuración de compilación** y cambie el **plataforma** a *Universal Windows Platform*y, a continuación, haga clic en el **Cambiar plataforma** botón.</span><span class="sxs-lookup"><span data-stu-id="80077-226">Next, go to **File > Build Settings** and switch the **Platform** to *Universal Windows Platform*, and then clicking on the **Switch Platform** button.</span></span>

    ![](images/AzureLabs-Lab310-24.png)

5.  <span data-ttu-id="80077-227">En el mismo **configuración de compilación** ventana, asegúrese de que se establezca lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="80077-227">In the same **Build Settings** window, ensure the following are set:</span></span>

    1.  <span data-ttu-id="80077-228">**Dispositivo de destino** está establecido en **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="80077-228">**Target Device** is set to **HoloLens**</span></span>        
    2.  <span data-ttu-id="80077-229">**Tipo de compilación** está establecido en **D3D**</span><span class="sxs-lookup"><span data-stu-id="80077-229">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="80077-230">**SDK** está establecido en **instalada más reciente**</span><span class="sxs-lookup"><span data-stu-id="80077-230">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="80077-231">**Versión de Visual Studio** está establecido en **instalada más reciente**</span><span class="sxs-lookup"><span data-stu-id="80077-231">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="80077-232">**Compilar y ejecutar** está establecido en **máquina Local**</span><span class="sxs-lookup"><span data-stu-id="80077-232">**Build and Run** is set to **Local Machine**</span></span>            
    6.  <span data-ttu-id="80077-233">El resto de la configuración, en **configuración de compilación**, debe dejarse como predeterminada por ahora.</span><span class="sxs-lookup"><span data-stu-id="80077-233">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab310-25.png)

6.  <span data-ttu-id="80077-234">En el mismo **configuración de compilación** ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el **Inspector** se encuentra.</span><span class="sxs-lookup"><span data-stu-id="80077-234">In the same **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7. <span data-ttu-id="80077-235">En este panel, es necesario comprobar algunas opciones de configuración:</span><span class="sxs-lookup"><span data-stu-id="80077-235">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="80077-236">En el **otra configuración** pestaña:</span><span class="sxs-lookup"><span data-stu-id="80077-236">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="80077-237">**Versión en tiempo de ejecución de secuencias de comandos** debe ser **Experimental** (.NET 4.6 equivalente), que desencadenará una necesidad de reiniciar el Editor.</span><span class="sxs-lookup"><span data-stu-id="80077-237">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="80077-238">**Scripting de back-end** debe ser **.NET**.</span><span class="sxs-lookup"><span data-stu-id="80077-238">**Scripting Backend** should be **.NET**.</span></span>

        3. <span data-ttu-id="80077-239">**Nivel de compatibilidad de API** debe ser **.NET 4.6**.</span><span class="sxs-lookup"><span data-stu-id="80077-239">**API Compatibility Level** should be **.NET 4.6**.</span></span>

            ![](images/AzureLabs-Lab310-26.png)

    2.  <span data-ttu-id="80077-240">Dentro de la **configuración de publicación** ficha **capacidades**, consulte:</span><span class="sxs-lookup"><span data-stu-id="80077-240">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="80077-241">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="80077-241">**InternetClient**</span></span>

        2.  <span data-ttu-id="80077-242">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="80077-242">**Webcam**</span></span>

        3. <span data-ttu-id="80077-243">**SpatialPerception**</span><span class="sxs-lookup"><span data-stu-id="80077-243">**SpatialPerception**</span></span>

            <span data-ttu-id="80077-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span><span class="sxs-lookup"><span data-stu-id="80077-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span></span>

    3.  <span data-ttu-id="80077-245">Más abajo el panel, en **XR configuración** (situado debajo de **configuración de publicación**), graduación **admite la realidad Virtual**, a continuación, asegúrese de que el **mixto de Windows Realidad SDK** se agrega.</span><span class="sxs-lookup"><span data-stu-id="80077-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, then make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab310-29.png)

8.  <span data-ttu-id="80077-246">En **configuración de compilación**, *Unity C\# proyectos* ya no está atenuado: Marque la casilla situada junto a esto.</span><span class="sxs-lookup"><span data-stu-id="80077-246">Back in **Build Settings**, *Unity C\# Projects* is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="80077-247">Cerrar la **configuración de compilación** ventana.</span><span class="sxs-lookup"><span data-stu-id="80077-247">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="80077-248">En el **Editor**, haga clic en **editar** > **configuración del proyecto** > **gráficos**.</span><span class="sxs-lookup"><span data-stu-id="80077-248">In the **Editor**, click on **Edit** > **Project Settings** > **Graphics**.</span></span>

    ![](images/AzureLabs-Lab310-30.png)

11. <span data-ttu-id="80077-249">En el **Panel Inspector** el *configuración gráficos* estará abierto.</span><span class="sxs-lookup"><span data-stu-id="80077-249">In the **Inspector Panel** the *Graphics Settings* will be open.</span></span> <span data-ttu-id="80077-250">Desplácese hacia abajo hasta que vea una matriz denominada **siempre incluyen los sombreadores**.</span><span class="sxs-lookup"><span data-stu-id="80077-250">Scroll down until you see an array called **Always Include Shaders**.</span></span> <span data-ttu-id="80077-251">Agregar una ranura aumentando la **tamaño** variable en uno (en este ejemplo, fuera 8 por lo que lo hicimos 9).</span><span class="sxs-lookup"><span data-stu-id="80077-251">Add a slot by increasing the **Size** variable by one (in this example, it was 8 so we made it 9).</span></span> <span data-ttu-id="80077-252">Una nueva ranura aparecerá en la última posición de la matriz, como se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="80077-252">A new slot will appear, in the last position of the array, as shown below:</span></span>

    ![](images/AzureLabs-Lab310-31.png)

12. <span data-ttu-id="80077-253">En la ranura, haga clic en el círculo pequeño de destino junto a la ranura para abrir una lista de los sombreadores.</span><span class="sxs-lookup"><span data-stu-id="80077-253">In the slot, click on the small target circle next to the slot to open a list of shaders.</span></span> <span data-ttu-id="80077-254">Busque el **heredado sombreadores/Transparent/difuso** sombreador y haga doble clic en él.</span><span class="sxs-lookup"><span data-stu-id="80077-254">Look for the **Legacy Shaders/Transparent/Diffuse** shader and double-click it.</span></span> 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a><span data-ttu-id="80077-255">Capítulo 4: importar el paquete de CustomVisionObjDetection Unity</span><span class="sxs-lookup"><span data-stu-id="80077-255">Chapter 4 - Importing the CustomVisionObjDetection Unity package</span></span>

<span data-ttu-id="80077-256">Para este curso se proporcionan con un paquete de activos de Unity, denominada **MR-Azure-310.unitypackage**.</span><span class="sxs-lookup"><span data-stu-id="80077-256">For this course you are provided with a Unity Asset Package called **Azure-MR-310.unitypackage**.</span></span> 

> <span data-ttu-id="80077-257">[SUGERENCIA] Todos los objetos compatibles con Unity, incluidas las escenas completas, se pueden empaquetar en un **.unitypackage** archivo y exportar / importar en otros proyectos.</span><span class="sxs-lookup"><span data-stu-id="80077-257">[TIP] Any objects supported by Unity, including entire scenes, can be packaged into a **.unitypackage** file, and exported / imported in other projects.</span></span> <span data-ttu-id="80077-258">Es la manera más segura y más eficaz para mover recursos entre los distintos **proyectos de Unity**.</span><span class="sxs-lookup"><span data-stu-id="80077-258">It is the safest, and most efficient, way to move assets between different **Unity projects**.</span></span>

<span data-ttu-id="80077-259">Puede encontrar el [paquete Azure-MR-310 que deba descargar aquí](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="80077-259">You can find the [Azure-MR-310 package that you need to download here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span></span>

1.  <span data-ttu-id="80077-260">Con el panel de Unity delante de usted, haga clic en **activos** en el menú en la parte superior de la pantalla, a continuación, haga clic en **Importar paquete > paquete personalizado**.</span><span class="sxs-lookup"><span data-stu-id="80077-260">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![](images/AzureLabs-Lab310-33.png)

2.  <span data-ttu-id="80077-261">Utilice el selector de archivos para seleccionar la **MR-Azure-310.unitypackage** del paquete y haga clic en **abierto**.</span><span class="sxs-lookup"><span data-stu-id="80077-261">Use the file picker to select the **Azure-MR-310.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="80077-262">Se mostrará una lista de componentes para este recurso para usted.</span><span class="sxs-lookup"><span data-stu-id="80077-262">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="80077-263">Confirmar la importación, haga clic en el **importar** botón.</span><span class="sxs-lookup"><span data-stu-id="80077-263">Confirm the import by clicking the **Import** button.</span></span>

    ![](images/AzureLabs-Lab310-34.png)

3.  <span data-ttu-id="80077-264">Una vez que haya terminado de importarse, observará que ahora se han agregado las carpetas desde el paquete para su **activos** carpeta.</span><span class="sxs-lookup"><span data-stu-id="80077-264">Once it has finished importing, you will notice that folders from the package have now been added to your **Assets** folder.</span></span> <span data-ttu-id="80077-265">Este tipo de estructura de carpetas es típico de un proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="80077-265">This kind of folder structure is typical for a Unity project.</span></span>

    ![](images/AzureLabs-Lab310-35.png)

    1.  <span data-ttu-id="80077-266">El **materiales** carpeta contiene el material utilizado por la **que mirar Cursor**.</span><span class="sxs-lookup"><span data-stu-id="80077-266">The **Materials** folder contains the material used by the **Gaze Cursor**.</span></span> 

    2.  <span data-ttu-id="80077-267">El **complementos** carpeta contiene la DLL de Newtonsoft utilizado por el código para deserializar la respuesta del servicio web.</span><span class="sxs-lookup"><span data-stu-id="80077-267">The **Plugins** folder contains the Newtonsoft DLL used by the code to deserialize the Service web response.</span></span> <span data-ttu-id="80077-268">Las dos (2) diferentes versiones contenidas en la carpeta y la subcarpeta, son necesarias para permitir que la biblioteca para usarse y generados por el Editor de Unity y la compilación UWP.</span><span class="sxs-lookup"><span data-stu-id="80077-268">The two (2) different versions contained in the folder, and sub-folder, are necessary to allow the library to be used and built by both the Unity Editor and the UWP build.</span></span> 

    3.  <span data-ttu-id="80077-269">El **prefabricados** carpeta contiene el prefabricados contenidos en la escena.</span><span class="sxs-lookup"><span data-stu-id="80077-269">The **Prefabs** folder contains the prefabs contained in the scene.</span></span> <span data-ttu-id="80077-270">Esos son:</span><span class="sxs-lookup"><span data-stu-id="80077-270">Those are:</span></span>

        1.  <span data-ttu-id="80077-271">El **GazeCursor**, el cursor usado en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="80077-271">The **GazeCursor**, the cursor used in the application.</span></span> <span data-ttu-id="80077-272">Funciona junto con el recurso prefabricado de SpatialMapping que puedan colocarse en la escena encima de los objetos físicos.</span><span class="sxs-lookup"><span data-stu-id="80077-272">Will work together with the SpatialMapping prefab to be able to be placed in the scene on top of physical objects.</span></span>
        2.  <span data-ttu-id="80077-273">El **etiqueta**, que es el objeto de interfaz de usuario utilizado para mostrar la etiqueta de objeto en la escena cuando sea necesario.</span><span class="sxs-lookup"><span data-stu-id="80077-273">The **Label**, which is the UI object used to display the object tag in the scene when required.</span></span>
        3.  <span data-ttu-id="80077-274">El **SpatialMapping**, que es el objeto que permite usar la aplicación cree un mapa virtual, con seguimiento espacial de la Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="80077-274">The **SpatialMapping**, which is the object that enables the application to use create a virtual map, using the Microsoft HoloLens' spatial tracking.</span></span>

    4.  <span data-ttu-id="80077-275">El **escenas** carpeta que contiene actualmente la escena creada previamente en este curso.</span><span class="sxs-lookup"><span data-stu-id="80077-275">The **Scenes** folder which currently contains the pre-built scene for this course.</span></span>

4.  <span data-ttu-id="80077-276">Abra el **escenas** carpeta, en el **Panel proyecto**y haga doble clic en el **ObjDetectionScene**, cargar la escena que va a utilizar en este curso.</span><span class="sxs-lookup"><span data-stu-id="80077-276">Open the **Scenes** folder, in the **Project Panel**, and double-click on the **ObjDetectionScene**, to load the scene that you will use for this course.</span></span>

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  <span data-ttu-id="80077-277">**Se incluye ningún código**, escribirá el código siguiendo este curso.</span><span class="sxs-lookup"><span data-stu-id="80077-277">**No code is included**, you will write the code by following this course.</span></span>

## <a name="chapter-5---create-the-customvisionanalyser-class"></a><span data-ttu-id="80077-278">Capítulo 5: crear la clase CustomVisionAnalyser.</span><span class="sxs-lookup"><span data-stu-id="80077-278">Chapter 5 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="80077-279">En este momento está listo para escribir código.</span><span class="sxs-lookup"><span data-stu-id="80077-279">At this point you are ready to write some code.</span></span> <span data-ttu-id="80077-280">Se iniciará con la **CustomVisionAnalyser** clase.</span><span class="sxs-lookup"><span data-stu-id="80077-280">You will begin with the **CustomVisionAnalyser** class.</span></span>

> [!NOTE]
> <span data-ttu-id="80077-281">Las llamadas a la **Custom Vision Service**, realizados en el código se muestra a continuación, se realizan utilizando el **API de REST de Custom Vision**.</span><span class="sxs-lookup"><span data-stu-id="80077-281">The calls to the **Custom Vision Service**, made in the code shown below, are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="80077-282">A través del uso de esto, verá cómo implementar y hacer uso de esta API (útil para comprender cómo implementar algo similar en su propio).</span><span class="sxs-lookup"><span data-stu-id="80077-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="80077-283">Tenga en cuenta que Microsoft ofrece un **Custom Vision SDK** que también se puede utilizar para realizar llamadas al servicio.</span><span class="sxs-lookup"><span data-stu-id="80077-283">Be aware, that Microsoft offers a **Custom Vision SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="80077-284">Para obtener más información, visite la [artículo Custom Vision SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span><span class="sxs-lookup"><span data-stu-id="80077-284">For more information visit the [Custom Vision SDK article](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span></span>

<span data-ttu-id="80077-285">Esta clase es responsable de:</span><span class="sxs-lookup"><span data-stu-id="80077-285">This class is responsible for:</span></span>

- <span data-ttu-id="80077-286">Cargando la última imagen de captura como una matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="80077-286">Loading the latest image captured as an array of bytes.</span></span>

- <span data-ttu-id="80077-287">Envío de la matriz de bytes en su Azure **Custom Vision Service** instancia para el análisis.</span><span class="sxs-lookup"><span data-stu-id="80077-287">Sending the byte array to your Azure **Custom Vision Service** instance for analysis.</span></span>

- <span data-ttu-id="80077-288">Recibir la respuesta como una cadena JSON.</span><span class="sxs-lookup"><span data-stu-id="80077-288">Receiving the response as a JSON string.</span></span>

- <span data-ttu-id="80077-289">Al deserializar la respuesta y el paso resultante **predicción** a la **SceneOrganiser** (clase), que se encargará de cómo se debe mostrar la respuesta.</span><span class="sxs-lookup"><span data-stu-id="80077-289">Deserializing the response and passing the resulting **Prediction** to the **SceneOrganiser** class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="80077-290">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="80077-290">To create this class:</span></span>

1.  <span data-ttu-id="80077-291">Haga clic en el **carpeta de activos**, que se encuentra en la **Panel proyecto**, a continuación, haga clic en **crear** > **carpeta**.</span><span class="sxs-lookup"><span data-stu-id="80077-291">Right-click in the **Asset Folder**, located in the **Project Panel**, then click **Create** > **Folder**.</span></span> <span data-ttu-id="80077-292">Llame a la carpeta **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="80077-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab310-37.png)

2.  <span data-ttu-id="80077-293">Haga doble clic en la carpeta recién creada, para abrirlo.</span><span class="sxs-lookup"><span data-stu-id="80077-293">Double-click on the newly created folder, to open it.</span></span>

3.  <span data-ttu-id="80077-294">Haga clic en la carpeta, a continuación, haga clic en **crear** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="80077-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="80077-295">Nombre de la secuencia de comandos **CustomVisionAnalyser.**</span><span class="sxs-lookup"><span data-stu-id="80077-295">Name the script **CustomVisionAnalyser.**</span></span>

4.  <span data-ttu-id="80077-296">Haga doble clic en el nuevo **CustomVisionAnalyser** script para abrirlo con **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="80077-296">Double-click on the new **CustomVisionAnalyser** script to open it with **Visual Studio.**</span></span>

5.  <span data-ttu-id="80077-297">Asegúrese de que tiene los siguientes espacios de nombres al que hace referencia en la parte superior del archivo:</span><span class="sxs-lookup"><span data-stu-id="80077-297">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="80077-298">En el **CustomVisionAnalyser** de clases, agregue las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="80077-298">In the **CustomVisionAnalyser** class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Unique instance of this class
        /// </summary>
        public static CustomVisionAnalyser Instance;

        /// <summary>
        /// Insert your prediction key here
        /// </summary>
        private string predictionKey = "- Insert your key here -";

        /// <summary>
        /// Insert your prediction endpoint here
        /// </summary>
        private string predictionEndpoint = "Insert your prediction endpoint here";

        /// <summary>
        /// Bite array of the image to submit for analysis
        /// </summary>
        [HideInInspector] public byte[] imageBytes;
    ```

    > [!NOTE]
    > <span data-ttu-id="80077-299">Asegúrese de insertar el **clave de predicción de servicio** en el **predictionKey** variable y su **predicción extremo** en el **predictionEndpoint**  variable.</span><span class="sxs-lookup"><span data-stu-id="80077-299">Make sure you insert your **Service Prediction-Key** into the **predictionKey** variable and your **Prediction-Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="80077-300">Ha copiado a [el Bloc de notas anteriormente, en el capítulo 2, el paso 14](#chapter-2---training-your-custom-vision-project).</span><span class="sxs-lookup"><span data-stu-id="80077-300">You copied these to [Notepad earlier, in Chapter 2, Step 14](#chapter-2---training-your-custom-vision-project).</span></span>

7.  <span data-ttu-id="80077-301">El código para **Awake()** ahora debe agregarse para inicializar la variable de instancia:</span><span class="sxs-lookup"><span data-stu-id="80077-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }
    ```

8.  <span data-ttu-id="80077-302">Agregar la corrutina (con el método estático **GetImageAsByteArray()** método debajo de él), que obtendrá los resultados del análisis de la imagen, capturado por el **ImageCapture** clase.</span><span class="sxs-lookup"><span data-stu-id="80077-302">Add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image, captured by the **ImageCapture** class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="80077-303">En el **AnalyseImageCapture** corrutina, hay una llamada a la **SceneOrganiser** clase que aún está a crear.</span><span class="sxs-lookup"><span data-stu-id="80077-303">In the **AnalyseImageCapture** coroutine, there is a call to the **SceneOrganiser** class that you are yet to create.</span></span> <span data-ttu-id="80077-304">Por lo tanto, **las deje líneas de comentarios por ahora**.</span><span class="sxs-lookup"><span data-stu-id="80077-304">Therefore, **leave those lines commented for now**.</span></span>

    ```csharp    
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured(string imagePath)
        {
            Debug.Log("Analyzing...");

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

                Debug.Log("response: " + jsonResponse);

                // Create a texture. Texture size does not matter, since
                // LoadImage will replace with the incoming image size.
                //Texture2D tex = new Texture2D(1, 1);
                //tex.LoadImage(imageBytes);
                //SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);

                // The response will be in JSON format, therefore it needs to be deserialized
                //AnalysisRootObject analysisRootObject = new AnalysisRootObject();
                //analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);

                //SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
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

9. <span data-ttu-id="80077-305">Eliminar el **Start()** y **Update()** métodos, ya que no se usará.</span><span class="sxs-lookup"><span data-stu-id="80077-305">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span> 

10.  <span data-ttu-id="80077-306">Asegúrese de guardar los cambios en **Visual Studio**, antes de volver a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="80077-306">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="80077-307">Como se mencionó anteriormente, no se preocupe código que puede aparecer un error, ya que proporciona más clases pronto, lo que solucionará estas.</span><span class="sxs-lookup"><span data-stu-id="80077-307">As mentioned earlier, do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-6---create-the-customvisionobjects-class"></a><span data-ttu-id="80077-308">Capítulo 6: crear la clase CustomVisionObjects</span><span class="sxs-lookup"><span data-stu-id="80077-308">Chapter 6 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="80077-309">La clase que se va a crear es ahora el **CustomVisionObjects** clase.</span><span class="sxs-lookup"><span data-stu-id="80077-309">The class you will create now is the **CustomVisionObjects** class.</span></span>

<span data-ttu-id="80077-310">Este script contiene un número de objetos usados por otras clases para serializar y deserializar las llamadas realizadas a Custom Vision Service.</span><span class="sxs-lookup"><span data-stu-id="80077-310">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the Custom Vision Service.</span></span>

<span data-ttu-id="80077-311">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="80077-311">To create this class:</span></span>

1.  <span data-ttu-id="80077-312">Haga clic en el **Scripts** carpeta, a continuación, haga clic en **crear** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="80077-312">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="80077-313">Llame al script **CustomVisionObjects.**</span><span class="sxs-lookup"><span data-stu-id="80077-313">Call the script **CustomVisionObjects.**</span></span>

2.  <span data-ttu-id="80077-314">Haga doble clic en el nuevo **CustomVisionObjects** script para abrirlo con **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="80077-314">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="80077-315">Asegúrese de que tiene los siguientes espacios de nombres al que hace referencia en la parte superior del archivo:</span><span class="sxs-lookup"><span data-stu-id="80077-315">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="80077-316">Eliminar el **Start()** y **Update()** métodos dentro de la **CustomVisionObjects** (clase), esta clase ahora debe estar vacía.</span><span class="sxs-lookup"><span data-stu-id="80077-316">Delete the **Start()** and **Update()** methods inside the **CustomVisionObjects** class, this class should now be empty.</span></span>

    > [!WARNING]
    > <span data-ttu-id="80077-317">Es importante que siga cuidadosamente la siguiente instrucción.</span><span class="sxs-lookup"><span data-stu-id="80077-317">It is important you follow the next instruction carefully.</span></span> <span data-ttu-id="80077-318">Si coloca las declaraciones de clase nuevo dentro de la **CustomVisionObjects** (clase), obtendrá errores de compilación en [capítulo 10](#chapter-10---create-the-imagecapture-class), que indica que **AnalysisRootObject** y  **BoundingBox** no se encuentran.</span><span class="sxs-lookup"><span data-stu-id="80077-318">If you put the new class declarations inside the **CustomVisionObjects** class, you will get compile errors in [chapter 10](#chapter-10---create-the-imagecapture-class), stating that **AnalysisRootObject** and **BoundingBox** are not found.</span></span>

5.  <span data-ttu-id="80077-319">Agregue las siguientes clases *fuera* el **CustomVisionObjects** clase.</span><span class="sxs-lookup"><span data-stu-id="80077-319">Add the following classes *outside* the **CustomVisionObjects** class.</span></span> <span data-ttu-id="80077-320">Estos objetos se usan por el **Newtonsoft** library para serializar y deserializar los datos de respuesta:</span><span class="sxs-lookup"><span data-stu-id="80077-320">These objects are used by the **Newtonsoft** library to serialize and deserialize the response data:</span></span>

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
    /// JSON of images submitted
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
    /// Predictions received by the Service
    /// after submitting an image for analysis
    /// Includes Bounding Box
    /// </summary>
    public class AnalysisRootObject
    {
        public string id { get; set; }
        public string project { get; set; }
        public string iteration { get; set; }
        public DateTime created { get; set; }
        public List<Prediction> predictions { get; set; }
    }

    public class BoundingBox
    {
        public double left { get; set; }
        public double top { get; set; }
        public double width { get; set; }
        public double height { get; set; }
    }

    public class Prediction
    {
        public double probability { get; set; }
        public string tagId { get; set; }
        public string tagName { get; set; }
        public BoundingBox boundingBox { get; set; }
    }
    ```

6.  <span data-ttu-id="80077-321">Asegúrese de guardar los cambios en **Visual Studio**, antes de volver a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="80077-321">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-spatialmapping-class"></a><span data-ttu-id="80077-322">Capítulo 7: crear la clase SpatialMapping</span><span class="sxs-lookup"><span data-stu-id="80077-322">Chapter 7 - Create the SpatialMapping class</span></span>

<span data-ttu-id="80077-323">Esta clase se establecerá la **Colisionador asignación espacial** en la escena, por lo que para poder detectar las colisiones entre objetos virtuales y los objetos reales.</span><span class="sxs-lookup"><span data-stu-id="80077-323">This class will set the **Spatial Mapping Collider** in the scene so to be able to detect collisions between virtual objects and real objects.</span></span>

<span data-ttu-id="80077-324">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="80077-324">To create this class:</span></span>

1.  <span data-ttu-id="80077-325">Haga clic en el **Scripts** carpeta, a continuación, haga clic en **crear** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="80077-325">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="80077-326">Llame al script **SpatialMapping.**</span><span class="sxs-lookup"><span data-stu-id="80077-326">Call the script **SpatialMapping.**</span></span>

2.  <span data-ttu-id="80077-327">Haga doble clic en el nuevo **SpatialMapping** script para abrirlo con **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="80077-327">Double-click on the new **SpatialMapping** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="80077-328">Asegúrese de que tiene los siguientes espacios de nombres mencionada anteriormente el **SpatialMapping** clase:</span><span class="sxs-lookup"><span data-stu-id="80077-328">Make sure you have the following namespaces referenced above the **SpatialMapping** class:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  <span data-ttu-id="80077-329">A continuación, agregue las siguientes variables dentro de la **SpatialMapping** clase encima el **Start()** método:</span><span class="sxs-lookup"><span data-stu-id="80077-329">Then, add the following variables inside the **SpatialMapping** class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SpatialMapping Instance;

        /// <summary>
        /// Used by the GazeCursor as a property with the Raycast call
        /// </summary>
        internal static int PhysicsRaycastMask;

        /// <summary>
        /// The layer to use for spatial mapping collisions
        /// </summary>
        internal int physicsLayer = 31;

        /// <summary>
        /// Creates environment colliders to work with physics
        /// </summary>
        private SpatialMappingCollider spatialMappingCollider;
    ```

5.  <span data-ttu-id="80077-330">Agregar el **Awake()** y **Start()**:</span><span class="sxs-lookup"><span data-stu-id="80077-330">Add the **Awake()** and **Start()**:</span></span>

    ```csharp
        /// <summary>
        /// Initializes this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;
        }

        /// <summary>
        /// Runs at initialization right after Awake method
        /// </summary>
        void Start()
        {
            // Initialize and configure the collider
            spatialMappingCollider = gameObject.GetComponent<SpatialMappingCollider>();
            spatialMappingCollider.surfaceParent = this.gameObject;
            spatialMappingCollider.freezeUpdates = false;
            spatialMappingCollider.layer = physicsLayer;

            // define the mask
            PhysicsRaycastMask = 1 << physicsLayer;

            // set the object as active one
            gameObject.SetActive(true);
        }
    ```

6.  <span data-ttu-id="80077-331">Eliminar el **Update()** método.</span><span class="sxs-lookup"><span data-stu-id="80077-331">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="80077-332">Asegúrese de guardar los cambios en **Visual Studio**, antes de volver a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="80077-332">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>


## <a name="chapter-8---create-the-gazecursor-class"></a><span data-ttu-id="80077-333">Capítulo 8: crear la clase GazeCursor</span><span class="sxs-lookup"><span data-stu-id="80077-333">Chapter 8 - Create the GazeCursor class</span></span>

<span data-ttu-id="80077-334">Esta clase es responsable de configurar el cursor en la ubicación correcta en el espacio real, al hacer uso de la **SpatialMappingCollider**, creado en el capítulo anterior.</span><span class="sxs-lookup"><span data-stu-id="80077-334">This class is responsible for setting up the cursor in the correct location in real space, by making use of the **SpatialMappingCollider**, created in the previous chapter.</span></span>

<span data-ttu-id="80077-335">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="80077-335">To create this class:</span></span>

1.  <span data-ttu-id="80077-336">Haga clic en el **Scripts** carpeta, a continuación, haga clic en **crear** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="80077-336">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="80077-337">Llame al script **GazeCursor**</span><span class="sxs-lookup"><span data-stu-id="80077-337">Call the script **GazeCursor**</span></span>

2.  <span data-ttu-id="80077-338">Haga doble clic en el nuevo **GazeCursor** script para abrirlo con **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="80077-338">Double-click on the new **GazeCursor** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="80077-339">Asegúrese de que tiene el siguiente espacio de nombres mencionada anteriormente el **GazeCursor** clase:</span><span class="sxs-lookup"><span data-stu-id="80077-339">Make sure you have the following namespace referenced above the **GazeCursor** class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="80077-340">A continuación, agregue la siguiente variable dentro de la **GazeCursor** clase encima el **Start()** método.</span><span class="sxs-lookup"><span data-stu-id="80077-340">Then add the following variable inside the **GazeCursor** class, above the **Start()** method.</span></span> 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  <span data-ttu-id="80077-341">Actualización de la **Start()** método con el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="80077-341">Update the **Start()** method with the following code:</span></span>

    ```csharp
        /// <summary>
        /// Runs at initialization right after the Awake method
        /// </summary>
        void Start()
        {
            // Grab the mesh renderer that is on the same object as this script.
            meshRenderer = gameObject.GetComponent<MeshRenderer>();

            // Set the cursor reference
            SceneOrganiser.Instance.cursor = gameObject;
            gameObject.GetComponent<Renderer>().material.color = Color.green;

            // If you wish to change the size of the cursor you can do so here
            gameObject.transform.localScale = new Vector3(0.01f, 0.01f, 0.01f);
        }
    ```

6.  <span data-ttu-id="80077-342">Actualización de la **Update()** método con el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="80077-342">Update the **Update()** method with the following code:</span></span>

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            // Do a raycast into the world based on the user's head position and orientation.
            Vector3 headPosition = Camera.main.transform.position;
            Vector3 gazeDirection = Camera.main.transform.forward;

            RaycastHit gazeHitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out gazeHitInfo, 30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // If the raycast hit a hologram, display the cursor mesh.
                meshRenderer.enabled = true;
                // Move the cursor to the point where the raycast hit.
                transform.position = gazeHitInfo.point;
                // Rotate the cursor to hug the surface of the hologram.
                transform.rotation = Quaternion.FromToRotation(Vector3.up, gazeHitInfo.normal);
            }
            else
            {
                // If the raycast did not hit a hologram, hide the cursor mesh.
                meshRenderer.enabled = false;
            }
        }
    ```

    > [!NOTE]
    > <span data-ttu-id="80077-343">No se preocupe sobre el error para el **SceneOrganiser** clase no se encuentra, se creará en el próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="80077-343">Do not worry about the error for the **SceneOrganiser** class not being found, you will create it in the next chapter.</span></span>

7. <span data-ttu-id="80077-344">Asegúrese de guardar los cambios en **Visual Studio**, antes de volver a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="80077-344">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-9---create-the-sceneorganiser-class"></a><span data-ttu-id="80077-345">Capítulo 9: crear la clase SceneOrganiser</span><span class="sxs-lookup"><span data-stu-id="80077-345">Chapter 9 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="80077-346">Esta clase hará lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="80077-346">This class will:</span></span>

-   <span data-ttu-id="80077-347">Configurar la *cámara principal* adjuntando los componentes adecuados a él.</span><span class="sxs-lookup"><span data-stu-id="80077-347">Set up the *Main Camera* by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="80077-348">Cuando se detecta un objeto, será responsable de su posición en el mundo real y el lugar de calcular una **etiqueta** cerca de él con los valores adecuados **nombre de la etiqueta**.</span><span class="sxs-lookup"><span data-stu-id="80077-348">When an object is detected, it will be responsible for calculating its position in the real world and place a **Tag Label** near it with the appropriate **Tag Name**.</span></span>    

<span data-ttu-id="80077-349">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="80077-349">To create this class:</span></span>

1.  <span data-ttu-id="80077-350">Haga clic en el **Scripts** carpeta, a continuación, haga clic en **crear** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="80077-350">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="80077-351">Nombre de la secuencia de comandos **SceneOrganiser**.</span><span class="sxs-lookup"><span data-stu-id="80077-351">Name the script **SceneOrganiser**.</span></span>

2.  <span data-ttu-id="80077-352">Haga doble clic en el nuevo **SceneOrganiser** script para abrirlo con **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="80077-352">Double-click on the new **SceneOrganiser** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="80077-353">Asegúrese de que tiene los siguientes espacios de nombres mencionada anteriormente el **SceneOrganiser** clase:</span><span class="sxs-lookup"><span data-stu-id="80077-353">Make sure you have the following namespaces referenced above the **SceneOrganiser** class:</span></span>

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  <span data-ttu-id="80077-354">A continuación, agregue las siguientes variables dentro de la **SceneOrganiser** clase encima el **Start()** método:</span><span class="sxs-lookup"><span data-stu-id="80077-354">Then add the following variables inside the **SceneOrganiser** class, above the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The cursor object attached to the Main Camera
        /// </summary>
        internal GameObject cursor;

        /// <summary>
        /// The label used to display the analysis on the objects in the real world
        /// </summary>
        public GameObject label;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal Transform lastLabelPlaced;

        /// <summary>
        /// Reference to the last Label positioned
        /// </summary>
        internal TextMesh lastLabelPlacedText;

        /// <summary>
        /// Current threshold accepted for displaying the label
        /// Reduce this value to display the recognition more often
        /// </summary>
        internal float probabilityThreshold = 0.8f;

        /// <summary>
        /// The quad object hosting the imposed image captured
        /// </summary>
        private GameObject quad;

        /// <summary>
        /// Renderer of the quad object
        /// </summary>
        internal Renderer quadRenderer;
    ```

5.  <span data-ttu-id="80077-355">Eliminar el **Start()** y **Update()** métodos.</span><span class="sxs-lookup"><span data-stu-id="80077-355">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="80077-356">Debajo de las variables, agregue el **Awake()** método, que inicializará la clase y configuración de la escena.</span><span class="sxs-lookup"><span data-stu-id="80077-356">Underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization
        /// </summary>
        private void Awake()
        {
            // Use this class instance as singleton
            Instance = this;

            // Add the ImageCapture class to this Gameobject
            gameObject.AddComponent<ImageCapture>();

            // Add the CustomVisionAnalyser class to this Gameobject
            gameObject.AddComponent<CustomVisionAnalyser>();

            // Add the CustomVisionObjects class to this Gameobject
            gameObject.AddComponent<CustomVisionObjects>();
        }
    ```

7.  <span data-ttu-id="80077-357">Agregar el **PlaceAnalysisLabel()** método, que se *Instantiate* la etiqueta de la escena (que en este momento es invisible para el usuario).</span><span class="sxs-lookup"><span data-stu-id="80077-357">Add the **PlaceAnalysisLabel()** method, which will *Instantiate* the label in the scene (which at this point is invisible to the user).</span></span> <span data-ttu-id="80077-358">También coloca el cuádruple (también invisible) donde se coloca la imagen y se superpone con el mundo real.</span><span class="sxs-lookup"><span data-stu-id="80077-358">It also places the quad (also invisible) where the image is placed, and overlaps with the real world.</span></span> <span data-ttu-id="80077-359">Esto es importante porque las coordenadas del cuadro recuperados del servicio después de análisis se realizar un seguimiento en este cuádruple para determinar la ubicación aproximada del objeto en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="80077-359">This is important because the box coordinates retrieved from the Service after analysis are traced back into this quad to determined the approximate location of the object in the real world.</span></span> 

    ```csharp
        /// <summary>
        /// Instantiate a Label in the appropriate location relative to the Main Camera.
        /// </summary>
        public void PlaceAnalysisLabel()
        {
            lastLabelPlaced = Instantiate(label.transform, cursor.transform.position, transform.rotation);
            lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
            lastLabelPlacedText.text = "";
            lastLabelPlaced.transform.localScale = new Vector3(0.005f,0.005f,0.005f);

            // Create a GameObject to which the texture can be applied
            quad = GameObject.CreatePrimitive(PrimitiveType.Quad);
            quadRenderer = quad.GetComponent<Renderer>() as Renderer;
            Material m = new Material(Shader.Find("Legacy Shaders/Transparent/Diffuse"));
            quadRenderer.material = m;

            // Here you can set the transparency of the quad. Useful for debugging
            float transparency = 0f;
            quadRenderer.material.color = new Color(1, 1, 1, transparency);

            // Set the position and scale of the quad depending on user position
            quad.transform.parent = transform;
            quad.transform.rotation = transform.rotation;

            // The quad is positioned slightly forward in font of the user
            quad.transform.localPosition = new Vector3(0.0f, 0.0f, 3.0f);

            // The quad scale as been set with the following value following experimentation,  
            // to allow the image on the quad to be as precisely imposed to the real world as possible
            quad.transform.localScale = new Vector3(3f, 1.65f, 1f);
            quad.transform.parent = null;
        }
    ```

8.  <span data-ttu-id="80077-360">Agregar el **FinaliseLabel()** método.</span><span class="sxs-lookup"><span data-stu-id="80077-360">Add the **FinaliseLabel()** method.</span></span> <span data-ttu-id="80077-361">Es responsable de:</span><span class="sxs-lookup"><span data-stu-id="80077-361">It is responsible for:</span></span>

    *   <span data-ttu-id="80077-362">Establecer el *etiqueta* texto con el *etiqueta* de la predicción con la confianza más alta.</span><span class="sxs-lookup"><span data-stu-id="80077-362">Setting the *Label* text with the *Tag* of the Prediction with the highest confidence.</span></span>
    *   <span data-ttu-id="80077-363">Una llamada al cálculo de la *cuadro límite* en el objeto cuádruple, colocado anteriormente y sitúa la etiqueta de la escena.</span><span class="sxs-lookup"><span data-stu-id="80077-363">Calling the calculation of the *Bounding Box* on the quad object, positioned previously, and placing the label in the scene.</span></span>
    *   <span data-ttu-id="80077-364">Cómo ajustar la profundidad de la etiqueta mediante un Raycast hacia el *cuadro límite*, que debe entrar en conflicto con el objeto en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="80077-364">Adjusting the label depth by using a Raycast towards the *Bounding Box*, which should collide against the object in the real world.</span></span>
    * <span data-ttu-id="80077-365">Restableciendo el proceso de captura para permitir al usuario capturar la imagen de otro.</span><span class="sxs-lookup"><span data-stu-id="80077-365">Resetting the capture process to allow the user to capture another image.</span></span>

    ```csharp
        /// <summary>
        /// Set the Tags as Text of the last label created. 
        /// </summary>
        public void FinaliseLabel(AnalysisRootObject analysisObject)
        {
            if (analysisObject.predictions != null)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();
                // Sort the predictions to locate the highest one
                List<Prediction> sortedPredictions = new List<Prediction>();
                sortedPredictions = analysisObject.predictions.OrderBy(p => p.probability).ToList();
                Prediction bestPrediction = new Prediction();
                bestPrediction = sortedPredictions[sortedPredictions.Count - 1];

                if (bestPrediction.probability > probabilityThreshold)
                {
                    quadRenderer = quad.GetComponent<Renderer>() as Renderer;
                    Bounds quadBounds = quadRenderer.bounds;

                    // Position the label as close as possible to the Bounding Box of the prediction 
                    // At this point it will not consider depth
                    lastLabelPlaced.transform.parent = quad.transform;
                    lastLabelPlaced.transform.localPosition = CalculateBoundingBoxPosition(quadBounds, bestPrediction.boundingBox);

                    // Set the tag text
                    lastLabelPlacedText.text = bestPrediction.tagName;

                    // Cast a ray from the user's head to the currently placed label, it should hit the object detected by the Service.
                    // At that point it will reposition the label where the ray HL sensor collides with the object,
                    // (using the HL spatial tracking)
                    Debug.Log("Repositioning Label");
                    Vector3 headPosition = Camera.main.transform.position;
                    RaycastHit objHitInfo;
                    Vector3 objDirection = lastLabelPlaced.position;
                    if (Physics.Raycast(headPosition, objDirection, out objHitInfo, 30.0f,   SpatialMapping.PhysicsRaycastMask))
                    {
                        lastLabelPlaced.position = objHitInfo.point;
                    }
                }
            }
            // Reset the color of the cursor
            cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the analysis process
            ImageCapture.Instance.ResetImageCapture();        
        }
    ```

9.  <span data-ttu-id="80077-366">Agregar el **CalculateBoundingBoxPosition()** método, que hospeda una serie de cálculos necesarios para traducir el *cuadro límite* coordenadas recuperados del servicio y volver a crearlos proporcionalmente en lo cuatro.</span><span class="sxs-lookup"><span data-stu-id="80077-366">Add the **CalculateBoundingBoxPosition()** method, which hosts a number of calculations necessary to translate the *Bounding Box* coordinates retrieved from the Service and recreate them proportionally on the quad.</span></span>

    ```csharp
        /// <summary>
        /// This method hosts a series of calculations to determine the position 
        /// of the Bounding Box on the quad created in the real world
        /// by using the Bounding Box received back alongside the Best Prediction
        /// </summary>
        public Vector3 CalculateBoundingBoxPosition(Bounds b, BoundingBox boundingBox)
        {
            Debug.Log($"BB: left {boundingBox.left}, top {boundingBox.top}, width {boundingBox.width}, height {boundingBox.height}");

            double centerFromLeft = boundingBox.left + (boundingBox.width / 2);
            double centerFromTop = boundingBox.top + (boundingBox.height / 2);
            Debug.Log($"BB CenterFromLeft {centerFromLeft}, CenterFromTop {centerFromTop}");

            double quadWidth = b.size.normalized.x;
            double quadHeight = b.size.normalized.y;
            Debug.Log($"Quad Width {b.size.normalized.x}, Quad Height {b.size.normalized.y}");

            double normalisedPos_X = (quadWidth * centerFromLeft) - (quadWidth/2);
            double normalisedPos_Y = (quadHeight * centerFromTop) - (quadHeight/2);

            return new Vector3((float)normalisedPos_X, (float)normalisedPos_Y, 0);
        }
    ```

10. <span data-ttu-id="80077-367">Asegúrese de guardar los cambios en **Visual Studio**, antes de volver a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="80077-367">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="80077-368">Antes de continuar, abra el **CustomVisionAnalyser** (clase) y dentro del **AnalyseLastImageCaptured()** método, *quite* las líneas siguientes:</span><span class="sxs-lookup"><span data-stu-id="80077-368">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
    >
    >   ```csharp
    >   // Create a texture. Texture size does not matter, since 
    >   // LoadImage will replace with the incoming image size.
    >   Texture2D tex = new Texture2D(1, 1);
    >   tex.LoadImage(imageBytes);
    >   SceneOrganiser.Instance.quadRenderer.material.SetTexture("_MainTex", tex);
    >
    >   // The response will be in JSON format, therefore it needs to be deserialized
    >   AnalysisRootObject analysisRootObject = new AnalysisRootObject();
    >   analysisRootObject = JsonConvert.DeserializeObject<AnalysisRootObject>(jsonResponse);
    >
    >   SceneOrganiser.Instance.FinaliseLabel(analysisRootObject);
    >   ```

> [!NOTE]
> <span data-ttu-id="80077-369">No se preocupe la **ImageCapture** class 'no se pudo encontrar' mensaje, se creará en el próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="80077-369">Do not worry about the **ImageCapture** class 'could not be found' message, you will create it in the next chapter.</span></span>


## <a name="chapter-10---create-the-imagecapture-class"></a><span data-ttu-id="80077-370">Capítulo 10: crear la clase ImageCapture</span><span class="sxs-lookup"><span data-stu-id="80077-370">Chapter 10 - Create the ImageCapture class</span></span>

<span data-ttu-id="80077-371">La siguiente clase que se va a crear es la **ImageCapture** clase.</span><span class="sxs-lookup"><span data-stu-id="80077-371">The next class you are going to create is the **ImageCapture** class.</span></span>

<span data-ttu-id="80077-372">Esta clase es responsable de:</span><span class="sxs-lookup"><span data-stu-id="80077-372">This class is responsible for:</span></span>

*   <span data-ttu-id="80077-373">Capturar una imagen con la cámara de HoloLens y almacenarla en la *aplicación* carpeta.</span><span class="sxs-lookup"><span data-stu-id="80077-373">Capturing an image using the HoloLens camera and storing it in the *App* folder.</span></span>
*   <span data-ttu-id="80077-374">Control *pulse* gestos del usuario.</span><span class="sxs-lookup"><span data-stu-id="80077-374">Handling *Tap* gestures from the user.</span></span>

<span data-ttu-id="80077-375">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="80077-375">To create this class:</span></span>

1.  <span data-ttu-id="80077-376">Vaya a la **Scripts** carpeta que creó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="80077-376">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="80077-377">Haga clic en la carpeta, a continuación, haga clic en **crear** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="80077-377">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="80077-378">Nombre de la secuencia de comandos **ImageCapture**.</span><span class="sxs-lookup"><span data-stu-id="80077-378">Name the script **ImageCapture**.</span></span>

3.  <span data-ttu-id="80077-379">Haga doble clic en el nuevo **ImageCapture** script para abrirlo con **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="80077-379">Double-click on the new **ImageCapture** script to open it with **Visual Studio.**</span></span>

4.  <span data-ttu-id="80077-380">Reemplace los espacios de nombres en la parte superior del archivo por lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="80077-380">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="80077-381">A continuación, agregue las siguientes variables dentro de la **ImageCapture** clase encima el **Start()** método:</span><span class="sxs-lookup"><span data-stu-id="80077-381">Then add the following variables inside the **ImageCapture** class, above the **Start()** method:</span></span>

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
        /// Flagging if the capture loop is running
        /// </summary>
        internal bool captureIsActive;
        
        /// <summary>
        /// File path of current analysed photo
        /// </summary>
        internal string filePath = string.Empty;
    ```

6.  <span data-ttu-id="80077-382">El código para **Awake()** y **Start()** métodos ahora debe agregar:</span><span class="sxs-lookup"><span data-stu-id="80077-382">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

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

            // Subscribing to the Microsoft HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="80077-383">Implementar un controlador que se llamará cuando se produce un gesto de pulsar:</span><span class="sxs-lookup"><span data-stu-id="80077-383">Implement a handler that will be called when a Tap gesture occurs:</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            if (!captureIsActive)
            {
                captureIsActive = true;

                // Set the cursor color to red
                SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.red;

                // Begin the capture loop
                Invoke("ExecuteImageCaptureAndAnalysis", 0);
            }
        }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="80077-384">Cuando el cursor está **verde**, significa que la cámara está disponible para tomar la imagen.</span><span class="sxs-lookup"><span data-stu-id="80077-384">When the cursor is **green**, it means the camera is available to take the image.</span></span> <span data-ttu-id="80077-385">Cuando el cursor está **rojo**, lo que significa que la cámara está ocupada.</span><span class="sxs-lookup"><span data-stu-id="80077-385">When the cursor is **red**, it means the camera is busy.</span></span>

8.  <span data-ttu-id="80077-386">Agregue el método que utiliza la aplicación para iniciar el proceso de captura de imagen y almacenar la imagen:</span><span class="sxs-lookup"><span data-stu-id="80077-386">Add the method that the application uses to start the image capture process and store the image:</span></span>

    ```csharp
        /// <summary>
        /// Begin process of image capturing and send to Azure Custom Vision Service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            // Create a label in world space using the ResultsLabel class 
            // Invisible at this point but correctly positioned where the image was taken
            SceneOrganiser.Instance.PlaceAnalysisLabel();

            // Set the camera resolution to be the highest possible
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            // Begin capture process, set the image format
            PhotoCapture.CreateAsync(true, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters camParameters = new CameraParameters
                {
                    hologramOpacity = 1.0f,
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

9.  <span data-ttu-id="80077-387">Agregue los controladores que se llamará cuando se ha capturado la foto y para cuando esté listo para ser analizados.</span><span class="sxs-lookup"><span data-stu-id="80077-387">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="80077-388">El resultado se pasa a la **CustomVisionAnalyser** para el análisis.</span><span class="sxs-lookup"><span data-stu-id="80077-388">The result is then passed to the **CustomVisionAnalyser** for analysis.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. 
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            try
            {
                // Call StopPhotoMode once the image has successfully captured
                photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
            }
            catch (Exception e)
            {
                Debug.LogFormat("Exception capturing photo to disk: {0}", e.Message);
            }
        }

        /// <summary>
        /// The camera photo mode has stopped after the capture.
        /// Begin the image analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            Debug.LogFormat("Stopped Photo Mode");
        
            // Dispose from the object in memory and request the image analysis 
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Call the image analysis
            StartCoroutine(CustomVisionAnalyser.Instance.AnalyseLastImageCaptured(filePath)); 
        }

        /// <summary>
        /// Stops all capture pending actions
        /// </summary>
        internal void ResetImageCapture()
        {
            captureIsActive = false;

            // Set the cursor color to green
            SceneOrganiser.Instance.cursor.GetComponent<Renderer>().material.color = Color.green;

            // Stop the capture loop if active
            CancelInvoke();
        }
    ```

10. <span data-ttu-id="80077-389">Asegúrese de guardar los cambios en **Visual Studio**, antes de volver a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="80077-389">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a><span data-ttu-id="80077-390">Capítulo 11: configuración de las secuencias de comandos de la escena</span><span class="sxs-lookup"><span data-stu-id="80077-390">Chapter 11 - Setting up the scripts in the scene</span></span>

<span data-ttu-id="80077-391">Ahora que hemos escrito todo el código necesario para este proyecto, es momento de configurar las secuencias de comandos de la escena y en prefabricados, para que se comporten correctamente.</span><span class="sxs-lookup"><span data-stu-id="80077-391">Now that you have written all of the code necessary for this project, is time to set up the scripts in the scene, and on the prefabs, for them to behave correctly.</span></span>

1.  <span data-ttu-id="80077-392">Dentro de la **Editor de Unity**, en el **jerarquía Panel**, seleccione el **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="80077-392">Within the **Unity Editor**, in the **Hierarchy Panel**, select the **Main Camera**.</span></span>
2.  <span data-ttu-id="80077-393">En el **Panel Inspector**, con el **cámara principal** seleccionado, haga clic en **Agregar componente**, a continuación, busque **SceneOrganiser** secuencia de comandos y Haga doble clic para agregarlo.</span><span class="sxs-lookup"><span data-stu-id="80077-393">In the **Inspector Panel**, with the **Main Camera** selected, click on **Add Component**, then search for **SceneOrganiser** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-38.png)

3.  <span data-ttu-id="80077-394">En el **Panel proyecto**, abra el **carpeta prefabricados**, arrastre el **etiqueta** prefabricado en el *etiqueta* área, de entrada de destino de la referencia vacía en el **SceneOrganiser** secuencia de comandos que acaba de agregar a la *cámara principal*, tal y como se muestra en la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="80077-394">In the **Project Panel**, open the **Prefabs folder**, drag the **Label** prefab into the *Label* empty reference target input area, in the **SceneOrganiser** script that you have just added to the *Main Camera*, as shown in the image below:</span></span>

    ![](images/AzureLabs-Lab310-39.png)

4.  <span data-ttu-id="80077-395">En el **jerarquía Panel**, seleccione el **GazeCursor** secundarios de la **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="80077-395">In the **Hierarchy Panel**, select the **GazeCursor** child of the **Main Camera**.</span></span>
5.  <span data-ttu-id="80077-396">En el **Panel Inspector**, con el **GazeCursor** seleccionado, haga clic en **Agregar componente**, a continuación, busque **GazeCursor** secuencia de comandos y Haga doble clic para agregarlo.</span><span class="sxs-lookup"><span data-stu-id="80077-396">In the **Inspector Panel**, with the **GazeCursor** selected, click on **Add Component**, then search for **GazeCursor** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-40.png)

6.  <span data-ttu-id="80077-397">De nuevo, en el **jerarquía Panel**, seleccione el **SpatialMapping** secundarios de la **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="80077-397">Again, in the **Hierarchy Panel**, select the **SpatialMapping** child of the **Main Camera**.</span></span>
7.  <span data-ttu-id="80077-398">En el **Panel Inspector**, con el **SpatialMapping** seleccionado, haga clic en **Agregar componente**, a continuación, busque **SpatialMapping** secuencia de comandos y haga doble clic para agregarlo.</span><span class="sxs-lookup"><span data-stu-id="80077-398">In the **Inspector Panel**, with the **SpatialMapping** selected, click on **Add Component**, then search for **SpatialMapping** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-41.png)

<span data-ttu-id="80077-399">Las secuencias de comandos restantes de la no tienen conjunto se agregará el código de la **SceneOrganiser** script en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="80077-399">The remaining scripts thats you have not set will be added by the code in the **SceneOrganiser** script, during runtime.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="80077-400">Capítulo 12 - antes de compilar</span><span class="sxs-lookup"><span data-stu-id="80077-400">Chapter 12 - Before building</span></span>

<span data-ttu-id="80077-401">Para llevar a cabo una prueba completa de la aplicación se necesitará para transferir localmente en su Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="80077-401">To perform a thorough test of your application you will need to sideload it onto your Microsoft HoloLens.</span></span>

<span data-ttu-id="80077-402">Antes de hacerlo, asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="80077-402">Before you do, ensure that:</span></span>

-  <span data-ttu-id="80077-403">Todas las configuraciones que se mencionan en la [capítulo 3](#chapter-3---set-up-the-unity-project) están establecidas correctamente.</span><span class="sxs-lookup"><span data-stu-id="80077-403">All the settings mentioned in the [Chapter 3](#chapter-3---set-up-the-unity-project) are set correctly.</span></span>
- <span data-ttu-id="80077-404">La secuencia de comandos **SceneOrganiser** está asociado a la **cámara principal** objeto.</span><span class="sxs-lookup"><span data-stu-id="80077-404">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>
- <span data-ttu-id="80077-405">La secuencia de comandos **GazeCursor** está asociado a la **GazeCursor** objeto.</span><span class="sxs-lookup"><span data-stu-id="80077-405">The script **GazeCursor** is attached to the **GazeCursor** object.</span></span>
- <span data-ttu-id="80077-406">La secuencia de comandos **SpatialMapping** está asociado a la **SpatialMapping** objeto.</span><span class="sxs-lookup"><span data-stu-id="80077-406">The script **SpatialMapping** is attached to the **SpatialMapping** object.</span></span>
- <span data-ttu-id="80077-407">En [capítulo 5](#chapter-5---create-the-customvisionanalyser-class), paso 6:</span><span class="sxs-lookup"><span data-stu-id="80077-407">In [Chapter 5](#chapter-5---create-the-customvisionanalyser-class), Step 6:</span></span>

    - <span data-ttu-id="80077-408">Asegúrese de insertar el **clave del servicio de predicción** en el **predictionKey** variable.</span><span class="sxs-lookup"><span data-stu-id="80077-408">Make sure you insert your **Service Prediction Key** into the **predictionKey** variable.</span></span>
    - <span data-ttu-id="80077-409">Ha insertado el **punto de conexión de predicción** en el **predictionEndpoint** clase.</span><span class="sxs-lookup"><span data-stu-id="80077-409">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** class.</span></span>

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a><span data-ttu-id="80077-410">Capítulo 13 - compilar la solución UWP y transferir localmente la aplicación</span><span class="sxs-lookup"><span data-stu-id="80077-410">Chapter 13 - Build the UWP solution and sideload your application</span></span>

<span data-ttu-id="80077-411">Ahora está listo para compilar la aplicación como una solución de UWP que podrá implementar en el Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="80077-411">You are now ready to build you application as a UWP Solution that you will be able to deploy on to the Microsoft HoloLens.</span></span> <span data-ttu-id="80077-412">Para comenzar el proceso de compilación:</span><span class="sxs-lookup"><span data-stu-id="80077-412">To begin the build process:</span></span>

1.  <span data-ttu-id="80077-413">Vaya a **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="80077-413">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="80077-414">Graduación **Unity C\# proyectos**.</span><span class="sxs-lookup"><span data-stu-id="80077-414">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="80077-415">Haga clic en **agregar escenas abiertos**.</span><span class="sxs-lookup"><span data-stu-id="80077-415">Click on **Add Open Scenes**.</span></span> <span data-ttu-id="80077-416">Esto agregará la escena abierta actualmente a la compilación.</span><span class="sxs-lookup"><span data-stu-id="80077-416">This will add the currently open scene to the build.</span></span>

    ![](images/AzureLabs-Lab310-42.png)

4.  <span data-ttu-id="80077-417">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="80077-417">Click **Build**.</span></span> <span data-ttu-id="80077-418">Unity se iniciará un *Explorador de archivos* ventana, donde se debe crear y, a continuación, seleccione una carpeta para compilar la aplicación en.</span><span class="sxs-lookup"><span data-stu-id="80077-418">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="80077-419">Crear la carpeta y asígnele el nombre **aplicación**.</span><span class="sxs-lookup"><span data-stu-id="80077-419">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="80077-420">A continuación, con el **aplicación** carpeta seleccionada, haga clic en **seleccionar la carpeta**.</span><span class="sxs-lookup"><span data-stu-id="80077-420">Then with the **App** folder selected, click **Select Folder**.</span></span>

5.  <span data-ttu-id="80077-421">Unity empezará a compilar el proyecto para el **aplicación** carpeta.</span><span class="sxs-lookup"><span data-stu-id="80077-421">Unity will begin building your project to the **App** folder.</span></span>

6.  <span data-ttu-id="80077-422">Una vez Unity ha finalizado la compilación (puede tardar algún tiempo), se abrirá un **Explorador de archivos** ventana en la ubicación de la compilación (comprobación de la barra de tareas, tal y como es posible que no siempre aparecen por encima de las ventanas, pero le informará de la adición de un nuevo ventana).</span><span class="sxs-lookup"><span data-stu-id="80077-422">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

7.  <span data-ttu-id="80077-423">Para implementar la sesión en Microsoft HoloLens, necesitará la dirección IP del dispositivo (para la implementación remota), y para asegurarse de que también tiene **modo de programador** establecido.</span><span class="sxs-lookup"><span data-stu-id="80077-423">To deploy on to Microsoft HoloLens, you will need the IP Address of that device (for Remote Deploy), and to ensure that it also has **Developer Mode** set.</span></span> <span data-ttu-id="80077-424">Para ello:</span><span class="sxs-lookup"><span data-stu-id="80077-424">To do this:</span></span>

    1.  <span data-ttu-id="80077-425">Mientras que el exceso de su HoloLens, abra el **configuración**.</span><span class="sxs-lookup"><span data-stu-id="80077-425">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="80077-426">Vaya a **red e Internet** > **Wi-Fi** > **opciones avanzadas**</span><span class="sxs-lookup"><span data-stu-id="80077-426">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="80077-427">Tenga en cuenta la **IPv4** dirección.</span><span class="sxs-lookup"><span data-stu-id="80077-427">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="80077-428">A continuación, vaya a **configuración**y, a continuación, en **actualización y seguridad** > **para desarrolladores**</span><span class="sxs-lookup"><span data-stu-id="80077-428">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="80077-429">Establecer **modo de programador** *en*.</span><span class="sxs-lookup"><span data-stu-id="80077-429">Set **Developer Mode** *On*.</span></span>

8.  <span data-ttu-id="80077-430">Vaya a la nueva compilación de Unity (la **aplicación** carpeta) y abra el archivo de solución con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="80077-430">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

9.  <span data-ttu-id="80077-431">En, seleccione la configuración de la solución **depurar**.</span><span class="sxs-lookup"><span data-stu-id="80077-431">In the Solution Configuration select **Debug**.</span></span>

10. <span data-ttu-id="80077-432">En la plataforma de soluciones, seleccione **x86, máquina remota**.</span><span class="sxs-lookup"><span data-stu-id="80077-432">In the Solution Platform, select **x86, Remote Machine**.</span></span> <span data-ttu-id="80077-433">Se le pedirá que inserte la **dirección IP** de un dispositivo remoto (el Microsoft HoloLens, en este caso, lo cual observó).</span><span class="sxs-lookup"><span data-stu-id="80077-433">You will be prompted to insert the **IP address** of a remote device (the Microsoft HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab310-43.png)

11. <span data-ttu-id="80077-434">Vaya a la **compilar** menú y haga clic en **implementar solución** para transferir localmente la aplicación a su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="80077-434">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

12. <span data-ttu-id="80077-435">La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas en el Microsoft HoloLens, lista para iniciarse.</span><span class="sxs-lookup"><span data-stu-id="80077-435">Your app should now appear in the list of installed apps on your Microsoft HoloLens, ready to be launched!</span></span>

### <a name="to-use-the-application"></a><span data-ttu-id="80077-436">Para usar la aplicación:</span><span class="sxs-lookup"><span data-stu-id="80077-436">To use the application:</span></span>

* <span data-ttu-id="80077-437">Examine un objeto que se ha entrenado con su **Azure Custom Vision Service, detección de objetos**y usar el **gesto**.</span><span class="sxs-lookup"><span data-stu-id="80077-437">Look at an object, which you have trained with your **Azure Custom Vision Service, Object Detection**, and use the **Tap gesture**.</span></span>
* <span data-ttu-id="80077-438">Si el objeto se detecte correctamente, un espacio global *texto de la etiqueta* aparecerá con el nombre de etiqueta.</span><span class="sxs-lookup"><span data-stu-id="80077-438">If the object is successfully detected, a world-space *Label Text* will appear with the tag name.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="80077-439">Cada vez que se captura una foto y enviarlo al servicio, puede volver a la página de servicio y reciclar el servicio con las imágenes de recién capturados.</span><span class="sxs-lookup"><span data-stu-id="80077-439">Every time you capture a photo and send it to the Service, you can go back to the Service page and retrain the Service with the newly captured images.</span></span> <span data-ttu-id="80077-440">Al principio, probablemente también tenga que corregir la *cuadros de límite* para ser más preciso y reciclar el servicio.</span><span class="sxs-lookup"><span data-stu-id="80077-440">At the beginning, you will probably also have to correct the *Bounding Boxes* to be more accurate and retrain the Service.</span></span>

> [!NOTE]
> <span data-ttu-id="80077-441">Coloca el texto de la etiqueta podría no aparecer cerca del objeto cuando los sensores de Microsoft HoloLens o la SpatialTrackingComponent en Unity no se puede colocar el colisionadores adecuados, en relación con los objetos del mundo real.</span><span class="sxs-lookup"><span data-stu-id="80077-441">The Label Text placed might not appear near the object when the Microsoft HoloLens sensors and/or the SpatialTrackingComponent in Unity fails to place the appropriate colliders, relative to the real world objects.</span></span> <span data-ttu-id="80077-442">Pruebe a usar la aplicación en una superficie diferente si ese es el caso.</span><span class="sxs-lookup"><span data-stu-id="80077-442">Try to use the application on a different surface if that is the case.</span></span>

## <a name="your-custom-vision-object-detection-application"></a><span data-ttu-id="80077-443">Tu visión personalizada, aplicación de detección de objetos</span><span class="sxs-lookup"><span data-stu-id="80077-443">Your Custom Vision, Object Detection application</span></span>

<span data-ttu-id="80077-444">Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha Azure Custom Vision, API de detección de objeto, que puede reconocer un objeto desde una imagen y, a continuación, proporcione una ubicación aproximada para ese objeto en el espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="80077-444">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision, Object Detection API, which can recognize an object from an image, and then provide an approximate position for that object in 3D space.</span></span>

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="80077-445">Ejercicios de bonificación</span><span class="sxs-lookup"><span data-stu-id="80077-445">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="80077-446">Ejercicio 1</span><span class="sxs-lookup"><span data-stu-id="80077-446">Exercise 1</span></span>

<span data-ttu-id="80077-447">Agregar a la etiqueta de texto, utilice un cubo semitransparente para encapsular el objeto real en 3D *cuadro límite*.</span><span class="sxs-lookup"><span data-stu-id="80077-447">Adding to the Text Label, use a semi-transparent cube to wrap the real object in a 3D *Bounding Box*.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="80077-448">Ejercicio 2</span><span class="sxs-lookup"><span data-stu-id="80077-448">Exercise 2</span></span>

<span data-ttu-id="80077-449">Entrenar su Custom Vision Service para reconocer más objetos.</span><span class="sxs-lookup"><span data-stu-id="80077-449">Train your Custom Vision Service to recognize more objects.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="80077-450">Ejercicio 3</span><span class="sxs-lookup"><span data-stu-id="80077-450">Exercise 3</span></span>

<span data-ttu-id="80077-451">Reproducir un sonido cuando se reconoce un objeto.</span><span class="sxs-lookup"><span data-stu-id="80077-451">Play a sound when an object is recognized.</span></span>

### <a name="exercise-4"></a><span data-ttu-id="80077-452">Ejercicio 4</span><span class="sxs-lookup"><span data-stu-id="80077-452">Exercise 4</span></span>

<span data-ttu-id="80077-453">Usar la API para volver a entrenar el servicio con las mismas imágenes que se está analizando la aplicación, por lo tanto, para que el servicio más precisos (realizar tareas de predicción y aprendizaje de forma simultánea).</span><span class="sxs-lookup"><span data-stu-id="80077-453">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
