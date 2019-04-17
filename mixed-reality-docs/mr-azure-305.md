---
title: El Sr. y Azure 305 - funciones y almacenamiento
description: Realice este curso para obtener información sobre cómo implementar el almacenamiento de Azure y las funciones dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidad mixta, Azure, academy, unity, tutorial, api, funciones, almacenamiento, hololens, vr envolvente,
ms.openlocfilehash: a828c7f0ac3016462f5c7e874545bf50a2db6771
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598298"
---
>[!NOTE]
><span data-ttu-id="0873d-104">Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.</span><span class="sxs-lookup"><span data-stu-id="0873d-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="0873d-105">Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="0873d-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="0873d-106">Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.</span><span class="sxs-lookup"><span data-stu-id="0873d-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="0873d-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="0873d-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="0873d-108">Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0873d-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="0873d-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.</span><span class="sxs-lookup"><span data-stu-id="0873d-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-305-functions-and-storage"></a><span data-ttu-id="0873d-110">El Sr. y Azure 305: Funciones y almacenamiento</span><span class="sxs-lookup"><span data-stu-id="0873d-110">MR and Azure 305: Functions and storage</span></span>

![final producto-inicio](images/AzureLabs-Lab5-00.png)

<span data-ttu-id="0873d-112">En este curso, obtendrá información sobre cómo crear y usar Azure Functions y almacenar los datos con un recurso de almacenamiento de Azure, dentro de una aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="0873d-112">In this course, you will learn how to create and use Azure Functions and store data with an Azure Storage resource, within a mixed reality application.</span></span>

<span data-ttu-id="0873d-113">*Las funciones de Azure* es un servicio de Microsoft, que permite a los desarrolladores ejecutar pequeños fragmentos de código, "funciones", en Azure.</span><span class="sxs-lookup"><span data-stu-id="0873d-113">*Azure Functions* is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="0873d-114">Esto proporciona una manera para delegar el trabajo a la nube, en lugar de la aplicación local, lo que puede tener muchas ventajas.</span><span class="sxs-lookup"><span data-stu-id="0873d-114">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="0873d-115">*Las funciones de Azure* admite varios lenguajes de desarrollo, incluidos C\#, F\#, Node.js, Java y PHP.</span><span class="sxs-lookup"><span data-stu-id="0873d-115">*Azure Functions* supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="0873d-116">Para obtener más información, visite la [artículo de Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="0873d-116">For more information, visit the [Azure Functions article](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="0873d-117">*Almacenamiento de Azure* es un servicio de nube de Microsoft, lo que permite a los desarrolladores almacenar datos, con el seguro que será altamente disponible, seguro, duradero, escalable y redundante.</span><span class="sxs-lookup"><span data-stu-id="0873d-117">*Azure Storage* is a Microsoft cloud service, which allows developers to store data, with the insurance that it will be highly available, secure, durable, scalable, and redundant.</span></span> <span data-ttu-id="0873d-118">Esto significa que Microsoft controlará todas mantenimiento y los problemas críticos por usted.</span><span class="sxs-lookup"><span data-stu-id="0873d-118">This means Microsoft will handle all maintenance, and critical problems for you.</span></span> <span data-ttu-id="0873d-119">Para obtener más información, visite la [artículo de Azure Storage](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span><span class="sxs-lookup"><span data-stu-id="0873d-119">For more information, visit the [Azure Storage article](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span></span>

<span data-ttu-id="0873d-120">Una vez completado este curso, tendrá una aplicación de envolventes auriculares de realidad mixta que podrá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="0873d-120">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="0873d-121">Permitir que el usuario que mirar en torno a una escena.</span><span class="sxs-lookup"><span data-stu-id="0873d-121">Allow the user to gaze around a scene.</span></span>
2.  <span data-ttu-id="0873d-122">Desencadenar la creación de objetos cuando el usuario gazes en 3D "button".</span><span class="sxs-lookup"><span data-stu-id="0873d-122">Trigger the spawning of objects when the user gazes at a 3D 'button'.</span></span>
3.  <span data-ttu-id="0873d-123">Elegirá los objetos generados por una función de Azure.</span><span class="sxs-lookup"><span data-stu-id="0873d-123">The spawned objects will be chosen by an Azure Function.</span></span>
4.  <span data-ttu-id="0873d-124">Como cada objeto se genera, la aplicación almacenará el tipo de objeto en un *Azure File*, que se encuentra en *Azure Storage*.</span><span class="sxs-lookup"><span data-stu-id="0873d-124">As each object is spawned, the application will store the object type in an *Azure File*, located in *Azure Storage*.</span></span>
5.  <span data-ttu-id="0873d-125">Al cargar una segunda vez, el *Azure File* datos se recuperan y se usa para reproducir las acciones de generación de la instancia anterior de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="0873d-125">Upon loading a second time, the *Azure File* data will be retrieved, and used to replay the spawning actions from the previous instance of the application.</span></span>

<span data-ttu-id="0873d-126">En la aplicación, es depende de usted sobre cómo se integrará los resultados con el diseño.</span><span class="sxs-lookup"><span data-stu-id="0873d-126">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="0873d-127">Este curso está diseñado para mostrarle cómo integrar un servicio de Azure con el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="0873d-127">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="0873d-128">Es su trabajo consiste en usar los conocimientos que obtendrá de este curso para mejorar su aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="0873d-128">It is your job to use the knowledge you gain from this course to enhance your mixed reality Application.</span></span>

## <a name="device-support"></a><span data-ttu-id="0873d-129">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="0873d-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="0873d-130">Curso</span><span class="sxs-lookup"><span data-stu-id="0873d-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="0873d-131"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="0873d-131"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="0873d-132"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="0873d-132"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="0873d-133">El Sr. y Azure 305: Funciones y almacenamiento</span><span class="sxs-lookup"><span data-stu-id="0873d-133">MR and Azure 305: Functions and storage</span></span></td><td style="text-align: center;"> <span data-ttu-id="0873d-134">✔️</span><span class="sxs-lookup"><span data-stu-id="0873d-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="0873d-135">✔️</span><span class="sxs-lookup"><span data-stu-id="0873d-135">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="0873d-136">Aunque este curso se centra principalmente en inmersivos (VR) Windows Mixed Reality, también puede aplicar lo aprendido en este curso de Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0873d-136">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="0873d-137">Como seguir el curso, verá notas en cualquier cambio que deberá emplear para admitir HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0873d-137">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0873d-138">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="0873d-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="0873d-139">Este tutorial está diseñado para los desarrolladores con experiencia básica con Unity y C#.</span><span class="sxs-lookup"><span data-stu-id="0873d-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="0873d-140">También Ten en cuenta que los requisitos previos y las instrucciones escritas en este documento representan lo que se ha probado y comprobado en el momento de redactar (mayo de 2018).</span><span class="sxs-lookup"><span data-stu-id="0873d-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="0873d-141">Es libre de usar el software más reciente, como se muestra en el [instalar las herramientas de](install-the-tools.md) artículo, aunque no se debe suponer que la información de este curso perfectamente coincida con lo que encontrará en el software más reciente que se indica a continuación .</span><span class="sxs-lookup"><span data-stu-id="0873d-141">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="0873d-142">Se recomiendan el siguiente hardware y software para este curso:</span><span class="sxs-lookup"><span data-stu-id="0873d-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="0873d-143">Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desarrollo de auriculares envolvente (VR)</span><span class="sxs-lookup"><span data-stu-id="0873d-143">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="0873d-144">Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="0873d-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="0873d-145">El SDK más reciente de Windows 10</span><span class="sxs-lookup"><span data-stu-id="0873d-145">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="0873d-146">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="0873d-146">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="0873d-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0873d-147">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="0873d-148">Un [auriculares de Windows Mixed Reality envolventes (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="0873d-148">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="0873d-149">Una suscripción a una cuenta de Azure para crear recursos de Azure</span><span class="sxs-lookup"><span data-stu-id="0873d-149">A subscription to an Azure account for creating Azure resources</span></span>
- <span data-ttu-id="0873d-150">Acceso a Internet para la recuperación de datos e instalación de Azure</span><span class="sxs-lookup"><span data-stu-id="0873d-150">Internet access for Azure setup and data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="0873d-151">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="0873d-151">Before you start</span></span>

