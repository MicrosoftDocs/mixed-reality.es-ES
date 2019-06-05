---
title: El Sr. y Azure 307 - Machine learning
description: Realice este curso para obtener información sobre cómo implementar Azure Machine Learning Studio dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidad mixta, Azure, academy, unity, tutorial, api, aprendizaje automático, ml studio de machine learning, envolventes, hololens, vr
ms.openlocfilehash: 93263817df0fd809a09b32c1b34a636eab7026a1
ms.sourcegitcommit: 9b6949d7cd2e67e6bde9b32aebeaeea325baa6c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2019
ms.locfileid: "66516038"
---
>[!NOTE]
><span data-ttu-id="693ad-104">Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.</span><span class="sxs-lookup"><span data-stu-id="693ad-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="693ad-105">Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="693ad-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="693ad-106">Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.</span><span class="sxs-lookup"><span data-stu-id="693ad-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="693ad-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="693ad-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="693ad-108">Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="693ad-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="693ad-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.</span><span class="sxs-lookup"><span data-stu-id="693ad-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-307-machine-learning"></a><span data-ttu-id="693ad-110">El Sr. y Azure 307: Aprendizaje automático</span><span class="sxs-lookup"><span data-stu-id="693ad-110">MR and Azure 307: Machine learning</span></span>

![final producto-inicio](images/AzureLabs-Lab7-0.png)

<span data-ttu-id="693ad-112">En este curso, obtendrá información sobre cómo agregar funcionalidades de Machine Learning (ML) a una aplicación de realidad mixta mediante Azure Machine Learning Studio.</span><span class="sxs-lookup"><span data-stu-id="693ad-112">In this course, you will learn how to add Machine Learning (ML) capabilities to a mixed reality application using Azure Machine Learning Studio.</span></span>

<span data-ttu-id="693ad-113">*Azure Machine Learning Studio* es un servicio de Microsoft, que proporciona a los desarrolladores con un gran número de algoritmos de aprendizaje automático, lo que puede ayudar con la visualización, preparación, salida y entrada de datos.</span><span class="sxs-lookup"><span data-stu-id="693ad-113">*Azure Machine Learning Studio* is a Microsoft service, which provides developers with a large number of machine learning algorithms, which can help with data input, output, preparation, and visualization.</span></span> <span data-ttu-id="693ad-114">Desde estos componentes, a continuación, es posible desarrollar un experimento de análisis predictivo, realizar iteraciones sobre él y usarlo para entrenar el modelo.</span><span class="sxs-lookup"><span data-stu-id="693ad-114">From these components, it is then possible to develop a predictive analytics experiment, iterate on it, and use it to train your model.</span></span> <span data-ttu-id="693ad-115">Siguiendo el entrenamiento, puede hacer que su modelo de operativa dentro de la nube de Azure, por lo que, a continuación, pueden puntuar nuevos datos.</span><span class="sxs-lookup"><span data-stu-id="693ad-115">Following training, you can make your model operational within the Azure cloud, so that it can then score new data.</span></span> <span data-ttu-id="693ad-116">Para obtener más información, visite la [página de Azure Machine Learning Studio](https://azure.microsoft.com/en-au/services/machine-learning-studio/).</span><span class="sxs-lookup"><span data-stu-id="693ad-116">For more information, visit the [Azure Machine Learning Studio page](https://azure.microsoft.com/en-au/services/machine-learning-studio/).</span></span>

<span data-ttu-id="693ad-117">Una vez completado este curso, tendrá una aplicación envolventes auriculares de realidad mixta y habrá aprendido cómo hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="693ad-117">Having completed this course, you will have a mixed reality immersive headset application, and will have learned how do the following:</span></span>

1.  <span data-ttu-id="693ad-118">Proporcionar una tabla de datos de ventas para el *Azure Machine Learning Studio* portal y diseño de un algoritmo para predecir las ventas futuras de productos populares.</span><span class="sxs-lookup"><span data-stu-id="693ad-118">Provide a table of sales data to the *Azure Machine Learning Studio* portal, and        design an algorithm to predict future sales of popular items.</span></span>
2.  <span data-ttu-id="693ad-119">Crear un **proyecto Unity**, que puede recibir e interpretar los datos de predicción desde el servicio de aprendizaje automático.</span><span class="sxs-lookup"><span data-stu-id="693ad-119">Create a **Unity Project**, which can receive and interpret prediction data from the ML service.</span></span>
3.  <span data-ttu-id="693ad-120">Mostrar los datos por predicación visualmente dentro la **proyecto Unity**hasta que proporciona los elementos más populares de ventas, en una estantería.</span><span class="sxs-lookup"><span data-stu-id="693ad-120">Display the predication data visually within the **Unity Project**, through providing the most popular sales items, on a shelf.</span></span>

<span data-ttu-id="693ad-121">En la aplicación, es depende de usted sobre cómo se integrará los resultados con el diseño.</span><span class="sxs-lookup"><span data-stu-id="693ad-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="693ad-122">Este curso está diseñado para mostrarle cómo integrar un servicio de Azure con el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="693ad-122">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="693ad-123">Es su trabajo consiste en usar los conocimientos que obtendrá de este curso para mejorar las aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="693ad-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="693ad-124">Este curso es un tutorial independiente, que no implican directamente otros laboratorios realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="693ad-124">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="693ad-125">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="693ad-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="693ad-126">Curso</span><span class="sxs-lookup"><span data-stu-id="693ad-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="693ad-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="693ad-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="693ad-128"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="693ad-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="693ad-129">El Sr. y Azure 307: Aprendizaje automático</span><span class="sxs-lookup"><span data-stu-id="693ad-129">MR and Azure 307: Machine learning</span></span></td><td style="text-align: center;"> <span data-ttu-id="693ad-130">✔️</span><span class="sxs-lookup"><span data-stu-id="693ad-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="693ad-131">✔️</span><span class="sxs-lookup"><span data-stu-id="693ad-131">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="693ad-132">Aunque este curso se centra principalmente en inmersivos (VR) Windows Mixed Reality, también puede aplicar lo aprendido en este curso de Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="693ad-132">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="693ad-133">Como seguir el curso, verá notas en cualquier cambio que deberá emplear para admitir HoloLens.</span><span class="sxs-lookup"><span data-stu-id="693ad-133">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="693ad-134">Al usar HoloLens, es posible que observe algunos eco durante la captura de voz.</span><span class="sxs-lookup"><span data-stu-id="693ad-134">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="693ad-135">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="693ad-135">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="693ad-136">Este tutorial está diseñado para los desarrolladores con experiencia básica con Unity y C#.</span><span class="sxs-lookup"><span data-stu-id="693ad-136">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="693ad-137">También Ten en cuenta que los requisitos previos y las instrucciones escritas en este documento representan lo que se ha probado y comprobado en el momento de redactar (mayo de 2018).</span><span class="sxs-lookup"><span data-stu-id="693ad-137">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="693ad-138">Es libre de usar el software más reciente, como se muestra en el [instalar el artículo herramientas](install-the-tools.md), aunque no se debe suponer que la información de este curso perfectamente coincida con lo que encontrará en el software más reciente que se indica a continuación .</span><span class="sxs-lookup"><span data-stu-id="693ad-138">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="693ad-139">Se recomiendan el siguiente hardware y software para este curso:</span><span class="sxs-lookup"><span data-stu-id="693ad-139">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="693ad-140">Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desarrollo de auriculares envolvente (VR)</span><span class="sxs-lookup"><span data-stu-id="693ad-140">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="693ad-141">Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="693ad-141">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="693ad-142">El SDK más reciente de Windows 10</span><span class="sxs-lookup"><span data-stu-id="693ad-142">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="693ad-143">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="693ad-143">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="693ad-144">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="693ad-144">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="693ad-145">Un [auriculares de Windows Mixed Reality envolventes (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="693ad-145">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="693ad-146">Acceso a Internet para el programa de instalación de Azure y la recuperación de datos de aprendizaje automático</span><span class="sxs-lookup"><span data-stu-id="693ad-146">Internet access for Azure setup and ML data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="693ad-147">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="693ad-147">Before you start</span></span>

<span data-ttu-id="693ad-148">Para evitar problemas de creación de este proyecto, se recomienda encarecidamente que cree el proyecto se ha mencionado en este tutorial en una carpeta raíz o cerca de la raíz (rutas de acceso de carpeta largo pueden causar problemas en tiempo de compilación).</span><span class="sxs-lookup"><span data-stu-id="693ad-148">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 

## <a name="chapter-1---azure-storage-account-setup"></a><span data-ttu-id="693ad-149">Capítulo 1: configuración de la cuenta de almacenamiento de Azure</span><span class="sxs-lookup"><span data-stu-id="693ad-149">Chapter 1 - Azure Storage Account setup</span></span>

<span data-ttu-id="693ad-150">Para usar la API del traductor de Azure, deberá configurar una instancia del servicio esté disponible para su aplicación.</span><span class="sxs-lookup"><span data-stu-id="693ad-150">To use the Azure Translator API, you will need to configure an instance of the service to be made available to your application.</span></span>
1.  <span data-ttu-id="693ad-151">Inicie sesión en el [Portal Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="693ad-151">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="693ad-152">Si no dispone de una cuenta de Azure, deberá crear uno.</span><span class="sxs-lookup"><span data-stu-id="693ad-152">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="693ad-153">Si está siguiendo este tutorial en una situación de aula o laboratorio, pida el instructor o uno de los a los supervisores de ayuda para instalar la nueva cuenta.</span><span class="sxs-lookup"><span data-stu-id="693ad-153">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="693ad-154">Una vez que haya iniciado sesión, haga clic en **cuentas de almacenamiento** en el menú izquierdo.</span><span class="sxs-lookup"><span data-stu-id="693ad-154">Once you are logged in, click on **Storage Accounts** in the left menu.</span></span>

    ![Configuración de la cuenta de almacenamiento de Azure](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > <span data-ttu-id="693ad-156">La palabra **New** se han reemplazado con **crear un recurso**, en los portales más reciente.</span><span class="sxs-lookup"><span data-stu-id="693ad-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="693ad-157">En el **cuentas de almacenamiento** pestaña, haga clic en **agregar**.</span><span class="sxs-lookup"><span data-stu-id="693ad-157">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Configuración de la cuenta de almacenamiento de Azure](images/AzureLabs-Lab7-2.png)

4.  <span data-ttu-id="693ad-159">En el **crear cuenta de almacenamiento** panel:</span><span class="sxs-lookup"><span data-stu-id="693ad-159">In the **Create Storage Account** panel:</span></span>

    1.  <span data-ttu-id="693ad-160">Insertar un **nombre** para su cuenta, tenga en cuenta este campo sólo acepta números y letras minúsculas.</span><span class="sxs-lookup"><span data-stu-id="693ad-160">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>
    2.  <span data-ttu-id="693ad-161">Para **modelo de implementación,** seleccione **Administrador de recursos**.</span><span class="sxs-lookup"><span data-stu-id="693ad-161">For **Deployment model,** select **Resource manager**.</span></span>
    3.  <span data-ttu-id="693ad-162">Para **tipo de cuenta**, seleccione **almacenamiento (uso general v1)** .</span><span class="sxs-lookup"><span data-stu-id="693ad-162">For **Account kind**, select **Storage (general purpose v1)**.</span></span>
    4.  <span data-ttu-id="693ad-163">Para **rendimiento**, seleccione **estándar**.</span><span class="sxs-lookup"><span data-stu-id="693ad-163">For **Performance**, select **Standard**.</span></span>
    5.  <span data-ttu-id="693ad-164">Para **replicación** seleccione **lectura-access--almacenamiento con redundancia geográfica (RA-GRS)** .</span><span class="sxs-lookup"><span data-stu-id="693ad-164">For **Replication** select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>
    6.  <span data-ttu-id="693ad-165">Deje **se requiere transferencia segura** como **deshabilitado**.</span><span class="sxs-lookup"><span data-stu-id="693ad-165">Leave **Secure transfer required** as **Disabled**.</span></span>
    7.  <span data-ttu-id="693ad-166">Seleccione un **suscripción**.</span><span class="sxs-lookup"><span data-stu-id="693ad-166">Select a **Subscription**.</span></span>
    4. <span data-ttu-id="693ad-167">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="693ad-167">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="693ad-168">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="693ad-168">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="693ad-169">Se recomienda mantener todos los servicios de Azure asociados a un proyecto único (por ejemplo, por ejemplo, estos laboratorios) en un grupo de recursos comunes).</span><span class="sxs-lookup"><span data-stu-id="693ad-169">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="693ad-170">Si desea leer más acerca de los grupos de recursos de Azure, inicie [visite el artículo del grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="693ad-170">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>
    
    5.  <span data-ttu-id="693ad-171">Determinar la **ubicación** para el grupo de recursos (si está creando un nuevo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="693ad-171">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="693ad-172">La ubicación sería lo ideal es que en la región donde desea ejecutar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="693ad-172">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="693ad-173">Algunos recursos de Azure solo están disponibles en determinadas regiones.</span><span class="sxs-lookup"><span data-stu-id="693ad-173">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="693ad-174">También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.</span><span class="sxs-lookup"><span data-stu-id="693ad-174">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Configuración de la cuenta de almacenamiento de Azure](images/AzureLabs-Lab7-3.png)

6.  <span data-ttu-id="693ad-176">Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="693ad-176">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="693ad-177">Una vez creada la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="693ad-177">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Configuración de la cuenta de almacenamiento de Azure](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a><span data-ttu-id="693ad-179">Capítulo 2: Azure Machine Learning Studio</span><span class="sxs-lookup"><span data-stu-id="693ad-179">Chapter 2 - The Azure Machine Learning Studio</span></span>

<span data-ttu-id="693ad-180">Para usar el *Azure Machine Learning*, deberá configurar una instancia del servicio Machine Learning para que estén disponibles para su aplicación.</span><span class="sxs-lookup"><span data-stu-id="693ad-180">To use the *Azure Machine Learning*, you will need to configure an instance of the Machine Learning service to be made available to your application.</span></span>

1.  <span data-ttu-id="693ad-181">En el Portal de Azure, haga clic en **New** en la esquina superior izquierda esquina y busque **el área de trabajo de Machine Learning Studio**, presione **ENTRAR**.</span><span class="sxs-lookup"><span data-stu-id="693ad-181">In the Azure Portal, click on **New** in the top left corner, and search for **Machine Learning Studio Workspace**, press **Enter**.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-5.png)

2.  <span data-ttu-id="693ad-183">La nueva página proporcionará una descripción de la **el área de trabajo de Machine Learning Studio** service.</span><span class="sxs-lookup"><span data-stu-id="693ad-183">The new page will provide a description of the **Machine Learning Studio Workspace**  service.</span></span> <span data-ttu-id="693ad-184">En la parte inferior izquierda de este símbolo del sistema, haga clic en el **crear** botón para crear una asociación con este servicio.</span><span class="sxs-lookup"><span data-stu-id="693ad-184">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

3.  <span data-ttu-id="693ad-185">Una vez que ha hecho clic **crear**, se mostrará un panel donde debe proporcionar algunos detalles sobre la nueva **servicio Machine Learning Studio**:</span><span class="sxs-lookup"><span data-stu-id="693ad-185">Once you have clicked on **Create**, a panel will appear where you need to provide some details about your new **Machine Learning Studio service**:</span></span>

    1.  <span data-ttu-id="693ad-186">Insertar el elemento **nombre de área de trabajo** para esta instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="693ad-186">Insert your desired **Workspace name** for this service instance.</span></span>

    2.  <span data-ttu-id="693ad-187">Seleccione un **suscripción**.</span><span class="sxs-lookup"><span data-stu-id="693ad-187">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="693ad-188">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="693ad-188">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="693ad-189">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="693ad-189">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="693ad-190">Se recomienda mantener todos los servicios de Azure asociados a un proyecto único (por ejemplo, por ejemplo, estos laboratorios) en un grupo de recursos comunes).</span><span class="sxs-lookup"><span data-stu-id="693ad-190">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="693ad-191">Si desea leer más acerca de los grupos de recursos de Azure, inicie [visite el artículo del grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="693ad-191">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="693ad-192">Determinar la **ubicación** para el grupo de recursos (si está creando un nuevo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="693ad-192">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="693ad-193">La ubicación sería lo ideal es que en la región donde desea ejecutar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="693ad-193">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="693ad-194">Algunos recursos de Azure solo están disponibles en determinadas regiones.</span><span class="sxs-lookup"><span data-stu-id="693ad-194">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="693ad-195">Debe usar el mismo grupo de recursos que usó para crear el almacenamiento de Azure en el capítulo anterior.</span><span class="sxs-lookup"><span data-stu-id="693ad-195">You should use the same resource group that you used for creating the Azure Storage in the previous Chapter.</span></span>

    5.  <span data-ttu-id="693ad-196">Para el **cuenta de almacenamiento** sección, haga clic en **usar existente**, a continuación, haga clic en el menú desplegable y desde allí, haga clic en el **cuenta de almacenamiento** que creó en el último capítulo.</span><span class="sxs-lookup"><span data-stu-id="693ad-196">For the **Storage account** section, click **Use existing**, then click the dropdown menu, and from there, click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="693ad-197">Seleccione la **plan de tarifa del área de trabajo** para usted, en el menú desplegable.</span><span class="sxs-lookup"><span data-stu-id="693ad-197">Select the appropriate **Workspace pricing tier** for you, from the dropdown menu.</span></span>

    7.  <span data-ttu-id="693ad-198">Dentro de la **plan de servicio Web** sección, haga clic en **crear** **nuevos,** , a continuación, inserte un nombre para ella en el campo de texto.</span><span class="sxs-lookup"><span data-stu-id="693ad-198">Within the **Web service plan** section, click **Create** **new,** then insert a name for it in the text field.</span></span>

    8.  <span data-ttu-id="693ad-199">Desde el **plan de servicio Web tarifa** , seleccione el nivel de precios de su elección.</span><span class="sxs-lookup"><span data-stu-id="693ad-199">From the **Web service plan pricing tier** section, select the price tier of your choice.</span></span> <span data-ttu-id="693ad-200">Un nivel llamado de pruebas de desarrollo **DEVTEST estándar** deben estar disponibles para usted sin cargo alguno.</span><span class="sxs-lookup"><span data-stu-id="693ad-200">A development testing tier called **DEVTEST Standard** should be available to you at no charge.</span></span>

    9.  <span data-ttu-id="693ad-201">También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.</span><span class="sxs-lookup"><span data-stu-id="693ad-201">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    10. <span data-ttu-id="693ad-202">Haga clic en **Crear**.</span><span class="sxs-lookup"><span data-stu-id="693ad-202">Click **Create**.</span></span>

        ![Azure Machine Learning Studio](images/AzureLabs-Lab7-6.png)

4.  <span data-ttu-id="693ad-204">Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="693ad-204">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="693ad-205">Una vez creada la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="693ad-205">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-7.png)

6.  <span data-ttu-id="693ad-207">Haga clic en la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="693ad-207">Click on the notification to explore your new Service instance.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-8.png)

7.  <span data-ttu-id="693ad-209">Haga clic en el **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="693ad-209">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="693ad-210">En la página que aparece, en el **vínculos adicionales** sección, haga clic en **iniciar Machine Learning Studio**, que dirija el explorador a la **Machine Learning Studio** Portal.</span><span class="sxs-lookup"><span data-stu-id="693ad-210">In the page displayed, under the **Additional Links** section, click **Launch Machine Learning Studio**, which will direct your browser to the **Machine Learning Studio** portal.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-9.png)

