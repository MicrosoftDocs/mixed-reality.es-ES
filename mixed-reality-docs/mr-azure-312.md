---
title: 'MR y Azure 312: integración con bot'
description: Complete este curso para obtener información sobre cómo crear e implementar un bot, usar Microsoft bot Framework V4 y comunicarse con él en una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academy, Unity, tutorial, API, Computer Vision, hololens, inmersivo, VR, Microsoft bot Framework V4, Web App bot, Bot Framework, Microsoft bot
ms.openlocfilehash: 481693b5af8c946e1cb45dda5144e78a175fa771
ms.sourcegitcommit: 3b32339c5d5c79eaecd84ed27254a8f4321731f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2019
ms.locfileid: "70047228"
---
>[!NOTE]
><span data-ttu-id="1d77f-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="1d77f-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="1d77f-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="1d77f-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="1d77f-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1d77f-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="1d77f-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="1d77f-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="1d77f-108">Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1d77f-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="1d77f-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.</span><span class="sxs-lookup"><span data-stu-id="1d77f-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-312-bot-integration"></a><span data-ttu-id="1d77f-110">MR y Azure 312: Integración de bot</span><span class="sxs-lookup"><span data-stu-id="1d77f-110">MR and Azure 312: Bot integration</span></span>

<span data-ttu-id="1d77f-111">En este curso, aprenderá a crear e implementar un bot mediante Microsoft bot Framework V4 y a comunicarse con él a través de una aplicación de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="1d77f-111">In this course, you will learn how to create and deploy a bot using the Microsoft Bot Framework V4 and communicate with it through a Windows Mixed Reality application.</span></span> 

![](images/AzureLabs-Lab312-00.png)

<span data-ttu-id="1d77f-112">**Microsoft bot Framework V4** es un conjunto de API diseñadas para proporcionar a los desarrolladores las herramientas para crear una aplicación de bot extensible y escalable.</span><span class="sxs-lookup"><span data-stu-id="1d77f-112">The **Microsoft Bot Framework V4** is a set of APIs designed to provide developers with the tools to build an extensible and scalable bot application.</span></span> <span data-ttu-id="1d77f-113">Para obtener más información, visite la [Página Microsoft bot Framework](https://dev.botframework.com/) o el [repositorio git de V4](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span><span class="sxs-lookup"><span data-stu-id="1d77f-113">For more information, visit the [Microsoft Bot Framework page](https://dev.botframework.com/) or the [V4 Git Repository](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span></span>

<span data-ttu-id="1d77f-114">Después de completar este curso, habrá creado una aplicación de Windows Mixed Reality, que podrá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="1d77f-114">After completing this course, you will have built a Windows Mixed Reality application, which will be able to do the following:</span></span>

1. <span data-ttu-id="1d77f-115">Use un **gesto de TAP** para iniciar el bot que escucha la voz de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="1d77f-115">Use a **Tap Gesture** to start the bot listening for the users voice.</span></span>
2. <span data-ttu-id="1d77f-116">Cuando el usuario ha mencionado algo, el bot intentará proporcionar una respuesta.</span><span class="sxs-lookup"><span data-stu-id="1d77f-116">When the user has said something, the bot will attempt to provide a response.</span></span>
3. <span data-ttu-id="1d77f-117">Muestre la respuesta de bots como texto, situado cerca del bot, en la escena de Unity.</span><span class="sxs-lookup"><span data-stu-id="1d77f-117">Display the bots reply as text, positioned near the bot, in the Unity Scene.</span></span>

<span data-ttu-id="1d77f-118">En su aplicación, depende del modo en que va a integrar los resultados con el diseño.</span><span class="sxs-lookup"><span data-stu-id="1d77f-118">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="1d77f-119">Este curso está diseñado para enseñarle a integrar un servicio de Azure con su proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="1d77f-119">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="1d77f-120">Es su trabajo usar el conocimiento que obtiene de este curso para mejorar su aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="1d77f-120">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="1d77f-121">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="1d77f-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="1d77f-122">Recurso</span><span class="sxs-lookup"><span data-stu-id="1d77f-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="1d77f-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1d77f-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1d77f-124"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="1d77f-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="1d77f-125">MR y Azure 312: Integración de bot</span><span class="sxs-lookup"><span data-stu-id="1d77f-125">MR and Azure 312: Bot integration</span></span></td><td style="text-align: center;"> <span data-ttu-id="1d77f-126">✔️</span><span class="sxs-lookup"><span data-stu-id="1d77f-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="1d77f-127">✔️</span><span class="sxs-lookup"><span data-stu-id="1d77f-127">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="1d77f-128">Aunque este curso se centra principalmente en HoloLens, también puede aplicar lo que aprenda en este curso a los auriculares con Windows Mixed Reality inmersivo (VR).</span><span class="sxs-lookup"><span data-stu-id="1d77f-128">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="1d77f-129">Dado que los auriculares envolventes (VR) no tienen cámaras accesibles, necesitará una cámara externa conectada al equipo.</span><span class="sxs-lookup"><span data-stu-id="1d77f-129">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="1d77f-130">A medida que siga con el curso, verá notas sobre cualquier cambio que deba usar para admitir auriculares envolventes (VR).</span><span class="sxs-lookup"><span data-stu-id="1d77f-130">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1d77f-131">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="1d77f-131">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="1d77f-132">Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#.</span><span class="sxs-lookup"><span data-stu-id="1d77f-132">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="1d77f-133">Tenga en cuenta también que los requisitos previos y las instrucciones escritas dentro de este documento representan lo que se ha probado y comprobado en el momento de la escritura (2018 de julio).</span><span class="sxs-lookup"><span data-stu-id="1d77f-133">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="1d77f-134">Puede usar el software más reciente, como se indica en el artículo [instalar las herramientas](install-the-tools.md) , aunque no se debe suponer que la información de este curso se ajusta perfectamente a lo que encontrará en el software más reciente que el que se enumera a continuación.</span><span class="sxs-lookup"><span data-stu-id="1d77f-134">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="1d77f-135">Se recomienda el siguiente hardware y software para este curso:</span><span class="sxs-lookup"><span data-stu-id="1d77f-135">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="1d77f-136">Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de auriculares envolvente (VR)</span><span class="sxs-lookup"><span data-stu-id="1d77f-136">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="1d77f-137">Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="1d77f-137">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1d77f-138">El SDK de Windows 10 más reciente</span><span class="sxs-lookup"><span data-stu-id="1d77f-138">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1d77f-139">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="1d77f-139">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="1d77f-140">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="1d77f-140">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="1d77f-141">Un [auricular de Windows Mixed Reality inmersivo (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="1d77f-141">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="1d77f-142">Acceso a Internet para Azure y para la recuperación de Azure bot.</span><span class="sxs-lookup"><span data-stu-id="1d77f-142">Internet access for Azure, and for Azure Bot retrieval.</span></span> <span data-ttu-id="1d77f-143">Para obtener más información, [siga este vínculo](https://dev.botframework.com/).</span><span class="sxs-lookup"><span data-stu-id="1d77f-143">For more information, [please follow this link](https://dev.botframework.com/).</span></span>

### <a name="before-you-start"></a><span data-ttu-id="1d77f-144">Antes de comenzar</span><span class="sxs-lookup"><span data-stu-id="1d77f-144">Before you start</span></span>

1.  <span data-ttu-id="1d77f-145">Para evitar que se produzcan problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cerca de la raíz (las rutas de acceso de carpeta largas pueden producir problemas en tiempo de compilación).</span><span class="sxs-lookup"><span data-stu-id="1d77f-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="1d77f-146">Configure y pruebe su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1d77f-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="1d77f-147">Si necesita ayuda para configurar HoloLens, asegúrese [de visitar el artículo de configuración de hololens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="1d77f-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="1d77f-148">Es una buena idea realizar la calibración y el ajuste del sensor al empezar a desarrollar una nueva aplicación de HoloLens (a veces puede ayudar a realizar esas tareas para cada usuario).</span><span class="sxs-lookup"><span data-stu-id="1d77f-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="1d77f-149">Para obtener ayuda sobre la calibración, siga este [vínculo al artículo sobre la calibración de HoloLens](calibration.md#hololens-2).</span><span class="sxs-lookup"><span data-stu-id="1d77f-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens-2).</span></span>

