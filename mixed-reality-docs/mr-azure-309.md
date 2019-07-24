---
title: MR y Azure 309-Application Insights
description: Complete este curso para aprender a recopilar análisis sobre el comportamiento del usuario en una aplicación de realidad mixta, mediante el servicio de Aplicación de Azure Insights.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academia, Unity, tutorial, API, Application Insights, hololens, envolventes, VR
ms.openlocfilehash: e14a32f9a38e3e8f3054d19310782f7c2d4784a1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694569"
---
>[!NOTE]
><span data-ttu-id="0152e-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="0152e-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="0152e-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="0152e-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="0152e-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0152e-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="0152e-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="0152e-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="0152e-108">Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0152e-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="0152e-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.</span><span class="sxs-lookup"><span data-stu-id="0152e-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-309-application-insights"></a><span data-ttu-id="0152e-110">MR y Azure 309: Application Insights</span><span class="sxs-lookup"><span data-stu-id="0152e-110">MR and Azure 309: Application insights</span></span>

![Inicio del producto final](images/AzureLabs-Lab309-00.png)

<span data-ttu-id="0152e-112">En este curso, aprenderá a agregar funcionalidades de Application Insights a una aplicación de realidad mixta, mediante la API de Aplicación de Azure Insights para recopilar análisis sobre el comportamiento de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="0152e-112">In this course, you will learn how to add Application Insights capabilities to a mixed reality application, using the Azure Application Insights API to collect analytics regarding user behavior.</span></span>

<span data-ttu-id="0152e-113">Application Insights es un servicio de Microsoft, lo que permite a los desarrolladores recopilar análisis de sus aplicaciones y administrarlo desde un portal fácil de usar.</span><span class="sxs-lookup"><span data-stu-id="0152e-113">Application Insights is a Microsoft service, allowing developers to collect analytics from their applications and manage it from an easy-to-use portal.</span></span> <span data-ttu-id="0152e-114">El análisis puede ser cualquier cosa desde el rendimiento hasta la información personalizada que desea recopilar.</span><span class="sxs-lookup"><span data-stu-id="0152e-114">The analytics can be anything from performance to custom information you would like to collect.</span></span> <span data-ttu-id="0152e-115">Para obtener más información, visite la [página Application Insights](https://azure.microsoft.com/services/application-insights/).</span><span class="sxs-lookup"><span data-stu-id="0152e-115">For more information, visit the [Application Insights page](https://azure.microsoft.com/services/application-insights/).</span></span>

<span data-ttu-id="0152e-116">Una vez finalizado este curso, tendrá una aplicación de auriculares con un casco de realidad mixta que podrá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="0152e-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="0152e-117">Permite al usuario avanzar y desplazarse por una escena.</span><span class="sxs-lookup"><span data-stu-id="0152e-117">Allow the user to gaze and move around a scene.</span></span>
2.  <span data-ttu-id="0152e-118">Desencadene el envío de análisis al servicio de *Application Insights*, mediante el uso de miras y proximidad a objetos en la escena.</span><span class="sxs-lookup"><span data-stu-id="0152e-118">Trigger the sending of analytics to the *Application Insights Service*, through the use of Gaze and Proximity to in-scene objects.</span></span>
3.  <span data-ttu-id="0152e-119">La aplicación también llamará a en el servicio, obteniendo información sobre el objeto que el usuario ha abordado más en las últimas 24 horas.</span><span class="sxs-lookup"><span data-stu-id="0152e-119">The app will also call upon the Service, fetching information about which object has been approached the most by the user, within the last 24 hours.</span></span> <span data-ttu-id="0152e-120">Ese objeto cambiará su color a verde.</span><span class="sxs-lookup"><span data-stu-id="0152e-120">That object will change its color to green.</span></span>

<span data-ttu-id="0152e-121">Este curso le enseñará a obtener los resultados del servicio de Application Insights, en una aplicación de ejemplo basada en Unity.</span><span class="sxs-lookup"><span data-stu-id="0152e-121">This course will teach you how to get the results from the Application Insights Service, into a Unity-based sample application.</span></span> <span data-ttu-id="0152e-122">Depende de usted que aplique estos conceptos a una aplicación personalizada que pueda estar compilando.</span><span class="sxs-lookup"><span data-stu-id="0152e-122">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="0152e-123">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="0152e-123">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="0152e-124">Recurso</span><span class="sxs-lookup"><span data-stu-id="0152e-124">Course</span></span></th><th style="width:150px"> <span data-ttu-id="0152e-125"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="0152e-125"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="0152e-126"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="0152e-126"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="0152e-127">MR y Azure 309: Application Insights</span><span class="sxs-lookup"><span data-stu-id="0152e-127">MR and Azure 309: Application insights</span></span></td><td style="text-align: center;"> <span data-ttu-id="0152e-128">✔️</span><span class="sxs-lookup"><span data-stu-id="0152e-128">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="0152e-129">✔️</span><span class="sxs-lookup"><span data-stu-id="0152e-129">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="0152e-130">Aunque este curso se centra principalmente en los auriculares de Windows Mixed Reality inmersivo (VR), también puede aplicar lo que aprenda en este curso a Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0152e-130">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="0152e-131">A medida que siga con el curso, verá notas sobre cualquier cambio que deba usar para admitir HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0152e-131">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="0152e-132">Al usar HoloLens, puede observar algún Eco durante la captura de voz.</span><span class="sxs-lookup"><span data-stu-id="0152e-132">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0152e-133">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="0152e-133">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="0152e-134">Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#.</span><span class="sxs-lookup"><span data-stu-id="0152e-134">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="0152e-135">Tenga en cuenta también que los requisitos previos y las instrucciones escritas dentro de este documento representan lo que se ha probado y comprobado en el momento de la escritura (2018 de julio).</span><span class="sxs-lookup"><span data-stu-id="0152e-135">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="0152e-136">Puede usar el software más reciente, como se indica en el artículo [instalar las herramientas](install-the-tools.md) , aunque no se debe suponer que la información de este curso se ajusta perfectamente a lo que encontrará en el software más reciente que el que se enumera a continuación.</span><span class="sxs-lookup"><span data-stu-id="0152e-136">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="0152e-137">Se recomienda el siguiente hardware y software para este curso:</span><span class="sxs-lookup"><span data-stu-id="0152e-137">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="0152e-138">Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de auriculares envolvente (VR)</span><span class="sxs-lookup"><span data-stu-id="0152e-138">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="0152e-139">Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="0152e-139">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="0152e-140">El SDK de Windows 10 más reciente</span><span class="sxs-lookup"><span data-stu-id="0152e-140">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="0152e-141">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="0152e-141">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="0152e-142">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0152e-142">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="0152e-143">Un [auricular de Windows Mixed Reality inmersivo (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="0152e-143">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="0152e-144">Un conjunto de auriculares con un micrófono integrado (si el casco no tiene micrófonos y altavoces integrados)</span><span class="sxs-lookup"><span data-stu-id="0152e-144">A set of headphones with a built-in microphone (if the headset does not have a built-in mic and speakers)</span></span>
- <span data-ttu-id="0152e-145">Acceso a Internet para la instalación de Azure y Application Insights la recuperación de datos</span><span class="sxs-lookup"><span data-stu-id="0152e-145">Internet access for Azure setup and Application Insights data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="0152e-146">Antes de comenzar</span><span class="sxs-lookup"><span data-stu-id="0152e-146">Before you start</span></span>

<span data-ttu-id="0152e-147">Para evitar que se produzcan problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cerca de la raíz (las rutas de acceso de carpeta largas pueden producir problemas en tiempo de compilación).</span><span class="sxs-lookup"><span data-stu-id="0152e-147">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

> [!WARNING] 
> <span data-ttu-id="0152e-148">Tenga en cuenta que los datos que van a *Application Insights* lleva tiempo, por lo que debe ser paciente.</span><span class="sxs-lookup"><span data-stu-id="0152e-148">Be aware, data going to *Application Insights* takes time, so be patient.</span></span> <span data-ttu-id="0152e-149">Si desea comprobar si el servicio ha recibido los datos, consulte el [capítulo 14](#chapter-14---the-application-insights-service-portal), que le mostrará cómo navegar por el portal.</span><span class="sxs-lookup"><span data-stu-id="0152e-149">If you want to check if the Service has received your data, check out [Chapter 14](#chapter-14---the-application-insights-service-portal), which will show you how to navigate the portal.</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="0152e-150">Capítulo 1: Azure portal</span><span class="sxs-lookup"><span data-stu-id="0152e-150">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="0152e-151">Para usar *Application Insights*, debe crear y configurar un *servicio de Application Insights* en la Azure portal.</span><span class="sxs-lookup"><span data-stu-id="0152e-151">To use *Application Insights*, you will need to create and configure an *Application Insights Service* in the Azure portal.</span></span>

1.  <span data-ttu-id="0152e-152">Inicie sesión en el [portal de Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="0152e-152">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="0152e-153">Si aún no tiene una cuenta de Azure, tendrá que crear una.</span><span class="sxs-lookup"><span data-stu-id="0152e-153">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="0152e-154">Si sigue este tutorial en una situación de aula o de laboratorio, pregunte al instructor o a uno de los Proctors para obtener ayuda para configurar la nueva cuenta.</span><span class="sxs-lookup"><span data-stu-id="0152e-154">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="0152e-155">Una vez que haya iniciado sesión, haga clic en **nuevo** en la esquina superior izquierda y busque *Application Insights*y haga clic en **entrar**.</span><span class="sxs-lookup"><span data-stu-id="0152e-155">Once you are logged in, click on **New** in the top left corner, and search for *Application Insights*, and click **Enter**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="0152e-156">Es posible que la palabra **nuevo** se haya reemplazado por **crear un recurso**, en portales más recientes.</span><span class="sxs-lookup"><span data-stu-id="0152e-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-01.png)

3.  <span data-ttu-id="0152e-158">La nueva página a la derecha proporcionará una descripción del servicio *aplicación de Azure Insights* .</span><span class="sxs-lookup"><span data-stu-id="0152e-158">The new page to the right will provide a description of the *Azure Application Insights* Service.</span></span> <span data-ttu-id="0152e-159">En la parte inferior izquierda de esta página, seleccione el botón **crear** para crear una asociación con este servicio.</span><span class="sxs-lookup"><span data-stu-id="0152e-159">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-02.png)

4.  <span data-ttu-id="0152e-161">Una vez que haya hecho clic en **crear**:</span><span class="sxs-lookup"><span data-stu-id="0152e-161">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="0152e-162">Inserte el **nombre** que desee para esta instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="0152e-162">Insert your desired **Name** for this Service instance.</span></span>

    2.  <span data-ttu-id="0152e-163">Como **tipo de aplicación**, seleccione **General**.</span><span class="sxs-lookup"><span data-stu-id="0152e-163">As **Application Type**, select **General**.</span></span>

    3.  <span data-ttu-id="0152e-164">Seleccione una **suscripción**adecuada.</span><span class="sxs-lookup"><span data-stu-id="0152e-164">Select an appropriate **Subscription**.</span></span>

    4.  <span data-ttu-id="0152e-165">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="0152e-165">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="0152e-166">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="0152e-166">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="0152e-167">Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común).</span><span class="sxs-lookup"><span data-stu-id="0152e-167">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="0152e-168">Si desea leer más información sobre los grupos de recursos de Azure, [visite el artículo sobre el grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="0152e-168">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5.  <span data-ttu-id="0152e-169">Seleccione una **Ubicación**.</span><span class="sxs-lookup"><span data-stu-id="0152e-169">Select a **Location**.</span></span>

    6.  <span data-ttu-id="0152e-170">También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.</span><span class="sxs-lookup"><span data-stu-id="0152e-170">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="0152e-171">Seleccione **Crear**.</span><span class="sxs-lookup"><span data-stu-id="0152e-171">Select **Create**.</span></span>

        ![Azure Portal](images/AzureLabs-Lab309-03.png)

5.  <span data-ttu-id="0152e-173">Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="0152e-173">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="0152e-174">Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="0152e-174">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-04.png)

7.  <span data-ttu-id="0152e-176">Haga clic en las notificaciones para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="0152e-176">Click on the notifications to explore your new Service instance.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-05.png)

8.  <span data-ttu-id="0152e-178">Haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="0152e-178">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="0152e-179">Se le dirigirá a la nueva instancia de *servicio de Application Insights* .</span><span class="sxs-lookup"><span data-stu-id="0152e-179">You will be taken to your new *Application Insights Service* instance.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  <span data-ttu-id="0152e-181">Mantenga esta página web abierta y fácil de acceder; volverá a menudo para ver los datos recopilados.</span><span class="sxs-lookup"><span data-stu-id="0152e-181">Keep this web page open and easy to access, you will come back here often to see the data collected.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="0152e-182">Para implementar Application Insights, debe usar tres (3) valores específicos: **Clave de instrumentación**, **ID**. de aplicación y **clave de API**.</span><span class="sxs-lookup"><span data-stu-id="0152e-182">To implement Application Insights, you will need to use three (3) specific values: **Instrumentation Key**, **Application ID**, and **API Key**.</span></span> <span data-ttu-id="0152e-183">A continuación, verá cómo recuperar estos valores desde el servicio.</span><span class="sxs-lookup"><span data-stu-id="0152e-183">Below you will see how to retrieve these values from your Service.</span></span> <span data-ttu-id="0152e-184">Asegúrese de anotar estos valores en una página en blanco del *Bloc* de notas, ya que los usará pronto en el código.</span><span class="sxs-lookup"><span data-stu-id="0152e-184">Make sure to note these values on a blank *Notepad* page, because you will use them soon in your code.</span></span>

9.  <span data-ttu-id="0152e-185">Para buscar la **clave de instrumentación**, deberá desplazarse hacia abajo en la lista de funciones de servicio y hacer clic en **propiedades**; la pestaña que se muestra revelará la **clave de servicio**.</span><span class="sxs-lookup"><span data-stu-id="0152e-185">To find the **Instrumentation Key**, you will need to scroll down the list of Service functions, and click on **Properties**, the tab displayed will reveal the **Service Key**.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-07.png)

10. <span data-ttu-id="0152e-187">A continuación **, encontrará un**poco más bajo propiedades, en **las**que tendrá que hacer clic.</span><span class="sxs-lookup"><span data-stu-id="0152e-187">A little below **Properties**, you will find **API Access**, which you need to click.</span></span> <span data-ttu-id="0152e-188">En el panel de la derecha se proporcionará el identificador de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="0152e-188">The panel to the right will provide the **Application ID** of your app.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-08.png)

