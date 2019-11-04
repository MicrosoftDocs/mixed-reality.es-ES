---
title: MR y Azure 307-machine learning
description: Complete este curso para aprender a implementar Azure Machine Learning Studio en una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, tutorial, API, machine learning, ml, machine learning Studio, hololens, envolventes, VR
ms.openlocfilehash: c86c592573dd39d926869d8cce6025fa264cc90f
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437925"
---
>[!NOTE]
><span data-ttu-id="49892-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="49892-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="49892-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="49892-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="49892-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="49892-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="49892-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="49892-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="49892-108">Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="49892-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="49892-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.</span><span class="sxs-lookup"><span data-stu-id="49892-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-307-machine-learning"></a><span data-ttu-id="49892-110">MR y Azure 307: machine learning</span><span class="sxs-lookup"><span data-stu-id="49892-110">MR and Azure 307: Machine learning</span></span>

![Inicio del producto final](images/AzureLabs-Lab7-0.png)

<span data-ttu-id="49892-112">En este curso, aprenderá a agregar capacidades de Machine Learning (ML) a una aplicación de realidad mixta mediante Azure Machine Learning Studio.</span><span class="sxs-lookup"><span data-stu-id="49892-112">In this course, you will learn how to add Machine Learning (ML) capabilities to a mixed reality application using Azure Machine Learning Studio.</span></span>