<span data-ttu-id="0873d-152">Para evitar problemas de creación de este proyecto, se recomienda encarecidamente que cree el proyecto se ha mencionado en este tutorial en una carpeta raíz o cerca de la raíz (rutas de acceso de carpeta largo pueden causar problemas en tiempo de compilación).</span><span class="sxs-lookup"><span data-stu-id="0873d-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="0873d-153">Capítulo 1: el Portal de Azure</span><span class="sxs-lookup"><span data-stu-id="0873d-153">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="0873d-154">Para usar el **servicio Azure Storage**, deberá crear y configurar un **cuenta de almacenamiento** en Azure portal.</span><span class="sxs-lookup"><span data-stu-id="0873d-154">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="0873d-155">Inicie sesión en el [Portal Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="0873d-155">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="0873d-156">Si no dispone de una cuenta de Azure, deberá crear uno.</span><span class="sxs-lookup"><span data-stu-id="0873d-156">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="0873d-157">Si está siguiendo este tutorial en una situación de aula o laboratorio, pida el instructor o uno de los a los supervisores de ayuda para instalar la nueva cuenta.</span><span class="sxs-lookup"><span data-stu-id="0873d-157">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="0873d-158">Una vez que haya iniciado sesión, haga clic en **New** en la esquina superior izquierda esquina y busque *cuenta de almacenamiento*y haga clic en **ENTRAR**.</span><span class="sxs-lookup"><span data-stu-id="0873d-158">Once you are logged in, click on **New** in the top left corner, and search for *Storage account*, and click **Enter**.</span></span>

    ![búsqueda de almacenamiento de Azure](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > <span data-ttu-id="0873d-160">La palabra **New** se han reemplazado con **crear un recurso**, en los portales más reciente.</span><span class="sxs-lookup"><span data-stu-id="0873d-160">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="0873d-161">La nueva página proporcionará una descripción de la *cuenta de Azure Storage* service.</span><span class="sxs-lookup"><span data-stu-id="0873d-161">The new page will provide a description of the *Azure Storage account* service.</span></span> <span data-ttu-id="0873d-162">En la parte inferior izquierda de este símbolo del sistema, seleccione el **crear** botón para crear una asociación con este servicio.</span><span class="sxs-lookup"><span data-stu-id="0873d-162">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![Crear servicio](images/AzureLabs-Lab5-02.png)

4.  <span data-ttu-id="0873d-164">Una vez que ha hecho clic **crear**:</span><span class="sxs-lookup"><span data-stu-id="0873d-164">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="0873d-165">Insertar un *nombre* para su cuenta, tenga en cuenta este campo sólo acepta números y letras minúsculas.</span><span class="sxs-lookup"><span data-stu-id="0873d-165">Insert a *Name* for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="0873d-166">Para *modelo de implementación*, seleccione **Administrador de recursos**.</span><span class="sxs-lookup"><span data-stu-id="0873d-166">For *Deployment model*, select **Resource manager**.</span></span>

    3.  <span data-ttu-id="0873d-167">Para *tipo de cuenta*, seleccione **almacenamiento (uso general v1)**.</span><span class="sxs-lookup"><span data-stu-id="0873d-167">For *Account kind*, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="0873d-168">Determinar la *ubicación* para el grupo de recursos (si está creando un nuevo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="0873d-168">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="0873d-169">La ubicación sería lo ideal es que en la región donde desea ejecutar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="0873d-169">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="0873d-170">Algunos recursos de Azure solo están disponibles en determinadas regiones.</span><span class="sxs-lookup"><span data-stu-id="0873d-170">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="0873d-171">Para *replicación* seleccione **lectura-access--almacenamiento con redundancia geográfica (RA-GRS)**.</span><span class="sxs-lookup"><span data-stu-id="0873d-171">For *Replication* select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="0873d-172">Para *rendimiento*, seleccione **estándar**.</span><span class="sxs-lookup"><span data-stu-id="0873d-172">For *Performance*, select **Standard**.</span></span>

    7.  <span data-ttu-id="0873d-173">Deje *se requiere transferencia segura* como **deshabilitado**.</span><span class="sxs-lookup"><span data-stu-id="0873d-173">Leave *Secure transfer required* as **Disabled**.</span></span>

    8.  <span data-ttu-id="0873d-174">Seleccione un *suscripción*.</span><span class="sxs-lookup"><span data-stu-id="0873d-174">Select a *Subscription*.</span></span>

    9. <span data-ttu-id="0873d-175">Elija un *grupo de recursos* o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="0873d-175">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="0873d-176">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="0873d-176">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="0873d-177">Se recomienda mantener todos los servicios de Azure asociados a un proyecto único (por ejemplo, por ejemplo, estos laboratorios) en un grupo de recursos comunes).</span><span class="sxs-lookup"><span data-stu-id="0873d-177">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="0873d-178">Si desea leer más acerca de los grupos de recursos de Azure, inicie [visite el artículo del grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="0873d-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="0873d-179">También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.</span><span class="sxs-lookup"><span data-stu-id="0873d-179">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    11. <span data-ttu-id="0873d-180">Selecciona **Crear**.</span><span class="sxs-lookup"><span data-stu-id="0873d-180">Select **Create**.</span></span>

        ![información de entrada de servicio](images/AzureLabs-Lab5-03.png)

5.  <span data-ttu-id="0873d-182">Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="0873d-182">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="0873d-183">Una vez creada la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="0873d-183">A notification will appear in the portal once the Service instance is created.</span></span>

    ![nueva notificación en azure portal](images/AzureLabs-Lab5-04.png)

7.  <span data-ttu-id="0873d-185">Haga clic en las notificaciones para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="0873d-185">Click on the notifications to explore your new Service instance.</span></span>

    ![Ir al recurso](images/AzureLabs-Lab5-05.png)

8.  <span data-ttu-id="0873d-187">Haga clic en el **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="0873d-187">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="0873d-188">Se le dirigirá a la nueva *cuenta de almacenamiento* instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="0873d-188">You will be taken to your new *Storage account* service instance.</span></span>

    ![teclas de acceso](images/AzureLabs-Lab5-06.png)

9.  <span data-ttu-id="0873d-190">Haga clic en *claves de acceso*para revelar los puntos de conexión para este servicio en la nube.</span><span class="sxs-lookup"><span data-stu-id="0873d-190">Click *Access keys*, to reveal the endpoints for this cloud service.</span></span> <span data-ttu-id="0873d-191">Usar *el Bloc de notas* o similar, para copiar una de las claves para su uso posterior.</span><span class="sxs-lookup"><span data-stu-id="0873d-191">Use *Notepad* or similar, to copy one of your keys for use later.</span></span> <span data-ttu-id="0873d-192">Además, tenga en cuenta la *cadena de conexión* valor, tal como se usará en el *AzureServices* (clase), que creará más adelante.</span><span class="sxs-lookup"><span data-stu-id="0873d-192">Also, note the *Connection string* value, as it will be used in the *AzureServices* class, which you will create later.</span></span>

    ![Copie la cadena de conexión](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a><span data-ttu-id="0873d-194">Capítulo 2: configurar una función de Azure</span><span class="sxs-lookup"><span data-stu-id="0873d-194">Chapter 2 - Setting up an Azure Function</span></span>

<span data-ttu-id="0873d-195">Ahora escribirá un **Azure** **función** en el servicio de Azure.</span><span class="sxs-lookup"><span data-stu-id="0873d-195">You will now write an **Azure** **Function** in the Azure Service.</span></span>

<span data-ttu-id="0873d-196">Puede usar un **Azure Function** para casi todo lo que haría con una función clásica en el código, la diferencia es que cualquier aplicación que disponga de credenciales para tener acceso a su cuenta de Azure puede tener acceso a esta función hacer.</span><span class="sxs-lookup"><span data-stu-id="0873d-196">You can use an **Azure Function** to do nearly anything that you would do with a classic function in your code, the difference being that this function can be accessed by any application that has credentials to access your Azure Account.</span></span>

<span data-ttu-id="0873d-197">Para crear una función de Azure:</span><span class="sxs-lookup"><span data-stu-id="0873d-197">To create an Azure Function:</span></span>

1.  <span data-ttu-id="0873d-198">Desde su *Portal de Azure*, haga clic en **New** en la esquina superior izquierda esquina y busque *Function App*y haga clic en **ENTRAR**.</span><span class="sxs-lookup"><span data-stu-id="0873d-198">From your *Azure Portal*, click on **New** in the top left corner, and search for *Function App*, and click **Enter**.</span></span>

    ![Crear aplicación de función](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > <span data-ttu-id="0873d-200">La palabra **New** se han reemplazado con **crear un recurso**, en los portales más reciente.</span><span class="sxs-lookup"><span data-stu-id="0873d-200">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

2.  <span data-ttu-id="0873d-201">La nueva página proporcionará una descripción de la *Azure Function App* service.</span><span class="sxs-lookup"><span data-stu-id="0873d-201">The new page will provide a description of the *Azure Function App* service.</span></span> <span data-ttu-id="0873d-202">En la parte inferior izquierda de este símbolo del sistema, seleccione el **crear** botón para crear una asociación con este servicio.</span><span class="sxs-lookup"><span data-stu-id="0873d-202">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![información de la aplicación de función](images/AzureLabs-Lab5-09.png)

3.  <span data-ttu-id="0873d-204">Una vez que ha hecho clic **crear**:</span><span class="sxs-lookup"><span data-stu-id="0873d-204">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="0873d-205">Proporcione un *nombre de la aplicación*.</span><span class="sxs-lookup"><span data-stu-id="0873d-205">Provide an *App name*.</span></span> <span data-ttu-id="0873d-206">Solo letras y números se pueden emplear (ya sea en mayúsculas o minúsculas se permite).</span><span class="sxs-lookup"><span data-stu-id="0873d-206">Only letters and numbers can be used here (either upper or lower case is allowed).</span></span>

    2.  <span data-ttu-id="0873d-207">Seleccione la *suscripción*.</span><span class="sxs-lookup"><span data-stu-id="0873d-207">Select your preferred *Subscription*.</span></span>

    3. <span data-ttu-id="0873d-208">Elija un *grupo de recursos* o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="0873d-208">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="0873d-209">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="0873d-209">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="0873d-210">Se recomienda mantener todos los servicios de Azure asociados a un proyecto único (por ejemplo, por ejemplo, estos laboratorios) en un grupo de recursos comunes).</span><span class="sxs-lookup"><span data-stu-id="0873d-210">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="0873d-211">Si desea leer más acerca de los grupos de recursos de Azure, inicie [visite el artículo del grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="0873d-211">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="0873d-212">Para este ejercicio, seleccione *Windows* como los elegidos **OS**.</span><span class="sxs-lookup"><span data-stu-id="0873d-212">For this exercise, select *Windows* as the chosen **OS**.</span></span>

    5.  <span data-ttu-id="0873d-213">Seleccione *Plan de consumo* para el **Plan de hospedaje**.</span><span class="sxs-lookup"><span data-stu-id="0873d-213">Select *Consumption Plan* for the **Hosting Plan**.</span></span>

    6.  <span data-ttu-id="0873d-214">Determinar la *ubicación* para el grupo de recursos (si está creando un nuevo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="0873d-214">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="0873d-215">La ubicación sería lo ideal es que en la región donde desea ejecutar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="0873d-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="0873d-216">Algunos recursos de Azure solo están disponibles en determinadas regiones.</span><span class="sxs-lookup"><span data-stu-id="0873d-216">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="0873d-217">Para obtener un rendimiento óptimo, seleccione la misma región que la cuenta de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="0873d-217">For optimal performance, select the same region as the storage account.</span></span>

    7.  <span data-ttu-id="0873d-218">Para *almacenamiento*, seleccione **usar existente**, y, a continuación, mediante el menú desplegable, encontrar el almacenamiento creado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0873d-218">For *Storage*, select **Use existing**, and then using the dropdown menu, find your previously created storage.</span></span>

    8.  <span data-ttu-id="0873d-219">Deje *Application Insights* desactivado para este ejercicio.</span><span class="sxs-lookup"><span data-stu-id="0873d-219">Leave *Application Insights* off for this exercise.</span></span>

        ![detalles de la aplicación de función de entrada](images/AzureLabs-Lab5-10.png)

4.  <span data-ttu-id="0873d-221">Haga clic en el botón **Crear**.</span><span class="sxs-lookup"><span data-stu-id="0873d-221">Click the **Create** button.</span></span>

5.  <span data-ttu-id="0873d-222">Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="0873d-222">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="0873d-223">Una vez creada la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="0873d-223">A notification will appear in the portal once the Service instance is created.</span></span>

    ![nueva notificación en azure portal](images/AzureLabs-Lab5-11.png)

7.  <span data-ttu-id="0873d-225">Haga clic en las notificaciones para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="0873d-225">Click on the notifications to explore your new Service instance.</span></span> 

    ![Vaya a la aplicación de función de recursos](images/AzureLabs-Lab5-12.png)

8.  <span data-ttu-id="0873d-227">Haga clic en el **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="0873d-227">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="0873d-228">Se le dirigirá a la nueva *Function App* instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="0873d-228">You will be taken to your new *Function App* service instance.</span></span>

9.  <span data-ttu-id="0873d-229">En el *Function App* panel, mantenga el mouse sobre *funciones*, se encuentra en el panel de la izquierda y, a continuación, haga clic en el **+ (signo más)** símbolos.</span><span class="sxs-lookup"><span data-stu-id="0873d-229">On the *Function App* dashboard, hover your mouse over *Functions*, found within the panel on the left, and then click the **+ (plus)** symbol.</span></span>

    ![Crear una nueva función](images/AzureLabs-Lab5-13.png)

10. <span data-ttu-id="0873d-231">En la página siguiente, asegúrese de **Webhook y API** está seleccionada y para *elegir un idioma,* seleccione **CSharp**, ya que será el idioma utilizado para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="0873d-231">On the next page, ensure **Webhook + API** is selected, and for *Choose a language,* select **CSharp**, as this will be the language used for this tutorial.</span></span> <span data-ttu-id="0873d-232">Por último, haga clic en el **crear esta función** botón.</span><span class="sxs-lookup"><span data-stu-id="0873d-232">Lastly, click the **Create this function** button.</span></span>

    ![Seleccione web gancho csharp](images/AzureLabs-Lab5-14.png)

11. <span data-ttu-id="0873d-234">Debería ir al código de página (run.csx), si no, haga clic en la función recién creada en la lista de funciones dentro del panel de la izquierda.</span><span class="sxs-lookup"><span data-stu-id="0873d-234">You should be taken to the code page (run.csx), if not though, click on the newly created Function in the Functions list within the panel on the left.</span></span>

    ![Abra la nueva función](images/AzureLabs-Lab5-15.png)

12. <span data-ttu-id="0873d-236">Copie el código siguiente en la función.</span><span class="sxs-lookup"><span data-stu-id="0873d-236">Copy the following code into your function.</span></span> <span data-ttu-id="0873d-237">Esta función simplemente devolverá un entero aleatorio entre 0 y 2, cuando se llama.</span><span class="sxs-lookup"><span data-stu-id="0873d-237">This function will simply return a random integer between 0 and 2 when called.</span></span> <span data-ttu-id="0873d-238">No preocuparse por el código existente, no dude en pegue encima de él.</span><span class="sxs-lookup"><span data-stu-id="0873d-238">Do not worry about the existing code, feel free to paste over the top of it.</span></span>

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

13. <span data-ttu-id="0873d-239">Selecciona **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="0873d-239">Select **Save**.</span></span>

14. <span data-ttu-id="0873d-240">El resultado debería parecerse a la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="0873d-240">The result should look like the image below.</span></span>

15. <span data-ttu-id="0873d-241">Haga clic en **obtener la dirección URL de función** y tome nota de la *extremo* muestra.</span><span class="sxs-lookup"><span data-stu-id="0873d-241">Click on **Get function URL** and take note of the *endpoint* displayed.</span></span> <span data-ttu-id="0873d-242">Debe insertar en el *AzureServices* clase que creará más adelante en este curso.</span><span class="sxs-lookup"><span data-stu-id="0873d-242">You will need to insert it into the *AzureServices* class that you will create later in this course.</span></span>

    ![obtener punto de conexión de función](images/AzureLabs-Lab5-16.png)

    ![obtener punto de conexión de función](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="0873d-245">Capítulo 3: configurar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="0873d-245">Chapter 3 - Setting up the Unity project</span></span>

<span data-ttu-id="0873d-246">El siguiente es un conjunto típico de para el desarrollo con la realidad mixta y por lo tanto, es una buena plantilla para otros proyectos.</span><span class="sxs-lookup"><span data-stu-id="0873d-246">The following is a typical set up for developing with Mixed Reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="0873d-247">Configurar y probar los auriculares de realidad mixta envolventes.</span><span class="sxs-lookup"><span data-stu-id="0873d-247">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="0873d-248">Podrá **no** requieren controladores de movimiento de este curso.</span><span class="sxs-lookup"><span data-stu-id="0873d-248">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="0873d-249">Si necesita admite la configuración de los auriculares envolventes, [visite la realidad mixta configurar artículo](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="0873d-249">If you need support setting up the immersive headset, please [visit the mixed reality set up article](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="0873d-250">Abra Unity y haga clic en **New**.</span><span class="sxs-lookup"><span data-stu-id="0873d-250">Open Unity and click **New**.</span></span>

    ![Crear nuevo proyecto de unity](images/AzureLabs-Lab5-17.png)

2.  <span data-ttu-id="0873d-252">Ahora deberá proporcionar un nombre de proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="0873d-252">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="0873d-253">Insertar **MR_Azure_Functions**.</span><span class="sxs-lookup"><span data-stu-id="0873d-253">Insert **MR_Azure_Functions**.</span></span> <span data-ttu-id="0873d-254">Asegúrese de que el tipo de proyecto se establece en **3D**.</span><span class="sxs-lookup"><span data-stu-id="0873d-254">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="0873d-255">Establecer el *ubicación* a algún lugar adecuado para usted (Recuerde, es mejor cuanto más se acerque a los directorios raíz).</span><span class="sxs-lookup"><span data-stu-id="0873d-255">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="0873d-256">A continuación, haga clic en **crear un proyecto**.</span><span class="sxs-lookup"><span data-stu-id="0873d-256">Then, click **Create project**.</span></span>

    ![Asigne un nombre nuevo proyecto de unity](images/AzureLabs-Lab5-18.png)

3.  <span data-ttu-id="0873d-258">Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="0873d-258">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="0873d-259">Vaya a **editar* > *preferencias** y, a continuación, en la ventana nueva, vaya a **herramientas externas**.</span><span class="sxs-lookup"><span data-stu-id="0873d-259">Go to **Edit* > *Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="0873d-260">Cambio **External Script Editor** a **de Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="0873d-260">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="0873d-261">Cerrar la **preferencias** ventana.</span><span class="sxs-lookup"><span data-stu-id="0873d-261">Close the **Preferences** window.</span></span>

    ![conjunto de visual studio como editor de script](images/AzureLabs-Lab5-19.png)

4.  <span data-ttu-id="0873d-263">A continuación, vaya a **archivo > configuración de compilación** y cambiar la plataforma a **Universal Windows Platform**, haciendo clic en el **Cambiar plataforma** botón.</span><span class="sxs-lookup"><span data-stu-id="0873d-263">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![cambiar la plataforma a uwp](images/AzureLabs-Lab5-20.png)

5.  <span data-ttu-id="0873d-265">Vaya a **archivo > configuración de compilación** y asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="0873d-265">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="0873d-266">**Dispositivo de destino** está establecido en **cualquier dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="0873d-266">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="0873d-267">Para Microsoft HoloLens, establezca **dispositivo de destino** a *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="0873d-267">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="0873d-268">**Tipo de compilación** está establecido en **D3D**</span><span class="sxs-lookup"><span data-stu-id="0873d-268">**Build Type** is set to **D3D**</span></span>

    3. <span data-ttu-id="0873d-269">**SDK** está establecido en **instalada más reciente**</span><span class="sxs-lookup"><span data-stu-id="0873d-269">**SDK** is set to **Latest installed**</span></span>

    4. <span data-ttu-id="0873d-270">**Versión de Visual Studio** está establecido en **instalada más reciente**</span><span class="sxs-lookup"><span data-stu-id="0873d-270">**Visual Studio Version** is set to **Latest installed**</span></span>

    5. <span data-ttu-id="0873d-271">**Compilar y ejecutar** está establecido en **máquina Local**</span><span class="sxs-lookup"><span data-stu-id="0873d-271">**Build and Run** is set to **Local Machine**</span></span>

    6. <span data-ttu-id="0873d-272">Guarde la escena y agregarlo a la compilación.</span><span class="sxs-lookup"><span data-stu-id="0873d-272">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="0873d-273">Hacer esto seleccionando **agregar escenas abierto**.</span><span class="sxs-lookup"><span data-stu-id="0873d-273">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="0873d-274">Aparecerá el guardado de la ventana.</span><span class="sxs-lookup"><span data-stu-id="0873d-274">A save window will appear.</span></span>

            ![Agregar escenas abiertos](images/AzureLabs-Lab5-21.png)

        2.  <span data-ttu-id="0873d-276">Cree una nueva carpeta de esto y cualquier futuro, escena, a continuación, seleccione el **nueva carpeta** botón para crear una nueva carpeta y asígnele el nombre **escenas**.</span><span class="sxs-lookup"><span data-stu-id="0873d-276">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Crear carpeta de segundo plano](images/AzureLabs-Lab5-22.png)

        3.  <span data-ttu-id="0873d-278">Abra el recién creado **escenas** carpeta y, a continuación, en el **nombre de archivo:** campo de texto, escriba **FunctionsScene**, a continuación, presione **guardar**.</span><span class="sxs-lookup"><span data-stu-id="0873d-278">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **FunctionsScene**, then press **Save**.</span></span>

            ![Guardar escena de funciones](images/AzureLabs-Lab5-23.png)

6.  <span data-ttu-id="0873d-280">El resto de la configuración, en **configuración de compilación**, debe dejarse como predeterminada por ahora.</span><span class="sxs-lookup"><span data-stu-id="0873d-280">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

    ![Guardar escena de funciones](images/AzureLabs-Lab5-24.png)

7.  <span data-ttu-id="0873d-282">En el *configuración de compilación* ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el *Inspector* se encuentra.</span><span class="sxs-lookup"><span data-stu-id="0873d-282">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

    ![configuración del Reproductor en inspector](images/AzureLabs-Lab5-25.png)

8.  <span data-ttu-id="0873d-284">En este panel, es necesario comprobar algunas opciones de configuración:</span><span class="sxs-lookup"><span data-stu-id="0873d-284">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="0873d-285">En el **otra configuración** pestaña:</span><span class="sxs-lookup"><span data-stu-id="0873d-285">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="0873d-286">**Versión en tiempo de ejecución de secuencias de comandos** debe ser **Experimental** (.NET 4.6 equivalente), que desencadenará una necesidad de reiniciar el Editor.</span><span class="sxs-lookup"><span data-stu-id="0873d-286">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>
        2.  <span data-ttu-id="0873d-287">**Scripting de back-end** debe ser **.NET**</span><span class="sxs-lookup"><span data-stu-id="0873d-287">**Scripting Backend** should be **.NET**</span></span>
        3.  <span data-ttu-id="0873d-288">**Nivel de compatibilidad de API** debe ser **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="0873d-288">**API Compatibility Level** should be **.NET 4.6**</span></span>

    2.  <span data-ttu-id="0873d-289">Dentro de la **configuración de publicación** ficha **capacidades**, consulte:</span><span class="sxs-lookup"><span data-stu-id="0873d-289">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>
        
        -  <span data-ttu-id="0873d-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="0873d-290">**InternetClient**</span></span>

            ![conjunto de capacidades](images/AzureLabs-Lab5-26.png)

    3.  <span data-ttu-id="0873d-292">Más abajo el panel, en **XR configuración** (bajo **configuración de publicación**), graduación **admite la realidad Virtual**, asegúrese de que el **Windows Mixed Reality SDK** se agrega.</span><span class="sxs-lookup"><span data-stu-id="0873d-292">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![configuración del conjunto de XR](images/AzureLabs-Lab5-27.png)

9.  <span data-ttu-id="0873d-294">En *configuración de compilación* *Unity C# proyectos* ya no está atenuada; Marque la casilla situada junto a esto.</span><span class="sxs-lookup"><span data-stu-id="0873d-294">Back in *Build Settings* *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

    ![proyectos de c# graduación](images/AzureLabs-Lab5-28.png)

10.  <span data-ttu-id="0873d-296">Cierre la ventana de configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="0873d-296">Close the Build Settings window.</span></span>

11. <span data-ttu-id="0873d-297">Guarde la escena y el proyecto (**archivo > Guardar ESCENA / archivo > Guardar proyecto**).</span><span class="sxs-lookup"><span data-stu-id="0873d-297">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-4---setup-main-camera"></a><span data-ttu-id="0873d-298">Capítulo 4: configuración de cámara principal</span><span class="sxs-lookup"><span data-stu-id="0873d-298">Chapter 4 - Setup Main Camera</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0873d-299">Si desea omitir la *configurar Unity* componentes de este curso y continuar directamente en código, no dude en [descargar este .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)e importarlo en el proyecto como un [personalizado Paquete](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="0873d-299">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="0873d-300">Esto también contendrá los archivos DLL en el capítulo siguiente.</span><span class="sxs-lookup"><span data-stu-id="0873d-300">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="0873d-301">Después de la importación, continuar desde [capítulo 7](#chapter-7---create-the-azureservices-class).</span><span class="sxs-lookup"><span data-stu-id="0873d-301">After import, continue from [Chapter 7](#chapter-7---create-the-azureservices-class).</span></span> 

1.  <span data-ttu-id="0873d-302">En el *jerarquía Panel*, encontrará un objeto denominado **cámara principal**, este objeto representa el punto de vista de "head" una vez que esté "dentro" de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="0873d-302">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your "head" point of view once you are "inside" your application.</span></span>

2.  <span data-ttu-id="0873d-303">Con el panel de Unity delante de usted, seleccione el **Main cámara GameObject**.</span><span class="sxs-lookup"><span data-stu-id="0873d-303">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="0873d-304">Observará que el *Panel Inspector* (generalmente se encuentra a la derecha, en el panel) mostrará los distintos componentes de la que *GameObject*, con *transformar* en la parte superior, seguido por *cámara*y algunos otros componentes.</span><span class="sxs-lookup"><span data-stu-id="0873d-304">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="0873d-305">Deberá restablecer la transformación de la cámara principal, por lo que está colocado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0873d-305">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>

3.  <span data-ttu-id="0873d-306">Para ello, seleccione el **engranaje** icono situado junto a la cámara *transformar* componente y, a continuación, seleccione **restablecer**.</span><span class="sxs-lookup"><span data-stu-id="0873d-306">To do this, select the **Gear** icon next to the Camera's *Transform* component, and select **Reset**.</span></span>

    ![Restablecer transformación](images/AzureLabs-Lab5-29.png)

4.  <span data-ttu-id="0873d-308">A continuación, actualice el **transformar** componente tenga el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="0873d-308">Then update the **Transform** component to look like:</span></span>

    |         |    <span data-ttu-id="0873d-309">TRANSFORMACIÓN - POSICIÓN</span><span class="sxs-lookup"><span data-stu-id="0873d-309">TRANSFORM - POSITION</span></span>   |       |
    | :-----: | :-----------------------: | :----:|
    | <span data-ttu-id="0873d-310">**X**</span><span class="sxs-lookup"><span data-stu-id="0873d-310">**X**</span></span>   | <span data-ttu-id="0873d-311">**Y**</span><span class="sxs-lookup"><span data-stu-id="0873d-311">**Y**</span></span>                     | <span data-ttu-id="0873d-312">**Z**</span><span class="sxs-lookup"><span data-stu-id="0873d-312">**Z**</span></span> |
    | <span data-ttu-id="0873d-313">0</span><span class="sxs-lookup"><span data-stu-id="0873d-313">0</span></span>       | <span data-ttu-id="0873d-314">1</span><span class="sxs-lookup"><span data-stu-id="0873d-314">1</span></span>                         | <span data-ttu-id="0873d-315">0</span><span class="sxs-lookup"><span data-stu-id="0873d-315">0</span></span>     |    

    |       | <span data-ttu-id="0873d-316">-TRANSFORMACIÓN DE GIRO</span><span class="sxs-lookup"><span data-stu-id="0873d-316">TRANSFORM - ROTATION</span></span> |       |
    | :---: | :------------------: | :----:|
    | <span data-ttu-id="0873d-317">**X**</span><span class="sxs-lookup"><span data-stu-id="0873d-317">**X**</span></span> | <span data-ttu-id="0873d-318">**Y**</span><span class="sxs-lookup"><span data-stu-id="0873d-318">**Y**</span></span>                | <span data-ttu-id="0873d-319">**Z**</span><span class="sxs-lookup"><span data-stu-id="0873d-319">**Z**</span></span> |
    | <span data-ttu-id="0873d-320">0</span><span class="sxs-lookup"><span data-stu-id="0873d-320">0</span></span>     | <span data-ttu-id="0873d-321">0</span><span class="sxs-lookup"><span data-stu-id="0873d-321">0</span></span>                    | <span data-ttu-id="0873d-322">0</span><span class="sxs-lookup"><span data-stu-id="0873d-322">0</span></span>     |

    |       | <span data-ttu-id="0873d-323">TRANSFORMACIÓN - ESCALADO</span><span class="sxs-lookup"><span data-stu-id="0873d-323">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="0873d-324">**X**</span><span class="sxs-lookup"><span data-stu-id="0873d-324">**X**</span></span> | <span data-ttu-id="0873d-325">**Y**</span><span class="sxs-lookup"><span data-stu-id="0873d-325">**Y**</span></span>             | <span data-ttu-id="0873d-326">**Z**</span><span class="sxs-lookup"><span data-stu-id="0873d-326">**Z**</span></span> |
    | <span data-ttu-id="0873d-327">1</span><span class="sxs-lookup"><span data-stu-id="0873d-327">1</span></span>     | <span data-ttu-id="0873d-328">1</span><span class="sxs-lookup"><span data-stu-id="0873d-328">1</span></span>                 | <span data-ttu-id="0873d-329">1</span><span class="sxs-lookup"><span data-stu-id="0873d-329">1</span></span>     |

    ![conjunto de transformación de cámara](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a><span data-ttu-id="0873d-331">Capítulo 5: configuración de la escena de Unity</span><span class="sxs-lookup"><span data-stu-id="0873d-331">Chapter 5 - Setting up the Unity scene</span></span>

1.  <span data-ttu-id="0873d-332">Haga clic en un área vacía de la *jerarquía Panel*, en **objeto 3D**, agregue un **plano**.</span><span class="sxs-lookup"><span data-stu-id="0873d-332">Right-click in an empty area of the *Hierarchy Panel*, under **3D  Object**, add a **Plane**.</span></span>

    ![Crear nuevo plano](images/AzureLabs-Lab5-31.png)

2.  <span data-ttu-id="0873d-334">Con el **plano** objeto seleccionado, cambie los parámetros siguientes en el *Panel Inspector*:</span><span class="sxs-lookup"><span data-stu-id="0873d-334">With the **Plane** object selected, change the following parameters in the *Inspector Panel*:</span></span>

    |       | <span data-ttu-id="0873d-335">TRANSFORMACIÓN - POSICIÓN</span><span class="sxs-lookup"><span data-stu-id="0873d-335">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="0873d-336">**X**</span><span class="sxs-lookup"><span data-stu-id="0873d-336">**X**</span></span> | <span data-ttu-id="0873d-337">**Y**</span><span class="sxs-lookup"><span data-stu-id="0873d-337">**Y**</span></span>                | <span data-ttu-id="0873d-338">**Z**</span><span class="sxs-lookup"><span data-stu-id="0873d-338">**Z**</span></span> |
    | <span data-ttu-id="0873d-339">0</span><span class="sxs-lookup"><span data-stu-id="0873d-339">0</span></span>     | <span data-ttu-id="0873d-340">0</span><span class="sxs-lookup"><span data-stu-id="0873d-340">0</span></span>                    | <span data-ttu-id="0873d-341">4</span><span class="sxs-lookup"><span data-stu-id="0873d-341">4</span></span>     |

    |       | <span data-ttu-id="0873d-342">TRANSFORMACIÓN - ESCALADO</span><span class="sxs-lookup"><span data-stu-id="0873d-342">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="0873d-343">**X**</span><span class="sxs-lookup"><span data-stu-id="0873d-343">**X**</span></span> | <span data-ttu-id="0873d-344">**Y**</span><span class="sxs-lookup"><span data-stu-id="0873d-344">**Y**</span></span>             | <span data-ttu-id="0873d-345">**Z**</span><span class="sxs-lookup"><span data-stu-id="0873d-345">**Z**</span></span> |
    | <span data-ttu-id="0873d-346">10</span><span class="sxs-lookup"><span data-stu-id="0873d-346">10</span></span>    | <span data-ttu-id="0873d-347">1</span><span class="sxs-lookup"><span data-stu-id="0873d-347">1</span></span>                 | <span data-ttu-id="0873d-348">10</span><span class="sxs-lookup"><span data-stu-id="0873d-348">10</span></span>    |

    ![posición del conjunto plano y la escala](images/AzureLabs-Lab5-32.png)

    ![vista de la escena del plano](images/AzureLabs-Lab5-33.png)

3.  <span data-ttu-id="0873d-351">Haga clic en un área vacía de la *jerarquía Panel*, en **objeto 3D**, agregue un **cubo**.</span><span class="sxs-lookup"><span data-stu-id="0873d-351">Right-click in an empty area of the *Hierarchy Panel*, under **3D Object**, add a **Cube**.</span></span>

    1.  <span data-ttu-id="0873d-352">Cambiar el nombre del cubo a **GazeButton** (con el cubo seleccionado, pulse 'F2').</span><span class="sxs-lookup"><span data-stu-id="0873d-352">Rename the Cube to **GazeButton** (with the Cube selected, press 'F2').</span></span>

    2.  <span data-ttu-id="0873d-353">Cambiar los parámetros siguientes en el *Panel Inspector*:</span><span class="sxs-lookup"><span data-stu-id="0873d-353">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="0873d-354">TRANSFORMACIÓN - POSICIÓN</span><span class="sxs-lookup"><span data-stu-id="0873d-354">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:-----:|
        | <span data-ttu-id="0873d-355">**X**</span><span class="sxs-lookup"><span data-stu-id="0873d-355">**X**</span></span> | <span data-ttu-id="0873d-356">**Y**</span><span class="sxs-lookup"><span data-stu-id="0873d-356">**Y**</span></span>                | <span data-ttu-id="0873d-357">**Z**</span><span class="sxs-lookup"><span data-stu-id="0873d-357">**Z**</span></span> |
        | <span data-ttu-id="0873d-358">0</span><span class="sxs-lookup"><span data-stu-id="0873d-358">0</span></span>     | <span data-ttu-id="0873d-359">3</span><span class="sxs-lookup"><span data-stu-id="0873d-359">3</span></span>                    | <span data-ttu-id="0873d-360">5</span><span class="sxs-lookup"><span data-stu-id="0873d-360">5</span></span>     |


        ![conjunto mirada botón transformación](images/AzureLabs-Lab5-34.png)

        ![vista de escena de botón que mirar](images/AzureLabs-Lab5-35.png)

    3.  <span data-ttu-id="0873d-363">Haga clic en el **etiqueta** botón desplegable y haga clic en **Agregar etiqueta** para abrir el *etiquetas & panel Capas*.</span><span class="sxs-lookup"><span data-stu-id="0873d-363">Click on the **Tag** drop-down button and click on **Add Tag** to open the *Tags & Layers Pane*.</span></span>

        ![Agregar nueva etiqueta](images/AzureLabs-Lab5-36.png)

        ![Seleccione más](images/AzureLabs-Lab5-37.png)

    4.  <span data-ttu-id="0873d-366">Seleccione el **+ (signo más)** botón y en el *nuevo nombre de la etiqueta* , introduzca **GazeButton**y presione **guardar**.</span><span class="sxs-lookup"><span data-stu-id="0873d-366">Select the **+ (plus)** button, and in the *New Tag Name* field, enter **GazeButton**, and press **Save**.</span></span>

        ![nueva etiqueta de nombre](images/AzureLabs-Lab5-38.png)

    5.  <span data-ttu-id="0873d-368">Haga clic en el **GazeButton** objeto en el *jerarquía Panel*y en el *Panel Inspector*, asignar recién creado **GazeButton** etiqueta.</span><span class="sxs-lookup"><span data-stu-id="0873d-368">Click on the **GazeButton** object in the *Hierarchy Panel*, and in the *Inspector Panel*, assign the newly created **GazeButton** tag.</span></span>

        ![mirada botón asignar la nueva etiqueta](images/AzureLabs-Lab5-39.png)

4.  <span data-ttu-id="0873d-370">Haga doble clic en el **GazeButton** objeto, en el *jerarquía Panel*y agregue un **GameObject vacío** (que se agregará como un *secundarios* objeto).</span><span class="sxs-lookup"><span data-stu-id="0873d-370">Right-click on the **GazeButton** object, in the *Hierarchy Panel*, and add an **Empty GameObject** (which will be added as a *child* object).</span></span>

5.  <span data-ttu-id="0873d-371">Seleccione el nuevo objeto y cámbielo por **ShapeSpawnPoint**.</span><span class="sxs-lookup"><span data-stu-id="0873d-371">Select the new object and rename it **ShapeSpawnPoint**.</span></span>

    1.  <span data-ttu-id="0873d-372">Cambiar los parámetros siguientes en el *Panel Inspector*:</span><span class="sxs-lookup"><span data-stu-id="0873d-372">Change the following parameters in the *Inspector Panel*:</span></span>

        |       | <span data-ttu-id="0873d-373">TRANSFORMACIÓN - POSICIÓN</span><span class="sxs-lookup"><span data-stu-id="0873d-373">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:----: |
        | <span data-ttu-id="0873d-374">**X**</span><span class="sxs-lookup"><span data-stu-id="0873d-374">**X**</span></span> |<span data-ttu-id="0873d-375">**Y**</span><span class="sxs-lookup"><span data-stu-id="0873d-375">**Y**</span></span>                 | <span data-ttu-id="0873d-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="0873d-376">**Z**</span></span> |
        | <span data-ttu-id="0873d-377">0</span><span class="sxs-lookup"><span data-stu-id="0873d-377">0</span></span>     | <span data-ttu-id="0873d-378">-1</span><span class="sxs-lookup"><span data-stu-id="0873d-378">-1</span></span>                   | <span data-ttu-id="0873d-379">0</span><span class="sxs-lookup"><span data-stu-id="0873d-379">0</span></span>     |

        ![transformación de punto de actualización de forma spawn](images/AzureLabs-Lab5-40.png)

        ![vista de escena de forma spawn punto](images/AzureLabs-Lab5-41.png)

6.  <span data-ttu-id="0873d-382">A continuación creará un **texto 3D** objeto para proporcionar comentarios sobre el estado del servicio de Azure.</span><span class="sxs-lookup"><span data-stu-id="0873d-382">Next you will create a **3D Text** object to provide feedback on the status of the Azure service.</span></span>

    <span data-ttu-id="0873d-383">Haga clic con el botón derecho en el **GazeButton** en la jerarquía del nuevo Panel y agregar un **objeto 3D > texto 3D** objeto como un *secundarios*.</span><span class="sxs-lookup"><span data-stu-id="0873d-383">Right click on the **GazeButton** in the Hierarchy Panel again and add a **3D Object > 3D Text** object as a *child*.</span></span>

    ![Crear nuevo objeto de texto 3D](images/AzureLabs-Lab5-42.png)

7.  <span data-ttu-id="0873d-385">Cambiar el nombre de la **texto 3D** objeto **AzureStatusText**.</span><span class="sxs-lookup"><span data-stu-id="0873d-385">Rename the **3D Text** object to **AzureStatusText**.</span></span>

8.  <span data-ttu-id="0873d-386">Cambiar el **AzureStatusText** objeto transformación como sigue:</span><span class="sxs-lookup"><span data-stu-id="0873d-386">Change the **AzureStatusText** object Transform as follows:</span></span>

    |       | <span data-ttu-id="0873d-387">TRANSFORMACIÓN - POSICIÓN</span><span class="sxs-lookup"><span data-stu-id="0873d-387">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="0873d-388">**X**</span><span class="sxs-lookup"><span data-stu-id="0873d-388">**X**</span></span> | <span data-ttu-id="0873d-389">**Y**</span><span class="sxs-lookup"><span data-stu-id="0873d-389">**Y**</span></span>                | <span data-ttu-id="0873d-390">**Z**</span><span class="sxs-lookup"><span data-stu-id="0873d-390">**Z**</span></span> |
    | <span data-ttu-id="0873d-391">0</span><span class="sxs-lookup"><span data-stu-id="0873d-391">0</span></span>     | <span data-ttu-id="0873d-392">0</span><span class="sxs-lookup"><span data-stu-id="0873d-392">0</span></span>                    | <span data-ttu-id="0873d-393">-0.6</span><span class="sxs-lookup"><span data-stu-id="0873d-393">-0.6</span></span>  |

    |       | <span data-ttu-id="0873d-394">TRANSFORMACIÓN - ESCALADO</span><span class="sxs-lookup"><span data-stu-id="0873d-394">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="0873d-395">**X**</span><span class="sxs-lookup"><span data-stu-id="0873d-395">**X**</span></span> | <span data-ttu-id="0873d-396">**Y**</span><span class="sxs-lookup"><span data-stu-id="0873d-396">**Y**</span></span>             | <span data-ttu-id="0873d-397">**Z**</span><span class="sxs-lookup"><span data-stu-id="0873d-397">**Z**</span></span> |
    | <span data-ttu-id="0873d-398">0.1</span><span class="sxs-lookup"><span data-stu-id="0873d-398">0.1</span></span>   | <span data-ttu-id="0873d-399">0.1</span><span class="sxs-lookup"><span data-stu-id="0873d-399">0.1</span></span>               | <span data-ttu-id="0873d-400">0.1</span><span class="sxs-lookup"><span data-stu-id="0873d-400">0.1</span></span>   |


    > [!NOTE]
    > <span data-ttu-id="0873d-401">No se preocupe si parece estar fuera del centro, como esto se corregirá cuando el debajo del texto de la malla se actualiza el componente.</span><span class="sxs-lookup"><span data-stu-id="0873d-401">Do not worry if it appears to be off-centre, as this will be fixed when the below Text Mesh component is updated.</span></span>

9.  <span data-ttu-id="0873d-402">Cambiar el **texto de la malla** componente para que coincida con el a continuación:</span><span class="sxs-lookup"><span data-stu-id="0873d-402">Change the **Text Mesh** component to match the below:</span></span>

    ![componente de malla de conjunto de texto](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > <span data-ttu-id="0873d-404">Aquí, el color seleccionado es de color hexadecimal: **000000FF**, aunque no dude en Elija su propio, solo tiene que comprobar es legible.</span><span class="sxs-lookup"><span data-stu-id="0873d-404">The selected color here is Hex color: **000000FF**, though feel free to choose your own, just ensure it is readable.</span></span>

10. <span data-ttu-id="0873d-405">La estructura del Panel de la jerarquía debe ser ahora similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="0873d-405">Your Hierarchy Panel structure should now look like this:</span></span>

    ![texto de la malla en la vista de escena](images/AzureLabs-Lab5-43b.png)

10. <span data-ttu-id="0873d-407">La escena ahora un aspecto similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="0873d-407">Your scene should now look like this:</span></span>

    ![texto de la malla en la vista de escena](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a><span data-ttu-id="0873d-409">Capítulo 6: importar el almacenamiento de Azure para Unity</span><span class="sxs-lookup"><span data-stu-id="0873d-409">Chapter 6 - Import Azure Storage for Unity</span></span>

<span data-ttu-id="0873d-410">Va a usar Azure Storage para Unity (que a su vez aprovecha el .net SDK de Azure).</span><span class="sxs-lookup"><span data-stu-id="0873d-410">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="0873d-411">Puede leer más sobre esto en el [el almacenamiento de Azure para el artículo de Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="0873d-411">You can read more about this at the [Azure Storage for Unity article](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="0873d-412">Actualmente hay un problema conocido en Unity que requiere complementos volver a configurar tras la importación.</span><span class="sxs-lookup"><span data-stu-id="0873d-412">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="0873d-413">Estos pasos (4-7 en esta sección) ya no será necesarios una vez que se ha resuelto el error.</span><span class="sxs-lookup"><span data-stu-id="0873d-413">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="0873d-414">Para importar el SDK en su propio proyecto, asegúrese de que ha descargado la versión más reciente ['.unitypackage' desde GitHub](https://aka.ms/azstorage-unitysdk).</span><span class="sxs-lookup"><span data-stu-id="0873d-414">To import the SDK into your own project, make sure you have downloaded the latest ['.unitypackage' from GitHub](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="0873d-415">A continuación, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="0873d-415">Then, do the following:</span></span>

1.  <span data-ttu-id="0873d-416">Agregar el **.unitypackage** a Unity de un archivo utilizando el **activos > Importar paquete > paquete personalizado** opción de menú.</span><span class="sxs-lookup"><span data-stu-id="0873d-416">Add the **.unitypackage** file to Unity by using the **Assets > Import Package > Custom Package** menu option.</span></span>

2.  <span data-ttu-id="0873d-417">En el **Importar paquete de Unity** cuadro que aparece, puede seleccionar todo el contenido \**complemento* > \* Storage \*\*.</span><span class="sxs-lookup"><span data-stu-id="0873d-417">In the **Import Unity Package** box that pops up, you can select everything under \**Plugin* > \*Storage\*\*.</span></span> <span data-ttu-id="0873d-418">Desactive todo lo demás, ya no es necesaria para este curso.</span><span class="sxs-lookup"><span data-stu-id="0873d-418">Uncheck everything else, as it is not needed for this course.</span></span>

    ![Importar paquete](images/AzureLabs-Lab5-45.png)

3.  <span data-ttu-id="0873d-420">Haga clic en el **importación** para agregar los elementos al proyecto.</span><span class="sxs-lookup"><span data-stu-id="0873d-420">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="0873d-421">Vaya a la *almacenamiento* carpeta bajo *complementos*, en la vista del proyecto y seleccione los siguientes complementos *sólo*:</span><span class="sxs-lookup"><span data-stu-id="0873d-421">Go to the *Storage* folder under *Plugins*, in the Project view, and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="0873d-422">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="0873d-422">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="0873d-423">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="0873d-423">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="0873d-424">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="0873d-424">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="0873d-425">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="0873d-425">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="0873d-426">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="0873d-426">System.Spatial</span></span>

        ![Desactive cualquier plataforma](images/AzureLabs-Lab5-46.png)

5.  <span data-ttu-id="0873d-428">Con *estos complementos específicos* seleccionado, **desactive** *cualquier plataforma* y **desactive** *WSAPlayer* a continuación, haga clic en **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="0873d-428">With *these specific plugins* selected, **uncheck** *Any Platform* and **uncheck** *WSAPlayer* then click **Apply**.</span></span>

    ![se aplican a archivos DLL de plataforma](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > <span data-ttu-id="0873d-430">Vamos a marcar estos complementos determinados para su uso en el Editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="0873d-430">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="0873d-431">Esto es porque hay diferentes versiones de los complementos mismos en la carpeta WSA que se utilizará después de que el proyecto se exporta desde Unity.</span><span class="sxs-lookup"><span data-stu-id="0873d-431">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="0873d-432">En el *almacenamiento* carpeta de complemento, solo seleccione:</span><span class="sxs-lookup"><span data-stu-id="0873d-432">In the *Storage* plugin folder, select only:</span></span>

    -   <span data-ttu-id="0873d-433">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="0873d-433">Microsoft.Data.Services.Client</span></span>

        ![No procesar conjunto para archivos DLL](images/AzureLabs-Lab5-48.png)

7.  <span data-ttu-id="0873d-435">Compruebe el **proceso no** cuadro bajo *configuración de plataforma* y haga clic en **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="0873d-435">Check the **Don't Process** box under *Platform Settings* and click **Apply**.</span></span>

    ![no aplicar ningún procesamiento](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > <span data-ttu-id="0873d-437">Vamos a marcar este complemento "No procesar" porque la revisión del ensamblado de Unity tiene dificultades para procesar este complemento.</span><span class="sxs-lookup"><span data-stu-id="0873d-437">We are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="0873d-438">El complemento seguirá funcionando aunque no se ha procesado.</span><span class="sxs-lookup"><span data-stu-id="0873d-438">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-7---create-the-azureservices-class"></a><span data-ttu-id="0873d-439">Capítulo 7: crear la clase AzureServices</span><span class="sxs-lookup"><span data-stu-id="0873d-439">Chapter 7 - Create the AzureServices class</span></span>

<span data-ttu-id="0873d-440">Es la primera clase que se va a crear el *AzureServices* clase.</span><span class="sxs-lookup"><span data-stu-id="0873d-440">The first class you are going to create is the *AzureServices* class.</span></span>

<span data-ttu-id="0873d-441">El *AzureServices* clase será responsable de:</span><span class="sxs-lookup"><span data-stu-id="0873d-441">The *AzureServices* class will be responsible for:</span></span>

-   <span data-ttu-id="0873d-442">Almacenar las credenciales de cuenta de Azure.</span><span class="sxs-lookup"><span data-stu-id="0873d-442">Storing Azure Account credentials.</span></span>

-   <span data-ttu-id="0873d-443">Una llamada a la función de la aplicación de Azure.</span><span class="sxs-lookup"><span data-stu-id="0873d-443">Calling your Azure App Function.</span></span>

-   <span data-ttu-id="0873d-444">La carga y descarga del archivo de datos en la nube de Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="0873d-444">The upload and download of the data file in your Azure Cloud Storage.</span></span>

<span data-ttu-id="0873d-445">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="0873d-445">To create this Class:</span></span>

1.  <span data-ttu-id="0873d-446">Haga clic en el *activos* carpeta, que se encuentra en el Panel de proyecto **crear > carpeta**.</span><span class="sxs-lookup"><span data-stu-id="0873d-446">Right-click in the *Asset* Folder, located in the Project Panel, **Create > Folder**.</span></span> <span data-ttu-id="0873d-447">Nombre de la carpeta **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="0873d-447">Name the folder **Scripts**.</span></span>

    ![Crear nueva carpeta](images/AzureLabs-Lab5-50.png)

    ![Llame a la carpeta - secuencias de comandos](images/AzureLabs-Lab5-51.png)

2.  <span data-ttu-id="0873d-450">Haga doble clic en la carpeta que acaba de crear para abrirlo.</span><span class="sxs-lookup"><span data-stu-id="0873d-450">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="0873d-451">Haga clic en la carpeta, **crear > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="0873d-451">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="0873d-452">Llame al script *AzureServices*.</span><span class="sxs-lookup"><span data-stu-id="0873d-452">Call the script *AzureServices*.</span></span>

4.  <span data-ttu-id="0873d-453">Haga doble clic en el nuevo *AzureServices* clase para abrirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="0873d-453">Double click on the new *AzureServices* class to open it with *Visual Studio*.</span></span>

5.  <span data-ttu-id="0873d-454">Agregue los siguientes espacios de nombres al principio de la *AzureServices*:</span><span class="sxs-lookup"><span data-stu-id="0873d-454">Add the following namespaces to the top of the *AzureServices*:</span></span>

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  <span data-ttu-id="0873d-455">Agregue los siguientes campos de Inspector dentro de la *AzureServices* clase:</span><span class="sxs-lookup"><span data-stu-id="0873d-455">Add the following Inspector Fields inside the *AzureServices* class:</span></span>

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

7.  <span data-ttu-id="0873d-456">A continuación, agregue las siguientes variables de miembro dentro de la *AzureServices* clase:</span><span class="sxs-lookup"><span data-stu-id="0873d-456">Then add the following member variables inside the *AzureServices* class:</span></span>

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
    > <span data-ttu-id="0873d-457">Asegúrese de reemplazar el *extremo* y *cadena de conexión* valores con los valores de almacenamiento de Azure, se encuentran en el Portal de Azure</span><span class="sxs-lookup"><span data-stu-id="0873d-457">Make sure you replace the *endpoint* and *connection string* values with the values from your Azure storage, found in the Azure Portal</span></span>

8.  <span data-ttu-id="0873d-458">El código para *Awake()* y *Start()* métodos ahora debe agregarse.</span><span class="sxs-lookup"><span data-stu-id="0873d-458">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="0873d-459">Estos métodos se llamará cuando se inicializa la clase:</span><span class="sxs-lookup"><span data-stu-id="0873d-459">These methods will be called when the class initializes:</span></span>

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
    > <span data-ttu-id="0873d-460">Se rellenará en el código de *CallAzureFunctionForNextShape()* en un [capítulo futuras](#chapter-10---completing-the-AzureServices-class).</span><span class="sxs-lookup"><span data-stu-id="0873d-460">We will fill in the code for *CallAzureFunctionForNextShape()* in a [future Chapter](#chapter-10---completing-the-AzureServices-class).</span></span>

9.  <span data-ttu-id="0873d-461">Eliminar el *Update()* método puesto que esta clase no lo usará.</span><span class="sxs-lookup"><span data-stu-id="0873d-461">Delete the *Update()* method since this class will not use it.</span></span>

10. <span data-ttu-id="0873d-462">Guarde los cambios en Visual Studio y, a continuación, volver a Unity.</span><span class="sxs-lookup"><span data-stu-id="0873d-462">Save your changes in Visual Studio, and then return to Unity.</span></span>

11. <span data-ttu-id="0873d-463">Haga clic y arrastre el *AzureServices* clase a partir de la carpeta Scripts en el objeto de cámara principal en el *jerarquía Panel*.</span><span class="sxs-lookup"><span data-stu-id="0873d-463">Click and drag the *AzureServices* class from the Scripts folder to the Main Camera object in the *Hierarchy Panel*.</span></span>

12. <span data-ttu-id="0873d-464">Seleccione la cámara principal, a continuación, tomar el **AzureStatusText** objeto secundario debajo de la **GazeButton** objeto y colóquelo dentro de la **AzureStatusText** un destino de referencia campo en el *Inspector*, para proporcionar la referencia a la *AzureServices* secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="0873d-464">Select the Main Camera, then grab the **AzureStatusText** child object from beneath the **GazeButton** object, and place it within the **AzureStatusText** reference target field, in the *Inspector*, to provide the reference to the *AzureServices* script.</span></span>

    ![Asigne el destino de referencia de texto de estado de azure](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a><span data-ttu-id="0873d-466">Capítulo 8: crear la clase ShapeFactory</span><span class="sxs-lookup"><span data-stu-id="0873d-466">Chapter 8 - Create the ShapeFactory class</span></span>

<span data-ttu-id="0873d-467">El script siguiente para crear, es el *ShapeFactory* clase.</span><span class="sxs-lookup"><span data-stu-id="0873d-467">The next script to create, is the *ShapeFactory* class.</span></span> <span data-ttu-id="0873d-468">El rol de esta clase es crear una nueva forma, cuando se solicita y mantener un historial de las formas que creó en un *lista del historial de forma*.</span><span class="sxs-lookup"><span data-stu-id="0873d-468">The role of this class is to create a new shape, when requested, and keep a history of the shapes created in a *Shape History List*.</span></span> <span data-ttu-id="0873d-469">Cada vez que se crea una forma, el *lista del historial de forma* se actualiza en el *AzureService* clase y, a continuación, se almacenan en su *Azure Storage*.</span><span class="sxs-lookup"><span data-stu-id="0873d-469">Every time a shape is created, the *Shape History list* is updated in the *AzureService* class, and then stored in your *Azure Storage*.</span></span> <span data-ttu-id="0873d-470">Cuando se inicia la aplicación, si se encuentra un archivo almacenado en su *Azure Storage*, *lista del historial de forma* se recupera y reproduce, con el **texto 3D** que proporciona el objeto Si la forma generada es de almacenamiento o nuevo.</span><span class="sxs-lookup"><span data-stu-id="0873d-470">When the application starts, if a stored file is found in your *Azure Storage*, the *Shape History list* is retrieved and replayed, with the **3D Text** object providing whether the generated shape is from storage, or new.</span></span>

<span data-ttu-id="0873d-471">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="0873d-471">To create this class:</span></span>

1.  <span data-ttu-id="0873d-472">Vaya a la **Scripts** carpeta que creó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0873d-472">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="0873d-473">Haga clic en la carpeta, **crear > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="0873d-473">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="0873d-474">Llame al script *ShapeFactory*.</span><span class="sxs-lookup"><span data-stu-id="0873d-474">Call the script *ShapeFactory*.</span></span>

3.  <span data-ttu-id="0873d-475">Haga doble clic en el nuevo *ShapeFactory* script para abrirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="0873d-475">Double click on the new *ShapeFactory* script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="0873d-476">Asegúrese del *ShapeFactory* clase incluye los espacios de nombres siguientes:</span><span class="sxs-lookup"><span data-stu-id="0873d-476">Ensure the *ShapeFactory* class includes the following namespaces:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  <span data-ttu-id="0873d-477">Agregue las variables que se muestra a continuación para el *ShapeFactory* clase y reemplazar el *Start()* y *Awake()* funciones con los siguientes:</span><span class="sxs-lookup"><span data-stu-id="0873d-477">Add the variables shown below to the *ShapeFactory* class, and replace the *Start()* and *Awake()* functions with those below:</span></span>

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

6.  <span data-ttu-id="0873d-478">El *CreateShape()* método genera las formas de primitivas, según el proporcionado *entero* parámetro.</span><span class="sxs-lookup"><span data-stu-id="0873d-478">The *CreateShape()* method generates the primitive shapes, based upon the provided *integer* parameter.</span></span> <span data-ttu-id="0873d-479">El parámetro booleano se utiliza para especificar si es la forma actualmente creada desde el almacenamiento nuevo.</span><span class="sxs-lookup"><span data-stu-id="0873d-479">The Boolean parameter is used to specify whether the currently created shape is from storage, or new.</span></span> <span data-ttu-id="0873d-480">Coloque el código siguiente en su *ShapeFactory* (clase), a continuación de los métodos anteriores:</span><span class="sxs-lookup"><span data-stu-id="0873d-480">Place the following code in your *ShapeFactory* class, below the previous methods:</span></span>

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

7.  <span data-ttu-id="0873d-481">Asegúrese de guardar los cambios en Visual Studio antes de volver a Unity.</span><span class="sxs-lookup"><span data-stu-id="0873d-481">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

8.  <span data-ttu-id="0873d-482">Atrás en el Editor de Unity, haga clic y arrastre el *ShapeFactory* clase desde el **Scripts** carpeta a la **cámara principal** objeto en el *jerarquía Panel*.</span><span class="sxs-lookup"><span data-stu-id="0873d-482">Back in the Unity Editor, click and drag the *ShapeFactory* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

9. <span data-ttu-id="0873d-483">Con la cámara principal seleccionado, observará el *ShapeFactory* falta un componente de script el *punto Spawn* referencia.</span><span class="sxs-lookup"><span data-stu-id="0873d-483">With the Main Camera selected you will notice the *ShapeFactory* script component is missing the *Spawn Point* reference.</span></span> <span data-ttu-id="0873d-484">Para corregirlo, arrastre el **ShapeSpawnPoint** objeto desde el *jerarquía Panel* a la **Spawn punto** un destino de referencia.</span><span class="sxs-lookup"><span data-stu-id="0873d-484">To fix it, drag the **ShapeSpawnPoint** object from the *Hierarchy Panel* to the **Spawn Point** reference target.</span></span>

    ![destino de la referencia de conjunto de forma factory](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a><span data-ttu-id="0873d-486">Capítulo 9: crear la clase de mirada</span><span class="sxs-lookup"><span data-stu-id="0873d-486">Chapter 9 - Create the Gaze class</span></span>

<span data-ttu-id="0873d-487">Es el último script, deberá crear el *que mirar* clase.</span><span class="sxs-lookup"><span data-stu-id="0873d-487">The last script you need to create is the *Gaze* class.</span></span>

<span data-ttu-id="0873d-488">Esta clase es responsable de crear un **Raycast** que se proyectará hacia delante de la cámara principal, para detectar el objeto que está mirando el usuario.</span><span class="sxs-lookup"><span data-stu-id="0873d-488">This class is responsible for creating a **Raycast** that will be projected forward from the Main Camera, to detect which object the user is looking at.</span></span> <span data-ttu-id="0873d-489">En este caso, necesitará el Raycast identificar si el usuario está viendo la **GazeButton** de objetos de la escena y desencadenar un comportamiento.</span><span class="sxs-lookup"><span data-stu-id="0873d-489">In this case, the Raycast will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="0873d-490">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="0873d-490">To create this Class:</span></span>

1.  <span data-ttu-id="0873d-491">Vaya a la **Scripts** carpeta que creó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0873d-491">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="0873d-492">Haga clic en el Panel proyecto, **crear > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="0873d-492">Right-click in the Project Panel, **Create > C# Script**.</span></span> <span data-ttu-id="0873d-493">Llame al script *que mirar*.</span><span class="sxs-lookup"><span data-stu-id="0873d-493">Call the script *Gaze*.</span></span>

3.  <span data-ttu-id="0873d-494">Haga doble clic en el nuevo *que mirar* script para abrirlo con *Visual Studio.*</span><span class="sxs-lookup"><span data-stu-id="0873d-494">Double click on the new *Gaze* script to open it with *Visual Studio.*</span></span>

4.  <span data-ttu-id="0873d-495">Asegúrese de que el espacio de nombres siguiente se incluye en la parte superior de la secuencia de comandos:</span><span class="sxs-lookup"><span data-stu-id="0873d-495">Ensure the following namespace is included at the top of the script:</span></span>

    ```csharp
        using UnityEngine;
    ```

5.  <span data-ttu-id="0873d-496">A continuación, agregue las siguientes variables dentro de la *que mirar* clase:</span><span class="sxs-lookup"><span data-stu-id="0873d-496">Then add the following variables inside the *Gaze* class:</span></span>

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
> <span data-ttu-id="0873d-497">Algunas de estas variables podrán modificarse en el *Editor*.</span><span class="sxs-lookup"><span data-stu-id="0873d-497">Some of these variables will be able to be edited in the *Editor*.</span></span>

6.  <span data-ttu-id="0873d-498">El código para el *Awake()* y *Start()* métodos ahora debe agregarse.</span><span class="sxs-lookup"><span data-stu-id="0873d-498">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span>

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

7.  <span data-ttu-id="0873d-499">Agregue el código siguiente, que se creará un objeto de cursor al iniciarse, junto con el *Update()* método, que se ejecutará el método Raycast, junto con que se va a donde se alterna el valor booleano GazeEnabled:</span><span class="sxs-lookup"><span data-stu-id="0873d-499">Add the following code, which will create a cursor object at start, along with the *Update()* method, which will run the Raycast method, along with being where the GazeEnabled boolean is toggled:</span></span>

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

8. <span data-ttu-id="0873d-500">A continuación agregue el *UpdateRaycast()* método, lo que un Raycast del proyecto y detectar el posicionamiento de destino.</span><span class="sxs-lookup"><span data-stu-id="0873d-500">Next add the *UpdateRaycast()* method, which will project a Raycast and detect the hit target.</span></span>

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

9. <span data-ttu-id="0873d-501">Por último, agregue el *ResetFocusedObject()* método, que cambiará el GazeButton objetos color actual, que indica si se está creando una nueva forma o no.</span><span class="sxs-lookup"><span data-stu-id="0873d-501">Lastly, add the *ResetFocusedObject()* method, which will toggle the GazeButton objects current color, indicating whether it is creating a new shape or not.</span></span>

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

10.  <span data-ttu-id="0873d-502">Guarde los cambios en Visual Studio antes de volver a Unity.</span><span class="sxs-lookup"><span data-stu-id="0873d-502">Save your changes in Visual Studio before returning to Unity.</span></span>

11.  <span data-ttu-id="0873d-503">Haga clic y arrastre el *que mirar* clase a partir de la carpeta Scripts para la **cámara principal** objeto en el *jerarquía Panel*.</span><span class="sxs-lookup"><span data-stu-id="0873d-503">Click and drag the *Gaze* class from the Scripts folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>

## <a name="chapter-10---completing-the-azureservices-class"></a><span data-ttu-id="0873d-504">Capítulo 10: finalización de la clase AzureServices</span><span class="sxs-lookup"><span data-stu-id="0873d-504">Chapter 10 - Completing the AzureServices class</span></span>

<span data-ttu-id="0873d-505">Con los demás scripts en su lugar, es posible *completa* el *AzureServices* clase.</span><span class="sxs-lookup"><span data-stu-id="0873d-505">With the other scripts in place, it is now possible to *complete* the *AzureServices* class.</span></span> <span data-ttu-id="0873d-506">Esto se conseguirá mediante:</span><span class="sxs-lookup"><span data-stu-id="0873d-506">This will be achieved through:</span></span>

1.  <span data-ttu-id="0873d-507">Agregar un nuevo método denominado *CreateCloudIdentityAsync()*, para establecer las variables de autenticación necesarias para la comunicación con Azure.</span><span class="sxs-lookup"><span data-stu-id="0873d-507">Adding a new method named *CreateCloudIdentityAsync()*, to set up the authentication variables needed for communicating with Azure.</span></span>

    > <span data-ttu-id="0873d-508">Este método también comprobará la existencia de un archivo almacenado anteriormente que contiene la lista de la forma.</span><span class="sxs-lookup"><span data-stu-id="0873d-508">This method will also check for the existence of a previously stored File containing the Shape List.</span></span>
    >
    > <span data-ttu-id="0873d-509">**Si se encuentra el archivo**, deshabilitará el usuario *que mirar*y desencadenar la creación de formas, según el patrón de formas, tal como está almacenado en el **archivos de Azure Storage**.</span><span class="sxs-lookup"><span data-stu-id="0873d-509">**If the file is found**, it will disable the user *Gaze*, and trigger Shape creation, according to the pattern of shapes, as stored in the **Azure Storage file**.</span></span> <span data-ttu-id="0873d-510">El usuario puede ver esto, como el **texto de la malla** proporcionará mostrar 'Storage' o 'New', dependiendo del origen de las formas.</span><span class="sxs-lookup"><span data-stu-id="0873d-510">The user can see this, as the **Text Mesh** will provide display 'Storage' or 'New', depending on the shapes origin.</span></span>
    >
    > <span data-ttu-id="0873d-511">**Si se encuentra ningún archivo**, se habilitará la *que mirar*, permitir que el usuario crear formas al observar la **GazeButton** objeto en la escena.</span><span class="sxs-lookup"><span data-stu-id="0873d-511">**If no file is found**, it will enable the *Gaze*, enabling the user to create shapes when looking at the **GazeButton** object in the scene.</span></span>

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

2.  <span data-ttu-id="0873d-512">Es el siguiente fragmento de código desde el *Start()* método; en la que se realizará una llamada a la *CreateCloudIdentityAsync()* método.</span><span class="sxs-lookup"><span data-stu-id="0873d-512">The next code snippet is from within the *Start()* method; wherein a call will be made to the *CreateCloudIdentityAsync()* method.</span></span> <span data-ttu-id="0873d-513">No dude en Copiar a través de su actual *Start()* método, con la siguiente:</span><span class="sxs-lookup"><span data-stu-id="0873d-513">Feel free to copy over your current *Start()* method, with the below:</span></span>

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

3.  <span data-ttu-id="0873d-514">Rellene el código para el método *CallAzureFunctionForNextShape()*.</span><span class="sxs-lookup"><span data-stu-id="0873d-514">Fill in the code for the method *CallAzureFunctionForNextShape()*.</span></span> <span data-ttu-id="0873d-515">Va a usar creado previamente *Azure Function App* para solicitar un índice de la forma.</span><span class="sxs-lookup"><span data-stu-id="0873d-515">You will use the previously created *Azure Function App* to request a shape index.</span></span> <span data-ttu-id="0873d-516">Una vez que se recibe la nueva forma, este método enviará la forma para el *ShapeFactory* clase para crear la nueva forma de la escena.</span><span class="sxs-lookup"><span data-stu-id="0873d-516">Once the new shape is received, this method will send the shape to the *ShapeFactory* class to create the new shape in the scene.</span></span> <span data-ttu-id="0873d-517">Utilice el código siguiente para completar el cuerpo de *CallAzureFunctionForNextShape()*.</span><span class="sxs-lookup"><span data-stu-id="0873d-517">Use the code below to complete the body of *CallAzureFunctionForNextShape()*.</span></span>

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

4.  <span data-ttu-id="0873d-518">Agregue un método para crear una cadena, mediante la concatenación de los enteros almacenados en la lista de historial de la forma y guardarlos en su *archivos de almacenamiento de Azure*.</span><span class="sxs-lookup"><span data-stu-id="0873d-518">Add a method to create a string, by concatenating the integers stored in the shape history list, and saving it in your *Azure Storage File*.</span></span>

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

5.  <span data-ttu-id="0873d-519">Agregue un método para recuperar el texto almacenado en el archivo se encuentra en su *archivos de almacenamiento de Azure* y *deserializar* en una lista.</span><span class="sxs-lookup"><span data-stu-id="0873d-519">Add a method to retrieve the text stored in the file located in your *Azure Storage File* and *deserialize* it into a list.</span></span>

6.  <span data-ttu-id="0873d-520">Una vez completado este proceso, el método vuelve a habilita a la mirada para que el usuario puede agregar más formas a la escena.</span><span class="sxs-lookup"><span data-stu-id="0873d-520">Once this process is completed, the method re-enables the gaze so that the user can add more shapes to the scene.</span></span>

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

7.  <span data-ttu-id="0873d-521">Guarde los cambios en Visual Studio antes de volver a Unity.</span><span class="sxs-lookup"><span data-stu-id="0873d-521">Save your changes in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-11---build-the-uwp-solution"></a><span data-ttu-id="0873d-522">Capítulo 11: Compile la solución UWP</span><span class="sxs-lookup"><span data-stu-id="0873d-522">Chapter 11 - Build the UWP Solution</span></span>

<span data-ttu-id="0873d-523">Para comenzar el proceso de compilación:</span><span class="sxs-lookup"><span data-stu-id="0873d-523">To begin the Build process:</span></span>

1.  <span data-ttu-id="0873d-524">Vaya a **archivo > configuración de compilación**.</span><span class="sxs-lookup"><span data-stu-id="0873d-524">Go to **File > Build Settings**.</span></span>

    ![Compilar la aplicación](images/AzureLabs-Lab5-54.png)

2.  <span data-ttu-id="0873d-526">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="0873d-526">Click **Build**.</span></span> <span data-ttu-id="0873d-527">Unity se iniciará un *Explorador de archivos* ventana, donde se debe crear y, a continuación, seleccione una carpeta para compilar la aplicación en.</span><span class="sxs-lookup"><span data-stu-id="0873d-527">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="0873d-528">Crear la carpeta y asígnele el nombre *aplicación*.</span><span class="sxs-lookup"><span data-stu-id="0873d-528">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="0873d-529">A continuación, con el *aplicación* carpeta seleccionada, presione **seleccionar la carpeta**.</span><span class="sxs-lookup"><span data-stu-id="0873d-529">Then with the *App* folder selected, press **Select Folder**.</span></span>

3.  <span data-ttu-id="0873d-530">Unity empezará a compilar el proyecto para el *aplicación* carpeta.</span><span class="sxs-lookup"><span data-stu-id="0873d-530">Unity will begin building your project to the *App* folder.</span></span>

4.  <span data-ttu-id="0873d-531">Una vez Unity ha finalizado la compilación (puede tardar algún tiempo), se abrirá un *Explorador de archivos* ventana en la ubicación de la compilación (comprobación de la barra de tareas, tal y como es posible que no siempre aparecen por encima de las ventanas, pero le informará de la adición de un nuevo ventana).</span><span class="sxs-lookup"><span data-stu-id="0873d-531">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploying-your-application"></a><span data-ttu-id="0873d-532">Capítulo 12 - implementación de la aplicación</span><span class="sxs-lookup"><span data-stu-id="0873d-532">Chapter 12 - Deploying your application</span></span>

<span data-ttu-id="0873d-533">Para implementar la aplicación:</span><span class="sxs-lookup"><span data-stu-id="0873d-533">To deploy your application:</span></span>

1.  <span data-ttu-id="0873d-534">Navegue hasta la *aplicación* carpeta que creó en el [último capítulo](#chapter-11---build-the-uwp-solution).</span><span class="sxs-lookup"><span data-stu-id="0873d-534">Navigate to the *App* folder which was created in the [last Chapter](#chapter-11---build-the-uwp-solution).</span></span> <span data-ttu-id="0873d-535">Verá un archivo con el nombre de las aplicaciones, con la extensión '.sln', que debería haga doble clic en, por lo que para abrirlo en *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="0873d-535">You will see a file with your apps name, with the '.sln' extension, which you should double-click, so to open it within *Visual Studio*.</span></span>

2.  <span data-ttu-id="0873d-536">En el **plataforma de solución**, seleccione **x86, equipo Local**.</span><span class="sxs-lookup"><span data-stu-id="0873d-536">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="0873d-537">En el **configuración de la solución** seleccione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="0873d-537">In the **Solution Configuration** select **Debug**.</span></span>

    > <span data-ttu-id="0873d-538">Para el Microsoft HoloLens, quizá le resulte más fácil establecer esto en *máquina remota*, de modo que no están atados a su equipo.</span><span class="sxs-lookup"><span data-stu-id="0873d-538">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="0873d-539">Sin embargo, necesitará también hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="0873d-539">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="0873d-540">Conocer el **dirección IP** de su HoloLens, que se encuentra dentro de la *configuración > red e Internet > Wi-Fi > Opciones avanzadas*; IPv4 es la dirección que debe usar.</span><span class="sxs-lookup"><span data-stu-id="0873d-540">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="0873d-541">Asegúrese de **modo de programador** es **en**; se encuentra en *configuración > actualización y seguridad > para los desarrolladores*.</span><span class="sxs-lookup"><span data-stu-id="0873d-541">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Implementar solución](images/AzureLabs-Lab5-55.png)

4.  <span data-ttu-id="0873d-543">Vaya a la **compilar** menú y haga clic en **implementar solución** para transferir localmente la aplicación en el equipo.</span><span class="sxs-lookup"><span data-stu-id="0873d-543">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="0873d-544">La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas, listas para iniciar y probado.</span><span class="sxs-lookup"><span data-stu-id="0873d-544">Your App should now appear in the list of installed apps, ready to be launched and tested!</span></span>

## <a name="your-finished-azure-functions-and-storage-application"></a><span data-ttu-id="0873d-545">El Azure Functions y la aplicación de almacenamiento finalizado</span><span class="sxs-lookup"><span data-stu-id="0873d-545">Your finished Azure Functions and Storage Application</span></span>

<span data-ttu-id="0873d-546">Enhorabuena, compila una aplicación de realidad mixta que aprovecha los servicios de la funciones de Azure y el almacenamiento de Azure.</span><span class="sxs-lookup"><span data-stu-id="0873d-546">Congratulations, you built a mixed reality app that leverages both the Azure Functions and Azure Storage services.</span></span> <span data-ttu-id="0873d-547">La aplicación podrá dibujar en los datos almacenados y proporcionar una acción basada en esos datos.</span><span class="sxs-lookup"><span data-stu-id="0873d-547">Your app will be able to draw on stored data, and provide an action based on that data.</span></span>

![final producto-end](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="0873d-549">Ejercicios de bonificación</span><span class="sxs-lookup"><span data-stu-id="0873d-549">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="0873d-550">Ejercicio 1</span><span class="sxs-lookup"><span data-stu-id="0873d-550">Exercise 1</span></span>

<span data-ttu-id="0873d-551">Cree una segunda spawn punto y registro que se creó un objeto desde el punto de generar.</span><span class="sxs-lookup"><span data-stu-id="0873d-551">Create a second spawn point and record which spawn point an object was created from.</span></span> <span data-ttu-id="0873d-552">Al cargar el archivo de datos, reproducir las formas que se generan a partir de la ubicación que se crearon originalmente.</span><span class="sxs-lookup"><span data-stu-id="0873d-552">When you load the data file, replay the shapes being spawned from the location they originally were created.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="0873d-553">Ejercicio 2</span><span class="sxs-lookup"><span data-stu-id="0873d-553">Exercise 2</span></span>

<span data-ttu-id="0873d-554">Crear un método para reiniciar la aplicación, en lugar de tener que volver a abrirlo cada vez.</span><span class="sxs-lookup"><span data-stu-id="0873d-554">Create a way to restart the app, rather than having to re-open it each time.</span></span> <span data-ttu-id="0873d-555">**Cargar escenas** es un buen lugar para comenzar.</span><span class="sxs-lookup"><span data-stu-id="0873d-555">**Loading Scenes** is a good spot to start.</span></span> <span data-ttu-id="0873d-556">Después de hacer eso, cree una forma de borrar la lista almacenada en *Azure Storage*, de modo que pueden restablecerse fácilmente desde su aplicación.</span><span class="sxs-lookup"><span data-stu-id="0873d-556">After doing that, create a way to clear the stored list in *Azure Storage*, so that it can be easily reset from your app.</span></span> 