11. <span data-ttu-id="0152e-190">Con el panel **ID. de aplicación** todavía abierto, haga clic en **crear clave de API**, que abrirá el panel *crear clave de API* .</span><span class="sxs-lookup"><span data-stu-id="0152e-190">With the **Application ID** panel still open, click **Create API Key**, which will open the *Create API key* panel.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-09.png)

12. <span data-ttu-id="0152e-192">En el panel abrir ahora *crear clave de API* , escriba una descripción y **marque los tres cuadros**.</span><span class="sxs-lookup"><span data-stu-id="0152e-192">Within the now open *Create API key* panel, type a description, and **tick the three boxes**.</span></span>

13. <span data-ttu-id="0152e-193">Haga clic en **generar clave**.</span><span class="sxs-lookup"><span data-stu-id="0152e-193">Click **Generate Key**.</span></span> <span data-ttu-id="0152e-194">Se creará y mostrará la **clave de API** .</span><span class="sxs-lookup"><span data-stu-id="0152e-194">Your **API Key** will be created and displayed.</span></span> 

    ![Azure Portal](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > <span data-ttu-id="0152e-196">Esta es la única vez que se mostrará la **clave de servicio** , por lo que debe asegurarse de hacer una copia de ella ahora.</span><span class="sxs-lookup"><span data-stu-id="0152e-196">This is the only time your **Service Key** will be displayed, so ensure you make a copy of it now.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="0152e-197">Capítulo 2: configurar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="0152e-197">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="0152e-198">Lo siguiente es una configuración típica para desarrollar con la realidad mixta y, como tal, es una buena plantilla para otros proyectos.</span><span class="sxs-lookup"><span data-stu-id="0152e-198">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="0152e-199">Abra *Unity* y haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="0152e-199">Open *Unity* and click **New**.</span></span>

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-11.png)

2.  <span data-ttu-id="0152e-201">Ahora tendrá que proporcionar un nombre de proyecto de Unity e insertar **Mr\_Azure\_Application\_Insights**.</span><span class="sxs-lookup"><span data-stu-id="0152e-201">You will now need to provide a Unity Project name, insert **MR\_Azure\_Application\_Insights**.</span></span> <span data-ttu-id="0152e-202">Asegúrese de que la *plantilla* está establecida en **3D**.</span><span class="sxs-lookup"><span data-stu-id="0152e-202">Make sure the *Template* is set to **3D**.</span></span> <span data-ttu-id="0152e-203">Establezca la *Ubicación* en algún lugar adecuado para usted (Recuerde que, más cerca de los directorios raíz es mejor).</span><span class="sxs-lookup"><span data-stu-id="0152e-203">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="0152e-204">A continuación, haga clic en **crear proyecto**.</span><span class="sxs-lookup"><span data-stu-id="0152e-204">Then, click **Create project**.</span></span>

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-12.png)

3.  <span data-ttu-id="0152e-206">Con Unity abierto, merece la pena comprobar que el **Editor** de scripts predeterminado está establecido en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="0152e-206">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="0152e-207">Vaya a **Editar \> preferencias** y, a continuación, en la nueva ventana, vaya a **herramientas externas**.</span><span class="sxs-lookup"><span data-stu-id="0152e-207">Go to **Edit \> Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="0152e-208">Cambie el **Editor de script externo** a **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="0152e-208">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="0152e-209">Cierre la ventana **preferencias** .</span><span class="sxs-lookup"><span data-stu-id="0152e-209">Close the **Preferences** window.</span></span>

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-13.png)

4.  <span data-ttu-id="0152e-211">A continuación, vaya **a \> configuración de compilación de archivos** y cambie la plataforma a **plataforma universal de Windows**, haciendo clic en el botón **cambiar plataforma** .</span><span class="sxs-lookup"><span data-stu-id="0152e-211">Next, go to **File \> Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-14.png)

5.  <span data-ttu-id="0152e-213">Vaya a **configuración \> de compilación de archivos** y asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="0152e-213">Go to **File \> Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="0152e-214">El **dispositivo de destino** se establece en **cualquier dispositivo**</span><span class="sxs-lookup"><span data-stu-id="0152e-214">**Target Device** is set to **Any device**</span></span>

        > <span data-ttu-id="0152e-215">Para Microsoft HoloLens, establezca el **dispositivo de destino** en *hololens*.</span><span class="sxs-lookup"><span data-stu-id="0152e-215">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="0152e-216">El **tipo de compilación** se establece en **D3D**</span><span class="sxs-lookup"><span data-stu-id="0152e-216">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="0152e-217">**SDK** está establecido en la **versión más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="0152e-217">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="0152e-218">**Compilar y ejecutar** está establecido en **equipo local**</span><span class="sxs-lookup"><span data-stu-id="0152e-218">**Build and Run** is set to **Local Machine**</span></span>

    5.  <span data-ttu-id="0152e-219">Guarde la escena y agréguela a la compilación.</span><span class="sxs-lookup"><span data-stu-id="0152e-219">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="0152e-220">Para ello, seleccione **Agregar escenas abiertas**.</span><span class="sxs-lookup"><span data-stu-id="0152e-220">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="0152e-221">Aparecerá una ventana de guardar.</span><span class="sxs-lookup"><span data-stu-id="0152e-221">A save window will appear.</span></span>

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-15.png)

        2. <span data-ttu-id="0152e-223">Cree una nueva carpeta para esta y cualquier escena futura, haga clic en el botón **nueva carpeta** para crear una nueva carpeta, asígnele el nombre **Scenes**.</span><span class="sxs-lookup"><span data-stu-id="0152e-223">Create a new folder for this, and any future scene, then click the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-16.png)

        3. <span data-ttu-id="0152e-225">Abra la carpeta Scenes recién creada y, a continuación, en el campo *nombre de archivo:* , escriba **ApplicationInsightsScene**y haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="0152e-225">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **ApplicationInsightsScene**, then click **Save**.</span></span>

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-17.png)

6.  <span data-ttu-id="0152e-227">El resto de la configuración, en la **configuración de compilación**, debe dejarse como predeterminada por ahora.</span><span class="sxs-lookup"><span data-stu-id="0152e-227">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

7.  <span data-ttu-id="0152e-228">En la ventana **configuración de compilación** , haga clic en el botón Configuración del **reproductor** ; se abrirá el panel relacionado en el espacio donde se encuentra el **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="0152e-228">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-18.png)

8. <span data-ttu-id="0152e-230">En este panel, deben comprobarse algunas opciones de configuración:</span><span class="sxs-lookup"><span data-stu-id="0152e-230">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="0152e-231">En la pestaña **otros valores** :</span><span class="sxs-lookup"><span data-stu-id="0152e-231">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="0152e-232">**Scripting** La **versión del tiempo de ejecución** debe ser **Experimental (.net 4,6 equivalente)** , lo que desencadenará una necesidad de reiniciar el editor.</span><span class="sxs-lookup"><span data-stu-id="0152e-232">**Scripting** **Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2.  <span data-ttu-id="0152e-233">El **back-end** de scripting debe ser **.net**</span><span class="sxs-lookup"><span data-stu-id="0152e-233">**Scripting Backend** should be **.NET**</span></span>

        3.  <span data-ttu-id="0152e-234">El **nivel de compatibilidad de API** debe ser **.net 4,6**</span><span class="sxs-lookup"><span data-stu-id="0152e-234">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-19.png)

    2.  <span data-ttu-id="0152e-236">En la pestaña **configuración de publicación** , en **capacidades**, seleccione:</span><span class="sxs-lookup"><span data-stu-id="0152e-236">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="0152e-237">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="0152e-237">**InternetClient**</span></span>     

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-20.png)

    3.  <span data-ttu-id="0152e-239">Más abajo en el panel, en la **configuración de XR** (se encuentra debajo de **configuración de publicación**), tick **Virtual Reality compatible**, asegúrese de que se agrega el **SDK de Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="0152e-239">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-21.png)

9.  <span data-ttu-id="0152e-241">De nuevo en la **configuración de compilación**, los **proyectos de Unity C#**  ya no están atenuados; Marque la casilla situada junto a este.</span><span class="sxs-lookup"><span data-stu-id="0152e-241">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span>

