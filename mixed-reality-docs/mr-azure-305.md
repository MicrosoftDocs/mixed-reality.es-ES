---
title: 'MR y Azure 305: funciones y almacenamiento'
description: Complete este curso para aprender a implementar Azure Storage y funciones en una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academia, Unity, tutorial, API, funciones, almacenamiento, hololens, envolventes, VR
ms.openlocfilehash: 79c276d45163465c9921d02343d41d52d5f094e7
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437988"
---
>[!NOTE]
><span data-ttu-id="601bd-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="601bd-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="601bd-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="601bd-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="601bd-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="601bd-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="601bd-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="601bd-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="601bd-108">Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="601bd-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="601bd-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.</span><span class="sxs-lookup"><span data-stu-id="601bd-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a><span data-ttu-id="601bd-110">MR y Azure 305: funciones y almacenamiento</span><span class="sxs-lookup"><span data-stu-id="601bd-110">MR and Azure 305: Functions and storage</span></span>

![Inicio del producto final](images/AzureLabs-Lab5-00.png)

<span data-ttu-id="601bd-112">En este curso, aprenderá a crear y usar Azure Functions y almacenar datos con un recurso Azure Storage, dentro de una aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="601bd-112">In this course, you will learn how to create and use Azure Functions and store data with an Azure Storage resource, within a mixed reality application.</span></span>

<span data-ttu-id="601bd-113">*Azure Functions* es un servicio de Microsoft, que permite a los desarrolladores ejecutar pequeños fragmentos de código, "funciones", en Azure.</span><span class="sxs-lookup"><span data-stu-id="601bd-113">*Azure Functions* is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="601bd-114">Esto proporciona una manera de delegar el trabajo en la nube, en lugar de la aplicación local, que puede tener muchas ventajas.</span><span class="sxs-lookup"><span data-stu-id="601bd-114">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="601bd-115">*Azure Functions* admite varios lenguajes de desarrollo, como C\#, F\#, node. js, Java y php.</span><span class="sxs-lookup"><span data-stu-id="601bd-115">*Azure Functions* supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="601bd-116">Para obtener más información, visite el [artículo Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="601bd-116">For more information, visit the [Azure Functions article](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="601bd-117">*Azure Storage* es un servicio en la nube de Microsoft, que permite a los desarrolladores almacenar datos, con el seguro de que estará altamente disponible, seguro, duradero, escalable y redundante.</span><span class="sxs-lookup"><span data-stu-id="601bd-117">*Azure Storage* is a Microsoft cloud service, which allows developers to store data, with the insurance that it will be highly available, secure, durable, scalable, and redundant.</span></span> <span data-ttu-id="601bd-118">Esto significa que Microsoft administrará todo el mantenimiento y los problemas críticos.</span><span class="sxs-lookup"><span data-stu-id="601bd-118">This means Microsoft will handle all maintenance, and critical problems for you.</span></span> <span data-ttu-id="601bd-119">Para obtener más información, visite el [artículo Azure Storage](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span><span class="sxs-lookup"><span data-stu-id="601bd-119">For more information, visit the [Azure Storage article](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span></span>

<span data-ttu-id="601bd-120">Una vez finalizado este curso, tendrá una aplicación de auriculares con un casco de realidad mixta que podrá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="601bd-120">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="601bd-121">Permite al usuario mirarse en una escena.</span><span class="sxs-lookup"><span data-stu-id="601bd-121">Allow the user to gaze around a scene.</span></span>
2.  <span data-ttu-id="601bd-122">Desencadenar la generación de objetos cuando el usuario mira en un "botón" 3D.</span><span class="sxs-lookup"><span data-stu-id="601bd-122">Trigger the spawning of objects when the user gazes at a 3D 'button'.</span></span>
3.  <span data-ttu-id="601bd-123">Los objetos generados serán elegidos por una función de Azure.</span><span class="sxs-lookup"><span data-stu-id="601bd-123">The spawned objects will be chosen by an Azure Function.</span></span>
4.  <span data-ttu-id="601bd-124">A medida que se genera cada objeto, la aplicación almacenará el tipo de objeto en un *archivo de Azure*, que se encuentra en *Azure Storage*.</span><span class="sxs-lookup"><span data-stu-id="601bd-124">As each object is spawned, the application will store the object type in an *Azure File*, located in *Azure Storage*.</span></span>
5.  <span data-ttu-id="601bd-125">Tras la carga por segunda vez, los datos del *archivo de Azure* se recuperarán y se usarán para reproducir las acciones de generación de la instancia anterior de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="601bd-125">Upon loading a second time, the *Azure File* data will be retrieved, and used to replay the spawning actions from the previous instance of the application.</span></span>

<span data-ttu-id="601bd-126">En su aplicación, depende del modo en que va a integrar los resultados con el diseño.</span><span class="sxs-lookup"><span data-stu-id="601bd-126">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="601bd-127">Este curso está diseñado para enseñarle a integrar un servicio de Azure con su proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="601bd-127">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="601bd-128">Es su trabajo usar el conocimiento que obtiene de este curso para mejorar su aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="601bd-128">It is your job to use the knowledge you gain from this course to enhance your mixed reality Application.</span></span>

## <a name="device-support"></a><span data-ttu-id="601bd-129">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="601bd-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="601bd-130">Recurso</span><span class="sxs-lookup"><span data-stu-id="601bd-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="601bd-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="601bd-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="601bd-132"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="601bd-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="601bd-133">MR y Azure 305: funciones y almacenamiento</span><span class="sxs-lookup"><span data-stu-id="601bd-133">MR and Azure 305: Functions and storage</span></span></td><td style="text-align: center;"> <span data-ttu-id="601bd-134">✔️</span><span class="sxs-lookup"><span data-stu-id="601bd-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="601bd-135">✔️</span><span class="sxs-lookup"><span data-stu-id="601bd-135">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="601bd-136">Aunque este curso se centra principalmente en los auriculares de Windows Mixed Reality inmersivo (VR), también puede aplicar lo que aprenda en este curso a Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="601bd-136">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="601bd-137">A medida que siga con el curso, verá notas sobre cualquier cambio que deba usar para admitir HoloLens.</span><span class="sxs-lookup"><span data-stu-id="601bd-137">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="601bd-138">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="601bd-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="601bd-139">Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#.</span><span class="sxs-lookup"><span data-stu-id="601bd-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="601bd-140">Tenga en cuenta también que los requisitos previos y las instrucciones escritas dentro de este documento representan lo que se ha probado y comprobado en el momento de la escritura (2018 de mayo).</span><span class="sxs-lookup"><span data-stu-id="601bd-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="601bd-141">Puede usar el software más reciente, como se indica en el artículo [instalar las herramientas](install-the-tools.md) , aunque no se debe suponer que la información de este curso se ajusta perfectamente a lo que encontrará en el software más reciente que el que se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="601bd-141">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="601bd-142">Se recomienda el siguiente hardware y software para este curso:</span><span class="sxs-lookup"><span data-stu-id="601bd-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="601bd-143">Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de auriculares envolvente (VR)</span><span class="sxs-lookup"><span data-stu-id="601bd-143">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="601bd-144">Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="601bd-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="601bd-145">El SDK de Windows 10 más reciente</span><span class="sxs-lookup"><span data-stu-id="601bd-145">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="601bd-146">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="601bd-146">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="601bd-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="601bd-147">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="601bd-148">Un [auricular de Windows Mixed Reality inmersivo (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="601bd-148">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="601bd-149">Una suscripción a una cuenta de Azure para crear recursos de Azure</span><span class="sxs-lookup"><span data-stu-id="601bd-149">A subscription to an Azure account for creating Azure resources</span></span>
- <span data-ttu-id="601bd-150">Acceso a Internet para la configuración de Azure y la recuperación de datos</span><span class="sxs-lookup"><span data-stu-id="601bd-150">Internet access for Azure setup and data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="601bd-151">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="601bd-151">Before you start</span></span>