9.  <span data-ttu-id="693ad-212">Use la **sesión** botón, en la esquina superior derecha o en el centro, para iniciar sesión en el Machine Learning Studio.</span><span class="sxs-lookup"><span data-stu-id="693ad-212">Use the **Sign In** button, at the top right or in the center, to log into your Machine Learning Studio.</span></span>

    ![Azure Machine Learning Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a><span data-ttu-id="693ad-214">Capítulo 3: Machine Learning Studio: Programa de instalación del conjunto de datos</span><span class="sxs-lookup"><span data-stu-id="693ad-214">Chapter 3 - The Machine Learning Studio: Dataset setup</span></span>

<span data-ttu-id="693ad-215">Una de las maneras en que funcionan los algoritmos de Machine Learning es analizar los datos existentes y, a continuación, intentar predecir resultados futuros según el conjunto de datos existente.</span><span class="sxs-lookup"><span data-stu-id="693ad-215">One of the ways Machine Learning algorithms work is by analyzing existing data and then attempting to predict future results based on the existing data set.</span></span> <span data-ttu-id="693ad-216">Esto generalmente significa que los datos más existentes que tiene, mejor que será el algoritmo predecir resultados futuros.</span><span class="sxs-lookup"><span data-stu-id="693ad-216">This generally means that the more existing data you have, the better the algorithm will be at predicting future results.</span></span>

<span data-ttu-id="693ad-217">Se proporciona una tabla de ejemplo, en este curso, llamado [ProductsTableCSV y puede descargarse aquí](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span><span class="sxs-lookup"><span data-stu-id="693ad-217">A sample table is provided to you, for this course, called [ProductsTableCSV and can be downloaded here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="693ad-218">El archivo .zip anterior contiene tanto el **ProductsTableCSV** y el **.unitypackage**, ya que lo necesitará en [capítulo 6](#chapter-6---importing-the-mlproducts-unity-package).</span><span class="sxs-lookup"><span data-stu-id="693ad-218">The above .zip file contains both the **ProductsTableCSV** and the **.unitypackage**, which you will need in [Chapter 6](#chapter-6---importing-the-mlproducts-unity-package).</span></span> <span data-ttu-id="693ad-219">Este paquete también se proporciona en este capítulo, aunque independiente para el archivo csv.</span><span class="sxs-lookup"><span data-stu-id="693ad-219">This package is also provided within that Chapter, though separate to the csv file.</span></span>

<span data-ttu-id="693ad-220">Este conjunto de datos de ejemplo contiene un registro de los objetos vendidos en cada hora de cada día del año 2017.</span><span class="sxs-lookup"><span data-stu-id="693ad-220">This sample data set contains a record of the best-selling objects at every hour of each day of the year 2017.</span></span>
        
![Machine Learning Studio: Programa de instalación del conjunto de datos](images/AzureLabs-Lab7-11.png)

<span data-ttu-id="693ad-222">Por ejemplo, en el día 1 de 2017, a la 1 p.m. (hora 13), el elemento vendido fue sal y pimienta.</span><span class="sxs-lookup"><span data-stu-id="693ad-222">For example, on day 1 of 2017, at 1pm (hour 13), the best-selling item was salt and pepper.</span></span>

<span data-ttu-id="693ad-223">Esta tabla de ejemplo contiene 9998 entradas.</span><span class="sxs-lookup"><span data-stu-id="693ad-223">This sample table contains 9998 entries.</span></span>

1.  <span data-ttu-id="693ad-224">Regrese a la **Machine Learning Studio** portal, y agregue esta tabla como un **Dataset** para el aprendizaje automático.</span><span class="sxs-lookup"><span data-stu-id="693ad-224">Head back to the **Machine Learning Studio** portal, and add this table as a **Dataset** for your ML.</span></span> <span data-ttu-id="693ad-225">Haga clic en el **+ nuevo** botón en la esquina inferior izquierda de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="693ad-225">Do this by clicking the **+ New** button in the bottom left corner of the screen.</span></span>

    ![Machine Learning Studio: Programa de instalación del conjunto de datos](images/AzureLabs-Lab7-12.png)

2.  <span data-ttu-id="693ad-227">Una sección aparecerá en la parte inferior y en que es el panel de navegación de la izquierda.</span><span class="sxs-lookup"><span data-stu-id="693ad-227">A section will come up from the bottom, and within that there is navigation panel on the left.</span></span> <span data-ttu-id="693ad-228">Haga clic en **Dataset**, a continuación, a la derecha, **desde archivo Local**.</span><span class="sxs-lookup"><span data-stu-id="693ad-228">Click **Dataset**, then to the right of that, **From Local File**.</span></span>

    ![Machine Learning Studio: Programa de instalación del conjunto de datos](images/AzureLabs-Lab7-13.png)

3.  <span data-ttu-id="693ad-230">Cargar el nuevo **Dataset** siguiendo estos pasos:</span><span class="sxs-lookup"><span data-stu-id="693ad-230">Upload the new **Dataset** by following these steps:</span></span>

    1. <span data-ttu-id="693ad-231">Aparecerá la ventana de carga, donde puede **examinar** el disco duro para el nuevo conjunto de datos.</span><span class="sxs-lookup"><span data-stu-id="693ad-231">The upload window will appear, where you can **Browse** your hard drive for the new dataset.</span></span>

        ![Machine Learning Studio: Programa de instalación del conjunto de datos](images/AzureLabs-Lab7-14.png)

    2.  <span data-ttu-id="693ad-233">Una vez seleccionado y realizar una copia en la ventana de carga, deje la casilla de verificación desactivado.</span><span class="sxs-lookup"><span data-stu-id="693ad-233">Once selected, and back in the upload window, leave the checkbox unticked.</span></span>

    3.  <span data-ttu-id="693ad-234">En el campo de texto, escriba **ProductsTableCSV.csv** como el nombre del conjunto de datos (aunque debería agregarse automáticamente).</span><span class="sxs-lookup"><span data-stu-id="693ad-234">In the text field below, enter **ProductsTableCSV.csv** as the name for the dataset (though should automatically be added).</span></span>

    4.  <span data-ttu-id="693ad-235">Mediante el menú desplegable de **tipo**, seleccione **archivo CSV genérico con un encabezado (.csv)** .</span><span class="sxs-lookup"><span data-stu-id="693ad-235">Using the dropdown menu for **Type**, select **Generic CSV File with a header (.csv)**.</span></span>

    5.  <span data-ttu-id="693ad-236">Presione el "Tick" en la parte inferior derecha de la ventana de carga y su **Dataset** se cargará.</span><span class="sxs-lookup"><span data-stu-id="693ad-236">Press the tick in the bottom right of the upload window, and your **Dataset** will be uploaded.</span></span>

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a><span data-ttu-id="693ad-237">Capítulo 4: Machine Learning Studio: El experimento</span><span class="sxs-lookup"><span data-stu-id="693ad-237">Chapter 4 - The Machine Learning Studio: The Experiment</span></span>

<span data-ttu-id="693ad-238">Antes de generar el sistema de aprendizaje automático, deberá crear un experimento para validar su teoría acerca de los datos.</span><span class="sxs-lookup"><span data-stu-id="693ad-238">Before you can build your machine learning system, you will need to build an experiment, to validate your theory about your data.</span></span> <span data-ttu-id="693ad-239">Con los resultados, sabrá si necesita más datos, o si no hay ninguna correlación entre los datos y un resultado posible.</span><span class="sxs-lookup"><span data-stu-id="693ad-239">With the results, you will know whether you need more data, or if there is no correlation between the data and a possible outcome.</span></span>

<span data-ttu-id="693ad-240">Para empezar a crear un experimento:</span><span class="sxs-lookup"><span data-stu-id="693ad-240">To start creating an experiment:</span></span>

1.  <span data-ttu-id="693ad-241">Haga clic en nuevo en el **+ nuevo** situado en la parte inferior izquierda de la página y luego haga clic en **experimento** > **experimento en blanco**.</span><span class="sxs-lookup"><span data-stu-id="693ad-241">Click again on the **+ New** button on the bottom left of the page, then click on **Experiment** > **Blank Experiment**.</span></span>

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-15.png)

2.  <span data-ttu-id="693ad-243">Se mostrará una página nueva con un experimento en blanco:</span><span class="sxs-lookup"><span data-stu-id="693ad-243">A new page will be displayed with a blank Experiment:</span></span>

3.  <span data-ttu-id="693ad-244">En el panel de la izquierda expanda **conjuntos de datos guardados* > *Mis conjuntos de datos** y arrastre el **ProductsTableCSV** en el **Lienzo del experimento**.</span><span class="sxs-lookup"><span data-stu-id="693ad-244">From the panel on the left expand **Saved Datasets* > *My Datasets** and drag the  **ProductsTableCSV** on to the **Experiment Canvas**.</span></span>

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-16.png)

4.  <span data-ttu-id="693ad-246">En el panel de la izquierda, expanda **transformación de datos** > **muestrear y dividir**.</span><span class="sxs-lookup"><span data-stu-id="693ad-246">In the panel on the left, expand **Data Transformation** > **Sample and Split**.</span></span> <span data-ttu-id="693ad-247">A continuación, arrastre el **dividir datos** en de elemento para el **lienzo de experimento**.</span><span class="sxs-lookup"><span data-stu-id="693ad-247">Then drag the **Split Data** item in to the **Experiment Canvas**.</span></span> <span data-ttu-id="693ad-248">El elemento de datos de la división dividirá el conjunto de datos en dos partes.</span><span class="sxs-lookup"><span data-stu-id="693ad-248">The Split Data item will split the data set into two parts.</span></span> <span data-ttu-id="693ad-249">Una parte usará para entrenar el algoritmo de aprendizaje automático.</span><span class="sxs-lookup"><span data-stu-id="693ad-249">One part you will use for training the machine learning algorithm.</span></span> <span data-ttu-id="693ad-250">La segunda parte se utilizará para evaluar la precisión del algoritmo que genera.</span><span class="sxs-lookup"><span data-stu-id="693ad-250">The second part will be used to evaluate the accuracy of the algorithm generated.</span></span>

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-17.png)

5.  <span data-ttu-id="693ad-252">En el panel derecho (mientras que los datos de la división se selecciona el elemento en el lienzo), edite el **fracción de filas del primer conjunto de datos de salida** a **0,7**.</span><span class="sxs-lookup"><span data-stu-id="693ad-252">In the right panel (while the Split Data item on the canvas is selected), edit the **Fraction of rows in the first output dataset** to **0.7**.</span></span> <span data-ttu-id="693ad-253">Esto dividirá los datos en dos partes, la primera parte será un 70% de los datos y la segunda parte será el 30% restante.</span><span class="sxs-lookup"><span data-stu-id="693ad-253">This will split the data into two parts, the first part will be 70% of the data, and the second part will be the remaining 30%.</span></span> <span data-ttu-id="693ad-254">Para asegurarse de que los datos se dividen al azar, asegúrese de que el **división aleatoria** permanezca activada la casilla de verificación.</span><span class="sxs-lookup"><span data-stu-id="693ad-254">To ensure that the data is split randomly, make sure the **Randomized split** checkbox remains checked.</span></span>

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-18.png)