10.  <span data-ttu-id="0152e-242">Cierre la ventana Configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="0152e-242">Close the Build Settings window.</span></span>

11.  <span data-ttu-id="0152e-243">Guarde la escena y el proyecto (**archivo** > **Guardar escena/archivo** > **Guardar proyecto**).</span><span class="sxs-lookup"><span data-stu-id="0152e-243">Save your Scene and Project (**FILE** > **SAVE SCENE / FILE** > **SAVE PROJECT**).</span></span>


## <a name="chapter-3---import-the-unity-package"></a><span data-ttu-id="0152e-244">Capítulo 3: importación del paquete Unity</span><span class="sxs-lookup"><span data-stu-id="0152e-244">Chapter 3 - Import the Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0152e-245">Si desea omitir los componentes de *configuración de Unity* de este curso y continuar directamente en el código, no dude en descargar este [Azure-Mr-309. unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), impórtelo en el proyecto como un [**paquete personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="0152e-245">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to download this [Azure-MR-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="0152e-246">También contendrá los archivos DLL del siguiente capítulo.</span><span class="sxs-lookup"><span data-stu-id="0152e-246">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="0152e-247">Después de la importación, continúe en el [**capítulo 6**](#chapter-6---create-the-applicationinsightstracker-class).</span><span class="sxs-lookup"><span data-stu-id="0152e-247">After import, continue from [**Chapter 6**](#chapter-6---create-the-applicationinsightstracker-class).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0152e-248">Para usar Application Insights en Unity, debe importar el archivo DLL para él, junto con el archivo DLL de Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="0152e-248">To use Application Insights within Unity, you need to import the DLL for it, along with the Newtonsoft DLL.</span></span> <span data-ttu-id="0152e-249">Actualmente hay un problema conocido en Unity que requiere que los complementos se vuelvan a configurar después de la importación.</span><span class="sxs-lookup"><span data-stu-id="0152e-249">There is currently a known issue in Unity which requires plugins to be  reconfigured after import.</span></span> <span data-ttu-id="0152e-250">Estos pasos (4-7 en esta sección) ya no serán necesarios una vez resuelto el error.</span><span class="sxs-lookup"><span data-stu-id="0152e-250">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="0152e-251">Para importar Application Insights en su propio proyecto, asegúrese de que ha [descargado el ". unitypackage Tools", que contiene los complementos](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="0152e-251">To import Application Insights into your own project, make sure you have [downloaded the '.unitypackage', containing the plugins](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage).</span></span> <span data-ttu-id="0152e-252">A continuación, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="0152e-252">Then, do the following:</span></span>

1.  <span data-ttu-id="0152e-253">Agregue el **. unitypackage Tools** a Unity mediante la opción de menú de  **\> paquetes \> importar paquete personalizado** de paquetes.</span><span class="sxs-lookup"><span data-stu-id="0152e-253">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="0152e-254">En el cuadro **importar paquete Unity** que aparece, asegúrese de que todo lo que hay en **Complementos** (y incluido) está seleccionado.</span><span class="sxs-lookup"><span data-stu-id="0152e-254">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Importar el paquete de Unity](images/AzureLabs-Lab309-22.png)

3.  <span data-ttu-id="0152e-256">Haga clic en el botón **importar** para agregar los elementos al proyecto.</span><span class="sxs-lookup"><span data-stu-id="0152e-256">Click the **Import** button, to add the items to your project.</span></span>

4.  <span data-ttu-id="0152e-257">Vaya a la  carpeta Insights en **Complementos** en la vista de proyecto y seleccione *solo*los siguientes complementos:</span><span class="sxs-lookup"><span data-stu-id="0152e-257">Go to the **Insights** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="0152e-258">Microsoft. ApplicationInsights</span><span class="sxs-lookup"><span data-stu-id="0152e-258">Microsoft.ApplicationInsights</span></span>

    ![Importar el paquete de Unity](images/AzureLabs-Lab309-23.png)

5.  <span data-ttu-id="0152e-260">Con este *complemento* seleccionado, asegúrese de que **cualquier plataforma** esté desactivada, Asegúrese de que **WSAPlayer** también está desactivado y haga clic en **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="0152e-260">With this *plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="0152e-261">Para ello, solo hay que confirmar que los archivos están configurados correctamente.</span><span class="sxs-lookup"><span data-stu-id="0152e-261">Doing this is just to confirm that the files are configured correctly.</span></span>

    ![Importar el paquete de Unity](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > <span data-ttu-id="0152e-263">Al marcar los complementos de este modo, se configuran para que solo se usen en el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="0152e-263">Marking the plugins like this, configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="0152e-264">Hay un conjunto diferente de archivos dll en la carpeta WSA que se usarán después de exportar el proyecto desde Unity.</span><span class="sxs-lookup"><span data-stu-id="0152e-264">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="0152e-265">A continuación, debe abrir la carpeta **WSA** , dentro de la  carpeta Insights.</span><span class="sxs-lookup"><span data-stu-id="0152e-265">Next, you need to open the **WSA** folder, within the **Insights** folder.</span></span> <span data-ttu-id="0152e-266">Verá una copia del mismo archivo que acaba de configurar.</span><span class="sxs-lookup"><span data-stu-id="0152e-266">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="0152e-267">Seleccione este archivo y, a continuación, en el inspector, asegúrese de que  **cualquier plataforma** esté desactivada y, a continuación, asegúrese de que **solo** **WSAPlayer** está **activada**.</span><span class="sxs-lookup"><span data-stu-id="0152e-267">Select this file, and then in the inspector, ensure that **Any Platform** is **unchecked**, then ensure that **only** **WSAPlayer** is **checked**.</span></span> <span data-ttu-id="0152e-268">Haga clic en **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="0152e-268">Click **Apply**.</span></span>

    ![Importar el paquete de Unity](images/AzureLabs-Lab309-25.png)

7. <span data-ttu-id="0152e-270">Ahora tendrá que seguir **los pasos 4-6**, pero para los complementos de *Newtonsoft* en su lugar.</span><span class="sxs-lookup"><span data-stu-id="0152e-270">You will now need to follow **steps 4-6**, but for the *Newtonsoft* plugins instead.</span></span> <span data-ttu-id="0152e-271">Vea la captura de pantalla siguiente para saber cuál debe ser el resultado.</span><span class="sxs-lookup"><span data-stu-id="0152e-271">See the below screenshot for what the outcome should look like.</span></span>

    ![Importar el paquete de Unity](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a><span data-ttu-id="0152e-273">Capítulo 4: configurar la cámara y los controles de usuario</span><span class="sxs-lookup"><span data-stu-id="0152e-273">Chapter 4 - Set up the camera and user controls</span></span>

<span data-ttu-id="0152e-274">En este capítulo, configurará la cámara y los controles para que el usuario pueda ver y desplace en la escena.</span><span class="sxs-lookup"><span data-stu-id="0152e-274">In this Chapter you will set up the camera and the controls to allow the user to see and move in the scene.</span></span>

1.  <span data-ttu-id="0152e-275">Haga clic con el botón secundario en un área vacía del panel jerarquía y, después, en **crear** > **vacío**.</span><span class="sxs-lookup"><span data-stu-id="0152e-275">Right-click in an empty area in the Hierarchy Panel, then on **Create** > **Empty**.</span></span>

    ![Configurar la cámara y los controles de usuario](images/AzureLabs-Lab309-26.png)

2.  <span data-ttu-id="0152e-277">Cambie el nombre de la nueva GameObject vacía a **cámara primaria**.</span><span class="sxs-lookup"><span data-stu-id="0152e-277">Rename the new empty GameObject to **Camera Parent**.</span></span>

    ![Configurar la cámara y los controles de usuario](images/AzureLabs-Lab309-27.png)

3.  <span data-ttu-id="0152e-279">Haga clic con el botón secundario en un área vacía del panel de jerarquías y, después, en el **objeto 3D**, en **esfera**.</span><span class="sxs-lookup"><span data-stu-id="0152e-279">Right-click in an empty area in the Hierarchy Panel, then on **3D Object**, then on **Sphere**.</span></span>

4.  <span data-ttu-id="0152e-280">Cambie el nombre de la esfera a **derecha**.</span><span class="sxs-lookup"><span data-stu-id="0152e-280">Rename the Sphere to **Right Hand**.</span></span>

5.  <span data-ttu-id="0152e-281">Establezca la **escala de transformación** de la mano derecha en **0,1, 0,1, 0,1**</span><span class="sxs-lookup"><span data-stu-id="0152e-281">Set the **Transform Scale** of the Right Hand to **0.1, 0.1, 0.1**</span></span>

    ![Configurar la cámara y los controles de usuario](images/AzureLabs-Lab309-28.png)

6.  <span data-ttu-id="0152e-283">Quite el componente Colisionador de **esfera** de la mano derecha; para ello, haga clic en el **engranaje** del componente Colisionador de *esfera* y, a continuación, **Quite el componente**.</span><span class="sxs-lookup"><span data-stu-id="0152e-283">Remove the **Sphere Collider** component from the Right Hand by clicking on the **Gear** in the *Sphere Collider* component, and then **Remove Component**.</span></span>

    ![Configurar la cámara y los controles de usuario](images/AzureLabs-Lab309-29.png)

7.  <span data-ttu-id="0152e-285">En el panel jerarquía, arrastre la **cámara principal** y los objetos de la **mano derecha** al objeto primario de la **cámara** .</span><span class="sxs-lookup"><span data-stu-id="0152e-285">In the Hierarchy Panel drag the **Main Camera** and the **Right Hand** objects onto the **Camera Parent** object.</span></span>

    ![Configurar la cámara y los controles de usuario](images/AzureLabs-Lab309-30.png)

8.  <span data-ttu-id="0152e-287">Establezca la **posición de transformación** de la **cámara principal** y del objeto de la **derecha** en **0, 0,** 0.</span><span class="sxs-lookup"><span data-stu-id="0152e-287">Set the **Transform Position** of both the **Main Camera** and the **Right Hand** object to **0, 0, 0**.</span></span>

    ![Configurar la cámara y los controles de usuario](images/AzureLabs-Lab309-31.png)

    ![Configurar la cámara y los controles de usuario](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a><span data-ttu-id="0152e-290">Capítulo 5: configuración de los objetos de la escena de Unity</span><span class="sxs-lookup"><span data-stu-id="0152e-290">Chapter 5 - Set up the objects in the Unity scene</span></span>

<span data-ttu-id="0152e-291">Ahora creará algunas formas básicas para la escena, con las que el usuario puede interactuar.</span><span class="sxs-lookup"><span data-stu-id="0152e-291">You will now create some basic shapes for your scene, with which the user can interact.</span></span>

1.  <span data-ttu-id="0152e-292">Haga clic con el botón secundario en un área vacía del *Panel jerarquía*y, a continuación, en **objeto 3D**y seleccione **plano**.</span><span class="sxs-lookup"><span data-stu-id="0152e-292">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object**, then select **Plane**.</span></span>

2.  <span data-ttu-id="0152e-293">Establezca la posición de la **transformación** del plano en **0,-1, 0**.</span><span class="sxs-lookup"><span data-stu-id="0152e-293">Set the Plane **Transform Position** to **0, -1, 0**.</span></span>

3.  <span data-ttu-id="0152e-294">Establezca la escala de la **transformación** del plano en **5, 1, 5**.</span><span class="sxs-lookup"><span data-stu-id="0152e-294">Set the Plane **Transform Scale** to **5, 1, 5**.</span></span>

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-33.png)

4.  <span data-ttu-id="0152e-296">Cree un material básico para usarlo con el objeto de **plano** , de modo que las demás formas sean más fáciles de ver.</span><span class="sxs-lookup"><span data-stu-id="0152e-296">Create a basic material to use with your **Plane** object, so that the other shapes are easier to see.</span></span> <span data-ttu-id="0152e-297">Vaya al *panel del proyecto*, haga clic con el botón secundario y, a continuación, **cree**, seguido de la **carpeta**, para crear una nueva carpeta.</span><span class="sxs-lookup"><span data-stu-id="0152e-297">Navigate to your *Project Panel*, right-click, then **Create**, followed by **Folder**, to create a new folder.</span></span> <span data-ttu-id="0152e-298">Asígnele el nombre **materiales**.</span><span class="sxs-lookup"><span data-stu-id="0152e-298">Name it **Materials**.</span></span>

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-34.png) ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-35.png)

