---
title: El Sr. y Azure 309 - Application insights
description: Realice este curso para obtener información sobre cómo recopilar análisis relacionadas con el comportamiento de los usuarios dentro de una aplicación de realidad mixta, mediante el servicio de Azure Application Insights.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidad mixta, Azure, academy, unity, tutorial, api, información de la aplicación, hololens, envolventes, vr
ms.openlocfilehash: e14a32f9a38e3e8f3054d19310782f7c2d4784a1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694569"
---
>[!NOTE]
><span data-ttu-id="a57d4-104">Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.</span><span class="sxs-lookup"><span data-stu-id="a57d4-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="a57d4-105">Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="a57d4-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="a57d4-106">Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.</span><span class="sxs-lookup"><span data-stu-id="a57d4-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="a57d4-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="a57d4-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="a57d4-108">Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="a57d4-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="a57d4-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.</span><span class="sxs-lookup"><span data-stu-id="a57d4-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

# <a name="mr-and-azure-309-application-insights"></a><span data-ttu-id="a57d4-110">El Sr. y Azure 309: Información de la aplicación</span><span class="sxs-lookup"><span data-stu-id="a57d4-110">MR and Azure 309: Application insights</span></span>

![final producto-inicio](images/AzureLabs-Lab309-00.png)

<span data-ttu-id="a57d4-112">En este curso, obtendrá información sobre cómo agregar funcionalidades de Application Insights a una aplicación de realidad mixta, mediante la API de Azure Application Insights para recopilar análisis de comportamiento del usuario.</span><span class="sxs-lookup"><span data-stu-id="a57d4-112">In this course, you will learn how to add Application Insights capabilities to a mixed reality application, using the Azure Application Insights API to collect analytics regarding user behavior.</span></span>

<span data-ttu-id="a57d4-113">Application Insights es un servicio de Microsoft, lo que permite a los desarrolladores recopilar análisis de sus aplicaciones y administrarla desde un portal fácil de usar.</span><span class="sxs-lookup"><span data-stu-id="a57d4-113">Application Insights is a Microsoft service, allowing developers to collect analytics from their applications and manage it from an easy-to-use portal.</span></span> <span data-ttu-id="a57d4-114">El análisis pueden ser cualquier cosa, desde rendimiento a la información personalizada que desea recopilar.</span><span class="sxs-lookup"><span data-stu-id="a57d4-114">The analytics can be anything from performance to custom information you would like to collect.</span></span> <span data-ttu-id="a57d4-115">Para obtener más información, visite la [página Application Insights](https://azure.microsoft.com/services/application-insights/).</span><span class="sxs-lookup"><span data-stu-id="a57d4-115">For more information, visit the [Application Insights page](https://azure.microsoft.com/services/application-insights/).</span></span>

<span data-ttu-id="a57d4-116">Una vez completado este curso, tendrá una aplicación de envolventes auriculares de realidad mixta que podrá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a57d4-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="a57d4-117">Permitir que el usuario que mirar y para desplazarse por una escena.</span><span class="sxs-lookup"><span data-stu-id="a57d4-117">Allow the user to gaze and move around a scene.</span></span>
2.  <span data-ttu-id="a57d4-118">Desencadenar el envío de análisis para el *servicio Application Insights*, mediante el uso de mirada y proximidad a los objetos en la escena.</span><span class="sxs-lookup"><span data-stu-id="a57d4-118">Trigger the sending of analytics to the *Application Insights Service*, through the use of Gaze and Proximity to in-scene objects.</span></span>
3.  <span data-ttu-id="a57d4-119">También llamará la aplicación en el servicio, la obtención de información acerca del objeto que ha sido abordó la mayor parte por el usuario, dentro de las últimas 24 horas.</span><span class="sxs-lookup"><span data-stu-id="a57d4-119">The app will also call upon the Service, fetching information about which object has been approached the most by the user, within the last 24 hours.</span></span> <span data-ttu-id="a57d4-120">Ese objeto cambiará su color en verde.</span><span class="sxs-lookup"><span data-stu-id="a57d4-120">That object will change its color to green.</span></span>

<span data-ttu-id="a57d4-121">Este curso le mostrará cómo obtener los resultados desde el servicio de Application Insights, en una aplicación de ejemplo basada en Unity.</span><span class="sxs-lookup"><span data-stu-id="a57d4-121">This course will teach you how to get the results from the Application Insights Service, into a Unity-based sample application.</span></span> <span data-ttu-id="a57d4-122">Será quien decide estos conceptos se aplican a una aplicación personalizada puede que esté creando.</span><span class="sxs-lookup"><span data-stu-id="a57d4-122">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="a57d4-123">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="a57d4-123">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="a57d4-124">Curso</span><span class="sxs-lookup"><span data-stu-id="a57d4-124">Course</span></span></th><th style="width:150px"> <span data-ttu-id="a57d4-125"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="a57d4-125"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="a57d4-126"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="a57d4-126"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="a57d4-127">El Sr. y Azure 309: Información de la aplicación</span><span class="sxs-lookup"><span data-stu-id="a57d4-127">MR and Azure 309: Application insights</span></span></td><td style="text-align: center;"> <span data-ttu-id="a57d4-128">✔️</span><span class="sxs-lookup"><span data-stu-id="a57d4-128">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="a57d4-129">✔️</span><span class="sxs-lookup"><span data-stu-id="a57d4-129">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="a57d4-130">Aunque este curso se centra principalmente en inmersivos (VR) Windows Mixed Reality, también puede aplicar lo aprendido en este curso de Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a57d4-130">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="a57d4-131">Como seguir el curso, verá notas en cualquier cambio que deberá emplear para admitir HoloLens.</span><span class="sxs-lookup"><span data-stu-id="a57d4-131">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="a57d4-132">Al usar HoloLens, es posible que observe algunos eco durante la captura de voz.</span><span class="sxs-lookup"><span data-stu-id="a57d4-132">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a57d4-133">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="a57d4-133">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="a57d4-134">Este tutorial está diseñado para los desarrolladores con experiencia básica con Unity y C#.</span><span class="sxs-lookup"><span data-stu-id="a57d4-134">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="a57d4-135">También Ten en cuenta que los requisitos previos y las instrucciones escritas en este documento representan lo que se ha probado y comprobado en el momento de redactar (julio de 2018).</span><span class="sxs-lookup"><span data-stu-id="a57d4-135">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="a57d4-136">Es libre de usar el software más reciente, como se muestra en el [instalar las herramientas de](install-the-tools.md) artículo, aunque no se debe suponer que la información de este curso perfectamente coincida con lo que encontrará en el software más reciente que se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="a57d4-136">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="a57d4-137">Se recomiendan el siguiente hardware y software para este curso:</span><span class="sxs-lookup"><span data-stu-id="a57d4-137">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="a57d4-138">Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desarrollo de auriculares envolvente (VR)</span><span class="sxs-lookup"><span data-stu-id="a57d4-138">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="a57d4-139">Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="a57d4-139">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="a57d4-140">El SDK más reciente de Windows 10</span><span class="sxs-lookup"><span data-stu-id="a57d4-140">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="a57d4-141">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="a57d4-141">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="a57d4-142">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="a57d4-142">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="a57d4-143">Un [auriculares de Windows Mixed Reality envolventes (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="a57d4-143">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="a57d4-144">Un conjunto de auriculares con micrófono integrado (si no tiene los auriculares altavoces y un micrófono integrado)</span><span class="sxs-lookup"><span data-stu-id="a57d4-144">A set of headphones with a built-in microphone (if the headset does not have a built-in mic and speakers)</span></span>
- <span data-ttu-id="a57d4-145">Acceso a Internet para el programa de instalación de Azure y la recuperación de datos de Application Insights</span><span class="sxs-lookup"><span data-stu-id="a57d4-145">Internet access for Azure setup and Application Insights data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="a57d4-146">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="a57d4-146">Before you start</span></span>

<span data-ttu-id="a57d4-147">Para evitar problemas de creación de este proyecto, se recomienda encarecidamente que cree el proyecto se ha mencionado en este tutorial en una carpeta raíz o cerca de la raíz (rutas de acceso de carpeta largo pueden causar problemas en tiempo de compilación).</span><span class="sxs-lookup"><span data-stu-id="a57d4-147">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

> [!WARNING] 
> <span data-ttu-id="a57d4-148">Tenga en cuenta, los datos que van a *Application Insights* lleva tiempo, así que los paciente.</span><span class="sxs-lookup"><span data-stu-id="a57d4-148">Be aware, data going to *Application Insights* takes time, so be patient.</span></span> <span data-ttu-id="a57d4-149">Si desea comprobar si el servicio ha recibido los datos, consulte [capítulo 14](#chapter-14---the-application-insights-service-portal), que le mostrará cómo navegar por el portal.</span><span class="sxs-lookup"><span data-stu-id="a57d4-149">If you want to check if the Service has received your data, check out [Chapter 14](#chapter-14---the-application-insights-service-portal), which will show you how to navigate the portal.</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="a57d4-150">Capítulo 1: el Portal de Azure</span><span class="sxs-lookup"><span data-stu-id="a57d4-150">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="a57d4-151">Para usar *Application Insights*, deberá crear y configurar un *servicio Application Insights* en Azure portal.</span><span class="sxs-lookup"><span data-stu-id="a57d4-151">To use *Application Insights*, you will need to create and configure an *Application Insights Service* in the Azure portal.</span></span>

1.  <span data-ttu-id="a57d4-152">Inicie sesión en el [Portal Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="a57d4-152">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="a57d4-153">Si no dispone de una cuenta de Azure, deberá crear uno.</span><span class="sxs-lookup"><span data-stu-id="a57d4-153">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="a57d4-154">Si está siguiendo este tutorial en una situación de aula o laboratorio, pida el instructor o uno de los a los supervisores de ayuda para instalar la nueva cuenta.</span><span class="sxs-lookup"><span data-stu-id="a57d4-154">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="a57d4-155">Una vez que haya iniciado sesión, haga clic en **New** en la esquina superior izquierda esquina y busque *Application Insights*y haga clic en **ENTRAR**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-155">Once you are logged in, click on **New** in the top left corner, and search for *Application Insights*, and click **Enter**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a57d4-156">La palabra **New** se han reemplazado con **crear un recurso**, en los portales más reciente.</span><span class="sxs-lookup"><span data-stu-id="a57d4-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-01.png)

3.  <span data-ttu-id="a57d4-158">La nueva página a la derecha proporcionará una descripción de la *Azure Application Insights* Service.</span><span class="sxs-lookup"><span data-stu-id="a57d4-158">The new page to the right will provide a description of the *Azure Application Insights* Service.</span></span> <span data-ttu-id="a57d4-159">En la parte inferior izquierda de esta página, seleccione el **crear** botón para crear una asociación con este servicio.</span><span class="sxs-lookup"><span data-stu-id="a57d4-159">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-02.png)

4.  <span data-ttu-id="a57d4-161">Una vez que ha hecho clic **crear**:</span><span class="sxs-lookup"><span data-stu-id="a57d4-161">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="a57d4-162">Insertar el elemento **nombre** para esta instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="a57d4-162">Insert your desired **Name** for this Service instance.</span></span>

    2.  <span data-ttu-id="a57d4-163">Como **tipo de aplicación**, seleccione **General**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-163">As **Application Type**, select **General**.</span></span>

    3.  <span data-ttu-id="a57d4-164">Seleccione un **suscripción**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-164">Select an appropriate **Subscription**.</span></span>

    4.  <span data-ttu-id="a57d4-165">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="a57d4-165">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="a57d4-166">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="a57d4-166">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="a57d4-167">Se recomienda que todos los servicios de Azure asociados con un único proyecto (por ejemplo, como estos cursos) en un grupo de recursos comunes).</span><span class="sxs-lookup"><span data-stu-id="a57d4-167">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="a57d4-168">Si desea leer más acerca de los grupos de recursos de Azure, inicie [visite el artículo del grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="a57d4-168">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5.  <span data-ttu-id="a57d4-169">Seleccione un **ubicación**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-169">Select a **Location**.</span></span>

    6.  <span data-ttu-id="a57d4-170">También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.</span><span class="sxs-lookup"><span data-stu-id="a57d4-170">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="a57d4-171">Selecciona **Crear**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-171">Select **Create**.</span></span>

        ![Azure Portal](images/AzureLabs-Lab309-03.png)

5.  <span data-ttu-id="a57d4-173">Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="a57d4-173">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="a57d4-174">Una vez creada la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="a57d4-174">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-04.png)

7.  <span data-ttu-id="a57d4-176">Haga clic en las notificaciones para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="a57d4-176">Click on the notifications to explore your new Service instance.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-05.png)

