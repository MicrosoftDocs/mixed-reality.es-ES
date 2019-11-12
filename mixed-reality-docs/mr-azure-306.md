---
title: 'Sr. d y Azure 306: vídeo de streaming'
description: Complete este curso para aprender a implementar Azure Media Services en una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academia, Unity, tutorial, API, Media Services, streaming video, 360, envolventes, VR
ms.openlocfilehash: e0350d69eed9b922e174bc521107beac7d11b1bc
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926826"
---
>[!NOTE]
><span data-ttu-id="ac25f-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="ac25f-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="ac25f-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="ac25f-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="ac25f-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ac25f-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="ac25f-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="ac25f-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="ac25f-108">Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ac25f-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="ac25f-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.</span><span class="sxs-lookup"><span data-stu-id="ac25f-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-306-streaming-video"></a><span data-ttu-id="ac25f-110">MR y Azure 306: streaming de vídeo</span><span class="sxs-lookup"><span data-stu-id="ac25f-110">MR and Azure 306: Streaming video</span></span>

<span data-ttu-id="ac25f-111">![última](images/AzureLabs-Lab6-00.png)
de inicio del producto ![última](images/AzureLabs-Lab6-01.png) de inicio del producto</span><span class="sxs-lookup"><span data-stu-id="ac25f-111">![final product -start](images/AzureLabs-Lab6-00.png)
![final product -start](images/AzureLabs-Lab6-01.png)</span></span>

<span data-ttu-id="ac25f-112">En este curso aprenderá a conectar su Azure Media Services a una experiencia de Windows Mixed Reality VR para permitir la reproducción de vídeo a través de streaming de 360 Degree en auriculares de gran rendimiento.</span><span class="sxs-lookup"><span data-stu-id="ac25f-112">In this course you will learn how connect your Azure Media Services to a Windows Mixed Reality VR experience to allow streaming 360 degree video playback on immersive headsets.</span></span> 

