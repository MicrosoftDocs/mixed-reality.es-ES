---
title: El Sr. y Azure 308 - notificaciones entre dispositivos
description: Realice este curso para obtener información sobre cómo implementar Azure Notification Hubs, Azure Functions y el almacenamiento de Azure y las tablas dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidad mixta, Azure, academy, unity, tutorial, api, notificaciones, funciones, tablas, centros de notificaciones, vr envolventes, hololens,
ms.openlocfilehash: 3b6e930acd81c7d6e3addc107ec0da605d38cad1
ms.sourcegitcommit: 06ac2200d10b50fb5bcc413ce2a839e0ab6d6ed1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2019
ms.locfileid: "67694601"
---
>[!NOTE]
><span data-ttu-id="1a9eb-104">Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="1a9eb-105">Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="1a9eb-106">Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="1a9eb-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="1a9eb-108">Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="1a9eb-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-308-cross-device-notifications"></a><span data-ttu-id="1a9eb-110">El Sr. y Azure 308: Notificaciones entre dispositivos</span><span class="sxs-lookup"><span data-stu-id="1a9eb-110">MR and Azure 308: Cross-device notifications</span></span>

![final producto-inicio](images/AzureLabs-Lab8-00.png)

<span data-ttu-id="1a9eb-112">En este curso, obtendrá información sobre cómo agregar funcionalidades de Notification Hubs a una aplicación de realidad mixta mediante Azure Notification Hubs, las tablas de Azure y Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-112">In this course, you will learn how to add Notification Hubs capabilities to a mixed reality application using Azure Notification Hubs, Azure Tables, and Azure Functions.</span></span>

