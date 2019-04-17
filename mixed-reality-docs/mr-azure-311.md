---
title: El Sr. y 311 - Microsoft Graph de Azure
description: Realice este curso para obtener información sobre cómo aprovechar Microsoft Graph y conectarse a los datos que impulsan la productividad, dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidad mixta, Azure, academy, unity, tutorial, api, graph de microsoft, hololens, envolventes, vr
ms.openlocfilehash: 98fe2c872f332a21fff3af6751ae555968073a24
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597658"
---
>[!NOTE]
><span data-ttu-id="78584-104">Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.</span><span class="sxs-lookup"><span data-stu-id="78584-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="78584-105">Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="78584-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="78584-106">Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.</span><span class="sxs-lookup"><span data-stu-id="78584-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="78584-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="78584-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="78584-108">Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="78584-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="78584-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.</span><span class="sxs-lookup"><span data-stu-id="78584-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

# <a name="mr-and-azure-311---microsoft-graph"></a><span data-ttu-id="78584-110">El Sr. y 311 - Microsoft Graph de Azure</span><span class="sxs-lookup"><span data-stu-id="78584-110">MR and Azure 311 - Microsoft Graph</span></span>

<span data-ttu-id="78584-111">En este curso, obtendrá información sobre cómo usar *Microsoft Graph* para iniciar sesión en tu cuenta Microsoft con autenticación segura dentro de una aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="78584-111">In this course, you will learn how to use *Microsoft Graph* to log in into your Microsoft account using secure authentication within a mixed reality application.</span></span> <span data-ttu-id="78584-112">A continuación, recuperará y mostrar sus reuniones programadas en la interfaz de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="78584-112">You will then retrieve and display your scheduled meetings in the application interface.</span></span>

![](images/AzureLabs-Lab311-00.png)

<span data-ttu-id="78584-113">*Microsoft Graph* es un conjunto de API que se ha diseñado para permitir el acceso a muchos de los servicios de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="78584-113">*Microsoft Graph* is a set of APIs designed to enable access to many of Microsoft's services.</span></span> <span data-ttu-id="78584-114">Microsoft describe Microsoft Graph como una matriz de los recursos conectados mediante relaciones, lo que significa que permite que una aplicación tener acceso a todo tipo de datos de usuario conectado.</span><span class="sxs-lookup"><span data-stu-id="78584-114">Microsoft describes Microsoft Graph as being a matrix of resources connected by relationships, meaning it allows an application to access all sorts of connected user data.</span></span> <span data-ttu-id="78584-115">Para obtener más información, visite la [página de Microsoft Graph](https://developer.microsoft.com/graph).</span><span class="sxs-lookup"><span data-stu-id="78584-115">For more information, visit the [Microsoft Graph page](https://developer.microsoft.com/graph).</span></span>

<span data-ttu-id="78584-116">Desarrollo incluirá la creación de una aplicación donde el usuario le indicará que mire y, a continuación, puntee en una esfera, que se le pedirá al usuario que inicie sesión con seguridad en una cuenta de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="78584-116">Development will include the creation of an app where the user will be instructed to gaze at and then tap a sphere, which will prompt the user to log in safely to a Microsoft account.</span></span> <span data-ttu-id="78584-117">Una vez que inicia sesión en su cuenta, el usuario podrá ver una lista de las reuniones programadas para el día.</span><span class="sxs-lookup"><span data-stu-id="78584-117">Once logged in to their account, the user will be able to see a list of meetings scheduled for the day.</span></span>

<span data-ttu-id="78584-118">Una vez completado este curso, tendrá una realidad mixta HoloLens aplicación, que podrá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="78584-118">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="78584-119">Con el gesto de pulsar, puntee en un objeto que se le pedirá al usuario iniciar sesión en un Account de Microsoft (sale de la aplicación para iniciar sesión y, a continuación, volver a la aplicación).</span><span class="sxs-lookup"><span data-stu-id="78584-119">Using the Tap gesture, tap on an object, which will prompt the user to log into a Microsoft Account (moving out of the app to log in, and then back into the app again).</span></span>
2.  <span data-ttu-id="78584-120">Ver una lista de las reuniones programadas para el día.</span><span class="sxs-lookup"><span data-stu-id="78584-120">View a list of meetings scheduled for the day.</span></span> 