5.  <span data-ttu-id="0152e-301">Abra la carpeta **materiales** y, a continuación, haga clic con el botón secundario en, haga clic en **crear**y luego en **material**para crear un nuevo material.</span><span class="sxs-lookup"><span data-stu-id="0152e-301">Open the **Materials** folder, then right-click, click **Create**, then **Material**, to create a new material.</span></span> <span data-ttu-id="0152e-302">Asígnele el nombre **Blue**.</span><span class="sxs-lookup"><span data-stu-id="0152e-302">Name it **Blue**.</span></span>

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-36.png) ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-37.png)

6.  <span data-ttu-id="0152e-305">Con el nuevo material **azul** seleccionado, examine el *Inspector*y haga clic en la ventana rectangular junto a **Albedo**.</span><span class="sxs-lookup"><span data-stu-id="0152e-305">With the new **Blue** material selected, look at the *Inspector*, and click the rectangular window alongside **Albedo**.</span></span> <span data-ttu-id="0152e-306">Seleccione un color azul (la imagen siguiente es **el color hexadecimal: \#3592FFFF**).</span><span class="sxs-lookup"><span data-stu-id="0152e-306">Select a blue color (the one picture below is **Hex Color: \#3592FFFF**).</span></span> <span data-ttu-id="0152e-307">Haga clic en el botón cerrar cuando haya elegido.</span><span class="sxs-lookup"><span data-stu-id="0152e-307">Click the close button once you have chosen.</span></span>

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-38.png)

7.  <span data-ttu-id="0152e-309">Arrastre el nuevo material desde la carpeta **materiales** hasta el **plano**que acaba de crear, dentro de la escena (o colóquelo en el objeto de **plano** dentro de la *jerarquía*).</span><span class="sxs-lookup"><span data-stu-id="0152e-309">Drag your new material from the **Materials** folder, onto your newly created **Plane**, within your scene (or drop it on the **Plane** object within the *Hierarchy*).</span></span>

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-39.png)

8.  <span data-ttu-id="0152e-311">Haga clic con el botón secundario en un área vacía del *Panel jerarquía*y, a continuación, en **objeto 3D, cápsula**.</span><span class="sxs-lookup"><span data-stu-id="0152e-311">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Capsule**.</span></span>

    -  <span data-ttu-id="0152e-312">Con la **cápsula** seleccionada, cambie su  *posición* de transformación a: **-10, 1, 0**.</span><span class="sxs-lookup"><span data-stu-id="0152e-312">With the **Capsule** selected, change its **Transform** *Position* to: **-10, 1, 0**.</span></span>

9.  <span data-ttu-id="0152e-313">Haga clic con el botón secundario en un área vacía del *Panel jerarquía*y, a continuación, en **objeto 3D, cubo**.</span><span class="sxs-lookup"><span data-stu-id="0152e-313">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Cube**.</span></span>

    -  <span data-ttu-id="0152e-314">Con el **cubo** seleccionado, cambie su  *posición* de transformación a: **0, 0, 10**.</span><span class="sxs-lookup"><span data-stu-id="0152e-314">With the **Cube** selected, change its **Transform** *Position* to: **0, 0, 10**.</span></span>

10. <span data-ttu-id="0152e-315">Haga clic con el botón secundario en un área vacía del *Panel jerarquía*y, a continuación, en **objeto 3D, esfera**.</span><span class="sxs-lookup"><span data-stu-id="0152e-315">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Sphere**.</span></span>

    -  <span data-ttu-id="0152e-316">Con la **esfera** seleccionada, cambie su  *posición* de transformación a: **10, 0,0**.</span><span class="sxs-lookup"><span data-stu-id="0152e-316">With the **Sphere** selected, change its **Transform** *Position* to: **10, 0, 0**.</span></span>

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > <span data-ttu-id="0152e-318">Estos valores de *posición* son *sugerencias*.</span><span class="sxs-lookup"><span data-stu-id="0152e-318">These *Position* values are *suggestions*.</span></span> <span data-ttu-id="0152e-319">Puede establecer las posiciones de los objetos en el que desee, aunque es más fácil para el usuario de la aplicación si las distancias de los objetos no están demasiado lejos de la cámara.</span><span class="sxs-lookup"><span data-stu-id="0152e-319">You are free to set the positions of the objects to whatever you would like, though it is easier for the user of the application if the objects distances are not too far from the camera.</span></span>

11. <span data-ttu-id="0152e-320">Cuando la aplicación se está ejecutando, debe ser capaz de identificar los objetos dentro de la escena para lograrlo, es necesario etiquetarlos.</span><span class="sxs-lookup"><span data-stu-id="0152e-320">When your application is running, it needs to be able to identify the objects within the scene, to achieve this, they need to be tagged.</span></span> <span data-ttu-id="0152e-321">Seleccione uno de los objetos y, en el panel *Inspector* , haga clic en **Agregar etiqueta...** , que intercambiará el *Inspector* con las **etiquetas & panel capas** .</span><span class="sxs-lookup"><span data-stu-id="0152e-321">Select one of the objects, and in the *Inspector* panel, click **Add Tag...**, which will swap the *Inspector* with the **Tags & Layers** panel.</span></span>

    <span data-ttu-id="0152e-322">![Configurar los objetos de la escena](images/AzureLabs-Lab309-41.png) de Unity![](images/AzureLabs-Lab309-42.png)</span><span class="sxs-lookup"><span data-stu-id="0152e-322">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span></span>

12. <span data-ttu-id="0152e-323">Haga clic en el signo **+ (más)** y, a continuación, escriba el nombre de la etiqueta como **ObjectInScene**.</span><span class="sxs-lookup"><span data-stu-id="0152e-323">Click the **+ (plus)** symbol, then type the tag name as **ObjectInScene**.</span></span>

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > <span data-ttu-id="0152e-325">Si usa un nombre diferente para la etiqueta, deberá asegurarse de que este cambio también se convierte en los scripts de *DataFromAnalytics*, *ObjectTrigger*y *fijamente*más adelante, de modo que los objetos se encuentren y detecten dentro de la escena.</span><span class="sxs-lookup"><span data-stu-id="0152e-325">If you use a different name for your tag, you will need to ensure this change is also made the *DataFromAnalytics*, *ObjectTrigger*, and *Gaze*, scripts later, so that your objects are found, and detected, within your scene.</span></span>

13. <span data-ttu-id="0152e-326">Con la etiqueta creada, ahora debe aplicarla a los tres objetos.</span><span class="sxs-lookup"><span data-stu-id="0152e-326">With the tag created, you now need to apply it to all three of your objects.</span></span> <span data-ttu-id="0152e-327">En la *jerarquía*, mantenga presionada la tecla **MAYÚS** , haga clic en la **cápsula**, el **cubo**y la **esfera**, objetos y, después, en el *Inspector*, haga clic en el menú desplegable junto a **etiqueta**y, a continuación, haga clic en *ObjectInScene* etiqueta que creó.</span><span class="sxs-lookup"><span data-stu-id="0152e-327">From the *Hierarchy*, hold the **Shift** key, then click the **Capsule**, **Cube**, and **Sphere**, objects, then in the *Inspector*, click the dropdown menu alongside **Tag**, then click the *ObjectInScene* tag you created.</span></span>

    <span data-ttu-id="0152e-328">![Configurar los objetos de la escena](images/AzureLabs-Lab309-44.png) de Unity![](images/AzureLabs-Lab309-45.png)</span><span class="sxs-lookup"><span data-stu-id="0152e-328">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span></span>

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a><span data-ttu-id="0152e-329">Capítulo 6: crear la clase ApplicationInsightsTracker</span><span class="sxs-lookup"><span data-stu-id="0152e-329">Chapter 6 - Create the ApplicationInsightsTracker class</span></span>

<span data-ttu-id="0152e-330">El primer script que debe crear es **ApplicationInsightsTracker**, que es responsable de:</span><span class="sxs-lookup"><span data-stu-id="0152e-330">The first script you need to create is **ApplicationInsightsTracker**, which is responsible for:</span></span>

1.  <span data-ttu-id="0152e-331">Creación de eventos basados en interacciones de usuario para enviar a Aplicación de Azure Insights.</span><span class="sxs-lookup"><span data-stu-id="0152e-331">Creating events based on user interactions to submit to Azure Application Insights.</span></span>

2. <span data-ttu-id="0152e-332">Crear los nombres de evento adecuados, en función de la interacción del usuario.</span><span class="sxs-lookup"><span data-stu-id="0152e-332">Creating appropriate Event names, depending on user interaction.</span></span>

3. <span data-ttu-id="0152e-333">Enviar eventos a la instancia de servicio de Application Insights.</span><span class="sxs-lookup"><span data-stu-id="0152e-333">Submitting events to the Application Insights Service instance.</span></span>

<span data-ttu-id="0152e-334">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="0152e-334">To create this class:</span></span>

1.  <span data-ttu-id="0152e-335">Haga clic con el botón derecho en el *panel Proyecto*y, a continuación, en **crear** > **carpeta**.</span><span class="sxs-lookup"><span data-stu-id="0152e-335">Right-click in the *Project Panel*, then **Create** > **Folder**.</span></span> <span data-ttu-id="0152e-336">Asigne a la carpeta el nombre scripts.</span><span class="sxs-lookup"><span data-stu-id="0152e-336">Name the folder **Scripts**.</span></span>

    ![Crear la clase ApplicationInsightsTracker](images/AzureLabs-Lab309-46.png)  ![Crear la clase ApplicationInsightsTracker](images/AzureLabs-Lab309-47.png)

2.  <span data-ttu-id="0152e-339">Con la  carpeta scripts creada, haga doble clic en ella para abrirla.</span><span class="sxs-lookup"><span data-stu-id="0152e-339">With the **Scripts** folder created, double-click it, to open.</span></span> <span data-ttu-id="0152e-340">A continuación, en esa carpeta, haga clic con el botón secundario en **crear**  >   **C# script**.</span><span class="sxs-lookup"><span data-stu-id="0152e-340">Then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="0152e-341">Asigne al script el nombre **ApplicationInsightsTracker**.</span><span class="sxs-lookup"><span data-stu-id="0152e-341">Name the script **ApplicationInsightsTracker**.</span></span>

