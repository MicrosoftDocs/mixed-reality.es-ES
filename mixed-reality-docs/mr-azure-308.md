---
title: 'MR y Azure 308: notificaciones entre dispositivos'
description: Complete este curso para aprender a implementar Azure Notification Hubs, Azure Functions, Azure Storage y tablas en una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, tutorial, API, notificación, funciones, tablas, Notification hubs, hololens, envolventes, VR
ms.openlocfilehash: 3b6e930acd81c7d6e3addc107ec0da605d38cad1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694601"
---
>[!NOTE]
><span data-ttu-id="4ad1b-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="4ad1b-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="4ad1b-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="4ad1b-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="4ad1b-108">Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="4ad1b-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a><span data-ttu-id="4ad1b-110">MR y Azure 308: Notificaciones entre dispositivos</span><span class="sxs-lookup"><span data-stu-id="4ad1b-110">MR and Azure 308: Cross-device notifications</span></span>

![Inicio del producto final](images/AzureLabs-Lab8-00.png)

<span data-ttu-id="4ad1b-112">En este curso, aprenderá a agregar funcionalidades de Notification Hubs a una aplicación de realidad mixta con Azure Notification Hubs, tablas de Azure y Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-112">In this course, you will learn how to add Notification Hubs capabilities to a mixed reality application using Azure Notification Hubs, Azure Tables, and Azure Functions.</span></span>

<span data-ttu-id="4ad1b-113">**Azure Notification hubs** es un servicio de Microsoft que permite a los desarrolladores enviar notificaciones de envío personalizadas y personalizadas a cualquier plataforma, todo ello en la nube.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-113">**Azure Notification Hubs** is a Microsoft service, which allows developers to send targeted and personalized push notifications to any platform, all powered within the cloud.</span></span> <span data-ttu-id="4ad1b-114">Esto puede permitir que los desarrolladores se comuniquen con los usuarios finales o incluso comunicarse entre varias aplicaciones, dependiendo del escenario.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-114">This can effectively allow developers to communicate with end users, or even communicate between various applications, depending on the scenario.</span></span> <span data-ttu-id="4ad1b-115">Para obtener más información, visite la [Página](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview)de **Notification hubs de Azure** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-115">For more information, visit the **Azure Notification Hubs** [page](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview).</span></span>

<span data-ttu-id="4ad1b-116">**Azure Functions** es un servicio de Microsoft, que permite a los desarrolladores ejecutar pequeños fragmentos de código, "funciones", en Azure.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-116">**Azure Functions** is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="4ad1b-117">Esto proporciona una manera de delegar el trabajo en la nube, en lugar de la aplicación local, que puede tener muchas ventajas.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-117">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="4ad1b-118">**Azure Functions** admite varios lenguajes de desarrollo,\#como C\#, F, node. js, Java y php.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-118">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="4ad1b-119">Para obtener más información, visite la [página](https://docs.microsoft.com/azure/azure-functions/functions-overview) **Azure Functions** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-119">For more information, visit the **Azure Functions** [page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="4ad1b-120">**Azure tables** es un servicio en la nube de Microsoft, que permite a los desarrolladores almacenar datos estructurados que no son de SQL en la nube, lo que facilita el acceso desde cualquier lugar.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-120">**Azure Tables** is a Microsoft cloud service, which allows developers to store structured non-SQL data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="4ad1b-121">El servicio ofrece un diseño sin esquemas, lo que permite la evolución de las tablas según sea necesario y, por tanto, es muy flexible.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-121">The service boasts a schemaless design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="4ad1b-122">Para obtener más información, visite la [Página](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) **tablas de Azure** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-122">For more information, visit the **Azure Tables** [page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="4ad1b-123">Una vez completado este curso, tendrá una aplicación de auriculares envolvente de realidad mixta y una aplicación de equipo de escritorio, que podrá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-123">Having completed this course, you will have a mixed reality immersive headset application, and a Desktop PC application, which will be able to do the following:</span></span>

1. <span data-ttu-id="4ad1b-124">La aplicación de equipo de escritorio permitirá al usuario desplace un objeto en el espacio 2D (X e y) con el mouse.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-124">The Desktop PC app will allow the user to move an object in 2D space (X and Y), using the mouse.</span></span>

2. <span data-ttu-id="4ad1b-125">El movimiento de objetos dentro de la aplicación de PC se enviará a la nube mediante JSON, que tendrá el formato de una cadena que contiene un identificador de objeto, un tipo y una información de transformación (coordenadas X e y).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-125">The movement of objects within the PC app will be sent to the cloud using JSON, which will be in the form of a string, containing an object ID, type, and transform information (X and Y coordinates).</span></span> 

3. <span data-ttu-id="4ad1b-126">La aplicación de realidad mixta, que tiene una escena idéntica a la aplicación de escritorio, recibirá notificaciones sobre el movimiento de objetos, desde el servicio de Notification Hubs (que acaba de actualizar la aplicación de equipo de escritorio).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-126">The mixed reality app, which has an identical scene to the desktop app, will receive notifications regarding object movement, from the Notification Hubs service (which has just been updated by the Desktop PC app).</span></span> 

4. <span data-ttu-id="4ad1b-127">Tras recibir una notificación, que contendrá el identificador de objeto, el tipo y la información de transformación, la aplicación de realidad mixta aplicará la información recibida a su propia escena.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-127">Upon receiving a notification, which will contain the object ID, type, and transform information, the mixed reality app will apply the received information to its own scene.</span></span>

<span data-ttu-id="4ad1b-128">En su aplicación, depende del modo en que va a integrar los resultados con el diseño.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-128">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="4ad1b-129">Este curso está diseñado para enseñarle a integrar un servicio de Azure con su proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-129">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="4ad1b-130">Es su trabajo usar el conocimiento que obtiene de este curso para mejorar su aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-130">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span> <span data-ttu-id="4ad1b-131">Este curso es un tutorial independiente, que no implica directamente ningún otro laboratorio de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-131">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="4ad1b-132">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="4ad1b-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="4ad1b-133">Recurso</span><span class="sxs-lookup"><span data-stu-id="4ad1b-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="4ad1b-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="4ad1b-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="4ad1b-135"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="4ad1b-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="4ad1b-136">MR y Azure 308: Notificaciones entre dispositivos</span><span class="sxs-lookup"><span data-stu-id="4ad1b-136">MR and Azure 308: Cross-device notifications</span></span></td><td style="text-align: center;"> <span data-ttu-id="4ad1b-137">✔️</span><span class="sxs-lookup"><span data-stu-id="4ad1b-137">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="4ad1b-138">✔️</span><span class="sxs-lookup"><span data-stu-id="4ad1b-138">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="4ad1b-139">Aunque este curso se centra principalmente en los auriculares de Windows Mixed Reality inmersivo (VR), también puede aplicar lo que aprenda en este curso a Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-139">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="4ad1b-140">A medida que siga con el curso, verá notas sobre cualquier cambio que deba usar para admitir HoloLens.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-140">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="4ad1b-141">Al usar HoloLens, puede observar algún Eco durante la captura de voz.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-141">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4ad1b-142">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="4ad1b-142">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="4ad1b-143">Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-143">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="4ad1b-144">Tenga en cuenta también que los requisitos previos y las instrucciones escritas dentro de este documento representan lo que se ha probado y comprobado en el momento de la escritura (2018 de mayo).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-144">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="4ad1b-145">Puede usar el software más reciente, como se indica en el artículo [instalar las herramientas](install-the-tools.md) , aunque no se debe suponer que la información de este curso se ajusta perfectamente a lo que encontrará en el software más reciente que el que se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-145">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="4ad1b-146">Se recomienda el siguiente hardware y software para este curso:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-146">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="4ad1b-147">Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de auriculares envolvente (VR)</span><span class="sxs-lookup"><span data-stu-id="4ad1b-147">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="4ad1b-148">Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="4ad1b-148">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="4ad1b-149">El SDK de Windows 10 más reciente</span><span class="sxs-lookup"><span data-stu-id="4ad1b-149">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="4ad1b-150">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="4ad1b-150">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="4ad1b-151">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="4ad1b-151">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="4ad1b-152">Un [auricular de Windows Mixed Reality inmersivo (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="4ad1b-152">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="4ad1b-153">Acceso a Internet para la instalación de Azure y acceso a Notification Hubs</span><span class="sxs-lookup"><span data-stu-id="4ad1b-153">Internet access for Azure setup and to access Notification Hubs</span></span>

## <a name="before-you-start"></a><span data-ttu-id="4ad1b-154">Antes de comenzar</span><span class="sxs-lookup"><span data-stu-id="4ad1b-154">Before you start</span></span>

