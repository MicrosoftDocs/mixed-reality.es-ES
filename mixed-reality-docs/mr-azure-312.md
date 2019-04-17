---
title: El Sr. y 312 Azure - integración de Bot
description: Complete este curso para obtener información sobre cómo crear e implementar un bot mediante Microsoft Bot Framework v4 y comunicarse con él en una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidad mixta, Azure, academy, unity, tutorial, api, computer vision o hololens, vr envolventes, microsoft bot framework v4, bot de web Apps, framework bot, bot de microsoft
ms.openlocfilehash: b828aa4415103d280459bd2c666004c994b3e59d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605760"
---
>[!NOTE]
><span data-ttu-id="670cd-104">Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.</span><span class="sxs-lookup"><span data-stu-id="670cd-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="670cd-105">Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="670cd-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="670cd-106">Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.</span><span class="sxs-lookup"><span data-stu-id="670cd-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="670cd-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="670cd-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="670cd-108">Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="670cd-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="670cd-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.</span><span class="sxs-lookup"><span data-stu-id="670cd-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-312-bot-integration"></a><span data-ttu-id="670cd-110">El Sr. y Azure 312: Integración de bot</span><span class="sxs-lookup"><span data-stu-id="670cd-110">MR and Azure 312: Bot integration</span></span>

<span data-ttu-id="670cd-111">En este curso, obtendrá información sobre cómo crear e implementar un bot mediante el V4 de Microsoft Bot Framework y comunicarse con él a través de una aplicación de Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="670cd-111">In this course, you will learn how to create and deploy a bot using the Microsoft Bot Framework V4 and communicate with it through a Windows Mixed Reality application.</span></span> 

![](images/AzureLabs-Lab312-00.png)