<span data-ttu-id="ac25f-113">**Azure Media Services** son una colección de servicios que ofrece servicios de streaming de vídeo con calidad de difusión para llegar a audiencias de mayor tamaño en los dispositivos móviles más populares de hoy en día.</span><span class="sxs-lookup"><span data-stu-id="ac25f-113">**Azure Media Services** are a collection of services that gives you broadcast-quality video streaming services to reach larger audiences on today’s most popular mobile devices.</span></span> <span data-ttu-id="ac25f-114">Para obtener más información, visite la [página Azure Media Services](https://azure.microsoft.com/services/media-services).</span><span class="sxs-lookup"><span data-stu-id="ac25f-114">For more information, visit the [Azure Media Services page](https://azure.microsoft.com/services/media-services).</span></span>

<span data-ttu-id="ac25f-115">Una vez finalizado este curso, tendrá una aplicación de auriculares envolvente de realidad mixta, que podrá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="ac25f-115">Having completed this course, you will have a mixed reality immersive headset application, which will be able to do the following:</span></span>

1. <span data-ttu-id="ac25f-116">Recupere un vídeo de 360 grados de un **Azure Storage**a través de **Azure Media Services**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-116">Retrieve a 360 degree video from an **Azure Storage**, through the **Azure Media Service**.</span></span>

2. <span data-ttu-id="ac25f-117">Muestra el vídeo de 360 Degree recuperado dentro de una escena de Unity.</span><span class="sxs-lookup"><span data-stu-id="ac25f-117">Display the retrieved 360 degree video within a Unity scene.</span></span>

3. <span data-ttu-id="ac25f-118">Desplazarse entre dos escenas, con dos vídeos diferentes.</span><span class="sxs-lookup"><span data-stu-id="ac25f-118">Navigate between two scenes, with two different videos.</span></span>

<span data-ttu-id="ac25f-119">En su aplicación, depende del modo en que va a integrar los resultados con el diseño.</span><span class="sxs-lookup"><span data-stu-id="ac25f-119">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="ac25f-120">Este curso está diseñado para enseñarle a integrar un servicio de Azure con su proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="ac25f-120">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="ac25f-121">Es su trabajo usar el conocimiento que obtiene de este curso para mejorar su aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="ac25f-121">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="ac25f-122">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="ac25f-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="ac25f-123">Recurso</span><span class="sxs-lookup"><span data-stu-id="ac25f-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="ac25f-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ac25f-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ac25f-125"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="ac25f-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="ac25f-126">MR y Azure 306: streaming de vídeo</span><span class="sxs-lookup"><span data-stu-id="ac25f-126">MR and Azure 306: Streaming video</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="ac25f-127">✔️</span><span class="sxs-lookup"><span data-stu-id="ac25f-127">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="ac25f-128">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="ac25f-128">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="ac25f-129">Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#.</span><span class="sxs-lookup"><span data-stu-id="ac25f-129">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="ac25f-130">Tenga en cuenta también que los requisitos previos y las instrucciones escritas dentro de este documento representan lo que se ha probado y comprobado en el momento de la escritura (2018 de mayo).</span><span class="sxs-lookup"><span data-stu-id="ac25f-130">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="ac25f-131">Puede usar el software más reciente, como se indica en el [artículo instalar las herramientas](install-the-tools.md), aunque no se debe suponer que la información de este curso se ajusta perfectamente a lo que encontrará en el software más reciente que el que se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="ac25f-131">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="ac25f-132">Se recomienda el siguiente hardware y software para este curso:</span><span class="sxs-lookup"><span data-stu-id="ac25f-132">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="ac25f-133">Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de auriculares envolvente (VR)</span><span class="sxs-lookup"><span data-stu-id="ac25f-133">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="ac25f-134">Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="ac25f-134">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ac25f-135">El SDK de Windows 10 más reciente</span><span class="sxs-lookup"><span data-stu-id="ac25f-135">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ac25f-136">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="ac25f-136">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ac25f-137">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ac25f-137">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="ac25f-138">Un [auricular de Windows Mixed Reality inmersivo (VR)](immersive-headset-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="ac25f-138">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md)</span></span>
- <span data-ttu-id="ac25f-139">Acceso a Internet para la configuración de Azure y la recuperación de datos</span><span class="sxs-lookup"><span data-stu-id="ac25f-139">Internet access for Azure setup and data retrieval</span></span>
- <span data-ttu-id="ac25f-140">Vídeos de 2 360 grados en formato MP4 (puede encontrar algunos vídeos sin derechos de autor [en esta página de descarga](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span><span class="sxs-lookup"><span data-stu-id="ac25f-140">Two 360-degree videos in mp4 format (you can find some royalty-free videos [at this download page](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span></span>

## <a name="before-you-start"></a><span data-ttu-id="ac25f-141">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="ac25f-141">Before you start</span></span>

1.  <span data-ttu-id="ac25f-142">Para evitar que se produzcan problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cerca de la raíz (las rutas de acceso de carpeta largas pueden producir problemas en tiempo de compilación).</span><span class="sxs-lookup"><span data-stu-id="ac25f-142">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="ac25f-143">Configure y pruebe sus auriculares de la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="ac25f-143">Set up and test your Mixed Reality Immersive Headset.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ac25f-144">**No** necesitará controladores de movimiento para este curso.</span><span class="sxs-lookup"><span data-stu-id="ac25f-144">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="ac25f-145">Si necesita ayuda para configurar el casco envolvente, haga clic en [el vínculo para configurar Windows Mixed Reality](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="ac25f-145">If you need support setting up the Immersive Headset, please click [link on how to set up Windows Mixed Reality](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a><span data-ttu-id="ac25f-146">Capítulo 1: Azure Portal: creación de la cuenta de Azure Storage</span><span class="sxs-lookup"><span data-stu-id="ac25f-146">Chapter 1 - The Azure Portal: creating the Azure Storage Account</span></span>

<span data-ttu-id="ac25f-147">Para usar el **servicio Azure Storage**, debe crear y configurar una **cuenta de almacenamiento** en el Azure portal.</span><span class="sxs-lookup"><span data-stu-id="ac25f-147">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="ac25f-148">Inicie sesión en el [portal de Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="ac25f-148">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="ac25f-149">Si aún no tiene una cuenta de Azure, tendrá que crear una.</span><span class="sxs-lookup"><span data-stu-id="ac25f-149">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="ac25f-150">Si sigue este tutorial en una situación de aula o de laboratorio, pregunte al instructor o a uno de los Proctors para obtener ayuda para configurar la nueva cuenta.</span><span class="sxs-lookup"><span data-stu-id="ac25f-150">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="ac25f-151">Una vez que haya iniciado sesión, haga clic en **cuentas de almacenamiento** en el menú de la izquierda.</span><span class="sxs-lookup"><span data-stu-id="ac25f-151">Once you are logged in, click on **Storage accounts** in the left menu.</span></span>

    ![Configuración de Azure Storage cuenta](images/AzureLabs-Lab6-02.png)

3.  <span data-ttu-id="ac25f-153">En la pestaña **cuentas de almacenamiento** , haga clic en **Agregar**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-153">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Configuración de Azure Storage cuenta](images/AzureLabs-Lab6-03.png)

4.  <span data-ttu-id="ac25f-155">En la pestaña **crear cuenta de almacenamiento** :</span><span class="sxs-lookup"><span data-stu-id="ac25f-155">In the **Create storage account** tab:</span></span>

    1.  <span data-ttu-id="ac25f-156">Inserte un **nombre** para la cuenta. tenga en cuenta que este campo solo acepta números y letras minúsculas.</span><span class="sxs-lookup"><span data-stu-id="ac25f-156">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="ac25f-157">En **modelo de implementación,** seleccione **Resource Manager**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-157">For **Deployment model,** select **Resource manager**.</span></span>

    3.  <span data-ttu-id="ac25f-158">En **tipo de cuenta**, seleccione **almacenamiento (uso general V1)** .</span><span class="sxs-lookup"><span data-stu-id="ac25f-158">For **Account kind**, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="ac25f-159">En **rendimiento**, seleccione \**estándar *.**</span><span class="sxs-lookup"><span data-stu-id="ac25f-159">For **Performance**, select **Standard\*.**</span></span>

    5.  <span data-ttu-id="ac25f-160">En **replicación** **, seleccione almacenamiento con redundancia local (LRS)** .</span><span class="sxs-lookup"><span data-stu-id="ac25f-160">For **Replication** select **Locally-redundant storage (LRS)**.</span></span>

    6.  <span data-ttu-id="ac25f-161">Deje la **transferencia segura requerida** como **deshabilitada**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-161">Leave **Secure transfer required** as **Disabled**.</span></span>

    7.  <span data-ttu-id="ac25f-162">Seleccione una **suscripción**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-162">Select a **Subscription**.</span></span>

    8.  <span data-ttu-id="ac25f-163">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="ac25f-163">Choose a **Resource group** or create a new one.</span></span> <span data-ttu-id="ac25f-164">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="ac25f-164">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span>

    9.  <span data-ttu-id="ac25f-165">Determine la **Ubicación** del grupo de recursos (si va a crear un nuevo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="ac25f-165">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="ac25f-166">Idealmente, la ubicación estará en la región donde se ejecutará la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ac25f-166">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="ac25f-167">Algunos recursos de Azure solo están disponibles en determinadas regiones.</span><span class="sxs-lookup"><span data-stu-id="ac25f-167">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="ac25f-168">Tendrá que confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.</span><span class="sxs-lookup"><span data-stu-id="ac25f-168">You will need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Configuración de Azure Storage cuenta](images/AzureLabs-Lab6-04.png)

6.  <span data-ttu-id="ac25f-170">Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="ac25f-170">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="ac25f-171">Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="ac25f-171">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Configuración de Azure Storage cuenta](images/AzureLabs-Lab6-05.png)

8.  <span data-ttu-id="ac25f-173">En este momento no es necesario seguir el recurso, simplemente vaya al siguiente capítulo.</span><span class="sxs-lookup"><span data-stu-id="ac25f-173">At this point you do not need to follow the resource, simply move to the next Chapter.</span></span>

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a><span data-ttu-id="ac25f-174">Capítulo 2: Azure Portal: creación del servicio multimedia</span><span class="sxs-lookup"><span data-stu-id="ac25f-174">Chapter 2 - The Azure Portal: creating the Media Service</span></span>

<span data-ttu-id="ac25f-175">Para usar Azure Media Services, debe configurar una instancia del servicio para que esté disponible para la aplicación (donde el titular de la cuenta debe ser un administrador).</span><span class="sxs-lookup"><span data-stu-id="ac25f-175">To use the Azure Media Service, you will need to configure an instance of the service to be made available to your application (wherein the account holder needs to be an Admin).</span></span>

1.  <span data-ttu-id="ac25f-176">En Azure portal, haga clic en **crear un recurso** en la esquina superior izquierda y busque **Media Service,** Presione **entrar**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-176">In the Azure Portal, click on **Create a resource** in the top left corner, and search for **Media Service,** press **Enter**.</span></span> <span data-ttu-id="ac25f-177">El recurso que desea actualmente tiene un icono de color rosa; Haga clic en esta para mostrar una nueva página.</span><span class="sxs-lookup"><span data-stu-id="ac25f-177">The resource you want currently has a pink icon; click this, to show a new page.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-06.png)

2.  <span data-ttu-id="ac25f-179">La nueva página proporcionará una descripción del **servicio multimedia**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-179">The new page will provide a description of the **Media Service**.</span></span> <span data-ttu-id="ac25f-180">En la parte inferior izquierda de este mensaje, haga clic en el botón **crear** para crear una asociación con este servicio.</span><span class="sxs-lookup"><span data-stu-id="ac25f-180">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-07.png)

3.  <span data-ttu-id="ac25f-182">Una vez que haya hecho clic en **crear** un panel, aparecerá donde debe proporcionar algunos detalles sobre el nuevo servicio multimedia:</span><span class="sxs-lookup"><span data-stu-id="ac25f-182">Once you have clicked on **Create** a panel will appear where you need to provide some details about your new Media Service:</span></span>

    1.  <span data-ttu-id="ac25f-183">Inserte el **nombre de cuenta** que desee para esta instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="ac25f-183">Insert your desired **Account Name** for this service instance.</span></span>

    2.  <span data-ttu-id="ac25f-184">Seleccione una **suscripción**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-184">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="ac25f-185">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="ac25f-185">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="ac25f-186">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="ac25f-186">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="ac25f-187">Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común).</span><span class="sxs-lookup"><span data-stu-id="ac25f-187">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 
    
    > <span data-ttu-id="ac25f-188">Si desea leer más sobre los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar grupos de recursos de Azure](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="ac25f-188">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage Azure Resource Groups](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="ac25f-189">Determine la **Ubicación** del grupo de recursos (si va a crear un nuevo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="ac25f-189">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="ac25f-190">Idealmente, la ubicación estará en la región donde se ejecutará la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ac25f-190">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="ac25f-191">Algunos recursos de Azure solo están disponibles en determinadas regiones.</span><span class="sxs-lookup"><span data-stu-id="ac25f-191">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="ac25f-192">En la sección **cuenta de almacenamiento** , haga clic en la sección **Seleccione..** . y luego haga clic en la **cuenta de almacenamiento** que creó en el último capítulo.</span><span class="sxs-lookup"><span data-stu-id="ac25f-192">For the **Storage Account** section, click the **Please select...** section, then click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="ac25f-193">También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.</span><span class="sxs-lookup"><span data-stu-id="ac25f-193">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="ac25f-194">Haz clic en **Crear**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-194">Click **Create**.</span></span>

        ![Azure portal](images/AzureLabs-Lab6-08.png)

4.  <span data-ttu-id="ac25f-196">Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="ac25f-196">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="ac25f-197">Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="ac25f-197">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-09.png)

6.  <span data-ttu-id="ac25f-199">Haga clic en la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="ac25f-199">Click on the notification to explore your new Service instance.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-10.png)

7.  <span data-ttu-id="ac25f-201">Haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="ac25f-201">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="ac25f-202">Dentro de la página nuevo servicio multimedia, dentro del panel de la izquierda, haga clic en el vínculo **activos** , que se encuentra cerca de la mitad.</span><span class="sxs-lookup"><span data-stu-id="ac25f-202">Within the new Media service page, within the panel on the left, click on the **Assets** link, which is about halfway down.</span></span>

9.  <span data-ttu-id="ac25f-203">En la página siguiente, en la esquina superior izquierda de la página, haga clic en **cargar**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-203">On the next page, in the top-left corner of the page, click **Upload**.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-11.png)

10. <span data-ttu-id="ac25f-205">Haga clic en el icono de la **carpeta** para examinar los archivos y seleccione el primer vídeo 360 que le gustaría transmitir.</span><span class="sxs-lookup"><span data-stu-id="ac25f-205">Click on the **Folder** icon to browse your files and select the first 360 Video that you would like to stream.</span></span> 
    
    > <span data-ttu-id="ac25f-206">Puede seguir este [vínculo para descargar un vídeo de ejemplo](https://vimeo.com/214401712).</span><span class="sxs-lookup"><span data-stu-id="ac25f-206">You can follow this [link to download a sample video](https://vimeo.com/214401712).</span></span>

    ![Azure portal](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> <span data-ttu-id="ac25f-208">Los nombres de archivo largos pueden producir un problema con el codificador: para asegurarse de que los vídeos no tienen problemas, considere la posibilidad de acortar la longitud de los nombres de archivo de vídeo.</span><span class="sxs-lookup"><span data-stu-id="ac25f-208">Long filenames may cause an issue with the encoder: so to ensure videos do not have issues, consider shortening the length of your video file names.</span></span>

11. <span data-ttu-id="ac25f-209">La barra de progreso se volverá verde cuando el vídeo termine de cargarse.</span><span class="sxs-lookup"><span data-stu-id="ac25f-209">The progress bar will turn green when the video has finished uploading.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-13.png)

12. <span data-ttu-id="ac25f-211">Haga clic en el texto anterior (**yourservicename-assets**) para volver a la página **activos** .</span><span class="sxs-lookup"><span data-stu-id="ac25f-211">Click on the text above (**yourservicename - Assets**) to return to the **Assets** page.</span></span>

13. <span data-ttu-id="ac25f-212">Observará que el vídeo se ha cargado correctamente.</span><span class="sxs-lookup"><span data-stu-id="ac25f-212">You will notice that your video has been successfully uploaded.</span></span> <span data-ttu-id="ac25f-213">Haga clic en él.</span><span class="sxs-lookup"><span data-stu-id="ac25f-213">Click on it.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-14.png)

14. <span data-ttu-id="ac25f-215">La página a la que se redirige le mostrará información detallada acerca del vídeo.</span><span class="sxs-lookup"><span data-stu-id="ac25f-215">The page you are redirected to will show you detailed information about your video.</span></span> <span data-ttu-id="ac25f-216">Para poder usar el vídeo debe codificarlo, haga clic en el botón **codificar** situado en la parte superior izquierda de la página.</span><span class="sxs-lookup"><span data-stu-id="ac25f-216">To be able to use your video you need to encode it, by clicking the **Encode** button at the top-left of the page.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-15.png)

15. <span data-ttu-id="ac25f-218">Aparecerá un nuevo panel a la derecha, donde podrá establecer las opciones de codificación para el archivo.</span><span class="sxs-lookup"><span data-stu-id="ac25f-218">A new panel will appear to the right, where you will be able to set encoding options for your file.</span></span> <span data-ttu-id="ac25f-219">Establezca las siguientes propiedades (algunas ya estarán establecidas de forma predeterminada):</span><span class="sxs-lookup"><span data-stu-id="ac25f-219">Set the following properties (some will be already set by default):</span></span>

    1.  <span data-ttu-id="ac25f-220">**Nombre del codificador multimedia *Media Encoder Standard***</span><span class="sxs-lookup"><span data-stu-id="ac25f-220">**Media encoder name *Media Encoder Standard***</span></span>

    2.  <span data-ttu-id="ac25f-221">**Contenido preestablecido de codificación de *varias velocidades de bits adaptables MP4***</span><span class="sxs-lookup"><span data-stu-id="ac25f-221">**Encoding preset *Content Adaptive Multiple Bitrate MP4***</span></span>

    3.  <span data-ttu-id="ac25f-222">**Nombre *del trabajo Media Encoder Standard procesamiento de VIDEO1. mp4***</span><span class="sxs-lookup"><span data-stu-id="ac25f-222">**Job name *Media Encoder Standard processing of Video1.mp4***</span></span>

    4.  <span data-ttu-id="ac25f-223">**Nombre de recurso multimedia *de salida VIDEO1. MP4: Media Encoder Standard codificado***</span><span class="sxs-lookup"><span data-stu-id="ac25f-223">**Output media asset name *Video1.mp4 -- Media Encoder Standard encoded***</span></span>

        ![Azure portal](images/AzureLabs-Lab6-16.png)

16. <span data-ttu-id="ac25f-225">Haga clic en el botón **Crear**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-225">Click the **Create** button.</span></span>

17. <span data-ttu-id="ac25f-226">Observará que se **ha agregado**una barra con el trabajo de codificación, haga clic en esa barra y aparecerá un panel con el progreso de la codificación que se muestra en ella.</span><span class="sxs-lookup"><span data-stu-id="ac25f-226">You will notice a bar with **Encoding job added**, click on that bar and a panel will appear with the Encoding progress displayed in it.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-17.png)

    ![Azure portal](images/AzureLabs-Lab6-18.png)

18. <span data-ttu-id="ac25f-229">Espere a que se complete el trabajo.</span><span class="sxs-lookup"><span data-stu-id="ac25f-229">Wait for the Job to be completed.</span></span> <span data-ttu-id="ac25f-230">Una vez hecho esto, no dude en cerrar el panel con la "X" en la parte superior derecha de ese panel.</span><span class="sxs-lookup"><span data-stu-id="ac25f-230">Once it is done, feel free to close the panel with the 'X' at the top right of that panel.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-19.png)

    ![Azure portal](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > <span data-ttu-id="ac25f-233">El tiempo que tarda, depende del tamaño de archivo del vídeo.</span><span class="sxs-lookup"><span data-stu-id="ac25f-233">The time this takes, depends on the file size of your video.</span></span> <span data-ttu-id="ac25f-234">Este proceso puede tardar bastante tiempo.</span><span class="sxs-lookup"><span data-stu-id="ac25f-234">This process can take quite some time.</span></span>

19. <span data-ttu-id="ac25f-235">Ahora que se ha creado la versión codificada del vídeo, puede publicarla para que sea accesible.</span><span class="sxs-lookup"><span data-stu-id="ac25f-235">Now that the encoded version of the video has been created, you can publish it to make it accessible.</span></span> <span data-ttu-id="ac25f-236">Para ello, haga clic en los **recursos** de vínculo azul para volver a la página activos.</span><span class="sxs-lookup"><span data-stu-id="ac25f-236">To do so, click the blue link **Assets** to go back to the assets page.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-21.png)

20. <span data-ttu-id="ac25f-238">Verá el vídeo junto con otro, que es el tipo de **recurso _MP4 de velocidad de bits múltiple_** .</span><span class="sxs-lookup"><span data-stu-id="ac25f-238">You will see your video along with another, which is of **Asset Type _Multi-Bitrate MP4_**.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > <span data-ttu-id="ac25f-240">Es posible que observe que el nuevo recurso, junto con el vídeo inicial, es *desconocido*y tiene ' 0 ' bytes para su **tamaño**, solo tiene que actualizar la ventana para que se actualice.</span><span class="sxs-lookup"><span data-stu-id="ac25f-240">You may notice that the new asset, alongside your initial video, is *Unknown*, and has '0' bytes for it's **Size**, just refresh your window for it to update.</span></span>

21. <span data-ttu-id="ac25f-241">Haga clic en este nuevo recurso.</span><span class="sxs-lookup"><span data-stu-id="ac25f-241">Click this new asset.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-23.png)

22. <span data-ttu-id="ac25f-243">Verá un panel similar al que usó antes, solo que se trata de un recurso diferente.</span><span class="sxs-lookup"><span data-stu-id="ac25f-243">You will see a similar panel to the one you used before, just this is a different asset.</span></span> <span data-ttu-id="ac25f-244">Haga clic en el botón **publicar** situado en el centro superior de la página.</span><span class="sxs-lookup"><span data-stu-id="ac25f-244">Click the **Publish** button located at the top-center of the page.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-24.png)