6.  <span data-ttu-id="693ad-256">Arrastre una conexión de la base de la **ProductsTableCSV** elemento en el lienzo en la parte superior del elemento de datos de la división.</span><span class="sxs-lookup"><span data-stu-id="693ad-256">Drag a connection from the base of the **ProductsTableCSV** item on the canvas to the top of the Split Data item.</span></span> <span data-ttu-id="693ad-257">Esto se conectará los elementos y enviar el **ProductsTableCSV** salida del conjunto de datos (los datos) a la entrada de datos de división.</span><span class="sxs-lookup"><span data-stu-id="693ad-257">This will connect the items and send the **ProductsTableCSV** dataset output (the data) to the Split Data input.</span></span>  

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-19.png)

7.  <span data-ttu-id="693ad-259">En el **experimentos** del panel en el lado izquierdo, expanda \**Machine Learning* > \* "Train" \*\*.</span><span class="sxs-lookup"><span data-stu-id="693ad-259">In the **Experiments** panel on the left side, expand \**Machine Learning* > \*Train\*\*.</span></span> <span data-ttu-id="693ad-260">Arrastre el **Train Model** elemento alejar en al lienzo del experimento.</span><span class="sxs-lookup"><span data-stu-id="693ad-260">Drag the **Train Model** item out in to the Experiment canvas.</span></span> <span data-ttu-id="693ad-261">El lienzo debe ser igual a la siguiente.</span><span class="sxs-lookup"><span data-stu-id="693ad-261">Your canvas should look the same as the below.</span></span>

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-20.png)

8.  <span data-ttu-id="693ad-263">Desde el ***inferior izquierdo*** de la **dividir datos** elemento arrastrar una conexión a la **la parte superior derecha** de la **Train Model** elemento.</span><span class="sxs-lookup"><span data-stu-id="693ad-263">From the ***bottom left*** of the **Split Data** item drag a connection to the **top right** of the **Train Model** item.</span></span> <span data-ttu-id="693ad-264">La primera división de un 70% del conjunto de datos se usará el modelo de entrenamiento para entrenar el algoritmo.</span><span class="sxs-lookup"><span data-stu-id="693ad-264">The first 70% split from the dataset will be used by the Train Model to train the algorithm.</span></span>

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-21.png)

9.  <span data-ttu-id="693ad-266">Seleccione el **Train Model** elemento en el lienzo y, en el **propiedades** panel (en el lado derecho de la ventana del explorador), haga clic la **iniciar el selector de columna** botón.</span><span class="sxs-lookup"><span data-stu-id="693ad-266">Select the **Train Model** item on the canvas, and in the **Properties** panel (on the right-hand side of your browser window) click the **Launch column selector** button.</span></span>

10. <span data-ttu-id="693ad-267">En el cuadro de texto escriba **producto** y, a continuación, presione **ENTRAR**, *producto* se establecerá como una columna para entrenar predicciones.</span><span class="sxs-lookup"><span data-stu-id="693ad-267">In the text box type **product** and then press **Enter**, *product* will be set as a column to train predictions.</span></span> <span data-ttu-id="693ad-268">A continuación, haga clic en el **graduación** en la esquina inferior derecha para cerrar el cuadro de diálogo de selección.</span><span class="sxs-lookup"><span data-stu-id="693ad-268">Following this, click on the **tick** in the bottom-right corner to close the selection dialog.</span></span>

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-22.png)