<span data-ttu-id="49892-113">*Azure machine learning Studio* es un servicio de Microsoft, que proporciona a los desarrolladores un gran número de algoritmos de aprendizaje automático, que pueden ayudar con la entrada, la salida, la preparación y la visualización de datos.</span><span class="sxs-lookup"><span data-stu-id="49892-113">*Azure Machine Learning Studio* is a Microsoft service, which provides developers with a large number of machine learning algorithms, which can help with data input, output, preparation, and visualization.</span></span> <span data-ttu-id="49892-114">A partir de estos componentes, es posible desarrollar un experimento de análisis predictivo, realizar una iteración en él y usarlo para entrenar el modelo.</span><span class="sxs-lookup"><span data-stu-id="49892-114">From these components, it is then possible to develop a predictive analytics experiment, iterate on it, and use it to train your model.</span></span> <span data-ttu-id="49892-115">Después del entrenamiento, puede hacer que el modelo sea operativo dentro de la nube de Azure, para que pueda puntuar nuevos datos.</span><span class="sxs-lookup"><span data-stu-id="49892-115">Following training, you can make your model operational within the Azure cloud, so that it can then score new data.</span></span> <span data-ttu-id="49892-116">Para obtener más información, visite la [página Azure machine learning Studio](https://azure.microsoft.com/services/machine-learning-studio/).</span><span class="sxs-lookup"><span data-stu-id="49892-116">For more information, visit the [Azure Machine Learning Studio page](https://azure.microsoft.com/services/machine-learning-studio/).</span></span>

<span data-ttu-id="49892-117">Una vez completado este curso, tendrá una aplicación de auriculares con un casco de realidad mixta y habrá aprendido lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="49892-117">Having completed this course, you will have a mixed reality immersive headset application, and will have learned how do the following:</span></span>

1.  <span data-ttu-id="49892-118">Proporcione una tabla de datos de ventas al portal de *Azure machine learning Studio* y diseñe un algoritmo para predecir las ventas futuras de los artículos más populares.</span><span class="sxs-lookup"><span data-stu-id="49892-118">Provide a table of sales data to the *Azure Machine Learning Studio* portal, and        design an algorithm to predict future sales of popular items.</span></span>
2.  <span data-ttu-id="49892-119">Cree un **proyecto de Unity**, que puede recibir e interpretar los datos de predicción del servicio de ml.</span><span class="sxs-lookup"><span data-stu-id="49892-119">Create a **Unity Project**, which can receive and interpret prediction data from the ML service.</span></span>
3.  <span data-ttu-id="49892-120">Mostrar visualmente los datos de predication en el **proyecto de Unity**a través de la entrega de los artículos de ventas más populares, en una estantería.</span><span class="sxs-lookup"><span data-stu-id="49892-120">Display the predication data visually within the **Unity Project**, through providing the most popular sales items, on a shelf.</span></span>

<span data-ttu-id="49892-121">En su aplicación, depende del modo en que va a integrar los resultados con el diseño.</span><span class="sxs-lookup"><span data-stu-id="49892-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="49892-122">Este curso está diseñado para enseñarle a integrar un servicio de Azure con su proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="49892-122">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="49892-123">Es su trabajo usar el conocimiento que obtiene de este curso para mejorar su aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="49892-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="49892-124">Este curso es un tutorial independiente, que no implica directamente ningún otro laboratorio de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="49892-124">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="49892-125">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="49892-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="49892-126">Recurso</span><span class="sxs-lookup"><span data-stu-id="49892-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="49892-127"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="49892-127"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="49892-128"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="49892-128"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="49892-129">MR y Azure 307: machine learning</span><span class="sxs-lookup"><span data-stu-id="49892-129">MR and Azure 307: Machine learning</span></span></td><td style="text-align: center;"> <span data-ttu-id="49892-130">✔️</span><span class="sxs-lookup"><span data-stu-id="49892-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="49892-131">✔️</span><span class="sxs-lookup"><span data-stu-id="49892-131">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="49892-132">Aunque este curso se centra principalmente en los auriculares de Windows Mixed Reality inmersivo (VR), también puede aplicar lo que aprenda en este curso a Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="49892-132">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="49892-133">A medida que siga con el curso, verá notas sobre cualquier cambio que deba usar para admitir HoloLens.</span><span class="sxs-lookup"><span data-stu-id="49892-133">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="49892-134">Al usar HoloLens, puede observar algún Eco durante la captura de voz.</span><span class="sxs-lookup"><span data-stu-id="49892-134">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="49892-135">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="49892-135">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="49892-136">Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#.</span><span class="sxs-lookup"><span data-stu-id="49892-136">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="49892-137">Tenga en cuenta también que los requisitos previos y las instrucciones escritas dentro de este documento representan lo que se ha probado y comprobado en el momento de la escritura (2018 de mayo).</span><span class="sxs-lookup"><span data-stu-id="49892-137">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="49892-138">Puede usar el software más reciente, como se indica en el [artículo instalar las herramientas](install-the-tools.md), aunque no se debe suponer que la información de este curso se ajusta perfectamente a lo que encontrará en el software más reciente que el que se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="49892-138">You are free to use the latest software, as listed within the [install the tools article](install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="49892-139">Se recomienda el siguiente hardware y software para este curso:</span><span class="sxs-lookup"><span data-stu-id="49892-139">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="49892-140">Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de auriculares envolvente (VR)</span><span class="sxs-lookup"><span data-stu-id="49892-140">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="49892-141">Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="49892-141">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="49892-142">El SDK de Windows 10 más reciente</span><span class="sxs-lookup"><span data-stu-id="49892-142">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="49892-143">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="49892-143">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="49892-144">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="49892-144">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="49892-145">Un [auricular de Windows Mixed Reality inmersivo (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="49892-145">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="49892-146">Acceso a Internet para la configuración de Azure y la recuperación de datos de ML</span><span class="sxs-lookup"><span data-stu-id="49892-146">Internet access for Azure setup and ML data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="49892-147">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="49892-147">Before you start</span></span>

<span data-ttu-id="49892-148">Para evitar que se produzcan problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cerca de la raíz (las rutas de acceso de carpeta largas pueden producir problemas en tiempo de compilación).</span><span class="sxs-lookup"><span data-stu-id="49892-148">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 

## <a name="chapter-1---azure-storage-account-setup"></a><span data-ttu-id="49892-149">Capítulo 1: configuración de la cuenta de Azure Storage</span><span class="sxs-lookup"><span data-stu-id="49892-149">Chapter 1 - Azure Storage Account setup</span></span>

<span data-ttu-id="49892-150">Para usar la API de traductor de Azure, tendrá que configurar una instancia del servicio para que esté disponible para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="49892-150">To use the Azure Translator API, you will need to configure an instance of the service to be made available to your application.</span></span>
1.  <span data-ttu-id="49892-151">Inicie sesión en el [portal de Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="49892-151">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="49892-152">Si aún no tiene una cuenta de Azure, tendrá que crear una.</span><span class="sxs-lookup"><span data-stu-id="49892-152">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="49892-153">Si sigue este tutorial en una situación de aula o de laboratorio, pregunte al instructor o a uno de los Proctors para obtener ayuda para configurar la nueva cuenta.</span><span class="sxs-lookup"><span data-stu-id="49892-153">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="49892-154">Una vez que haya iniciado sesión, haga clic en **cuentas de almacenamiento** en el menú de la izquierda.</span><span class="sxs-lookup"><span data-stu-id="49892-154">Once you are logged in, click on **Storage Accounts** in the left menu.</span></span>

    ![Configuración de Azure Storage cuenta](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > <span data-ttu-id="49892-156">Es posible que la palabra **nuevo** se haya reemplazado por **crear un recurso**, en portales más recientes.</span><span class="sxs-lookup"><span data-stu-id="49892-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="49892-157">En la pestaña **cuentas de almacenamiento** , haga clic en **Agregar**.</span><span class="sxs-lookup"><span data-stu-id="49892-157">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Configuración de Azure Storage cuenta](images/AzureLabs-Lab7-2.png)

4.  <span data-ttu-id="49892-159">En el panel **crear cuenta de almacenamiento** :</span><span class="sxs-lookup"><span data-stu-id="49892-159">In the **Create Storage Account** panel:</span></span>

    1.  <span data-ttu-id="49892-160">Inserte un **nombre** para la cuenta. tenga en cuenta que este campo solo acepta números y letras minúsculas.</span><span class="sxs-lookup"><span data-stu-id="49892-160">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>
    2.  <span data-ttu-id="49892-161">En **modelo de implementación,** seleccione **Resource Manager**.</span><span class="sxs-lookup"><span data-stu-id="49892-161">For **Deployment model,** select **Resource manager**.</span></span>
    3.  <span data-ttu-id="49892-162">En **tipo de cuenta**, seleccione **almacenamiento (uso general V1)** .</span><span class="sxs-lookup"><span data-stu-id="49892-162">For **Account kind**, select **Storage (general purpose v1)**.</span></span>
    4.  <span data-ttu-id="49892-163">En **rendimiento**, seleccione **estándar**.</span><span class="sxs-lookup"><span data-stu-id="49892-163">For **Performance**, select **Standard**.</span></span>
    5.  <span data-ttu-id="49892-164">En **replicación** , seleccione **almacenamiento con redundancia geográfica con acceso de lectura (RA-grs)** .</span><span class="sxs-lookup"><span data-stu-id="49892-164">For **Replication** select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>
    6.  <span data-ttu-id="49892-165">Deje la **transferencia segura requerida** como **deshabilitada**.</span><span class="sxs-lookup"><span data-stu-id="49892-165">Leave **Secure transfer required** as **Disabled**.</span></span>
    7.  <span data-ttu-id="49892-166">Seleccione una **suscripción**.</span><span class="sxs-lookup"><span data-stu-id="49892-166">Select a **Subscription**.</span></span>
    4. <span data-ttu-id="49892-167">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="49892-167">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="49892-168">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="49892-168">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="49892-169">Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común).</span><span class="sxs-lookup"><span data-stu-id="49892-169">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="49892-170">Si desea leer más información sobre los grupos de recursos de Azure, [visite el artículo sobre el grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="49892-170">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>
    
    5.  <span data-ttu-id="49892-171">Determine la **Ubicación** del grupo de recursos (si va a crear un nuevo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="49892-171">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="49892-172">Idealmente, la ubicación estará en la región donde se ejecutará la aplicación.</span><span class="sxs-lookup"><span data-stu-id="49892-172">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="49892-173">Algunos recursos de Azure solo están disponibles en determinadas regiones.</span><span class="sxs-lookup"><span data-stu-id="49892-173">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="49892-174">También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.</span><span class="sxs-lookup"><span data-stu-id="49892-174">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Configuración de Azure Storage cuenta](images/AzureLabs-Lab7-3.png)

6.  <span data-ttu-id="49892-176">Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="49892-176">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="49892-177">Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="49892-177">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Configuración de Azure Storage cuenta](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio"></a><span data-ttu-id="49892-179">Capítulo 2: el Azure Machine Learning Studio</span><span class="sxs-lookup"><span data-stu-id="49892-179">Chapter 2 - The Azure Machine Learning Studio</span></span>

<span data-ttu-id="49892-180">Para usar el *Azure machine learning*, deberá configurar una instancia del servicio machine learning para que esté disponible para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="49892-180">To use the *Azure Machine Learning*, you will need to configure an instance of the Machine Learning service to be made available to your application.</span></span>

1.  <span data-ttu-id="49892-181">En Azure portal, haga clic en **nuevo** en la esquina superior izquierda y busque **machine learning Studio área de trabajo**, presione **entrar**.</span><span class="sxs-lookup"><span data-stu-id="49892-181">In the Azure Portal, click on **New** in the top left corner, and search for **Machine Learning Studio Workspace**, press **Enter**.</span></span>

    ![El Azure Machine Learning Studio](images/AzureLabs-Lab7-5.png)

2.  <span data-ttu-id="49892-183">La nueva página proporcionará una descripción de la **machine learning Studio** servicio del área de trabajo.</span><span class="sxs-lookup"><span data-stu-id="49892-183">The new page will provide a description of the **Machine Learning Studio Workspace**  service.</span></span> <span data-ttu-id="49892-184">En la parte inferior izquierda de este mensaje, haga clic en el botón **crear** para crear una asociación con este servicio.</span><span class="sxs-lookup"><span data-stu-id="49892-184">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

3.  <span data-ttu-id="49892-185">Una vez que haya hecho clic en **crear**, aparecerá un panel donde debe proporcionar algunos detalles sobre el nuevo servicio de **machine learning Studio**:</span><span class="sxs-lookup"><span data-stu-id="49892-185">Once you have clicked on **Create**, a panel will appear where you need to provide some details about your new **Machine Learning Studio service**:</span></span>

    1.  <span data-ttu-id="49892-186">Inserte el **nombre de área de trabajo** que desee para esta instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="49892-186">Insert your desired **Workspace name** for this service instance.</span></span>

    2.  <span data-ttu-id="49892-187">Seleccione una **suscripción**.</span><span class="sxs-lookup"><span data-stu-id="49892-187">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="49892-188">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="49892-188">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="49892-189">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="49892-189">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="49892-190">Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común).</span><span class="sxs-lookup"><span data-stu-id="49892-190">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="49892-191">Si desea leer más información sobre los grupos de recursos de Azure, [visite el artículo sobre el grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="49892-191">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="49892-192">Determine la **Ubicación** del grupo de recursos (si va a crear un nuevo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="49892-192">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="49892-193">Idealmente, la ubicación estará en la región donde se ejecutará la aplicación.</span><span class="sxs-lookup"><span data-stu-id="49892-193">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="49892-194">Algunos recursos de Azure solo están disponibles en determinadas regiones.</span><span class="sxs-lookup"><span data-stu-id="49892-194">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="49892-195">Debe usar el mismo grupo de recursos que utilizó para crear el Azure Storage en el capítulo anterior.</span><span class="sxs-lookup"><span data-stu-id="49892-195">You should use the same resource group that you used for creating the Azure Storage in the previous Chapter.</span></span>

    5.  <span data-ttu-id="49892-196">En la sección **cuenta de almacenamiento** , haga clic en **usar existente**, haga clic en el menú desplegable y, desde allí, haga clic en la **cuenta de almacenamiento** que creó en el último capítulo.</span><span class="sxs-lookup"><span data-stu-id="49892-196">For the **Storage account** section, click **Use existing**, then click the dropdown menu, and from there, click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="49892-197">Seleccione el **plan de tarifa del área de trabajo** adecuado en el menú desplegable.</span><span class="sxs-lookup"><span data-stu-id="49892-197">Select the appropriate **Workspace pricing tier** for you, from the dropdown menu.</span></span>

    7.  <span data-ttu-id="49892-198">En la sección **plan de servicio Web** , haga clic en **crear** **nuevo y** , a continuación, inserte un nombre en el campo de texto.</span><span class="sxs-lookup"><span data-stu-id="49892-198">Within the **Web service plan** section, click **Create** **new,** then insert a name for it in the text field.</span></span>

    8.  <span data-ttu-id="49892-199">En la sección **nivel de precios del plan de servicio Web** , seleccione el nivel de precios que prefiera.</span><span class="sxs-lookup"><span data-stu-id="49892-199">From the **Web service plan pricing tier** section, select the price tier of your choice.</span></span> <span data-ttu-id="49892-200">Un nivel de prueba de desarrollo denominado **DEVTEST Standard** debe estar disponible sin cargo alguno.</span><span class="sxs-lookup"><span data-stu-id="49892-200">A development testing tier called **DEVTEST Standard** should be available to you at no charge.</span></span>

    9.  <span data-ttu-id="49892-201">También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.</span><span class="sxs-lookup"><span data-stu-id="49892-201">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    10. <span data-ttu-id="49892-202">Haz clic en **Crear**.</span><span class="sxs-lookup"><span data-stu-id="49892-202">Click **Create**.</span></span>

        ![El Azure Machine Learning Studio](images/AzureLabs-Lab7-6.png)

4.  <span data-ttu-id="49892-204">Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="49892-204">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="49892-205">Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="49892-205">A notification will appear in the portal once the Service instance is created.</span></span>

    ![El Azure Machine Learning Studio](images/AzureLabs-Lab7-7.png)

6.  <span data-ttu-id="49892-207">Haga clic en la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="49892-207">Click on the notification to explore your new Service instance.</span></span>

    ![El Azure Machine Learning Studio](images/AzureLabs-Lab7-8.png)

7.  <span data-ttu-id="49892-209">Haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="49892-209">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="49892-210">En la página que se muestra, en la sección **vínculos adicionales** , haga clic en **iniciar machine learning Studio**, que dirigirá el explorador al portal de **machine learning Studio** .</span><span class="sxs-lookup"><span data-stu-id="49892-210">In the page displayed, under the **Additional Links** section, click **Launch Machine Learning Studio**, which will direct your browser to the **Machine Learning Studio** portal.</span></span>

    ![El Azure Machine Learning Studio](images/AzureLabs-Lab7-9.png)

9.  <span data-ttu-id="49892-212">Use el botón **iniciar sesión** , en la parte superior derecha o en el centro, para iniciar sesión en el machine learning Studio.</span><span class="sxs-lookup"><span data-stu-id="49892-212">Use the **Sign In** button, at the top right or in the center, to log into your Machine Learning Studio.</span></span>

    ![El Azure Machine Learning Studio](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-dataset-setup"></a><span data-ttu-id="49892-214">Capítulo 3: configuración Machine Learning Studio del conjunto de</span><span class="sxs-lookup"><span data-stu-id="49892-214">Chapter 3 - The Machine Learning Studio: Dataset setup</span></span>

<span data-ttu-id="49892-215">Una de las formas en que Machine Learning funcionan los algoritmos es analizar los datos existentes y, a continuación, intentar predecir resultados futuros basados en el conjunto de datos existente.</span><span class="sxs-lookup"><span data-stu-id="49892-215">One of the ways Machine Learning algorithms work is by analyzing existing data and then attempting to predict future results based on the existing data set.</span></span> <span data-ttu-id="49892-216">Por lo general, esto significa que los datos más existentes que tenga, mejor será el algoritmo para predecir resultados futuros.</span><span class="sxs-lookup"><span data-stu-id="49892-216">This generally means that the more existing data you have, the better the algorithm will be at predicting future results.</span></span>

<span data-ttu-id="49892-217">Se le proporciona una tabla de ejemplo, para este curso, denominada [ProductsTableCSV, que se puede descargar aquí](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span><span class="sxs-lookup"><span data-stu-id="49892-217">A sample table is provided to you, for this course, called [ProductsTableCSV and can be downloaded here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="49892-218">El archivo. zip anterior contiene **ProductsTableCSV** y **. unitypackage Tools**, que necesitará en el [capítulo 6](#chapter-6---importing-the-mlproducts-unity-package).</span><span class="sxs-lookup"><span data-stu-id="49892-218">The above .zip file contains both the **ProductsTableCSV** and the **.unitypackage**, which you will need in [Chapter 6](#chapter-6---importing-the-mlproducts-unity-package).</span></span> <span data-ttu-id="49892-219">Este paquete también se proporciona en ese capítulo, aunque sea independiente del archivo CSV.</span><span class="sxs-lookup"><span data-stu-id="49892-219">This package is also provided within that Chapter, though separate to the csv file.</span></span>

<span data-ttu-id="49892-220">Este conjunto de datos de ejemplo contiene un registro de los objetos que mejor se venden cada hora de cada día del año 2017.</span><span class="sxs-lookup"><span data-stu-id="49892-220">This sample data set contains a record of the best-selling objects at every hour of each day of the year 2017.</span></span>
        
![La Machine Learning Studio: configuración del conjunto de](images/AzureLabs-Lab7-11.png)

<span data-ttu-id="49892-222">Por ejemplo, en el día 1 de 2017, a la 13:00 (hora 13), el artículo de mejor venta era Salt y pimiento.</span><span class="sxs-lookup"><span data-stu-id="49892-222">For example, on day 1 of 2017, at 1pm (hour 13), the best-selling item was salt and pepper.</span></span>

<span data-ttu-id="49892-223">Esta tabla de ejemplo contiene 9998 entradas.</span><span class="sxs-lookup"><span data-stu-id="49892-223">This sample table contains 9998 entries.</span></span>

1.  <span data-ttu-id="49892-224">Vuelva al portal de **machine learning Studio** y agregue esta tabla como un **conjunto** de datos para los ml.</span><span class="sxs-lookup"><span data-stu-id="49892-224">Head back to the **Machine Learning Studio** portal, and add this table as a **Dataset** for your ML.</span></span> <span data-ttu-id="49892-225">Para ello, haga clic en el botón **+ nuevo** en la esquina inferior izquierda de la pantalla.</span><span class="sxs-lookup"><span data-stu-id="49892-225">Do this by clicking the **+ New** button in the bottom left corner of the screen.</span></span>

    ![La Machine Learning Studio: configuración del conjunto de](images/AzureLabs-Lab7-12.png)

2.  <span data-ttu-id="49892-227">Una sección aparecerá en la parte inferior y, dentro de ella, en el panel de navegación de la izquierda.</span><span class="sxs-lookup"><span data-stu-id="49892-227">A section will come up from the bottom, and within that there is navigation panel on the left.</span></span> <span data-ttu-id="49892-228">Haga clic en **conjunto**de archivos y, a la derecha de, **desde archivo local**.</span><span class="sxs-lookup"><span data-stu-id="49892-228">Click **Dataset**, then to the right of that, **From Local File**.</span></span>

    ![La Machine Learning Studio: configuración del conjunto de](images/AzureLabs-Lab7-13.png)

3.  <span data-ttu-id="49892-230">Cargue el nuevo **conjunto** de elementos siguiendo estos pasos:</span><span class="sxs-lookup"><span data-stu-id="49892-230">Upload the new **Dataset** by following these steps:</span></span>

    1. <span data-ttu-id="49892-231">Aparecerá la ventana cargar, donde puede examinar el disco duro para **Ver** el nuevo conjunto de</span><span class="sxs-lookup"><span data-stu-id="49892-231">The upload window will appear, where you can **Browse** your hard drive for the new dataset.</span></span>

        ![La Machine Learning Studio: configuración del conjunto de](images/AzureLabs-Lab7-14.png)

    2.  <span data-ttu-id="49892-233">Una vez seleccionado, y de nuevo en la ventana de carga, deje la casilla sin marcar.</span><span class="sxs-lookup"><span data-stu-id="49892-233">Once selected, and back in the upload window, leave the checkbox unticked.</span></span>

    3.  <span data-ttu-id="49892-234">En el campo de texto que aparece a continuación, escriba **ProductsTableCSV. csv** como el nombre del conjunto de nombres (aunque debe agregarse automáticamente).</span><span class="sxs-lookup"><span data-stu-id="49892-234">In the text field below, enter **ProductsTableCSV.csv** as the name for the dataset (though should automatically be added).</span></span>

    4.  <span data-ttu-id="49892-235">En el menú desplegable de **tipo**, seleccione **archivo CSV genérico con un encabezado (. csv)** .</span><span class="sxs-lookup"><span data-stu-id="49892-235">Using the dropdown menu for **Type**, select **Generic CSV File with a header (.csv)**.</span></span>

    5.  <span data-ttu-id="49892-236">Presione la marca de verificación en la parte inferior derecha de la ventana de carga y se cargará el **conjunto** de resultados.</span><span class="sxs-lookup"><span data-stu-id="49892-236">Press the tick in the bottom right of the upload window, and your **Dataset** will be uploaded.</span></span>

## <a name="chapter-4---the-machine-learning-studio-the-experiment"></a><span data-ttu-id="49892-237">Capítulo 4: el Machine Learning Studio: el experimento</span><span class="sxs-lookup"><span data-stu-id="49892-237">Chapter 4 - The Machine Learning Studio: The Experiment</span></span>

<span data-ttu-id="49892-238">Antes de poder compilar el sistema de aprendizaje automático, deberá compilar un experimento para validar su teoría sobre los datos.</span><span class="sxs-lookup"><span data-stu-id="49892-238">Before you can build your machine learning system, you will need to build an experiment, to validate your theory about your data.</span></span> <span data-ttu-id="49892-239">Con los resultados, sabrá si necesita más datos o si no hay ninguna correlación entre los datos y un resultado posible.</span><span class="sxs-lookup"><span data-stu-id="49892-239">With the results, you will know whether you need more data, or if there is no correlation between the data and a possible outcome.</span></span>

<span data-ttu-id="49892-240">Para empezar a crear un experimento:</span><span class="sxs-lookup"><span data-stu-id="49892-240">To start creating an experiment:</span></span>

1.  <span data-ttu-id="49892-241">Haga **clic de nuevo** en el botón **+ nuevo** situado en la parte inferior izquierda de la página y, a continuación, haga clic en experimento > **experimento en blanco**.</span><span class="sxs-lookup"><span data-stu-id="49892-241">Click again on the **+ New** button on the bottom left of the page, then click on **Experiment** > **Blank Experiment**.</span></span>

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-15.png)

2.  <span data-ttu-id="49892-243">Se mostrará una nueva página con un experimento en blanco:</span><span class="sxs-lookup"><span data-stu-id="49892-243">A new page will be displayed with a blank Experiment:</span></span>

3.  <span data-ttu-id="49892-244">En el panel de la izquierda, expanda **conjuntos de valores guardados** > **mis conjuntos de valores** y arrastre el **ProductsTableCSV** al **lienzo del experimento**.</span><span class="sxs-lookup"><span data-stu-id="49892-244">From the panel on the left expand **Saved Datasets** > **My Datasets** and drag the  **ProductsTableCSV** on to the **Experiment Canvas**.</span></span>

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-16.png)

4.  <span data-ttu-id="49892-246">En el panel de la izquierda, expanda **transformación de datos** > **ejemplo y dividir**.</span><span class="sxs-lookup"><span data-stu-id="49892-246">In the panel on the left, expand **Data Transformation** > **Sample and Split**.</span></span> <span data-ttu-id="49892-247">A continuación, arrastre el elemento **Split Data** al **lienzo del experimento**.</span><span class="sxs-lookup"><span data-stu-id="49892-247">Then drag the **Split Data** item in to the **Experiment Canvas**.</span></span> <span data-ttu-id="49892-248">El elemento dividir datos dividirá el conjunto de datos en dos partes.</span><span class="sxs-lookup"><span data-stu-id="49892-248">The Split Data item will split the data set into two parts.</span></span> <span data-ttu-id="49892-249">Una parte que se utilizará para entrenar el algoritmo de aprendizaje automático.</span><span class="sxs-lookup"><span data-stu-id="49892-249">One part you will use for training the machine learning algorithm.</span></span> <span data-ttu-id="49892-250">La segunda parte se usará para evaluar la precisión del algoritmo generado.</span><span class="sxs-lookup"><span data-stu-id="49892-250">The second part will be used to evaluate the accuracy of the algorithm generated.</span></span>

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-17.png)

5.  <span data-ttu-id="49892-252">En el panel derecho (mientras está seleccionado el elemento dividir datos en el lienzo), edite la **fracción de filas del primer conjunto de** datos de salida a **0,7**.</span><span class="sxs-lookup"><span data-stu-id="49892-252">In the right panel (while the Split Data item on the canvas is selected), edit the **Fraction of rows in the first output dataset** to **0.7**.</span></span> <span data-ttu-id="49892-253">Esto dividirá los datos en dos partes, la primera parte será del 70% de los datos y la segunda parte será el 30% restante.</span><span class="sxs-lookup"><span data-stu-id="49892-253">This will split the data into two parts, the first part will be 70% of the data, and the second part will be the remaining 30%.</span></span> <span data-ttu-id="49892-254">Para asegurarse de que los datos se dividen de forma aleatoria, asegúrese de que la casilla **División aleatoria** permanece activada.</span><span class="sxs-lookup"><span data-stu-id="49892-254">To ensure that the data is split randomly, make sure the **Randomized split** checkbox remains checked.</span></span>

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-18.png)

6.  <span data-ttu-id="49892-256">Arrastre una conexión desde la base del elemento **ProductsTableCSV** del lienzo hasta la parte superior del elemento de datos dividido.</span><span class="sxs-lookup"><span data-stu-id="49892-256">Drag a connection from the base of the **ProductsTableCSV** item on the canvas to the top of the Split Data item.</span></span> <span data-ttu-id="49892-257">Esto conectará los elementos y enviará la salida del conjunto de datos **ProductsTableCSV** (los datos) a la entrada de datos divididos.</span><span class="sxs-lookup"><span data-stu-id="49892-257">This will connect the items and send the **ProductsTableCSV** dataset output (the data) to the Split Data input.</span></span>  

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-19.png)

7.  <span data-ttu-id="49892-259">En el panel **experimentos** en el lado izquierdo, expanda **machine learning** > **entrenar**.</span><span class="sxs-lookup"><span data-stu-id="49892-259">In the **Experiments** panel on the left side, expand **Machine Learning** > **Train**.</span></span> <span data-ttu-id="49892-260">Arrastre el elemento **entrenar modelo** hacia el lienzo del experimento.</span><span class="sxs-lookup"><span data-stu-id="49892-260">Drag the **Train Model** item out in to the Experiment canvas.</span></span> <span data-ttu-id="49892-261">El lienzo debería tener el mismo aspecto que el siguiente.</span><span class="sxs-lookup"><span data-stu-id="49892-261">Your canvas should look the same as the below.</span></span>

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-20.png)

8.  <span data-ttu-id="49892-263">En la ***parte inferior izquierda*** del elemento **dividir datos** , arrastre una conexión a la **parte superior derecha** del elemento **entrenar modelo** .</span><span class="sxs-lookup"><span data-stu-id="49892-263">From the ***bottom left*** of the **Split Data** item drag a connection to the **top right** of the **Train Model** item.</span></span> <span data-ttu-id="49892-264">El modelo de entrenamiento usará la primera división del 70% del conjunto de filas para entrenar el algoritmo.</span><span class="sxs-lookup"><span data-stu-id="49892-264">The first 70% split from the dataset will be used by the Train Model to train the algorithm.</span></span>

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-21.png)

9.  <span data-ttu-id="49892-266">Seleccione el elemento **entrenar modelo** en el lienzo y, en el panel **propiedades** (en el lado derecho de la ventana del explorador), haga clic en el botón **iniciar selector de columnas** .</span><span class="sxs-lookup"><span data-stu-id="49892-266">Select the **Train Model** item on the canvas, and in the **Properties** panel (on the right-hand side of your browser window) click the **Launch column selector** button.</span></span>

10. <span data-ttu-id="49892-267">En el cuadro de texto escriba **Product** y, a continuación, presione **entrar**; *Product* se establecerá como una columna para entrenar las predicciones.</span><span class="sxs-lookup"><span data-stu-id="49892-267">In the text box type **product** and then press **Enter**, *product* will be set as a column to train predictions.</span></span> <span data-ttu-id="49892-268">Después, haga clic en la **marca** de verificación en la esquina inferior derecha para cerrar el cuadro de diálogo de selección.</span><span class="sxs-lookup"><span data-stu-id="49892-268">Following this, click on the **tick** in the bottom-right corner to close the selection dialog.</span></span>

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-22.png)