<span data-ttu-id="78584-121">En la aplicación, es depende de usted sobre cómo se integrará los resultados con el diseño.</span><span class="sxs-lookup"><span data-stu-id="78584-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="78584-122">Este curso está diseñado para mostrarle cómo integrar un servicio de Azure con el proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="78584-122">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="78584-123">Es su trabajo consiste en usar los conocimientos que obtendrá de este curso para mejorar las aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="78584-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="78584-124">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="78584-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="78584-125">Curso</span><span class="sxs-lookup"><span data-stu-id="78584-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="78584-126"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="78584-126"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="78584-127"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="78584-127"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="78584-128">El Sr. y 311 de Azure: Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="78584-128">MR and Azure 311: Microsoft Graph</span></span></td><td style="text-align: center;"> <span data-ttu-id="78584-129">✔️</span><span class="sxs-lookup"><span data-stu-id="78584-129">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="78584-130">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="78584-130">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="78584-131">Este tutorial está diseñado para los desarrolladores con experiencia básica con Unity y C#.</span><span class="sxs-lookup"><span data-stu-id="78584-131">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="78584-132">También Ten en cuenta que los requisitos previos y las instrucciones escritas en este documento representan lo que se ha probado y comprobado en el momento de redactar (julio de 2018).</span><span class="sxs-lookup"><span data-stu-id="78584-132">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="78584-133">Es libre de usar el software más reciente, como se muestra en el [instalar las herramientas de](install-the-tools.md) artículo, aunque no se debe suponer que la información de este curso perfectamente coincida con lo que encontrará en el software más reciente que se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="78584-133">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="78584-134">Se recomiendan el siguiente hardware y software para este curso:</span><span class="sxs-lookup"><span data-stu-id="78584-134">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="78584-135">Un equipo de desarrollo</span><span class="sxs-lookup"><span data-stu-id="78584-135">A development PC</span></span>
- [<span data-ttu-id="78584-136">Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="78584-136">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="78584-137">El SDK más reciente de Windows 10</span><span class="sxs-lookup"><span data-stu-id="78584-137">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="78584-138">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="78584-138">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="78584-139">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="78584-139">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="78584-140">Un [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="78584-140">A [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="78584-141">Acceso a Internet para el programa de instalación de Azure y la recuperación de datos de Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="78584-141">Internet access for Azure setup and Microsoft Graph data retrieval</span></span>
- <span data-ttu-id="78584-142">Válido **Account Microsoft** (personal o profesional o educativa)</span><span class="sxs-lookup"><span data-stu-id="78584-142">A valid **Microsoft Account** (either personal or work/school)</span></span>
- <span data-ttu-id="78584-143">Algunas reuniones programadas para el día actual, con la misma Account de Microsoft</span><span class="sxs-lookup"><span data-stu-id="78584-143">A few meetings scheduled for the current day, using the same Microsoft Account</span></span>

### <a name="before-you-start"></a><span data-ttu-id="78584-144">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="78584-144">Before you start</span></span>

1.  <span data-ttu-id="78584-145">Para evitar problemas de creación de este proyecto, se recomienda encarecidamente que cree el proyecto se ha mencionado en este tutorial en una carpeta raíz o cerca de la raíz (rutas de acceso de carpeta largo pueden causar problemas en tiempo de compilación).</span><span class="sxs-lookup"><span data-stu-id="78584-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="78584-146">Configurar y probar su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="78584-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="78584-147">Si necesita admite la configuración de su HoloLens, [Asegúrese de visitar el artículo del programa de instalación de HoloLens](https://docs.microsoft.com/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="78584-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="78584-148">Es una buena idea para realizar la calibración y optimización Sensor cuando comienza a desarrollar una App HoloLens nuevo (a veces puede ayudar a realizar dichas tareas para cada usuario).</span><span class="sxs-lookup"><span data-stu-id="78584-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="78584-149">Para obtener ayuda sobre la calibración, siga este [vínculo al artículo de calibración de HoloLens](calibration.md#hololens).</span><span class="sxs-lookup"><span data-stu-id="78584-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](calibration.md#hololens).</span></span>

<span data-ttu-id="78584-150">Para obtener ayuda sobre optimización Sensor, siga este [vínculo al artículo optimización Sensor de HoloLens](sensor-tuning.md).</span><span class="sxs-lookup"><span data-stu-id="78584-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](sensor-tuning.md).</span></span>

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a><span data-ttu-id="78584-151">Capítulo 1: crear la aplicación en el Portal de registro de aplicación</span><span class="sxs-lookup"><span data-stu-id="78584-151">Chapter 1 - Create your app in the Application Registration Portal</span></span>

<span data-ttu-id="78584-152">Para empezar, deberá crear y registrar la aplicación en el **Portal de registro de aplicación**.</span><span class="sxs-lookup"><span data-stu-id="78584-152">To begin with, you will need to create and register your application in the **Application Registration Portal**.</span></span>

<span data-ttu-id="78584-153">En este capítulo también encontrará la clave de servicio que le permitirá realizar llamadas a *Microsoft Graph* para tener acceso a su contenido de la cuenta.</span><span class="sxs-lookup"><span data-stu-id="78584-153">In this Chapter you will also find the Service Key that will allow you to make calls to *Microsoft Graph* to access your account content.</span></span>

1.  <span data-ttu-id="78584-154">Navegue hasta la [Portal de registro de aplicaciones de Microsoft](https://apps.dev.microsoft.com) e inicie sesión con su Account de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="78584-154">Navigate to the [Microsoft Application Registration Portal](https://apps.dev.microsoft.com) and login with your Microsoft Account.</span></span> <span data-ttu-id="78584-155">Una vez que haya iniciado sesión, se le redirigirá a la **Portal de registro de aplicación**.</span><span class="sxs-lookup"><span data-stu-id="78584-155">Once you have logged in, you will be redirected to the **Application Registration Portal**.</span></span>

2.  <span data-ttu-id="78584-156">En el **mis aplicaciones** sección, haga clic en el botón **agregar una aplicación**.</span><span class="sxs-lookup"><span data-stu-id="78584-156">In the **My applications** section, click on the button **Add an app**.</span></span>

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > <span data-ttu-id="78584-157">El **Portal de registro de aplicación** puede parecer diferente, dependiendo de si ha trabajado previamente con *Microsoft Graph*.</span><span class="sxs-lookup"><span data-stu-id="78584-157">The **Application Registration Portal** can look different, depending on whether you have previously worked with *Microsoft Graph*.</span></span> <span data-ttu-id="78584-158">Las siguientes capturas de pantalla muestra las distintas versiones.</span><span class="sxs-lookup"><span data-stu-id="78584-158">The below screenshots display these different versions.</span></span>

3.  <span data-ttu-id="78584-159">Agregue un nombre para la aplicación y haga clic en **crear**.</span><span class="sxs-lookup"><span data-stu-id="78584-159">Add a name for your application and click **Create**.</span></span>

    ![](images/AzureLabs-Lab311-03.png)

4.  <span data-ttu-id="78584-160">Una vez creada la aplicación, se le redirigirá a la página principal de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="78584-160">Once the application has been created, you will be redirected to the application main page.</span></span> <span data-ttu-id="78584-161">Copia el **Id. de aplicación** y asegúrese de que tener en cuenta este valor en un lugar seguro, se usará pronto en el código.</span><span class="sxs-lookup"><span data-stu-id="78584-161">Copy the **Application Id** and make sure to note this value somewhere safe, you will use it soon in your code.</span></span>

    ![](images/AzureLabs-Lab311-04.png)

5.  <span data-ttu-id="78584-162">En el **plataformas** sección, asegúrese de que **aplicación nativa** se muestra.</span><span class="sxs-lookup"><span data-stu-id="78584-162">In the **Platforms** section, make sure **Native Application** is displayed.</span></span> <span data-ttu-id="78584-163">Si *no* haga clic en **Agregar plataforma** y seleccione **aplicación nativa**.</span><span class="sxs-lookup"><span data-stu-id="78584-163">If *not* click on **Add Platform** and select **Native Application**.</span></span>

    ![](images/AzureLabs-Lab311-05.png)

6.  <span data-ttu-id="78584-164">Desplácese hacia abajo en la misma página y en la sección denominada **permisos de Microsoft Graph** deberá agregar permisos adicionales para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="78584-164">Scroll down in the same page and in the section called **Microsoft Graph Permissions** you will need to add additional permissions for the application.</span></span> <span data-ttu-id="78584-165">Haga clic en **agregar** junto a **permisos delegados**.</span><span class="sxs-lookup"><span data-stu-id="78584-165">Click on **Add** next to **Delegated Permissions**.</span></span>

    ![](images/AzureLabs-Lab311-06.png)

7.  <span data-ttu-id="78584-166">Puesto que desea que su aplicación tenga acceso al calendario del usuario, active la casilla denominada **Calendars.Read** y haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="78584-166">Since you want your application to access the user's Calendar, check the box called **Calendars.Read** and click **OK**.</span></span>

    ![](images/AzureLabs-Lab311-07.png)

8.  <span data-ttu-id="78584-167">Desplácese hacia abajo y haga clic en el **guardar** botón.</span><span class="sxs-lookup"><span data-stu-id="78584-167">Scroll to the bottom and click the **Save** button.</span></span>

    ![](images/AzureLabs-Lab311-08.png)

9.  <span data-ttu-id="78584-168">Se confirmará la de guardar y cerrar desde la **Portal de registro de aplicación**.</span><span class="sxs-lookup"><span data-stu-id="78584-168">Your save will be confirmed, and you can log out from the **Application Registration Portal**.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="78584-169">Capítulo 2: configurar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="78584-169">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="78584-170">El siguiente es un conjunto típico de para el desarrollo con la realidad mixta y por lo tanto, es una buena plantilla para otros proyectos.</span><span class="sxs-lookup"><span data-stu-id="78584-170">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="78584-171">Abra *Unity* y haga clic en **New**.</span><span class="sxs-lookup"><span data-stu-id="78584-171">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab311-09.png)

2.  <span data-ttu-id="78584-172">Deberá proporcionar un nombre de proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="78584-172">You need to provide a Unity project name.</span></span> <span data-ttu-id="78584-173">Insertar **MSGraphMR**.</span><span class="sxs-lookup"><span data-stu-id="78584-173">Insert **MSGraphMR**.</span></span> <span data-ttu-id="78584-174">Asegúrese de que la plantilla de proyecto se establece en **3D**.</span><span class="sxs-lookup"><span data-stu-id="78584-174">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="78584-175">Establecer el **ubicación** a algún lugar adecuado para usted (Recuerde, es mejor cuanto más se acerque a los directorios raíz).</span><span class="sxs-lookup"><span data-stu-id="78584-175">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="78584-176">A continuación, haga clic en **crear un proyecto**.</span><span class="sxs-lookup"><span data-stu-id="78584-176">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab311-10.png)

3.  <span data-ttu-id="78584-177">Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="78584-177">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="78584-178">Vaya a **Editar > Preferencias** y, a continuación, en la ventana nueva, vaya a **herramientas externas**.</span><span class="sxs-lookup"><span data-stu-id="78584-178">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="78584-179">Cambio **External Script Editor** a **de Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="78584-179">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="78584-180">Cerrar la **preferencias** ventana.</span><span class="sxs-lookup"><span data-stu-id="78584-180">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab311-11.png)

4.  <span data-ttu-id="78584-181">Vaya a **archivo > configuración de compilación** y seleccione **Universal Windows Platform**, a continuación, haga clic en el **Cambiar plataforma** botón para aplicar la selección.</span><span class="sxs-lookup"><span data-stu-id="78584-181">Go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab311-12.png)

5.  <span data-ttu-id="78584-182">Mientras sigue en **archivo > configuración de compilación**, asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="78584-182">While still in **File > Build Settings**, make sure that:</span></span>

    1. <span data-ttu-id="78584-183">**Dispositivo de destino** está establecido en **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="78584-183">**Target Device** is set to **HoloLens**</span></span>
    2. <span data-ttu-id="78584-184">**Tipo de compilación** está establecido en **D3D**</span><span class="sxs-lookup"><span data-stu-id="78584-184">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="78584-185">**SDK** está establecido en **instalada más reciente**</span><span class="sxs-lookup"><span data-stu-id="78584-185">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="78584-186">**Versión de Visual Studio** está establecido en **instalada más reciente**</span><span class="sxs-lookup"><span data-stu-id="78584-186">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="78584-187">**Compilar y ejecutar** está establecido en **máquina Local**</span><span class="sxs-lookup"><span data-stu-id="78584-187">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="78584-188">Guarde la escena y agregarlo a la compilación.</span><span class="sxs-lookup"><span data-stu-id="78584-188">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="78584-189">Hacer esto seleccionando **agregar escenas abierto**.</span><span class="sxs-lookup"><span data-stu-id="78584-189">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="78584-190">Aparecerá el guardado de la ventana.</span><span class="sxs-lookup"><span data-stu-id="78584-190">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab311-13.png)

        2. <span data-ttu-id="78584-191">Cree una nueva carpeta de esto y cualquier futuro, escena.</span><span class="sxs-lookup"><span data-stu-id="78584-191">Create a new folder for this, and any future, scene.</span></span> <span data-ttu-id="78584-192">Seleccione el **nueva carpeta** botón para crear una nueva carpeta y asígnele el nombre **escenas**.</span><span class="sxs-lookup"><span data-stu-id="78584-192">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab311-14.png)

        3. <span data-ttu-id="78584-193">Abra su recién creado **escenas** carpeta y, a continuación, en el *nombre de archivo*: campo de texto, escriba **MR_ComputerVisionScene**, a continuación, haga clic en **guardar** .</span><span class="sxs-lookup"><span data-stu-id="78584-193">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > <span data-ttu-id="78584-194">Tenga en cuenta, debe guardar sus escenas de Unity dentro de la *activos* carpeta, ya que deben estar asociados al proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="78584-194">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="78584-195">Creación de la carpeta de segundo plano (y otras carpetas similares) es una forma habitual de estructurar un proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="78584-195">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7.  <span data-ttu-id="78584-196">El resto de la configuración, en *configuración de compilación*, debe dejarse como predeterminada por ahora.</span><span class="sxs-lookup"><span data-stu-id="78584-196">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6.  <span data-ttu-id="78584-197">En el *configuración de compilación* ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el *Inspector* se encuentra.</span><span class="sxs-lookup"><span data-stu-id="78584-197">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![](images/AzureLabs-Lab311-16.png)