<span data-ttu-id="1d77f-150">Para obtener ayuda sobre la optimización de sensores, siga este [vínculo al artículo sobre la optimización del sensor de HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="1d77f-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--create-the-bot-application"></a><span data-ttu-id="1d77f-151">Capítulo 1: creación de la aplicación bot</span><span class="sxs-lookup"><span data-stu-id="1d77f-151">Chapter 1 – Create the Bot application</span></span>

<span data-ttu-id="1d77f-152">El primer paso es crear el bot como una aplicación Web de ASP.Net Core local.</span><span class="sxs-lookup"><span data-stu-id="1d77f-152">The first step is to create your bot as a local ASP.Net Core Web application.</span></span> <span data-ttu-id="1d77f-153">Una vez que haya terminado y probado, lo publicará en Azure portal.</span><span class="sxs-lookup"><span data-stu-id="1d77f-153">Once you have finished and tested it, you will publish it to the Azure Portal.</span></span>

1.  <span data-ttu-id="1d77f-154">Abra Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1d77f-154">Open Visual Studio.</span></span> <span data-ttu-id="1d77f-155">Cree un nuevo proyecto, seleccione **asp net Core aplicación web** como el tipo de proyecto (lo encontrará en la subsección .net Core) y llámelo **MyBot**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-155">Create a new project, select **ASP NET Core Web Application** as the project type (you will find it under the subsection .NET Core) and call it **MyBot**.</span></span> <span data-ttu-id="1d77f-156">Haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-156">Click **OK**.</span></span>

2.  <span data-ttu-id="1d77f-157">En la ventana que aparecerá, seleccione **vacío**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-157">In the Window that will appear select **Empty**.</span></span> <span data-ttu-id="1d77f-158">Asegúrese también de que el destino esté establecido en **asp net Core 2,0** y que la autenticación esté establecida en **sin autenticación**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-158">Also make sure the target is set to **ASP NET Core 2.0** and the Authentication is set to **No Authentication**.</span></span> <span data-ttu-id="1d77f-159">Haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-159">Click **OK**.</span></span>  

    ![Creación de la aplicación bot](images/AzureLabs-Lab312-01.png)

3.  <span data-ttu-id="1d77f-161">La solución se abrirá ahora.</span><span class="sxs-lookup"><span data-stu-id="1d77f-161">The solution will now open.</span></span> <span data-ttu-id="1d77f-162">Haga clic con el botón derecho en la solución **Mybot** en el **Explorador de soluciones** y haga clic en **administrar paquetes NuGet para la solución**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-162">Right-click on Solution **Mybot** in the **Solution Explorer** and click on **Manage NuGet Packages for Solution**.</span></span> 

    ![Creación de la aplicación bot](images/AzureLabs-Lab312-02.png)

4.  <span data-ttu-id="1d77f-164">En la pestaña **examinar** , busque **Microsoft. bot. Builder. Integration. Aspnet. Core** (Asegúrese de que tiene activada **la versión preliminar** ).</span><span class="sxs-lookup"><span data-stu-id="1d77f-164">In the **Browse** tab, search for **Microsoft.Bot.Builder.Integration.AspNet.Core** (make sure you have **Include pre-release** checked).</span></span> <span data-ttu-id="1d77f-165">Seleccione la versión **de paquete 4.0.1-Preview**y marque las casillas de proyecto.</span><span class="sxs-lookup"><span data-stu-id="1d77f-165">Select the package version **4.0.1-preview**, and tick the project boxes.</span></span> <span data-ttu-id="1d77f-166">A continuación, haga clic en **instalar**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-166">Then click on **Install**.</span></span> <span data-ttu-id="1d77f-167">Ya ha instalado las bibliotecas necesarias para **Bot Framework V4**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-167">You have now installed the libraries needed for the **Bot Framework v4**.</span></span> <span data-ttu-id="1d77f-168">Cierre la página NuGet.</span><span class="sxs-lookup"><span data-stu-id="1d77f-168">Close the NuGet page.</span></span>

    ![Creación de la aplicación bot](images/AzureLabs-Lab312-03.png)

5.  <span data-ttu-id="1d77f-170">Haga clic con el botón derecho en el *proyecto*, **MyBot**, en el **Explorador de soluciones** y haga clic en **Agregar** **|** **clase**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-170">Right-click on your *Project*, **MyBot**, in the **Solution Explorer** and click on **Add** **|** **Class**.</span></span>

    ![Creación de la aplicación bot](images/AzureLabs-Lab312-04.png)

6.  <span data-ttu-id="1d77f-172">Asigne a la clase el nombre **MyBot** y haga clic en **Agregar**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-172">Name the class **MyBot** and click on **Add**.</span></span>

    ![Creación de la aplicación bot](images/AzureLabs-Lab312-05.png)

7.  <span data-ttu-id="1d77f-174">Repita el punto anterior para crear otra clase denominada **ConversationContext**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-174">Repeat the previous point, to create another class named **ConversationContext**.</span></span> 

8.  <span data-ttu-id="1d77f-175">Haga clic con el botón derecho en **wwwroot** en el **Explorador de soluciones** y haga clic en **Agregar** **|** **nuevo elemento**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-175">Right-click on **wwwroot** in the **Solution Explorer** and click on **Add** **|** **New Item**.</span></span> <span data-ttu-id="1d77f-176">Seleccione **página HTML** (la encontrará en la subsección Web).</span><span class="sxs-lookup"><span data-stu-id="1d77f-176">Select  **HTML Page** (you will find it under the subsection Web).</span></span> <span data-ttu-id="1d77f-177">Asigne al archivo el nombre **default. html**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-177">Name the file **default.html**.</span></span> <span data-ttu-id="1d77f-178">Haga clic en **Agregar**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-178">Click **Add**.</span></span>

    ![Creación de la aplicación bot](images/AzureLabs-Lab312-06.png)

9.  <span data-ttu-id="1d77f-180">La lista de clases y objetos en el **Explorador de soluciones** debe ser similar a la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="1d77f-180">The list of classes / objects in the **Solution Explorer** should look like the image below.</span></span>

    ![Creación de la aplicación bot](images/AzureLabs-Lab312-07.png)

10. <span data-ttu-id="1d77f-182">Haga doble clic en la clase **ConversationContext** .</span><span class="sxs-lookup"><span data-stu-id="1d77f-182">Double-click on the **ConversationContext** class.</span></span> <span data-ttu-id="1d77f-183">Esta clase es responsable de conservar las variables que usa el bot para mantener el contexto de la conversación.</span><span class="sxs-lookup"><span data-stu-id="1d77f-183">This class is responsible for holding the variables used by the bot to maintain the context of the conversation.</span></span> <span data-ttu-id="1d77f-184">Estos valores de contexto de conversación se mantienen en una instancia de esta clase, porque cualquier instancia de la clase **MyBot** se actualizará cada vez que se reciba una actividad.</span><span class="sxs-lookup"><span data-stu-id="1d77f-184">These conversation context values are maintained in an instance of this class, because any instance of the **MyBot** class will refresh each time an activity is received.</span></span> <span data-ttu-id="1d77f-185">Agregue el código siguiente a la clase:</span><span class="sxs-lookup"><span data-stu-id="1d77f-185">Add the following code to the class:</span></span>

    ```csharp
    namespace MyBot
    {
        public static class ConversationContext
        {
            internal static string userName;

            internal static string userMsg;
        }
    }
    ```

11. <span data-ttu-id="1d77f-186">Haga doble clic en la clase **MyBot** .</span><span class="sxs-lookup"><span data-stu-id="1d77f-186">Double-click on the **MyBot** class.</span></span> <span data-ttu-id="1d77f-187">Esta clase hospedará los controladores a los que llama cualquier actividad entrante del cliente.</span><span class="sxs-lookup"><span data-stu-id="1d77f-187">This class will host the handlers called by any incoming activity from the customer.</span></span> <span data-ttu-id="1d77f-188">En esta clase agregará el código que se usa para crear la conversación entre el bot y el cliente.</span><span class="sxs-lookup"><span data-stu-id="1d77f-188">In this class you will add the code used to build the conversation between the bot and the customer.</span></span> <span data-ttu-id="1d77f-189">Como se mencionó anteriormente, una instancia de esta clase se inicializa cada vez que se recibe una actividad.</span><span class="sxs-lookup"><span data-stu-id="1d77f-189">As mentioned earlier, an instance of this class is initialized each time an activity is received.</span></span> <span data-ttu-id="1d77f-190">Agregue el código siguiente a esta clase:</span><span class="sxs-lookup"><span data-stu-id="1d77f-190">Add the following code to this class:</span></span>

    ```csharp
    using Microsoft.Bot;
    using Microsoft.Bot.Builder;
    using Microsoft.Bot.Schema;
    using System.Threading.Tasks;

    namespace MyBot
    {
        public class MyBot : IBot
        {       
            public async Task OnTurn(ITurnContext context)
            {
                ConversationContext.userMsg = context.Activity.Text;

                if (context.Activity.Type is ActivityTypes.Message)
                {
                    if (string.IsNullOrEmpty(ConversationContext.userName))
                    {
                        ConversationContext.userName = ConversationContext.userMsg;
                        await context.SendActivity($"Hello {ConversationContext.userName}. Looks like today it is going to rain. \nLuckily I have umbrellas and waterproof jackets to sell!");
                    }
                    else
                    {
                        if (ConversationContext.userMsg.Contains("how much"))
                        {
                            if (ConversationContext.userMsg.Contains("umbrella")) await context.SendActivity($"Umbrellas are $13.");
                            else if (ConversationContext.userMsg.Contains("jacket")) await context.SendActivity($"Waterproof jackets are $30.");
                            else await context.SendActivity($"Umbrellas are $13. \nWaterproof jackets are $30.");
                        }
                        else if (ConversationContext.userMsg.Contains("color") || ConversationContext.userMsg.Contains("colour"))
                        {
                            await context.SendActivity($"Umbrellas are black. \nWaterproof jackets are yellow.");
                        }
                        else
                        {
                            await context.SendActivity($"Sorry {ConversationContext.userName}. I did not understand the question");
                        }
                    }
                }
                else
                {

                    ConversationContext.userMsg = string.Empty;
                    ConversationContext.userName = string.Empty;
                    await context.SendActivity($"Welcome! \nI am the Weather Shop Bot \nWhat is your name?");
                }

            }
        }
    }
    ```

12. <span data-ttu-id="1d77f-191">Haga doble clic en la clase **Startup** .</span><span class="sxs-lookup"><span data-stu-id="1d77f-191">Double-click on the **Startup** class.</span></span> <span data-ttu-id="1d77f-192">Esta clase inicializará el bot.</span><span class="sxs-lookup"><span data-stu-id="1d77f-192">This class will initialize the bot.</span></span> <span data-ttu-id="1d77f-193">Agregue el código siguiente a la clase:</span><span class="sxs-lookup"><span data-stu-id="1d77f-193">Add the following code to the class:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Bot.Builder.BotFramework;
    using Microsoft.Bot.Builder.Integration.AspNet.Core;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;

    namespace MyBot
    {
    public class Startup
        {
            public IConfiguration Configuration { get; }

            public Startup(IHostingEnvironment env)
            {
                var builder = new ConfigurationBuilder()
                    .SetBasePath(env.ContentRootPath)
                    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
                    .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                    .AddEnvironmentVariables();
                Configuration = builder.Build();
            }

            // This method gets called by the runtime. Use this method to add services to the container.
            public void ConfigureServices(IServiceCollection services)
            {
                services.AddSingleton(_ => Configuration);
                services.AddBot<MyBot>(options =>
                {
                    options.CredentialProvider = new ConfigurationCredentialProvider(Configuration);
                });
            }

            // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
            public void Configure(IApplicationBuilder app, IHostingEnvironment env)
            {
                if (env.IsDevelopment())
                {
                    app.UseDeveloperExceptionPage();
                }

                app.UseDefaultFiles();
                app.UseStaticFiles();
                app.UseBotFramework();
            }
        }
    }
    ```

13. <span data-ttu-id="1d77f-194">Abra el archivo de clase de **programa** y compruebe que el código es el mismo que el siguiente:</span><span class="sxs-lookup"><span data-stu-id="1d77f-194">Open the **Program** class file and verify the code in it is the same as the following:</span></span>

    ```csharp
    using Microsoft.AspNetCore;
    using Microsoft.AspNetCore.Hosting;

    namespace MyBot
    {
        public class Program
        {
            public static void Main(string[] args)
            {
                BuildWebHost(args).Run();
            }

            public static IWebHost BuildWebHost(string[] args) =>
                WebHost.CreateDefaultBuilder(args)
                    .UseStartup<Startup>()
                    .Build();
        }
    }
    ```

14. <span data-ttu-id="1d77f-195">Recuerde guardar los cambios; para ello, vaya a **archivo** > **guardar todo**en la barra de herramientas de la parte superior de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1d77f-195">Remember to save your changes, to do so, go to **File** > **Save All**, from the toolbar at the top of Visual Studio.</span></span>

## <a name="chapter-2---create-the-azure-bot-service"></a><span data-ttu-id="1d77f-196">Capítulo 2: creación del Azure Bot Service</span><span class="sxs-lookup"><span data-stu-id="1d77f-196">Chapter 2 - Create the Azure Bot Service</span></span>

<span data-ttu-id="1d77f-197">Ahora que ha compilado el código para el bot, debe publicarlo en una instancia de *Web App bot* Service en Azure portal.</span><span class="sxs-lookup"><span data-stu-id="1d77f-197">Now that you have built the code for your bot, you have to publish it to an instance of the *Web App Bot* Service, on the Azure Portal.</span></span> <span data-ttu-id="1d77f-198">En este capítulo se muestra cómo crear y configurar el servicio bot en Azure y, después, publicar el código en él.</span><span class="sxs-lookup"><span data-stu-id="1d77f-198">This Chapter will show you how to create and configure the Bot Service on Azure and then publish your code to it.</span></span>

1.  <span data-ttu-id="1d77f-199">En primer lugar, inicie sesión en Azure portal https://portal.azure.com) (.</span><span class="sxs-lookup"><span data-stu-id="1d77f-199">First, log in to the Azure Portal (https://portal.azure.com).</span></span> 

    1. <span data-ttu-id="1d77f-200">Si aún no tiene una cuenta de Azure, tendrá que crear una.</span><span class="sxs-lookup"><span data-stu-id="1d77f-200">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="1d77f-201">Si sigue este tutorial en una situación de aula o de laboratorio, pregunte al instructor o a uno de los Proctors para obtener ayuda para configurar la nueva cuenta.</span><span class="sxs-lookup"><span data-stu-id="1d77f-201">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="1d77f-202">Una vez que haya iniciado sesión, haga clic en **crear un recurso** en la esquina superior izquierda, busque *Bot App bot*y haga clic en **entrar**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-202">Once you are logged in, click on **Create a resource** in the top left corner, and search for *Web App bot*, and click **Enter**.</span></span>

    ![Cree el Azure Bot Service](images/AzureLabs-Lab312-08.png)
 
3.  <span data-ttu-id="1d77f-204">La nueva página proporcionará una descripción de *Web App bot* Service.</span><span class="sxs-lookup"><span data-stu-id="1d77f-204">The new page will provide a description of the *Web App Bot* Service.</span></span> <span data-ttu-id="1d77f-205">En la parte inferior izquierda de esta página, seleccione el botón **crear** para crear una asociación con este servicio.</span><span class="sxs-lookup"><span data-stu-id="1d77f-205">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Cree el Azure Bot Service](images/AzureLabs-Lab312-09.png)
 
4.  <span data-ttu-id="1d77f-207">Una vez que haya hecho clic en **crear**:</span><span class="sxs-lookup"><span data-stu-id="1d77f-207">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="1d77f-208">Inserte el **nombre** que desee para esta instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="1d77f-208">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="1d77f-209">Seleccione una **suscripción**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-209">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="1d77f-210">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="1d77f-210">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="1d77f-211">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="1d77f-211">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="1d77f-212">Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos cursos) en un grupo de recursos común).</span><span class="sxs-lookup"><span data-stu-id="1d77f-212">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="1d77f-213">Si desea leer más información sobre los grupos de recursos de Azure, [siga este vínculo.](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="1d77f-213">If you wish to read more about Azure Resource Groups, [please follow this link](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4. <span data-ttu-id="1d77f-214">Determine la ubicación del grupo de recursos (si va a crear un nuevo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="1d77f-214">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="1d77f-215">Idealmente, la ubicación estará en la región donde se ejecutará la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1d77f-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="1d77f-216">Algunos recursos de Azure solo están disponibles en determinadas regiones.</span><span class="sxs-lookup"><span data-stu-id="1d77f-216">Some Azure assets are only available in certain regions.</span></span>
    5. <span data-ttu-id="1d77f-217">Seleccione el **plan de tarifa** que sea adecuado para usted; si es la primera vez que crea un servicio *Web App bot* , debe estar disponible un nivel gratis (denominado F0)</span><span class="sxs-lookup"><span data-stu-id="1d77f-217">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Web App Bot* Service, a free tier (named F0) should be available to you</span></span>
    6. <span data-ttu-id="1d77f-218">El nombre de la **aplicación** puede dejarse igual que el *nombre del bot*.</span><span class="sxs-lookup"><span data-stu-id="1d77f-218">**App name** can just be left the same as the *Bot name*.</span></span> 
    7. <span data-ttu-id="1d77f-219">Deje la *plantilla de bot* como **básicaC#()** .</span><span class="sxs-lookup"><span data-stu-id="1d77f-219">Leave the *Bot template* as **Basic (C#)**.</span></span>
    8. <span data-ttu-id="1d77f-220">El *plan de App Service/ubicación* debe haberse rellenado automáticamente para su cuenta.</span><span class="sxs-lookup"><span data-stu-id="1d77f-220">*App service plan/Location* should have been auto-filled for your account.</span></span>
    9. <span data-ttu-id="1d77f-221">Establezca la **Azure Storage** que desea usar para hospedar el bot.</span><span class="sxs-lookup"><span data-stu-id="1d77f-221">Set the **Azure Storage** that you wish to use to host your Bot.</span></span> <span data-ttu-id="1d77f-222">Si aún no tiene una, puede crearla aquí.</span><span class="sxs-lookup"><span data-stu-id="1d77f-222">If you dont have one already, you can create it here.</span></span>
    10. <span data-ttu-id="1d77f-223">También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.</span><span class="sxs-lookup"><span data-stu-id="1d77f-223">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    11. <span data-ttu-id="1d77f-224">Haga clic en crear.</span><span class="sxs-lookup"><span data-stu-id="1d77f-224">Click Create.</span></span>
 
        ![Cree el Azure Bot Service](images/AzureLabs-Lab312-10.png)

5.  <span data-ttu-id="1d77f-226">Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="1d77f-226">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="1d77f-227">Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="1d77f-227">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![Cree el Azure Bot Service](images/AzureLabs-Lab312-11.png) 
 
7.  <span data-ttu-id="1d77f-229">Haga clic en la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="1d77f-229">Click on the notification to explore your new Service instance.</span></span> 

    ![Cree el Azure Bot Service](images/AzureLabs-Lab312-12.png)
 
8. <span data-ttu-id="1d77f-231">Haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="1d77f-231">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="1d77f-232">Se le dirigirá a la nueva instancia de servicio de Azure.</span><span class="sxs-lookup"><span data-stu-id="1d77f-232">You will be taken to your new Azure Service instance.</span></span> 

    ![Cree el Azure Bot Service](images/AzureLabs-Lab312-13.png)
 
9.  <span data-ttu-id="1d77f-234">En este momento, debe configurar una característica denominada **Direct line** para permitir que la aplicación cliente se comunique con este servicio de bot.</span><span class="sxs-lookup"><span data-stu-id="1d77f-234">At this point you need to setup a feature called **Direct Line** to allow your client application to communicate with this Bot Service.</span></span> <span data-ttu-id="1d77f-235">Haga clic en **canales**y, a continuación, en la sección **Agregar un canal destacado** , haga clic en **configurar canal de línea directa**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-235">Click on **Channels**, then in the **Add a featured channel** section, click on **Configure Direct Line channel**.</span></span>

    ![Cree el Azure Bot Service](images/AzureLabs-Lab312-14.png)

10. <span data-ttu-id="1d77f-237">En esta página encontrará las **claves secretas** que permitirán que la aplicación cliente se autentique con el bot.</span><span class="sxs-lookup"><span data-stu-id="1d77f-237">In this page you will find the **Secret keys** that will allow your client app to authenticate with the bot.</span></span> <span data-ttu-id="1d77f-238">Haga clic en el botón **Mostrar** y realice una copia de una de las claves mostradas, ya que lo necesitará más adelante en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="1d77f-238">Click on the **Show** button and take a copy of one of the displayed Keys, as you will need this later in your project.</span></span> 

    ![Cree el Azure Bot Service](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a><span data-ttu-id="1d77f-240">Capítulo 3: publicación del bot en Azure Web App bot Service</span><span class="sxs-lookup"><span data-stu-id="1d77f-240">Chapter 3 – Publish the Bot to the Azure Web App Bot Service</span></span>

<span data-ttu-id="1d77f-241">Ahora que el servicio está listo, debe publicar el código de bot que creó previamente en el servicio bot de aplicación web recién creado.</span><span class="sxs-lookup"><span data-stu-id="1d77f-241">Now that your Service is ready, you need to publish your Bot code, that you built previously, to your newly created Web App Bot Service.</span></span>

> [!NOTE] 
> <span data-ttu-id="1d77f-242">Tendrá que publicar su bot en el servicio de Azure cada vez que realice cambios en la solución o el código de bot.</span><span class="sxs-lookup"><span data-stu-id="1d77f-242">You will have to publish your Bot to the Azure Service every time you make changes to the Bot solution / code.</span></span>

1.  <span data-ttu-id="1d77f-243">Vuelva a la solución de Visual Studio que creó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1d77f-243">Go back to your Visual Studio Solution that you created previously.</span></span> 
2.  <span data-ttu-id="1d77f-244">Haga clic con el botón derecho en el proyecto **MyBot** , en el **Explorador de soluciones**y, a continuación, haga clic en **publicar**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-244">Right-click on your **MyBot** project, in the **Solution Explorer**, then click on **Publish**.</span></span>

    ![Publicar el bot en el servicio de bot de aplicaciones Web de Azure](images/AzureLabs-Lab312-16.png)

3.  <span data-ttu-id="1d77f-246">En la página *seleccionar un destino de publicación* , haga clic en **App Service**y, a continuación, **Seleccione existente**; por último, haga clic en **crear perfil** (puede que tenga que hacer clic en la flecha desplegable junto al botón *publicar* , si no está visible).</span><span class="sxs-lookup"><span data-stu-id="1d77f-246">On the *Pick a publish target* page, click **App Service**, then **Select Existing**, lastly click on **Create Profile** (you may need to click on the dropdown arrow alongside the *Publish* button, if this is not visible).</span></span>

    ![Publicar el bot en el servicio de bot de aplicaciones Web de Azure](images/AzureLabs-Lab312-17.png)

4. <span data-ttu-id="1d77f-248">Si aún no ha iniciado sesión en su cuenta de Microsoft, tendrá que hacerlo aquí.</span><span class="sxs-lookup"><span data-stu-id="1d77f-248">If you are not yet logged in into your Microsoft Account, you have to do it here.</span></span>
5. <span data-ttu-id="1d77f-249">En la página **publicar** , verá que tiene que establecer la misma **suscripción** que usó para la creación del servicio *Web App bot* .</span><span class="sxs-lookup"><span data-stu-id="1d77f-249">On the **Publish** page you will find you have to set the same **Subscription** that you used for the *Web App Bot* Service creation.</span></span> <span data-ttu-id="1d77f-250">A continuación, establezca la **vista** como **grupo de recursos** y, en la lista desplegable de la estructura de carpetas, seleccione el **grupo de recursos** que creó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1d77f-250">Then set the **View** as **Resource Group** and, in the drop down folder structure, select the **Resource Group** you have created previously.</span></span> <span data-ttu-id="1d77f-251">Haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-251">Click **OK**.</span></span> 

    ![Publicar el bot en el servicio de bot de aplicaciones Web de Azure](images/AzureLabs-Lab312-18.png)

6.  <span data-ttu-id="1d77f-253">Ahora, haga clic en el botón **publicar** y espere a que se publique el bot (puede tardar unos minutos).</span><span class="sxs-lookup"><span data-stu-id="1d77f-253">Now click on the **Publish** button, and wait for the Bot to be published (it might take a few minutes).</span></span>

    ![Publicar el bot en el servicio de bot de aplicaciones Web de Azure](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a><span data-ttu-id="1d77f-255">Capítulo 4: configurar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="1d77f-255">Chapter 4 – Set up the Unity project</span></span>

<span data-ttu-id="1d77f-256">Lo siguiente es una configuración típica para desarrollar con la realidad mixta y, como tal, es una buena plantilla para otros proyectos.</span><span class="sxs-lookup"><span data-stu-id="1d77f-256">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="1d77f-257">Abra *Unity* y haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-257">Open *Unity* and click **New**.</span></span> 

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-20.png)

2.  <span data-ttu-id="1d77f-259">Ahora tendrá que proporcionar un nombre de proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="1d77f-259">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="1d77f-260">Inserte el **Bot de Hololens**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-260">Insert **Hololens Bot**.</span></span> <span data-ttu-id="1d77f-261">Asegúrese de que la plantilla de proyecto está establecida en **3D**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-261">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="1d77f-262">Establezca la **Ubicación** en algún lugar adecuado para usted (Recuerde que, más cerca de los directorios raíz es mejor).</span><span class="sxs-lookup"><span data-stu-id="1d77f-262">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="1d77f-263">A continuación, haga clic en **crear proyecto**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-263">Then, click **Create project**.</span></span>

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-21.png)

3.  <span data-ttu-id="1d77f-265">Con Unity abierto, merece la pena comprobar que el **Editor** de scripts predeterminado está establecido en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-265">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="1d77f-266">Vaya a **editar > preferencias** y, a continuación, en la nueva ventana, vaya a **herramientas externas**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-266">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="1d77f-267">Cambie el **Editor de script externo** a **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-267">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="1d77f-268">Cierre la ventana **preferencias** .</span><span class="sxs-lookup"><span data-stu-id="1d77f-268">Close the **Preferences** window.</span></span>

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-22.png)

4.  <span data-ttu-id="1d77f-270">A continuación, vaya a **archivo > configuración de compilación** y seleccione **plataforma universal de Windows**y, después, haga clic en el botón **cambiar plataforma** para aplicar la selección.</span><span class="sxs-lookup"><span data-stu-id="1d77f-270">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-23.png)

5.  <span data-ttu-id="1d77f-272">Mientras sigue en el **archivo > la configuración de compilación** y asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="1d77f-272">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="1d77f-273">El **dispositivo de destino** está establecido en **Hololens**</span><span class="sxs-lookup"><span data-stu-id="1d77f-273">**Target Device** is set to **Hololens**</span></span>

        > <span data-ttu-id="1d77f-274">Para los auriculares envolventes, establezca el **dispositivo de destino** en *cualquier dispositivo*.</span><span class="sxs-lookup"><span data-stu-id="1d77f-274">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2.  <span data-ttu-id="1d77f-275">El **tipo de compilación** se establece en **D3D**</span><span class="sxs-lookup"><span data-stu-id="1d77f-275">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="1d77f-276">**SDK** está establecido en la **versión más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="1d77f-276">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="1d77f-277">La **versión de Visual Studio** está establecida en la **más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="1d77f-277">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="1d77f-278">**Compilar y ejecutar** está establecido en **equipo local**</span><span class="sxs-lookup"><span data-stu-id="1d77f-278">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="1d77f-279">Guarde la escena y agréguela a la compilación.</span><span class="sxs-lookup"><span data-stu-id="1d77f-279">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="1d77f-280">Para ello, seleccione **Agregar escenas abiertas**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-280">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="1d77f-281">Aparecerá una ventana de guardar.</span><span class="sxs-lookup"><span data-stu-id="1d77f-281">A save window will appear.</span></span>
        
            ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-24.png)

        2. <span data-ttu-id="1d77f-283">Cree una nueva carpeta para este, y en cualquier momento, en el futuro, seleccione el botón **nueva carpeta** para crear una nueva carpeta, asígneleel nombre Scenes.</span><span class="sxs-lookup"><span data-stu-id="1d77f-283">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

             ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-25.png)

        3. <span data-ttu-id="1d77f-285">Abra la carpeta Scenes recién creada y, a continuación, en el campo *nombre de archivo*:, escriba **BotScene**y, a continuación, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-285">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **BotScene**, then click on **Save**.</span></span>

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-26.png)

    7. <span data-ttu-id="1d77f-287">El resto de la configuración, en la **configuración de compilación**, debe dejarse como predeterminada por ahora.</span><span class="sxs-lookup"><span data-stu-id="1d77f-287">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6. <span data-ttu-id="1d77f-288">En la ventana *configuración de compilación* , haga clic en el botón Configuración del **reproductor** ; se abrirá el panel relacionado en el espacio donde se encuentra el *Inspector* .</span><span class="sxs-lookup"><span data-stu-id="1d77f-288">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-27.png)

7. <span data-ttu-id="1d77f-290">En este panel, deben comprobarse algunas opciones de configuración:</span><span class="sxs-lookup"><span data-stu-id="1d77f-290">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="1d77f-291">En la pestaña **otros valores** :</span><span class="sxs-lookup"><span data-stu-id="1d77f-291">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="1d77f-292">La **versión de scripting en tiempo de ejecución** debe ser **experimental (equivalente en net 4,6)** ; cambiar esto requerirá un reinicio del editor.</span><span class="sxs-lookup"><span data-stu-id="1d77f-292">**Scripting Runtime Version** should be **Experimental (NET 4.6 Equivalent)**; changing this will require a restart of the Editor.</span></span>
        2. <span data-ttu-id="1d77f-293">El **back-end** de scripting debe ser **.net**</span><span class="sxs-lookup"><span data-stu-id="1d77f-293">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="1d77f-294">El **nivel de compatibilidad de API** debe ser **.net 4,6**</span><span class="sxs-lookup"><span data-stu-id="1d77f-294">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-28.png)
      
    2. <span data-ttu-id="1d77f-296">En la pestaña **configuración de publicación** , en **capacidades**, seleccione:</span><span class="sxs-lookup"><span data-stu-id="1d77f-296">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="1d77f-297">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="1d77f-297">**InternetClient**</span></span>
        - <span data-ttu-id="1d77f-298">**Micrófono**</span><span class="sxs-lookup"><span data-stu-id="1d77f-298">**Microphone**</span></span>

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-29.png)

    3. <span data-ttu-id="1d77f-300">Más abajo en el panel, en la **configuración de XR** (se encuentra debajo de **configuración de publicación**), tick **Virtual Reality compatible**, asegúrese de que se agrega el **SDK de Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="1d77f-300">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-30.png)

8.  <span data-ttu-id="1d77f-302">De nuevo en la *configuración de compilación* , los proyectos de _Unity C#_  ya no están atenuados; Marque la casilla situada junto a este.</span><span class="sxs-lookup"><span data-stu-id="1d77f-302">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="1d77f-303">Cierre la ventana Configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="1d77f-303">Close the Build Settings window.</span></span>
10. <span data-ttu-id="1d77f-304">Guarde la escena y el proyecto (**archivo > guardar la escena o el archivo > guardar proyecto**).</span><span class="sxs-lookup"><span data-stu-id="1d77f-304">Save your scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-5--camera-setup"></a><span data-ttu-id="1d77f-305">Capítulo 5: configuración de cámara</span><span class="sxs-lookup"><span data-stu-id="1d77f-305">Chapter 5 – Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1d77f-306">Si desea omitir el componente de *configuración de Unity* de este curso y continuar directamente en el código, no dude en descargar este [paquete Azure-Mr-312-package. unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), impórtelo en el proyecto como un [**paquete personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)y, después, continúe desde [ Capítulo 7](#chapter-8--create-the-botobjects-class).</span><span class="sxs-lookup"><span data-stu-id="1d77f-306">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-312-Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 7](#chapter-8--create-the-botobjects-class).</span></span>

1.  <span data-ttu-id="1d77f-307">En el *Panel jerarquía*, seleccione la **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-307">In the *Hierarchy panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="1d77f-308">Una vez seleccionado, podrá ver todos los componentes de la **cámara principal** en el *panel del inspector*.</span><span class="sxs-lookup"><span data-stu-id="1d77f-308">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector panel*.</span></span>

    1. <span data-ttu-id="1d77f-309">El **objeto de cámara** se debe llamar **cámara principal** (tenga en cuenta la ortografía)</span><span class="sxs-lookup"><span data-stu-id="1d77f-309">The **Camera object** must be named **Main Camera** (note the spelling)</span></span>
    2. <span data-ttu-id="1d77f-310">La **etiqueta** de cámara principal se debe establecer en **MainCamera** (tenga en cuenta la ortografía)</span><span class="sxs-lookup"><span data-stu-id="1d77f-310">The Main Camera **Tag** must be set to **MainCamera** (note the spelling)</span></span>
    3. <span data-ttu-id="1d77f-311">Asegúrese de que la **posición de transformación** está establecida en **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="1d77f-311">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="1d77f-312">Establezca **marcas** de borrado en **color sólido**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-312">Set **Clear Flags** to **Solid Color**.</span></span>
    5. <span data-ttu-id="1d77f-313">Establezca el color de **fondo** del componente de la cámara en **negro, alfa 0 (código hexadecimal: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="1d77f-313">Set the **Background** Color of the Camera component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

    ![Configuración de la cámara](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a><span data-ttu-id="1d77f-315">Capítulo 6: importar la biblioteca Newtonsoft</span><span class="sxs-lookup"><span data-stu-id="1d77f-315">Chapter 6 – Import the Newtonsoft library</span></span>

<span data-ttu-id="1d77f-316">Para ayudarle a deserializar y serializar los objetos recibidos y enviados al servicio bot, debe descargar la biblioteca **Newtonsoft** .</span><span class="sxs-lookup"><span data-stu-id="1d77f-316">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the **Newtonsoft** library.</span></span> <span data-ttu-id="1d77f-317">Aquí encontrará una [versión compatible que ya está organizada con la estructura de carpetas de Unity correcta](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="1d77f-317">You will find a [compatible version already organized with the correct Unity folder structure here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="1d77f-318">Para importar la biblioteca de Newtonsoft en el proyecto, use el paquete de Unity que se incluía con este curso.</span><span class="sxs-lookup"><span data-stu-id="1d77f-318">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="1d77f-319">Agregue el *. unitypackage Tools* a Unity mediante la opción > de menú de paquetes**importar paquete** > **personalizado** de paquetes.</span><span class="sxs-lookup"><span data-stu-id="1d77f-319">Add the *.unitypackage* to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

    ![Importar la biblioteca Newtonsoft](images/AzureLabs-Lab312-34.png)

2.  <span data-ttu-id="1d77f-321">En el cuadro **importar paquete Unity** que aparece, asegúrese de que todo lo que hay en **Complementos** (y incluido) está seleccionado.</span><span class="sxs-lookup"><span data-stu-id="1d77f-321">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Importar la biblioteca Newtonsoft](images/AzureLabs-Lab312-35.png)

3.  <span data-ttu-id="1d77f-323">Haga clic en el botón **importar** para agregar los elementos al proyecto.</span><span class="sxs-lookup"><span data-stu-id="1d77f-323">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="1d77f-324">Vaya a la carpeta **Newtonsoft** en **Complementos** en la vista de proyecto y seleccione el complemento Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="1d77f-324">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the Newtonsoft plugin.</span></span>

    ![](images/AzureLabs-Lab312-35b.png)

5.  <span data-ttu-id="1d77f-325">Con el complemento Newtonsoft seleccionado, asegúrese de que **cualquier plataforma** esté desactivada, asegúrese de que **WSAPlayer** también está desactivado y haga clic en **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-325">With the Newtonsoft plugin selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="1d77f-326">Esto es solo para confirmar que los archivos están configurados correctamente.</span><span class="sxs-lookup"><span data-stu-id="1d77f-326">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > <span data-ttu-id="1d77f-327">Al marcar estos complementos, se configuran para que solo se usen en el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="1d77f-327">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="1d77f-328">Hay un conjunto diferente de ellos en la carpeta WSA que se usará después de exportar el proyecto desde Unity.</span><span class="sxs-lookup"><span data-stu-id="1d77f-328">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="1d77f-329">A continuación, debe abrir la carpeta **WSA** , dentro de la carpeta **Newtonsoft**</span><span class="sxs-lookup"><span data-stu-id="1d77f-329">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="1d77f-330">Verá una copia del mismo archivo que acaba de configurar.</span><span class="sxs-lookup"><span data-stu-id="1d77f-330">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="1d77f-331">Seleccione el archivo y, a continuación, en el inspector, asegúrese de que</span><span class="sxs-lookup"><span data-stu-id="1d77f-331">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="1d77f-332">**Cualquier plataforma** está desactivada</span><span class="sxs-lookup"><span data-stu-id="1d77f-332">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="1d77f-333">**solo** **WSAPlayer** está **activado**</span><span class="sxs-lookup"><span data-stu-id="1d77f-333">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="1d77f-334">No **procesar** está **activado**</span><span class="sxs-lookup"><span data-stu-id="1d77f-334">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a><span data-ttu-id="1d77f-335">Capítulo 7: creación de BotTag</span><span class="sxs-lookup"><span data-stu-id="1d77f-335">Chapter 7 – Create the BotTag</span></span>

1.  <span data-ttu-id="1d77f-336">Cree un nuevo objeto de **etiqueta** denominado **BotTag**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-336">Create a new **Tag** object called **BotTag**.</span></span> <span data-ttu-id="1d77f-337">Seleccione la cámara principal en la escena.</span><span class="sxs-lookup"><span data-stu-id="1d77f-337">Select the Main Camera in the scene.</span></span> <span data-ttu-id="1d77f-338">Haga clic en el menú desplegable etiqueta en el panel Inspector.</span><span class="sxs-lookup"><span data-stu-id="1d77f-338">Click on the Tag drop down menu in the Inspector panel.</span></span> <span data-ttu-id="1d77f-339">Haga clic en **Agregar etiqueta**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-339">Click on **Add Tag**.</span></span>

    ![Configuración de la cámara](images/AzureLabs-Lab312-32.png)
 
2.  <span data-ttu-id="1d77f-341">Haga clic en **+** el símbolo.</span><span class="sxs-lookup"><span data-stu-id="1d77f-341">Click on the **+** symbol.</span></span> <span data-ttu-id="1d77f-342">Asigne a la nueva **etiqueta** el nombre **BotTag**, *Guardar*.</span><span class="sxs-lookup"><span data-stu-id="1d77f-342">Name the new **Tag** as **BotTag**, *Save*.</span></span>

    ![Configuración de la cámara](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> <span data-ttu-id="1d77f-344">**No** aplique el **BotTag** a la cámara principal.</span><span class="sxs-lookup"><span data-stu-id="1d77f-344">**Do not** apply the **BotTag** to the Main Camera.</span></span> <span data-ttu-id="1d77f-345">Si ha hecho esto accidentalmente, asegúrese de volver a cambiar la etiqueta de cámara principal a *MainCamera*.</span><span class="sxs-lookup"><span data-stu-id="1d77f-345">If you have accidentally done this, make sure to change the Main Camera tag back to *MainCamera*.</span></span>

## <a name="chapter-8--create-the-botobjects-class"></a><span data-ttu-id="1d77f-346">Capítulo 8: creación de la clase BotObjects</span><span class="sxs-lookup"><span data-stu-id="1d77f-346">Chapter 8 – Create the BotObjects class</span></span>

<span data-ttu-id="1d77f-347">El primer script que necesita crear es la clase **BotObjects** , que es una clase vacía creada para que se pueda almacenar una serie de otros objetos de clase en el mismo script y que otros scripts de la escena tengan acceso a ellos.</span><span class="sxs-lookup"><span data-stu-id="1d77f-347">The first script you need to create is the **BotObjects** class, which is an empty class created so that a series of other class objects can be stored within the same script and accessed by other scripts in the scene.</span></span>

<span data-ttu-id="1d77f-348">La creación de esta clase es puramente una opción arquitectónica, en su lugar, estos objetos se pueden hospedar en el script de bot que creará más adelante en este curso.</span><span class="sxs-lookup"><span data-stu-id="1d77f-348">The creation of this class is purely an architectural choice, these objects could instead be hosted in the Bot script that you will create later in this course.</span></span>

<span data-ttu-id="1d77f-349">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="1d77f-349">To create this class:</span></span> 

1.  <span data-ttu-id="1d77f-350">Haga clic con el botón derecho en el *panel Proyecto*y, a continuación, **cree > carpeta**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-350">Right-click in the *Project panel*, then **Create > Folder**.</span></span> <span data-ttu-id="1d77f-351">Asigne a lacarpeta el nombre scripts.</span><span class="sxs-lookup"><span data-stu-id="1d77f-351">Name the folder **Scripts**.</span></span> 

    ![Crear carpeta de scripts.](images/AzureLabs-Lab312-36.png)

2.  <span data-ttu-id="1d77f-353">Haga doble clic en la carpeta scripts para abrirla.</span><span class="sxs-lookup"><span data-stu-id="1d77f-353">Double-click on the **Scripts** folder to open it.</span></span> <span data-ttu-id="1d77f-354">Después, en esa carpeta, haga clic con el botón derecho y seleccione **crear > C# script**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-354">Then within that folder, right-click, and select **Create > C# Script**.</span></span> <span data-ttu-id="1d77f-355">Asigne al script el nombre **BotObjects**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-355">Name the script **BotObjects**.</span></span> 

3.  <span data-ttu-id="1d77f-356">Haga doble clic en el nuevo script **BotObjects** para abrirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-356">Double-click on the new **BotObjects** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="1d77f-357">Elimine el contenido del script y reemplácelo por el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="1d77f-357">Delete the content of the script and replace it with the following code:</span></span>

    ```csharp
    using System;
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public class BotObjects : MonoBehaviour{}

    /// <summary>
    /// Object received when first opening a conversation
    /// </summary>
    [Serializable]
    public class ConversationObject
    {
        public string ConversationId;
        public string token;
        public string expires_in;
        public string streamUrl;
        public string referenceGrammarId;
    }

    /// <summary>
    /// Object including all Activities
    /// </summary>
    [Serializable]
    public class ActivitiesRootObject
    {
        public List<Activity> activities { get; set; }
        public string watermark { get; set; }
    }
    [Serializable]
    public class Conversation
    {
        public string id { get; set; }
    }
    [Serializable]
    public class From
    {
        public string id { get; set; }
        public string name { get; set; }
    }
    [Serializable]
    public class Activity
    {
        public string type { get; set; }
        public string channelId { get; set; }
        public Conversation conversation { get; set; }
        public string id { get; set; }
        public From from { get; set; }
        public string text { get; set; }
        public string textFormat { get; set; }
        public DateTime timestamp { get; set; }
        public string serviceUrl { get; set; }
    }
    ```

6.  <span data-ttu-id="1d77f-358">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="1d77f-358">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--create-the-gazeinput-class"></a><span data-ttu-id="1d77f-359">Capítulo 9: creación de la clase GazeInput</span><span class="sxs-lookup"><span data-stu-id="1d77f-359">Chapter 9 – Create the GazeInput class</span></span>

<span data-ttu-id="1d77f-360">La clase siguiente que va a crear es la clase **GazeInput** .</span><span class="sxs-lookup"><span data-stu-id="1d77f-360">The next class you are going to create is the **GazeInput** class.</span></span> <span data-ttu-id="1d77f-361">Esta clase es responsable de:</span><span class="sxs-lookup"><span data-stu-id="1d77f-361">This class is responsible for:</span></span>

- <span data-ttu-id="1d77f-362">Crear un cursor que represente la *mirada* al jugador.</span><span class="sxs-lookup"><span data-stu-id="1d77f-362">Creating a cursor that will represent the *gaze* of the player.</span></span>
- <span data-ttu-id="1d77f-363">Detección de objetos detectados por la mirada del reproductor y que contiene una referencia a los objetos detectados.</span><span class="sxs-lookup"><span data-stu-id="1d77f-363">Detecting objects hit by the gaze of the player, and holding a reference to detected objects.</span></span>

<span data-ttu-id="1d77f-364">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="1d77f-364">To create this class:</span></span> 

1.  <span data-ttu-id="1d77f-365">Vaya a la carpeta scripts que creó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1d77f-365">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="1d77f-366">Haga clic con el botón derecho dentro de la carpeta, **cree > C# script**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-366">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="1d77f-367">Llame al script **GazeInput**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-367">Call the script **GazeInput**.</span></span> 
3.  <span data-ttu-id="1d77f-368">Haga doble clic en el nuevo script **GazeInput** para abrirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-368">Double-click on the new **GazeInput** script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="1d77f-369">Inserte la siguiente línea justo encima del nombre de clase:</span><span class="sxs-lookup"><span data-stu-id="1d77f-369">Insert the following line right on top of the class name:</span></span>

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  <span data-ttu-id="1d77f-370">A continuación, agregue las siguientes variables dentro de la clase **GazeInput** , sobre el método **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="1d77f-370">Then add the following variables inside the **GazeInput** class, above the **Start()** method:</span></span>

    ```csharp
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "BotTag";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject _oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  <span data-ttu-id="1d77f-371">Debe agregarse el código para el método **Start ()** .</span><span class="sxs-lookup"><span data-stu-id="1d77f-371">Code for **Start()** method should be added.</span></span> <span data-ttu-id="1d77f-372">Se llamará cuando se inicialice la clase:</span><span class="sxs-lookup"><span data-stu-id="1d77f-372">This will be called when the class initializes:</span></span>

    ```csharp
        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  <span data-ttu-id="1d77f-373">Implemente un método que creará instancias y configurará el cursor de miración:</span><span class="sxs-lookup"><span data-stu-id="1d77f-373">Implement a method that will instantiate and setup the gaze cursor:</span></span> 

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it does not block Raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

8.  <span data-ttu-id="1d77f-374">Implemente los métodos que configurarán el Raycast desde la cámara principal y realizarán un seguimiento del objeto con el foco actual.</span><span class="sxs-lookup"><span data-stu-id="1d77f-374">Implement the methods that will setup the Raycast from the Main Camera and will keep track of the current focused object.</span></span>

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        internal virtual void Update()
        {
            _gazeOrigin = Camera.main.transform.position;

            _gazeDirection = Camera.main.transform.forward;

            UpdateRaycast();
        }


        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag))
                {
                    // Provide the OnGazeExited event.
                    _oldFocusedObject.SendMessage("OnGazeExited", 
                        SendMessageOptions.DontRequireReceiver);
                }
            }
        }


        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
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

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the OnGazeEntered event.
                        FocusedObject.SendMessage("OnGazeEntered",
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```
 
9.  <span data-ttu-id="1d77f-375">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="1d77f-375">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10--create-the-bot-class"></a><span data-ttu-id="1d77f-376">Capítulo 10: crear la clase bot</span><span class="sxs-lookup"><span data-stu-id="1d77f-376">Chapter 10 – Create the Bot class</span></span>

<span data-ttu-id="1d77f-377">El script que va a crear ahora se llama **Bot**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-377">The script you are going to create now is called **Bot**.</span></span> <span data-ttu-id="1d77f-378">Esta es la clase principal de la aplicación, que almacena:</span><span class="sxs-lookup"><span data-stu-id="1d77f-378">This is the core class of your application, it stores:</span></span> 

- <span data-ttu-id="1d77f-379">Sus credenciales de bot de aplicación Web</span><span class="sxs-lookup"><span data-stu-id="1d77f-379">Your Web App Bot credentials</span></span>
- <span data-ttu-id="1d77f-380">El método que recopila los comandos de voz de usuario.</span><span class="sxs-lookup"><span data-stu-id="1d77f-380">The method that collects the user voice commands</span></span>
- <span data-ttu-id="1d77f-381">El método necesario para iniciar conversaciones con el bot de la aplicación Web</span><span class="sxs-lookup"><span data-stu-id="1d77f-381">The method necessary to initiate conversations with your Web App Bot</span></span> 
- <span data-ttu-id="1d77f-382">El método necesario para enviar mensajes al bot de la aplicación Web</span><span class="sxs-lookup"><span data-stu-id="1d77f-382">The method necessary to send messages to your Web App Bot</span></span> 

<span data-ttu-id="1d77f-383">Para enviar mensajes al servicio bot, la corutina **SendMessageToBot ()** creará una actividad, que es un objeto reconocido por el marco bot como datos enviados por el usuario.</span><span class="sxs-lookup"><span data-stu-id="1d77f-383">To send messages to the Bot Service, the **SendMessageToBot()** coroutine will build an activity, which is an object recognized by the Bot Framework as data sent by the user.</span></span> 
 
<span data-ttu-id="1d77f-384">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="1d77f-384">To create this class:</span></span> 

1. <span data-ttu-id="1d77f-385">Haga doble clic en la carpeta scripts para abrirla.</span><span class="sxs-lookup"><span data-stu-id="1d77f-385">Double-click on the **Scripts** folder, to open it.</span></span> 
2. <span data-ttu-id="1d77f-386">Haga clic con el botón derecho en la carpeta scripts y haga clic en **crear > C# script**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-386">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="1d77f-387">Asigne al **Bot**el nombre de la secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="1d77f-387">Name the script **Bot**.</span></span> 
3. <span data-ttu-id="1d77f-388">Haga doble clic en el nuevo script para abrirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1d77f-388">Double-click on the new script to open it with Visual Studio.</span></span>
4. <span data-ttu-id="1d77f-389">Actualice los espacios de nombres para que sean los mismos que los que se indican a continuación, en la parte superior de la clase **Bot** :</span><span class="sxs-lookup"><span data-stu-id="1d77f-389">Update the namespaces to be the same as the following, at the top of the **Bot** class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. <span data-ttu-id="1d77f-390">Dentro de la clase **Bot** , agregue las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="1d77f-390">Inside the **Bot** class add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static Bot Instance;

        /// <summary>
        /// Material of the sphere representing the Bot in the scene
        /// </summary>
        internal Material botMaterial;

        /// <summary>
        /// Speech recognizer class reference, which will convert speech to text.
        /// </summary>
        private DictationRecognizer dictationRecognizer;

        /// <summary>
        /// Use this variable to identify the Bot Id
        /// Can be any value
        /// </summary>
        private string botId = "MRBotId";

        /// <summary>
        /// Use this variable to identify the Bot Name
        /// Can be any value
        /// </summary>
        private string botName = "MRBotName";

        /// <summary>
        /// The Bot Secret key found on the Web App Bot Service on the Azure Portal
        /// </summary>
        private string botSecret = "-- Add your Secret Key here --"; 

        /// <summary>
        /// Bot Endpoint, v4 Framework uses v3 endpoint at this point in time
        /// </summary>
        private string botEndpoint = "https://directline.botframework.com/v3/directline";

        /// <summary>
        /// The conversation object reference
        /// </summary>
        private ConversationObject conversation;

        /// <summary>
        /// Bot states to regulate the application flow
        /// </summary>
        internal enum BotState {ReadyToListen, Listening, Processing}

        /// <summary>
        /// Flag for the Bot state
        /// </summary>
        internal BotState botState;

        /// <summary>
        /// Flag for the conversation status
        /// </summary>
        internal bool conversationStarted = false;
    ```

    > [!NOTE] 
    > <span data-ttu-id="1d77f-391">Asegúrese de insertar la **clave de bot secreta** en la variable **botSecret** .</span><span class="sxs-lookup"><span data-stu-id="1d77f-391">Make sure you insert your **Bot Secret Key** into the **botSecret** variable.</span></span> <span data-ttu-id="1d77f-392">Habrá anotado la **clave secreta de bot** al principio de este curso, en el  **[capítulo 2](#chapter-2---create-the-azure-bot-service), paso 10**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-392">You will have noted your **Bot Secret Key** at the beginning of this course, in **[Chapter 2](#chapter-2---create-the-azure-bot-service), step 10**.</span></span>

7. <span data-ttu-id="1d77f-393">Ahora es necesario agregar el código para el **activo ()** y el **Inicio ()** .</span><span class="sxs-lookup"><span data-stu-id="1d77f-393">Code for **Awake()** and **Start()** now needs to be added.</span></span> 

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start()
        {
            botState = BotState.ReadyToListen;
        }
    ```

8. <span data-ttu-id="1d77f-394">Agregue los dos controladores a los que llaman las bibliotecas de voz cuando comienza y finaliza la captura de voz.</span><span class="sxs-lookup"><span data-stu-id="1d77f-394">Add the two handlers that are called by the speech libraries when voice capture begins and ends.</span></span> <span data-ttu-id="1d77f-395">*DictationRecognizer* dejará de capturar automáticamente la voz de usuario cuando el usuario deje de hablar.</span><span class="sxs-lookup"><span data-stu-id="1d77f-395">The *DictationRecognizer* will automatically stop capturing the user voice when the user stops speaking.</span></span>

    ```csharp
        /// <summary>
        /// Start microphone capture.
        /// </summary>
        public void StartCapturingAudio()
        {
            botState = BotState.Listening;
            botMaterial.color = Color.red;

            // Start dictation
            dictationRecognizer = new DictationRecognizer();
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
            dictationRecognizer.Start();
        }
        

        /// <summary>
        /// Stop microphone capture.
        /// </summary>
        public void StopCapturingAudio()
        {
            botState = BotState.Processing;
            dictationRecognizer.Stop();
        }
        
    ```

1. <span data-ttu-id="1d77f-396">El siguiente controlador recopila el resultado de la entrada de voz de usuario y llama a la corutina responsable de enviar el mensaje a Web App bot Service.</span><span class="sxs-lookup"><span data-stu-id="1d77f-396">The following handler collects the result of the user voice input and calls the coroutine responsible for sending the message to the Web App Bot Service.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Debug.Log($"User just said: {text}");      

            // Send dictation to Bot
            StartCoroutine(SendMessageToBot(text, botId, botName, "message"));
            StopCapturingAudio();
        }     
    ```

10. <span data-ttu-id="1d77f-397">Se llama a la siguiente corutina para iniciar una conversación con el bot.</span><span class="sxs-lookup"><span data-stu-id="1d77f-397">The following coroutine is called to begin a conversation with the Bot.</span></span> <span data-ttu-id="1d77f-398">Observará que una vez completada la llamada de conversación, llamará a **SendMessageToCoroutine ()** pasando una serie de parámetros que establecerán la actividad que se va a enviar al servicio bot como un mensaje vacío.</span><span class="sxs-lookup"><span data-stu-id="1d77f-398">You will notice that once the conversation call is complete, it will call the **SendMessageToCoroutine()** by passing a series of parameters that will set the activity to be sent to the Bot Service as an empty message.</span></span> <span data-ttu-id="1d77f-399">Esto se hace para pedir al servicio de bot que inicie el cuadro de diálogo.</span><span class="sxs-lookup"><span data-stu-id="1d77f-399">This is done to prompt the Bot Service to initiate the dialogue.</span></span>

    ```csharp
        /// <summary>
        /// Request a conversation with the Bot Service
        /// </summary>
        internal IEnumerator StartConversation()
        {
            string conversationEndpoint = string.Format("{0}/conversations", botEndpoint);

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(conversationEndpoint, webForm))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + botSecret);
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                yield return unityWebRequest.SendWebRequest();
                string jsonResponse = unityWebRequest.downloadHandler.text;
            
                conversation = new ConversationObject();
                conversation = JsonConvert.DeserializeObject<ConversationObject>(jsonResponse);
                Debug.Log($"Start Conversation - Id: {conversation.ConversationId}");
                conversationStarted = true; 
            }

            // The following call is necessary to create and inject an activity of type //"conversationUpdate" to request a first "introduction" from the Bot Service.
            StartCoroutine(SendMessageToBot("", botId, botName, "conversationUpdate"));
        }    
    ```

11. <span data-ttu-id="1d77f-400">Se llama a la siguiente corutina para compilar la actividad que se va a enviar al servicio bot.</span><span class="sxs-lookup"><span data-stu-id="1d77f-400">The following coroutine is called to build the activity to be sent to the Bot Service.</span></span> 

    ```csharp
        /// <summary>
        /// Send the user message to the Bot Service in form of activity
        /// and call for a response
        /// </summary>
        private IEnumerator SendMessageToBot(string message, string fromId, string fromName, string activityType)
        {
            Debug.Log($"SendMessageCoroutine: {conversation.ConversationId}, message: {message} from Id: {fromId} from name: {fromName}");

            // Create a new activity here
            Activity activity = new Activity();
            activity.from = new From();
            activity.conversation = new Conversation();
            activity.from.id = fromId;
            activity.from.name = fromName;
            activity.text = message;
            activity.type = activityType;
            activity.channelId = "DirectLineChannelId";
            activity.conversation.id = conversation.ConversationId;     

            // Serialize the activity
            string json = JsonConvert.SerializeObject(activity);

            string sendActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);
            
            // Send the activity to the Bot
            using (UnityWebRequest www = new UnityWebRequest(sendActivityEndpoint, "POST"))
            {
                www.uploadHandler = new UploadHandlerRaw(Encoding.UTF8.GetBytes(json));

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + botSecret);
                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                // extrapolate the response Id used to keep track of the conversation
                string jsonResponse = www.downloadHandler.text;
                string cleanedJsonResponse = jsonResponse.Replace("\r\n", string.Empty);
                string responseConvId = cleanedJsonResponse.Substring(10, 30);

                // Request a response from the Bot Service
                StartCoroutine(GetResponseFromBot(activity));
            }
        }
    ```

12. <span data-ttu-id="1d77f-401">Se llama a la siguiente corutina para solicitar una respuesta después de enviar una actividad al servicio bot.</span><span class="sxs-lookup"><span data-stu-id="1d77f-401">The following coroutine is called to request a response after sending an activity to the Bot Service.</span></span> 

    ```csharp
        /// <summary>
        /// Request a response from the Bot by using a previously sent activity
        /// </summary>
        private IEnumerator GetResponseFromBot(Activity activity)
        {
            string getActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);

            using (UnityWebRequest unityWebRequest1 = UnityWebRequest.Get(getActivityEndpoint))
            {
                unityWebRequest1.downloadHandler = new DownloadHandlerBuffer();
                unityWebRequest1.SetRequestHeader("Authorization", "Bearer " + botSecret);

                yield return unityWebRequest1.SendWebRequest();

                string jsonResponse = unityWebRequest1.downloadHandler.text;

                ActivitiesRootObject root = new ActivitiesRootObject();
                root = JsonConvert.DeserializeObject<ActivitiesRootObject>(jsonResponse);

                foreach (var act in root.activities)
                {
                    Debug.Log($"Bot Response: {act.text}");
                    SetBotResponseText(act.text);
                }

                botState = BotState.ReadyToListen;
                botMaterial.color = Color.blue;
            }
        } 
    ```

13. <span data-ttu-id="1d77f-402">El último método que se va a agregar a esta clase es necesario para mostrar el mensaje en la escena:</span><span class="sxs-lookup"><span data-stu-id="1d77f-402">The last method to be added to this class, is required to display the message in the scene:</span></span>

    ```csharp
        /// <summary>
        /// Set the UI Response Text of the bot
        /// </summary>
        internal void SetBotResponseText(string responseString)
        {        
            SceneOrganiser.Instance.botResponseText.text =  responseString;
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="1d77f-403">Es posible que vea un error en la consola del editor de Unity, sobre la falta de la clase **SceneOrganiser** .</span><span class="sxs-lookup"><span data-stu-id="1d77f-403">You may see an error within the Unity Editor Console, about missing the **SceneOrganiser** class.</span></span> <span data-ttu-id="1d77f-404">Pase por alto este mensaje, ya que creará esta clase más adelante en el tutorial.</span><span class="sxs-lookup"><span data-stu-id="1d77f-404">Disregard this message, as you will create this class later in the tutorial.</span></span>

14.  <span data-ttu-id="1d77f-405">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="1d77f-405">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11--create-the-interactions-class"></a><span data-ttu-id="1d77f-406">Capítulo 11: crear la clase Interactions</span><span class="sxs-lookup"><span data-stu-id="1d77f-406">Chapter 11 – Create the Interactions class</span></span>

<span data-ttu-id="1d77f-407">La clase que va a crear ahora se denomina **interacciones**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-407">The class you are going to create now is called **Interactions**.</span></span> <span data-ttu-id="1d77f-408">Esta clase se usa para detectar la entrada de la pulsación de HoloLens del usuario.</span><span class="sxs-lookup"><span data-stu-id="1d77f-408">This class is used to detect the HoloLens Tap Input from the user.</span></span> 

<span data-ttu-id="1d77f-409">Si el usuario pulsa mientras mira el objeto *Bot* en la escena y el bot está listo para escuchar las entradas de voz, el objeto bot cambiará el color a **rojo** y comenzará a escuchar las entradas de voz.</span><span class="sxs-lookup"><span data-stu-id="1d77f-409">If the user taps while looking at the *Bot* object in the scene, and the Bot is ready to listen for voice inputs, the Bot object will change color to **red** and begin listening for voice inputs.</span></span> 

<span data-ttu-id="1d77f-410">Esta clase hereda de la clase **GazeInput** y, por lo tanto, puede hacer referencia al método **Start ()** y a las variables de esa clase, que se indican mediante el uso de **base**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-410">This class inherits from the **GazeInput** class, and so is able to reference the **Start()** method and variables from that class, denoted by the use of **base**.</span></span> 
 
<span data-ttu-id="1d77f-411">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="1d77f-411">To create this class:</span></span>

1.  <span data-ttu-id="1d77f-412">Haga doble clic en la carpeta scripts para abrirla.</span><span class="sxs-lookup"><span data-stu-id="1d77f-412">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="1d77f-413">Haga clic con el botón derecho en la carpeta scripts y haga clic en **crear > C# script**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="1d77f-414">Asigne un nombrea las interacciones del script.</span><span class="sxs-lookup"><span data-stu-id="1d77f-414">Name the script **Interactions**.</span></span> 
3.  <span data-ttu-id="1d77f-415">Haga doble clic en el nuevo script para abrirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1d77f-415">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="1d77f-416">Actualice los espacios de nombres y la herencia de clases para que sea igual que la siguiente, en la parte superior de la clase Interactions:</span><span class="sxs-lookup"><span data-stu-id="1d77f-416">Update the namespaces and the class inheritance to be the same as the following, at the top of the **Interactions** class:</span></span>

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  <span data-ttu-id="1d77f-417">Dentro de la clase Interactions, agregue la siguiente variable:</span><span class="sxs-lookup"><span data-stu-id="1d77f-417">Inside the **Interactions** class add the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  <span data-ttu-id="1d77f-418">A continuación, agregue el método **Start ()** :</span><span class="sxs-lookup"><span data-stu-id="1d77f-418">Then add the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            //Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="1d77f-419">Agregar el controlador que se desencadenará cuando el usuario realice el gesto de TAP delante de la cámara HoloLens</span><span class="sxs-lookup"><span data-stu-id="1d77f-419">Add the handler that will be triggered when the user performs the tap gesture in front of the HoloLens camera</span></span>

    ```csharp
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            // Ensure the bot is being gazed upon.
            if(base.FocusedObject != null)
            {
                // If the user is tapping on Bot and the Bot is ready to listen
                if (base.FocusedObject.name == "Bot" && Bot.Instance.botState == Bot.BotState.ReadyToListen)
                {
                    // If a conversation has not started yet, request one
                    if(Bot.Instance.conversationStarted)
                    {
                        Bot.Instance.SetBotResponseText("Listening...");
                        Bot.Instance.StartCapturingAudio();
                    }
                    else
                    {
                        Bot.Instance.SetBotResponseText("Requesting Conversation...");
                        StartCoroutine(Bot.Instance.StartConversation());
                    }                                  
                }
            }
        }
    ```

8. <span data-ttu-id="1d77f-420">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="1d77f-420">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-12--create-the-sceneorganiser-class"></a><span data-ttu-id="1d77f-421">Capítulo 12: creación de la clase SceneOrganiser</span><span class="sxs-lookup"><span data-stu-id="1d77f-421">Chapter 12 – Create the SceneOrganiser class</span></span>

<span data-ttu-id="1d77f-422">La última clase requerida en este laboratorio se denomina **SceneOrganiser**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-422">The last class required in this Lab is called **SceneOrganiser**.</span></span> <span data-ttu-id="1d77f-423">Esta clase configurará la escena mediante programación, agregando componentes y scripts a la cámara principal y creando los objetos adecuados en la escena.</span><span class="sxs-lookup"><span data-stu-id="1d77f-423">This class will setup the scene programmatically, by adding components and scripts to the Main Camera, and creating the appropriate objects in the scene.</span></span>
 
<span data-ttu-id="1d77f-424">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="1d77f-424">To create this class:</span></span>

1.  <span data-ttu-id="1d77f-425">Haga doble clic en la carpeta scripts para abrirla.</span><span class="sxs-lookup"><span data-stu-id="1d77f-425">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="1d77f-426">Haga clic con el botón derecho en la carpeta scripts y haga clic en **crear > C# script**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-426">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="1d77f-427">Asigne al script el nombre **SceneOrganiser**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-427">Name the script **SceneOrganiser**.</span></span> 
3.  <span data-ttu-id="1d77f-428">Haga doble clic en el nuevo script para abrirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1d77f-428">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="1d77f-429">Dentro de la clase **SceneOrganiser** , agregue las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="1d77f-429">Inside the **SceneOrganiser** class add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The 3D text representing the Bot response
        /// </summary>
        internal TextMesh botResponseText;
    ```

6.  <span data-ttu-id="1d77f-430">A continuación, agregue los métodos **activo ()** e **Inicio ()** :</span><span class="sxs-lookup"><span data-stu-id="1d77f-430">Then add the **Awake()** and **Start()** methods:</span></span>

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start ()
        {
            // Add the GazeInput class to this object
            gameObject.AddComponent<GazeInput>();

            // Add the Interactions class to this object
            gameObject.AddComponent<Interactions>();

            // Create the Bot in the scene
            CreateBotInScene();
        }
    ```

7.  <span data-ttu-id="1d77f-431">Agregue el método siguiente, responsable de crear el objeto bot en la escena y configurar los parámetros y componentes:</span><span class="sxs-lookup"><span data-stu-id="1d77f-431">Add the following method, responsible for creating the Bot object in the scene and setting up the parameters and components:</span></span>

    ```csharp
        /// <summary>
        /// Create the Sign In button object in the scene
        /// and sets its properties
        /// </summary>
        private void CreateBotInScene()
        {
            GameObject botObjInScene = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            botObjInScene.name = "Bot";
            
            // Add the Bot class to the Bot GameObject
            botObjInScene.AddComponent<Bot>();

            // Create the Bot UI
            botResponseText = CreateBotResponseText();

            // Set properties of Bot GameObject
            Bot.Instance.botMaterial = new Material(Shader.Find("Diffuse"));
            botObjInScene.GetComponent<Renderer>().material = Bot.Instance.botMaterial;
            Bot.Instance.botMaterial.color = Color.blue;
            botObjInScene.transform.position = new Vector3(0f, 2f, 10f);
            botObjInScene.tag = "BotTag";
        }
    ```

7.  <span data-ttu-id="1d77f-432">Agregue el método siguiente, responsable de crear el objeto de interfaz de usuario en la escena, que representa las respuestas del bot:</span><span class="sxs-lookup"><span data-stu-id="1d77f-432">Add the following method, responsible for creating the UI object in the scene, representing the responses from the Bot:</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private TextMesh CreateBotResponseText()
        {
            // Create a sphere as new cursor
            GameObject textObject = new GameObject();
            textObject.transform.parent = Bot.Instance.transform;
            textObject.transform.localPosition = new Vector3(0,1,0);

            // Resize the new cursor
            textObject.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            // Creating the text of the Label
            TextMesh textMesh = textObject.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            textMesh.fontSize = 50;
            textMesh.text = "Hi there, tap on me and I will start listening.";
            
            return textMesh;
        }
    ```

8.  <span data-ttu-id="1d77f-433">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="1d77f-433">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
9.  <span data-ttu-id="1d77f-434">En el editor de Unity, arrastre el script **SceneOrganiser** desde la carpeta scripts a la cámara principal.</span><span class="sxs-lookup"><span data-stu-id="1d77f-434">In the Unity Editor, drag the **SceneOrganiser** script from the Scripts folder to the Main Camera.</span></span> <span data-ttu-id="1d77f-435">El componente de organizador de escenas debe aparecer ahora en el objeto de cámara principal, como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="1d77f-435">The Scene Organiser component should now appear on the Main Camera object, as shown in the image below.</span></span>

    ![Cree el Azure Bot Service](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a><span data-ttu-id="1d77f-437">Capítulo 13: antes de compilar</span><span class="sxs-lookup"><span data-stu-id="1d77f-437">Chapter 13 – Before building</span></span>

<span data-ttu-id="1d77f-438">Para realizar una prueba exhaustiva de la aplicación, debe transferirla a su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1d77f-438">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="1d77f-439">Antes de hacerlo, asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="1d77f-439">Before you do, ensure that:</span></span>

-   <span data-ttu-id="1d77f-440">Toda la configuración mencionada en el [**capítulo 4**](#chapter-4--set-up-the-unity-project) se establece correctamente.</span><span class="sxs-lookup"><span data-stu-id="1d77f-440">All the settings mentioned in the [**Chapter 4**](#chapter-4--set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="1d77f-441">El script **SceneOrganiser** se adjunta al objeto de **cámara principal** .</span><span class="sxs-lookup"><span data-stu-id="1d77f-441">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="1d77f-442">En la clase **Bot** , asegúrese de que ha insertado la **clave de bot secreta** en la variable **botSecret** .</span><span class="sxs-lookup"><span data-stu-id="1d77f-442">In the **Bot** class, make sure you have inserted your **Bot Secret Key** into the **botSecret** variable.</span></span>

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a><span data-ttu-id="1d77f-443">Capítulo 14: compilar y transferir localmente a HoloLens</span><span class="sxs-lookup"><span data-stu-id="1d77f-443">Chapter 14 – Build and Sideload to the HoloLens</span></span>

<span data-ttu-id="1d77f-444">Ya se ha completado todo lo necesario para la sección Unity de este proyecto, por lo que es el momento de compilarla desde Unity.</span><span class="sxs-lookup"><span data-stu-id="1d77f-444">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="1d77f-445">Vaya a **configuración de compilación**, **archivo > configuración de compilación.** .</span><span class="sxs-lookup"><span data-stu-id="1d77f-445">Navigate to **Build Settings**, **File > Build Settings…**.</span></span>
2.  <span data-ttu-id="1d77f-446">En la ventana **configuración de compilación** , haga clic en compilar.</span><span class="sxs-lookup"><span data-stu-id="1d77f-446">From the **Build Settings** window, click **Build**.</span></span>

    ![Compilar la aplicación desde Unity](images/AzureLabs-Lab312-38.png)

3.  <span data-ttu-id="1d77f-448">Si aún no lo está, marque los **proyectos de Unity C#** .</span><span class="sxs-lookup"><span data-stu-id="1d77f-448">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="1d77f-449">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-449">Click **Build**.</span></span> <span data-ttu-id="1d77f-450">Unity iniciará una ventana del **Explorador de archivos** , donde tendrá que crear y seleccionar una carpeta en la que compilar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1d77f-450">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="1d77f-451">Cree esa carpeta ahora y asígnele el nombre **App**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-451">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="1d77f-452">Después, con la carpeta de la **aplicación** seleccionada, haga clic en **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-452">Then with the **App** folder selected, click **Select Folder**.</span></span> 
5.  <span data-ttu-id="1d77f-453">Unity comenzará a compilar el proyecto en la carpeta de la **aplicación** .</span><span class="sxs-lookup"><span data-stu-id="1d77f-453">Unity will begin building your project to the **App** folder.</span></span> 
6.  <span data-ttu-id="1d77f-454">Una vez que Unity termine de compilar (puede tardar algún tiempo), se abrirá una ventana del **Explorador de archivos** en la ubicación de la compilación (Compruebe la barra de tareas, ya que es posible que no aparezca siempre por encima de las ventanas, pero le notificará la adición de una nueva ventana).</span><span class="sxs-lookup"><span data-stu-id="1d77f-454">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-15--deploy-to-hololens"></a><span data-ttu-id="1d77f-455">Capítulo 15: implementación en HoloLens</span><span class="sxs-lookup"><span data-stu-id="1d77f-455">Chapter 15 – Deploy to HoloLens</span></span>

<span data-ttu-id="1d77f-456">Para implementar en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="1d77f-456">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="1d77f-457">Necesitará la dirección IP de HoloLens (para la implementación remota) y para asegurarse de que HoloLens está en **modo de desarrollador**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-457">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="1d77f-458">Para ello:</span><span class="sxs-lookup"><span data-stu-id="1d77f-458">To do this:</span></span>

    1. <span data-ttu-id="1d77f-459">Mientras se contenga HoloLens, abra la **configuración**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-459">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="1d77f-460">Vaya a **Network & Internet > Wi-Fi > opciones avanzadas** .</span><span class="sxs-lookup"><span data-stu-id="1d77f-460">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="1d77f-461">Anote la dirección **IPv4** .</span><span class="sxs-lookup"><span data-stu-id="1d77f-461">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="1d77f-462">A continuación, vuelva a **configuración**y, a continuación, **actualice & seguridad > para desarrolladores**</span><span class="sxs-lookup"><span data-stu-id="1d77f-462">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="1d77f-463">Establezca el modo de Desarrollador en.</span><span class="sxs-lookup"><span data-stu-id="1d77f-463">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="1d77f-464">Vaya a la nueva compilación de Unity (la carpeta de la **aplicación** ) y abra el archivo de solución con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-464">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>
3.  <span data-ttu-id="1d77f-465">En la **configuración de soluciones** , seleccione Depurar.</span><span class="sxs-lookup"><span data-stu-id="1d77f-465">In the **Solution Configuration** select **Debug**.</span></span>
4.  <span data-ttu-id="1d77f-466">En la **plataforma**de la solución, seleccione **x86**, **equipo remoto**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-466">In the **Solution Platform**, select **x86**, **Remote Machine**.</span></span> 

    ![Implemente la solución desde Visual Studio.](images/AzureLabs-Lab312-39.png)
 
5.  <span data-ttu-id="1d77f-468">Vaya al **menú** compilar y haga clic en **implementar solución**para transferir localmente la aplicación a HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1d77f-468">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="1d77f-469">La aplicación debe aparecer ahora en la lista de aplicaciones instaladas en HoloLens, lista para su lanzamiento.</span><span class="sxs-lookup"><span data-stu-id="1d77f-469">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

    > [!NOTE]
    > <span data-ttu-id="1d77f-470">Para implementar en auriculares inmersivo, establezca la **plataforma** de la solución en el *equipo local*y establezca la **configuración** en depurar, con *x86* como **plataforma**.</span><span class="sxs-lookup"><span data-stu-id="1d77f-470">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="1d77f-471">A continuación, implemente en el equipo local, mediante el **menú**compilar, seleccionando *implementar solución*.</span><span class="sxs-lookup"><span data-stu-id="1d77f-471">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="chapter-16--using-the-application-on-the-hololens"></a><span data-ttu-id="1d77f-472">Capítulo 16: uso de la aplicación en HoloLens</span><span class="sxs-lookup"><span data-stu-id="1d77f-472">Chapter 16 – Using the application on the HoloLens</span></span>

- <span data-ttu-id="1d77f-473">Una vez que haya iniciado la aplicación, verá el bot como una esfera azul delante de usted.</span><span class="sxs-lookup"><span data-stu-id="1d77f-473">Once you have launched the application, you will see the Bot as a blue sphere in front of you.</span></span>

- <span data-ttu-id="1d77f-474">Use el **gesto de TAP** mientras está Gazing en la esfera para iniciar una conversación.</span><span class="sxs-lookup"><span data-stu-id="1d77f-474">Use the **Tap Gesture** while you are gazing at the sphere to initiate a conversation.</span></span> 
 
- <span data-ttu-id="1d77f-475">Espere a que se inicie la conversación (la interfaz de usuario mostrará un mensaje cuando se produzca).</span><span class="sxs-lookup"><span data-stu-id="1d77f-475">Wait for the conversation to start (The UI will display a message when it happens).</span></span> <span data-ttu-id="1d77f-476">Una vez que reciba el mensaje introductorio del bot, pulse de nuevo en el bot para que se vuelva rojo y empiece a escuchar la voz.</span><span class="sxs-lookup"><span data-stu-id="1d77f-476">Once you receive the introductory message from the Bot, tap again on the Bot so it will turn red and begin to listen to your voice.</span></span> 

- <span data-ttu-id="1d77f-477">Una vez que haya dejado de hablar, la aplicación enviará el mensaje al bot y recibirá una respuesta que se mostrará en la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="1d77f-477">Once you stop talking, your application will send your message to the Bot and you will promptly receive a response that will be displayed in the UI.</span></span> 

- <span data-ttu-id="1d77f-478">Repita el proceso para enviar más mensajes a su Bot (debe puntear cada vez que desee enviar un mensaje).</span><span class="sxs-lookup"><span data-stu-id="1d77f-478">Repeat the process to send more messages to your Bot (you have to tap each time you want to sen a message).</span></span>

<span data-ttu-id="1d77f-479">Esta conversación muestra cómo el bot puede conservar la información (su nombre), a la vez que proporciona información conocida (como los elementos que están almacenados en existencias).</span><span class="sxs-lookup"><span data-stu-id="1d77f-479">This conversation demonstrates how the Bot can retain information (your name), whilst also providing known information (such as the items that are stocked).</span></span>

#### <a name="some-questions-to-ask-the-bot"></a><span data-ttu-id="1d77f-480">Algunas preguntas para preguntar al bot:</span><span class="sxs-lookup"><span data-stu-id="1d77f-480">Some questions to ask the Bot:</span></span>

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a><span data-ttu-id="1d77f-481">Su aplicación Web App Bot (v4) finalizada</span><span class="sxs-lookup"><span data-stu-id="1d77f-481">Your finished Web App Bot (v4) application</span></span>

<span data-ttu-id="1d77f-482">Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha el bot de aplicaciones Web de Azure, Microsoft bot Framework V4.</span><span class="sxs-lookup"><span data-stu-id="1d77f-482">Congratulations, you built a mixed reality app that leverages the Azure Web App Bot, Microsoft Bot Framework v4.</span></span>

![Producto final](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="1d77f-484">Ejercicios de bonus</span><span class="sxs-lookup"><span data-stu-id="1d77f-484">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="1d77f-485">Ejercicio 1</span><span class="sxs-lookup"><span data-stu-id="1d77f-485">Exercise 1</span></span>

<span data-ttu-id="1d77f-486">La estructura de conversación de este laboratorio es muy básica.</span><span class="sxs-lookup"><span data-stu-id="1d77f-486">The conversation structure in this Lab is very basic.</span></span> <span data-ttu-id="1d77f-487">Utilice Microsoft LUIS para ofrecer capacidades de comprensión del lenguaje natural de bot.</span><span class="sxs-lookup"><span data-stu-id="1d77f-487">Use Microsoft LUIS to give your bot natural language understanding capabilities.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="1d77f-488">Ejercicio 2</span><span class="sxs-lookup"><span data-stu-id="1d77f-488">Exercise 2</span></span>

<span data-ttu-id="1d77f-489">En este ejemplo no se incluye la finalización de una conversación y el reinicio de una nueva.</span><span class="sxs-lookup"><span data-stu-id="1d77f-489">This example does not include terminating a conversation and restarting a new one.</span></span> <span data-ttu-id="1d77f-490">Para que la característica de bot se complete, intente implementar el cierre de la conversación.</span><span class="sxs-lookup"><span data-stu-id="1d77f-490">To make the Bot feature complete, try to implement closure to the conversation.</span></span>