11. <span data-ttu-id="49892-270">Va a entrenar un algoritmo de **regresión logística multiclase** para predecir el **producto** más vendido en función de la hora del día y la fecha.</span><span class="sxs-lookup"><span data-stu-id="49892-270">You are going to train a **Multiclass Logistic Regression** algorithm to predict the most sold **product** based on the hour of the day and the date.</span></span> <span data-ttu-id="49892-271">Sin embargo, queda fuera del ámbito de este documento la explicación de los detalles de los distintos algoritmos proporcionados por Azure Machine Learning Studio. puede encontrar más información en la hoja de referencia rápida de [algoritmos de machine learning](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span><span class="sxs-lookup"><span data-stu-id="49892-271">It is beyond the scope of this document to explain the details of the different algorithms provided by the Azure Machine Learning studio, though, you can find out more from the [Machine Learning Algorithm Cheat Sheet](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span></span>

12. <span data-ttu-id="49892-272">En el panel elementos del experimento de la izquierda, expanda **Machine Learning** > **inicializar modelo** > **clasificación**y arrastre el elemento **regresión logística multiclase** al lienzo del experimento.</span><span class="sxs-lookup"><span data-stu-id="49892-272">From the experiment items panel on the left, expand **Machine Learning** > **Initialize Model** > **Classification**, and drag the **Multiclass Logistic Regression** item on to the experiment canvas.</span></span>

13. <span data-ttu-id="49892-273">Conecte la salida, desde la parte inferior de la **regresión logística multiclase**, a la entrada superior izquierda del elemento **entrenar modelo** .</span><span class="sxs-lookup"><span data-stu-id="49892-273">Connect the output, from the bottom of the **Multiclass Logistic Regression**, to the top-left input of the **Train Model** item.</span></span>

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-23.png)

14. <span data-ttu-id="49892-275">En la lista de elementos del experimento en el panel de la izquierda, expanda **Machine Learning** > **puntuación**y arrastre el elemento **puntuar modelo** al lienzo.</span><span class="sxs-lookup"><span data-stu-id="49892-275">In list of experiment items in the panel on the left, expand **Machine Learning** > **Score**, and drag the **Score Model** item on to the canvas.</span></span>

15. <span data-ttu-id="49892-276">Conecte la salida, desde la parte inferior del **modelo de tren**, a la entrada superior izquierda del **modelo de puntuación**.</span><span class="sxs-lookup"><span data-stu-id="49892-276">Connect the output, from the bottom of the **Train Model**, to the top-left input of the **Score Model**.</span></span>

16. <span data-ttu-id="49892-277">Conecte la salida inferior derecha de **Split Data (dividir datos**) a la entrada superior derecha del elemento **score Model (puntuar modelo** ).</span><span class="sxs-lookup"><span data-stu-id="49892-277">Connect the bottom-right output from **Split Data**, to the top-right input of the **Score Model** item.</span></span>

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-24.png)