3.  <span data-ttu-id="0152e-342">Haga doble clic en el nuevo script **ApplicationInsightsTracker** para abrirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="0152e-342">Double-click on the new **ApplicationInsightsTracker** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="0152e-343">Actualice los espacios de nombres en la parte superior del script para que sea como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="0152e-343">Update namespaces at the top of the script to be as below:</span></span>

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  <span data-ttu-id="0152e-344">Dentro de la clase, inserte las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="0152e-344">Inside the class insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behavior like a singleton
        /// </summary>
        public static ApplicationInsightsTracker Instance;
        
        /// <summary>
        /// Insert your Instrumentation Key here
        /// </summary>
        internal string instrumentationKey = "Insert Instrumentation Key here";

        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        internal string applicationId = "Insert Application Id here";

        /// <summary>
        /// Insert your API Key here
        /// </summary>
        internal string API_Key = "Insert API Key here";

        /// <summary>
        /// Represent the Analytic Custom Event object
        /// </summary>
        private TelemetryClient telemetryClient;

        /// <summary>
        /// Represent the Analytic object able to host gaze duration
        /// </summary>
        private MetricTelemetry metric;
    ```

    > [!NOTE] 
    > <span data-ttu-id="0152e-345">Establezca los valores **instrumentationKey, ApplicationID y API_Key** de forma adecuada, con las *claves de servicio* de Azure portal, como se mencionó en el [capítulo 1](#chapter-1---the-azure-portal), en el paso 9, en adelante.</span><span class="sxs-lookup"><span data-stu-id="0152e-345">Set the **instrumentationKey, applicationId and API_Key** values appropriately, using the *Service Keys* from the Azure Portal as mentioned in [Chapter 1](#chapter-1---the-azure-portal), step 9 onwards.</span></span>

6.  <span data-ttu-id="0152e-346">A continuación, agregue los métodos **Start ()** y Activate **()** , a los que se llamará cuando se inicialice la clase:</span><span class="sxs-lookup"><span data-stu-id="0152e-346">Then add the **Start()** and **Awake()** methods, which will be called when the class initializes:</span></span>

    ```csharp
        /// <summary>
        /// Sets this class instance as a singleton
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Instantiate telemetry and metric
            telemetryClient = new TelemetryClient();

            metric = new MetricTelemetry();

            // Assign the Instrumentation Key to the Event and Metric objects
            TelemetryConfiguration.Active.InstrumentationKey = instrumentationKey;

            telemetryClient.InstrumentationKey = instrumentationKey;
        }
    ```

7.  <span data-ttu-id="0152e-347">Agregue los métodos responsables de enviar los eventos y las métricas registrados por la aplicación:</span><span class="sxs-lookup"><span data-stu-id="0152e-347">Add the methods responsible for sending the events and metrics registered by your application:</span></span>

    ```csharp
        /// <summary>
        /// Submit the Event to Azure Analytics using the event trigger object
        /// </summary>
        public void RecordProximityEvent(string objectName)
        {
            telemetryClient.TrackEvent(CreateEventName(objectName));
        }

        /// <summary>
        /// Uses the name of the object involved in the event to create 
        /// and return an Event Name convention
        /// </summary>
        public string CreateEventName(string name)
        {
            string eventName = $"User near {name}";
            return eventName;
        }

        /// <summary>
        /// Submit a Metric to Azure Analytics using the metric gazed object
        /// and the time count of the gaze
        /// </summary>
        public void RecordGazeMetrics(string objectName, int time)
        {
            // Output Console information about gaze.
            Debug.Log($"Finished gazing at {objectName}, which went for <b>{time}</b> second{(time != 1 ? "s" : "")}");

            metric.Name = $"Gazed {objectName}";

            metric.Value = time;

            telemetryClient.TrackMetric(metric);
        }
    ```

8.  <span data-ttu-id="0152e-348">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="0152e-348">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-7---create-the-gaze-script"></a><span data-ttu-id="0152e-349">Capítulo 7: creación del script de mira</span><span class="sxs-lookup"><span data-stu-id="0152e-349">Chapter 7 - Create the Gaze script</span></span>

<span data-ttu-id="0152e-350">El siguiente script que se va a  crear es el script de miras.</span><span class="sxs-lookup"><span data-stu-id="0152e-350">The next script to create is the **Gaze** script.</span></span> <span data-ttu-id="0152e-351">Este script es responsable de crear un *Raycast* que se proyectará hacia delante desde la *cámara principal*, para detectar qué objeto está examinando el usuario.</span><span class="sxs-lookup"><span data-stu-id="0152e-351">This script is responsible for creating a *Raycast* that will be projected forward from the *Main Camera*, to detect which object the user is looking at.</span></span> <span data-ttu-id="0152e-352">En este caso, *Raycast* deberá identificar si el usuario está viendo un objeto con la etiqueta **ObjectInScene** y, a continuación, contar cuánto tiempo el usuario *mira* el objeto.</span><span class="sxs-lookup"><span data-stu-id="0152e-352">In this case, the *Raycast* will need to identify if the user is looking at an object with the **ObjectInScene** tag, and then count how long the user *gazes* at that object.</span></span>

1.  <span data-ttu-id="0152e-353">Haga doble clic en la  carpeta scripts para abrirla.</span><span class="sxs-lookup"><span data-stu-id="0152e-353">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="0152e-354">Haga clic con el botón  derecho en la carpeta scripts y haga clic en **crear**  >   **C# script**.</span><span class="sxs-lookup"><span data-stu-id="0152e-354">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="0152e-355">Asigne un nombre **al script.**</span><span class="sxs-lookup"><span data-stu-id="0152e-355">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="0152e-356">Haga doble clic en el script para abrirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0152e-356">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="0152e-357">Reemplace el código existente por lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="0152e-357">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {
            /// <summary>
            /// Provides Singleton-like behavior to this class.
            /// </summary>
            public static Gaze Instance;

            /// <summary>
            /// Provides a reference to the object the user is currently looking at.
            /// </summary>
            public GameObject FocusedGameObject { get; private set; }

            /// <summary>
            /// Provides whether an object has been successfully hit by the raycast.
            /// </summary>
            public bool Hit { get; private set; }

            /// <summary>
            /// Provides a reference to compare whether the user is still looking at 
            /// the same object (and has not looked away).
            /// </summary>
            private GameObject _oldFocusedObject = null;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeMaxDistance = 300;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeTimeCounter = 0;

            /// <summary>
            /// The cursor object will be created when the app is running,
            /// this will store its values. 
            /// </summary>
            private GameObject _cursor;
        }
    ```

5.  <span data-ttu-id="0152e-358">Ahora es necesario agregar el código para los métodos **activo ()** e **Inicio ()** .</span><span class="sxs-lookup"><span data-stu-id="0152e-358">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton
            Instance = this;
            _cursor = CreateCursor();
        }

        void Start()
        {
            FocusedGameObject = null;
        }

        /// <summary>
        /// Create a cursor object, to provide what the user
        /// is looking at.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()    
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Remove the collider, so it does not block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());

            newCursor.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            newCursor.GetComponent<MeshRenderer>().material.color = 
            Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

            newCursor.SetActive(false);
            return newCursor;
        }
    ```

6.  <span data-ttu-id="0152e-359">Dentro de la clase **fijamente** , agregue el siguiente código en el método **Update ()** para proyectar un *Raycast* y detectar el acierto de destino:</span><span class="sxs-lookup"><span data-stu-id="0152e-359">Inside the **Gaze** class, add the following code in the **Update()** method to project a *Raycast* and detect the target hit:</span></span>

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        void Update()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedGameObject;

            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, _gazeMaxDistance);

            // Check whether raycast has hit.
            if (Hit == true)
            {
                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedGameObject = hitInfo.collider.gameObject;

                    // Lerp the cursor to the hit point, which helps to stabilize the gaze.
                    _cursor.transform.position = Vector3.Lerp(_cursor.transform.position, hitInfo.point, 0.6f);

                    _cursor.SetActive(true);
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedGameObject = null;

                    _cursor.SetActive(false);
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;

                _cursor.SetActive(false);
            }

            // Check whether the previous focused object is this same object. If so, reset the focused object.
            if (FocusedGameObject != _oldFocusedObject)
            {
                ResetFocusedObject();
            }
            // If they are the same, but are null, reset the counter. 
            else if (FocusedGameObject == null && _oldFocusedObject == null)
            {
                _gazeTimeCounter = 0;
            }
            // Count whilst the user continues looking at the same object.
            else
            {
                _gazeTimeCounter += Time.deltaTime;
            }
        }
    ```

7.  <span data-ttu-id="0152e-360">Agregue el método **ResetFocusedObject ()** para enviar datos a **Application Insights** cuando el usuario haya examinado un objeto.</span><span class="sxs-lookup"><span data-stu-id="0152e-360">Add the **ResetFocusedObject()** method, to send data to **Application Insights** when the user has looked at an object.</span></span>

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        public void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                // Only looking for objects with the correct tag.
                if (_oldFocusedObject.CompareTag("ObjectInScene"))
                {
                    // Turn the timer into an int, and ensure that more than zero time has passed.
                    int gazeAsInt = (int)_gazeTimeCounter;

                    if (gazeAsInt > 0)
                    {
                        //Record the object gazed and duration of gaze for Analytics
                        ApplicationInsightsTracker.Instance.RecordGazeMetrics(_oldFocusedObject.name, gazeAsInt);
                    }
                    //Reset timer
                    _gazeTimeCounter = 0;
                }
            }
        }
    ```

8.  <span data-ttu-id="0152e-361">Ya ha completado el script  de miras.</span><span class="sxs-lookup"><span data-stu-id="0152e-361">You have now completed the **Gaze** script.</span></span> <span data-ttu-id="0152e-362">Guarde los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="0152e-362">Save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8---create-the-objecttrigger-class"></a><span data-ttu-id="0152e-363">Capítulo 8: creación de la clase ObjectTrigger</span><span class="sxs-lookup"><span data-stu-id="0152e-363">Chapter 8 - Create the ObjectTrigger class</span></span>

<span data-ttu-id="0152e-364">El siguiente script que debe crear es **ObjectTrigger**, que es responsable de:</span><span class="sxs-lookup"><span data-stu-id="0152e-364">The next script you need to create is **ObjectTrigger**, which is responsible for:</span></span>

- <span data-ttu-id="0152e-365">Agregando componentes necesarios para la colisión a la cámara principal.</span><span class="sxs-lookup"><span data-stu-id="0152e-365">Adding components needed for collision to the Main Camera.</span></span>
- <span data-ttu-id="0152e-366">Detectar si la cámara está cerca de un objeto etiquetado como **ObjectInScene**.</span><span class="sxs-lookup"><span data-stu-id="0152e-366">Detecting if the camera is near an object tagged as **ObjectInScene**.</span></span>

<span data-ttu-id="0152e-367">Para crear el script:</span><span class="sxs-lookup"><span data-stu-id="0152e-367">To create the script:</span></span>

1.  <span data-ttu-id="0152e-368">Haga doble clic en la  carpeta scripts para abrirla.</span><span class="sxs-lookup"><span data-stu-id="0152e-368">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="0152e-369">Haga clic con el botón  derecho en la carpeta scripts y haga clic en **crear**  >   **C# script**.</span><span class="sxs-lookup"><span data-stu-id="0152e-369">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="0152e-370">Asigne al script el nombre **ObjectTrigger**.</span><span class="sxs-lookup"><span data-stu-id="0152e-370">Name the script **ObjectTrigger**.</span></span>

3.  <span data-ttu-id="0152e-371">Haga doble clic en el script para abrirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0152e-371">Double-click on the script to open it with Visual Studio.</span></span> <span data-ttu-id="0152e-372">Reemplace el código existente por lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="0152e-372">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;

        public class ObjectTrigger : MonoBehaviour
        {
            private void Start()
            {
                // Add the Collider and Rigidbody components, 
                // and set their respective settings. This allows for collision.
                gameObject.AddComponent<SphereCollider>().radius = 1.5f;

                gameObject.AddComponent<Rigidbody>().useGravity = false;
            }

            /// <summary>
            /// Triggered when an object with a collider enters this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionEnter(Collision collision)
            {
                CompareTriggerEvent(collision, true);
            }

            /// <summary>
            /// Triggered when an object with a collider exits this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionExit(Collision collision)
            {
                CompareTriggerEvent(collision, false);
            }

            /// <summary>
            /// Method for providing debug message, and sending event information to InsightsTracker.
            /// </summary>
            /// <param name="other">Collided object</param>
            /// <param name="enter">Enter = true, Exit = False</param>
            private void CompareTriggerEvent(Collision other, bool enter)
            {
                if (other.collider.CompareTag("ObjectInScene"))
                {
                    string message = $"User is{(enter == true ? " " : " no longer ")}near <b>{other.gameObject.name}</b>";

                    if (enter == true)
                    {
                        ApplicationInsightsTracker.Instance.RecordProximityEvent(other.gameObject.name);
                    }
                    Debug.Log(message);
                }
            }
        }
    ```