23. <span data-ttu-id="ac25f-246">Se le pedirá que establezca un **localizador**, que es el punto de entrada, en archivo/s en los recursos.</span><span class="sxs-lookup"><span data-stu-id="ac25f-246">You will be prompted to set a **Locator**, which is the entry point, to file/s in your Assets.</span></span> <span data-ttu-id="ac25f-247">En el escenario, establezca las siguientes propiedades:</span><span class="sxs-lookup"><span data-stu-id="ac25f-247">For your scenario set the following properties:</span></span>

    1.  <span data-ttu-id="ac25f-248">**Tipo de localizador** > **progresiva**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-248">**Locator type** > **Progressive**.</span></span>

    2.  <span data-ttu-id="ac25f-249">La **fecha** y la **hora** se establecerán automáticamente, desde la fecha actual, hasta una hora futura (100 años en este caso).</span><span class="sxs-lookup"><span data-stu-id="ac25f-249">The **date** and **time** will be set for you, from your current date, to a time in the future (one hundred years in this case).</span></span> <span data-ttu-id="ac25f-250">Deje tal cual o cámbielo para adaptarse.</span><span class="sxs-lookup"><span data-stu-id="ac25f-250">Leave as is or change it to suit.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ac25f-251">Para obtener más información acerca de los localizadores y lo que puede elegir, visite la [documentación de Azure Media Services](https://docs.microsoft.com/azure/media-services/media-services-concepts).</span><span class="sxs-lookup"><span data-stu-id="ac25f-251">For more information about Locators, and what you can choose, visit the [Azure Media Services Documentation](https://docs.microsoft.com/azure/media-services/media-services-concepts).</span></span>

24. <span data-ttu-id="ac25f-252">En la parte inferior de ese panel, haga clic en el botón **Agregar** .</span><span class="sxs-lookup"><span data-stu-id="ac25f-252">At the bottom of that panel, click on the **Add** button.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-25.png)

25. <span data-ttu-id="ac25f-254">El vídeo ya está publicado y se puede transmitir mediante su punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="ac25f-254">Your video is now published and can be streamed by using its endpoint.</span></span> <span data-ttu-id="ac25f-255">Más abajo, la página es una sección de **archivos** .</span><span class="sxs-lookup"><span data-stu-id="ac25f-255">Further down the page is a **Files** section.</span></span> <span data-ttu-id="ac25f-256">Aquí es donde serán las distintas versiones codificadas del vídeo.</span><span class="sxs-lookup"><span data-stu-id="ac25f-256">This is where the different encoded versions of your video will be.</span></span> <span data-ttu-id="ac25f-257">Seleccione la resolución más alta posible (en la imagen siguiente es el archivo 1920x960) y, a continuación, aparecerá un panel a la derecha.</span><span class="sxs-lookup"><span data-stu-id="ac25f-257">Select the highest possible resolution one (in the image below it is the 1920x960 file), and then a panel to the right will appear.</span></span> <span data-ttu-id="ac25f-258">Allí encontrará una **dirección URL de descarga**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-258">There you will find a **Download URL**.</span></span> <span data-ttu-id="ac25f-259">Copie este **punto de conexión** , ya que lo usará más adelante en el código.</span><span class="sxs-lookup"><span data-stu-id="ac25f-259">Copy this **Endpoint** as you will use it later in your code.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-26.png)    

    ![Azure portal](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > <span data-ttu-id="ac25f-262">También puede hacer clic en el botón **reproducir** para reproducir el vídeo y probarlo.</span><span class="sxs-lookup"><span data-stu-id="ac25f-262">You can also press the **Play** button to play your video and test it.</span></span>

26. <span data-ttu-id="ac25f-263">Ahora debe cargar el segundo vídeo que usará en este laboratorio.</span><span class="sxs-lookup"><span data-stu-id="ac25f-263">You now need to upload the second video that you will use in this Lab.</span></span> <span data-ttu-id="ac25f-264">Siga los pasos anteriores y repita el mismo proceso para el segundo vídeo.</span><span class="sxs-lookup"><span data-stu-id="ac25f-264">Follow the steps above, repeating the same process for the second video.</span></span> <span data-ttu-id="ac25f-265">Asegúrese de copiar también el segundo **punto de conexión** .</span><span class="sxs-lookup"><span data-stu-id="ac25f-265">Ensure you copy the second **Endpoint** also.</span></span> <span data-ttu-id="ac25f-266">Use el siguiente [vínculo para descargar un segundo vídeo](https://vimeo.com/214402865).</span><span class="sxs-lookup"><span data-stu-id="ac25f-266">Use the following [link to download a second video](https://vimeo.com/214402865).</span></span>

27. <span data-ttu-id="ac25f-267">Una vez publicados ambos vídeos, está listo para pasar al siguiente capítulo.</span><span class="sxs-lookup"><span data-stu-id="ac25f-267">Once both videos have been published, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="ac25f-268">Capítulo 3: configuración del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="ac25f-268">Chapter 3 - Setting up the Unity Project</span></span>

<span data-ttu-id="ac25f-269">Lo siguiente es una configuración típica para desarrollar con la realidad mixta y, como tal, es una buena plantilla para otros proyectos.</span><span class="sxs-lookup"><span data-stu-id="ac25f-269">The following is a typical set up for developing with the Mixed Reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="ac25f-270">Abra **Unity** y haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-270">Open **Unity** and click **New**.</span></span> 

    ![Azure portal](images/AzureLabs-Lab6-28.png)

2.  <span data-ttu-id="ac25f-272">Ahora tendrá que proporcionar un nombre de proyecto de Unity, insertar **MR\_360VideoStreaming.** .</span><span class="sxs-lookup"><span data-stu-id="ac25f-272">You will now need to provide a Unity Project name, insert **MR\_360VideoStreaming.**.</span></span> <span data-ttu-id="ac25f-273">Asegúrese de que el tipo de proyecto está establecido en **3D**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-273">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="ac25f-274">Establezca la ubicación en algún lugar adecuado para usted (Recuerde que, más cerca de los directorios raíz es mejor).</span><span class="sxs-lookup"><span data-stu-id="ac25f-274">Set the Location to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="ac25f-275">A continuación, haga clic en **crear proyecto**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-275">Then, click **Create project**.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-29.png)

3.  <span data-ttu-id="ac25f-277">Con Unity abierto, merece la pena comprobar que el **Editor de scripts** predeterminado está establecido en **Visual Studio.**</span><span class="sxs-lookup"><span data-stu-id="ac25f-277">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio.**</span></span> <span data-ttu-id="ac25f-278">Vaya a ***Editar* *preferencias*** y, a continuación, en la nueva ventana, vaya a **herramientas externas**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-278">Go to ***Edit* *Preferences*** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="ac25f-279">Cambie el **Editor de script externo** a **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-279">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="ac25f-280">Cierre la ventana **preferencias** .</span><span class="sxs-lookup"><span data-stu-id="ac25f-280">Close the **Preferences** window.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-30.png)

4.  <span data-ttu-id="ac25f-282">A continuación, vaya a configuración de compilación de ***archivos*** y cambie la plataforma a **plataforma universal de Windows**, haciendo clic en el botón **cambiar plataforma** .</span><span class="sxs-lookup"><span data-stu-id="ac25f-282">Next, go to ***File* *Build Settings*** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

5.  <span data-ttu-id="ac25f-283">Asegúrese también de que:</span><span class="sxs-lookup"><span data-stu-id="ac25f-283">Also make sure that:</span></span>

    1. <span data-ttu-id="ac25f-284">El **dispositivo de destino** se establece en **cualquier dispositivo.**</span><span class="sxs-lookup"><span data-stu-id="ac25f-284">**Target Device** is set to **Any Device.**</span></span>
    
    2.  <span data-ttu-id="ac25f-285">El **tipo de compilación** se establece en **D3D.**</span><span class="sxs-lookup"><span data-stu-id="ac25f-285">**Build Type** is set to **D3D.**</span></span>

    3.  <span data-ttu-id="ac25f-286">**SDK** está establecido en **instalado más recientemente.**</span><span class="sxs-lookup"><span data-stu-id="ac25f-286">**SDK** is set to **Latest installed.**</span></span>

    4.  <span data-ttu-id="ac25f-287">La **versión de Visual Studio** está establecida en **instalación más reciente.**</span><span class="sxs-lookup"><span data-stu-id="ac25f-287">**Visual Studio Version** is set to **Latest installed.**</span></span>

    5.  <span data-ttu-id="ac25f-288">**Compilar y ejecutar** está establecido en **equipo local.**</span><span class="sxs-lookup"><span data-stu-id="ac25f-288">**Build and Run** is set to **Local Machine.**</span></span>

    6.  <span data-ttu-id="ac25f-289">No se preocupe por la configuración de **escenas** en este momento, ya que las configurará más adelante.</span><span class="sxs-lookup"><span data-stu-id="ac25f-289">Do not worry about setting up **Scenes** right now, as you will set these up later.</span></span>

    7.  <span data-ttu-id="ac25f-290">El resto de la configuración debe dejarse como predeterminada por ahora.</span><span class="sxs-lookup"><span data-stu-id="ac25f-290">The remaining settings should be left as default for now.</span></span>

        ![Configuración del proyecto de Unity](images/AzureLabs-Lab6-31.png)