17. <span data-ttu-id="49892-279">En la lista de elementos del **experimento** en el panel de la izquierda, expanda **machine learning** > **evaluar**y arrastre el elemento **Evaluar modelo** al lienzo.</span><span class="sxs-lookup"><span data-stu-id="49892-279">In the list of **Experiment** items in the panel on the left, expand **Machine Learning** > **Evaluate**, and drag the **Evaluate Model** item onto the canvas.</span></span>

18. <span data-ttu-id="49892-280">Conecte el resultado del **modelo de puntuación** a la entrada superior izquierda del modelo de **evaluación**.</span><span class="sxs-lookup"><span data-stu-id="49892-280">Connect the output from the **Score Model** to the top-left input of the **Evaluate Model**.</span></span>

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-25.png)

19. <span data-ttu-id="49892-282">Ha creado su primer experimento Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="49892-282">You have built your first Machine Learning Experiment.</span></span> <span data-ttu-id="49892-283">Ahora puede guardar y ejecutar el experimento.</span><span class="sxs-lookup"><span data-stu-id="49892-283">You can now save and run the experiment.</span></span> <span data-ttu-id="49892-284">En el menú de la parte inferior de la página, haga clic en el botón **Guardar** para guardar el experimento y, a continuación, haga clic en **Ejecutar** para iniciar el experimento.</span><span class="sxs-lookup"><span data-stu-id="49892-284">In the menu at the bottom of the page, click on the **Save** button to save your experiment and then click **Run** to the start the experiment.</span></span>

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-26.png)

20. <span data-ttu-id="49892-286">Puede ver el **Estado** del experimento en la parte superior derecha del lienzo.</span><span class="sxs-lookup"><span data-stu-id="49892-286">You can see the **status** of the experiment in the top-right of the canvas.</span></span> <span data-ttu-id="49892-287">Espere unos instantes hasta que finalice el experimento.</span><span class="sxs-lookup"><span data-stu-id="49892-287">Wait a few moments for the experiment to finish.</span></span>

    > <span data-ttu-id="49892-288">Si tiene un conjunto de datos grande (mundo real), es probable que el experimento tarde horas en ejecutarse.</span><span class="sxs-lookup"><span data-stu-id="49892-288">If you have a big (real world) dataset it is likely that the experiment could take hours to run.</span></span>

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-27.png)

21. <span data-ttu-id="49892-290">Haga clic con el botón derecho en el elemento **Evaluar modelo** del lienzo y, en el menú contextual, mantenga el mouse sobre **los resultados**de la evaluación y seleccione **visualizar**.</span><span class="sxs-lookup"><span data-stu-id="49892-290">Right click on the **Evaluate Model** item in the canvas and from the context menu hover the mouse over **Evaluation Results**, then select **Visualize**.</span></span>

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-28.png)

22. <span data-ttu-id="49892-292">Los resultados de la evaluación se mostrarán mostrando los resultados previstos frente a los resultados reales.</span><span class="sxs-lookup"><span data-stu-id="49892-292">The evaluation results will be displayed showing the predicted outcomes versus the actual outcomes.</span></span> <span data-ttu-id="49892-293">Esto utiliza el 30% del conjunto de filas original, que se dividió anteriormente, para evaluar el modelo.</span><span class="sxs-lookup"><span data-stu-id="49892-293">This uses the 30% of the original dataset, that was split earlier, for evaluating the model.</span></span> <span data-ttu-id="49892-294">Puede ver que los resultados no son excelentes; lo ideal es que el número más alto de cada fila sea el elemento resaltado en las columnas.</span><span class="sxs-lookup"><span data-stu-id="49892-294">You can see the results are not great, ideally you would have the highest number in each row be the highlighted item in the columns.</span></span>

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-29.png)

23. <span data-ttu-id="49892-296">Cierre los **resultados**.</span><span class="sxs-lookup"><span data-stu-id="49892-296">Close the **Results**.</span></span>

24. <span data-ttu-id="49892-297">Para usar el modelo de Machine Learning recién entrenado, debe exponerlo como un **servicio Web**.</span><span class="sxs-lookup"><span data-stu-id="49892-297">To use your newly trained Machine Learning model you need to expose it as a **Web Service**.</span></span> <span data-ttu-id="49892-298">Para ello, haga clic en el elemento de menú **configurar servicio Web** en el menú de la parte inferior de la página y haga clic en **servicio Web predictivo**.</span><span class="sxs-lookup"><span data-stu-id="49892-298">To do this, click on the **Set Up Web Service** menu item in the menu at the bottom of the page, and click on **Predictive Web Service**.</span></span>

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-30.png)

25. <span data-ttu-id="49892-300">Se creará una nueva pestaña y se combinará el modelo de entrenamiento para crear el nuevo servicio Web.</span><span class="sxs-lookup"><span data-stu-id="49892-300">A new tab will be created, and the train model merged to create the new web service.</span></span> 

26. <span data-ttu-id="49892-301">En el menú de la parte inferior de la página, haga clic en **Guardar**y, a continuación, haga clic en **Ejecutar**.</span><span class="sxs-lookup"><span data-stu-id="49892-301">In the menu at the bottom of the page click **Save**, then click **Run**.</span></span> <span data-ttu-id="49892-302">Verá el estado actualizado en la esquina superior derecha del lienzo del experimento.</span><span class="sxs-lookup"><span data-stu-id="49892-302">You will see the status updated in the top-right corner of the experiment canvas.</span></span>

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-31.png)