4.  <span data-ttu-id="0152e-373">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="0152e-373">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9---create-the-datafromanalytics-class"></a><span data-ttu-id="0152e-374">Capítulo 9: creación de la clase DataFromAnalytics</span><span class="sxs-lookup"><span data-stu-id="0152e-374">Chapter 9 - Create the DataFromAnalytics class</span></span>

<span data-ttu-id="0152e-375">Ahora tendrá que crear el script **DataFromAnalytics** , que es responsable de:</span><span class="sxs-lookup"><span data-stu-id="0152e-375">You will now need to create the **DataFromAnalytics** script, which is responsible for:</span></span>

- <span data-ttu-id="0152e-376">Recuperación de datos de análisis sobre qué objeto se ha aproximado a la cámara.</span><span class="sxs-lookup"><span data-stu-id="0152e-376">Fetching analytics data about which object has been approached by the camera the most.</span></span>
- <span data-ttu-id="0152e-377">Con las *claves de servicio*, que permiten la comunicación con la instancia de servicio de aplicación de Azure Insights.</span><span class="sxs-lookup"><span data-stu-id="0152e-377">Using the *Service Keys*, that allow communication with your Azure Application Insights Service instance.</span></span>
- <span data-ttu-id="0152e-378">Ordenar los objetos en la escena, según el número de eventos más alto.</span><span class="sxs-lookup"><span data-stu-id="0152e-378">Sorting the objects in scene, according to which has the highest event count.</span></span>
- <span data-ttu-id="0152e-379">Cambiar el color del material, del objeto más enfocado, a *verde*.</span><span class="sxs-lookup"><span data-stu-id="0152e-379">Changing the material color, of the most approached object, to *green*.</span></span>

<span data-ttu-id="0152e-380">Para crear el script:</span><span class="sxs-lookup"><span data-stu-id="0152e-380">To create the script:</span></span>

1.  <span data-ttu-id="0152e-381">Haga doble clic en la  carpeta scripts para abrirla.</span><span class="sxs-lookup"><span data-stu-id="0152e-381">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="0152e-382">Haga clic con el botón  derecho en la carpeta scripts y haga clic en **crear**  >   **C# script**.</span><span class="sxs-lookup"><span data-stu-id="0152e-382">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="0152e-383">Asigne al script el nombre **DataFromAnalytics**.</span><span class="sxs-lookup"><span data-stu-id="0152e-383">Name the script **DataFromAnalytics**.</span></span>

3.  <span data-ttu-id="0152e-384">Haga doble clic en el script para abrirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0152e-384">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="0152e-385">Inserte los espacios de nombres siguientes:</span><span class="sxs-lookup"><span data-stu-id="0152e-385">Insert the following namespaces:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="0152e-386">En el script, inserte lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="0152e-386">Inside the script, insert the following:</span></span>

    ```csharp
        /// <summary>
        /// Number of most recent events to be queried
        /// </summary>
        private int _quantityOfEventsQueried = 10;

        /// <summary>
        /// The timespan with which to query. Needs to be in hours.
        /// </summary>
        private int _timepspanAsHours = 24;

        /// <summary>
        /// A list of the objects in the scene
        /// </summary>
        private List<GameObject> _listOfGameObjectsInScene;

        /// <summary>
        /// Number of queries which have returned, after being sent.
        /// </summary>
        private int _queriesReturned = 0;

        /// <summary>
        /// List of GameObjects, as the Key, with their event count, as the Value.
        /// </summary>
        private List<KeyValuePair<GameObject, int>> _pairedObjectsWithEventCount = new List<KeyValuePair<GameObject, int>>();

        // Use this for initialization
        void Start()
        {
            // Find all objects in scene which have the ObjectInScene tag (as there may be other GameObjects in the scene which you do not want).
            _listOfGameObjectsInScene = GameObject.FindGameObjectsWithTag("ObjectInScene").ToList();

            FetchAnalytics();
        }
    ```

6.  <span data-ttu-id="0152e-387">Dentro de la clase **DataFromAnalytics** , justo después del método **Start ()** , agregue el siguiente método denominado **FetchAnalytics ()** .</span><span class="sxs-lookup"><span data-stu-id="0152e-387">Within the **DataFromAnalytics** class, right after the **Start()** method, add the following method called **FetchAnalytics()**.</span></span> <span data-ttu-id="0152e-388">Este método es responsable de rellenar la lista de pares clave-valor, con un *GameObject* y un número de recuento de eventos de marcador de posición.</span><span class="sxs-lookup"><span data-stu-id="0152e-388">This method is responsible for populating the list of key value pairs, with a *GameObject* and a placeholder event count number.</span></span> <span data-ttu-id="0152e-389">A continuación, inicializa la corutina **GetWebRequest ()** .</span><span class="sxs-lookup"><span data-stu-id="0152e-389">It then initializes the **GetWebRequest()** coroutine.</span></span> <span data-ttu-id="0152e-390">La estructura de la consulta de la llamada a *Application Insights* se puede encontrar también en este método, como punto de conexión de la *dirección URL* de la consulta.</span><span class="sxs-lookup"><span data-stu-id="0152e-390">The query structure of the call to *Application Insights* can be found within this method also, as the *Query URL* endpoint.</span></span>

    ```csharp
        private void FetchAnalytics()
        {
            // Iterate through the objects in the list
            for (int i = 0; i < _listOfGameObjectsInScene.Count; i++)
            {
                // The current event number is not known, so set it to zero.
                int eventCount = 0;

                // Add new pair to list, as placeholder, until eventCount is known.
                _pairedObjectsWithEventCount.Add(new KeyValuePair<GameObject, int>(_listOfGameObjectsInScene[i], eventCount));

                // Set the renderer of the object to the default color, white
                _listOfGameObjectsInScene[i].GetComponent<Renderer>().material.color = Color.white;

                // Create the appropriate object name using Insights structure
                string objectName = _listOfGameObjectsInScene[i].name;
 
                // Build the queryUrl for this object.
                string queryUrl = Uri.EscapeUriString(string.Format(
                    "https://api.applicationinsights.io/v1/apps/{0}/events/$all?timespan=PT{1}H&$search={2}&$select=customMetric/name&$top={3}&$count=true",
                    ApplicationInsightsTracker.Instance.applicationId, _timepspanAsHours, "Gazed " + objectName, _quantityOfEventsQueried));


                // Send this object away within the WebRequest Coroutine, to determine it is event count.
                StartCoroutine("GetWebRequest", new KeyValuePair<string, int>(queryUrl, i));
            }
        }
    ```

