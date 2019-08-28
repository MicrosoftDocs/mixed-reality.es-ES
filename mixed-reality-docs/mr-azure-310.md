---
title: 'MR y Azure 310: detección de objetos'
description: Complete este curso para aprender a entrenar un modelo de aprendizaje automático y, a continuación, use el modelo entrenado para reconocer objetos similares y su posición en el mundo real desde una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, visión personalizada, detección de objetos, realidad mixta, Academia, Unity, tutorial, API, hololens
ms.openlocfilehash: 71370db84a9b90b017e8d5fac0799a862883d046
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047226"
---
>[!NOTE]
><span data-ttu-id="7b246-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="7b246-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="7b246-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="7b246-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="7b246-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7b246-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="7b246-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="7b246-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="7b246-108">Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="7b246-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="7b246-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.</span><span class="sxs-lookup"><span data-stu-id="7b246-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-310-object-detection"></a><span data-ttu-id="7b246-110">Mr y Azure 310: Detección de objetos</span><span class="sxs-lookup"><span data-stu-id="7b246-110">Mr and Azure 310: Object detection</span></span>

<span data-ttu-id="7b246-111">En este curso, aprenderá a reconocer el contenido visual personalizado y su posición espacial dentro de una imagen proporcionada, mediante las funcionalidades de Azure Custom Vision "detección de objetos" en una aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="7b246-111">In this course, you will learn how to recognize custom visual content and its spatial position within a provided image, using Azure Custom Vision "Object Detection" capabilities in a mixed reality application.</span></span>

<span data-ttu-id="7b246-112">Este servicio le permitirá entrenar un modelo de aprendizaje automático mediante imágenes de objeto.</span><span class="sxs-lookup"><span data-stu-id="7b246-112">This service will allow you to train a machine learning model using object images.</span></span> <span data-ttu-id="7b246-113">A continuación, usará el modelo entrenado para reconocer objetos similares y aproximar su ubicación en el mundo real, tal como lo proporciona la captura de cámara de Microsoft HoloLens o una cámara conectarse a un equipo para recibir auriculares envolventes (VR).</span><span class="sxs-lookup"><span data-stu-id="7b246-113">You will then use the trained model to recognize similar objects and approximate their location in the real world, as provided by the camera capture of Microsoft HoloLens or a camera connect to a PC for immersive (VR) headsets.</span></span>

![resultado del curso](images/AzureLabs-Lab310-00.png)

<span data-ttu-id="7b246-115">**Azure Custom Vision, la detección de objetos** es un servicio de Microsoft que permite a los desarrolladores crear clasificadores de imágenes personalizados.</span><span class="sxs-lookup"><span data-stu-id="7b246-115">**Azure Custom Vision, Object Detection** is a Microsoft Service which allows developers to build custom image classifiers.</span></span> <span data-ttu-id="7b246-116">Estos clasificadores se pueden usar con nuevas imágenes para detectar objetos dentro de esa nueva imagen, proporcionando **límites de cuadro** dentro de la propia imagen.</span><span class="sxs-lookup"><span data-stu-id="7b246-116">These classifiers can then be used with new images to detect objects within that new image, by providing **Box Boundaries** within the image itself.</span></span> <span data-ttu-id="7b246-117">El servicio proporciona un portal en línea sencillo y fácil de usar para simplificar este proceso.</span><span class="sxs-lookup"><span data-stu-id="7b246-117">The Service provides a simple, easy to use, online portal to streamline this process.</span></span> <span data-ttu-id="7b246-118">Para obtener más información, visite los vínculos siguientes:</span><span class="sxs-lookup"><span data-stu-id="7b246-118">For more information, visit the following links:</span></span>

* [<span data-ttu-id="7b246-119">Página de Custom Vision de Azure</span><span class="sxs-lookup"><span data-stu-id="7b246-119">Azure Custom Vision page</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home)
* [<span data-ttu-id="7b246-120">Límites y cuotas</span><span class="sxs-lookup"><span data-stu-id="7b246-120">Limits and Quotas</span></span>](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/limits-and-quotas)

<span data-ttu-id="7b246-121">Al finalizar este curso, tendrá una aplicación de realidad mixta que podrá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="7b246-121">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1. <span data-ttu-id="7b246-122">El usuario podrá hacer una *mirada* a un objeto, que ha entrenado con la Custom Vision Service de Azure, la detección de objetos.</span><span class="sxs-lookup"><span data-stu-id="7b246-122">The user will be able to *gaze* at an object, which they have trained using the Azure Custom Vision Service, Object Detection.</span></span> 
2. <span data-ttu-id="7b246-123">El usuario usará el gesto de puntear para capturar una imagen de lo que están examinando.</span><span class="sxs-lookup"><span data-stu-id="7b246-123">The user will use the *Tap* gesture to capture an image of what they are looking at.</span></span>
3. <span data-ttu-id="7b246-124">La aplicación enviará la imagen a Azure Custom Vision Service.</span><span class="sxs-lookup"><span data-stu-id="7b246-124">The app will send the image to the Azure Custom Vision Service.</span></span>
4. <span data-ttu-id="7b246-125">Habrá una respuesta del servicio que mostrará el resultado del reconocimiento como texto de espacio universal.</span><span class="sxs-lookup"><span data-stu-id="7b246-125">There will be a reply from the Service which will display the result of the recognition as world-space text.</span></span> <span data-ttu-id="7b246-126">Esto se consigue mediante el seguimiento espacial de Microsoft HoloLens, como una forma de entender la posición mundial del objeto reconocido y, a continuación, usando la *etiqueta* asociada a lo que se detecta en la imagen para proporcionar el texto de la etiqueta.</span><span class="sxs-lookup"><span data-stu-id="7b246-126">This will be accomplished through utilizing the Microsoft HoloLens' Spatial Tracking, as a way of understanding the world position of the recognized object, and then using the *Tag* associated with what is detected in the image, to provide the label text.</span></span>

<span data-ttu-id="7b246-127">El curso también cubrirá la carga manual de imágenes, la creación de etiquetas y el entrenamiento del servicio, para reconocer objetos diferentes (en el ejemplo proporcionado, una copa), estableciendo el *cuadro de límite* dentro de la imagen que envía.</span><span class="sxs-lookup"><span data-stu-id="7b246-127">The course will also cover manually uploading images, creating tags, and training the Service, to recognize different objects (in the provided example, a cup), by setting the *Boundary Box* within the image you submit.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="7b246-128">Después de la creación y el uso de la aplicación, el desarrollador debe volver a la Custom Vision Service de Azure e identificar las predicciones realizadas por el servicio y determinar si son correctas o no (mediante el etiquetado de todo el servicio que faltaba y ajustar los *rectángulos*de selección).</span><span class="sxs-lookup"><span data-stu-id="7b246-128">Following the creation and use of the app, the developer should navigate back to the Azure Custom Vision Service, and identify the predictions made by the Service, and determine whether they were correct or not (through tagging anything the Service missed, and adjusting the *Bounding Boxes*).</span></span> <span data-ttu-id="7b246-129">Después, se puede volver a entrenar el servicio, lo que aumentará la probabilidad de que reconozca objetos del mundo real.</span><span class="sxs-lookup"><span data-stu-id="7b246-129">The Service can then be re-trained, which will increase the likelihood of it recognizing real world objects.</span></span>