<span data-ttu-id="670cd-112">El **Microsoft Bot Framework V4** es un conjunto de API diseñadas para ofrecer a los desarrolladores las herramientas necesarias para crear un bot escalable y extensible application.</span><span class="sxs-lookup"><span data-stu-id="670cd-112">The **Microsoft Bot Framework V4** is a set of APIs designed to provide developers with the tools to build an extensible and scalable bot application.</span></span> <span data-ttu-id="670cd-113">Para obtener más información, visite la [página Microsoft Bot Framework](https://dev.botframework.com/) o [V4 repositorio](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span><span class="sxs-lookup"><span data-stu-id="670cd-113">For more information, visit the [Microsoft Bot Framework page](https://dev.botframework.com/) or the [V4 Git Repository](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span></span>

<span data-ttu-id="670cd-114">Después de completar este curso, habrá creado una aplicación Windows Mixed Reality, que podrá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="670cd-114">After completing this course, you will have built a Windows Mixed Reality application, which will be able to do the following:</span></span>

1. <span data-ttu-id="670cd-115">Use un **gesto de pulsar** para iniciar el bot a la escucha de la voz de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="670cd-115">Use a **Tap Gesture** to start the bot listening for the users voice.</span></span>
2. <span data-ttu-id="670cd-116">Cuando el usuario indicaba un mensaje, el bot intentará proporcionar una respuesta.</span><span class="sxs-lookup"><span data-stu-id="670cd-116">When the user has said something, the bot will attempt to provide a response.</span></span>
3. <span data-ttu-id="670cd-117">Muestra la respuesta de los bots como texto, situado cerca de bot, en la escena de Unity.</span><span class="sxs-lookup"><span data-stu-id="670cd-117">Display the bots reply as text, positioned near the bot, in the Unity Scene.</span></span>

<span data-ttu-id="670cd-118">En la aplicación, es depende de usted sobre cómo se integrará los resultados con el diseño.</span><span class="sxs-lookup"><span data-stu-id="670cd-118">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="670cd-119">Este curso está diseñado para mostrarle cómo integrar un servicio de Azure con el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="670cd-119">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="670cd-120">Es su trabajo consiste en usar los conocimientos que obtendrá de este curso para mejorar las aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="670cd-120">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="670cd-121">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="670cd-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="670cd-122">Curso</span><span class="sxs-lookup"><span data-stu-id="670cd-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="670cd-123"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="670cd-123"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="670cd-124"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="670cd-124"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="670cd-125">El Sr. y Azure 312: Integración de bot</span><span class="sxs-lookup"><span data-stu-id="670cd-125">MR and Azure 312: Bot integration</span></span></td><td style="text-align: center;"> <span data-ttu-id="670cd-126">✔️</span><span class="sxs-lookup"><span data-stu-id="670cd-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="670cd-127">✔️</span><span class="sxs-lookup"><span data-stu-id="670cd-127">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="670cd-128">Aunque este curso se centra principalmente en HoloLens, también puede aplicar lo aprendido en este curso a inmersivos (VR) Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="670cd-128">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="670cd-129">Dado que inmersivos (VR) no tienen cámaras accesible, necesitará una cámara externa conectada a su PC.</span><span class="sxs-lookup"><span data-stu-id="670cd-129">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="670cd-130">Como seguir el curso, verá las notas de la de los cambios que deberá emplear para admitir inmersivos (VR).</span><span class="sxs-lookup"><span data-stu-id="670cd-130">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="670cd-131">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="670cd-131">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="670cd-132">Este tutorial está diseñado para los desarrolladores con experiencia básica con Unity y C#.</span><span class="sxs-lookup"><span data-stu-id="670cd-132">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="670cd-133">También Ten en cuenta que los requisitos previos y las instrucciones escritas en este documento representan lo que se ha probado y comprobado en el momento de redactar (julio de 2018).</span><span class="sxs-lookup"><span data-stu-id="670cd-133">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="670cd-134">Es libre de usar el software más reciente, como se muestra en el [instalar las herramientas de](install-the-tools.md) artículo, aunque no se debe suponer que la información de este curso perfectamente coincida con lo que encontrará en el software más reciente que se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="670cd-134">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="670cd-135">Se recomiendan el siguiente hardware y software para este curso:</span><span class="sxs-lookup"><span data-stu-id="670cd-135">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="670cd-136">Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desarrollo de auriculares envolvente (VR)</span><span class="sxs-lookup"><span data-stu-id="670cd-136">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="670cd-137">Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="670cd-137">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="670cd-138">El SDK más reciente de Windows 10</span><span class="sxs-lookup"><span data-stu-id="670cd-138">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="670cd-139">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="670cd-139">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="670cd-140">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="670cd-140">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="670cd-141">Un [auriculares de Windows Mixed Reality envolventes (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="670cd-141">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="670cd-142">Acceso a Internet para Azure y para la recuperación de Azure Bot.</span><span class="sxs-lookup"><span data-stu-id="670cd-142">Internet access for Azure, and for Azure Bot retrieval.</span></span> <span data-ttu-id="670cd-143">Para obtener más información, [, siga este vínculo](https://dev.botframework.com/).</span><span class="sxs-lookup"><span data-stu-id="670cd-143">For more information, [please follow this link](https://dev.botframework.com/).</span></span>

### <a name="before-you-start"></a><span data-ttu-id="670cd-144">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="670cd-144">Before you start</span></span>

1.  <span data-ttu-id="670cd-145">Para evitar problemas de creación de este proyecto, se recomienda encarecidamente que cree el proyecto se ha mencionado en este tutorial en una carpeta raíz o cerca de la raíz (rutas de acceso de carpeta largo pueden causar problemas en tiempo de compilación).</span><span class="sxs-lookup"><span data-stu-id="670cd-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="670cd-146">Configurar y probar su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="670cd-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="670cd-147">Si necesita admite la configuración de su HoloLens, [Asegúrese de visitar el artículo del programa de instalación de HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="670cd-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="670cd-148">Es una buena idea para realizar la calibración y optimización Sensor cuando comienza a desarrollar una nueva aplicación de HoloLens (a veces puede ayudar a realizar dichas tareas para cada usuario).</span><span class="sxs-lookup"><span data-stu-id="670cd-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="670cd-149">Para obtener ayuda sobre la calibración, siga este [vínculo al artículo de calibración de HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="670cd-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="670cd-150">Para obtener ayuda sobre optimización Sensor, siga este [vínculo al artículo optimización Sensor de HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="670cd-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1--create-the-bot-application"></a><span data-ttu-id="670cd-151">Capítulo 1: crear la aplicación Bot</span><span class="sxs-lookup"><span data-stu-id="670cd-151">Chapter 1 – Create the Bot application</span></span>

<span data-ttu-id="670cd-152">El primer paso es crear un bot como aplicación Web de ASP.Net Core local.</span><span class="sxs-lookup"><span data-stu-id="670cd-152">The first step is to create your bot as a local ASP.Net Core Web application.</span></span> <span data-ttu-id="670cd-153">Una vez que haya finalizado y probado, se publicará en el Portal de Azure.</span><span class="sxs-lookup"><span data-stu-id="670cd-153">Once you have finished and tested it, you will publish it to the Azure Portal.</span></span>

1.  <span data-ttu-id="670cd-154">Abra Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="670cd-154">Open Visual Studio.</span></span> <span data-ttu-id="670cd-155">Crear un nuevo proyecto, seleccione **aplicación Web de ASP NET Core** como el tipo de proyecto (lo encontrará en la subsección .NET Core) y llámelo **MyBot**.</span><span class="sxs-lookup"><span data-stu-id="670cd-155">Create a new project, select **ASP NET Core Web Application** as the project type (you will find it under the subsection .NET Core) and call it **MyBot**.</span></span> <span data-ttu-id="670cd-156">Haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="670cd-156">Click **OK**.</span></span>

2.  <span data-ttu-id="670cd-157">En la ventana que va a aparecer seleccione **vacía**.</span><span class="sxs-lookup"><span data-stu-id="670cd-157">In the Window that will appear select **Empty**.</span></span> <span data-ttu-id="670cd-158">También asegúrese de que el destino se establece en **ASP NET Core 2.0** y la autenticación se establece en **sin autenticación**.</span><span class="sxs-lookup"><span data-stu-id="670cd-158">Also make sure the target is set to **ASP NET Core 2.0** and the Authentication is set to **No Authentication**.</span></span> <span data-ttu-id="670cd-159">Haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="670cd-159">Click **OK**.</span></span>  

    ![Crear la aplicación bot](images/AzureLabs-Lab312-01.png)

3.  <span data-ttu-id="670cd-161">Ahora se abrirá la solución.</span><span class="sxs-lookup"><span data-stu-id="670cd-161">The solution will now open.</span></span> <span data-ttu-id="670cd-162">Haga doble clic en la solución **Mybot** en el **el Explorador de soluciones** y haga clic en **administrar paquetes de NuGet para la solución**.</span><span class="sxs-lookup"><span data-stu-id="670cd-162">Right-click on Solution **Mybot** in the **Solution Explorer** and click on **Manage NuGet Packages for Solution**.</span></span> 

    ![Crear la aplicación Bot](images/AzureLabs-Lab312-02.png)

4.  <span data-ttu-id="670cd-164">En el **examinar** pestaña, busque **Microsoft.Bot.Builder.Integration.AspNet.Core** (asegúrese de tener **incluir versión preliminar** activada).</span><span class="sxs-lookup"><span data-stu-id="670cd-164">In the **Browse** tab, search for **Microsoft.Bot.Builder.Integration.AspNet.Core** (make sure you have **Include pre-release** checked).</span></span> <span data-ttu-id="670cd-165">Seleccione la versión del paquete **4.0.1-Preview**y marque las casillas de proyecto.</span><span class="sxs-lookup"><span data-stu-id="670cd-165">Select the package version **4.0.1-preview**, and tick the project boxes.</span></span> <span data-ttu-id="670cd-166">A continuación, haga clic en **instalar**.</span><span class="sxs-lookup"><span data-stu-id="670cd-166">Then click on **Install**.</span></span> <span data-ttu-id="670cd-167">Ahora ha instalado las bibliotecas necesarias para la **Bot Framework v4**.</span><span class="sxs-lookup"><span data-stu-id="670cd-167">You have now installed the libraries needed for the **Bot Framework v4**.</span></span> <span data-ttu-id="670cd-168">Cierre la página de NuGet.</span><span class="sxs-lookup"><span data-stu-id="670cd-168">Close the NuGet page.</span></span>

    ![Crear la aplicación bot](images/AzureLabs-Lab312-03.png)

5.  <span data-ttu-id="670cd-170">Haga doble clic en su *proyecto*, **MyBot**, en el **el Explorador de soluciones** y haga clic en **agregar** **|** **Clase**.</span><span class="sxs-lookup"><span data-stu-id="670cd-170">Right-click on your *Project*, **MyBot**, in the **Solution Explorer** and click on **Add** **|** **Class**.</span></span>

    ![Crear la aplicación Bot](images/AzureLabs-Lab312-04.png)

6.  <span data-ttu-id="670cd-172">Nombre de la clase **MyBot** y haga clic en **agregar**.</span><span class="sxs-lookup"><span data-stu-id="670cd-172">Name the class **MyBot** and click on **Add**.</span></span>

    ![Crear la aplicación bot](images/AzureLabs-Lab312-05.png)

7.  <span data-ttu-id="670cd-174">Repita el punto anterior, para crear otra clase denominada **ConversationContext**.</span><span class="sxs-lookup"><span data-stu-id="670cd-174">Repeat the previous point, to create another class named **ConversationContext**.</span></span> 

8.  <span data-ttu-id="670cd-175">Haga doble clic en **wwwroot** en el **el Explorador de soluciones** y haga clic en **agregar** **|** **denuevoelemento**.</span><span class="sxs-lookup"><span data-stu-id="670cd-175">Right-click on **wwwroot** in the **Solution Explorer** and click on **Add** **|** **New Item**.</span></span> <span data-ttu-id="670cd-176">Seleccione **página HTML** (lo encontrará en la subsección Web).</span><span class="sxs-lookup"><span data-stu-id="670cd-176">Select  **HTML Page** (you will find it under the subsection Web).</span></span> <span data-ttu-id="670cd-177">Nombre del archivo **default.html**.</span><span class="sxs-lookup"><span data-stu-id="670cd-177">Name the file **default.html**.</span></span> <span data-ttu-id="670cd-178">Haz clic en **Agregar**.</span><span class="sxs-lookup"><span data-stu-id="670cd-178">Click **Add**.</span></span>

    ![Crear la aplicación bot](images/AzureLabs-Lab312-06.png)

9.  <span data-ttu-id="670cd-180">La lista de clases y objetos en el **el Explorador de soluciones** debería ser similar a la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="670cd-180">The list of classes / objects in the **Solution Explorer** should look like the image below.</span></span>

    ![Crear la aplicación bot](images/AzureLabs-Lab312-07.png)

10. <span data-ttu-id="670cd-182">Haga doble clic en el **ConversationContext** clase.</span><span class="sxs-lookup"><span data-stu-id="670cd-182">Double-click on the **ConversationContext** class.</span></span> <span data-ttu-id="670cd-183">Esta clase es responsable de almacenar las variables utilizadas por el bot para mantener el contexto de la conversación.</span><span class="sxs-lookup"><span data-stu-id="670cd-183">This class is responsible for holding the variables used by the bot to maintain the context of the conversation.</span></span> <span data-ttu-id="670cd-184">Estos valores de contexto de la conversación se mantienen en una instancia de esta clase, porque cualquier instancia de la **MyBot** clase actualizará cada vez que se recibe una actividad.</span><span class="sxs-lookup"><span data-stu-id="670cd-184">These conversation context values are maintained in an instance of this class, because any instance of the **MyBot** class will refresh each time an activity is received.</span></span> <span data-ttu-id="670cd-185">Agregue el código siguiente a la clase:</span><span class="sxs-lookup"><span data-stu-id="670cd-185">Add the following code to the class:</span></span>

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

11. <span data-ttu-id="670cd-186">Haga doble clic en el **MyBot** clase.</span><span class="sxs-lookup"><span data-stu-id="670cd-186">Double-click on the **MyBot** class.</span></span> <span data-ttu-id="670cd-187">Esta clase va a hospedar los controladores que se llama a cualquier actividad entrante del cliente.</span><span class="sxs-lookup"><span data-stu-id="670cd-187">This class will host the handlers called by any incoming activity from the customer.</span></span> <span data-ttu-id="670cd-188">En esta clase se agregará el código usado para crear la conversación entre el bot y el cliente.</span><span class="sxs-lookup"><span data-stu-id="670cd-188">In this class you will add the code used to build the conversation between the bot and the customer.</span></span> <span data-ttu-id="670cd-189">Como se mencionó anteriormente, una instancia de esta clase se inicializa cada vez que se recibe una actividad.</span><span class="sxs-lookup"><span data-stu-id="670cd-189">As mentioned earlier, an instance of this class is initialized each time an activity is received.</span></span> <span data-ttu-id="670cd-190">Agregue el código siguiente a esta clase:</span><span class="sxs-lookup"><span data-stu-id="670cd-190">Add the following code to this class:</span></span>

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

12. <span data-ttu-id="670cd-191">Haga doble clic en el **inicio** clase.</span><span class="sxs-lookup"><span data-stu-id="670cd-191">Double-click on the **Startup** class.</span></span> <span data-ttu-id="670cd-192">Esta clase inicializará el bot.</span><span class="sxs-lookup"><span data-stu-id="670cd-192">This class will initialize the bot.</span></span> <span data-ttu-id="670cd-193">Agregue el código siguiente a la clase:</span><span class="sxs-lookup"><span data-stu-id="670cd-193">Add the following code to the class:</span></span>

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

13. <span data-ttu-id="670cd-194">Abra el **programa** archivo de clase y compruebe el código en él es igual a lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="670cd-194">Open the **Program** class file and verify the code in it is the same as the following:</span></span>

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

14. <span data-ttu-id="670cd-195">No olvide guardar los cambios, para ello, vaya a **archivo** > **guardar todo**, desde la barra de herramientas en la parte superior de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="670cd-195">Remember to save your changes, to do so, go to **File** > **Save All**, from the toolbar at the top of Visual Studio.</span></span>

## <a name="chapter-2---create-the-azure-bot-service"></a><span data-ttu-id="670cd-196">Capítulo 2: crear el servicio de Azure Bot</span><span class="sxs-lookup"><span data-stu-id="670cd-196">Chapter 2 - Create the Azure Bot Service</span></span>

<span data-ttu-id="670cd-197">Ahora que ha creado el código para el bot, tiene que publicarla en una instancia de la *Bot de Web Apps* servicio, en el Portal de Azure.</span><span class="sxs-lookup"><span data-stu-id="670cd-197">Now that you have built the code for your bot, you have to publish it to an instance of the *Web App Bot* Service, on the Azure Portal.</span></span> <span data-ttu-id="670cd-198">Este capítulo le mostrará cómo crear y configurar el servicio Bot en Azure y, a continuación, publicar el código en él.</span><span class="sxs-lookup"><span data-stu-id="670cd-198">This Chapter will show you how to create and configure the Bot Service on Azure and then publish your code to it.</span></span>

1.  <span data-ttu-id="670cd-199">En primer lugar, inicie sesión en el Portal de Azure (https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="670cd-199">First, log in to the Azure Portal (https://portal.azure.com).</span></span> 

    1. <span data-ttu-id="670cd-200">Si no dispone de una cuenta de Azure, deberá crear uno.</span><span class="sxs-lookup"><span data-stu-id="670cd-200">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="670cd-201">Si está siguiendo este tutorial en una situación de aula o laboratorio, pida el instructor o uno de los a los supervisores de ayuda para instalar la nueva cuenta.</span><span class="sxs-lookup"><span data-stu-id="670cd-201">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="670cd-202">Una vez que haya iniciado sesión, haga clic en **crear un recurso** en la esquina superior izquierda esquina y busque *bot de aplicación Web*y haga clic en **ENTRAR**.</span><span class="sxs-lookup"><span data-stu-id="670cd-202">Once you are logged in, click on **Create a resource** in the top left corner, and search for *Web App bot*, and click **Enter**.</span></span>

    ![Crear el servicio de Azure Bot](images/AzureLabs-Lab312-08.png)
 
3.  <span data-ttu-id="670cd-204">La nueva página proporcionará una descripción de la *Bot de Web Apps* Service.</span><span class="sxs-lookup"><span data-stu-id="670cd-204">The new page will provide a description of the *Web App Bot* Service.</span></span> <span data-ttu-id="670cd-205">En la parte inferior izquierda de esta página, seleccione el **crear** botón para crear una asociación con este servicio.</span><span class="sxs-lookup"><span data-stu-id="670cd-205">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Crear el servicio de Azure Bot](images/AzureLabs-Lab312-09.png)
 
4.  <span data-ttu-id="670cd-207">Una vez que ha hecho clic **crear**:</span><span class="sxs-lookup"><span data-stu-id="670cd-207">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="670cd-208">Insertar el elemento **nombre** para esta instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="670cd-208">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="670cd-209">Seleccione un **suscripción**.</span><span class="sxs-lookup"><span data-stu-id="670cd-209">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="670cd-210">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="670cd-210">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="670cd-211">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="670cd-211">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="670cd-212">Se recomienda que todos los servicios de Azure asociados con un único proyecto (por ejemplo, como estos cursos) en un grupo de recursos comunes).</span><span class="sxs-lookup"><span data-stu-id="670cd-212">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="670cd-213">Si desea leer más acerca de los grupos de recursos de Azure, [, siga este vínculo](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="670cd-213">If you wish to read more about Azure Resource Groups, [please follow this link](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)</span></span>

    4. <span data-ttu-id="670cd-214">Determinar la ubicación del grupo de recursos (si está creando un nuevo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="670cd-214">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="670cd-215">La ubicación sería lo ideal es que en la región donde desea ejecutar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="670cd-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="670cd-216">Algunos recursos de Azure solo están disponibles en determinadas regiones.</span><span class="sxs-lookup"><span data-stu-id="670cd-216">Some Azure assets are only available in certain regions.</span></span>
    5. <span data-ttu-id="670cd-217">Seleccione el **tarifa** adecuado para usted, si ésta es la primera tiempo creando una *Bot de Web Apps* servicio, un nivel gratuito (denominado F0) debe estar disponible para usted</span><span class="sxs-lookup"><span data-stu-id="670cd-217">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Web App Bot* Service, a free tier (named F0) should be available to you</span></span>
    6. <span data-ttu-id="670cd-218">**Nombre de la aplicación** sólo se puede dejar el mismo que el *nombre Bot*.</span><span class="sxs-lookup"><span data-stu-id="670cd-218">**App name** can just be left the same as the *Bot name*.</span></span> 
    7. <span data-ttu-id="670cd-219">Deje el *plantilla Bot* como **básica (C#)**.</span><span class="sxs-lookup"><span data-stu-id="670cd-219">Leave the *Bot template* as **Basic (C#)**.</span></span>
    8. <span data-ttu-id="670cd-220">*Plan de App service/ubicación* debería haber sido rellenados automáticamente para su cuenta.</span><span class="sxs-lookup"><span data-stu-id="670cd-220">*App service plan/Location* should have been auto-filled for your account.</span></span>
    9. <span data-ttu-id="670cd-221">Establecer el **Azure Storage** que desea usar para hospedar su Bot.</span><span class="sxs-lookup"><span data-stu-id="670cd-221">Set the **Azure Storage** that you wish to use to host your Bot.</span></span> <span data-ttu-id="670cd-222">Si no tiene uno ya, puede crear aquí.</span><span class="sxs-lookup"><span data-stu-id="670cd-222">If you dont have one already, you can create it here.</span></span>
    10. <span data-ttu-id="670cd-223">También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.</span><span class="sxs-lookup"><span data-stu-id="670cd-223">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    11. <span data-ttu-id="670cd-224">Haga clic en crear.</span><span class="sxs-lookup"><span data-stu-id="670cd-224">Click Create.</span></span>
 
        ![Crear el servicio de Azure Bot](images/AzureLabs-Lab312-10.png)

5.  <span data-ttu-id="670cd-226">Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="670cd-226">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="670cd-227">Una vez creada la instancia de servicio, aparecerá una notificación en el Portal.</span><span class="sxs-lookup"><span data-stu-id="670cd-227">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![Crear el servicio de Azure Bot](images/AzureLabs-Lab312-11.png) 
 
7.  <span data-ttu-id="670cd-229">Haga clic en la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="670cd-229">Click on the notification to explore your new Service instance.</span></span> 

    ![Crear el servicio de Azure Bot](images/AzureLabs-Lab312-12.png)
 
8. <span data-ttu-id="670cd-231">Haga clic en el **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="670cd-231">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="670cd-232">Se le llevará a la nueva instancia del servicio de Azure.</span><span class="sxs-lookup"><span data-stu-id="670cd-232">You will be taken to your new Azure Service instance.</span></span> 

    ![Crear el servicio de Azure Bot](images/AzureLabs-Lab312-13.png)
 
9.  <span data-ttu-id="670cd-234">En este momento debe configurar una característica denominada **línea directa** para permitir que la aplicación cliente para comunicarse con este servicio de bots.</span><span class="sxs-lookup"><span data-stu-id="670cd-234">At this point you need to setup a feature called **Direct Line** to allow your client application to communicate with this Bot Service.</span></span> <span data-ttu-id="670cd-235">Haga clic en **canales**, a continuación, en el **agregar un canal destacado** sección, haga clic en **canal de línea directa configurar**.</span><span class="sxs-lookup"><span data-stu-id="670cd-235">Click on **Channels**, then in the **Add a featured channel** section, click on **Configure Direct Line channel**.</span></span>

    ![Crear el servicio de Azure Bot](images/AzureLabs-Lab312-14.png)

10. <span data-ttu-id="670cd-237">En esta página encontrará el **claves secretas** que permitirá que la aplicación cliente se autentique con el bot.</span><span class="sxs-lookup"><span data-stu-id="670cd-237">In this page you will find the **Secret keys** that will allow your client app to authenticate with the bot.</span></span> <span data-ttu-id="670cd-238">Haga clic en el **mostrar** botón y realice una copia de una de las claves de muestra, ya que lo necesitará más adelante en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="670cd-238">Click on the **Show** button and take a copy of one of the displayed Keys, as you will need this later in your project.</span></span> 

    ![Crear el servicio de Azure Bot](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a><span data-ttu-id="670cd-240">Capítulo 3: publicar el Bot en el servicio Bot de aplicación Web de Azure</span><span class="sxs-lookup"><span data-stu-id="670cd-240">Chapter 3 – Publish the Bot to the Azure Web App Bot Service</span></span>

<span data-ttu-id="670cd-241">Ahora que el servicio está listo, deberá publicar el código de Bot, que creó anteriormente, a su servicio de Bot de aplicación Web recién creada.</span><span class="sxs-lookup"><span data-stu-id="670cd-241">Now that your Service is ready, you need to publish your Bot code, that you built previously, to your newly created Web App Bot Service.</span></span>

> [!NOTE] 
> <span data-ttu-id="670cd-242">Tendrá que publicar su Bot en el servicio de Azure cada vez que realice cambios en la solución de Bot / código.</span><span class="sxs-lookup"><span data-stu-id="670cd-242">You will have to publish your Bot to the Azure Service every time you make changes to the Bot solution / code.</span></span>

1.  <span data-ttu-id="670cd-243">Vuelva a la solución de Visual Studio que creó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="670cd-243">Go back to your Visual Studio Solution that you created previously.</span></span> 
2.  <span data-ttu-id="670cd-244">Haga doble clic en su **MyBot** del proyecto, en el **el Explorador de soluciones**, a continuación, haga clic en **publicar**.</span><span class="sxs-lookup"><span data-stu-id="670cd-244">Right-click on your **MyBot** project, in the **Solution Explorer**, then click on **Publish**.</span></span>

    ![Publicar el Bot en el servicio Bot de aplicación Web de Azure](images/AzureLabs-Lab312-16.png)

3.  <span data-ttu-id="670cd-246">En el *elegir un destino de publicación* página, haga clic en **App Service**, a continuación, **seleccionar existente**, por último, haga clic en **Crear perfil** (es posible que deba Haga clic en la flecha desplegable junto a la *publicar* button, si esto no está visible).</span><span class="sxs-lookup"><span data-stu-id="670cd-246">On the *Pick a publish target* page, click **App Service**, then **Select Existing**, lastly click on **Create Profile** (you may need to click on the dropdown arrow alongside the *Publish* button, if this is not visible).</span></span>

    ![Publicar el Bot en el servicio Bot de aplicación Web de Azure](images/AzureLabs-Lab312-17.png)

4. <span data-ttu-id="670cd-248">Si están aún no iniciaron sesión en su Account de Microsoft, deberá hacerlo aquí.</span><span class="sxs-lookup"><span data-stu-id="670cd-248">If you are not yet logged in into your Microsoft Account, you have to do it here.</span></span>
5. <span data-ttu-id="670cd-249">En el **publicar** página encontrará tendrá que establecer el mismo **suscripción** que usó para la *Bot de Web Apps* la creación del servicio.</span><span class="sxs-lookup"><span data-stu-id="670cd-249">On the **Publish** page you will find you have to set the same **Subscription** that you used for the *Web App Bot* Service creation.</span></span> <span data-ttu-id="670cd-250">A continuación, establezca el **vista** como **grupo de recursos** y, en la lista desplegable de la estructura de carpetas, seleccione el **grupo de recursos** creado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="670cd-250">Then set the **View** as **Resource Group** and, in the drop down folder structure, select the **Resource Group** you have created previously.</span></span> <span data-ttu-id="670cd-251">Haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="670cd-251">Click **OK**.</span></span> 

    ![Publicar el Bot en el servicio Bot de aplicación Web de Azure](images/AzureLabs-Lab312-18.png)

6.  <span data-ttu-id="670cd-253">Ahora haga clic en el **publicar** botón y espere a que el Bot a publicarse (podría tardar unos minutos).</span><span class="sxs-lookup"><span data-stu-id="670cd-253">Now click on the **Publish** button, and wait for the Bot to be published (it might take a few minutes).</span></span>

    ![Publicar el Bot en el servicio Bot de aplicación Web de Azure](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a><span data-ttu-id="670cd-255">Capítulo 4: configurar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="670cd-255">Chapter 4 – Set up the Unity project</span></span>

<span data-ttu-id="670cd-256">El siguiente es un conjunto típico de para el desarrollo con la realidad mixta y por lo tanto, es una buena plantilla para otros proyectos.</span><span class="sxs-lookup"><span data-stu-id="670cd-256">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="670cd-257">Abra *Unity* y haga clic en **New**.</span><span class="sxs-lookup"><span data-stu-id="670cd-257">Open *Unity* and click **New**.</span></span> 

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-20.png)

2.  <span data-ttu-id="670cd-259">Ahora deberá proporcionar un nombre de proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="670cd-259">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="670cd-260">Insertar **Hololens Bot**.</span><span class="sxs-lookup"><span data-stu-id="670cd-260">Insert **Hololens Bot**.</span></span> <span data-ttu-id="670cd-261">Asegúrese de que la plantilla de proyecto se establece en **3D**.</span><span class="sxs-lookup"><span data-stu-id="670cd-261">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="670cd-262">Establecer el **ubicación** a algún lugar adecuado para usted (Recuerde, es mejor cuanto más se acerque a los directorios raíz).</span><span class="sxs-lookup"><span data-stu-id="670cd-262">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="670cd-263">A continuación, haga clic en **crear un proyecto**.</span><span class="sxs-lookup"><span data-stu-id="670cd-263">Then, click **Create project**.</span></span>

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-21.png)

3.  <span data-ttu-id="670cd-265">Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="670cd-265">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="670cd-266">Vaya a **Editar > Preferencias** y, a continuación, en la ventana nueva, vaya a **herramientas externas**.</span><span class="sxs-lookup"><span data-stu-id="670cd-266">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="670cd-267">Cambio **External Script Editor** a **de Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="670cd-267">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="670cd-268">Cerrar la **preferencias** ventana.</span><span class="sxs-lookup"><span data-stu-id="670cd-268">Close the **Preferences** window.</span></span>

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-22.png)

4.  <span data-ttu-id="670cd-270">A continuación, vaya a **archivo > configuración de compilación** y seleccione **Universal Windows Platform**, a continuación, haga clic en el **Cambiar plataforma** botón para aplicar la selección.</span><span class="sxs-lookup"><span data-stu-id="670cd-270">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-23.png)

5.  <span data-ttu-id="670cd-272">Mientras sigue en **archivo > configuración de compilación** y asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="670cd-272">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="670cd-273">**Dispositivo de destino** está establecido en **Hololens**</span><span class="sxs-lookup"><span data-stu-id="670cd-273">**Target Device** is set to **Hololens**</span></span>

        > <span data-ttu-id="670cd-274">Establezca el inmersivos, **dispositivo de destino** a *cualquier dispositivo*.</span><span class="sxs-lookup"><span data-stu-id="670cd-274">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2.  <span data-ttu-id="670cd-275">**Tipo de compilación** está establecido en **D3D**</span><span class="sxs-lookup"><span data-stu-id="670cd-275">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="670cd-276">**SDK** está establecido en **instalada más reciente**</span><span class="sxs-lookup"><span data-stu-id="670cd-276">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="670cd-277">**Versión de Visual Studio** está establecido en **instalada más reciente**</span><span class="sxs-lookup"><span data-stu-id="670cd-277">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="670cd-278">**Compilar y ejecutar** está establecido en **máquina Local**</span><span class="sxs-lookup"><span data-stu-id="670cd-278">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="670cd-279">Guarde la escena y agregarlo a la compilación.</span><span class="sxs-lookup"><span data-stu-id="670cd-279">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="670cd-280">Hacer esto seleccionando **agregar escenas abierto**.</span><span class="sxs-lookup"><span data-stu-id="670cd-280">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="670cd-281">Aparecerá el guardado de la ventana.</span><span class="sxs-lookup"><span data-stu-id="670cd-281">A save window will appear.</span></span>
        
            ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-24.png)

        2. <span data-ttu-id="670cd-283">Cree una nueva carpeta de esto y cualquier futuro, escena, a continuación, seleccione el **nueva carpeta** botón para crear una nueva carpeta y asígnele el nombre **escenas**.</span><span class="sxs-lookup"><span data-stu-id="670cd-283">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

             ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-25.png)

        3. <span data-ttu-id="670cd-285">Abra su recién creado **escenas** carpeta y, a continuación, en el *nombre de archivo*: campo de texto, escriba **BotScene**, a continuación, haga clic en **guardar**.</span><span class="sxs-lookup"><span data-stu-id="670cd-285">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **BotScene**, then click on **Save**.</span></span>

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-26.png)

    7. <span data-ttu-id="670cd-287">El resto de la configuración, en **configuración de compilación**, debe dejarse como predeterminada por ahora.</span><span class="sxs-lookup"><span data-stu-id="670cd-287">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6. <span data-ttu-id="670cd-288">En el *configuración de compilación* ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el *Inspector* se encuentra.</span><span class="sxs-lookup"><span data-stu-id="670cd-288">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-27.png)