7.  <span data-ttu-id="0152e-391">Justo debajo del método **FetchAnalytics ()** , agregue un método denominado **GetWebRequest ()** , que devuelve una *IEnumerator*.</span><span class="sxs-lookup"><span data-stu-id="0152e-391">Right below the **FetchAnalytics()** method, add a method called **GetWebRequest()**, which returns an *IEnumerator*.</span></span> <span data-ttu-id="0152e-392">Este método es responsable de solicitar el número de veces que se ha llamado a un evento, que corresponde a un *GameObject*específico, dentro de *Application Insights*.</span><span class="sxs-lookup"><span data-stu-id="0152e-392">This method is responsible for requesting the number of times an event, corresponding with a specific *GameObject*, has been called within *Application Insights*.</span></span> <span data-ttu-id="0152e-393">Cuando se devuelven todas las consultas enviadas, se llama al método **DetermineWinner ()** .</span><span class="sxs-lookup"><span data-stu-id="0152e-393">When all the sent queries have returned, the **DetermineWinner()** method is called.</span></span>

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readibility).
            string url = webQueryPair.Key;
            int currentCount = webQueryPair.Value;

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(url))
            {
                DownloadHandlerBuffer handlerBuffer = new DownloadHandlerBuffer();

                unityWebRequest.downloadHandler = handlerBuffer;

                unityWebRequest.SetRequestHeader("host", "api.applicationinsights.io");

                unityWebRequest.SetRequestHeader("x-api-key", ApplicationInsightsTracker.Instance.API_Key);

                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError)
                {
                    // Failure with web request.
                    Debug.Log("<color=red>Error Sending:</color> " + unityWebRequest.error);
                }
                else
                {
                    // This query has returned, so add to the current count.
                    _queriesReturned++;

                    // Initialize event count integer.
                    int eventCount = 0;

                    // Deserialize the response with the custom Analytics class.
                    Analytics welcome = JsonConvert.DeserializeObject<Analytics>(unityWebRequest.downloadHandler.text);

                    // Get and return the count for the Event
                    if (int.TryParse(welcome.OdataCount, out eventCount) == false)
                    {
                        // Parsing failed. Can sometimes mean that the Query URL was incorrect.
                        Debug.Log("<color=red>Failure to Parse Data Results. Check Query URL for issues.</color>");
                    }
                    else
                    {
                        // Overwrite the current pair, with its actual values, now that the event count is known.
                        _pairedObjectsWithEventCount[currentCount] = new KeyValuePair<GameObject, int>(_pairedObjectsWithEventCount[currentCount].Key, eventCount);
                    }

                    // If all queries (compared with the number which was sent away) have 
                    // returned, then run the determine winner method. 
                    if (_queriesReturned == _pairedObjectsWithEventCount.Count)
                    {
                        DetermineWinner();
                    }
                }
            }
        }
    ```

8.  <span data-ttu-id="0152e-394">El siguiente método es **DetermineWinner ()** , que ordena la lista de pares *GameObject* e *int* , según el recuento de eventos más alto.</span><span class="sxs-lookup"><span data-stu-id="0152e-394">The next method is **DetermineWinner()**, which sorts the list of *GameObject* and *Int* pairs, according to the highest event count.</span></span> <span data-ttu-id="0152e-395">A continuación, cambia el color del material de ese *GameObject* a *verde* (como comentarios sobre el recuento más alto).</span><span class="sxs-lookup"><span data-stu-id="0152e-395">It then changes the material color of that *GameObject* to *green* (as feedback for it having the highest count).</span></span> <span data-ttu-id="0152e-396">Se muestra un mensaje con los resultados del análisis.</span><span class="sxs-lookup"><span data-stu-id="0152e-396">This displays a message with the analytics results.</span></span>

    ```csharp
        /// <summary>
        /// Call to determine the keyValue pair, within the objects list, 
        /// with the highest event count.
        /// </summary>
        private void DetermineWinner()
        {
            // Sort the values within the list of pairs.
            _pairedObjectsWithEventCount.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Change its colour to green
            _pairedObjectsWithEventCount.First().Key.GetComponent<Renderer>().material.color = Color.green;

            // Provide the winner, and other results, within the console window. 
            string message = $"<b>Analytics Results:</b>\n " +
                $"<i>{_pairedObjectsWithEventCount.First().Key.name}</i> has the highest event count, " +
                $"with <i>{_pairedObjectsWithEventCount.First().Value.ToString()}</i>.\nFollowed by: ";

            for (int i = 1; i < _pairedObjectsWithEventCount.Count; i++)
            {
                message += $"{_pairedObjectsWithEventCount[i].Key.name}, " +
                    $"with {_pairedObjectsWithEventCount[i].Value.ToString()} events.\n";
            }

            Debug.Log(message);
        }
    ```

9.  <span data-ttu-id="0152e-397">Agregue la estructura de clase que se usará para deserializar el objeto JSON, recibida de *Application Insights*.</span><span class="sxs-lookup"><span data-stu-id="0152e-397">Add the class structure which will be used to deserialize the JSON object, received from *Application Insights*.</span></span> <span data-ttu-id="0152e-398">Agregue estas clases en la parte inferior del archivo de la clase **DataFromAnalytics** , **fuera** de la definición de clase.</span><span class="sxs-lookup"><span data-stu-id="0152e-398">Add these classes at the very bottom of your **DataFromAnalytics** class file, **outside** of the class definition.</span></span>

    ```csharp
        /// <summary>
        /// These classes represent the structure of the JSON response from Azure Insight
        /// </summary>
        [Serializable]
        public class Analytics
        {
            [JsonProperty("@odata.context")]
            public string OdataContext { get; set; }

            [JsonProperty("@odata.count")]
            public string OdataCount { get; set; }

            [JsonProperty("value")]
            public Value[] Value { get; set; }
        }

        [Serializable]
        public class Value
        {
            [JsonProperty("customMetric")]
            public CustomMetric CustomMetric { get; set; }
        }

        [Serializable]
        public class CustomMetric
        {
            [JsonProperty("name")]
            public string Name { get; set; }
        }
    ```

10. <span data-ttu-id="0152e-399">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="0152e-399">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10---create-the-movement-class"></a><span data-ttu-id="0152e-400">Capítulo 10: creación de la clase movimiento</span><span class="sxs-lookup"><span data-stu-id="0152e-400">Chapter 10 - Create the Movement class</span></span>

<span data-ttu-id="0152e-401">El script de **movimiento** es el siguiente script que tendrá que crear.</span><span class="sxs-lookup"><span data-stu-id="0152e-401">The **Movement** script is the next script you will need to create.</span></span> <span data-ttu-id="0152e-402">Es responsable de:</span><span class="sxs-lookup"><span data-stu-id="0152e-402">It is responsible for:</span></span>

- <span data-ttu-id="0152e-403">Mover la cámara principal según la dirección que está buscando la cámara.</span><span class="sxs-lookup"><span data-stu-id="0152e-403">Moving the Main Camera according to the direction the camera is looking towards.</span></span>
- <span data-ttu-id="0152e-404">Agregar todos los demás scripts a los objetos de la escena.</span><span class="sxs-lookup"><span data-stu-id="0152e-404">Adding all other scripts to scene objects.</span></span>

<span data-ttu-id="0152e-405">Para crear el script:</span><span class="sxs-lookup"><span data-stu-id="0152e-405">To create the script:</span></span>

1.  <span data-ttu-id="0152e-406">Haga doble clic en la  carpeta scripts para abrirla.</span><span class="sxs-lookup"><span data-stu-id="0152e-406">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="0152e-407">Haga clic con el botón  derecho en la carpeta scripts y haga clic en **crear**  >   **C# script**.</span><span class="sxs-lookup"><span data-stu-id="0152e-407">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="0152e-408">Asigne un nombre al **movimiento**del script.</span><span class="sxs-lookup"><span data-stu-id="0152e-408">Name the script **Movement**.</span></span>

3.  <span data-ttu-id="0152e-409">Haga doble clic en el script para abrirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="0152e-409">Double-click on the script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="0152e-410">Reemplace el código existente por lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="0152e-410">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;

        public class Movement : MonoBehaviour
        {
            /// <summary>
            /// The rendered object representing the right controller.
            /// </summary>
            public GameObject Controller;

            /// <summary>
            /// The movement speed of the user.
            /// </summary>
            public float UserSpeed;

            /// <summary>
            /// Provides whether source updates have been registered.
            /// </summary>
            private bool _isAttached = false;

            /// <summary>
            /// The chosen controller hand to use. 
            /// </summary>
            private InteractionSourceHandedness _handness = InteractionSourceHandedness.Right;

            /// <summary>
            /// Used to calculate and proposes movement translation.
            /// </summary>
            private Vector3 _playerMovementTranslation;

            private void Start()
            {
                // You are now adding components dynamically 
                // to ensure they are existing on the correct object  

                // Add all camera related scripts to the camera. 
                Camera.main.gameObject.AddComponent<Gaze>();
                Camera.main.gameObject.AddComponent<ObjectTrigger>();
        
                // Add all other scripts to this object.
                gameObject.AddComponent<ApplicationInsightsTracker>();
                gameObject.AddComponent<DataFromAnalytics>();
            }

            // Update is called once per frame
            void Update()
            {
            
            }
        }
    ```

5.  <span data-ttu-id="0152e-411">Dentro de la clase de **movimiento** , *debajo* del método **Update ()** vacío, inserte los siguientes métodos que permiten al usuario usar el controlador de mano para desplazarse por el espacio virtual:</span><span class="sxs-lookup"><span data-stu-id="0152e-411">Within the **Movement** class, *below* the empty **Update()** method, insert the following methods that allow the user to use the hand controller to move in the virtual space:</span></span>

    ```csharp
        /// <summary>
        /// Used for tracking the current position and rotation of the controller.
        /// </summary>
        private void UpdateControllerState()
        {
    #if UNITY_WSA && UNITY_2017_2_OR_NEWER
            // Check for current connected controllers, only if WSA.
            string message = string.Empty;

            if (InteractionManager.GetCurrentReading().Length > 0)
            {
                foreach (var sourceState in InteractionManager.GetCurrentReading())
                {
                    if (sourceState.source.kind == InteractionSourceKind.Controller && sourceState.source.handedness == _handness)
                    {
                        // If a controller source is found, which matches the selected handness, 
                        // check whether interaction source updated events have been registered. 
                        if (_isAttached == false)
                        {
                            // Register events, as not yet registered.
                            message = "<color=green>Source Found: Registering Controller Source Events</color>";
                            _isAttached = true;

                            InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
                        }

                        // Update the position and rotation information for the controller.
                        Vector3 newPosition;
                        if (sourceState.sourcePose.TryGetPosition(out newPosition, InteractionSourceNode.Pointer) && ValidPosition(newPosition))
                        {
                            Controller.transform.localPosition = newPosition;
                        }

                        Quaternion newRotation;

                        if (sourceState.sourcePose.TryGetRotation(out newRotation, InteractionSourceNode.Pointer) && ValidRotation(newRotation))
                        {
                            Controller.transform.localRotation = newRotation;
                        }
                    }
                }
            }
            else
            {
                // Controller source not detected. 
                message = "<color=blue>Trying to detect controller source</color>";

                if (_isAttached == true)
                {
                    // A source was previously connected, however, has been lost. Disconnected
                    // all registered events. 

                    _isAttached = false;

                    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;

                    message = "<color=red>Source Lost: Detaching Controller Source Events</color>";
                }
            }

            if(message != string.Empty)
            {
                Debug.Log(message);
            }
    #endif
        }
    ```

    ```csharp
        /// <summary>
        /// This registered event is triggered when a source state has been updated.
        /// </summary>
        /// <param name="obj"></param>
        private void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
        {
            if (obj.state.source.handedness == _handness)
            {
                if(obj.state.thumbstickPosition.magnitude > 0.2f)
                {
                    float thumbstickY = obj.state.thumbstickPosition.y;

                    // Vertical Input.
                    if (thumbstickY > 0.3f || thumbstickY < -0.3f)
                    {
                        _playerMovementTranslation = Camera.main.transform.forward;
                        _playerMovementTranslation.y = 0;
                        transform.Translate(_playerMovementTranslation * UserSpeed * Time.deltaTime * thumbstickY, Space.World);
                    }
                }
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Check that controller position is valid. 
        /// </summary>
        /// <param name="inputVector3">The Vector3 to check</param>
        /// <returns>The position is valid</returns>
        private bool ValidPosition(Vector3 inputVector3)
        {
            return !float.IsNaN(inputVector3.x) && !float.IsNaN(inputVector3.y) && !float.IsNaN(inputVector3.z) && !float.IsInfinity(inputVector3.x) && !float.IsInfinity(inputVector3.y) && !float.IsInfinity(inputVector3.z);
        }

        /// <summary>
        /// Check that controller rotation is valid. 
        /// </summary>
        /// <param name="inputQuaternion">The Quaternion to check</param>
        /// <returns>The rotation is valid</returns>
        private bool ValidRotation(Quaternion inputQuaternion)
        {
            return !float.IsNaN(inputQuaternion.x) && !float.IsNaN(inputQuaternion.y) && !float.IsNaN(inputQuaternion.z) && !float.IsNaN(inputQuaternion.w) && !float.IsInfinity(inputQuaternion.x) && !float.IsInfinity(inputQuaternion.y) && !float.IsInfinity(inputQuaternion.z) && !float.IsInfinity(inputQuaternion.w);
        }   
    ```

6.  <span data-ttu-id="0152e-412">Por último, agregue la llamada al método en el método **Update ()** .</span><span class="sxs-lookup"><span data-stu-id="0152e-412">Lastly add the method call within the **Update()** method.</span></span>

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  <span data-ttu-id="0152e-413">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="0152e-413">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11---setting-up-the-scripts-references"></a><span data-ttu-id="0152e-414">Capítulo 11: configuración de las referencias de scripts</span><span class="sxs-lookup"><span data-stu-id="0152e-414">Chapter 11 - Setting up the scripts references</span></span>

<span data-ttu-id="0152e-415">En este capítulo, debe colocar el script de **movimiento** en el **elemento primario** de la cámara y establecer sus objetivos de referencia.</span><span class="sxs-lookup"><span data-stu-id="0152e-415">In this Chapter you need to place the **Movement** script onto the **Camera Parent** and set its reference targets.</span></span> <span data-ttu-id="0152e-416">Después, ese script controlará la colocación de los demás scripts en los que sea necesario.</span><span class="sxs-lookup"><span data-stu-id="0152e-416">That script will then handle placing the other scripts where they need to be.</span></span>