<span data-ttu-id="7b246-130">Este curso le enseñará cómo obtener los resultados de la Custom Vision Service de Azure, la detección de objetos, en una aplicación de ejemplo basada en Unity.</span><span class="sxs-lookup"><span data-stu-id="7b246-130">This course will teach you how to get the results from the Azure Custom Vision Service, Object Detection, into a Unity-based sample application.</span></span> <span data-ttu-id="7b246-131">Depende de usted que aplique estos conceptos a una aplicación personalizada que pueda estar compilando.</span><span class="sxs-lookup"><span data-stu-id="7b246-131">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="7b246-132">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="7b246-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="7b246-133">Recurso</span><span class="sxs-lookup"><span data-stu-id="7b246-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="7b246-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="7b246-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="7b246-135"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="7b246-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="7b246-136">MR y Azure 310: Detección de objetos</span><span class="sxs-lookup"><span data-stu-id="7b246-136">MR and Azure 310: Object detection</span></span></td><td style="text-align: center;"> <span data-ttu-id="7b246-137">✔️</span><span class="sxs-lookup"><span data-stu-id="7b246-137">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="7b246-138">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="7b246-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="7b246-139">Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#.</span><span class="sxs-lookup"><span data-stu-id="7b246-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="7b246-140">Tenga en cuenta también que los requisitos previos y las instrucciones escritas dentro de este documento representan lo que se ha probado y comprobado en el momento de la escritura (2018 de julio).</span><span class="sxs-lookup"><span data-stu-id="7b246-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="7b246-141">Puede usar el software más reciente, como se indica en el artículo [instalar las herramientas](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) , aunque no se debe suponer que la información de este curso se ajusta perfectamente a lo que encontrará en el software más reciente que el que se enumera a continuación.</span><span class="sxs-lookup"><span data-stu-id="7b246-141">You are free to use the latest software, as listed within the [install the tools](https://docs.microsoft.com/windows/mixed-reality/install-the-tools) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="7b246-142">Se recomienda el siguiente hardware y software para este curso:</span><span class="sxs-lookup"><span data-stu-id="7b246-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="7b246-143">Un equipo de desarrollo</span><span class="sxs-lookup"><span data-stu-id="7b246-143">A development PC</span></span>
- [<span data-ttu-id="7b246-144">Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="7b246-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="7b246-145">El SDK de Windows 10 más reciente</span><span class="sxs-lookup"><span data-stu-id="7b246-145">The latest Windows 10 SDK</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="7b246-146">Unity 2017,4 LTS</span><span class="sxs-lookup"><span data-stu-id="7b246-146">Unity 2017.4 LTS</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- [<span data-ttu-id="7b246-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="7b246-147">Visual Studio 2017</span></span>](https://docs.microsoft.com/windows/mixed-reality/install-the-tools#installation-checklist-for-hololens)
- <span data-ttu-id="7b246-148">Un [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="7b246-148">A [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details) with Developer mode enabled</span></span>
- <span data-ttu-id="7b246-149">Acceso a Internet para la configuración y recuperación de Custom Vision Service de Azure</span><span class="sxs-lookup"><span data-stu-id="7b246-149">Internet access for Azure setup and Custom Vision Service retrieval</span></span>
-  <span data-ttu-id="7b246-150">Se requiere una serie de al menos quince (15) imágenes) para cada objeto que desea que reconozca el Custom Vision.</span><span class="sxs-lookup"><span data-stu-id="7b246-150">A series of at least fifteen (15) images are required) for each object that you would like the Custom Vision to recognize.</span></span> <span data-ttu-id="7b246-151">Si lo desea, puede usar las imágenes que ya se proporcionan con este curso, [una serie de tazas](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span><span class="sxs-lookup"><span data-stu-id="7b246-151">If you wish, you can use the images already provided with this course, [a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

## <a name="before-you-start"></a><span data-ttu-id="7b246-152">Antes de comenzar</span><span class="sxs-lookup"><span data-stu-id="7b246-152">Before you start</span></span>

1.  <span data-ttu-id="7b246-153">Para evitar que se produzcan problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cerca de la raíz (las rutas de acceso de carpeta largas pueden producir problemas en tiempo de compilación).</span><span class="sxs-lookup"><span data-stu-id="7b246-153">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="7b246-154">Configure y pruebe su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7b246-154">Set up and test your HoloLens.</span></span> <span data-ttu-id="7b246-155">Si necesita ayuda para configurar HoloLens, asegúrese [de visitar el artículo de configuración de hololens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="7b246-155">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="7b246-156">Es una buena idea realizar la calibración y el ajuste del sensor al empezar a desarrollar una nueva aplicación de HoloLens (a veces puede ayudar a realizar esas tareas para cada usuario).</span><span class="sxs-lookup"><span data-stu-id="7b246-156">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="7b246-157">Para obtener ayuda sobre la calibración, siga este [vínculo al artículo sobre la calibración de HoloLens](calibration.md#hololens-2).</span><span class="sxs-lookup"><span data-stu-id="7b246-157">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="7b246-158">Para obtener ayuda sobre la optimización de sensores, siga este [vínculo al artículo sobre la optimización del sensor de HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="7b246-158">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-custom-vision-portal"></a><span data-ttu-id="7b246-159">Capítulo 1: portal de Custom Vision</span><span class="sxs-lookup"><span data-stu-id="7b246-159">Chapter 1 - The Custom Vision Portal</span></span>

<span data-ttu-id="7b246-160">Para usar la **Custom Vision Service de Azure**, debe configurar una instancia de para que esté disponible para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7b246-160">To use the **Azure Custom Vision Service**, you will need to configure an instance of it to be made available to your application.</span></span>

1.  <span data-ttu-id="7b246-161">Navegue [hasta el **Custom Vision Service** Página principal](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span><span class="sxs-lookup"><span data-stu-id="7b246-161">Navigate [to the **Custom Vision Service** main page](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/).</span></span>

2.  <span data-ttu-id="7b246-162">Haga clic en **Introducción**.</span><span class="sxs-lookup"><span data-stu-id="7b246-162">Click on **Getting Started**.</span></span>

    ![](images/AzureLabs-Lab310-01.png)

3.  <span data-ttu-id="7b246-163">Inicie sesión en el portal de Custom Vision.</span><span class="sxs-lookup"><span data-stu-id="7b246-163">Sign in to the Custom Vision Portal.</span></span>

    ![](images/AzureLabs-Lab310-02.png)

4.  <span data-ttu-id="7b246-164">Si aún no tiene una cuenta de Azure, tendrá que crear una.</span><span class="sxs-lookup"><span data-stu-id="7b246-164">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="7b246-165">Si sigue este tutorial en una situación de aula o de laboratorio, pregunte al instructor o a uno de los Proctors para obtener ayuda para configurar la nueva cuenta.</span><span class="sxs-lookup"><span data-stu-id="7b246-165">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

5.  <span data-ttu-id="7b246-166">Una vez iniciada la sesión por primera vez, se le solicitará el panel *de condiciones de servicio* .</span><span class="sxs-lookup"><span data-stu-id="7b246-166">Once you are logged in for the first time, you will be prompted with the *Terms of Service* panel.</span></span> <span data-ttu-id="7b246-167">Haga clic en la casilla para *aceptar los términos*.</span><span class="sxs-lookup"><span data-stu-id="7b246-167">Click the checkbox to *agree to the terms*.</span></span> <span data-ttu-id="7b246-168">A continuación, haga clic en Acepto.</span><span class="sxs-lookup"><span data-stu-id="7b246-168">Then click **I agree**.</span></span>

    ![](images/AzureLabs-Lab310-03.png)

6.  <span data-ttu-id="7b246-169">Una vez aceptados los términos, ahora está en la sección *mis proyectos* .</span><span class="sxs-lookup"><span data-stu-id="7b246-169">Having agreed to the terms, you are now in the *My Projects* section.</span></span> <span data-ttu-id="7b246-170">Haga clic en **nuevo proyecto**.</span><span class="sxs-lookup"><span data-stu-id="7b246-170">Click on **New Project**.</span></span>

    ![](images/AzureLabs-Lab310-04.png)

7.  <span data-ttu-id="7b246-171">Aparecerá una pestaña en el lado derecho, que le pedirá que especifique algunos campos para el proyecto.</span><span class="sxs-lookup"><span data-stu-id="7b246-171">A tab will appear on the right-hand side, which will prompt you to specify some fields for the project.</span></span>

    1.  <span data-ttu-id="7b246-172">Insertar un nombre para el proyecto</span><span class="sxs-lookup"><span data-stu-id="7b246-172">Insert a name for your project</span></span>

    2.  <span data-ttu-id="7b246-173">Insertar una descripción para el proyecto (**opcional**)</span><span class="sxs-lookup"><span data-stu-id="7b246-173">Insert a description for your project (**Optional**)</span></span>

    3.  <span data-ttu-id="7b246-174">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="7b246-174">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="7b246-175">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="7b246-175">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="7b246-176">Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común).</span><span class="sxs-lookup"><span data-stu-id="7b246-176">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        ![](images/AzureLabs-Lab310-05.png)

        > [!NOTE]
        > <span data-ttu-id="7b246-177">Si desea [leer más información sobre los grupos de recursos de Azure, vaya a los documentos asociados](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal) .</span><span class="sxs-lookup"><span data-stu-id="7b246-177">If you wish to [read more about Azure Resource Groups, navigate to the associated Docs](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4.  <span data-ttu-id="7b246-178">Establezca los **tipos de proyecto** como **detección de objetos (vista previa)** .</span><span class="sxs-lookup"><span data-stu-id="7b246-178">Set the **Project Types** as **Object Detection (preview)**.</span></span>

8.  <span data-ttu-id="7b246-179">Cuando haya terminado, haga clic en **crear proyecto**y se le redirigirá a la página Custom Vision Service proyecto.</span><span class="sxs-lookup"><span data-stu-id="7b246-179">Once you are finished, click on **Create project**, and you will be redirected to the Custom Vision Service project page.</span></span>


## <a name="chapter-2---training-your-custom-vision-project"></a><span data-ttu-id="7b246-180">Capítulo 2: entrenar el proyecto de Custom Vision</span><span class="sxs-lookup"><span data-stu-id="7b246-180">Chapter 2 - Training your Custom Vision project</span></span>

<span data-ttu-id="7b246-181">Una vez en el portal de Custom Vision, el objetivo principal es entrenar el proyecto para que reconozca objetos específicos en las imágenes.</span><span class="sxs-lookup"><span data-stu-id="7b246-181">Once in the Custom Vision Portal, your primary objective is to train your project to recognize specific objects in images.</span></span>

<span data-ttu-id="7b246-182">Necesita al menos quince (15) imágenes para cada objeto que desea que reconozca la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7b246-182">You need at least fifteen (15) images for each object that you would like your application to recognize.</span></span> <span data-ttu-id="7b246-183">Puede usar las imágenes que se proporcionan con este curso ([una serie de tazas](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span><span class="sxs-lookup"><span data-stu-id="7b246-183">You can use the images provided with this course ([a series of cups](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Cup%20Images.zip)).</span></span>

<span data-ttu-id="7b246-184">Para entrenar su proyecto de Custom Vision:</span><span class="sxs-lookup"><span data-stu-id="7b246-184">To train your Custom Vision project:</span></span>

1.  <span data-ttu-id="7b246-185">Haga clic en **+** el botón situado junto a **etiquetas**.</span><span class="sxs-lookup"><span data-stu-id="7b246-185">Click on the **+** button next to **Tags**.</span></span>

    ![](images/AzureLabs-Lab310-06.png)

2.  <span data-ttu-id="7b246-186">Agregue un **nombre** para la etiqueta que se utilizará para asociar las imágenes con.</span><span class="sxs-lookup"><span data-stu-id="7b246-186">Add a **name** for the tag that will be used to associate your images with.</span></span> <span data-ttu-id="7b246-187">En este ejemplo se usan imágenes de copas para el reconocimiento, por lo que hemos llamado a la etiqueta de esta, **Cup**.</span><span class="sxs-lookup"><span data-stu-id="7b246-187">In this example we are using images of cups for recognition, so have named the tag for this, **Cup**.</span></span> <span data-ttu-id="7b246-188">Haga clic en **Guardar** cuando haya terminado.</span><span class="sxs-lookup"><span data-stu-id="7b246-188">Click **Save** once finished.</span></span>

    ![](images/AzureLabs-Lab310-07.png)

3.  <span data-ttu-id="7b246-189">Observará que se ha agregado la **etiqueta** (es posible que tenga que volver a cargar la página para que aparezca).</span><span class="sxs-lookup"><span data-stu-id="7b246-189">You will notice your **Tag** has been added (you may need to reload your page for it to appear).</span></span> 

    ![](images/AzureLabs-Lab310-08.png)

4.  <span data-ttu-id="7b246-190">Haga clic en **Agregar imágenes** en el centro de la página.</span><span class="sxs-lookup"><span data-stu-id="7b246-190">Click on **Add images** in the center of the page.</span></span>

    ![](images/AzureLabs-Lab310-09.png)

5.  <span data-ttu-id="7b246-191">Haga clic en **examinar archivos locales**y busque las imágenes que desea cargar para un objeto, con el mínimo de quince (15).</span><span class="sxs-lookup"><span data-stu-id="7b246-191">Click on **Browse local files**, and browse to the images you would like to upload for one object, with the minimum being fifteen (15).</span></span>

    > [!TIP]
    >  <span data-ttu-id="7b246-192">Puede seleccionar varias imágenes a la vez para cargarlas.</span><span class="sxs-lookup"><span data-stu-id="7b246-192">You can select several images at a time, to upload.</span></span>

    ![](images/AzureLabs-Lab310-10.png)

6.  <span data-ttu-id="7b246-193">Presione **cargar archivos** una vez que haya seleccionado todas las imágenes con las que desea entrenar el proyecto.</span><span class="sxs-lookup"><span data-stu-id="7b246-193">Press **Upload files** once you have selected all the images you would like to train the project with.</span></span> <span data-ttu-id="7b246-194">Los archivos comenzarán a cargarse.</span><span class="sxs-lookup"><span data-stu-id="7b246-194">The files will begin uploading.</span></span> <span data-ttu-id="7b246-195">Una vez que haya confirmado la carga, haga clic en **listo**.</span><span class="sxs-lookup"><span data-stu-id="7b246-195">Once you have confirmation of the upload, click **Done**.</span></span>

    ![](images/AzureLabs-Lab310-11.png)

7.  <span data-ttu-id="7b246-196">En este momento, las imágenes se cargan, pero no se etiquetan.</span><span class="sxs-lookup"><span data-stu-id="7b246-196">At this point your images are uploaded, but not tagged.</span></span>

    ![](images/AzureLabs-Lab310-12.png)

8.  <span data-ttu-id="7b246-197">Para etiquetar las imágenes, use el mouse.</span><span class="sxs-lookup"><span data-stu-id="7b246-197">To tag your images, use your mouse.</span></span> <span data-ttu-id="7b246-198">Al mantener el mouse sobre la imagen, un resaltado de selección le ayudará a dibujar automáticamente una selección alrededor del objeto.</span><span class="sxs-lookup"><span data-stu-id="7b246-198">As you hover over your image, a selection highlight will aid you by automatically drawing a selection around your object.</span></span> <span data-ttu-id="7b246-199">Si no es preciso, puede dibujar el suyo propio.</span><span class="sxs-lookup"><span data-stu-id="7b246-199">If it is not accurate, you can draw your own.</span></span> <span data-ttu-id="7b246-200">Para ello, mantenga pulsado el botón primario del mouse y arrastre la región de selección para abarcar el objeto.</span><span class="sxs-lookup"><span data-stu-id="7b246-200">This is accomplished by holding left-click on the mouse, and dragging the selection region to encompass your object.</span></span> 

    ![](images/AzureLabs-Lab310-13.png) 

9. <span data-ttu-id="7b246-201">Tras la selección del objeto dentro de la imagen, una pequeña solicitud le pedirá que *agregue la etiqueta de región*.</span><span class="sxs-lookup"><span data-stu-id="7b246-201">Following the selection of your object within the image, a small prompt will ask for you to *Add Region Tag*.</span></span> <span data-ttu-id="7b246-202">Seleccione la etiqueta creada anteriormente (' Cup ', en el ejemplo anterior) o, si va a agregar más etiquetas, escríbala y haga clic en el botón **+ (Plus)** .</span><span class="sxs-lookup"><span data-stu-id="7b246-202">Select your previously created tag ('Cup', in the above example), or if you are adding more tags, type that in and click the **+ (plus)** button.</span></span>

    ![](images/AzureLabs-Lab310-14.png) 

10. <span data-ttu-id="7b246-203">Para etiquetar la imagen siguiente, puede hacer clic en la flecha situada a la derecha de la hoja o cerrar la hoja de etiquetas (haciendo clic en la **X** en la esquina superior derecha de la hoja) y, a continuación, haga clic en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="7b246-203">To tag the next image, you can click the arrow to the right of the blade, or close the tag blade (by clicking the **X** in the top-right corner of the blade) and then click the next image.</span></span> <span data-ttu-id="7b246-204">Una vez que tenga la siguiente imagen lista, repita el mismo procedimiento.</span><span class="sxs-lookup"><span data-stu-id="7b246-204">Once you have the next image ready, repeat the same procedure.</span></span> <span data-ttu-id="7b246-205">Haga esto para todas las imágenes que ha cargado hasta que se etiqueten todas.</span><span class="sxs-lookup"><span data-stu-id="7b246-205">Do this for all the images you have uploaded, until they are all tagged.</span></span> 

    > [!NOTE]
    >  <span data-ttu-id="7b246-206">Puede seleccionar varios objetos en la misma imagen, como en la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="7b246-206">You can select several objects in the same image, like the image below:</span></span> 
    > 
    > ![](images/AzureLabs-Lab310-15.png)

11. <span data-ttu-id="7b246-207">Una vez que las etiquete todas, haga clic en el botón **etiquetado** , situado a la izquierda de la pantalla, para mostrar las imágenes etiquetadas.</span><span class="sxs-lookup"><span data-stu-id="7b246-207">Once you have tagged them all, click on the **tagged** button, on the left of the screen, to reveal the tagged images.</span></span> 

    ![](images/AzureLabs-Lab310-16.png)

12. <span data-ttu-id="7b246-208">Ya está listo para entrenar su servicio.</span><span class="sxs-lookup"><span data-stu-id="7b246-208">You are now ready to train your Service.</span></span> <span data-ttu-id="7b246-209">Haga clic en el botón **entrenar** y comenzará la primera iteración de entrenamiento.</span><span class="sxs-lookup"><span data-stu-id="7b246-209">Click the **Train** button, and the first training iteration will begin.</span></span>

    ![](images/AzureLabs-Lab310-17.png)

    ![](images/AzureLabs-Lab310-18.png)

13. <span data-ttu-id="7b246-210">Una vez compilada, podrá ver dos botones denominados establecer **dirección URL** **predeterminada** y de predicción.</span><span class="sxs-lookup"><span data-stu-id="7b246-210">Once it is built, you will be able to see two buttons called **Make default** and **Prediction URL**.</span></span> <span data-ttu-id="7b246-211">Haga clic en **establecer como predeterminado** primero y luego haga clic en **dirección URL**de predicción.</span><span class="sxs-lookup"><span data-stu-id="7b246-211">Click on **Make default** first, then click on **Prediction URL**.</span></span>

    ![](images/AzureLabs-Lab310-19.png)

    > [!NOTE] 
    > <span data-ttu-id="7b246-212">El extremo que se proporciona a partir de este, se establece en la iteración que se haya marcado como predeterminada.</span><span class="sxs-lookup"><span data-stu-id="7b246-212">The endpoint which is provided from this, is set to whichever *Iteration* has been marked as default.</span></span> <span data-ttu-id="7b246-213">Por lo tanto, si posteriormente realiza una nueva *iteración* y la actualiza como predeterminada, no necesitará cambiar el código.</span><span class="sxs-lookup"><span data-stu-id="7b246-213">As such, if you later make a new *Iteration* and update it as default, you will not need to change your code.</span></span>

14. <span data-ttu-id="7b246-214">Una vez que haya hecho clic **en URL**de predicción, abra el *Bloc de notas*y copie y pegue la **dirección URL** (también denominada predicción **-punto de conexión**) y la **clave de predicción del servicio**para que pueda recuperarla cuando la necesite más adelante en el código.</span><span class="sxs-lookup"><span data-stu-id="7b246-214">Once you have clicked on **Prediction URL**, open *Notepad*, and copy and paste the **URL** (also called your **Prediction-Endpoint**) and the **Service Prediction-Key**, so that you can retrieve it when you need it later in the code.</span></span>

    ![](images/AzureLabs-Lab310-20.png)

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="7b246-215">Capítulo 3: configuración del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="7b246-215">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="7b246-216">Lo siguiente es una configuración típica para desarrollar con la realidad mixta y, como tal, es una buena plantilla para otros proyectos.</span><span class="sxs-lookup"><span data-stu-id="7b246-216">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="7b246-217">Abra **Unity** y haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="7b246-217">Open **Unity** and click **New**.</span></span>

    ![](images/AzureLabs-Lab310-21.png)

2.  <span data-ttu-id="7b246-218">Ahora tendrá que proporcionar un nombre de proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="7b246-218">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="7b246-219">Inserte **CustomVisionObjDetection**.</span><span class="sxs-lookup"><span data-stu-id="7b246-219">Insert **CustomVisionObjDetection**.</span></span> <span data-ttu-id="7b246-220">Asegúrese de que el tipo de proyecto está establecido en **3D**y establezca la **Ubicación** en algún lugar adecuado para usted (Recuerde que, más cerca de los directorios raíz es mejor).</span><span class="sxs-lookup"><span data-stu-id="7b246-220">Make sure the project type is set to **3D**, and set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="7b246-221">A continuación, haga clic en **crear proyecto**.</span><span class="sxs-lookup"><span data-stu-id="7b246-221">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab310-22.png)

3.  <span data-ttu-id="7b246-222">Con Unity abierto, merece la pena comprobar que el **Editor** de scripts predeterminado está establecido en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7b246-222">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="7b246-223">Vaya a **Editar* > *preferencias** y, a continuación, en la nueva ventana, vaya a **herramientas externas**.</span><span class="sxs-lookup"><span data-stu-id="7b246-223">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="7b246-224">Cambie el **Editor de script externo** a **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7b246-224">Change **External Script Editor** to **Visual Studio**.</span></span> <span data-ttu-id="7b246-225">Cierre la ventana **preferencias** .</span><span class="sxs-lookup"><span data-stu-id="7b246-225">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab310-23.png)

4.  <span data-ttu-id="7b246-226">A continuación, vaya a **archivo > configuración de compilación** y cambie la **plataforma** a *plataforma universal de Windows*y, a continuación, haga clic en el botón **cambiar plataforma** .</span><span class="sxs-lookup"><span data-stu-id="7b246-226">Next, go to **File > Build Settings** and switch the **Platform** to *Universal Windows Platform*, and then clicking on the **Switch Platform** button.</span></span>

    ![](images/AzureLabs-Lab310-24.png)

5.  <span data-ttu-id="7b246-227">En la misma ventana de **configuración de compilación** , asegúrese de que se establece lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="7b246-227">In the same **Build Settings** window, ensure the following are set:</span></span>

    1.  <span data-ttu-id="7b246-228">El **dispositivo de destino** está establecido en **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="7b246-228">**Target Device** is set to **HoloLens**</span></span>        
    2.  <span data-ttu-id="7b246-229">El **tipo de compilación** se establece en **D3D**</span><span class="sxs-lookup"><span data-stu-id="7b246-229">**Build Type** is set to **D3D**</span></span>
    3.  <span data-ttu-id="7b246-230">**SDK** está establecido en la **versión más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="7b246-230">**SDK** is set to **Latest installed**</span></span>
    4.  <span data-ttu-id="7b246-231">La **versión de Visual Studio** está establecida en la **más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="7b246-231">**Visual Studio Version** is set to **Latest installed**</span></span>
    5.  <span data-ttu-id="7b246-232">**Compilar y ejecutar** está establecido en **equipo local**</span><span class="sxs-lookup"><span data-stu-id="7b246-232">**Build and Run** is set to **Local Machine**</span></span>            
    6.  <span data-ttu-id="7b246-233">El resto de la configuración, en la **configuración de compilación**, debe dejarse como predeterminada por ahora.</span><span class="sxs-lookup"><span data-stu-id="7b246-233">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

        ![](images/AzureLabs-Lab310-25.png)

6.  <span data-ttu-id="7b246-234">En la misma ventana de configuración de la **compilación** , haga clic en el botón **configuración del reproductor** ; se abrirá el panel relacionado en el espacio donde se encuentra el **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="7b246-234">In the same **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7. <span data-ttu-id="7b246-235">En este panel, deben comprobarse algunas opciones de configuración:</span><span class="sxs-lookup"><span data-stu-id="7b246-235">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="7b246-236">En la pestaña **otros valores** :</span><span class="sxs-lookup"><span data-stu-id="7b246-236">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="7b246-237">La **versión de scripting en tiempo de ejecución** debe ser **Experimental** (.net 4,6 equivalente), lo que desencadenará una necesidad de reiniciar el editor.</span><span class="sxs-lookup"><span data-stu-id="7b246-237">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="7b246-238">El **back-end** de scripting debe ser **.net**.</span><span class="sxs-lookup"><span data-stu-id="7b246-238">**Scripting Backend** should be **.NET**.</span></span>

        3. <span data-ttu-id="7b246-239">El **nivel de compatibilidad de API** debe ser **.net 4,6**.</span><span class="sxs-lookup"><span data-stu-id="7b246-239">**API Compatibility Level** should be **.NET 4.6**.</span></span>

            ![](images/AzureLabs-Lab310-26.png)

    2.  <span data-ttu-id="7b246-240">En la pestaña **configuración de publicación** , en **capacidades**, seleccione:</span><span class="sxs-lookup"><span data-stu-id="7b246-240">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="7b246-241">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="7b246-241">**InternetClient**</span></span>

        2.  <span data-ttu-id="7b246-242">**Web**</span><span class="sxs-lookup"><span data-stu-id="7b246-242">**Webcam**</span></span>

        3. <span data-ttu-id="7b246-243">**SpatialPerception**</span><span class="sxs-lookup"><span data-stu-id="7b246-243">**SpatialPerception**</span></span>

            <span data-ttu-id="7b246-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span><span class="sxs-lookup"><span data-stu-id="7b246-244">![](images/AzureLabs-Lab310-27.png) ![](images/AzureLabs-Lab310-28.png)</span></span>

    3.  <span data-ttu-id="7b246-245">Más abajo en el panel, en la **configuración de XR** (se encuentra debajo de **configuración de publicación**), marque la **realidad virtual compatible**y asegúrese de que se agrega el **SDK de Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="7b246-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, then make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab310-29.png)

8.  <span data-ttu-id="7b246-246">De nuevo en la **configuración de compilación**, los *proyectos de Unity C\#*  ya no están atenuados: Marque la casilla situada junto a este.</span><span class="sxs-lookup"><span data-stu-id="7b246-246">Back in **Build Settings**, *Unity C\# Projects* is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="7b246-247">Cierre la ventana **configuración de compilación** .</span><span class="sxs-lookup"><span data-stu-id="7b246-247">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="7b246-248">En el **Editor**, haga clic en **Editar** > **configuración** > del proyecto**gráficos**.</span><span class="sxs-lookup"><span data-stu-id="7b246-248">In the **Editor**, click on **Edit** > **Project Settings** > **Graphics**.</span></span>

    ![](images/AzureLabs-Lab310-30.png)

11. <span data-ttu-id="7b246-249">En el **panel Inspector** , se abrirá la *configuración de gráficos* .</span><span class="sxs-lookup"><span data-stu-id="7b246-249">In the **Inspector Panel** the *Graphics Settings* will be open.</span></span> <span data-ttu-id="7b246-250">Desplácese hacia abajo hasta que vea una matriz denominada **incluir siempre sombreadores**.</span><span class="sxs-lookup"><span data-stu-id="7b246-250">Scroll down until you see an array called **Always Include Shaders**.</span></span> <span data-ttu-id="7b246-251">Agregue una ranura aumentando la variable de **tamaño** en uno (en este ejemplo, era 8, por lo que lo hicimos 9).</span><span class="sxs-lookup"><span data-stu-id="7b246-251">Add a slot by increasing the **Size** variable by one (in this example, it was 8 so we made it 9).</span></span> <span data-ttu-id="7b246-252">Aparecerá una nueva ranura en la última posición de la matriz, como se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="7b246-252">A new slot will appear, in the last position of the array, as shown below:</span></span>

    ![](images/AzureLabs-Lab310-31.png)

12. <span data-ttu-id="7b246-253">En la ranura, haga clic en el círculo de destino pequeño junto a la ranura para abrir una lista de sombreadores.</span><span class="sxs-lookup"><span data-stu-id="7b246-253">In the slot, click on the small target circle next to the slot to open a list of shaders.</span></span> <span data-ttu-id="7b246-254">Busque los sombreadores **heredados/transparente/difusor** y haga doble clic en él.</span><span class="sxs-lookup"><span data-stu-id="7b246-254">Look for the **Legacy Shaders/Transparent/Diffuse** shader and double-click it.</span></span> 

    ![](images/AzureLabs-Lab310-32.png)

## <a name="chapter-4---importing-the-customvisionobjdetection-unity-package"></a><span data-ttu-id="7b246-255">Capítulo 4: importación del paquete Unity de CustomVisionObjDetection</span><span class="sxs-lookup"><span data-stu-id="7b246-255">Chapter 4 - Importing the CustomVisionObjDetection Unity package</span></span>

<span data-ttu-id="7b246-256">En este curso, se proporciona un paquete de recursos de Unity llamado **Azure-Mr-310. unitypackage Tools**.</span><span class="sxs-lookup"><span data-stu-id="7b246-256">For this course you are provided with a Unity Asset Package called **Azure-MR-310.unitypackage**.</span></span> 

> <span data-ttu-id="7b246-257">Tip Cualquier objeto admitido por Unity, incluidas todas las escenas, se puede empaquetar en un archivo **. unitypackage Tools** y exportarse o importarse en otros proyectos.</span><span class="sxs-lookup"><span data-stu-id="7b246-257">[TIP] Any objects supported by Unity, including entire scenes, can be packaged into a **.unitypackage** file, and exported / imported in other projects.</span></span> <span data-ttu-id="7b246-258">Es la forma más segura y eficaz de trasladar recursos entre distintos proyectos de **Unity**.</span><span class="sxs-lookup"><span data-stu-id="7b246-258">It is the safest, and most efficient, way to move assets between different **Unity projects**.</span></span>

<span data-ttu-id="7b246-259">Puede encontrar el [paquete Azure-Mr-310 que necesita descargar aquí](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="7b246-259">You can find the [Azure-MR-310 package that you need to download here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20310%20-%20Object%20detection/Azure-MR-310.unitypackage).</span></span>

1.  <span data-ttu-id="7b246-260">Con el panel de Unity delante de usted, haga clic en **recursos** en el menú de la parte superior de la pantalla y, a continuación, haga clic en **importar paquete > paquete personalizado**.</span><span class="sxs-lookup"><span data-stu-id="7b246-260">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![](images/AzureLabs-Lab310-33.png)

2.  <span data-ttu-id="7b246-261">Use el selector de archivos para seleccionar el paquete **Azure-Mr-310. unitypackage Tools** y haga clic en **abrir**.</span><span class="sxs-lookup"><span data-stu-id="7b246-261">Use the file picker to select the **Azure-MR-310.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="7b246-262">Se le mostrará una lista de los componentes de este recurso.</span><span class="sxs-lookup"><span data-stu-id="7b246-262">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="7b246-263">Para confirmar la importación, haga clic en el botón **importar** .</span><span class="sxs-lookup"><span data-stu-id="7b246-263">Confirm the import by clicking the **Import** button.</span></span>

    ![](images/AzureLabs-Lab310-34.png)

3.  <span data-ttu-id="7b246-264">Una vez que haya finalizado la importación, observará que ahora se han agregado carpetas del paquete a la carpeta **assets** .</span><span class="sxs-lookup"><span data-stu-id="7b246-264">Once it has finished importing, you will notice that folders from the package have now been added to your **Assets** folder.</span></span> <span data-ttu-id="7b246-265">Este tipo de estructura de carpetas es típico para un proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="7b246-265">This kind of folder structure is typical for a Unity project.</span></span>

    ![](images/AzureLabs-Lab310-35.png)

    1.  <span data-ttu-id="7b246-266">La carpeta **materiales** contiene el material usado por el **cursor de mira fijamente**.</span><span class="sxs-lookup"><span data-stu-id="7b246-266">The **Materials** folder contains the material used by the **Gaze Cursor**.</span></span> 

    2.  <span data-ttu-id="7b246-267">La carpeta plugins contiene el archivo dll de Newtonsoft que usa el código para deserializar la respuesta web del servicio.</span><span class="sxs-lookup"><span data-stu-id="7b246-267">The **Plugins** folder contains the Newtonsoft DLL used by the code to deserialize the Service web response.</span></span> <span data-ttu-id="7b246-268">Las dos (2) versiones diferentes contenidas en la carpeta y subcarpeta, son necesarias para permitir que la biblioteca sea utilizada y compilada por el editor de Unity y la compilación de UWP.</span><span class="sxs-lookup"><span data-stu-id="7b246-268">The two (2) different versions contained in the folder, and sub-folder, are necessary to allow the library to be used and built by both the Unity Editor and the UWP build.</span></span> 

    3.  <span data-ttu-id="7b246-269">La carpeta **Prefabs** contiene el Prefabs contenido en la escena.</span><span class="sxs-lookup"><span data-stu-id="7b246-269">The **Prefabs** folder contains the prefabs contained in the scene.</span></span> <span data-ttu-id="7b246-270">Estos son:</span><span class="sxs-lookup"><span data-stu-id="7b246-270">Those are:</span></span>

        1.  <span data-ttu-id="7b246-271">**GazeCursor**, el cursor que se usa en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7b246-271">The **GazeCursor**, the cursor used in the application.</span></span> <span data-ttu-id="7b246-272">Funcionará junto con el recurso prefabricado de SpatialMapping para poder colocarse en la escena sobre objetos físicos.</span><span class="sxs-lookup"><span data-stu-id="7b246-272">Will work together with the SpatialMapping prefab to be able to be placed in the scene on top of physical objects.</span></span>
        2.  <span data-ttu-id="7b246-273">La **etiqueta**, que es el objeto de interfaz de usuario que se usa para mostrar la etiqueta de objeto en la escena cuando sea necesario.</span><span class="sxs-lookup"><span data-stu-id="7b246-273">The **Label**, which is the UI object used to display the object tag in the scene when required.</span></span>
        3.  <span data-ttu-id="7b246-274">**SpatialMapping**, que es el objeto que permite a la aplicación usar crear un mapa virtual, mediante el seguimiento espacial de Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7b246-274">The **SpatialMapping**, which is the object that enables the application to use create a virtual map, using the Microsoft HoloLens' spatial tracking.</span></span>

    4.  <span data-ttu-id="7b246-275">La carpeta Scenes que contiene actualmente la escena pregenerada para este curso.</span><span class="sxs-lookup"><span data-stu-id="7b246-275">The **Scenes** folder which currently contains the pre-built scene for this course.</span></span>

4.  <span data-ttu-id="7b246-276">Abra la carpeta Scenes, en el **panel Proyecto**, y haga doble clic en **ObjDetectionScene**para cargar la escena que usará para este curso.</span><span class="sxs-lookup"><span data-stu-id="7b246-276">Open the **Scenes** folder, in the **Project Panel**, and double-click on the **ObjDetectionScene**, to load the scene that you will use for this course.</span></span>

    ![](images/AzureLabs-Lab310-36.png)

    > [!NOTE] 
    >  <span data-ttu-id="7b246-277">**No se incluye ningún código**, se escribirá el código siguiendo este curso.</span><span class="sxs-lookup"><span data-stu-id="7b246-277">**No code is included**, you will write the code by following this course.</span></span>

## <a name="chapter-5---create-the-customvisionanalyser-class"></a><span data-ttu-id="7b246-278">Capítulo 5: creación de la clase CustomVisionAnalyser.</span><span class="sxs-lookup"><span data-stu-id="7b246-278">Chapter 5 - Create the CustomVisionAnalyser class.</span></span>

<span data-ttu-id="7b246-279">En este momento está listo para escribir código.</span><span class="sxs-lookup"><span data-stu-id="7b246-279">At this point you are ready to write some code.</span></span> <span data-ttu-id="7b246-280">Comenzará con la clase **CustomVisionAnalyser** .</span><span class="sxs-lookup"><span data-stu-id="7b246-280">You will begin with the **CustomVisionAnalyser** class.</span></span>

> [!NOTE]
> <span data-ttu-id="7b246-281">Las llamadas al **Custom Vision Service**, realizadas en el código que se muestra a continuación, se realizan mediante la **API de REST de Custom Vision**.</span><span class="sxs-lookup"><span data-stu-id="7b246-281">The calls to the **Custom Vision Service**, made in the code shown below, are made using the **Custom Vision REST API**.</span></span> <span data-ttu-id="7b246-282">Mediante este procedimiento, verá cómo implementar y usar esta API (útil para entender cómo implementar algo similar por su cuenta).</span><span class="sxs-lookup"><span data-stu-id="7b246-282">Through using this, you will see how to implement and make use of this API (useful for understanding how to implement something similar on your own).</span></span> <span data-ttu-id="7b246-283">Tenga en cuenta que Microsoft ofrece un **SDK de Custom Vision** que también se puede usar para realizar llamadas al servicio.</span><span class="sxs-lookup"><span data-stu-id="7b246-283">Be aware, that Microsoft offers a **Custom Vision SDK** that can also be used to make calls to the Service.</span></span> <span data-ttu-id="7b246-284">Para obtener más información, visite el [artículo Custom Vision SDK](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span><span class="sxs-lookup"><span data-stu-id="7b246-284">For more information visit the [Custom Vision SDK article](https://github.com/Microsoft/Cognitive-CustomVision-Windows/).</span></span>

<span data-ttu-id="7b246-285">Esta clase es responsable de:</span><span class="sxs-lookup"><span data-stu-id="7b246-285">This class is responsible for:</span></span>

- <span data-ttu-id="7b246-286">Cargar la imagen más reciente capturada como una matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="7b246-286">Loading the latest image captured as an array of bytes.</span></span>

- <span data-ttu-id="7b246-287">Envío de la matriz de bytes a la instancia de Azure **Custom Vision Service** para su análisis.</span><span class="sxs-lookup"><span data-stu-id="7b246-287">Sending the byte array to your Azure **Custom Vision Service** instance for analysis.</span></span>

- <span data-ttu-id="7b246-288">Recibir la respuesta como una cadena JSON.</span><span class="sxs-lookup"><span data-stu-id="7b246-288">Receiving the response as a JSON string.</span></span>

- <span data-ttu-id="7b246-289">Deserializar la respuesta y pasar la **predicción** resultante a la clase **SceneOrganiser** , que se encargará de cómo se debe mostrar la respuesta.</span><span class="sxs-lookup"><span data-stu-id="7b246-289">Deserializing the response and passing the resulting **Prediction** to the **SceneOrganiser** class, which will take care of how the response should be displayed.</span></span>

<span data-ttu-id="7b246-290">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="7b246-290">To create this class:</span></span>

1.  <span data-ttu-id="7b246-291">Haga clic con el botón derecho en la **carpeta de recursos**, que se encuentra en el **panel Proyecto**y, a continuación, haga clic en **crear** > **carpeta**.</span><span class="sxs-lookup"><span data-stu-id="7b246-291">Right-click in the **Asset Folder**, located in the **Project Panel**, then click **Create** > **Folder**.</span></span> <span data-ttu-id="7b246-292">Llame a los **scripts**de la carpeta.</span><span class="sxs-lookup"><span data-stu-id="7b246-292">Call the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab310-37.png)

2.  <span data-ttu-id="7b246-293">Haga doble clic en la carpeta que acaba de crear para abrirla.</span><span class="sxs-lookup"><span data-stu-id="7b246-293">Double-click on the newly created folder, to open it.</span></span>

3.  <span data-ttu-id="7b246-294">Haga clic con el botón derecho en la carpeta y luego haga clic en **crear** > **script de C\#** .</span><span class="sxs-lookup"><span data-stu-id="7b246-294">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="7b246-295">Asigne al script el nombre **CustomVisionAnalyser.**</span><span class="sxs-lookup"><span data-stu-id="7b246-295">Name the script **CustomVisionAnalyser.**</span></span>

4.  <span data-ttu-id="7b246-296">Haga doble clic en el nuevo script **CustomVisionAnalyser** para abrirlo con **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="7b246-296">Double-click on the new **CustomVisionAnalyser** script to open it with **Visual Studio.**</span></span>

5.  <span data-ttu-id="7b246-297">Asegúrese de que tiene los siguientes espacios de nombres a los que se hace referencia en la parte superior del archivo:</span><span class="sxs-lookup"><span data-stu-id="7b246-297">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.IO;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="7b246-298">En la clase **CustomVisionAnalyser** , agregue las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="7b246-298">In the **CustomVisionAnalyser** class, add the following variables:</span></span>

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
    > <span data-ttu-id="7b246-299">Asegúrese de insertar la **clave de predicción de servicio** en la **variable PredictionKey** y el **punto de conexión de predicción** en la variable **predictionEndpoint** .</span><span class="sxs-lookup"><span data-stu-id="7b246-299">Make sure you insert your **Service Prediction-Key** into the **predictionKey** variable and your **Prediction-Endpoint** into the **predictionEndpoint** variable.</span></span> <span data-ttu-id="7b246-300">Los copió en [el Bloc de notas anterior, en el capítulo 2, paso 14](#chapter-2---training-your-custom-vision-project).</span><span class="sxs-lookup"><span data-stu-id="7b246-300">You copied these to [Notepad earlier, in Chapter 2, Step 14](#chapter-2---training-your-custom-vision-project).</span></span>

7.  <span data-ttu-id="7b246-301">Ahora es necesario agregar el código para **activo ()** para inicializar la variable de instancia:</span><span class="sxs-lookup"><span data-stu-id="7b246-301">Code for **Awake()** now needs to be added to initialize the Instance variable:</span></span>

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

8.  <span data-ttu-id="7b246-302">Agregue la corutina (con el método estático **GetImageAsByteArray ()** debajo de ella), que obtendrá los resultados del análisis de la imagen, capturado por la clase **ImageCapture** .</span><span class="sxs-lookup"><span data-stu-id="7b246-302">Add the coroutine (with the static **GetImageAsByteArray()** method below it), which will obtain the results of the analysis of the image, captured by the **ImageCapture** class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7b246-303">En la corutina **AnalyseImageCapture** , hay una llamada a la clase **SceneOrganiser** que se va a crear todavía.</span><span class="sxs-lookup"><span data-stu-id="7b246-303">In the **AnalyseImageCapture** coroutine, there is a call to the **SceneOrganiser** class that you are yet to create.</span></span> <span data-ttu-id="7b246-304">Por lo tanto, **deje las líneas comentadas por ahora**.</span><span class="sxs-lookup"><span data-stu-id="7b246-304">Therefore, **leave those lines commented for now**.</span></span>

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

9. <span data-ttu-id="7b246-305">Elimine los métodos **Start ()** y **Update ()** , ya que no se usarán.</span><span class="sxs-lookup"><span data-stu-id="7b246-305">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span> 

10.  <span data-ttu-id="7b246-306">Asegúrese de guardar los cambios en **Visual Studio**antes de volver a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="7b246-306">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7b246-307">Como se mencionó anteriormente, no se preocupe por el código que podría parecer que tiene un error, ya que proporcionaremos más clases pronto, lo que solucionará estos errores.</span><span class="sxs-lookup"><span data-stu-id="7b246-307">As mentioned earlier, do not worry about code which might appear to have an error, as you will provide further classes soon, which will fix these.</span></span>

## <a name="chapter-6---create-the-customvisionobjects-class"></a><span data-ttu-id="7b246-308">Capítulo 6: crear la clase CustomVisionObjects</span><span class="sxs-lookup"><span data-stu-id="7b246-308">Chapter 6 - Create the CustomVisionObjects class</span></span>

<span data-ttu-id="7b246-309">La clase que creará ahora es la clase **CustomVisionObjects** .</span><span class="sxs-lookup"><span data-stu-id="7b246-309">The class you will create now is the **CustomVisionObjects** class.</span></span>

<span data-ttu-id="7b246-310">Este script contiene una serie de objetos utilizados por otras clases para serializar y deserializar las llamadas realizadas a la Custom Vision Service.</span><span class="sxs-lookup"><span data-stu-id="7b246-310">This script contains a number of objects used by other classes to serialize and deserialize the calls made to the Custom Vision Service.</span></span>

<span data-ttu-id="7b246-311">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="7b246-311">To create this class:</span></span>

1.  <span data-ttu-id="7b246-312">Haga clic con el botón derecho en la carpeta scripts y luego haga clic en **crear** > **script de C\#** .</span><span class="sxs-lookup"><span data-stu-id="7b246-312">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="7b246-313">Llame al script **CustomVisionObjects.**</span><span class="sxs-lookup"><span data-stu-id="7b246-313">Call the script **CustomVisionObjects.**</span></span>

2.  <span data-ttu-id="7b246-314">Haga doble clic en el nuevo script **CustomVisionObjects** para abrirlo con **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="7b246-314">Double-click on the new **CustomVisionObjects** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="7b246-315">Asegúrese de que tiene los siguientes espacios de nombres a los que se hace referencia en la parte superior del archivo:</span><span class="sxs-lookup"><span data-stu-id="7b246-315">Make sure you have the following namespaces referenced at the top of the file:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

4.  <span data-ttu-id="7b246-316">Elimine los métodos **Start ()** y **Update ()** dentro de la clase **CustomVisionObjects** , esta clase debe estar ahora vacía.</span><span class="sxs-lookup"><span data-stu-id="7b246-316">Delete the **Start()** and **Update()** methods inside the **CustomVisionObjects** class, this class should now be empty.</span></span>

    > [!WARNING]
    > <span data-ttu-id="7b246-317">Es importante que siga detenidamente la siguiente instrucción.</span><span class="sxs-lookup"><span data-stu-id="7b246-317">It is important you follow the next instruction carefully.</span></span> <span data-ttu-id="7b246-318">Si coloca las nuevas declaraciones de clase dentro de la clase **CustomVisionObjects** , obtendrá errores de compilación en el [capítulo 10](#chapter-10---create-the-imagecapture-class), lo que indica que no se encuentran **AnalysisRootObject** y **BoundingBox** .</span><span class="sxs-lookup"><span data-stu-id="7b246-318">If you put the new class declarations inside the **CustomVisionObjects** class, you will get compile errors in [chapter 10](#chapter-10---create-the-imagecapture-class), stating that **AnalysisRootObject** and **BoundingBox** are not found.</span></span>

5.  <span data-ttu-id="7b246-319">Agregue las siguientes clases *fuera* de la clase **CustomVisionObjects** .</span><span class="sxs-lookup"><span data-stu-id="7b246-319">Add the following classes *outside* the **CustomVisionObjects** class.</span></span> <span data-ttu-id="7b246-320">La biblioteca **Newtonsoft** usa estos objetos para serializar y deserializar los datos de respuesta:</span><span class="sxs-lookup"><span data-stu-id="7b246-320">These objects are used by the **Newtonsoft** library to serialize and deserialize the response data:</span></span>

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

6.  <span data-ttu-id="7b246-321">Asegúrese de guardar los cambios en **Visual Studio**antes de volver a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="7b246-321">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-7---create-the-spatialmapping-class"></a><span data-ttu-id="7b246-322">Capítulo 7: creación de la clase SpatialMapping</span><span class="sxs-lookup"><span data-stu-id="7b246-322">Chapter 7 - Create the SpatialMapping class</span></span>

<span data-ttu-id="7b246-323">Esta clase establecerá el **Colisionador de asignación espacial** en la escena para poder detectar colisiones entre objetos virtuales y objetos reales.</span><span class="sxs-lookup"><span data-stu-id="7b246-323">This class will set the **Spatial Mapping Collider** in the scene so to be able to detect collisions between virtual objects and real objects.</span></span>

<span data-ttu-id="7b246-324">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="7b246-324">To create this class:</span></span>

1.  <span data-ttu-id="7b246-325">Haga clic con el botón derecho en la carpeta scripts y luego haga clic en **crear** > **script de C\#** .</span><span class="sxs-lookup"><span data-stu-id="7b246-325">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="7b246-326">Llame al script **SpatialMapping.**</span><span class="sxs-lookup"><span data-stu-id="7b246-326">Call the script **SpatialMapping.**</span></span>

2.  <span data-ttu-id="7b246-327">Haga doble clic en el nuevo script **SpatialMapping** para abrirlo con **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="7b246-327">Double-click on the new **SpatialMapping** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="7b246-328">Asegúrese de que tiene los siguientes espacios de nombres a los que se hace referencia sobre la clase **SpatialMapping** :</span><span class="sxs-lookup"><span data-stu-id="7b246-328">Make sure you have the following namespaces referenced above the **SpatialMapping** class:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA;
    ```

4.  <span data-ttu-id="7b246-329">A continuación, agregue las siguientes variables dentro de la clase **SpatialMapping** , sobre el método **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="7b246-329">Then, add the following variables inside the **SpatialMapping** class, above the **Start()** method:</span></span>

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

5.  <span data-ttu-id="7b246-330">Agregue el **activo ()** y el **Inicio ()** :</span><span class="sxs-lookup"><span data-stu-id="7b246-330">Add the **Awake()** and **Start()**:</span></span>

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

6.  <span data-ttu-id="7b246-331">Elimine el método **Update ()** .</span><span class="sxs-lookup"><span data-stu-id="7b246-331">Delete the **Update()** method.</span></span>

7.  <span data-ttu-id="7b246-332">Asegúrese de guardar los cambios en **Visual Studio**antes de volver a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="7b246-332">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>


## <a name="chapter-8---create-the-gazecursor-class"></a><span data-ttu-id="7b246-333">Capítulo 8: creación de la clase GazeCursor</span><span class="sxs-lookup"><span data-stu-id="7b246-333">Chapter 8 - Create the GazeCursor class</span></span>

<span data-ttu-id="7b246-334">Esta clase es responsable de configurar el cursor en la ubicación correcta en el espacio real, mediante el uso de **SpatialMappingCollider**, que se creó en el capítulo anterior.</span><span class="sxs-lookup"><span data-stu-id="7b246-334">This class is responsible for setting up the cursor in the correct location in real space, by making use of the **SpatialMappingCollider**, created in the previous chapter.</span></span>

<span data-ttu-id="7b246-335">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="7b246-335">To create this class:</span></span>

1.  <span data-ttu-id="7b246-336">Haga clic con el botón derecho en la carpeta scripts y luego haga clic en **crear** > **script de C\#** .</span><span class="sxs-lookup"><span data-stu-id="7b246-336">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="7b246-337">Llame al script **GazeCursor**</span><span class="sxs-lookup"><span data-stu-id="7b246-337">Call the script **GazeCursor**</span></span>

2.  <span data-ttu-id="7b246-338">Haga doble clic en el nuevo script **GazeCursor** para abrirlo con **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="7b246-338">Double-click on the new **GazeCursor** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="7b246-339">Asegúrese de que tiene el siguiente espacio de nombres al que se hace referencia sobre la clase **GazeCursor** :</span><span class="sxs-lookup"><span data-stu-id="7b246-339">Make sure you have the following namespace referenced above the **GazeCursor** class:</span></span>

    ```csharp
    using UnityEngine;
    ```

4.  <span data-ttu-id="7b246-340">A continuación, agregue la variable siguiente dentro de la clase **GazeCursor** , sobre el método **Start ()** .</span><span class="sxs-lookup"><span data-stu-id="7b246-340">Then add the following variable inside the **GazeCursor** class, above the **Start()** method.</span></span> 

    ```csharp
        /// <summary>
        /// The cursor (this object) mesh renderer
        /// </summary>
        private MeshRenderer meshRenderer;
    ```

5.  <span data-ttu-id="7b246-341">Actualice el método **Start ()** con el siguiente código:</span><span class="sxs-lookup"><span data-stu-id="7b246-341">Update the **Start()** method with the following code:</span></span>

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

6.  <span data-ttu-id="7b246-342">Actualice el método **Update ()** con el siguiente código:</span><span class="sxs-lookup"><span data-stu-id="7b246-342">Update the **Update()** method with the following code:</span></span>

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
    > <span data-ttu-id="7b246-343">No se preocupe por el error de la clase **SceneOrganiser** que no se encuentra, la creará en el siguiente capítulo.</span><span class="sxs-lookup"><span data-stu-id="7b246-343">Do not worry about the error for the **SceneOrganiser** class not being found, you will create it in the next chapter.</span></span>

7. <span data-ttu-id="7b246-344">Asegúrese de guardar los cambios en **Visual Studio**antes de volver a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="7b246-344">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-9---create-the-sceneorganiser-class"></a><span data-ttu-id="7b246-345">Capítulo 9: creación de la clase SceneOrganiser</span><span class="sxs-lookup"><span data-stu-id="7b246-345">Chapter 9 - Create the SceneOrganiser class</span></span>

<span data-ttu-id="7b246-346">Esta clase hará lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="7b246-346">This class will:</span></span>

-   <span data-ttu-id="7b246-347">Configure la *cámara principal* adjuntando los componentes adecuados.</span><span class="sxs-lookup"><span data-stu-id="7b246-347">Set up the *Main Camera* by attaching the appropriate components to it.</span></span>

-   <span data-ttu-id="7b246-348">Cuando se detecta un objeto, será responsable de calcular su posición en el mundo real y de colocar una etiqueta de **etiqueta** cerca del **nombre de etiqueta**adecuado.</span><span class="sxs-lookup"><span data-stu-id="7b246-348">When an object is detected, it will be responsible for calculating its position in the real world and place a **Tag Label** near it with the appropriate **Tag Name**.</span></span>    

<span data-ttu-id="7b246-349">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="7b246-349">To create this class:</span></span>

1.  <span data-ttu-id="7b246-350">Haga clic con el botón derecho en la carpeta scripts y luego haga clic en **crear** > **script de C\#** .</span><span class="sxs-lookup"><span data-stu-id="7b246-350">Right-click inside the **Scripts** folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="7b246-351">Asigne al script el nombre **SceneOrganiser**.</span><span class="sxs-lookup"><span data-stu-id="7b246-351">Name the script **SceneOrganiser**.</span></span>

2.  <span data-ttu-id="7b246-352">Haga doble clic en el nuevo script **SceneOrganiser** para abrirlo con **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="7b246-352">Double-click on the new **SceneOrganiser** script to open it with **Visual Studio.**</span></span>

3.  <span data-ttu-id="7b246-353">Asegúrese de que tiene los siguientes espacios de nombres a los que se hace referencia sobre la clase **SceneOrganiser** :</span><span class="sxs-lookup"><span data-stu-id="7b246-353">Make sure you have the following namespaces referenced above the **SceneOrganiser** class:</span></span>

    ```csharp
    using System.Collections.Generic;
    using System.Linq;
    using UnityEngine;
    ```

4.  <span data-ttu-id="7b246-354">A continuación, agregue las siguientes variables dentro de la clase **SceneOrganiser** , sobre el método **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="7b246-354">Then add the following variables inside the **SceneOrganiser** class, above the **Start()** method:</span></span>

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

5.  <span data-ttu-id="7b246-355">Elimine los métodos **Start ()** y **Update ()** .</span><span class="sxs-lookup"><span data-stu-id="7b246-355">Delete the **Start()** and **Update()** methods.</span></span>

6.  <span data-ttu-id="7b246-356">Debajo de las variables, agregue el método **activo ()** , que inicializará la clase y configurará la escena.</span><span class="sxs-lookup"><span data-stu-id="7b246-356">Underneath the variables, add the **Awake()** method, which will initialize the class and set up the scene.</span></span>

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

7.  <span data-ttu-id="7b246-357">Agregue el método **PlaceAnalysisLabel ()** , que creará *una instancia* de la etiqueta en la escena (que en este punto es invisible para el usuario).</span><span class="sxs-lookup"><span data-stu-id="7b246-357">Add the **PlaceAnalysisLabel()** method, which will *Instantiate* the label in the scene (which at this point is invisible to the user).</span></span> <span data-ttu-id="7b246-358">También coloca el cuádruple (también invisible) en el que se coloca la imagen y se superpone con el mundo real.</span><span class="sxs-lookup"><span data-stu-id="7b246-358">It also places the quad (also invisible) where the image is placed, and overlaps with the real world.</span></span> <span data-ttu-id="7b246-359">Esto es importante porque las coordenadas del cuadro recuperadas del servicio después del análisis se devuelven a este cuádruple para determinar la ubicación aproximada del objeto en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="7b246-359">This is important because the box coordinates retrieved from the Service after analysis are traced back into this quad to determined the approximate location of the object in the real world.</span></span> 

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

8.  <span data-ttu-id="7b246-360">Agregue el método **FinaliseLabel ()** .</span><span class="sxs-lookup"><span data-stu-id="7b246-360">Add the **FinaliseLabel()** method.</span></span> <span data-ttu-id="7b246-361">Es responsable de:</span><span class="sxs-lookup"><span data-stu-id="7b246-361">It is responsible for:</span></span>

    *   <span data-ttu-id="7b246-362">Establecer el texto de la *etiqueta* con la *etiqueta* de la predicción con la mayor confianza.</span><span class="sxs-lookup"><span data-stu-id="7b246-362">Setting the *Label* text with the *Tag* of the Prediction with the highest confidence.</span></span>
    *   <span data-ttu-id="7b246-363">Llamar al cálculo del *cuadro de límite* en el objeto cuádruple, colocado previamente y colocar la etiqueta en la escena.</span><span class="sxs-lookup"><span data-stu-id="7b246-363">Calling the calculation of the *Bounding Box* on the quad object, positioned previously, and placing the label in the scene.</span></span>
    *   <span data-ttu-id="7b246-364">Ajustar la profundidad de la etiqueta mediante una Raycast hacia el *cuadro de límite*, que debe entrar en conflicto con el objeto en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="7b246-364">Adjusting the label depth by using a Raycast towards the *Bounding Box*, which should collide against the object in the real world.</span></span>
    * <span data-ttu-id="7b246-365">Restablecer el proceso de captura para permitir que el usuario Capture otra imagen.</span><span class="sxs-lookup"><span data-stu-id="7b246-365">Resetting the capture process to allow the user to capture another image.</span></span>

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

9.  <span data-ttu-id="7b246-366">Agregue el método **CalculateBoundingBoxPosition ()** , que hospeda varios cálculos necesarios para traducir las coordenadas del *cuadro de límite* recuperadas del servicio y volver a crearlas proporcionalmente en el cuádruple.</span><span class="sxs-lookup"><span data-stu-id="7b246-366">Add the **CalculateBoundingBoxPosition()** method, which hosts a number of calculations necessary to translate the *Bounding Box* coordinates retrieved from the Service and recreate them proportionally on the quad.</span></span>

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

10. <span data-ttu-id="7b246-367">Asegúrese de guardar los cambios en **Visual Studio**antes de volver a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="7b246-367">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="7b246-368">Antes de continuar, abra la clase **CustomVisionAnalyser** y, en el método **AnalyseLastImageCaptured ()** , *Quite las marcas de comentario* de las líneas siguientes:</span><span class="sxs-lookup"><span data-stu-id="7b246-368">Before you continue, open the **CustomVisionAnalyser** class, and within the **AnalyseLastImageCaptured()** method, *uncomment* the following lines:</span></span>
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
> <span data-ttu-id="7b246-369">No se preocupe por el mensaje "no se encontró la clase **ImageCapture** ", se creará en el siguiente capítulo.</span><span class="sxs-lookup"><span data-stu-id="7b246-369">Do not worry about the **ImageCapture** class 'could not be found' message, you will create it in the next chapter.</span></span>


## <a name="chapter-10---create-the-imagecapture-class"></a><span data-ttu-id="7b246-370">Capítulo 10: creación de la clase ImageCapture</span><span class="sxs-lookup"><span data-stu-id="7b246-370">Chapter 10 - Create the ImageCapture class</span></span>

<span data-ttu-id="7b246-371">La clase siguiente que va a crear es la clase **ImageCapture** .</span><span class="sxs-lookup"><span data-stu-id="7b246-371">The next class you are going to create is the **ImageCapture** class.</span></span>

<span data-ttu-id="7b246-372">Esta clase es responsable de:</span><span class="sxs-lookup"><span data-stu-id="7b246-372">This class is responsible for:</span></span>

*   <span data-ttu-id="7b246-373">Captura de una imagen con la cámara de HoloLens y su almacenamiento en la carpeta de la *aplicación* .</span><span class="sxs-lookup"><span data-stu-id="7b246-373">Capturing an image using the HoloLens camera and storing it in the *App* folder.</span></span>
*   <span data-ttu-id="7b246-374">Controlar los gestos de *TAP* del usuario.</span><span class="sxs-lookup"><span data-stu-id="7b246-374">Handling *Tap* gestures from the user.</span></span>

<span data-ttu-id="7b246-375">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="7b246-375">To create this class:</span></span>

1.  <span data-ttu-id="7b246-376">Vaya a la carpeta scripts que creó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="7b246-376">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="7b246-377">Haga clic con el botón derecho en la carpeta y luego haga clic en **crear** > **script de C\#** .</span><span class="sxs-lookup"><span data-stu-id="7b246-377">Right-click inside the folder, then click **Create** > **C\# Script**.</span></span> <span data-ttu-id="7b246-378">Asigne al script el nombre **ImageCapture**.</span><span class="sxs-lookup"><span data-stu-id="7b246-378">Name the script **ImageCapture**.</span></span>

3.  <span data-ttu-id="7b246-379">Haga doble clic en el nuevo script **ImageCapture** para abrirlo con **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="7b246-379">Double-click on the new **ImageCapture** script to open it with **Visual Studio.**</span></span>

4.  <span data-ttu-id="7b246-380">Reemplace los espacios de nombres en la parte superior del archivo por lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="7b246-380">Replace the namespaces at the top of the file with the following:</span></span>

    ```csharp
    using System;
    using System.IO;
    using System.Linq;
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="7b246-381">A continuación, agregue las siguientes variables dentro de la clase **ImageCapture** , sobre el método **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="7b246-381">Then add the following variables inside the **ImageCapture** class, above the **Start()** method:</span></span>

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

6.  <span data-ttu-id="7b246-382">Ahora es necesario agregar el código para los métodos **activo ()** e **Inicio ()** :</span><span class="sxs-lookup"><span data-stu-id="7b246-382">Code for **Awake()** and **Start()** methods now needs to be added:</span></span>

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

7.  <span data-ttu-id="7b246-383">Implemente un controlador que se llamará cuando se produzca un gesto de punteo:</span><span class="sxs-lookup"><span data-stu-id="7b246-383">Implement a handler that will be called when a Tap gesture occurs:</span></span>

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
    > <span data-ttu-id="7b246-384">Cuando el cursor está en **verde**, significa que la cámara está disponible para tomar la imagen.</span><span class="sxs-lookup"><span data-stu-id="7b246-384">When the cursor is **green**, it means the camera is available to take the image.</span></span> <span data-ttu-id="7b246-385">Cuando el cursor está en **rojo**, significa que la cámara está ocupada.</span><span class="sxs-lookup"><span data-stu-id="7b246-385">When the cursor is **red**, it means the camera is busy.</span></span>

8.  <span data-ttu-id="7b246-386">Agregue el método que usa la aplicación para iniciar el proceso de captura de imagen y almacenar la imagen:</span><span class="sxs-lookup"><span data-stu-id="7b246-386">Add the method that the application uses to start the image capture process and store the image:</span></span>

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

9.  <span data-ttu-id="7b246-387">Agregue los controladores a los que se llamará cuando se haya capturado la foto y cuando esté listo para su análisis.</span><span class="sxs-lookup"><span data-stu-id="7b246-387">Add the handlers that will be called when the photo has been captured and for when it is ready to be analyzed.</span></span> <span data-ttu-id="7b246-388">A continuación, el resultado se pasa a **CustomVisionAnalyser** para su análisis.</span><span class="sxs-lookup"><span data-stu-id="7b246-388">The result is then passed to the **CustomVisionAnalyser** for analysis.</span></span>

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

10. <span data-ttu-id="7b246-389">Asegúrese de guardar los cambios en **Visual Studio**antes de volver a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="7b246-389">Be sure to save your changes in **Visual Studio**, before returning to **Unity**.</span></span>

## <a name="chapter-11---setting-up-the-scripts-in-the-scene"></a><span data-ttu-id="7b246-390">Capítulo 11: configuración de los scripts de la escena</span><span class="sxs-lookup"><span data-stu-id="7b246-390">Chapter 11 - Setting up the scripts in the scene</span></span>

<span data-ttu-id="7b246-391">Ahora que ha escrito todo el código necesario para este proyecto, es el momento de configurar los scripts en la escena y en Prefabs para que se comporten correctamente.</span><span class="sxs-lookup"><span data-stu-id="7b246-391">Now that you have written all of the code necessary for this project, is time to set up the scripts in the scene, and on the prefabs, for them to behave correctly.</span></span>

1.  <span data-ttu-id="7b246-392">Dentro del **Editor de Unity**, en el **Panel jerarquía**, seleccione la **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="7b246-392">Within the **Unity Editor**, in the **Hierarchy Panel**, select the **Main Camera**.</span></span>
2.  <span data-ttu-id="7b246-393">En el **panel Inspector**, con la **cámara principal** seleccionada, haga clic en **Agregar componente**, busque el script **SceneOrganiser** y haga doble clic en, para agregarlo.</span><span class="sxs-lookup"><span data-stu-id="7b246-393">In the **Inspector Panel**, with the **Main Camera** selected, click on **Add Component**, then search for **SceneOrganiser** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-38.png)

3.  <span data-ttu-id="7b246-394">En el **panel Proyecto**, abra la **carpeta Prefabs**, arrastre la **etiqueta** recurso prefabricado al área de entrada de destino de referencia vacía de *etiqueta* , en el script **SceneOrganiser** que acaba de agregar a la *cámara principal*, como se muestra en la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="7b246-394">In the **Project Panel**, open the **Prefabs folder**, drag the **Label** prefab into the *Label* empty reference target input area, in the **SceneOrganiser** script that you have just added to the *Main Camera*, as shown in the image below:</span></span>

    ![](images/AzureLabs-Lab310-39.png)

4.  <span data-ttu-id="7b246-395">En el **Panel jerarquía**, seleccione el elemento secundario **GazeCursor** de la **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="7b246-395">In the **Hierarchy Panel**, select the **GazeCursor** child of the **Main Camera**.</span></span>
5.  <span data-ttu-id="7b246-396">En el **panel Inspector**, con la **GazeCursor** seleccionada, haga clic en **Agregar componente**, busque el script **GazeCursor** y haga doble clic en para agregarlo.</span><span class="sxs-lookup"><span data-stu-id="7b246-396">In the **Inspector Panel**, with the **GazeCursor** selected, click on **Add Component**, then search for **GazeCursor** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-40.png)

6.  <span data-ttu-id="7b246-397">De nuevo, en el **Panel jerarquía**, seleccione el elemento secundario **SpatialMapping** de la **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="7b246-397">Again, in the **Hierarchy Panel**, select the **SpatialMapping** child of the **Main Camera**.</span></span>
7.  <span data-ttu-id="7b246-398">En el **panel Inspector**, con la **SpatialMapping** seleccionada, haga clic en **Agregar componente**, busque el script **SpatialMapping** y haga doble clic en para agregarlo.</span><span class="sxs-lookup"><span data-stu-id="7b246-398">In the **Inspector Panel**, with the **SpatialMapping** selected, click on **Add Component**, then search for **SpatialMapping** script and double-click, to add it.</span></span>

    ![](images/AzureLabs-Lab310-41.png)

<span data-ttu-id="7b246-399">Los scripts restantes que no haya establecido se agregarán mediante el código del script **SceneOrganiser** , durante el tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="7b246-399">The remaining scripts thats you have not set will be added by the code in the **SceneOrganiser** script, during runtime.</span></span>

## <a name="chapter-12---before-building"></a><span data-ttu-id="7b246-400">Capítulo 12: antes de la compilación</span><span class="sxs-lookup"><span data-stu-id="7b246-400">Chapter 12 - Before building</span></span>

<span data-ttu-id="7b246-401">Para realizar una prueba exhaustiva de la aplicación, debe transferirla a Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7b246-401">To perform a thorough test of your application you will need to sideload it onto your Microsoft HoloLens.</span></span>

<span data-ttu-id="7b246-402">Antes de hacerlo, asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="7b246-402">Before you do, ensure that:</span></span>

-  <span data-ttu-id="7b246-403">Toda la configuración mencionada en el [capítulo 3](#chapter-3---set-up-the-unity-project) se establece correctamente.</span><span class="sxs-lookup"><span data-stu-id="7b246-403">All the settings mentioned in the [Chapter 3](#chapter-3---set-up-the-unity-project) are set correctly.</span></span>
- <span data-ttu-id="7b246-404">El script **SceneOrganiser** se adjunta al objeto de **cámara principal** .</span><span class="sxs-lookup"><span data-stu-id="7b246-404">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span>
- <span data-ttu-id="7b246-405">El script **GazeCursor** se adjunta al objeto **GazeCursor** .</span><span class="sxs-lookup"><span data-stu-id="7b246-405">The script **GazeCursor** is attached to the **GazeCursor** object.</span></span>
- <span data-ttu-id="7b246-406">El script **SpatialMapping** se adjunta al objeto **SpatialMapping** .</span><span class="sxs-lookup"><span data-stu-id="7b246-406">The script **SpatialMapping** is attached to the **SpatialMapping** object.</span></span>
- <span data-ttu-id="7b246-407">En el [capítulo 5](#chapter-5---create-the-customvisionanalyser-class), paso 6:</span><span class="sxs-lookup"><span data-stu-id="7b246-407">In [Chapter 5](#chapter-5---create-the-customvisionanalyser-class), Step 6:</span></span>

    - <span data-ttu-id="7b246-408">Asegúrese de insertar la clave de predicción de **servicio** en la variable **predictionKey** .</span><span class="sxs-lookup"><span data-stu-id="7b246-408">Make sure you insert your **Service Prediction Key** into the **predictionKey** variable.</span></span>
    - <span data-ttu-id="7b246-409">Ha insertado el **punto de conexión** de predicción en la clase **predictionEndpoint** .</span><span class="sxs-lookup"><span data-stu-id="7b246-409">You have inserted your **Prediction Endpoint** into the **predictionEndpoint** class.</span></span>

## <a name="chapter-13---build-the-uwp-solution-and-sideload-your-application"></a><span data-ttu-id="7b246-410">Capítulo 13: compilar la solución UWP y transferir localmente la aplicación</span><span class="sxs-lookup"><span data-stu-id="7b246-410">Chapter 13 - Build the UWP solution and sideload your application</span></span>

<span data-ttu-id="7b246-411">Ya está listo para compilar la aplicación como una solución de UWP en la que podrá realizar la implementación en Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7b246-411">You are now ready to build you application as a UWP Solution that you will be able to deploy on to the Microsoft HoloLens.</span></span> <span data-ttu-id="7b246-412">Para comenzar el proceso de compilación:</span><span class="sxs-lookup"><span data-stu-id="7b246-412">To begin the build process:</span></span>

1.  <span data-ttu-id="7b246-413">Vaya a **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="7b246-413">Go to **File > Build Settings**.</span></span>

2.  <span data-ttu-id="7b246-414">Marque **proyectos de\# Unity C**.</span><span class="sxs-lookup"><span data-stu-id="7b246-414">Tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="7b246-415">Haga clic en **Agregar escenas abiertas**.</span><span class="sxs-lookup"><span data-stu-id="7b246-415">Click on **Add Open Scenes**.</span></span> <span data-ttu-id="7b246-416">Esto agregará la escena abierta actualmente a la compilación.</span><span class="sxs-lookup"><span data-stu-id="7b246-416">This will add the currently open scene to the build.</span></span>

    ![](images/AzureLabs-Lab310-42.png)

4.  <span data-ttu-id="7b246-417">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="7b246-417">Click **Build**.</span></span> <span data-ttu-id="7b246-418">Unity iniciará una ventana del *Explorador de archivos* , donde tendrá que crear y seleccionar una carpeta en la que compilar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7b246-418">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="7b246-419">Cree esa carpeta ahora y asígnele el nombre **App**.</span><span class="sxs-lookup"><span data-stu-id="7b246-419">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="7b246-420">Después, con la carpeta de la **aplicación** seleccionada, haga clic en **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="7b246-420">Then with the **App** folder selected, click **Select Folder**.</span></span>

5.  <span data-ttu-id="7b246-421">Unity comenzará a compilar el proyecto en la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="7b246-421">Unity will begin building your project to the **App** folder.</span></span>

6.  <span data-ttu-id="7b246-422">Una vez que Unity termine de compilar (puede tardar algún tiempo), se abrirá una ventana del **Explorador de archivos** en la ubicación de la compilación (Compruebe la barra de tareas, ya que es posible que no aparezca siempre por encima de las ventanas, pero le notificará la adición de una nueva ventana).</span><span class="sxs-lookup"><span data-stu-id="7b246-422">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

7.  <span data-ttu-id="7b246-423">Para realizar la implementación en Microsoft HoloLens, necesitará la dirección IP de ese dispositivo (para la implementación remota) y para asegurarse de que también tiene establecido el **modo de desarrollador** .</span><span class="sxs-lookup"><span data-stu-id="7b246-423">To deploy on to Microsoft HoloLens, you will need the IP Address of that device (for Remote Deploy), and to ensure that it also has **Developer Mode** set.</span></span> <span data-ttu-id="7b246-424">Para ello:</span><span class="sxs-lookup"><span data-stu-id="7b246-424">To do this:</span></span>

    1.  <span data-ttu-id="7b246-425">Mientras se contenga HoloLens, abra la **configuración**.</span><span class="sxs-lookup"><span data-stu-id="7b246-425">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="7b246-426">Vaya a **red &**  > **Opciones avanzadas** **de Wi-Fi** > de Internet</span><span class="sxs-lookup"><span data-stu-id="7b246-426">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="7b246-427">Anote la dirección **IPv4** .</span><span class="sxs-lookup"><span data-stu-id="7b246-427">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="7b246-428">A continuación, vuelva a **configuración**y, a continuación, **actualice & Security** > **para desarrolladores**</span><span class="sxs-lookup"><span data-stu-id="7b246-428">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="7b246-429">Establezca el **modo de desarrollador** *en*.</span><span class="sxs-lookup"><span data-stu-id="7b246-429">Set **Developer Mode** *On*.</span></span>

8.  <span data-ttu-id="7b246-430">Vaya a la nueva compilación de Unity (la carpeta de la **aplicación** ) y abra el archivo de solución con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="7b246-430">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

9.  <span data-ttu-id="7b246-431">En la configuración de soluciones, seleccione Depurar.</span><span class="sxs-lookup"><span data-stu-id="7b246-431">In the Solution Configuration select **Debug**.</span></span>

10. <span data-ttu-id="7b246-432">En la plataforma de la solución, seleccione **x86, equipo remoto**.</span><span class="sxs-lookup"><span data-stu-id="7b246-432">In the Solution Platform, select **x86, Remote Machine**.</span></span> <span data-ttu-id="7b246-433">Se le pedirá que inserte la **dirección IP** de un dispositivo remoto (Microsoft HoloLens, en este caso, que anotó).</span><span class="sxs-lookup"><span data-stu-id="7b246-433">You will be prompted to insert the **IP address** of a remote device (the Microsoft HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab310-43.png)

11. <span data-ttu-id="7b246-434">Vaya al menú compilar y haga clic en **implementar solución** para transferir localmente la aplicación a HoloLens.</span><span class="sxs-lookup"><span data-stu-id="7b246-434">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

12. <span data-ttu-id="7b246-435">La aplicación debe aparecer ahora en la lista de aplicaciones instaladas en Microsoft HoloLens, lista para su lanzamiento.</span><span class="sxs-lookup"><span data-stu-id="7b246-435">Your app should now appear in the list of installed apps on your Microsoft HoloLens, ready to be launched!</span></span>

### <a name="to-use-the-application"></a><span data-ttu-id="7b246-436">Para usar la aplicación:</span><span class="sxs-lookup"><span data-stu-id="7b246-436">To use the application:</span></span>

* <span data-ttu-id="7b246-437">Examine un objeto, que ha entrenado con la Custom Vision Service de **Azure, la detección de objetos**y use el **gesto de TAP**.</span><span class="sxs-lookup"><span data-stu-id="7b246-437">Look at an object, which you have trained with your **Azure Custom Vision Service, Object Detection**, and use the **Tap gesture**.</span></span>
* <span data-ttu-id="7b246-438">Si el objeto se detecta correctamente, aparecerá un texto de *etiqueta* de espacio mundial con el nombre de la etiqueta.</span><span class="sxs-lookup"><span data-stu-id="7b246-438">If the object is successfully detected, a world-space *Label Text* will appear with the tag name.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7b246-439">Cada vez que capture una foto y la envíe al servicio, puede volver a la página de servicio y volver a entrenar el servicio con las imágenes recién capturadas.</span><span class="sxs-lookup"><span data-stu-id="7b246-439">Every time you capture a photo and send it to the Service, you can go back to the Service page and retrain the Service with the newly captured images.</span></span> <span data-ttu-id="7b246-440">Al principio, probablemente también tendrá que corregir los *cuadros de límite* para ser más precisos y volver a entrenar el servicio.</span><span class="sxs-lookup"><span data-stu-id="7b246-440">At the beginning, you will probably also have to correct the *Bounding Boxes* to be more accurate and retrain the Service.</span></span>

> [!NOTE]
> <span data-ttu-id="7b246-441">El texto de la etiqueta que se coloca podría no aparecer cerca del objeto cuando los sensores de Microsoft HoloLens y/o SpatialTrackingComponent en Unity no pueden colocar los colisionadores adecuados, en relación con los objetos reales.</span><span class="sxs-lookup"><span data-stu-id="7b246-441">The Label Text placed might not appear near the object when the Microsoft HoloLens sensors and/or the SpatialTrackingComponent in Unity fails to place the appropriate colliders, relative to the real world objects.</span></span> <span data-ttu-id="7b246-442">Si es así, intente usar la aplicación en una superficie diferente.</span><span class="sxs-lookup"><span data-stu-id="7b246-442">Try to use the application on a different surface if that is the case.</span></span>

## <a name="your-custom-vision-object-detection-application"></a><span data-ttu-id="7b246-443">La aplicación de detección de objetos de Custom Vision</span><span class="sxs-lookup"><span data-stu-id="7b246-443">Your Custom Vision, Object Detection application</span></span>

<span data-ttu-id="7b246-444">Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha el Custom Vision de Azure, la API de detección de objetos, que puede reconocer un objeto de una imagen y, a continuación, proporcionar una posición aproximada para ese objeto en el espacio 3D.</span><span class="sxs-lookup"><span data-stu-id="7b246-444">Congratulations, you built a mixed reality app that leverages the Azure Custom Vision, Object Detection API, which can recognize an object from an image, and then provide an approximate position for that object in 3D space.</span></span>

![](images/AzureLabs-Lab310-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="7b246-445">Ejercicios de bonus</span><span class="sxs-lookup"><span data-stu-id="7b246-445">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="7b246-446">Ejercicio 1</span><span class="sxs-lookup"><span data-stu-id="7b246-446">Exercise 1</span></span>

<span data-ttu-id="7b246-447">Agregando a la etiqueta de texto, use un cubo semitransparente para ajustar el objeto real en un *cuadro de límite*3D.</span><span class="sxs-lookup"><span data-stu-id="7b246-447">Adding to the Text Label, use a semi-transparent cube to wrap the real object in a 3D *Bounding Box*.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="7b246-448">Ejercicio 2</span><span class="sxs-lookup"><span data-stu-id="7b246-448">Exercise 2</span></span>

<span data-ttu-id="7b246-449">Entrenar el Custom Vision Service para reconocer más objetos.</span><span class="sxs-lookup"><span data-stu-id="7b246-449">Train your Custom Vision Service to recognize more objects.</span></span>

### <a name="exercise-3"></a><span data-ttu-id="7b246-450">Ejercicio 3</span><span class="sxs-lookup"><span data-stu-id="7b246-450">Exercise 3</span></span>

<span data-ttu-id="7b246-451">Reproducir un sonido cuando se reconoce un objeto.</span><span class="sxs-lookup"><span data-stu-id="7b246-451">Play a sound when an object is recognized.</span></span>

### <a name="exercise-4"></a><span data-ttu-id="7b246-452">Ejercicio 4</span><span class="sxs-lookup"><span data-stu-id="7b246-452">Exercise 4</span></span>

<span data-ttu-id="7b246-453">Use la API para volver a entrenar su servicio con las mismas imágenes que está analizando la aplicación, para que el servicio sea más preciso (realice la predicción y el entrenamiento simultáneamente).</span><span class="sxs-lookup"><span data-stu-id="7b246-453">Use the API to re-train your Service with the same images your app is analyzing, so to make the Service more accurate (do both prediction and training simultaneously).</span></span>