7. <span data-ttu-id="78584-198">En este panel, es necesario comprobar algunas opciones de configuración:</span><span class="sxs-lookup"><span data-stu-id="78584-198">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="78584-199">En el **otra configuración** pestaña:</span><span class="sxs-lookup"><span data-stu-id="78584-199">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="78584-200">**Scripting** **en tiempo de ejecución versión** debe ser **Experimental** (.NET 4.6 equivalente), que desencadenará una necesidad de reiniciar el Editor.</span><span class="sxs-lookup"><span data-stu-id="78584-200">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="78584-201">**Scripting de back-end** debe ser **.NET**</span><span class="sxs-lookup"><span data-stu-id="78584-201">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="78584-202">**Nivel de compatibilidad de API** debe ser **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="78584-202">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![](images/AzureLabs-Lab311-17.png)

    2.  <span data-ttu-id="78584-203">Dentro de la **configuración de publicación** ficha **capacidades**, consulte:</span><span class="sxs-lookup"><span data-stu-id="78584-203">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="78584-204">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="78584-204">**InternetClient**</span></span>

            ![](images/AzureLabs-Lab311-18.png)

    3.  <span data-ttu-id="78584-205">Más abajo el panel, en **XR configuración** (bajo **configuración de publicación**), compruebe **admite la realidad Virtual**, asegúrese de que el **Windows Mixed Reality SDK** se agrega.</span><span class="sxs-lookup"><span data-stu-id="78584-205">Further down the panel, in **XR Settings** (found below **Publish Settings**), check **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab311-19.png)

8.  <span data-ttu-id="78584-206">En *configuración de compilación*, *Unity C# proyectos* ya no está atenuada; Active la casilla situada junto a esto.</span><span class="sxs-lookup"><span data-stu-id="78584-206">Back in *Build Settings*, *Unity C# Projects* is no longer greyed out; check the checkbox next to this.</span></span>

9.  <span data-ttu-id="78584-207">Cerrar la *configuración de compilación* ventana.</span><span class="sxs-lookup"><span data-stu-id="78584-207">Close the *Build Settings* window.</span></span>

