---
title: El Sr. y Azure 304 - reconocimiento de caras
description: Realice este curso para obtener información sobre cómo implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, se enfrentan a mixed reality, academy, unity, tutorial, api, reconocimiento, vr envolventes, hololens,
ms.openlocfilehash: 6330d3e5c51d6b2cbc43ea795a3f953a5b14d6f1
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605505"
---
>[!NOTE]
><span data-ttu-id="00518-104">Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.</span><span class="sxs-lookup"><span data-stu-id="00518-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="00518-105">Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="00518-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="00518-106">Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.</span><span class="sxs-lookup"><span data-stu-id="00518-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="00518-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="00518-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="00518-108">Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="00518-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="00518-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.</span><span class="sxs-lookup"><span data-stu-id="00518-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-304-face-recognition"></a><span data-ttu-id="00518-110">El Sr. y Azure 304: Reconocimiento de caras</span><span class="sxs-lookup"><span data-stu-id="00518-110">MR and Azure 304: Face recognition</span></span>

![resultado de realizar este curso](images/AzureLabs-Lab4-00.png)

<span data-ttu-id="00518-112">En este curso obtendrá información sobre cómo agregar funcionalidades de reconocimiento de cara a una aplicación de realidad mixta, con Azure Cognitive Services, Microsoft Face API.</span><span class="sxs-lookup"><span data-stu-id="00518-112">In this course you will learn how to add face recognition capabilities to a mixed reality application, using Azure Cognitive Services, with the Microsoft Face API.</span></span>