<span data-ttu-id="601bd-152">Para evitar que se produzcan problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cerca de la raíz (las rutas de acceso de carpeta largas pueden producir problemas en tiempo de compilación).</span><span class="sxs-lookup"><span data-stu-id="601bd-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="601bd-153">Capítulo 1: Azure portal</span><span class="sxs-lookup"><span data-stu-id="601bd-153">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="601bd-154">Para usar el **servicio Azure Storage**, debe crear y configurar una **cuenta de almacenamiento** en el Azure portal.</span><span class="sxs-lookup"><span data-stu-id="601bd-154">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="601bd-155">Inicie sesión en el [portal de Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="601bd-155">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="601bd-156">Si aún no tiene una cuenta de Azure, tendrá que crear una.</span><span class="sxs-lookup"><span data-stu-id="601bd-156">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="601bd-157">Si sigue este tutorial en una situación de aula o de laboratorio, pregunte al instructor o a uno de los Proctors para obtener ayuda para configurar la nueva cuenta.</span><span class="sxs-lookup"><span data-stu-id="601bd-157">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="601bd-158">Una vez que haya iniciado sesión, haga clic en **nuevo** en la esquina superior izquierda, busque la *cuenta de almacenamiento*y haga clic en **entrar**.</span><span class="sxs-lookup"><span data-stu-id="601bd-158">Once you are logged in, click on **New** in the top left corner, and search for *Storage account*, and click **Enter**.</span></span>

    ![búsqueda de Azure Storage](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > <span data-ttu-id="601bd-160">Es posible que la palabra **nuevo** se haya reemplazado por **crear un recurso**, en portales más recientes.</span><span class="sxs-lookup"><span data-stu-id="601bd-160">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="601bd-161">La nueva página proporcionará una descripción del servicio de *cuenta de Azure Storage* .</span><span class="sxs-lookup"><span data-stu-id="601bd-161">The new page will provide a description of the *Azure Storage account* service.</span></span> <span data-ttu-id="601bd-162">En la parte inferior izquierda de este mensaje, seleccione el botón **crear** para crear una asociación con este servicio.</span><span class="sxs-lookup"><span data-stu-id="601bd-162">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![crear servicio](images/AzureLabs-Lab5-02.png)

4.  <span data-ttu-id="601bd-164">Una vez que haya hecho clic en **crear**:</span><span class="sxs-lookup"><span data-stu-id="601bd-164">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="601bd-165">Inserte un *nombre* para la cuenta. tenga en cuenta que este campo solo acepta números y letras minúsculas.</span><span class="sxs-lookup"><span data-stu-id="601bd-165">Insert a *Name* for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="601bd-166">En *modelo de implementación*, seleccione **Resource Manager**.</span><span class="sxs-lookup"><span data-stu-id="601bd-166">For *Deployment model*, select **Resource manager**.</span></span>

    3.  <span data-ttu-id="601bd-167">En *tipo de cuenta*, seleccione **almacenamiento (uso general V1)** .</span><span class="sxs-lookup"><span data-stu-id="601bd-167">For *Account kind*, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="601bd-168">Determine la *Ubicación* del grupo de recursos (si va a crear un nuevo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="601bd-168">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="601bd-169">Idealmente, la ubicación estará en la región donde se ejecutará la aplicación.</span><span class="sxs-lookup"><span data-stu-id="601bd-169">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="601bd-170">Algunos recursos de Azure solo están disponibles en determinadas regiones.</span><span class="sxs-lookup"><span data-stu-id="601bd-170">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="601bd-171">En *replicación* , seleccione **almacenamiento con redundancia geográfica con acceso de lectura (RA-grs)** .</span><span class="sxs-lookup"><span data-stu-id="601bd-171">For *Replication* select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="601bd-172">En *rendimiento*, seleccione **estándar**.</span><span class="sxs-lookup"><span data-stu-id="601bd-172">For *Performance*, select **Standard**.</span></span>

    7.  <span data-ttu-id="601bd-173">Deje la *transferencia segura requerida* como **deshabilitada**.</span><span class="sxs-lookup"><span data-stu-id="601bd-173">Leave *Secure transfer required* as **Disabled**.</span></span>

    8.  <span data-ttu-id="601bd-174">Seleccione una *suscripción*.</span><span class="sxs-lookup"><span data-stu-id="601bd-174">Select a *Subscription*.</span></span>

    9. <span data-ttu-id="601bd-175">Elija un *grupo de recursos* o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="601bd-175">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="601bd-176">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="601bd-176">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="601bd-177">Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común).</span><span class="sxs-lookup"><span data-stu-id="601bd-177">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="601bd-178">Si desea leer más información sobre los grupos de recursos de Azure, [visite el artículo sobre el grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="601bd-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="601bd-179">También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.</span><span class="sxs-lookup"><span data-stu-id="601bd-179">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    11. <span data-ttu-id="601bd-180">Selecciona **Crear**.</span><span class="sxs-lookup"><span data-stu-id="601bd-180">Select **Create**.</span></span>

        ![información del servicio de entrada](images/AzureLabs-Lab5-03.png)

5.  <span data-ttu-id="601bd-182">Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="601bd-182">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="601bd-183">Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="601bd-183">A notification will appear in the portal once the Service instance is created.</span></span>

    ![nueva notificación en Azure portal](images/AzureLabs-Lab5-04.png)

7.  <span data-ttu-id="601bd-185">Haga clic en las notificaciones para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="601bd-185">Click on the notifications to explore your new Service instance.</span></span>

    ![ir al recurso](images/AzureLabs-Lab5-05.png)

8.  <span data-ttu-id="601bd-187">Haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="601bd-187">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="601bd-188">Se le dirigirá a la nueva instancia de servicio de la *cuenta de almacenamiento* .</span><span class="sxs-lookup"><span data-stu-id="601bd-188">You will be taken to your new *Storage account* service instance.</span></span>

    ![teclas de acceso](images/AzureLabs-Lab5-06.png)

9.  <span data-ttu-id="601bd-190">Haga clic en *claves de acceso*para mostrar los puntos de conexión de este servicio en la nube.</span><span class="sxs-lookup"><span data-stu-id="601bd-190">Click *Access keys*, to reveal the endpoints for this cloud service.</span></span> <span data-ttu-id="601bd-191">Use *el Bloc de notas* o similar para copiar una de las claves para usarla más adelante.</span><span class="sxs-lookup"><span data-stu-id="601bd-191">Use *Notepad* or similar, to copy one of your keys for use later.</span></span> <span data-ttu-id="601bd-192">Además, tenga en cuenta el valor de la *cadena de conexión* , ya que se usará en la clase *AzureServices* , que se creará más adelante.</span><span class="sxs-lookup"><span data-stu-id="601bd-192">Also, note the *Connection string* value, as it will be used in the *AzureServices* class, which you will create later.</span></span>

    ![copiar cadena de conexión](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a><span data-ttu-id="601bd-194">Capítulo 2: configuración de una función de Azure</span><span class="sxs-lookup"><span data-stu-id="601bd-194">Chapter 2 - Setting up an Azure Function</span></span>

<span data-ttu-id="601bd-195">Ahora escribirá una **función** de **Azure** en el servicio de Azure.</span><span class="sxs-lookup"><span data-stu-id="601bd-195">You will now write an **Azure** **Function** in the Azure Service.</span></span>

<span data-ttu-id="601bd-196">Puede usar una **función de Azure** para hacer prácticamente todo lo que haría con una función clásica en el código, la diferencia es que cualquier aplicación que tenga credenciales para acceder a la cuenta de Azure puede tener acceso a esta función.</span><span class="sxs-lookup"><span data-stu-id="601bd-196">You can use an **Azure Function** to do nearly anything that you would do with a classic function in your code, the difference being that this function can be accessed by any application that has credentials to access your Azure Account.</span></span>

<span data-ttu-id="601bd-197">Para crear una función de Azure:</span><span class="sxs-lookup"><span data-stu-id="601bd-197">To create an Azure Function:</span></span>

1.  <span data-ttu-id="601bd-198">En *Azure portal*, haga clic en **nuevo** en la esquina superior izquierda y busque *function App*y haga clic en **entrar**.</span><span class="sxs-lookup"><span data-stu-id="601bd-198">From your *Azure Portal*, click on **New** in the top left corner, and search for *Function App*, and click **Enter**.</span></span>

    ![creación de una aplicación de función](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > <span data-ttu-id="601bd-200">Es posible que la palabra **nuevo** se haya reemplazado por **crear un recurso**, en portales más recientes.</span><span class="sxs-lookup"><span data-stu-id="601bd-200">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

2.  <span data-ttu-id="601bd-201">La nueva página proporcionará una descripción del servicio *Azure function App* .</span><span class="sxs-lookup"><span data-stu-id="601bd-201">The new page will provide a description of the *Azure Function App* service.</span></span> <span data-ttu-id="601bd-202">En la parte inferior izquierda de este mensaje, seleccione el botón **crear** para crear una asociación con este servicio.</span><span class="sxs-lookup"><span data-stu-id="601bd-202">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![información de la aplicación de función](images/AzureLabs-Lab5-09.png)

3.  <span data-ttu-id="601bd-204">Una vez que haya hecho clic en **crear**:</span><span class="sxs-lookup"><span data-stu-id="601bd-204">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="601bd-205">Proporcione un *nombre de aplicación*.</span><span class="sxs-lookup"><span data-stu-id="601bd-205">Provide an *App name*.</span></span> <span data-ttu-id="601bd-206">Aquí solo se pueden usar letras y números (en mayúsculas o minúsculas).</span><span class="sxs-lookup"><span data-stu-id="601bd-206">Only letters and numbers can be used here (either upper or lower case is allowed).</span></span>

    2.  <span data-ttu-id="601bd-207">Seleccione su *suscripción*preferida.</span><span class="sxs-lookup"><span data-stu-id="601bd-207">Select your preferred *Subscription*.</span></span>

    3. <span data-ttu-id="601bd-208">Elija un *grupo de recursos* o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="601bd-208">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="601bd-209">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="601bd-209">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="601bd-210">Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común).</span><span class="sxs-lookup"><span data-stu-id="601bd-210">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="601bd-211">Si desea leer más información sobre los grupos de recursos de Azure, [visite el artículo sobre el grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="601bd-211">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="601bd-212">Para este ejercicio, seleccione *Windows* como el **sistema operativo**elegido.</span><span class="sxs-lookup"><span data-stu-id="601bd-212">For this exercise, select *Windows* as the chosen **OS**.</span></span>

    5.  <span data-ttu-id="601bd-213">Seleccione *plan de consumo* para el **plan de hospedaje**.</span><span class="sxs-lookup"><span data-stu-id="601bd-213">Select *Consumption Plan* for the **Hosting Plan**.</span></span>

    6.  <span data-ttu-id="601bd-214">Determine la *Ubicación* del grupo de recursos (si va a crear un nuevo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="601bd-214">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="601bd-215">Idealmente, la ubicación estará en la región donde se ejecutará la aplicación.</span><span class="sxs-lookup"><span data-stu-id="601bd-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="601bd-216">Algunos recursos de Azure solo están disponibles en determinadas regiones.</span><span class="sxs-lookup"><span data-stu-id="601bd-216">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="601bd-217">Para obtener un rendimiento óptimo, seleccione la misma región que la cuenta de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="601bd-217">For optimal performance, select the same region as the storage account.</span></span>

    7.  <span data-ttu-id="601bd-218">En *almacenamiento*, seleccione **usar existente**y, a continuación, use el menú desplegable para buscar el almacenamiento creado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="601bd-218">For *Storage*, select **Use existing**, and then using the dropdown menu, find your previously created storage.</span></span>

    8.  <span data-ttu-id="601bd-219">Deje *Application Insights* desactivado para este ejercicio.</span><span class="sxs-lookup"><span data-stu-id="601bd-219">Leave *Application Insights* off for this exercise.</span></span>

        ![detalles de la aplicación de función de entrada](images/AzureLabs-Lab5-10.png)

4.  <span data-ttu-id="601bd-221">Haga clic en el botón **Crear**.</span><span class="sxs-lookup"><span data-stu-id="601bd-221">Click the **Create** button.</span></span>

5.  <span data-ttu-id="601bd-222">Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="601bd-222">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="601bd-223">Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="601bd-223">A notification will appear in the portal once the Service instance is created.</span></span>

    ![nueva notificación de Azure portal](images/AzureLabs-Lab5-11.png)

7.  <span data-ttu-id="601bd-225">Haga clic en las notificaciones para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="601bd-225">Click on the notifications to explore your new Service instance.</span></span> 

    ![vaya a la aplicación de función de recursos](images/AzureLabs-Lab5-12.png)

8.  <span data-ttu-id="601bd-227">Haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="601bd-227">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="601bd-228">Se le dirigirá a la nueva instancia de servicio de *function App* .</span><span class="sxs-lookup"><span data-stu-id="601bd-228">You will be taken to your new *Function App* service instance.</span></span>

9.  <span data-ttu-id="601bd-229">En el panel de *function App* , mantenga el mouse sobre *las funciones*, que se encuentran dentro del panel de la izquierda y, a continuación, haga clic en el símbolo **+ (más)** .</span><span class="sxs-lookup"><span data-stu-id="601bd-229">On the *Function App* dashboard, hover your mouse over *Functions*, found within the panel on the left, and then click the **+ (plus)** symbol.</span></span>

    ![crear nueva función](images/AzureLabs-Lab5-13.png)

10. <span data-ttu-id="601bd-231">En la página siguiente, asegúrese de que se ha seleccionado **webhook + API** y, para *elegir un idioma,* seleccione **CSharp**, ya que este será el idioma usado para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="601bd-231">On the next page, ensure **Webhook + API** is selected, and for *Choose a language,* select **CSharp**, as this will be the language used for this tutorial.</span></span> <span data-ttu-id="601bd-232">Por último, haga clic en el botón **crear esta función** .</span><span class="sxs-lookup"><span data-stu-id="601bd-232">Lastly, click the **Create this function** button.</span></span>

    ![seleccionar CSharp de webhook](images/AzureLabs-Lab5-14.png)

11. <span data-ttu-id="601bd-234">Debe ir a la página de códigos (Run. CSX); si no es así, haga clic en la función recién creada en la lista de funciones dentro del panel de la izquierda.</span><span class="sxs-lookup"><span data-stu-id="601bd-234">You should be taken to the code page (run.csx), if not though, click on the newly created Function in the Functions list within the panel on the left.</span></span>

    ![abrir nueva función](images/AzureLabs-Lab5-15.png)

12. <span data-ttu-id="601bd-236">Copie el código siguiente en la función.</span><span class="sxs-lookup"><span data-stu-id="601bd-236">Copy the following code into your function.</span></span> <span data-ttu-id="601bd-237">Esta función simplemente devolverá un entero aleatorio entre 0 y 2 cuando se llame a.</span><span class="sxs-lookup"><span data-stu-id="601bd-237">This function will simply return a random integer between 0 and 2 when called.</span></span> <span data-ttu-id="601bd-238">No se preocupe por el código existente, no dude en pegarlo encima de la parte superior.</span><span class="sxs-lookup"><span data-stu-id="601bd-238">Do not worry about the existing code, feel free to paste over the top of it.</span></span>

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. <span data-ttu-id="601bd-239">Selecciona **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="601bd-239">Select **Save**.</span></span>

14. <span data-ttu-id="601bd-240">El resultado debería ser similar a la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="601bd-240">The result should look like the image below.</span></span>

15. <span data-ttu-id="601bd-241">Haga clic en **obtener la dirección URL** de la función y tome nota del *punto de conexión* mostrado.</span><span class="sxs-lookup"><span data-stu-id="601bd-241">Click on **Get function URL** and take note of the *endpoint* displayed.</span></span> <span data-ttu-id="601bd-242">Tendrá que insertarlo en la clase *AzureServices* que creará más adelante en este curso.</span><span class="sxs-lookup"><span data-stu-id="601bd-242">You will need to insert it into the *AzureServices* class that you will create later in this course.</span></span>

    ![obtener extremo de función](images/AzureLabs-Lab5-16.png)

    ![obtener extremo de función](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="601bd-245">Capítulo 3: configuración del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="601bd-245">Chapter 3 - Setting up the Unity project</span></span>

<span data-ttu-id="601bd-246">Lo siguiente es una configuración típica para desarrollar con la realidad mixta y, como tal, es una buena plantilla para otros proyectos.</span><span class="sxs-lookup"><span data-stu-id="601bd-246">The following is a typical set up for developing with Mixed Reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="601bd-247">Configure y pruebe sus auriculares de la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="601bd-247">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="601bd-248">**No** necesitará controladores de movimiento para este curso.</span><span class="sxs-lookup"><span data-stu-id="601bd-248">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="601bd-249">Si necesita ayuda para configurar el casco inmersivo, [visite el artículo sobre la](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)configuración de la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="601bd-249">If you need support setting up the immersive headset, please [visit the mixed reality set up article](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="601bd-250">Abra Unity y haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="601bd-250">Open Unity and click **New**.</span></span>

    ![crear nuevo proyecto de Unity](images/AzureLabs-Lab5-17.png)

2.  <span data-ttu-id="601bd-252">Ahora tendrá que proporcionar un nombre de proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="601bd-252">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="601bd-253">Inserte **MR_Azure_Functions**.</span><span class="sxs-lookup"><span data-stu-id="601bd-253">Insert **MR_Azure_Functions**.</span></span> <span data-ttu-id="601bd-254">Asegúrese de que el tipo de proyecto está establecido en **3D**.</span><span class="sxs-lookup"><span data-stu-id="601bd-254">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="601bd-255">Establezca la *Ubicación* en algún lugar adecuado para usted (Recuerde que, más cerca de los directorios raíz es mejor).</span><span class="sxs-lookup"><span data-stu-id="601bd-255">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="601bd-256">A continuación, haga clic en **crear proyecto**.</span><span class="sxs-lookup"><span data-stu-id="601bd-256">Then, click **Create project**.</span></span>

    ![asignar un nombre al nuevo proyecto de Unity](images/AzureLabs-Lab5-18.png)

3.  <span data-ttu-id="601bd-258">Con Unity abierto, merece la pena comprobar que el **Editor de scripts** predeterminado está establecido en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="601bd-258">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="601bd-259">Vaya a **editar** > **preferencias** y, a continuación, en la nueva ventana, vaya a **herramientas externas**.</span><span class="sxs-lookup"><span data-stu-id="601bd-259">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="601bd-260">Cambie el **Editor de script externo** a **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="601bd-260">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="601bd-261">Cierre la ventana **preferencias** .</span><span class="sxs-lookup"><span data-stu-id="601bd-261">Close the **Preferences** window.</span></span>

    ![establecer Visual Studio como editor de scripts](images/AzureLabs-Lab5-19.png)

4.  <span data-ttu-id="601bd-263">A continuación, vaya a **archivo** > **configuración de compilación** y cambie la plataforma a **plataforma universal de Windows**, haciendo clic en el botón **cambiar plataforma** .</span><span class="sxs-lookup"><span data-stu-id="601bd-263">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![cambiar la plataforma a UWP](images/AzureLabs-Lab5-20.png)

5.  <span data-ttu-id="601bd-265">Vaya a **archivo** > **configuración de compilación** y asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="601bd-265">Go to **File** > **Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="601bd-266">El **dispositivo de destino** se establece en **cualquier dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="601bd-266">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="601bd-267">Para Microsoft HoloLens, establezca el **dispositivo de destino** en *hololens*.</span><span class="sxs-lookup"><span data-stu-id="601bd-267">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="601bd-268">El **tipo de compilación** se establece en **D3D**</span><span class="sxs-lookup"><span data-stu-id="601bd-268">**Build Type** is set to **D3D**</span></span>

    3. <span data-ttu-id="601bd-269">**SDK** está establecido en la **versión más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="601bd-269">**SDK** is set to **Latest installed**</span></span>

    4. <span data-ttu-id="601bd-270">La **versión de Visual Studio** está establecida en la **más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="601bd-270">**Visual Studio Version** is set to **Latest installed**</span></span>

    5. <span data-ttu-id="601bd-271">**Compilar y ejecutar** está establecido en **equipo local**</span><span class="sxs-lookup"><span data-stu-id="601bd-271">**Build and Run** is set to **Local Machine**</span></span>

    6. <span data-ttu-id="601bd-272">Guarde la escena y agréguela a la compilación.</span><span class="sxs-lookup"><span data-stu-id="601bd-272">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="601bd-273">Para ello, seleccione **Agregar escenas abiertas**.</span><span class="sxs-lookup"><span data-stu-id="601bd-273">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="601bd-274">Aparecerá una ventana de guardar.</span><span class="sxs-lookup"><span data-stu-id="601bd-274">A save window will appear.</span></span>

            ![agregar escenas abiertas](images/AzureLabs-Lab5-21.png)

        2.  <span data-ttu-id="601bd-276">Cree una nueva carpeta para este, y en cualquier momento, en el futuro, seleccione el botón **nueva carpeta** para crear una nueva carpeta, asígnele el nombre **Scenes**.</span><span class="sxs-lookup"><span data-stu-id="601bd-276">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![crear carpeta de escenas](images/AzureLabs-Lab5-22.png)

        3.  <span data-ttu-id="601bd-278">Abra la carpeta **Scenes** recién creada y, a continuación, en el campo **nombre de archivo:** , escriba **FunctionsScene**y, a continuación, presione **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="601bd-278">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **FunctionsScene**, then press **Save**.</span></span>

            ![escena de Save Functions](images/AzureLabs-Lab5-23.png)

6.  <span data-ttu-id="601bd-280">El resto de la configuración, en la **configuración de compilación**, debe dejarse como predeterminada por ahora.</span><span class="sxs-lookup"><span data-stu-id="601bd-280">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

    ![escena de Save Functions](images/AzureLabs-Lab5-24.png)

7.  <span data-ttu-id="601bd-282">En la ventana *configuración de compilación* , haga clic en el botón Configuración del **reproductor** ; se abrirá el panel relacionado en el espacio donde se encuentra el *Inspector* .</span><span class="sxs-lookup"><span data-stu-id="601bd-282">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

    ![configuración del reproductor en el inspector](images/AzureLabs-Lab5-25.png)

8.  <span data-ttu-id="601bd-284">En este panel, deben comprobarse algunas opciones de configuración:</span><span class="sxs-lookup"><span data-stu-id="601bd-284">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="601bd-285">En la pestaña **otros valores** :</span><span class="sxs-lookup"><span data-stu-id="601bd-285">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="601bd-286">La **versión de scripting en tiempo de ejecución** debe ser **Experimental** (.net 4,6 equivalente), lo que desencadenará una necesidad de reiniciar el editor.</span><span class="sxs-lookup"><span data-stu-id="601bd-286">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>
        2.  <span data-ttu-id="601bd-287">El **back-end de scripting** debe ser **.net**</span><span class="sxs-lookup"><span data-stu-id="601bd-287">**Scripting Backend** should be **.NET**</span></span>
        3.  <span data-ttu-id="601bd-288">El **nivel de compatibilidad de API** debe ser **.net 4,6**</span><span class="sxs-lookup"><span data-stu-id="601bd-288">**API Compatibility Level** should be **.NET 4.6**</span></span>

    2.  <span data-ttu-id="601bd-289">En la pestaña **configuración de publicación** , en **capacidades**, seleccione:</span><span class="sxs-lookup"><span data-stu-id="601bd-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>
        
        -  <span data-ttu-id="601bd-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="601bd-290">**InternetClient**</span></span>

            ![establecer capacidades](images/AzureLabs-Lab5-26.png)

    3.  <span data-ttu-id="601bd-292">Más abajo en el panel, en la **configuración de XR** (se encuentra debajo de **configuración de publicación**), tick **Virtual Reality compatible**, asegúrese de que se agrega el **SDK de Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="601bd-292">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![establecer la configuración de XR](images/AzureLabs-Lab5-27.png)

9.  <span data-ttu-id="601bd-294">De nuevo en la *configuración de compilación* , los *proyectos de Unity C#*  ya no están atenuados; Marque la casilla situada junto a este.</span><span class="sxs-lookup"><span data-stu-id="601bd-294">Back in *Build Settings* *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

    ![proyectos de c# de tick](images/AzureLabs-Lab5-28.png)

10.  <span data-ttu-id="601bd-296">Cierre la ventana Configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="601bd-296">Close the Build Settings window.</span></span>

11. <span data-ttu-id="601bd-297">Guarde la escena y el proyecto (**archivo** > **guardar la escena o el archivo** > **Guardar proyecto**).</span><span class="sxs-lookup"><span data-stu-id="601bd-297">Save your Scene and Project (**FILE** > **SAVE SCENE / FILE** > **SAVE PROJECT**).</span></span>

## <a name="chapter-4---setup-main-camera"></a><span data-ttu-id="601bd-298">Capítulo 4: configuración de la cámara principal</span><span class="sxs-lookup"><span data-stu-id="601bd-298">Chapter 4 - Setup Main Camera</span></span>

> [!IMPORTANT]
> <span data-ttu-id="601bd-299">Si desea omitir los componentes de *configuración de Unity* de este curso y continuar directamente en el código, no dude en [Descargar este. unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)e importarlo en el proyecto como un [paquete personalizado](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="601bd-299">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="601bd-300">También contendrá los archivos DLL del siguiente capítulo.</span><span class="sxs-lookup"><span data-stu-id="601bd-300">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="601bd-301">Después de la importación, continúe en el [capítulo 7](#chapter-7---create-the-azureservices-class).</span><span class="sxs-lookup"><span data-stu-id="601bd-301">After import, continue from [Chapter 7](#chapter-7---create-the-azureservices-class).</span></span> 

1.  <span data-ttu-id="601bd-302">En el *Panel jerarquía*, encontrará un objeto denominado **cámara principal**, este objeto representa el punto de vista "principal" una vez que está "dentro" de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="601bd-302">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your "head" point of view once you are "inside" your application.</span></span>

2.  <span data-ttu-id="601bd-303">Con el panel de Unity delante de usted, seleccione la **cámara principal GameObject**.</span><span class="sxs-lookup"><span data-stu-id="601bd-303">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="601bd-304">Observará que el *panel Inspector* (generalmente situado a la derecha, dentro del panel) mostrará los distintos componentes de ese *GameObject*, con la *transformación* en la parte superior, la *cámara*y otros componentes.</span><span class="sxs-lookup"><span data-stu-id="601bd-304">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="601bd-305">Tendrá que restablecer la transformación de la cámara principal, de modo que esté colocada correctamente.</span><span class="sxs-lookup"><span data-stu-id="601bd-305">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>

3.  <span data-ttu-id="601bd-306">Para ello, seleccione el icono de **engranaje** situado junto al componente de *transformación* de la cámara y seleccione **restablecer**.</span><span class="sxs-lookup"><span data-stu-id="601bd-306">To do this, select the **Gear** icon next to the Camera's *Transform* component, and select **Reset**.</span></span>

    ![restablecer transformación](images/AzureLabs-Lab5-29.png)

4.  <span data-ttu-id="601bd-308">A continuación, actualice el componente de **transformación** para que tenga el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="601bd-308">Then update the **Transform** component to look like:</span></span>

    |         |    <span data-ttu-id="601bd-309">TRANSFORMACIÓN: POSICIÓN</span><span class="sxs-lookup"><span data-stu-id="601bd-309">TRANSFORM - POSITION</span></span>   |       |
    | :-----: | :-----------------------: | :----:|
    | <span data-ttu-id="601bd-310">**X1**</span><span class="sxs-lookup"><span data-stu-id="601bd-310">**X**</span></span>   | <span data-ttu-id="601bd-311">**Sí**</span><span class="sxs-lookup"><span data-stu-id="601bd-311">**Y**</span></span>                     | <span data-ttu-id="601bd-312">**Z**</span><span class="sxs-lookup"><span data-stu-id="601bd-312">**Z**</span></span> |
    | <span data-ttu-id="601bd-313">0</span><span class="sxs-lookup"><span data-stu-id="601bd-313">0</span></span>       | <span data-ttu-id="601bd-314">1</span><span class="sxs-lookup"><span data-stu-id="601bd-314">1</span></span>                         | <span data-ttu-id="601bd-315">0</span><span class="sxs-lookup"><span data-stu-id="601bd-315">0</span></span>     |    

    |       | <span data-ttu-id="601bd-316">TRANSFORMACIÓN-GIRO</span><span class="sxs-lookup"><span data-stu-id="601bd-316">TRANSFORM - ROTATION</span></span> |       |
    | :---: | :------------------: | :----:|
    | <span data-ttu-id="601bd-317">**X1**</span><span class="sxs-lookup"><span data-stu-id="601bd-317">**X**</span></span> | <span data-ttu-id="601bd-318">**Sí**</span><span class="sxs-lookup"><span data-stu-id="601bd-318">**Y**</span></span>                | <span data-ttu-id="601bd-319">**Z**</span><span class="sxs-lookup"><span data-stu-id="601bd-319">**Z**</span></span> |
    | <span data-ttu-id="601bd-320">0</span><span class="sxs-lookup"><span data-stu-id="601bd-320">0</span></span>     | <span data-ttu-id="601bd-321">0</span><span class="sxs-lookup"><span data-stu-id="601bd-321">0</span></span>                    | <span data-ttu-id="601bd-322">0</span><span class="sxs-lookup"><span data-stu-id="601bd-322">0</span></span>     |

    |       | <span data-ttu-id="601bd-323">TRANSFORMACIÓN DE ESCALA</span><span class="sxs-lookup"><span data-stu-id="601bd-323">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="601bd-324">**X1**</span><span class="sxs-lookup"><span data-stu-id="601bd-324">**X**</span></span> | <span data-ttu-id="601bd-325">**Sí**</span><span class="sxs-lookup"><span data-stu-id="601bd-325">**Y**</span></span>             | <span data-ttu-id="601bd-326">**Z**</span><span class="sxs-lookup"><span data-stu-id="601bd-326">**Z**</span></span> |
    | <span data-ttu-id="601bd-327">1</span><span class="sxs-lookup"><span data-stu-id="601bd-327">1</span></span>     | <span data-ttu-id="601bd-328">1</span><span class="sxs-lookup"><span data-stu-id="601bd-328">1</span></span>                 | <span data-ttu-id="601bd-329">1</span><span class="sxs-lookup"><span data-stu-id="601bd-329">1</span></span>     |

    ![establecer transformación de cámara](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a><span data-ttu-id="601bd-331">Capítulo 5: configuración de la escena de Unity</span><span class="sxs-lookup"><span data-stu-id="601bd-331">Chapter 5 - Setting up the Unity scene</span></span>

1.  <span data-ttu-id="601bd-332">Haga clic con el botón secundario en un área vacía del *Panel de jerarquías*, en **objeto 3D**, agregar un **plano**.</span><span class="sxs-lookup"><span data-stu-id="601bd-332">Right-click in an empty area of the *Hierarchy Panel*, under **3D  Object**, add a **Plane**.</span></span>

    ![crear nuevo plano](images/AzureLabs-Lab5-31.png)

2.  <span data-ttu-id="601bd-334">Con el objeto de **plano** seleccionado, cambie los siguientes parámetros en el *panel del inspector*:</span><span class="sxs-lookup"><span data-stu-id="601bd-334">With the **Plane** object selected, change the following parameters in the *Inspector Panel*:</span></span>

    |       | <span data-ttu-id="601bd-335">TRANSFORMACIÓN: POSICIÓN</span><span class="sxs-lookup"><span data-stu-id="601bd-335">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="601bd-336">**X1**</span><span class="sxs-lookup"><span data-stu-id="601bd-336">**X**</span></span> | <span data-ttu-id="601bd-337">**Sí**</span><span class="sxs-lookup"><span data-stu-id="601bd-337">**Y**</span></span>                | <span data-ttu-id="601bd-338">**Z**</span><span class="sxs-lookup"><span data-stu-id="601bd-338">**Z**</span></span> |
    | <span data-ttu-id="601bd-339">0</span><span class="sxs-lookup"><span data-stu-id="601bd-339">0</span></span>     | <span data-ttu-id="601bd-340">0</span><span class="sxs-lookup"><span data-stu-id="601bd-340">0</span></span>                    | <span data-ttu-id="601bd-341">4</span><span class="sxs-lookup"><span data-stu-id="601bd-341">4</span></span>     |

    |       | <span data-ttu-id="601bd-342">TRANSFORMACIÓN DE ESCALA</span><span class="sxs-lookup"><span data-stu-id="601bd-342">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="601bd-343">**X1**</span><span class="sxs-lookup"><span data-stu-id="601bd-343">**X**</span></span> | <span data-ttu-id="601bd-344">**Sí**</span><span class="sxs-lookup"><span data-stu-id="601bd-344">**Y**</span></span>             | <span data-ttu-id="601bd-345">**Z**</span><span class="sxs-lookup"><span data-stu-id="601bd-345">**Z**</span></span> |
    | <span data-ttu-id="601bd-346">10</span><span class="sxs-lookup"><span data-stu-id="601bd-346">10</span></span>    | <span data-ttu-id="601bd-347">1</span><span class="sxs-lookup"><span data-stu-id="601bd-347">1</span></span>                 | <span data-ttu-id="601bd-348">10</span><span class="sxs-lookup"><span data-stu-id="601bd-348">10</span></span>    |

    ![establecer la posición y la escala del plano](images/AzureLabs-Lab5-32.png)

    ![vista de escena de plano](images/AzureLabs-Lab5-33.png)

3.  <span data-ttu-id="601bd-351">Haga clic con el botón secundario en un área vacía del *Panel jerarquía*, en **objeto 3D**, agregar un **cubo**.</span><span class="sxs-lookup"><span data-stu-id="601bd-351">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Cube**.</span></span>

    1.  <span data-ttu-id="601bd-352">Cambie el nombre del cubo a **GazeButton** (con el cubo seleccionado, presione ' F2 ').</span><span class="sxs-lookup"><span data-stu-id="601bd-352">Rename the Cube to **GazeButton** (with the Cube selected, press 'F2').</span></span>

    2.  <span data-ttu-id="601bd-353">Cambie los parámetros siguientes en el *panel Inspector*:</span><span class="sxs-lookup"><span data-stu-id="601bd-353">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="601bd-354">TRANSFORMACIÓN: POSICIÓN</span><span class="sxs-lookup"><span data-stu-id="601bd-354">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:-----:|
        | <span data-ttu-id="601bd-355">**X1**</span><span class="sxs-lookup"><span data-stu-id="601bd-355">**X**</span></span> | <span data-ttu-id="601bd-356">**Sí**</span><span class="sxs-lookup"><span data-stu-id="601bd-356">**Y**</span></span>                | <span data-ttu-id="601bd-357">**Z**</span><span class="sxs-lookup"><span data-stu-id="601bd-357">**Z**</span></span> |
        | <span data-ttu-id="601bd-358">0</span><span class="sxs-lookup"><span data-stu-id="601bd-358">0</span></span>     | <span data-ttu-id="601bd-359">3</span><span class="sxs-lookup"><span data-stu-id="601bd-359">3</span></span>                    | <span data-ttu-id="601bd-360">5</span><span class="sxs-lookup"><span data-stu-id="601bd-360">5</span></span>     |


        ![establecer transformación de botón de mira](images/AzureLabs-Lab5-34.png)

        ![vista de escena de botón de mira](images/AzureLabs-Lab5-35.png)

    3.  <span data-ttu-id="601bd-363">Haga clic en el botón desplegable **etiqueta** y haga clic en **Agregar etiqueta** para abrir el *panel Etiquetas & capas*.</span><span class="sxs-lookup"><span data-stu-id="601bd-363">Click on the **Tag** drop-down button and click on **Add Tag** to open the *Tags & Layers Pane*.</span></span>

        ![Agregar nueva etiqueta](images/AzureLabs-Lab5-36.png)

        ![seleccionar más](images/AzureLabs-Lab5-37.png)

    4.  <span data-ttu-id="601bd-366">Seleccione el botón **+ (más)** y, en el campo *nuevo nombre de etiqueta* , escriba **GazeButton**y presione **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="601bd-366">Select the **+ (plus)** button, and in the *New Tag Name* field, enter **GazeButton**, and press **Save**.</span></span>

        ![nombre nueva etiqueta](images/AzureLabs-Lab5-38.png)

    5.  <span data-ttu-id="601bd-368">Haga clic en el objeto **GazeButton** en el *Panel jerarquía*y, en el *panel Inspector*, asigne la etiqueta **GazeButton** recién creada.</span><span class="sxs-lookup"><span data-stu-id="601bd-368">Click on the **GazeButton** object in the *Hierarchy Panel*, and in the *Inspector Panel*, assign the newly created **GazeButton** tag.</span></span>

        ![asignar botón de mira la nueva etiqueta](images/AzureLabs-Lab5-39.png)

4.  <span data-ttu-id="601bd-370">Haga clic con el botón derecho en el objeto **GazeButton** , en el *Panel jerarquía*, y agregue un **GameObject vacío** (que se agregará como un objeto *secundario* ).</span><span class="sxs-lookup"><span data-stu-id="601bd-370">Right-click on the **GazeButton** object, in the *Hierarchy Panel*, and add an **Empty GameObject** (which will be added as a *child* object).</span></span>

5.  <span data-ttu-id="601bd-371">Seleccione el nuevo objeto y cambie su nombre a **ShapeSpawnPoint**.</span><span class="sxs-lookup"><span data-stu-id="601bd-371">Select the new object and rename it **ShapeSpawnPoint**.</span></span>

    1.  <span data-ttu-id="601bd-372">Cambie los parámetros siguientes en el *panel Inspector*:</span><span class="sxs-lookup"><span data-stu-id="601bd-372">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="601bd-373">TRANSFORMACIÓN: POSICIÓN</span><span class="sxs-lookup"><span data-stu-id="601bd-373">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:----: |
        | <span data-ttu-id="601bd-374">**X1**</span><span class="sxs-lookup"><span data-stu-id="601bd-374">**X**</span></span> |<span data-ttu-id="601bd-375">**Sí**</span><span class="sxs-lookup"><span data-stu-id="601bd-375">**Y**</span></span>                 | <span data-ttu-id="601bd-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="601bd-376">**Z**</span></span> |
        | <span data-ttu-id="601bd-377">0</span><span class="sxs-lookup"><span data-stu-id="601bd-377">0</span></span>     | <span data-ttu-id="601bd-378">-1</span><span class="sxs-lookup"><span data-stu-id="601bd-378">-1</span></span>                   | <span data-ttu-id="601bd-379">0</span><span class="sxs-lookup"><span data-stu-id="601bd-379">0</span></span>     |

        ![transformación actualizar punto de generación de forma](images/AzureLabs-Lab5-40.png)

        ![vista de escena de punto de generación de formas](images/AzureLabs-Lab5-41.png)

6.  <span data-ttu-id="601bd-382">A continuación, creará un objeto de **texto 3D** para proporcionar comentarios sobre el estado del servicio de Azure.</span><span class="sxs-lookup"><span data-stu-id="601bd-382">Next you will create a **3D Text** object to provide feedback on the status of the Azure service.</span></span>

    <span data-ttu-id="601bd-383">Vuelva a hacer clic con el botón derecho en **GazeButton** en el panel jerarquía y agregue un **objeto 3D** > objeto de **texto 3D** como un *elemento secundario*.</span><span class="sxs-lookup"><span data-stu-id="601bd-383">Right click on the **GazeButton** in the Hierarchy Panel again and add a **3D Object** > **3D Text** object as a *child*.</span></span>

    ![crear nuevo objeto de texto 3D](images/AzureLabs-Lab5-42.png)

7.  <span data-ttu-id="601bd-385">Cambie el nombre del objeto de **texto 3D** a **AzureStatusText**.</span><span class="sxs-lookup"><span data-stu-id="601bd-385">Rename the **3D Text** object to **AzureStatusText**.</span></span>

8.  <span data-ttu-id="601bd-386">Cambie la transformación del objeto **AzureStatusText** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="601bd-386">Change the **AzureStatusText** object Transform as follows:</span></span>

    |       | <span data-ttu-id="601bd-387">TRANSFORMACIÓN: POSICIÓN</span><span class="sxs-lookup"><span data-stu-id="601bd-387">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="601bd-388">**X1**</span><span class="sxs-lookup"><span data-stu-id="601bd-388">**X**</span></span> | <span data-ttu-id="601bd-389">**Sí**</span><span class="sxs-lookup"><span data-stu-id="601bd-389">**Y**</span></span>                | <span data-ttu-id="601bd-390">**Z**</span><span class="sxs-lookup"><span data-stu-id="601bd-390">**Z**</span></span> |
    | <span data-ttu-id="601bd-391">0</span><span class="sxs-lookup"><span data-stu-id="601bd-391">0</span></span>     | <span data-ttu-id="601bd-392">0</span><span class="sxs-lookup"><span data-stu-id="601bd-392">0</span></span>                    | <span data-ttu-id="601bd-393">-0,6</span><span class="sxs-lookup"><span data-stu-id="601bd-393">-0.6</span></span>  |

    |       | <span data-ttu-id="601bd-394">TRANSFORMACIÓN DE ESCALA</span><span class="sxs-lookup"><span data-stu-id="601bd-394">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="601bd-395">**X1**</span><span class="sxs-lookup"><span data-stu-id="601bd-395">**X**</span></span> | <span data-ttu-id="601bd-396">**Sí**</span><span class="sxs-lookup"><span data-stu-id="601bd-396">**Y**</span></span>             | <span data-ttu-id="601bd-397">**Z**</span><span class="sxs-lookup"><span data-stu-id="601bd-397">**Z**</span></span> |
    | <span data-ttu-id="601bd-398">0,1</span><span class="sxs-lookup"><span data-stu-id="601bd-398">0.1</span></span>   | <span data-ttu-id="601bd-399">0,1</span><span class="sxs-lookup"><span data-stu-id="601bd-399">0.1</span></span>               | <span data-ttu-id="601bd-400">0,1</span><span class="sxs-lookup"><span data-stu-id="601bd-400">0.1</span></span>   |


    > [!NOTE]
    > <span data-ttu-id="601bd-401">No se preocupe si parece estar fuera del centro, ya que se solucionará cuando se actualice el componente de malla de texto siguiente.</span><span class="sxs-lookup"><span data-stu-id="601bd-401">Do not worry if it appears to be off-centre, as this will be fixed when the below Text Mesh component is updated.</span></span>

9.  <span data-ttu-id="601bd-402">Cambie el componente de **malla de texto** para que coincida con el siguiente:</span><span class="sxs-lookup"><span data-stu-id="601bd-402">Change the **Text Mesh** component to match the below:</span></span>

    ![establecer componente de malla de texto](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > <span data-ttu-id="601bd-404">El color seleccionado aquí es color Hex: **000000FF**, aunque no dude en elegir el suyo propio, solo tiene que asegurarse de que es legible.</span><span class="sxs-lookup"><span data-stu-id="601bd-404">The selected color here is Hex color: **000000FF**, though feel free to choose your own, just ensure it is readable.</span></span>

10. <span data-ttu-id="601bd-405">La estructura del panel de jerarquías debería tener ahora el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="601bd-405">Your Hierarchy Panel structure should now look like this:</span></span>

    ![malla de texto en la vista de escenas](images/AzureLabs-Lab5-43b.png)

10. <span data-ttu-id="601bd-407">La escena debe tener ahora el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="601bd-407">Your scene should now look like this:</span></span>

    ![malla de texto en la vista de escenas](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a><span data-ttu-id="601bd-409">Capítulo 6: importar Azure Storage para Unity</span><span class="sxs-lookup"><span data-stu-id="601bd-409">Chapter 6 - Import Azure Storage for Unity</span></span>

<span data-ttu-id="601bd-410">Usará Azure Storage para Unity (que a su vez usa el SDK de .net para Azure).</span><span class="sxs-lookup"><span data-stu-id="601bd-410">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="601bd-411">Puede leer más sobre esto en el [artículo Azure Storage para Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="601bd-411">You can read more about this at the [Azure Storage for Unity article](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="601bd-412">Actualmente hay un problema conocido en Unity que requiere que los complementos se vuelvan a configurar después de la importación.</span><span class="sxs-lookup"><span data-stu-id="601bd-412">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="601bd-413">Estos pasos (4-7 en esta sección) ya no serán necesarios una vez resuelto el error.</span><span class="sxs-lookup"><span data-stu-id="601bd-413">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="601bd-414">Para importar el SDK en su propio proyecto, asegúrese de que ha descargado el [". unitypackage Tools" más reciente de github](https://aka.ms/azstorage-unitysdk).</span><span class="sxs-lookup"><span data-stu-id="601bd-414">To import the SDK into your own project, make sure you have downloaded the latest ['.unitypackage' from GitHub](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="601bd-415">A continuación, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="601bd-415">Then, do the following:</span></span>

1.  <span data-ttu-id="601bd-416">Agregue el archivo **. unitypackage Tools** a Unity mediante la opción de menú **activos** > **importar paquete** > **paquete personalizado** .</span><span class="sxs-lookup"><span data-stu-id="601bd-416">Add the **.unitypackage** file to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

2.  <span data-ttu-id="601bd-417">En el cuadro **importar paquete Unity** que aparece, puede seleccionar todo en **complemento** > **Storage**.</span><span class="sxs-lookup"><span data-stu-id="601bd-417">In the **Import Unity Package** box that pops up, you can select everything under **Plugin** > **Storage**.</span></span> <span data-ttu-id="601bd-418">Desactive todo lo demás, ya que no es necesario para este curso.</span><span class="sxs-lookup"><span data-stu-id="601bd-418">Uncheck everything else, as it is not needed for this course.</span></span>

    ![importar a paquete](images/AzureLabs-Lab5-45.png)

3.  <span data-ttu-id="601bd-420">Haga clic en el botón **importar** para agregar los elementos al proyecto.</span><span class="sxs-lookup"><span data-stu-id="601bd-420">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="601bd-421">Vaya a la carpeta *Storage* en *Complementos*, en la vista proyecto, y seleccione *solo*los siguientes complementos:</span><span class="sxs-lookup"><span data-stu-id="601bd-421">Go to the *Storage* folder under *Plugins*, in the Project view, and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="601bd-422">Microsoft. Data. Edm</span><span class="sxs-lookup"><span data-stu-id="601bd-422">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="601bd-423">Microsoft. Data. OData</span><span class="sxs-lookup"><span data-stu-id="601bd-423">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="601bd-424">Microsoft. WindowsAzure. Storage</span><span class="sxs-lookup"><span data-stu-id="601bd-424">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="601bd-425">Newtonsoft. JSON</span><span class="sxs-lookup"><span data-stu-id="601bd-425">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="601bd-426">System. espacial</span><span class="sxs-lookup"><span data-stu-id="601bd-426">System.Spatial</span></span>

        ![desactive cualquier plataforma](images/AzureLabs-Lab5-46.png)

5.  <span data-ttu-id="601bd-428">Con *estos complementos específicos* seleccionados, **desactive** *cualquier plataforma* y **desactive** *WSAPlayer* y haga clic en **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="601bd-428">With *these specific plugins* selected, **uncheck** *Any Platform* and **uncheck** *WSAPlayer* then click **Apply**.</span></span>

    ![aplicar dll de plataforma](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > <span data-ttu-id="601bd-430">Estamos marcando estos complementos concretos para usarlos solo en el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="601bd-430">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="601bd-431">Esto se debe a que hay diferentes versiones de los mismos complementos en la carpeta WSA que se usarán después de exportar el proyecto desde Unity.</span><span class="sxs-lookup"><span data-stu-id="601bd-431">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="601bd-432">En la carpeta del complemento de *almacenamiento* , seleccione solo:</span><span class="sxs-lookup"><span data-stu-id="601bd-432">In the *Storage* plugin folder, select only:</span></span>

    -   <span data-ttu-id="601bd-433">Microsoft. Data. Services. Client</span><span class="sxs-lookup"><span data-stu-id="601bd-433">Microsoft.Data.Services.Client</span></span>

        ![establecer no procesar para archivos dll](images/AzureLabs-Lab5-48.png)

7.  <span data-ttu-id="601bd-435">Active la casilla **no procesar** en *configuración de plataforma* y haga clic en **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="601bd-435">Check the **Don't Process** box under *Platform Settings* and click **Apply**.</span></span>

    ![no aplicar procesamiento](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > <span data-ttu-id="601bd-437">Estamos marcando este complemento como "no procesar" porque el parche de ensamblado de Unity tiene dificultades para procesar este complemento.</span><span class="sxs-lookup"><span data-stu-id="601bd-437">We are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="601bd-438">El complemento seguirá funcionando aunque no se haya procesado.</span><span class="sxs-lookup"><span data-stu-id="601bd-438">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-7---create-the-azureservices-class"></a><span data-ttu-id="601bd-439">Capítulo 7: creación de la clase AzureServices</span><span class="sxs-lookup"><span data-stu-id="601bd-439">Chapter 7 - Create the AzureServices class</span></span>

<span data-ttu-id="601bd-440">La primera clase que va a crear es la clase *AzureServices* .</span><span class="sxs-lookup"><span data-stu-id="601bd-440">The first class you are going to create is the *AzureServices* class.</span></span>

<span data-ttu-id="601bd-441">La clase *AzureServices* se encargará de:</span><span class="sxs-lookup"><span data-stu-id="601bd-441">The *AzureServices* class will be responsible for:</span></span>

-   <span data-ttu-id="601bd-442">Almacenamiento de las credenciales de la cuenta de Azure.</span><span class="sxs-lookup"><span data-stu-id="601bd-442">Storing Azure Account credentials.</span></span>

-   <span data-ttu-id="601bd-443">Llamar a la función App de Azure.</span><span class="sxs-lookup"><span data-stu-id="601bd-443">Calling your Azure App Function.</span></span>

-   <span data-ttu-id="601bd-444">La carga y descarga del archivo de datos en el almacenamiento en la nube de Azure.</span><span class="sxs-lookup"><span data-stu-id="601bd-444">The upload and download of the data file in your Azure Cloud Storage.</span></span>

<span data-ttu-id="601bd-445">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="601bd-445">To create this Class:</span></span>

1.  <span data-ttu-id="601bd-446">Haga clic con el botón derecho en la carpeta de *recursos* , que se encuentra en el panel Proyecto, **cree** > **carpeta**.</span><span class="sxs-lookup"><span data-stu-id="601bd-446">Right-click in the *Asset* Folder, located in the Project Panel, **Create** > **Folder**.</span></span> <span data-ttu-id="601bd-447">Asigne a la carpeta el nombre **scripts**.</span><span class="sxs-lookup"><span data-stu-id="601bd-447">Name the folder **Scripts**.</span></span>

    ![crear nueva carpeta](images/AzureLabs-Lab5-50.png)

    ![carpeta de llamadas: scripts](images/AzureLabs-Lab5-51.png)

2.  <span data-ttu-id="601bd-450">Haga doble clic en la carpeta que acaba de crear para abrirla.</span><span class="sxs-lookup"><span data-stu-id="601bd-450">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="601bd-451">Haga clic con el botón derecho dentro de la carpeta, **cree** >  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="601bd-451">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="601bd-452">Llame al script *AzureServices*.</span><span class="sxs-lookup"><span data-stu-id="601bd-452">Call the script *AzureServices*.</span></span>

4.  <span data-ttu-id="601bd-453">Haga doble clic en la nueva clase *AzureServices* para abrirla con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="601bd-453">Double click on the new *AzureServices* class to open it with *Visual Studio*.</span></span>

5.  <span data-ttu-id="601bd-454">Agregue los siguientes espacios de nombres en la parte superior de *AzureServices*:</span><span class="sxs-lookup"><span data-stu-id="601bd-454">Add the following namespaces to the top of the *AzureServices*:</span></span>

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  <span data-ttu-id="601bd-455">Agregue los siguientes campos de inspector dentro de la clase *AzureServices* :</span><span class="sxs-lookup"><span data-stu-id="601bd-455">Add the following Inspector Fields inside the *AzureServices* class:</span></span>

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  <span data-ttu-id="601bd-456">A continuación, agregue las siguientes variables de miembro dentro de la clase *AzureServices* :</span><span class="sxs-lookup"><span data-stu-id="601bd-456">Then add the following member variables inside the *AzureServices* class:</span></span>

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="601bd-457">Asegúrese de reemplazar los valores de *punto* de conexión y de *cadena de conexión* con los valores de Azure Storage, que se encuentran en Azure portal.</span><span class="sxs-lookup"><span data-stu-id="601bd-457">Make sure you replace the *endpoint* and *connection string* values with the values from your Azure storage, found in the Azure Portal</span></span>

8.  <span data-ttu-id="601bd-458">Ahora es necesario agregar el código para los métodos *activo ()* e *Inicio ()* .</span><span class="sxs-lookup"><span data-stu-id="601bd-458">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="601bd-459">Se llamará a estos métodos cuando se inicialice la clase:</span><span class="sxs-lookup"><span data-stu-id="601bd-459">These methods will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="601bd-460">En un [capítulo futuro](#chapter-10---completing-the-azureservices-class), rellenaremos el código para *CallAzureFunctionForNextShape ()* .</span><span class="sxs-lookup"><span data-stu-id="601bd-460">We will fill in the code for *CallAzureFunctionForNextShape()* in a [future Chapter](#chapter-10---completing-the-azureservices-class).</span></span>

9.  <span data-ttu-id="601bd-461">Elimine el método *Update ()* , ya que esta clase no lo usará.</span><span class="sxs-lookup"><span data-stu-id="601bd-461">Delete the *Update()* method since this class will not use it.</span></span>

10. <span data-ttu-id="601bd-462">Guarde los cambios en Visual Studio y vuelva a Unity.</span><span class="sxs-lookup"><span data-stu-id="601bd-462">Save your changes in Visual Studio, and then return to Unity.</span></span>

11. <span data-ttu-id="601bd-463">Haga clic y arrastre la clase *AzureServices* desde la carpeta scripts hasta el objeto cámara principal en el *Panel jerarquía*.</span><span class="sxs-lookup"><span data-stu-id="601bd-463">Click and drag the *AzureServices* class from the Scripts folder to the Main Camera object in the *Hierarchy Panel*.</span></span>

12. <span data-ttu-id="601bd-464">Seleccione la cámara principal, después arrastre el objeto secundario **AzureStatusText** de debajo del objeto **GazeButton** y colóquelo en el campo destino de referencia **AzureStatusText** , en el *Inspector*, para proporcionar la referencia al  *Script AzureServices* .</span><span class="sxs-lookup"><span data-stu-id="601bd-464">Select the Main Camera, then grab the **AzureStatusText** child object from beneath the **GazeButton** object, and place it within the **AzureStatusText** reference target field, in the *Inspector*, to provide the reference to the *AzureServices* script.</span></span>

    ![asignar destino de referencia de texto de estado de Azure](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a><span data-ttu-id="601bd-466">Capítulo 8: creación de la clase ShapeFactory</span><span class="sxs-lookup"><span data-stu-id="601bd-466">Chapter 8 - Create the ShapeFactory class</span></span>

<span data-ttu-id="601bd-467">El siguiente script que se va a crear es la clase *ShapeFactory* .</span><span class="sxs-lookup"><span data-stu-id="601bd-467">The next script to create, is the *ShapeFactory* class.</span></span> <span data-ttu-id="601bd-468">El rol de esta clase es crear una nueva forma, cuando se solicita, y mantener un historial de las formas creadas en una *lista de historial de formas*.</span><span class="sxs-lookup"><span data-stu-id="601bd-468">The role of this class is to create a new shape, when requested, and keep a history of the shapes created in a *Shape History List*.</span></span> <span data-ttu-id="601bd-469">Cada vez que se crea una forma, se actualiza la *lista de historial de formas* en la clase *AzureService* y, a continuación, se almacena en el *Azure Storage*.</span><span class="sxs-lookup"><span data-stu-id="601bd-469">Every time a shape is created, the *Shape History list* is updated in the *AzureService* class, and then stored in your *Azure Storage*.</span></span> <span data-ttu-id="601bd-470">Cuando se inicia la aplicación, si se encuentra un archivo almacenado en el *Azure Storage*, se recupera y se vuelve a reproducir la *lista de historial de formas* , con el objeto de **texto 3D** que proporciona si la forma generada es de almacenamiento o nueva.</span><span class="sxs-lookup"><span data-stu-id="601bd-470">When the application starts, if a stored file is found in your *Azure Storage*, the *Shape History list* is retrieved and replayed, with the **3D Text** object providing whether the generated shape is from storage, or new.</span></span>

<span data-ttu-id="601bd-471">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="601bd-471">To create this class:</span></span>

1.  <span data-ttu-id="601bd-472">Vaya a la carpeta **scripts** que creó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="601bd-472">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="601bd-473">Haga clic con el botón derecho dentro de la carpeta, **cree** >  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="601bd-473">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="601bd-474">Llame al script *ShapeFactory*.</span><span class="sxs-lookup"><span data-stu-id="601bd-474">Call the script *ShapeFactory*.</span></span>

3.  <span data-ttu-id="601bd-475">Haga doble clic en el nuevo script *ShapeFactory* para abrirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="601bd-475">Double click on the new *ShapeFactory* script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="601bd-476">Asegúrese de que la clase *ShapeFactory* incluye los siguientes espacios de nombres:</span><span class="sxs-lookup"><span data-stu-id="601bd-476">Ensure the *ShapeFactory* class includes the following namespaces:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  <span data-ttu-id="601bd-477">Agregue las variables que se muestran a continuación a la clase *ShapeFactory* y reemplace las funciones *Start ()* y Activate *()* con las siguientes:</span><span class="sxs-lookup"><span data-stu-id="601bd-477">Add the variables shown below to the *ShapeFactory* class, and replace the *Start()* and *Awake()* functions with those below:</span></span>

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  <span data-ttu-id="601bd-478">El método *CreateShape ()* genera las formas primitivas, basándose en el parámetro de *entero* proporcionado.</span><span class="sxs-lookup"><span data-stu-id="601bd-478">The *CreateShape()* method generates the primitive shapes, based upon the provided *integer* parameter.</span></span> <span data-ttu-id="601bd-479">El parámetro booleano se usa para especificar si la forma creada actualmente es de almacenamiento o nueva.</span><span class="sxs-lookup"><span data-stu-id="601bd-479">The Boolean parameter is used to specify whether the currently created shape is from storage, or new.</span></span> <span data-ttu-id="601bd-480">Coloque el código siguiente en la clase *ShapeFactory* , debajo de los métodos anteriores:</span><span class="sxs-lookup"><span data-stu-id="601bd-480">Place the following code in your *ShapeFactory* class, below the previous methods:</span></span>

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  <span data-ttu-id="601bd-481">Asegúrese de guardar los cambios en Visual Studio antes de volver a Unity.</span><span class="sxs-lookup"><span data-stu-id="601bd-481">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

8.  <span data-ttu-id="601bd-482">De nuevo en el editor de Unity, haga clic y arrastre la clase *ShapeFactory* desde la carpeta **scripts** hasta el objeto **cámara principal** en el *Panel jerarquía*.</span><span class="sxs-lookup"><span data-stu-id="601bd-482">Back in the Unity Editor, click and drag the *ShapeFactory* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

9. <span data-ttu-id="601bd-483">Con la cámara principal seleccionada, observará que en el componente de script *ShapeFactory* falta la referencia de *punto de generación* .</span><span class="sxs-lookup"><span data-stu-id="601bd-483">With the Main Camera selected you will notice the *ShapeFactory* script component is missing the *Spawn Point* reference.</span></span> <span data-ttu-id="601bd-484">Para corregirlo, arrastre el objeto **ShapeSpawnPoint** desde el *Panel jerarquía* hasta el destino de referencia de **punto de generación** .</span><span class="sxs-lookup"><span data-stu-id="601bd-484">To fix it, drag the **ShapeSpawnPoint** object from the *Hierarchy Panel* to the **Spawn Point** reference target.</span></span>

    ![establecer destino de referencia de generador de formas](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a><span data-ttu-id="601bd-486">Capítulo 9: creación de la clase fijamente</span><span class="sxs-lookup"><span data-stu-id="601bd-486">Chapter 9 - Create the Gaze class</span></span>

<span data-ttu-id="601bd-487">El último script que necesita crear es la clase *mira* .</span><span class="sxs-lookup"><span data-stu-id="601bd-487">The last script you need to create is the *Gaze* class.</span></span>

<span data-ttu-id="601bd-488">Esta clase es responsable de crear un **Raycast** que se proyectará hacia delante desde la cámara principal, para detectar qué objeto está examinando el usuario.</span><span class="sxs-lookup"><span data-stu-id="601bd-488">This class is responsible for creating a **Raycast** that will be projected forward from the Main Camera, to detect which object the user is looking at.</span></span> <span data-ttu-id="601bd-489">En este caso, Raycast deberá identificar si el usuario mira el objeto **GazeButton** en la escena y desencadena un comportamiento.</span><span class="sxs-lookup"><span data-stu-id="601bd-489">In this case, the Raycast will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="601bd-490">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="601bd-490">To create this Class:</span></span>

1.  <span data-ttu-id="601bd-491">Vaya a la carpeta **scripts** que creó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="601bd-491">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="601bd-492">Haga clic con el botón derecho en el panel Proyecto, **cree** >  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="601bd-492">Right-click in the Project Panel, **Create** > **C# Script**.</span></span> <span data-ttu-id="601bd-493">Llame al script *fijamente*.</span><span class="sxs-lookup"><span data-stu-id="601bd-493">Call the script *Gaze*.</span></span>

3.  <span data-ttu-id="601bd-494">Haga doble clic en el nuevo script de *miraciones* para abrirlo con *Visual Studio.*</span><span class="sxs-lookup"><span data-stu-id="601bd-494">Double click on the new *Gaze* script to open it with *Visual Studio.*</span></span>

4.  <span data-ttu-id="601bd-495">Asegúrese de que el siguiente espacio de nombres se incluye en la parte superior del script:</span><span class="sxs-lookup"><span data-stu-id="601bd-495">Ensure the following namespace is included at the top of the script:</span></span>

    ```csharp
        using UnityEngine;
    ```

5.  <span data-ttu-id="601bd-496">Después, agregue las siguientes variables dentro de la clase *mirate* :</span><span class="sxs-lookup"><span data-stu-id="601bd-496">Then add the following variables inside the *Gaze* class:</span></span>

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> <span data-ttu-id="601bd-497">Algunas de estas variables se podrán editar en el *Editor*.</span><span class="sxs-lookup"><span data-stu-id="601bd-497">Some of these variables will be able to be edited in the *Editor*.</span></span>

6.  <span data-ttu-id="601bd-498">Ahora es necesario agregar el código para los métodos *activo ()* e *Inicio ()* .</span><span class="sxs-lookup"><span data-stu-id="601bd-498">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span>

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  <span data-ttu-id="601bd-499">Agregue el código siguiente, que creará un objeto cursor en el inicio, junto con el método *Update ()* , que ejecutará el método Raycast, junto con el lugar donde se alterna el valor booleano GazeEnabled:</span><span class="sxs-lookup"><span data-stu-id="601bd-499">Add the following code, which will create a cursor object at start, along with the *Update()* method, which will run the Raycast method, along with being where the GazeEnabled boolean is toggled:</span></span>

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. <span data-ttu-id="601bd-500">A continuación, agregue el método *UpdateRaycast ()* , que proyectará un Raycast y detectará el destino de la visita.</span><span class="sxs-lookup"><span data-stu-id="601bd-500">Next add the *UpdateRaycast()* method, which will project a Raycast and detect the hit target.</span></span>

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;

                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. <span data-ttu-id="601bd-501">Por último, agregue el método *ResetFocusedObject ()* , que cambiará el color actual de los objetos GazeButton, lo que indicará si está creando una nueva forma o no.</span><span class="sxs-lookup"><span data-stu-id="601bd-501">Lastly, add the *ResetFocusedObject()* method, which will toggle the GazeButton objects current color, indicating whether it is creating a new shape or not.</span></span>

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  <span data-ttu-id="601bd-502">Guarde los cambios en Visual Studio antes de volver a Unity.</span><span class="sxs-lookup"><span data-stu-id="601bd-502">Save your changes in Visual Studio before returning to Unity.</span></span>

11.  <span data-ttu-id="601bd-503">Haga clic y arrastre la clase *mira* desde la carpeta scripts hasta el objeto **cámara principal** en el *Panel jerarquía*.</span><span class="sxs-lookup"><span data-stu-id="601bd-503">Click and drag the *Gaze* class from the Scripts folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-10---completing-the-azureservices-class"></a><span data-ttu-id="601bd-504">Capítulo 10: completar la clase AzureServices</span><span class="sxs-lookup"><span data-stu-id="601bd-504">Chapter 10 - Completing the AzureServices class</span></span>

<span data-ttu-id="601bd-505">Con los demás scripts en su lugar, ahora es posible *completar* la clase *AzureServices* .</span><span class="sxs-lookup"><span data-stu-id="601bd-505">With the other scripts in place, it is now possible to *complete* the *AzureServices* class.</span></span> <span data-ttu-id="601bd-506">Esto se logra mediante:</span><span class="sxs-lookup"><span data-stu-id="601bd-506">This will be achieved through:</span></span>

1.  <span data-ttu-id="601bd-507">Agregar un nuevo método denominado *CreateCloudIdentityAsync ()* para configurar las variables de autenticación necesarias para comunicarse con Azure.</span><span class="sxs-lookup"><span data-stu-id="601bd-507">Adding a new method named *CreateCloudIdentityAsync()*, to set up the authentication variables needed for communicating with Azure.</span></span>

    > <span data-ttu-id="601bd-508">Este método también comprobará la existencia de un archivo previamente almacenado que contenga la lista de formas.</span><span class="sxs-lookup"><span data-stu-id="601bd-508">This method will also check for the existence of a previously stored File containing the Shape List.</span></span>
    >
    > <span data-ttu-id="601bd-509">**Si se encuentra el archivo**, se deshabilitará el *usuario y*se desencadenará la creación de la forma, según el patrón de formas, tal como se almacena en el **archivo de Azure Storage**.</span><span class="sxs-lookup"><span data-stu-id="601bd-509">**If the file is found**, it will disable the user *Gaze*, and trigger Shape creation, according to the pattern of shapes, as stored in the **Azure Storage file**.</span></span> <span data-ttu-id="601bd-510">El usuario puede ver esto, ya que la **malla de texto** proporcionará la pantalla "almacenamiento" o "nuevo", según el origen de las formas.</span><span class="sxs-lookup"><span data-stu-id="601bd-510">The user can see this, as the **Text Mesh** will provide display 'Storage' or 'New', depending on the shapes origin.</span></span>
    >
    > <span data-ttu-id="601bd-511">**Si no se encuentra ningún archivo**, se habilitará la *mirada*, lo que permite al usuario crear formas al mirar el objeto **GazeButton** de la escena.</span><span class="sxs-lookup"><span data-stu-id="601bd-511">**If no file is found**, it will enable the *Gaze*, enabling the user to create shapes when looking at the **GazeButton** object in the scene.</span></span>

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  <span data-ttu-id="601bd-512">El siguiente fragmento de código se encuentra dentro del método *Start ()* ; donde se realizará una llamada al método *CreateCloudIdentityAsync ()* .</span><span class="sxs-lookup"><span data-stu-id="601bd-512">The next code snippet is from within the *Start()* method; wherein a call will be made to the *CreateCloudIdentityAsync()* method.</span></span> <span data-ttu-id="601bd-513">No dude en copiar sobre el método *Start ()* actual, con lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="601bd-513">Feel free to copy over your current *Start()* method, with the below:</span></span>

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  <span data-ttu-id="601bd-514">Rellene el código para el método *CallAzureFunctionForNextShape ()* .</span><span class="sxs-lookup"><span data-stu-id="601bd-514">Fill in the code for the method *CallAzureFunctionForNextShape()*.</span></span> <span data-ttu-id="601bd-515">Usará el *function App de Azure* creado anteriormente para solicitar un índice de forma.</span><span class="sxs-lookup"><span data-stu-id="601bd-515">You will use the previously created *Azure Function App* to request a shape index.</span></span> <span data-ttu-id="601bd-516">Una vez recibida la nueva forma, este método enviará la forma a la clase *ShapeFactory* para crear la nueva forma en la escena.</span><span class="sxs-lookup"><span data-stu-id="601bd-516">Once the new shape is received, this method will send the shape to the *ShapeFactory* class to create the new shape in the scene.</span></span> <span data-ttu-id="601bd-517">Use el código siguiente para completar el cuerpo de *CallAzureFunctionForNextShape ()* .</span><span class="sxs-lookup"><span data-stu-id="601bd-517">Use the code below to complete the body of *CallAzureFunctionForNextShape()*.</span></span>

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  <span data-ttu-id="601bd-518">Agregue un método para crear una cadena mediante la concatenación de los enteros almacenados en la lista de historial de formas y guárdelo en el *archivo de Azure Storage*.</span><span class="sxs-lookup"><span data-stu-id="601bd-518">Add a method to create a string, by concatenating the integers stored in the shape history list, and saving it in your *Azure Storage File*.</span></span>

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  <span data-ttu-id="601bd-519">Agregue un método para recuperar el texto almacenado en el archivo que se encuentra en el *archivo de Azure Storage* y *deserializarlo* en una lista.</span><span class="sxs-lookup"><span data-stu-id="601bd-519">Add a method to retrieve the text stored in the file located in your *Azure Storage File* and *deserialize* it into a list.</span></span>

6.  <span data-ttu-id="601bd-520">Una vez completado este proceso, el método vuelve a habilitar la mirada para que el usuario pueda agregar más formas a la escena.</span><span class="sxs-lookup"><span data-stu-id="601bd-520">Once this process is completed, the method re-enables the gaze so that the user can add more shapes to the scene.</span></span>

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  <span data-ttu-id="601bd-521">Guarde los cambios en Visual Studio antes de volver a Unity.</span><span class="sxs-lookup"><span data-stu-id="601bd-521">Save your changes in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-11---build-the-uwp-solution"></a><span data-ttu-id="601bd-522">Capítulo 11: compilar la solución UWP</span><span class="sxs-lookup"><span data-stu-id="601bd-522">Chapter 11 - Build the UWP Solution</span></span>

<span data-ttu-id="601bd-523">Para comenzar el proceso de compilación:</span><span class="sxs-lookup"><span data-stu-id="601bd-523">To begin the Build process:</span></span>

1.  <span data-ttu-id="601bd-524">Vaya a **archivo** > **configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="601bd-524">Go to **File** > **Build Settings**.</span></span>

    ![compilar la aplicación](images/AzureLabs-Lab5-54.png)

2.  <span data-ttu-id="601bd-526">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="601bd-526">Click **Build**.</span></span> <span data-ttu-id="601bd-527">Unity iniciará una ventana del *Explorador de archivos* , donde tendrá que crear y seleccionar una carpeta en la que compilar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="601bd-527">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="601bd-528">Cree esa carpeta ahora y asígnele el nombre *App*.</span><span class="sxs-lookup"><span data-stu-id="601bd-528">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="601bd-529">Después, con la carpeta de la *aplicación* seleccionada, presione **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="601bd-529">Then with the *App* folder selected, press **Select Folder**.</span></span>

3.  <span data-ttu-id="601bd-530">Unity comenzará a compilar el proyecto en la carpeta de la *aplicación* .</span><span class="sxs-lookup"><span data-stu-id="601bd-530">Unity will begin building your project to the *App* folder.</span></span>

4.  <span data-ttu-id="601bd-531">Una vez que Unity termine de compilar (puede tardar algún tiempo), se abrirá una ventana del *Explorador de archivos* en la ubicación de la compilación (Compruebe la barra de tareas, ya que es posible que no aparezca siempre por encima de las ventanas, pero le notificará la adición de una nueva ventana).</span><span class="sxs-lookup"><span data-stu-id="601bd-531">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploying-your-application"></a><span data-ttu-id="601bd-532">Capítulo 12: implementación de la aplicación</span><span class="sxs-lookup"><span data-stu-id="601bd-532">Chapter 12 - Deploying your application</span></span>

<span data-ttu-id="601bd-533">Para implementar la aplicación:</span><span class="sxs-lookup"><span data-stu-id="601bd-533">To deploy your application:</span></span>

1.  <span data-ttu-id="601bd-534">Navegue hasta la carpeta de la *aplicación* que se creó en el [último capítulo](#chapter-11---build-the-uwp-solution).</span><span class="sxs-lookup"><span data-stu-id="601bd-534">Navigate to the *App* folder which was created in the [last Chapter](#chapter-11---build-the-uwp-solution).</span></span> <span data-ttu-id="601bd-535">Verá un archivo con el nombre de la aplicación, con la extensión '. sln ', en la que debe hacer doble clic para abrirlo en *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="601bd-535">You will see a file with your apps name, with the '.sln' extension, which you should double-click, so to open it within *Visual Studio*.</span></span>

2.  <span data-ttu-id="601bd-536">En la **plataforma**de la solución, seleccione **x86, equipo local**.</span><span class="sxs-lookup"><span data-stu-id="601bd-536">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="601bd-537">En la **configuración de soluciones** , seleccione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="601bd-537">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="601bd-538">En el caso de Microsoft HoloLens, es posible que le resulte más fácil establecer esto en el *equipo remoto*, de modo que no esté anclado al equipo.</span><span class="sxs-lookup"><span data-stu-id="601bd-538">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="601bd-539">Sin embargo, también tendrá que hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="601bd-539">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="601bd-540">Conozca la **dirección IP** de HoloLens, que puede encontrarse en la **configuración** > **red & Internet** > **Wi-Fi** > **Opciones avanzadas**; IPv4 es la dirección que debe usar.</span><span class="sxs-lookup"><span data-stu-id="601bd-540">Know the **IP Address** of your HoloLens, which can be found within the **Settings** > **Network & Internet** > **Wi-Fi** > **Advanced Options**; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="601bd-541">Asegurarse de que el **modo de desarrollador** está **activado**; se encuentra en **configuración** > **Actualizar &**  > **de seguridad para desarrolladores**.</span><span class="sxs-lookup"><span data-stu-id="601bd-541">Ensure **Developer Mode** is **On**; found in **Settings** > **Update & Security** > **For developers**.</span></span>

    ![implementar solución](images/AzureLabs-Lab5-55.png)

4.  <span data-ttu-id="601bd-543">Vaya al menú **compilar** y haga clic en **implementar solución** para transferir localmente la aplicación a la máquina.</span><span class="sxs-lookup"><span data-stu-id="601bd-543">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="601bd-544">La aplicación debe aparecer ahora en la lista de aplicaciones instaladas, lista para iniciarse y probarse.</span><span class="sxs-lookup"><span data-stu-id="601bd-544">Your App should now appear in the list of installed apps, ready to be launched and tested!</span></span>

## <a name="your-finished-azure-functions-and-storage-application"></a><span data-ttu-id="601bd-545">La aplicación de almacenamiento y Azure Functions finalizada</span><span class="sxs-lookup"><span data-stu-id="601bd-545">Your finished Azure Functions and Storage Application</span></span>

<span data-ttu-id="601bd-546">Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha los servicios Azure Functions y Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="601bd-546">Congratulations, you built a mixed reality app that leverages both the Azure Functions and Azure Storage services.</span></span> <span data-ttu-id="601bd-547">La aplicación podrá dibujar en datos almacenados y proporcionar una acción basada en esos datos.</span><span class="sxs-lookup"><span data-stu-id="601bd-547">Your app will be able to draw on stored data, and provide an action based on that data.</span></span>

![final del producto final](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="601bd-549">Ejercicios de bonus</span><span class="sxs-lookup"><span data-stu-id="601bd-549">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="601bd-550">Ejercicio 1</span><span class="sxs-lookup"><span data-stu-id="601bd-550">Exercise 1</span></span>

<span data-ttu-id="601bd-551">Cree un segundo punto de generación y grabe el punto de generación a partir del que se creó un objeto.</span><span class="sxs-lookup"><span data-stu-id="601bd-551">Create a second spawn point and record which spawn point an object was created from.</span></span> <span data-ttu-id="601bd-552">Al cargar el archivo de datos, reproduzca las formas que se van a generar desde la ubicación en la que se crearon originalmente.</span><span class="sxs-lookup"><span data-stu-id="601bd-552">When you load the data file, replay the shapes being spawned from the location they originally were created.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="601bd-553">Ejercicio 2</span><span class="sxs-lookup"><span data-stu-id="601bd-553">Exercise 2</span></span>

<span data-ttu-id="601bd-554">Cree una manera de reiniciar la aplicación, en lugar de tener que volver a abrirla cada vez.</span><span class="sxs-lookup"><span data-stu-id="601bd-554">Create a way to restart the app, rather than having to re-open it each time.</span></span> <span data-ttu-id="601bd-555">La **carga de escenas** es un buen punto de partida.</span><span class="sxs-lookup"><span data-stu-id="601bd-555">**Loading Scenes** is a good spot to start.</span></span> <span data-ttu-id="601bd-556">Después de hacerlo, cree una manera de borrar la lista almacenada en *Azure Storage*, para que se pueda restablecer fácilmente desde la aplicación.</span><span class="sxs-lookup"><span data-stu-id="601bd-556">After doing that, create a way to clear the stored list in *Azure Storage*, so that it can be easily reset from your app.</span></span> 