11. <span data-ttu-id="693ad-270">Va a entrenar un **regresión logística Multiclase** para predecir la dirección de venta más **producto** según la hora del día y la fecha.</span><span class="sxs-lookup"><span data-stu-id="693ad-270">You are going to train a **Multiclass Logistic Regression** algorithm to predict the most sold **product** based on the hour of the day and the date.</span></span> <span data-ttu-id="693ad-271">Queda fuera del ámbito de este documento para explicar los detalles de los diferentes algoritmos proporcionados por Azure Machine Learning studio, sin embargo, puede encontrar más información en el [hoja de referencia rápida de algoritmos de Machine Learning](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span><span class="sxs-lookup"><span data-stu-id="693ad-271">It is beyond the scope of this document to explain the details of the different algorithms provided by the Azure Machine Learning studio, though, you can find out more from the [Machine Learning Algorithm Cheat Sheet](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span></span>

12. <span data-ttu-id="693ad-272">En el panel de elementos de experimento de la izquierda, expanda \*\**Machine Learning* > *Initialize Model* > \* \*\*\* clasificación y arrastre el **regresión logística Multiclase**  elemento de sesión en el lienzo del experimento.</span><span class="sxs-lookup"><span data-stu-id="693ad-272">From the experiment items panel on the left, expand \*\**Machine Learning* > *Initialize Model* > \*Classification\*\*\*, and drag the **Multiclass Logistic Regression** item on to the experiment canvas.</span></span>

13. <span data-ttu-id="693ad-273">Conecte la salida, de la parte inferior de la **regresión logística Multiclase**, a la entrada de la parte superior izquierda de la **Train Model** elemento.</span><span class="sxs-lookup"><span data-stu-id="693ad-273">Connect the output, from the bottom of the **Multiclass Logistic Regression**, to the top-left input of the **Train Model** item.</span></span>

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-23.png)

14. <span data-ttu-id="693ad-275">En la lista de elementos de experimento en el panel de la izquierda, expanda \**Machine Learning* > \* puntuación \*\* y arrastre el **Score Model** elemento de sesión en el lienzo.</span><span class="sxs-lookup"><span data-stu-id="693ad-275">In list of experiment items in the panel on the left, expand \**Machine Learning* > \*Score\*\*, and drag the **Score Model** item on to the canvas.</span></span>

15. <span data-ttu-id="693ad-276">Conecte la salida, de la parte inferior de la **Train Model**, a la entrada de la parte superior izquierda de la **Score Model**.</span><span class="sxs-lookup"><span data-stu-id="693ad-276">Connect the output, from the bottom of the **Train Model**, to the top-left input of the **Score Model**.</span></span>

16. <span data-ttu-id="693ad-277">Conecte la salida de la esquina inferior derecha de **dividir datos**, a la entrada de la parte superior derecha de la  **Score Model* elemento*.</span><span class="sxs-lookup"><span data-stu-id="693ad-277">Connect the bottom-right output from **Split Data**, to the top-right input of the **Score Model* item*.</span></span>

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-24.png)

17. <span data-ttu-id="693ad-279">En la lista de **experimento** elementos en el panel de la izquierda, expanda \*\**Machine Learning* > \* \*\*\* Evaluate y arrastre el **Evaluate Model** elemento hasta el lienzo.</span><span class="sxs-lookup"><span data-stu-id="693ad-279">In the list of **Experiment** items in the panel on the left, expand \*\**Machine Learning* > \*Evaluate\*\*\*, and drag the **Evaluate Model** item onto the canvas.</span></span>

18. <span data-ttu-id="693ad-280">Conecte la salida desde el **Score Model** a la entrada de la parte superior izquierda de la **Evaluate Model**.</span><span class="sxs-lookup"><span data-stu-id="693ad-280">Connect the output from the **Score Model** to the top-left input of the **Evaluate Model**.</span></span>

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-25.png)

19. <span data-ttu-id="693ad-282">Ha creado su primer experimento de Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="693ad-282">You have built your first Machine Learning Experiment.</span></span> <span data-ttu-id="693ad-283">Ahora puede guardar y ejecutar el experimento.</span><span class="sxs-lookup"><span data-stu-id="693ad-283">You can now save and run the experiment.</span></span> <span data-ttu-id="693ad-284">En el menú en la parte inferior de la página, haga clic en el **guardar** botón para guardar el experimento y, a continuación, haga clic en **ejecutar** al principio del experimento.</span><span class="sxs-lookup"><span data-stu-id="693ad-284">In the menu at the bottom of the page, click on the **Save** button to save your experiment and then click **Run** to the start the experiment.</span></span>

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-26.png)

20. <span data-ttu-id="693ad-286">Puede ver el **estado** del experimento en la parte superior derecha del lienzo.</span><span class="sxs-lookup"><span data-stu-id="693ad-286">You can see the **status** of the experiment in the top-right of the canvas.</span></span> <span data-ttu-id="693ad-287">Espere unos instantes para el experimento finalice.</span><span class="sxs-lookup"><span data-stu-id="693ad-287">Wait a few moments for the experiment to finish.</span></span>

    > <span data-ttu-id="693ad-288">Si tiene un conjunto de datos grande (reales) es probable que el experimento podría tardar horas en ejecutarse.</span><span class="sxs-lookup"><span data-stu-id="693ad-288">If you have a big (real world) dataset it is likely that the experiment could take hours to run.</span></span>

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-27.png)

21. <span data-ttu-id="693ad-290">Haga clic con el botón derecho en el **Evaluate Model** de elemento en el lienzo y de mantener el mouse del menú de contexto el mouse sobre **resultados de la evaluación**, a continuación, seleccione **visualizar**.</span><span class="sxs-lookup"><span data-stu-id="693ad-290">Right click on the **Evaluate Model** item in the canvas and from the context menu hover the mouse over **Evaluation Results**, then select **Visualize**.</span></span>

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-28.png)

22. <span data-ttu-id="693ad-292">Se mostrará los resultados de evaluación que muestra los resultados predichos frente a los resultados reales.</span><span class="sxs-lookup"><span data-stu-id="693ad-292">The evaluation results will be displayed showing the predicted outcomes versus the actual outcomes.</span></span> <span data-ttu-id="693ad-293">Esto usa el 30% del conjunto de datos original, que se ha dividido en versiones anteriores, para evaluar el modelo.</span><span class="sxs-lookup"><span data-stu-id="693ad-293">This uses the 30% of the original dataset, that was split earlier, for evaluating the model.</span></span> <span data-ttu-id="693ad-294">Puede ver que los resultados no son excelentes, lo ideal es que podría tener el número más alto en cada fila estará el elemento resaltado en las columnas.</span><span class="sxs-lookup"><span data-stu-id="693ad-294">You can see the results are not great, ideally you would have the highest number in each row be the highlighted item in the columns.</span></span>

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-29.png)

23. <span data-ttu-id="693ad-296">Cerrar la **resultados**.</span><span class="sxs-lookup"><span data-stu-id="693ad-296">Close the **Results**.</span></span>

24. <span data-ttu-id="693ad-297">Para usar el modelo recién entrenado de Machine Learning debe exponer como un **servicio Web**.</span><span class="sxs-lookup"><span data-stu-id="693ad-297">To use your newly trained Machine Learning model you need to expose it as a **Web Service**.</span></span> <span data-ttu-id="693ad-298">Para ello, haga clic en el **Configurar servicio Web** menú de elemento en el menú en la parte inferior de la página y haga clic en **servicio Web predictivo**.</span><span class="sxs-lookup"><span data-stu-id="693ad-298">To do this, click on the **Set Up Web Service** menu item in the menu at the bottom of the page, and click on **Predictive Web Service**.</span></span>

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-30.png)

25. <span data-ttu-id="693ad-300">Se creará una nueva pestaña y el modelo de entrenamiento se combina para crear el nuevo servicio web.</span><span class="sxs-lookup"><span data-stu-id="693ad-300">A new tab will be created, and the train model merged to create the new web service.</span></span> 

26. <span data-ttu-id="693ad-301">En el menú en la parte inferior de la página, haga clic en **guardar**, a continuación, haga clic en **ejecutar**.</span><span class="sxs-lookup"><span data-stu-id="693ad-301">In the menu at the bottom of the page click **Save**, then click **Run**.</span></span> <span data-ttu-id="693ad-302">Verá el estado actualizado en la esquina superior derecha del lienzo del experimento.</span><span class="sxs-lookup"><span data-stu-id="693ad-302">You will see the status updated in the top-right corner of the experiment canvas.</span></span>

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-31.png)

27. <span data-ttu-id="693ad-304">Una vez que haya terminado de ejecutarse, una **implementar servicio Web** botón aparecerá en la parte inferior de la página.</span><span class="sxs-lookup"><span data-stu-id="693ad-304">Once it has finished running, a **Deploy Web Service** button will appear at the bottom of the page.</span></span> <span data-ttu-id="693ad-305">Está listo para implementar el servicio web.</span><span class="sxs-lookup"><span data-stu-id="693ad-305">You are ready to deploy the web service.</span></span> <span data-ttu-id="693ad-306">Haga clic en **implementar servicio Web** (clásica) en el menú en la parte inferior de la página.</span><span class="sxs-lookup"><span data-stu-id="693ad-306">Click **Deploy Web Service** (Classic) in the menu at the bottom of the page.</span></span>

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-32.png)

    > <span data-ttu-id="693ad-308">El explorador puede preguntar para permitir que una ventana emergente, que debería **permitir**, aunque es posible que deba presionar **implementar servicio Web** nuevamente, si no aparece la página implementar.</span><span class="sxs-lookup"><span data-stu-id="693ad-308">Your browser may prompt to allow a pop-up, which you should **allow**, though you may need to press **Deploy Web Service** again, if the deploy page does not show.</span></span> 

28. <span data-ttu-id="693ad-309">Una vez creado el experimento se le redirigirá a una **panel** página donde tendrá su **clave de API** muestra.</span><span class="sxs-lookup"><span data-stu-id="693ad-309">Once the Experiment has been created you will be redirected to a **Dashboard** page where you will have your **API Key** displayed.</span></span> <span data-ttu-id="693ad-310">Cópiela en el Bloc de notas por el momento, ya que lo necesitará en el código muy pronto.</span><span class="sxs-lookup"><span data-stu-id="693ad-310">Copy it into a notepad for the moment, you will need it in your code very soon.</span></span> <span data-ttu-id="693ad-311">Una vez que haya anotado la clave de API, haga clic en el **solicitud/respuesta** situado en la **punto de conexión predeterminado** sección debajo de la clave.</span><span class="sxs-lookup"><span data-stu-id="693ad-311">Once you have noted your API Key, click on the **REQUEST/RESPONSE** button in the **Default Endpoint** section underneath the Key.</span></span>

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > <span data-ttu-id="693ad-313">Si hace clic en prueba en esta página, podrá escribir datos de entrada y ver la salida.</span><span class="sxs-lookup"><span data-stu-id="693ad-313">If you click Test in this page, you will be able to enter input data and view the output.</span></span> <span data-ttu-id="693ad-314">Escriba el **día** y **hora**.</span><span class="sxs-lookup"><span data-stu-id="693ad-314">Enter the **day** and **hour**.</span></span> <span data-ttu-id="693ad-315">Deje el **producto** entrada en blanco.</span><span class="sxs-lookup"><span data-stu-id="693ad-315">Leave the **product** entry blank.</span></span> <span data-ttu-id="693ad-316">A continuación, haga clic en el **confirmar** botón.</span><span class="sxs-lookup"><span data-stu-id="693ad-316">Then click the **Confirm** button.</span></span> <span data-ttu-id="693ad-317">La salida en la parte inferior de la página mostrará el JSON que representa la probabilidad de cada producto que se va a la opción.</span><span class="sxs-lookup"><span data-stu-id="693ad-317">The output on the bottom of the page will show the JSON representing the likelihood of each product being the choice.</span></span>