6.  <span data-ttu-id="ac25f-292">En la ventana **configuración de compilación** , haga clic en el botón Configuración del **reproductor** ; se abrirá el panel relacionado en el espacio donde se encuentra el **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="ac25f-292">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

7. <span data-ttu-id="ac25f-293">En este panel, deben comprobarse algunas opciones de configuración:</span><span class="sxs-lookup"><span data-stu-id="ac25f-293">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="ac25f-294">En la pestaña **otros valores** :</span><span class="sxs-lookup"><span data-stu-id="ac25f-294">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="ac25f-295">La versión de **scripting** **en tiempo de ejecución** debe ser **estable** (.net 3,5 equivalente).</span><span class="sxs-lookup"><span data-stu-id="ac25f-295">**Scripting** **Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>

        2. <span data-ttu-id="ac25f-296">El **back-end de scripting** debe ser **.net.**</span><span class="sxs-lookup"><span data-stu-id="ac25f-296">**Scripting Backend** should be **.NET.**</span></span>

        3. <span data-ttu-id="ac25f-297">El **nivel de compatibilidad de API** debe ser **.net 4,6.**</span><span class="sxs-lookup"><span data-stu-id="ac25f-297">**API Compatibility Level** should be **.NET 4.6.**</span></span>

            ![Configuración del proyecto de Unity](images/AzureLabs-Lab6-32.png)

    2.  <span data-ttu-id="ac25f-299">Más abajo en el panel, en la **configuración de XR** (se encuentra debajo de **configuración de publicación**), tick **Virtual Reality compatible**, asegúrese de que se agrega el **SDK de Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="ac25f-299">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Configuración del proyecto de Unity](images/AzureLabs-Lab6-33.png)

    3.  <span data-ttu-id="ac25f-301">En la pestaña **configuración de publicación** , en **capacidades**, seleccione:</span><span class="sxs-lookup"><span data-stu-id="ac25f-301">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="ac25f-302">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="ac25f-302">**InternetClient**</span></span>

            ![Configuración del proyecto de Unity](images/AzureLabs-Lab6-34.png)

8.  <span data-ttu-id="ac25f-304">Una vez realizados los cambios, cierre la ventana **configuración de compilación** .</span><span class="sxs-lookup"><span data-stu-id="ac25f-304">Once you have made those changes, close the **Build Settings** window.</span></span>

9.  <span data-ttu-id="ac25f-305">Guarde el proyecto \**archivo* \* guardar proyecto \* \*.</span><span class="sxs-lookup"><span data-stu-id="ac25f-305">Save your Project \**File* \*Save Project\*\*.</span></span>



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a><span data-ttu-id="ac25f-306">Capítulo 4: importación del paquete Unity de InsideOutSphere</span><span class="sxs-lookup"><span data-stu-id="ac25f-306">Chapter 4 - Importing the InsideOutSphere Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ac25f-307">Si desea omitir el componente *de configuración de Unity* de este curso y continuar directamente en el código, no dude en descargar este [. unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), impórtelo en el proyecto como un [**paquete personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)y, después, continúe con el **capítulo 5**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-307">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from **Chapter 5**.</span></span> <span data-ttu-id="ac25f-308">Todavía tendrá que crear un proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="ac25f-308">You will still need to create a Unity Project.</span></span>