8.  <span data-ttu-id="a57d4-178">Haga clic en el **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="a57d4-178">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="a57d4-179">Se le dirigirá a la nueva *servicio Application Insights* instancia.</span><span class="sxs-lookup"><span data-stu-id="a57d4-179">You will be taken to your new *Application Insights Service* instance.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  <span data-ttu-id="a57d4-181">Mantenga abierta esta página web y de fácil acceso, procederá a este punto a menudo para ver los datos recopilados.</span><span class="sxs-lookup"><span data-stu-id="a57d4-181">Keep this web page open and easy to access, you will come back here often to see the data collected.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="a57d4-182">Para implementar Application Insights, deberá usar los valores específicos de tres (3): **Clave de instrumentación**, **Id. de aplicación**, y **clave de API**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-182">To implement Application Insights, you will need to use three (3) specific values: **Instrumentation Key**, **Application ID**, and **API Key**.</span></span> <span data-ttu-id="a57d4-183">A continuación verá cómo recuperar estos valores desde el servicio.</span><span class="sxs-lookup"><span data-stu-id="a57d4-183">Below you will see how to retrieve these values from your Service.</span></span> <span data-ttu-id="a57d4-184">Asegúrese de que tener en cuenta estos valores en un espacio en blanco *el Bloc de notas* página, ya que lo usará pronto en el código.</span><span class="sxs-lookup"><span data-stu-id="a57d4-184">Make sure to note these values on a blank *Notepad* page, because you will use them soon in your code.</span></span>

9.  <span data-ttu-id="a57d4-185">Para buscar el **clave de instrumentación**, deberá desplazarse hacia abajo en la lista de funciones de servicio y haga clic en **propiedades**, se mostrará la pestaña muestra la **clave de servicio**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-185">To find the **Instrumentation Key**, you will need to scroll down the list of Service functions, and click on **Properties**, the tab displayed will reveal the **Service Key**.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-07.png)

10. <span data-ttu-id="a57d4-187">Un poco a continuación **propiedades**, encontrará **acceso a la API**, que tiene que hacer clic.</span><span class="sxs-lookup"><span data-stu-id="a57d4-187">A little below **Properties**, you will find **API Access**, which you need to click.</span></span> <span data-ttu-id="a57d4-188">El panel a la derecha le proporcionará la **Id. de aplicación** de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a57d4-188">The panel to the right will provide the **Application ID** of your app.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-08.png)

11. <span data-ttu-id="a57d4-190">Con el **Id. de aplicación** panel sigue abierto, haga clic en **Create API Key**, que abrirá el *crear clave de API* panel.</span><span class="sxs-lookup"><span data-stu-id="a57d4-190">With the **Application ID** panel still open, click **Create API Key**, which will open the *Create API key* panel.</span></span>

    ![Azure Portal](images/AzureLabs-Lab309-09.png)

12. <span data-ttu-id="a57d4-192">Dentro de la apertura ahora *crear clave de API* del panel, escriba una descripción, y **los tres cuadros de graduación**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-192">Within the now open *Create API key* panel, type a description, and **tick the three boxes**.</span></span>

13. <span data-ttu-id="a57d4-193">Haga clic en **generar clave**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-193">Click **Generate Key**.</span></span> <span data-ttu-id="a57d4-194">Su **clave de API** se crean y se mostrará.</span><span class="sxs-lookup"><span data-stu-id="a57d4-194">Your **API Key** will be created and displayed.</span></span> 

    ![Azure Portal](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > <span data-ttu-id="a57d4-196">Esta es la única vez su **clave de servicio** se mostrará, así que asegúrese de realizar ahora una copia del mismo.</span><span class="sxs-lookup"><span data-stu-id="a57d4-196">This is the only time your **Service Key** will be displayed, so ensure you make a copy of it now.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="a57d4-197">Capítulo 2: configurar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="a57d4-197">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="a57d4-198">El siguiente es un conjunto típico de para el desarrollo con la realidad mixta y por lo tanto, es una buena plantilla para otros proyectos.</span><span class="sxs-lookup"><span data-stu-id="a57d4-198">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="a57d4-199">Abra *Unity* y haga clic en **New**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-199">Open *Unity* and click **New**.</span></span>

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-11.png)

2.  <span data-ttu-id="a57d4-201">Ahora deberá proporcionar un nombre de proyecto de Unity, insertar **MR\_Azure\_aplicación\_Insights**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-201">You will now need to provide a Unity Project name, insert **MR\_Azure\_Application\_Insights**.</span></span> <span data-ttu-id="a57d4-202">Asegúrese de que el *plantilla* está establecido en **3D**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-202">Make sure the *Template* is set to **3D**.</span></span> <span data-ttu-id="a57d4-203">Establecer el *ubicación* a algún lugar adecuado para usted (Recuerde, es mejor cuanto más se acerque a los directorios raíz).</span><span class="sxs-lookup"><span data-stu-id="a57d4-203">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="a57d4-204">A continuación, haga clic en **crear un proyecto**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-204">Then, click **Create project**.</span></span>

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-12.png)

3.  <span data-ttu-id="a57d4-206">Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-206">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="a57d4-207">Vaya a **editar \> preferencias** y, a continuación, en la ventana nueva, vaya a **herramientas externas**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-207">Go to **Edit \> Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="a57d4-208">Cambio **External Script Editor** a **de Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-208">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="a57d4-209">Cerrar la **preferencias** ventana.</span><span class="sxs-lookup"><span data-stu-id="a57d4-209">Close the **Preferences** window.</span></span>

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-13.png)