27. <span data-ttu-id="49892-304">Una vez que haya finalizado la ejecución, aparecerá un botón **implementar servicio Web** en la parte inferior de la página.</span><span class="sxs-lookup"><span data-stu-id="49892-304">Once it has finished running, a **Deploy Web Service** button will appear at the bottom of the page.</span></span> <span data-ttu-id="49892-305">Está listo para implementar el servicio Web.</span><span class="sxs-lookup"><span data-stu-id="49892-305">You are ready to deploy the web service.</span></span> <span data-ttu-id="49892-306">Haga clic en **implementar servicio Web** (clásico) en el menú de la parte inferior de la página.</span><span class="sxs-lookup"><span data-stu-id="49892-306">Click **Deploy Web Service** (Classic) in the menu at the bottom of the page.</span></span>

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-32.png)

    > <span data-ttu-id="49892-308">Es posible que el explorador le solicite que permita un elemento emergente, que debe **permitir**, aunque es posible que tenga que volver a presionar **implementar servicio Web** si no se muestra la página implementar.</span><span class="sxs-lookup"><span data-stu-id="49892-308">Your browser may prompt to allow a pop-up, which you should **allow**, though you may need to press **Deploy Web Service** again, if the deploy page does not show.</span></span> 

28. <span data-ttu-id="49892-309">Una vez creado el experimento, se le redirigirá a una página de **Panel** en la que se mostrará la **clave de API** .</span><span class="sxs-lookup"><span data-stu-id="49892-309">Once the Experiment has been created you will be redirected to a **Dashboard** page where you will have your **API Key** displayed.</span></span> <span data-ttu-id="49892-310">Cópielo en un bloc de notas por el momento, lo necesitará en el código muy pronto.</span><span class="sxs-lookup"><span data-stu-id="49892-310">Copy it into a notepad for the moment, you will need it in your code very soon.</span></span> <span data-ttu-id="49892-311">Una vez que haya anotado la clave de API, haga clic en el botón **solicitud/respuesta** en la sección **punto de conexión predeterminado** debajo de la clave.</span><span class="sxs-lookup"><span data-stu-id="49892-311">Once you have noted your API Key, click on the **REQUEST/RESPONSE** button in the **Default Endpoint** section underneath the Key.</span></span>

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > <span data-ttu-id="49892-313">Si hace clic en probar en esta página, podrá especificar los datos de entrada y ver la salida.</span><span class="sxs-lookup"><span data-stu-id="49892-313">If you click Test in this page, you will be able to enter input data and view the output.</span></span> <span data-ttu-id="49892-314">Especifique el **día** y la **hora**.</span><span class="sxs-lookup"><span data-stu-id="49892-314">Enter the **day** and **hour**.</span></span> <span data-ttu-id="49892-315">Deje la entrada del **producto** en blanco.</span><span class="sxs-lookup"><span data-stu-id="49892-315">Leave the **product** entry blank.</span></span> <span data-ttu-id="49892-316">A continuación, haga clic en el botón **confirmar** .</span><span class="sxs-lookup"><span data-stu-id="49892-316">Then click the **Confirm** button.</span></span> <span data-ttu-id="49892-317">La salida en la parte inferior de la página mostrará el JSON que representa la probabilidad de que cada producto sea la elección.</span><span class="sxs-lookup"><span data-stu-id="49892-317">The output on the bottom of the page will show the JSON representing the likelihood of each product being the choice.</span></span>

29. <span data-ttu-id="49892-318">Se abrirá una nueva página web, en la que se mostrarán las instrucciones y algunos ejemplos sobre la estructura de la solicitud requerida por el Machine Learning Studio.</span><span class="sxs-lookup"><span data-stu-id="49892-318">A new web page will open up, displaying the instructions and some examples about the Request structure required by the Machine Learning Studio.</span></span> <span data-ttu-id="49892-319">Copie el **URI de solicitud** que se muestra en esta página en el Bloc de notas.</span><span class="sxs-lookup"><span data-stu-id="49892-319">Copy the **Request URI** displayed in this page, into your notepad.</span></span>

    ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-34.png)

<span data-ttu-id="49892-321">Ahora ha creado un sistema de aprendizaje automático que proporciona el producto más probable que se venda en función de los datos de compra históricos, correlacionados con la hora del día y el día del año.</span><span class="sxs-lookup"><span data-stu-id="49892-321">You have now built a machine learning system that provides the most likely product to be sold based on historical purchasing data, correlated with the time of the day and day of the year.</span></span>

<span data-ttu-id="49892-322">Para llamar al servicio Web, necesitará la dirección URL del punto de conexión de servicio y una clave de API para el servicio.</span><span class="sxs-lookup"><span data-stu-id="49892-322">To call the web service, you will need the URL for the service endpoint and an API Key for the service.</span></span> <span data-ttu-id="49892-323">Haga clic en la pestaña **consumo** , en el menú superior.</span><span class="sxs-lookup"><span data-stu-id="49892-323">Click on the **Consume** tab, from the top menu.</span></span>

<span data-ttu-id="49892-324">En la página información de **consumo** se mostrará la información necesaria para llamar al servicio web desde el código.</span><span class="sxs-lookup"><span data-stu-id="49892-324">The **Consumption** Info page will display the information you will need to call the web service from your code.</span></span> <span data-ttu-id="49892-325">Realice una copia de la **clave principal** y la dirección URL **de solicitud-respuesta** .</span><span class="sxs-lookup"><span data-stu-id="49892-325">Take a copy of the **Primary Key** and the **Request-Response** URL.</span></span> <span data-ttu-id="49892-326">Los necesitará en el siguiente capítulo.</span><span class="sxs-lookup"><span data-stu-id="49892-326">You will need these in the next Chapter.</span></span>

## <a name="chapter-5---setting-up-the-unity-project"></a><span data-ttu-id="49892-327">Capítulo 5: configuración del proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="49892-327">Chapter 5 - Setting up the Unity Project</span></span>

<span data-ttu-id="49892-328">Configure y pruebe sus auriculares de la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="49892-328">Set up and test your Mixed Reality Immersive Headset.</span></span>