7. <span data-ttu-id="670cd-290">En este panel, es necesario comprobar algunas opciones de configuración:</span><span class="sxs-lookup"><span data-stu-id="670cd-290">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="670cd-291">En el **otra configuración** pestaña:</span><span class="sxs-lookup"><span data-stu-id="670cd-291">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="670cd-292">**Versión en tiempo de ejecución de secuencias de comandos** debe ser **Experimental (NET 4.6 equivalente)**; cambiar esto requerirá un reinicio del Editor.</span><span class="sxs-lookup"><span data-stu-id="670cd-292">**Scripting Runtime Version** should be **Experimental (NET 4.6 Equivalent)**; changing this will require a restart of the Editor.</span></span>
        2. <span data-ttu-id="670cd-293">**Scripting de back-end** debe ser **.NET**</span><span class="sxs-lookup"><span data-stu-id="670cd-293">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="670cd-294">**Nivel de compatibilidad de API** debe ser **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="670cd-294">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-28.png)
      
    2. <span data-ttu-id="670cd-296">Dentro de la **configuración de publicación** ficha **capacidades**, consulte:</span><span class="sxs-lookup"><span data-stu-id="670cd-296">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="670cd-297">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="670cd-297">**InternetClient**</span></span>
        - <span data-ttu-id="670cd-298">**Micrófono**</span><span class="sxs-lookup"><span data-stu-id="670cd-298">**Microphone**</span></span>

            ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-29.png)

    3. <span data-ttu-id="670cd-300">Más abajo el panel, en **XR configuración** (bajo **configuración de publicación**), graduación **admite la realidad Virtual**, asegúrese de que el **SDK de Windows Mixed Reality**  se agrega.</span><span class="sxs-lookup"><span data-stu-id="670cd-300">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Configurar el proyecto de Unity](images/AzureLabs-Lab312-30.png)