4.  <span data-ttu-id="a57d4-211">A continuación, vaya a **archivo \> configuración de compilación** y cambiar la plataforma a **Universal Windows Platform**, haciendo clic en el **Cambiar plataforma** botón.</span><span class="sxs-lookup"><span data-stu-id="a57d4-211">Next, go to **File \> Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-14.png)

5.  <span data-ttu-id="a57d4-213">Vaya a **archivo \> configuración de compilación** y asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="a57d4-213">Go to **File \> Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="a57d4-214">**Dispositivo de destino** está establecido en **cualquier dispositivo**</span><span class="sxs-lookup"><span data-stu-id="a57d4-214">**Target Device** is set to **Any device**</span></span>

        > <span data-ttu-id="a57d4-215">Para el Microsoft HoloLens, establezca **dispositivo de destino** a *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="a57d4-215">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="a57d4-216">**Tipo de compilación** está establecido en **D3D**</span><span class="sxs-lookup"><span data-stu-id="a57d4-216">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="a57d4-217">**SDK** está establecido en **instalada más reciente**</span><span class="sxs-lookup"><span data-stu-id="a57d4-217">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="a57d4-218">**Compilar y ejecutar** está establecido en **máquina Local**</span><span class="sxs-lookup"><span data-stu-id="a57d4-218">**Build and Run** is set to **Local Machine**</span></span>

    5.  <span data-ttu-id="a57d4-219">Guarde la escena y agregarlo a la compilación.</span><span class="sxs-lookup"><span data-stu-id="a57d4-219">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="a57d4-220">Hacer esto seleccionando **agregar escenas abierto**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-220">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="a57d4-221">Aparecerá el guardado de la ventana.</span><span class="sxs-lookup"><span data-stu-id="a57d4-221">A save window will appear.</span></span>

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-15.png)

        2. <span data-ttu-id="a57d4-223">Cree una nueva carpeta para este y cualquier futura escena, a continuación, haga clic en el **nueva carpeta** botón para crear una nueva carpeta y asígnele el nombre **escenas**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-223">Create a new folder for this, and any future scene, then click the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-16.png)

        3. <span data-ttu-id="a57d4-225">Abra su recién creado **escenas** carpeta y, a continuación, en el *nombre de archivo:* campo de texto, escriba **ApplicationInsightsScene**, a continuación, haga clic en **guardar**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-225">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **ApplicationInsightsScene**, then click **Save**.</span></span>

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-17.png)

6.  <span data-ttu-id="a57d4-227">El resto de la configuración, en **configuración de compilación**, debe dejarse como predeterminada por ahora.</span><span class="sxs-lookup"><span data-stu-id="a57d4-227">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

7.  <span data-ttu-id="a57d4-228">En el **configuración de compilación** ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el **Inspector** se encuentra.</span><span class="sxs-lookup"><span data-stu-id="a57d4-228">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-18.png)

8. <span data-ttu-id="a57d4-230">En este panel, es necesario comprobar algunas opciones de configuración:</span><span class="sxs-lookup"><span data-stu-id="a57d4-230">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="a57d4-231">En el **otra configuración** pestaña:</span><span class="sxs-lookup"><span data-stu-id="a57d4-231">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="a57d4-232">**Scripting** **en tiempo de ejecución versión** debe ser **Experimental (.NET 4.6 equivalente)** , que desencadenará una necesidad de reiniciar el Editor.</span><span class="sxs-lookup"><span data-stu-id="a57d4-232">**Scripting** **Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2.  <span data-ttu-id="a57d4-233">**Scripting de back-end** debe ser **.NET**</span><span class="sxs-lookup"><span data-stu-id="a57d4-233">**Scripting Backend** should be **.NET**</span></span>

        3.  <span data-ttu-id="a57d4-234">**Nivel de compatibilidad de API** debe ser **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="a57d4-234">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-19.png)

    2.  <span data-ttu-id="a57d4-236">Dentro de la **configuración de publicación** ficha **capacidades**, consulte:</span><span class="sxs-lookup"><span data-stu-id="a57d4-236">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="a57d4-237">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="a57d4-237">**InternetClient**</span></span>     

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-20.png)

    3.  <span data-ttu-id="a57d4-239">Más abajo el panel, en **XR configuración** (bajo **configuración de publicación**), graduación **admite la realidad Virtual**, asegúrese de que el **Windows Mixed Reality SDK** se agrega.</span><span class="sxs-lookup"><span data-stu-id="a57d4-239">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Configurar el proyecto de Unity](images/AzureLabs-Lab309-21.png)

9.  <span data-ttu-id="a57d4-241">En **configuración de compilación**, **Unity C# proyectos** ya no está atenuada; Marque la casilla situada junto a esto.</span><span class="sxs-lookup"><span data-stu-id="a57d4-241">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span>

10.  <span data-ttu-id="a57d4-242">Cierre la ventana de configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="a57d4-242">Close the Build Settings window.</span></span>

11.  <span data-ttu-id="a57d4-243">Guarde la escena y el proyecto (**archivo** > **guardar ESCENA / archivo** > **Guardar proyecto**).</span><span class="sxs-lookup"><span data-stu-id="a57d4-243">Save your Scene and Project (**FILE** > **SAVE SCENE / FILE** > **SAVE PROJECT**).</span></span>


## <a name="chapter-3---import-the-unity-package"></a><span data-ttu-id="a57d4-244">Capítulo 3: importar el paquete de Unity</span><span class="sxs-lookup"><span data-stu-id="a57d4-244">Chapter 3 - Import the Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a57d4-245">Si desea omitir la *configurar Unity* componentes de este curso y continuar directamente en código, no dude en descargar este [MR-Azure-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), importarlo en el proyecto como un [ **Paquete personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html).</span><span class="sxs-lookup"><span data-stu-id="a57d4-245">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to download this [Azure-MR-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="a57d4-246">Esto también contendrá los archivos DLL en el capítulo siguiente.</span><span class="sxs-lookup"><span data-stu-id="a57d4-246">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="a57d4-247">Después de la importación, continuar desde [ **capítulo 6**](#chapter-6---create-the-applicationinsightstracker-class).</span><span class="sxs-lookup"><span data-stu-id="a57d4-247">After import, continue from [**Chapter 6**](#chapter-6---create-the-applicationinsightstracker-class).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a57d4-248">Para usar Application Insights en Unity, deberá importar el archivo DLL, junto con la DLL de Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="a57d4-248">To use Application Insights within Unity, you need to import the DLL for it, along with the Newtonsoft DLL.</span></span> <span data-ttu-id="a57d4-249">Actualmente hay un problema conocido en Unity que requiere complementos volver a configurar tras la importación.</span><span class="sxs-lookup"><span data-stu-id="a57d4-249">There is currently a known issue in Unity which requires plugins to be  reconfigured after import.</span></span> <span data-ttu-id="a57d4-250">Estos pasos (4-7 en esta sección) ya no será necesarios una vez que se ha resuelto el error.</span><span class="sxs-lookup"><span data-stu-id="a57d4-250">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="a57d4-251">Para importar Application Insights en su propio proyecto, asegúrese de que haya [descargado '.unitypackage', que contiene los complementos](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="a57d4-251">To import Application Insights into your own project, make sure you have [downloaded the '.unitypackage', containing the plugins](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage).</span></span> <span data-ttu-id="a57d4-252">A continuación, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a57d4-252">Then, do the following:</span></span>

1.  <span data-ttu-id="a57d4-253">Agregar el **.unitypackage** a Unity mediante el uso de la **activos \> Importar paquete \> paquete personalizado** opción de menú.</span><span class="sxs-lookup"><span data-stu-id="a57d4-253">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="a57d4-254">En el **Importar paquete de Unity** cuadro que aparece hacia arriba, asegúrese de todo el contenido en (e incluido) **complementos** está seleccionada.</span><span class="sxs-lookup"><span data-stu-id="a57d4-254">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Importar el paquete de Unity](images/AzureLabs-Lab309-22.png)

3.  <span data-ttu-id="a57d4-256">Haga clic en el **importación** botón para agregar los elementos al proyecto.</span><span class="sxs-lookup"><span data-stu-id="a57d4-256">Click the **Import** button, to add the items to your project.</span></span>

4.  <span data-ttu-id="a57d4-257">Vaya a la **Insights** carpeta bajo **complementos** en el proyecto, ver y seleccione los siguientes complementos *sólo*:</span><span class="sxs-lookup"><span data-stu-id="a57d4-257">Go to the **Insights** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="a57d4-258">Microsoft.ApplicationInsights</span><span class="sxs-lookup"><span data-stu-id="a57d4-258">Microsoft.ApplicationInsights</span></span>

    ![Importar el paquete de Unity](images/AzureLabs-Lab309-23.png)