29. <span data-ttu-id="693ad-318">Se abrirá una página web nueva, mostrar las instrucciones y algunos ejemplos sobre la estructura de solicitud requeridos por Machine Learning Studio.</span><span class="sxs-lookup"><span data-stu-id="693ad-318">A new web page will open up, displaying the instructions and some examples about the Request structure required by the Machine Learning Studio.</span></span> <span data-ttu-id="693ad-319">Copia el **URI de solicitud** muestra en esta página, en el Bloc de notas.</span><span class="sxs-lookup"><span data-stu-id="693ad-319">Copy the **Request URI** displayed in this page, into your notepad.</span></span>

    ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-34.png)

<span data-ttu-id="693ad-321">Ahora ha creado un sistema de aprendizaje automático que proporciona el producto para venderse probablemente basándose en datos históricos de compras, que se correlacionan con la hora del día y el día del año.</span><span class="sxs-lookup"><span data-stu-id="693ad-321">You have now built a machine learning system that provides the most likely product to be sold based on historical purchasing data, correlated with the time of the day and day of the year.</span></span>

<span data-ttu-id="693ad-322">Para llamar al servicio web, necesitará la dirección URL para el extremo de servicio y una clave de API para el servicio.</span><span class="sxs-lookup"><span data-stu-id="693ad-322">To call the web service, you will need the URL for the service endpoint and an API Key for the service.</span></span> <span data-ttu-id="693ad-323">Haga clic en el **Consume** ficha, en el menú superior.</span><span class="sxs-lookup"><span data-stu-id="693ad-323">Click on the **Consume** tab, from the top menu.</span></span>

<span data-ttu-id="693ad-324">El **consumo** página de información mostrará la información que necesitará llamar al servicio web desde el código.</span><span class="sxs-lookup"><span data-stu-id="693ad-324">The **Consumption** Info page will display the information you will need to call the web service from your code.</span></span> <span data-ttu-id="693ad-325">Realice una copia de la **Primary Key** y **Request-Response** dirección URL.</span><span class="sxs-lookup"><span data-stu-id="693ad-325">Take a copy of the **Primary Key** and the **Request-Response** URL.</span></span> <span data-ttu-id="693ad-326">Necesitará estos en el capítulo siguiente.</span><span class="sxs-lookup"><span data-stu-id="693ad-326">You will need these in the next Chapter.</span></span>

## <a name="chapter-5---setting-up-the-unity-project"></a><span data-ttu-id="693ad-327">Capítulo 5: configurar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="693ad-327">Chapter 5 - Setting up the Unity Project</span></span>

<span data-ttu-id="693ad-328">Configurar y probar los auriculares envolventes de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="693ad-328">Set up and test your Mixed Reality Immersive Headset.</span></span>

> [!NOTE]
>  <span data-ttu-id="693ad-329">Podrá **no** requieren controladores de movimiento de este curso.</span><span class="sxs-lookup"><span data-stu-id="693ad-329">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="693ad-330">Si necesita admite la configuración de los auriculares envolventes, por favor, haga clic en [aquí](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="693ad-330">If you need support setting up the Immersive Headset, please click [HERE](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="693ad-331">Abra **Unity** y cree un nuevo proyecto de Unity denominado **MR\_MachineLearning.**</span><span class="sxs-lookup"><span data-stu-id="693ad-331">Open **Unity** and create a new Unity Project called **MR\_MachineLearning.**</span></span> <span data-ttu-id="693ad-332">Asegúrese de que el tipo de proyecto se establece en **3D**.</span><span class="sxs-lookup"><span data-stu-id="693ad-332">Make sure the project type is set to **3D**.</span></span>

2.  <span data-ttu-id="693ad-333">Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="693ad-333">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="693ad-334">Vaya a ***editar* > *preferencias*** y, a continuación, en la ventana nueva, vaya a **herramientas externas**.</span><span class="sxs-lookup"><span data-stu-id="693ad-334">Go to ***Edit* > *Preferences*** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="693ad-335">Cambio **External Script Editor** a **de Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="693ad-335">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="693ad-336">Cerrar la **preferencias** ventana.</span><span class="sxs-lookup"><span data-stu-id="693ad-336">Close the **Preferences** window.</span></span>

3.  <span data-ttu-id="693ad-337">A continuación, vaya a ***archivo* > *configuración de compilación*** y cambiar la plataforma a **Universal Windows Platform**, haciendo clic en el ***Cambiar plataforma*** botón.</span><span class="sxs-lookup"><span data-stu-id="693ad-337">Next, go to ***File* > *Build Settings*** and switch the platform to **Universal Windows Platform**, by clicking on the ***Switch Platform*** button.</span></span>

4.  <span data-ttu-id="693ad-338">También asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="693ad-338">Also make sure that:</span></span>

    1.  <span data-ttu-id="693ad-339">**Dispositivo de destino** está establecido en **cualquier dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="693ad-339">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="693ad-340">Para el Microsoft HoloLens, establezca **dispositivo de destino** a *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="693ad-340">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="693ad-341">**Tipo de compilación** está establecido en **D3D**.</span><span class="sxs-lookup"><span data-stu-id="693ad-341">**Build Type** is set to **D3D**.</span></span>

    3.  <span data-ttu-id="693ad-342">**SDK** está establecido en **más reciente instalado**.</span><span class="sxs-lookup"><span data-stu-id="693ad-342">**SDK** is set to **Latest installed**.</span></span>

    4.  <span data-ttu-id="693ad-343">**Versión de Visual Studio** está establecido en **más reciente instalado**.</span><span class="sxs-lookup"><span data-stu-id="693ad-343">**Visual Studio Version** is set to **Latest installed**.</span></span>

    5.  <span data-ttu-id="693ad-344">**Compilar y ejecutar** está establecido en **máquina Local**.</span><span class="sxs-lookup"><span data-stu-id="693ad-344">**Build and Run** is set to **Local Machine**.</span></span>

    6.  <span data-ttu-id="693ad-345">No se preocupe sobre cómo configurar **escenas** ahora mismo, tal como se proporcionan más adelante.</span><span class="sxs-lookup"><span data-stu-id="693ad-345">Do not worry about setting up **Scenes** right now, as these are provided later.</span></span>

    7.  <span data-ttu-id="693ad-346">Por ahora, se debe dejar el resto de la configuración como valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="693ad-346">The remaining settings should be left as default for now.</span></span>

        ![Configurar el proyecto de Unity](images/AzureLabs-Lab7-35.png)

5.  <span data-ttu-id="693ad-348">En el **configuración de compilación** ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el **Inspector** se encuentra.</span><span class="sxs-lookup"><span data-stu-id="693ad-348">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

6. <span data-ttu-id="693ad-349">En este panel, es necesario comprobar algunas opciones de configuración:</span><span class="sxs-lookup"><span data-stu-id="693ad-349">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="693ad-350">En el **otra configuración** pestaña:</span><span class="sxs-lookup"><span data-stu-id="693ad-350">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="693ad-351">**Scripting** **en tiempo de ejecución versión** debe ser **Experimental** (.NET 4.6 equivalente)</span><span class="sxs-lookup"><span data-stu-id="693ad-351">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>

        2. <span data-ttu-id="693ad-352">**Scripting de back-end** debe ser ***.NET***</span><span class="sxs-lookup"><span data-stu-id="693ad-352">**Scripting Backend** should be ***.NET***</span></span>

        3. <span data-ttu-id="693ad-353">**Nivel de compatibilidad de API** debe ser **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="693ad-353">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab7-36.png)

    2.  <span data-ttu-id="693ad-355">Dentro de la **configuración de publicación** ficha **capacidades**, consulte:</span><span class="sxs-lookup"><span data-stu-id="693ad-355">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="693ad-356">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="693ad-356">**InternetClient**</span></span>

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab7-37.png)

    3.  <span data-ttu-id="693ad-358">Más abajo el panel, en **XR configuración** (bajo **configuración de publicación**), graduación **admite la realidad Virtual**, asegúrese de que el **SDK de Windows Mixed Reality**  se agrega</span><span class="sxs-lookup"><span data-stu-id="693ad-358">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![Configurar el proyecto de Unity](images/AzureLabs-Lab7-38.png)

    

6.  <span data-ttu-id="693ad-360">En **configuración de compilación** *Unity C#*  proyectos ya no está atenuada; Marque la casilla situada junto a esto.</span><span class="sxs-lookup"><span data-stu-id="693ad-360">Back in **Build Settings** *Unity C#* Projects is no longer greyed out; tick the checkbox next to this.</span></span> 

7.  <span data-ttu-id="693ad-361">Cierre la ventana de configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="693ad-361">Close the Build Settings window.</span></span>