<span data-ttu-id="00518-113">*Azure Face API* es un servicio de Microsoft, que proporciona a los desarrolladores con los algoritmos más avanzados de cara, todo ello en la nube.</span><span class="sxs-lookup"><span data-stu-id="00518-113">*Azure Face API* is a Microsoft service, which provides developers with the most advanced face algorithms, all in the cloud.</span></span> <span data-ttu-id="00518-114">El *Face API* tiene dos funciones principales: la detección con atributos de caras y reconocimiento se enfrentan.</span><span class="sxs-lookup"><span data-stu-id="00518-114">The *Face API* has two main functions: face detection with attributes, and face recognition.</span></span> <span data-ttu-id="00518-115">Esto permite a los desarrolladores simplemente un conjunto de grupos de caras y, a continuación, enviar las imágenes de la consulta al servicio más adelante, para determinar a quién pertenece una cara.</span><span class="sxs-lookup"><span data-stu-id="00518-115">This allows developers to simply set a set of groups for faces, and then, send query images to the service later, to determine to whom a face belongs.</span></span> <span data-ttu-id="00518-116">Para obtener más información, visite la [página Azure Face Recognition](https://azure.microsoft.com/services/cognitive-services/face/).</span><span class="sxs-lookup"><span data-stu-id="00518-116">For more information, visit the [Azure Face Recognition page](https://azure.microsoft.com/services/cognitive-services/face/).</span></span>

<span data-ttu-id="00518-117">Una vez completado este curso, tendrá una realidad mixta HoloLens aplicación, que podrá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="00518-117">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1. <span data-ttu-id="00518-118">Use un **gesto de pulsar** para iniciar la captura de una imagen con la cámara integrada de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="00518-118">Use a **Tap Gesture** to initiate the capture of an image using the on-board HoloLens camera.</span></span> 
2. <span data-ttu-id="00518-119">Enviar la imagen capturada a la *Azure Face API* service.</span><span class="sxs-lookup"><span data-stu-id="00518-119">Send the captured image to the *Azure Face API* service.</span></span>
3. <span data-ttu-id="00518-120">Recibir los resultados de la *Face API* algoritmo.</span><span class="sxs-lookup"><span data-stu-id="00518-120">Receive the results of the *Face API* algorithm.</span></span>
4. <span data-ttu-id="00518-121">Use una interfaz de usuario simple para mostrar el nombre de las personas coincidentes.</span><span class="sxs-lookup"><span data-stu-id="00518-121">Use a simple User Interface, to display the name of matched people.</span></span>

<span data-ttu-id="00518-122">Esto le mostrará cómo obtener los resultados desde el servicio de API de cara a la aplicación de realidad mixta basada en Unity.</span><span class="sxs-lookup"><span data-stu-id="00518-122">This will teach you how to get the results from the Face API Service into your Unity-based mixed reality application.</span></span>

<span data-ttu-id="00518-123">En la aplicación, es depende de usted sobre cómo se integrará los resultados con el diseño.</span><span class="sxs-lookup"><span data-stu-id="00518-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="00518-124">Este curso está diseñado para mostrarle cómo integrar un servicio de Azure con el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="00518-124">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="00518-125">Es su trabajo consiste en usar los conocimientos que obtendrá de este curso para mejorar las aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="00518-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="00518-126">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="00518-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="00518-127">Curso</span><span class="sxs-lookup"><span data-stu-id="00518-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="00518-128"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="00518-128"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="00518-129"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="00518-129"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="00518-130">El Sr. y Azure 304: Reconocimiento de caras</span><span class="sxs-lookup"><span data-stu-id="00518-130">MR and Azure 304: Face recognition</span></span></td><td style="text-align: center;"> <span data-ttu-id="00518-131">✔️</span><span class="sxs-lookup"><span data-stu-id="00518-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="00518-132">✔️</span><span class="sxs-lookup"><span data-stu-id="00518-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="00518-133">Aunque este curso se centra principalmente en HoloLens, también puede aplicar lo aprendido en este curso a inmersivos (VR) Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="00518-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="00518-134">Dado que inmersivos (VR) no tienen cámaras accesible, necesitará una cámara externa conectada a su PC.</span><span class="sxs-lookup"><span data-stu-id="00518-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="00518-135">Como seguir el curso, verá las notas de la de los cambios que deberá emplear para admitir inmersivos (VR).</span><span class="sxs-lookup"><span data-stu-id="00518-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="00518-136">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="00518-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="00518-137">Este tutorial está diseñado para los desarrolladores con experiencia básica con Unity y C#.</span><span class="sxs-lookup"><span data-stu-id="00518-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="00518-138">También Ten en cuenta que los requisitos previos y las instrucciones escritas en este documento representan lo que se ha probado y comprobado en el momento de redactar (mayo de 2018).</span><span class="sxs-lookup"><span data-stu-id="00518-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="00518-139">Es libre de usar el software más reciente, como se muestra en el [instalar las herramientas de](install-the-tools.md) artículo, aunque no se debe suponer que la información de este curso perfectamente coincida con lo que encontrará en el software más reciente que se indica a continuación .</span><span class="sxs-lookup"><span data-stu-id="00518-139">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="00518-140">Se recomiendan el siguiente hardware y software para este curso:</span><span class="sxs-lookup"><span data-stu-id="00518-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="00518-141">Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desarrollo de auriculares envolvente (VR)</span><span class="sxs-lookup"><span data-stu-id="00518-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="00518-142">Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="00518-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md)
- [<span data-ttu-id="00518-143">El SDK más reciente de Windows 10</span><span class="sxs-lookup"><span data-stu-id="00518-143">The latest Windows 10 SDK</span></span>](install-the-tools.md)
- [<span data-ttu-id="00518-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="00518-144">Unity 2017.4</span></span>](install-the-tools.md)
- [<span data-ttu-id="00518-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="00518-145">Visual Studio 2017</span></span>](install-the-tools.md)
- <span data-ttu-id="00518-146">Un [auriculares de Windows Mixed Reality envolventes (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="00518-146">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="00518-147">Una cámara conectada a su equipo (para el desarrollo de amplias auriculares)</span><span class="sxs-lookup"><span data-stu-id="00518-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="00518-148">Acceso a Internet para el programa de instalación de Azure y la recuperación de Face API</span><span class="sxs-lookup"><span data-stu-id="00518-148">Internet access for Azure setup and Face API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="00518-149">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="00518-149">Before you start</span></span>

1.  <span data-ttu-id="00518-150">Para evitar problemas de creación de este proyecto, se recomienda encarecidamente que cree el proyecto se ha mencionado en este tutorial en una carpeta raíz o cerca de la raíz (rutas de acceso de carpeta largo pueden causar problemas en tiempo de compilación).</span><span class="sxs-lookup"><span data-stu-id="00518-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="00518-151">Configurar y probar su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="00518-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="00518-152">Si necesita admite la configuración de su HoloLens, [Asegúrese de visitar el artículo del programa de instalación de HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="00518-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="00518-153">Es una buena idea para realizar la calibración y optimización Sensor cuando comienza a desarrollar una App HoloLens nuevo (a veces puede ayudar a realizar dichas tareas para cada usuario).</span><span class="sxs-lookup"><span data-stu-id="00518-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="00518-154">Para obtener ayuda sobre la calibración, siga este [vínculo al artículo de calibración de HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="00518-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="00518-155">Para obtener ayuda sobre optimización Sensor, siga este [vínculo al artículo optimización Sensor de HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="00518-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="00518-156">Capítulo 1: el Portal de Azure</span><span class="sxs-lookup"><span data-stu-id="00518-156">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="00518-157">Para usar el *Face API* service en Azure, deberá configurar una instancia del servicio esté disponible para su aplicación.</span><span class="sxs-lookup"><span data-stu-id="00518-157">To use the *Face API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="00518-158">En primer lugar, inicie sesión en el [Portal de Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="00518-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="00518-159">Si no dispone de una cuenta de Azure, deberá crear uno.</span><span class="sxs-lookup"><span data-stu-id="00518-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="00518-160">Si está siguiendo este tutorial en una situación de aula o laboratorio, pida el instructor o uno de los a los supervisores de ayuda para instalar la nueva cuenta.</span><span class="sxs-lookup"><span data-stu-id="00518-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="00518-161">Una vez que haya iniciado sesión, haga clic en **New** en la esquina superior izquierda esquina y busque *Face API*, presione **ENTRAR**.</span><span class="sxs-lookup"><span data-stu-id="00518-161">Once you are logged in, click on **New** in the top left corner, and search for *Face API*, press **Enter**.</span></span>

    ![Busque se enfrentan a api](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > <span data-ttu-id="00518-163">La palabra **New** se han reemplazado con **crear un recurso**, en los portales más reciente.</span><span class="sxs-lookup"><span data-stu-id="00518-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="00518-164">La nueva página proporcionará una descripción de la *Face API* service.</span><span class="sxs-lookup"><span data-stu-id="00518-164">The new page will provide a description of the *Face API* service.</span></span> <span data-ttu-id="00518-165">En la parte inferior izquierda de este símbolo del sistema, seleccione el **crear** botón para crear una asociación con este servicio.</span><span class="sxs-lookup"><span data-stu-id="00518-165">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![información de la api se enfrentan](images/AzureLabs-Lab4-02.png)

4.  <span data-ttu-id="00518-167">Una vez que ha hecho clic **crear**:</span><span class="sxs-lookup"><span data-stu-id="00518-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="00518-168">Inserte el nombre deseado para esta instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="00518-168">Insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="00518-169">Seleccione una suscripción.</span><span class="sxs-lookup"><span data-stu-id="00518-169">Select a subscription.</span></span>

    3. <span data-ttu-id="00518-170">Seleccione el plan de tarifa adecuado para usted, si ésta es la primera hora de creación de un *Face API de servicio*, un nivel gratuito (denominado F0) debe estar disponible para usted.</span><span class="sxs-lookup"><span data-stu-id="00518-170">Select the pricing tier appropriate for you, if this is the first time creating a *Face API Service*, a free tier (named F0) should be available to you.</span></span>

    4. <span data-ttu-id="00518-171">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="00518-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="00518-172">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="00518-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="00518-173">Se recomienda mantener todos los servicios de Azure asociados a un proyecto único (por ejemplo, por ejemplo, estos laboratorios) en un grupo de recursos comunes).</span><span class="sxs-lookup"><span data-stu-id="00518-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="00518-174">Si desea leer más acerca de los grupos de recursos de Azure, inicie [visite el artículo del grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="00518-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="00518-175">La aplicación para UWP, **persona Maker**, que usará más adelante, requiere el uso de "West US" para la ubicación.</span><span class="sxs-lookup"><span data-stu-id="00518-175">The UWP app, **Person Maker**, which you use later, requires the use of 'West US' for location.</span></span>

    6. <span data-ttu-id="00518-176">También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.</span><span class="sxs-lookup"><span data-stu-id="00518-176">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="00518-177">Seleccione \**crear *.**</span><span class="sxs-lookup"><span data-stu-id="00518-177">Select **Create\*.**</span></span>

        ![Crear servicio de api se enfrentan](images/AzureLabs-Lab4-03.png)

5.  <span data-ttu-id="00518-179">Una vez que ha hecho clic \*\*crear \*\*\* tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="00518-179">Once you have clicked on **Create\*,** you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="00518-180">Una vez creada la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="00518-180">A notification will appear in the portal once the Service instance is created.</span></span>

    ![notificación de creación de servicio](images/AzureLabs-Lab4-04.png)

7.  <span data-ttu-id="00518-182">Haga clic en las notificaciones para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="00518-182">Click on the notifications to explore your new Service instance.</span></span>

    ![Vaya a la notificación de recursos](images/AzureLabs-Lab4-05.png)

8.  <span data-ttu-id="00518-184">Cuando esté listo, haga clic en **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="00518-184">When you are ready, click **Go to resource** button in the notification to explore your new Service instance.</span></span>

    ![claves de api se enfrentan a Access](images/AzureLabs-Lab4-06.png)

9.  <span data-ttu-id="00518-186">En este tutorial, la aplicación necesitará realizar llamadas al servicio, que se realiza a través de la suscripción del servicio en la "clave".</span><span class="sxs-lookup"><span data-stu-id="00518-186">Within this tutorial, your application will need to make calls to your service, which is done through using your service's subscription 'key'.</span></span> <span data-ttu-id="00518-187">Desde el *inicio rápido* página, de su *Face API* , el primer punto de servicio es el número a 1, *obtener las claves.*</span><span class="sxs-lookup"><span data-stu-id="00518-187">From the *Quick start* page, of your *Face API* service, the first point is number 1, to *Grab your keys.*</span></span>

10. <span data-ttu-id="00518-188">En el *servicio* página Seleccionar cualquier azul **claves** hipervínculo (si está en la página de inicio rápido), o la **claves** vínculo en el menú de navegación de servicios (a la izquierda, indicado por la ' clave ' icono), para revelar las claves.</span><span class="sxs-lookup"><span data-stu-id="00518-188">On the *Service* page select either the blue **Keys** hyperlink (if on the Quick start page), or the **Keys** link in the services navigation menu (to the left, denoted by the 'key' icon), to reveal your keys.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="00518-189">Tome nota de cualquiera de las claves y protegerla, ya que lo necesitará más adelante.</span><span class="sxs-lookup"><span data-stu-id="00518-189">Take note of either one of the keys and safeguard it, as you will need it later.</span></span>

## <a name="chapter-2---using-the-person-maker-uwp-application"></a><span data-ttu-id="00518-190">Capítulo 2: mediante la aplicación de UWP 'Persona Maker'</span><span class="sxs-lookup"><span data-stu-id="00518-190">Chapter 2 - Using the 'Person Maker' UWP application</span></span>

<span data-ttu-id="00518-191">Asegúrese de descargar la aplicación de UWP creado previamente denominado [persona Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip).</span><span class="sxs-lookup"><span data-stu-id="00518-191">Make sure to download the prebuilt UWP Application called [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip).</span></span> <span data-ttu-id="00518-192">Esta aplicación no es el producto final de este curso, sólo una herramienta que le ayudarán a crear las entradas de Azure, que utilizan el proyecto más adelante.</span><span class="sxs-lookup"><span data-stu-id="00518-192">This app is not the end product for this course, just a tool to help you create your Azure entries, which the later project will rely upon.</span></span>

<span data-ttu-id="00518-193">**Persona Maker** le permite crear entradas de Azure, que están asociadas con las personas y grupos de personas.</span><span class="sxs-lookup"><span data-stu-id="00518-193">**Person Maker** allows you to create Azure entries, which are associated with people, and groups of people.</span></span> <span data-ttu-id="00518-194">La aplicación colocará toda la información necesaria en un formato que, a continuación, más adelante se puede usar por el FaceAPI, para reconocer las caras de personas a las que han agregado.</span><span class="sxs-lookup"><span data-stu-id="00518-194">The application will place all the needed information in a format which can then later be used by the FaceAPI, in order to recognize the faces of people whom you have added.</span></span> 

> <span data-ttu-id="00518-195">[IMPORTANTE] **Persona Maker** ciertas limitaciones básica, se utiliza para ayudar a garantizar que no superen el número de llamadas de servicio por minuto para el **nivel de suscripción gratuita**.</span><span class="sxs-lookup"><span data-stu-id="00518-195">[IMPORTANT] **Person Maker** uses some basic throttling, to help ensure that you do not exceed the number of service calls per minute for the **free subscription tier**.</span></span> <span data-ttu-id="00518-196">El texto de color verde en la parte superior se cambia a rojo y actualizar como "Activo" cuando se produce la limitación; Si este es el caso, simplemente espera la aplicación (esperará hasta que siguiente puede continuar teniendo acceso al servicio de cara, como activo / en la actualización cuando se puede volver a usarlo).</span><span class="sxs-lookup"><span data-stu-id="00518-196">The green text at the top will change to red and update as 'ACTIVE' when throttling is happening; if this is the case, simply wait for the application (it will wait until it can next continue accessing the face service, updating as 'IN-ACTIVE' when you can use it again).</span></span>

<span data-ttu-id="00518-197">Esta aplicación usa el *Microsoft.ProjectOxford.Face* bibliotecas, que le permitirán sacar el máximo usan de Face API.</span><span class="sxs-lookup"><span data-stu-id="00518-197">This application uses the *Microsoft.ProjectOxford.Face* libraries, which will allow you to make full use of the Face API.</span></span> <span data-ttu-id="00518-198">Esta biblioteca está disponible gratuitamente como un paquete de NuGet.</span><span class="sxs-lookup"><span data-stu-id="00518-198">This library is available for free as a NuGet Package.</span></span> <span data-ttu-id="00518-199">Para obtener más información acerca de esto y otros similares, las API [Asegúrese de visitar el artículo de referencia de API](https://docs.microsoft.com/azure/cognitive-services/face/apireference).</span><span class="sxs-lookup"><span data-stu-id="00518-199">For more information about this, and similar, APIs [make sure to visit the API reference article](https://docs.microsoft.com/azure/cognitive-services/face/apireference).</span></span>

> [!NOTE] 
> <span data-ttu-id="00518-200">Estas son solo los pasos necesarios, instrucciones sobre cómo realizar estas operaciones es más abajo en el documento.</span><span class="sxs-lookup"><span data-stu-id="00518-200">These are just the steps required, instructions for how to do these things is further down the document.</span></span> <span data-ttu-id="00518-201">El **persona Maker** aplicación le permitirá:</span><span class="sxs-lookup"><span data-stu-id="00518-201">The **Person Maker** app will allow you to:</span></span>
>
> - <span data-ttu-id="00518-202">Crear un *persona grupo*, que es un grupo compuesto por varias personas que desea asociar con ella.</span><span class="sxs-lookup"><span data-stu-id="00518-202">Create a *Person Group*, which is a group composed of several people which you want to associate with it.</span></span> <span data-ttu-id="00518-203">Con su cuenta de Azure puede hospedar varios grupos de personas.</span><span class="sxs-lookup"><span data-stu-id="00518-203">With your Azure account you can host multiple Person Groups.</span></span>
>
> - <span data-ttu-id="00518-204">Crear un *persona*, que es un miembro de un grupo de persona.</span><span class="sxs-lookup"><span data-stu-id="00518-204">Create a *Person*, which is a member of a Person Group.</span></span> <span data-ttu-id="00518-205">Cada persona tiene un número de *cara* imágenes asociadas con él.</span><span class="sxs-lookup"><span data-stu-id="00518-205">Each person has a number of *Face* images associated with it.</span></span>
>
> -  <span data-ttu-id="00518-206">Asignar *se enfrentan a imágenes* a un *persona*, para permitir que el servicio de Azure Face API reconocer una *persona* por la correspondiente *cara*.</span><span class="sxs-lookup"><span data-stu-id="00518-206">Assign *face images* to a *Person*, to allow your Azure Face API Service to recognize a *Person* by the corresponding *face*.</span></span>
>
> -  <span data-ttu-id="00518-207">*Entrenar* su *servicio de API se enfrentan a Azure*.</span><span class="sxs-lookup"><span data-stu-id="00518-207">*Train* your *Azure Face API Service*.</span></span>

<span data-ttu-id="00518-208">Tenga en cuenta, por lo que para formar a esta aplicación para que reconozca las personas, deberán fotos de primer planos diez (10) de cada persona que le gustaría agregar a la persona del grupo.</span><span class="sxs-lookup"><span data-stu-id="00518-208">Be aware, so to train this app to recognize people, you will need ten (10) close-up photos of each person which you would like to add to your Person Group.</span></span> <span data-ttu-id="00518-209">La aplicación para Windows 10 Cam puede ayudarle a tenerla.</span><span class="sxs-lookup"><span data-stu-id="00518-209">The Windows 10 Cam App can help you to take these.</span></span> <span data-ttu-id="00518-210">Debe asegurarse de que cada foto está desactivada (evitar desenfoque, ocultar o estén demasiado lejos, desde el asunto), tiene la foto en formato de archivo jpg o png, con el tamaño del archivo de imagen que se va a no más **4 MB**y no menos de **1 KB**.</span><span class="sxs-lookup"><span data-stu-id="00518-210">You must ensure that each photo is clear (avoid blurring, obscuring, or being too far, from the subject), have the photo in jpg or png file format, with the image file size being no larger **4 MB**, and no less than **1 KB**.</span></span>

> [!NOTE]
> <span data-ttu-id="00518-211">Si está siguiendo este tutorial, no use su propia imagen para el entrenamiento, como cuando se coloca el HoloLens, no se observa usted mismo.</span><span class="sxs-lookup"><span data-stu-id="00518-211">If you are following this tutorial, do not use your own face for training, as when you put the HoloLens on, you cannot look at yourself.</span></span> <span data-ttu-id="00518-212">Utilice la cara de un alumno colega o empleado.</span><span class="sxs-lookup"><span data-stu-id="00518-212">Use the face of a colleague or fellow student.</span></span>

<span data-ttu-id="00518-213">Ejecutando **Maker persona**:</span><span class="sxs-lookup"><span data-stu-id="00518-213">Running **Person Maker**:</span></span>

1.  <span data-ttu-id="00518-214">Abra el **PersonMaker** carpeta y haga doble clic en el *PersonMaker solución* para abrirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="00518-214">Open the **PersonMaker** folder and double click on the *PersonMaker solution* to open it with *Visual Studio*.</span></span>

2.  <span data-ttu-id="00518-215">Una vez el *PersonMaker solución* está abierto, asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="00518-215">Once the *PersonMaker solution* is open, make sure that:</span></span>

    1. <span data-ttu-id="00518-216">El *configuración de la solución* está establecido en **depurar**.</span><span class="sxs-lookup"><span data-stu-id="00518-216">The *Solution Configuration* is set to **Debug**.</span></span>

    2. <span data-ttu-id="00518-217">El *plataforma de solución* está establecido en **x86**</span><span class="sxs-lookup"><span data-stu-id="00518-217">The *Solution Platform* is set to **x86**</span></span>

    3. <span data-ttu-id="00518-218">El *plataforma de destino* es **máquina Local**.</span><span class="sxs-lookup"><span data-stu-id="00518-218">The *Target Platform* is **Local Machine**.</span></span>

    4.  <span data-ttu-id="00518-219">También es posible que deba *restaurar paquetes NuGet* (haga clic en el *solución* y seleccione **restaurar paquetes NuGet**).</span><span class="sxs-lookup"><span data-stu-id="00518-219">You also may need to *Restore NuGet Packages* (right-click the *Solution* and select **Restore NuGet Packages**).</span></span>

3.  <span data-ttu-id="00518-220">Haga clic en *máquina Local* y se iniciará la aplicación.</span><span class="sxs-lookup"><span data-stu-id="00518-220">Click *Local Machine* and the application will start.</span></span> <span data-ttu-id="00518-221">Tenga en cuenta en pantallas más pequeñas, todo el contenido puede no estar visible, aunque puede desplazarse más abajo para verlo.</span><span class="sxs-lookup"><span data-stu-id="00518-221">Be aware, on smaller screens, all content may not be visible, though you can scroll further down to view it.</span></span>

    ![interfaz de usuario del creador de persona](images/AzureLabs-Lab4-07.png)

4.  <span data-ttu-id="00518-223">Inserte su **clave de autenticación de Azure**, que debe tener, desde su *Face API* servicio dentro de Azure.</span><span class="sxs-lookup"><span data-stu-id="00518-223">Insert your **Azure Authentication Key**, which you should have, from your *Face API* service within Azure.</span></span>

5.  <span data-ttu-id="00518-224">insertar:</span><span class="sxs-lookup"><span data-stu-id="00518-224">Insert:</span></span>

    1. <span data-ttu-id="00518-225">El *ID* que desea asignar a la *persona grupo*.</span><span class="sxs-lookup"><span data-stu-id="00518-225">The *ID* you want to assign to the *Person Group*.</span></span> <span data-ttu-id="00518-226">El identificador debe estar en minúscula, sin espacios en blanco.</span><span class="sxs-lookup"><span data-stu-id="00518-226">The ID must be lowercase, with no spaces.</span></span> <span data-ttu-id="00518-227">Tome nota de este identificador, tal como se requerirá más adelante en el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="00518-227">Make note of this ID, as it will be required later in your Unity project.</span></span>
    2. <span data-ttu-id="00518-228">El *nombre* que desea asignar a la *persona grupo* (puede tener espacios).</span><span class="sxs-lookup"><span data-stu-id="00518-228">The *Name* you want to assign to the *Person Group* (can have spaces).</span></span>


6.  <span data-ttu-id="00518-229">Presione **crear grupo de persona** botón.</span><span class="sxs-lookup"><span data-stu-id="00518-229">Press **Create Person Group** button.</span></span> <span data-ttu-id="00518-230">Debajo del botón, debería aparecer un mensaje de confirmación.</span><span class="sxs-lookup"><span data-stu-id="00518-230">A confirmation message should appear underneath the button.</span></span>

> [!NOTE]
> <span data-ttu-id="00518-231">Si tiene un error "Acceso denegado", compruebe la ubicación que haya configurado para su servicio de Azure.</span><span class="sxs-lookup"><span data-stu-id="00518-231">If you have an 'Access Denied' error, check the location you set for your Azure service.</span></span> <span data-ttu-id="00518-232">Como se indicó anteriormente, esta aplicación está diseñada para "West US".</span><span class="sxs-lookup"><span data-stu-id="00518-232">As stated above, this app is designed for 'West US'.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="00518-233">Observará que también puede hacer clic en el **capturar un grupo conocido** botón: se trata de si ya ha creado una persona grupo y deseos para usarlo en lugar de crear uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="00518-233">You will notice that you can also click the **Fetch a Known Group** button: this is for if you have already created a person group, and wish to use that, rather than create a new one.</span></span> <span data-ttu-id="00518-234">Tenga en cuenta, si hace clic en *crear un grupo de persona* con un grupo conocido, esto también capturará un grupo.</span><span class="sxs-lookup"><span data-stu-id="00518-234">Be aware, if you click *Create a Person Group* with a known group, this will also fetch a group.</span></span>

7.  <span data-ttu-id="00518-235">Insertar el *nombre* de la *persona* que desea crear.</span><span class="sxs-lookup"><span data-stu-id="00518-235">Insert the *Name* of the *Person* you want to create.</span></span>

    1. <span data-ttu-id="00518-236">Haga clic en el **crear persona** botón.</span><span class="sxs-lookup"><span data-stu-id="00518-236">Click the **Create Person** button.</span></span>

    2. <span data-ttu-id="00518-237">Debajo del botón, debería aparecer un mensaje de confirmación.</span><span class="sxs-lookup"><span data-stu-id="00518-237">A confirmation message should appear underneath the button.</span></span>

    3. <span data-ttu-id="00518-238">Si desea eliminar una persona ha creado anteriormente, puede escribir el nombre en el cuadro de texto y presione **persona eliminar**</span><span class="sxs-lookup"><span data-stu-id="00518-238">If you wish to delete a person you have previously created, you can write the name into the textbox and press **Delete Person**</span></span>

8.  <span data-ttu-id="00518-239">Asegúrese de que conoce la ubicación de fotos de diez (10) de la persona que le gustaría agregar a su grupo.</span><span class="sxs-lookup"><span data-stu-id="00518-239">Make sure you know the location of ten (10) photos of the person you would like to add to your group.</span></span>

9.  <span data-ttu-id="00518-240">Presione **crear y Abrir carpeta** para abrir el Explorador de Windows en la carpeta asociada a la persona.</span><span class="sxs-lookup"><span data-stu-id="00518-240">Press **Create and Open Folder** to open Windows Explorer to the folder associated to the person.</span></span> <span data-ttu-id="00518-241">Agregar las imágenes de diez (10) en la carpeta.</span><span class="sxs-lookup"><span data-stu-id="00518-241">Add the ten (10) images in the folder.</span></span> <span data-ttu-id="00518-242">Debe tratarse de *JPG* o *PNG* formato de archivo.</span><span class="sxs-lookup"><span data-stu-id="00518-242">These must be of *JPG* or *PNG* file format.</span></span>

10. <span data-ttu-id="00518-243">Haga clic en **enviar a Azure**.</span><span class="sxs-lookup"><span data-stu-id="00518-243">Click on **Submit To Azure**.</span></span> <span data-ttu-id="00518-244">Un contador le mostrará el estado del envío, seguido de un mensaje cuando se ha completado.</span><span class="sxs-lookup"><span data-stu-id="00518-244">A counter will show you the state of the submission, followed by a message when it has completed.</span></span>

11. <span data-ttu-id="00518-245">Una vez que ha finalizado el contador y se ha mostrado un mensaje de confirmación, haga clic en **entrenar** para entrenar el servicio.</span><span class="sxs-lookup"><span data-stu-id="00518-245">Once the counter has finished and a confirmation message has been displayed click on **Train** to train your Service.</span></span>

<span data-ttu-id="00518-246">Una vez que haya completado el proceso, está listo para mover a Unity.</span><span class="sxs-lookup"><span data-stu-id="00518-246">Once the process has completed, you are ready to move into Unity.</span></span>

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="00518-247">Capítulo 3: configurar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="00518-247">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="00518-248">El siguiente es un conjunto típico de para el desarrollo con la realidad mixta y por lo tanto, es una buena plantilla para otros proyectos.</span><span class="sxs-lookup"><span data-stu-id="00518-248">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="00518-249">Abra *Unity* y haga clic en **New**.</span><span class="sxs-lookup"><span data-stu-id="00518-249">Open *Unity* and click **New**.</span></span> 

    ![Inicie el nuevo proyecto de Unity.](images/AzureLabs-Lab4-08.png)

2.  <span data-ttu-id="00518-251">Ahora deberá proporcionar un nombre de proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="00518-251">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="00518-252">Insertar **MR_FaceRecognition**.</span><span class="sxs-lookup"><span data-stu-id="00518-252">Insert **MR_FaceRecognition**.</span></span> <span data-ttu-id="00518-253">Asegúrese de que el tipo de proyecto se establece en **3D**.</span><span class="sxs-lookup"><span data-stu-id="00518-253">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="00518-254">Establecer el **ubicación** a algún lugar adecuado para usted (Recuerde, es mejor cuanto más se acerque a los directorios raíz).</span><span class="sxs-lookup"><span data-stu-id="00518-254">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="00518-255">A continuación, haga clic en **crear un proyecto**.</span><span class="sxs-lookup"><span data-stu-id="00518-255">Then, click **Create project**.</span></span>

    ![Se proporcionan detalles para el nuevo proyecto de Unity.](images/AzureLabs-Lab4-09.png)

3.  <span data-ttu-id="00518-257">Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="00518-257">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="00518-258">Vaya a **Editar > Preferencias** y, a continuación, en la ventana nueva, vaya a **herramientas externas**.</span><span class="sxs-lookup"><span data-stu-id="00518-258">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="00518-259">Cambio **External Script Editor** a **de Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="00518-259">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="00518-260">Cerrar la **preferencias** ventana.</span><span class="sxs-lookup"><span data-stu-id="00518-260">Close the **Preferences** window.</span></span>

    ![Actualizar las preferencias del editor de secuencia de comandos.](images/AzureLabs-Lab4-10.png)

4.  <span data-ttu-id="00518-262">A continuación, vaya a **archivo > configuración de compilación** y cambiar la plataforma a **Universal Windows Platform**, haciendo clic en el **Cambiar plataforma** botón.</span><span class="sxs-lookup"><span data-stu-id="00518-262">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Crear ventana de configuración de la plataforma del conmutador para UWP.](images/AzureLabs-Lab4-11.png)

5.  <span data-ttu-id="00518-264">Vaya a **archivo > configuración de compilación** y asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="00518-264">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="00518-265">**Dispositivo de destino** está establecido en **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="00518-265">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="00518-266">Establezca el inmersivos, **dispositivo de destino** a *cualquier dispositivo*.</span><span class="sxs-lookup"><span data-stu-id="00518-266">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="00518-267">**Tipo de compilación** está establecido en **D3D**</span><span class="sxs-lookup"><span data-stu-id="00518-267">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="00518-268">**SDK** está establecido en **instalada más reciente**</span><span class="sxs-lookup"><span data-stu-id="00518-268">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="00518-269">**Versión de Visual Studio** está establecido en **instalada más reciente**</span><span class="sxs-lookup"><span data-stu-id="00518-269">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="00518-270">**Compilar y ejecutar** está establecido en **máquina Local**</span><span class="sxs-lookup"><span data-stu-id="00518-270">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="00518-271">Guarde la escena y agregarlo a la compilación.</span><span class="sxs-lookup"><span data-stu-id="00518-271">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="00518-272">Hacer esto seleccionando **agregar escenas abierto**.</span><span class="sxs-lookup"><span data-stu-id="00518-272">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="00518-273">Aparecerá el guardado de la ventana.</span><span class="sxs-lookup"><span data-stu-id="00518-273">A save window will appear.</span></span>

            ![Haga clic en Agregar botón de escenas abierto](images/AzureLabs-Lab4-12.png)

        2. <span data-ttu-id="00518-275">Seleccione el **nueva carpeta** botón para crear una nueva carpeta y asígnele el nombre **escenas**.</span><span class="sxs-lookup"><span data-stu-id="00518-275">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Crear nueva carpeta de scripts](images/AzureLabs-Lab4-13.png)

        3. <span data-ttu-id="00518-277">Abra el recién creado **escenas** carpeta y, a continuación, en el **nombre de archivo**: campo de texto, escriba **FaceRecScene**, a continuación, presione **guardar**.</span><span class="sxs-lookup"><span data-stu-id="00518-277">Open your newly created **Scenes** folder, and then in the **File name**: text field, type **FaceRecScene**, then press **Save**.</span></span>

            ![Asigne un nombre de nueva escena.](images/AzureLabs-Lab4-14.png)

    7. <span data-ttu-id="00518-279">El resto de la configuración, en *configuración de compilación*, debe dejarse como predeterminada por ahora.</span><span class="sxs-lookup"><span data-stu-id="00518-279">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="00518-280">En el *configuración de compilación* ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el *Inspector* se encuentra.</span><span class="sxs-lookup"><span data-stu-id="00518-280">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Abra Configuración del Reproductor.](images/AzureLabs-Lab4-15.png)

7. <span data-ttu-id="00518-282">En este panel, es necesario comprobar algunas opciones de configuración:</span><span class="sxs-lookup"><span data-stu-id="00518-282">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="00518-283">En el **otra configuración** pestaña:</span><span class="sxs-lookup"><span data-stu-id="00518-283">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="00518-284">**Scripting** **en tiempo de ejecución versión** debe ser **Experimental** (.NET 4.6 equivalente).</span><span class="sxs-lookup"><span data-stu-id="00518-284">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent).</span></span> <span data-ttu-id="00518-285">Cambiar esto desencadenará una necesidad de reiniciar el Editor.</span><span class="sxs-lookup"><span data-stu-id="00518-285">Changing this will trigger a need to restart the Editor.</span></span>
        2. <span data-ttu-id="00518-286">**Scripting de back-end** debe ser **.NET**</span><span class="sxs-lookup"><span data-stu-id="00518-286">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="00518-287">**Nivel de compatibilidad de API** debe ser **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="00518-287">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Actualizar la configuración de otros.](images/AzureLabs-Lab4-16.png)
      
    2. <span data-ttu-id="00518-289">Dentro de la **configuración de publicación** ficha **capacidades**, consulte:</span><span class="sxs-lookup"><span data-stu-id="00518-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="00518-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="00518-290">**InternetClient**</span></span>
        - <span data-ttu-id="00518-291">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="00518-291">**Webcam**</span></span>

            ![Actualizando la configuración de publicación.](images/AzureLabs-Lab4-17.png)

    3. <span data-ttu-id="00518-293">Más abajo el panel, en **XR configuración** (bajo **configuración de publicación**), graduación **admite la realidad Virtual**, asegúrese de que el **SDK de Windows Mixed Reality**  se agrega.</span><span class="sxs-lookup"><span data-stu-id="00518-293">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Actualice la configuración de R de X.](images/AzureLabs-Lab4-18.png)

8.  <span data-ttu-id="00518-295">En *configuración de compilación*, **Unity C# proyectos** ya no está atenuada; Marque la casilla situada junto a esto.</span><span class="sxs-lookup"><span data-stu-id="00518-295">Back in *Build Settings*, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="00518-296">Cierre la ventana de configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="00518-296">Close the Build Settings window.</span></span>
10. <span data-ttu-id="00518-297">Guarde la escena y el proyecto (**archivo > Guardar ESCENA / archivo > Guardar proyecto**).</span><span class="sxs-lookup"><span data-stu-id="00518-297">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4---main-camera-setup"></a><span data-ttu-id="00518-298">Capítulo 4: configuración de cámara principal</span><span class="sxs-lookup"><span data-stu-id="00518-298">Chapter 4 - Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="00518-299">Si desea omitir la *configurar Unity* componente de este curso y continuar directamente en código, no dude en [descargar este .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)e importarlo en el proyecto como un [personalizado Paquete](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="00518-299">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="00518-300">Tenga en cuenta que este paquete también incluye la importación de la *Newtonsoft DLL*, descrito en [capítulo 5](#chapter-5--import-the-newtonsoft.json-library).</span><span class="sxs-lookup"><span data-stu-id="00518-300">Be aware that this package also includes the import of the *Newtonsoft DLL*, covered in [Chapter 5](#chapter-5--import-the-newtonsoft.json-library).</span></span> <span data-ttu-id="00518-301">Con esto se importa, puede continuar desde [capítulo 6](#chapter-6-create-the-faceanalysis-class).</span><span class="sxs-lookup"><span data-stu-id="00518-301">With this imported, you can continue from [Chapter 6](#chapter-6-create-the-faceanalysis-class).</span></span>

1.  <span data-ttu-id="00518-302">En el *jerarquía* Panel, seleccione el **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="00518-302">In the *Hierarchy* Panel, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="00518-303">Una vez seleccionado, podrá ver todos los componentes de la **cámara principal** en el *Panel Inspector*.</span><span class="sxs-lookup"><span data-stu-id="00518-303">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="00518-304">El **objeto de cámara** debe denominarse **cámara principal** (tenga en cuenta la ortografía!)</span><span class="sxs-lookup"><span data-stu-id="00518-304">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2. <span data-ttu-id="00518-305">La cámara principal **etiqueta** debe establecerse en **MainCamera** (tenga en cuenta la ortografía!)</span><span class="sxs-lookup"><span data-stu-id="00518-305">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3. <span data-ttu-id="00518-306">Asegúrese de que el **transformar posición** está establecido en **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="00518-306">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4. <span data-ttu-id="00518-307">Establecer **borrar las marcas de** a **Color sólido**</span><span class="sxs-lookup"><span data-stu-id="00518-307">Set **Clear Flags** to **Solid Color**</span></span>

    5. <span data-ttu-id="00518-308">Establecer el **en segundo plano** Color del componente de cámara para **negro, alfa de 0 (Hex código: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="00518-308">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

        ![configurar componentes de la cámara](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a><span data-ttu-id="00518-310">Capítulo 5: importación de la biblioteca de Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="00518-310">Chapter 5 – Import the Newtonsoft.Json library</span></span>

> [!IMPORTANT]
> <span data-ttu-id="00518-311">Si ha importado el '.unitypackage' en el [último capítulo](#chapter-4--main-camera-setup), puede omitir este capítulo.</span><span class="sxs-lookup"><span data-stu-id="00518-311">If you imported the '.unitypackage' in the [last Chapter](#chapter-4--main-camera-setup), you can skip this Chapter.</span></span>

<span data-ttu-id="00518-312">Para ayudarle a deserializan y serializan objetos recibidos y enviados al servicio Bot debe descargar el *Newtonsoft.Json* biblioteca.</span><span class="sxs-lookup"><span data-stu-id="00518-312">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the *Newtonsoft.Json* library.</span></span> <span data-ttu-id="00518-313">Encontrará una versión compatible ya organizada con la estructura de carpetas de Unity correcta en esta [archivo de paquete de Unity](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="00518-313">You will find a compatible version already organized with the correct Unity folder structure in this [Unity package file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="00518-314">Para importar la biblioteca:</span><span class="sxs-lookup"><span data-stu-id="00518-314">To import the library:</span></span>

1.  <span data-ttu-id="00518-315">Descargue el paquete de Unity.</span><span class="sxs-lookup"><span data-stu-id="00518-315">Download the Unity Package.</span></span>
2.  <span data-ttu-id="00518-316">Haga clic en **activos**, **Importar paquete**, **paquete personalizado**.</span><span class="sxs-lookup"><span data-stu-id="00518-316">Click on **Assets**, **Import Package**, **Custom Package**.</span></span>

    ![Importación de la biblioteca de Newtonsoft.Json](images/AzureLabs-Lab4-20.png)

3.  <span data-ttu-id="00518-318">Busque el paquete de Unity que ha descargado y haga clic en Abrir.</span><span class="sxs-lookup"><span data-stu-id="00518-318">Look for the Unity Package you have downloaded, and click Open.</span></span>
4.  <span data-ttu-id="00518-319">Asegúrese de que todos los componentes del paquete están activados y haga clic en **importación**.</span><span class="sxs-lookup"><span data-stu-id="00518-319">Make sure all the components of the package are ticked and click **Import**.</span></span>

    ![Importación de la biblioteca de Newtonsoft.Json](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a><span data-ttu-id="00518-321">Capítulo 6: crear la clase FaceAnalysis</span><span class="sxs-lookup"><span data-stu-id="00518-321">Chapter 6 - Create the FaceAnalysis class</span></span>

<span data-ttu-id="00518-322">El propósito de la clase FaceAnalysis va a hospedar los métodos necesarios para comunicarse con el servicio de reconocimiento de caras de Azure.</span><span class="sxs-lookup"><span data-stu-id="00518-322">The purpose of the FaceAnalysis class is to host the methods necessary to communicate with your Azure Face Recognition Service.</span></span> 

- <span data-ttu-id="00518-323">Después de enviar el servicio de una imagen de captura, su análisis e identificará las caras dentro y determinar si cualquiera pertenecen a una persona conocida.</span><span class="sxs-lookup"><span data-stu-id="00518-323">After sending the service a capture image, it will analyse it and identify the faces within, and determine if any belong to a known person.</span></span> 
- <span data-ttu-id="00518-324">Si se encuentra una persona conocida, esta clase mostrará su nombre como texto de la interfaz de usuario de la escena.</span><span class="sxs-lookup"><span data-stu-id="00518-324">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="00518-325">Para crear el *FaceAnalysis* clase:</span><span class="sxs-lookup"><span data-stu-id="00518-325">To create the *FaceAnalysis* class:</span></span>

 1. <span data-ttu-id="00518-326">Haga clic en el *carpeta Assets* ubicado en el Panel proyecto, haga clic en **crear** > **carpeta**.</span><span class="sxs-lookup"><span data-stu-id="00518-326">Right-click in the *Assets Folder* located in the Project Panel, then click on **Create** > **Folder**.</span></span> <span data-ttu-id="00518-327">Llame a la carpeta **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="00518-327">Call the folder **Scripts**.</span></span> 

    ![Cree la clase FaceAnalysis.](images/AzureLabs-Lab4-22.png)

2.  <span data-ttu-id="00518-329">Haga doble clic en la carpeta que acaba de crear para abrirlo.</span><span class="sxs-lookup"><span data-stu-id="00518-329">Double click on the folder just created, to open it.</span></span> 
3.  <span data-ttu-id="00518-330">Haga clic en la carpeta, a continuación, haga clic en **crear**  >   **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="00518-330">Right-click inside the folder, then click on **Create** > **C# Script**.</span></span> <span data-ttu-id="00518-331">Llame al script *FaceAnalysis*.</span><span class="sxs-lookup"><span data-stu-id="00518-331">Call the script *FaceAnalysis*.</span></span> 
4.  <span data-ttu-id="00518-332">Haga doble clic en el nuevo *FaceAnalysis* script para abrirlo con Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="00518-332">Double click on the new *FaceAnalysis* script to open it with Visual Studio 2017.</span></span>
5.  <span data-ttu-id="00518-333">Escriba los siguientes espacios de nombres anterior el *FaceAnalysis* clase:</span><span class="sxs-lookup"><span data-stu-id="00518-333">Enter the following namespaces above the *FaceAnalysis* class:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="00518-334">Deberá agregar todos los objetos que se usan para deserialising.</span><span class="sxs-lookup"><span data-stu-id="00518-334">You now need to add all of the objects which are used for deserialising.</span></span> <span data-ttu-id="00518-335">Estos objetos deben agregarse **fuera** de la *FaceAnalysis* script (debajo de la llave inferior).</span><span class="sxs-lookup"><span data-stu-id="00518-335">These objects need to be added **outside** of the *FaceAnalysis* script (beneath the bottom curly bracket).</span></span> 

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
7. <span data-ttu-id="00518-336">El *Start()* y *Update()* métodos no se usará, por lo que eliminarlos ahora.</span><span class="sxs-lookup"><span data-stu-id="00518-336">The *Start()* and *Update()* methods will not be used, so delete them now.</span></span> 

8.  <span data-ttu-id="00518-337">Dentro de la *FaceAnalysis* de clases, agregue las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="00518-337">Inside the *FaceAnalysis* class, add the following variables:</span></span>

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
    > <span data-ttu-id="00518-338">Reemplace el **clave** y **personGroupId** con su clave de servicio y el identificador del grupo que creó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="00518-338">Replace the **key** and the **personGroupId** with your Service Key and the Id of the group that you created previously.</span></span>

9.  <span data-ttu-id="00518-339">Agregar el *Awake()* método, que initialises la clase, agregando el *ImageCapture* clase a la cámara principal y llama al método de creación de etiqueta:</span><span class="sxs-lookup"><span data-stu-id="00518-339">Add the *Awake()* method, which initialises the class, adding the *ImageCapture* class to the Main Camera and calls the Label creation method:</span></span>

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

10. <span data-ttu-id="00518-340">Agregar el *CreateLabel()* método, que crea el *etiqueta* objeto para mostrar el resultado del análisis:</span><span class="sxs-lookup"><span data-stu-id="00518-340">Add the *CreateLabel()* method, which creates the *Label* object to display the analysis result:</span></span>

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

11. <span data-ttu-id="00518-341">Agregar el *DetectFacesFromImage()* y *GetImageAsByteArray()* método.</span><span class="sxs-lookup"><span data-stu-id="00518-341">Add the *DetectFacesFromImage()* and *GetImageAsByteArray()* method.</span></span> <span data-ttu-id="00518-342">La primera solicitud que el servicio de reconocimiento de caras para detectar cualquier posible cara en la imagen enviada, mientras que el último es necesario para convertir la imagen capturada en una matriz de bytes:</span><span class="sxs-lookup"><span data-stu-id="00518-342">The former will request the Face Recognition Service to detect any possible face in the submitted image, while the latter is necessary to convert the captured image into a bytes array:</span></span>

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

12. <span data-ttu-id="00518-343">Agregar el *IdentifyFaces()* método, que solicita la *servicio de reconocimiento de caras* para identificar cualquier cara conocido detectado anteriormente en la imagen enviada.</span><span class="sxs-lookup"><span data-stu-id="00518-343">Add the *IdentifyFaces()* method, which requests the *Face Recognition Service* to identify any known face previously detected in the submitted image.</span></span> <span data-ttu-id="00518-344">La solicitud devolverá un identificador de la persona identificada pero no el nombre:</span><span class="sxs-lookup"><span data-stu-id="00518-344">The request will return an id of the identified person but not the name:</span></span>

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

13. <span data-ttu-id="00518-345">Agregar el *GetPerson()* método.</span><span class="sxs-lookup"><span data-stu-id="00518-345">Add the *GetPerson()* method.</span></span> <span data-ttu-id="00518-346">Al proporcionar dicho Id., este método, a continuación, las solicitudes para el *servicio de reconocimiento de caras* para devolver el nombre de la persona identificado:</span><span class="sxs-lookup"><span data-stu-id="00518-346">By providing the person id, this method then requests for the *Face Recognition Service* to return the name of the identified person:</span></span>

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

14.  <span data-ttu-id="00518-347">No olvide **guardar** los cambios antes de volver al Editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="00518-347">Remember to **Save** the changes before going back to the Unity Editor.</span></span>
15.  <span data-ttu-id="00518-348">En el Editor de Unity, arrastre la secuencia de comandos FaceAnalysis desde la carpeta de Scripts en el panel de proyecto para el objeto de cámara principal en el *panel jerarquía*.</span><span class="sxs-lookup"><span data-stu-id="00518-348">In the Unity Editor, drag the FaceAnalysis script from the Scripts folder in Project panel to the Main Camera object in the *Hierarchy panel*.</span></span> <span data-ttu-id="00518-349">El nuevo componente de script se agregará a la cámara principal así.</span><span class="sxs-lookup"><span data-stu-id="00518-349">The new script component will be so added to the Main Camera.</span></span> 

![Colocar FaceAnalysis hasta la cámara principal](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a><span data-ttu-id="00518-351">Capítulo 7: crear la clase ImageCapture</span><span class="sxs-lookup"><span data-stu-id="00518-351">Chapter 7 - Create the ImageCapture class</span></span>

<span data-ttu-id="00518-352">El propósito de la *ImageCapture* clase va a hospedar los métodos necesarios para comunicarse con su *servicio de reconocimiento de caras Azure* para analizar la imagen que capturará, identificación de caras en él y determinar si pertenece a una persona conocida.</span><span class="sxs-lookup"><span data-stu-id="00518-352">The purpose of the *ImageCapture* class is to host the methods necessary to communicate with your *Azure Face Recognition Service* to analyse the image you will capture, identifying faces in it and determining if it belongs to a known person.</span></span> <span data-ttu-id="00518-353">Si se encuentra una persona conocida, esta clase mostrará su nombre como texto de la interfaz de usuario de la escena.</span><span class="sxs-lookup"><span data-stu-id="00518-353">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="00518-354">Para crear el *ImageCapture* clase:</span><span class="sxs-lookup"><span data-stu-id="00518-354">To create the *ImageCapture* class:</span></span>
 
1.  <span data-ttu-id="00518-355">Haga clic en el **Scripts** carpeta que ha creado anteriormente y, después, haga clic en **crear**,  **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="00518-355">Right-click inside the **Scripts** folder you have created previously, then click on **Create**, **C# Script**.</span></span> <span data-ttu-id="00518-356">Llame al script *ImageCapture*.</span><span class="sxs-lookup"><span data-stu-id="00518-356">Call the script *ImageCapture*.</span></span> 
2.  <span data-ttu-id="00518-357">Haga doble clic en el nuevo *ImageCapture* script para abrirlo con Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="00518-357">Double click on the new *ImageCapture* script to open it with Visual Studio 2017.</span></span>
3.  <span data-ttu-id="00518-358">Escriba los siguientes espacios de nombres encima de la clase ImageCapture:</span><span class="sxs-lookup"><span data-stu-id="00518-358">Enter the following namespaces above the ImageCapture class:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  <span data-ttu-id="00518-359">Dentro de la *ImageCapture* de clases, agregue las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="00518-359">Inside the *ImageCapture* class, add the following variables:</span></span>

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

5.  <span data-ttu-id="00518-360">Agregar el *Awake()* y *Start()* métodos necesarios para inicializar la clase y permitir la HoloLens capturar los gestos del usuario:</span><span class="sxs-lookup"><span data-stu-id="00518-360">Add the *Awake()* and *Start()* methods necessary to initialise the class and allow the HoloLens to capture the user's gestures:</span></span>

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

6.  <span data-ttu-id="00518-361">Agregar el *TapHandler()* que se llama cuando el usuario realiza una *pulse* gestos:</span><span class="sxs-lookup"><span data-stu-id="00518-361">Add the *TapHandler()* which is called when the user performs a *Tap* gesture:</span></span>

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

7.  <span data-ttu-id="00518-362">Agregar el *ExecuteImageCaptureAndAnalysis()* método, que se iniciará el proceso de captura de imagen:</span><span class="sxs-lookup"><span data-stu-id="00518-362">Add the *ExecuteImageCaptureAndAnalysis()* method, which will begin the process of Image Capturing:</span></span>

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

8.  <span data-ttu-id="00518-363">Agregue los controladores que se llaman cuando se ha completado el proceso de captura de fotos:</span><span class="sxs-lookup"><span data-stu-id="00518-363">Add the handlers that are called when the photo capture process has been completed:</span></span>

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

9. <span data-ttu-id="00518-364">No olvide **guardar** los cambios antes de volver al Editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="00518-364">Remember to **Save** the changes before going back to the Unity Editor.</span></span>

## <a name="chapter-8---building-the-solution"></a><span data-ttu-id="00518-365">Capítulo 8: creación de la solución</span><span class="sxs-lookup"><span data-stu-id="00518-365">Chapter 8 - Building the solution</span></span>

<span data-ttu-id="00518-366">Para llevar a cabo una prueba completa de la aplicación se necesitará para transferir localmente en su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="00518-366">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="00518-367">Antes de hacerlo, asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="00518-367">Before you do, ensure that:</span></span>

-   <span data-ttu-id="00518-368">Todas las configuraciones que se mencionan en el capítulo 3 se establecen correctamente.</span><span class="sxs-lookup"><span data-stu-id="00518-368">All the settings mentioned in the Chapter 3 are set correctly.</span></span> 
-   <span data-ttu-id="00518-369">La secuencia de comandos *FaceAnalysis* se adjunta al objeto de cámara principal.</span><span class="sxs-lookup"><span data-stu-id="00518-369">The script *FaceAnalysis* is attached to the Main Camera object.</span></span> 
-   <span data-ttu-id="00518-370">Tanto el **Auth Key** y **Id. de grupo** se han establecido dentro de la *FaceAnalysis* secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="00518-370">Both the **Auth Key** and **Group Id** have been set within the *FaceAnalysis* script.</span></span>

<span data-ttu-id="00518-371">Este punto, está listo para compilar la solución.</span><span class="sxs-lookup"><span data-stu-id="00518-371">A this point you are ready to build the Solution.</span></span> <span data-ttu-id="00518-372">Una vez que se ha compilado la solución, estará listo para implementar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="00518-372">Once the Solution has been built, you will be ready to deploy your application.</span></span>

<span data-ttu-id="00518-373">Para comenzar el proceso de compilación:</span><span class="sxs-lookup"><span data-stu-id="00518-373">To begin the Build process:</span></span>

1.  <span data-ttu-id="00518-374">Guarde la escena actual haciendo clic en archivo, guardar.</span><span class="sxs-lookup"><span data-stu-id="00518-374">Save the current scene by clicking on File, Save.</span></span>
2.  <span data-ttu-id="00518-375">Vaya al archivo de configuración de compilación, haga clic en Agregar escenas abierto.</span><span class="sxs-lookup"><span data-stu-id="00518-375">Go to File, Build Settings, click on Add Open Scenes.</span></span>
3.  <span data-ttu-id="00518-376">Asegúrese de graduación Unity C# proyectos.</span><span class="sxs-lookup"><span data-stu-id="00518-376">Make sure to tick Unity C# Projects.</span></span>

    ![Implementar la solución de Visual Studio.](images/AzureLabs-Lab4-24.png)

4.  <span data-ttu-id="00518-378">Presione la compilación.</span><span class="sxs-lookup"><span data-stu-id="00518-378">Press Build.</span></span> <span data-ttu-id="00518-379">Al hacerlo, Unity iniciará una ventana del explorador de archivos, donde se debe crear y, a continuación, seleccione una carpeta para compilar la aplicación en.</span><span class="sxs-lookup"><span data-stu-id="00518-379">Upon doing so, Unity will launch a File Explorer window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="00518-380">Crear la carpeta ahora, dentro del proyecto de Unity y llámelo App.</span><span class="sxs-lookup"><span data-stu-id="00518-380">Create that folder now, within the Unity project, and call it App.</span></span> <span data-ttu-id="00518-381">A continuación, con la carpeta de la aplicación seleccionada, presione seleccionar la carpeta.</span><span class="sxs-lookup"><span data-stu-id="00518-381">Then with the App folder selected, press Select Folder.</span></span> 
5.  <span data-ttu-id="00518-382">Unity empezará a crear el proyecto, en la carpeta de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="00518-382">Unity will begin building your project, out to the App folder.</span></span> 
6.  <span data-ttu-id="00518-383">Una vez Unity ha finalizado la compilación (puede tardar algún tiempo), se abrirá una ventana del explorador de archivos en la ubicación de la compilación.</span><span class="sxs-lookup"><span data-stu-id="00518-383">Once Unity has finished building (it might take some time), it will open a File Explorer window at the location of your build.</span></span>

    ![Implementar la solución de Visual Studio.](images/AzureLabs-Lab4-25.png)

7.  <span data-ttu-id="00518-385">Abra la carpeta de aplicación y, a continuación, abra la nueva solución de proyecto (tal y como se muestra anteriormente, MR_FaceRecognition.sln).</span><span class="sxs-lookup"><span data-stu-id="00518-385">Open your App folder, and then open the new Project Solution (as seen above, MR_FaceRecognition.sln).</span></span>


## <a name="chapter-9---deploying-your-application"></a><span data-ttu-id="00518-386">Capítulo 9: implementación de la aplicación</span><span class="sxs-lookup"><span data-stu-id="00518-386">Chapter 9 - Deploying your application</span></span>

<span data-ttu-id="00518-387">Para implementar en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="00518-387">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="00518-388">Necesitará la dirección IP de su HoloLens (para la implementación remota), y garantizar su HoloLens se encuentra en **modo de programador**.</span><span class="sxs-lookup"><span data-stu-id="00518-388">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="00518-389">Para ello:</span><span class="sxs-lookup"><span data-stu-id="00518-389">To do this:</span></span>

    1. <span data-ttu-id="00518-390">Mientras que el exceso de su HoloLens, abra el **configuración**.</span><span class="sxs-lookup"><span data-stu-id="00518-390">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="00518-391">Vaya a **red e Internet > Wi-Fi > Opciones avanzadas**</span><span class="sxs-lookup"><span data-stu-id="00518-391">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="00518-392">Tenga en cuenta la **IPv4** dirección.</span><span class="sxs-lookup"><span data-stu-id="00518-392">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="00518-393">A continuación, vaya a **configuración**y, a continuación, para **actualización y seguridad > para desarrolladores**</span><span class="sxs-lookup"><span data-stu-id="00518-393">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="00518-394">Activar el modo de programador.</span><span class="sxs-lookup"><span data-stu-id="00518-394">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="00518-395">Vaya a la nueva compilación de Unity (la *aplicación* carpeta) y abra el archivo de solución con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="00518-395">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="00518-396">En, seleccione la configuración de la solución **depurar**.</span><span class="sxs-lookup"><span data-stu-id="00518-396">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="00518-397">En la plataforma de soluciones, seleccione **x86**, **máquina remota**.</span><span class="sxs-lookup"><span data-stu-id="00518-397">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![Implementar la solución de Visual Studio.](images/AzureLabs-Lab4-26.png)
 
5.  <span data-ttu-id="00518-399">Vaya a la **menú compilar** y haga clic en **implementar solución**, para transferir localmente la aplicación a su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="00518-399">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="00518-400">La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas en su HoloLens, lista para iniciarse.</span><span class="sxs-lookup"><span data-stu-id="00518-400">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="00518-401">Para implementar en los auriculares envolventes, establezca el **plataforma de solución** a *máquina Local*y establezca el **configuración** a *depurar*, con *x86* como el **plataforma**.</span><span class="sxs-lookup"><span data-stu-id="00518-401">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="00518-402">Implementar, a continuación, en el equipo local machine, utilizando el **menú compilar**, seleccionar *implementar solución*.</span><span class="sxs-lookup"><span data-stu-id="00518-402">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 


## <a name="chapter-10---using-the-application"></a><span data-ttu-id="00518-403">Capítulo 10: uso de la aplicación</span><span class="sxs-lookup"><span data-stu-id="00518-403">Chapter 10 - Using the application</span></span>

1.  <span data-ttu-id="00518-404">El exceso de la HoloLens, inicie la aplicación.</span><span class="sxs-lookup"><span data-stu-id="00518-404">Wearing the HoloLens, launch the app.</span></span>
2.  <span data-ttu-id="00518-405">Examine la persona que haya registrado con el *Face API*.</span><span class="sxs-lookup"><span data-stu-id="00518-405">Look at the person that you have registered with the *Face API*.</span></span> <span data-ttu-id="00518-406">Asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="00518-406">Make sure that:</span></span>

    -  <span data-ttu-id="00518-407">Su cara no está claramente visibles y demasiado distantes</span><span class="sxs-lookup"><span data-stu-id="00518-407">The person's face is not too distant and clearly visible</span></span>
    -  <span data-ttu-id="00518-408">La iluminación de entorno no es demasiado oscura</span><span class="sxs-lookup"><span data-stu-id="00518-408">The environment lighting is not too dark</span></span>

3.  <span data-ttu-id="00518-409">Usar el gesto de pulsar para capturar la imagen de la persona.</span><span class="sxs-lookup"><span data-stu-id="00518-409">Use the tap gesture to capture the person's picture.</span></span>
4.  <span data-ttu-id="00518-410">Espere a que la aplicación enviar la solicitud de análisis y recibir una respuesta.</span><span class="sxs-lookup"><span data-stu-id="00518-410">Wait for the App to send the analysis request and receive a response.</span></span>
5.  <span data-ttu-id="00518-411">Si la persona que ha sido reconocida correctamente, el nombre de persona aparecerá como texto de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="00518-411">If the person has been successfully recognized, the person's name will appear as UI text.</span></span>
6.  <span data-ttu-id="00518-412">Puede repetir el proceso de captura con el gesto de pulsar cada pocos segundos.</span><span class="sxs-lookup"><span data-stu-id="00518-412">You can repeat the capture process using the tap gesture every few seconds.</span></span>

## <a name="your-finished-azure-face-api-application"></a><span data-ttu-id="00518-413">La aplicación de API de cara Azure finalizada</span><span class="sxs-lookup"><span data-stu-id="00518-413">Your finished Azure Face API Application</span></span>

<span data-ttu-id="00518-414">Enhorabuena, compila una aplicación de realidad mixta que aprovecha el servicio de reconocimiento de caras de Azure para detectar caras dentro de una imagen e identificar cualquier caras conocidas.</span><span class="sxs-lookup"><span data-stu-id="00518-414">Congratulations, you built a mixed reality app that leverages the Azure Face Recognition service to detect faces within an image, and identify any known faces.</span></span>

![resultado de realizar este curso](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="00518-416">Ejercicios de bonificación</span><span class="sxs-lookup"><span data-stu-id="00518-416">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="00518-417">Ejercicio 1</span><span class="sxs-lookup"><span data-stu-id="00518-417">Exercise 1</span></span>

<span data-ttu-id="00518-418">El **Azure Face API** es lo suficientemente eficaz para detectar hasta 64 caras en una sola imagen.</span><span class="sxs-lookup"><span data-stu-id="00518-418">The **Azure Face API** is powerful enough to detect up to 64 faces in a single image.</span></span> <span data-ttu-id="00518-419">Ampliar la aplicación, por lo que pudieran reconocer caras de dos o tres, entre muchas otras personas.</span><span class="sxs-lookup"><span data-stu-id="00518-419">Extend the application, so that it could recognize two or three faces, amongst many other people.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="00518-420">Ejercicio 2</span><span class="sxs-lookup"><span data-stu-id="00518-420">Exercise 2</span></span>

<span data-ttu-id="00518-421">El **Azure Face API** también es capaz de proporcionar todos los tipos de información de atributos de vuelta.</span><span class="sxs-lookup"><span data-stu-id="00518-421">The **Azure Face API** is also able to provide back all kinds of attribute information.</span></span> <span data-ttu-id="00518-422">Integrar esto en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="00518-422">Integrate this into the application.</span></span> <span data-ttu-id="00518-423">Esto podría ser aún más interesante, cuando se combina con la [Emotion API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).</span><span class="sxs-lookup"><span data-stu-id="00518-423">This could be even more interesting, when combined with the [Emotion API](https://azure.microsoft.com/en-au/services/cognitive-services/emotion/).</span></span>