5.  <span data-ttu-id="a57d4-260">Con esto *complemento* seleccionado, asegúrese de que **cualquier plataforma** es **desactivada**, a continuación, asegúrese de que **WSAPlayer** también es  **unchecked**, a continuación, haga clic en **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-260">With this *plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="a57d4-261">Esto es solo para confirmar que los archivos están configurados correctamente.</span><span class="sxs-lookup"><span data-stu-id="a57d4-261">Doing this is just to confirm that the files are configured correctly.</span></span>

    ![Importar el paquete de Unity](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > <span data-ttu-id="a57d4-263">Marcar los complementos como esta, configura que solo se utilicen en el Editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="a57d4-263">Marking the plugins like this, configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="a57d4-264">Hay un conjunto diferente de DLL en la carpeta WSA que se utilizará después de que el proyecto se exporta desde Unity.</span><span class="sxs-lookup"><span data-stu-id="a57d4-264">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="a57d4-265">A continuación, deberá abrir el **WSA** carpeta, en el **Insights** carpeta.</span><span class="sxs-lookup"><span data-stu-id="a57d4-265">Next, you need to open the **WSA** folder, within the **Insights** folder.</span></span> <span data-ttu-id="a57d4-266">Verá una copia del mismo archivo que acaba de configurar.</span><span class="sxs-lookup"><span data-stu-id="a57d4-266">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="a57d4-267">Seleccione este archivo y, a continuación, en el inspector, asegúrese de que **cualquier plataforma** es **unchecked**, a continuación, asegúrese de que **sólo** **WSAPlayer** es **comprueban**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-267">Select this file, and then in the inspector, ensure that **Any Platform** is **unchecked**, then ensure that **only** **WSAPlayer** is **checked**.</span></span> <span data-ttu-id="a57d4-268">Haga clic en **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-268">Click **Apply**.</span></span>

    ![Importar el paquete de Unity](images/AzureLabs-Lab309-25.png)

7. <span data-ttu-id="a57d4-270">Ahora deberá seguir **los pasos 4 a 6**, pero para el *Newtonsoft* complementos en su lugar.</span><span class="sxs-lookup"><span data-stu-id="a57d4-270">You will now need to follow **steps 4-6**, but for the *Newtonsoft* plugins instead.</span></span> <span data-ttu-id="a57d4-271">Consulte la siguiente captura de pantalla de aspecto que debería tener el resultado.</span><span class="sxs-lookup"><span data-stu-id="a57d4-271">See the below screenshot for what the outcome should look like.</span></span>

    ![Importar el paquete de Unity](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a><span data-ttu-id="a57d4-273">Capítulo 4: configuración de la cámara y el usuario controles</span><span class="sxs-lookup"><span data-stu-id="a57d4-273">Chapter 4 - Set up the camera and user controls</span></span>

<span data-ttu-id="a57d4-274">En este capítulo configurará la cámara y los controles para permitir al usuario ver y mover de la escena.</span><span class="sxs-lookup"><span data-stu-id="a57d4-274">In this Chapter you will set up the camera and the controls to allow the user to see and move in the scene.</span></span>

1.  <span data-ttu-id="a57d4-275">Haga doble clic en un área vacía en el Panel de la jerarquía, a continuación, en **crear** > **vacía**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-275">Right-click in an empty area in the Hierarchy Panel, then on **Create** > **Empty**.</span></span>

    ![Configuración de la cámara y los controles de usuario](images/AzureLabs-Lab309-26.png)

2.  <span data-ttu-id="a57d4-277">Cambiar el nombre del nuevo GameObject vacío a **cámara primaria**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-277">Rename the new empty GameObject to **Camera Parent**.</span></span>

    ![Configuración de la cámara y los controles de usuario](images/AzureLabs-Lab309-27.png)

3.  <span data-ttu-id="a57d4-279">Haga doble clic en un área vacía en el Panel de la jerarquía, a continuación, en **objeto 3D**, a continuación, en **esfera**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-279">Right-click in an empty area in the Hierarchy Panel, then on **3D Object**, then on **Sphere**.</span></span>

4.  <span data-ttu-id="a57d4-280">Cambiar el nombre de la esfera **derecho**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-280">Rename the Sphere to **Right Hand**.</span></span>

5.  <span data-ttu-id="a57d4-281">Establecer el **transformar escala** de la mano derecha para **0,1, 0,1, 0,1**</span><span class="sxs-lookup"><span data-stu-id="a57d4-281">Set the **Transform Scale** of the Right Hand to **0.1, 0.1, 0.1**</span></span>

    ![Configuración de la cámara y los controles de usuario](images/AzureLabs-Lab309-28.png)

6.  <span data-ttu-id="a57d4-283">Quitar el **esfera Colisionador** componente desde el lado derecho, haga clic en el **engranaje** en el *esfera Colisionador* componente y, a continuación, **quitar componente** .</span><span class="sxs-lookup"><span data-stu-id="a57d4-283">Remove the **Sphere Collider** component from the Right Hand by clicking on the **Gear** in the *Sphere Collider* component, and then **Remove Component**.</span></span>

    ![Configuración de la cámara y los controles de usuario](images/AzureLabs-Lab309-29.png)

7.  <span data-ttu-id="a57d4-285">En la operación de arrastrar al Panel de la jerarquía la **cámara principal** y **mano derecha** objetos la **cámara primaria** objeto.</span><span class="sxs-lookup"><span data-stu-id="a57d4-285">In the Hierarchy Panel drag the **Main Camera** and the **Right Hand** objects onto the **Camera Parent** object.</span></span>

    ![Configuración de la cámara y los controles de usuario](images/AzureLabs-Lab309-30.png)

8.  <span data-ttu-id="a57d4-287">Establecer el **posición transformar** de ambos el **cámara principal** y el **mano derecha** objeto **0, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-287">Set the **Transform Position** of both the **Main Camera** and the **Right Hand** object to **0, 0, 0**.</span></span>

    ![Configuración de la cámara y los controles de usuario](images/AzureLabs-Lab309-31.png)

    ![Configuración de la cámara y los controles de usuario](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a><span data-ttu-id="a57d4-290">Capítulo 5: configurar los objetos de la escena de Unity</span><span class="sxs-lookup"><span data-stu-id="a57d4-290">Chapter 5 - Set up the objects in the Unity scene</span></span>

<span data-ttu-id="a57d4-291">Ahora creará algunas formas básicas para la escena, con el que el usuario puede interactuar.</span><span class="sxs-lookup"><span data-stu-id="a57d4-291">You will now create some basic shapes for your scene, with which the user can interact.</span></span>

1.  <span data-ttu-id="a57d4-292">Haga clic en un área vacía en el *jerarquía Panel*, a continuación, en **objeto 3D**, a continuación, seleccione **plano**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-292">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object**, then select **Plane**.</span></span>

2.  <span data-ttu-id="a57d4-293">Definir el plano **transformar posición** a **0, -1, 0**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-293">Set the Plane **Transform Position** to **0, -1, 0**.</span></span>

3.  <span data-ttu-id="a57d4-294">Definir el plano **transformar escala** a **5, 1, 5**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-294">Set the Plane **Transform Scale** to **5, 1, 5**.</span></span>

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-33.png)

4.  <span data-ttu-id="a57d4-296">Crear un material básico para usar con su **plano** objeto, para que sean fáciles de ver las demás formas.</span><span class="sxs-lookup"><span data-stu-id="a57d4-296">Create a basic material to use with your **Plane** object, so that the other shapes are easier to see.</span></span> <span data-ttu-id="a57d4-297">Vaya a su *Panel proyecto*, con el botón secundario, a continuación, **crear**, seguido de **carpeta**, para crear una nueva carpeta.</span><span class="sxs-lookup"><span data-stu-id="a57d4-297">Navigate to your *Project Panel*, right-click, then **Create**, followed by **Folder**, to create a new folder.</span></span> <span data-ttu-id="a57d4-298">Asígnele el nombre **materiales**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-298">Name it **Materials**.</span></span>

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-34.png) ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-35.png)

5.  <span data-ttu-id="a57d4-301">Abrir el **materiales** carpeta y, a continuación, haga clic **crear**, a continuación, **Material**, para crear un nuevo material.</span><span class="sxs-lookup"><span data-stu-id="a57d4-301">Open the **Materials** folder, then right-click, click **Create**, then **Material**, to create a new material.</span></span> <span data-ttu-id="a57d4-302">Asígnele el nombre **azul**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-302">Name it **Blue**.</span></span>

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-36.png) ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-37.png)

6.  <span data-ttu-id="a57d4-305">Con el nuevo **azul** material seleccionado, busque en el *Inspector*y haga clic en la ventana rectangular junto con **Albedo**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-305">With the new **Blue** material selected, look at the *Inspector*, and click the rectangular window alongside **Albedo**.</span></span> <span data-ttu-id="a57d4-306">Seleccione un color azul (es la siguiente uno imagen **de Color hexadecimal: \#3592FFFF**).</span><span class="sxs-lookup"><span data-stu-id="a57d4-306">Select a blue color (the one picture below is **Hex Color: \#3592FFFF**).</span></span> <span data-ttu-id="a57d4-307">Haga clic en el botón Cerrar cuando haya elegido.</span><span class="sxs-lookup"><span data-stu-id="a57d4-307">Click the close button once you have chosen.</span></span>

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-38.png)