- <span data-ttu-id="4ad1b-155">Para evitar que se produzcan problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cerca de la raíz (las rutas de acceso de carpeta largas pueden producir problemas en tiempo de compilación).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-155">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="4ad1b-156">Debe ser el propietario del portal para desarrolladores de Microsoft y el portal de registro de aplicaciones; de lo contrario, no tendrá permiso para acceder a la aplicación en el [capítulo 2](#chapter-2---retrieve-your-new-apps-credentials).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-156">You must be the owner of your Microsoft Developer Portal and your Application Registration Portal, otherwise you will not have permission to access the app in [Chapter 2](#chapter-2---retrieve-your-new-apps-credentials).</span></span>

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a><span data-ttu-id="4ad1b-157">Capítulo 1: creación de una aplicación en el portal para desarrolladores de Microsoft</span><span class="sxs-lookup"><span data-stu-id="4ad1b-157">Chapter 1 - Create an application on the Microsoft Developer Portal</span></span>

<span data-ttu-id="4ad1b-158">Para usar el servicio **Azure Notification hubs** , tendrá que crear una aplicación en el portal para desarrolladores de Microsoft, ya que será necesario registrar la aplicación para que pueda enviar y recibir notificaciones.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-158">To use the **Azure Notification Hubs** Service, you will need to create an Application on the Microsoft Developer Portal, as your application will need to be registered, so that it can send and receive notifications.</span></span>

1.  <span data-ttu-id="4ad1b-159">Inicie sesión en el [portal para desarrolladores de Microsoft](https://developer.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-159">Log in to the [Microsoft Developer Portal](https://developer.microsoft.com/dashboard).</span></span>

    > <span data-ttu-id="4ad1b-160">Tendrá que iniciar sesión en su cuenta de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-160">You will need to log in to your Microsoft Account.</span></span>

2.  <span data-ttu-id="4ad1b-161">En el panel, haga clic en **crear una nueva aplicación**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-161">From the Dashboard, click **Create a new app**.</span></span>

    ![Creación de una aplicación](images/AzureLabs-Lab8-01.png)

3.  <span data-ttu-id="4ad1b-163">Aparecerá un elemento emergente en el que debe reservar un nombre para la nueva aplicación.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-163">A popup will appear, wherein you need to reserve a name for your new app.</span></span> <span data-ttu-id="4ad1b-164">En el cuadro de texto, inserte un nombre apropiado; Si el nombre elegido está disponible, aparecerá un paso a la derecha del cuadro de texto.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-164">In the textbox, insert an appropriate name; if the chosen name is available, a tick will appear to the right of the textbox.</span></span> <span data-ttu-id="4ad1b-165">Una vez que haya insertado un nombre disponible, haga clic en el botón **reservar nombre del producto** situado en la parte inferior izquierda de la ventana emergente.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-165">Once you have an available name inserted, click the **Reserve product name** button to the bottom left of the popup.</span></span>

    ![invertir un nombre](images/AzureLabs-Lab8-02.png)

4.  <span data-ttu-id="4ad1b-167">Una vez creada la aplicación, estará listo para pasar al siguiente capítulo.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-167">With the app now created, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a><span data-ttu-id="4ad1b-168">Capítulo 2: recuperar las nuevas credenciales de las aplicaciones</span><span class="sxs-lookup"><span data-stu-id="4ad1b-168">Chapter 2 - Retrieve your new apps credentials</span></span>

<span data-ttu-id="4ad1b-169">Inicie sesión en el portal de registro de aplicaciones, donde se mostrará la nueva aplicación y recupere las credenciales que se usarán para configurar el **servicio de Notification hubs** en **Azure portal**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-169">Log into the Application Registration Portal, where your new app will be listed, and retrieve the credentials which will be used to setup the **Notification Hubs Service** within the **Azure Portal**.</span></span>

1.  <span data-ttu-id="4ad1b-170">Vaya al [portal de registro de aplicaciones](http://apps.dev.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-170">Navigate to the [Application Registration Portal](http://apps.dev.microsoft.com).</span></span>

    ![Portal de registro de aplicaciones](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > <span data-ttu-id="4ad1b-172">Tendrá que usar su cuenta de Microsoft para iniciar sesión.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-172">You will need to use your Microsoft Account to Login.</span></span>  
    > <span data-ttu-id="4ad1b-173">**Debe** ser la cuenta de Microsoft que usó en el [capítulo](#chapter-1---create-an-application-on-the-microsoft-developer-portal)anterior, con el portal para desarrolladores de la tienda Windows.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-173">This **must** be the Microsoft Account which you used in the previous [Chapter](#chapter-1---create-an-application-on-the-microsoft-developer-portal), with the Windows Store Developer portal.</span></span>

2.  <span data-ttu-id="4ad1b-174">La aplicación se encuentra en la sección **mis aplicaciones** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-174">You will find your app under the **My applications** section.</span></span> <span data-ttu-id="4ad1b-175">Una vez que lo encuentre, haga clic en él y se le dirigirá a una nueva página que tiene el nombre de la aplicación más el **registro**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-175">Once you have found it, click on it and you will be taken to a new page which has the app name plus **Registration**.</span></span>

    ![la aplicación recién registrada](images/AzureLabs-Lab8-04.png)

3.  <span data-ttu-id="4ad1b-177">Desplácese hacia abajo en la página de registro para buscar la sección de secretos de la **aplicación** y el **SID del paquete** de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-177">Scroll down the registration page to find your **Application Secrets** section and the **Package SID** for your app.</span></span> <span data-ttu-id="4ad1b-178">Copie ambos para usarlos con la configuración del **servicio Azure Notification hubs** en el siguiente capítulo.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-178">Copy both for use with setting up the **Azure Notification Hubs Service** in the next Chapter.</span></span>

    ![secretos de la aplicación](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a><span data-ttu-id="4ad1b-180">Capítulo 3: instalación de Azure Portal: creación de un servicio de Notification Hubs</span><span class="sxs-lookup"><span data-stu-id="4ad1b-180">Chapter 3 - Setup Azure Portal: create Notification Hubs Service</span></span>

<span data-ttu-id="4ad1b-181">Una vez que se recuperen las credenciales de las aplicaciones, tendrá que ir a Azure portal, donde creará un servicio de Azure Notification Hubs.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-181">With your apps credentials retrieved, you will need to go to the Azure Portal, where you will create an Azure Notification Hubs Service.</span></span>

1.  <span data-ttu-id="4ad1b-182">Inicie sesión en el [portal de Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-182">Log into the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="4ad1b-183">Si aún no tiene una cuenta de Azure, tendrá que crear una.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-183">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="4ad1b-184">Si sigue este tutorial en una situación de aula o de laboratorio, pregunte al instructor o a uno de los Proctors para obtener ayuda para configurar la nueva cuenta.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-184">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="4ad1b-185">Una vez que haya iniciado sesión, haga clic en **nuevo** en la esquina superior izquierda y busque **Centro**de notificaciones y haga clic en ***entrar***.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-185">Once you are logged in, click on **New** in the top left corner, and search for **Notification Hub**, and click ***Enter***.</span></span>

    ![búsqueda del centro de notificaciones](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > <span data-ttu-id="4ad1b-187">Es posible que la palabra ***nuevo*** se haya reemplazado por **crear un recurso**, en portales más recientes.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-187">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="4ad1b-188">La nueva página proporcionará una descripción del servicio *Notification hubs* .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-188">The new page will provide a description of the *Notification Hubs* service.</span></span> <span data-ttu-id="4ad1b-189">En la parte inferior izquierda de este mensaje, seleccione el botón **crear** para crear una asociación con este servicio.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-189">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![Crear instancia de Notification hubs](images/AzureLabs-Lab8-07.png)

4.  <span data-ttu-id="4ad1b-191">Una vez que haya hecho clic en ***crear***:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-191">Once you have clicked on ***Create***:</span></span>

    1.  <span data-ttu-id="4ad1b-192">Inserte el nombre que desee para esta instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-192">Insert your desired name for this service instance.</span></span>

    2.  <span data-ttu-id="4ad1b-193">Proporcione un **espacio de nombres** que podrá asociar a esta aplicación.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-193">Provide a **namespace** which you will be able to associate with this app.</span></span>

    3.  <span data-ttu-id="4ad1b-194">Seleccione una **ubicación.**</span><span class="sxs-lookup"><span data-stu-id="4ad1b-194">Select a **Location.**</span></span>

    4.  <span data-ttu-id="4ad1b-195">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-195">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="4ad1b-196">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-196">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="4ad1b-197">Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-197">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="4ad1b-198">Si desea leer más sobre los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-198">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span> 

    5.  <span data-ttu-id="4ad1b-199">Seleccione una **suscripción**adecuada.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-199">Select an appropriate **Subscription**.</span></span>

    6.  <span data-ttu-id="4ad1b-200">También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-200">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="4ad1b-201">Seleccione **Crear**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-201">Select **Create**.</span></span>

        ![detalles del servicio de rellenado](images/AzureLabs-Lab8-08.png)

5.  <span data-ttu-id="4ad1b-203">Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-203">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="4ad1b-204">Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-204">A notification will appear in the portal once the Service instance is created.</span></span>

    ![notificación](images/AzureLabs-Lab8-09.png)

7.  <span data-ttu-id="4ad1b-206">Haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-206">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="4ad1b-207">Se le dirigirá a la nueva instancia de servicio del **Centro** de notificaciones.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-207">You will be taken to your new **Notification Hub** service instance.</span></span>

    ![Ir al recurso](images/AzureLabs-Lab8-10.png)
    
8.  <span data-ttu-id="4ad1b-209">En la página información general, en el medio de la página, haga clic en **Windows (WNS).**</span><span class="sxs-lookup"><span data-stu-id="4ad1b-209">From the overview page, halfway down the page, click **Windows (WNS).**</span></span> <span data-ttu-id="4ad1b-210">El panel de la derecha cambiará para mostrar dos campos de texto, que requieren el **SID del paquete** y la clave de **seguridad**, de la aplicación que configuró anteriormente.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-210">The panel on the right will change to show two text fields, which require your **Package SID** and **Security Key**, from the app you set up previously.</span></span>

    ![servicio de hubs recién creado](images/AzureLabs-Lab8-11.png)

9. <span data-ttu-id="4ad1b-212">Una vez que haya copiado los detalles en los campos correctos, haga clic en **Guardar**y recibirá una notificación cuando se haya actualizado correctamente el centro de notificaciones.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-212">Once you have copied the details into the correct fields, click **Save**, and you will receive a notification when the Notification Hub has been successfully updated.</span></span>

    ![copiar detalles de seguridad](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a><span data-ttu-id="4ad1b-214">Capítulo 4: configurar el servicio tabla de Azure portal</span><span class="sxs-lookup"><span data-stu-id="4ad1b-214">Chapter 4 - Setup Azure Portal: create Table Service</span></span>

<span data-ttu-id="4ad1b-215">Después de crear la instancia de servicio de Notification Hubs, vuelva a Azure portal, donde creará un servicio de tablas de Azure mediante la creación de un recurso de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-215">After creating your Notification Hubs Service instance, navigate back to your Azure Portal, where you will create an Azure Tables Service by creating a Storage Resource.</span></span>

1.  <span data-ttu-id="4ad1b-216">Si aún no ha iniciado sesión, inicie sesión en [Azure portal](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-216">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="4ad1b-217">Una vez que haya iniciado sesión, haga clic en **nuevo** en la esquina superior izquierda, busque la **cuenta de almacenamiento**y haga clic en **entrar**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-217">Once logged in, click on **New** in the top left corner, and search for **Storage account**, and click **Enter**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="4ad1b-218">Es posible que la palabra ***nuevo*** se haya reemplazado por **crear un recurso**, en portales más recientes.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-218">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="4ad1b-219">Seleccione **cuenta de almacenamiento: BLOB, archivo, tabla, cola** en la lista.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-219">Select **Storage account - blob, file, table, queue** from the list.</span></span>

    ![búsqueda de la cuenta de almacenamiento](images/AzureLabs-Lab8-13.png)

4.  <span data-ttu-id="4ad1b-221">La nueva página proporcionará una descripción del servicio de la **cuenta de almacenamiento** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-221">The new page will provide a description of the **Storage account** service.</span></span> <span data-ttu-id="4ad1b-222">En la parte inferior izquierda de este mensaje, seleccione el botón **crear** para crear una instancia de este servicio.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-222">At the bottom left of this prompt, select the **Create** button, to create an instance of this service.</span></span>

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab8-14.png)

5.  <span data-ttu-id="4ad1b-224">Una vez que haya hecho clic en **crear**, aparecerá un panel:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-224">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="4ad1b-225">Inserte el **nombre** que desee para esta instancia de servicio (debe estar todo en minúsculas).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-225">Insert your desired **Name** for this service instance (must be all lowercase).</span></span>

    2. <span data-ttu-id="4ad1b-226">En **modelo de implementación**, haga clic en **Administrador de recursos**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-226">For **Deployment model**, click **Resource manager**.</span></span>

    3.  <span data-ttu-id="4ad1b-227">En **tipo de cuenta**, en el menú desplegable, seleccione **almacenamiento (uso general V1)** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-227">For **Account kind**, using the dropdown menu, select **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="4ad1b-228">Seleccione una **Ubicación**adecuada.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-228">Select an appropriate **Location**.</span></span>
    
    5.  <span data-ttu-id="4ad1b-229">En el menú desplegable **replicación** , seleccione **almacenamiento con redundancia geográfica con acceso de lectura (RA-grs)** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-229">For the **Replication** dropdown menu, select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="4ad1b-230">En **rendimiento**, haga clic en **estándar**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-230">For **Performance**, click **Standard**.</span></span>

    7.  <span data-ttu-id="4ad1b-231">En la sección **transferencia segura requerida** , seleccionedeshabilitado.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-231">Within the **Secure transfer required** section, select **Disabled**.</span></span>

    8.  <span data-ttu-id="4ad1b-232">En el menú desplegable **suscripción** , seleccione una suscripción adecuada.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-232">From the **Subscription** dropdown menu, select an appropriate subscription.</span></span>

    9.  <span data-ttu-id="4ad1b-233">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-233">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="4ad1b-234">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-234">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="4ad1b-235">Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-235">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="4ad1b-236">Si desea leer más sobre los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-236">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="4ad1b-237">Deje las **redes virtuales** como deshabilitadas si se trata de una opción.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-237">Leave **Virtual networks** as **Disabled** if this is an option for you.</span></span>

    11. <span data-ttu-id="4ad1b-238">Haga clic en **Create**(Crear).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-238">Click **Create**.</span></span>

        ![Rellene los detalles de almacenamiento](images/AzureLabs-Lab8-15.png)

6.  <span data-ttu-id="4ad1b-240">Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-240">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="4ad1b-241">Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-241">A notification will appear in the portal once the Service instance is created.</span></span> <span data-ttu-id="4ad1b-242">Haga clic en las notificaciones para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-242">Click on the notifications to explore your new Service instance.</span></span>

    ![nueva notificación de almacenamiento](images/AzureLabs-Lab8-16.png)

8.  <span data-ttu-id="4ad1b-244">Haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-244">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="4ad1b-245">Se le dirigirá a la página de información general de la nueva instancia del servicio de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-245">You will be taken to your new Storage Service instance overview page.</span></span>

    ![Ir al recurso](images/AzureLabs-Lab8-17.PNG)

9. <span data-ttu-id="4ad1b-247">En la página información general, en la parte derecha, haga clic en **tablas**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-247">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. <span data-ttu-id="4ad1b-248">El panel de la derecha cambiará para mostrar la información de **Table Service** , en la que es necesario agregar una nueva tabla.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-248">The panel on the right will change to show the **Table service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="4ad1b-249">Para ello, haga clic **+** en el botón **tabla** situado en la esquina superior izquierda.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-249">Do this by clicking the **+** **Table** button to the top-left corner.</span></span>

    ![abrir tablas](images/AzureLabs-Lab8-19.png)

11. <span data-ttu-id="4ad1b-251">Se mostrará una nueva página, en la que es necesario escribir un **nombre de tabla**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-251">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="4ad1b-252">Este es el nombre que usará para hacer referencia a los datos de la aplicación en capítulos posteriores.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-252">This is the name you will use to refer to the data in your application in later Chapters.</span></span> <span data-ttu-id="4ad1b-253">Inserte un nombre apropiado y haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-253">Insert an appropriate name and click **OK**.</span></span>

    ![crear nueva tabla](images/AzureLabs-Lab8-20.png)    

12. <span data-ttu-id="4ad1b-255">Una vez creada la nueva tabla, podrá verla dentro de la página **Table Service** (en la parte inferior).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-255">Once the new table has been created, you will be able to see it within the **Table service** page (at the bottom).</span></span>

    ![nueva tabla creada](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a><span data-ttu-id="4ad1b-257">Capítulo 5: completar la tabla de Azure en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4ad1b-257">Chapter 5 - Completing the Azure Table in Visual Studio</span></span>

<span data-ttu-id="4ad1b-258">Ahora que ha configurado la cuenta de almacenamiento de **Table Service** , es el momento de agregar datos a ella, que se usará para almacenar y recuperar información.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-258">Now that your **Table service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="4ad1b-259">La edición de las tablas se puede realizar a través de **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-259">The editing of your Tables can be done through **Visual Studio**.</span></span>

1.  <span data-ttu-id="4ad1b-260">Abra **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-260">Open **Visual Studio**.</span></span>

2.  <span data-ttu-id="4ad1b-261">En el menú, haga clic en **Ver** > **Cloud Explorer**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-261">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![Abra Cloud Explorer](images/AzureLabs-Lab8-22.png)

3.  <span data-ttu-id="4ad1b-263">El **Cloud Explorer** se abrirá como un elemento acoplado (sea paciente, ya que la carga puede tardar tiempo).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-263">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="4ad1b-264">Si la suscripción que usó para crear las *cuentas de almacenamiento* no es visible, asegúrese de que tiene:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-264">If the Subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="4ad1b-265">Ha iniciado sesión en la misma cuenta que la que usó para Azure portal.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-265">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="4ad1b-266">Seleccionó su suscripción desde la página de administración de cuentas (puede que tenga que aplicar un filtro de la configuración de la cuenta):</span><span class="sxs-lookup"><span data-stu-id="4ad1b-266">Selected your Subscription from the Account Management Page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![buscar suscripción](images/AzureLabs-Lab8-22-5.png)

4.  <span data-ttu-id="4ad1b-268">Se mostrarán los servicios en la nube de Azure.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-268">Your Azure cloud services will be shown.</span></span> <span data-ttu-id="4ad1b-269">Busque **cuentas de almacenamiento** y haga clic en la flecha situada a la izquierda de ella para expandir sus cuentas.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-269">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![abrir cuentas de almacenamiento](images/AzureLabs-Lab8-23.png)

5.  <span data-ttu-id="4ad1b-271">Una vez expandida, la **cuenta de almacenamiento** recién creada debe estar disponible.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-271">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="4ad1b-272">Haga clic en la flecha situada a la izquierda de su almacenamiento y, después, una vez expandida, busque **tablas** y haga clic en la flecha situada junto a ella para mostrar la **tabla** que ha creado en el último capítulo.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-272">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="4ad1b-273">Haga doble clic en la **tabla**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-273">Double click your **Table**.</span></span>

    ![abrir tabla de objetos de escenas](images/AzureLabs-Lab8-24.png)

6.  <span data-ttu-id="4ad1b-275">La tabla se abrirá en el centro de la ventana de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-275">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="4ad1b-276">Haga clic en el icono de **+** la tabla con el signo (más).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-276">Click the table icon with the **+** (plus) on it.</span></span>

    ![Agregar nueva tabla](images/AzureLabs-Lab8-25.png)

7.  <span data-ttu-id="4ad1b-278">Aparecerá una ventana que le solicitará que *agregue la entidad*.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-278">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="4ad1b-279">Creará tres entidades en total, cada una con varias propiedades.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-279">You will create three entities in total, each with several properties.</span></span> <span data-ttu-id="4ad1b-280">Observará que *PartitionKey* y *RowKey* ya se han proporcionado, ya que se usan en la tabla para buscar los datos.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-280">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![partición y clave de fila](images/AzureLabs-Lab8-26.png)

8. <span data-ttu-id="4ad1b-282">Actualice el *valor* de **PartitionKey** y **RowKey** como se indica a continuación (Recuerde hacer esto para cada propiedad de fila que agregue, aunque incremente el RowKey cada vez):</span><span class="sxs-lookup"><span data-stu-id="4ad1b-282">Update the *Value* of the **PartitionKey** and **RowKey** as follows (remember to do this for each row property you add, though increment the RowKey each time):</span></span>

    ![agregar valores correctos](images/AzureLabs-Lab8-26-5.png)

9.  <span data-ttu-id="4ad1b-284">Haga clic en **Agregar propiedad** para agregar filas de datos adicionales.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-284">Click **Add property** to add extra rows of data.</span></span> <span data-ttu-id="4ad1b-285">Haga que la primera tabla vacía coincida con la tabla siguiente.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-285">Make your first empty table match the below table.</span></span>

10. <span data-ttu-id="4ad1b-286">Cuando haya terminado, haga clic en **Aceptar** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-286">Click **OK** when you are finished.</span></span>

    ![Haga clic en Aceptar cuando haya terminado](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > <span data-ttu-id="4ad1b-288">Asegúrese de que ha cambiado el **tipo** de las entradas **X**, **y**y **Z**, a **doble**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-288">Ensure that you have changed the **Type** of the **X**, **Y**, and **Z**, entries to **Double**.</span></span> 

11. <span data-ttu-id="4ad1b-289">Observará que la tabla tiene ahora una fila de datos.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-289">You will notice your table now has a row of data.</span></span> <span data-ttu-id="4ad1b-290">Haga clic **+** de nuevo en el icono de (más) para agregar otra entidad.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-290">Click the **+** (plus) icon again to add another entity.</span></span>

    ![primera fila](images/AzureLabs-Lab8-27-5.png)

12. <span data-ttu-id="4ad1b-292">Cree una propiedad adicional y, a continuación, establezca los valores de la nueva entidad para que coincidan con los que se muestran a continuación.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-292">Create an additional property, and then set the values of the new entity to match those shown below.</span></span>

    ![Agregar cubo](images/AzureLabs-Lab8-28.png)

13. <span data-ttu-id="4ad1b-294">Repita el último paso para agregar otra entidad.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-294">Repeat the last step to add another entity.</span></span> <span data-ttu-id="4ad1b-295">Establezca los valores de esta entidad en los que se muestran a continuación.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-295">Set the values for this entity to those shown below.</span></span>

    ![Agregar cilindro](images/AzureLabs-Lab8-29.png)

14. <span data-ttu-id="4ad1b-297">La tabla debería tener ahora el siguiente aspecto.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-297">Your table should now look like the one below.</span></span>

    ![tabla completa](images/AzureLabs-Lab8-30.png)

15. <span data-ttu-id="4ad1b-299">Ha completado este capítulo.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-299">You have completed this Chapter.</span></span> <span data-ttu-id="4ad1b-300">Asegúrese de guardar.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-300">Make sure to save.</span></span>

## <a name="chapter-6---create-an-azure-function-app"></a><span data-ttu-id="4ad1b-301">Capítulo 6: creación de una Function App de Azure</span><span class="sxs-lookup"><span data-stu-id="4ad1b-301">Chapter 6 - Create an Azure Function App</span></span>

<span data-ttu-id="4ad1b-302">Cree una Function App de Azure, a la que llamará la aplicación de escritorio para actualizar **TABLE** Service y enviar una notificación a través del **Centro**de notificaciones.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-302">Create an Azure Function App, which will be called by the Desktop application to update the **Table** service and send a notification through the **Notification Hub**.</span></span>

<span data-ttu-id="4ad1b-303">En primer lugar, debe crear un archivo que permita que la función de Azure cargue las bibliotecas que necesita.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-303">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="4ad1b-304">Abra **el Bloc de notas** (Presione la tecla Windows y escriba Bloc de notas).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-304">Open **Notepad** (press Windows Key and type notepad).</span></span>

    ![abrir el Bloc de notas](images/AzureLabs-Lab8-31.png)

2.  <span data-ttu-id="4ad1b-306">Con el Bloc de notas abierto, inserte la siguiente estructura JSON en él.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-306">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="4ad1b-307">Una vez hecho esto, guárdelo en el escritorio como **Project. JSON**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-307">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="4ad1b-308">Es importante que la nomenclatura sea correcta: Asegúrese de que **no tiene una extensión de archivo. txt** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-308">It is important that the naming is correct: ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="4ad1b-309">Este archivo define las bibliotecas que utilizará la función. Si ha usado NuGet, le resultará familiar.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-309">This file defines the libraries your function will use, if you have used NuGet it will look familiar.</span></span>

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "7.0.0",
            "Microsoft.Azure.NotificationHubs" : "1.0.9",
            "Microsoft.Azure.WebJobs.Extensions.NotificationHubs" :"1.1.0"
        }
        }
    }
    }
    ```

3.  <span data-ttu-id="4ad1b-310">Inicie sesión en el [portal de Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-310">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="4ad1b-311">Una vez que haya iniciado sesión, haga clic en **nuevo** en la esquina superior izquierda y busque **function App**, presione **entrar**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-311">Once you are logged in, click on **New** in the top left corner, and search for **Function App**, press **Enter**.</span></span>

    ![búsqueda de function App](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > <span data-ttu-id="4ad1b-313">Es posible que la palabra **nuevo** se haya reemplazado por **crear un recurso**, en portales más recientes.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-313">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

5.  <span data-ttu-id="4ad1b-314">La nueva página proporcionará una descripción del servicio **function App** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-314">The new page will provide a description of the **Function App** service.</span></span> <span data-ttu-id="4ad1b-315">En la parte inferior izquierda de este mensaje, seleccione el botón **crear** para crear una asociación con este servicio.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-315">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![instancia de la aplicación de función](images/AzureLabs-Lab8-33.png)

6.  <span data-ttu-id="4ad1b-317">Una vez que haya hecho clic en **crear**, rellene lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-317">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="4ad1b-318">En **nombre**de la aplicación, inserte el nombre que desee para esta instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-318">For **App name**, insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="4ad1b-319">Seleccione una **suscripción**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-319">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="4ad1b-320">Seleccione el plan de tarifa adecuado para usted; si es la primera vez que crea un **servicio de function App**, debe estar disponible un nivel gratis.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-320">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="4ad1b-321">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-321">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="4ad1b-322">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-322">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="4ad1b-323">Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-323">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="4ad1b-324">Si desea leer más sobre los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-324">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="4ad1b-325">En el caso de **sistemas operativos**, haga clic en Windows, ya que es la plataforma prevista.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-325">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="4ad1b-326">Seleccione un **plan de hospedaje** (este tutorial usa un **plan de consumo**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-326">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="4ad1b-327">Seleccione una **Ubicación** **(elija la misma ubicación que el almacenamiento que ha creado en el paso anterior)**</span><span class="sxs-lookup"><span data-stu-id="4ad1b-327">Select a **Location** **(choose the same location as the storage you have built in the previous step)**</span></span>

    8. <span data-ttu-id="4ad1b-328">En la sección **almacenamiento** , **debe seleccionar el servicio de almacenamiento que creó en el paso anterior**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-328">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="4ad1b-329">No necesitará *Application Insights* en esta aplicación, así que no dude en dejarlo **fuera**de servicio.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-329">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="4ad1b-330">Haga clic en **Create**(Crear).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-330">Click **Create**.</span></span>

        ![crear nueva instancia](images/AzureLabs-Lab8-34.png)

7.  <span data-ttu-id="4ad1b-332">Una vez que haya hecho clic en **crear** , tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-332">Once you have clicked on **Create** you will have to wait for the service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="4ad1b-333">Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-333">A notification will appear in the portal once the Service instance is created.</span></span>

    ![nueva notificación](images/AzureLabs-Lab8-35.png)

9.  <span data-ttu-id="4ad1b-335">Haga clic en las notificaciones para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-335">Click on the notifications to explore your new Service instance.</span></span>

10. <span data-ttu-id="4ad1b-336">Haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-336">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![Ir al recurso](images/AzureLabs-Lab8-36.png)

11. <span data-ttu-id="4ad1b-338">Haga clic **+** en el icono (más) situado junto a *funciones*para *crear un nuevo*.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-338">Click the **+** (plus) icon next to *Functions*, to *Create new*.</span></span>

    ![Agregar nueva función](images/AzureLabs-Lab8-37.png)

12. <span data-ttu-id="4ad1b-340">En el panel central, aparecerá la ventana de creación de la **función** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-340">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="4ad1b-341">Omita la información de la mitad superior del panel y haga clic en **función personalizada**, que se encuentra cerca de la parte inferior (en el área azul, como se muestra a continuación).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-341">Ignore the information in the upper half of the panel, and click **Custom function**, which is located near the bottom (in the blue area, as below).</span></span>

    ![función personalizada](images/AzureLabs-Lab8-38.png)

13. <span data-ttu-id="4ad1b-343">La nueva página dentro de la ventana mostrará varios tipos de función.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-343">The new page within the window will show various function types.</span></span> <span data-ttu-id="4ad1b-344">Desplácese hacia abajo para ver los tipos púrpura y haga clic en el elemento **http Put** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-344">Scroll down to view the purple types, and click **HTTP PUT** element.</span></span>

    ![http put (vínculo)](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > <span data-ttu-id="4ad1b-346">Es posible que tenga que desplazarse más hacia abajo en la página (y es posible que esta imagen no tenga exactamente el mismo aspecto, si se han realizado actualizaciones de Azure portal), pero busca un elemento denominado *http Put*.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-346">You may have to scroll further the down the page (and this image may not look exactly the same, if Azure Portal updates have taken place), however, you are looking for an element called *HTTP PUT*.</span></span>

14. <span data-ttu-id="4ad1b-347">Aparecerá la ventana **put de http** , donde tendrá que configurar la función (vea la imagen siguiente).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-347">The **HTTP PUT** window will appear, where you need to configure the function (see below for image).</span></span>

    1.  <span data-ttu-id="4ad1b-348">En **idioma,** en el menú desplegable, seleccione\#C.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-348">For **Language,** using the dropdown menu, select C\#.</span></span>

    2.  <span data-ttu-id="4ad1b-349">En **nombre,** escriba un nombre adecuado.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-349">For **Name,** input an appropriate name.</span></span>

    3.  <span data-ttu-id="4ad1b-350">En el menú desplegable **nivel de autenticación** , seleccione **función**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-350">In the **Authentication level** dropdown menu, select **Function**.</span></span>

    4.  <span data-ttu-id="4ad1b-351">En la sección **nombre de tabla** , debe usar el nombre exacto que usó para crear el servicio **tabla** previamente (incluido el mismo caso de letra).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-351">For the **Table name** section, you need to use the exact name you used to create your **Table** service previously (including the same letter case).</span></span>

    5.  <span data-ttu-id="4ad1b-352">En la sección conexión de la **cuenta de almacenamiento** , use el menú desplegable y seleccione la cuenta de almacenamiento desde allí.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-352">Within the **Storage account connection** section, use the dropdown menu, and select your storage account from there.</span></span> <span data-ttu-id="4ad1b-353">Si no está allí, haga clic en el **nuevo** hipervínculo que aparece junto al título de la sección para mostrar otro panel, donde debe aparecer la cuenta de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-353">If it is not there, click the **New** hyperlink alongside the section title, to show another panel, where your storage account should be listed.</span></span>

        ![nuevo almacenamiento](images/AzureLabs-Lab8-40.png)

15. <span data-ttu-id="4ad1b-355">Haga clic en **crear** y recibirá una notificación que le notificará que la configuración se ha actualizado correctamente.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-355">Click **Create** and you will receive a notification that your settings have been updated successfully.</span></span>

    ![Create (función)](images/AzureLabs-Lab8-41.png)

16. <span data-ttu-id="4ad1b-357">Después de hacer clic en **crear**, se le redirigirá al editor de funciones.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-357">After clicking **Create**, you will be redirected to the function editor.</span></span>

    ![actualizar código de función](images/AzureLabs-Lab8-42.png)

17. <span data-ttu-id="4ad1b-359">Inserte el código siguiente en el editor de funciones (reemplazando el código de la función):</span><span class="sxs-lookup"><span data-stu-id="4ad1b-359">Insert the following code into the function editor (replacing the code in the function):</span></span>

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Microsoft.Azure.NotificationHubs;
    using Newtonsoft.Json;

    public static async Task Run(UnityGameObject gameObj, CloudTable table, IAsyncCollector<Notification> notification, TraceWriter log)
    {
        //RowKey of the table object to be changed
        string rowKey = gameObj.RowKey;

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<UnityGameObject>("UnityPartitionKey", rowKey); 

        TableResult result = table.Execute(operation);

        //Create a UnityGameObject so to set its parameters
        UnityGameObject existingGameObj = (UnityGameObject)result.Result; 

        existingGameObj.RowKey = rowKey;
        existingGameObj.X = gameObj.X;
        existingGameObj.Y = gameObj.Y;
        existingGameObj.Z = gameObj.Z;

        //Replace the table appropriate table Entity with the value of the UnityGameObject
        operation = TableOperation.Replace(existingGameObj); 

        table.Execute(operation);

        log.Verbose($"Updated object position");

        //Serialize the UnityGameObject
        string wnsNotificationPayload = JsonConvert.SerializeObject(existingGameObj);
        
        log.Info($"{wnsNotificationPayload}");

        var headers = new Dictionary<string, string>();

        headers["X-WNS-Type"] = @"wns/raw";

        //Send the raw notification to subscribed devices
        await notification.AddAsync(new WindowsNotification(wnsNotificationPayload, headers)); 

        log.Verbose($"Sent notification");
    }

    // This UnityGameObject represent a Table Entity
    public class UnityGameObject : TableEntity
    {
        public string Type { get; set; }
        public double X { get; set; }
        public double Y { get; set; }
        public double Z { get; set; }
        public string RowKey { get; set; }
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="4ad1b-360">Con las bibliotecas incluidas, la función recibe el nombre y la ubicación del objeto que se ha colocado en la escena de Unity ( C# como un objeto, denominado **UnityGameObject**).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-360">Using the included libraries, the function receives the name and location of the object which was moved in the Unity scene (as a C# object, called **UnityGameObject**).</span></span> <span data-ttu-id="4ad1b-361">A continuación, este objeto se utiliza para actualizar los parámetros de objeto de la tabla creada.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-361">This object is then used to update the object parameters within the created table.</span></span> <span data-ttu-id="4ad1b-362">Después, la función realiza una llamada al servicio de centro de notificaciones creado, que notifica a todas las aplicaciones suscritas.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-362">Following this, the function makes a call to your created Notification Hub service, which notifies all subscribed applications.</span></span>

18. <span data-ttu-id="4ad1b-363">Con el código en su lugar, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-363">With the code in place, click **Save**.</span></span>

19. <span data-ttu-id="4ad1b-364">A continuación, haga **\<** clic en el icono (flecha) situado en el lado derecho de la página.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-364">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![abrir el panel de carga](images/AzureLabs-Lab8-43.png)

20. <span data-ttu-id="4ad1b-366">Un panel se deslizará hacia la derecha.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-366">A panel will slide in from the right.</span></span> <span data-ttu-id="4ad1b-367">En ese panel, haga clic en **cargar**y aparecerá un explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-367">In that panel, click **Upload**, and a File Browser will appear.</span></span>

21. <span data-ttu-id="4ad1b-368">Vaya a y haga clic en el archivo **Project. JSON** , que ha creado anteriormente en el **Bloc de notas** y, a continuación, haga clic en el botón **abrir** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-368">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="4ad1b-369">Este archivo define las bibliotecas que utilizará la función.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-369">This file defines the libraries that your function will use.</span></span>

    ![cargar JSON](images/AzureLabs-Lab8-44.png)

22. <span data-ttu-id="4ad1b-371">Cuando se haya cargado el archivo, aparecerá en el panel de la derecha.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-371">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="4ad1b-372">Al hacer clic en él se abrirá en el editor de **funciones** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-372">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="4ad1b-373">Debe tener **exactamente** el mismo aspecto que la siguiente imagen (debajo del paso 23).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-373">It must look **exactly** the same as the next image (below step 23).</span></span>

23. <span data-ttu-id="4ad1b-374">A continuación, en el panel de la izquierda, debajo de **funciones**, haga clic en el vínculo **integrar** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-374">Then, in the panel on the left, beneath **Functions**, click the **Integrate** link.</span></span>

    ![función Integrate](images/AzureLabs-Lab8-45.png)

24. <span data-ttu-id="4ad1b-376">En la siguiente página, en la esquina superior derecha, haga clic en **editor avanzado** (como se muestra a continuación).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-376">On the next page, in the top right corner, click **Advanced editor** (as below).</span></span>

    ![Abrir el editor avanzado](images/AzureLabs-Lab8-46.png)

25. <span data-ttu-id="4ad1b-378">Se abrirá un archivo **function. JSON** en el panel central, que debe reemplazarse por el siguiente fragmento de código.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-378">A **function.json** file will be opened in the center panel, which needs to be replaced with the following code snippet.</span></span> <span data-ttu-id="4ad1b-379">Esto define la función que se va a compilar y los parámetros que se pasan a la función.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-379">This defines the function you are building and the parameters passed into the function.</span></span>

    ```json
    {
    "bindings": [
        {
        "authLevel": "function",
        "type": "httpTrigger",
        "methods": [
            "get",
            "post"
        ],
        "name": "gameObj",
        "direction": "in"
        },
        {
        "type": "table",
        "name": "table",
        "tableName": "SceneObjectsTable",
        "connection": "mrnothubstorage_STORAGE",
        "direction": "in"
        },
        {
        "type": "notificationHub",
        "direction": "out",
        "name": "notification",
        "hubName": "MR_NotHub_ServiceInstance",
        "connection": "MRNotHubNS_DefaultFullSharedAccessSignature_NH",
        "platform": "wns"
        }
    ]
    }
    ```

26. <span data-ttu-id="4ad1b-380">El editor debe ser ahora similar a la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-380">Your editor should now look like the image below:</span></span>

    ![volver al editor estándar](images/AzureLabs-Lab8-47.png)

27. <span data-ttu-id="4ad1b-382">Es posible que observe que los parámetros de entrada que acaba de insertar podrían no coincidir con los detalles de almacenamiento y tabla y, por tanto, deben actualizarse con la información.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-382">You may notice the input parameters that you have just inserted might not match your table and storage details and therefore will need to be updated with your information.</span></span> <span data-ttu-id="4ad1b-383">No **lo haga aquí**, como se explica a continuación.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-383">**Do not do this here**, as it is covered next.</span></span> <span data-ttu-id="4ad1b-384">Simplemente haga clic en el vínculo **Editor estándar** , en la esquina superior derecha de la página, para volver atrás.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-384">Simply click the **Standard editor** link, in the top-right corner of the page, to go back.</span></span>

28. <span data-ttu-id="4ad1b-385">De nuevo en el **Editor estándar**, haga clic en **Azure Table Storage (tabla)** , en **entradas**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-385">Back in the **Standard editor**, click **Azure Table Storage (table)**, under **Inputs**.</span></span> 
    
    ![Entradas de tabla](images/AzureLabs-Lab8-47-5.png)

29. <span data-ttu-id="4ad1b-387">Asegúrese de que la siguiente coincidencia con **su** información es diferente (hay una imagen por debajo de los pasos siguientes):</span><span class="sxs-lookup"><span data-stu-id="4ad1b-387">Ensure the following match to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="4ad1b-388">**Nombre de tabla**: el nombre de la tabla que ha creado en el Azure Storage, Table Service.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-388">**Table name**: the name of the table you created within your Azure Storage, Tables service.</span></span>

    2.  <span data-ttu-id="4ad1b-389">**Conexión de la cuenta de almacenamiento:** haga clic en **nuevo**, que aparece junto al menú desplegable, y aparecerá un panel a la derecha de la ventana.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-389">**Storage account connection:** click **new**, which appears alongside the dropdown menu, and a panel will appear to the right of the window.</span></span>

        ![nuevo almacenamiento](images/AzureLabs-Lab8-48.png)

        1.  <span data-ttu-id="4ad1b-391">Seleccione la **cuenta de almacenamiento**que creó anteriormente para hospedar las **aplicaciones de función.**</span><span class="sxs-lookup"><span data-stu-id="4ad1b-391">Select your **Storage Account**, which you created previously to host the **Function Apps.**</span></span>

        2. <span data-ttu-id="4ad1b-392">Observará que se ha creado el valor de conexión de la **cuenta de almacenamiento** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-392">You will notice that the **Storage Account** connection value has been created.</span></span>

        3. <span data-ttu-id="4ad1b-393">Asegúrese de presionar **Guardar** cuando haya terminado.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-393">Make sure to press **Save** once you are done.</span></span>

    3.  <span data-ttu-id="4ad1b-394">La página **entradas** debe coincidir con la que se muestra a continuación, mostrando **su** información.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-394">The **Inputs** page should now match the below, showing **your** information.</span></span>

        ![entradas completadas](images/AzureLabs-Lab8-49.png)

30. <span data-ttu-id="4ad1b-396">A continuación, haga clic en centro de notificaciones de **Azure (notificación)** en **salidas**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-396">Next, click **Azure Notification Hub (notification)** - under **Outputs**.</span></span> <span data-ttu-id="4ad1b-397">Asegúrese de que los siguientes elementos coinciden con **su** información, ya que pueden ser diferentes (hay una imagen por debajo de los pasos siguientes):</span><span class="sxs-lookup"><span data-stu-id="4ad1b-397">Ensure the following are matched to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="4ad1b-398">**Nombre del centro**de notificaciones: este es el nombre de la instancia de servicio del **Centro** de notificaciones que creó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-398">**Notification Hub Name**: this is the name of your **Notification Hub** service instance, which you created previously.</span></span>

    2.  <span data-ttu-id="4ad1b-399">**Notification hubs conexión de espacio de nombres**: haga clic en **nuevo**, que aparece junto al menú desplegable.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-399">**Notification Hubs namespace connection**: click **new**, which appears alongside the dropdown menu.</span></span>

        ![comprobar salidas](images/AzureLabs-Lab8-50.png)

    3. <span data-ttu-id="4ad1b-401">Aparecerá el cuadro emergente de **conexión** (consulte la imagen siguiente), donde debe seleccionar el **espacio de nombres** del **Centro**de notificaciones, que configuró anteriormente.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-401">The **Connection** popup will appear (see image below), where you need to select the **Namespace** of the **Notification Hub**, which you set up previously.</span></span>

    4. <span data-ttu-id="4ad1b-402">Seleccione el nombre del **Centro** de notificaciones en el menú desplegable central.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-402">Select your **Notification Hub** name from the middle dropdown menu.</span></span>

    5.  <span data-ttu-id="4ad1b-403">Establezca el menú desplegable **Directiva** en **DefaultFullSharedAccessSignature**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-403">Set the **Policy** dropdown menu to **DefaultFullSharedAccessSignature**.</span></span>

    6. <span data-ttu-id="4ad1b-404">Haga clic en el botón **seleccionar** para volver atrás.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-404">Click the **Select** button to go back.</span></span>

        ![actualización de salida](images/AzureLabs-Lab8-51.png)

31.  <span data-ttu-id="4ad1b-406">La página de **resultados** debe coincidir ahora con la siguiente, pero con **su** información en su lugar.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-406">The **Outputs** page should now match the below, but with **your** information instead.</span></span> <span data-ttu-id="4ad1b-407">Asegúrese de presionar **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-407">Make sure to press **Save**.</span></span>

> [!WARNING]
> <span data-ttu-id="4ad1b-408">*No editar el nombre del centro de notificaciones directamente* (todo esto debe realizarse mediante el **editor avanzado**, siempre y cuando haya seguido los pasos anteriores correctamente.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-408">*Do not edit the Notification Hub name directly* (this should all be done using the **Advanced Editor**, provided you followed the previous steps correctly.</span></span>

![salidas completadas](images/AzureLabs-Lab8-50.png)

32. <span data-ttu-id="4ad1b-410">En este punto, debe probar la función para asegurarse de que funciona.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-410">At this point, you should test the function, to ensure it is working.</span></span> <span data-ttu-id="4ad1b-411">Para ello:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-411">To do this:</span></span> 

    1. <span data-ttu-id="4ad1b-412">Vaya a la página de la función una vez más:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-412">Navigate to the function page once more:</span></span>

        ![salidas completadas](images/AzureLabs-Lab8-50-1.png)

    2. <span data-ttu-id="4ad1b-414">De nuevo en la página de la función, haga clic en la pestaña **probar** en el extremo derecho de la página para abrir la hoja *prueba* :</span><span class="sxs-lookup"><span data-stu-id="4ad1b-414">Back on the function page, click the **Test** tab on the far right side of the page, to open the *Test* blade:</span></span>

        ![salidas completadas](images/AzureLabs-Lab8-50-2.png)

    3. <span data-ttu-id="4ad1b-416">En el cuadro de texto cuerpo de la **solicitud** de la hoja, pegue el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-416">Within the **Request body** textbox of the blade, paste the below code:</span></span>

        ```
        {  
            "Type":null,
            "X":3,
            "Y":0,
            "Z":1,
            "PartitionKey":null,
            "RowKey":"Obj2",
            "Timestamp":"0001-01-01T00:00:00+00:00",
            "ETag":null
        }
        ```

    4. <span data-ttu-id="4ad1b-417">Con el código de prueba en su lugar, haga clic en el botón **Ejecutar** situado en la parte inferior derecha y se ejecutará la prueba.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-417">With the test code in place, click the **Run** button at the bottom right, and the test will be run.</span></span> <span data-ttu-id="4ad1b-418">Los registros de salida de la prueba aparecerán en el área de la consola, debajo del código de la función.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-418">The output logs of the test will appear in the console area, below your function code.</span></span>

        ![salidas completadas](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > <span data-ttu-id="4ad1b-420">Si se produce un error en la prueba anterior, tendrá que comprobar que ha seguido los pasos anteriores exactamente, en particular, en el **Panel de integración**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-420">If the above test fails, you will need to double check that you have followed the above steps exactly, particularly the settings within the **integrate panel**.</span></span> 

## <a name="chapter-7---set-up-desktop-unity-project"></a><span data-ttu-id="4ad1b-421">Capítulo 7: configurar un proyecto de Unity de escritorio</span><span class="sxs-lookup"><span data-stu-id="4ad1b-421">Chapter 7 - Set up Desktop Unity Project</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4ad1b-422">La aplicación de escritorio que está creando ahora **no** funcionará en el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-422">The Desktop application which you are now creating, **will not** work in the Unity Editor.</span></span> <span data-ttu-id="4ad1b-423">Debe ejecutarse fuera del editor, después de la compilación de la aplicación, mediante Visual Studio (o la aplicación implementada).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-423">It needs to be run outside of the Editor, following the Building of the application, using Visual Studio (or the deployed application).</span></span> 

<span data-ttu-id="4ad1b-424">Lo siguiente es una configuración típica para desarrollar con Unity y la realidad mixta, y como tal, es una buena plantilla para otros proyectos.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-424">The following is a typical set up for developing with Unity and mixed reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="4ad1b-425">Configure y pruebe sus auriculares de la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-425">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE] 
> <span data-ttu-id="4ad1b-426">**No** necesitará controladores de movimiento para este curso.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-426">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="4ad1b-427">Si necesita ayuda para configurar el casco inmersivo, siga este [vínculo sobre cómo configurar Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-427">If you need support setting up the immersive headset, please follow this [link on how to set up Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="4ad1b-428">Abra **Unity** y haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-428">Open **Unity** and click **New**.</span></span>

    ![nuevo proyecto de Unity](images/AzureLabs-Lab8-52.png)

2.  <span data-ttu-id="4ad1b-430">Debe proporcionar un nombre de proyecto de Unity, insertar **UnityDesktopNotifHub**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-430">You need to provide a Unity Project name, insert **UnityDesktopNotifHub**.</span></span> <span data-ttu-id="4ad1b-431">Asegúrese de que el tipo de proyecto está establecido en **3D**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-431">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="4ad1b-432">Establezca la **Ubicación** en algún lugar adecuado para usted (Recuerde que, más cerca de los directorios raíz es mejor).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-432">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="4ad1b-433">A continuación, haga clic en **crear proyecto**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-433">Then, click **Create project**.</span></span>

    ![crear proyecto](images/AzureLabs-Lab8-53.png)

3.  <span data-ttu-id="4ad1b-435">Con Unity abierto, merece la pena comprobar que el **Editor** de scripts predeterminado está establecido en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-435">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="4ad1b-436">Vaya a **Editar** > **preferencias** y, a continuación, en la nueva ventana, vaya a **herramientas externas**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-436">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="4ad1b-437">Cambie el **Editor de script externo** a **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-437">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="4ad1b-438">Cierre la ventana **preferencias** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-438">Close the **Preferences** window.</span></span>

    ![establecer herramientas externas de VS](images/AzureLabs-Lab8-54.png)

4.  <span data-ttu-id="4ad1b-440">A continuación, vaya a**configuración de compilación** de **archivos** > y seleccione **plataforma universal de Windows**y, a continuación, haga clic en el botón **cambiar plataforma** para aplicar la selección.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-440">Next, go to **File** > **Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![cambiar plataformas](images/AzureLabs-Lab8-55.png)

5.  <span data-ttu-id="4ad1b-442">Mientras sigue en la**configuración de compilación**de **archivos** > , asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-442">While still in **File** > **Build Settings**, make sure that:</span></span>

    1.  <span data-ttu-id="4ad1b-443">El **dispositivo de destino** se establece en **cualquier dispositivo**</span><span class="sxs-lookup"><span data-stu-id="4ad1b-443">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="4ad1b-444">Esta aplicación será para el escritorio, por lo que debe ser **cualquier dispositivo** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-444">This Application will be for your desktop, so must be **Any Device**</span></span>

    2.  <span data-ttu-id="4ad1b-445">El **tipo de compilación** se establece en **D3D**</span><span class="sxs-lookup"><span data-stu-id="4ad1b-445">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="4ad1b-446">**SDK** está establecido en la **versión más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="4ad1b-446">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="4ad1b-447">La **versión de Visual Studio** está establecida en la **más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="4ad1b-447">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="4ad1b-448">**Compilar y ejecutar** está establecido en **equipo local**</span><span class="sxs-lookup"><span data-stu-id="4ad1b-448">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="4ad1b-449">Mientras tanto, merece la pena guardar la escena y agregarla a la compilación.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-449">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="4ad1b-450">Para ello, seleccione **Agregar escenas abiertas**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-450">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="4ad1b-451">Aparecerá una ventana de guardar.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-451">A save window will appear.</span></span>

            ![agregar escenas abiertas](images/AzureLabs-Lab8-56.png)

        2. <span data-ttu-id="4ad1b-453">Cree una nueva carpeta para este, y en cualquier momento, en el futuro, seleccione el botón **nueva carpeta** para crear una nueva carpeta, asígneleel nombre Scenes.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-453">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![nueva carpeta Scenes](images/AzureLabs-Lab8-57.png)

        3. <span data-ttu-id="4ad1b-455">Abra la carpeta Scenes recién creada y, a continuación, en el campo **nombre de archivo:** , escriba **NH\_Desktop\_Scene**y, a continuación, presione **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-455">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_Desktop\_Scene**, then press **Save**.</span></span>

            ![nuevo NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  <span data-ttu-id="4ad1b-457">El resto de la configuración, en la **configuración de compilación**, debe dejarse como predeterminada por ahora.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-457">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="4ad1b-458">En la misma ventana, haga clic en el botón **configuración del reproductor** ; se abrirá el panel relacionado en el espacio donde se encuentra el **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-458">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7.  <span data-ttu-id="4ad1b-459">En este panel, deben comprobarse algunas opciones de configuración:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-459">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="4ad1b-460">En la pestaña **otros valores** :</span><span class="sxs-lookup"><span data-stu-id="4ad1b-460">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="4ad1b-461">La **versión de scripting en tiempo de ejecución** debe ser **Experimental (.net 4,6 equivalente)**</span><span class="sxs-lookup"><span data-stu-id="4ad1b-461">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**</span></span>

        2. <span data-ttu-id="4ad1b-462">El **back-end** de scripting debe ser **.net**</span><span class="sxs-lookup"><span data-stu-id="4ad1b-462">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="4ad1b-463">El **nivel de compatibilidad de API** debe ser **.net 4,6**</span><span class="sxs-lookup"><span data-stu-id="4ad1b-463">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![versión de 4,6 net](images/AzureLabs-Lab8-59.png)

    2.  <span data-ttu-id="4ad1b-465">En la pestaña **configuración de publicación** , en **capacidades**, seleccione:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-465">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="4ad1b-466">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="4ad1b-466">**InternetClient**</span></span>

            ![marcar el cliente de Internet](images/AzureLabs-Lab8-60.png)

8.  <span data-ttu-id="4ad1b-468">De nuevo en la **configuración de compilación** , los *proyectos de Unity C\#*  ya no están atenuados; Marque la casilla situada junto a este.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-468">Back in **Build Settings** *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="4ad1b-469">Cierre la ventana **configuración de compilación** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-469">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="4ad1b-470">Guarde la escena y el **archivo** > de proyecto**Guardar escena/archivo** > **Guardar proyecto**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-470">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="4ad1b-471">Si desea omitir el componente de *configuración de Unity* para este proyecto (aplicación de escritorio) y continuar directamente en el código, no dude en [Descargar este. unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), impórtelo en el proyecto como un [**paquete personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)y, después, continúe con el [capítulo. 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-471">If you wish to skip the *Unity Set up* component for this project (Desktop App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>  <span data-ttu-id="4ad1b-472">Todavía tendrá que agregar los componentes de script.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-472">You will still need to add the script components.</span></span>

## <a name="chapter-8---importing-the-dlls-in-unity"></a><span data-ttu-id="4ad1b-473">Capítulo 8: importación de los archivos dll en Unity</span><span class="sxs-lookup"><span data-stu-id="4ad1b-473">Chapter 8 - Importing the DLLs in Unity</span></span>

<span data-ttu-id="4ad1b-474">Usará Azure Storage para Unity (que a su vez usa el SDK de .net para Azure).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-474">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="4ad1b-475">Para obtener más información, siga este [vínculo sobre Azure Storage para Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-475">For more information follow this [link about Azure Storage for Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="4ad1b-476">Actualmente hay un problema conocido en Unity que requiere que los complementos se vuelvan a configurar después de la importación.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-476">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="4ad1b-477">Estos pasos (4-7 en esta sección) ya no serán necesarios una vez resuelto el error.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-477">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="4ad1b-478">Para importar el SDK en su propio proyecto, asegúrese de que ha descargado el [ **. unitypackage Tools**](https://aka.ms/azstorage-unitysdk) más reciente de github.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-478">To import the SDK into your own project, make sure you have downloaded the latest [**.unitypackage**](https://aka.ms/azstorage-unitysdk) from GitHub.</span></span> <span data-ttu-id="4ad1b-479">A continuación, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-479">Then, do the following:</span></span>

1.  <span data-ttu-id="4ad1b-480">Agregue el **. unitypackage Tools** a Unity mediante la opción de menú de  **\> paquetes \> importar paquete personalizado** de paquetes.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-480">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="4ad1b-481">En el cuadro **importar paquete Unity** que aparece, puede seleccionar todo en **plugin**\>**Storage**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-481">In the **Import Unity Package** box that pops up, you can select everything under \*\**Plugin* \> \*Storage\*\*\*.</span></span>  <span data-ttu-id="4ad1b-482">Desactive todo lo demás, ya que no es necesario para este curso.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-482">Uncheck everything else, as it is not needed for this course.</span></span>

    ![importar a paquete](images/AzureLabs-Lab8-61.png)

3.  <span data-ttu-id="4ad1b-484">Haga clic en el botón ***importar*** para agregar los elementos al proyecto.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-484">Click the ***Import*** button to add the items to your project.</span></span>

4.  <span data-ttu-id="4ad1b-485">Vaya a la carpeta **Storage** en **Complementos** en la vista proyecto y seleccione *solo*los siguientes complementos:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-485">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="4ad1b-486">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="4ad1b-486">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="4ad1b-487">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="4ad1b-487">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="4ad1b-488">Microsoft. WindowsAzure. Storage</span><span class="sxs-lookup"><span data-stu-id="4ad1b-488">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="4ad1b-489">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="4ad1b-489">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="4ad1b-490">System. espacial</span><span class="sxs-lookup"><span data-stu-id="4ad1b-490">System.Spatial</span></span>

![desactive cualquier plataforma](images/AzureLabs-Lab8-62.png)

5.  <span data-ttu-id="4ad1b-492">Con *estos complementos específicos* seleccionados, **desactive** **cualquier plataforma** y **desactive** **WSAPlayer** y haga clic en **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-492">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![aplicar dll de plataforma](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > <span data-ttu-id="4ad1b-494">Estamos marcando estos complementos concretos para usarlos solo en el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-494">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="4ad1b-495">Esto se debe a que hay diferentes versiones de los mismos complementos en la carpeta WSA que se usarán después de exportar el proyecto desde Unity.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-495">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="4ad1b-496">En la carpeta del complemento de **almacenamiento** , seleccione solo:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-496">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="4ad1b-497">Microsoft. Data. Services. Client</span><span class="sxs-lookup"><span data-stu-id="4ad1b-497">Microsoft.Data.Services.Client</span></span>

        ![establecer no procesar para archivos dll](images/AzureLabs-Lab8-64.png)

7.  <span data-ttu-id="4ad1b-499">Active la casilla **no procesar** en **configuración de plataforma** y haga clic en ***aplicar***.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-499">Check the **Don't Process** box under **Platform Settings** and click ***Apply***.</span></span>

    ![no aplicar procesamiento](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > <span data-ttu-id="4ad1b-501">Estamos marcando este complemento como "no procesar", ya que el parche de ensamblado de Unity tiene dificultades para procesar este complemento.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-501">We are marking this plugin "Don't process", because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="4ad1b-502">El complemento seguirá funcionando aunque no se haya procesado.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-502">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="4ad1b-503">Capítulo 9: creación de la clase TableToScene en el proyecto de Unity de escritorio</span><span class="sxs-lookup"><span data-stu-id="4ad1b-503">Chapter 9 - Create the TableToScene class in the Desktop Unity project</span></span>

<span data-ttu-id="4ad1b-504">Ahora debe crear los scripts que contienen el código para ejecutar esta aplicación.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-504">You now need to create the scripts containing the code to run this application.</span></span>

<span data-ttu-id="4ad1b-505">El primer script que debe crear es **TableToScene**, que es responsable de:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-505">The first script you need to create is **TableToScene**, which is responsible for:</span></span>

-   <span data-ttu-id="4ad1b-506">Lectura de entidades en la tabla de Azure.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-506">Reading entities within the Azure Table.</span></span>
-   <span data-ttu-id="4ad1b-507">Con los datos de la tabla, determine qué objetos generar y en qué posición.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-507">Using the Table data, determine which objects to spawn, and in which position.</span></span>

<span data-ttu-id="4ad1b-508">El segundo script que debe crear es **CloudScene**, que es responsable de:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-508">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="4ad1b-509">Registrar el evento de clic izquierdo para permitir que el usuario arrastre objetos alrededor de la escena.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-509">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>
-   <span data-ttu-id="4ad1b-510">Serializar los datos de objeto de esta escena de Unity y enviarlos a Azure Function App.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-510">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="4ad1b-511">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-511">To create this class:</span></span>

1.  <span data-ttu-id="4ad1b-512">Haga clic con el botón derecho en la carpeta de **recursos** que se encuentra en el panel Proyecto, **crear** > **carpeta**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-512">Right-click in the **Asset** Folder located in the Project Panel, **Create** > **Folder**.</span></span> <span data-ttu-id="4ad1b-513">Asigne a lacarpeta el nombre scripts.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-513">Name the folder **Scripts**.</span></span>

    ![crear carpeta de scripts](images/AzureLabs-Lab8-66.png)

    ![crear scripts (carpeta 2)](images/AzureLabs-Lab8-67.png)

2.  <span data-ttu-id="4ad1b-516">Haga doble clic en la carpeta que acaba de crear para abrirla.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-516">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="4ad1b-517">Haga clic con el botón derecho en la carpeta scripts y haga clic en **crear**  >   **C# script**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-517">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="4ad1b-518">Asigne al script el nombre **TableToScene**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-518">Name the script **TableToScene**.</span></span>

    <span data-ttu-id="4ad1b-519">![nuevo script](images/AzureLabs-Lab8-68.png)
    ![de c# TableToScene Rename](images/AzureLabs-Lab8-69.png)</span><span class="sxs-lookup"><span data-stu-id="4ad1b-519">![new c# script](images/AzureLabs-Lab8-68.png)
![TableToScene rename](images/AzureLabs-Lab8-69.png)</span></span>

4.  <span data-ttu-id="4ad1b-520">Haga doble clic en el script para abrirlo en Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-520">Double-click on the script to open it in Visual Studio 2017.</span></span>

5.  <span data-ttu-id="4ad1b-521">Agregue los siguientes espacios de nombres:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-521">Add the following namespaces:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  <span data-ttu-id="4ad1b-522">Dentro de la clase, inserte las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-522">Within the class, insert the following variables:</span></span>

    ```csharp
        /// <summary>    
        /// allows this class to behave like a singleton
        /// </summary>    
        public static TableToScene instance;

        /// <summary>    
        /// Insert here you Azure Storage name     
        /// </summary>    
        private string accountName = " -- Insert your Azure Storage name -- ";

        /// <summary>    
        /// Insert here you Azure Storage key    
        /// </summary>    
        private string accountKey = " -- Insert your Azure Storage key -- ";
    ```
    
    > [!NOTE] 
    > <span data-ttu-id="4ad1b-523">Sustituya el valor **accountName** por el nombre del servicio de Azure Storage y el valor **accountKey** por el valor de clave que se encuentra en el servicio Azure Storage, en Azure portal (consulte la imagen siguiente).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-523">Substitute the **accountName** value with your Azure Storage Service name and **accountKey** value with the key value found in the Azure Storage Service, in the Azure Portal (See Image below).</span></span> 
    >
    > ![capturar clave de cuenta](images/AzureLabs-Lab8-70.png)

7.  <span data-ttu-id="4ad1b-525">Ahora, agregue los métodos **Start ()** y Activate **()** para inicializar la clase.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-525">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {  
            // Call method to populate the scene with new objects as 
            // pecified in the Azure Table
            PopulateSceneFromTableAsync();
        }
    ```

8.  <span data-ttu-id="4ad1b-526">Dentro de la clase **TableToScene** , agregue el método que recuperará los valores de la tabla de Azure y los usará para generar los primitivos adecuados en la escena.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-526">Within the **TableToScene** class, add the method that will retrieve the values from the Azure Table and use them to spawn the appropriate primitives in the scene.</span></span>

    ```csharp
        /// <summary>    
        /// Populate the scene with new objects as specified in the Azure Table    
        /// </summary>    
        private async void PopulateSceneFromTableAsync()
        {
            // Obtain credentials for the Azure Storage
            StorageCredentials creds = new StorageCredentials(accountName, accountKey);

            // Storage account
            CloudStorageAccount account = new CloudStorageAccount(creds, useHttps: true);
            
            // Storage client
            CloudTableClient client = account.CreateCloudTableClient(); 
            
            // Table reference
            CloudTable table = client.GetTableReference("SceneObjectsTable");

            TableContinuationToken token = null;

            // Query the table for every existing Entity
            do
            {
                // Queries the whole table by breaking it into segments
                // (would happen only if the table had huge number of Entities)
                TableQuerySegment<AzureTableEntity> queryResult = await table.ExecuteQuerySegmentedAsync(new TableQuery<AzureTableEntity>(), token); 

                foreach (AzureTableEntity entity in queryResult.Results)
                {
                    GameObject newSceneGameObject = null;
                    Color newColor;

                    // check for the Entity Type and spawn in the scene the appropriate Primitive
                    switch (entity.Type)
                    {
                        case "Cube":
                            // Create a Cube in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                            newColor = Color.blue;
                            break;

                        case "Sphere":
                            // Create a Sphere in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                            newColor = Color.red;
                            break;

                        case "Cylinder":
                            // Create a Cylinder in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                            newColor = Color.yellow;
                            break;
                        default:
                            newColor = Color.white;
                            break;
                    }

                    newSceneGameObject.name = entity.RowKey;

                    newSceneGameObject.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
                    {
                        color = newColor
                    };

                    //check for the Entity X,Y,Z and move the Primitive at those coordinates
                    newSceneGameObject.transform.position = new Vector3((float)entity.X, (float)entity.Y, (float)entity.Z);
                }

                // if the token is null, it means there are no more segments left to query
                token = queryResult.ContinuationToken;
            }

            while (token != null);
        }
    ```

9.  <span data-ttu-id="4ad1b-527">Fuera de la clase **TableToScene** , debe definir la clase utilizada por la aplicación para serializar y deserializar las **entidades de tabla**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-527">Outside the **TableToScene** class, you need to define the class used by the application to serialize and deserialize the **Table Entities**.</span></span>

    ```csharp
        /// <summary>
        /// This objects is used to serialize and deserialize the Azure Table Entity
        /// </summary>
        [System.Serializable]
        public class AzureTableEntity : TableEntity
        {
            public AzureTableEntity(string partitionKey, string rowKey)
                : base(partitionKey, rowKey) { }

            public AzureTableEntity() { }
            public string Type { get; set; }
            public double X { get; set; }
            public double Y { get; set; }
            public double Z { get; set; }
        }
    ```

10. <span data-ttu-id="4ad1b-528">Asegúrese de **Guardar** antes de volver al editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-528">Make sure you **Save** before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="4ad1b-529">En el panel **jerarquía** , haga clic en la **cámara principal** para que sus propiedades aparezcan en el **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-529">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="4ad1b-530">Con la carpeta scripts abierta, seleccione el **archivo** de script TableToScene y arrástrelo a la **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-530">With the **Scripts** folder open, select the script **TableToScene file** and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="4ad1b-531">El resultado debe ser el siguiente:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-531">The result should be as below:</span></span>

    ![Agregar script a la cámara principal](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="4ad1b-533">Capítulo 10: creación de la clase CloudScene en el proyecto de Unity de escritorio</span><span class="sxs-lookup"><span data-stu-id="4ad1b-533">Chapter 10 - Create the CloudScene class in the Desktop Unity Project</span></span>

<span data-ttu-id="4ad1b-534">El segundo script que debe crear es **CloudScene**, que es responsable de:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-534">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="4ad1b-535">Registrar el evento de clic izquierdo para permitir que el usuario arrastre objetos alrededor de la escena.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-535">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>

-   <span data-ttu-id="4ad1b-536">Serializar los datos de objeto de esta escena de Unity y enviarlos a Azure Function App.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-536">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="4ad1b-537">Para crear el segundo script:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-537">To create the second script:</span></span>

1.  <span data-ttu-id="4ad1b-538">Haga clic con el botón derecho en la carpeta scripts, haga clic en **crear**, **script de C\#** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-538">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="4ad1b-539">Asigne un nombre al script **CloudScene**</span><span class="sxs-lookup"><span data-stu-id="4ad1b-539">Name the script **CloudScene**</span></span>
    
    <span data-ttu-id="4ad1b-540">![nuevo script](images/AzureLabs-Lab8-72.png)
    ![de c# Rename CloudScene](images/AzureLabs-Lab8-73.png)</span><span class="sxs-lookup"><span data-stu-id="4ad1b-540">![new c# script](images/AzureLabs-Lab8-72.png)
![rename CloudScene](images/AzureLabs-Lab8-73.png)</span></span>

2.  <span data-ttu-id="4ad1b-541">Agregue los siguientes espacios de nombres:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-541">Add the following namespaces:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  <span data-ttu-id="4ad1b-542">Inserte las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-542">Insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CloudScene instance;

        /// <summary>
        /// Insert here you Azure Function Url
        /// </summary>
        private string azureFunctionEndpoint = "--Insert here you Azure Function Endpoint--";

        /// <summary>
        /// Flag for object being moved
        /// </summary>
        private bool gameObjHasMoved;

        /// <summary>
        /// Transform of the object being dragged by the mouse
        /// </summary>
        private Transform gameObjHeld;

        /// <summary>
        /// Class hosted in the TableToScene script
        /// </summary>
        private AzureTableEntity azureTableEntity;
    ```

4.  <span data-ttu-id="4ad1b-543">Sustituya el valor de **azureFunctionEndpoint** por la dirección URL de Azure function App que se encuentra en el servicio Azure function App, en Azure portal, tal como se muestra en la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-543">Substitute the **azureFunctionEndpoint** value with your Azure Function App URL found in the Azure Function App Service, in the Azure Portal, as shown in the image below:</span></span>

    ![Obtener dirección URL de la función](images/AzureLabs-Lab8-74.png)

5.  <span data-ttu-id="4ad1b-545">Ahora, agregue los métodos **Start ()** y Activate **()** para inicializar la clase.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-545">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // initialise an AzureTableEntity
            azureTableEntity = new AzureTableEntity();
        }
    ```

6.  <span data-ttu-id="4ad1b-546">En el método **Update ()** , agregue el siguiente código que detectará la entrada del mouse y arrastre, que a su vez moverá GameObjects en la escena.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-546">Within the **Update()** method, add the following code that will detect the mouse input and drag, which will in turn move GameObjects in the scene.</span></span> <span data-ttu-id="4ad1b-547">Si el usuario ha arrastrado y colocado un objeto, pasará el nombre y las coordenadas del objeto al método **UpdateCloudScene ()** , que llamará al servicio Azure function App, que actualizará la tabla de Azure y desencadenará la notificación.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-547">If the user has dragged and dropped an object, it will pass the name and coordinates of the object to the method **UpdateCloudScene()**, which will call the Azure Function App service, which will update the Azure table and trigger the notification.</span></span>

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            //Enable Drag if button is held down
            if (Input.GetMouseButton(0))
            {
                // Get the mouse position
                Vector3 mousePosition = new Vector3(Input.mousePosition.x, Input.mousePosition.y, 10);

                Vector3 objPos = Camera.main.ScreenToWorldPoint(mousePosition);

                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

                RaycastHit hit;

                // Raycast from the current mouse position to the object overlapped by the mouse
                if (Physics.Raycast(ray, out hit))
                {
                    // update the position of the object "hit" by the mouse
                    hit.transform.position = objPos;

                    gameObjHasMoved = true;

                    gameObjHeld = hit.transform;
                }
            }

            // check if the left button mouse is released while holding an object
            if (Input.GetMouseButtonUp(0) && gameObjHasMoved)
            {
                gameObjHasMoved = false;

                // Call the Azure Function that will update the appropriate Entity in the Azure Table
                // and send a Notification to all subscribed Apps
                Debug.Log("Calling Azure Function");

                StartCoroutine(UpdateCloudScene(gameObjHeld.name, gameObjHeld.position.x, gameObjHeld.position.y, gameObjHeld.position.z));
            }
        }
    ```

7.  <span data-ttu-id="4ad1b-548">Ahora, agregue el método **UpdateCloudScene ()** , como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-548">Now add the **UpdateCloudScene()** method, as below:</span></span>

    ```csharp
        private IEnumerator UpdateCloudScene(string objName, double xPos, double yPos, double zPos)
        {
            WWWForm form = new WWWForm();

            // set the properties of the AzureTableEntity
            azureTableEntity.RowKey = objName;

            azureTableEntity.X = xPos;

            azureTableEntity.Y = yPos;

            azureTableEntity.Z = zPos;

            // Serialize the AzureTableEntity object to be sent to Azure
            string jsonObject = JsonConvert.SerializeObject(azureTableEntity);

            using (UnityWebRequest www = UnityWebRequest.Post(azureFunctionEndpoint, jsonObject))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(jsonObject);

                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.uploadHandler.contentType = "application/json";

                www.downloadHandler = new DownloadHandlerBuffer();

                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                string response = www.responseCode.ToString();
            }
        }
    ```

8.  <span data-ttu-id="4ad1b-549">Guardar el código y volver a Unity</span><span class="sxs-lookup"><span data-stu-id="4ad1b-549">Save the code and return to Unity</span></span>

9.  <span data-ttu-id="4ad1b-550">Arrastre el script **CloudScene** a la **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-550">Drag the **CloudScene** script onto the **Main Camera**.</span></span> 

    1. <span data-ttu-id="4ad1b-551">En el panel **jerarquía** , haga clic en la **cámara principal** para que sus propiedades aparezcan en el **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-551">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span> 

    2. <span data-ttu-id="4ad1b-552">Con la carpeta scripts abierta, seleccione el script **CloudScene** y arrástrelo a la **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-552">With the **Scripts** folder open, select the **CloudScene** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="4ad1b-553">El resultado debe ser el siguiente:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-553">The result should be as below:</span></span>

        > ![Arrastre el script de nube a la cámara principal](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a><span data-ttu-id="4ad1b-555">Capítulo 11: compilar el proyecto de escritorio en UWP</span><span class="sxs-lookup"><span data-stu-id="4ad1b-555">Chapter 11 - Build the Desktop Project to UWP</span></span>

<span data-ttu-id="4ad1b-556">Ya se ha completado todo lo necesario para la sección Unity de este proyecto.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-556">Everything needed for the Unity section of this project has now been completed.</span></span>

1.  <span data-ttu-id="4ad1b-557">Vaya a **configuración de compilación** (**configuración de compilación**de**archivos** > ).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-557">Navigate to **Build Settings** (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="4ad1b-558">En la ventana **configuración de compilación** , haga clic en compilar.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-558">From the **Build Settings** window, click **Build**.</span></span>

    ![compilar proyecto](images/AzureLabs-Lab8-76.png)

3.  <span data-ttu-id="4ad1b-560">Se abrirá una ventana del **Explorador de archivos** en la que se le solicitará una ubicación para compilar.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-560">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="4ad1b-561">Cree una nueva carpeta (haciendo clic en **nueva carpeta** en la esquina superior izquierda) y asígnele el nombrecompilaciones.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-561">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![nueva carpeta para compilación](images/AzureLabs-Lab8-77.png)

    1.  <span data-ttu-id="4ad1b-563">Abra la nueva carpeta Compilaciones y cree otra carpeta (con la **nueva carpeta** una vez más) y asígnele el nombre **\_NH Desktop\_App**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-563">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_Desktop\_App**.</span></span>

        ![nombre de carpeta NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  <span data-ttu-id="4ad1b-565">Con la **aplicación\_NH\_Desktop** seleccionada.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-565">With the **NH\_Desktop\_App** selected.</span></span> <span data-ttu-id="4ad1b-566">Haga clic en **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-566">click **Select Folder**.</span></span> <span data-ttu-id="4ad1b-567">El proyecto tardará un minuto o más en compilarse.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-567">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="4ad1b-568">Después de la compilación, aparecerá el **Explorador de archivos** que muestra la ubicación del nuevo proyecto.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-568">Following build, **File Explorer** will appear showing you the location of your new project.</span></span> <span data-ttu-id="4ad1b-569">Sin embargo, no es necesario abrirlo, ya que primero debe crear el otro proyecto de Unity, en los próximos capítulos.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-569">No need to open it, though, as you need to create the other Unity project first, in the next few Chapters.</span></span>


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a><span data-ttu-id="4ad1b-570">Capítulo 12: configuración de un proyecto de Unity de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="4ad1b-570">Chapter 12 - Set up Mixed Reality Unity Project</span></span>

<span data-ttu-id="4ad1b-571">Lo siguiente es una configuración típica para desarrollar con la realidad mixta y, como tal, es una buena plantilla para otros proyectos.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-571">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="4ad1b-572">Abra **Unity** y haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-572">Open **Unity** and click **New**.</span></span>

    ![nuevo proyecto de Unity](images/AzureLabs-Lab8-79.png)

2.  <span data-ttu-id="4ad1b-574">Ahora tendrá que proporcionar un nombre de proyecto de Unity, insertar **UnityMRNotifHub**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-574">You will now need to provide a Unity Project name, insert **UnityMRNotifHub**.</span></span> <span data-ttu-id="4ad1b-575">Asegúrese de que el tipo de proyecto está establecido en **3D**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-575">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="4ad1b-576">Establezca la **Ubicación** en algún lugar adecuado para usted (Recuerde que, más cerca de los directorios raíz es mejor).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-576">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="4ad1b-577">A continuación, haga clic en **crear proyecto**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-577">Then, click **Create project**.</span></span>

    ![nombre UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  <span data-ttu-id="4ad1b-579">Con Unity abierto, merece la pena comprobar que el **Editor** de scripts predeterminado está establecido en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-579">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="4ad1b-580">Vaya a **Editar** > **preferencias** y, a continuación, en la nueva ventana, vaya a **herramientas externas**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-580">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="4ad1b-581">Cambie el **Editor de script externo** a **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-581">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="4ad1b-582">Cierre la ventana **preferencias** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-582">Close the **Preferences** window.</span></span>

    ![establecer el editor externo en VS](images/AzureLabs-Lab8-81.png)

4.  <span data-ttu-id="4ad1b-584">A continuación, vaya a**configuración de compilación** de **archivos** > y cambie la plataforma a **plataforma universal de Windows**, haciendo clic en el botón **cambiar plataforma** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-584">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![cambiar de plataforma a UWP](images/AzureLabs-Lab8-82.png)

5.  <span data-ttu-id="4ad1b-586">Vaya a**configuración de compilación** de **archivos** > y asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-586">Go to **File** > **Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="4ad1b-587">El **dispositivo de destino** se establece en **cualquier dispositivo**</span><span class="sxs-lookup"><span data-stu-id="4ad1b-587">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="4ad1b-588">Para Microsoft HoloLens, establezca el **dispositivo de destino** en *hololens*.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-588">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="4ad1b-589">El **tipo de compilación** se establece en **D3D**</span><span class="sxs-lookup"><span data-stu-id="4ad1b-589">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="4ad1b-590">**SDK** está establecido en la **versión más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="4ad1b-590">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="4ad1b-591">La **versión de Visual Studio** está establecida en la **más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="4ad1b-591">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="4ad1b-592">**Compilar y ejecutar** está establecido en **equipo local**</span><span class="sxs-lookup"><span data-stu-id="4ad1b-592">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="4ad1b-593">Mientras tanto, merece la pena guardar la escena y agregarla a la compilación.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-593">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="4ad1b-594">Para ello, seleccione **Agregar escenas abiertas**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-594">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="4ad1b-595">Aparecerá una ventana de guardar.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-595">A save window will appear.</span></span>

            ![agregar escenas abiertas](images/AzureLabs-Lab8-83.png)

        2. <span data-ttu-id="4ad1b-597">Cree una nueva carpeta para este, y en cualquier momento, en el futuro, seleccione el botón **nueva carpeta** para crear una nueva carpeta, asígneleel nombre Scenes.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-597">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![nueva carpeta Scenes](images/AzureLabs-Lab8-84.png)

        3. <span data-ttu-id="4ad1b-599">Abra la carpeta Scenes recién creada y, a continuación, en el campo **nombre de archivo:** , escriba **NH\_Mr\_Scene**y, a continuación, presione **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-599">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_MR\_Scene**, then press **Save**.</span></span>

            ![nueva escena: NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  <span data-ttu-id="4ad1b-601">El resto de la configuración, en la **configuración de compilación**, debe dejarse como predeterminada por ahora.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-601">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="4ad1b-602">En la misma ventana, haga clic en el botón **configuración del reproductor** ; se abrirá el panel relacionado en el espacio donde se encuentra el **Inspector** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-602">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>    

    ![abrir configuración del reproductor](images/AzureLabs-Lab8-86.png)

7.  <span data-ttu-id="4ad1b-604">En este panel, deben comprobarse algunas opciones de configuración:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-604">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="4ad1b-605">En la pestaña **otros valores** :</span><span class="sxs-lookup"><span data-stu-id="4ad1b-605">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="4ad1b-606">La **versión de scripting en tiempo de ejecución** debe ser **Experimental** (.net 4,6 equivalente)</span><span class="sxs-lookup"><span data-stu-id="4ad1b-606">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>
        2.  <span data-ttu-id="4ad1b-607">El **back-end** de scripting debe ser ***.net***</span><span class="sxs-lookup"><span data-stu-id="4ad1b-607">**Scripting Backend** should be ***.NET***</span></span>
        3.  <span data-ttu-id="4ad1b-608">El **nivel de compatibilidad de API** debe ser **.net 4,6**</span><span class="sxs-lookup"><span data-stu-id="4ad1b-608">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![compatibilidad de API](images/AzureLabs-Lab8-87.png)

    2.  <span data-ttu-id="4ad1b-610">Más abajo en el panel, en la **configuración de XR** (se encuentra debajo de **configuración de publicación**), tick **Virtual Reality compatible**, asegúrese de que se ha agregado el **SDK de Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-610">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![actualizar la configuración de XR](images/AzureLabs-Lab8-88.png)        

    3.  <span data-ttu-id="4ad1b-612">En la pestaña **configuración de publicación** , en **capacidades**, tenga en cuentan lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-612">Within the **Publishing Settings** tab, under **Capabilities**, heck:</span></span>

        - <span data-ttu-id="4ad1b-613">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="4ad1b-613">**InternetClient**</span></span>           

            ![marcar el cliente de Internet](images/AzureLabs-Lab8-89.png)

8.  <span data-ttu-id="4ad1b-615">De nuevo en la **configuración de compilación**, los **proyectos de Unity C#**  ya no están atenuados: Marque la casilla situada junto a este.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-615">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="4ad1b-616">Una vez realizados estos cambios, cierre la ventana Configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-616">With these changes done, close the Build Settings window.</span></span>

10. <span data-ttu-id="4ad1b-617">Guarde la escena y el **archivo** > de proyecto**Guardar escena/archivo** > **Guardar proyecto**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-617">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="4ad1b-618">Si desea omitir el componente de *configuración de Unity* para este proyecto (aplicación de realidad mixta) y continuar directamente en el código, no dude en [Descargar este. unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), impórtelo en el proyecto como un [**paquete personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)y, después, continúe desde [ Capítulo 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-618">If you wish to skip the *Unity Set up* component for this project (mixed reality App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span></span> <span data-ttu-id="4ad1b-619">Todavía tendrá que agregar los componentes de script.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-619">You will still need to add the script components.</span></span>

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a><span data-ttu-id="4ad1b-620">Capítulo 13: importación de los archivos dll en el proyecto de Unity de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="4ad1b-620">Chapter 13 - Importing the DLLs in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="4ad1b-621">Usará Azure Storage para la biblioteca de Unity (que usa el SDK de .net para Azure).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-621">You will be using Azure Storage for Unity library (which uses the .Net SDK for Azure).</span></span> <span data-ttu-id="4ad1b-622">Siga este [vínculo sobre cómo usar Azure Storage con Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-622">Please follow this [link on how to use Azure Storage with Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>
<span data-ttu-id="4ad1b-623">Actualmente hay un problema conocido en Unity que requiere que los complementos se vuelvan a configurar después de la importación.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-623">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="4ad1b-624">Estos pasos (4-7 en esta sección) ya no serán necesarios una vez resuelto el error.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-624">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="4ad1b-625">Para importar el SDK en su propio proyecto, asegúrese de que ha descargado la versión más reciente de [. unitypackage Tools](https://aka.ms/azstorage-unitysdk).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-625">To import the SDK into your own project, make sure you have downloaded the latest [.unitypackage](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="4ad1b-626">A continuación, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-626">Then, do the following:</span></span>

1.  <span data-ttu-id="4ad1b-627">Agregue el. unitypackage Tools que descargó desde el anterior a Unity mediante la opción de menú de**paquete personalizado** de importación de **recursos** > del**paquete** > .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-627">Add the .unitypackage you downloaded from the above, to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

2.  <span data-ttu-id="4ad1b-628">En el cuadro **importar paquete Unity** que aparece, puede seleccionar todo en**almacenamiento**de **Complementos** > .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-628">In the **Import Unity Package** box that pops up, you can select everything under **Plugin** > **Storage**.</span></span>

    ![importar paquete](images/AzureLabs-Lab8-90.png)

3.  <span data-ttu-id="4ad1b-630">Haga clic en el botón **importar** para agregar los elementos al proyecto.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-630">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="4ad1b-631">Vaya a la carpeta **Storage** en **Complementos** en la vista proyecto y seleccione *solo*los siguientes complementos:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-631">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="4ad1b-632">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="4ad1b-632">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="4ad1b-633">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="4ad1b-633">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="4ad1b-634">Microsoft. WindowsAzure. Storage</span><span class="sxs-lookup"><span data-stu-id="4ad1b-634">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="4ad1b-635">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="4ad1b-635">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="4ad1b-636">System. espacial</span><span class="sxs-lookup"><span data-stu-id="4ad1b-636">System.Spatial</span></span>

    ![seleccionar complementos](images/AzureLabs-Lab8-91.png)

5.  <span data-ttu-id="4ad1b-638">Con *estos complementos específicos* seleccionados, **desactive** **cualquier plataforma** y **desactive** **WSAPlayer** y haga clic en **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-638">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![aplicar cambios de plataforma](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > <span data-ttu-id="4ad1b-640">Está marcando estos complementos concretos para usarlos solo en el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-640">You are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="4ad1b-641">Esto se debe a que hay diferentes versiones de los mismos complementos en la carpeta WSA que se usarán después de exportar el proyecto desde Unity.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-641">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="4ad1b-642">En la carpeta del complemento de **almacenamiento** , seleccione solo:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-642">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="4ad1b-643">Microsoft. Data. Services. Client</span><span class="sxs-lookup"><span data-stu-id="4ad1b-643">Microsoft.Data.Services.Client</span></span>

        ![seleccionar cliente de servicios de datos](images/AzureLabs-Lab8-93.png)

7.  <span data-ttu-id="4ad1b-645">Active la casilla **no procesar** en **configuración de plataforma** y haga clic en **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-645">Check the **Don't Process** box under **Platform Settings** and click **Apply**.</span></span>

    ![no procesar](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > <span data-ttu-id="4ad1b-647">Está marcando este complemento "no procesar" porque el parche de ensamblado de Unity tiene dificultades para procesar este complemento.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-647">You are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="4ad1b-648">El complemento seguirá funcionando aunque no se haya procesado.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-648">The plugin will still work even though it isn't processed.</span></span>

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="4ad1b-649">Capítulo 14: creación de la clase TableToScene en el proyecto de Unity de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="4ad1b-649">Chapter 14 - Creating the TableToScene class in the mixed reality Unity project</span></span>

<span data-ttu-id="4ad1b-650">La clase **TableToScene** es idéntica a la que se explica en el [capítulo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-650">The **TableToScene** class is identical to the one explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span> <span data-ttu-id="4ad1b-651">Cree la misma clase en el proyecto de Unity de realidad mixta siguiendo el mismo procedimiento descrito en el [capítulo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-651">Create the same class in the mixed reality Unity Project following the same procedure explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>

<span data-ttu-id="4ad1b-652">Una vez que haya completado este capítulo, los dos **proyectos de Unity** tendrán esta clase configurada en la cámara principal.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-652">Once you have completed this Chapter, both of your **Unity Projects** will have this class set up on the Main Camera.</span></span>

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="4ad1b-653">Capítulo 15: creación de la clase NotificationReceiver en el proyecto de Unity de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="4ad1b-653">Chapter 15 - Creating the NotificationReceiver class in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="4ad1b-654">El segundo script que debe crear es **NotificationReceiver**, que es responsable de:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-654">The second script you need to create is **NotificationReceiver**, which is responsible for:</span></span>

-   <span data-ttu-id="4ad1b-655">Registrando la aplicación con el centro de notificaciones en la inicialización.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-655">Registering the app with the Notification Hub at initialization.</span></span>
-   <span data-ttu-id="4ad1b-656">Escucha de notificaciones procedentes del centro de notificaciones.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-656">Listening to notifications coming from the Notification Hub.</span></span>
-   <span data-ttu-id="4ad1b-657">Deserializar los datos de objeto de las notificaciones recibidas.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-657">Deserializing the object data from received notifications.</span></span>
-   <span data-ttu-id="4ad1b-658">Mueva GameObjects en la escena, en función de los datos deserializados.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-658">Move the GameObjects in the scene, based on the deserialized data.</span></span>

<span data-ttu-id="4ad1b-659">Para crear el script **NotificationReceiver** :</span><span class="sxs-lookup"><span data-stu-id="4ad1b-659">To create the **NotificationReceiver** script:</span></span>

1.  <span data-ttu-id="4ad1b-660">Haga clic con el botón derecho en la carpeta scripts, haga clic en **crear**, **script de C\#** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-660">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="4ad1b-661">Asigne al script el nombre **NotificationReceiver**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-661">Name the script **NotificationReceiver**.</span></span>

    <span data-ttu-id="4ad1b-662">![crear un nuevo nombre](images/AzureLabs-Lab8-95.png)
    de script![de c# NotificationReceiver](images/AzureLabs-Lab8-96.png)</span><span class="sxs-lookup"><span data-stu-id="4ad1b-662">![create new c# script](images/AzureLabs-Lab8-95.png)
![name it NotificationReceiver](images/AzureLabs-Lab8-96.png)</span></span>

2.  <span data-ttu-id="4ad1b-663">Haga doble clic en el script para abrirlo.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-663">Double click on the script to open it.</span></span>

3.  <span data-ttu-id="4ad1b-664">Agregue los siguientes espacios de nombres:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-664">Add the following namespaces:</span></span>

    ```csharp
    //using Microsoft.WindowsAzure.Messaging;
    using Newtonsoft.Json;
    using System;
    using System.Collections;
    using UnityEngine;

    #if UNITY_WSA_10_0 && !UNITY_EDITOR
    using Windows.Networking.PushNotifications;
    #endif
    ```

4.  <span data-ttu-id="4ad1b-665">Inserte las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-665">Insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// allows this class to behave like a singleton
        /// </summary>
        public static NotificationReceiver instance;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        Vector3 newObjPosition;

        /// <summary>
        /// Value set by the notification, object name
        /// </summary>
        string gameObjectName;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        bool notifReceived;

        /// <summary>
        /// Insert here your Notification Hub Service name 
        /// </summary>
        private string hubName = " -- Insert the name of your service -- ";

        /// <summary>
        /// Insert here your Notification Hub Service "Listen endpoint"
        /// </summary>
        private string hubListenEndpoint = "-Insert your Notification Hub Service Listen endpoint-";
    ```

5.  <span data-ttu-id="4ad1b-666">Sustituya el valor de **hubName** por el nombre del servicio de centro de notificaciones y el valor de **hubListenEndpoint** por el valor de punto de conexión que se encuentra en la pestaña directivas de acceso, servicio Azure Notification Hub, en Azure portal (consulte la imagen siguiente).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-666">Substitute the **hubName** value with your Notification Hub Service name, and **hubListenEndpoint** value with the endpoint value found in the Access Policies tab, Azure Notification Hub Service, in the Azure Portal (see image below).</span></span>

    ![Insertar punto de conexión de directiva de Notification hubs](images/AzureLabs-Lab8-97.png)

6.  <span data-ttu-id="4ad1b-668">Ahora, agregue los métodos **Start ()** y Activate **()** para inicializar la clase.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-668">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Register the App at launch
            InitNotificationsAsync();

            // Begin listening for notifications
            StartCoroutine(WaitForNotification());
        }
    ```

7.  <span data-ttu-id="4ad1b-669">Agregue el método **WaitForNotification** para permitir que la aplicación reciba notificaciones de la biblioteca del centro de notificaciones sin entrar en conflicto con el subproceso principal:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-669">Add the **WaitForNotification** method to allow the app to receive notifications from the Notification Hub Library without clashing with the Main Thread:</span></span>

    ```csharp
        /// <summary>
        /// This notification listener is necessary to avoid clashes 
        /// between the notification hub and the main thread   
        /// </summary>
        private IEnumerator WaitForNotification()
        {
            while (true)
            {
                // Checks for notifications each second
                yield return new WaitForSeconds(1f);

                if (notifReceived)
                {
                    // If a notification is arrived, moved the appropriate object to the new position
                    GameObject.Find(gameObjectName).transform.position = newObjPosition;

                    // Reset the flag
                    notifReceived = false;
                }
            }
        }
    ```

8.  <span data-ttu-id="4ad1b-670">El método siguiente, **InitNotificationAsync ()** , registrará la aplicación con el servicio del centro de notificaciones en la inicialización.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-670">The following method, **InitNotificationAsync()**, will register the application with the notification Hub Service at initialization.</span></span> <span data-ttu-id="4ad1b-671">El código se marca como comentario, ya que Unity no podrá compilar el proyecto.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-671">The code is commented out as Unity will not be able to Build the project.</span></span> <span data-ttu-id="4ad1b-672">Se quitarán los comentarios al importar el paquete Nuget de mensajería de Azure en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-672">You will remove the comments when you import the Azure Messaging Nuget package in Visual Studio.</span></span>

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            // PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            // NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            // Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            // if (result.RegistrationId != null)
            // {
            //     Debug.Log($"Registration Successful: {result.RegistrationId}");
            //     channel.PushNotificationReceived += Channel_PushNotificationReceived;
            // }
        }
    ```

9.  <span data-ttu-id="4ad1b-673">El siguiente controlador, **Channel\_PushNotificationReceived ()** , se desencadenará cada vez que se reciba una notificación.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-673">The following handler, **Channel\_PushNotificationReceived()**, will be triggered every time a notification is received.</span></span> <span data-ttu-id="4ad1b-674">Deserializará la notificación, que será la entidad de la tabla de Azure que se ha movido a la aplicación de escritorio y, a continuación, moverá el GameObject correspondiente de la escena MR a la misma posición.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-674">It will deserialize the notification, which will be the Azure Table Entity that has been moved on the Desktop Application, and then move the corresponding GameObject in the MR scene to the same position.</span></span> 
    
    > [!IMPORTANT]
    > <span data-ttu-id="4ad1b-675">El código está comentado porque el código hace referencia a la biblioteca de mensajería de Azure, que agregará después de compilar el proyecto de Unity mediante el administrador de paquetes Nuget, dentro de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-675">The code is commented out because the code references the Azure Messaging library, which you will add after building the Unity project using the Nuget Package Manager, within Visual Studio.</span></span> <span data-ttu-id="4ad1b-676">Como tal, el proyecto de Unity no podrá compilar, a menos que esté comentado. Tenga en cuenta que, para compilar el proyecto y, a continuación, desea volver a Unity, deberá **cambiar el comentario** del código.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-676">As such, the Unity project will not be able to build, unless it is commented out. Be aware, that should you build your project, and then wish to return to Unity, you will need to **re-comment** that code.</span></span>

    ```csharp
        ///// <summary>
        ///// Handler called when a Push Notification is received
        ///// </summary>
        //private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)    
        //{
        //    Debug.Log("New Push Notification Received");
        //
        //    if (args.NotificationType == PushNotificationType.Raw)
        //    {
        //        //  Raw content of the Notification
        //        string jsonContent = args.RawNotification.Content;
        //
        //        // Deserialise the Raw content into an AzureTableEntity object
        //        AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);
        //
        //        // The name of the Game Object to be moved
        //        gameObjectName = ate.RowKey;          
        //
        //        // The position where the Game Object has to be moved
        //        newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);
        //
        //        // Flag thats a notification has been received
        //        notifReceived = true;
        //    }
        //}
    ```

10. <span data-ttu-id="4ad1b-677">Recuerde guardar los cambios antes de volver al editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-677">Remember to save your changes before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="4ad1b-678">En el panel **jerarquía** , haga clic en la **cámara principal** para que sus propiedades aparezcan en el **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-678">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="4ad1b-679">Con la carpeta scripts abierta, seleccione el script **NotificationReceiver** y arrástrelo a la **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-679">With the **Scripts** folder open, select the **NotificationReceiver** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="4ad1b-680">El resultado debe ser el siguiente:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-680">The result should be as below:</span></span>

    ![Arrastre el script del receptor de notificaciones a la cámara](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > <span data-ttu-id="4ad1b-682">Si va a desarrollar esto para Microsoft HoloLens, tendrá que actualizar el componente de *cámara* de la **cámara principal**para que:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-682">If you are developing this for the Microsoft HoloLens, you will need to update the **Main Camera**'s *Camera* component, so that:</span></span>
    > - <span data-ttu-id="4ad1b-683">Borrar marcas: Color sólido</span><span class="sxs-lookup"><span data-stu-id="4ad1b-683">Clear Flags: Solid Color</span></span>
    > - <span data-ttu-id="4ad1b-684">General Negro</span><span class="sxs-lookup"><span data-stu-id="4ad1b-684">Background: Black</span></span>

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a><span data-ttu-id="4ad1b-685">Capítulo 16: compilar el proyecto de realidad mixta en UWP</span><span class="sxs-lookup"><span data-stu-id="4ad1b-685">Chapter 16 - Build the Mixed Reality Project to UWP</span></span>

<span data-ttu-id="4ad1b-686">Este capítulo es idéntico al proceso de compilación del proyecto anterior.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-686">This Chapter is identical to build process for the previous project.</span></span> <span data-ttu-id="4ad1b-687">Ya se ha completado todo lo necesario para la sección Unity de este proyecto, por lo que es el momento de compilarla desde Unity.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-687">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="4ad1b-688">Vaya a **configuración de compilación** (**configuración de compilación** de **archivos** > ).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-688">Navigate to **Build Settings** ( **File** > **Build Settings** ).</span></span>

2.  <span data-ttu-id="4ad1b-689">En el menú **configuración de compilación** , asegúrese de que los proyectos de **Unity C#** \* se marcan (lo que le permitirá editar los scripts en este proyecto después de la compilación).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-689">From the **Build Settings** menu, ensure **Unity C# Projects**\* is ticked (which will allow you to edit the scripts in this project, after build).</span></span>

3.  <span data-ttu-id="4ad1b-690">Una vez hecho esto, hagaclic en compilar.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-690">After this is done, click **Build**.</span></span>

    ![compilar proyecto](images/AzureLabs-Lab8-99.png)

4.  <span data-ttu-id="4ad1b-692">Se abrirá una ventana del **Explorador de archivos** en la que se le solicitará una ubicación para compilar.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-692">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="4ad1b-693">Cree una nueva carpeta (haciendo clic en **nueva carpeta** en la esquina superior izquierda) y asígnele el nombrecompilaciones.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-693">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![crear carpeta de compilaciones](images/AzureLabs-Lab8-100.png)

    1.  <span data-ttu-id="4ad1b-695">Abra la nueva carpeta Compilaciones y cree otra carpeta (con la **nueva carpeta** una vez más) y asígnele el nombre **NH\_Mr\_** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-695">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_MR\_App**.</span></span>

        ![crear carpeta NH_MR_Apps](images/AzureLabs-Lab8-101.png)

    2.  <span data-ttu-id="4ad1b-697">Con la **aplicación\_NH\_Mr** seleccionada.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-697">With the **NH\_MR\_App** selected.</span></span> <span data-ttu-id="4ad1b-698">Haga clic en **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-698">click **Select Folder**.</span></span> <span data-ttu-id="4ad1b-699">El proyecto tardará un minuto o más en compilarse.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-699">The project will take a minute or so to build.</span></span>

5.  <span data-ttu-id="4ad1b-700">Después de la compilación, se abrirá una ventana del **Explorador de archivos** en la ubicación del nuevo proyecto.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-700">Following the build, a **File Explorer** window will open at the location of your new project.</span></span>



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a><span data-ttu-id="4ad1b-701">Capítulo 17: adición de paquetes NuGet a la solución UnityMRNotifHub</span><span class="sxs-lookup"><span data-stu-id="4ad1b-701">Chapter 17 - Add NuGet packages to the UnityMRNotifHub Solution</span></span>

> [!WARNING] 
> <span data-ttu-id="4ad1b-702">Recuerde que, una vez que agregue los siguientes paquetes NuGet (y quite los comentarios del código en el siguiente [capítulo](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)), el código, cuando se vuelve a abrir en el proyecto Unity, presentará errores.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-702">Please remember that, once you add the following NuGet Packages (and uncomment the code in the next [Chapter](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)), the Code, when reopened within the Unity Project, will present errors.</span></span> <span data-ttu-id="4ad1b-703">Si desea volver y seguir editando en el editor de Unity, necesitará comentar que errosome código y, a continuación, quitar el comentario de nuevo más tarde, una vez que vuelva a usar Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-703">If you wish to go back and continue editing in the Unity Editor, you will need comment that errosome code, and then uncomment again later, once you are back in Visual Studio.</span></span> 

<span data-ttu-id="4ad1b-704">Una vez completada la compilación de realidad mixta, navegue hasta el proyecto de realidad mixta, que creó, y haga doble clic en el archivo de solución (. sln) dentro de esa carpeta para abrir la solución con Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-704">Once the mixed reality build has been completed, navigate to the mixed reality project, which you built, and double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>
<span data-ttu-id="4ad1b-705">Ahora deberá agregar el paquete de NuGet **WindowsAzure. Messaging. Managed** . se trata de una biblioteca que se usa para recibir notificaciones del centro de notificaciones.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-705">You will now need to add the **WindowsAzure.Messaging.managed** NuGet package; this is a library that is used to receive Notifications from the Notification Hub.</span></span>

<span data-ttu-id="4ad1b-706">Para importar el paquete NuGet:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-706">To import the NuGet package:</span></span>

1.  <span data-ttu-id="4ad1b-707">En el **Explorador de soluciones**, haga clic con el botón derecho en la solución.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-707">In the **Solution Explorer**, right click on your Solution</span></span>

2.  <span data-ttu-id="4ad1b-708">Haga clic en **administrar paquetes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-708">Click on **Manage NuGet Packages**.</span></span>

    ![abrir el administrador de Nuget](images/AzureLabs-Lab8-102.png)

3.  <span data-ttu-id="4ad1b-710">Seleccione la pestaña ***examinar*** y busque **WindowsAzure. Messaging. Managed**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-710">Select the ***Browse*** tab and search for **WindowsAzure.Messaging.managed**.</span></span>

    ![buscar paquete de mensajería de Windows Azure](images/AzureLabs-Lab8-103.png)

4.  <span data-ttu-id="4ad1b-712">Seleccione el resultado (como se muestra a continuación) y, en la ventana de la derecha, active la casilla junto a **proyecto**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-712">Select the result (as shown below), and in the window to the right, select the checkbox next to **Project**.</span></span> <span data-ttu-id="4ad1b-713">Esto colocará un paso en la casilla junto a **proyecto**, junto con la casilla junto al proyecto **Assembly-CSharp** y **UnityMRNotifHub** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-713">This will place a tick in the checkbox next to **Project**, along with the checkbox next to the **Assembly-CSharp** and **UnityMRNotifHub** project.</span></span>

    ![marcar todos los proyectos](images/AzureLabs-Lab8-104.png)

5.  <span data-ttu-id="4ad1b-715">**Es posible que** la versión proporcionada inicialmente no sea compatible con este proyecto.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-715">The version initially provided **may not** be compatible with this project.</span></span> <span data-ttu-id="4ad1b-716">Por lo tanto, haga clic en el menú desplegable junto a **versión**y haga clic en **versión 0.1.7.9**y, a continuación, haga clic en **instalar**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-716">Therefore, click on the dropdown menu next to **Version**, and click **Version 0.1.7.9**, then click **Install**.</span></span>

6.  <span data-ttu-id="4ad1b-717">Ya ha terminado de instalar el paquete NuGet.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-717">You have now finished installing the NuGet package.</span></span> <span data-ttu-id="4ad1b-718">Busque el código comentado que escribió en la clase **NotificationReceiver** y quite los comentarios.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-718">Find the commented code you entered in the **NotificationReceiver** class and remove the comments..</span></span>



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a><span data-ttu-id="4ad1b-719">Capítulo 18: edición de la aplicación UnityMRNotifHub, clase NotificationReceiver</span><span class="sxs-lookup"><span data-stu-id="4ad1b-719">Chapter 18 - Edit UnityMRNotifHub application, NotificationReceiver class</span></span>

<span data-ttu-id="4ad1b-720">Después de haber agregado los **paquetes de NuGet**, deberá quitar la marca de *Comentario* de parte del código dentro de la clase **NotificationReceiver** .</span><span class="sxs-lookup"><span data-stu-id="4ad1b-720">Following having added the **NuGet Packages**, you will need to *uncomment* some of the code within the **NotificationReceiver** class.</span></span>

<span data-ttu-id="4ad1b-721">Esto incluye:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-721">This includes:</span></span>

1. <span data-ttu-id="4ad1b-722">Espacio de nombres en la parte superior:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-722">The namespace at the top:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. <span data-ttu-id="4ad1b-723">Todo el código dentro del método **InitNotificationsAsync ()** :</span><span class="sxs-lookup"><span data-stu-id="4ad1b-723">All the code within the **InitNotificationsAsync()** method:</span></span>

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            if (result.RegistrationId != null)
            {
                Debug.Log($"Registration Successful: {result.RegistrationId}");
                channel.PushNotificationReceived += Channel_PushNotificationReceived;
            }
        }
    ```

> [!WARNING]
> <span data-ttu-id="4ad1b-724">El código anterior tiene un Comentario en él: Asegúrese de que no ha eliminado accidentalmente *ese comentario* (ya que el código no se compilará si lo tiene!).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-724">The code above has a comment in it: ensure that you have not accidentally *uncommented* that comment (as the code will not compile if you have!).</span></span>

3. <span data-ttu-id="4ad1b-725">Y, por último, el evento **Channel_PushNotificationReceived** :</span><span class="sxs-lookup"><span data-stu-id="4ad1b-725">And, lastly, the **Channel_PushNotificationReceived** event:</span></span>

    ```csharp
        /// <summary>
        /// Handler called when a Push Notification is received
        /// </summary>
        private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)
        {
            Debug.Log("New Push Notification Received");

            if (args.NotificationType == PushNotificationType.Raw)
            {
                //  Raw content of the Notification
                string jsonContent = args.RawNotification.Content;

                // Deserialize the Raw content into an AzureTableEntity object
                AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);

                // The name of the Game Object to be moved
                gameObjectName = ate.RowKey;

                // The position where the Game Object has to be moved
                newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);

                // Flag thats a notification has been received
                notifReceived = true;
            }
        }
    ```

<span data-ttu-id="4ad1b-726">Con estos sin comentarios, asegúrese de guardar y, a continuación, continúe con el siguiente capítulo.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-726">With these uncommented, ensure that you save, and then proceed to the next Chapter.</span></span>

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a><span data-ttu-id="4ad1b-727">Capítulo 19: asociar el proyecto de realidad mixta a la aplicación de la tienda</span><span class="sxs-lookup"><span data-stu-id="4ad1b-727">Chapter 19 - Associate the mixed reality project to the Store app</span></span>

<span data-ttu-id="4ad1b-728">Ahora debe asociar el proyecto de **realidad mixta** a la aplicación de la tienda que creó en al principio del laboratorio.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-728">You now need to associate the **mixed reality** project to the Store App you created in at the start of the lab.</span></span>

1.  <span data-ttu-id="4ad1b-729">Abra la solución.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-729">Open the solution.</span></span>

2.  <span data-ttu-id="4ad1b-730">Haga clic con el botón derecho en el proyecto de aplicación de UWP en el panel de Explorador de soluciones, vaya a **tienda**y **asocie la aplicación con la tienda..** ..</span><span class="sxs-lookup"><span data-stu-id="4ad1b-730">Right click on the UWP app Project in the Solution Explorer panel, the go to **Store**, and **Associate App with the Store...**.</span></span>

    ![Asociación de la tienda abierta](images/AzureLabs-Lab8-105.png)

3.  <span data-ttu-id="4ad1b-732">Aparecerá una nueva ventana denominada **asociar la aplicación a la tienda Windows**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-732">A new window will appear called **Associate Your App with the Windows Store**.</span></span> <span data-ttu-id="4ad1b-733">Haga clic en **Next**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-733">Click **Next**.</span></span>

    ![ir a la pantalla siguiente](images/AzureLabs-Lab8-106.png)

4.  <span data-ttu-id="4ad1b-735">Se cargarán todas las aplicaciones asociadas a la cuenta con la que ha iniciado sesión.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-735">It will load up all the Applications associated with the Account which you have logged in.</span></span> <span data-ttu-id="4ad1b-736">Si no ha iniciado sesión en su cuenta, puede **iniciar sesión** en esta página.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-736">If you are not logged in to your account, you can **Log In** on this page.</span></span>

5.  <span data-ttu-id="4ad1b-737">Busque el **nombre** de la aplicación de la tienda que creó al principio de este tutorial y selecciónelo.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-737">Find the **Store App name** that you created at the start of this tutorial and select it.</span></span> <span data-ttu-id="4ad1b-738">Haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-738">Then click **Next**.</span></span>

    ![buscar y seleccionar el nombre del almacén](images/AzureLabs-Lab8-107.png)

6.  <span data-ttu-id="4ad1b-740">Hagaclic en asociar.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-740">Click **Associate**.</span></span>

    ![asociar la aplicación](images/AzureLabs-Lab8-108.png)

7.  <span data-ttu-id="4ad1b-742">La aplicación está ahora **asociada** a la aplicación de la tienda.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-742">Your App is now **Associated** with the Store App.</span></span> <span data-ttu-id="4ad1b-743">Esto es necesario para habilitar las notificaciones.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-743">This is necessary for enabling Notifications.</span></span>

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a><span data-ttu-id="4ad1b-744">Capítulo 20: implementación de aplicaciones UnityMRNotifHub y UnityDesktopNotifHub</span><span class="sxs-lookup"><span data-stu-id="4ad1b-744">Chapter 20 - Deploy UnityMRNotifHub and UnityDesktopNotifHub applications</span></span>

<span data-ttu-id="4ad1b-745">Este capítulo puede ser más fácil con dos personas, ya que el resultado incluirá las aplicaciones que se ejecutan, una que se ejecuta en el escritorio del equipo y la otra dentro de los auriculares que se incluyen.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-745">This Chapter may be easier with two people, as the result will include both apps running, one running on your computer Desktop, and the other within your immersive headset.</span></span>

<span data-ttu-id="4ad1b-746">La aplicación de casco envolvente está esperando recibir los cambios en la escena (los cambios de posición del GameObjects local) y la aplicación de escritorio realizará cambios en su escena local (cambios de posición), que se compartirán en la aplicación MR.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-746">The immersive headset app is waiting to receive changes to the scene (position changes of the local GameObjects), and the Desktop app will be making changes to their local scene (position changes), which will be shared to the MR app.</span></span> <span data-ttu-id="4ad1b-747">Tiene sentido implementar la aplicación MR primero, seguida de la aplicación de escritorio, de modo que el receptor pueda empezar a escuchar.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-747">It makes sense to deploy the MR app first, followed by the Desktop app, so that the receiver can begin listening.</span></span>

<span data-ttu-id="4ad1b-748">Para implementar la aplicación **UnityMRNotifHub** en el equipo local:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-748">To deploy the **UnityMRNotifHub** app on your Local Machine:</span></span>

1.  <span data-ttu-id="4ad1b-749">Abra el archivo de solución de la aplicación **UnityMRNotifHub** en **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-749">Open the solution file of your **UnityMRNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="4ad1b-750">En la **plataforma**de la solución, seleccione **x86, equipo local**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-750">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="4ad1b-751">En la **configuración de soluciones** , seleccione Depurar.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-751">In the **Solution Configuration** select **Debug**.</span></span>

    ![establecer la configuración del proyecto](images/AzureLabs-Lab8-109.png)

4.  <span data-ttu-id="4ad1b-753">Vaya al **menú** compilar y haga clic en **implementar solución** para transferir localmente la aplicación a la máquina.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-753">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="4ad1b-754">La aplicación debe aparecer ahora en la lista de aplicaciones instaladas, lista para iniciarse.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-754">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="4ad1b-755">Para implementar la aplicación **UnityDesktopNotifHub** en la máquina local:</span><span class="sxs-lookup"><span data-stu-id="4ad1b-755">To deploy the **UnityDesktopNotifHub** app on Local Machine:</span></span>

1.  <span data-ttu-id="4ad1b-756">Abra el archivo de solución de la aplicación **UnityDesktopNotifHub** en **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-756">Open the solution file of your **UnityDesktopNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="4ad1b-757">En la **plataforma**de la solución, seleccione **x86, equipo local**.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-757">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="4ad1b-758">En la **configuración de soluciones** , seleccione Depurar.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-758">In the **Solution Configuration** select **Debug**.</span></span>

    ![establecer la configuración del proyecto](images/AzureLabs-Lab8-110.png)

4.  <span data-ttu-id="4ad1b-760">Vaya al **menú** compilar y haga clic en **implementar solución** para transferir localmente la aplicación a la máquina.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-760">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="4ad1b-761">La aplicación debe aparecer ahora en la lista de aplicaciones instaladas, lista para iniciarse.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-761">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

6.  <span data-ttu-id="4ad1b-762">Inicie la aplicación de realidad mixta, seguida de la aplicación de escritorio.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-762">Launch the mixed reality application, followed by the Desktop application.</span></span>

<span data-ttu-id="4ad1b-763">Con ambas aplicaciones en ejecución, mueva un objeto en la escena del escritorio (con el botón primario del mouse).</span><span class="sxs-lookup"><span data-stu-id="4ad1b-763">With both applications running, move an object in the desktop scene (using the Left Mouse Button).</span></span> <span data-ttu-id="4ad1b-764">Estos cambios posicionales se realizarán de forma local, se serializarán y se enviarán al servicio Function App.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-764">These positional changes will be made locally, serialized, and sent to the Function App service.</span></span> <span data-ttu-id="4ad1b-765">El servicio de Function App actualizará la tabla junto con el centro de notificaciones.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-765">The Function App service will then update the Table along with the Notification Hub.</span></span> <span data-ttu-id="4ad1b-766">Tras recibir una actualización, el centro de notificaciones enviará los datos actualizados directamente a todas las aplicaciones registradas (en este caso, la aplicación de auriculares envolvente), que luego deserializará los datos entrantes y aplicará los nuevos datos posicionales a los objetos locales. moviéndolos en la escena.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-766">Having received an update, the Notification Hub will send the updated data directly to all the registered applications (in this case the immersive headset app), which will then deserialize the incoming data, and apply the new positional data to the local objects, moving them in scene.</span></span>


## <a name="your-finished-your-azure-notification-hubs-application"></a><span data-ttu-id="4ad1b-767">Su aplicación de Azure Notification Hubs finalizada</span><span class="sxs-lookup"><span data-stu-id="4ad1b-767">Your finished your Azure Notification Hubs application</span></span>
 
<span data-ttu-id="4ad1b-768">Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha el servicio Azure Notification Hubs y permite la comunicación entre las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="4ad1b-768">Congratulations, you built a mixed reality app that leverages the Azure Notification Hubs Service and allow communication between apps.</span></span>
 
![final del producto final](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a><span data-ttu-id="4ad1b-770">Ejercicios de bonus</span><span class="sxs-lookup"><span data-stu-id="4ad1b-770">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="4ad1b-771">Ejercicio 1</span><span class="sxs-lookup"><span data-stu-id="4ad1b-771">Exercise 1</span></span>

<span data-ttu-id="4ad1b-772">¿Puede averiguar cómo cambiar el color del GameObjects y enviar la notificación a otras aplicaciones que vean la escena?</span><span class="sxs-lookup"><span data-stu-id="4ad1b-772">Can you work out how to change the color of the GameObjects and send that notification to other apps viewing the scene?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="4ad1b-773">Ejercicio 2</span><span class="sxs-lookup"><span data-stu-id="4ad1b-773">Exercise 2</span></span>

<span data-ttu-id="4ad1b-774">¿Puede Agregar movimiento de GameObjects a la aplicación MR y ver la escena actualizada en la aplicación de escritorio?</span><span class="sxs-lookup"><span data-stu-id="4ad1b-774">Can you add movement of the GameObjects to your MR app and see the updated scene in your desktop app?</span></span>
