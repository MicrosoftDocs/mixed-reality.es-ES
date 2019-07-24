---
title: 'MR y Azure 301: traducción de idiomas'
description: Complete este curso para aprender a implementar el Translator Text API de Azure en una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, Mixed Reality, Academia, Unity, tutorial, API, texto de traductor, hololens, envolventes, VR
ms.openlocfilehash: 6fe31d1bcb72337f0a3e8664893ea0f7c0540aae
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63554334"
---
>[!NOTE]
><span data-ttu-id="3d8fc-104">Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="3d8fc-105">Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="3d8fc-106">Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="3d8fc-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="3d8fc-108">Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="3d8fc-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-301-language-translation"></a><span data-ttu-id="3d8fc-110">MR y Azure 301: Traducción de idiomas</span><span class="sxs-lookup"><span data-stu-id="3d8fc-110">MR and Azure 301: Language translation</span></span>

<span data-ttu-id="3d8fc-111">En este curso, aprenderá a agregar funcionalidades de traducción a una aplicación de realidad mixta con Azure Cognitive Services, con el Translator Text API.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-111">In this course, you will learn how to add translation capabilities to a mixed reality application using Azure Cognitive Services, with the Translator Text API.</span></span>

![Producto final](images/AzureLabs-Lab1-00.png)

<span data-ttu-id="3d8fc-113">El Translator Text API es un servicio de traducción que funciona casi en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-113">The Translator Text API is a translation Service which works in near real-time.</span></span> <span data-ttu-id="3d8fc-114">El servicio se basa en la nube y, mediante una llamada de API de REST, una aplicación puede usar la tecnología de traducción automática de la máquina neuronal para traducir texto en otro idioma.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-114">The Service is cloud-based, and, using a REST API call, an app can make use of the neural machine translation technology to translate text to another language.</span></span> <span data-ttu-id="3d8fc-115">Para obtener más información, visite la [Página de Translator Text API de Azure](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span><span class="sxs-lookup"><span data-stu-id="3d8fc-115">For more information, visit the [Azure Translator Text API page](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span></span>

<span data-ttu-id="3d8fc-116">Al finalizar este curso, tendrá una aplicación de realidad mixta que podrá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-116">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1.  <span data-ttu-id="3d8fc-117">El usuario hablará con un micrófono conectado a un casco envolvente (VR) (o el micrófono integrado de HoloLens).</span><span class="sxs-lookup"><span data-stu-id="3d8fc-117">The user will speak into a microphone connected to an immersive (VR) headset (or the built-in microphone of HoloLens).</span></span>
2.  <span data-ttu-id="3d8fc-118">La aplicación capturará el dictado y lo enviará a Azure Translator Text API.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-118">The app will capture the dictation and send it to the Azure Translator Text API.</span></span>
3.  <span data-ttu-id="3d8fc-119">El resultado de la traducción se mostrará en un grupo de interfaz de usuario simple en la escena de Unity.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-119">The translation result will be displayed in a simple UI group in the Unity Scene.</span></span>

<span data-ttu-id="3d8fc-120">Este curso le enseñará a obtener los resultados del servicio de Traductor en una aplicación de ejemplo basada en Unity.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-120">This course will teach you how to get the results from the Translator Service into a Unity-based sample application.</span></span> <span data-ttu-id="3d8fc-121">Depende de usted que aplique estos conceptos a una aplicación personalizada que pueda estar compilando.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-121">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="3d8fc-122">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="3d8fc-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="3d8fc-123">Recurso</span><span class="sxs-lookup"><span data-stu-id="3d8fc-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="3d8fc-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="3d8fc-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="3d8fc-125"><a href="immersive-headset-hardware-details.md">Cascos envolventes</a></span><span class="sxs-lookup"><span data-stu-id="3d8fc-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="3d8fc-126">MR y Azure 301: Traducción de idiomas</span><span class="sxs-lookup"><span data-stu-id="3d8fc-126">MR and Azure 301: Language translation</span></span></td><td style="text-align: center;"> <span data-ttu-id="3d8fc-127">✔️</span><span class="sxs-lookup"><span data-stu-id="3d8fc-127">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="3d8fc-128">✔️</span><span class="sxs-lookup"><span data-stu-id="3d8fc-128">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="3d8fc-129">Aunque este curso se centra principalmente en los auriculares de Windows Mixed Reality inmersivo (VR), también puede aplicar lo que aprenda en este curso a Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-129">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="3d8fc-130">A medida que siga con el curso, verá notas sobre cualquier cambio que deba usar para admitir HoloLens.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-130">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="3d8fc-131">Al usar HoloLens, puede observar algún Eco durante la captura de voz.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-131">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3d8fc-132">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="3d8fc-132">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="3d8fc-133">Este tutorial está diseñado para desarrolladores que tienen experiencia básica con Unity y C#.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-133">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="3d8fc-134">Tenga en cuenta también que los requisitos previos y las instrucciones escritas dentro de este documento representan lo que se ha probado y comprobado en el momento de la escritura (2018 de mayo).</span><span class="sxs-lookup"><span data-stu-id="3d8fc-134">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="3d8fc-135">Puede usar el software más reciente, como se indica en el artículo [instalar las herramientas](install-the-tools.md) , aunque no se debe suponer que la información de este curso se ajusta perfectamente a lo que encontrará en el software más reciente que el que se indica a continuación.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-135">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="3d8fc-136">Se recomienda el siguiente hardware y software para este curso:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-136">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="3d8fc-137">Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para el desarrollo de auriculares envolvente (VR)</span><span class="sxs-lookup"><span data-stu-id="3d8fc-137">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="3d8fc-138">Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="3d8fc-138">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="3d8fc-139">El SDK de Windows 10 más reciente</span><span class="sxs-lookup"><span data-stu-id="3d8fc-139">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="3d8fc-140">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="3d8fc-140">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="3d8fc-141">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="3d8fc-141">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="3d8fc-142">Un [auricular de Windows Mixed Reality inmersivo (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="3d8fc-142">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="3d8fc-143">Un conjunto de auriculares con micrófono integrado (si el casco no tiene micrófonos y altavoces integrados)</span><span class="sxs-lookup"><span data-stu-id="3d8fc-143">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="3d8fc-144">Acceso a Internet para la instalación y la recuperación de traducciones de Azure</span><span class="sxs-lookup"><span data-stu-id="3d8fc-144">Internet access for Azure setup and translation retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="3d8fc-145">Antes de comenzar</span><span class="sxs-lookup"><span data-stu-id="3d8fc-145">Before you start</span></span>

- <span data-ttu-id="3d8fc-146">Para evitar que se produzcan problemas al compilar este proyecto, se recomienda encarecidamente que cree el proyecto mencionado en este tutorial en una carpeta raíz o cerca de la raíz (las rutas de acceso de carpeta largas pueden producir problemas en tiempo de compilación).</span><span class="sxs-lookup"><span data-stu-id="3d8fc-146">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="3d8fc-147">El código de este tutorial le permitirá grabar desde el dispositivo de micrófono predeterminado conectado al equipo.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-147">The code in this tutorial will allow you to record from the default microphone device connected to your PC.</span></span> <span data-ttu-id="3d8fc-148">Asegúrese de que el dispositivo de micrófono predeterminado está establecido en el dispositivo que va a usar para capturar la voz.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-148">Make sure the default microphone device is set to the device you plan to use to capture your voice.</span></span>
- <span data-ttu-id="3d8fc-149">Para permitir que su equipo habilite el dictado, vaya a **configuración > privacidad > voz, entrada manuscrita & escriba** y seleccione el botón **activar servicios de voz y sugerencias de escritura**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-149">To allow your PC to enable dictation, go to **Settings > Privacy > Speech, inking & typing** and select the button **Turn On speech services and typing suggestions**.</span></span>
- <span data-ttu-id="3d8fc-150">Si usa un micrófono y auriculares conectados (o incorporados a) el casco, asegúrese de que la opción "cuando he gastado el casco, cambiar a MIC micro" está activada en la **configuración > realidad mixta > audio y voz**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-150">If you're using a microphone and headphones connected to (or built-in to) your headset, make sure the option “When I wear my headset, switch to headset mic” is turned on in **Settings > Mixed reality > Audio and speech**.</span></span>

   ![Configuración de realidad mixta](images/AzureLabs-Lab1-00-5.png)

   ![Configuración del micrófono](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> <span data-ttu-id="3d8fc-153">Tenga en cuenta que si está desarrollando para un casco envolvente para este laboratorio, puede experimentar problemas con el dispositivo de salida de audio.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-153">Be aware that if you are developing for an immersive headset for this lab, you may experience audio output device issues.</span></span> <span data-ttu-id="3d8fc-154">Esto se debe a un problema con Unity, que se corrige en versiones posteriores de Unity (Unity 2018,2).</span><span class="sxs-lookup"><span data-stu-id="3d8fc-154">This is due to an issue with Unity, which is fixed in later versions of Unity (Unity 2018.2).</span></span> <span data-ttu-id="3d8fc-155">El problema impide que Unity cambie el dispositivo de salida de audio predeterminado en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-155">The issue prevents Unity from changing the default audio output device at run time.</span></span> <span data-ttu-id="3d8fc-156">Como solución alternativa, asegúrese de que ha completado los pasos anteriores y cierre y vuelva a abrir el editor cuando este problema se presente.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-156">As a work around, ensure you have completed the above steps, and close and re-open the Editor, when this issue presents itself.</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="3d8fc-157">Capítulo 1: Azure portal</span><span class="sxs-lookup"><span data-stu-id="3d8fc-157">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="3d8fc-158">Para usar la API de traductor de Azure, tendrá que configurar una instancia del servicio para que esté disponible para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-158">To use the Azure Translator API, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="3d8fc-159">Inicie sesión en el [portal de Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="3d8fc-159">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="3d8fc-160">Si aún no tiene una cuenta de Azure, tendrá que crear una.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="3d8fc-161">Si sigue este tutorial en una situación de aula o de laboratorio, pregunte al instructor o a uno de los Proctors para obtener ayuda para configurar la nueva cuenta.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="3d8fc-162">Una vez que haya iniciado sesión, haga clic en **nuevo** en la esquina superior izquierda y busque "Translator Text API".</span><span class="sxs-lookup"><span data-stu-id="3d8fc-162">Once you are logged in, click on **New** in the top left corner and search for "Translator Text API."</span></span> <span data-ttu-id="3d8fc-163">Seleccione **entrar**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-163">Select **Enter**.</span></span>

    ![Nuevo recurso](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > <span data-ttu-id="3d8fc-165">Es posible que la palabra **nuevo** se haya reemplazado por **crear un recurso**, en portales más recientes.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-165">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="3d8fc-166">La nueva página proporcionará una descripción del servicio *Translator Text API* .</span><span class="sxs-lookup"><span data-stu-id="3d8fc-166">The new page will provide a description of the *Translator Text API* Service.</span></span> <span data-ttu-id="3d8fc-167">En la parte inferior izquierda de esta página, seleccione el botón **crear** para crear una asociación con este servicio.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-167">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Crear servicio de Translator Text API](images/AzureLabs-Lab1-03.png)

4.  <span data-ttu-id="3d8fc-169">Una vez que haya hecho clic en **crear**:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-169">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="3d8fc-170">Inserte el **nombre** que desee para esta instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-170">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="3d8fc-171">Seleccione una **suscripción**adecuada.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-171">Select an appropriate **Subscription**.</span></span>
    3. <span data-ttu-id="3d8fc-172">Seleccione el **plan de tarifa** adecuado para usted; si es la primera vez que crea un *servicio de Translator Text*, debe tener a su disposición un nivel gratis (denominado F0).</span><span class="sxs-lookup"><span data-stu-id="3d8fc-172">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Translator Text Service*, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="3d8fc-173">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="3d8fc-174">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación de una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="3d8fc-175">Se recomienda mantener todos los servicios de Azure asociados a un único proyecto (por ejemplo, estos laboratorios) en un grupo de recursos común).</span><span class="sxs-lookup"><span data-stu-id="3d8fc-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="3d8fc-176">Si desea leer más información sobre los grupos de recursos de Azure, [visite el artículo sobre el grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="3d8fc-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="3d8fc-177">Determine la **Ubicación** del grupo de recursos (si va a crear un nuevo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="3d8fc-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="3d8fc-178">Idealmente, la ubicación estará en la región donde se ejecutará la aplicación.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="3d8fc-179">Algunos recursos de Azure solo están disponibles en determinadas regiones.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="3d8fc-180">También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="3d8fc-181">Seleccione **Crear**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-181">Select **Create**.</span></span>

        ![Seleccione el botón crear.](images/AzureLabs-Lab1-04.png)

5.  <span data-ttu-id="3d8fc-183">Una vez que haya hecho clic en **crear**, tendrá que esperar a que se cree el servicio, lo que puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-183">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="3d8fc-184">Una vez que se crea la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-184">A notification will appear in the portal once the Service instance is created.</span></span> 

    ![Notificación de creación de servicio de Azure](images/AzureLabs-Lab1-05.png)

7.  <span data-ttu-id="3d8fc-186">Haga clic en la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-186">Click on the notification to explore your new Service instance.</span></span> 

    ![Vaya a menú emergente de recursos.](images/AzureLabs-Lab1-06.png)

8.  <span data-ttu-id="3d8fc-188">Haga clic en el botón **ir a recurso** de la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="3d8fc-189">Se le dirigirá a la nueva instancia de servicio de Translator Text API.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-189">You will be taken to your new Translator Text API Service instance.</span></span> 

    ![Translator Text API página de servicio](images/AzureLabs-Lab1-07.png)

9.  <span data-ttu-id="3d8fc-191">En este tutorial, la aplicación necesitará realizar llamadas al servicio, lo que se realiza mediante el uso de la clave de suscripción del servicio.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-191">Within this tutorial, your application will need to make calls to your Service, which is done through using your Service’s Subscription Key.</span></span> 
10. <span data-ttu-id="3d8fc-192">En la página *Inicio rápido* del servicio de *Translator Text* , navegue hasta el primer paso, *grabe sus claves*y haga clic en **claves** (también puede conseguirlo haciendo clic en las teclas de hipervínculo azul, que se encuentran en el menú de navegación servicios, indicado por el icono de clave).</span><span class="sxs-lookup"><span data-stu-id="3d8fc-192">From the *Quick start* page of your *Translator Text* Service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the Services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="3d8fc-193">Esto revelará las *claves*de servicio.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-193">This will reveal your Service *Keys*.</span></span>
11. <span data-ttu-id="3d8fc-194">Realice una copia de una de las claves que se muestran, ya que la necesitará más adelante en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="3d8fc-195">Capítulo 2: configurar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="3d8fc-195">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="3d8fc-196">Configure y pruebe sus auriculares de la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-196">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="3d8fc-197">No necesitará controladores de movimiento para este curso.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-197">You will not need motion controllers for this course.</span></span> <span data-ttu-id="3d8fc-198">Si necesita admitir la configuración de un casco inmersivo, [siga estos pasos](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="3d8fc-198">If you need support setting up an immersive headset, please [follow these steps](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

<span data-ttu-id="3d8fc-199">Lo siguiente es una configuración típica para desarrollar con la realidad mixta y, como tal, es una buena plantilla para otros proyectos:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-199">The following is a typical set up for developing with mixed reality and, as such, is a good template for other projects:</span></span>

1.  <span data-ttu-id="3d8fc-200">Abra *Unity* y haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-200">Open *Unity* and click **New**.</span></span> 

    ![Inicie el nuevo proyecto de Unity.](images/AzureLabs-Lab1-08.png)

2.  <span data-ttu-id="3d8fc-202">Ahora tendrá que proporcionar un nombre de proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="3d8fc-203">Inserte **MR_Translation**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-203">Insert **MR_Translation**.</span></span> <span data-ttu-id="3d8fc-204">Asegúrese de que el tipo de proyecto está establecido en **3D**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="3d8fc-205">Establezca la *Ubicación* en algún lugar adecuado para usted (Recuerde que, más cerca de los directorios raíz es mejor).</span><span class="sxs-lookup"><span data-stu-id="3d8fc-205">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="3d8fc-206">A continuación, haga clic en **crear proyecto**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-206">Then, click **Create project**.</span></span>

    ![Proporcione los detalles del nuevo proyecto de Unity.](images/AzureLabs-Lab1-09.png)

3.  <span data-ttu-id="3d8fc-208">Con Unity abierto, merece la pena comprobar que el **Editor** de scripts predeterminado está establecido en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="3d8fc-209">Vaya a **editar > preferencias** y, a continuación, en la nueva ventana, vaya a **herramientas externas**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="3d8fc-210">Cambie el **Editor de script externo** a **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="3d8fc-211">Cierre la ventana **preferencias** .</span><span class="sxs-lookup"><span data-stu-id="3d8fc-211">Close the **Preferences** window.</span></span>

    ![Actualice las preferencias del editor de scripts.](images/AzureLabs-Lab1-10.png)

4.  <span data-ttu-id="3d8fc-213">A continuación, vaya a **archivo > configuración de compilación** y cambie la plataforma a **plataforma universal de Windows**, haciendo clic en el botón **cambiar plataforma** .</span><span class="sxs-lookup"><span data-stu-id="3d8fc-213">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Ventana Configuración de compilación, cambiar plataforma a UWP.](images/AzureLabs-Lab1-11.png)

5.  <span data-ttu-id="3d8fc-215">Vaya a **archivo > configuración de compilación** y asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-215">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="3d8fc-216">El **dispositivo de destino** se establece en **cualquier dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-216">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="3d8fc-217">Para Microsoft HoloLens, establezca el **dispositivo de destino** en *hololens*.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-217">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="3d8fc-218">El **tipo de compilación** se establece en **D3D**</span><span class="sxs-lookup"><span data-stu-id="3d8fc-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="3d8fc-219">**SDK** está establecido en la **versión más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="3d8fc-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="3d8fc-220">La **versión de Visual Studio** está establecida en la **más reciente instalada**</span><span class="sxs-lookup"><span data-stu-id="3d8fc-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="3d8fc-221">**Compilar y ejecutar** está establecido en **equipo local**</span><span class="sxs-lookup"><span data-stu-id="3d8fc-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="3d8fc-222">Guarde la escena y agréguela a la compilación.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="3d8fc-223">Para ello, seleccione **Agregar escenas abiertas**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="3d8fc-224">Aparecerá una ventana de guardar.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-224">A save window will appear.</span></span>

            ![Haga clic en el botón Agregar escenas abiertas](images/AzureLabs-Lab1-12.png)

        2. <span data-ttu-id="3d8fc-226">Cree una nueva carpeta para este, y en cualquier momento, en el futuro, seleccione el botón **nueva carpeta** para crear una nueva carpeta, asígnele el nombre Scenes.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Crear nueva carpeta de scripts](images/AzureLabs-Lab1-13.png)

        3. <span data-ttu-id="3d8fc-228">Abra la carpeta Scenes recién creada y, a continuación, en el campo *nombre de archivo*:, escriba **MR_TranslationScene**y, a continuación, presione **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_TranslationScene**, then press **Save**.</span></span>

            ![Asigne un nombre a la nueva escena.](images/AzureLabs-Lab1-14.png)

            > <span data-ttu-id="3d8fc-230">Tenga en cuenta que debe guardar las escenas de Unity dentro de la carpeta *assets* , ya que deben estar asociadas con el proyecto Unity.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="3d8fc-231">La creación de la carpeta Scenes (y otras carpetas similares) es una forma habitual de estructurar un proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="3d8fc-232">El resto de la configuración, en la *configuración de compilación*, debe dejarse como predeterminada por ahora.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="3d8fc-233">En la ventana *configuración de compilación* , haga clic en el botón Configuración del **reproductor** ; se abrirá el panel relacionado en el espacio donde se encuentra el *Inspector* .</span><span class="sxs-lookup"><span data-stu-id="3d8fc-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Abra configuración del reproductor.](images/AzureLabs-Lab1-15.png)

7. <span data-ttu-id="3d8fc-235">En este panel, deben comprobarse algunas opciones de configuración:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="3d8fc-236">En la pestaña **otros valores** :</span><span class="sxs-lookup"><span data-stu-id="3d8fc-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="3d8fc-237">La **versión de scripting en tiempo de ejecución** debe ser **estable** (.net 3,5 equivalente).</span><span class="sxs-lookup"><span data-stu-id="3d8fc-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="3d8fc-238">El **back-end** de scripting debe ser **.net**</span><span class="sxs-lookup"><span data-stu-id="3d8fc-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="3d8fc-239">El **nivel de compatibilidad de API** debe ser **.net 4,6**</span><span class="sxs-lookup"><span data-stu-id="3d8fc-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Actualice otras opciones de configuración.](images/AzureLabs-Lab1-16.png)
      
    2. <span data-ttu-id="3d8fc-241">En la pestaña **configuración de publicación** , en **capacidades**, seleccione:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="3d8fc-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="3d8fc-242">**InternetClient**</span></span>
        2. <span data-ttu-id="3d8fc-243">**Micrófono**</span><span class="sxs-lookup"><span data-stu-id="3d8fc-243">**Microphone**</span></span>

            ![Actualizando la configuración de publicación.](images/AzureLabs-Lab1-17.png)

    3. <span data-ttu-id="3d8fc-245">Más abajo en el panel, en la **configuración de XR** (se encuentra debajo de **configuración de publicación**), tick **Virtual Reality compatible**, asegúrese de que se agrega el **SDK de Windows Mixed Reality** .</span><span class="sxs-lookup"><span data-stu-id="3d8fc-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Actualice la configuración de X R.](images/AzureLabs-Lab1-18.png)

8.  <span data-ttu-id="3d8fc-247">De nuevo en la **configuración de compilación**, los *proyectos de Unity C#*  ya no están atenuados; Marque la casilla situada junto a este.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-247">Back in **Build Settings**, *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="3d8fc-248">Cierre la ventana Configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="3d8fc-249">Guarde la escena y el proyecto (**archivo > guardar la escena o el archivo > guardar proyecto**).</span><span class="sxs-lookup"><span data-stu-id="3d8fc-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="3d8fc-250">Capítulo 3: configuración de la cámara principal</span><span class="sxs-lookup"><span data-stu-id="3d8fc-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3d8fc-251">Si desea omitir el componente *de configuración de Unity* de este curso y continuar directamente en el código, no dude en [Descargar este. unitypackage Tools](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), impórtelo en el proyecto como un [*paquete personalizado*](https://docs.unity3d.com/Manual/AssetPackages.html)y, después, continúe con el [capítulo 5](#chapter-5--create-the-results-class).</span><span class="sxs-lookup"><span data-stu-id="3d8fc-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), import it into your project as a [*Custom Package*](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-results-class).</span></span> <span data-ttu-id="3d8fc-252">Todavía tendrá que crear un proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-252">You will still need to create a Unity Project.</span></span>

1.  <span data-ttu-id="3d8fc-253">En el *Panel jerarquía*, encontrará un objeto denominado **cámara principal**, este objeto representa el punto de vista "principal" una vez que está "dentro" de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-253">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your “head” point of view once you are “inside” your application.</span></span>
2.  <span data-ttu-id="3d8fc-254">Con el panel de Unity delante de usted, seleccione la **cámara principal GameObject**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-254">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="3d8fc-255">Observará que el *panel Inspector* (generalmente situado a la derecha, dentro del panel) mostrará los distintos componentes de ese *GameObject*, con la *transformación* en la parte superior, la *cámara*y otros componentes.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-255">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="3d8fc-256">Tendrá que restablecer la transformación de la cámara principal, de modo que esté colocada correctamente.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-256">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>
3.  <span data-ttu-id="3d8fc-257">Para ello, seleccione el icono de **engranaje** situado junto al componente de *transformación* de la cámara y seleccione **restablecer**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-257">To do this, select the **Gear** icon next to the Camera’s *Transform* component, and selecting **Reset**.</span></span> 

    ![Restablezca la transformación de cámara principal.](images/AzureLabs-Lab1-19.png)
 
4.  <span data-ttu-id="3d8fc-259">El componente de *transformación* debería tener el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-259">The *Transform* component should then look like:</span></span>

    1. <span data-ttu-id="3d8fc-260">La *posición* se establece en **0, 0,0**</span><span class="sxs-lookup"><span data-stu-id="3d8fc-260">The *Position* is set to **0, 0, 0**</span></span>
    2. <span data-ttu-id="3d8fc-261">La *rotación* se establece en **0,** 0,0</span><span class="sxs-lookup"><span data-stu-id="3d8fc-261">*Rotation* is set to **0, 0, 0**</span></span>
    3. <span data-ttu-id="3d8fc-262">Y *escala* se establece en **1, 1, 1**</span><span class="sxs-lookup"><span data-stu-id="3d8fc-262">And *Scale* is set to **1, 1, 1**</span></span>

        ![Transformación de la información de la cámara](images/AzureLabs-Lab1-20.png)

5.  <span data-ttu-id="3d8fc-264">A continuación, con el objeto de **cámara principal** seleccionado, vea el botón **Agregar componente** situado en la parte inferior del *panel Inspector*.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-264">Next, with the **Main Camera** object selected, see the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span> 
6.  <span data-ttu-id="3d8fc-265">Seleccione ese botón y busque (escriba el origen de *audio* en el campo de búsqueda o navegue por las secciones) del componente denominado **origen de audio** como se muestra a continuación y selecciónelo (presione Entrar en él también funciona).</span><span class="sxs-lookup"><span data-stu-id="3d8fc-265">Select that button, and search (by either typing *Audio Source* into the search field or navigating the sections) for the component called **Audio Source** as shown below and select it (pressing enter on it also works).</span></span>
7.  <span data-ttu-id="3d8fc-266">Se agregará un componente de *origen de audio* a la **cámara principal**, como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-266">An *Audio Source* component will be added to the **Main Camera**, as demonstrated below.</span></span>

    ![Agregue un componente de origen de audio.](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > <span data-ttu-id="3d8fc-268">En el caso de Microsoft HoloLens, también tendrá que cambiar lo siguiente, que forman parte del componente de **cámara** de la **cámara principal**:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-268">For Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component on your **Main Camera**:</span></span>
    > - <span data-ttu-id="3d8fc-269">**Borrar marcas:** Color sólido.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-269">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="3d8fc-270">**Información general** ' Black, Alpha 0 ' – color Hex: #00000000.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-270">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

## <a name="chapter-4--setup-debug-canvas"></a><span data-ttu-id="3d8fc-271">Capítulo 4: configurar el lienzo de depuración</span><span class="sxs-lookup"><span data-stu-id="3d8fc-271">Chapter 4 – Setup Debug Canvas</span></span>

<span data-ttu-id="3d8fc-272">Para mostrar la entrada y la salida de la traducción, es necesario crear una interfaz de usuario básica.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-272">To show the input and output of the translation, a basic UI needs to be created.</span></span> <span data-ttu-id="3d8fc-273">En este curso, creará un objeto de interfaz de usuario de lienzo, con varios objetos de texto para mostrar los datos.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-273">For this course, you will create a Canvas UI object, with several ‘Text’ objects to show the data.</span></span>

1.  <span data-ttu-id="3d8fc-274">Haga clic con el botón secundario en un área vacía del *Panel jerarquía*, en **UI**, agregar un **lienzo**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-274">Right-click in an empty area of the *Hierarchy Panel*, under **UI**, add a **Canvas**.</span></span>

    ![Agregue un nuevo objeto de interfaz de usuario de lienzo.](images/AzureLabs-Lab1-22.png)

2.  <span data-ttu-id="3d8fc-276">Con el objeto Canvas seleccionado, en el *panel Inspector* (dentro del componente ' Canvas '), cambie el **modo de representación** a **espacio universal**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-276">With the Canvas object selected, in the *Inspector Panel* (within the ‘Canvas’ component), change **Render Mode** to **World Space**.</span></span> 
3.  <span data-ttu-id="3d8fc-277">A continuación, cambie los siguientes parámetros en la *transformación Rect del panel Inspector*:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-277">Next, change the following parameters in the *Inspector Panel’s Rect Transform*:</span></span>

    1. <span data-ttu-id="3d8fc-278">*POS*    X 0 Y 0 Z 40 -  </span><span class="sxs-lookup"><span data-stu-id="3d8fc-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span></span>
    2. <span data-ttu-id="3d8fc-279">*Ancho* : 500</span><span class="sxs-lookup"><span data-stu-id="3d8fc-279">*Width* -    500</span></span>
    3. <span data-ttu-id="3d8fc-280">*Alto* : 300</span><span class="sxs-lookup"><span data-stu-id="3d8fc-280">*Height* -   300</span></span>
    4. <span data-ttu-id="3d8fc-281">*Escala*    X 0,13 Y 0,13 Z 0,13 - </span><span class="sxs-lookup"><span data-stu-id="3d8fc-281">*Scale* - **X** 0.13 **Y** 0.13  **Z** 0.13</span></span>

        ![Actualice la transformación Rect para el lienzo.](images/AzureLabs-Lab1-23.png)
 
4.  <span data-ttu-id="3d8fc-283">Haga clic con el botón derecho en el **lienzo** en el *Panel jerarquía*, en **UI**, y agregue un **Panel**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-283">Right click on the **Canvas** in the *Hierarchy Panel*, under **UI**, and add a **Panel**.</span></span> <span data-ttu-id="3d8fc-284">Este **Panel** proporcionará un fondo para el texto que se mostrará en la escena.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-284">This **Panel** will provide a background to the text that you will be displaying in the scene.</span></span>
5.  <span data-ttu-id="3d8fc-285">Haga clic con el botón derecho en el **Panel de** jerarquías, en **UI**, y agregue un **objeto de texto**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-285">Right click on the **Panel** in the *Hierarchy Panel*, under **UI**, and add a **Text object**.</span></span> <span data-ttu-id="3d8fc-286">Repita el mismo proceso hasta que haya creado cuatro objetos de texto de interfaz de usuario en total (sugerencia: Si tiene seleccionado el primer objeto ' text ', simplemente presione **' Ctrl ' + ' d '** para duplicarlo, hasta que tenga cuatro en total).</span><span class="sxs-lookup"><span data-stu-id="3d8fc-286">Repeat the same process until you have created four UI Text objects in total (Hint: if you have the first ‘Text’ object selected, you can simply press **‘Ctrl’ + ‘D’**, to duplicate it, until you have four in total).</span></span> 
6.  <span data-ttu-id="3d8fc-287">Para cada **objeto de texto**, selecciónelo y use las tablas siguientes para establecer los parámetros en el *panel Inspector*.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-287">For each **Text Object**, select it and use the below tables to set the parameters in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="3d8fc-288">Para el componente de *transformación Rect* :</span><span class="sxs-lookup"><span data-stu-id="3d8fc-288">For the *Rect Transform* component:</span></span>

        | <span data-ttu-id="3d8fc-289">NOMBRE</span><span class="sxs-lookup"><span data-stu-id="3d8fc-289">Name</span></span>                   | <span data-ttu-id="3d8fc-290">Transformación: *posición*</span><span class="sxs-lookup"><span data-stu-id="3d8fc-290">Transform - *Position*</span></span>             | <span data-ttu-id="3d8fc-291">Ancho</span><span class="sxs-lookup"><span data-stu-id="3d8fc-291">Width</span></span>      | <span data-ttu-id="3d8fc-292">Alto</span><span class="sxs-lookup"><span data-stu-id="3d8fc-292">Height</span></span>    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | <span data-ttu-id="3d8fc-293">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="3d8fc-293">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="3d8fc-294">**X** -80 **Y** 90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="3d8fc-294">**X** -80 **Y** 90 **Z** 0</span></span>         | <span data-ttu-id="3d8fc-295">300</span><span class="sxs-lookup"><span data-stu-id="3d8fc-295">300</span></span>        | <span data-ttu-id="3d8fc-296">30</span><span class="sxs-lookup"><span data-stu-id="3d8fc-296">30</span></span>        |
        | <span data-ttu-id="3d8fc-297">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="3d8fc-297">AzureResponseLabel</span></span>     | <span data-ttu-id="3d8fc-298">**X** -80 **Y** 30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="3d8fc-298">**X** -80 **Y** 30 **Z** 0</span></span>         | <span data-ttu-id="3d8fc-299">300</span><span class="sxs-lookup"><span data-stu-id="3d8fc-299">300</span></span>        | <span data-ttu-id="3d8fc-300">30</span><span class="sxs-lookup"><span data-stu-id="3d8fc-300">30</span></span>        |
        | <span data-ttu-id="3d8fc-301">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="3d8fc-301">DictationLabel</span></span>         | <span data-ttu-id="3d8fc-302">**X** -80 **Y** -30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="3d8fc-302">**X** -80 **Y** -30 **Z** 0</span></span>        | <span data-ttu-id="3d8fc-303">300</span><span class="sxs-lookup"><span data-stu-id="3d8fc-303">300</span></span>        | <span data-ttu-id="3d8fc-304">30</span><span class="sxs-lookup"><span data-stu-id="3d8fc-304">30</span></span>        |
        | <span data-ttu-id="3d8fc-305">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="3d8fc-305">TranslationResultLabel</span></span> | <span data-ttu-id="3d8fc-306">**X** -80 **Y** -90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="3d8fc-306">**X** -80 **Y** -90 **Z** 0</span></span>        | <span data-ttu-id="3d8fc-307">300</span><span class="sxs-lookup"><span data-stu-id="3d8fc-307">300</span></span>        | <span data-ttu-id="3d8fc-308">30</span><span class="sxs-lookup"><span data-stu-id="3d8fc-308">30</span></span>        |


    2. <span data-ttu-id="3d8fc-309">Para el componente de **texto (Script)** :</span><span class="sxs-lookup"><span data-stu-id="3d8fc-309">For the **Text (Script)** component:</span></span>


        | <span data-ttu-id="3d8fc-310">Name</span><span class="sxs-lookup"><span data-stu-id="3d8fc-310">Name</span></span>                   | <span data-ttu-id="3d8fc-311">Text</span><span class="sxs-lookup"><span data-stu-id="3d8fc-311">Text</span></span>               | <span data-ttu-id="3d8fc-312">Tamaño de fuente</span><span class="sxs-lookup"><span data-stu-id="3d8fc-312">Font Size</span></span>    |
        |:----------------------:|:------------------:|:------------:|
        | <span data-ttu-id="3d8fc-313">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="3d8fc-313">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="3d8fc-314">Estado del micrófono:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-314">Microphone Status:</span></span> | <span data-ttu-id="3d8fc-315">20</span><span class="sxs-lookup"><span data-stu-id="3d8fc-315">20</span></span>           |
        | <span data-ttu-id="3d8fc-316">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="3d8fc-316">AzureResponseLabel</span></span>     | <span data-ttu-id="3d8fc-317">Respuesta web de Azure</span><span class="sxs-lookup"><span data-stu-id="3d8fc-317">Azure Web Response</span></span> | <span data-ttu-id="3d8fc-318">20</span><span class="sxs-lookup"><span data-stu-id="3d8fc-318">20</span></span>           |
        | <span data-ttu-id="3d8fc-319">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="3d8fc-319">DictationLabel</span></span>         |   <span data-ttu-id="3d8fc-320">Acaba de decir:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-320">You just said:</span></span>   | <span data-ttu-id="3d8fc-321">20</span><span class="sxs-lookup"><span data-stu-id="3d8fc-321">20</span></span>           |
        | <span data-ttu-id="3d8fc-322">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="3d8fc-322">TranslationResultLabel</span></span> |    <span data-ttu-id="3d8fc-323">Automática</span><span class="sxs-lookup"><span data-stu-id="3d8fc-323">Translation:</span></span>    | <span data-ttu-id="3d8fc-324">20</span><span class="sxs-lookup"><span data-stu-id="3d8fc-324">20</span></span>           |

        ![Escriba los valores correspondientes para las etiquetas de la interfaz de usuario.](images/AzureLabs-Lab1-24.png)

    3. <span data-ttu-id="3d8fc-326">Además, haga que el estilo de fuente esté en **negrita**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-326">Also, make the Font Style **Bold**.</span></span> <span data-ttu-id="3d8fc-327">Esto hará que el texto sea más fácil de leer.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-327">This will make the text easier to read.</span></span>

        ![Fuente Negrita.](images/AzureLabs-Lab1-25.png)

7.  <span data-ttu-id="3d8fc-329">Para cada *objeto de texto de interfaz de usuario* creado en el [capítulo 5](#chapter-5--create-the-results-class), cree un nuevo **objeto de texto de interfaz de usuario** *secundaria* .</span><span class="sxs-lookup"><span data-stu-id="3d8fc-329">For each *UI Text object* created in [Chapter 5](#chapter-5--create-the-results-class), create a new *child* **UI Text object**.</span></span> <span data-ttu-id="3d8fc-330">Estos elementos secundarios mostrarán la salida de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-330">These children will display the output of the application.</span></span> <span data-ttu-id="3d8fc-331">Cree objetos *secundarios* haciendo clic con el botón derecho en el elemento primario previsto (por ejemplo, *MicrophoneStatusLabel*) y, a continuación, seleccione **interfaz de usuario** y, después, seleccione **texto**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-331">Create *child* objects through right-clicking your intended parent (e.g. *MicrophoneStatusLabel*) and then select **UI** and then select **Text**.</span></span>
8.  <span data-ttu-id="3d8fc-332">Para cada uno de estos elementos secundarios, selecciónelo y use las tablas siguientes para establecer los parámetros en el panel del inspector.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-332">For each of these children, select it and use the below tables to set the parameters in the Inspector Panel.</span></span>

    1. <span data-ttu-id="3d8fc-333">Para el componente de **transformación Rect** :</span><span class="sxs-lookup"><span data-stu-id="3d8fc-333">For the **Rect Transform** component:</span></span>

        | <span data-ttu-id="3d8fc-334">NOMBRE</span><span class="sxs-lookup"><span data-stu-id="3d8fc-334">Name</span></span>                  | <span data-ttu-id="3d8fc-335">Transformación: *posición*</span><span class="sxs-lookup"><span data-stu-id="3d8fc-335">Transform - *Position*</span></span> | <span data-ttu-id="3d8fc-336">Ancho</span><span class="sxs-lookup"><span data-stu-id="3d8fc-336">Width</span></span>      | <span data-ttu-id="3d8fc-337">Alto</span><span class="sxs-lookup"><span data-stu-id="3d8fc-337">Height</span></span>    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | <span data-ttu-id="3d8fc-338">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="3d8fc-338">MicrophoneStatusText</span></span>  | <span data-ttu-id="3d8fc-339">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="3d8fc-339">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="3d8fc-340">300</span><span class="sxs-lookup"><span data-stu-id="3d8fc-340">300</span></span>        | <span data-ttu-id="3d8fc-341">30</span><span class="sxs-lookup"><span data-stu-id="3d8fc-341">30</span></span>        |
        | <span data-ttu-id="3d8fc-342">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="3d8fc-342">AzureResponseText</span></span>     | <span data-ttu-id="3d8fc-343">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="3d8fc-343">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="3d8fc-344">300</span><span class="sxs-lookup"><span data-stu-id="3d8fc-344">300</span></span>        | <span data-ttu-id="3d8fc-345">30</span><span class="sxs-lookup"><span data-stu-id="3d8fc-345">30</span></span>        |
        | <span data-ttu-id="3d8fc-346">DictationText</span><span class="sxs-lookup"><span data-stu-id="3d8fc-346">DictationText</span></span>         | <span data-ttu-id="3d8fc-347">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="3d8fc-347">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="3d8fc-348">300</span><span class="sxs-lookup"><span data-stu-id="3d8fc-348">300</span></span>        | <span data-ttu-id="3d8fc-349">30</span><span class="sxs-lookup"><span data-stu-id="3d8fc-349">30</span></span>        |
        | <span data-ttu-id="3d8fc-350">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="3d8fc-350">TranslationResultText</span></span> | <span data-ttu-id="3d8fc-351">X 0 Y-30 Z 0</span><span class="sxs-lookup"><span data-stu-id="3d8fc-351">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="3d8fc-352">300</span><span class="sxs-lookup"><span data-stu-id="3d8fc-352">300</span></span>        | <span data-ttu-id="3d8fc-353">30</span><span class="sxs-lookup"><span data-stu-id="3d8fc-353">30</span></span>        |

    2. <span data-ttu-id="3d8fc-354">Para el componente de **texto (Script)** :</span><span class="sxs-lookup"><span data-stu-id="3d8fc-354">For the **Text (Script)** component:</span></span>

        | <span data-ttu-id="3d8fc-355">NOMBRE</span><span class="sxs-lookup"><span data-stu-id="3d8fc-355">Name</span></span>                  | <span data-ttu-id="3d8fc-356">Text</span><span class="sxs-lookup"><span data-stu-id="3d8fc-356">Text</span></span>          | <span data-ttu-id="3d8fc-357">Tamaño de fuente</span><span class="sxs-lookup"><span data-stu-id="3d8fc-357">Font Size</span></span>    |
        |:---------------------:|:-------------:|:------------:|
        | <span data-ttu-id="3d8fc-358">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="3d8fc-358">MicrophoneStatusText</span></span>  |      <span data-ttu-id="3d8fc-359">??</span><span class="sxs-lookup"><span data-stu-id="3d8fc-359">??</span></span>       | <span data-ttu-id="3d8fc-360">20</span><span class="sxs-lookup"><span data-stu-id="3d8fc-360">20</span></span>           |
        | <span data-ttu-id="3d8fc-361">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="3d8fc-361">AzureResponseText</span></span>     |      <span data-ttu-id="3d8fc-362">??</span><span class="sxs-lookup"><span data-stu-id="3d8fc-362">??</span></span>       | <span data-ttu-id="3d8fc-363">20</span><span class="sxs-lookup"><span data-stu-id="3d8fc-363">20</span></span>           |
        | <span data-ttu-id="3d8fc-364">DictationText</span><span class="sxs-lookup"><span data-stu-id="3d8fc-364">DictationText</span></span>         |      <span data-ttu-id="3d8fc-365">??</span><span class="sxs-lookup"><span data-stu-id="3d8fc-365">??</span></span>       | <span data-ttu-id="3d8fc-366">20</span><span class="sxs-lookup"><span data-stu-id="3d8fc-366">20</span></span>           |
        | <span data-ttu-id="3d8fc-367">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="3d8fc-367">TranslationResultText</span></span> |      <span data-ttu-id="3d8fc-368">??</span><span class="sxs-lookup"><span data-stu-id="3d8fc-368">??</span></span>       | <span data-ttu-id="3d8fc-369">20</span><span class="sxs-lookup"><span data-stu-id="3d8fc-369">20</span></span>           |

9. <span data-ttu-id="3d8fc-370">A continuación, seleccione la opción de alineación ' centro ' para cada componente de texto:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-370">Next, select the 'centre' alignment option for each text component:</span></span>

    ![alinear texto.](images/AzureLabs-Lab1-26.png)

10. <span data-ttu-id="3d8fc-372">Para asegurarse de que los objetos de texto de la interfaz de usuario **secundarios** se pueden leer fácilmente, cambie su *color*.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-372">To ensure the **child UI Text** objects are easily readable, change their *Color*.</span></span> <span data-ttu-id="3d8fc-373">Para ello, haga clic en la barra (actualmente ' negra ') junto a *color*.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-373">Do this by clicking on the bar (currently ‘Black’) next to *Color*.</span></span> 

    ![Escriba los valores correspondientes para las salidas de texto de la interfaz de usuario.](images/AzureLabs-Lab1-27.png)
 
11. <span data-ttu-id="3d8fc-375">A continuación, en la ventana nuevo, pequeño, *color* , cambie el *color Hex* a: **0032EAFF**</span><span class="sxs-lookup"><span data-stu-id="3d8fc-375">Then, in the new, little, *Color* window, change the *Hex Color* to: **0032EAFF**</span></span>

    ![Actualice el color a azul.](images/AzureLabs-Lab1-28.png)
 
12. <span data-ttu-id="3d8fc-377">A continuación se muestra el aspecto de la **interfaz de usuario** .</span><span class="sxs-lookup"><span data-stu-id="3d8fc-377">Below is how the **UI** should look.</span></span>
    1.  <span data-ttu-id="3d8fc-378">En el *Panel jerarquía*:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-378">In the *Hierarchy Panel*:</span></span>

        ![Tienen una jerarquía en la estructura proporcionada.](images/AzureLabs-Lab1-29.png)

    2.  <span data-ttu-id="3d8fc-380">En las vistas de *escena* y *juego*:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-380">In the *Scene* and *Game Views*:</span></span>

        ![Tenga las vistas escena y juego en la misma estructura.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a><span data-ttu-id="3d8fc-382">Capítulo 5: crear la clase de resultados</span><span class="sxs-lookup"><span data-stu-id="3d8fc-382">Chapter 5 – Create the Results class</span></span>

<span data-ttu-id="3d8fc-383">El primer script que debe crear es la clase *Results* , que es responsable de proporcionar una manera de ver los resultados de la traducción.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-383">The first script you need to create is the *Results* class, which is responsible for providing a way to see the results of translation.</span></span> <span data-ttu-id="3d8fc-384">La clase almacena y muestra lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-384">The Class stores and displays the following:</span></span> 

- <span data-ttu-id="3d8fc-385">Resultado de la respuesta de Azure.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-385">The response result from Azure.</span></span>
- <span data-ttu-id="3d8fc-386">El estado del micrófono.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-386">The microphone status.</span></span> 
- <span data-ttu-id="3d8fc-387">Resultado del dictado (voz a texto).</span><span class="sxs-lookup"><span data-stu-id="3d8fc-387">The result of the dictation (voice to text).</span></span>
- <span data-ttu-id="3d8fc-388">Resultado de la conversión.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-388">The result of the translation.</span></span>

<span data-ttu-id="3d8fc-389">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-389">To create this class:</span></span> 

1.  <span data-ttu-id="3d8fc-390">Haga clic con el botón derecho en el *panel Proyecto*y, a continuación, **cree > carpeta**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-390">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="3d8fc-391">Asigne a la carpeta el nombre scripts.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-391">Name the folder **Scripts**.</span></span> 
 
    ![Crear carpeta de scripts.](images/AzureLabs-Lab1-31.png)

    ![Abra la carpeta scripts.](images/AzureLabs-Lab1-32.png)
 
2.  <span data-ttu-id="3d8fc-394">Con la  carpeta scripts creada, haga doble clic en ella para abrirla.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-394">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="3d8fc-395">Después, dentro de esa carpeta, haga clic con el botón derecho y seleccione **crear >** después  **C# script**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-395">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="3d8fc-396">Asigne un nombre a los *resultados*del script.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-396">Name the script *Results*.</span></span> 

    ![Cree el primer script.](images/AzureLabs-Lab1-33.png)
 
3.  <span data-ttu-id="3d8fc-398">Haga doble clic en el nuevo script de *resultados* para abrirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-398">Double click on the new *Results* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="3d8fc-399">Inserte los espacios de nombres siguientes:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-399">Insert the following namespaces:</span></span>

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  <span data-ttu-id="3d8fc-400">Dentro de la clase, inserte las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-400">Inside the Class insert the following variables:</span></span>

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  <span data-ttu-id="3d8fc-401">A continuación, agregue el método *activo ()* , al que se llamará cuando se inicialice la clase.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-401">Then add the *Awake()* method, which will be called when the class initializes.</span></span> 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  <span data-ttu-id="3d8fc-402">Por último, agregue los métodos que son responsables de generar la información de los diversos resultados en la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-402">Finally, add the methods which are responsible for outputting the various results information to the UI.</span></span> 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  <span data-ttu-id="3d8fc-403">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-403">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-6--create-the-microphonemanager-class"></a><span data-ttu-id="3d8fc-404">Capítulo 6: crear la clase *MicrophoneManager*</span><span class="sxs-lookup"><span data-stu-id="3d8fc-404">Chapter 6 – Create the *MicrophoneManager* class</span></span>

<span data-ttu-id="3d8fc-405">La segunda clase que va a crear es *MicrophoneManager*.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-405">The second class you are going to create is the *MicrophoneManager*.</span></span>

<span data-ttu-id="3d8fc-406">Esta clase es responsable de:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-406">This class is responsible for:</span></span>

- <span data-ttu-id="3d8fc-407">Detección del dispositivo de grabación conectado a los auriculares o al equipo (el valor predeterminado).</span><span class="sxs-lookup"><span data-stu-id="3d8fc-407">Detecting the recording device attached to the headset or machine (whichever is the default).</span></span>
- <span data-ttu-id="3d8fc-408">Capture el audio (voz) y use el dictado para almacenarlo como una cadena.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-408">Capture the audio (voice) and use dictation to store it as a string.</span></span>
- <span data-ttu-id="3d8fc-409">Una vez que se haya pausado la voz, envíe el dictado a la clase Translator.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-409">Once the voice has paused, submit the dictation to the Translator class.</span></span>
- <span data-ttu-id="3d8fc-410">Hospede un método que pueda detener la captura de voz si lo desea.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-410">Host a method that can stop the voice capture if desired.</span></span>

<span data-ttu-id="3d8fc-411">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-411">To create this class:</span></span> 
1.  <span data-ttu-id="3d8fc-412">Haga doble clic en  la carpeta scripts para abrirla.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-412">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="3d8fc-413">Haga clic con el botón  derecho en la carpeta scripts y haga clic en **crear > C# script**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="3d8fc-414">Asigne al script el nombre *MicrophoneManager*.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-414">Name the script *MicrophoneManager*.</span></span> 
3.  <span data-ttu-id="3d8fc-415">Haga doble clic en el nuevo script para abrirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-415">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="3d8fc-416">Actualice los espacios de nombres para que sean los mismos que los que se indican a continuación, en la parte superior de la clase *MicrophoneManager* :</span><span class="sxs-lookup"><span data-stu-id="3d8fc-416">Update the namespaces to be the same as the following, at the top of the *MicrophoneManager* class:</span></span>

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="3d8fc-417">A continuación, agregue las siguientes variables dentro de la clase *MicrophoneManager* :</span><span class="sxs-lookup"><span data-stu-id="3d8fc-417">Then, add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  <span data-ttu-id="3d8fc-418">Ahora es necesario agregar el código para los métodos *activo ()* e *Inicio ()* .</span><span class="sxs-lookup"><span data-stu-id="3d8fc-418">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="3d8fc-419">Se llamará cuando se inicialice la clase:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-419">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  <span data-ttu-id="3d8fc-420">Puede *eliminar* el método *Update ()* , ya que esta clase no lo usará.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-420">You can *delete* the *Update()* method since this class will not use it.</span></span>
8.  <span data-ttu-id="3d8fc-421">Ahora necesita los métodos que usa la aplicación para iniciar y detener la captura de voz y pasarlo a la clase *Translator* , que creará pronto.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-421">Now you need the methods that the App uses to start and stop the voice capture, and pass it to the *Translator* class, that you will build soon.</span></span> <span data-ttu-id="3d8fc-422">Copie el código siguiente y péguelo debajo del método *Start ()* .</span><span class="sxs-lookup"><span data-stu-id="3d8fc-422">Copy the following code and paste it beneath the *Start()* method.</span></span>

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > <span data-ttu-id="3d8fc-423">Aunque esta aplicación no hará uso de ella, el método *StopCapturingAudio ()* también se ha proporcionado aquí, si desea implementar la capacidad de detener la captura de audio en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-423">Though this application will not make use of it, the *StopCapturingAudio()* method has also been provided here, should you want to implement the ability to stop capturing audio in your application.</span></span>

9.  <span data-ttu-id="3d8fc-424">Ahora debe agregar un controlador de dictado que se invocará cuando se detenga la voz.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-424">You now need to add a Dictation Handler that will be invoked when the voice stops.</span></span> <span data-ttu-id="3d8fc-425">A continuación, este método pasará el texto dictado a la clase *Translator* .</span><span class="sxs-lookup"><span data-stu-id="3d8fc-425">This method will then pass the dictated text to the *Translator* class.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. <span data-ttu-id="3d8fc-426">Asegúrese de guardar los cambios en Visual Studio antes de volver a Unity.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-426">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

> [!WARNING]  
> <span data-ttu-id="3d8fc-427">En este punto, observará que aparece un error en el panel de la *consola del editor de Unity* ("el nombre ' Translator ' no existe...").</span><span class="sxs-lookup"><span data-stu-id="3d8fc-427">At this point you will notice an error appearing in the *Unity Editor Console* Panel (“The name ‘Translator’ does not exist...”).</span></span> <span data-ttu-id="3d8fc-428">Esto se debe a que el código hace referencia a la clase *Translator* , que creará en el siguiente capítulo.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-428">This is because the code references the *Translator* class, which you will create in the next chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-translator-service"></a><span data-ttu-id="3d8fc-429">Capítulo 7: llamada a Azure y a servicio de traductor</span><span class="sxs-lookup"><span data-stu-id="3d8fc-429">Chapter 7 – Call to Azure and translator service</span></span>

<span data-ttu-id="3d8fc-430">El último script que debe crear es la clase *Translator* .</span><span class="sxs-lookup"><span data-stu-id="3d8fc-430">The last script you need to create is the *Translator* class.</span></span> 

<span data-ttu-id="3d8fc-431">Esta clase es responsable de:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-431">This class is responsible for:</span></span>

-   <span data-ttu-id="3d8fc-432">Autenticación de la aplicación con *Azure*, en Exchange para un **token de autenticación**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-432">Authenticating the App with *Azure*, in exchange for an **Auth Token**.</span></span>
-   <span data-ttu-id="3d8fc-433">Use el **token de autenticación** para enviar el texto (recibido de la clase *MicrophoneManager* ) para su traducción.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-433">Use the **Auth Token** to submit text (received from the *MicrophoneManager* Class) to be translated.</span></span>
-   <span data-ttu-id="3d8fc-434">Reciba el resultado traducido y páselo a la clase de *resultados* que se visualizará en la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-434">Receive the translated result and pass it to the *Results* Class to be visualized in the UI.</span></span>

<span data-ttu-id="3d8fc-435">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-435">To create this Class:</span></span> 
1.  <span data-ttu-id="3d8fc-436">Vaya a la  carpeta scripts que creó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-436">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="3d8fc-437">Haga clic con el botón derecho en el **panel Proyecto**, **cree > C# script**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-437">Right-click in the **Project Panel**, **Create > C# Script**.</span></span> <span data-ttu-id="3d8fc-438">Llame al *traductor*de scripts.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-438">Call the script *Translator*.</span></span>
3.  <span data-ttu-id="3d8fc-439">Haga doble clic en el nuevo script de *traductor* para abrirlo **con Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-439">Double click on the new *Translator* script to open it **with Visual Studio**.</span></span>
4.  <span data-ttu-id="3d8fc-440">Agregue los siguientes espacios de nombres al principio del archivo:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-440">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="3d8fc-441">A continuación, agregue las siguientes variables dentro de la clase *Translator* :</span><span class="sxs-lookup"><span data-stu-id="3d8fc-441">Then add the following variables inside the *Translator* class:</span></span>

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - <span data-ttu-id="3d8fc-442">Los lenguajes insertados en  la enumeración de lenguajes son solo ejemplos.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-442">The languages inserted into the languages **enum** are just examples.</span></span> <span data-ttu-id="3d8fc-443">No dude en agregar más si lo desea; la [API admite más de 60 idiomas](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (incluido Klingon).</span><span class="sxs-lookup"><span data-stu-id="3d8fc-443">Feel free to add more if you wish; the [API supports over 60 languages](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (including Klingon)!</span></span>
    > - <span data-ttu-id="3d8fc-444">Hay una [página más interactiva que cubre los idiomas disponibles](https://www.microsoft.com/translator/business/languages/), aunque tenga en cuenta que la página solo parece funcionar cuando el idioma del sitio se establece en "en-US" (y el sitio de Microsoft probablemente redirigirá a su idioma nativo).</span><span class="sxs-lookup"><span data-stu-id="3d8fc-444">There is a [more interactive page covering available languages](https://www.microsoft.com/translator/business/languages/), though be aware the page only appears to work when the site language is set to 'en-us' (and the Microsoft site will likely redirect to your native language).</span></span> <span data-ttu-id="3d8fc-445">Puede cambiar el idioma del sitio en la parte inferior de la página o mediante la modificación de la dirección URL.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-445">You can change site language at the bottom of the page or by altering the URL.</span></span>
    > - <span data-ttu-id="3d8fc-446">El valor **authorizationKey** , en el fragmento de código anterior, debe ser la **clave** que recibió al suscribirse a *Azure Translator Text API*.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-446">The **authorizationKey** value, in the above code snippet, must be the **Key**  you received when you subscribed to the *Azure Translator Text API*.</span></span> <span data-ttu-id="3d8fc-447">Esto se trató en el [capítulo 1](#chapter-1--the-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="3d8fc-447">This was covered in [Chapter 1](#chapter-1--the-azure-portal).</span></span>

6.  <span data-ttu-id="3d8fc-448">Ahora es necesario agregar el código para los métodos *activo ()* e *Inicio ()* .</span><span class="sxs-lookup"><span data-stu-id="3d8fc-448">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> 
7.  <span data-ttu-id="3d8fc-449">En este caso, el código realizará una llamada a *Azure* mediante la clave de autorización para obtener un *token*.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-449">In this case, the code will make a call to *Azure* using the authorization Key, to get a *Token*.</span></span>

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > <span data-ttu-id="3d8fc-450">El token expirará después de 10 minutos.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-450">The token will expire after 10 minutes.</span></span> <span data-ttu-id="3d8fc-451">En función del escenario de la aplicación, es posible que tenga que realizar la misma llamada de corutina varias veces.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-451">Depending on the scenario for your app, you might have to make the same coroutine call multiple times.</span></span>

8.  <span data-ttu-id="3d8fc-452">La corutina para obtener el token es la siguiente:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-452">The coroutine to obtain the Token is the following:</span></span>

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > <span data-ttu-id="3d8fc-453">Si edita el nombre del método IEnumerator **GetTokenCoroutine ()** , debe actualizar los valores de cadena de llamada *StartCoroutine* y *StopCoroutine* en el código anterior.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-453">If you edit the name of the IEnumerator method **GetTokenCoroutine()**, you need to update the *StartCoroutine* and *StopCoroutine* call string values in the above code.</span></span> <span data-ttu-id="3d8fc-454">[Según la documentación de Unity](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), para detener una *corutina*concreta, debe usar el método de valor de cadena.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-454">[As per Unity documentation](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), to Stop a specific *Coroutine*, you need to use the string value method.</span></span>

9.  <span data-ttu-id="3d8fc-455">A continuación, agregue la corutina (con un método de secuencia "support" justo debajo de ella) para obtener la traducción del texto que recibe la clase *MicrophoneManager* .</span><span class="sxs-lookup"><span data-stu-id="3d8fc-455">Next, add the coroutine (with a “support” stream method right below it) to obtain the translation of the text received by the *MicrophoneManager* class.</span></span> <span data-ttu-id="3d8fc-456">Este código crea una cadena de consulta para enviar a *Azure Translator Text API*y, a continuación, usa la clase UnityWebRequest de Unity interna para realizar una llamada "Get" al punto de conexión con la cadena de consulta.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-456">This code creates a query string to send to the *Azure Translator Text API*, and then uses the internal Unity UnityWebRequest class to make a ‘Get’ call to the endpoint with the query string.</span></span> <span data-ttu-id="3d8fc-457">A continuación, el resultado se usa para establecer la traducción en el objeto de resultados.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-457">The result is then used to set the translation in your Results object.</span></span> <span data-ttu-id="3d8fc-458">En el código siguiente se muestra la implementación:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-458">The code below shows the implementation:</span></span>

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. <span data-ttu-id="3d8fc-459">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-459">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--configure-the-unity-scene"></a><span data-ttu-id="3d8fc-460">Capítulo 8: configuración de la escena de Unity</span><span class="sxs-lookup"><span data-stu-id="3d8fc-460">Chapter 8 – Configure the Unity Scene</span></span>

1.  <span data-ttu-id="3d8fc-461">De nuevo en el editor de Unity, haga clic y arrastre la clase de *resultados* *desde* la carpeta **scripts** hasta el objeto de **cámara principal** en el *Panel jerarquía*.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-461">Back in the Unity Editor, click and drag the *Results* class *from* the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="3d8fc-462">Haga clic en la **cámara principal** y mire en el *panel del inspector*.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-462">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="3d8fc-463">Observará que, dentro del componente de *script* recién agregado, hay cuatro campos con valores vacíos.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-463">You will notice that within the newly added *Script* component, there are four fields with empty values.</span></span> <span data-ttu-id="3d8fc-464">Estas son las referencias de salida a las propiedades del código.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-464">These are the output references to the properties in the code.</span></span> 
3.  <span data-ttu-id="3d8fc-465">Arrastre los objetos de **texto** correspondientes desde el *Panel jerarquía* hasta las cuatro ranuras, tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-465">Drag the appropriate **Text** objects from the *Hierarchy Panel* to those four slots, as shown in the image below.</span></span>

    ![Actualice las referencias de destino con los valores especificados.](images/AzureLabs-Lab1-34.png)
  
4.  <span data-ttu-id="3d8fc-467">A continuación, haga clic y arrastre la clase *Translator* desde la carpeta **scripts** hasta el objeto **cámara principal** en el *Panel jerarquía*.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-467">Next, click and drag the *Translator* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
5.  <span data-ttu-id="3d8fc-468">A continuación, haga clic y arrastre la clase *MicrophoneManager* desde la carpeta **scripts** hasta el objeto **cámara principal** en el *Panel jerarquía*.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-468">Then, click and drag the *MicrophoneManager* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
6.  <span data-ttu-id="3d8fc-469">Por último, haga clic en la **cámara principal** y mire en el *panel del inspector*.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-469">Lastly, click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="3d8fc-470">Observará que en el script que ha arrastrado, hay dos cuadros desplegables que le permitirán establecer los idiomas.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-470">You will notice that in the script you dragged on, there are two drop down boxes that will allow you to set the languages.</span></span>
 
    ![Asegúrese de que se introducen los idiomas de traducción previstos.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a><span data-ttu-id="3d8fc-472">Capítulo 9: probar en realidad mixta</span><span class="sxs-lookup"><span data-stu-id="3d8fc-472">Chapter 9 – Test in mixed reality</span></span>

<span data-ttu-id="3d8fc-473">Llegados a este punto, debe probar que la escena se ha implementado correctamente.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-473">At this point you need to test that the Scene has been properly implemented.</span></span>

<span data-ttu-id="3d8fc-474">Asegúrate de lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-474">Ensure that:</span></span>

- <span data-ttu-id="3d8fc-475">Toda la configuración mencionada en el [capítulo 1](#chapter-1--the-azure-portal) se establece correctamente.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-475">All the settings mentioned in [Chapter 1](#chapter-1--the-azure-portal) are set correctly.</span></span> 
- <span data-ttu-id="3d8fc-476">Los scripts Results, *Translator*y *MicrophoneManager*se adjuntan al objeto de **cámara principal** .</span><span class="sxs-lookup"><span data-stu-id="3d8fc-476">The *Results*, *Translator*, and *MicrophoneManager*, scripts are attached to the **Main Camera** object.</span></span> 
- <span data-ttu-id="3d8fc-477">Ha colocado la **clave** de servicio de *Azure Translator Text API* dentro de la variable **AuthorizationKey** dentro del script de *traductor* .</span><span class="sxs-lookup"><span data-stu-id="3d8fc-477">You have placed your *Azure Translator Text API* Service **Key** within the **authorizationKey** variable within the *Translator* Script.</span></span>  
- <span data-ttu-id="3d8fc-478">Todos los campos del *panel Inspector de cámara principal* están asignados correctamente.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-478">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
- <span data-ttu-id="3d8fc-479">El micrófono funciona al ejecutar la escena (si no es así, compruebe que el micrófono conectado es el dispositivo *predeterminado* y que lo ha [configurado correctamente en Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span><span class="sxs-lookup"><span data-stu-id="3d8fc-479">Your microphone is working when running your scene (if not, check that your attached microphone is the *default* device, and that you have [set it up correctly within Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span></span>

<span data-ttu-id="3d8fc-480">Puede probar el casco envolvente presionando el botón **reproducir** en el editor de *Unity*.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-480">You can test the immersive headset by pressing the **Play** button in the *Unity Editor*.</span></span>
<span data-ttu-id="3d8fc-481">La aplicación debe estar funcionando a través de los auriculares que se agregan.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-481">The App should be functioning through the attached immersive headset.</span></span>

> [!WARNING]  
> <span data-ttu-id="3d8fc-482">Si ve un error en la consola de Unity sobre el cambio del dispositivo de audio predeterminado, es posible que la escena no funcione según lo previsto.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-482">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="3d8fc-483">Esto se debe a la forma en que el portal de realidad mixta trata los micrófonos integrados para los auriculares que los tienen.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-483">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="3d8fc-484">Si ve este error, simplemente detenga la escena e iníciela de nuevo y las cosas deberían funcionar según lo previsto.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-484">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a><span data-ttu-id="3d8fc-485">Capítulo 10: compilar la solución de UWP y transferir localmente en el equipo local</span><span class="sxs-lookup"><span data-stu-id="3d8fc-485">Chapter 10 – Build the UWP solution and sideload on local machine</span></span>

<span data-ttu-id="3d8fc-486">Ya se ha completado todo lo necesario para la sección Unity de este proyecto, por lo que es el momento de compilarla desde Unity.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-486">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="3d8fc-487">Vaya a **configuración de compilación**: **Configuración de compilación de > de archivos...**</span><span class="sxs-lookup"><span data-stu-id="3d8fc-487">Navigate to **Build Settings**: **File > Build Settings...**</span></span>
2.  <span data-ttu-id="3d8fc-488">En la ventana **configuración de compilación** , haga clic en compilar.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-488">From the **Build Settings** window, click **Build**.</span></span>

    ![Compile la escena de Unity.](images/AzureLabs-Lab1-36.png)
  
3.  <span data-ttu-id="3d8fc-490">Si aún no lo está, marque los **proyectos de Unity C#** .</span><span class="sxs-lookup"><span data-stu-id="3d8fc-490">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="3d8fc-491">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-491">Click **Build**.</span></span> <span data-ttu-id="3d8fc-492">Unity iniciará una ventana del *Explorador de archivos* , donde tendrá que crear y seleccionar una carpeta en la que compilar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-492">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="3d8fc-493">Cree esa carpeta ahora y asígnele el nombre *App*.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-493">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="3d8fc-494">Después, con la carpeta de la *aplicación* seleccionada, presione **Seleccionar carpeta**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-494">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="3d8fc-495">Unity comenzará a compilar el proyecto en la carpeta de la *aplicación* .</span><span class="sxs-lookup"><span data-stu-id="3d8fc-495">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="3d8fc-496">Una vez que Unity termine de compilar (puede tardar algún tiempo), se abrirá una ventana del *Explorador de archivos* en la ubicación de la compilación (Compruebe la barra de tareas, ya que es posible que no aparezca siempre por encima de las ventanas, pero le notificará la adición de una nueva ventana).</span><span class="sxs-lookup"><span data-stu-id="3d8fc-496">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11--deploy-your-application"></a><span data-ttu-id="3d8fc-497">Capítulo 11: implementación de la aplicación</span><span class="sxs-lookup"><span data-stu-id="3d8fc-497">Chapter 11 – Deploy your application</span></span>

<span data-ttu-id="3d8fc-498">Para implementar la aplicación:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-498">To deploy your application:</span></span>

1.  <span data-ttu-id="3d8fc-499">Vaya a la nueva compilación de Unity (la carpeta de la *aplicación* ) y abra el archivo de solución con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-499">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
2.  <span data-ttu-id="3d8fc-500">En la configuración de soluciones , seleccione Depurar.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-500">In the Solution Configuration select **Debug**.</span></span>
3.  <span data-ttu-id="3d8fc-501">En la plataforma de la solución, seleccione **x86**, **equipo local**.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-501">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="3d8fc-502">En el caso de Microsoft HoloLens, es posible que le resulte más fácil establecer esto en el *equipo remoto*, de modo que no esté anclado al equipo.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-502">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="3d8fc-503">Sin embargo, también tendrá que hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="3d8fc-503">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="3d8fc-504">Conozca la **dirección IP** de HoloLens, que puede encontrarse en la *configuración > red & Internet > Wi-Fi > Opciones avanzadas*; IPv4 es la dirección que debe usar.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-504">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="3d8fc-505">Asegurarse de que el *modo de desarrollador* está **activado**; se encuentra en *configuración > actualizar & > de seguridad para desarrolladores*.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-505">Ensure *Developer Mode* is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Implemente la solución desde Visual Studio.](images/AzureLabs-Lab1-37.png)
    
 
4.  <span data-ttu-id="3d8fc-507">Vaya al **menú** compilar y haga clic en **implementar solución** para transferir localmente la aplicación a su equipo.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-507">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>
5.  <span data-ttu-id="3d8fc-508">La aplicación debe aparecer ahora en la lista de aplicaciones instaladas, lista para iniciarse.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-508">Your App should now appear in the list of installed apps, ready to be launched.</span></span>
6.  <span data-ttu-id="3d8fc-509">Una vez iniciado, la aplicación le pedirá que autorice el acceso al micrófono.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-509">Once launched, the App will prompt you to authorize access to the Microphone.</span></span> <span data-ttu-id="3d8fc-510">Asegúrese de hacer clic en el botón **sí** .</span><span class="sxs-lookup"><span data-stu-id="3d8fc-510">Make sure to click the **YES** button.</span></span>
7.  <span data-ttu-id="3d8fc-511">Ya está listo para empezar a traducir.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-511">You are now ready to start translating!</span></span>

## <a name="your-finished-translation-text-api-application"></a><span data-ttu-id="3d8fc-512">Su aplicación de API de texto de traducción finalizada</span><span class="sxs-lookup"><span data-stu-id="3d8fc-512">Your finished Translation Text API application</span></span>

<span data-ttu-id="3d8fc-513">Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha la API de texto de traducción de Azure para convertir voz en texto traducido.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-513">Congratulations, you built a mixed reality app that leverages the Azure Translation Text API to convert speech to translated text.</span></span>

![Producto final.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="3d8fc-515">Ejercicios de bonus</span><span class="sxs-lookup"><span data-stu-id="3d8fc-515">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="3d8fc-516">Ejercicio 1</span><span class="sxs-lookup"><span data-stu-id="3d8fc-516">Exercise 1</span></span>

<span data-ttu-id="3d8fc-517">¿Se puede Agregar funcionalidad de texto a voz a la aplicación para que se diga el texto devuelto?</span><span class="sxs-lookup"><span data-stu-id="3d8fc-517">Can you add text-to-speech functionality to the app, so that the returned text is spoken?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="3d8fc-518">Ejercicio 2</span><span class="sxs-lookup"><span data-stu-id="3d8fc-518">Exercise 2</span></span>

<span data-ttu-id="3d8fc-519">Permite que el usuario cambie los idiomas de origen y de salida ("de" y "a") dentro de la propia aplicación, por lo que no es necesario recompilar la aplicación cada vez que desee cambiar los idiomas.</span><span class="sxs-lookup"><span data-stu-id="3d8fc-519">Make it possible for the user to change the source and output languages ('from' and 'to') within the app itself, so the app does not need to be rebuilt every time you want to change languages.</span></span>