8.  <span data-ttu-id="670cd-302">En *configuración de compilación* _Unity C#_  proyectos ya no está atenuada; Marque la casilla situada junto a esto.</span><span class="sxs-lookup"><span data-stu-id="670cd-302">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="670cd-303">Cierre la ventana de configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="670cd-303">Close the Build Settings window.</span></span>
10. <span data-ttu-id="670cd-304">Guarde la escena y el proyecto (**archivo > Guardar ESCENA / archivo > Guardar proyecto**).</span><span class="sxs-lookup"><span data-stu-id="670cd-304">Save your scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-5--camera-setup"></a><span data-ttu-id="670cd-305">Capítulo 5: configuración de cámara</span><span class="sxs-lookup"><span data-stu-id="670cd-305">Chapter 5 – Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="670cd-306">Si desea omitir la *configurar Unity* componente de este curso y continuar directamente en código, no dude en descargar este [Package.unitypackage-Azure-MR-312](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), importarlo en el proyecto como un [ **Paquete personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)y, a continuación, continuar desde [capítulo 7](#chapter-7-–-create-the-botobjects-class).</span><span class="sxs-lookup"><span data-stu-id="670cd-306">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-312-Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 7](#chapter-7-–-create-the-botobjects-class).</span></span>

1.  <span data-ttu-id="670cd-307">En el *panel jerarquía*, seleccione el **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="670cd-307">In the *Hierarchy panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="670cd-308">Una vez seleccionado, podrá ver todos los componentes de la **cámara principal** en el *panel Inspector*.</span><span class="sxs-lookup"><span data-stu-id="670cd-308">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector panel*.</span></span>

    1. <span data-ttu-id="670cd-309">El **objeto de cámara** debe denominarse **cámara principal** (tenga en cuenta la ortografía)</span><span class="sxs-lookup"><span data-stu-id="670cd-309">The **Camera object** must be named **Main Camera** (note the spelling)</span></span>
    2. <span data-ttu-id="670cd-310">La cámara principal **etiqueta** debe establecerse en **MainCamera** (tenga en cuenta la ortografía)</span><span class="sxs-lookup"><span data-stu-id="670cd-310">The Main Camera **Tag** must be set to **MainCamera** (note the spelling)</span></span>
    3. <span data-ttu-id="670cd-311">Asegúrese de que el **transformar posición** está establecido en **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="670cd-311">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="670cd-312">Establecer **borrar las marcas de** a **Color sólido**.</span><span class="sxs-lookup"><span data-stu-id="670cd-312">Set **Clear Flags** to **Solid Color**.</span></span>
    5. <span data-ttu-id="670cd-313">Establecer el **en segundo plano** Color del componente de cámara para **negro, alfa de 0 (código hexadecimal: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="670cd-313">Set the **Background** Color of the Camera component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

    ![Configuración de cámara](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a><span data-ttu-id="670cd-315">Capítulo 6: importar la biblioteca de Newtonsoft</span><span class="sxs-lookup"><span data-stu-id="670cd-315">Chapter 6 – Import the Newtonsoft library</span></span>

<span data-ttu-id="670cd-316">Para ayudarle a deserializan y serializan objetos recibidos y enviados al servicio Bot debe descargar el **Newtonsoft** biblioteca.</span><span class="sxs-lookup"><span data-stu-id="670cd-316">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the **Newtonsoft** library.</span></span> <span data-ttu-id="670cd-317">Encontrará un [versión compatible ya organizado con la correcta Unity estructura de carpetas aquí](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="670cd-317">You will find a [compatible version already organized with the correct Unity folder structure here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="670cd-318">Para importar la biblioteca de Newtonsoft en el proyecto, use el paquete de Unity que acompaña a este curso.</span><span class="sxs-lookup"><span data-stu-id="670cd-318">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="670cd-319">Agregar el *.unitypackage* a Unity mediante el uso de la **activos** > **Importar paquete** > **paquete personalizado** opción de menú.</span><span class="sxs-lookup"><span data-stu-id="670cd-319">Add the *.unitypackage* to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

    ![Importación de la biblioteca de Newtonsoft](images/AzureLabs-Lab312-34.png)

2.  <span data-ttu-id="670cd-321">En el **Importar paquete de Unity** cuadro que aparece hacia arriba, asegúrese de todo el contenido en (e incluido) **complementos** está seleccionada.</span><span class="sxs-lookup"><span data-stu-id="670cd-321">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Importación de la biblioteca de Newtonsoft](images/AzureLabs-Lab312-35.png)

3.  <span data-ttu-id="670cd-323">Haga clic en el **importación** para agregar los elementos al proyecto.</span><span class="sxs-lookup"><span data-stu-id="670cd-323">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="670cd-324">Vaya a la **Newtonsoft** carpeta bajo **complementos** en la vista de proyecto y seleccione el complemento de Newtonsoft.</span><span class="sxs-lookup"><span data-stu-id="670cd-324">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the Newtonsoft plugin.</span></span>

    ![](images/AzureLabs-Lab312-35b.png)

5.  <span data-ttu-id="670cd-325">Con el complemento de Newtonsoft seleccionado, asegúrese de que **cualquier plataforma** es **unchecked**, a continuación, asegúrese de que **WSAPlayer** también es **unchecked**, a continuación, haga clic en **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="670cd-325">With the Newtonsoft plugin selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="670cd-326">Esto es solo para confirmar que los archivos están configurados correctamente.</span><span class="sxs-lookup"><span data-stu-id="670cd-326">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > <span data-ttu-id="670cd-327">Marcar estos complementos configura para su uso en el Editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="670cd-327">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="670cd-328">Hay un conjunto diferente de ellos en la carpeta WSA que se utilizará después de que el proyecto se exporta desde Unity.</span><span class="sxs-lookup"><span data-stu-id="670cd-328">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="670cd-329">A continuación, deberá abrir el **WSA** carpeta, en el **Newtonsoft** carpeta.</span><span class="sxs-lookup"><span data-stu-id="670cd-329">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="670cd-330">Verá una copia del mismo archivo que acaba de configurar.</span><span class="sxs-lookup"><span data-stu-id="670cd-330">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="670cd-331">Seleccione el archivo y, a continuación, en el inspector, asegúrese de que</span><span class="sxs-lookup"><span data-stu-id="670cd-331">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="670cd-332">**Cualquier plataforma** es **desactivada**</span><span class="sxs-lookup"><span data-stu-id="670cd-332">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="670cd-333">**solo** **WSAPlayer** es **activada**</span><span class="sxs-lookup"><span data-stu-id="670cd-333">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="670cd-334">**No procesar** es **activada**</span><span class="sxs-lookup"><span data-stu-id="670cd-334">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a><span data-ttu-id="670cd-335">Capítulo 7: crear el BotTag</span><span class="sxs-lookup"><span data-stu-id="670cd-335">Chapter 7 – Create the BotTag</span></span>

1.  <span data-ttu-id="670cd-336">Cree un nuevo **etiqueta** objeto llamado **BotTag**.</span><span class="sxs-lookup"><span data-stu-id="670cd-336">Create a new **Tag** object called **BotTag**.</span></span> <span data-ttu-id="670cd-337">Seleccione la cámara principal de la escena.</span><span class="sxs-lookup"><span data-stu-id="670cd-337">Select the Main Camera in the scene.</span></span> <span data-ttu-id="670cd-338">Haga clic en el menú en el panel del Inspector desplegable etiqueta.</span><span class="sxs-lookup"><span data-stu-id="670cd-338">Click on the Tag drop down menu in the Inspector panel.</span></span> <span data-ttu-id="670cd-339">Haga clic en **Agregar etiqueta**.</span><span class="sxs-lookup"><span data-stu-id="670cd-339">Click on **Add Tag**.</span></span>

    ![Configuración de cámara](images/AzureLabs-Lab312-32.png)
 
2.  <span data-ttu-id="670cd-341">Haga clic en el **+** símbolos.</span><span class="sxs-lookup"><span data-stu-id="670cd-341">Click on the **+** symbol.</span></span> <span data-ttu-id="670cd-342">El nombre del nuevo **etiqueta** como **BotTag**, *guardar*.</span><span class="sxs-lookup"><span data-stu-id="670cd-342">Name the new **Tag** as **BotTag**, *Save*.</span></span>

    ![Configuración de cámara](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> <span data-ttu-id="670cd-344">**No** aplicar el **BotTag** a la cámara principal.</span><span class="sxs-lookup"><span data-stu-id="670cd-344">**Do not** apply the **BotTag** to the Main Camera.</span></span> <span data-ttu-id="670cd-345">Si accidentalmente lo ha hecho, no olvide cambiar la cámara principal al etiqueta *MainCamera*.</span><span class="sxs-lookup"><span data-stu-id="670cd-345">If you have accidentally done this, make sure to change the Main Camera tag back to *MainCamera*.</span></span>

## <a name="chapter-8--create-the-botobjects-class"></a><span data-ttu-id="670cd-346">Capítulo 8: crear la clase BotObjects</span><span class="sxs-lookup"><span data-stu-id="670cd-346">Chapter 8 – Create the BotObjects class</span></span>

<span data-ttu-id="670cd-347">Es el primer script, deberá crear el **BotObjects** (clase), que es una clase vacía que se crean de modo que se puede almacenar una serie de otros objetos de clase dentro de la misma secuencia de comandos y el acceso a otros scripts de la escena.</span><span class="sxs-lookup"><span data-stu-id="670cd-347">The first script you need to create is the **BotObjects** class, which is an empty class created so that a series of other class objects can be stored within the same script and accessed by other scripts in the scene.</span></span>

<span data-ttu-id="670cd-348">La creación de esta clase es puramente una opción de arquitectura, estos objetos podrían hospedarse en su lugar en el script de Bot que creará más adelante en este curso.</span><span class="sxs-lookup"><span data-stu-id="670cd-348">The creation of this class is purely an architectural choice, these objects could instead be hosted in the Bot script that you will create later in this course.</span></span>

<span data-ttu-id="670cd-349">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="670cd-349">To create this class:</span></span> 

1.  <span data-ttu-id="670cd-350">Haga clic en el *panel proyecto*, a continuación, **crear > carpeta**.</span><span class="sxs-lookup"><span data-stu-id="670cd-350">Right-click in the *Project panel*, then **Create > Folder**.</span></span> <span data-ttu-id="670cd-351">Nombre de la carpeta **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="670cd-351">Name the folder **Scripts**.</span></span> 

    ![Crear carpeta de scripts.](images/AzureLabs-Lab312-36.png)

2.  <span data-ttu-id="670cd-353">Haga doble clic en el **Scripts** carpeta para abrirla.</span><span class="sxs-lookup"><span data-stu-id="670cd-353">Double-click on the **Scripts** folder to open it.</span></span> <span data-ttu-id="670cd-354">A continuación, dentro de esa carpeta, contextual y seleccione **crear > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="670cd-354">Then within that folder, right-click, and select **Create > C# Script**.</span></span> <span data-ttu-id="670cd-355">Nombre de la secuencia de comandos **BotObjects**.</span><span class="sxs-lookup"><span data-stu-id="670cd-355">Name the script **BotObjects**.</span></span> 

3.  <span data-ttu-id="670cd-356">Haga doble clic en el nuevo **BotObjects** script para abrirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="670cd-356">Double-click on the new **BotObjects** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="670cd-357">Elimine el contenido de la secuencia de comandos y reemplazarlo por el código siguiente:</span><span class="sxs-lookup"><span data-stu-id="670cd-357">Delete the content of the script and replace it with the following code:</span></span>

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

6.  <span data-ttu-id="670cd-358">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="670cd-358">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--create-the-gazeinput-class"></a><span data-ttu-id="670cd-359">Capítulo 9: crear la clase GazeInput</span><span class="sxs-lookup"><span data-stu-id="670cd-359">Chapter 9 – Create the GazeInput class</span></span>

<span data-ttu-id="670cd-360">La siguiente clase que se va a crear es la **GazeInput** clase.</span><span class="sxs-lookup"><span data-stu-id="670cd-360">The next class you are going to create is the **GazeInput** class.</span></span> <span data-ttu-id="670cd-361">Esta clase es responsable de:</span><span class="sxs-lookup"><span data-stu-id="670cd-361">This class is responsible for:</span></span>

- <span data-ttu-id="670cd-362">Creación de un cursor que representará el *que mirar* del Reproductor.</span><span class="sxs-lookup"><span data-stu-id="670cd-362">Creating a cursor that will represent the *gaze* of the player.</span></span>
- <span data-ttu-id="670cd-363">Detección de objetos que se vea afectados por la mirada del Reproductor y que contiene una referencia a objetos detectados.</span><span class="sxs-lookup"><span data-stu-id="670cd-363">Detecting objects hit by the gaze of the player, and holding a reference to detected objects.</span></span>

<span data-ttu-id="670cd-364">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="670cd-364">To create this class:</span></span> 

1.  <span data-ttu-id="670cd-365">Vaya a la **Scripts** carpeta que creó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="670cd-365">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="670cd-366">Haga clic en la carpeta, **crear > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="670cd-366">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="670cd-367">Llame al script **GazeInput**.</span><span class="sxs-lookup"><span data-stu-id="670cd-367">Call the script **GazeInput**.</span></span> 
3.  <span data-ttu-id="670cd-368">Haga doble clic en el nuevo **GazeInput** script para abrirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="670cd-368">Double-click on the new **GazeInput** script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="670cd-369">Inserte la siguiente línea justo encima del nombre de clase:</span><span class="sxs-lookup"><span data-stu-id="670cd-369">Insert the following line right on top of the class name:</span></span>

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  <span data-ttu-id="670cd-370">A continuación, agregue las siguientes variables dentro de la **GazeInput** clase encima el **Start()** método:</span><span class="sxs-lookup"><span data-stu-id="670cd-370">Then add the following variables inside the **GazeInput** class, above the **Start()** method:</span></span>

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

6.  <span data-ttu-id="670cd-371">El código para **Start()** se debe agregar el método.</span><span class="sxs-lookup"><span data-stu-id="670cd-371">Code for **Start()** method should be added.</span></span> <span data-ttu-id="670cd-372">Se llamará cuando se inicializa la clase:</span><span class="sxs-lookup"><span data-stu-id="670cd-372">This will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="670cd-373">Implementar un método que va a crear una instancia y el cursor mirada de instalación:</span><span class="sxs-lookup"><span data-stu-id="670cd-373">Implement a method that will instantiate and setup the gaze cursor:</span></span> 

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

8.  <span data-ttu-id="670cd-374">Implemente los métodos que le permitirán configurar el Raycast desde la cámara principal y realizará el seguimiento del objeto foco actual.</span><span class="sxs-lookup"><span data-stu-id="670cd-374">Implement the methods that will setup the Raycast from the Main Camera and will keep track of the current focused object.</span></span>

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
 
9.  <span data-ttu-id="670cd-375">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="670cd-375">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10--create-the-bot-class"></a><span data-ttu-id="670cd-376">Capítulo 10: crear la clase de Bot</span><span class="sxs-lookup"><span data-stu-id="670cd-376">Chapter 10 – Create the Bot class</span></span>

<span data-ttu-id="670cd-377">El script que se va a crear ahora se llama **Bot**.</span><span class="sxs-lookup"><span data-stu-id="670cd-377">The script you are going to create now is called **Bot**.</span></span> <span data-ttu-id="670cd-378">Esta es la clase principal de la aplicación, almacena:</span><span class="sxs-lookup"><span data-stu-id="670cd-378">This is the core class of your application, it stores:</span></span> 

- <span data-ttu-id="670cd-379">Las credenciales de Bot de Web Apps</span><span class="sxs-lookup"><span data-stu-id="670cd-379">Your Web App Bot credentials</span></span>
- <span data-ttu-id="670cd-380">El método que se recopilan en los comandos de voz del usuario</span><span class="sxs-lookup"><span data-stu-id="670cd-380">The method that collects the user voice commands</span></span>
- <span data-ttu-id="670cd-381">El método necesario iniciar conversaciones con el Bot de aplicación Web</span><span class="sxs-lookup"><span data-stu-id="670cd-381">The method necessary to initiate conversations with your Web App Bot</span></span> 
- <span data-ttu-id="670cd-382">El método necesario enviar mensajes a su Bot de aplicación Web</span><span class="sxs-lookup"><span data-stu-id="670cd-382">The method necessary to send messages to your Web App Bot</span></span> 

<span data-ttu-id="670cd-383">Para enviar mensajes a Bot Service, el **SendMessageToBot()** corrutina creará una actividad, que es un objeto de Bot Framework reconocido como datos enviados por el usuario.</span><span class="sxs-lookup"><span data-stu-id="670cd-383">To send messages to the Bot Service, the **SendMessageToBot()** coroutine will build an activity, which is an object recognized by the Bot Framework as data sent by the user.</span></span> 
 
<span data-ttu-id="670cd-384">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="670cd-384">To create this class:</span></span> 

1. <span data-ttu-id="670cd-385">Haga doble clic en el **Scripts** carpeta para abrirla.</span><span class="sxs-lookup"><span data-stu-id="670cd-385">Double-click on the **Scripts** folder, to open it.</span></span> 
2. <span data-ttu-id="670cd-386">Haga clic en el **Scripts** carpeta, haga clic en **crear > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="670cd-386">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="670cd-387">Nombre de la secuencia de comandos **Bot**.</span><span class="sxs-lookup"><span data-stu-id="670cd-387">Name the script **Bot**.</span></span> 
3. <span data-ttu-id="670cd-388">Haga doble clic en el nuevo script para abrirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="670cd-388">Double-click on the new script to open it with Visual Studio.</span></span>
4. <span data-ttu-id="670cd-389">Actualice los espacios de nombres para que sea igual a lo siguiente en la parte superior de la **Bot** clase:</span><span class="sxs-lookup"><span data-stu-id="670cd-389">Update the namespaces to be the same as the following, at the top of the **Bot** class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. <span data-ttu-id="670cd-390">Dentro de la **Bot** clase agregue las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="670cd-390">Inside the **Bot** class add the following variables:</span></span>

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
    > <span data-ttu-id="670cd-391">Asegúrese de insertar el **clave secreta de Bot** en el **botSecret** variable.</span><span class="sxs-lookup"><span data-stu-id="670cd-391">Make sure you insert your **Bot Secret Key** into the **botSecret** variable.</span></span> <span data-ttu-id="670cd-392">Habrá anotó la **clave secreta de Bot** al principio de este curso, en  **[capítulo 2](#chapter-2---create-the-azure-bot-service), paso 10**.</span><span class="sxs-lookup"><span data-stu-id="670cd-392">You will have noted your **Bot Secret Key** at the beginning of this course, in **[Chapter 2](#chapter-2---create-the-azure-bot-service), step 10**.</span></span>

7. <span data-ttu-id="670cd-393">El código para **Awake()** y **Start()** ahora debe agregarse.</span><span class="sxs-lookup"><span data-stu-id="670cd-393">Code for **Awake()** and **Start()** now needs to be added.</span></span> 

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

8. <span data-ttu-id="670cd-394">Agregue los dos controladores que se llama a las bibliotecas de voz cuando la captura de voz comienza y termina.</span><span class="sxs-lookup"><span data-stu-id="670cd-394">Add the two handlers that are called by the speech libraries when voice capture begins and ends.</span></span> <span data-ttu-id="670cd-395">El *DictationRecognizer* automáticamente dejará de capturar la voz del usuario cuando el usuario deja de habla.</span><span class="sxs-lookup"><span data-stu-id="670cd-395">The *DictationRecognizer* will automatically stop capturing the user voice when the user stops speaking.</span></span>

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

1. <span data-ttu-id="670cd-396">El siguiente controlador recopila el resultado de la entrada de voz del usuario y llama a la corrutina responsable de enviar el mensaje al servicio de Bot de aplicación Web.</span><span class="sxs-lookup"><span data-stu-id="670cd-396">The following handler collects the result of the user voice input and calls the coroutine responsible for sending the message to the Web App Bot Service.</span></span>

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

10. <span data-ttu-id="670cd-397">Se llama a la corrutina siguiente para iniciar una conversación con el Bot.</span><span class="sxs-lookup"><span data-stu-id="670cd-397">The following coroutine is called to begin a conversation with the Bot.</span></span> <span data-ttu-id="670cd-398">Observará que una vez completada la llamada de la conversación, llamará el **SendMessageToCoroutine()** pasando una serie de parámetros que se establecerá la actividad para enviarse al servicio Bot como un mensaje vacío.</span><span class="sxs-lookup"><span data-stu-id="670cd-398">You will notice that once the conversation call is complete, it will call the **SendMessageToCoroutine()** by passing a series of parameters that will set the activity to be sent to the Bot Service as an empty message.</span></span> <span data-ttu-id="670cd-399">Esto sirve para solicitar el servicio de bots para iniciar el cuadro de diálogo.</span><span class="sxs-lookup"><span data-stu-id="670cd-399">This is done to prompt the Bot Service to initiate the dialogue.</span></span>

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

11. <span data-ttu-id="670cd-400">Se llama a la corrutina siguiente para crear la actividad para enviarse al servicio de bots.</span><span class="sxs-lookup"><span data-stu-id="670cd-400">The following coroutine is called to build the activity to be sent to the Bot Service.</span></span> 

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

12. <span data-ttu-id="670cd-401">La corrutina siguiente se llama para solicitar una respuesta después de enviar una actividad para el servicio Bot.</span><span class="sxs-lookup"><span data-stu-id="670cd-401">The following coroutine is called to request a response after sending an activity to the Bot Service.</span></span> 

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

13. <span data-ttu-id="670cd-402">El último método que se agregarán a esta clase, es necesario para mostrar el mensaje de la escena:</span><span class="sxs-lookup"><span data-stu-id="670cd-402">The last method to be added to this class, is required to display the message in the scene:</span></span>

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
    > <span data-ttu-id="670cd-403">Verá un error en la consola Editor de Unity, falta la **SceneOrganiser** clase.</span><span class="sxs-lookup"><span data-stu-id="670cd-403">You may see an error within the Unity Editor Console, about missing the **SceneOrganiser** class.</span></span> <span data-ttu-id="670cd-404">Pasar por alto este mensaje, ya que creará esta clase más adelante en el tutorial.</span><span class="sxs-lookup"><span data-stu-id="670cd-404">Disregard this message, as you will create this class later in the tutorial.</span></span>

14.  <span data-ttu-id="670cd-405">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="670cd-405">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11--create-the-interactions-class"></a><span data-ttu-id="670cd-406">Capítulo 11: crear la clase interacciones</span><span class="sxs-lookup"><span data-stu-id="670cd-406">Chapter 11 – Create the Interactions class</span></span>

<span data-ttu-id="670cd-407">La clase que se va a crear ahora se denomina **interacciones**.</span><span class="sxs-lookup"><span data-stu-id="670cd-407">The class you are going to create now is called **Interactions**.</span></span> <span data-ttu-id="670cd-408">Esta clase se utiliza para detectar la HoloLens pulse entrada del usuario.</span><span class="sxs-lookup"><span data-stu-id="670cd-408">This class is used to detect the HoloLens Tap Input from the user.</span></span> 

<span data-ttu-id="670cd-409">Si el usuario puntea al examinar el *Bot* objeto en la escena y el Bot está listo para realizar escuchas para las entradas de voz, el objeto de Bot cambiará de color a **rojo** y empezar a escuchar las entradas de voz.</span><span class="sxs-lookup"><span data-stu-id="670cd-409">If the user taps while looking at the *Bot* object in the scene, and the Bot is ready to listen for voice inputs, the Bot object will change color to **red** and begin listening for voice inputs.</span></span> 

<span data-ttu-id="670cd-410">Esta clase hereda de la **GazeInput** clase por lo que es capaz de hacer referencia a la **Start()** método y variables de esa clase, que se indica mediante el uso de **base**.</span><span class="sxs-lookup"><span data-stu-id="670cd-410">This class inherits from the **GazeInput** class, and so is able to reference the **Start()** method and variables from that class, denoted by the use of **base**.</span></span> 
 
<span data-ttu-id="670cd-411">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="670cd-411">To create this class:</span></span>

1.  <span data-ttu-id="670cd-412">Haga doble clic en el **Scripts** carpeta para abrirla.</span><span class="sxs-lookup"><span data-stu-id="670cd-412">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="670cd-413">Haga clic en el **Scripts** carpeta, haga clic en **crear > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="670cd-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="670cd-414">Nombre de la secuencia de comandos **interacciones**.</span><span class="sxs-lookup"><span data-stu-id="670cd-414">Name the script **Interactions**.</span></span> 
3.  <span data-ttu-id="670cd-415">Haga doble clic en el nuevo script para abrirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="670cd-415">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="670cd-416">Actualice los espacios de nombres y la herencia de clases para ser el mismo que el siguiente, en la parte superior de la **interacciones** clase:</span><span class="sxs-lookup"><span data-stu-id="670cd-416">Update the namespaces and the class inheritance to be the same as the following, at the top of the **Interactions** class:</span></span>

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  <span data-ttu-id="670cd-417">Dentro de la **interacciones** clase agregue la siguiente variable:</span><span class="sxs-lookup"><span data-stu-id="670cd-417">Inside the **Interactions** class add the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  <span data-ttu-id="670cd-418">A continuación, agregue el **Start()** método:</span><span class="sxs-lookup"><span data-stu-id="670cd-418">Then add the **Start()** method:</span></span>

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

7.  <span data-ttu-id="670cd-419">Agregue el controlador que se desencadena cuando el usuario realiza el gesto de pulsar delante de la cámara de HoloLens</span><span class="sxs-lookup"><span data-stu-id="670cd-419">Add the handler that will be triggered when the user performs the tap gesture in front of the HoloLens camera</span></span>

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

8. <span data-ttu-id="670cd-420">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="670cd-420">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-12--create-the-sceneorganiser-class"></a><span data-ttu-id="670cd-421">Capítulo 12: crear la clase SceneOrganiser</span><span class="sxs-lookup"><span data-stu-id="670cd-421">Chapter 12 – Create the SceneOrganiser class</span></span>

<span data-ttu-id="670cd-422">Se llama a la última clase necesaria en este laboratorio **SceneOrganiser**.</span><span class="sxs-lookup"><span data-stu-id="670cd-422">The last class required in this Lab is called **SceneOrganiser**.</span></span> <span data-ttu-id="670cd-423">Esta clase configurará la escena mediante programación, agregando componentes y las secuencias de comandos a la cámara principal, y crear los objetos adecuados en la escena.</span><span class="sxs-lookup"><span data-stu-id="670cd-423">This class will setup the scene programmatically, by adding components and scripts to the Main Camera, and creating the appropriate objects in the scene.</span></span>
 
<span data-ttu-id="670cd-424">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="670cd-424">To create this class:</span></span>

1.  <span data-ttu-id="670cd-425">Haga doble clic en el **Scripts** carpeta para abrirla.</span><span class="sxs-lookup"><span data-stu-id="670cd-425">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="670cd-426">Haga clic en el **Scripts** carpeta, haga clic en **crear > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="670cd-426">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="670cd-427">Nombre de la secuencia de comandos **SceneOrganiser**.</span><span class="sxs-lookup"><span data-stu-id="670cd-427">Name the script **SceneOrganiser**.</span></span> 
3.  <span data-ttu-id="670cd-428">Haga doble clic en el nuevo script para abrirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="670cd-428">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="670cd-429">Dentro de la **SceneOrganiser** clase agregue las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="670cd-429">Inside the **SceneOrganiser** class add the following variables:</span></span>

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

6.  <span data-ttu-id="670cd-430">A continuación, agregue el **Awake()** y **Start()** métodos:</span><span class="sxs-lookup"><span data-stu-id="670cd-430">Then add the **Awake()** and **Start()** methods:</span></span>

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

7.  <span data-ttu-id="670cd-431">Agregue el siguiente método, responsable de crear el objeto de Bot en la escena y la configuración de los parámetros y los componentes:</span><span class="sxs-lookup"><span data-stu-id="670cd-431">Add the following method, responsible for creating the Bot object in the scene and setting up the parameters and components:</span></span>

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

7.  <span data-ttu-id="670cd-432">Agregue el siguiente método, responsable de crear el objeto de interfaz de usuario de la escena, que representa las respuestas del Bot:</span><span class="sxs-lookup"><span data-stu-id="670cd-432">Add the following method, responsible for creating the UI object in the scene, representing the responses from the Bot:</span></span>

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

8.  <span data-ttu-id="670cd-433">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="670cd-433">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
9.  <span data-ttu-id="670cd-434">En el Editor de Unity, arrastre el **SceneOrganiser** script desde la carpeta de Scripts a la cámara principal.</span><span class="sxs-lookup"><span data-stu-id="670cd-434">In the Unity Editor, drag the **SceneOrganiser** script from the Scripts folder to the Main Camera.</span></span> <span data-ttu-id="670cd-435">El componente de la escena organizador debería aparecer ahora en el objeto de cámara principal, como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="670cd-435">The Scene Organiser component should now appear on the Main Camera object, as shown in the image below.</span></span>

    ![Crear el servicio de Azure Bot](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a><span data-ttu-id="670cd-437">Capítulo 13: antes de compilar</span><span class="sxs-lookup"><span data-stu-id="670cd-437">Chapter 13 – Before building</span></span>

<span data-ttu-id="670cd-438">Para llevar a cabo una prueba completa de la aplicación se necesitará para transferir localmente en su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="670cd-438">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="670cd-439">Antes de hacerlo, asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="670cd-439">Before you do, ensure that:</span></span>

-   <span data-ttu-id="670cd-440">Todas las configuraciones que se mencionan en la [ **Chapter 4** ](#Chapter-4-–-Set-up-the-unity-project) están establecidas correctamente.</span><span class="sxs-lookup"><span data-stu-id="670cd-440">All the settings mentioned in the [**Chapter 4**](#Chapter-4-–-Set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="670cd-441">La secuencia de comandos **SceneOrganiser** está asociado a la **cámara principal** objeto.</span><span class="sxs-lookup"><span data-stu-id="670cd-441">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="670cd-442">En el **Bot** class, asegúrese de que haya insertado el **clave secreta de Bot** en el **botSecret** variable.</span><span class="sxs-lookup"><span data-stu-id="670cd-442">In the **Bot** class, make sure you have inserted your **Bot Secret Key** into the **botSecret** variable.</span></span>

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a><span data-ttu-id="670cd-443">Capítulo 14: compilación y transfiérala localmente para el HoloLens</span><span class="sxs-lookup"><span data-stu-id="670cd-443">Chapter 14 – Build and Sideload to the HoloLens</span></span>

<span data-ttu-id="670cd-444">Todo lo necesario para la sección de Unity de este proyecto ahora se completó, por lo que es el momento de crearla desde Unity.</span><span class="sxs-lookup"><span data-stu-id="670cd-444">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="670cd-445">Vaya a **configuración de compilación**, **archivo > configuración de compilación...** .</span><span class="sxs-lookup"><span data-stu-id="670cd-445">Navigate to **Build Settings**, **File > Build Settings…**.</span></span>
2.  <span data-ttu-id="670cd-446">Desde el **configuración de compilación** ventana, haga clic en **compilar**.</span><span class="sxs-lookup"><span data-stu-id="670cd-446">From the **Build Settings** window, click **Build**.</span></span>

    ![Creación de la aplicación de Unity](images/AzureLabs-Lab312-38.png)

3.  <span data-ttu-id="670cd-448">Si aún no marque **Unity C# proyectos**.</span><span class="sxs-lookup"><span data-stu-id="670cd-448">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="670cd-449">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="670cd-449">Click **Build**.</span></span> <span data-ttu-id="670cd-450">Unity se iniciará un **Explorador de archivos** ventana, donde se debe crear y, a continuación, seleccione una carpeta para compilar la aplicación en.</span><span class="sxs-lookup"><span data-stu-id="670cd-450">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="670cd-451">Crear la carpeta y asígnele el nombre **aplicación**.</span><span class="sxs-lookup"><span data-stu-id="670cd-451">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="670cd-452">A continuación, con el **aplicación** carpeta seleccionada, haga clic en **seleccionar la carpeta**.</span><span class="sxs-lookup"><span data-stu-id="670cd-452">Then with the **App** folder selected, click **Select Folder**.</span></span> 
5.  <span data-ttu-id="670cd-453">Unity empezará a compilar el proyecto para el **aplicación** carpeta.</span><span class="sxs-lookup"><span data-stu-id="670cd-453">Unity will begin building your project to the **App** folder.</span></span> 
6.  <span data-ttu-id="670cd-454">Una vez Unity ha finalizado la compilación (puede tardar algún tiempo), se abrirá un **Explorador de archivos** ventana en la ubicación de la compilación (comprobación de la barra de tareas, tal y como es posible que no siempre aparecen por encima de las ventanas, pero le informará de la adición de un nuevo ventana).</span><span class="sxs-lookup"><span data-stu-id="670cd-454">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-15--deploy-to-hololens"></a><span data-ttu-id="670cd-455">Capítulo 15: implementar en HoloLens</span><span class="sxs-lookup"><span data-stu-id="670cd-455">Chapter 15 – Deploy to HoloLens</span></span>

<span data-ttu-id="670cd-456">Para implementar en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="670cd-456">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="670cd-457">Necesitará la dirección IP de su HoloLens (para la implementación remota), y garantizar su HoloLens se encuentra en **modo de programador**.</span><span class="sxs-lookup"><span data-stu-id="670cd-457">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="670cd-458">Para ello:</span><span class="sxs-lookup"><span data-stu-id="670cd-458">To do this:</span></span>

    1. <span data-ttu-id="670cd-459">Mientras que el exceso de su HoloLens, abra el **configuración**.</span><span class="sxs-lookup"><span data-stu-id="670cd-459">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="670cd-460">Vaya a **red e Internet > Wi-Fi > Opciones avanzadas**</span><span class="sxs-lookup"><span data-stu-id="670cd-460">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="670cd-461">Tenga en cuenta la **IPv4** dirección.</span><span class="sxs-lookup"><span data-stu-id="670cd-461">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="670cd-462">A continuación, vaya a **configuración**y, a continuación, para **actualización y seguridad > para desarrolladores**</span><span class="sxs-lookup"><span data-stu-id="670cd-462">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="670cd-463">Activar el modo de programador.</span><span class="sxs-lookup"><span data-stu-id="670cd-463">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="670cd-464">Vaya a la nueva compilación de Unity (la **aplicación** carpeta) y abra el archivo de solución con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="670cd-464">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>
3.  <span data-ttu-id="670cd-465">En el **configuración de la solución** seleccione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="670cd-465">In the **Solution Configuration** select **Debug**.</span></span>
4.  <span data-ttu-id="670cd-466">En el **plataforma de solución**, seleccione **x86**, **máquina remota**.</span><span class="sxs-lookup"><span data-stu-id="670cd-466">In the **Solution Platform**, select **x86**, **Remote Machine**.</span></span> 

    ![Implementar la solución de Visual Studio.](images/AzureLabs-Lab312-39.png)
 
5.  <span data-ttu-id="670cd-468">Vaya a la **menú compilar** y haga clic en **implementar solución**, para transferir localmente la aplicación a su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="670cd-468">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="670cd-469">La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas en su HoloLens, lista para iniciarse.</span><span class="sxs-lookup"><span data-stu-id="670cd-469">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

    > [!NOTE]
    > <span data-ttu-id="670cd-470">Para implementar en los auriculares envolventes, establezca el **plataforma de solución** a *máquina Local*y establezca el **configuración** a *depurar*, con *x86* como el **plataforma**.</span><span class="sxs-lookup"><span data-stu-id="670cd-470">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="670cd-471">Implementar, a continuación, en el equipo local machine, utilizando el **menú compilar**, seleccionar *implementar solución*.</span><span class="sxs-lookup"><span data-stu-id="670cd-471">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="chapter-16--using-the-application-on-the-hololens"></a><span data-ttu-id="670cd-472">Capítulo 16: uso de la aplicación en el HoloLens</span><span class="sxs-lookup"><span data-stu-id="670cd-472">Chapter 16 – Using the application on the HoloLens</span></span>

- <span data-ttu-id="670cd-473">Una vez que haya iniciado la aplicación, verá el Bot como una esfera azul delante de usted.</span><span class="sxs-lookup"><span data-stu-id="670cd-473">Once you have launched the application, you will see the Bot as a blue sphere in front of you.</span></span>

- <span data-ttu-id="670cd-474">Use la **gesto de pulsar** mientras se gazing en la esfera para iniciar una conversación.</span><span class="sxs-lookup"><span data-stu-id="670cd-474">Use the **Tap Gesture** while you are gazing at the sphere to initiate a conversation.</span></span> 
 
- <span data-ttu-id="670cd-475">Espere a que la conversación iniciar (la interfaz de usuario se mostrará un mensaje cuando ocurre).</span><span class="sxs-lookup"><span data-stu-id="670cd-475">Wait for the conversation to start (The UI will display a message when it happens).</span></span> <span data-ttu-id="670cd-476">Una vez que reciba un mensaje de la introducción del Bot, pulse de nuevo en el Bot para que se vuelven de color rojo y empezar a escuchar su voz.</span><span class="sxs-lookup"><span data-stu-id="670cd-476">Once you receive the introductory message from the Bot, tap again on the Bot so it will turn red and begin to listen to your voice.</span></span> 

- <span data-ttu-id="670cd-477">Una vez detenido hablando, la aplicación enviará el mensaje al Bot y con prontitud recibirán una respuesta que se mostrará en la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="670cd-477">Once you stop talking, your application will send your message to the Bot and you will promptly receive a response that will be displayed in the UI.</span></span> 

- <span data-ttu-id="670cd-478">Repita el proceso para enviar más mensajes a su Bot (que tiene que puntear en cada vez que desee enviar un mensaje).</span><span class="sxs-lookup"><span data-stu-id="670cd-478">Repeat the process to send more messages to your Bot (you have to tap each time you want to sen a message).</span></span>

<span data-ttu-id="670cd-479">Esta conversación, muestra cómo el Bot pueda conservar la información (su nombre), mientras que también proporciona la información conocida (por ejemplo, los elementos que se almacenó).</span><span class="sxs-lookup"><span data-stu-id="670cd-479">This conversation demonstrates how the Bot can retain information (your name), whilst also providing known information (such as the items that are stocked).</span></span>

#### <a name="some-questions-to-ask-the-bot"></a><span data-ttu-id="670cd-480">Algunas preguntas para formular el Bot:</span><span class="sxs-lookup"><span data-stu-id="670cd-480">Some questions to ask the Bot:</span></span>

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a><span data-ttu-id="670cd-481">La aplicación finalizada de Bot de Web Apps (v4)</span><span class="sxs-lookup"><span data-stu-id="670cd-481">Your finished Web App Bot (v4) application</span></span>

<span data-ttu-id="670cd-482">Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha el Bot de aplicación Web de Azure, Microsoft Bot Framework v4.</span><span class="sxs-lookup"><span data-stu-id="670cd-482">Congratulations, you built a mixed reality app that leverages the Azure Web App Bot, Microsoft Bot Framework v4.</span></span>

![Final producto](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="670cd-484">Ejercicios de bonificación</span><span class="sxs-lookup"><span data-stu-id="670cd-484">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="670cd-485">Ejercicio 1</span><span class="sxs-lookup"><span data-stu-id="670cd-485">Exercise 1</span></span>

<span data-ttu-id="670cd-486">La estructura de la conversación en este laboratorio es muy básica.</span><span class="sxs-lookup"><span data-stu-id="670cd-486">The conversation structure in this Lab is very basic.</span></span> <span data-ttu-id="670cd-487">Uso de LUIS de Microsoft para proporcionar capacidades de comprensión de lenguaje natural a su bot.</span><span class="sxs-lookup"><span data-stu-id="670cd-487">Use Microsoft LUIS to give your bot natural language understanding capabilities.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="670cd-488">Ejercicio 2</span><span class="sxs-lookup"><span data-stu-id="670cd-488">Exercise 2</span></span>

<span data-ttu-id="670cd-489">En este ejemplo no incluyen finalizar una conversación y el reinicio de una nueva.</span><span class="sxs-lookup"><span data-stu-id="670cd-489">This example does not include terminating a conversation and restarting a new one.</span></span> <span data-ttu-id="670cd-490">Para hacer que el Bot que todas las características, intente implementar el cierre para la conversación.</span><span class="sxs-lookup"><span data-stu-id="670cd-490">To make the Bot feature complete, try to implement closure to the conversation.</span></span>