> [!NOTE]
>  <span data-ttu-id="49892-329">**No** necesitará controladores de movimiento para este curso.</span><span class="sxs-lookup"><span data-stu-id="49892-329">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="49892-330">Si necesita ayuda para configurar el casco envolvente, haga clic [aquí](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="49892-330">If you need support setting up the Immersive Headset, please click [HERE](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="49892-331">Abra **Unity** y cree un nuevo proyecto de Unity denominado **Mr\_MachineLearning.**</span><span class="sxs-lookup"><span data-stu-id="49892-331">Open **Unity** and create a new Unity Project called **MR\_MachineLearning.**</span></span> <span data-ttu-id="49892-332">Asegúrese de que el tipo de proyecto está establecido en **3D**.</span><span class="sxs-lookup"><span data-stu-id="49892-332">Make sure the project type is set to **3D**.</span></span>

2.  <span data-ttu-id="49892-333">Con Unity abierto, merece la pena comprobar que el **Editor de scripts** predeterminado está establecido en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="49892-333">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="49892-334">Vaya a **editar** > **preferencias** y, a continuación, en la nueva ventana, vaya a **herramientas externas**.</span><span class="sxs-lookup"><span data-stu-id="49892-334">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="49892-335">Cambie el **Editor de script externo** a **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="49892-335">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="49892-336">Cierre la ventana **preferencias** .</span><span class="sxs-lookup"><span data-stu-id="49892-336">Close the **Preferences** window.</span></span>

3.  <span data-ttu-id="49892-337">A continuación, vaya a **archivo** > **configuración de compilación** y cambie la plataforma a **plataforma universal de Windows**, haciendo clic en el botón ***cambiar plataforma*** .</span><span class="sxs-lookup"><span data-stu-id="49892-337">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the ***Switch Platform*** button.</span></span>

4.  <span data-ttu-id="49892-338">Asegúrese también de que:</span><span class="sxs-lookup"><span data-stu-id="49892-338">Also make sure that:</span></span>

    1.  <span data-ttu-id="49892-339">El **dispositivo de destino** se establece en **cualquier dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="49892-339">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="49892-340">Para Microsoft HoloLens, establezca el **dispositivo de destino** en *hololens*.</span><span class="sxs-lookup"><span data-stu-id="49892-340">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="49892-341">El **tipo de compilación** se establece en **D3D**.</span><span class="sxs-lookup"><span data-stu-id="49892-341">**Build Type** is set to **D3D**.</span></span>

    3.  <span data-ttu-id="49892-342">**SDK** está establecido en **instalado más**recientemente.</span><span class="sxs-lookup"><span data-stu-id="49892-342">**SDK** is set to **Latest installed**.</span></span>

    4.  <span data-ttu-id="49892-343">La **versión de Visual Studio** está establecida en **instalación más reciente**.</span><span class="sxs-lookup"><span data-stu-id="49892-343">**Visual Studio Version** is set to **Latest installed**.</span></span>

    5.  <span data-ttu-id="49892-344">**Compilar y ejecutar** está establecido en **equipo local**.</span><span class="sxs-lookup"><span data-stu-id="49892-344">**Build and Run** is set to **Local Machine**.</span></span>

    6.  <span data-ttu-id="49892-345">No se preocupe por la configuración de **escenas** ahora, ya que se proporcionan más adelante.</span><span class="sxs-lookup"><span data-stu-id="49892-345">Do not worry about setting up **Scenes** right now, as these are provided later.</span></span>

    7.  <span data-ttu-id="49892-346">El resto de la configuración debe dejarse como predeterminada por ahora.</span><span class="sxs-lookup"><span data-stu-id="49892-346">The remaining settings should be left as default for now.</span></span>

        ![Configuración del proyecto de Unity](images/AzureLabs-Lab7-35.png)

5.  <span data-ttu-id="49892-348">En la ventana **configuración de compilación** , haga clic en el botón Configuración del **reproductor** ; se abrirá el panel relacionado en el espacio donde se encuentra el **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="49892-348">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

6. <span data-ttu-id="49892-349">En este panel, deben comprobarse algunas opciones de configuración:</span><span class="sxs-lookup"><span data-stu-id="49892-349">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="49892-350">En la pestaña **otros valores** :</span><span class="sxs-lookup"><span data-stu-id="49892-350">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="49892-351">La versión de **scripting** **en tiempo de ejecución** debe ser **experimental** (.net 4,6 equivalente)</span><span class="sxs-lookup"><span data-stu-id="49892-351">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>

        2. <span data-ttu-id="49892-352">El **back-end de scripting** debe ser ***.net***</span><span class="sxs-lookup"><span data-stu-id="49892-352">**Scripting Backend** should be ***.NET***</span></span>

        3. <span data-ttu-id="49892-353">El **nivel de compatibilidad de API** debe ser **.net 4,6**</span><span class="sxs-lookup"><span data-stu-id="49892-353">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Configuración del proyecto de Unity](images/AzureLabs-Lab7-36.png)

    2.  <span data-ttu-id="49892-355">En la pestaña **configuración de publicación** , en **capacidades**, seleccione:</span><span class="sxs-lookup"><span data-stu-id="49892-355">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="49892-356">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="49892-356">**InternetClient**</span></span>

            ![Configuración del proyecto de Unity](images/AzureLabs-Lab7-37.png)

    3.  <span data-ttu-id="49892-358">Más abajo en el panel, en la **configuración de XR** (se encuentra debajo de **configuración de publicación**), tick **Virtual Reality compatible**, asegúrese de que se ha agregado el **SDK de Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="49892-358">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![Configuración del proyecto de Unity](images/AzureLabs-Lab7-38.png)

    

6.  <span data-ttu-id="49892-360">De nuevo en la **configuración de compilación** , los proyectos de *Unity C#*  ya no están atenuados; Marque la casilla situada junto a este.</span><span class="sxs-lookup"><span data-stu-id="49892-360">Back in **Build Settings** *Unity C#* Projects is no longer greyed out; tick the checkbox next to this.</span></span> 

7.  <span data-ttu-id="49892-361">Cierre la ventana Configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="49892-361">Close the Build Settings window.</span></span>

8.  <span data-ttu-id="49892-362">Guarde el proyecto (**archivo > guardar proyecto**).</span><span class="sxs-lookup"><span data-stu-id="49892-362">Save your Project (**FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a><span data-ttu-id="49892-363">Capítulo 6: importar el paquete de Unity de MLProducts</span><span class="sxs-lookup"><span data-stu-id="49892-363">Chapter 6 - Importing the MLProducts Unity Package</span></span>

<span data-ttu-id="49892-364">En este curso, tendrá que descargar un paquete de recursos de Unity llamado [**Azure-Mr-307. unitypackage Tools**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="49892-364">For this course, you will need to download a Unity Asset Package called [**Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span></span> <span data-ttu-id="49892-365">Este paquete viene completo con una escena, con todos los objetos de que se han creado previamente, por lo que puede centrarse en conseguir que todo funcione.</span><span class="sxs-lookup"><span data-stu-id="49892-365">This package comes complete with a scene, with all objects in that prebuilt, so you can focus on getting it all working.</span></span> <span data-ttu-id="49892-366">Se proporciona el script **ShelfKeeper** , aunque solo contiene las variables públicas para la estructura de configuración de la escena.</span><span class="sxs-lookup"><span data-stu-id="49892-366">The **ShelfKeeper** script is provided, though only holds the public variables, for the purpose of scene setup structure.</span></span> <span data-ttu-id="49892-367">Tendrá que realizar todas las demás secciones.</span><span class="sxs-lookup"><span data-stu-id="49892-367">You will need to do all other sections.</span></span> 

<span data-ttu-id="49892-368">Para importar este paquete:</span><span class="sxs-lookup"><span data-stu-id="49892-368">To import this package:</span></span>

1.  <span data-ttu-id="49892-369">Con el panel de Unity delante de usted, haga clic en **recursos** en el menú de la parte superior de la pantalla y, luego, haga clic en **importar paquete, paquete personalizado**.</span><span class="sxs-lookup"><span data-stu-id="49892-369">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package, Custom Package**.</span></span>

    ![Importación del paquete Unity de MLProducts](images/AzureLabs-Lab7-39.png)

2.  <span data-ttu-id="49892-371">Use el selector de archivos para seleccionar el paquete **Azure-Mr-307. unitypackage Tools** y haga clic en **abrir**.</span><span class="sxs-lookup"><span data-stu-id="49892-371">Use the file picker to select the **Azure-MR-307.unitypackage** package and click **Open**.</span></span>

3.  <span data-ttu-id="49892-372">Se le mostrará una lista de los componentes de este recurso.</span><span class="sxs-lookup"><span data-stu-id="49892-372">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="49892-373">Confirme la importación haciendo clic en **importar**.</span><span class="sxs-lookup"><span data-stu-id="49892-373">Confirm the import by clicking **Import**.</span></span>

    ![Importación del paquete Unity de MLProducts](images/AzureLabs-Lab7-40.png)

4.  <span data-ttu-id="49892-375">Una vez que haya finalizado la importación, observará que algunas nuevas carpetas aparecen en el **panel del proyecto**de Unity.</span><span class="sxs-lookup"><span data-stu-id="49892-375">Once it has finished importing, you will notice that some new folders have appeared in your Unity **Project Panel**.</span></span> <span data-ttu-id="49892-376">Estos son los modelos 3D y los materiales respectivos que forman parte de la escena previamente realizada en la que trabajará.</span><span class="sxs-lookup"><span data-stu-id="49892-376">Those are the 3D models and the respective materials that are part of the pre-made scene you will work on.</span></span> <span data-ttu-id="49892-377">En este curso, escribirá la mayor parte del código.</span><span class="sxs-lookup"><span data-stu-id="49892-377">You will write the majority of the code in this course.</span></span>

    ![Importación del paquete Unity de MLProducts](images/AzureLabs-Lab7-41.png)

5.  <span data-ttu-id="49892-379">En la carpeta **panel del proyecto** , haga clic en la carpeta **Scenes** y haga doble clic en la escena dentro de (llamada **MR_MachineLearningScene**).</span><span class="sxs-lookup"><span data-stu-id="49892-379">Within the **Project Panel** folder, click on the **Scenes** folder and double click on the scene inside (called **MR_MachineLearningScene**).</span></span> <span data-ttu-id="49892-380">La escena se abrirá (consulte la imagen siguiente).</span><span class="sxs-lookup"><span data-stu-id="49892-380">The scene will open (see image below).</span></span> <span data-ttu-id="49892-381">Si faltan los rombos rojos, simplemente haga clic en el botón **Gizmos** , en la parte superior derecha del **Panel de juego**.</span><span class="sxs-lookup"><span data-stu-id="49892-381">If the red diamonds are missing, simply click the **Gizmos** button, at the top right of the **Game Panel**.</span></span>

    ![Importación del paquete Unity de MLProducts](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a><span data-ttu-id="49892-383">Capítulo 7: comprobación de los archivos dll en Unity</span><span class="sxs-lookup"><span data-stu-id="49892-383">Chapter 7 - Checking the DLLs in Unity</span></span>

<span data-ttu-id="49892-384">Para aprovechar el uso de las bibliotecas JSON (que se usan para serializar y deserializar), se ha implementado un archivo DLL de Newtonsoft con el paquete que se ha incorporado.</span><span class="sxs-lookup"><span data-stu-id="49892-384">To leverage the use of JSON libraries (used for serializing and deserializing), a Newtonsoft DLL has been implemented with the package you brought in.</span></span> <span data-ttu-id="49892-385">La biblioteca debe tener la configuración correcta, aunque merece la pena realizar una comprobación (especialmente si tiene problemas con el código que no funciona).</span><span class="sxs-lookup"><span data-stu-id="49892-385">The library should have the correct configuration, though it is worth checking (particularly if you are having issues with code not working).</span></span> 

<span data-ttu-id="49892-386">Para ello:</span><span class="sxs-lookup"><span data-stu-id="49892-386">To do so:</span></span>

-  <span data-ttu-id="49892-387">Haga clic con el botón izquierdo en el archivo Newtonsoft dentro de la carpeta plugins y mire en el **panel Inspector**.</span><span class="sxs-lookup"><span data-stu-id="49892-387">Left-click on the Newtonsoft file inside the Plugins folder and look at the **Inspector panel**.</span></span> <span data-ttu-id="49892-388">Asegúrese de que se realiza una marca en **cualquier plataforma** .</span><span class="sxs-lookup"><span data-stu-id="49892-388">Make sure **Any Platform** is ticked.</span></span> <span data-ttu-id="49892-389">Vaya a la **pestaña UWP** y asegúrese también de que no se ha activado el **proceso** .</span><span class="sxs-lookup"><span data-stu-id="49892-389">Go to the **UWP tab** and also ensure **Don't process** is ticked.</span></span>

    ![Importación de los archivos dll en Unity](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a><span data-ttu-id="49892-391">Capítulo 8: creación de la clase ShelfKeeper</span><span class="sxs-lookup"><span data-stu-id="49892-391">Chapter 8 - Create the ShelfKeeper class</span></span>

<span data-ttu-id="49892-392">La clase **ShelfKeeper** hospeda métodos que controlan la interfaz de usuario y los productos generados en la escena.</span><span class="sxs-lookup"><span data-stu-id="49892-392">The **ShelfKeeper** class hosts methods that control the UI and products spawned in the scene.</span></span>

<span data-ttu-id="49892-393">Como parte del paquete importado, se le proporcionará esta clase, aunque está incompleta.</span><span class="sxs-lookup"><span data-stu-id="49892-393">As part of the imported package, you will have been given this class, though it is incomplete.</span></span> <span data-ttu-id="49892-394">Ahora es el momento de completar esa clase:</span><span class="sxs-lookup"><span data-stu-id="49892-394">It is now time to complete that class:</span></span>

1.  <span data-ttu-id="49892-395">Haga doble clic en el script **ShelfKeeper** , dentro de la carpeta **scripts** , para abrirlo con **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="49892-395">Double click on the **ShelfKeeper** script, within the **Scripts** folder, to open it with **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="49892-396">Reemplace todo el código existente en el script con el código siguiente, que establece la fecha y la hora, y tiene un método para mostrar un producto.</span><span class="sxs-lookup"><span data-stu-id="49892-396">Replace all the code existing in the script with the following code, which sets the time and date and has a method to show a product.</span></span>

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

3.  <span data-ttu-id="49892-397">Asegúrese de guardar los cambios en **Visual Studio** antes de volver a **Unity**.</span><span class="sxs-lookup"><span data-stu-id="49892-397">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

4.  <span data-ttu-id="49892-398">De nuevo en el editor de Unity, compruebe que la clase **ShelfKeeper** es similar a la siguiente:</span><span class="sxs-lookup"><span data-stu-id="49892-398">Back in the Unity Editor, check that the **ShelfKeeper** class looks like the below:</span></span>

    ![Crear la clase ShelfKeeper](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > <span data-ttu-id="49892-400">Si el script no tiene destinos de referencia (es decir, *Date (malla de texto)* ), simplemente arrastre los objetos correspondientes del **Panel jerarquía**a los campos de destino.</span><span class="sxs-lookup"><span data-stu-id="49892-400">If your script does not have the reference targets (i.e. *Date (Text Mesh)*), simply drag the corresponding objects from the **Hierarchy Panel**, into the target fields.</span></span> <span data-ttu-id="49892-401">Consulte a continuación la explicación, si es necesario:</span><span class="sxs-lookup"><span data-stu-id="49892-401">See below for explanation, if needed:</span></span>
    > 
    > 1.  <span data-ttu-id="49892-402">Abra la matriz de **puntos de generación** dentro del script del componente **ShelfKeeper** . para ello, haga clic en ella.</span><span class="sxs-lookup"><span data-stu-id="49892-402">Open the **Spawn Point** array within the **ShelfKeeper** component script by left-clicking it.</span></span> <span data-ttu-id="49892-403">Una subsección aparecerá denominada **size**, que indica el tamaño de la matriz.</span><span class="sxs-lookup"><span data-stu-id="49892-403">A sub-section will appear called **Size**, which indicates the size of the array.</span></span> <span data-ttu-id="49892-404">Escriba **3** en el cuadro de texto junto a **tamaño** y presione **entrar**; se crearán tres ranuras debajo.</span><span class="sxs-lookup"><span data-stu-id="49892-404">Type **3** into the textbox next to **Size** and press **Enter**, and three slots will be created beneath.</span></span>
    > 2. <span data-ttu-id="49892-405">Dentro de la **jerarquía** , expanda el objeto **Time display** (haciendo clic con el botón izquierdo en la flecha situada junto a él).</span><span class="sxs-lookup"><span data-stu-id="49892-405">Within the **Hierarchy** expand the **Time Display** object (by left-clicking the arrow beside it).</span></span> <span data-ttu-id="49892-406">A continuación, haga clic en la ***cámara principal*** desde dentro de la **jerarquía**para que el **Inspector** muestre su información.</span><span class="sxs-lookup"><span data-stu-id="49892-406">Next click the ***Main Camera*** from within the **Hierarchy**, so that the **Inspector** shows its information.</span></span>
    > 3. <span data-ttu-id="49892-407">Seleccione la **cámara principal** en el **Panel jerarquía**.</span><span class="sxs-lookup"><span data-stu-id="49892-407">Select the **Main Camera** in the **Hierarchy Panel**.</span></span> <span data-ttu-id="49892-408">Arrastre los objetos de **fecha** y **hora** desde **el panel jerarquía** hasta las ranuras de **texto** de **fecha** y hora del **Inspector** de la **cámara principal** en el componente **ShelfKeeper** .</span><span class="sxs-lookup"><span data-stu-id="49892-408">Drag the **Date** and **Time** objects from the **Hierarchy Panel** to the **Date Text** and **Time Text** slots within the **Inspector** of the **Main Camera** in the **ShelfKeeper** component.</span></span>
    > 4. <span data-ttu-id="49892-409">Arrastre los **puntos de generación** desde el **Panel de jerarquía** (debajo del objeto de *estantería* ) hasta los **tres** destinos de referencia de **elemento** debajo de la matriz de **puntos de generación** , como se muestra en la imagen.</span><span class="sxs-lookup"><span data-stu-id="49892-409">Drag the **Spawn Points** from the **Hierarchy Panel** (beneath the *Shelf* object) to the **3** **Element** reference targets beneath the **Spawn Point** array, as shown in the image.</span></span>
    > 
    >     ![Crear la clase ShelfKeeper](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a><span data-ttu-id="49892-411">Capítulo 9: creación de la clase ProductPrediction</span><span class="sxs-lookup"><span data-stu-id="49892-411">Chapter 9 - Create the ProductPrediction class</span></span>

<span data-ttu-id="49892-412">La clase siguiente que va a crear es la clase **ProductPrediction** .</span><span class="sxs-lookup"><span data-stu-id="49892-412">The next class you are going to create is the **ProductPrediction** class.</span></span>

<span data-ttu-id="49892-413">Esta clase es responsable de:</span><span class="sxs-lookup"><span data-stu-id="49892-413">This class is responsible for:</span></span>

-   <span data-ttu-id="49892-414">Consultar la instancia de **servicio de machine learning** , que proporciona la fecha y hora actuales.</span><span class="sxs-lookup"><span data-stu-id="49892-414">Querying the **Machine Learning Service** instance, providing the current date and time.</span></span>

-   <span data-ttu-id="49892-415">Deserializar la respuesta JSON en datos utilizables.</span><span class="sxs-lookup"><span data-stu-id="49892-415">Deserializing the JSON response into usable data.</span></span>

-   <span data-ttu-id="49892-416">Interpretar los datos, recuperar los 3 productos recomendados.</span><span class="sxs-lookup"><span data-stu-id="49892-416">Interpreting the data, retrieving the 3 recommended products.</span></span>

-   <span data-ttu-id="49892-417">Llamar a los métodos de la clase **ShelfKeeper** para mostrar los datos de la escena.</span><span class="sxs-lookup"><span data-stu-id="49892-417">Calling the **ShelfKeeper** class methods to display the data in the Scene.</span></span>

<span data-ttu-id="49892-418">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="49892-418">To create this class:</span></span>

1.  <span data-ttu-id="49892-419">Vaya a la carpeta **scripts** , en el **panel Proyecto**.</span><span class="sxs-lookup"><span data-stu-id="49892-419">Go to the **Scripts** folder, in the **Project Panel**.</span></span>

2.  <span data-ttu-id="49892-420">Haga clic con el botón derecho dentro de la carpeta, **cree** >  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="49892-420">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="49892-421">Llame al script **ProductPrediction**.</span><span class="sxs-lookup"><span data-stu-id="49892-421">Call the script **ProductPrediction**.</span></span>

3.  <span data-ttu-id="49892-422">Haga doble clic en el nuevo script **ProductPrediction** para abrirlo con **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="49892-422">Double click on the new **ProductPrediction** script to open it with **Visual Studio 2017**.</span></span>

4.  <span data-ttu-id="49892-423">Si aparece el cuadro de diálogo se **ha detectado la modificación del archivo** , haga clic en \***volver a cargar la solución**.</span><span class="sxs-lookup"><span data-stu-id="49892-423">If the **File Modification Detected** dialog pops up, click \***Reload Solution**.</span></span>

5.  <span data-ttu-id="49892-424">Agregue los siguientes espacios de nombres en la parte superior de la clase ProductPrediction:</span><span class="sxs-lookup"><span data-stu-id="49892-424">Add the following namespaces to the top of the ProductPrediction class:</span></span>

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

6.  <span data-ttu-id="49892-425">Dentro de la clase **ProductPrediction** , inserte los dos objetos siguientes, que se componen de un número de clases anidadas.</span><span class="sxs-lookup"><span data-stu-id="49892-425">Inside the **ProductPrediction** class insert the following two objects which are composed of a number of nested classes.</span></span> <span data-ttu-id="49892-426">Estas clases se usan para serializar y deserializar el archivo JSON para el servicio Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="49892-426">These classes are used to serialize and deserialize the JSON for the Machine Learning Service.</span></span>

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

7.  <span data-ttu-id="49892-427">A continuación, agregue las siguientes variables sobre el código anterior (de modo que el código relacionado con JSON esté en la parte inferior del script, debajo del resto del código y fuera del camino):</span><span class="sxs-lookup"><span data-stu-id="49892-427">Then add the following variables above the previous code (so that the JSON related code is at the bottom of the script, below all other code, and out of the way):</span></span>

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
    > <span data-ttu-id="49892-428">Asegúrese de insertar la **clave principal** y el **punto de conexión de solicitud-respuesta**, desde el portal de machine learning, en las variables aquí.</span><span class="sxs-lookup"><span data-stu-id="49892-428">Make sure to insert the **primary key** and **request-response endpoint**, from the Machine Learning Portal, into the variables here.</span></span> <span data-ttu-id="49892-429">Las siguientes imágenes muestran dónde habría tomado la clave y el punto de conexión de.</span><span class="sxs-lookup"><span data-stu-id="49892-429">The below images show where you would have taken the key and endpoint from.</span></span> 
    >  
    > ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-53-1.png)
    >
    > ![El Machine Learning Studio: el experimento](images/AzureLabs-Lab7-53-2.png)

8.  <span data-ttu-id="49892-432">Inserte este código dentro del método **Start ()** .</span><span class="sxs-lookup"><span data-stu-id="49892-432">Insert this code within the **Start()** method.</span></span> <span data-ttu-id="49892-433">Se llama al método **Start ()** cuando se inicializa la clase:</span><span class="sxs-lookup"><span data-stu-id="49892-433">The **Start()** method is called when the class initializes:</span></span>

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

9.  <span data-ttu-id="49892-434">El siguiente es el método que recopila la fecha y la hora de Windows y las convierte en un formato que el experimento de Machine Learning puede utilizar para comparar con los datos almacenados en la tabla.</span><span class="sxs-lookup"><span data-stu-id="49892-434">The following is the method that collects the date and time from Windows and converts it into a format that our Machine Learning Experiment can use to compare with the data stored in the table.</span></span>

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

10. <span data-ttu-id="49892-435">Puede **eliminar** el método **Update ()** , ya que esta clase no lo usará.</span><span class="sxs-lookup"><span data-stu-id="49892-435">You can **delete** the **Update()** method since this class will not use it.</span></span>

11. <span data-ttu-id="49892-436">Agregue el método siguiente, que comunicará la fecha y hora actuales con el punto de conexión de Machine Learning y recibirá una respuesta en formato JSON.</span><span class="sxs-lookup"><span data-stu-id="49892-436">Add the following method which will communicate the current date and time to the Machine Learning endpoint and receive a response in JSON format.</span></span>

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

12. <span data-ttu-id="49892-437">Agregue el método siguiente, que es responsable de deserializar la respuesta JSON y de comunicar el resultado de la deserialización a la clase **ShelfKeeper** .</span><span class="sxs-lookup"><span data-stu-id="49892-437">Add the following method, which is responsible for deserializing the JSON response, and communicating the result of the deserialization to the **ShelfKeeper** class.</span></span> <span data-ttu-id="49892-438">Este resultado será el nombre de los tres elementos previstos para vender más en la fecha y hora actuales.</span><span class="sxs-lookup"><span data-stu-id="49892-438">This result will be the names of the three items predicted to sell the most at current date and time.</span></span> <span data-ttu-id="49892-439">Inserte el código siguiente en la clase **ProductPrediction** , debajo del método anterior.</span><span class="sxs-lookup"><span data-stu-id="49892-439">Insert the code below into the **ProductPrediction** class, below the previous method.</span></span>

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

13. <span data-ttu-id="49892-440">Guarde **Visual Studio** y vuelva a la sección **Unity**.</span><span class="sxs-lookup"><span data-stu-id="49892-440">Save **Visual Studio** and head back to **Unity**.</span></span>

14. <span data-ttu-id="49892-441">Arrastre el script de la clase **ProductPrediction** desde la carpeta **script** hasta el objeto **Camera principal** .</span><span class="sxs-lookup"><span data-stu-id="49892-441">Drag the **ProductPrediction** class script from the **Script** folder, onto the **Main Camera** object.</span></span>

15. <span data-ttu-id="49892-442">Guarde la escena y el **archivo** de proyecto > **guardar la escena o el archivo** > **guardar el proyecto**.</span><span class="sxs-lookup"><span data-stu-id="49892-442">Save your scene and project **File** > **Save Scene/File** > **Save Project**.</span></span>

## <a name="chapter-10---build-the-uwp-solution"></a><span data-ttu-id="49892-443">Capítulo 10: compilar la solución UWP</span><span class="sxs-lookup"><span data-stu-id="49892-443">Chapter 10 - Build the UWP Solution</span></span>

<span data-ttu-id="49892-444">Ahora es el momento de compilar el proyecto como una solución de UWP, de modo que pueda ejecutarse como una aplicación independiente.</span><span class="sxs-lookup"><span data-stu-id="49892-444">It is now time to build your project as a UWP solution, so that it can run as a standalone application.</span></span>

<span data-ttu-id="49892-445">Para compilar:</span><span class="sxs-lookup"><span data-stu-id="49892-445">To Build:</span></span>

1.  <span data-ttu-id="49892-446">Guarde la escena actual haciendo clic en **archivo** > **Guardar escenas**.</span><span class="sxs-lookup"><span data-stu-id="49892-446">Save the current scene by clicking on **File** > **Save Scenes**.</span></span>

2.  <span data-ttu-id="49892-447">Ir a **archivo** > **configuración de compilación**</span><span class="sxs-lookup"><span data-stu-id="49892-447">Go to **File** > **Build Settings**</span></span>

3.  <span data-ttu-id="49892-448">Active la casilla denominada **proyectos C# de Unity** (esto es importante porque le permitirá editar las clases una vez completada la compilación).</span><span class="sxs-lookup"><span data-stu-id="49892-448">Check the box called **Unity C# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

4.  <span data-ttu-id="49892-449">Haga clic en **Agregar escenas abiertas**,</span><span class="sxs-lookup"><span data-stu-id="49892-449">Click on **Add Open Scenes**,</span></span>

5.  <span data-ttu-id="49892-450">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="49892-450">Click **Build**.</span></span>

    ![Compilar la solución de UWP](images/AzureLabs-Lab7-54.png)

6.  <span data-ttu-id="49892-452">Se le pedirá que seleccione la carpeta en la que desea compilar la solución.</span><span class="sxs-lookup"><span data-stu-id="49892-452">You will be prompted to select the folder where you want to build the Solution.</span></span>

7.  <span data-ttu-id="49892-453">Cree una carpeta **compilaciones** y, dentro de esa carpeta, cree otra carpeta con un nombre adecuado de su elección.</span><span class="sxs-lookup"><span data-stu-id="49892-453">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

8.  <span data-ttu-id="49892-454">Haga clic en la nueva carpeta y, a continuación, haga clic en **Seleccionar carpeta**para iniciar la compilación en esa ubicación.</span><span class="sxs-lookup"><span data-stu-id="49892-454">Click your new folder and then click **Select Folder**, to begin the build at that location.</span></span>

    ![Compilar la solución de UWP](images/AzureLabs-Lab7-55.png)

    ![Compilar la solución de UWP](images/AzureLabs-Lab7-56.png)

9.  <span data-ttu-id="49892-457">Una vez que Unity termine de compilar (puede tardar algún tiempo), se abrirá una ventana del **Explorador de archivos** en la ubicación de la compilación (Compruebe la barra de tareas, ya que es posible que no aparezca siempre por encima de las ventanas, pero le notificará la adición de una nueva ventana).</span><span class="sxs-lookup"><span data-stu-id="49892-457">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11---deploy-your-application"></a><span data-ttu-id="49892-458">Capítulo 11: implementación de la aplicación</span><span class="sxs-lookup"><span data-stu-id="49892-458">Chapter 11 - Deploy your Application</span></span>

<span data-ttu-id="49892-459">Para implementar la aplicación:</span><span class="sxs-lookup"><span data-stu-id="49892-459">To deploy your application:</span></span>

1.  <span data-ttu-id="49892-460">Vaya a la nueva compilación de Unity (la carpeta de la **aplicación** ) y abra el archivo de solución con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="49892-460">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

2.  <span data-ttu-id="49892-461">Con Visual Studio abierto, debe restaurar los paquetes NuGet, que se pueden realizar a través del clic con el botón derecho en la solución MachineLearningLab_Build, desde el Explorador de soluciones (que se encuentra a la derecha de Visual Studio) y, a continuación, haciendo clic en restaurar paquetes NuGet:</span><span class="sxs-lookup"><span data-stu-id="49892-461">With Visual Studio open, you need to Restore NuGet Packages, which can be done through right-clicking your MachineLearningLab_Build solution, from the Solution Explorer (found to the right of Visual Studio), and then clicking Restore NuGet Packages:</span></span>

    ![Agregar paquetes NuGet](images/AzureLabs-Lab7-57.png)

3.  <span data-ttu-id="49892-463">En la configuración de soluciones, seleccione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="49892-463">In the Solution Configuration select **Debug**.</span></span>

4.  <span data-ttu-id="49892-464">En la plataforma de la solución, seleccione **x86**, **equipo local**.</span><span class="sxs-lookup"><span data-stu-id="49892-464">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="49892-465">En el caso de Microsoft HoloLens, es posible que le resulte más fácil establecer esto en el *equipo remoto*, de modo que no esté anclado al equipo.</span><span class="sxs-lookup"><span data-stu-id="49892-465">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="49892-466">Sin embargo, también tendrá que hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="49892-466">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="49892-467">Conozca la **dirección IP** de HoloLens, que puede encontrarse en la *configuración > red & Internet > Wi-Fi > Opciones avanzadas*; IPv4 es la dirección que debe usar.</span><span class="sxs-lookup"><span data-stu-id="49892-467">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="49892-468">Asegurarse de que el **modo de desarrollador** está **activado**; se encuentra en *configuración > actualizar & > de seguridad para desarrolladores*.</span><span class="sxs-lookup"><span data-stu-id="49892-468">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Agregar paquetes NuGet](images/AzureLabs-Lab7-58.png)

5.  <span data-ttu-id="49892-470">Vaya al **menú compilar** y haga clic en **implementar solución** para transferir localmente la aplicación a su equipo.</span><span class="sxs-lookup"><span data-stu-id="49892-470">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>

6.  <span data-ttu-id="49892-471">La aplicación debe aparecer ahora en la lista de aplicaciones instaladas, lista para iniciarse.</span><span class="sxs-lookup"><span data-stu-id="49892-471">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="49892-472">Al ejecutar la aplicación de realidad mixta, verá la banco que se configuró en la escena de Unity y, desde la inicialización, se capturarán los datos que configuró en Azure.</span><span class="sxs-lookup"><span data-stu-id="49892-472">When you run the Mixed Reality application, you will see the bench that was set up in your Unity scene, and from initialization, the data you set up within Azure will be fetched.</span></span> <span data-ttu-id="49892-473">Los datos se deserializarán dentro de la aplicación y los tres resultados principales de la fecha y hora actuales se proporcionarán visualmente, como tres modelos en la banco.</span><span class="sxs-lookup"><span data-stu-id="49892-473">The data will be deserialized within your application, and the three top results for your current date and time will be provided visually, as three models on the bench.</span></span>


## <a name="your-finished-machine-learning-application"></a><span data-ttu-id="49892-474">La aplicación Machine Learning finalizada</span><span class="sxs-lookup"><span data-stu-id="49892-474">Your finished Machine Learning application</span></span>
 
<span data-ttu-id="49892-475">Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha las Azure Machine Learning para hacer predicciones de datos y mostrarlas en la escena.</span><span class="sxs-lookup"><span data-stu-id="49892-475">Congratulations, you built a mixed reality app that leverages the Azure Machine Learning to make data predictions and display it on your scene.</span></span>

![Agregar paquetes NuGet](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a><span data-ttu-id="49892-477">Dicha</span><span class="sxs-lookup"><span data-stu-id="49892-477">Exercise</span></span>

<span data-ttu-id="49892-478">**Ejercicio 1**</span><span class="sxs-lookup"><span data-stu-id="49892-478">**Exercise 1**</span></span>

<span data-ttu-id="49892-479">Experimente con el criterio de ordenación de la aplicación y tenga en cuenta que las tres predicciones inferiores aparecen en la estantería, ya que estos datos también podrían resultar útiles.</span><span class="sxs-lookup"><span data-stu-id="49892-479">Experiment with the sort order of your application and have the three bottom predictions appear on the shelf, as this data would potentially be useful also.</span></span>

<span data-ttu-id="49892-480">**Ejercicio 2**</span><span class="sxs-lookup"><span data-stu-id="49892-480">**Exercise 2**</span></span>

<span data-ttu-id="49892-481">El uso de **tablas de Azure** rellenará una nueva tabla con información meteorológica y creará un nuevo experimento con los datos.</span><span class="sxs-lookup"><span data-stu-id="49892-481">Using **Azure Tables** populate a new table with weather information and create a new experiment using the data.</span></span>