8.  <span data-ttu-id="693ad-362">Guarde el proyecto (**archivo > Guardar proyecto**).</span><span class="sxs-lookup"><span data-stu-id="693ad-362">Save your Project (**FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a><span data-ttu-id="693ad-363">Capítulo 6: importar el paquete de Unity MLProducts</span><span class="sxs-lookup"><span data-stu-id="693ad-363">Chapter 6 - Importing the MLProducts Unity Package</span></span>

<span data-ttu-id="693ad-364">En este curso, deberá descargar un paquete de activos de Unity llamado [ **MR-Azure-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="693ad-364">For this course, you will need to download a Unity Asset Package called [**Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span></span> <span data-ttu-id="693ad-365">Este paquete viene acompañada de una escena, con todos los objetos de ese creados previamente, para que pueda centrarse en hacer que todo funciona correctamente.</span><span class="sxs-lookup"><span data-stu-id="693ad-365">This package comes complete with a scene, with all objects in that prebuilt, so you can focus on getting it all working.</span></span> <span data-ttu-id="693ad-366">El **ShelfKeeper** se proporciona la secuencia de comandos, aunque solo contiene las variables públicas, con el fin de la estructura del programa de instalación de escena.</span><span class="sxs-lookup"><span data-stu-id="693ad-366">The **ShelfKeeper** script is provided, though only holds the public variables, for the purpose of scene setup structure.</span></span> <span data-ttu-id="693ad-367">Deberá realizar todas las demás secciones.</span><span class="sxs-lookup"><span data-stu-id="693ad-367">You will need to do all other sections.</span></span> 

<span data-ttu-id="693ad-368">Para importar este paquete:</span><span class="sxs-lookup"><span data-stu-id="693ad-368">To import this package:</span></span>

1.  <span data-ttu-id="693ad-369">Con el panel de Unity delante de usted, haga clic en **activos** en el menú en la parte superior de la pantalla, a continuación, haga clic en **Importar paquete, paquete personalizado**.</span><span class="sxs-lookup"><span data-stu-id="693ad-369">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package, Custom Package**.</span></span>

    ![Importar el paquete de Unity MLProducts](images/AzureLabs-Lab7-39.png)

2.  <span data-ttu-id="693ad-371">Utilice el selector de archivos para seleccionar la **MR-Azure-307.unitypackage** del paquete y haga clic en **abierto**.</span><span class="sxs-lookup"><span data-stu-id="693ad-371">Use the file picker to select the **Azure-MR-307.unitypackage** package and click **Open**.</span></span>

3.  <span data-ttu-id="693ad-372">Se mostrará una lista de componentes para este recurso para usted.</span><span class="sxs-lookup"><span data-stu-id="693ad-372">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="693ad-373">Haga clic en confirmar la importación **importar**.</span><span class="sxs-lookup"><span data-stu-id="693ad-373">Confirm the import by clicking **Import**.</span></span>

    ![Importar el paquete de Unity MLProducts](images/AzureLabs-Lab7-40.png)

4.  <span data-ttu-id="693ad-375">Una vez que haya terminado de importarse, observará que algunas carpetas nuevas han aparecido en el Unity **Panel proyecto**.</span><span class="sxs-lookup"><span data-stu-id="693ad-375">Once it has finished importing, you will notice that some new folders have appeared in your Unity **Project Panel**.</span></span> <span data-ttu-id="693ad-376">Estos son los modelos 3D y los materiales respectivos que forman parte de la escena prefabricada que funcionará en.</span><span class="sxs-lookup"><span data-stu-id="693ad-376">Those are the 3D models and the respective materials that are part of the pre-made scene you will work on.</span></span> <span data-ttu-id="693ad-377">En este curso, escribirá la mayoría del código.</span><span class="sxs-lookup"><span data-stu-id="693ad-377">You will write the majority of the code in this course.</span></span>

    ![Importar el paquete de Unity MLProducts](images/AzureLabs-Lab7-41.png)

5.  <span data-ttu-id="693ad-379">Dentro de la **Panel proyecto** carpeta, haga clic en el **escenas** carpeta y haga doble clic en la escena dentro de (denominada **MR_MachineLearningScene**).</span><span class="sxs-lookup"><span data-stu-id="693ad-379">Within the **Project Panel** folder, click on the **Scenes** folder and double click on the scene inside (called **MR_MachineLearningScene**).</span></span> <span data-ttu-id="693ad-380">Se abrirá la escena (consulte la imagen siguiente).</span><span class="sxs-lookup"><span data-stu-id="693ad-380">The scene will open (see image below).</span></span> <span data-ttu-id="693ad-381">Si faltan los rombos rojo, simplemente haga clic en el **Gizmos** situado en la parte superior derecha de la **Panel juego**.</span><span class="sxs-lookup"><span data-stu-id="693ad-381">If the red diamonds are missing, simply click the **Gizmos** button, at the top right of the **Game Panel**.</span></span>

    ![Importar el paquete de Unity MLProducts](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a><span data-ttu-id="693ad-383">Capítulo 7: comprobación de los archivos DLL en Unity</span><span class="sxs-lookup"><span data-stu-id="693ad-383">Chapter 7 - Checking the DLLs in Unity</span></span>

<span data-ttu-id="693ad-384">Para aprovechar el uso de bibliotecas JSON (usado para serializar y deserializar), se ha implementado con el paquete en que puede poner una DLL de Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="693ad-384">To leverage the use of JSON libraries (used for serializing and deserializing), a Newtonsoft DLL has been implemented with the package you brought in.</span></span> <span data-ttu-id="693ad-385">La biblioteca debe tener la configuración correcta, aunque es conveniente comprobar (especialmente si tiene problemas con el código no funciona).</span><span class="sxs-lookup"><span data-stu-id="693ad-385">The library should have the correct configuration, though it is worth checking (particularly if you are having issues with code not working).</span></span> 

<span data-ttu-id="693ad-386">Para ello:</span><span class="sxs-lookup"><span data-stu-id="693ad-386">To do so:</span></span>

-  <span data-ttu-id="693ad-387">Haga clic en el archivo Newtonsoft dentro de la carpeta de complementos y examine el **panel Inspector**.</span><span class="sxs-lookup"><span data-stu-id="693ad-387">Left-click on the Newtonsoft file inside the Plugins folder and look at the **Inspector panel**.</span></span> <span data-ttu-id="693ad-388">Asegúrese de que **cualquier plataforma** está activada.</span><span class="sxs-lookup"><span data-stu-id="693ad-388">Make sure **Any Platform** is ticked.</span></span> <span data-ttu-id="693ad-389">Vaya a la **ficha UWP** y asegúrese también de **no procesar** está activada.</span><span class="sxs-lookup"><span data-stu-id="693ad-389">Go to the **UWP tab** and also ensure **Don't process** is ticked.</span></span>

    ![Importar los archivos DLL en Unity](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a><span data-ttu-id="693ad-391">Capítulo 8: crear la clase ShelfKeeper</span><span class="sxs-lookup"><span data-stu-id="693ad-391">Chapter 8 - Create the ShelfKeeper class</span></span>

<span data-ttu-id="693ad-392">El **ShelfKeeper** clase hospeda a los métodos que controlan la interfaz de usuario y los productos generados en la escena.</span><span class="sxs-lookup"><span data-stu-id="693ad-392">The **ShelfKeeper** class hosts methods that control the UI and products spawned in the scene.</span></span>

<span data-ttu-id="693ad-393">Como parte del paquete importado, se habrá ha dado esta clase, aunque es incompleta.</span><span class="sxs-lookup"><span data-stu-id="693ad-393">As part of the imported package, you will have been given this class, though it is incomplete.</span></span> <span data-ttu-id="693ad-394">Ahora es el momento de completar dicha clase:</span><span class="sxs-lookup"><span data-stu-id="693ad-394">It is now time to complete that class:</span></span>

1.  <span data-ttu-id="693ad-395">Haga doble clic en el **ShelfKeeper** secuencia de comandos, en el **Scripts** carpeta para abrirla con **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="693ad-395">Double click on the **ShelfKeeper** script, within the **Scripts** folder, to open it with **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="693ad-396">Reemplace todo el código existente en el script con el código siguiente, que establece la fecha y hora y tiene un método para mostrar un producto.</span><span class="sxs-lookup"><span data-stu-id="693ad-396">Replace all the code existing in the script with the following code, which sets the time and date and has a method to show a product.</span></span>

    ```csharp
    using UnityEngine;

    public class ShelfKeeper : MonoBehaviour
    {
        /// <summary>
        /// Provides this class Singleton-like behavior
        /// </summary>
        public static ShelfKeeper instance;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for data
        /// </summary>
        public TextMesh dateText;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for time
        /// </summary>
        public TextMesh timeText;

        /// <summary>
        /// Provides references to the spawn locations for the products prefabs
        /// </summary>
        public Transform[] spawnPoint;

        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Set the text of the date in the scene
        /// </summary>
        public void SetDate(string day, string month)
        {
            dateText.text = day + " " + month;
        }

        /// <summary>
        /// Set the text of the time in the scene
        /// </summary>
        public void SetTime(string hour)
        {
            timeText.text = hour + ":00";
        }

        /// <summary>
        /// Spawn a product on the shelf by providing the name and selling grade
        /// </summary>
        /// <param name="name"></param>
        /// <param name="sellingGrade">0 being the best seller</param>
        public void SpawnProduct(string name, int sellingGrade)
        {
            Instantiate(Resources.Load(name),
                spawnPoint[sellingGrade].transform.position, spawnPoint[sellingGrade].transform.rotation);
        }
    }
    ```

3.  <span data-ttu-id="693ad-397">Asegúrese de guardar los cambios en **Visual Studio** antes de volver a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="693ad-397">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

4.  <span data-ttu-id="693ad-398">Atrás en el Editor de Unity, compruebe que la **ShelfKeeper** clase similar a la siguiente:</span><span class="sxs-lookup"><span data-stu-id="693ad-398">Back in the Unity Editor, check that the **ShelfKeeper** class looks like the below:</span></span>

    ![Crear la clase ShelfKeeper](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > <span data-ttu-id="693ad-400">Si la secuencia de comandos no tiene los destinos de referencia (es decir, *fecha (texto de la malla)* ), basta con arrastrar los objetos correspondientes de la **jerarquía Panel**, en los campos de destino.</span><span class="sxs-lookup"><span data-stu-id="693ad-400">If your script does not have the reference targets (i.e. *Date (Text Mesh)*), simply drag the corresponding objects from the **Hierarchy Panel**, into the target fields.</span></span> <span data-ttu-id="693ad-401">Consulte más abajo para ver una explicación, si es necesario:</span><span class="sxs-lookup"><span data-stu-id="693ad-401">See below for explanation, if needed:</span></span>
    > 
    > 1.  <span data-ttu-id="693ad-402">Abra el **punto Spawn** matriz dentro de la **ShelfKeeper** script componente pulsando en él.</span><span class="sxs-lookup"><span data-stu-id="693ad-402">Open the **Spawn Point** array within the **ShelfKeeper** component script by left-clicking it.</span></span> <span data-ttu-id="693ad-403">Una subsección aparecerá llamada **tamaño**, lo que indica el tamaño de la matriz.</span><span class="sxs-lookup"><span data-stu-id="693ad-403">A sub-section will appear called **Size**, which indicates the size of the array.</span></span> <span data-ttu-id="693ad-404">Tipo **3** en el cuadro de texto junto a **tamaño** y presione **ENTRAR**, y se crearán tres ranuras debajo.</span><span class="sxs-lookup"><span data-stu-id="693ad-404">Type **3** into the textbox next to **Size** and press **Enter**, and three slots will be created beneath.</span></span>
    > 2. <span data-ttu-id="693ad-405">Dentro de la **jerarquía** expandir la **tiempo mostrar** objeto (pulsando la flecha situada junto a él).</span><span class="sxs-lookup"><span data-stu-id="693ad-405">Within the **Hierarchy** expand the **Time Display** object (by left-clicking the arrow beside it).</span></span> <span data-ttu-id="693ad-406">A continuación, haga clic en el ***cámara principal*** desde el **jerarquía**, de modo que el **Inspector** muestra su información.</span><span class="sxs-lookup"><span data-stu-id="693ad-406">Next click the ***Main Camera*** from within the **Hierarchy**, so that the **Inspector** shows its information.</span></span>
    > 3. <span data-ttu-id="693ad-407">Seleccione el **cámara principal** en el **jerarquía Panel**.</span><span class="sxs-lookup"><span data-stu-id="693ad-407">Select the **Main Camera** in the **Hierarchy Panel**.</span></span> <span data-ttu-id="693ad-408">Arrastre el **fecha** y **tiempo** objetos desde el **jerarquía Panel** a la **texto de fecha** y **texto en tiempo de** ranuras dentro de la **Inspector** de la **cámara principal** en el **ShelfKeeper** componente.</span><span class="sxs-lookup"><span data-stu-id="693ad-408">Drag the **Date** and **Time** objects from the **Hierarchy Panel** to the **Date Text** and **Time Text** slots within the **Inspector** of the **Main Camera** in the **ShelfKeeper** component.</span></span>
    > 4. <span data-ttu-id="693ad-409">Arrastre el **Spawn puntos** desde el **jerarquía Panel** (debajo de la *estante* objeto) a la **3** **elemento**hacen referencia a los destinos por debajo de la **punto Spawn** de matriz, como se muestra en la imagen.</span><span class="sxs-lookup"><span data-stu-id="693ad-409">Drag the **Spawn Points** from the **Hierarchy Panel** (beneath the *Shelf* object) to the **3** **Element** reference targets beneath the **Spawn Point** array, as shown in the image.</span></span>
    > 
    >     ![Crear la clase ShelfKeeper](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a><span data-ttu-id="693ad-411">Capítulo 9: crear la clase ProductPrediction</span><span class="sxs-lookup"><span data-stu-id="693ad-411">Chapter 9 - Create the ProductPrediction class</span></span>

<span data-ttu-id="693ad-412">La siguiente clase que se va a crear es la **ProductPrediction** clase.</span><span class="sxs-lookup"><span data-stu-id="693ad-412">The next class you are going to create is the **ProductPrediction** class.</span></span>

<span data-ttu-id="693ad-413">Esta clase es responsable de:</span><span class="sxs-lookup"><span data-stu-id="693ad-413">This class is responsible for:</span></span>

-   <span data-ttu-id="693ad-414">Consultar el **servicio Machine Learning** instancia, que proporciona la fecha y hora actuales.</span><span class="sxs-lookup"><span data-stu-id="693ad-414">Querying the **Machine Learning Service** instance, providing the current date and time.</span></span>

-   <span data-ttu-id="693ad-415">Deserializar la respuesta JSON en datos utilizables.</span><span class="sxs-lookup"><span data-stu-id="693ad-415">Deserializing the JSON response into usable data.</span></span>

-   <span data-ttu-id="693ad-416">Interpretación de los datos, recuperar los 3 productos recomendados.</span><span class="sxs-lookup"><span data-stu-id="693ad-416">Interpreting the data, retrieving the 3 recommended products.</span></span>

-   <span data-ttu-id="693ad-417">Una llamada a la **ShelfKeeper** métodos para mostrar los datos de la escena de la clase.</span><span class="sxs-lookup"><span data-stu-id="693ad-417">Calling the **ShelfKeeper** class methods to display the data in the Scene.</span></span>

<span data-ttu-id="693ad-418">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="693ad-418">To create this class:</span></span>

1.  <span data-ttu-id="693ad-419">Vaya a la **Scripts** carpeta, en el **Panel proyecto**.</span><span class="sxs-lookup"><span data-stu-id="693ad-419">Go to the **Scripts** folder, in the **Project Panel**.</span></span>

2.  <span data-ttu-id="693ad-420">Haga clic en la carpeta, **crear** > **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="693ad-420">Right-click inside the folder, **Create** > **C\# Script**.</span></span> <span data-ttu-id="693ad-421">Llame al script **ProductPrediction**.</span><span class="sxs-lookup"><span data-stu-id="693ad-421">Call the script **ProductPrediction**.</span></span>

3.  <span data-ttu-id="693ad-422">Haga doble clic en el nuevo **ProductPrediction** script para abrirlo con **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="693ad-422">Double click on the new **ProductPrediction** script to open it with **Visual Studio 2017**.</span></span>

4.  <span data-ttu-id="693ad-423">Si el **modificación de archivo detectada** cuadro de diálogo emergente, haga clic en \***recargar solución**.</span><span class="sxs-lookup"><span data-stu-id="693ad-423">If the **File Modification Detected** dialog pops up, click \***Reload Solution**.</span></span>

5.  <span data-ttu-id="693ad-424">Agregue los siguientes espacios de nombres en la parte superior de la clase ProductPrediction:</span><span class="sxs-lookup"><span data-stu-id="693ad-424">Add the following namespaces to the top of the ProductPrediction class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using System.Linq;
    using Newtonsoft.Json;
    using UnityEngine.Networking;
    using System.Runtime.Serialization;
    using System.Collections;
    ```

6.  <span data-ttu-id="693ad-425">Dentro de la **ProductPrediction** clase insertar los siguientes dos objetos que están compuestos de una serie de clases anidadas.</span><span class="sxs-lookup"><span data-stu-id="693ad-425">Inside the **ProductPrediction** class insert the following two objects which are composed of a number of nested classes.</span></span> <span data-ttu-id="693ad-426">Estas clases se utilizan para serializar y deserializar el JSON para el servicio Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="693ad-426">These classes are used to serialize and deserialize the JSON for the Machine Learning Service.</span></span>

    ```csharp
        /// <summary>
        /// This object represents the Prediction request
        /// It host the day of the year and hour of the day
        /// The product must be left blank when serialising
        /// </summary>
        public class RootObject
        {
            public Inputs Inputs { get; set; }
        }

        public class Inputs
        {
            public Input1 input1 { get; set; }
        }

        public class Input1
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

    ```csharp
        /// <summary>
        /// This object containing the deserialised Prediction result
        /// It host the list of the products
        /// and the likelihood of them being sold at current date and time
        /// </summary>
        public class Prediction
        {
            public Results Results { get; set; }
        }

        public class Results
        {
            public Output1 output1;
        }

        public class Output1
        {
            public string type;
            public Value value;
        }

        public class Value
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

7.  <span data-ttu-id="693ad-427">A continuación, agregue las siguientes variables encima del código anterior (de modo que el JSON relacionados con el código está en la parte inferior de la secuencia de comandos, todos los demás código siguiente y fuera de la forma):</span><span class="sxs-lookup"><span data-stu-id="693ad-427">Then add the following variables above the previous code (so that the JSON related code is at the bottom of the script, below all other code, and out of the way):</span></span>

    ```csharp
        /// <summary>
        /// The 'Primary Key' from your Machine Learning Portal
        /// </summary>
        private string authKey = "-- Insert your service authentication key here --";

        /// <summary>
        /// The 'Request-Response' Service Endpoint from your Machine Learning Portal
        /// </summary>
        private string serviceEndpoint = "-- Insert your service endpoint here --";

        /// <summary>
        /// The Hour as set in Windows
        /// </summary>
        private string thisHour;

        /// <summary>
        /// The Day, as set in Windows
        /// </summary>
        private string thisDay;

        /// <summary>
        /// The Month, as set in Windows
        /// </summary>
        private string thisMonth;

        /// <summary>
        /// The Numeric Day from current Date Conversion
        /// </summary>
        private string dayOfTheYear;

        /// <summary>
        /// Dictionary for holding the first (or default) provided prediction 
        /// from the Machine Learning Experiment
        /// </summary>    
        private Dictionary<string, string> predictionDictionary;

        /// <summary>
        /// List for holding product prediction with name and scores
        /// </summary>
        private List<KeyValuePair<string, double>> keyValueList;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="693ad-428">Asegúrese de que se va a insertar el **clave principal** y **punto de conexión solicitud-respuesta**, desde el Portal de Machine Learning, a continuación las variables.</span><span class="sxs-lookup"><span data-stu-id="693ad-428">Make sure to insert the **primary key** and **request-response endpoint**, from the Machine Learning Portal, into the variables here.</span></span> <span data-ttu-id="693ad-429">Las siguientes imágenes muestran que habría necesitado la clave y el punto de conexión desde.</span><span class="sxs-lookup"><span data-stu-id="693ad-429">The below images show where you would have taken the key and endpoint from.</span></span> 
    >  
    > ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-53-1.png)
    >
    > ![Machine Learning Studio: El experimento](images/AzureLabs-Lab7-53-2.png)

8.  <span data-ttu-id="693ad-432">Inserte este código dentro de la **Start()** método.</span><span class="sxs-lookup"><span data-stu-id="693ad-432">Insert this code within the **Start()** method.</span></span> <span data-ttu-id="693ad-433">El **Start()** método se llama cuando se inicializa la clase:</span><span class="sxs-lookup"><span data-stu-id="693ad-433">The **Start()** method is called when the class initializes:</span></span>

    ```csharp
        void Start()
        {
            // Call to get the current date and time as set in Windows
            GetTodayDateAndTime();

            // Call to set the HOUR in the UI
            ShelfKeeper.instance.SetTime(thisHour);

            // Call to set the DATE in the UI
            ShelfKeeper.instance.SetDate(thisDay, thisMonth);

            // Run the method to Get Predication from Azure Machine Learning
            StartCoroutine(GetPrediction(thisHour, dayOfTheYear));
        }
    ```

9.  <span data-ttu-id="693ad-434">El siguiente es el método que recopila la fecha y hora de Windows y lo convierte en un formato que puede usar nuestro experimento de Machine Learning que se compara con los datos almacenados en la tabla.</span><span class="sxs-lookup"><span data-stu-id="693ad-434">The following is the method that collects the date and time from Windows and converts it into a format that our Machine Learning Experiment can use to compare with the data stored in the table.</span></span>

    ```csharp
        /// <summary>
        /// Get current date and hour
        /// </summary>
        private void GetTodayDateAndTime()
        {
            // Get today date and time
            DateTime todayDate = DateTime.Now;

            // Extrapolate the HOUR
            thisHour = todayDate.Hour.ToString();

            // Extrapolate the DATE
            thisDay = todayDate.Day.ToString();
            thisMonth = todayDate.ToString("MMM");

            // Extrapolate the day of the year
            dayOfTheYear = todayDate.DayOfYear.ToString();
        }
    ```

10. <span data-ttu-id="693ad-435">También puede **eliminar** el **Update()** método puesto que esta clase no lo usará.</span><span class="sxs-lookup"><span data-stu-id="693ad-435">You can **delete** the **Update()** method since this class will not use it.</span></span>

11. <span data-ttu-id="693ad-436">Agregue el siguiente método que se comunican la fecha y hora actuales para el punto de conexión de Machine Learning y recibir una respuesta en formato JSON.</span><span class="sxs-lookup"><span data-stu-id="693ad-436">Add the following method which will communicate the current date and time to the Machine Learning endpoint and receive a response in JSON format.</span></span>

    ```csharp
        private IEnumerator GetPrediction(string timeOfDay, string dayOfYear)
        {
            // Populate the request object 
            // Using current day of the year and hour of the day
            RootObject ro = new RootObject
            {
                Inputs = new Inputs
                {
                    input1 = new Input1
                    {
                        ColumnNames = new List<string>
                        {
                            "day",
                            "hour",
                        "product"
                        },
                        Values = new List<List<string>>()
                    }
                }
            };

            List<string> l = new List<string>
            {
                dayOfYear,
                timeOfDay,
                ""
            };

            ro.Inputs.input1.Values.Add(l);

            Debug.LogFormat("Score request built");

            // Serialise the request
            string json = JsonConvert.SerializeObject(ro);

            using (UnityWebRequest www = UnityWebRequest.Post(serviceEndpoint, "POST"))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(json);
                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + authKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.SetRequestHeader("Accept", "application/json");

                yield return www.SendWebRequest();
                string response = www.downloadHandler.text;

                // Deserialize the response
                DataContractSerializer serializer;
                serializer = new DataContractSerializer(typeof(string));
                DeserialiseJsonResponse(response);
            }
        }
    ```

12. <span data-ttu-id="693ad-437">Agregue el método siguiente, que es responsable de deserializar la respuesta JSON y comunica el resultado de la deserialización para el **ShelfKeeper** clase.</span><span class="sxs-lookup"><span data-stu-id="693ad-437">Add the following method, which is responsible for deserializing the JSON response, and communicating the result of the deserialization to the **ShelfKeeper** class.</span></span> <span data-ttu-id="693ad-438">Este resultado será que los nombres de los tres elementos que se prevé que para vender el máximo partido a la fecha y hora actuales.</span><span class="sxs-lookup"><span data-stu-id="693ad-438">This result will be the names of the three items predicted to sell the most at current date and time.</span></span> <span data-ttu-id="693ad-439">Inserte el código siguiente en el **ProductPrediction** (clase), a continuación el método anterior.</span><span class="sxs-lookup"><span data-stu-id="693ad-439">Insert the code below into the **ProductPrediction** class, below the previous method.</span></span>

    ```csharp
        /// <summary>
        /// Deserialize the response received from the Machine Learning portal
        /// </summary>
        public void DeserialiseJsonResponse(string jsonResponse)
        {
            // Deserialize JSON
            Prediction prediction = JsonConvert.DeserializeObject<Prediction>(jsonResponse);
            predictionDictionary = new Dictionary<string, string>();

            for (int i = 0; i < prediction.Results.output1.value.ColumnNames.Count; i++)
            {
                if (prediction.Results.output1.value.Values[0][i] != null)
                {
                    predictionDictionary.Add(prediction.Results.output1.value.ColumnNames[i], prediction.Results.output1.value.Values[0][i]);
                }
            }

            keyValueList = new List<KeyValuePair<string, double>>();

            // Strip all non-results, by adding only items of interest to the scoreList
            for (int i = 0; i < predictionDictionary.Count; i++)
            {
                KeyValuePair<string, string> pair = predictionDictionary.ElementAt(i);
                if (pair.Key.StartsWith("Scored Probabilities"))
                {
                    // Parse string as double then simplify the string key so to only have the item name
                    double scorefloat = 0f;
                    double.TryParse(pair.Value, out scorefloat);
                    string simplifiedName =
                        pair.Key.Replace("\"", "").Replace("Scored Probabilities for Class", "").Trim();
                    keyValueList.Add(new KeyValuePair<string, double>(simplifiedName, scorefloat));
                }
            }

            // Sort Predictions (results will be lowest to highest)
            keyValueList.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Spawn the top three items, from the keyValueList, which we have sorted
            for (int i = 0; i < 3; i++)
            {
                ShelfKeeper.instance.SpawnProduct(keyValueList[i].Key, i);
            }

            // Clear lists in case of reuse
            keyValueList.Clear();
            predictionDictionary.Clear();
        }
    ```

13. <span data-ttu-id="693ad-440">Guardar **Visual Studio** y regrese a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="693ad-440">Save **Visual Studio** and head back to **Unity**.</span></span>

14. <span data-ttu-id="693ad-441">Arrastre el **ProductPrediction** clase script desde el **Script** carpeta, en el **cámara principal** objeto.</span><span class="sxs-lookup"><span data-stu-id="693ad-441">Drag the **ProductPrediction** class script from the **Script** folder, onto the **Main Camera** object.</span></span>

15. <span data-ttu-id="693ad-442">Guarde la escena y el proyecto **archivo** >  ***Guardar escena* / *archivo***   >  **Guardar proyecto**.</span><span class="sxs-lookup"><span data-stu-id="693ad-442">Save your scene and project **File** > ***Save Scene* / *File*** > **Save Project**.</span></span>

## <a name="chapter-10---build-the-uwp-solution"></a><span data-ttu-id="693ad-443">Capítulo 10: Compile la solución UWP</span><span class="sxs-lookup"><span data-stu-id="693ad-443">Chapter 10 - Build the UWP Solution</span></span>

<span data-ttu-id="693ad-444">Ahora es momento de compilar el proyecto como una solución UWP, para que pueda ejecutarse como una aplicación independiente.</span><span class="sxs-lookup"><span data-stu-id="693ad-444">It is now time to build your project as a UWP solution, so that it can run as a standalone application.</span></span>

<span data-ttu-id="693ad-445">Para compilar:</span><span class="sxs-lookup"><span data-stu-id="693ad-445">To Build:</span></span>

1.  <span data-ttu-id="693ad-446">Guarde la escena actual haciendo clic en **archivo** **guardar escenas**.</span><span class="sxs-lookup"><span data-stu-id="693ad-446">Save the current scene by clicking on **File** **Save Scenes**.</span></span>

2.  <span data-ttu-id="693ad-447">Vaya a **archivo** **configuración de compilación**</span><span class="sxs-lookup"><span data-stu-id="693ad-447">Go to **File** **Build Settings**</span></span>

3.  <span data-ttu-id="693ad-448">Active la casilla denominada **Unity C\# proyectos** (Esto es importante porque permite editar las clases, una vez completada la compilación).</span><span class="sxs-lookup"><span data-stu-id="693ad-448">Check the box called **Unity C\# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

4.  <span data-ttu-id="693ad-449">Haga clic en **agregar escenas abiertos**,</span><span class="sxs-lookup"><span data-stu-id="693ad-449">Click on **Add Open Scenes**,</span></span>

5.  <span data-ttu-id="693ad-450">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="693ad-450">Click **Build**.</span></span>

    ![Compile la solución UWP](images/AzureLabs-Lab7-54.png)

6.  <span data-ttu-id="693ad-452">Se le pedirá que seleccione la carpeta donde desea compilar la solución.</span><span class="sxs-lookup"><span data-stu-id="693ad-452">You will be prompted to select the folder where you want to build the Solution.</span></span>

7.  <span data-ttu-id="693ad-453">Crear un **compilaciones** carpeta y dentro de esa carpeta, cree otra carpeta con un nombre adecuado de su elección.</span><span class="sxs-lookup"><span data-stu-id="693ad-453">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

8.  <span data-ttu-id="693ad-454">Haga clic en la nueva carpeta y, a continuación, haga clic en **seleccionar la carpeta**, para comenzar a la compilación en esa ubicación.</span><span class="sxs-lookup"><span data-stu-id="693ad-454">Click your new folder and then click **Select Folder**, to begin the build at that location.</span></span>

    ![Compile la solución UWP](images/AzureLabs-Lab7-55.png)

    ![Compile la solución UWP](images/AzureLabs-Lab7-56.png)

9.  <span data-ttu-id="693ad-457">Una vez Unity ha finalizado la compilación (puede tardar algún tiempo), se abrirá un **Explorador de archivos** ventana en la ubicación de la compilación (comprobación de la barra de tareas, tal y como es posible que no siempre aparecen por encima de las ventanas, pero le informará de la adición de un nuevo ventana).</span><span class="sxs-lookup"><span data-stu-id="693ad-457">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11---deploy-your-application"></a><span data-ttu-id="693ad-458">Capítulo 11: implementar la aplicación</span><span class="sxs-lookup"><span data-stu-id="693ad-458">Chapter 11 - Deploy your Application</span></span>

<span data-ttu-id="693ad-459">Para implementar la aplicación:</span><span class="sxs-lookup"><span data-stu-id="693ad-459">To deploy your application:</span></span>

1.  <span data-ttu-id="693ad-460">Vaya a la nueva compilación de Unity (la **aplicación** carpeta) y abra el archivo de solución con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="693ad-460">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

2.  <span data-ttu-id="693ad-461">Con Visual Studio abierto, es preciso restaurar los paquetes de NuGet, lo que puede realizarse a través de haciendo clic en la solución MachineLearningLab_Build, desde el Explorador de soluciones (que se encuentra a la derecha de Visual Studio) y, a continuación, haga clic en restaurar paquetes NuGet:</span><span class="sxs-lookup"><span data-stu-id="693ad-461">With Visual Studio open, you need to Restore NuGet Packages, which can be done through right-clicking your MachineLearningLab_Build solution, from the Solution Explorer (found to the right of Visual Studio), and then clicking Restore NuGet Packages:</span></span>

    ![Agregar paquetes de NuGet](images/AzureLabs-Lab7-57.png)

3.  <span data-ttu-id="693ad-463">En, seleccione la configuración de la solución **depurar**.</span><span class="sxs-lookup"><span data-stu-id="693ad-463">In the Solution Configuration select **Debug**.</span></span>

4.  <span data-ttu-id="693ad-464">En la plataforma de soluciones, seleccione **x86**, **máquina Local**.</span><span class="sxs-lookup"><span data-stu-id="693ad-464">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="693ad-465">Para el Microsoft HoloLens, quizá le resulte más fácil establecer esto en *máquina remota*, de modo que no están atados a su equipo.</span><span class="sxs-lookup"><span data-stu-id="693ad-465">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="693ad-466">Sin embargo, necesitará también hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="693ad-466">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="693ad-467">Conocer el **dirección IP** de su HoloLens, que se encuentra dentro de la *configuración > red e Internet > Wi-Fi > Opciones avanzadas*; IPv4 es la dirección que debe usar.</span><span class="sxs-lookup"><span data-stu-id="693ad-467">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="693ad-468">Asegúrese de **modo de programador** es **en**; se encuentra en *configuración > actualización y seguridad > para los desarrolladores*.</span><span class="sxs-lookup"><span data-stu-id="693ad-468">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Agregar paquetes de NuGet](images/AzureLabs-Lab7-58.png)

5.  <span data-ttu-id="693ad-470">Vaya a **menú compilar** y haga clic en **implementar solución** para transferir localmente la aplicación a su equipo.</span><span class="sxs-lookup"><span data-stu-id="693ad-470">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>

6.  <span data-ttu-id="693ad-471">La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas, listos para iniciarse.</span><span class="sxs-lookup"><span data-stu-id="693ad-471">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="693ad-472">Al ejecutar la aplicación de realidad mixta, verá el banco que configuró en la escena de Unity y, desde la inicialización, se recuperarán los datos configurado dentro de Azure.</span><span class="sxs-lookup"><span data-stu-id="693ad-472">When you run the Mixed Reality application, you will see the bench that was set up in your Unity scene, and from initialization, the data you set up within Azure will be fetched.</span></span> <span data-ttu-id="693ad-473">Se va a deserializar los datos dentro de la aplicación y se proporcionará visualmente, como en el banco de tres modelos de los tres primeros resultados de la fecha y hora actuales.</span><span class="sxs-lookup"><span data-stu-id="693ad-473">The data will be deserialized within your application, and the three top results for your current date and time will be provided visually, as three models on the bench.</span></span>


## <a name="your-finished-machine-learning-application"></a><span data-ttu-id="693ad-474">La aplicación finalizada de Machine Learning</span><span class="sxs-lookup"><span data-stu-id="693ad-474">Your finished Machine Learning application</span></span>
 
<span data-ttu-id="693ad-475">Enhorabuena, creó una aplicación de realidad mixta que aprovecha Azure Machine Learning para realizar predicciones de datos y mostrarlos en la escena.</span><span class="sxs-lookup"><span data-stu-id="693ad-475">Congratulations, you built a mixed reality app that leverages the Azure Machine Learning to make data predictions and display it on your scene.</span></span>

![Agregar paquetes de NuGet](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a><span data-ttu-id="693ad-477">Ejercicio</span><span class="sxs-lookup"><span data-stu-id="693ad-477">Exercise</span></span>

<span data-ttu-id="693ad-478">**Ejercicio 1**</span><span class="sxs-lookup"><span data-stu-id="693ad-478">**Exercise 1**</span></span>

<span data-ttu-id="693ad-479">Experimentar con el criterio de ordenación de la aplicación y tener las predicciones de tres inferior aparecen en las estanterías como estos datos potencialmente sería útiles también.</span><span class="sxs-lookup"><span data-stu-id="693ad-479">Experiment with the sort order of your application and have the three bottom predictions appear on the shelf, as this data would potentially be useful also.</span></span>

<span data-ttu-id="693ad-480">**Ejercicio 2**</span><span class="sxs-lookup"><span data-stu-id="693ad-480">**Exercise 2**</span></span>

<span data-ttu-id="693ad-481">Uso de **Azure Tables** rellenar una tabla nueva con información meteorológica y cree un nuevo experimento usando los datos.</span><span class="sxs-lookup"><span data-stu-id="693ad-481">Using **Azure Tables** populate a new table with weather information and create a new experiment using the data.</span></span>