7.  <span data-ttu-id="a57d4-309">Arrastre el nuevo material de la **materiales** carpeta, en la recién creado **plano**, dentro de su escena (o colóquela en la **plano** objeto dentro de la  *Jerarquía*).</span><span class="sxs-lookup"><span data-stu-id="a57d4-309">Drag your new material from the **Materials** folder, onto your newly created **Plane**, within your scene (or drop it on the **Plane** object within the *Hierarchy*).</span></span>

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-39.png)

8.  <span data-ttu-id="a57d4-311">Haga clic en un área vacía en el *jerarquía Panel*, a continuación, en **objeto 3D, Capsule**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-311">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Capsule**.</span></span>

    -  <span data-ttu-id="a57d4-312">Con el **Capsule** seleccionado, cambie su **transformar** *posición* a: **-10, 1, 0**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-312">With the **Capsule** selected, change its **Transform** *Position* to: **-10, 1, 0**.</span></span>

9.  <span data-ttu-id="a57d4-313">Haga clic en un área vacía en el *jerarquía Panel*, a continuación, en **objeto 3D, cubo**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-313">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Cube**.</span></span>

    -  <span data-ttu-id="a57d4-314">Con el **cubo** seleccionado, cambie su **transformar** *posición* para: **0, 0, 10**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-314">With the **Cube** selected, change its **Transform** *Position* to: **0, 0, 10**.</span></span>

10. <span data-ttu-id="a57d4-315">Haga clic en un área vacía en el *jerarquía Panel*, a continuación, en **objeto 3D, esfera**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-315">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Sphere**.</span></span>

    -  <span data-ttu-id="a57d4-316">Con el **esfera** seleccionado, cambie su **transformar** *posición* para: **10, 0, 0**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-316">With the **Sphere** selected, change its **Transform** *Position* to: **10, 0, 0**.</span></span>

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > <span data-ttu-id="a57d4-318">Estos *posición* los valores son *sugerencias*.</span><span class="sxs-lookup"><span data-stu-id="a57d4-318">These *Position* values are *suggestions*.</span></span> <span data-ttu-id="a57d4-319">Es libre para establecer las posiciones de los objetos que desee, aunque es más fácil para el usuario de la aplicación si las distancias de objetos no son demasiado lejos de la cámara.</span><span class="sxs-lookup"><span data-stu-id="a57d4-319">You are free to set the positions of the objects to whatever you would like, though it is easier for the user of the application if the objects distances are not too far from the camera.</span></span>