<span data-ttu-id="1a9eb-113">**Azure Notification Hubs** es un servicio de Microsoft, que permite a los desarrolladores enviar notificaciones push personalizadas y dirigidas a cualquier plataforma, todo ello gracias dentro de la nube.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-113">**Azure Notification Hubs** is a Microsoft service, which allows developers to send targeted and personalized push notifications to any platform, all powered within the cloud.</span></span> <span data-ttu-id="1a9eb-114">Esto puede eficazmente permiten a los desarrolladores para comunicarse con los usuarios finales, o incluso comunicarse entre varias aplicaciones, según el escenario.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-114">This can effectively allow developers to communicate with end users, or even communicate between various applications, depending on the scenario.</span></span> <span data-ttu-id="1a9eb-115">Para obtener más información, visite la **Azure Notification Hubs** [página](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-115">For more information, visit the **Azure Notification Hubs** [page](https://docs.microsoft.com/azure/notification-hubs/notification-hubs-push-notification-overview).</span></span>

<span data-ttu-id="1a9eb-116">**Las funciones de Azure** es un servicio de Microsoft, que permite a los desarrolladores ejecutar pequeños fragmentos de código, "funciones", en Azure.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-116">**Azure Functions** is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="1a9eb-117">Esto proporciona una manera para delegar el trabajo a la nube, en lugar de la aplicación local, lo que puede tener muchas ventajas.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-117">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="1a9eb-118">**Las funciones de Azure** admite varios lenguajes de desarrollo, incluidos C\#, F\#, Node.js, Java y PHP.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-118">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="1a9eb-119">Para obtener más información, visite la **Azure Functions** [página](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-119">For more information, visit the **Azure Functions** [page](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="1a9eb-120">**Las tablas de Azure** es un servicio de nube de Microsoft, que permite a los desarrolladores almacenar datos estructurados que no sean de SQL en la nube, lo que sea fácilmente accesible en cualquier lugar.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-120">**Azure Tables** is a Microsoft cloud service, which allows developers to store structured non-SQL data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="1a9eb-121">El servicio cuenta con un diseño sin esquema, lo que permite la evolución de las tablas según sea necesario y, por tanto, es muy flexible.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-121">The service boasts a schemaless design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="1a9eb-122">Para obtener más información, visite la **Azure Tables** [página](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="1a9eb-122">For more information, visit the **Azure Tables** [page](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="1a9eb-123">Una vez completado este curso, tendrá una aplicación envolventes auriculares de realidad mixta y una aplicación de PC de escritorio, que podrá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-123">Having completed this course, you will have a mixed reality immersive headset application, and a Desktop PC application, which will be able to do the following:</span></span>

1. <span data-ttu-id="1a9eb-124">La aplicación de PC de escritorio permite al usuario mover un objeto en el espacio 2D (X y), con el mouse.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-124">The Desktop PC app will allow the user to move an object in 2D space (X and Y), using the mouse.</span></span>

2. <span data-ttu-id="1a9eb-125">El movimiento de objetos dentro de la aplicación de PC se enviarán a la nube mediante JSON, que estará en la forma de cadena, que contiene un identificador de objeto, tipo y transformar la información (coordenadas X e Y).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-125">The movement of objects within the PC app will be sent to the cloud using JSON, which will be in the form of a string, containing an object ID, type, and transform information (X and Y coordinates).</span></span> 

3. <span data-ttu-id="1a9eb-126">La aplicación de realidad mixta, que tiene una escena idéntica a la aplicación de escritorio, recibirá notificaciones sobre el movimiento de objetos desde el servicio Notification Hubs (que simplemente se ha actualizado la aplicación de PC de escritorio).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-126">The mixed reality app, which has an identical scene to the desktop app, will receive notifications regarding object movement, from the Notification Hubs service (which has just been updated by the Desktop PC app).</span></span> 

4. <span data-ttu-id="1a9eb-127">Al recibir una notificación, que contiene el Id. de objeto, el tipo y la información de transformación, la aplicación de realidad mixta aplicará la información recibida a su escena.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-127">Upon receiving a notification, which will contain the object ID, type, and transform information, the mixed reality app will apply the received information to its own scene.</span></span>

<span data-ttu-id="1a9eb-128">En la aplicación, es depende de usted sobre cómo se integrará los resultados con el diseño.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-128">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="1a9eb-129">Este curso está diseñado para mostrarle cómo integrar un servicio de Azure con el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-129">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="1a9eb-130">Es su trabajo consiste en usar los conocimientos que obtendrá de este curso para mejorar las aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-130">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span> <span data-ttu-id="1a9eb-131">Este curso es un tutorial independiente, que no implican directamente otros laboratorios realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-131">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="1a9eb-132">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="1a9eb-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="1a9eb-133">Curso</span><span class="sxs-lookup"><span data-stu-id="1a9eb-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="1a9eb-134"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1a9eb-134"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1a9eb-135"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="1a9eb-135"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="1a9eb-136">El Sr. y Azure 308: Notificaciones entre dispositivos</span><span class="sxs-lookup"><span data-stu-id="1a9eb-136">MR and Azure 308: Cross-device notifications</span></span></td><td style="text-align: center;"> <span data-ttu-id="1a9eb-137">✔️</span><span class="sxs-lookup"><span data-stu-id="1a9eb-137">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="1a9eb-138">✔️</span><span class="sxs-lookup"><span data-stu-id="1a9eb-138">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="1a9eb-139">Aunque este curso se centra principalmente en inmersivos (VR) Windows Mixed Reality, también puede aplicar lo aprendido en este curso de Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-139">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="1a9eb-140">Como seguir el curso, verá notas en cualquier cambio que deberá emplear para admitir HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-140">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="1a9eb-141">Al usar HoloLens, es posible que observe algunos eco durante la captura de voz.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-141">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1a9eb-142">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="1a9eb-142">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="1a9eb-143">Este tutorial está diseñado para los desarrolladores con experiencia básica con Unity y C#.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-143">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="1a9eb-144">También Ten en cuenta que los requisitos previos y las instrucciones escritas en este documento representan lo que se ha probado y comprobado en el momento de redactar (mayo de 2018).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-144">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="1a9eb-145">Es libre de usar el software más reciente, como se muestra en el [instalar las herramientas de](install-the-tools.md) artículo, aunque no se debe suponer que la información de este curso perfectamente coincida con lo que encontrará en el software más reciente que se indica a continuación .</span><span class="sxs-lookup"><span data-stu-id="1a9eb-145">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="1a9eb-146">Se recomiendan el siguiente hardware y software para este curso:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-146">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="1a9eb-147">Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desarrollo de auriculares envolvente (VR)</span><span class="sxs-lookup"><span data-stu-id="1a9eb-147">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="1a9eb-148">Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="1a9eb-148">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1a9eb-149">El SDK más reciente de Windows 10</span><span class="sxs-lookup"><span data-stu-id="1a9eb-149">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1a9eb-150">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="1a9eb-150">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1a9eb-151">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="1a9eb-151">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="1a9eb-152">Un [auriculares de Windows Mixed Reality envolventes (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="1a9eb-152">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="1a9eb-153">Acceso a Internet para la instalación de Azure y tener acceso a Notification Hubs</span><span class="sxs-lookup"><span data-stu-id="1a9eb-153">Internet access for Azure setup and to access Notification Hubs</span></span>

## <a name="before-you-start"></a><span data-ttu-id="1a9eb-154">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="1a9eb-154">Before you start</span></span>

- <span data-ttu-id="1a9eb-155">Para evitar problemas de creación de este proyecto, se recomienda encarecidamente que cree el proyecto se ha mencionado en este tutorial en una carpeta raíz o cerca de la raíz (rutas de acceso de carpeta largo pueden causar problemas en tiempo de compilación).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-155">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="1a9eb-156">Debe ser el propietario de su Portal para desarrolladores de Microsoft y el Portal de registro de aplicación, en caso contrario, no tendrá permiso para tener acceso a la aplicación en [capítulo 2](#chapter-2---retrieve-your-new-apps-credentials).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-156">You must be the owner of your Microsoft Developer Portal and your Application Registration Portal, otherwise you will not have permission to access the app in [Chapter 2](#chapter-2---retrieve-your-new-apps-credentials).</span></span>

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a><span data-ttu-id="1a9eb-157">Capítulo 1: crear una aplicación en el Portal para desarrolladores de Microsoft</span><span class="sxs-lookup"><span data-stu-id="1a9eb-157">Chapter 1 - Create an application on the Microsoft Developer Portal</span></span>

<span data-ttu-id="1a9eb-158">Para usar el **Azure Notification Hubs** servicio, deberá crear una aplicación en el Portal para desarrolladores de Microsoft, como la aplicación deberá registrarse, para que pueda enviar y recibir notificaciones.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-158">To use the **Azure Notification Hubs** Service, you will need to create an Application on the Microsoft Developer Portal, as your application will need to be registered, so that it can send and receive notifications.</span></span>

1.  <span data-ttu-id="1a9eb-159">Inicie sesión en el [Portal para desarrolladores de Microsoft](https://developer.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-159">Log in to the [Microsoft Developer Portal](https://developer.microsoft.com/dashboard).</span></span>

    > <span data-ttu-id="1a9eb-160">Deberá iniciar sesión en su Account de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-160">You will need to log in to your Microsoft Account.</span></span>

2.  <span data-ttu-id="1a9eb-161">En el panel, haga clic en **crear una nueva aplicación**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-161">From the Dashboard, click **Create a new app**.</span></span>

    ![Creación de una aplicación](images/AzureLabs-Lab8-01.png)

3.  <span data-ttu-id="1a9eb-163">Aparecerá un menú emergente en la que necesita reservar un nombre para la nueva aplicación.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-163">A popup will appear, wherein you need to reserve a name for your new app.</span></span> <span data-ttu-id="1a9eb-164">En el cuadro de texto, inserte un nombre adecuado; Si el nombre elegido está disponible, aparecerá una marca de verificación a la derecha del cuadro de texto.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-164">In the textbox, insert an appropriate name; if the chosen name is available, a tick will appear to the right of the textbox.</span></span> <span data-ttu-id="1a9eb-165">Una vez que tenga un nombre disponible insertado, haga clic en el **reservar nombre de producto** botón a la parte inferior izquierda de la ventana emergente.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-165">Once you have an available name inserted, click the **Reserve product name** button to the bottom left of the popup.</span></span>

    ![un nombre inverso](images/AzureLabs-Lab8-02.png)

4.  <span data-ttu-id="1a9eb-167">Con la aplicación creada ahora, está listo para pasar al siguiente capítulo.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-167">With the app now created, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a><span data-ttu-id="1a9eb-168">Capítulo 2: recuperar las credenciales de las aplicaciones nuevas</span><span class="sxs-lookup"><span data-stu-id="1a9eb-168">Chapter 2 - Retrieve your new apps credentials</span></span>

<span data-ttu-id="1a9eb-169">Inicie sesión en el Portal de registro de aplicación, donde se mostrará la nueva aplicación y recuperar las credenciales que se usará para el programa de instalación la **Notification Hubs Service** dentro de la **Portal de Azure**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-169">Log into the Application Registration Portal, where your new app will be listed, and retrieve the credentials which will be used to setup the **Notification Hubs Service** within the **Azure Portal**.</span></span>

1.  <span data-ttu-id="1a9eb-170">Navegue hasta la [Portal de registro de aplicación](http://apps.dev.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-170">Navigate to the [Application Registration Portal](http://apps.dev.microsoft.com).</span></span>

    ![portal de registro de aplicación](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > <span data-ttu-id="1a9eb-172">Deberá usar su Account de Microsoft para inicio de sesión.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-172">You will need to use your Microsoft Account to Login.</span></span>  
    > <span data-ttu-id="1a9eb-173">Esto **debe** ser la Account de Microsoft que ha usado en el anterior [capítulo](#chapter-1---create-an-application-on-the-microsoft-developer-portal), con el portal para desarrolladores de Windows Store.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-173">This **must** be the Microsoft Account which you used in the previous [Chapter](#chapter-1---create-an-application-on-the-microsoft-developer-portal), with the Windows Store Developer portal.</span></span>

2.  <span data-ttu-id="1a9eb-174">Encontrará la aplicación en el **mis aplicaciones** sección.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-174">You will find your app under the **My applications** section.</span></span> <span data-ttu-id="1a9eb-175">Una vez encontrado, haga clic en él y se le llevará a una página nueva que tenga la aplicación más nombre **registro**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-175">Once you have found it, click on it and you will be taken to a new page which has the app name plus **Registration**.</span></span>

    ![la aplicación recién registrada](images/AzureLabs-Lab8-04.png)

3.  <span data-ttu-id="1a9eb-177">Desplácese hacia abajo en la página de registro para encontrar su **secretos de aplicación** sección y la **SID del paquete** para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-177">Scroll down the registration page to find your **Application Secrets** section and the **Package SID** for your app.</span></span> <span data-ttu-id="1a9eb-178">Copie las dos para su uso con la configuración de la **servicio de Azure Notification Hubs** en el capítulo siguiente.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-178">Copy both for use with setting up the **Azure Notification Hubs Service** in the next Chapter.</span></span>

    ![Secretos de aplicación](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a><span data-ttu-id="1a9eb-180">Capítulo 3: configurar el Portal de Azure: creación de servicio de Notification Hubs</span><span class="sxs-lookup"><span data-stu-id="1a9eb-180">Chapter 3 - Setup Azure Portal: create Notification Hubs Service</span></span>

<span data-ttu-id="1a9eb-181">Con las credenciales de las aplicaciones recuperar, se tendrán que ir al Portal de Azure, donde creará un servicio de Azure Notification Hubs.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-181">With your apps credentials retrieved, you will need to go to the Azure Portal, where you will create an Azure Notification Hubs Service.</span></span>

1.  <span data-ttu-id="1a9eb-182">Inicie sesión en el [Portal Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-182">Log into the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="1a9eb-183">Si no dispone de una cuenta de Azure, deberá crear uno.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-183">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="1a9eb-184">Si está siguiendo este tutorial en una situación de aula o laboratorio, pida el instructor o uno de los a los supervisores de ayuda para instalar la nueva cuenta.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-184">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="1a9eb-185">Una vez que haya iniciado sesión, haga clic en **New** en la esquina superior izquierda esquina y busque **centro de notificaciones**y haga clic en ***ENTRAR***.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-185">Once you are logged in, click on **New** in the top left corner, and search for **Notification Hub**, and click ***Enter***.</span></span>

    ![Buscar centro de notificaciones](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > <span data-ttu-id="1a9eb-187">La palabra ***New*** se han reemplazado con **crear un recurso**, en los portales más reciente.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-187">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="1a9eb-188">La nueva página proporcionará una descripción de la *Notification Hubs* service.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-188">The new page will provide a description of the *Notification Hubs* service.</span></span> <span data-ttu-id="1a9eb-189">En la parte inferior izquierda de este símbolo del sistema, seleccione el **crear** botón para crear una asociación con este servicio.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-189">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![Crear instancia de notification hubs](images/AzureLabs-Lab8-07.png)

4.  <span data-ttu-id="1a9eb-191">Una vez que ha hecho clic ***crear***:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-191">Once you have clicked on ***Create***:</span></span>

    1.  <span data-ttu-id="1a9eb-192">Inserte el nombre deseado para esta instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-192">Insert your desired name for this service instance.</span></span>

    2.  <span data-ttu-id="1a9eb-193">Proporcione un **espacio de nombres** que podrá asociar a esta aplicación.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-193">Provide a **namespace** which you will be able to associate with this app.</span></span>

    3.  <span data-ttu-id="1a9eb-194">Seleccione un **ubicación.**</span><span class="sxs-lookup"><span data-stu-id="1a9eb-194">Select a **Location.**</span></span>

    4.  <span data-ttu-id="1a9eb-195">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-195">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="1a9eb-196">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-196">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="1a9eb-197">Se recomienda mantener todos los servicios de Azure asociados a un proyecto único (por ejemplo, por ejemplo, estos laboratorios) en un grupo de recursos comunes).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-197">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="1a9eb-198">Si desea leer más acerca de los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-198">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span> 

    5.  <span data-ttu-id="1a9eb-199">Seleccione un **suscripción**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-199">Select an appropriate **Subscription**.</span></span>

    6.  <span data-ttu-id="1a9eb-200">También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-200">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="1a9eb-201">Selecciona **Crear**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-201">Select **Create**.</span></span>

        ![Rellene los detalles del servicio](images/AzureLabs-Lab8-08.png)

5.  <span data-ttu-id="1a9eb-203">Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-203">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="1a9eb-204">Una vez creada la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-204">A notification will appear in the portal once the Service instance is created.</span></span>

    ![notificación](images/AzureLabs-Lab8-09.png)

7.  <span data-ttu-id="1a9eb-206">Haga clic en el **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-206">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="1a9eb-207">Se le dirigirá a la nueva **centro de notificaciones** instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-207">You will be taken to your new **Notification Hub** service instance.</span></span>

    ![Ir al recurso](images/AzureLabs-Lab8-10.png)
    
8.  <span data-ttu-id="1a9eb-209">En la página de introducción a medio camino hacia abajo en la página, haga clic en **Windows (WNS).**</span><span class="sxs-lookup"><span data-stu-id="1a9eb-209">From the overview page, halfway down the page, click **Windows (WNS).**</span></span> <span data-ttu-id="1a9eb-210">El panel de la derecha cambiará a mostrar dos campos de texto que requieren su **SID del paquete** y **clave de seguridad**, desde la aplicación configurada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-210">The panel on the right will change to show two text fields, which require your **Package SID** and **Security Key**, from the app you set up previously.</span></span>

    ![recién creado el servicio de concentradores](images/AzureLabs-Lab8-11.png)

9. <span data-ttu-id="1a9eb-212">Una vez que haya copiado los detalles en los campos correctos, haga clic en **guardar**, y recibirá una notificación cuando se ha actualizado correctamente el centro de notificaciones.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-212">Once you have copied the details into the correct fields, click **Save**, and you will receive a notification when the Notification Hub has been successfully updated.</span></span>

    ![Copiar detalles de seguridad](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a><span data-ttu-id="1a9eb-214">Capítulo 4: configurar el Portal de Azure: creación de Table Service</span><span class="sxs-lookup"><span data-stu-id="1a9eb-214">Chapter 4 - Setup Azure Portal: create Table Service</span></span>

<span data-ttu-id="1a9eb-215">Después de crear la instancia del servicio de Notification Hubs, navegar hasta el Portal de Azure, donde creará un servicio de tablas de Azure mediante la creación de un recurso de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-215">After creating your Notification Hubs Service instance, navigate back to your Azure Portal, where you will create an Azure Tables Service by creating a Storage Resource.</span></span>

1.  <span data-ttu-id="1a9eb-216">Si no ha iniciado sesión, inicie sesión en el [Portal de Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-216">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="1a9eb-217">Una vez iniciada la sesión, haga clic en **New** en la esquina superior izquierda esquina y busque **cuenta de almacenamiento**y haga clic en **ENTRAR**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-217">Once logged in, click on **New** in the top left corner, and search for **Storage account**, and click **Enter**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="1a9eb-218">La palabra ***New*** se han reemplazado con **crear un recurso**, en los portales más reciente.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-218">The word ***New*** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="1a9eb-219">Seleccione **cuenta de almacenamiento: blob, archivo, tabla, cola** en la lista.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-219">Select **Storage account - blob, file, table, queue** from the list.</span></span>

    ![Busque la cuenta de almacenamiento](images/AzureLabs-Lab8-13.png)

4.  <span data-ttu-id="1a9eb-221">La nueva página proporcionará una descripción de la **cuenta de almacenamiento** service.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-221">The new page will provide a description of the **Storage account** service.</span></span> <span data-ttu-id="1a9eb-222">En la parte inferior izquierda de este símbolo del sistema, seleccione el **crear** botón para crear una instancia de este servicio.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-222">At the bottom left of this prompt, select the **Create** button, to create an instance of this service.</span></span>

    ![Crear instancia de almacenamiento](images/AzureLabs-Lab8-14.png)

5.  <span data-ttu-id="1a9eb-224">Una vez que ha hecho clic **crear**, aparecerá un panel:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-224">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="1a9eb-225">Insertar el elemento **nombre** para esta instancia de servicio (debe estar en minúsculas).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-225">Insert your desired **Name** for this service instance (must be all lowercase).</span></span>

    2. <span data-ttu-id="1a9eb-226">Para **modelo de implementación**, haga clic en **Administrador de recursos**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-226">For **Deployment model**, click **Resource manager**.</span></span>

    3.  <span data-ttu-id="1a9eb-227">Para **tipo de cuenta**, mediante el menú desplegable, seleccione **almacenamiento (uso general v1)** .</span><span class="sxs-lookup"><span data-stu-id="1a9eb-227">For **Account kind**, using the dropdown menu, select **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="1a9eb-228">Seleccione un **ubicación**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-228">Select an appropriate **Location**.</span></span>
    
    5.  <span data-ttu-id="1a9eb-229">Para el **replicación** menú desplegable, seleccione **lectura-access--almacenamiento con redundancia geográfica (RA-GRS)** .</span><span class="sxs-lookup"><span data-stu-id="1a9eb-229">For the **Replication** dropdown menu, select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="1a9eb-230">Para **rendimiento**, haga clic en **estándar**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-230">For **Performance**, click **Standard**.</span></span>

    7.  <span data-ttu-id="1a9eb-231">Dentro de la **se requiere transferencia segura** sección, seleccione **deshabilitado**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-231">Within the **Secure transfer required** section, select **Disabled**.</span></span>

    8.  <span data-ttu-id="1a9eb-232">Desde el **suscripción** menú desplegable, seleccione una suscripción adecuada.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-232">From the **Subscription** dropdown menu, select an appropriate subscription.</span></span>

    9.  <span data-ttu-id="1a9eb-233">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-233">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="1a9eb-234">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-234">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="1a9eb-235">Se recomienda mantener todos los servicios de Azure asociados a un proyecto único (por ejemplo, por ejemplo, estos laboratorios) en un grupo de recursos comunes).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-235">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="1a9eb-236">Si desea leer más acerca de los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-236">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="1a9eb-237">Deje **redes virtuales** como **deshabilitado** si se trata de una opción para usted.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-237">Leave **Virtual networks** as **Disabled** if this is an option for you.</span></span>

    11. <span data-ttu-id="1a9eb-238">Haga clic en **Crear**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-238">Click **Create**.</span></span>

        ![Rellene los detalles de almacenamiento](images/AzureLabs-Lab8-15.png)

6.  <span data-ttu-id="1a9eb-240">Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-240">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="1a9eb-241">Una vez creada la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-241">A notification will appear in the portal once the Service instance is created.</span></span> <span data-ttu-id="1a9eb-242">Haga clic en las notificaciones para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-242">Click on the notifications to explore your new Service instance.</span></span>

    ![nueva notificación de almacenamiento](images/AzureLabs-Lab8-16.png)

8.  <span data-ttu-id="1a9eb-244">Haga clic en el **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-244">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="1a9eb-245">Se le llevará a la nueva página de información general de instancia de servicio de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-245">You will be taken to your new Storage Service instance overview page.</span></span>

    ![Ir al recurso](images/AzureLabs-Lab8-17.PNG)

9. <span data-ttu-id="1a9eb-247">En la página de información general, en el lado derecho, haga clic en **tablas**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-247">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. <span data-ttu-id="1a9eb-248">El panel de la derecha cambiará para mostrar el **de Table service** información, en la que deberá agregar una nueva tabla.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-248">The panel on the right will change to show the **Table service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="1a9eb-249">Haga clic en el **+** **tabla** botón a la esquina superior izquierda.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-249">Do this by clicking the **+** **Table** button to the top-left corner.</span></span>

    ![abrir tablas](images/AzureLabs-Lab8-19.png)

11. <span data-ttu-id="1a9eb-251">Se mostrará una página nueva, en la que tiene que introducir un **nombre de la tabla**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-251">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="1a9eb-252">Este es el nombre que usará para hacer referencia a los datos en la aplicación en los capítulos posteriores.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-252">This is the name you will use to refer to the data in your application in later Chapters.</span></span> <span data-ttu-id="1a9eb-253">Inserte un nombre adecuado y haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-253">Insert an appropriate name and click **OK**.</span></span>

    ![Crear nueva tabla](images/AzureLabs-Lab8-20.png)    

12. <span data-ttu-id="1a9eb-255">Una vez creada la nueva tabla, podrá verlo en el **de Table service** página (en la parte inferior).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-255">Once the new table has been created, you will be able to see it within the **Table service** page (at the bottom).</span></span>

    ![nueva tabla creada](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a><span data-ttu-id="1a9eb-257">Capítulo 5: completar la tabla de Azure en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1a9eb-257">Chapter 5 - Completing the Azure Table in Visual Studio</span></span>

<span data-ttu-id="1a9eb-258">Ahora que su **de Table service** cuenta de almacenamiento ha sido el programa de instalación, es momento de agregar datos a él, que se usará para almacenar y recuperar información.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-258">Now that your **Table service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="1a9eb-259">La edición de las tablas puede realizarse a través de **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-259">The editing of your Tables can be done through **Visual Studio**.</span></span>

1.  <span data-ttu-id="1a9eb-260">Abra **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-260">Open **Visual Studio**.</span></span>

2.  <span data-ttu-id="1a9eb-261">En el menú, haga clic en **vista** > **Cloud Explorer**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-261">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![Abra cloud explorer](images/AzureLabs-Lab8-22.png)

3.  <span data-ttu-id="1a9eb-263">El **Cloud Explorer** se abrirá como un elemento acoplado (tenga paciencia, como la carga puede tardar tiempo).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-263">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="1a9eb-264">Si la suscripción que usó para crear su *cuentas de almacenamiento* no está visible, asegúrese de que tiene:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-264">If the Subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="1a9eb-265">Iniciar sesión en la misma cuenta que usan para el Portal de Azure.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-265">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="1a9eb-266">Selecciona la suscripción desde la página de administración de cuenta (es posible que deba aplicar un filtro de la configuración de su cuenta):</span><span class="sxs-lookup"><span data-stu-id="1a9eb-266">Selected your Subscription from the Account Management Page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![encuentra la suscripción](images/AzureLabs-Lab8-22-5.png)

4.  <span data-ttu-id="1a9eb-268">Se mostrarán los servicios de nube de Azure.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-268">Your Azure cloud services will be shown.</span></span> <span data-ttu-id="1a9eb-269">Buscar **cuentas de almacenamiento** y haga clic en la flecha situada a la izquierda de la que se va a expandir sus cuentas.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-269">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![Abra cuentas de almacenamiento](images/AzureLabs-Lab8-23.png)

5.  <span data-ttu-id="1a9eb-271">Una vez que se expande el recién creado **cuenta de almacenamiento** debe estar disponible.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-271">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="1a9eb-272">Haga clic en la flecha situada a la izquierda de su almacenamiento y, a continuación, una vez que se expande, encontrar **tablas** y haga clic en la flecha situada junto a la que, para que se muestre el **tabla** que creó en el último capítulo.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-272">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="1a9eb-273">Haga doble clic en su **tabla**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-273">Double click your **Table**.</span></span>

    ![Abra la tabla de objetos de la escena](images/AzureLabs-Lab8-24.png)

6.  <span data-ttu-id="1a9eb-275">La tabla se abrirá en el centro de la ventana de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-275">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="1a9eb-276">Haga clic en el icono de tabla con el **+** (más) en él.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-276">Click the table icon with the **+** (plus) on it.</span></span>

    ![Agregar nueva tabla](images/AzureLabs-Lab8-25.png)

7.  <span data-ttu-id="1a9eb-278">Se mostrará una ventana, se le pide para permitirle *Agregar entidad*.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-278">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="1a9eb-279">Creará tres entidades en total, cada una con varias propiedades.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-279">You will create three entities in total, each with several properties.</span></span> <span data-ttu-id="1a9eb-280">Observará que *PartitionKey* y *RowKey* ya se proporcionan, ya que se usan para buscar los datos en la tabla.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-280">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![clave de partición y fila](images/AzureLabs-Lab8-26.png)

8. <span data-ttu-id="1a9eb-282">Actualización el *valor* de la **PartitionKey** y **RowKey** como sigue (no olvide hacer esto para cada propiedad de la fila agregar, aunque incremente la clave de fila cada vez):</span><span class="sxs-lookup"><span data-stu-id="1a9eb-282">Update the *Value* of the **PartitionKey** and **RowKey** as follows (remember to do this for each row property you add, though increment the RowKey each time):</span></span>

    ![Agregue los valores correctos](images/AzureLabs-Lab8-26-5.png)

9.  <span data-ttu-id="1a9eb-284">Haga clic en **Agregar propiedad** para agregar filas de datos adicionales.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-284">Click **Add property** to add extra rows of data.</span></span> <span data-ttu-id="1a9eb-285">Hacer la primera tabla vacía que coincida con la tabla siguiente.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-285">Make your first empty table match the below table.</span></span>

10. <span data-ttu-id="1a9eb-286">Haga clic en **Aceptar** cuando haya terminado.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-286">Click **OK** when you are finished.</span></span>

    ![Cuando haya terminado, haga clic en Aceptar](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > <span data-ttu-id="1a9eb-288">Asegúrese de que ha cambiado el **tipo** de la **X**, **Y**, y **Z**, entradas de **doble**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-288">Ensure that you have changed the **Type** of the **X**, **Y**, and **Z**, entries to **Double**.</span></span> 

11. <span data-ttu-id="1a9eb-289">Observará que la tabla tiene ahora una fila de datos.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-289">You will notice your table now has a row of data.</span></span> <span data-ttu-id="1a9eb-290">Haga clic en el **+** (icono nuevo para agregar otra entidad más).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-290">Click the **+** (plus) icon again to add another entity.</span></span>

    ![primera fila](images/AzureLabs-Lab8-27-5.png)

12. <span data-ttu-id="1a9eb-292">Cree una propiedad adicional y, a continuación, establezca los valores de la nueva entidad que coincidan con las que se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-292">Create an additional property, and then set the values of the new entity to match those shown below.</span></span>

    ![Agregar cubo](images/AzureLabs-Lab8-28.png)

13. <span data-ttu-id="1a9eb-294">Repita el último paso para agregar otra entidad.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-294">Repeat the last step to add another entity.</span></span> <span data-ttu-id="1a9eb-295">Establezca los valores para esta entidad en los que se muestran a continuación.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-295">Set the values for this entity to those shown below.</span></span>

    ![Agregar cilindro](images/AzureLabs-Lab8-29.png)

14. <span data-ttu-id="1a9eb-297">Ahora, la tabla debería parecerse a lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-297">Your table should now look like the one below.</span></span>

    ![tabla completa](images/AzureLabs-Lab8-30.png)

15. <span data-ttu-id="1a9eb-299">Ha completado este capítulo.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-299">You have completed this Chapter.</span></span> <span data-ttu-id="1a9eb-300">Asegúrese de guardar.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-300">Make sure to save.</span></span>

## <a name="chapter-6---create-an-azure-function-app"></a><span data-ttu-id="1a9eb-301">Capítulo 6: crear una aplicación de función de Azure</span><span class="sxs-lookup"><span data-stu-id="1a9eb-301">Chapter 6 - Create an Azure Function App</span></span>

<span data-ttu-id="1a9eb-302">Crear una aplicación de función de Azure, que será llamado por la aplicación de escritorio para actualizar el **tabla** de servicio y enviar una notificación a través de la **centro de notificaciones**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-302">Create an Azure Function App, which will be called by the Desktop application to update the **Table** service and send a notification through the **Notification Hub**.</span></span>

<span data-ttu-id="1a9eb-303">En primer lugar, deberá crear un archivo que permitirá que la función de Azure cargar las bibliotecas que necesarias.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-303">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="1a9eb-304">Abra **el Bloc de notas** (presione la tecla de Windows y escriba notepad).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-304">Open **Notepad** (press Windows Key and type notepad).</span></span>

    ![Abra el Bloc de notas](images/AzureLabs-Lab8-31.png)

2.  <span data-ttu-id="1a9eb-306">Con el Bloc de notas abierto, inserte la siguiente estructura JSON en ella.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-306">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="1a9eb-307">Una vez que lo haya hecho, guárdelo en el escritorio como **project.json**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-307">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="1a9eb-308">Es importante que la nomenclatura sea correcta: asegúrese de que lo hace **no tienen un .txt** la extensión de archivo.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-308">It is important that the naming is correct: ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="1a9eb-309">Este archivo define las bibliotecas que se va a utilizar la función, si ha usado NuGet le resultarán familiares.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-309">This file defines the libraries your function will use, if you have used NuGet it will look familiar.</span></span>

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

3.  <span data-ttu-id="1a9eb-310">Inicie sesión en el [Portal Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-310">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="1a9eb-311">Una vez que haya iniciado sesión, haga clic en **New** en la esquina superior izquierda esquina y busque **Function App**, presione **ENTRAR**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-311">Once you are logged in, click on **New** in the top left corner, and search for **Function App**, press **Enter**.</span></span>

    ![Busque la aplicación de función](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > <span data-ttu-id="1a9eb-313">La palabra **New** se han reemplazado con **crear un recurso**, en los portales más reciente.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-313">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

5.  <span data-ttu-id="1a9eb-314">La nueva página proporcionará una descripción de la **Function App** service.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-314">The new page will provide a description of the **Function App** service.</span></span> <span data-ttu-id="1a9eb-315">En la parte inferior izquierda de este símbolo del sistema, seleccione el **crear** botón para crear una asociación con este servicio.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-315">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![instancia de la aplicación de función](images/AzureLabs-Lab8-33.png)

6.  <span data-ttu-id="1a9eb-317">Una vez que ha hecho clic **crear**, rellene lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-317">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="1a9eb-318">Para **nombre de la aplicación**, inserte el nombre deseado para esta instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-318">For **App name**, insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="1a9eb-319">Seleccione un **suscripción**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-319">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="1a9eb-320">Seleccione el plan de tarifa adecuado para usted, si ésta es la primera hora de creación de un **Function App Service**, un nivel gratuito debe estar disponible para usted.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-320">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="1a9eb-321">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-321">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="1a9eb-322">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-322">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="1a9eb-323">Se recomienda mantener todos los servicios de Azure asociados a un proyecto único (por ejemplo, por ejemplo, estos laboratorios) en un grupo de recursos comunes).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-323">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="1a9eb-324">Si desea leer más acerca de los grupos de recursos de Azure, siga este [vínculo sobre cómo administrar un grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-324">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="1a9eb-325">Para **OS**, haga clic en Windows, ya que es la plataforma prevista.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-325">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="1a9eb-326">Seleccione un **Plan de hospedaje** (este tutorial se usará un **Plan de consumo**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-326">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="1a9eb-327">Seleccione un **ubicación** **(elija la misma ubicación que el almacenamiento que ha creado en el paso anterior)**</span><span class="sxs-lookup"><span data-stu-id="1a9eb-327">Select a **Location** **(choose the same location as the storage you have built in the previous step)**</span></span>

    8. <span data-ttu-id="1a9eb-328">Para el **almacenamiento** sección **debe seleccionar el servicio de almacenamiento que creó en el paso anterior**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-328">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="1a9eb-329">No necesitará *Application Insights* en esta aplicación, por lo que no dude en dejarlo **desactivar**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-329">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="1a9eb-330">Haga clic en **Crear**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-330">Click **Create**.</span></span>

        ![Crear nueva instancia](images/AzureLabs-Lab8-34.png)

7.  <span data-ttu-id="1a9eb-332">Una vez que ha hecho clic **crear** tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-332">Once you have clicked on **Create** you will have to wait for the service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="1a9eb-333">Una vez creada la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-333">A notification will appear in the portal once the Service instance is created.</span></span>

    ![nueva notificación](images/AzureLabs-Lab8-35.png)

9.  <span data-ttu-id="1a9eb-335">Haga clic en las notificaciones para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-335">Click on the notifications to explore your new Service instance.</span></span>

10. <span data-ttu-id="1a9eb-336">Haga clic en el **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-336">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![Ir al recurso](images/AzureLabs-Lab8-36.png)

11. <span data-ttu-id="1a9eb-338">Haga clic en el **+** (más) situado junto a *funciones*a *crear nuevo*.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-338">Click the **+** (plus) icon next to *Functions*, to *Create new*.</span></span>

    ![Agregar nueva función](images/AzureLabs-Lab8-37.png)

12. <span data-ttu-id="1a9eb-340">En el panel central, el **función** aparecerá la ventana de creación.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-340">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="1a9eb-341">Omitir la información de la mitad superior del panel y haga clic en **función personalizada**, que se encuentra en la parte inferior (en el área azul más abajo).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-341">Ignore the information in the upper half of the panel, and click **Custom function**, which is located near the bottom (in the blue area, as below).</span></span>

    ![función personalizada](images/AzureLabs-Lab8-38.png)

13. <span data-ttu-id="1a9eb-343">La nueva página dentro de la ventana mostrará los distintos tipos de función.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-343">The new page within the window will show various function types.</span></span> <span data-ttu-id="1a9eb-344">Desplácese hacia abajo para ver los tipos de color púrpuras y haga clic en **HTTP PUT** elemento.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-344">Scroll down to view the purple types, and click **HTTP PUT** element.</span></span>

    ![vínculo de put de http](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > <span data-ttu-id="1a9eb-346">Es posible que tenga que desplazarse aún más la profundidad la página (y esta imagen puede no ser exactamente el mismo, si han realizado actualizaciones del Portal de Azure), sin embargo, que busca un elemento denominado *HTTP PUT*.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-346">You may have to scroll further the down the page (and this image may not look exactly the same, if Azure Portal updates have taken place), however, you are looking for an element called *HTTP PUT*.</span></span>

14. <span data-ttu-id="1a9eb-347">El **HTTP PUT** ventana aparecerá, donde deberá configurar la función (vea a continuación para la imagen).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-347">The **HTTP PUT** window will appear, where you need to configure the function (see below for image).</span></span>

    1.  <span data-ttu-id="1a9eb-348">Para **lenguaje,** mediante el menú desplegable, seleccione C\#.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-348">For **Language,** using the dropdown menu, select C\#.</span></span>

    2.  <span data-ttu-id="1a9eb-349">Para **nombre,** un nombre adecuado de entrada.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-349">For **Name,** input an appropriate name.</span></span>

    3.  <span data-ttu-id="1a9eb-350">En el **nivel de autenticación** menú desplegable, seleccione **función**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-350">In the **Authentication level** dropdown menu, select **Function**.</span></span>

    4.  <span data-ttu-id="1a9eb-351">Para el **nombre de la tabla** sección, deberá usar el nombre exacto que usó para crear su **tabla** servicio anteriormente (incluido letras mayúsculas y minúsculas).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-351">For the **Table name** section, you need to use the exact name you used to create your **Table** service previously (including the same letter case).</span></span>

    5.  <span data-ttu-id="1a9eb-352">Dentro de la **conexión de la cuenta de almacenamiento** sección, use el menú desplegable y seleccione la cuenta de almacenamiento a partir de ahí.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-352">Within the **Storage account connection** section, use the dropdown menu, and select your storage account from there.</span></span> <span data-ttu-id="1a9eb-353">Si no está allí, clic la **New** hipervínculo junto con el título de sección para mostrar otro panel, donde debería aparecer su cuenta de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-353">If it is not there, click the **New** hyperlink alongside the section title, to show another panel, where your storage account should be listed.</span></span>

        ![nuevo almacenamiento](images/AzureLabs-Lab8-40.png)

15. <span data-ttu-id="1a9eb-355">Haga clic en **crear** y recibirá una notificación que se ha actualizado correctamente la configuración.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-355">Click **Create** and you will receive a notification that your settings have been updated successfully.</span></span>

    ![Crear función](images/AzureLabs-Lab8-41.png)

16. <span data-ttu-id="1a9eb-357">Después de hacer clic **crear**, se le redirigirá al editor de función.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-357">After clicking **Create**, you will be redirected to the function editor.</span></span>

    ![Actualizar código de función](images/AzureLabs-Lab8-42.png)

17. <span data-ttu-id="1a9eb-359">Inserte el código siguiente en el editor de funciones (el código de la función que reemplaza):</span><span class="sxs-lookup"><span data-stu-id="1a9eb-359">Insert the following code into the function editor (replacing the code in the function):</span></span>

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
    > <span data-ttu-id="1a9eb-360">Mediante las bibliotecas incluyen, la función recibe el nombre y la ubicación del objeto que se ha movido de la escena de Unity (como un C# objeto, denominado **UnityGameObject**).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-360">Using the included libraries, the function receives the name and location of the object which was moved in the Unity scene (as a C# object, called **UnityGameObject**).</span></span> <span data-ttu-id="1a9eb-361">Este objeto, a continuación, se usa para actualizar los parámetros de objeto dentro de la tabla creada.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-361">This object is then used to update the object parameters within the created table.</span></span> <span data-ttu-id="1a9eb-362">De este modo, la función realiza una llamada al servicio creado centro de notificaciones, que notifica a todos los de las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-362">Following this, the function makes a call to your created Notification Hub service, which notifies all subscribed applications.</span></span>

18. <span data-ttu-id="1a9eb-363">Con el código en su lugar, haga clic en **guardar**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-363">With the code in place, click **Save**.</span></span>

19. <span data-ttu-id="1a9eb-364">A continuación, haga clic en el **\<** icono (flecha), en el lado derecho de la página.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-364">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![panel de carga abierta](images/AzureLabs-Lab8-43.png)

20. <span data-ttu-id="1a9eb-366">Un panel se desliza en desde la derecha.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-366">A panel will slide in from the right.</span></span> <span data-ttu-id="1a9eb-367">En el panel de control, haga clic en **cargar**, y se mostrará un explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-367">In that panel, click **Upload**, and a File Browser will appear.</span></span>

21. <span data-ttu-id="1a9eb-368">Vaya a y haga clic en, el **project.json** archivo que creó en **el Bloc de notas** anteriormente y, a continuación, haga clic en el **abierto** botón.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-368">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="1a9eb-369">Este archivo define las bibliotecas que se va a usar la función.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-369">This file defines the libraries that your function will use.</span></span>

    ![upload json](images/AzureLabs-Lab8-44.png)

22. <span data-ttu-id="1a9eb-371">Cuando se ha cargado el archivo, aparecerá en el panel de la derecha.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-371">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="1a9eb-372">Haga clic en él se abrirá dentro la **función** editor.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-372">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="1a9eb-373">Debe examinar **exactamente** igual que la imagen siguiente (siguiente paso 23).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-373">It must look **exactly** the same as the next image (below step 23).</span></span>

23. <span data-ttu-id="1a9eb-374">A continuación, en el panel de la izquierda, bajo **funciones**, haga clic en el **integrar** vínculo.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-374">Then, in the panel on the left, beneath **Functions**, click the **Integrate** link.</span></span>

    ![integrar (función)](images/AzureLabs-Lab8-45.png)

24. <span data-ttu-id="1a9eb-376">En la página siguiente, en la esquina superior derecha, haga clic en **editor avanzado** (continuación).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-376">On the next page, in the top right corner, click **Advanced editor** (as below).</span></span>

    ![Abrir el editor avanzado](images/AzureLabs-Lab8-46.png)

25. <span data-ttu-id="1a9eb-378">Un **function.json** archivo se abrirá en el panel central, que debe reemplazarse por el siguiente fragmento de código.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-378">A **function.json** file will be opened in the center panel, which needs to be replaced with the following code snippet.</span></span> <span data-ttu-id="1a9eb-379">Esto define la función que se va a compilar y los parámetros pasados a la función.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-379">This defines the function you are building and the parameters passed into the function.</span></span>

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

26. <span data-ttu-id="1a9eb-380">El editor ahora debería parecerse a la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-380">Your editor should now look like the image below:</span></span>

    ![volver al editor estándar](images/AzureLabs-Lab8-47.png)

27. <span data-ttu-id="1a9eb-382">Es posible que observe los parámetros de entrada que acaba de insertar podrían no coincidir con los detalles de la tabla y el almacenamiento y, por tanto, deberá actualizarse con la información.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-382">You may notice the input parameters that you have just inserted might not match your table and storage details and therefore will need to be updated with your information.</span></span> <span data-ttu-id="1a9eb-383">**Esta operación no aquí**, tal y como se trata a continuación.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-383">**Do not do this here**, as it is covered next.</span></span> <span data-ttu-id="1a9eb-384">Simplemente haga clic en el **editor estándar** vínculo, en la esquina superior derecha de la página para volver atrás.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-384">Simply click the **Standard editor** link, in the top-right corner of the page, to go back.</span></span>

28. <span data-ttu-id="1a9eb-385">En el **editor estándar**, haga clic en **(tabla) de Azure Table Storage**, en **entradas**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-385">Back in the **Standard editor**, click **Azure Table Storage (table)**, under **Inputs**.</span></span> 
    
    ![Entradas de tabla](images/AzureLabs-Lab8-47-5.png)

29. <span data-ttu-id="1a9eb-387">Asegúrese de que la siguiente coincidencia **su** información, como pueden ser diferentes (no hay una imagen hasta por debajo de los pasos siguientes):</span><span class="sxs-lookup"><span data-stu-id="1a9eb-387">Ensure the following match to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="1a9eb-388">**Nombre de la tabla**: el nombre de la tabla que creó en el almacenamiento de Azure, servicio de tablas.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-388">**Table name**: the name of the table you created within your Azure Storage, Tables service.</span></span>

    2.  <span data-ttu-id="1a9eb-389">**Conexión de la cuenta de almacenamiento:** haga clic en **nuevo**, que aparece junto con el menú desplegable, y aparecerá un panel a la derecha de la ventana.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-389">**Storage account connection:** click **new**, which appears alongside the dropdown menu, and a panel will appear to the right of the window.</span></span>

        ![nuevo almacenamiento](images/AzureLabs-Lab8-48.png)

        1.  <span data-ttu-id="1a9eb-391">Seleccione su **cuenta de almacenamiento**, que creó anteriormente para hospedar el **aplicaciones de función.**</span><span class="sxs-lookup"><span data-stu-id="1a9eb-391">Select your **Storage Account**, which you created previously to host the **Function Apps.**</span></span>

        2. <span data-ttu-id="1a9eb-392">Observará que el **cuenta de almacenamiento** se ha creado el valor de la conexión.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-392">You will notice that the **Storage Account** connection value has been created.</span></span>

        3. <span data-ttu-id="1a9eb-393">Asegúrese de que presionar **guardar** cuando haya terminado.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-393">Make sure to press **Save** once you are done.</span></span>

    3.  <span data-ttu-id="1a9eb-394">El **entradas** página ahora debe coincidir con la muestra a continuación, **su** información.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-394">The **Inputs** page should now match the below, showing **your** information.</span></span>

        ![complete las entradas](images/AzureLabs-Lab8-49.png)

30. <span data-ttu-id="1a9eb-396">A continuación, haga clic en **(notificación) de Azure Notification Hub** : en **salidas**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-396">Next, click **Azure Notification Hub (notification)** - under **Outputs**.</span></span> <span data-ttu-id="1a9eb-397">Asegúrese de que coincidan con los siguientes **su** información, como pueden ser diferentes (no hay una imagen hasta por debajo de los pasos siguientes):</span><span class="sxs-lookup"><span data-stu-id="1a9eb-397">Ensure the following are matched to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="1a9eb-398">**Nombre del centro de notificaciones**: éste es el nombre de su **centro de notificaciones** instancia de servicio que creó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-398">**Notification Hub Name**: this is the name of your **Notification Hub** service instance, which you created previously.</span></span>

    2.  <span data-ttu-id="1a9eb-399">**Conexión de espacio de nombres de Notification Hubs**: haga clic en **nuevo**, que aparece junto con el menú desplegable.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-399">**Notification Hubs namespace connection**: click **new**, which appears alongside the dropdown menu.</span></span>

        ![Comprobar resultados](images/AzureLabs-Lab8-50.png)

    3. <span data-ttu-id="1a9eb-401">El **conexión** emergente aparecerá (consulte la imagen siguiente), donde se debe seleccionar la **Namespace** de la **centro de notificaciones**, que configuró anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-401">The **Connection** popup will appear (see image below), where you need to select the **Namespace** of the **Notification Hub**, which you set up previously.</span></span>

    4. <span data-ttu-id="1a9eb-402">Seleccione su **centro de notificaciones** nombre en el menú desplegable central.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-402">Select your **Notification Hub** name from the middle dropdown menu.</span></span>

    5.  <span data-ttu-id="1a9eb-403">Establecer el **directiva** del menú desplegable para **DefaultFullSharedAccessSignature**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-403">Set the **Policy** dropdown menu to **DefaultFullSharedAccessSignature**.</span></span>

    6. <span data-ttu-id="1a9eb-404">Haga clic en el **seleccione** botón para volver atrás.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-404">Click the **Select** button to go back.</span></span>

        ![actualización de salida](images/AzureLabs-Lab8-51.png)

31.  <span data-ttu-id="1a9eb-406">El **salidas** página ahora debe coincidir con el más abajo, pero con **su** información en su lugar.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-406">The **Outputs** page should now match the below, but with **your** information instead.</span></span> <span data-ttu-id="1a9eb-407">Asegúrese de que presionar **guardar**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-407">Make sure to press **Save**.</span></span>

> [!WARNING]
> <span data-ttu-id="1a9eb-408">*No modifique directamente el nombre del centro de notificaciones* (debería todo esto se realiza mediante el **Editor avanzado**, siempre que ha seguido los pasos anteriores correctamente.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-408">*Do not edit the Notification Hub name directly* (this should all be done using the **Advanced Editor**, provided you followed the previous steps correctly.</span></span>

![salidas completa](images/AzureLabs-Lab8-50.png)

32. <span data-ttu-id="1a9eb-410">En este momento, debe probar la función, para asegurarse de que funciona.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-410">At this point, you should test the function, to ensure it is working.</span></span> <span data-ttu-id="1a9eb-411">Para ello:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-411">To do this:</span></span> 

    1. <span data-ttu-id="1a9eb-412">Vaya a la página de la función una vez más:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-412">Navigate to the function page once more:</span></span>

        ![salidas completa](images/AzureLabs-Lab8-50-1.png)

    2. <span data-ttu-id="1a9eb-414">En la página de la función, haga clic en el **prueba** ficha en el extremo derecho de la página para abrir el *prueba* hoja:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-414">Back on the function page, click the **Test** tab on the far right side of the page, to open the *Test* blade:</span></span>

        ![salidas completa](images/AzureLabs-Lab8-50-2.png)

    3. <span data-ttu-id="1a9eb-416">Dentro de la **cuerpo de la solicitud** cuadro de texto de la hoja, pegue el siguiente código:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-416">Within the **Request body** textbox of the blade, paste the below code:</span></span>

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

    4. <span data-ttu-id="1a9eb-417">Con el código de prueba en su lugar, haga clic en el **ejecutar** situado en la esquina inferior derecha y la prueba se ejecutará.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-417">With the test code in place, click the **Run** button at the bottom right, and the test will be run.</span></span> <span data-ttu-id="1a9eb-418">Los registros de salida de la prueba aparecerá en el área de la consola, bajo el código de función.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-418">The output logs of the test will appear in the console area, below your function code.</span></span>

        ![salidas completa](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > <span data-ttu-id="1a9eb-420">Si se produce un error en la prueba anterior, deberá comprobar que ha seguido los pasos anteriores exactamente, especialmente la configuración de la **integrar panel**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-420">If the above test fails, you will need to double check that you have followed the above steps exactly, particularly the settings within the **integrate panel**.</span></span> 

## <a name="chapter-7---set-up-desktop-unity-project"></a><span data-ttu-id="1a9eb-421">Capítulo 7: configurar el proyecto de Unity de escritorio</span><span class="sxs-lookup"><span data-stu-id="1a9eb-421">Chapter 7 - Set up Desktop Unity Project</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1a9eb-422">La aplicación de escritorio que se va a crear, **no** profesional en el Editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-422">The Desktop application which you are now creating, **will not** work in the Unity Editor.</span></span> <span data-ttu-id="1a9eb-423">Necesita para ejecutarse fuera del Editor, siguiendo la compilación de la aplicación con Visual Studio (o la aplicación implementada).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-423">It needs to be run outside of the Editor, following the Building of the application, using Visual Studio (or the deployed application).</span></span> 

<span data-ttu-id="1a9eb-424">El siguiente es un conjunto típico de para desarrollar con Unity y realidad mixta y por lo tanto, es una buena plantilla para otros proyectos.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-424">The following is a typical set up for developing with Unity and mixed reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="1a9eb-425">Configurar y probar los auriculares de realidad mixta envolventes.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-425">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE] 
> <span data-ttu-id="1a9eb-426">Podrá **no** requieren controladores de movimiento de este curso.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-426">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="1a9eb-427">Si necesita admite la configuración de los auriculares envolventes, siga esta [vínculo sobre cómo configurar Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-427">If you need support setting up the immersive headset, please follow this [link on how to set up Windows Mixed Reality](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="1a9eb-428">Abra **Unity** y haga clic en **New**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-428">Open **Unity** and click **New**.</span></span>

    ![nuevo proyecto de unity](images/AzureLabs-Lab8-52.png)

2.  <span data-ttu-id="1a9eb-430">Deberá proporcionar un nombre de proyecto de Unity, inserte **UnityDesktopNotifHub**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-430">You need to provide a Unity Project name, insert **UnityDesktopNotifHub**.</span></span> <span data-ttu-id="1a9eb-431">Asegúrese de que el tipo de proyecto se establece en **3D**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-431">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="1a9eb-432">Establecer el **ubicación** a algún lugar adecuado para usted (Recuerde, es mejor cuanto más se acerque a los directorios raíz).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-432">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="1a9eb-433">A continuación, haga clic en **crear un proyecto**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-433">Then, click **Create project**.</span></span>

    ![Crear proyecto](images/AzureLabs-Lab8-53.png)

3.  <span data-ttu-id="1a9eb-435">Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-435">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="1a9eb-436">Vaya a **editar** > **preferencias** y, a continuación, en la ventana nueva, vaya a **herramientas externas**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-436">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="1a9eb-437">Cambio **External Script Editor** a **de Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-437">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="1a9eb-438">Cerrar la **preferencias** ventana.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-438">Close the **Preferences** window.</span></span>

    ![conjunto de herramientas de VS externas](images/AzureLabs-Lab8-54.png)

4.  <span data-ttu-id="1a9eb-440">A continuación, vaya a **archivo** > **configuración de compilación** y seleccione **Universal Windows Platform**, a continuación, haga clic en el **Cambiar plataforma**botón para aplicar la selección.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-440">Next, go to **File** > **Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![cambiar la plataforma](images/AzureLabs-Lab8-55.png)

5.  <span data-ttu-id="1a9eb-442">Mientras sigue en **archivo** > **configuración de compilación**, asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-442">While still in **File** > **Build Settings**, make sure that:</span></span>

    1.  <span data-ttu-id="1a9eb-443">**Dispositivo de destino** está establecido en **cualquier dispositivo**</span><span class="sxs-lookup"><span data-stu-id="1a9eb-443">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="1a9eb-444">Esta aplicación será para el escritorio, por lo que debe ser **cualquier dispositivo**</span><span class="sxs-lookup"><span data-stu-id="1a9eb-444">This Application will be for your desktop, so must be **Any Device**</span></span>

    2.  <span data-ttu-id="1a9eb-445">**Tipo de compilación** está establecido en **D3D**</span><span class="sxs-lookup"><span data-stu-id="1a9eb-445">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="1a9eb-446">**SDK** está establecido en **instalada más reciente**</span><span class="sxs-lookup"><span data-stu-id="1a9eb-446">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="1a9eb-447">**Versión de Visual Studio** está establecido en **instalada más reciente**</span><span class="sxs-lookup"><span data-stu-id="1a9eb-447">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="1a9eb-448">**Compilar y ejecutar** está establecido en **máquina Local**</span><span class="sxs-lookup"><span data-stu-id="1a9eb-448">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="1a9eb-449">Aquí, merece la pena guardar la escena y agregarlo a la compilación.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-449">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="1a9eb-450">Hacer esto seleccionando **agregar escenas abierto**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-450">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="1a9eb-451">Aparecerá el guardado de la ventana.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-451">A save window will appear.</span></span>

            ![Agregar escenas abiertos](images/AzureLabs-Lab8-56.png)

        2. <span data-ttu-id="1a9eb-453">Cree una nueva carpeta de esto y cualquier futuro, escena, a continuación, seleccione el **nueva carpeta** botón para crear una nueva carpeta y asígnele el nombre **escenas**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-453">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![nueva carpeta de segundo plano](images/AzureLabs-Lab8-57.png)

        3. <span data-ttu-id="1a9eb-455">Abra el recién creado **escenas** carpeta y, a continuación, en el **nombre de archivo:** campo de texto, escriba **NH\_Desktop\_escena**, a continuación, presione **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-455">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_Desktop\_Scene**, then press **Save**.</span></span>

            ![nuevo NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  <span data-ttu-id="1a9eb-457">El resto de la configuración, en **configuración de compilación**, debe dejarse como predeterminada por ahora.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-457">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="1a9eb-458">En la misma ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el **Inspector** se encuentra.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-458">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7.  <span data-ttu-id="1a9eb-459">En este panel, es necesario comprobar algunas opciones de configuración:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-459">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="1a9eb-460">En el **otra configuración** pestaña:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-460">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="1a9eb-461">**Versión en tiempo de ejecución de secuencias de comandos** debe ser **Experimental (.NET 4.6 equivalente)**</span><span class="sxs-lookup"><span data-stu-id="1a9eb-461">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**</span></span>

        2. <span data-ttu-id="1a9eb-462">**Scripting de back-end** debe ser **.NET**</span><span class="sxs-lookup"><span data-stu-id="1a9eb-462">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="1a9eb-463">**Nivel de compatibilidad de API** debe ser **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="1a9eb-463">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![versión de .NET 4.6](images/AzureLabs-Lab8-59.png)

    2.  <span data-ttu-id="1a9eb-465">Dentro de la **configuración de publicación** ficha **capacidades**, consulte:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-465">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="1a9eb-466">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="1a9eb-466">**InternetClient**</span></span>

            ![cliente de internet de graduación](images/AzureLabs-Lab8-60.png)

8.  <span data-ttu-id="1a9eb-468">En **configuración de compilación** *Unity C\# proyectos* ya no está atenuada; Marque la casilla situada junto a esto.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-468">Back in **Build Settings** *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="1a9eb-469">Cerrar la **configuración de compilación** ventana.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-469">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="1a9eb-470">Guarde la escena y el proyecto **archivo** > **Guardar escena / archivo** > **Guardar proyecto**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-470">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="1a9eb-471">Si desea omitir la *configurar Unity* componente para este proyecto (aplicación de escritorio) y continuar directamente en código, no dude en [descargar este .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), importarlo en el proyecto como un [ **Paquete personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)y, a continuación, continuar desde [capítulo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-471">If you wish to skip the *Unity Set up* component for this project (Desktop App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>  <span data-ttu-id="1a9eb-472">Deberá agregar los componentes de script.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-472">You will still need to add the script components.</span></span>

## <a name="chapter-8---importing-the-dlls-in-unity"></a><span data-ttu-id="1a9eb-473">Capítulo 8: importar los archivos DLL en Unity</span><span class="sxs-lookup"><span data-stu-id="1a9eb-473">Chapter 8 - Importing the DLLs in Unity</span></span>

<span data-ttu-id="1a9eb-474">Va a usar Azure Storage para Unity (que a su vez aprovecha el .net SDK de Azure).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-474">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="1a9eb-475">Para obtener más información, siga este [vínculo acerca del almacenamiento de Azure para Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-475">For more information follow this [link about Azure Storage for Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="1a9eb-476">Actualmente hay un problema conocido en Unity que requiere complementos volver a configurar tras la importación.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-476">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="1a9eb-477">Estos pasos (4-7 en esta sección) ya no será necesarios una vez que se ha resuelto el error.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-477">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="1a9eb-478">Para importar el SDK en su propio proyecto, asegúrese de que ha descargado la versión más reciente [ **.unitypackage** ](https://aka.ms/azstorage-unitysdk) desde GitHub.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-478">To import the SDK into your own project, make sure you have downloaded the latest [**.unitypackage**](https://aka.ms/azstorage-unitysdk) from GitHub.</span></span> <span data-ttu-id="1a9eb-479">A continuación, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-479">Then, do the following:</span></span>

1.  <span data-ttu-id="1a9eb-480">Agregar el **.unitypackage** a Unity mediante el uso de la **activos \> Importar paquete \> paquete personalizado** opción de menú.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-480">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="1a9eb-481">En el **Importar paquete de Unity** cuadro que aparece, puede seleccionar todo el contenido \*\**complemento* \> \* \*\*\* de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-481">In the **Import Unity Package** box that pops up, you can select everything under \*\**Plugin* \> \*Storage\*\*\*.</span></span>  <span data-ttu-id="1a9eb-482">Desactive todo lo demás, ya no es necesaria para este curso.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-482">Uncheck everything else, as it is not needed for this course.</span></span>

    ![Importar paquete](images/AzureLabs-Lab8-61.png)

3.  <span data-ttu-id="1a9eb-484">Haga clic en el ***importación*** para agregar los elementos al proyecto.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-484">Click the ***Import*** button to add the items to your project.</span></span>

4.  <span data-ttu-id="1a9eb-485">Vaya a la **almacenamiento** carpeta bajo **complementos** en el proyecto, ver y seleccione los siguientes complementos *sólo*:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-485">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="1a9eb-486">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="1a9eb-486">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="1a9eb-487">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="1a9eb-487">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="1a9eb-488">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="1a9eb-488">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="1a9eb-489">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="1a9eb-489">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="1a9eb-490">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="1a9eb-490">System.Spatial</span></span>

![Desactive cualquier plataforma](images/AzureLabs-Lab8-62.png)

5.  <span data-ttu-id="1a9eb-492">Con *estos complementos específicos* seleccionado, **desactive** **cualquier plataforma** y **desactive** **WSAPlayer** a continuación, haga clic en **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-492">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![se aplican a archivos DLL de plataforma](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > <span data-ttu-id="1a9eb-494">Vamos a marcar estos complementos determinados para su uso en el Editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-494">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="1a9eb-495">Esto es porque hay diferentes versiones de los complementos mismos en la carpeta WSA que se utilizará después de que el proyecto se exporta desde Unity.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-495">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="1a9eb-496">En el **almacenamiento** carpeta de complemento, solo seleccione:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-496">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="1a9eb-497">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="1a9eb-497">Microsoft.Data.Services.Client</span></span>

        ![No procesar conjunto para archivos DLL](images/AzureLabs-Lab8-64.png)

7.  <span data-ttu-id="1a9eb-499">Compruebe el **proceso no** cuadro bajo **configuración de plataforma** y haga clic en ***aplicar***.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-499">Check the **Don't Process** box under **Platform Settings** and click ***Apply***.</span></span>

    ![no aplicar ningún procesamiento](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > <span data-ttu-id="1a9eb-501">Vamos a marcar este complemento "No procesar", porque la revisión del ensamblado de Unity tiene dificultades para procesar este complemento.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-501">We are marking this plugin "Don't process", because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="1a9eb-502">El complemento seguirá funcionando aunque no se ha procesado.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-502">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="1a9eb-503">Capítulo 9: crear la clase TableToScene en el proyecto de Unity de escritorio</span><span class="sxs-lookup"><span data-stu-id="1a9eb-503">Chapter 9 - Create the TableToScene class in the Desktop Unity project</span></span>

<span data-ttu-id="1a9eb-504">Deberá crear las secuencias de comandos que contiene el código para ejecutar esta aplicación.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-504">You now need to create the scripts containing the code to run this application.</span></span>

<span data-ttu-id="1a9eb-505">Es el primer script, deberá crear **TableToScene**, que es responsable de:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-505">The first script you need to create is **TableToScene**, which is responsible for:</span></span>

-   <span data-ttu-id="1a9eb-506">Leer entidades dentro de la tabla de Azure.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-506">Reading entities within the Azure Table.</span></span>
-   <span data-ttu-id="1a9eb-507">Con los datos de tabla, determinar qué objetos desea generar y en qué posición.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-507">Using the Table data, determine which objects to spawn, and in which position.</span></span>

<span data-ttu-id="1a9eb-508">Es el segundo script, deberá crear **CloudScene**, que es responsable de:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-508">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="1a9eb-509">Registrando el evento primario, para permitir al usuario arrastrar objetos en torno a la escena.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-509">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>
-   <span data-ttu-id="1a9eb-510">Serializar los datos del objeto de esta escena de Unity y enviarlo a la aplicación de función de Azure.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-510">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="1a9eb-511">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-511">To create this class:</span></span>

1.  <span data-ttu-id="1a9eb-512">Haga clic en el **activos** carpeta se encuentra en el Panel de proyecto **crear** > **carpeta**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-512">Right-click in the **Asset** Folder located in the Project Panel, **Create** > **Folder**.</span></span> <span data-ttu-id="1a9eb-513">Nombre de la carpeta **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-513">Name the folder **Scripts**.</span></span>

    ![Crear carpeta de scripts](images/AzureLabs-Lab8-66.png)

    ![Crear carpeta de scripts 2](images/AzureLabs-Lab8-67.png)

2.  <span data-ttu-id="1a9eb-516">Haga doble clic en la carpeta que acaba de crear para abrirlo.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-516">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="1a9eb-517">Haga clic en el **Scripts** carpeta, haga clic en **crear**  >   **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-517">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="1a9eb-518">Nombre de la secuencia de comandos **TableToScene**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-518">Name the script **TableToScene**.</span></span>

    <span data-ttu-id="1a9eb-519">![script de c#](images/AzureLabs-Lab8-68.png)
    ![TableToScene rename](images/AzureLabs-Lab8-69.png)</span><span class="sxs-lookup"><span data-stu-id="1a9eb-519">![new c# script](images/AzureLabs-Lab8-68.png)
![TableToScene rename](images/AzureLabs-Lab8-69.png)</span></span>

4.  <span data-ttu-id="1a9eb-520">Haga doble clic en el script para abrirlo en Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-520">Double-click on the script to open it in Visual Studio 2017.</span></span>

5.  <span data-ttu-id="1a9eb-521">Agregue los espacios de nombres siguientes:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-521">Add the following namespaces:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  <span data-ttu-id="1a9eb-522">Dentro de la clase, inserte las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-522">Within the class, insert the following variables:</span></span>

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
    > <span data-ttu-id="1a9eb-523">Sustituya el **accountName** valor con el nombre del servicio de almacenamiento de Azure y **accountKey** valor con el valor de clave que se encuentra en el servicio de almacenamiento de Azure, en el Portal de Azure (consulte la imagen siguiente).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-523">Substitute the **accountName** value with your Azure Storage Service name and **accountKey** value with the key value found in the Azure Storage Service, in the Azure Portal (See Image below).</span></span> 
    >
    > ![clave de cuenta de captura](images/AzureLabs-Lab8-70.png)

7.  <span data-ttu-id="1a9eb-525">Ahora, agregue el **Start()** y **Awake()** métodos para inicializar la clase.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-525">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

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

8.  <span data-ttu-id="1a9eb-526">Dentro de la **TableToScene** clase, agregue el método que recupere los valores de la tabla de Azure y usarlas para generar los tipos primitivos adecuados en la escena.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-526">Within the **TableToScene** class, add the method that will retrieve the values from the Azure Table and use them to spawn the appropriate primitives in the scene.</span></span>

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

9.  <span data-ttu-id="1a9eb-527">Fuera del **TableToScene** (clase), deberá definir la clase usada por la aplicación de serializar y deserializar la **las entidades de tabla**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-527">Outside the **TableToScene** class, you need to define the class used by the application to serialize and deserialize the **Table Entities**.</span></span>

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

10. <span data-ttu-id="1a9eb-528">Asegúrese de que **guardar** antes de volver al Editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-528">Make sure you **Save** before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="1a9eb-529">Haga clic en el **cámara principal** desde el **jerarquía** panel, para que sus propiedades aparecen en la **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-529">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="1a9eb-530">Con el **Scripts** carpeta abierta, seleccione la secuencia de comandos **TableToScene archivo** y arrástrelo hasta el **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-530">With the **Scripts** folder open, select the script **TableToScene file** and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="1a9eb-531">El resultado debería ser como sigue:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-531">The result should be as below:</span></span>

    ![Agregar script a la cámara principal](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="1a9eb-533">Capítulo 10: crear la clase CloudScene en el proyecto de Unity de escritorio</span><span class="sxs-lookup"><span data-stu-id="1a9eb-533">Chapter 10 - Create the CloudScene class in the Desktop Unity Project</span></span>

<span data-ttu-id="1a9eb-534">Es el segundo script, deberá crear **CloudScene**, que es responsable de:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-534">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="1a9eb-535">Registrando el evento primario, para permitir al usuario arrastrar objetos en torno a la escena.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-535">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>

-   <span data-ttu-id="1a9eb-536">Serializar los datos del objeto de esta escena de Unity y enviarlo a la aplicación de función de Azure.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-536">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="1a9eb-537">Para crear el segundo script:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-537">To create the second script:</span></span>

1.  <span data-ttu-id="1a9eb-538">Haga clic en el **Scripts** carpeta, haga clic en **crear**, **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-538">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="1a9eb-539">Nombre de la secuencia de comandos **CloudScene**</span><span class="sxs-lookup"><span data-stu-id="1a9eb-539">Name the script **CloudScene**</span></span>
    
    <span data-ttu-id="1a9eb-540">![script de c#](images/AzureLabs-Lab8-72.png)
    ![cambiar el nombre de CloudScene](images/AzureLabs-Lab8-73.png)</span><span class="sxs-lookup"><span data-stu-id="1a9eb-540">![new c# script](images/AzureLabs-Lab8-72.png)
![rename CloudScene](images/AzureLabs-Lab8-73.png)</span></span>

2.  <span data-ttu-id="1a9eb-541">Agregue los espacios de nombres siguientes:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-541">Add the following namespaces:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  <span data-ttu-id="1a9eb-542">Inserte las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-542">Insert the following variables:</span></span>

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

4.  <span data-ttu-id="1a9eb-543">Sustituya el **azureFunctionEndpoint** valor por su URL de aplicación de función de Azure se encuentra en el servicio de aplicación de función de Azure, en el Portal de Azure, como se muestra en la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-543">Substitute the **azureFunctionEndpoint** value with your Azure Function App URL found in the Azure Function App Service, in the Azure Portal, as shown in the image below:</span></span>

    ![obtener la dirección URL de función](images/AzureLabs-Lab8-74.png)

5.  <span data-ttu-id="1a9eb-545">Ahora, agregue el **Start()** y **Awake()** métodos para inicializar la clase.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-545">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

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

6.  <span data-ttu-id="1a9eb-546">Dentro de la **Update()** método, agregue el código siguiente que detectará la entrada del mouse y arrastre, lo que a su vez se moverá GameObjects en la escena.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-546">Within the **Update()** method, add the following code that will detect the mouse input and drag, which will in turn move GameObjects in the scene.</span></span> <span data-ttu-id="1a9eb-547">Si el usuario ha arrastrar y colocar un objeto, se pasará el nombre y las coordenadas del objeto al método **UpdateCloudScene()** , que llamará el servicio de Azure Function App, que actualizará la tabla de Azure y desencadenar el notificación.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-547">If the user has dragged and dropped an object, it will pass the name and coordinates of the object to the method **UpdateCloudScene()**, which will call the Azure Function App service, which will update the Azure table and trigger the notification.</span></span>

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

7.  <span data-ttu-id="1a9eb-548">Ahora, agregue el **UpdateCloudScene()** método, como sigue:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-548">Now add the **UpdateCloudScene()** method, as below:</span></span>

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

8.  <span data-ttu-id="1a9eb-549">Guarde el código y volver a Unity</span><span class="sxs-lookup"><span data-stu-id="1a9eb-549">Save the code and return to Unity</span></span>

9.  <span data-ttu-id="1a9eb-550">Arrastre el **CloudScene** de script en el **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-550">Drag the **CloudScene** script onto the **Main Camera**.</span></span> 

    1. <span data-ttu-id="1a9eb-551">Haga clic en el **cámara principal** desde el **jerarquía** panel, para que sus propiedades aparecen en la **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-551">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span> 

    2. <span data-ttu-id="1a9eb-552">Con el **Scripts** abierto, seleccione de la carpeta la **CloudScene** de secuencias de comandos y arrástrelo hasta el **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-552">With the **Scripts** folder open, select the **CloudScene** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="1a9eb-553">El resultado debería ser como sigue:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-553">The result should be as below:</span></span>

        > ![Arrastre el script en la nube a cámara principal](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a><span data-ttu-id="1a9eb-555">Capítulo 11: Compile el proyecto de escritorio para UWP</span><span class="sxs-lookup"><span data-stu-id="1a9eb-555">Chapter 11 - Build the Desktop Project to UWP</span></span>

<span data-ttu-id="1a9eb-556">Ahora todo lo necesario para la sección de Unity de este proyecto se ha completado.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-556">Everything needed for the Unity section of this project has now been completed.</span></span>

1.  <span data-ttu-id="1a9eb-557">Vaya a **configuración de compilación** (**archivo** > **configuración de compilación**).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-557">Navigate to **Build Settings** (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="1a9eb-558">Desde el **configuración de compilación** ventana, haga clic en **compilar**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-558">From the **Build Settings** window, click **Build**.</span></span>

    ![Compilar proyecto](images/AzureLabs-Lab8-76.png)

3.  <span data-ttu-id="1a9eb-560">Un **Explorador de archivos** menú emergente de voluntad de ventana, que le solicitará una ubicación para la compilación.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-560">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="1a9eb-561">Cree una nueva carpeta (haciendo clic en **nueva carpeta** en la esquina superior izquierda) y asígnele el nombre **compilaciones**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-561">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![nueva carpeta de compilación](images/AzureLabs-Lab8-77.png)

    1.  <span data-ttu-id="1a9eb-563">Abra el nuevo **compilaciones** carpeta y cree otra carpeta (mediante **nueva carpeta** una vez más) y asígnele el nombre **NH\_Desktop\_aplicación**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-563">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_Desktop\_App**.</span></span>

        ![nombre de la carpeta NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  <span data-ttu-id="1a9eb-565">Con el **NH\_Desktop\_aplicación** seleccionado.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-565">With the **NH\_Desktop\_App** selected.</span></span> <span data-ttu-id="1a9eb-566">Haga clic en **seleccionar la carpeta**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-566">click **Select Folder**.</span></span> <span data-ttu-id="1a9eb-567">El proyecto tardará un minuto o más en crear.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-567">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="1a9eb-568">Después de la compilación, **Explorador de archivos** aparecerá con la ubicación del nuevo proyecto.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-568">Following build, **File Explorer** will appear showing you the location of your new project.</span></span> <span data-ttu-id="1a9eb-569">No hay necesidad de abrirlo, aunque, como necesite para crear otro Unity del proyecto en primer lugar, en los siguientes capítulos.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-569">No need to open it, though, as you need to create the other Unity project first, in the next few Chapters.</span></span>


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a><span data-ttu-id="1a9eb-570">Capítulo 12: configurar el proyecto de Unity de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="1a9eb-570">Chapter 12 - Set up Mixed Reality Unity Project</span></span>

<span data-ttu-id="1a9eb-571">El siguiente es un conjunto típico de para el desarrollo con la realidad mixta y por lo tanto, es una buena plantilla para otros proyectos.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-571">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="1a9eb-572">Abra **Unity** y haga clic en **New**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-572">Open **Unity** and click **New**.</span></span>

    ![nuevo proyecto de unity](images/AzureLabs-Lab8-79.png)

2.  <span data-ttu-id="1a9eb-574">Ahora deberá proporcionar un nombre de proyecto de Unity, insertar **UnityMRNotifHub**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-574">You will now need to provide a Unity Project name, insert **UnityMRNotifHub**.</span></span> <span data-ttu-id="1a9eb-575">Asegúrese de que el tipo de proyecto se establece en **3D**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-575">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="1a9eb-576">Establecer el **ubicación** a algún lugar adecuado para usted (Recuerde, es mejor cuanto más se acerque a los directorios raíz).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-576">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="1a9eb-577">A continuación, haga clic en **crear un proyecto**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-577">Then, click **Create project**.</span></span>

    ![nombre UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  <span data-ttu-id="1a9eb-579">Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-579">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="1a9eb-580">Vaya a **editar** > **preferencias** y, a continuación, en la ventana nueva, vaya a **herramientas externas**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-580">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="1a9eb-581">Cambio **External Script Editor** a **de Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-581">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="1a9eb-582">Cerrar la **preferencias** ventana.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-582">Close the **Preferences** window.</span></span>

    ![editor de conjuntos de externas a VS](images/AzureLabs-Lab8-81.png)

4.  <span data-ttu-id="1a9eb-584">A continuación, vaya a **archivo** > **configuración de compilación** y cambiar la plataforma a **Universal Windows Platform**, haciendo clic en el **Cambiar plataforma**  botón.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-584">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![cambiar la plataforma a UWP](images/AzureLabs-Lab8-82.png)

5.  <span data-ttu-id="1a9eb-586">Vaya a **archivo** > **configuración de compilación** y asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-586">Go to **File** > **Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="1a9eb-587">**Dispositivo de destino** está establecido en **cualquier dispositivo**</span><span class="sxs-lookup"><span data-stu-id="1a9eb-587">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="1a9eb-588">Para el Microsoft HoloLens, establezca **dispositivo de destino** a *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-588">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="1a9eb-589">**Tipo de compilación** está establecido en **D3D**</span><span class="sxs-lookup"><span data-stu-id="1a9eb-589">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="1a9eb-590">**SDK** está establecido en **instalada más reciente**</span><span class="sxs-lookup"><span data-stu-id="1a9eb-590">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="1a9eb-591">**Versión de Visual Studio** está establecido en **instalada más reciente**</span><span class="sxs-lookup"><span data-stu-id="1a9eb-591">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="1a9eb-592">**Compilar y ejecutar** está establecido en **máquina Local**</span><span class="sxs-lookup"><span data-stu-id="1a9eb-592">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="1a9eb-593">Aquí, merece la pena guardar la escena y agregarlo a la compilación.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-593">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="1a9eb-594">Hacer esto seleccionando **agregar escenas abierto**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-594">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="1a9eb-595">Aparecerá el guardado de la ventana.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-595">A save window will appear.</span></span>

            ![Agregar escenas abiertos](images/AzureLabs-Lab8-83.png)

        2. <span data-ttu-id="1a9eb-597">Cree una nueva carpeta de esto y cualquier futuro, escena, a continuación, seleccione el **nueva carpeta** botón para crear una nueva carpeta y asígnele el nombre **escenas**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-597">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![nueva carpeta de segundo plano](images/AzureLabs-Lab8-84.png)

        3. <span data-ttu-id="1a9eb-599">Abra el recién creado **escenas** carpeta y, a continuación, en el **nombre de archivo:** campo de texto, escriba **NH\_MR\_escena**, a continuación, presione  **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-599">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_MR\_Scene**, then press **Save**.</span></span>

            ![new scene - NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  <span data-ttu-id="1a9eb-601">El resto de la configuración, en **configuración de compilación**, debe dejarse como predeterminada por ahora.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-601">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="1a9eb-602">En la misma ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el **Inspector** se encuentra.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-602">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>    

    ![Abrir configuración del Reproductor](images/AzureLabs-Lab8-86.png)

7.  <span data-ttu-id="1a9eb-604">En este panel, es necesario comprobar algunas opciones de configuración:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-604">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="1a9eb-605">En el **otra configuración** pestaña:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-605">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="1a9eb-606">**Versión en tiempo de ejecución de secuencias de comandos** debe ser **Experimental** (.NET 4.6 equivalente)</span><span class="sxs-lookup"><span data-stu-id="1a9eb-606">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>
        2.  <span data-ttu-id="1a9eb-607">**Scripting de back-end** debe ser ***.NET***</span><span class="sxs-lookup"><span data-stu-id="1a9eb-607">**Scripting Backend** should be ***.NET***</span></span>
        3.  <span data-ttu-id="1a9eb-608">**Nivel de compatibilidad de API** debe ser **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="1a9eb-608">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![compatibilidad con la API](images/AzureLabs-Lab8-87.png)

    2.  <span data-ttu-id="1a9eb-610">Más abajo el panel, en **XR configuración** (bajo **configuración de publicación**), graduación **admite la realidad Virtual**, asegúrese de que el **SDK de Windows Mixed Reality**  se agrega</span><span class="sxs-lookup"><span data-stu-id="1a9eb-610">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![actualizar la configuración de xr](images/AzureLabs-Lab8-88.png)        

    3.  <span data-ttu-id="1a9eb-612">Dentro de la **configuración de publicación** ficha **capacidades**, documentales:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-612">Within the **Publishing Settings** tab, under **Capabilities**, heck:</span></span>

        - <span data-ttu-id="1a9eb-613">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="1a9eb-613">**InternetClient**</span></span>           

            ![cliente de internet de graduación](images/AzureLabs-Lab8-89.png)

8.  <span data-ttu-id="1a9eb-615">En **configuración de compilación**, **Unity C# proyectos** ya no está atenuado: Marque la casilla situada junto a esto.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-615">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="1a9eb-616">Con estos cambios realizados, cierre la ventana de configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-616">With these changes done, close the Build Settings window.</span></span>

10. <span data-ttu-id="1a9eb-617">Guarde la escena y el proyecto **archivo** > **Guardar escena / archivo** > **Guardar proyecto**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-617">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="1a9eb-618">Si desea omitir la *configurar Unity* componente para este proyecto (aplicación de la realidad mixta) y continuar directamente en código, no dude en [descargar este .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), importarlo en el proyecto como un [ **Paquete personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)y, a continuación, continuar desde [capítulo 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-618">If you wish to skip the *Unity Set up* component for this project (mixed reality App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span></span> <span data-ttu-id="1a9eb-619">Deberá agregar los componentes de script.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-619">You will still need to add the script components.</span></span>

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a><span data-ttu-id="1a9eb-620">Capítulo 13: importar los archivos DLL en el proyecto de Unity de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="1a9eb-620">Chapter 13 - Importing the DLLs in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="1a9eb-621">Va a usar el almacenamiento de Azure para la biblioteca de Unity (que usa el SDK de .net para Azure).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-621">You will be using Azure Storage for Unity library (which uses the .Net SDK for Azure).</span></span> <span data-ttu-id="1a9eb-622">Siga esta [vínculo sobre cómo usar el almacenamiento de Azure con Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-622">Please follow this [link on how to use Azure Storage with Unity](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>
<span data-ttu-id="1a9eb-623">Actualmente hay un problema conocido en Unity que requiere complementos volver a configurar tras la importación.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-623">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="1a9eb-624">Estos pasos (4-7 en esta sección) ya no será necesarios una vez que se ha resuelto el error.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-624">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="1a9eb-625">Para importar el SDK en su propio proyecto, asegúrese de que ha descargado la versión más reciente [.unitypackage](https://aka.ms/azstorage-unitysdk).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-625">To import the SDK into your own project, make sure you have downloaded the latest [.unitypackage](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="1a9eb-626">A continuación, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-626">Then, do the following:</span></span>

1.  <span data-ttu-id="1a9eb-627">Agregar el .unitypackage que descargó desde el anterior a Unity mediante el uso de la **activos** > **Importar paquete** > **paquete personalizado** opción de menú .</span><span class="sxs-lookup"><span data-stu-id="1a9eb-627">Add the .unitypackage you downloaded from the above, to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

2.  <span data-ttu-id="1a9eb-628">En el **Importar paquete de Unity** cuadro que aparece, puede seleccionar todo el contenido **complemento** > **almacenamiento**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-628">In the **Import Unity Package** box that pops up, you can select everything under **Plugin** > **Storage**.</span></span>

    ![Importar paquete](images/AzureLabs-Lab8-90.png)

3.  <span data-ttu-id="1a9eb-630">Haga clic en el **importación** para agregar los elementos al proyecto.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-630">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="1a9eb-631">Vaya a la **almacenamiento** carpeta bajo **complementos** en el proyecto, ver y seleccione los siguientes complementos *sólo*:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-631">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="1a9eb-632">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="1a9eb-632">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="1a9eb-633">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="1a9eb-633">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="1a9eb-634">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="1a9eb-634">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="1a9eb-635">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="1a9eb-635">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="1a9eb-636">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="1a9eb-636">System.Spatial</span></span>

    ![Seleccione los complementos](images/AzureLabs-Lab8-91.png)

5.  <span data-ttu-id="1a9eb-638">Con *estos complementos específicos* seleccionado, **desactive** **cualquier plataforma** y **desactive** **WSAPlayer** a continuación, haga clic en **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-638">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![Aplicar cambios de plataforma](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > <span data-ttu-id="1a9eb-640">Marca estos complementos determinados para su uso en el Editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-640">You are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="1a9eb-641">Esto es porque hay diferentes versiones de los complementos mismos en la carpeta WSA que se utilizará después de que el proyecto se exporta desde Unity.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-641">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="1a9eb-642">En el **almacenamiento** carpeta de complemento, solo seleccione:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-642">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="1a9eb-643">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="1a9eb-643">Microsoft.Data.Services.Client</span></span>

        ![Seleccione el cliente de servicios de datos](images/AzureLabs-Lab8-93.png)

7.  <span data-ttu-id="1a9eb-645">Compruebe el **proceso no** cuadro bajo **configuración de plataforma** y haga clic en **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-645">Check the **Don't Process** box under **Platform Settings** and click **Apply**.</span></span>

    ![No procesar](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > <span data-ttu-id="1a9eb-647">Marca este complemento "No procesar" porque la revisión del ensamblado de Unity tiene dificultades para procesar este complemento.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-647">You are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="1a9eb-648">El complemento seguirá funcionando aunque no se procesa.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-648">The plugin will still work even though it isn't processed.</span></span>

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="1a9eb-649">Capítulo 14: creación de la clase TableToScene en el proyecto de Unity de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="1a9eb-649">Chapter 14 - Creating the TableToScene class in the mixed reality Unity project</span></span>

<span data-ttu-id="1a9eb-650">El **TableToScene** clase es idéntica a la que se explica en [capítulo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-650">The **TableToScene** class is identical to the one explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span> <span data-ttu-id="1a9eb-651">Crear la misma clase en el proyecto de Unity siguiendo el mismo procedimiento se explica en la realidad mixta [capítulo 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-651">Create the same class in the mixed reality Unity Project following the same procedure explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>

<span data-ttu-id="1a9eb-652">Cuando haya completado este capítulo, tanto de su **proyectos de Unity** tendrá esta clase en la cámara principal.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-652">Once you have completed this Chapter, both of your **Unity Projects** will have this class set up on the Main Camera.</span></span>

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="1a9eb-653">Capítulo 15: creación de la clase NotificationReceiver en el proyecto de Unity de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="1a9eb-653">Chapter 15 - Creating the NotificationReceiver class in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="1a9eb-654">Es el segundo script, deberá crear **NotificationReceiver**, que es responsable de:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-654">The second script you need to create is **NotificationReceiver**, which is responsible for:</span></span>

-   <span data-ttu-id="1a9eb-655">Registrar la aplicación con el centro de notificaciones en la inicialización.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-655">Registering the app with the Notification Hub at initialization.</span></span>
-   <span data-ttu-id="1a9eb-656">Escuchar notificaciones procedentes del centro de notificaciones.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-656">Listening to notifications coming from the Notification Hub.</span></span>
-   <span data-ttu-id="1a9eb-657">Al deserializar los datos del objeto desde las notificaciones recibidas.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-657">Deserializing the object data from received notifications.</span></span>
-   <span data-ttu-id="1a9eb-658">Mueva los GameObjects en la escena, en función de los datos deserializados.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-658">Move the GameObjects in the scene, based on the deserialized data.</span></span>

<span data-ttu-id="1a9eb-659">Para crear el **NotificationReceiver** secuencia de comandos:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-659">To create the **NotificationReceiver** script:</span></span>

1.  <span data-ttu-id="1a9eb-660">Haga clic en el **Scripts** carpeta, haga clic en **crear**, **C\# Script**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-660">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="1a9eb-661">Nombre de la secuencia de comandos **NotificationReceiver**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-661">Name the script **NotificationReceiver**.</span></span>

    <span data-ttu-id="1a9eb-662">![Crear script de c#](images/AzureLabs-Lab8-95.png)
    ![denomínelo NotificationReceiver](images/AzureLabs-Lab8-96.png)</span><span class="sxs-lookup"><span data-stu-id="1a9eb-662">![create new c# script](images/AzureLabs-Lab8-95.png)
![name it NotificationReceiver](images/AzureLabs-Lab8-96.png)</span></span>

2.  <span data-ttu-id="1a9eb-663">Haga doble clic en el script para abrirlo.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-663">Double click on the script to open it.</span></span>

3.  <span data-ttu-id="1a9eb-664">Agregue los espacios de nombres siguientes:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-664">Add the following namespaces:</span></span>

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

4.  <span data-ttu-id="1a9eb-665">Inserte las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-665">Insert the following variables:</span></span>

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

5.  <span data-ttu-id="1a9eb-666">Sustituya el **hubName** valor por el nombre de servicio de Notification hubs y **hubListenEndpoint** con el valor de punto de conexión se encuentra en la pestaña de directivas de acceso, el servicio de Azure Notification hubs, en el Portal de Azure (consulte la imagen siguiente).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-666">Substitute the **hubName** value with your Notification Hub Service name, and **hubListenEndpoint** value with the endpoint value found in the Access Policies tab, Azure Notification Hub Service, in the Azure Portal (see image below).</span></span>

    ![Insertar punto de conexión de directiva de notification hubs](images/AzureLabs-Lab8-97.png)

6.  <span data-ttu-id="1a9eb-668">Ahora, agregue el **Start()** y **Awake()** métodos para inicializar la clase.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-668">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

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

7.  <span data-ttu-id="1a9eb-669">Agregar el **WaitForNotification** método para permitir que la aplicación recibir notificaciones de la biblioteca de centro de notificaciones sin conflictos con el subproceso principal:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-669">Add the **WaitForNotification** method to allow the app to receive notifications from the Notification Hub Library without clashing with the Main Thread:</span></span>

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

8.  <span data-ttu-id="1a9eb-670">El método siguiente, **InitNotificationAsync()** , registrará la aplicación con la notificación del servicio de concentrador en la inicialización.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-670">The following method, **InitNotificationAsync()**, will register the application with the notification Hub Service at initialization.</span></span> <span data-ttu-id="1a9eb-671">El código está comentado como Unity, no podrá compilar el proyecto.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-671">The code is commented out as Unity will not be able to Build the project.</span></span> <span data-ttu-id="1a9eb-672">Se quitará los comentarios al importar el paquete Nuget de mensajería de Azure en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-672">You will remove the comments when you import the Azure Messaging Nuget package in Visual Studio.</span></span>

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

9.  <span data-ttu-id="1a9eb-673">El siguiente controlador, **canal\_PushNotificationReceived()** , se desencadenará cada vez que se recibe una notificación.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-673">The following handler, **Channel\_PushNotificationReceived()**, will be triggered every time a notification is received.</span></span> <span data-ttu-id="1a9eb-674">Deserializará la notificación, que es la entidad de tabla de Azure que se ha movido de la aplicación de escritorio y, a continuación, mueva el GameObject correspondiente en la escena MR a la misma posición.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-674">It will deserialize the notification, which will be the Azure Table Entity that has been moved on the Desktop Application, and then move the corresponding GameObject in the MR scene to the same position.</span></span> 
    
    > [!IMPORTANT]
    > <span data-ttu-id="1a9eb-675">El código está comentado porque el código hace referencia a la biblioteca de mensajería de Azure, que se va a agregar después de compilar el proyecto de Unity mediante el Administrador de paquetes de Nuget en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-675">The code is commented out because the code references the Azure Messaging library, which you will add after building the Unity project using the Nuget Package Manager, within Visual Studio.</span></span> <span data-ttu-id="1a9eb-676">Por lo tanto, el proyecto de Unity no podrá compilar, a menos que se está comentada. Tenga en cuenta que debe compilar el proyecto y, a continuación, se va a devolver a Unity, deberá **volver a comentar** ese código.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-676">As such, the Unity project will not be able to build, unless it is commented out. Be aware, that should you build your project, and then wish to return to Unity, you will need to **re-comment** that code.</span></span>

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

10. <span data-ttu-id="1a9eb-677">No olvide guardar los cambios antes de volver al Editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-677">Remember to save your changes before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="1a9eb-678">Haga clic en el **cámara principal** desde el **jerarquía** panel, para que sus propiedades aparecen en la **Inspector**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-678">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="1a9eb-679">Con el **Scripts** abierto, seleccione de la carpeta la **NotificationReceiver** de secuencias de comandos y arrástrelo hasta el **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-679">With the **Scripts** folder open, select the **NotificationReceiver** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="1a9eb-680">El resultado debería ser como sigue:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-680">The result should be as below:</span></span>

    ![Arrastre el script del receptor de notificaciones a la cámara](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > <span data-ttu-id="1a9eb-682">Si va a desarrollar para el Microsoft HoloLens, deberá actualizar el **cámara principal**del *cámara* componente, por lo que:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-682">If you are developing this for the Microsoft HoloLens, you will need to update the **Main Camera**'s *Camera* component, so that:</span></span>
    > - <span data-ttu-id="1a9eb-683">Borrar las marcas de: Color sólido</span><span class="sxs-lookup"><span data-stu-id="1a9eb-683">Clear Flags: Solid Color</span></span>
    > - <span data-ttu-id="1a9eb-684">En segundo plano: Negro</span><span class="sxs-lookup"><span data-stu-id="1a9eb-684">Background: Black</span></span>

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a><span data-ttu-id="1a9eb-685">Capítulo 16: compilar el proyecto de realidad mixta a UWP</span><span class="sxs-lookup"><span data-stu-id="1a9eb-685">Chapter 16 - Build the Mixed Reality Project to UWP</span></span>

<span data-ttu-id="1a9eb-686">Este capítulo es idéntico al proceso para el proyecto anterior de compilación.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-686">This Chapter is identical to build process for the previous project.</span></span> <span data-ttu-id="1a9eb-687">Todo lo necesario para la sección de Unity de este proyecto ahora se completó, por lo que es el momento de crearla desde Unity.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-687">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="1a9eb-688">Vaya a **configuración de compilación** ( **archivo** > **configuración de compilación** ).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-688">Navigate to **Build Settings** ( **File** > **Build Settings** ).</span></span>

2.  <span data-ttu-id="1a9eb-689">Desde el **configuración de compilación** menú, asegúrese de **Unity C# proyectos**\* está activada (lo que le permitirá modificar los scripts de este proyecto, después de la compilación).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-689">From the **Build Settings** menu, ensure **Unity C# Projects**\* is ticked (which will allow you to edit the scripts in this project, after build).</span></span>

3.  <span data-ttu-id="1a9eb-690">Una vez hecho esto, haga clic en **compilar**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-690">After this is done, click **Build**.</span></span>

    ![Compilar proyecto](images/AzureLabs-Lab8-99.png)

4.  <span data-ttu-id="1a9eb-692">Un **Explorador de archivos** menú emergente de voluntad de ventana, que le solicitará una ubicación para la compilación.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-692">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="1a9eb-693">Cree una nueva carpeta (haciendo clic en **nueva carpeta** en la esquina superior izquierda) y asígnele el nombre **compilaciones**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-693">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![Crear carpeta compilaciones](images/AzureLabs-Lab8-100.png)

    1.  <span data-ttu-id="1a9eb-695">Abra el nuevo **compilaciones** carpeta y cree otra carpeta (mediante **nueva carpeta** una vez más) y asígnele el nombre **NH\_MR\_aplicación**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-695">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_MR\_App**.</span></span>

        ![Crear carpeta NH_MR_Apps](images/AzureLabs-Lab8-101.png)

    2.  <span data-ttu-id="1a9eb-697">Con el **NH\_MR\_aplicación** seleccionado.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-697">With the **NH\_MR\_App** selected.</span></span> <span data-ttu-id="1a9eb-698">Haga clic en **seleccionar la carpeta**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-698">click **Select Folder**.</span></span> <span data-ttu-id="1a9eb-699">El proyecto tardará un minuto o más en crear.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-699">The project will take a minute or so to build.</span></span>

5.  <span data-ttu-id="1a9eb-700">Después de la compilación, un **Explorador de archivos** se abrirá una ventana en la ubicación del nuevo proyecto.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-700">Following the build, a **File Explorer** window will open at the location of your new project.</span></span>



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a><span data-ttu-id="1a9eb-701">Capítulo 17: agregar paquetes de NuGet para la solución UnityMRNotifHub</span><span class="sxs-lookup"><span data-stu-id="1a9eb-701">Chapter 17 - Add NuGet packages to the UnityMRNotifHub Solution</span></span>

> [!WARNING] 
> <span data-ttu-id="1a9eb-702">Recuerde que, una vez que agregue los siguientes paquetes NuGet (y quite los comentarios del código en los próximos [capítulo](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)), el código, cuando vuelva a abrir dentro del proyecto de Unity, presentará errores.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-702">Please remember that, once you add the following NuGet Packages (and uncomment the code in the next [Chapter](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)), the Code, when reopened within the Unity Project, will present errors.</span></span> <span data-ttu-id="1a9eb-703">Si desea volver atrás y continuar con la edición en el Editor de Unity, deberá comentar ese código errosome y, a continuación, quite a intentarlo más tarde, una vez que esté de nuevo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-703">If you wish to go back and continue editing in the Unity Editor, you will need comment that errosome code, and then uncomment again later, once you are back in Visual Studio.</span></span> 

<span data-ttu-id="1a9eb-704">Una vez completada la compilación de realidad mixta, navegue hasta el proyecto de realidad mixta, que ha creado, y haga doble clic en el archivo de solución (.sln) dentro de esa carpeta para abrir la solución con Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-704">Once the mixed reality build has been completed, navigate to the mixed reality project, which you built, and double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>
<span data-ttu-id="1a9eb-705">Ahora deberá agregar el **WindowsAzure.Messaging.managed** paquete de NuGet; se trata de una biblioteca que se usa para recibir notificaciones desde el centro de notificaciones.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-705">You will now need to add the **WindowsAzure.Messaging.managed** NuGet package; this is a library that is used to receive Notifications from the Notification Hub.</span></span>

<span data-ttu-id="1a9eb-706">Para importar el paquete de NuGet:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-706">To import the NuGet package:</span></span>

1.  <span data-ttu-id="1a9eb-707">En el **el Explorador de soluciones**, haga clic con el botón derecho en la solución</span><span class="sxs-lookup"><span data-stu-id="1a9eb-707">In the **Solution Explorer**, right click on your Solution</span></span>

2.  <span data-ttu-id="1a9eb-708">Haga clic en **administrar paquetes de NuGet**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-708">Click on **Manage NuGet Packages**.</span></span>

    ![Abra el Administrador de nuget](images/AzureLabs-Lab8-102.png)

3.  <span data-ttu-id="1a9eb-710">Seleccione el ***examinar*** pestaña y busque **WindowsAzure.Messaging.managed**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-710">Select the ***Browse*** tab and search for **WindowsAzure.Messaging.managed**.</span></span>

    ![Busque el paquete de mensajería de windows azure](images/AzureLabs-Lab8-103.png)

4.  <span data-ttu-id="1a9eb-712">Seleccione el resultado (como se muestra a continuación) y, en la ventana a la derecha, seleccione la casilla de verificación junto a **proyecto**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-712">Select the result (as shown below), and in the window to the right, select the checkbox next to **Project**.</span></span> <span data-ttu-id="1a9eb-713">Esto colocará una marca de verificación en la casilla de verificación junto a **proyecto**, junto con la casilla junto a la **ensamblado CSharp** y **UnityMRNotifHub** proyecto.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-713">This will place a tick in the checkbox next to **Project**, along with the checkbox next to the **Assembly-CSharp** and **UnityMRNotifHub** project.</span></span>

    ![Marque todos los proyectos](images/AzureLabs-Lab8-104.png)

5.  <span data-ttu-id="1a9eb-715">La versión proporcionada inicialmente **no** que sean compatibles con este proyecto.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-715">The version initially provided **may not** be compatible with this project.</span></span> <span data-ttu-id="1a9eb-716">Por lo tanto, haga clic en el menú desplegable junto a **versión**y haga clic en **versión 0.1.7.9**, a continuación, haga clic en **instalar**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-716">Therefore, click on the dropdown menu next to **Version**, and click **Version 0.1.7.9**, then click **Install**.</span></span>

6.  <span data-ttu-id="1a9eb-717">Ahora ha terminado de instalar el paquete NuGet.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-717">You have now finished installing the NuGet package.</span></span> <span data-ttu-id="1a9eb-718">Busque el código comentado que escribió en el **NotificationReceiver** clase y quite los comentarios...</span><span class="sxs-lookup"><span data-stu-id="1a9eb-718">Find the commented code you entered in the **NotificationReceiver** class and remove the comments..</span></span>



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a><span data-ttu-id="1a9eb-719">Capítulo 18: aplicación de edición UnityMRNotifHub, clase NotificationReceiver</span><span class="sxs-lookup"><span data-stu-id="1a9eb-719">Chapter 18 - Edit UnityMRNotifHub application, NotificationReceiver class</span></span>

<span data-ttu-id="1a9eb-720">Siguiendo una vez agregada la **paquetes de NuGet**, deberá *quite* parte del código dentro de la **NotificationReceiver** clase.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-720">Following having added the **NuGet Packages**, you will need to *uncomment* some of the code within the **NotificationReceiver** class.</span></span>

<span data-ttu-id="1a9eb-721">Esto incluye:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-721">This includes:</span></span>

1. <span data-ttu-id="1a9eb-722">El espacio de nombres en la parte superior:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-722">The namespace at the top:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. <span data-ttu-id="1a9eb-723">Todo el código dentro de la **InitNotificationsAsync()** método:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-723">All the code within the **InitNotificationsAsync()** method:</span></span>

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
> <span data-ttu-id="1a9eb-724">El código anterior tiene un comentario en él: asegúrese de que tiene no accidentalmente *marca de comentario* que comentar (como el código no se compilará si tienes!).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-724">The code above has a comment in it: ensure that you have not accidentally *uncommented* that comment (as the code will not compile if you have!).</span></span>

3. <span data-ttu-id="1a9eb-725">Y, por último, el **Channel_PushNotificationReceived** eventos:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-725">And, lastly, the **Channel_PushNotificationReceived** event:</span></span>

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

<span data-ttu-id="1a9eb-726">Con estos marca de comentario, asegúrese de guardar y, a continuación, continúe con el siguiente capítulo.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-726">With these uncommented, ensure that you save, and then proceed to the next Chapter.</span></span>

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a><span data-ttu-id="1a9eb-727">Capítulo 19: asociar el proyecto de realidad mixta en el app Store</span><span class="sxs-lookup"><span data-stu-id="1a9eb-727">Chapter 19 - Associate the mixed reality project to the Store app</span></span>

<span data-ttu-id="1a9eb-728">Ahora debe asociar el **la realidad mixta** proyecto a la aplicación Store que creó en el principio del laboratorio.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-728">You now need to associate the **mixed reality** project to the Store App you created in at the start of the lab.</span></span>

1.  <span data-ttu-id="1a9eb-729">Abra la solución.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-729">Open the solution.</span></span>

2.  <span data-ttu-id="1a9eb-730">Haga clic con el botón derecho en la aplicación para UWP proyecto en el panel Explorador de soluciones, el ir a **Store**, y **asociar aplicación con el Store...** .</span><span class="sxs-lookup"><span data-stu-id="1a9eb-730">Right click on the UWP app Project in the Solution Explorer panel, the go to **Store**, and **Associate App with the Store...**.</span></span>

    ![Abrir almacén de asociación](images/AzureLabs-Lab8-105.png)

3.  <span data-ttu-id="1a9eb-732">Se mostrará una nueva ventana llamada **asociar la aplicación con el Store Windows**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-732">A new window will appear called **Associate Your App with the Windows Store**.</span></span> <span data-ttu-id="1a9eb-733">Haz clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-733">Click **Next**.</span></span>

    ![Vaya a la pantalla siguiente](images/AzureLabs-Lab8-106.png)

4.  <span data-ttu-id="1a9eb-735">La carga de seguridad de todas las aplicaciones asociadas con la cuenta que ha iniciado sesión.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-735">It will load up all the Applications associated with the Account which you have logged in.</span></span> <span data-ttu-id="1a9eb-736">Si no ha iniciado sesión en su cuenta, puede **sesión** en esta página.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-736">If you are not logged in to your account, you can **Log In** on this page.</span></span>

5.  <span data-ttu-id="1a9eb-737">Buscar el **nombre de la aplicación Store** que creó al principio de este tutorial y selecciónelo.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-737">Find the **Store App name** that you created at the start of this tutorial and select it.</span></span> <span data-ttu-id="1a9eb-738">Haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-738">Then click **Next**.</span></span>

    ![Busque y seleccione el nombre del almacén](images/AzureLabs-Lab8-107.png)

6.  <span data-ttu-id="1a9eb-740">Haga clic en **asociar**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-740">Click **Associate**.</span></span>

    ![asociar la aplicación](images/AzureLabs-Lab8-108.png)

7.  <span data-ttu-id="1a9eb-742">La aplicación está ahora **asociado** con la aplicación Store.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-742">Your App is now **Associated** with the Store App.</span></span> <span data-ttu-id="1a9eb-743">Esto es necesario para habilitar las notificaciones.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-743">This is necessary for enabling Notifications.</span></span>

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a><span data-ttu-id="1a9eb-744">Capítulo 20: implementar aplicaciones UnityMRNotifHub y UnityDesktopNotifHub</span><span class="sxs-lookup"><span data-stu-id="1a9eb-744">Chapter 20 - Deploy UnityMRNotifHub and UnityDesktopNotifHub applications</span></span>

<span data-ttu-id="1a9eb-745">Este capítulo puede ser más fácil con las dos personas, como el resultado incluirá tanto aplicaciones que se ejecutan, uno que ejecute en el equipo, escritorio y la otra en los auriculares envolventes.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-745">This Chapter may be easier with two people, as the result will include both apps running, one running on your computer Desktop, and the other within your immersive headset.</span></span>

<span data-ttu-id="1a9eb-746">La aplicación de auriculares envolventes está esperando a recibir los cambios a la escena (cambia de posición de los GameObjects local) y la aplicación de escritorio se realicen cambios en su escena local (cambia de posición), que se van a compartir a la aplicación MR.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-746">The immersive headset app is waiting to receive changes to the scene (position changes of the local GameObjects), and the Desktop app will be making changes to their local scene (position changes), which will be shared to the MR app.</span></span> <span data-ttu-id="1a9eb-747">Tiene sentido implementar la aplicación MR en primer lugar, seguida de la aplicación de escritorio, para que el receptor puede empezar a escuchar.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-747">It makes sense to deploy the MR app first, followed by the Desktop app, so that the receiver can begin listening.</span></span>

<span data-ttu-id="1a9eb-748">Para implementar el **UnityMRNotifHub** aplicación en el equipo Local:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-748">To deploy the **UnityMRNotifHub** app on your Local Machine:</span></span>

1.  <span data-ttu-id="1a9eb-749">Abra el archivo de solución de su **UnityMRNotifHub** app en **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-749">Open the solution file of your **UnityMRNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="1a9eb-750">En el **plataforma de solución**, seleccione **x86, equipo Local**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-750">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="1a9eb-751">En el **configuración de la solución** seleccione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-751">In the **Solution Configuration** select **Debug**.</span></span>

    ![conjunto de configuración del proyecto](images/AzureLabs-Lab8-109.png)

4.  <span data-ttu-id="1a9eb-753">Vaya a **menú compilar** y haga clic en **implementar solución** para transferir localmente la aplicación en el equipo.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-753">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="1a9eb-754">La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas, listos para iniciarse.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-754">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="1a9eb-755">Para implementar el **UnityDesktopNotifHub** aplicación en el equipo Local:</span><span class="sxs-lookup"><span data-stu-id="1a9eb-755">To deploy the **UnityDesktopNotifHub** app on Local Machine:</span></span>

1.  <span data-ttu-id="1a9eb-756">Abra el archivo de solución de su **UnityDesktopNotifHub** app en **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-756">Open the solution file of your **UnityDesktopNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="1a9eb-757">En el **plataforma de solución**, seleccione **x86, equipo Local**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-757">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="1a9eb-758">En el **configuración de la solución** seleccione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-758">In the **Solution Configuration** select **Debug**.</span></span>

    ![conjunto de configuración del proyecto](images/AzureLabs-Lab8-110.png)

4.  <span data-ttu-id="1a9eb-760">Vaya a **menú compilar** y haga clic en **implementar solución** para transferir localmente la aplicación en el equipo.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-760">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="1a9eb-761">La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas, listos para iniciarse.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-761">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

6.  <span data-ttu-id="1a9eb-762">Inicie la aplicación de realidad mixta, seguida de la aplicación de escritorio.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-762">Launch the mixed reality application, followed by the Desktop application.</span></span>

<span data-ttu-id="1a9eb-763">Con ambas aplicaciones se ejecutan, mover un objeto de la escena de escritorio (con el botón de Mouse de la izquierda).</span><span class="sxs-lookup"><span data-stu-id="1a9eb-763">With both applications running, move an object in the desktop scene (using the Left Mouse Button).</span></span> <span data-ttu-id="1a9eb-764">Estos cambios de posición se se realizan localmente, serializados y enviados al servicio de aplicación de función.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-764">These positional changes will be made locally, serialized, and sent to the Function App service.</span></span> <span data-ttu-id="1a9eb-765">El servicio de aplicación de función, a continuación, actualizará la tabla junto con el centro de notificaciones.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-765">The Function App service will then update the Table along with the Notification Hub.</span></span> <span data-ttu-id="1a9eb-766">Que ha recibido una actualización, el centro de notificaciones se enviarán los datos actualizados directamente a todas las aplicaciones registradas (en este caso, la aplicación envolventes auriculares), que, a continuación, deserializar los datos entrantes y los nuevos datos posicionales se aplican a los objetos locales, moverlos en escena.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-766">Having received an update, the Notification Hub will send the updated data directly to all the registered applications (in this case the immersive headset app), which will then deserialize the incoming data, and apply the new positional data to the local objects, moving them in scene.</span></span>


## <a name="your-finished-your-azure-notification-hubs-application"></a><span data-ttu-id="1a9eb-767">Su terminado la aplicación de Azure Notification Hubs</span><span class="sxs-lookup"><span data-stu-id="1a9eb-767">Your finished your Azure Notification Hubs application</span></span>
 
<span data-ttu-id="1a9eb-768">Enhorabuena, compila una aplicación de realidad mixta que aprovecha el servicio de Azure Notification Hubs y permite la comunicación entre aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="1a9eb-768">Congratulations, you built a mixed reality app that leverages the Azure Notification Hubs Service and allow communication between apps.</span></span>
 
![final producto-end](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a><span data-ttu-id="1a9eb-770">Ejercicios de bonificación</span><span class="sxs-lookup"><span data-stu-id="1a9eb-770">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="1a9eb-771">Ejercicio 1</span><span class="sxs-lookup"><span data-stu-id="1a9eb-771">Exercise 1</span></span>

<span data-ttu-id="1a9eb-772">¿Puede averiguar cómo cambiar el color de los GameObjects y enviar notificación a otras aplicaciones de visualización de la escena?</span><span class="sxs-lookup"><span data-stu-id="1a9eb-772">Can you work out how to change the color of the GameObjects and send that notification to other apps viewing the scene?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="1a9eb-773">Ejercicio 2</span><span class="sxs-lookup"><span data-stu-id="1a9eb-773">Exercise 2</span></span>

<span data-ttu-id="1a9eb-774">¿Puede agregar el movimiento de los GameObjects a la aplicación MR y ver la escena actualizada en su aplicación de escritorio?</span><span class="sxs-lookup"><span data-stu-id="1a9eb-774">Can you add movement of the GameObjects to your MR app and see the updated scene in your desktop app?</span></span>