1.  <span data-ttu-id="0152e-417">En la  carpeta scripts del *panel Proyecto*, arrastre el script de **movimiento** hasta el objeto primario de la **cámara** , situado en el *Panel jerarquía*.</span><span class="sxs-lookup"><span data-stu-id="0152e-417">From the **Scripts** folder in the *Project Panel*, drag the **Movement** script to the **Camera Parent** object, located in the *Hierarchy Panel*.</span></span>

    ![Configuración de las referencias de scripts en la escena de Unity](images/AzureLabs-Lab309-48.png)

2.  <span data-ttu-id="0152e-419">Haga clic en el **elemento primario**de la cámara.</span><span class="sxs-lookup"><span data-stu-id="0152e-419">Click on the **Camera Parent**.</span></span> <span data-ttu-id="0152e-420">En el *Panel jerarquía*, arrastre el objeto **situado** a la derecha desde el *Panel jerarquía* hasta el destino de referencia, **controlador**, en el *panel Inspector*.</span><span class="sxs-lookup"><span data-stu-id="0152e-420">In the *Hierarchy Panel*, drag the **Right Hand** object from the *Hierarchy Panel* to the reference target, **Controller**, in the *Inspector Panel*.</span></span> <span data-ttu-id="0152e-421">Establezca la **velocidad del usuario** en **5**, tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="0152e-421">Set the **User Speed** to **5**, as shown in the image below.</span></span>

    ![Configuración de las referencias de scripts en la escena de Unity](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a><span data-ttu-id="0152e-423">Capítulo 12: compilar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="0152e-423">Chapter 12 - Build the Unity project</span></span>

<span data-ttu-id="0152e-424">Ya se ha completado todo lo necesario para la sección Unity de este proyecto, por lo que es el momento de compilarla desde Unity.</span><span class="sxs-lookup"><span data-stu-id="0152e-424">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="0152e-425">Vaya a **configuración de compilación**(**configuración de compilación**de**archivos** > ).</span><span class="sxs-lookup"><span data-stu-id="0152e-425">Navigate to **Build Settings**, (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="0152e-426">En la ventana **configuración de compilación** , haga clic en compilar.</span><span class="sxs-lookup"><span data-stu-id="0152e-426">From the **Build Settings** window, click **Build**.</span></span>

    ![Compilar el proyecto de Unity en la solución de UWP](images/AzureLabs-Lab309-50.png)

3.  <span data-ttu-id="0152e-428">Aparecerá una ventana del **Explorador de archivos** que le pedirá una ubicación para la compilación.</span><span class="sxs-lookup"><span data-stu-id="0152e-428">A **File Explorer** window will pop-up, prompting you for a location for the build.</span></span> <span data-ttu-id="0152e-429">Cree una nueva carpeta (haciendo clic en **nueva carpeta** en la esquina superior izquierda) y asígnele el nombre compilaciones.</span><span class="sxs-lookup"><span data-stu-id="0152e-429">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![Compilar el proyecto de Unity en la solución de UWP](images/AzureLabs-Lab309-51.png)

    1.  <span data-ttu-id="0152e-431">Abra la nueva  carpeta Compilaciones y cree otra carpeta (con la **nueva carpeta** una vez más) y asígnele el nombre **Mr\_\_Azure Application\_Insights**.</span><span class="sxs-lookup"><span data-stu-id="0152e-431">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **MR\_Azure\_Application\_Insights**.</span></span>

        ![Compilar el proyecto de Unity en la solución de UWP](images/AzureLabs-Lab309-52.png)

    2.  <span data-ttu-id="0152e-433">Con la **carpeta\_Mr\_de\_Azure Application Insights** seleccionada, haga clic en **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="0152e-433">With the **MR\_Azure\_Application\_Insights** folder selected, click **Select Folder**.</span></span> <span data-ttu-id="0152e-434">El proyecto tardará un minuto o más en compilarse.</span><span class="sxs-lookup"><span data-stu-id="0152e-434">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="0152e-435">Después de la *compilación*, aparecerá el **Explorador de archivos** que muestra la ubicación del nuevo proyecto.</span><span class="sxs-lookup"><span data-stu-id="0152e-435">Following *Build*, **File Explorer** will appear showing you the location of your new project.</span></span>

## <a name="chapter-13---deploy-mrazureapplicationinsights-app-to-your-machine"></a><span data-ttu-id="0152e-436">Capítulo 13: implementación de la aplicación MR_Azure_Application_Insights en el equipo</span><span class="sxs-lookup"><span data-stu-id="0152e-436">Chapter 13 - Deploy MR_Azure_Application_Insights app to your machine</span></span>

<span data-ttu-id="0152e-437">Para implementar la aplicación de **\_Azure\_\_Application Insights Mr** en el equipo local:</span><span class="sxs-lookup"><span data-stu-id="0152e-437">To deploy the **MR\_Azure\_Application\_Insights** app on your Local Machine:</span></span>

1.  <span data-ttu-id="0152e-438">Abra el archivo de solución de **la\_aplicación\_Mr\_de Azure Application Insights** en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="0152e-438">Open the solution file of your **MR\_Azure\_Application\_Insights** app in **Visual Studio**.</span></span>

2.  <span data-ttu-id="0152e-439">En la **plataforma**de la solución, seleccione **x86, equipo local**.</span><span class="sxs-lookup"><span data-stu-id="0152e-439">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="0152e-440">En la **configuración de soluciones** , seleccione Depurar.</span><span class="sxs-lookup"><span data-stu-id="0152e-440">In the **Solution Configuration** select **Debug**.</span></span>

    ![Compilar el proyecto de Unity en la solución de UWP](images/AzureLabs-Lab309-53.png)

4.  <span data-ttu-id="0152e-442">Vaya al **menú** compilar y haga clic en **implementar solución** para transferir localmente la aplicación a la máquina.</span><span class="sxs-lookup"><span data-stu-id="0152e-442">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="0152e-443">La aplicación debe aparecer ahora en la lista de aplicaciones instaladas, lista para iniciarse.</span><span class="sxs-lookup"><span data-stu-id="0152e-443">Your app should now appear in the list of installed apps, ready to be launched.</span></span>

6. <span data-ttu-id="0152e-444">Inicie la aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="0152e-444">Launch the mixed reality application.</span></span>

7. <span data-ttu-id="0152e-445">Desplazarse por la escena, cerca de los objetos y observando ellos, cuando el *servicio Azure Insights* haya recopilado suficientes datos de eventos, establecerá el objeto que se ha centrado más en verde.</span><span class="sxs-lookup"><span data-stu-id="0152e-445">Move around the scene, approaching objects and looking at them, when the *Azure Insight Service* has collected enough event data, it will set the object that has been approached the most to green.</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="0152e-446">Aunque el tiempo de espera promedio de los *eventos y* las métricas que va a recopilar el servicio tarda aproximadamente 15 minutos, en algunas ocasiones, puede tardar hasta 1 hora.</span><span class="sxs-lookup"><span data-stu-id="0152e-446">While the average waiting time for the *Events and Metrics* to be collected by the Service takes around 15 min, in some occasions it might take up to 1 hour.</span></span>

## <a name="chapter-14---the-application-insights-service-portal"></a><span data-ttu-id="0152e-447">Capítulo 14: portal de servicios de Application Insights</span><span class="sxs-lookup"><span data-stu-id="0152e-447">Chapter 14 - The Application Insights Service portal</span></span>

<span data-ttu-id="0152e-448">Una vez que haya movido en torno a la escena y haya mirado en varios objetos, puede ver los datos recopilados en el portal de *servicios de Application Insights* .</span><span class="sxs-lookup"><span data-stu-id="0152e-448">Once you have roamed around the scene and gazed at several objects you can see the data collected in the *Application Insights Service* portal.</span></span>

1.  <span data-ttu-id="0152e-449">Vuelva al portal de servicios de Application Insights.</span><span class="sxs-lookup"><span data-stu-id="0152e-449">Go back to your Application Insights Service portal.</span></span>

2.  <span data-ttu-id="0152e-450">Haga clic en *Explorador de métricas*.</span><span class="sxs-lookup"><span data-stu-id="0152e-450">Click on *Metrics Explorer*.</span></span>

    ![Examinar los datos recopilados](images/AzureLabs-Lab309-54.png)

3.  <span data-ttu-id="0152e-452">Se abrirá en una pestaña que contiene el gráfico que representa los *eventos y* las métricas relacionados con la aplicación.</span><span class="sxs-lookup"><span data-stu-id="0152e-452">It will open in a tab containing the graph which represent the *Events and Metrics* related to your application.</span></span> <span data-ttu-id="0152e-453">Como se mencionó anteriormente, es posible que se tarde un tiempo (hasta 1 hora) en mostrar los datos en el gráfico.</span><span class="sxs-lookup"><span data-stu-id="0152e-453">As mentioned above, it might take some time (up to 1 hour) for the data to be displayed in the graph</span></span>

    ![Examinar los datos recopilados](images/AzureLabs-Lab309-55.png)

4.  <span data-ttu-id="0152e-455">Haga clic en la *barra eventos* en el *total de eventos* por versión de la aplicación para ver un desglose detallado de los eventos con sus nombres.</span><span class="sxs-lookup"><span data-stu-id="0152e-455">Click on the *Events bar* in the *Total of Events* by Application Version, to see a detailed breakdown of the events with their names.</span></span>

    ![Examinar los datos recopilados](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a><span data-ttu-id="0152e-457">Su aplicación de servicio de Application Insights finalizada</span><span class="sxs-lookup"><span data-stu-id="0152e-457">Your finished your Application Insights Service application</span></span>

<span data-ttu-id="0152e-458">Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha el servicio de Application Insights para supervisar la actividad del usuario dentro de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="0152e-458">Congratulations, you built a mixed reality app that leverages the Application Insights Service to monitor user's activity within your app.</span></span>

![resultado del curso](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="0152e-460">Ejercicios de bonus</span><span class="sxs-lookup"><span data-stu-id="0152e-460">Bonus Exercises</span></span>

<span data-ttu-id="0152e-461">**Ejercicio 1**</span><span class="sxs-lookup"><span data-stu-id="0152e-461">**Exercise 1**</span></span>

<span data-ttu-id="0152e-462">Pruebe a generar, en lugar de crear manualmente, los objetos ObjectInScene y establecer sus coordenadas en el plano dentro de los scripts.</span><span class="sxs-lookup"><span data-stu-id="0152e-462">Try spawning, rather than manually creating, the ObjectInScene objects and set their coordinates on the plane within your scripts.</span></span> <span data-ttu-id="0152e-463">De esta manera, podría solicitar a Azure lo que era el objeto más popular (ya sea desde los resultados de mirarnos o de proximidad) y generar uno *extra* de esos objetos.</span><span class="sxs-lookup"><span data-stu-id="0152e-463">In this way, you could ask Azure what the most popular object was (either from gaze or proximity results) and spawn an *extra* one of those objects.</span></span>

<span data-ttu-id="0152e-464">**Ejercicio 2**</span><span class="sxs-lookup"><span data-stu-id="0152e-464">**Exercise 2**</span></span>

<span data-ttu-id="0152e-465">Ordene los resultados de la Application Insights por hora, para obtener los datos más relevantes e implementar esos datos confidenciales en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="0152e-465">Sort your Application Insights results by time, so that you get the most relevant data, and implement that time sensitive data in your application.</span></span>

