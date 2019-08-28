---
title: 'MR y Azure 304: reconocimiento facial'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academia, Unity, tutorial, API, reconocimiento facial, hololens, envolventes, VR
ms.openlocfilehash: 7cd2a6683c80279129934c619a9b9cb857badf67
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047182"
---
>[!NOTE]
><span data-ttu-id="a6bb6-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="a6bb6-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="a6bb6-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="a6bb6-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="a6bb6-108">Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="a6bb6-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-304-face-recognition"></a><span data-ttu-id="a6bb6-110">MR y Azure 304: Reconocimiento facial</span><span class="sxs-lookup"><span data-stu-id="a6bb6-110">MR and Azure 304: Face recognition</span></span>

![resultado de la finalización de este curso](images/AzureLabs-Lab4-00.png)

<span data-ttu-id="a6bb6-112">En este curso aprenderá a agregar funcionalidades de reconocimiento facial a una aplicación de realidad mixta, con Azure Cognitive Services, con el Face API de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-112">In this course you will learn how to add face recognition capabilities to a mixed reality application, using Azure Cognitive Services, with the Microsoft Face API.</span></span>

<span data-ttu-id="a6bb6-113">*Azure Face API* es un servicio de Microsoft, que proporciona a los desarrolladores los algoritmos de caras más avanzados, todo en la nube.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-113">*Azure Face API* is a Microsoft service, which provides developers with the most advanced face algorithms, all in the cloud.</span></span> <span data-ttu-id="a6bb6-114">El *face API* tiene dos funciones principales: detección de caras con atributos y reconocimiento facial.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-114">The *Face API* has two main functions: face detection with attributes, and face recognition.</span></span> <span data-ttu-id="a6bb6-115">Esto permite a los desarrolladores simplemente establecer un conjunto de grupos para caras y, a continuación, enviar imágenes de consulta al servicio más adelante para determinar a quién pertenece una cara.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-115">This allows developers to simply set a set of groups for faces, and then, send query images to the service later, to determine to whom a face belongs.</span></span> <span data-ttu-id="a6bb6-116">Para obtener más información, visite la [Página de reconocimiento facial de Azure](https://azure.microsoft.com/services/cognitive-services/face/).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-116">For more information, visit the [Azure Face Recognition page](https://azure.microsoft.com/services/cognitive-services/face/).</span></span>

<span data-ttu-id="a6bb6-117">Una vez completado este curso, tendrá una aplicación de realidad HoloLens mixta, que podrá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a6bb6-117">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1. <span data-ttu-id="a6bb6-118">Use un **gesto de TAP** para iniciar la captura de una imagen mediante la cámara HoloLens incorporada.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-118">Use a **Tap Gesture** to initiate the capture of an image using the on-board HoloLens camera.</span></span> 
2. <span data-ttu-id="a6bb6-119">Envíe la imagen capturada al servicio *Azure Face API* .</span><span class="sxs-lookup"><span data-stu-id="a6bb6-119">Send the captured image to the *Azure Face API* service.</span></span>
3. <span data-ttu-id="a6bb6-120">Recibir los resultados del algoritmo de *face API* .</span><span class="sxs-lookup"><span data-stu-id="a6bb6-120">Receive the results of the *Face API* algorithm.</span></span>
4. <span data-ttu-id="a6bb6-121">Use una interfaz de usuario simple para mostrar el nombre de las personas coincidentes.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-121">Use a simple User Interface, to display the name of matched people.</span></span>

<span data-ttu-id="a6bb6-122">Esto le enseñará a obtener los resultados del servicio de Face API en la aplicación de realidad mixta basada en Unity.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-122">This will teach you how to get the results from the Face API Service into your Unity-based mixed reality application.</span></span>

<span data-ttu-id="a6bb6-123">En su aplicación, depende del modo en que va a integrar los resultados con el diseño.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="a6bb6-124">Este curso está diseñado para enseñarle a integrar un servicio de Azure con su proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-124">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="a6bb6-125">Es su trabajo usar el conocimiento que obtiene de este curso para mejorar su aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="a6bb6-126">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="a6bb6-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="a6bb6-127">Recurso</span><span class="sxs-lookup"><span data-stu-id="a6bb6-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="a6bb6-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="a6bb6-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="a6bb6-129"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="a6bb6-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="a6bb6-130">MR y Azure 304: Reconocimiento facial</span><span class="sxs-lookup"><span data-stu-id="a6bb6-130">MR and Azure 304: Face recognition</span></span></td><td style="text-align: center;"> <span data-ttu-id="a6bb6-131">✔️</span><span class="sxs-lookup"><span data-stu-id="a6bb6-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="a6bb6-132">✔️</span><span class="sxs-lookup"><span data-stu-id="a6bb6-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="a6bb6-133">Aunque este curso se centra principalmente en HoloLens, también puede aplicar lo que aprenda en este curso a los auriculares con Windows Mixed Reality inmersivo (VR).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="a6bb6-134">Dado que los auriculares envolventes (VR) no tienen cámaras accesibles, necesitará una cámara externa conectada al equipo.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="a6bb6-135">A medida que siga con el curso, verá notas sobre cualquier cambio que deba usar para admitir auriculares envolventes (VR).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a6bb6-136">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="a6bb6-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="a6bb6-137">Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="a6bb6-138">Tenga en cuenta también que los requisitos previos y las instrucciones escritas dentro de este documento representan lo que se ha probado y comprobado en el momento de la escritura (2018 de mayo).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="a6bb6-139">Puede usar el software más reciente, como se indica en el artículo [instalar las herramientas](install-the-tools.md) , aunque no se debe suponer que la información de este curso se ajusta perfectamente a lo que encontrará en el software más reciente que el que se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="a6bb6-140">Se recomienda el siguiente hardware y software para este curso:</span><span class="sxs-lookup"><span data-stu-id="a6bb6-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="a6bb6-141">Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de auriculares envolvente (VR)</span><span class="sxs-lookup"><span data-stu-id="a6bb6-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="a6bb6-142">Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="a6bb6-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="a6bb6-143">El SDK de Windows 10 más reciente</span><span class="sxs-lookup"><span data-stu-id="a6bb6-143">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="a6bb6-144">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="a6bb6-144">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="a6bb6-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="a6bb6-145">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="a6bb6-146">Un [auricular de Windows Mixed Reality inmersivo (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="a6bb6-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="a6bb6-147">Una cámara conectada al equipo (para el desarrollo de auriculares envolvente)</span><span class="sxs-lookup"><span data-stu-id="a6bb6-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="a6bb6-148">Acceso a Internet para la configuración y recuperación de Face API de Azure</span><span class="sxs-lookup"><span data-stu-id="a6bb6-148">Internet access for Azure setup and Face API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="a6bb6-149">Antes de comenzar</span><span class="sxs-lookup"><span data-stu-id="a6bb6-149">Before you start</span></span>

1.  <span data-ttu-id="a6bb6-150">Para evitar que se produzcan problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cerca de la raíz (las rutas de acceso de carpeta largas pueden producir problemas en tiempo de compilación).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="a6bb6-151">Configure y pruebe su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="a6bb6-152">Si necesita ayuda para configurar HoloLens, asegúrese [de visitar el artículo de configuración de hololens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="a6bb6-153">Es una buena idea realizar la calibración y el ajuste del sensor al empezar a desarrollar una nueva aplicación de HoloLens (a veces puede ayudar a realizar esas tareas para cada usuario).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="a6bb6-154">Para obtener ayuda sobre la calibración, siga este [vínculo al artículo sobre la calibración de HoloLens](calibration.md#hololens-2).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="a6bb6-155">Para obtener ayuda sobre la optimización de sensores, siga este [vínculo al artículo sobre la optimización del sensor de HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="a6bb6-156">Capítulo 1: Azure portal</span><span class="sxs-lookup"><span data-stu-id="a6bb6-156">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="a6bb6-157">Para usar el servicio de *face API* en Azure, tendrá que configurar una instancia del servicio para que esté disponible para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-157">To use the *Face API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="a6bb6-158">En primer lugar, inicie sesión en [Azure portal](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="a6bb6-159">Si aún no tiene una cuenta de Azure, tendrá que crear una.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="a6bb6-160">Si sigue este tutorial en una situación de aula o de laboratorio, pregunte al instructor o a uno de los Proctors para obtener ayuda para configurar la nueva cuenta.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="a6bb6-161">Una vez que haya iniciado sesión, haga clic en **nuevo** en la esquina superior izquierda y busque *face API*, presione **entrar**.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-161">Once you are logged in, click on **New** in the top left corner, and search for *Face API*, press **Enter**.</span></span>

    ![búsqueda de facial API](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > <span data-ttu-id="a6bb6-163">Es posible que la palabra **nuevo** se haya reemplazado por **crear un recurso**, en portales más recientes.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="a6bb6-164">La nueva página proporcionará una descripción del servicio *face API* .</span><span class="sxs-lookup"><span data-stu-id="a6bb6-164">The new page will provide a description of the *Face API* service.</span></span> <span data-ttu-id="a6bb6-165">En la parte inferior izquierda de este mensaje, seleccione el botón **crear** para crear una asociación con este servicio.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-165">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![información de la API facial](images/AzureLabs-Lab4-02.png)

4.  <span data-ttu-id="a6bb6-167">Una vez que haya hecho clic en **crear**:</span><span class="sxs-lookup"><span data-stu-id="a6bb6-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="a6bb6-168">Inserte el nombre que desee para esta instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-168">Insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="a6bb6-169">Seleccione una suscripción.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-169">Select a subscription.</span></span>

    3. <span data-ttu-id="a6bb6-170">Seleccione el plan de tarifa adecuado para usted; si es la primera vez que crea un *servicio de Face API*, debe tener a su disposición un nivel gratis (denominado F0).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-170">Select the pricing tier appropriate for you, if this is the first time creating a *Face API Service*, a free tier (named F0) should be available to you.</span></span>

    4. <span data-ttu-id="a6bb6-171">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="a6bb6-172">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="a6bb6-173">Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="a6bb6-174">Si desea leer más información sobre los grupos de recursos de Azure, [visite el artículo sobre el grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="a6bb6-175">La aplicación para UWP, **Person Maker**, que se usa más adelante, requiere el uso de ' oeste de EE. UU. ' en la ubicación.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-175">The UWP app, **Person Maker**, which you use later, requires the use of 'West US' for location.</span></span>

    6. <span data-ttu-id="a6bb6-176">También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-176">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="a6bb6-177">Seleccione **crear\*.**</span><span class="sxs-lookup"><span data-stu-id="a6bb6-177">Select **Create\*.**</span></span>

        ![creación de un servicio facial API](images/AzureLabs-Lab4-03.png)

5.  <span data-ttu-id="a6bb6-179">Una vez que ha hecho clic **crear**\* tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-179">Once you have clicked on **Create\*,** you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="a6bb6-180">Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-180">A notification will appear in the portal once the Service instance is created.</span></span>

    ![notificación de creación de servicio](images/AzureLabs-Lab4-04.png)

7.  <span data-ttu-id="a6bb6-182">Haga clic en las notificaciones para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-182">Click on the notifications to explore your new Service instance.</span></span>

    ![ir a la notificación de recursos](images/AzureLabs-Lab4-05.png)

8.  <span data-ttu-id="a6bb6-184">Cuando esté listo, haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-184">When you are ready, click **Go to resource** button in the notification to explore your new Service instance.</span></span>

    ![acceso a las claves de la API facial](images/AzureLabs-Lab4-06.png)

9.  <span data-ttu-id="a6bb6-186">En este tutorial, la aplicación tendrá que realizar llamadas al servicio, lo que se realiza mediante el uso de la suscripción de su servicio.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-186">Within this tutorial, your application will need to make calls to your service, which is done through using your service's subscription 'key'.</span></span> <span data-ttu-id="a6bb6-187">En la página de *Inicio rápido* , del servicio *face API* , el primer punto es el número 1, para *tomar las claves.*</span><span class="sxs-lookup"><span data-stu-id="a6bb6-187">From the *Quick start* page, of your *Face API* service, the first point is number 1, to *Grab your keys.*</span></span>

10. <span data-ttu-id="a6bb6-188">En la página de *servicio* , seleccione el hipervínculo de **teclas** azules (si se trata de la página inicio rápido) o el vínculo **claves** en el menú de navegación servicios (a la izquierda, indicado por el icono "clave"), para mostrar las claves.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-188">On the *Service* page select either the blue **Keys** hyperlink (if on the Quick start page), or the **Keys** link in the services navigation menu (to the left, denoted by the 'key' icon), to reveal your keys.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="a6bb6-189">Tome nota de cualquiera de las claves y protéjalo, ya que la necesitará más adelante.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-189">Take note of either one of the keys and safeguard it, as you will need it later.</span></span>

## <a name="chapter-2---using-the-person-maker-uwp-application"></a><span data-ttu-id="a6bb6-190">Capítulo 2: uso de la aplicación de UWP ' Person Maker '</span><span class="sxs-lookup"><span data-stu-id="a6bb6-190">Chapter 2 - Using the 'Person Maker' UWP application</span></span>

<span data-ttu-id="a6bb6-191">Asegúrese de descargar la aplicación de UWP precompilada denominada [persona Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-191">Make sure to download the prebuilt UWP Application called [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip).</span></span> <span data-ttu-id="a6bb6-192">Esta aplicación no es el producto final de este curso, solo una herramienta que le ayudará a crear sus entradas de Azure, en las que se basará el proyecto posterior.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-192">This app is not the end product for this course, just a tool to help you create your Azure entries, which the later project will rely upon.</span></span>

<span data-ttu-id="a6bb6-193">**Person Maker** le permite crear entradas de Azure, que están asociadas a personas y grupos de personas.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-193">**Person Maker** allows you to create Azure entries, which are associated with people, and groups of people.</span></span> <span data-ttu-id="a6bb6-194">La aplicación colocará toda la información necesaria en un formato que posteriormente pueda usar el FaceAPI para reconocer las caras de las personas que ha agregado.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-194">The application will place all the needed information in a format which can then later be used by the FaceAPI, in order to recognize the faces of people whom you have added.</span></span> 

> <span data-ttu-id="a6bb6-195">AÚN **Person Maker** usa algunas limitaciones básicas para asegurarse de que no supere el número de llamadas de servicio por minuto para el nivel de **suscripción gratuita**.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-195">[IMPORTANT] **Person Maker** uses some basic throttling, to help ensure that you do not exceed the number of service calls per minute for the **free subscription tier**.</span></span> <span data-ttu-id="a6bb6-196">El texto verde de la parte superior cambiará a rojo y se actualizará como ' activo ' cuando se esté produciendo la limitación; Si este es el caso, simplemente espere a que la aplicación (esperará hasta que pueda seguir accediendo al servicio de caras, actualizando como "en activo" cuando pueda volver a usarla).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-196">The green text at the top will change to red and update as 'ACTIVE' when throttling is happening; if this is the case, simply wait for the application (it will wait until it can next continue accessing the face service, updating as 'IN-ACTIVE' when you can use it again).</span></span>

<span data-ttu-id="a6bb6-197">Esta aplicación usa las bibliotecas *Microsoft. ProjectOxford. facial* , que le permitirán hacer uso completo de los Face API.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-197">This application uses the *Microsoft.ProjectOxford.Face* libraries, which will allow you to make full use of the Face API.</span></span> <span data-ttu-id="a6bb6-198">Esta biblioteca está disponible de forma gratuita como paquete NuGet.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-198">This library is available for free as a NuGet Package.</span></span> <span data-ttu-id="a6bb6-199">Para obtener más información sobre esta y las API similares, asegúrese [de visitar el artículo de referencia de la API](https://docs.microsoft.com/azure/cognitive-services/face/apireference).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-199">For more information about this, and similar, APIs [make sure to visit the API reference article](https://docs.microsoft.com/azure/cognitive-services/face/apireference).</span></span>

> [!NOTE] 
> <span data-ttu-id="a6bb6-200">Estos son solo los pasos necesarios, las instrucciones sobre cómo realizar estas acciones se encuentran en el documento.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-200">These are just the steps required, instructions for how to do these things is further down the document.</span></span> <span data-ttu-id="a6bb6-201">La aplicación **creador de personas** le permitirá:</span><span class="sxs-lookup"><span data-stu-id="a6bb6-201">The **Person Maker** app will allow you to:</span></span>
>
> - <span data-ttu-id="a6bb6-202">Cree un *grupo de personas*, que es un grupo compuesto por varias personas a las que desea asociarla.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-202">Create a *Person Group*, which is a group composed of several people which you want to associate with it.</span></span> <span data-ttu-id="a6bb6-203">Con su cuenta de Azure, puede hospedar varios grupos de personas.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-203">With your Azure account you can host multiple Person Groups.</span></span>
>
> - <span data-ttu-id="a6bb6-204">Cree una *persona*, que sea miembro de un grupo de personas.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-204">Create a *Person*, which is a member of a Person Group.</span></span> <span data-ttu-id="a6bb6-205">Cada persona tiene varias imágenes de *caras* asociadas.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-205">Each person has a number of *Face* images associated with it.</span></span>
>
> -  <span data-ttu-id="a6bb6-206">Asigne *imágenes faciales* a una *persona*, para permitir que el servicio Azure Face API reconozca a una *persona* por la *esfera*correspondiente.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-206">Assign *face images* to a *Person*, to allow your Azure Face API Service to recognize a *Person* by the corresponding *face*.</span></span>
>
> -  <span data-ttu-id="a6bb6-207">*Entrenar* su *servicio Azure Face API*.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-207">*Train* your *Azure Face API Service*.</span></span>

<span data-ttu-id="a6bb6-208">Tenga en cuenta que, para entrenar a esta aplicación para que reconozca a los usuarios, necesitará diez (10) fotos próximas de cada persona que le gustaría agregar a su grupo de personas.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-208">Be aware, so to train this app to recognize people, you will need ten (10) close-up photos of each person which you would like to add to your Person Group.</span></span> <span data-ttu-id="a6bb6-209">La aplicación CAM de Windows 10 puede ayudarle a tomarlos.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-209">The Windows 10 Cam App can help you to take these.</span></span> <span data-ttu-id="a6bb6-210">Debe asegurarse de que cada foto esté clara (Evite Desenfocar, ocultar o estar demasiado lejos, del asunto), tener la foto en formato de archivo jpg o PNG, con un tamaño de archivo de imagen no mayor de **4 MB**y no inferior a **1 KB**.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-210">You must ensure that each photo is clear (avoid blurring, obscuring, or being too far, from the subject), have the photo in jpg or png file format, with the image file size being no larger **4 MB**, and no less than **1 KB**.</span></span>

> [!NOTE]
> <span data-ttu-id="a6bb6-211">Si sigue este tutorial, no use su propio aspecto para el entrenamiento, al igual que cuando se coloca HoloLens en, no se puede ver.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-211">If you are following this tutorial, do not use your own face for training, as when you put the HoloLens on, you cannot look at yourself.</span></span> <span data-ttu-id="a6bb6-212">Usar el aspecto de un colega o de un estudiante.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-212">Use the face of a colleague or fellow student.</span></span>

<span data-ttu-id="a6bb6-213">Encargado de la ejecución de la **persona**:</span><span class="sxs-lookup"><span data-stu-id="a6bb6-213">Running **Person Maker**:</span></span>

1.  <span data-ttu-id="a6bb6-214">Abra la carpeta **PersonMaker** y haga doble clic en la *solución PersonMaker* para abrirla con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-214">Open the **PersonMaker** folder and double click on the *PersonMaker solution* to open it with *Visual Studio*.</span></span>

2.  <span data-ttu-id="a6bb6-215">Una vez abierta la *solución PersonMaker* , asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="a6bb6-215">Once the *PersonMaker solution* is open, make sure that:</span></span>

    1. <span data-ttu-id="a6bb6-216">La *configuración* de la solución estáestablecida en depurar.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-216">The *Solution Configuration* is set to **Debug**.</span></span>

    2. <span data-ttu-id="a6bb6-217">La *plataforma* de la solución está establecida en **x86**</span><span class="sxs-lookup"><span data-stu-id="a6bb6-217">The *Solution Platform* is set to **x86**</span></span>

    3. <span data-ttu-id="a6bb6-218">La *plataforma de destino* es la **máquina local**.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-218">The *Target Platform* is **Local Machine**.</span></span>

    4.  <span data-ttu-id="a6bb6-219">También es posible que necesite *restaurar paquetes Nuget* (haga clic con el botón derecho en la *solución* y seleccione **restaurar paquetes Nuget**).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-219">You also may need to *Restore NuGet Packages* (right-click the *Solution* and select **Restore NuGet Packages**).</span></span>

3.  <span data-ttu-id="a6bb6-220">Haga clic en *equipo local* y se iniciará la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-220">Click *Local Machine* and the application will start.</span></span> <span data-ttu-id="a6bb6-221">Tenga en cuenta que, en pantallas más pequeñas, todo el contenido puede no estar visible, aunque puede desplazarse hacia abajo para verlo.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-221">Be aware, on smaller screens, all content may not be visible, though you can scroll further down to view it.</span></span>

    ![interfaz de usuario de creador de personas](images/AzureLabs-Lab4-07.png)

4.  <span data-ttu-id="a6bb6-223">Inserte su **clave de autenticación de Azure**, que debe tener, desde el servicio de *face API* dentro de Azure.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-223">Insert your **Azure Authentication Key**, which you should have, from your *Face API* service within Azure.</span></span>

5.  <span data-ttu-id="a6bb6-224">Introducir</span><span class="sxs-lookup"><span data-stu-id="a6bb6-224">Insert:</span></span>

    1. <span data-ttu-id="a6bb6-225">El *identificador* que desea asignar al *Grupo Person*.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-225">The *ID* you want to assign to the *Person Group*.</span></span> <span data-ttu-id="a6bb6-226">El identificador debe estar en minúsculas, sin espacios en blanco.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-226">The ID must be lowercase, with no spaces.</span></span> <span data-ttu-id="a6bb6-227">Tome nota de este identificador, ya que será necesario más adelante en el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-227">Make note of this ID, as it will be required later in your Unity project.</span></span>
    2. <span data-ttu-id="a6bb6-228">El *nombre* que desea asignar al *Grupo Person* (puede tener espacios).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-228">The *Name* you want to assign to the *Person Group* (can have spaces).</span></span>


6.  <span data-ttu-id="a6bb6-229">Presione el botón **Crear grupo de personas** .</span><span class="sxs-lookup"><span data-stu-id="a6bb6-229">Press **Create Person Group** button.</span></span> <span data-ttu-id="a6bb6-230">Debe aparecer un mensaje de confirmación debajo del botón.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-230">A confirmation message should appear underneath the button.</span></span>

> [!NOTE]
> <span data-ttu-id="a6bb6-231">Si tiene un error de "acceso denegado", Compruebe la ubicación que estableció para el servicio de Azure.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-231">If you have an 'Access Denied' error, check the location you set for your Azure service.</span></span> <span data-ttu-id="a6bb6-232">Como se indicó anteriormente, esta aplicación está diseñada para ' oeste de EE. UU. '.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-232">As stated above, this app is designed for 'West US'.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a6bb6-233">Observará que también puede hacer clic en el botón **capturar un grupo conocido** : es para si ya ha creado un grupo de personas y desea usarlo, en lugar de crear uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-233">You will notice that you can also click the **Fetch a Known Group** button: this is for if you have already created a person group, and wish to use that, rather than create a new one.</span></span> <span data-ttu-id="a6bb6-234">Tenga en cuenta que, si hace clic en *crear un grupo de personas* con un grupo conocido, también se recuperará un grupo.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-234">Be aware, if you click *Create a Person Group* with a known group, this will also fetch a group.</span></span>

7.  <span data-ttu-id="a6bb6-235">Inserte el *nombre* de la *persona* que desea crear.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-235">Insert the *Name* of the *Person* you want to create.</span></span>

    1. <span data-ttu-id="a6bb6-236">Haga clic en el botón **crear persona** .</span><span class="sxs-lookup"><span data-stu-id="a6bb6-236">Click the **Create Person** button.</span></span>

    2. <span data-ttu-id="a6bb6-237">Debe aparecer un mensaje de confirmación debajo del botón.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-237">A confirmation message should appear underneath the button.</span></span>

    3. <span data-ttu-id="a6bb6-238">Si desea eliminar una persona que ha creado anteriormente, puede escribir el nombre en el cuadro de texto y presionar **eliminar persona**</span><span class="sxs-lookup"><span data-stu-id="a6bb6-238">If you wish to delete a person you have previously created, you can write the name into the textbox and press **Delete Person**</span></span>

8.  <span data-ttu-id="a6bb6-239">Asegúrese de que conoce la ubicación de diez (10) fotos de la persona que desea agregar al grupo.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-239">Make sure you know the location of ten (10) photos of the person you would like to add to your group.</span></span>

9.  <span data-ttu-id="a6bb6-240">Presione **crear y abrir carpeta** para abrir el explorador de Windows en la carpeta asociada a la persona.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-240">Press **Create and Open Folder** to open Windows Explorer to the folder associated to the person.</span></span> <span data-ttu-id="a6bb6-241">Agregue las diez (10) imágenes en la carpeta.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-241">Add the ten (10) images in the folder.</span></span> <span data-ttu-id="a6bb6-242">Deben ser del formato de archivo *jpg* o *PNG* .</span><span class="sxs-lookup"><span data-stu-id="a6bb6-242">These must be of *JPG* or *PNG* file format.</span></span>

10. <span data-ttu-id="a6bb6-243">Haga clic en **Enviar a Azure**.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-243">Click on **Submit To Azure**.</span></span> <span data-ttu-id="a6bb6-244">Un contador mostrará el estado del envío, seguido de un mensaje cuando se haya completado.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-244">A counter will show you the state of the submission, followed by a message when it has completed.</span></span>

11. <span data-ttu-id="a6bb6-245">Una vez que el contador ha finalizado y se ha mostrado un mensaje de confirmación, haga clic en **entrenar** para entrenar su servicio.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-245">Once the counter has finished and a confirmation message has been displayed click on **Train** to train your Service.</span></span>

<span data-ttu-id="a6bb6-246">Una vez completado el proceso, está listo para pasar a Unity.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-246">Once the process has completed, you are ready to move into Unity.</span></span>

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="a6bb6-247">Capítulo 3: configuración del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="a6bb6-247">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="a6bb6-248">Lo siguiente es una configuración típica para desarrollar con la realidad mixta y, como tal, es una buena plantilla para otros proyectos.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-248">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="a6bb6-249">Abra *Unity* y haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-249">Open *Unity* and click **New**.</span></span> 

    ![Inicie el nuevo proyecto de Unity.](images/AzureLabs-Lab4-08.png)

2.  <span data-ttu-id="a6bb6-251">Ahora tendrá que proporcionar un nombre de proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-251">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="a6bb6-252">Inserte **MR_FaceRecognition**.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-252">Insert **MR_FaceRecognition**.</span></span> <span data-ttu-id="a6bb6-253">Asegúrese de que el tipo de proyecto está establecido en **3D**.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-253">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="a6bb6-254">Establezca la **Ubicación** en algún lugar adecuado para usted (Recuerde que, más cerca de los directorios raíz es mejor).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-254">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="a6bb6-255">A continuación, haga clic en **crear proyecto**.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-255">Then, click **Create project**.</span></span>

    ![Proporcione los detalles del nuevo proyecto de Unity.](images/AzureLabs-Lab4-09.png)

3.  <span data-ttu-id="a6bb6-257">Con Unity abierto, merece la pena comprobar que el **Editor** de scripts predeterminado está establecido en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-257">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="a6bb6-258">Vaya a **editar > preferencias** y, a continuación, en la nueva ventana, vaya a **herramientas externas**.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-258">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="a6bb6-259">Cambie el **Editor de script externo** a **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-259">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="a6bb6-260">Cierre la ventana **preferencias** .</span><span class="sxs-lookup"><span data-stu-id="a6bb6-260">Close the **Preferences** window.</span></span>

    ![Actualice las preferencias del editor de scripts.](images/AzureLabs-Lab4-10.png)

4.  <span data-ttu-id="a6bb6-262">A continuación, vaya a **archivo > configuración de compilación** y cambie la plataforma a **plataforma universal de Windows**, haciendo clic en el botón **cambiar plataforma** .</span><span class="sxs-lookup"><span data-stu-id="a6bb6-262">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Ventana Configuración de compilación, cambiar plataforma a UWP.](images/AzureLabs-Lab4-11.png)

5.  <span data-ttu-id="a6bb6-264">Vaya a **archivo > configuración de compilación** y asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="a6bb6-264">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="a6bb6-265">El **dispositivo de destino** está establecido en **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="a6bb6-265">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="a6bb6-266">Para los auriculares envolventes, establezca el **dispositivo de destino** en *cualquier dispositivo*.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-266">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="a6bb6-267">El **tipo de compilación** se establece en **D3D**</span><span class="sxs-lookup"><span data-stu-id="a6bb6-267">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="a6bb6-268">**SDK** está establecido en la **versión más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="a6bb6-268">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="a6bb6-269">La **versión de Visual Studio** está establecida en la **más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="a6bb6-269">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="a6bb6-270">**Compilar y ejecutar** está establecido en **equipo local**</span><span class="sxs-lookup"><span data-stu-id="a6bb6-270">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="a6bb6-271">Guarde la escena y agréguela a la compilación.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-271">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="a6bb6-272">Para ello, seleccione **Agregar escenas abiertas**.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-272">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="a6bb6-273">Aparecerá una ventana de guardar.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-273">A save window will appear.</span></span>

            ![Haga clic en el botón Agregar escenas abiertas](images/AzureLabs-Lab4-12.png)

        2. <span data-ttu-id="a6bb6-275">Seleccione el botón **nueva carpeta** para crear una nueva carpeta, asígnele el nombre **Scenes**.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-275">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Crear nueva carpeta de scripts](images/AzureLabs-Lab4-13.png)

        3. <span data-ttu-id="a6bb6-277">Abra la carpeta Scenes recién creada y, a continuación, en el campo **nombre de archivo**:, escriba **FaceRecScene**y, a continuación, presione **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-277">Open your newly created **Scenes** folder, and then in the **File name**: text field, type **FaceRecScene**, then press **Save**.</span></span>

            ![Asigne un nombre a la nueva escena.](images/AzureLabs-Lab4-14.png)

    7. <span data-ttu-id="a6bb6-279">El resto de la configuración, en la *configuración de compilación*, debe dejarse como predeterminada por ahora.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-279">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="a6bb6-280">En la ventana *configuración de compilación* , haga clic en el botón Configuración del **reproductor** ; se abrirá el panel relacionado en el espacio donde se encuentra el *Inspector* .</span><span class="sxs-lookup"><span data-stu-id="a6bb6-280">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Abra configuración del reproductor.](images/AzureLabs-Lab4-15.png)

7. <span data-ttu-id="a6bb6-282">En este panel, deben comprobarse algunas opciones de configuración:</span><span class="sxs-lookup"><span data-stu-id="a6bb6-282">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="a6bb6-283">En la pestaña **otros valores** :</span><span class="sxs-lookup"><span data-stu-id="a6bb6-283">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="a6bb6-284">**Scripting** La **versión del tiempo de ejecución** debe ser **Experimental** (.net 4,6 equivalente).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-284">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent).</span></span> <span data-ttu-id="a6bb6-285">Al cambiar esto se desencadenará la necesidad de reiniciar el editor.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-285">Changing this will trigger a need to restart the Editor.</span></span>
        2. <span data-ttu-id="a6bb6-286">El **back-end** de scripting debe ser **.net**</span><span class="sxs-lookup"><span data-stu-id="a6bb6-286">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="a6bb6-287">El **nivel de compatibilidad de API** debe ser **.net 4,6**</span><span class="sxs-lookup"><span data-stu-id="a6bb6-287">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Actualice otras opciones de configuración.](images/AzureLabs-Lab4-16.png)
      
    2. <span data-ttu-id="a6bb6-289">En la pestaña **configuración de publicación** , en **capacidades**, seleccione:</span><span class="sxs-lookup"><span data-stu-id="a6bb6-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="a6bb6-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="a6bb6-290">**InternetClient**</span></span>
        - <span data-ttu-id="a6bb6-291">**Web**</span><span class="sxs-lookup"><span data-stu-id="a6bb6-291">**Webcam**</span></span>

            ![Actualizando la configuración de publicación.](images/AzureLabs-Lab4-17.png)

    3. <span data-ttu-id="a6bb6-293">Más abajo en el panel, en la **configuración de XR** (se encuentra debajo de **configuración de publicación**), tick **Virtual Reality compatible**, asegúrese de que se agrega el **SDK de Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="a6bb6-293">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Actualice la configuración de X R.](images/AzureLabs-Lab4-18.png)

8.  <span data-ttu-id="a6bb6-295">De nuevo en la *configuración de compilación*, los **proyectos de Unity C#**  ya no están atenuados; Marque la casilla situada junto a este.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-295">Back in *Build Settings*, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="a6bb6-296">Cierre la ventana Configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-296">Close the Build Settings window.</span></span>
10. <span data-ttu-id="a6bb6-297">Guarde la escena y el proyecto (**archivo > guardar la escena o el archivo > guardar proyecto**).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-297">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4---main-camera-setup"></a><span data-ttu-id="a6bb6-298">Capítulo 4: configuración de la cámara principal</span><span class="sxs-lookup"><span data-stu-id="a6bb6-298">Chapter 4 - Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a6bb6-299">Si desea omitir el componente de *configuración de Unity* de este curso y continuar directamente en el código, no dude en [Descargar este. unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)e importarlo en el proyecto como un [paquete personalizado](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-299">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="a6bb6-300">Tenga en cuenta que este paquete también incluye la importación del *archivo dll de Newtonsoft*, que se describe en el [capítulo 5](#chapter-5--import-the-newtonsoftjson-library).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-300">Be aware that this package also includes the import of the *Newtonsoft DLL*, covered in [Chapter 5](#chapter-5--import-the-newtonsoftjson-library).</span></span> <span data-ttu-id="a6bb6-301">Con esta importación, puede continuar en el [capítulo 6](#chapter-6---create-the-faceanalysis-class).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-301">With this imported, you can continue from [Chapter 6](#chapter-6---create-the-faceanalysis-class).</span></span>

1.  <span data-ttu-id="a6bb6-302">En el panel *jerarquía* , seleccione la **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-302">In the *Hierarchy* Panel, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="a6bb6-303">Una vez seleccionado, podrá ver todos los componentes de la **cámara principal** en el *panel del inspector*.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-303">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="a6bb6-304">El **objeto de cámara** debe tener el nombre de la **cámara principal** (tenga en cuenta la ortografía).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-304">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2. <span data-ttu-id="a6bb6-305">La **etiqueta** de cámara principal se debe establecer en **MainCamera** (tenga en cuenta la ortografía).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-305">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3. <span data-ttu-id="a6bb6-306">Asegúrese de que la **posición de transformación** está establecida en **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="a6bb6-306">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4. <span data-ttu-id="a6bb6-307">Establecer **marcas** de borrado en **color sólido**</span><span class="sxs-lookup"><span data-stu-id="a6bb6-307">Set **Clear Flags** to **Solid Color**</span></span>

    5. <span data-ttu-id="a6bb6-308">Establezca el color de **fondo** del componente de la cámara en **negro, alfa 0 (código hexadecimal: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="a6bb6-308">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

        ![configuración de componentes de cámara](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a><span data-ttu-id="a6bb6-310">Capítulo 5: importar la biblioteca Newtonsoft. JSON</span><span class="sxs-lookup"><span data-stu-id="a6bb6-310">Chapter 5 – Import the Newtonsoft.Json library</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a6bb6-311">Si importó el ". unitypackage Tools" en el [último capítulo](#chapter-4---main-camera-setup), puede omitir este capítulo.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-311">If you imported the '.unitypackage' in the [last Chapter](#chapter-4---main-camera-setup), you can skip this Chapter.</span></span>

<span data-ttu-id="a6bb6-312">Para ayudarle a deserializar y serializar los objetos recibidos y enviados al servicio de bot, debe descargar la biblioteca *Newtonsoft. JSON* .</span><span class="sxs-lookup"><span data-stu-id="a6bb6-312">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the *Newtonsoft.Json* library.</span></span> <span data-ttu-id="a6bb6-313">Encontrará una versión compatible ya organizada con la estructura de carpetas de Unity correcta en este [archivo de paquete de Unity](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-313">You will find a compatible version already organized with the correct Unity folder structure in this [Unity package file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="a6bb6-314">Para importar la biblioteca:</span><span class="sxs-lookup"><span data-stu-id="a6bb6-314">To import the library:</span></span>

1.  <span data-ttu-id="a6bb6-315">Descargue el paquete de Unity.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-315">Download the Unity Package.</span></span>
2.  <span data-ttu-id="a6bb6-316">Haga clic en **activos**, **importar paquete**, **paquete personalizado**.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-316">Click on **Assets**, **Import Package**, **Custom Package**.</span></span>

    ![Importación de la biblioteca Newtonsoft. JSON](images/AzureLabs-Lab4-20.png)

3.  <span data-ttu-id="a6bb6-318">Busque el paquete de Unity que ha descargado y haga clic en abrir.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-318">Look for the Unity Package you have downloaded, and click Open.</span></span>
4.  <span data-ttu-id="a6bb6-319">Asegúrese de que todos los componentes del paquete estén marcados y haga clic en **importar**.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-319">Make sure all the components of the package are ticked and click **Import**.</span></span>

    ![Importación de la biblioteca Newtonsoft. JSON](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a><span data-ttu-id="a6bb6-321">Capítulo 6: crear la clase FaceAnalysis</span><span class="sxs-lookup"><span data-stu-id="a6bb6-321">Chapter 6 - Create the FaceAnalysis class</span></span>

<span data-ttu-id="a6bb6-322">El propósito de la clase FaceAnalysis es hospedar los métodos necesarios para comunicarse con el servicio de reconocimiento facial de Azure.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-322">The purpose of the FaceAnalysis class is to host the methods necessary to communicate with your Azure Face Recognition Service.</span></span> 

- <span data-ttu-id="a6bb6-323">Después de enviar el servicio a una imagen de captura, se lo analizará e identificará las caras dentro de y determinará si alguna pertenece a una persona conocida.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-323">After sending the service a capture image, it will analyse it and identify the faces within, and determine if any belong to a known person.</span></span> 
- <span data-ttu-id="a6bb6-324">Si se encuentra una persona conocida, esta clase mostrará su nombre como texto de la interfaz de usuario en la escena.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-324">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="a6bb6-325">Para crear la clase *FaceAnalysis* :</span><span class="sxs-lookup"><span data-stu-id="a6bb6-325">To create the *FaceAnalysis* class:</span></span>

 1. <span data-ttu-id="a6bb6-326">Haga clic con el botón derecho en la *carpeta activos* que se encuentra en el panel Proyecto y, a continuación, haga clic en **crear** > **carpeta**.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-326">Right-click in the *Assets Folder* located in the Project Panel, then click on **Create** > **Folder**.</span></span> <span data-ttu-id="a6bb6-327">Llame a los **scripts**de la carpeta.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-327">Call the folder **Scripts**.</span></span> 

    ![Cree la clase FaceAnalysis.](images/AzureLabs-Lab4-22.png)

2.  <span data-ttu-id="a6bb6-329">Haga doble clic en la carpeta que acaba de crear para abrirla.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-329">Double click on the folder just created, to open it.</span></span> 
3.  <span data-ttu-id="a6bb6-330">Haga clic con el botón derecho en la carpeta y después haga clic en **crear**  >   **C# script**.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-330">Right-click inside the folder, then click on **Create** > **C# Script**.</span></span> <span data-ttu-id="a6bb6-331">Llame al script *FaceAnalysis*.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-331">Call the script *FaceAnalysis*.</span></span> 
4.  <span data-ttu-id="a6bb6-332">Haga doble clic en el nuevo script *FaceAnalysis* para abrirlo con Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-332">Double click on the new *FaceAnalysis* script to open it with Visual Studio 2017.</span></span>
5.  <span data-ttu-id="a6bb6-333">Escriba los siguientes espacios de nombres encima de la clase *FaceAnalysis* :</span><span class="sxs-lookup"><span data-stu-id="a6bb6-333">Enter the following namespaces above the *FaceAnalysis* class:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="a6bb6-334">Ahora debe agregar todos los objetos que se usan para deserialising.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-334">You now need to add all of the objects which are used for deserialising.</span></span> <span data-ttu-id="a6bb6-335">Estos objetos deben agregarse **fuera** del script *FaceAnalysis* (debajo del corchete de cierre).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-335">These objects need to be added **outside** of the *FaceAnalysis* script (beneath the bottom curly bracket).</span></span> 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. <span data-ttu-id="a6bb6-336">No se usarán los métodos *Start ()* y *Update ()* , así que elimínelos ahora.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-336">The *Start()* and *Update()* methods will not be used, so delete them now.</span></span> 

8.  <span data-ttu-id="a6bb6-337">Dentro de la clase *FaceAnalysis* , agregue las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="a6bb6-337">Inside the *FaceAnalysis* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > <span data-ttu-id="a6bb6-338">Reemplace la **clave** y el **PersonGroupId** por la clave de servicio y el identificador del grupo que creó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-338">Replace the **key** and the **personGroupId** with your Service Key and the Id of the group that you created previously.</span></span>

9.  <span data-ttu-id="a6bb6-339">Agregue el método *activo ()* , que inicializa la clase, agregando la clase *ImageCapture* a la cámara principal y llama al método de creación de la etiqueta:</span><span class="sxs-lookup"><span data-stu-id="a6bb6-339">Add the *Awake()* method, which initialises the class, adding the *ImageCapture* class to the Main Camera and calls the Label creation method:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. <span data-ttu-id="a6bb6-340">Agregue el método *CreateLabel ()* , que crea el objeto de *etiqueta* para mostrar el resultado del análisis:</span><span class="sxs-lookup"><span data-stu-id="a6bb6-340">Add the *CreateLabel()* method, which creates the *Label* object to display the analysis result:</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. <span data-ttu-id="a6bb6-341">Agregue el método *DetectFacesFromImage ()* y *GetImageAsByteArray ()* .</span><span class="sxs-lookup"><span data-stu-id="a6bb6-341">Add the *DetectFacesFromImage()* and *GetImageAsByteArray()* method.</span></span> <span data-ttu-id="a6bb6-342">La primera solicitud solicitará al servicio de reconocimiento facial que detecte cualquier posible aspecto en la imagen enviada, mientras que la última es necesaria para convertir la imagen capturada en una matriz de bytes:</span><span class="sxs-lookup"><span data-stu-id="a6bb6-342">The former will request the Face Recognition Service to detect any possible face in the submitted image, while the latter is necessary to convert the captured image into a bytes array:</span></span>

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. <span data-ttu-id="a6bb6-343">Agregue el método *IdentifyFaces ()* , que solicita al *servicio de reconocimiento facial* que identifique cualquier aspecto conocido detectado anteriormente en la imagen enviada.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-343">Add the *IdentifyFaces()* method, which requests the *Face Recognition Service* to identify any known face previously detected in the submitted image.</span></span> <span data-ttu-id="a6bb6-344">La solicitud devolverá un identificador de la persona identificada, pero no el nombre:</span><span class="sxs-lookup"><span data-stu-id="a6bb6-344">The request will return an id of the identified person but not the name:</span></span>

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialise to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. <span data-ttu-id="a6bb6-345">Agregue el método *GetPerson ()* .</span><span class="sxs-lookup"><span data-stu-id="a6bb6-345">Add the *GetPerson()* method.</span></span> <span data-ttu-id="a6bb6-346">Al proporcionar el identificador de persona, este método solicita al *servicio de reconocimiento facial* que devuelva el nombre de la persona identificada:</span><span class="sxs-lookup"><span data-stu-id="a6bb6-346">By providing the person id, this method then requests for the *Face Recognition Service* to return the name of the identified person:</span></span>

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  <span data-ttu-id="a6bb6-347">Recuerde **Guardar** los cambios antes de volver al editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-347">Remember to **Save** the changes before going back to the Unity Editor.</span></span>
15.  <span data-ttu-id="a6bb6-348">En el editor de Unity, arrastre el script FaceAnalysis desde la carpeta scripts del panel Proyecto hasta el objeto cámara principal en el *Panel jerarquía*.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-348">In the Unity Editor, drag the FaceAnalysis script from the Scripts folder in Project panel to the Main Camera object in the *Hierarchy panel*.</span></span> <span data-ttu-id="a6bb6-349">El nuevo componente de script se agregará a la cámara principal.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-349">The new script component will be so added to the Main Camera.</span></span> 

![Colocar FaceAnalysis en la cámara principal](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a><span data-ttu-id="a6bb6-351">Capítulo 7: creación de la clase ImageCapture</span><span class="sxs-lookup"><span data-stu-id="a6bb6-351">Chapter 7 - Create the ImageCapture class</span></span>

<span data-ttu-id="a6bb6-352">El propósito de la clase *ImageCapture* es hospedar los métodos necesarios para comunicarse con el *servicio de reconocimiento facial de Azure* para analizar la imagen que se va a capturar, identificar caras y determinar si pertenece a una persona conocida.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-352">The purpose of the *ImageCapture* class is to host the methods necessary to communicate with your *Azure Face Recognition Service* to analyse the image you will capture, identifying faces in it and determining if it belongs to a known person.</span></span> <span data-ttu-id="a6bb6-353">Si se encuentra una persona conocida, esta clase mostrará su nombre como texto de la interfaz de usuario en la escena.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-353">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="a6bb6-354">Para crear la clase *ImageCapture* :</span><span class="sxs-lookup"><span data-stu-id="a6bb6-354">To create the *ImageCapture* class:</span></span>
 
1.  <span data-ttu-id="a6bb6-355">Haga clic con el botón derecho dentro de la carpeta scripts que ha creado anteriormente y, a continuación, haga clic en **crear**,  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-355">Right-click inside the **Scripts** folder you have created previously, then click on **Create**, **C# Script**.</span></span> <span data-ttu-id="a6bb6-356">Llame al script *ImageCapture*.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-356">Call the script *ImageCapture*.</span></span> 
2.  <span data-ttu-id="a6bb6-357">Haga doble clic en el nuevo script *ImageCapture* para abrirlo con Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-357">Double click on the new *ImageCapture* script to open it with Visual Studio 2017.</span></span>
3.  <span data-ttu-id="a6bb6-358">Escriba los siguientes espacios de nombres encima de la clase ImageCapture:</span><span class="sxs-lookup"><span data-stu-id="a6bb6-358">Enter the following namespaces above the ImageCapture class:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  <span data-ttu-id="a6bb6-359">Dentro de la clase *ImageCapture* , agregue las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="a6bb6-359">Inside the *ImageCapture* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  <span data-ttu-id="a6bb6-360">Agregue los métodos *activo ()* e *Inicio ()* necesarios para inicializar la clase y permitir que HoloLens Capture los gestos del usuario:</span><span class="sxs-lookup"><span data-stu-id="a6bb6-360">Add the *Awake()* and *Start()* methods necessary to initialise the class and allow the HoloLens to capture the user's gestures:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  <span data-ttu-id="a6bb6-361">Agregue *TapHandler (),* al que se llama cuando el usuario realiza un gesto de *TAP* :</span><span class="sxs-lookup"><span data-stu-id="a6bb6-361">Add the *TapHandler()* which is called when the user performs a *Tap* gesture:</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  <span data-ttu-id="a6bb6-362">Agregue el método *ExecuteImageCaptureAndAnalysis ()* , que iniciará el proceso de captura de imágenes:</span><span class="sxs-lookup"><span data-stu-id="a6bb6-362">Add the *ExecuteImageCaptureAndAnalysis()* method, which will begin the process of Image Capturing:</span></span>

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  <span data-ttu-id="a6bb6-363">Agregue los controladores a los que se llama cuando se ha completado el proceso de captura de fotografías:</span><span class="sxs-lookup"><span data-stu-id="a6bb6-363">Add the handlers that are called when the photo capture process has been completed:</span></span>

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successfull, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. <span data-ttu-id="a6bb6-364">Recuerde **Guardar** los cambios antes de volver al editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-364">Remember to **Save** the changes before going back to the Unity Editor.</span></span>

## <a name="chapter-8---building-the-solution"></a><span data-ttu-id="a6bb6-365">Capítulo 8: compilar la solución</span><span class="sxs-lookup"><span data-stu-id="a6bb6-365">Chapter 8 - Building the solution</span></span>

<span data-ttu-id="a6bb6-366">Para realizar una prueba exhaustiva de la aplicación, debe transferirla a su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-366">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="a6bb6-367">Antes de hacerlo, asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="a6bb6-367">Before you do, ensure that:</span></span>

-   <span data-ttu-id="a6bb6-368">Toda la configuración mencionada en el capítulo 3 se establece correctamente.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-368">All the settings mentioned in the Chapter 3 are set correctly.</span></span> 
-   <span data-ttu-id="a6bb6-369">El script *FaceAnalysis* se adjunta al objeto de cámara principal.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-369">The script *FaceAnalysis* is attached to the Main Camera object.</span></span> 
-   <span data-ttu-id="a6bb6-370">La **clave de autenticación** y el ID. de **Grupo** se han establecido en el script *FaceAnalysis* .</span><span class="sxs-lookup"><span data-stu-id="a6bb6-370">Both the **Auth Key** and **Group Id** have been set within the *FaceAnalysis* script.</span></span>

<span data-ttu-id="a6bb6-371">En este momento está listo para compilar la solución.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-371">A this point you are ready to build the Solution.</span></span> <span data-ttu-id="a6bb6-372">Una vez creada la solución, estará listo para implementar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-372">Once the Solution has been built, you will be ready to deploy your application.</span></span>

<span data-ttu-id="a6bb6-373">Para comenzar el proceso de compilación:</span><span class="sxs-lookup"><span data-stu-id="a6bb6-373">To begin the Build process:</span></span>

1.  <span data-ttu-id="a6bb6-374">Guarde la escena actual haciendo clic en archivo, guardar.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-374">Save the current scene by clicking on File, Save.</span></span>
2.  <span data-ttu-id="a6bb6-375">Vaya a archivo, configuración de compilación y haga clic en agregar escenas abiertas.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-375">Go to File, Build Settings, click on Add Open Scenes.</span></span>
3.  <span data-ttu-id="a6bb6-376">Asegúrese de marcar los proyectos C# de Unity.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-376">Make sure to tick Unity C# Projects.</span></span>

    ![Implemente la solución desde Visual Studio.](images/AzureLabs-Lab4-24.png)

4.  <span data-ttu-id="a6bb6-378">Presione compilar.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-378">Press Build.</span></span> <span data-ttu-id="a6bb6-379">Al hacerlo, Unity iniciará una ventana del explorador de archivos, donde deberá crear y, a continuación, seleccionar una carpeta en la que compilar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-379">Upon doing so, Unity will launch a File Explorer window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="a6bb6-380">Cree esa carpeta ahora, dentro del proyecto de Unity y llámela.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-380">Create that folder now, within the Unity project, and call it App.</span></span> <span data-ttu-id="a6bb6-381">Después, con la carpeta de la aplicación seleccionada, Presione Seleccionar carpeta.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-381">Then with the App folder selected, press Select Folder.</span></span> 
5.  <span data-ttu-id="a6bb6-382">Unity comenzará a compilar el proyecto, en la carpeta de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-382">Unity will begin building your project, out to the App folder.</span></span> 
6.  <span data-ttu-id="a6bb6-383">Una vez que Unity termine de compilar (puede tardar algún tiempo), se abrirá una ventana del explorador de archivos en la ubicación de la compilación.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-383">Once Unity has finished building (it might take some time), it will open a File Explorer window at the location of your build.</span></span>

    ![Implemente la solución desde Visual Studio.](images/AzureLabs-Lab4-25.png)

7.  <span data-ttu-id="a6bb6-385">Abra la carpeta de la aplicación y, a continuación, abra la solución del nuevo proyecto (como se mostró anteriormente, MR_FaceRecognition. sln).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-385">Open your App folder, and then open the new Project Solution (as seen above, MR_FaceRecognition.sln).</span></span>


## <a name="chapter-9---deploying-your-application"></a><span data-ttu-id="a6bb6-386">Capítulo 9: implementación de la aplicación</span><span class="sxs-lookup"><span data-stu-id="a6bb6-386">Chapter 9 - Deploying your application</span></span>

<span data-ttu-id="a6bb6-387">Para implementar en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="a6bb6-387">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="a6bb6-388">Necesitará la dirección IP de HoloLens (para la implementación remota) y para asegurarse de que HoloLens está en **modo de desarrollador**.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-388">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="a6bb6-389">Para ello:</span><span class="sxs-lookup"><span data-stu-id="a6bb6-389">To do this:</span></span>

    1. <span data-ttu-id="a6bb6-390">Mientras se contenga HoloLens, abra la **configuración**.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-390">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="a6bb6-391">Vaya a **Network & Internet > Wi-Fi > opciones avanzadas** .</span><span class="sxs-lookup"><span data-stu-id="a6bb6-391">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="a6bb6-392">Anote la dirección **IPv4** .</span><span class="sxs-lookup"><span data-stu-id="a6bb6-392">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="a6bb6-393">A continuación, vuelva a **configuración**y, a continuación, **actualice & seguridad > para desarrolladores**</span><span class="sxs-lookup"><span data-stu-id="a6bb6-393">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="a6bb6-394">Establezca el modo de Desarrollador en.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-394">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="a6bb6-395">Vaya a la nueva compilación de Unity (la carpeta de la *aplicación* ) y abra el archivo de solución con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-395">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="a6bb6-396">En la configuración de soluciones, seleccione Depurar.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-396">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="a6bb6-397">En la plataforma de la solución, seleccione **x86**, **equipo remoto**.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-397">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![Implemente la solución desde Visual Studio.](images/AzureLabs-Lab4-26.png)
 
5.  <span data-ttu-id="a6bb6-399">Vaya al **menú** compilar y haga clic en **implementar solución**para transferir localmente la aplicación a HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-399">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="a6bb6-400">La aplicación debe aparecer ahora en la lista de aplicaciones instaladas en HoloLens, lista para su lanzamiento.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-400">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="a6bb6-401">Para implementar en auriculares inmersivo, establezca la **plataforma** de la solución en el *equipo local*y establezca la **configuración** en depurar, con *x86* como **plataforma**.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-401">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="a6bb6-402">A continuación, implemente en el equipo local, mediante el **menú**compilar, seleccionando *implementar solución*.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-402">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 


## <a name="chapter-10---using-the-application"></a><span data-ttu-id="a6bb6-403">Capítulo 10: uso de la aplicación</span><span class="sxs-lookup"><span data-stu-id="a6bb6-403">Chapter 10 - Using the application</span></span>

1.  <span data-ttu-id="a6bb6-404">Con HoloLens, inicie la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-404">Wearing the HoloLens, launch the app.</span></span>
2.  <span data-ttu-id="a6bb6-405">Fíjese en la persona que ha registrado con el *face API*.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-405">Look at the person that you have registered with the *Face API*.</span></span> <span data-ttu-id="a6bb6-406">Asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="a6bb6-406">Make sure that:</span></span>

    -  <span data-ttu-id="a6bb6-407">La superficie de la persona no está demasiado lejana y es claramente visible</span><span class="sxs-lookup"><span data-stu-id="a6bb6-407">The person's face is not too distant and clearly visible</span></span>
    -  <span data-ttu-id="a6bb6-408">La iluminación del entorno no es demasiado oscura</span><span class="sxs-lookup"><span data-stu-id="a6bb6-408">The environment lighting is not too dark</span></span>

3.  <span data-ttu-id="a6bb6-409">Use el gesto de puntear para capturar la imagen de la persona.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-409">Use the tap gesture to capture the person's picture.</span></span>
4.  <span data-ttu-id="a6bb6-410">Espere a que la aplicación envíe la solicitud de análisis y reciba una respuesta.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-410">Wait for the App to send the analysis request and receive a response.</span></span>
5.  <span data-ttu-id="a6bb6-411">Si la persona se reconoció correctamente, el nombre de la persona aparecerá como texto de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-411">If the person has been successfully recognized, the person's name will appear as UI text.</span></span>
6.  <span data-ttu-id="a6bb6-412">Puede repetir el proceso de captura con el gesto de punteo cada pocos segundos.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-412">You can repeat the capture process using the tap gesture every few seconds.</span></span>

## <a name="your-finished-azure-face-api-application"></a><span data-ttu-id="a6bb6-413">Su aplicación de Azure Face API finalizada</span><span class="sxs-lookup"><span data-stu-id="a6bb6-413">Your finished Azure Face API Application</span></span>

<span data-ttu-id="a6bb6-414">Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha el servicio de reconocimiento facial de Azure para detectar rostros dentro de una imagen e identificar cualquier rostro conocido.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-414">Congratulations, you built a mixed reality app that leverages the Azure Face Recognition service to detect faces within an image, and identify any known faces.</span></span>

![resultado de la finalización de este curso](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="a6bb6-416">Ejercicios de bonus</span><span class="sxs-lookup"><span data-stu-id="a6bb6-416">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="a6bb6-417">Ejercicio 1</span><span class="sxs-lookup"><span data-stu-id="a6bb6-417">Exercise 1</span></span>

<span data-ttu-id="a6bb6-418">**Azure Face API** es lo suficientemente eficaz como para detectar hasta 64 caras en una sola imagen.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-418">The **Azure Face API** is powerful enough to detect up to 64 faces in a single image.</span></span> <span data-ttu-id="a6bb6-419">Amplíe la aplicación para que pueda reconocer dos o tres caras, entre muchas otras personas.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-419">Extend the application, so that it could recognize two or three faces, amongst many other people.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="a6bb6-420">Ejercicio 2</span><span class="sxs-lookup"><span data-stu-id="a6bb6-420">Exercise 2</span></span>

<span data-ttu-id="a6bb6-421">**Azure Face API** también puede proporcionar todos los tipos de información de atributos.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-421">The **Azure Face API** is also able to provide back all kinds of attribute information.</span></span> <span data-ttu-id="a6bb6-422">Integre esto en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a6bb6-422">Integrate this into the application.</span></span> <span data-ttu-id="a6bb6-423">Esto podría ser aún más interesante, cuando se combina con el [Emotion API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).</span><span class="sxs-lookup"><span data-stu-id="a6bb6-423">This could be even more interesting, when combined with the [Emotion API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).</span></span>