11. <span data-ttu-id="a57d4-320">Cuando se ejecuta la aplicación, debe ser capaz de identificar los objetos dentro de la escena, para lograr esto, se deben etiquetar.</span><span class="sxs-lookup"><span data-stu-id="a57d4-320">When your application is running, it needs to be able to identify the objects within the scene, to achieve this, they need to be tagged.</span></span> <span data-ttu-id="a57d4-321">Seleccione uno de los objetos y, en el *Inspector* del panel, haga clic en **Agregar etiqueta...** , que intercambiará el *Inspector* con el **etiquetas & capas** panel.</span><span class="sxs-lookup"><span data-stu-id="a57d4-321">Select one of the objects, and in the *Inspector* panel, click **Add Tag...**, which will swap the *Inspector* with the **Tags & Layers** panel.</span></span>

    <span data-ttu-id="a57d4-322">![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span><span class="sxs-lookup"><span data-stu-id="a57d4-322">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span></span>

12. <span data-ttu-id="a57d4-323">Haga clic en el **+ (signo más)** de símbolos, a continuación, escriba el nombre de etiqueta como **ObjectInScene**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-323">Click the **+ (plus)** symbol, then type the tag name as **ObjectInScene**.</span></span>

    ![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > <span data-ttu-id="a57d4-325">Si usa un nombre diferente para la etiqueta, deberá asegurarse de que este cambio también se realiza el *DataFromAnalytics*, *ObjectTrigger*, y *que mirar*, scripts más adelante, para que su objetos se encuentra y detecta, dentro de la escena.</span><span class="sxs-lookup"><span data-stu-id="a57d4-325">If you use a different name for your tag, you will need to ensure this change is also made the *DataFromAnalytics*, *ObjectTrigger*, and *Gaze*, scripts later, so that your objects are found, and detected, within your scene.</span></span>

13. <span data-ttu-id="a57d4-326">Con la etiqueta que se creó, debe aplicarlo a las tres de los objetos.</span><span class="sxs-lookup"><span data-stu-id="a57d4-326">With the tag created, you now need to apply it to all three of your objects.</span></span> <span data-ttu-id="a57d4-327">Desde el *jerarquía*, mantenga el **MAYÚS** clave, a continuación, haga clic en el **Capsule**, **cubo**, y **esfera**, objetos, a continuación, en el *Inspector*, haga clic en el menú desplegable junto a **etiqueta**, a continuación, haga clic en el *ObjectInScene* de etiquetas que ha creado.</span><span class="sxs-lookup"><span data-stu-id="a57d4-327">From the *Hierarchy*, hold the **Shift** key, then click the **Capsule**, **Cube**, and **Sphere**, objects, then in the *Inspector*, click the dropdown menu alongside **Tag**, then click the *ObjectInScene* tag you created.</span></span>

    <span data-ttu-id="a57d4-328">![Configurar los objetos de la escena de Unity](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span><span class="sxs-lookup"><span data-stu-id="a57d4-328">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span></span>

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a><span data-ttu-id="a57d4-329">Capítulo 6: crear la clase ApplicationInsightsTracker</span><span class="sxs-lookup"><span data-stu-id="a57d4-329">Chapter 6 - Create the ApplicationInsightsTracker class</span></span>

<span data-ttu-id="a57d4-330">Es el primer script, deberá crear **ApplicationInsightsTracker**, que es responsable de:</span><span class="sxs-lookup"><span data-stu-id="a57d4-330">The first script you need to create is **ApplicationInsightsTracker**, which is responsible for:</span></span>

1.  <span data-ttu-id="a57d4-331">Creación de eventos en función de las interacciones del usuario para enviar a Azure Application Insights.</span><span class="sxs-lookup"><span data-stu-id="a57d4-331">Creating events based on user interactions to submit to Azure Application Insights.</span></span>

2. <span data-ttu-id="a57d4-332">Creación de nombres de evento adecuados, según la interacción del usuario.</span><span class="sxs-lookup"><span data-stu-id="a57d4-332">Creating appropriate Event names, depending on user interaction.</span></span>

3. <span data-ttu-id="a57d4-333">Envío de eventos a la instancia del servicio Application Insights.</span><span class="sxs-lookup"><span data-stu-id="a57d4-333">Submitting events to the Application Insights Service instance.</span></span>

<span data-ttu-id="a57d4-334">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="a57d4-334">To create this class:</span></span>

1.  <span data-ttu-id="a57d4-335">Haga clic en el *Panel del proyecto*, a continuación, **crear** > **carpeta**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-335">Right-click in the *Project Panel*, then **Create** > **Folder**.</span></span> <span data-ttu-id="a57d4-336">Nombre de la carpeta **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-336">Name the folder **Scripts**.</span></span>

    ![Crear la clase ApplicationInsightsTracker](images/AzureLabs-Lab309-46.png)  ![Crear la clase ApplicationInsightsTracker](images/AzureLabs-Lab309-47.png)

2.  <span data-ttu-id="a57d4-339">Con el **Scripts** carpeta creada, haga doble clic en él para abrirlo.</span><span class="sxs-lookup"><span data-stu-id="a57d4-339">With the **Scripts** folder created, double-click it, to open.</span></span> <span data-ttu-id="a57d4-340">A continuación, dentro de esa carpeta, con el botón secundario, **crear**  >   **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-340">Then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="a57d4-341">Nombre de la secuencia de comandos **ApplicationInsightsTracker**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-341">Name the script **ApplicationInsightsTracker**.</span></span>

3.  <span data-ttu-id="a57d4-342">Haga doble clic en el nuevo **ApplicationInsightsTracker** script para abrirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-342">Double-click on the new **ApplicationInsightsTracker** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="a57d4-343">Actualice los espacios de nombres en la parte superior de la secuencia de comandos como sigue:</span><span class="sxs-lookup"><span data-stu-id="a57d4-343">Update namespaces at the top of the script to be as below:</span></span>

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  <span data-ttu-id="a57d4-344">Dentro de la clase inserte las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="a57d4-344">Inside the class insert the following variables:</span></span>

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
    > <span data-ttu-id="a57d4-345">Establecer el **instrumentationKey, applicationId y API_Key** valores como corresponda, utilizando el *las claves del servicio* desde el Portal de Azure como se mencionó en [capítulo 1](#chapter-1---the-azure-portal), paso 9 y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="a57d4-345">Set the **instrumentationKey, applicationId and API_Key** values appropriately, using the *Service Keys* from the Azure Portal as mentioned in [Chapter 1](#chapter-1---the-azure-portal), step 9 onwards.</span></span>

6.  <span data-ttu-id="a57d4-346">A continuación, agregue el **Start()** y **Awake()** métodos, que se llamará cuando se inicializa la clase:</span><span class="sxs-lookup"><span data-stu-id="a57d4-346">Then add the **Start()** and **Awake()** methods, which will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="a57d4-347">Agregue los métodos que se encarga de enviar los eventos y las métricas registradas por la aplicación:</span><span class="sxs-lookup"><span data-stu-id="a57d4-347">Add the methods responsible for sending the events and metrics registered by your application:</span></span>

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

8.  <span data-ttu-id="a57d4-348">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="a57d4-348">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-7---create-the-gaze-script"></a><span data-ttu-id="a57d4-349">Capítulo 7: crear la secuencia de comandos de mirada</span><span class="sxs-lookup"><span data-stu-id="a57d4-349">Chapter 7 - Create the Gaze script</span></span>

<span data-ttu-id="a57d4-350">Es el script siguiente para crear el **que mirar** secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="a57d4-350">The next script to create is the **Gaze** script.</span></span> <span data-ttu-id="a57d4-351">Este script es responsable de crear un *Raycast* que se proyectará hacia delante desde el *cámara principal*, para detectar el objeto que está mirando el usuario.</span><span class="sxs-lookup"><span data-stu-id="a57d4-351">This script is responsible for creating a *Raycast* that will be projected forward from the *Main Camera*, to detect which object the user is looking at.</span></span> <span data-ttu-id="a57d4-352">En este caso, el *Raycast* tendrá que identificar si el usuario está viendo un objeto con el **ObjectInScene** etiqueta y, a continuación, contabilizar el tiempo que el usuario *gazes* en ese objeto.</span><span class="sxs-lookup"><span data-stu-id="a57d4-352">In this case, the *Raycast* will need to identify if the user is looking at an object with the **ObjectInScene** tag, and then count how long the user *gazes* at that object.</span></span>

1.  <span data-ttu-id="a57d4-353">Haga doble clic en el **Scripts** carpeta para abrirla.</span><span class="sxs-lookup"><span data-stu-id="a57d4-353">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="a57d4-354">Haga clic en el **Scripts** carpeta, haga clic en **crear**  >   **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-354">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="a57d4-355">Nombre de la secuencia de comandos **que mirar**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-355">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="a57d4-356">Haga doble clic en el script para abrirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a57d4-356">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="a57d4-357">Reemplace el código existente con lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a57d4-357">Replace the existing code with the following:</span></span>

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

5.  <span data-ttu-id="a57d4-358">El código para el **Awake()** y **Start()** métodos ahora debe agregarse.</span><span class="sxs-lookup"><span data-stu-id="a57d4-358">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

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

6.  <span data-ttu-id="a57d4-359">Dentro de la **que mirar** de clases, agregue el código siguiente en el **Update()** método al proyecto un *Raycast* y detectar el posicionamiento de destino:</span><span class="sxs-lookup"><span data-stu-id="a57d4-359">Inside the **Gaze** class, add the following code in the **Update()** method to project a *Raycast* and detect the target hit:</span></span>

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

7.  <span data-ttu-id="a57d4-360">Agregar el **ResetFocusedObject()** método envíe datos a **Application Insights** cuando el usuario ha examinado de un objeto.</span><span class="sxs-lookup"><span data-stu-id="a57d4-360">Add the **ResetFocusedObject()** method, to send data to **Application Insights** when the user has looked at an object.</span></span>

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

8.  <span data-ttu-id="a57d4-361">Ahora ha completado la **que mirar** secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="a57d4-361">You have now completed the **Gaze** script.</span></span> <span data-ttu-id="a57d4-362">Guarde los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="a57d4-362">Save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8---create-the-objecttrigger-class"></a><span data-ttu-id="a57d4-363">Capítulo 8: crear la clase ObjectTrigger</span><span class="sxs-lookup"><span data-stu-id="a57d4-363">Chapter 8 - Create the ObjectTrigger class</span></span>

<span data-ttu-id="a57d4-364">Es el siguiente script, deberá crear **ObjectTrigger**, que es responsable de:</span><span class="sxs-lookup"><span data-stu-id="a57d4-364">The next script you need to create is **ObjectTrigger**, which is responsible for:</span></span>

- <span data-ttu-id="a57d4-365">Agregar los componentes necesarios de colisión de la cámara principal.</span><span class="sxs-lookup"><span data-stu-id="a57d4-365">Adding components needed for collision to the Main Camera.</span></span>
- <span data-ttu-id="a57d4-366">Detectar si la cámara está cerca de un objeto etiquetado como **ObjectInScene**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-366">Detecting if the camera is near an object tagged as **ObjectInScene**.</span></span>

<span data-ttu-id="a57d4-367">Para crear la secuencia de comandos:</span><span class="sxs-lookup"><span data-stu-id="a57d4-367">To create the script:</span></span>

1.  <span data-ttu-id="a57d4-368">Haga doble clic en el **Scripts** carpeta para abrirla.</span><span class="sxs-lookup"><span data-stu-id="a57d4-368">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="a57d4-369">Haga clic en el **Scripts** carpeta, haga clic en **crear**  >   **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-369">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="a57d4-370">Nombre de la secuencia de comandos **ObjectTrigger**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-370">Name the script **ObjectTrigger**.</span></span>

3.  <span data-ttu-id="a57d4-371">Haga doble clic en el script para abrirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a57d4-371">Double-click on the script to open it with Visual Studio.</span></span> <span data-ttu-id="a57d4-372">Reemplace el código existente con lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a57d4-372">Replace the existing code with the following:</span></span>

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

4.  <span data-ttu-id="a57d4-373">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="a57d4-373">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9---create-the-datafromanalytics-class"></a><span data-ttu-id="a57d4-374">Capítulo 9: crear la clase DataFromAnalytics</span><span class="sxs-lookup"><span data-stu-id="a57d4-374">Chapter 9 - Create the DataFromAnalytics class</span></span>

<span data-ttu-id="a57d4-375">Ahora deberá crear el **DataFromAnalytics** script, que es responsable de:</span><span class="sxs-lookup"><span data-stu-id="a57d4-375">You will now need to create the **DataFromAnalytics** script, which is responsible for:</span></span>

- <span data-ttu-id="a57d4-376">Captura de datos de análisis sobre qué objeto se ha se aproxime a la cámara más.</span><span class="sxs-lookup"><span data-stu-id="a57d4-376">Fetching analytics data about which object has been approached by the camera the most.</span></span>
- <span data-ttu-id="a57d4-377">Mediante el *las claves del servicio*, que permiten la comunicación con la instancia de servicio de Azure Application Insights.</span><span class="sxs-lookup"><span data-stu-id="a57d4-377">Using the *Service Keys*, that allow communication with your Azure Application Insights Service instance.</span></span>
- <span data-ttu-id="a57d4-378">Ordenar los objetos de escena, según los cuales tiene el mayor número de eventos.</span><span class="sxs-lookup"><span data-stu-id="a57d4-378">Sorting the objects in scene, according to which has the highest event count.</span></span>
- <span data-ttu-id="a57d4-379">Cambiar el color del material, del objeto acerca más al *verde*.</span><span class="sxs-lookup"><span data-stu-id="a57d4-379">Changing the material color, of the most approached object, to *green*.</span></span>

<span data-ttu-id="a57d4-380">Para crear la secuencia de comandos:</span><span class="sxs-lookup"><span data-stu-id="a57d4-380">To create the script:</span></span>

1.  <span data-ttu-id="a57d4-381">Haga doble clic en el **Scripts** carpeta para abrirla.</span><span class="sxs-lookup"><span data-stu-id="a57d4-381">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="a57d4-382">Haga clic en el **Scripts** carpeta, haga clic en **crear**  >   **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-382">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="a57d4-383">Nombre de la secuencia de comandos **DataFromAnalytics**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-383">Name the script **DataFromAnalytics**.</span></span>

3.  <span data-ttu-id="a57d4-384">Haga doble clic en el script para abrirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a57d4-384">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="a57d4-385">Inserte los espacios de nombres siguientes:</span><span class="sxs-lookup"><span data-stu-id="a57d4-385">Insert the following namespaces:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="a57d4-386">Dentro de la secuencia de comandos, inserte el siguiente:</span><span class="sxs-lookup"><span data-stu-id="a57d4-386">Inside the script, insert the following:</span></span>

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

6.  <span data-ttu-id="a57d4-387">Dentro de la **DataFromAnalytics** class, justo después de la **Start()** método, agregue el siguiente método denominado **FetchAnalytics()** .</span><span class="sxs-lookup"><span data-stu-id="a57d4-387">Within the **DataFromAnalytics** class, right after the **Start()** method, add the following method called **FetchAnalytics()**.</span></span> <span data-ttu-id="a57d4-388">Este método es responsable de rellenar la lista de pares clave / valor, con un *GameObject* y un número de recuento de eventos de marcador de posición.</span><span class="sxs-lookup"><span data-stu-id="a57d4-388">This method is responsible for populating the list of key value pairs, with a *GameObject* and a placeholder event count number.</span></span> <span data-ttu-id="a57d4-389">A continuación, se inicializa el **GetWebRequest()** corrutina.</span><span class="sxs-lookup"><span data-stu-id="a57d4-389">It then initializes the **GetWebRequest()** coroutine.</span></span> <span data-ttu-id="a57d4-390">La estructura de consulta de la llamada a *Application Insights* puede encontrarse dentro de este método también, como el *dirección URL de consulta* punto de conexión.</span><span class="sxs-lookup"><span data-stu-id="a57d4-390">The query structure of the call to *Application Insights* can be found within this method also, as the *Query URL* endpoint.</span></span>

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

7.  <span data-ttu-id="a57d4-391">Justo debajo de la **FetchAnalytics()** método, agregue un método llamado **GetWebRequest()** , que devuelve un *IEnumerator*.</span><span class="sxs-lookup"><span data-stu-id="a57d4-391">Right below the **FetchAnalytics()** method, add a method called **GetWebRequest()**, which returns an *IEnumerator*.</span></span> <span data-ttu-id="a57d4-392">Este método es responsable de que solicita el número de veces que un evento, que se corresponde con un valor concreto *GameObject*, se ha llamado dentro de *Application Insights*.</span><span class="sxs-lookup"><span data-stu-id="a57d4-392">This method is responsible for requesting the number of times an event, corresponding with a specific *GameObject*, has been called within *Application Insights*.</span></span> <span data-ttu-id="a57d4-393">Cuando se hayan devuelto todas las consultas enviadas, el **DetermineWinner()** se llama al método.</span><span class="sxs-lookup"><span data-stu-id="a57d4-393">When all the sent queries have returned, the **DetermineWinner()** method is called.</span></span>

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

8.  <span data-ttu-id="a57d4-394">El siguiente método es **DetermineWinner()** , que ordena la lista de *GameObject* y *Int* pares, según el mayor número de eventos.</span><span class="sxs-lookup"><span data-stu-id="a57d4-394">The next method is **DetermineWinner()**, which sorts the list of *GameObject* and *Int* pairs, according to the highest event count.</span></span> <span data-ttu-id="a57d4-395">A continuación, cambia el color de dicho material *GameObject* a *verde* (como comentarios para que tenga el número más alto).</span><span class="sxs-lookup"><span data-stu-id="a57d4-395">It then changes the material color of that *GameObject* to *green* (as feedback for it having the highest count).</span></span> <span data-ttu-id="a57d4-396">Esto muestra un mensaje con los resultados del análisis.</span><span class="sxs-lookup"><span data-stu-id="a57d4-396">This displays a message with the analytics results.</span></span>

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

9.  <span data-ttu-id="a57d4-397">Agregue la estructura de clases que se usará para deserializar el objeto JSON procedente de *Application Insights*.</span><span class="sxs-lookup"><span data-stu-id="a57d4-397">Add the class structure which will be used to deserialize the JSON object, received from *Application Insights*.</span></span> <span data-ttu-id="a57d4-398">Agregue estas clases en la parte inferior de la **DataFromAnalytics** archivo de clase, **fuera** de la definición de clase.</span><span class="sxs-lookup"><span data-stu-id="a57d4-398">Add these classes at the very bottom of your **DataFromAnalytics** class file, **outside** of the class definition.</span></span>

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

10. <span data-ttu-id="a57d4-399">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="a57d4-399">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10---create-the-movement-class"></a><span data-ttu-id="a57d4-400">Capítulo 10: crear la clase de movimiento</span><span class="sxs-lookup"><span data-stu-id="a57d4-400">Chapter 10 - Create the Movement class</span></span>

<span data-ttu-id="a57d4-401">El **movimiento** script es el siguiente script deberá crear.</span><span class="sxs-lookup"><span data-stu-id="a57d4-401">The **Movement** script is the next script you will need to create.</span></span> <span data-ttu-id="a57d4-402">Es responsable de:</span><span class="sxs-lookup"><span data-stu-id="a57d4-402">It is responsible for:</span></span>

- <span data-ttu-id="a57d4-403">Mover la cámara principal según la dirección de la cámara mira hacia.</span><span class="sxs-lookup"><span data-stu-id="a57d4-403">Moving the Main Camera according to the direction the camera is looking towards.</span></span>
- <span data-ttu-id="a57d4-404">Agregar todos los demás scripts a objetos de la escena.</span><span class="sxs-lookup"><span data-stu-id="a57d4-404">Adding all other scripts to scene objects.</span></span>

<span data-ttu-id="a57d4-405">Para crear la secuencia de comandos:</span><span class="sxs-lookup"><span data-stu-id="a57d4-405">To create the script:</span></span>

1.  <span data-ttu-id="a57d4-406">Haga doble clic en el **Scripts** carpeta para abrirla.</span><span class="sxs-lookup"><span data-stu-id="a57d4-406">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="a57d4-407">Haga clic en el **Scripts** carpeta, haga clic en **crear**  >   **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-407">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="a57d4-408">Nombre de la secuencia de comandos **movimiento**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-408">Name the script **Movement**.</span></span>

3.  <span data-ttu-id="a57d4-409">Haga doble clic en el script para abrirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="a57d4-409">Double-click on the script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="a57d4-410">Reemplace el código existente con lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a57d4-410">Replace the existing code with the following:</span></span>

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

5.  <span data-ttu-id="a57d4-411">Dentro de la **movimiento** (clase), *debajo* vacío **Update()** método, inserte los siguientes métodos que permiten al usuario usar el controlador de mano para mover en el espacio virtual:</span><span class="sxs-lookup"><span data-stu-id="a57d4-411">Within the **Movement** class, *below* the empty **Update()** method, insert the following methods that allow the user to use the hand controller to move in the virtual space:</span></span>

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

6.  <span data-ttu-id="a57d4-412">Por último, agregar la llamada al método dentro de la **Update()** método.</span><span class="sxs-lookup"><span data-stu-id="a57d4-412">Lastly add the method call within the **Update()** method.</span></span>

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  <span data-ttu-id="a57d4-413">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="a57d4-413">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11---setting-up-the-scripts-references"></a><span data-ttu-id="a57d4-414">Capítulo 11: configuración de las referencias de scripts</span><span class="sxs-lookup"><span data-stu-id="a57d4-414">Chapter 11 - Setting up the scripts references</span></span>

<span data-ttu-id="a57d4-415">En este capítulo tiene que colocar el **movimiento** de script en el **cámara primaria** y establezca sus destinos de referencia.</span><span class="sxs-lookup"><span data-stu-id="a57d4-415">In this Chapter you need to place the **Movement** script onto the **Camera Parent** and set its reference targets.</span></span> <span data-ttu-id="a57d4-416">Ese script controlará la colocación de los demás scripts donde deben estar.</span><span class="sxs-lookup"><span data-stu-id="a57d4-416">That script will then handle placing the other scripts where they need to be.</span></span>

1.  <span data-ttu-id="a57d4-417">Desde el **Scripts** carpeta en el *Panel proyecto*, arrastre el **movimiento** scripts para la **cámara primaria** objeto, que se encuentra en la  *Panel de la jerarquía*.</span><span class="sxs-lookup"><span data-stu-id="a57d4-417">From the **Scripts** folder in the *Project Panel*, drag the **Movement** script to the **Camera Parent** object, located in the *Hierarchy Panel*.</span></span>

    ![Configuración de las referencias de scripts en la escena de Unity](images/AzureLabs-Lab309-48.png)

2.  <span data-ttu-id="a57d4-419">Haga clic en el **cámara primaria**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-419">Click on the **Camera Parent**.</span></span> <span data-ttu-id="a57d4-420">En el *jerarquía Panel*, arrastre el **mano derecha** objeto desde el *jerarquía Panel* al destino de referencia, **controlador**, en el *Panel inspector*.</span><span class="sxs-lookup"><span data-stu-id="a57d4-420">In the *Hierarchy Panel*, drag the **Right Hand** object from the *Hierarchy Panel* to the reference target, **Controller**, in the *Inspector Panel*.</span></span> <span data-ttu-id="a57d4-421">Establecer el **usuario velocidad** a **5**, tal y como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="a57d4-421">Set the **User Speed** to **5**, as shown in the image below.</span></span>

    ![Configuración de las referencias de scripts en la escena de Unity](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a><span data-ttu-id="a57d4-423">Capítulo 12: compilar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="a57d4-423">Chapter 12 - Build the Unity project</span></span>

<span data-ttu-id="a57d4-424">Todo lo necesario para la sección de Unity de este proyecto ahora se completó, por lo que es el momento de crearla desde Unity.</span><span class="sxs-lookup"><span data-stu-id="a57d4-424">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="a57d4-425">Vaya a **configuración de compilación**, (**archivo** > **configuración de compilación**).</span><span class="sxs-lookup"><span data-stu-id="a57d4-425">Navigate to **Build Settings**, (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="a57d4-426">Desde el **configuración de compilación** ventana, haga clic en **compilar**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-426">From the **Build Settings** window, click **Build**.</span></span>

    ![Compile el proyecto de Unity para la solución UWP](images/AzureLabs-Lab309-50.png)

3.  <span data-ttu-id="a57d4-428">Un **Explorador de archivos** will ventana emergente, que le solicitará una ubicación para la compilación.</span><span class="sxs-lookup"><span data-stu-id="a57d4-428">A **File Explorer** window will pop-up, prompting you for a location for the build.</span></span> <span data-ttu-id="a57d4-429">Cree una nueva carpeta (haciendo clic en **nueva carpeta** en la esquina superior izquierda) y asígnele el nombre **compilaciones**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-429">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![Compile el proyecto de Unity para la solución UWP](images/AzureLabs-Lab309-51.png)

    1.  <span data-ttu-id="a57d4-431">Abra el nuevo **compilaciones** carpeta y cree otra carpeta (mediante **nueva carpeta** una vez más) y asígnele el nombre **MR\_Azure\_aplicación\_ Insights**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-431">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **MR\_Azure\_Application\_Insights**.</span></span>

        ![Compile el proyecto de Unity para la solución UWP](images/AzureLabs-Lab309-52.png)

    2.  <span data-ttu-id="a57d4-433">Con el **MR\_Azure\_aplicación\_Insights** carpeta seleccionada, haga clic en **seleccionar la carpeta**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-433">With the **MR\_Azure\_Application\_Insights** folder selected, click **Select Folder**.</span></span> <span data-ttu-id="a57d4-434">El proyecto tardará un minuto o más en crear.</span><span class="sxs-lookup"><span data-stu-id="a57d4-434">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="a57d4-435">Siga *compilar*, **Explorador de archivos** aparecerá con la ubicación del nuevo proyecto.</span><span class="sxs-lookup"><span data-stu-id="a57d4-435">Following *Build*, **File Explorer** will appear showing you the location of your new project.</span></span>

## <a name="chapter-13---deploy-mrazureapplicationinsights-app-to-your-machine"></a><span data-ttu-id="a57d4-436">Capítulo 13 - implementar la aplicación MR_Azure_Application_Insights en la máquina</span><span class="sxs-lookup"><span data-stu-id="a57d4-436">Chapter 13 - Deploy MR_Azure_Application_Insights app to your machine</span></span>

<span data-ttu-id="a57d4-437">Para implementar el **MR\_Azure\_aplicación\_Insights** aplicación en el equipo Local:</span><span class="sxs-lookup"><span data-stu-id="a57d4-437">To deploy the **MR\_Azure\_Application\_Insights** app on your Local Machine:</span></span>

1.  <span data-ttu-id="a57d4-438">Abra el archivo de solución de su **MR\_Azure\_aplicación\_Insights** app en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-438">Open the solution file of your **MR\_Azure\_Application\_Insights** app in **Visual Studio**.</span></span>

2.  <span data-ttu-id="a57d4-439">En el **plataforma de solución**, seleccione **x86, equipo Local**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-439">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="a57d4-440">En el **configuración de la solución** seleccione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="a57d4-440">In the **Solution Configuration** select **Debug**.</span></span>

    ![Compile el proyecto de Unity para la solución UWP](images/AzureLabs-Lab309-53.png)

4.  <span data-ttu-id="a57d4-442">Vaya a **menú compilar** y haga clic en **implementar solución** para transferir localmente la aplicación en el equipo.</span><span class="sxs-lookup"><span data-stu-id="a57d4-442">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="a57d4-443">La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas, listos para iniciarse.</span><span class="sxs-lookup"><span data-stu-id="a57d4-443">Your app should now appear in the list of installed apps, ready to be launched.</span></span>

6. <span data-ttu-id="a57d4-444">Inicie la aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="a57d4-444">Launch the mixed reality application.</span></span>

7. <span data-ttu-id="a57d4-445">Mueva la escena, como elementos no utilizados los objetos y mirando, cuando el *Azure Insight Service* ha recopilado datos suficientes eventos, establecerá el objeto que se han analizado el máximo partido a verde.</span><span class="sxs-lookup"><span data-stu-id="a57d4-445">Move around the scene, approaching objects and looking at them, when the *Azure Insight Service* has collected enough event data, it will set the object that has been approached the most to green.</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="a57d4-446">Mientras que el tiempo de espera promedio para la *eventos y métricas* sea recopilado por el servicio tarda aproximadamente 15 minutos, en algunas ocasiones puede tardar hasta una hora.</span><span class="sxs-lookup"><span data-stu-id="a57d4-446">While the average waiting time for the *Events and Metrics* to be collected by the Service takes around 15 min, in some occasions it might take up to 1 hour.</span></span>

## <a name="chapter-14---the-application-insights-service-portal"></a><span data-ttu-id="a57d4-447">Capítulo 14: el portal de Application Insights</span><span class="sxs-lookup"><span data-stu-id="a57d4-447">Chapter 14 - The Application Insights Service portal</span></span>

<span data-ttu-id="a57d4-448">Una vez que han movido en torno a la escena y gazed en varios objetos puede ver los datos recopilados en el *servicio Application Insights* portal.</span><span class="sxs-lookup"><span data-stu-id="a57d4-448">Once you have roamed around the scene and gazed at several objects you can see the data collected in the *Application Insights Service* portal.</span></span>

1.  <span data-ttu-id="a57d4-449">Vuelva al portal de servicio Application Insights.</span><span class="sxs-lookup"><span data-stu-id="a57d4-449">Go back to your Application Insights Service portal.</span></span>

2.  <span data-ttu-id="a57d4-450">Haga clic en *Explorador de métricas*.</span><span class="sxs-lookup"><span data-stu-id="a57d4-450">Click on *Metrics Explorer*.</span></span>

    ![Examina los datos recopilados](images/AzureLabs-Lab309-54.png)

3.  <span data-ttu-id="a57d4-452">Se abrirá en una pestaña que contiene el gráfico que representan el *eventos y métricas* relacionados con la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a57d4-452">It will open in a tab containing the graph which represent the *Events and Metrics* related to your application.</span></span> <span data-ttu-id="a57d4-453">Como se mencionó anteriormente, puede tardar algún tiempo (hasta 1 hora) para que los datos que se mostrará en el gráfico</span><span class="sxs-lookup"><span data-stu-id="a57d4-453">As mentioned above, it might take some time (up to 1 hour) for the data to be displayed in the graph</span></span>

    ![Examina los datos recopilados](images/AzureLabs-Lab309-55.png)

4.  <span data-ttu-id="a57d4-455">Haga clic en el *barra eventos* en el *Total de eventos* por versión de la aplicación para ver un desglose detallado de los eventos con sus nombres.</span><span class="sxs-lookup"><span data-stu-id="a57d4-455">Click on the *Events bar* in the *Total of Events* by Application Version, to see a detailed breakdown of the events with their names.</span></span>

    ![Examina los datos recopilados](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a><span data-ttu-id="a57d4-457">Su terminado la aplicación de servicio Application Insights</span><span class="sxs-lookup"><span data-stu-id="a57d4-457">Your finished your Application Insights Service application</span></span>

<span data-ttu-id="a57d4-458">Enhorabuena, creó una aplicación de realidad mixta que aprovecha el servicio Application Insights para supervisar la actividad del usuario dentro de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a57d4-458">Congratulations, you built a mixed reality app that leverages the Application Insights Service to monitor user's activity within your app.</span></span>

![resultado del curso](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="a57d4-460">Ejercicios de bonificación</span><span class="sxs-lookup"><span data-stu-id="a57d4-460">Bonus Exercises</span></span>

<span data-ttu-id="a57d4-461">**Ejercicio 1**</span><span class="sxs-lookup"><span data-stu-id="a57d4-461">**Exercise 1**</span></span>

<span data-ttu-id="a57d4-462">Vuelva a generar, en lugar de crear manualmente los objetos ObjectInScene y establezca sus coordenadas en el plano dentro de sus scripts.</span><span class="sxs-lookup"><span data-stu-id="a57d4-462">Try spawning, rather than manually creating, the ObjectInScene objects and set their coordinates on the plane within your scripts.</span></span> <span data-ttu-id="a57d4-463">De esta manera, podría pedir que Azure era qué objeto más popular (ya sea desde resultados mirada o proximidad) y generar un *adicional* uno de esos objetos.</span><span class="sxs-lookup"><span data-stu-id="a57d4-463">In this way, you could ask Azure what the most popular object was (either from gaze or proximity results) and spawn an *extra* one of those objects.</span></span>

<span data-ttu-id="a57d4-464">**Ejercicio 2**</span><span class="sxs-lookup"><span data-stu-id="a57d4-464">**Exercise 2**</span></span>

<span data-ttu-id="a57d4-465">Ordenar los resultados de Application Insights por hora, para que obtenga los datos más relevantes e implementar esos datos confidenciales de tiempo en su aplicación.</span><span class="sxs-lookup"><span data-stu-id="a57d4-465">Sort your Application Insights results by time, so that you get the most relevant data, and implement that time sensitive data in your application.</span></span>