<span data-ttu-id="ac25f-309">En este curso, deberá descargar un paquete de recursos de Unity llamado [**InsideOutSphere. unitypackage Tools**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="ac25f-309">For this course you will need to download a Unity Asset Package called [**InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).</span></span>

<span data-ttu-id="ac25f-310">Cómo importar **unitypackage Tools**:</span><span class="sxs-lookup"><span data-stu-id="ac25f-310">How-to import the **unitypackage**:</span></span>

1.  <span data-ttu-id="ac25f-311">Con el panel de Unity delante de usted, haga clic en **recursos** en el menú de la parte superior de la pantalla y, a continuación, haga clic en **importar paquete > paquete personalizado**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-311">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![Importación del paquete Unity de InsideOutSphere](images/AzureLabs-Lab6-35.png)

2.  <span data-ttu-id="ac25f-313">Use el selector de archivos para seleccionar el paquete **InsideOutSphere. unitypackage Tools** y haga clic en **abrir**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-313">Use the file picker to select the **InsideOutSphere.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="ac25f-314">Se le mostrará una lista de los componentes de este recurso.</span><span class="sxs-lookup"><span data-stu-id="ac25f-314">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="ac25f-315">Confirme la importación haciendo clic en **importar**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-315">Confirm the import by clicking **Import**.</span></span>

    ![Importación del paquete Unity de InsideOutSphere](images/AzureLabs-Lab6-36.png)

3.  <span data-ttu-id="ac25f-317">Una vez que haya finalizado la importación, observará que se han agregado tres nuevas carpetas, **materiales**, **modelos**y **Prefabs**a la carpeta **assets** .</span><span class="sxs-lookup"><span data-stu-id="ac25f-317">Once it has finished importing, you will notice three new folders, **Materials**, **Models**, and **Prefabs**, have been added to your **Assets** folder.</span></span> <span data-ttu-id="ac25f-318">Este tipo de estructura de carpetas es típico para un proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="ac25f-318">This kind of folder structure is typical for a Unity project.</span></span>

    ![Importación del paquete Unity de InsideOutSphere](images/AzureLabs-Lab6-37.png)

    1.  <span data-ttu-id="ac25f-320">Abra la carpeta **modelos** y verá que se ha importado el modelo **InsideOutSphere** .</span><span class="sxs-lookup"><span data-stu-id="ac25f-320">Open the **Models** folder, and you will see that the **InsideOutSphere** model has been imported.</span></span>

    2.  <span data-ttu-id="ac25f-321">En la carpeta **materiales** encontrará el **InsideOutSpheres** material *lambert1*, junto con un material denominado *ButtonMaterial*, que se usa en el GazeButton, que verá en breve.</span><span class="sxs-lookup"><span data-stu-id="ac25f-321">Within the **Materials** folder you will find the **InsideOutSpheres** material  *lambert1*, along with a material called *ButtonMaterial*, which is used by the GazeButton, which you will see soon.</span></span>

    3.  <span data-ttu-id="ac25f-322">La carpeta **Prefabs** contiene recurso prefabricado **InsideOutSphere** , que contiene el modelo **InsideOutSphere** y el *GazeButton*.</span><span class="sxs-lookup"><span data-stu-id="ac25f-322">The **Prefabs** folder contains the **InsideOutSphere** prefab which contains both the **InsideOutSphere** *model* and the *GazeButton*.</span></span>

    4.  <span data-ttu-id="ac25f-323">**No se incluye ningún código**, se escribirá el código siguiendo este curso.</span><span class="sxs-lookup"><span data-stu-id="ac25f-323">**No code is included**, you will write the code by following this course.</span></span>


4.  <span data-ttu-id="ac25f-324">Dentro de la **jerarquía**, seleccione el objeto de **cámara principal** y actualice los siguientes componentes:</span><span class="sxs-lookup"><span data-stu-id="ac25f-324">Within the **Hierarchy**, select the **Main Camera** object, and update the following components:</span></span>

    1.  <span data-ttu-id="ac25f-325">**Transformación**</span><span class="sxs-lookup"><span data-stu-id="ac25f-325">**Transform**</span></span>

        1.  <span data-ttu-id="ac25f-326">Position = **X**: 0, **y**: 0, **Z**: 0.</span><span class="sxs-lookup"><span data-stu-id="ac25f-326">Position = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        2. <span data-ttu-id="ac25f-327">Rotation = **X**: 0, **y**: 0, **Z**: 0.</span><span class="sxs-lookup"><span data-stu-id="ac25f-327">Rotation = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        3. <span data-ttu-id="ac25f-328">Escala **X**: 1, **y**: 1, **Z**: 1.</span><span class="sxs-lookup"><span data-stu-id="ac25f-328">Scale **X**: 1, **Y**: 1, **Z**: 1.</span></span>

    2.  <span data-ttu-id="ac25f-329">**Cámara**</span><span class="sxs-lookup"><span data-stu-id="ac25f-329">**Camera**</span></span>

        1. <span data-ttu-id="ac25f-330">**Borrar marcas**: color sólido.</span><span class="sxs-lookup"><span data-stu-id="ac25f-330">**Clear Flags**: Solid Color.</span></span>

        2.  <span data-ttu-id="ac25f-331">**Planos de recorte**: Near: 0,1, Far: 6.</span><span class="sxs-lookup"><span data-stu-id="ac25f-331">**Clipping Planes**: Near: 0.1, Far: 6.</span></span>

            ![Importación del paquete Unity de InsideOutSphere](images/AzureLabs-Lab6-38.png)

5.  <span data-ttu-id="ac25f-333">Navegue hasta la carpeta **recurso prefabricado** y, a continuación, arrastre **InsideOutSphere** recurso prefabricado al panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="ac25f-333">Navigate to the **Prefab** folder, and then drag the **InsideOutSphere** prefab into the **Hierarchy** Panel.</span></span>

    ![Importación del paquete Unity de InsideOutSphere](images/AzureLabs-Lab6-39.png)

6.  <span data-ttu-id="ac25f-335">Expanda el objeto **InsideOutSphere** dentro de la **jerarquía** haciendo clic en la pequeña flecha situada junto a él.</span><span class="sxs-lookup"><span data-stu-id="ac25f-335">Expand the **InsideOutSphere** object within the **Hierarchy** by clicking the little arrow next to it.</span></span> <span data-ttu-id="ac25f-336">Verá un objeto **secundario** debajo de él denominado **GazeButton**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-336">You will see a **child** object beneath it called **GazeButton**.</span></span> <span data-ttu-id="ac25f-337">Se usará para cambiar escenas y, por lo tanto, vídeos.</span><span class="sxs-lookup"><span data-stu-id="ac25f-337">This will be used to change scenes and thus videos.</span></span>

    ![Importación del paquete Unity de InsideOutSphere](images/AzureLabs-Lab6-40.png)

7.  <span data-ttu-id="ac25f-339">En la ventana del inspector, haga clic en el componente de transformación de **InsideOutSphere**, asegúrese de que se establecen las siguientes propiedades:</span><span class="sxs-lookup"><span data-stu-id="ac25f-339">In the Inspector Window click on the **InsideOutSphere**'s Transform component, ensure that the following properties are set:</span></span>

    |            |    <span data-ttu-id="ac25f-340">TRANSFORMACIÓN: POSICIÓN</span><span class="sxs-lookup"><span data-stu-id="ac25f-340">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="ac25f-341">**X** 0</span><span class="sxs-lookup"><span data-stu-id="ac25f-341">**X** 0</span></span>  |          <span data-ttu-id="ac25f-342">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="ac25f-342">**Y** 0</span></span>          |  <span data-ttu-id="ac25f-343">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="ac25f-343">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="ac25f-344">TRANSFORMACIÓN-GIRO</span><span class="sxs-lookup"><span data-stu-id="ac25f-344">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="ac25f-345">**X** 0</span><span class="sxs-lookup"><span data-stu-id="ac25f-345">**X** 0</span></span>  |          <span data-ttu-id="ac25f-346">**Y** -50</span><span class="sxs-lookup"><span data-stu-id="ac25f-346">**Y** -50</span></span>        |  <span data-ttu-id="ac25f-347">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="ac25f-347">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="ac25f-348">TRANSFORMACIÓN DE ESCALA</span><span class="sxs-lookup"><span data-stu-id="ac25f-348">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="ac25f-349">**X** 1</span><span class="sxs-lookup"><span data-stu-id="ac25f-349">**X** 1</span></span>   |          <span data-ttu-id="ac25f-350">**S** 1</span><span class="sxs-lookup"><span data-stu-id="ac25f-350">**Y** 1</span></span>          |  <span data-ttu-id="ac25f-351">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="ac25f-351">**Z** 1</span></span>  |

    ![Importación del paquete Unity de InsideOutSphere](images/AzureLabs-Lab6-41.png)

8.  <span data-ttu-id="ac25f-353">Haga clic en el objeto secundario **GazeButton** y establezca su **transformación** como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="ac25f-353">Click on the **GazeButton** child object, and set its **Transform** as follows:</span></span>

    |            |    <span data-ttu-id="ac25f-354">TRANSFORMACIÓN: POSICIÓN</span><span class="sxs-lookup"><span data-stu-id="ac25f-354">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="ac25f-355">**X** 3,6</span><span class="sxs-lookup"><span data-stu-id="ac25f-355">**X** 3.6</span></span>|          <span data-ttu-id="ac25f-356">**Y** 1,3</span><span class="sxs-lookup"><span data-stu-id="ac25f-356">**Y** 1.3</span></span>        |  <span data-ttu-id="ac25f-357">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="ac25f-357">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="ac25f-358">TRANSFORMACIÓN-GIRO</span><span class="sxs-lookup"><span data-stu-id="ac25f-358">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="ac25f-359">**X** 0</span><span class="sxs-lookup"><span data-stu-id="ac25f-359">**X** 0</span></span>  |          <span data-ttu-id="ac25f-360">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="ac25f-360">**Y** 0</span></span>          |  <span data-ttu-id="ac25f-361">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="ac25f-361">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="ac25f-362">TRANSFORMACIÓN DE ESCALA</span><span class="sxs-lookup"><span data-stu-id="ac25f-362">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="ac25f-363">**X** 1</span><span class="sxs-lookup"><span data-stu-id="ac25f-363">**X** 1</span></span>   |          <span data-ttu-id="ac25f-364">**S** 1</span><span class="sxs-lookup"><span data-stu-id="ac25f-364">**Y** 1</span></span>          |  <span data-ttu-id="ac25f-365">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="ac25f-365">**Z** 1</span></span>  |

    ![Importación del paquete Unity de InsideOutSphere](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a><span data-ttu-id="ac25f-367">Capítulo 5: creación de la clase videocontroller</span><span class="sxs-lookup"><span data-stu-id="ac25f-367">Chapter 5 - Create the VideoController class</span></span>

<span data-ttu-id="ac25f-368">La clase **videocontroller** hospeda los dos puntos de conexión de vídeo que se usarán para transmitir el contenido de Azure Media Services.</span><span class="sxs-lookup"><span data-stu-id="ac25f-368">The **VideoController** class hosts the two video endpoints that will be used to stream the content from the Azure Media Service.</span></span>

<span data-ttu-id="ac25f-369">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="ac25f-369">To create this class:</span></span>

1.  <span data-ttu-id="ac25f-370">Haga clic con el botón derecho en la **carpeta de recursos**, que se encuentra en el panel **proyecto** , y haga clic en **crear > carpeta**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-370">Right-click in the **Asset Folder**, located in the **Project** Panel, and click **Create > Folder**.</span></span> <span data-ttu-id="ac25f-371">Asigne a la carpeta el nombre **scripts**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-371">Name the folder **Scripts**.</span></span>

    ![Creación de la clase videocontroller](images/AzureLabs-Lab6-43.png)

    ![Creación de la clase videocontroller](images/AzureLabs-Lab6-44.png)

2.  <span data-ttu-id="ac25f-374">Haga doble clic en la carpeta **scripts** para abrirla.</span><span class="sxs-lookup"><span data-stu-id="ac25f-374">Double click on the **Scripts** folder to open it.</span></span>

3.  <span data-ttu-id="ac25f-375">Haga clic con el botón derecho en la carpeta y, a continuación, haga clic en **crear > C\# script**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-375">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="ac25f-376">Asigne un nombre al **videocontrolador**del script.</span><span class="sxs-lookup"><span data-stu-id="ac25f-376">Name the script **VideoController**.</span></span>

    ![Creación de la clase videocontroller](images/AzureLabs-Lab6-45.png)

4.  <span data-ttu-id="ac25f-378">Haga doble clic en el nuevo script **videocontroller** para abrirlo con **Visual Studio 2017.**</span><span class="sxs-lookup"><span data-stu-id="ac25f-378">Double click on the new **VideoController** script to open it with **Visual Studio 2017.**</span></span>

    ![Creación de la clase videocontroller](images/AzureLabs-Lab6-46.png)

5.  <span data-ttu-id="ac25f-380">Actualice los espacios de nombres en la parte superior del archivo de código como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="ac25f-380">Update the namespaces at the top of the code file as follows:</span></span>

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  <span data-ttu-id="ac25f-381">Escriba las siguientes variables en la clase **videocontroller** , junto con el método **activo ()** :</span><span class="sxs-lookup"><span data-stu-id="ac25f-381">Enter the following variables in the **VideoController** class, along with the **Awake()** method:</span></span>

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static VideoController instance; 
        
        /// <summary> 
        /// Reference to the Camera VideoPlayer Component.
        /// </summary> 
        private VideoPlayer videoPlayer; 
        
        /// <summary>
        /// Reference to the Camera AudioSource Component.
        /// </summary> 
        private AudioSource audioSource; 
        
        /// <summary> 
        /// Reference to the texture used to project the video streaming 
        /// </summary> 
        private RenderTexture videoStreamRenderTexture;

        /// <summary>
        /// Insert here the first video endpoint
        /// </summary>
        private string video1endpoint = "-- Insert video 1 Endpoint here --";

        /// <summary>
        /// Insert here the second video endpoint
        /// </summary>
        private string video2endpoint = "-- Insert video 2 Endpoint here --";

        /// <summary> 
        /// Reference to the Inside-Out Sphere. 
        /// </summary> 
        public GameObject sphere;

        void Awake()
        {
            instance = this;
        }
    ```

7.  <span data-ttu-id="ac25f-382">Ahora es el momento de escribir los puntos de conexión de los vídeos de Azure Media Services:</span><span class="sxs-lookup"><span data-stu-id="ac25f-382">Now is the time to enter the endpoints from your Azure Media Service videos:</span></span>

    1.  <span data-ttu-id="ac25f-383">El primero en la variable *video1endpoint* .</span><span class="sxs-lookup"><span data-stu-id="ac25f-383">The first into the *video1endpoint* variable.</span></span>
    
    2.  <span data-ttu-id="ac25f-384">El segundo en la variable *video2endpoint* .</span><span class="sxs-lookup"><span data-stu-id="ac25f-384">The second into the *video2endpoint* variable.</span></span>

    > [!WARNING]
    > <span data-ttu-id="ac25f-385">Existe un problema conocido con el uso de *https* en Unity, con la versión 2017.4.1 F1.</span><span class="sxs-lookup"><span data-stu-id="ac25f-385">There is a known issue with using *https* within Unity, with version 2017.4.1f1.</span></span> <span data-ttu-id="ac25f-386">Si los vídeos proporcionan un error en la reproducción, pruebe a usar ' http ' en su lugar.</span><span class="sxs-lookup"><span data-stu-id="ac25f-386">If the videos provide an error on play, try using 'http' instead.</span></span>

8.  <span data-ttu-id="ac25f-387">A continuación, es necesario editar el método **Start ()** .</span><span class="sxs-lookup"><span data-stu-id="ac25f-387">Next, the **Start()** method needs to be edited.</span></span> <span data-ttu-id="ac25f-388">Este método se desencadenará cada vez que el usuario cambie la escena (por lo tanto, cambiando el vídeo) examinando el botón de mira.</span><span class="sxs-lookup"><span data-stu-id="ac25f-388">This method will be triggered every time the user switches scene (consequently switching the video) by looking at the Gaze Button.</span></span>

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  <span data-ttu-id="ac25f-389">Después del método **Start ()** , inserte el método *IEnumerator* **PlayVideo ()** , que se usará para iniciar vídeos sin problemas (por lo que no se verá ningún salto).</span><span class="sxs-lookup"><span data-stu-id="ac25f-389">Following the **Start()** method, insert the **PlayVideo()** *IEnumerator* method, which will be used to start videos seamlessly (so no stutter is seen).</span></span>

    ```csharp
        private IEnumerator PlayVideo()
        {
            // create a new render texture to display the video 
            videoStreamRenderTexture = new RenderTexture(2160, 1440, 32, RenderTextureFormat.ARGB32);

            videoStreamRenderTexture.Create();

            // assign the render texture to the object material 
            Material sphereMaterial = sphere.GetComponent<Renderer>().sharedMaterial;

            //create a VideoPlayer component 
            videoPlayer = gameObject.AddComponent<VideoPlayer>();

            // Set the video to loop. 
            videoPlayer.isLooping = true;

            // Set the VideoPlayer component to play the video from the texture 
            videoPlayer.renderMode = VideoRenderMode.RenderTexture;

            videoPlayer.targetTexture = videoStreamRenderTexture;

            // Add AudioSource 
            audioSource = gameObject.AddComponent<AudioSource>();

            // Pause Audio play on Awake 
            audioSource.playOnAwake = true;
            audioSource.Pause();

            // Set Audio Output to AudioSource 
            videoPlayer.audioOutputMode = VideoAudioOutputMode.AudioSource;
            videoPlayer.source = VideoSource.Url;

            // Assign the Audio from Video to AudioSource to be played 
            videoPlayer.EnableAudioTrack(0, true);
            videoPlayer.SetTargetAudioSource(0, audioSource);

            // Assign the video Url depending on the current scene 
            switch (SceneManager.GetActiveScene().name)
            {
                case "VideoScene1":
                    videoPlayer.url = video1endpoint;
                    break;

                case "VideoScene2":
                    videoPlayer.url = video2endpoint;
                    break;

                default:
                    break;
            }

            //Set video To Play then prepare Audio to prevent Buffering 
            videoPlayer.Prepare();

            while (!videoPlayer.isPrepared)
            {
                yield return null;
            }

            sphereMaterial.mainTexture = videoStreamRenderTexture;

            //Play Video 
            videoPlayer.Play();

            //Play Sound 
            audioSource.Play();

            while (videoPlayer.isPlaying)
            {
                yield return null;
            }
        }
    ```

10. <span data-ttu-id="ac25f-390">El último método que necesita para esta clase es el método **ChangeScene ()** , que se usará para intercambiar entre las escenas.</span><span class="sxs-lookup"><span data-stu-id="ac25f-390">The last method you need for this class is the **ChangeScene()** method, which will be used to swap between scenes.</span></span>

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > <span data-ttu-id="ac25f-391">El método **ChangeScene ()** utiliza una sencilla característica de C\# denominada *operador condicional*.</span><span class="sxs-lookup"><span data-stu-id="ac25f-391">The **ChangeScene()** method uses a handy C\# feature called the *Conditional Operator*.</span></span> <span data-ttu-id="ac25f-392">Esto permite comprobar las condiciones y, después, los valores devueltos en función del resultado de la comprobación, todo dentro de una única instrucción.</span><span class="sxs-lookup"><span data-stu-id="ac25f-392">This allows for conditions to be checked, and then values returned based on the outcome of the check, all within a single statement.</span></span> <span data-ttu-id="ac25f-393">Siga este [vínculo para obtener más información acerca del operador condicional](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).</span><span class="sxs-lookup"><span data-stu-id="ac25f-393">Follow this [link to learn more about Conditional Operator](https://docs.microsoft.com/dotnet/csharp/language-reference/operators/conditional-operator).</span></span>

11. <span data-ttu-id="ac25f-394">Guarde los cambios en Visual Studio antes de volver a Unity.</span><span class="sxs-lookup"><span data-stu-id="ac25f-394">Save your changes in Visual Studio before returning to Unity.</span></span>

12. <span data-ttu-id="ac25f-395">De nuevo en el editor de Unity, haga clic y arrastre la clase **videocontroller** [desde] {. Underline} la carpeta **scripts** al objeto de **cámara principal** en el panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="ac25f-395">Back in the Unity Editor, click and drag the **VideoController** class [from]{.underline} the **Scripts** folder to the **Main Camera** object in the **Hierarchy** Panel.</span></span>

13. <span data-ttu-id="ac25f-396">Haga clic en la **cámara principal** y mire en el **panel del inspector**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-396">Click on the **Main Camera** and look at the **Inspector Panel**.</span></span> <span data-ttu-id="ac25f-397">Observará que, dentro del componente de script recién agregado, hay un campo con un valor vacío.</span><span class="sxs-lookup"><span data-stu-id="ac25f-397">You will notice that within the newly added Script component, there is a field with an empty value.</span></span> <span data-ttu-id="ac25f-398">Se trata de un campo de referencia, que tiene como destino las variables públicas del código.</span><span class="sxs-lookup"><span data-stu-id="ac25f-398">This is a reference field, which targets the public variables within your code.</span></span>

14. <span data-ttu-id="ac25f-399">Arrastre el objeto **InsideOutSphere** desde el **Panel jerarquía** hasta la ranura de la **esfera** , tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="ac25f-399">Drag the **InsideOutSphere** object from the **Hierarchy Panel** to the **Sphere** slot, as shown in the image below.</span></span>

    <span data-ttu-id="ac25f-400">![crear la clase videocontroller](images/AzureLabs-Lab6-47.png)
    ![crear la clase videocontroller](images/AzureLabs-Lab6-48.png)</span><span class="sxs-lookup"><span data-stu-id="ac25f-400">![Create the VideoController class](images/AzureLabs-Lab6-47.png)
![Create the VideoController class](images/AzureLabs-Lab6-48.png)</span></span>

## <a name="chapter-6---create-the-gaze-class"></a><span data-ttu-id="ac25f-401">Capítulo 6: crear la clase fijamente</span><span class="sxs-lookup"><span data-stu-id="ac25f-401">Chapter 6 - Create the Gaze class</span></span>

<span data-ttu-id="ac25f-402">Esta clase es responsable de crear un **Raycast** que se proyectará hacia delante desde la **cámara principal**, para detectar qué objeto está examinando el usuario.</span><span class="sxs-lookup"><span data-stu-id="ac25f-402">This class is responsible for creating a **Raycast** that will be projected forward from the **Main Camera**, to detect which object the user is looking at.</span></span> <span data-ttu-id="ac25f-403">En este caso, **Raycast** deberá identificar si el usuario mira el objeto **GazeButton** en la escena y desencadena un comportamiento.</span><span class="sxs-lookup"><span data-stu-id="ac25f-403">In this case, the **Raycast** will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="ac25f-404">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="ac25f-404">To create this Class:</span></span>

1.  <span data-ttu-id="ac25f-405">Vaya a la carpeta **scripts** que creó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="ac25f-405">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="ac25f-406">Haga clic con el botón derecho en el panel **proyecto** , \**crear* \* C\# script \* \*.</span><span class="sxs-lookup"><span data-stu-id="ac25f-406">Right-click in the **Project** Panel, \**Create* \*C\# Script\*\*.</span></span> <span data-ttu-id="ac25f-407">Asigne un nombre **al script.**</span><span class="sxs-lookup"><span data-stu-id="ac25f-407">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="ac25f-408">Haga doble clic en el nuevo script de ***miraciones*** para abrirlo con **Visual Studio 2017.**</span><span class="sxs-lookup"><span data-stu-id="ac25f-408">Double click on the new ***Gaze*** script to open it with **Visual Studio 2017.**</span></span>

4.  <span data-ttu-id="ac25f-409">Asegúrese de que el siguiente espacio de nombres se encuentra en la parte superior del script y quite los demás:</span><span class="sxs-lookup"><span data-stu-id="ac25f-409">Ensure the following namespace is at the top of the script, and remove any others:</span></span>

    ```csharp
    using UnityEngine;
    ```

5.  <span data-ttu-id="ac25f-410">Después, agregue las siguientes variables dentro de la clase **mirate** :</span><span class="sxs-lookup"><span data-stu-id="ac25f-410">Then add the following variables inside the **Gaze** class:</span></span>

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static Gaze instance;

        /// <summary> 
        /// Provides a reference to the object the user is currently looking at. 
        /// </summary> 
        public GameObject FocusedGameObject { get; private set; }

        /// <summary> 
        /// Provides a reference to compare whether the user is still looking at 
        /// the same object (and has not looked away). 
        /// </summary> 
        private GameObject oldFocusedObject = null;

        /// <summary> 
        /// Max Ray Distance 
        /// </summary> 
        float gazeMaxDistance = 300;

        /// <summary> 
        /// Provides whether an object has been successfully hit by the raycast. 
        /// </summary> 
        public bool Hit { get; private set; }
    ```

6.  <span data-ttu-id="ac25f-411">Ahora es necesario agregar el código para los métodos **activo ()** e **Inicio ()** .</span><span class="sxs-lookup"><span data-stu-id="ac25f-411">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton 
            instance = this;
        }

        void Start()
        {
            FocusedGameObject = null;
        }
    ```

7.  <span data-ttu-id="ac25f-412">Agregue el código siguiente en el método **Update ()** para proyectar un Raycast y detectar el acierto de destino:</span><span class="sxs-lookup"><span data-stu-id="ac25f-412">Add the following code in the **Update()** method to project a Raycast and detect the target hit:</span></span>

    ```csharp
        void Update()
        {
            // Set the old focused gameobject. 
            oldFocusedObject = FocusedGameObject;
            RaycastHit hitInfo;

            // Initialise Raycasting. 
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, gazeMaxDistance);

            // Check whether raycast has hit. 
            if (Hit == true)
            {
                // Check whether the hit has a collider. 
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at. 
                    FocusedGameObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null. 
                    FocusedGameObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;
            }

            // Check whether the previous focused object is this same 
            // object (so to stop spamming of function). 
            if (FocusedGameObject != oldFocusedObject)
            {
                // Compare whether the new Focused Object has the desired tag we set previously. 
                if (FocusedGameObject.CompareTag("GazeButton"))
                {
                    FocusedGameObject.SetActive(false);
                    VideoController.instance.ChangeScene();
                }
            }
        }
    ```

8.  <span data-ttu-id="ac25f-413">Guarde los cambios en Visual Studio antes de volver a Unity.</span><span class="sxs-lookup"><span data-stu-id="ac25f-413">Save your changes in Visual Studio before returning to Unity.</span></span>

9.  <span data-ttu-id="ac25f-414">Haga clic y arrastre la clase **mira** desde la carpeta scripts hasta el objeto cámara principal en el panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="ac25f-414">Click and drag the **Gaze** class from the Scripts folder to the Main Camera object in the **Hierarchy** Panel.</span></span>

## <a name="chapter-7---setup-the-two-unity-scenes"></a><span data-ttu-id="ac25f-415">Capítulo 7: configuración de las dos escenas de Unity</span><span class="sxs-lookup"><span data-stu-id="ac25f-415">Chapter 7 - Setup the two Unity Scenes</span></span>

<span data-ttu-id="ac25f-416">El propósito de este capítulo es configurar las dos escenas, cada una de las cuales hospeda un vídeo para la transmisión.</span><span class="sxs-lookup"><span data-stu-id="ac25f-416">The purpose of this Chapter is to setup the two scenes, each hosting a video to stream.</span></span> <span data-ttu-id="ac25f-417">Duplicará la escena que ya ha creado, de modo que no necesite configurarla de nuevo, aunque después modificará la nueva escena, de modo que el objeto *GazeButton* esté en una ubicación diferente y tenga un aspecto diferente.</span><span class="sxs-lookup"><span data-stu-id="ac25f-417">You will duplicate the scene you have already created, so that you do not need to set it up again, though you will then edit the new scene, so that the *GazeButton* object is in a different location and has a different appearance.</span></span> <span data-ttu-id="ac25f-418">Esto es para mostrar cómo cambiar entre escenas.</span><span class="sxs-lookup"><span data-stu-id="ac25f-418">This is to show how to change between scenes.</span></span>

1.  <span data-ttu-id="ac25f-419">Para ello, vaya a **archivo > guardar la escena como...** . Aparecerá una ventana de guardar.</span><span class="sxs-lookup"><span data-stu-id="ac25f-419">Do this by going to **File > Save Scene as...**. A save window will appear.</span></span> <span data-ttu-id="ac25f-420">Haga clic en el botón **nueva carpeta** .</span><span class="sxs-lookup"><span data-stu-id="ac25f-420">Click the **New folder** button.</span></span>

    ![Capítulo 7: configuración de las dos escenas de Unity](images/AzureLabs-Lab6-49.png)

2.  <span data-ttu-id="ac25f-422">Asigne a la carpeta el nombre **Scenes**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-422">Name the folder **Scenes**.</span></span>

3.  <span data-ttu-id="ac25f-423">La ventana **Guardar escena** permanecerá abierta.</span><span class="sxs-lookup"><span data-stu-id="ac25f-423">The **Save Scene** window will still be open.</span></span> <span data-ttu-id="ac25f-424">Abra la carpeta de **escenas** recién creada.</span><span class="sxs-lookup"><span data-stu-id="ac25f-424">Open your newly created **Scenes** folder.</span></span>

4.  <span data-ttu-id="ac25f-425">En el campo **nombre de archivo:** , escriba **VideoScene1**y, a continuación, presione **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-425">In the **File name:** text field, type **VideoScene1**, then press **Save**.</span></span>

5.  <span data-ttu-id="ac25f-426">De nuevo en Unity, abra la carpeta **Scenes** y haga clic con el botón primario en el archivo **VideoScene1** .</span><span class="sxs-lookup"><span data-stu-id="ac25f-426">Back in Unity, open your **Scenes** folder, and left-click your **VideoScene1** file.</span></span> <span data-ttu-id="ac25f-427">Usar el teclado y presionar **Ctrl + D** se duplicará la escena</span><span class="sxs-lookup"><span data-stu-id="ac25f-427">Use your keyboard, and press **Ctrl + D** you will duplicate that scene</span></span>

    > [!TIP]
    > <span data-ttu-id="ac25f-428">El comando **duplicado** también puede realizarse desplazándose a **Editar > duplicar**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-428">The **Duplicate** command can also be performed by navigating to **Edit > Duplicate**.</span></span>

6.  <span data-ttu-id="ac25f-429">Unity incrementará automáticamente el número de nombres de escena, pero Compruébelo de todos modos para asegurarse de que coincide con el código insertado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="ac25f-429">Unity will automatically increment the scene names number, but check it anyway, to ensure it matches the previously inserted code.</span></span>

    >  <span data-ttu-id="ac25f-430">Debe tener **VideoScene1** y **VideoScene2**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-430">You should have **VideoScene1** and **VideoScene2**.</span></span>

7.  <span data-ttu-id="ac25f-431">Con las dos escenas, vaya a **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-431">With your two scenes, go to **File > Build Settings**.</span></span> <span data-ttu-id="ac25f-432">Con la ventana **configuración de compilación** abierta, arrastre las escenas hasta la sección **escenas en la compilación** .</span><span class="sxs-lookup"><span data-stu-id="ac25f-432">With the **Build Settings** window open, drag your scenes to the **Scenes in Build** section.</span></span>

    ![Capítulo 7: configuración de las dos escenas de Unity](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > <span data-ttu-id="ac25f-434">Puede seleccionar las dos escenas de la carpeta **Scenes** mientras mantiene presionado el botón **Ctrl** y, a continuación, hacer clic con el botón izquierdo en cada escena y, por último, arrastrar ambas cosas.</span><span class="sxs-lookup"><span data-stu-id="ac25f-434">You can select both of your scenes from your **Scenes** folder through holding the **Ctrl** button, and then left-clicking each scene, and finally drag both across.</span></span>

8.  <span data-ttu-id="ac25f-435">Cierre la ventana **configuración de compilación** y haga doble clic en **VideoScene2**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-435">Close the **Build Settings** window, and double click on **VideoScene2**.</span></span>

9.  <span data-ttu-id="ac25f-436">Con la segunda escena abierta, haga clic en el objeto secundario **GazeButton** de **InsideOutSphere**y establezca su transformación como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="ac25f-436">With the second scene open, click on the **GazeButton** child object of the **InsideOutSphere**, and set its Transform as follows:</span></span>

    |            |    <span data-ttu-id="ac25f-437">TRANSFORMACIÓN: POSICIÓN</span><span class="sxs-lookup"><span data-stu-id="ac25f-437">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="ac25f-438">**X** 0</span><span class="sxs-lookup"><span data-stu-id="ac25f-438">**X** 0</span></span>  |         <span data-ttu-id="ac25f-439">**Y** 1,3</span><span class="sxs-lookup"><span data-stu-id="ac25f-439">**Y** 1.3</span></span>         | <span data-ttu-id="ac25f-440">**Z** 3,6</span><span class="sxs-lookup"><span data-stu-id="ac25f-440">**Z** 3.6</span></span> |

    |            |    <span data-ttu-id="ac25f-441">TRANSFORMACIÓN-GIRO</span><span class="sxs-lookup"><span data-stu-id="ac25f-441">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="ac25f-442">**X** 0</span><span class="sxs-lookup"><span data-stu-id="ac25f-442">**X** 0</span></span>  |          <span data-ttu-id="ac25f-443">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="ac25f-443">**Y** 0</span></span>          |  <span data-ttu-id="ac25f-444">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="ac25f-444">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="ac25f-445">TRANSFORMACIÓN DE ESCALA</span><span class="sxs-lookup"><span data-stu-id="ac25f-445">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="ac25f-446">**X** 1</span><span class="sxs-lookup"><span data-stu-id="ac25f-446">**X** 1</span></span>   |          <span data-ttu-id="ac25f-447">**S** 1</span><span class="sxs-lookup"><span data-stu-id="ac25f-447">**Y** 1</span></span>          |  <span data-ttu-id="ac25f-448">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="ac25f-448">**Z** 1</span></span>  |

10. <span data-ttu-id="ac25f-449">Con el elemento secundario **GazeButton** todavía seleccionado, fíjese en el **Inspector** y en el **filtro de malla**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-449">With the **GazeButton** child still selected, look at the **Inspector** and at the **Mesh Filter**.</span></span> <span data-ttu-id="ac25f-450">Haga clic en el destino pequeño junto al campo de referencia de la **malla** :</span><span class="sxs-lookup"><span data-stu-id="ac25f-450">Click the little target next to the **Mesh** reference field:</span></span>

    ![Capítulo 7: configuración de las dos escenas de Unity](images/AzureLabs-Lab6-51.png)

11. <span data-ttu-id="ac25f-452">Aparecerá una ventana emergente de **la malla seleccionada** .</span><span class="sxs-lookup"><span data-stu-id="ac25f-452">A **Select Mesh** popup window will appear.</span></span> <span data-ttu-id="ac25f-453">Haga doble clic en la malla del **cubo** de la lista de **activos**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-453">Double click the **Cube** mesh from the list of **Assets**.</span></span>

    ![Capítulo 7: configuración de las dos escenas de Unity](images/AzureLabs-Lab6-52.png)

12. <span data-ttu-id="ac25f-455">El **filtro de malla** se actualizará y ahora será un **cubo**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-455">The **Mesh Filter** will update, and now be a **Cube**.</span></span> <span data-ttu-id="ac25f-456">Ahora, haga clic en el icono de **engranaje** junto a **Sphere Colisionador** y haga clic en **quitar componente**para eliminar el Colisionador de este objeto.</span><span class="sxs-lookup"><span data-stu-id="ac25f-456">Now, click the **Gear** icon next to **Sphere Collider** and click **Remove Component**, to delete the collider from this object.</span></span>

    ![Capítulo 7: configuración de las dos escenas de Unity](images/AzureLabs-Lab6-53.png)

13. <span data-ttu-id="ac25f-458">Con el **GazeButton** aún seleccionado, haga clic en el botón **Agregar componente** situado en la parte inferior del **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-458">With the **GazeButton** still selected, click the **Add Component** button at the bottom of the **Inspector**.</span></span> <span data-ttu-id="ac25f-459">En el campo de búsqueda, escriba **Box**y **Box Colisionador** será una opción; haga clic en él para agregar un **Colisionador de cuadro** al objeto **GazeButton** .</span><span class="sxs-lookup"><span data-stu-id="ac25f-459">In the search field, type **box**, and **Box Collider** will be an option -- click that, to add a **Box Collider** to your **GazeButton** object.</span></span>

    ![Capítulo 7: configuración de las dos escenas de Unity](images/AzureLabs-Lab6-54.png)

14. <span data-ttu-id="ac25f-461">El **GazeButton** se ha actualizado de forma parcial para que tenga un aspecto diferente. sin embargo, ahora creará un nuevo **material**, de modo que tenga un aspecto completamente diferente y sea más fácil de reconocer como un objeto diferente, que el objeto de la primera escena.</span><span class="sxs-lookup"><span data-stu-id="ac25f-461">The **GazeButton** is now partially updated, to look different, however, you will now create a new **Material**, so that it looks completely different, and is easier to recognize as a different object, than the object in the first scene.</span></span>

15. <span data-ttu-id="ac25f-462">Vaya a la carpeta **materiales** , dentro del **panel Proyecto**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-462">Navigate to your **Materials** folder, within the **Project Panel**.</span></span> <span data-ttu-id="ac25f-463">Duplique el material de **ButtonMaterial** (presione **Ctrl** + **D** en el teclado o haga clic con el botón primario en el **material**y, a continuación, en la opción de menú **Editar** archivo, seleccione **duplicar**).</span><span class="sxs-lookup"><span data-stu-id="ac25f-463">Duplicate the **ButtonMaterial** Material (press **Ctrl** + **D** on the keyboard, or left-click the **Material**, then from the **Edit** file menu option, select **Duplicate**).</span></span>

    <span data-ttu-id="ac25f-464">![capítulo 7: configuración de las dos escenas de Unity](images/AzureLabs-Lab6-55.png)
    ![capítulo 7: configuración de las dos escenas de Unity](images/AzureLabs-Lab6-56.png)</span><span class="sxs-lookup"><span data-stu-id="ac25f-464">![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-55.png)
![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-56.png)</span></span>

16. <span data-ttu-id="ac25f-465">Seleccione el nuevo material de **ButtonMaterial** (aquí llamado **ButtonMaterial 1**) y, dentro del **Inspector**, haga clic en la ventana color **Albedo** .</span><span class="sxs-lookup"><span data-stu-id="ac25f-465">Select the new **ButtonMaterial** Material (here named **ButtonMaterial 1**), and within the **Inspector**, click the **Albedo** color window.</span></span> <span data-ttu-id="ac25f-466">Aparecerá un menú emergente en el que podrá seleccionar otro color (elija el que desee) y, a continuación, cerrar el elemento emergente.</span><span class="sxs-lookup"><span data-stu-id="ac25f-466">A popup will appear, where you can select another color (choose whichever you like), then close the popup.</span></span> <span data-ttu-id="ac25f-467">El material será su propia instancia y diferente al original.</span><span class="sxs-lookup"><span data-stu-id="ac25f-467">The Material will be its own instance, and different to the original.</span></span>

    ![Capítulo 7: configuración de las dos escenas de Unity](images/AzureLabs-Lab6-57.png)

17. <span data-ttu-id="ac25f-469">Arrastre el nuevo **material** hasta el elemento secundario **GazeButton** y, a continuación, actualice su apariencia para que se pueda distinguir fácilmente del primer botón de escenas.</span><span class="sxs-lookup"><span data-stu-id="ac25f-469">Drag the new **Material** onto the **GazeButton** child, to now completely update its look, so that it is easily distinguishable from the first scenes button.</span></span>

    ![Capítulo 7: configuración de las dos escenas de Unity](images/AzureLabs-Lab6-58.png)

18. <span data-ttu-id="ac25f-471">Llegados a este punto, puede probar el proyecto en el editor antes de compilar el proyecto de UWP.</span><span class="sxs-lookup"><span data-stu-id="ac25f-471">At this point you can test the project in the Editor before building the UWP project.</span></span>

    -  <span data-ttu-id="ac25f-472">Presione el botón de **reproducción** en el **Editor** y desgaste el casco.</span><span class="sxs-lookup"><span data-stu-id="ac25f-472">Press the **Play** button in the **Editor** and wear your headset.</span></span>

        ![Capítulo 7: configuración de las dos escenas de Unity](images/AzureLabs-Lab6-59.png)

19. <span data-ttu-id="ac25f-474">Examine los dos objetos **GazeButton** para cambiar entre el primer y el segundo vídeo.</span><span class="sxs-lookup"><span data-stu-id="ac25f-474">Look at the two **GazeButton** objects to switch between the first and second video.</span></span>

## <a name="chapter-8---build-the-uwp-solution"></a><span data-ttu-id="ac25f-475">Capítulo 8: compilar la solución de UWP</span><span class="sxs-lookup"><span data-stu-id="ac25f-475">Chapter 8 - Build the UWP Solution</span></span>

<span data-ttu-id="ac25f-476">Una vez que se ha asegurado de que el editor no tiene errores, está listo para compilar.</span><span class="sxs-lookup"><span data-stu-id="ac25f-476">Once you have ensured that the editor has no errors, you are ready to Build.</span></span>

<span data-ttu-id="ac25f-477">Para compilar:</span><span class="sxs-lookup"><span data-stu-id="ac25f-477">To Build:</span></span>

1.  <span data-ttu-id="ac25f-478">Guarde la escena actual haciendo clic en **archivo > guardar**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-478">Save the current scene by clicking on **File > Save**.</span></span>

2.  <span data-ttu-id="ac25f-479">Active la casilla llamada **Unity C\# proyectos** (esto es importante porque le permitirá editar las clases una vez completada la compilación).</span><span class="sxs-lookup"><span data-stu-id="ac25f-479">Check the box called **Unity C\# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

3.  <span data-ttu-id="ac25f-480">Vaya a **archivo > configuración de compilación**y haga clic en **compilar**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-480">Go to **File > Build Settings**, click on **Build**.</span></span>

4.  <span data-ttu-id="ac25f-481">Se le pedirá que seleccione la carpeta en la que desea compilar la solución.</span><span class="sxs-lookup"><span data-stu-id="ac25f-481">You will be prompted to select the folder where you want to build the Solution.</span></span>

5.  <span data-ttu-id="ac25f-482">Cree una carpeta **compilaciones** y, dentro de esa carpeta, cree otra carpeta con un nombre adecuado de su elección.</span><span class="sxs-lookup"><span data-stu-id="ac25f-482">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

6.  <span data-ttu-id="ac25f-483">Haga clic en la nueva carpeta y, a continuación, haga clic en **Seleccionar carpeta**para que se inicie la compilación en esa ubicación.</span><span class="sxs-lookup"><span data-stu-id="ac25f-483">Click your new folder and then click **Select Folder**, so to choose that folder, to begin the build at that location.</span></span>

    <span data-ttu-id="ac25f-484">![el capítulo 8: compilar la solución UWP](images/AzureLabs-Lab6-60.png)
    ![capítulo 8: compilar la solución UWP](images/AzureLabs-Lab6-61.png)</span><span class="sxs-lookup"><span data-stu-id="ac25f-484">![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-60.png)
![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-61.png)</span></span>

7.  <span data-ttu-id="ac25f-485">Una vez que Unity termine de compilar (puede tardar algún tiempo), se abrirá una ventana del **Explorador de archivos** en la ubicación de la compilación.</span><span class="sxs-lookup"><span data-stu-id="ac25f-485">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build.</span></span>

## <a name="chapter-9---deploy-on-local-machine"></a><span data-ttu-id="ac25f-486">Capítulo 9: implementación en el equipo local</span><span class="sxs-lookup"><span data-stu-id="ac25f-486">Chapter 9 - Deploy on Local Machine</span></span>

<span data-ttu-id="ac25f-487">Una vez completada la compilación, aparecerá una ventana del **Explorador de archivos** en la ubicación de la compilación.</span><span class="sxs-lookup"><span data-stu-id="ac25f-487">Once the build has been completed, a **File Explorer** window will appear at the location of your build.</span></span> <span data-ttu-id="ac25f-488">Abra la carpeta con el nombre y la compilación en y, a continuación, haga doble clic en el archivo de solución (. sln) dentro de esa carpeta para abrir la solución con Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="ac25f-488">Open the Folder you named and built to, then double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>

<span data-ttu-id="ac25f-489">Lo único que queda por hacer es implementar la aplicación en el equipo (o *equipo local*).</span><span class="sxs-lookup"><span data-stu-id="ac25f-489">The only thing left to do is deploy your app to your computer (or *Local Machine*).</span></span>

<span data-ttu-id="ac25f-490">Para implementar en la máquina local:</span><span class="sxs-lookup"><span data-stu-id="ac25f-490">To deploy to Local Machine:</span></span>

1.  <span data-ttu-id="ac25f-491">En **Visual Studio 2017**, abra el archivo de solución que acaba de crear.</span><span class="sxs-lookup"><span data-stu-id="ac25f-491">In **Visual Studio 2017**, open the solution file that has just been created.</span></span>

2.  <span data-ttu-id="ac25f-492">En la **plataforma**de la solución, seleccione **x86, equipo local**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-492">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="ac25f-493">En la **configuración de soluciones** , seleccione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="ac25f-493">In the **Solution Configuration** select **Debug**.</span></span>

    ![Capítulo 9: implementación en el equipo local](images/AzureLabs-Lab6-62.png)

4.  <span data-ttu-id="ac25f-495">Ahora tendrá que restaurar los paquetes en la solución.</span><span class="sxs-lookup"><span data-stu-id="ac25f-495">You will now need to restore any packages to your solution.</span></span> <span data-ttu-id="ac25f-496">Haga clic con el botón derecho en la **solución**y haga clic en **restaurar paquetes NuGet para la solución...**</span><span class="sxs-lookup"><span data-stu-id="ac25f-496">Right-click on your **Solution**, and click **Restore NuGet Packages for Solution...**</span></span>

    > [!NOTE] 
    > <span data-ttu-id="ac25f-497">Esto se hace porque los paquetes compilados por Unity deben estar destinados a funcionar con las referencias de los equipos locales.</span><span class="sxs-lookup"><span data-stu-id="ac25f-497">This is done because the packages which Unity built need to be targeted to work with your local machines references.</span></span>

5.  <span data-ttu-id="ac25f-498">Vaya al **menú compilar** y haga clic en **implementar solución** para transferir localmente la aplicación a la máquina.</span><span class="sxs-lookup"><span data-stu-id="ac25f-498">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span> <span data-ttu-id="ac25f-499">Visual Studio compilará primero y, a continuación, implementará la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ac25f-499">Visual Studio will first build and then deploy your application.</span></span>

6.  <span data-ttu-id="ac25f-500">La aplicación debe aparecer ahora en la lista de aplicaciones instaladas, lista para iniciarse.</span><span class="sxs-lookup"><span data-stu-id="ac25f-500">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

    ![Capítulo 9: implementación en el equipo local](images/AzureLabs-Lab6-63.png)

<span data-ttu-id="ac25f-502">Al ejecutar la aplicación de realidad mixta, se encontrará dentro del modelo **InsideOutSphere** que usó en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ac25f-502">When you run the Mixed Reality application, you will you be within the **InsideOutSphere** model which you used within your app.</span></span> <span data-ttu-id="ac25f-503">Esta esfera será el lugar al que se transmitirá el vídeo, lo que proporciona una vista de 360 grados del vídeo entrante (que se filmó para este tipo de perspectiva).</span><span class="sxs-lookup"><span data-stu-id="ac25f-503">This sphere will be where the video will be streamed to, providing a 360-degree view, of the incoming video (which was filmed for this kind of perspective).</span></span> <span data-ttu-id="ac25f-504">No se sorprenda si el vídeo tarda un par de segundos en cargarse, la aplicación está sujeta a la velocidad de Internet disponible, ya que el vídeo debe capturarse y descargarse, por lo que debe transmitirse a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ac25f-504">Do not be surprised if the video takes a couple of seconds to load, your app is subject to your available Internet speed, as the video needs to be fetched and then downloaded, so to stream into your app.</span></span>
<span data-ttu-id="ac25f-505">Cuando esté listo, cambie las escenas y abra el segundo vídeo, Gazing en la esfera roja.</span><span class="sxs-lookup"><span data-stu-id="ac25f-505">When you are ready, change scenes and open your second video, by gazing at the red sphere!</span></span> <span data-ttu-id="ac25f-506">Después, no dude en volver, usando el cubo azul en la segunda escena.</span><span class="sxs-lookup"><span data-stu-id="ac25f-506">Then feel free to go back, using the blue cube in the second scene!</span></span>

## <a name="your-finished-azure-media-service-application"></a><span data-ttu-id="ac25f-507">Su aplicación finalizada de Azure Media Services</span><span class="sxs-lookup"><span data-stu-id="ac25f-507">Your finished Azure Media Service application</span></span>
 
<span data-ttu-id="ac25f-508">Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha Azure Media Services para transmitir vídeos de 360.</span><span class="sxs-lookup"><span data-stu-id="ac25f-508">Congratulations, you built a mixed reality app that leverages the Azure Media Service to stream 360 videos.</span></span>

![resultado de laboratorio](images/AzureLabs-Lab6-00.png)

![resultado de laboratorio](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a><span data-ttu-id="ac25f-511">Ejercicios de bonus</span><span class="sxs-lookup"><span data-stu-id="ac25f-511">Bonus Exercises</span></span>

<span data-ttu-id="ac25f-512">**Ejercicio 1**</span><span class="sxs-lookup"><span data-stu-id="ac25f-512">**Exercise 1**</span></span>

<span data-ttu-id="ac25f-513">Es totalmente posible usar una sola escena para cambiar vídeos en este tutorial.</span><span class="sxs-lookup"><span data-stu-id="ac25f-513">It is entirely possible to only use a single scene to change videos within this tutorial.</span></span> <span data-ttu-id="ac25f-514">Experimente con la aplicación y conviértalo en una sola escena.</span><span class="sxs-lookup"><span data-stu-id="ac25f-514">Experiment with your application and make it into a single scene!</span></span> <span data-ttu-id="ac25f-515">Quizás incluso agregue otro vídeo a la combinación.</span><span class="sxs-lookup"><span data-stu-id="ac25f-515">Perhaps even add another video to the mix.</span></span>

<span data-ttu-id="ac25f-516">**Ejercicio 2**</span><span class="sxs-lookup"><span data-stu-id="ac25f-516">**Exercise 2**</span></span>

<span data-ttu-id="ac25f-517">Experimente con Azure y Unity e intente implementar la capacidad de la aplicación para seleccionar automáticamente un vídeo con un tamaño de archivo diferente, en función de la seguridad de una conexión a Internet.</span><span class="sxs-lookup"><span data-stu-id="ac25f-517">Experiment with Azure and Unity, and attempt to implement the ability for the app to automatically select a video with a different file size, depending on the strength of an Internet connection.</span></span>