10.  <span data-ttu-id="78584-208">Guarde la escena y el proyecto (**archivo > Guardar ESCENAS / archivo > Guardar proyecto**).</span><span class="sxs-lookup"><span data-stu-id="78584-208">Save your scene and project (**FILE > SAVE SCENES / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3---import-libraries-in-unity"></a><span data-ttu-id="78584-209">Capítulo 3: las bibliotecas de importación en Unity</span><span class="sxs-lookup"><span data-stu-id="78584-209">Chapter 3 - Import Libraries in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="78584-210">Si desea omitir la *configurar Unity* componente de este curso y continuar directamente en código, no dude en descargar este [MR-Azure-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), importarlo en el proyecto como un [ **Paquete personalizado**](https://docs.unity3d.com/Manual/AssetPackages.html)y, a continuación, continuar desde [capítulo 5](#chapter-5---create-meetingsui-class).</span><span class="sxs-lookup"><span data-stu-id="78584-210">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5---create-meetingsui-class).</span></span>

<span data-ttu-id="78584-211">Para usar *Microsoft Graph* Unity es preciso que el uso de la **Microsoft.Identity.Client** DLL.</span><span class="sxs-lookup"><span data-stu-id="78584-211">To use *Microsoft Graph* within Unity you need to make use of the  **Microsoft.Identity.Client** DLL.</span></span> <span data-ttu-id="78584-212">Es posible usar el SDK de Microsoft Graph, sin embargo, requerirá la adición de un paquete NuGet después de compilar el proyecto de Unity (es decir, la posterior a la compilación del proyecto de edición).</span><span class="sxs-lookup"><span data-stu-id="78584-212">It is possible to use the Microsoft Graph SDK, however, it will require the addition of a NuGet package after you build the Unity project (meaning editing the project post-build).</span></span> <span data-ttu-id="78584-213">Se considera más sencillo importar los archivos DLL necesarios directamente en Unity.</span><span class="sxs-lookup"><span data-stu-id="78584-213">It is considered simpler to import the required DLLs directly into Unity.</span></span>

> [!NOTE]
> <span data-ttu-id="78584-214">Actualmente hay un problema conocido en Unity que requiere complementos volver a configurar tras la importación.</span><span class="sxs-lookup"><span data-stu-id="78584-214">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="78584-215">Estos pasos (4-7 en esta sección) ya no será necesarios una vez que se ha resuelto el error.</span><span class="sxs-lookup"><span data-stu-id="78584-215">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="78584-216">Para importar *Microsoft Graph* en su propio proyecto, [descargar el archivo MSGraph_LabPlugins.zip](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="78584-216">To import *Microsoft Graph* into your own project, [download the MSGraph_LabPlugins.zip file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage).</span></span> <span data-ttu-id="78584-217">Este paquete se creó con las versiones de las bibliotecas que se han probado.</span><span class="sxs-lookup"><span data-stu-id="78584-217">This package has been created with versions of the libraries that have been tested.</span></span>

<span data-ttu-id="78584-218">Si desea obtener más información acerca de cómo agregar archivos DLL personalizado a su proyecto de Unity, [siga este vínculo](https://docs.unity3d.com/Manual/UsingDLL.html).</span><span class="sxs-lookup"><span data-stu-id="78584-218">If you wish to know more about how to add custom DLLs to your Unity project, [follow this link](https://docs.unity3d.com/Manual/UsingDLL.html).</span></span>

<span data-ttu-id="78584-219">Para importar el paquete:</span><span class="sxs-lookup"><span data-stu-id="78584-219">To import the package:</span></span>

1.  <span data-ttu-id="78584-220">Agregar el paquete de Unity para Unity mediante el **activos* > *Importar paquete* > *paquete personalizado** opción de menú.</span><span class="sxs-lookup"><span data-stu-id="78584-220">Add the Unity Package to Unity by using the **Assets* > *Import Package* > *Custom Package** menu option.</span></span> <span data-ttu-id="78584-221">Seleccione el paquete que acaba de descargar.</span><span class="sxs-lookup"><span data-stu-id="78584-221">Select the package you just downloaded.</span></span>

2.  <span data-ttu-id="78584-222">En el **Importar paquete de Unity** cuadro que aparece hacia arriba, asegúrese de todo el contenido en (e incluido) **complementos** está seleccionada.</span><span class="sxs-lookup"><span data-stu-id="78584-222">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab311-20.png)

3.  <span data-ttu-id="78584-223">Haga clic en el **importación** para agregar los elementos al proyecto.</span><span class="sxs-lookup"><span data-stu-id="78584-223">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="78584-224">Vaya a la **MSGraph** carpeta bajo **complementos** en el *Panel proyecto* y seleccione el complemento llamado **Microsoft.Identity.Client**.</span><span class="sxs-lookup"><span data-stu-id="78584-224">Go to the **MSGraph** folder under **Plugins** in the *Project Panel* and select the plugin called **Microsoft.Identity.Client**.</span></span>

    ![](images/AzureLabs-Lab311-21.png)

5.  <span data-ttu-id="78584-225">Con el *complemento* seleccionado, asegúrese de que **cualquier plataforma** está desactivada y, después, asegúrese de que **WSAPlayer** también está desactivada y, después, haga clic en **aplicar**.</span><span class="sxs-lookup"><span data-stu-id="78584-225">With the *plugin* selected, ensure that **Any Platform** is unchecked, then ensure that **WSAPlayer** is also unchecked, then click **Apply**.</span></span> <span data-ttu-id="78584-226">Esto es solo para confirmar que los archivos están configurados correctamente.</span><span class="sxs-lookup"><span data-stu-id="78584-226">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > <span data-ttu-id="78584-227">Marcar estos complementos configura para su uso en el Editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="78584-227">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="78584-228">Hay un conjunto diferente de DLL en la carpeta WSA que se utilizará después de que el proyecto se exporta desde Unity como una aplicación Universal de Windows.</span><span class="sxs-lookup"><span data-stu-id="78584-228">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity as a Universal Windows Application.</span></span>

6.  <span data-ttu-id="78584-229">A continuación, deberá abrir el **WSA** carpeta, en el **MSGraph** carpeta.</span><span class="sxs-lookup"><span data-stu-id="78584-229">Next, you need to open the **WSA** folder, within the **MSGraph** folder.</span></span> <span data-ttu-id="78584-230">Verá una copia del mismo archivo que acaba de configurar.</span><span class="sxs-lookup"><span data-stu-id="78584-230">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="78584-231">Seleccione el archivo y, a continuación, en el inspector:</span><span class="sxs-lookup"><span data-stu-id="78584-231">Select the file, and then in the inspector:</span></span>

    -   <span data-ttu-id="78584-232">Asegúrese de que **cualquier plataforma** es **unchecked**y que **sólo** **WSAPlayer** es **comprueban**.</span><span class="sxs-lookup"><span data-stu-id="78584-232">ensure that **Any Platform** is **unchecked**, and that **only** **WSAPlayer** is **checked**.</span></span>

    -   <span data-ttu-id="78584-233">Asegúrese de **SDK** está establecido en **UWP**, y **back-end de Scripting** está establecido en **Dot Net**</span><span class="sxs-lookup"><span data-stu-id="78584-233">Ensure **SDK** is set to **UWP**, and **Scripting Backend** is set to **Dot Net**</span></span>

    -   <span data-ttu-id="78584-234">Asegúrese de que **no procesar** es **comprueban**.</span><span class="sxs-lookup"><span data-stu-id="78584-234">Ensure that **Don't process** is **checked**.</span></span>

        ![](images/AzureLabs-Lab311-23.png)

7.  <span data-ttu-id="78584-235">Haga clic en **Aplicar**.</span><span class="sxs-lookup"><span data-stu-id="78584-235">Click **Apply**.</span></span>

## <a name="chapter-4---camera-setup"></a><span data-ttu-id="78584-236">Capítulo 4: configuración de cámara</span><span class="sxs-lookup"><span data-stu-id="78584-236">Chapter 4 - Camera Setup</span></span>

<span data-ttu-id="78584-237">Durante este capítulo se configurará la cámara principal de la escena:</span><span class="sxs-lookup"><span data-stu-id="78584-237">During this Chapter you will set up the Main Camera of your scene:</span></span>

1.  <span data-ttu-id="78584-238">En el *jerarquía Panel*, seleccione el **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="78584-238">In the *Hierarchy Panel*, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="78584-239">Una vez seleccionado, podrá ver todos los componentes de la **cámara principal** en el *Inspector* panel.</span><span class="sxs-lookup"><span data-stu-id="78584-239">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector* panel.</span></span>

    1.  <span data-ttu-id="78584-240">El **objeto de cámara** debe denominarse **cámara principal** (tenga en cuenta la ortografía!)</span><span class="sxs-lookup"><span data-stu-id="78584-240">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="78584-241">La cámara principal **etiqueta** debe establecerse en **MainCamera** (tenga en cuenta la ortografía!)</span><span class="sxs-lookup"><span data-stu-id="78584-241">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="78584-242">Asegúrese de que el **transformar posición** está establecido en **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="78584-242">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="78584-243">Establecer **borrar las marcas de** a **Color sólido**</span><span class="sxs-lookup"><span data-stu-id="78584-243">Set **Clear Flags** to **Solid Color**</span></span>

    5.  <span data-ttu-id="78584-244">Establecer el **Color de fondo** del componente de cámara para **negro, alfa 0** **(Hex código: #00000000)**</span><span class="sxs-lookup"><span data-stu-id="78584-244">Set the **Background Color** of the Camera Component to **Black, Alpha 0** **(Hex Code: #00000000)**</span></span>

        ![](images/AzureLabs-Lab311-24.png)

3.  <span data-ttu-id="78584-245">La estructura del objeto final en el *jerarquía Panel* debe ser como se muestra en la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="78584-245">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a><span data-ttu-id="78584-246">Capítulo 5: crear la clase MeetingsUI</span><span class="sxs-lookup"><span data-stu-id="78584-246">Chapter 5 - Create MeetingsUI class</span></span>

<span data-ttu-id="78584-247">Es el primer script, deberá crear **MeetingsUI**, que es responsable del hospedaje y rellenar la interfaz de usuario de la aplicación (mensaje de bienvenida, instrucciones y los detalles de las reuniones).</span><span class="sxs-lookup"><span data-stu-id="78584-247">The first script you need to create is **MeetingsUI**, which is responsible for hosting and populating the UI of the application (welcome message, instructions and the meetings details).</span></span>

<span data-ttu-id="78584-248">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="78584-248">To create this class:</span></span>

1.  <span data-ttu-id="78584-249">Haga doble clic en el **activos** carpeta en el *Panel proyecto*, a continuación, seleccione \**crear* > \* carpeta \*\*.</span><span class="sxs-lookup"><span data-stu-id="78584-249">Right-click on the **Assets** folder in the *Project Panel*, then select \**Create* > \*Folder\*\*.</span></span> <span data-ttu-id="78584-250">Nombre de la carpeta **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="78584-250">Name the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  <span data-ttu-id="78584-251">Abra el **Scripts** carpeta, dentro de esa carpeta, haga clic en, \**crear* > \* C\# Script \*\*.</span><span class="sxs-lookup"><span data-stu-id="78584-251">Open the **Scripts** folder then, within that folder, right-click, \**Create* > \*C\# Script\*\*.</span></span> <span data-ttu-id="78584-252">Nombre de la secuencia de comandos **MeetingsUI.**</span><span class="sxs-lookup"><span data-stu-id="78584-252">Name the script **MeetingsUI.**</span></span>

    ![](images/AzureLabs-Lab311-28.png)

3.  <span data-ttu-id="78584-253">Haga doble clic en el nuevo **MeetingsUI** script para abrirlo con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="78584-253">Double-click on the new **MeetingsUI** script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="78584-254">Inserte los espacios de nombres siguientes:</span><span class="sxs-lookup"><span data-stu-id="78584-254">Insert the following namespaces:</span></span>

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  <span data-ttu-id="78584-255">Dentro de la clase inserte las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="78584-255">Inside the class insert the following variables:</span></span>

    ```csharp    
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static MeetingsUI Instance;

        /// <summary>
        /// The 3D text of the scene
        /// </summary>
        private TextMesh _meetingDisplayTextMesh;
    ```

6.  <span data-ttu-id="78584-256">A continuación, reemplace el **Start()** método y agregue un **Awake()** método.</span><span class="sxs-lookup"><span data-stu-id="78584-256">Then replace the **Start()** method and add an **Awake()** method.</span></span> <span data-ttu-id="78584-257">Estos se llamará cuando se inicializa la clase:</span><span class="sxs-lookup"><span data-stu-id="78584-257">These will be called when the class initializes:</span></span>

    ```csharp    
        /// <summary>
        /// Called on initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        void Start ()
        {
            // Creating the text mesh within the scene
            _meetingDisplayTextMesh = CreateMeetingsDisplay();
        }
    ```

7.  <span data-ttu-id="78584-258">Agregue los métodos responsables de crear el *reuniones UI* y rellenarla con las reuniones actuales cuando se solicite:</span><span class="sxs-lookup"><span data-stu-id="78584-258">Add the methods responsible for creating the *Meetings UI* and populate it with the current meetings when requested:</span></span>

    ```csharp    
        /// <summary>
        /// Set the welcome message for the user
        /// </summary>
        internal void WelcomeUser(string userName)
        {
            if(!string.IsNullOrEmpty(userName))
            {
                _meetingDisplayTextMesh.text = $"Welcome {userName}";
            }
            else 
            {
                _meetingDisplayTextMesh.text = "Welcome";
            }
        }

        /// <summary>
        /// Set up the parameters for the UI text
        /// </summary>
        /// <returns>Returns the 3D text in the scene</returns>
        private TextMesh CreateMeetingsDisplay()
        {
            GameObject display = new GameObject();
            display.transform.localScale = new Vector3(0.03f, 0.03f, 0.03f);
            display.transform.position = new Vector3(-3.5f, 2f, 9f);
            TextMesh textMesh = display.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleLeft;
            textMesh.alignment = TextAlignment.Left;
            textMesh.fontSize = 80;
            textMesh.text = "Welcome! \nPlease gaze at the button" +
                "\nand use the Tap Gesture to display your meetings";

            return textMesh;
        }

        /// <summary>
        /// Adds a new Meeting in the UI by chaining the existing UI text
        /// </summary>
        internal void AddMeeting(string subject, DateTime dateTime, string location)
        {
            string newText = $"\n{_meetingDisplayTextMesh.text}\n\n Meeting,\nSubject: {subject},\nToday at {dateTime},\nLocation: {location}";

            _meetingDisplayTextMesh.text = newText;
        }
    ```

8. <span data-ttu-id="78584-259">**Eliminar** el **Update()** método, y **guardar los cambios** en Visual Studio antes de volver a Unity.</span><span class="sxs-lookup"><span data-stu-id="78584-259">**Delete** the **Update()** method, and **save your changes** in Visual Studio before returning to Unity.</span></span> 

## <a name="chapter-6---create-the-graph-class"></a><span data-ttu-id="78584-260">Capítulo 6: crear la clase de gráfico</span><span class="sxs-lookup"><span data-stu-id="78584-260">Chapter 6 - Create the Graph class</span></span>

<span data-ttu-id="78584-261">Es el script siguiente para crear el **Graph** secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="78584-261">The next script to create is the **Graph** script.</span></span> <span data-ttu-id="78584-262">Este script es responsable de realizar las llamadas a autenticar al usuario y recuperar las reuniones programadas para el día actual desde el calendario del usuario.</span><span class="sxs-lookup"><span data-stu-id="78584-262">This script is responsible for making the calls to authenticate the user and retrieve the scheduled meetings for the current day from the user's calendar.</span></span>

<span data-ttu-id="78584-263">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="78584-263">To create this class:</span></span>

1.  <span data-ttu-id="78584-264">Haga doble clic en el **Scripts** carpeta para abrirla.</span><span class="sxs-lookup"><span data-stu-id="78584-264">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="78584-265">Haga clic en el **Scripts** carpeta, haga clic en **crear**  >   **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="78584-265">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="78584-266">Nombre de la secuencia de comandos **gráfico**.</span><span class="sxs-lookup"><span data-stu-id="78584-266">Name the script **Graph**.</span></span>

3.  <span data-ttu-id="78584-267">Haga doble clic en el script para abrirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="78584-267">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="78584-268">Inserte los espacios de nombres siguientes:</span><span class="sxs-lookup"><span data-stu-id="78584-268">Insert the following namespaces:</span></span>

    ```csharp
    using System.Collections.Generic;
    using UnityEngine;
    using Microsoft.Identity.Client;
    using System;
    using System.Threading.Tasks;
    
    #if !UNITY_EDITOR && UNITY_WSA
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Windows.Storage;
    #endif
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="78584-269">Observará que las partes del código en esta secuencia de comandos se ajustan en torno a [precompilar directivas](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), esto es para evitar problemas con las bibliotecas al compilar la solución de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="78584-269">You will notice that parts of the code in this script are wrapped around [Precompile Directives](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), this is to avoid issues with the libraries when building the Visual Studio Solution.</span></span>

5.  <span data-ttu-id="78584-270">Eliminar el **Start()** y **Update()** métodos, ya que no se usará.</span><span class="sxs-lookup"><span data-stu-id="78584-270">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span>

6.  <span data-ttu-id="78584-271">Fuera del **Graph** class, insertar los objetos siguientes, que son necesarios para deserializar el objeto JSON que representa las reuniones programadas diarias:</span><span class="sxs-lookup"><span data-stu-id="78584-271">Outside the **Graph** class, insert the following objects, which are necessary to deserialize the JSON object representing the daily scheduled meetings:</span></span>

    ```csharp
    /// <summary>
    /// The object hosting the scheduled meetings
    /// </summary>
    [Serializable]
    public class Rootobject
    {
        public List<Value> value;
    }

    [Serializable]
    public class Value
    {
        public string subject { get; set; }
        public StartTime start { get; set; }
        public Location location { get; set; }
    }

    [Serializable]
    public class StartTime
    {
        public string dateTime;

        private DateTime? _startDateTime;
        public DateTime StartDateTime
        {
            get
            {
                if (_startDateTime != null)
                    return _startDateTime.Value;
                DateTime dt;
                DateTime.TryParse(dateTime, out dt);
                _startDateTime = dt;
                return _startDateTime.Value;
            }
        }
    }

    [Serializable]
    public class Location
    {
        public string displayName { get; set; }
    }
    ```

7.  <span data-ttu-id="78584-272">Dentro de la **gráfico** de clases, agregue las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="78584-272">Inside the **Graph** class, add the following variables:</span></span>

    ```csharp    
        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        private string _appId = "-- Insert your Application Id here --";

        /// <summary>
        /// Application scopes, determine Microsoft Graph accessibility level to user account
        /// </summary>
        private IEnumerable<string> _scopes = new List<string>() { "User.Read", "Calendars.Read" };

        /// <summary>
        /// Microsoft Graph API, user reference
        /// </summary>
        private PublicClientApplication _client;

        /// <summary>
        /// Microsoft Graph API, authentication
        /// </summary>
        private AuthenticationResult _authResult;

    ```

    > [!NOTE]
    > <span data-ttu-id="78584-273">Cambiar el **appId** valor sea el **Id. de aplicación** que haya anotado en  **[capítulo 1](#chapter-1---create-your-app-in-the-application-registration-portal), paso 4**.</span><span class="sxs-lookup"><span data-stu-id="78584-273">Change the **appId** value to be the **App Id** that you have noted in **[Chapter 1](#chapter-1---create-your-app-in-the-application-registration-portal), step 4**.</span></span> <span data-ttu-id="78584-274">Este valor debe ser el mismo que se muestra en el **Portal de registro de aplicación,** en la página de registro de aplicación.</span><span class="sxs-lookup"><span data-stu-id="78584-274">This value should be the same as that displayed in the **Application Registration Portal,** in your application registration page.</span></span>

8.  <span data-ttu-id="78584-275">Dentro de la **Graph** de clases, agregue los métodos **SignInAsync()** y **AquireTokenAsync()**, que le solicitará al usuario que inserte las credenciales de inicio de sesión.</span><span class="sxs-lookup"><span data-stu-id="78584-275">Within the **Graph** class, add the methods **SignInAsync()** and **AquireTokenAsync()**, that will prompt the user to insert the log-in credentials.</span></span>

    ```csharp
        /// <summary>
        /// Begin the Sign In process using Microsoft Graph Library
        /// </summary>
        internal async void SignInAsync()
        {
    #if !UNITY_EDITOR && UNITY_WSA
            // Set up Grap user settings, determine if needs auth
            ApplicationDataContainer localSettings = ApplicationData.Current.LocalSettings;
            string userId = localSettings.Values["UserId"] as string;
            _client = new PublicClientApplication(_appId);

            // Attempt authentication
            _authResult = await AcquireTokenAsync(_client, _scopes, userId);

            // If authentication is successfull, retrieve the meetings
            if (!string.IsNullOrEmpty(_authResult.AccessToken))
            {
                // Once Auth as been completed, find the meetings for the day
                await ListMeetingsAsync(_authResult.AccessToken);
            }
    #endif
        }

        /// <summary>
        /// Attempt to retrieve the Access Token by either retrieving
        /// previously stored credentials or by prompting user to Login
        /// </summary>
        private async Task<AuthenticationResult> AcquireTokenAsync(
            IPublicClientApplication app, IEnumerable<string> scopes, string userId)
        {
            IUser user = !string.IsNullOrEmpty(userId) ? app.GetUser(userId) : null;
            string userName = user != null ? user.Name : "null";

            // Once the User name is found, display it as a welcome message
            MeetingsUI.Instance.WelcomeUser(userName);

            // Attempt to Log In the user with a pre-stored token. Only happens
            // in case the user Logged In with this app on this device previously
            try
            {
                _authResult = await app.AcquireTokenSilentAsync(scopes, user);
            }
            catch (MsalUiRequiredException)
            {
                // Pre-stored token not found, prompt the user to log-in 
                try
                {
                    _authResult = await app.AcquireTokenAsync(scopes);
                }
                catch (MsalException msalex)
                {
                    Debug.Log($"Error Acquiring Token: {msalex.Message}");
                    return _authResult;
                }
            }
            
            MeetingsUI.Instance.WelcomeUser(_authResult.User.Name);

    #if !UNITY_EDITOR && UNITY_WSA
            ApplicationData.Current.LocalSettings.Values["UserId"] = 
            _authResult.User.Identifier;
    #endif
            return _authResult;
        }
    ```

9.  <span data-ttu-id="78584-276">Agregue los dos métodos siguientes:</span><span class="sxs-lookup"><span data-stu-id="78584-276">Add the following two methods:</span></span>

    1.  <span data-ttu-id="78584-277">**BuildTodayCalendarEndpoint()**, que basa el URI que especifica el día y el intervalo de tiempo, en el que se recuperan las reuniones programadas.</span><span class="sxs-lookup"><span data-stu-id="78584-277">**BuildTodayCalendarEndpoint()**, which builds the URI specifying the day, and time span, in which the scheduled meetings are retrieved.</span></span>

    2.  <span data-ttu-id="78584-278">**ListMeetingsAsync()**, que solicita las reuniones programadas de *Microsoft Graph*.</span><span class="sxs-lookup"><span data-stu-id="78584-278">**ListMeetingsAsync()**, which requests the scheduled meetings from *Microsoft Graph*.</span></span>

    ```csharp
        /// <summary>
        /// Build the endpoint to retrieve the meetings for the current day.
        /// </summary>
        /// <returns>Returns the Calendar Endpoint</returns>
        public string BuildTodayCalendarEndpoint()
        {
            DateTime startOfTheDay = DateTime.Today.AddDays(0);
            DateTime endOfTheDay = DateTime.Today.AddDays(1);
            DateTime startOfTheDayUTC = startOfTheDay.ToUniversalTime();
            DateTime endOfTheDayUTC = endOfTheDay.ToUniversalTime();

            string todayDate = startOfTheDayUTC.ToString("o");
            string tomorrowDate = endOfTheDayUTC.ToString("o");
            string todayCalendarEndpoint = string.Format(
                "https://graph.microsoft.com/v1.0/me/calendarview?startdatetime={0}&enddatetime={1}",
                todayDate,
                tomorrowDate);

            return todayCalendarEndpoint;
        }

        /// <summary>
        /// Request all the scheduled meetings for the current day.
        /// </summary>
        private async Task ListMeetingsAsync(string accessToken)
        {
    #if !UNITY_EDITOR && UNITY_WSA
            var http = new HttpClient();

            http.DefaultRequestHeaders.Authorization = 
            new AuthenticationHeaderValue("Bearer", accessToken);
            var response = await http.GetAsync(BuildTodayCalendarEndpoint());

            var jsonResponse = await response.Content.ReadAsStringAsync();

            Rootobject rootObject = new Rootobject();
            try
            {
                // Parse the JSON response.
                rootObject = JsonUtility.FromJson<Rootobject>(jsonResponse);

                // Sort the meeting list by starting time.
                rootObject.value.Sort((x, y) => DateTime.Compare(x.start.StartDateTime, y.start.StartDateTime));

                // Populate the UI with the meetings.
                for (int i = 0; i < rootObject.value.Count; i++)
                {
                    MeetingsUI.Instance.AddMeeting(rootObject.value[i].subject,
                                                rootObject.value[i].start.StartDateTime.ToLocalTime(),
                                                rootObject.value[i].location.displayName);
                }
            }
            catch (Exception ex)
            {
                Debug.Log($"Error = {ex.Message}");
                return;
            }
    #endif
        }
    ```

10. <span data-ttu-id="78584-279">Ahora ha completado la **Graph** secuencia de comandos.</span><span class="sxs-lookup"><span data-stu-id="78584-279">You have now completed the **Graph** script.</span></span> <span data-ttu-id="78584-280">**Guarde los cambios** en Visual Studio antes de volver a Unity.</span><span class="sxs-lookup"><span data-stu-id="78584-280">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-7---create-the-gazeinput-script"></a><span data-ttu-id="78584-281">Capítulo 7: crear la secuencia de comandos GazeInput</span><span class="sxs-lookup"><span data-stu-id="78584-281">Chapter 7 - Create the GazeInput script</span></span>

<span data-ttu-id="78584-282">Ahora creará el **GazeInput**.</span><span class="sxs-lookup"><span data-stu-id="78584-282">You will now create the **GazeInput**.</span></span> <span data-ttu-id="78584-283">Esta clase controla y realiza un seguimiento de mirada del usuario, mediante un **Raycast** procedentes de la **cámara principal**, proyectar hacia delante.</span><span class="sxs-lookup"><span data-stu-id="78584-283">This class handles and keeps track of the user's gaze, using a **Raycast** coming from the **Main Camera**, projecting forward.</span></span>

<span data-ttu-id="78584-284">Para crear la secuencia de comandos:</span><span class="sxs-lookup"><span data-stu-id="78584-284">To create the script:</span></span>

1.  <span data-ttu-id="78584-285">Haga doble clic en el **Scripts** carpeta para abrirla.</span><span class="sxs-lookup"><span data-stu-id="78584-285">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="78584-286">Haga clic en el **Scripts** carpeta, haga clic en **crear**  >   **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="78584-286">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="78584-287">Nombre de la secuencia de comandos **GazeInput**.</span><span class="sxs-lookup"><span data-stu-id="78584-287">Name the script **GazeInput**.</span></span>

3.  <span data-ttu-id="78584-288">Haga doble clic en el script para abrirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="78584-288">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="78584-289">Cambiar el código de espacios de nombres para que coincida con lo siguiente, además de agregar el '**\[System.Serializable\]**' etiqueta anterior su **GazeInput** clase, para que pueda serializarse:</span><span class="sxs-lookup"><span data-stu-id="78584-289">Change the namespaces code to match the one below, along with adding the '**\[System.Serializable\]**' tag above your **GazeInput** class, so that it can be serialized:</span></span>

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  <span data-ttu-id="78584-290">Dentro de la **GazeInput** de clases, agregue las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="78584-290">Inside the **GazeInput** class, add the following variables:</span></span>

    ```csharp    
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "SignInButton";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject oldFocusedObject { get; private set; }

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

6.  <span data-ttu-id="78584-291">Agregar el **CreateCursor()** método para crear el cursor de HoloLens en la escena y llamar al método desde el **Start()** método:</span><span class="sxs-lookup"><span data-stu-id="78584-291">Add the **CreateCursor()** method to create the HoloLens cursor in the scene, and call the method from the **Start()** method:</span></span>

    ```csharp    
        /// <summary>
        /// Start method used upon initialisation.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }

        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

7.  <span data-ttu-id="78584-292">Los métodos siguientes permiten a la mirada Raycast y realizar un seguimiento de los objetos con foco.</span><span class="sxs-lookup"><span data-stu-id="78584-292">The following methods enable the gaze Raycast and keep track of the focused objects.</span></span>

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
        if (oldFocusedObject != null)
        {
            if (oldFocusedObject.CompareTag(InteractibleTag))
            {
                // Provide the 'Gaze Exited' event.
                oldFocusedObject.SendMessage("OnGazeExited", SendMessageOptions.DontRequireReceiver);
            }
        }
    }
    ```

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialise Raycasting.
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
            if (FocusedObject != oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the 'Gaze Entered' event.
                        FocusedObject.SendMessage("OnGazeEntered", 
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```

8.  <span data-ttu-id="78584-293">**Guarde los cambios** en Visual Studio antes de volver a Unity.</span><span class="sxs-lookup"><span data-stu-id="78584-293">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-8---create-the-interactions-class"></a><span data-ttu-id="78584-294">Capítulo 8: crear la clase interacciones</span><span class="sxs-lookup"><span data-stu-id="78584-294">Chapter 8 - Create the Interactions class</span></span>

<span data-ttu-id="78584-295">Ahora deberá crear el **interacciones** script, que es responsable de:</span><span class="sxs-lookup"><span data-stu-id="78584-295">You will now need to create the **Interactions** script, which is responsible for:</span></span>

-   <span data-ttu-id="78584-296">Controlar la **pulse** interacción y la **cámara que mirar**, lo que permite al usuario interactuar con el inicio de sesión "button" en la escena.</span><span class="sxs-lookup"><span data-stu-id="78584-296">Handling the **Tap** interaction and the **Camera Gaze**, which enables the user to interact with the log in "button" in the scene.</span></span>

-   <span data-ttu-id="78584-297">Crear el registro en el objeto de "button" en la escena para el usuario interactuar con.</span><span class="sxs-lookup"><span data-stu-id="78584-297">Creating the log in "button" object in the scene for the user to interact with.</span></span>

<span data-ttu-id="78584-298">Para crear la secuencia de comandos:</span><span class="sxs-lookup"><span data-stu-id="78584-298">To create the script:</span></span>

1.  <span data-ttu-id="78584-299">Haga doble clic en el **Scripts** carpeta para abrirla.</span><span class="sxs-lookup"><span data-stu-id="78584-299">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="78584-300">Haga clic en el **Scripts** carpeta, haga clic en **crear**  >   **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="78584-300">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="78584-301">Nombre de la secuencia de comandos **interacciones**.</span><span class="sxs-lookup"><span data-stu-id="78584-301">Name the script **Interactions**.</span></span>

3.  <span data-ttu-id="78584-302">Haga doble clic en el script para abrirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="78584-302">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="78584-303">Inserte los espacios de nombres siguientes:</span><span class="sxs-lookup"><span data-stu-id="78584-303">Insert the following namespaces:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  <span data-ttu-id="78584-304">Cambiar la herencia de la **interacción** clase *MonoBehaviour* a **GazeInput**.</span><span class="sxs-lookup"><span data-stu-id="78584-304">Change the inheritance of the **Interaction** class from *MonoBehaviour* to **GazeInput**.</span></span>

    <span data-ttu-id="78584-305">~~Interacciones de clase pública: MonoBehaviour~~</span><span class="sxs-lookup"><span data-stu-id="78584-305">~~public class Interactions : MonoBehaviour~~</span></span>

    ```csharp
    public class Interactions : GazeInput
    ```

6.  <span data-ttu-id="78584-306">Dentro de la **interacción** clase inserte la siguiente variable:</span><span class="sxs-lookup"><span data-stu-id="78584-306">Inside the **Interaction** class insert the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  <span data-ttu-id="78584-307">Reemplace el **iniciar** método; tenga en cuenta es un método de invalidación, que llama al método de clase 'base' mirada.</span><span class="sxs-lookup"><span data-stu-id="78584-307">Replace the **Start** method; notice it is an override method, which calls the 'base' Gaze class method.</span></span> <span data-ttu-id="78584-308">**Start()** se llamará cuando se inicializa la clase, registrar para el reconocimiento de entrada y crear el inicio de sesión *botón* en la escena:</span><span class="sxs-lookup"><span data-stu-id="78584-308">**Start()** will be called when the class initializes, registering for input recognition and creating the sign in *button* in the scene:</span></span>

    ```csharp    
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            // Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();

            // Add the Graph script to this object
            gameObject.AddComponent<MeetingsUI>();
            CreateSignInButton();
        }
    ```

8.  <span data-ttu-id="78584-309">Agregar el **CreateSignInButton()** método, que creará una instancia el inicio de sesión *botón* en la escena y establezca sus propiedades:</span><span class="sxs-lookup"><span data-stu-id="78584-309">Add the **CreateSignInButton()** method, which will instantiate the sign in *button* in the scene and set its properties:</span></span>

    ```csharp    
        /// <summary>
        /// Create the sign in button object in the scene
        /// and sets its properties
        /// </summary>
        void CreateSignInButton()
        {
            GameObject signInButton = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            Material mat = new Material(Shader.Find("Diffuse"));
            signInButton.GetComponent<Renderer>().material = mat;
            mat.color = Color.blue;

            signInButton.transform.position = new Vector3(3.5f, 2f, 9f);
            signInButton.tag = "SignInButton";
            signInButton.AddComponent<Graph>();
        }
    ```

9.  <span data-ttu-id="78584-310">Agregar el **GestureRecognizer_Tapped()** responder método, que ser el *pulse* evento de usuario.</span><span class="sxs-lookup"><span data-stu-id="78584-310">Add the **GestureRecognizer_Tapped()** method, which be respond for the *Tap* user event.</span></span>

    ```csharp   
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            if(base.FocusedObject != null)
            {
                Debug.Log($"TAP on {base.FocusedObject.name}");
                base.FocusedObject.SendMessage("SignInAsync", SendMessageOptions.RequireReceiver);
            }
        }
    ```

10. <span data-ttu-id="78584-311">**Eliminar** el **Update()** método y, a continuación, **guardar los cambios** en Visual Studio antes de volver a Unity.</span><span class="sxs-lookup"><span data-stu-id="78584-311">**Delete** the **Update()** method, and then **save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-9---set-up-the-script-references"></a><span data-ttu-id="78584-312">Capítulo 9: configurar las referencias de script</span><span class="sxs-lookup"><span data-stu-id="78584-312">Chapter 9 - Set up the script references</span></span>

<span data-ttu-id="78584-313">En este capítulo tiene que colocar el **interacciones** de script en el **cámara principal**.</span><span class="sxs-lookup"><span data-stu-id="78584-313">In this Chapter you need to place the **Interactions** script onto the **Main Camera**.</span></span> <span data-ttu-id="78584-314">Ese script controlará la colocación de los demás scripts donde deben estar.</span><span class="sxs-lookup"><span data-stu-id="78584-314">That script will then handle placing the other scripts where they need to be.</span></span>

-  <span data-ttu-id="78584-315">Desde el **Scripts** carpeta en el *Panel proyecto*, arrastre la secuencia de comandos **interacciones** a la **cámara principal** de objeto, como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="78584-315">From the **Scripts** folder in the *Project Panel*, drag the script **Interactions** to the **Main Camera** object, as pictured below.</span></span>

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a><span data-ttu-id="78584-316">Capítulo 10: configuración de la etiqueta</span><span class="sxs-lookup"><span data-stu-id="78584-316">Chapter 10 - Setting up the Tag</span></span>

<span data-ttu-id="78584-317">El código que controla la mirada hará uso de la etiqueta **SignInButton** para identificar el objeto que el usuario interactuará con para iniciar sesión *Microsoft Graph*.</span><span class="sxs-lookup"><span data-stu-id="78584-317">The code handling the gaze will make use of the Tag **SignInButton** to identify which object the user will interact with to sign-in to *Microsoft Graph*.</span></span>

<span data-ttu-id="78584-318">Para crear la etiqueta:</span><span class="sxs-lookup"><span data-stu-id="78584-318">To create the Tag:</span></span>

1.  <span data-ttu-id="78584-319">Haga clic en el Editor de Unity en el **cámara principal** en el *jerarquía Panel*.</span><span class="sxs-lookup"><span data-stu-id="78584-319">In the Unity Editor click on the **Main Camera** in the *Hierarchy Panel*.</span></span>

2.  <span data-ttu-id="78584-320">En el *Panel Inspector* haga clic en el **MainCamera** *etiqueta* para abrir una lista desplegable.</span><span class="sxs-lookup"><span data-stu-id="78584-320">In the *Inspector Panel* click on the **MainCamera** *Tag* to open a drop-down list.</span></span> <span data-ttu-id="78584-321">Haga clic en **Agregar etiqueta...**</span><span class="sxs-lookup"><span data-stu-id="78584-321">Click on **Add Tag...**</span></span>

    ![](images/AzureLabs-Lab311-30.png)

3.  <span data-ttu-id="78584-322">Haga clic en el **+** botón.</span><span class="sxs-lookup"><span data-stu-id="78584-322">Click on the **+** button.</span></span>

    ![](images/AzureLabs-Lab311-31.png)

4.  <span data-ttu-id="78584-323">Escribir el nombre de etiqueta como **SignInButton** y haga clic en Guardar.</span><span class="sxs-lookup"><span data-stu-id="78584-323">Write the Tag name as **SignInButton** and click Save.</span></span>

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a><span data-ttu-id="78584-324">Capítulo 11: Compile el proyecto de Unity a UWP</span><span class="sxs-lookup"><span data-stu-id="78584-324">Chapter 11 - Build the Unity project to UWP</span></span>

<span data-ttu-id="78584-325">Todo lo necesario para la sección de Unity de este proyecto ahora se completó, por lo que es el momento de crearla desde Unity.</span><span class="sxs-lookup"><span data-stu-id="78584-325">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="78584-326">Vaya a *configuración de compilación* (\**archivo* > \* compilar configuración \*\*).</span><span class="sxs-lookup"><span data-stu-id="78584-326">Navigate to *Build Settings* (\**File* > \*Build Settings\*\*).</span></span>

    ![](images/AzureLabs-Lab311-33.png)

2.  <span data-ttu-id="78584-327">Si aún no marque **Unity C\# proyectos**.</span><span class="sxs-lookup"><span data-stu-id="78584-327">If not already, tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="78584-328">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="78584-328">Click **Build**.</span></span> <span data-ttu-id="78584-329">Unity se iniciará un **Explorador de archivos** ventana, donde se debe crear y, a continuación, seleccione una carpeta para compilar la aplicación en.</span><span class="sxs-lookup"><span data-stu-id="78584-329">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="78584-330">Crear la carpeta y asígnele el nombre **aplicación**.</span><span class="sxs-lookup"><span data-stu-id="78584-330">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="78584-331">A continuación, con el **aplicación** carpeta seleccionada, haga clic en **seleccionar la carpeta**.</span><span class="sxs-lookup"><span data-stu-id="78584-331">Then with the **App** folder selected, click **Select Folder**.</span></span>

4.  <span data-ttu-id="78584-332">Unity empezará a compilar el proyecto para el **aplicación** carpeta.</span><span class="sxs-lookup"><span data-stu-id="78584-332">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="78584-333">Una vez Unity ha finalizado la compilación (puede tardar algún tiempo), se abrirá un **Explorador de archivos** ventana en la ubicación de la compilación (comprobación de la barra de tareas, tal y como es posible que no siempre aparecen por encima de las ventanas, pero le informará de la adición de un nuevo ventana).</span><span class="sxs-lookup"><span data-stu-id="78584-333">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploy-to-hololens"></a><span data-ttu-id="78584-334">Capítulo 12 - implementación en HoloLens</span><span class="sxs-lookup"><span data-stu-id="78584-334">Chapter 12 - Deploy to HoloLens</span></span>

<span data-ttu-id="78584-335">Para implementar en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="78584-335">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="78584-336">Necesitará la dirección IP de su HoloLens (para la implementación remota), y garantizar su HoloLens se encuentra en **modo de programador.**</span><span class="sxs-lookup"><span data-stu-id="78584-336">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode.**</span></span> <span data-ttu-id="78584-337">Para ello:</span><span class="sxs-lookup"><span data-stu-id="78584-337">To do this:</span></span>

    1.  <span data-ttu-id="78584-338">Mientras que el exceso de su HoloLens, abra el **configuración**.</span><span class="sxs-lookup"><span data-stu-id="78584-338">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="78584-339">Vaya a **red e Internet** > **Wi-Fi** > **opciones avanzadas**</span><span class="sxs-lookup"><span data-stu-id="78584-339">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="78584-340">Tenga en cuenta la **IPv4** dirección.</span><span class="sxs-lookup"><span data-stu-id="78584-340">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="78584-341">A continuación, vaya a **configuración**y, a continuación, en **actualización y seguridad** > **para desarrolladores**</span><span class="sxs-lookup"><span data-stu-id="78584-341">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="78584-342">Establecer **modo de programador en**.</span><span class="sxs-lookup"><span data-stu-id="78584-342">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="78584-343">Vaya a la nueva compilación de Unity (la **aplicación** carpeta) y abra el archivo de solución con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="78584-343">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="78584-344">En el **configuración de la solución** seleccione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="78584-344">In the **Solution Configuration** select **Debug**.</span></span>

4.  <span data-ttu-id="78584-345">En el **plataforma de solución**, seleccione **x86, máquina remota**.</span><span class="sxs-lookup"><span data-stu-id="78584-345">In the **Solution Platform**, select **x86, Remote Machine**.</span></span> <span data-ttu-id="78584-346">Se le pedirá que inserte la **dirección IP** de un dispositivo remoto (el HoloLens, en este caso, lo cual observó).</span><span class="sxs-lookup"><span data-stu-id="78584-346">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab311-34.png)

5.  <span data-ttu-id="78584-347">Vaya a **compilar** menú y haga clic en **implementar solución** para transferir localmente la aplicación a su HoloLens.</span><span class="sxs-lookup"><span data-stu-id="78584-347">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6.  <span data-ttu-id="78584-348">La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas en su HoloLens, lista para iniciarse.</span><span class="sxs-lookup"><span data-stu-id="78584-348">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

## <a name="your-microsoft-graph-hololens-application"></a><span data-ttu-id="78584-349">La aplicación de Microsoft Graph HoloLens</span><span class="sxs-lookup"><span data-stu-id="78584-349">Your Microsoft Graph HoloLens application</span></span>

<span data-ttu-id="78584-350">Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha Microsoft Graph, para leer y mostrar datos de calendario del usuario.</span><span class="sxs-lookup"><span data-stu-id="78584-350">Congratulations, you built a mixed reality app that leverages the Microsoft Graph, to read and display user Calendar data.</span></span>

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="78584-351">Ejercicios de bonificación</span><span class="sxs-lookup"><span data-stu-id="78584-351">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="78584-352">Ejercicio 1</span><span class="sxs-lookup"><span data-stu-id="78584-352">Exercise 1</span></span>

<span data-ttu-id="78584-353">Usar Microsoft Graph para mostrar otra información sobre el usuario</span><span class="sxs-lookup"><span data-stu-id="78584-353">Use Microsoft Graph to display other information about the user</span></span>

-   <span data-ttu-id="78584-354">Correo electrónico del usuario / número de teléfono / imagen del perfil</span><span class="sxs-lookup"><span data-stu-id="78584-354">User email / phone number / profile picture</span></span>

### <a name="exercise-1"></a><span data-ttu-id="78584-355">Ejercicio 1</span><span class="sxs-lookup"><span data-stu-id="78584-355">Exercise 1</span></span>

<span data-ttu-id="78584-356">Implementar el control de voz para navegar por la interfaz de usuario de Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="78584-356">Implement voice control to navigate the Microsoft Graph UI.</span></span>
