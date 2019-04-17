---
title: El Sr. y Azure 301 - traducción de idiomas
description: Realice este curso para obtener información sobre cómo implementar Azure Translator Text API dentro de una aplicación de realidad mixta.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: realidad mixta, Azure, academy, unity, tutorial, api, texto de traductor, hololens, envolventes, vr
ms.openlocfilehash: 6fe31d1bcb72337f0a3e8664893ea0f7c0540aae
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605455"
---
>[!NOTE]
><span data-ttu-id="9ecc4-104">Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-104">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="9ecc4-105">Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-105">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="9ecc4-106">Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-106">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="9ecc4-107">Se mantendrán para seguir trabajando en los dispositivos compatibles.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-107">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="9ecc4-108">Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-108">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="9ecc4-109">Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-109">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

# <a name="mr-and-azure-301-language-translation"></a><span data-ttu-id="9ecc4-110">El Sr. y Azure 301: Traducción de idiomas</span><span class="sxs-lookup"><span data-stu-id="9ecc4-110">MR and Azure 301: Language translation</span></span>

<span data-ttu-id="9ecc4-111">En este curso, obtendrá información sobre cómo agregar capacidades de traducción a una aplicación de realidad mixta con Azure Cognitive Services, con Translator Text API.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-111">In this course, you will learn how to add translation capabilities to a mixed reality application using Azure Cognitive Services, with the Translator Text API.</span></span>

![Final producto](images/AzureLabs-Lab1-00.png)

<span data-ttu-id="9ecc4-113">Translator Text API es una servicio que funciona en casi en tiempo real de traducción.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-113">The Translator Text API is a translation Service which works in near real-time.</span></span> <span data-ttu-id="9ecc4-114">El servicio está en la nube y, mediante una llamada de API de REST, una aplicación puede hacer uso de la tecnología de traducción automática neuronal para traducir texto en otro lenguaje.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-114">The Service is cloud-based, and, using a REST API call, an app can make use of the neural machine translation technology to translate text to another language.</span></span> <span data-ttu-id="9ecc4-115">Para obtener más información, visite la [página Azure Translator Text API](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span><span class="sxs-lookup"><span data-stu-id="9ecc4-115">For more information, visit the [Azure Translator Text API page](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span></span>

<span data-ttu-id="9ecc4-116">Tras la finalización de este curso, tendrá una aplicación de realidad mixta que podrá hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-116">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1.  <span data-ttu-id="9ecc4-117">El usuario se hable un micrófono conectado a un auricular (VR) envolvente (o el micrófono integrado de HoloLens).</span><span class="sxs-lookup"><span data-stu-id="9ecc4-117">The user will speak into a microphone connected to an immersive (VR) headset (or the built-in microphone of HoloLens).</span></span>
2.  <span data-ttu-id="9ecc4-118">La aplicación capturará el dictado y enviarla a Translator Text API de Azure.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-118">The app will capture the dictation and send it to the Azure Translator Text API.</span></span>
3.  <span data-ttu-id="9ecc4-119">El resultado de la traducción se mostrará en un grupo de interfaz de usuario simple en la escena de Unity.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-119">The translation result will be displayed in a simple UI group in the Unity Scene.</span></span>

<span data-ttu-id="9ecc4-120">Este curso le mostrará cómo obtener los resultados desde el servicio del traductor en una aplicación de ejemplo basada en Unity.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-120">This course will teach you how to get the results from the Translator Service into a Unity-based sample application.</span></span> <span data-ttu-id="9ecc4-121">Será quien decide estos conceptos se aplican a una aplicación personalizada puede que esté creando.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-121">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="9ecc4-122">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="9ecc4-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="9ecc4-123">Curso</span><span class="sxs-lookup"><span data-stu-id="9ecc4-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="9ecc4-124"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="9ecc4-124"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="9ecc4-125"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="9ecc4-125"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="9ecc4-126">El Sr. y Azure 301: Traducción de idiomas</span><span class="sxs-lookup"><span data-stu-id="9ecc4-126">MR and Azure 301: Language translation</span></span></td><td style="text-align: center;"> <span data-ttu-id="9ecc4-127">✔️</span><span class="sxs-lookup"><span data-stu-id="9ecc4-127">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="9ecc4-128">✔️</span><span class="sxs-lookup"><span data-stu-id="9ecc4-128">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="9ecc4-129">Aunque este curso se centra principalmente en inmersivos (VR) Windows Mixed Reality, también puede aplicar lo aprendido en este curso de Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-129">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="9ecc4-130">Como seguir el curso, verá notas en cualquier cambio que deberá emplear para admitir HoloLens.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-130">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="9ecc4-131">Al usar HoloLens, es posible que observe algunos eco durante la captura de voz.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-131">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9ecc4-132">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="9ecc4-132">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="9ecc4-133">Este tutorial está diseñado para los desarrolladores con experiencia básica con Unity y C#.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-133">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="9ecc4-134">También Ten en cuenta que los requisitos previos y las instrucciones escritas en este documento representan lo que se ha probado y comprobado en el momento de redactar (mayo de 2018).</span><span class="sxs-lookup"><span data-stu-id="9ecc4-134">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="9ecc4-135">Es libre de usar el software más reciente, como se muestra en el [instalar las herramientas de](install-the-tools.md) artículo, aunque no se debe suponer que la información de este curso perfectamente coincida con lo que encontrará en el software más reciente que se indica a continuación .</span><span class="sxs-lookup"><span data-stu-id="9ecc4-135">You are free to use the latest software, as listed within the [install the tools](install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="9ecc4-136">Se recomiendan el siguiente hardware y software para este curso:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-136">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="9ecc4-137">Un equipo de desarrollo, [compatible con Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desarrollo de auriculares envolvente (VR)</span><span class="sxs-lookup"><span data-stu-id="9ecc4-137">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="9ecc4-138">Windows 10 Fall Creators Update (o posterior) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="9ecc4-138">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="9ecc4-139">El SDK más reciente de Windows 10</span><span class="sxs-lookup"><span data-stu-id="9ecc4-139">The latest Windows 10 SDK</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="9ecc4-140">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="9ecc4-140">Unity 2017.4</span></span>](install-the-tools.md#installation-checklist)
- [<span data-ttu-id="9ecc4-141">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="9ecc4-141">Visual Studio 2017</span></span>](install-the-tools.md#installation-checklist)
- <span data-ttu-id="9ecc4-142">Un [auriculares de Windows Mixed Reality envolventes (VR)](immersive-headset-hardware-details.md) o [Microsoft HoloLens](hololens-hardware-details.md) con el modo de desarrollador habilitado</span><span class="sxs-lookup"><span data-stu-id="9ecc4-142">A [Windows Mixed Reality immersive (VR) headset](immersive-headset-hardware-details.md) or [Microsoft HoloLens](hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="9ecc4-143">Un conjunto de auriculares con micrófono integrado (si no tienen los auriculares altavoces y un micrófono integrado)</span><span class="sxs-lookup"><span data-stu-id="9ecc4-143">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="9ecc4-144">Acceso a Internet para el programa de instalación y traducción de la recuperación de Azure</span><span class="sxs-lookup"><span data-stu-id="9ecc4-144">Internet access for Azure setup and translation retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="9ecc4-145">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="9ecc4-145">Before you start</span></span>

- <span data-ttu-id="9ecc4-146">Para evitar problemas de creación de este proyecto, se recomienda encarecidamente que cree el proyecto se ha mencionado en este tutorial en una carpeta raíz o cerca de la raíz (rutas de acceso de carpeta largo pueden causar problemas en tiempo de compilación).</span><span class="sxs-lookup"><span data-stu-id="9ecc4-146">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="9ecc4-147">El código de este tutorial, podrá grabar desde el dispositivo de micrófono predeterminado conectado a su PC.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-147">The code in this tutorial will allow you to record from the default microphone device connected to your PC.</span></span> <span data-ttu-id="9ecc4-148">Asegúrese de que el dispositivo de micrófono predeterminado se establece en el dispositivo que se va a usar para capturar la voz.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-148">Make sure the default microphone device is set to the device you plan to use to capture your voice.</span></span>
- <span data-ttu-id="9ecc4-149">Para permitir que su equipo habilitar el dictado, vaya a **configuración > privacidad > voz de tinta & escribir** y seleccione el botón **activar servicios de voz y escritura sugerencias**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-149">To allow your PC to enable dictation, go to **Settings > Privacy > Speech, inking & typing** and select the button **Turn On speech services and typing suggestions**.</span></span>
- <span data-ttu-id="9ecc4-150">Si usas un micrófono y auriculares conectados a (o está integrada en) los auriculares, asegúrese de que la opción "Cuando wear mi auriculares, vaya a auriculares con micrófono" está activada en **configuración > la realidad mixta > Audio y voz**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-150">If you're using a microphone and headphones connected to (or built-in to) your headset, make sure the option “When I wear my headset, switch to headset mic” is turned on in **Settings > Mixed reality > Audio and speech**.</span></span>

   ![Configuración de la realidad mixta](images/AzureLabs-Lab1-00-5.png)

   ![Configuración del micrófono](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> <span data-ttu-id="9ecc4-153">Tenga en cuenta que si está desarrollando para un auricular envolvente para este laboratorio, puede experimentar problemas de dispositivo de salida de audio.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-153">Be aware that if you are developing for an immersive headset for this lab, you may experience audio output device issues.</span></span> <span data-ttu-id="9ecc4-154">Esto es debido a un problema con Unity, que se ha corregido en versiones posteriores de Unity (Unity 2018.2).</span><span class="sxs-lookup"><span data-stu-id="9ecc4-154">This is due to an issue with Unity, which is fixed in later versions of Unity (Unity 2018.2).</span></span> <span data-ttu-id="9ecc4-155">El problema impide que Unity cambie el dispositivo de salida de audio predeterminado en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-155">The issue prevents Unity from changing the default audio output device at run time.</span></span> <span data-ttu-id="9ecc4-156">Como solución alternativa, asegúrese de que haber completado los pasos anteriores y cierre y vuelva a abrir el Editor, cuando se presenta este problema.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-156">As a work around, ensure you have completed the above steps, and close and re-open the Editor, when this issue presents itself.</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="9ecc4-157">Capítulo 1: el Portal de Azure</span><span class="sxs-lookup"><span data-stu-id="9ecc4-157">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="9ecc4-158">Para usar la API del traductor de Azure, deberá configurar una instancia del servicio esté disponible para su aplicación.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-158">To use the Azure Translator API, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="9ecc4-159">Inicie sesión en el [Portal Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="9ecc4-159">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="9ecc4-160">Si no dispone de una cuenta de Azure, deberá crear uno.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="9ecc4-161">Si está siguiendo este tutorial en una situación de aula o laboratorio, pida el instructor o uno de los a los supervisores de ayuda para instalar la nueva cuenta.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="9ecc4-162">Una vez que haya iniciado sesión, haga clic en **New** en la parte superior izquierda esquina y busque "Translator Text API".</span><span class="sxs-lookup"><span data-stu-id="9ecc4-162">Once you are logged in, click on **New** in the top left corner and search for "Translator Text API."</span></span> <span data-ttu-id="9ecc4-163">Seleccione **escriba**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-163">Select **Enter**.</span></span>

    ![Nuevo recurso](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > <span data-ttu-id="9ecc4-165">La palabra **New** se han reemplazado con **crear un recurso**, en los portales más reciente.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-165">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="9ecc4-166">La nueva página proporcionará una descripción de la *Translator Text API* Service.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-166">The new page will provide a description of the *Translator Text API* Service.</span></span> <span data-ttu-id="9ecc4-167">En la parte inferior izquierda de esta página, seleccione el **crear** botón para crear una asociación con este servicio.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-167">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Crear servicio de API de texto de traductor](images/AzureLabs-Lab1-03.png)

4.  <span data-ttu-id="9ecc4-169">Una vez que ha hecho clic **crear**:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-169">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="9ecc4-170">Insertar el elemento **nombre** para esta instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-170">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="9ecc4-171">Seleccione un **suscripción**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-171">Select an appropriate **Subscription**.</span></span>
    3. <span data-ttu-id="9ecc4-172">Seleccione el **tarifa** adecuado para usted, si ésta es la primera tiempo creando una *Translator Text Service*, un nivel gratuito (denominado F0) debe estar disponible para usted.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-172">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Translator Text Service*, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="9ecc4-173">Elija un **grupo de recursos** o cree uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="9ecc4-174">Un grupo de recursos proporciona una manera de supervisar, controlar el acceso, aprovisionar y administrar la facturación para una colección de recursos de Azure.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="9ecc4-175">Se recomienda que todos los servicios de Azure asociados con un solo proyecto (por ejemplo, por ejemplo, estos laboratorios) en un grupo de recursos comunes).</span><span class="sxs-lookup"><span data-stu-id="9ecc4-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="9ecc4-176">Si desea leer más acerca de los grupos de recursos de Azure, inicie [visite el artículo del grupo de recursos](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="9ecc4-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="9ecc4-177">Determinar la **ubicación** para el grupo de recursos (si está creando un nuevo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="9ecc4-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="9ecc4-178">La ubicación sería lo ideal es que en la región donde desea ejecutar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="9ecc4-179">Algunos recursos de Azure solo están disponibles en determinadas regiones.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="9ecc4-180">También deberá confirmar que ha comprendido los términos y condiciones que se aplican a este servicio.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="9ecc4-181">Selecciona **Crear**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-181">Select **Create**.</span></span>

        ![Seleccione el botón Crear.](images/AzureLabs-Lab1-04.png)

5.  <span data-ttu-id="9ecc4-183">Una vez que ha hecho clic **crear**, tendrá que esperar para que se puede crear el servicio, esta operación puede tardar un minuto.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-183">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="9ecc4-184">Una vez creada la instancia de servicio, aparecerá una notificación en el portal.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-184">A notification will appear in the portal once the Service instance is created.</span></span> 

    ![Notificación de creación de servicio de Azure](images/AzureLabs-Lab1-05.png)

7.  <span data-ttu-id="9ecc4-186">Haga clic en la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-186">Click on the notification to explore your new Service instance.</span></span> 

    ![Vaya al menú emergente de recursos.](images/AzureLabs-Lab1-06.png)

8.  <span data-ttu-id="9ecc4-188">Haga clic en el **ir al recurso** botón en la notificación para explorar la nueva instancia de servicio.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="9ecc4-189">Se le llevará a la nueva instancia de servicio de API de texto de traductor.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-189">You will be taken to your new Translator Text API Service instance.</span></span> 

    ![Página de servicio de API de texto de traductor](images/AzureLabs-Lab1-07.png)

9.  <span data-ttu-id="9ecc4-191">En este tutorial, la aplicación necesitará realizar llamadas al servicio, que se realiza a través del uso clave del servicio en la de suscripción.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-191">Within this tutorial, your application will need to make calls to your Service, which is done through using your Service’s Subscription Key.</span></span> 
10. <span data-ttu-id="9ecc4-192">Desde el *inicio rápido* página de su *Translator Text* Service, navegue hasta el primer paso, *obtener las claves*y haga clic en **claves** (puede También lograr esto, haga clic en el hipervínculo azul claves, ubicado en el menú de navegación de servicios, indicado por el icono de llave).</span><span class="sxs-lookup"><span data-stu-id="9ecc4-192">From the *Quick start* page of your *Translator Text* Service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the Services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="9ecc4-193">Esto revelará su servicio *claves*.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-193">This will reveal your Service *Keys*.</span></span>
11. <span data-ttu-id="9ecc4-194">Realice una copia de una de las claves de muestra, ya que lo necesitará más adelante en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="9ecc4-195">Capítulo 2: configurar el proyecto de Unity</span><span class="sxs-lookup"><span data-stu-id="9ecc4-195">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="9ecc4-196">Configurar y probar los auriculares de realidad mixta envolventes.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-196">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="9ecc4-197">En este curso, no necesitará controladores de movimiento.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-197">You will not need motion controllers for this course.</span></span> <span data-ttu-id="9ecc4-198">Si necesita admite la configuración de un auricular envolvente, [siga estos pasos](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span><span class="sxs-lookup"><span data-stu-id="9ecc4-198">If you need support setting up an immersive headset, please [follow these steps](https://support.microsoft.com/en-au/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

<span data-ttu-id="9ecc4-199">El siguiente es un conjunto típico de para el desarrollo con la realidad mixta y, por lo tanto, es una buena plantilla para otros proyectos:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-199">The following is a typical set up for developing with mixed reality and, as such, is a good template for other projects:</span></span>

1.  <span data-ttu-id="9ecc4-200">Abra *Unity* y haga clic en **New**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-200">Open *Unity* and click **New**.</span></span> 

    ![Inicie el nuevo proyecto de Unity.](images/AzureLabs-Lab1-08.png)

2.  <span data-ttu-id="9ecc4-202">Ahora deberá proporcionar un nombre de proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="9ecc4-203">Insertar **MR_Translation**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-203">Insert **MR_Translation**.</span></span> <span data-ttu-id="9ecc4-204">Asegúrese de que el tipo de proyecto se establece en **3D**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="9ecc4-205">Establecer el *ubicación* a algún lugar adecuado para usted (Recuerde, es mejor cuanto más se acerque a los directorios raíz).</span><span class="sxs-lookup"><span data-stu-id="9ecc4-205">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="9ecc4-206">A continuación, haga clic en **crear un proyecto**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-206">Then, click **Create project**.</span></span>

    ![Se proporcionan detalles para el nuevo proyecto de Unity.](images/AzureLabs-Lab1-09.png)

3.  <span data-ttu-id="9ecc4-208">Con Unity abierto, es conveniente comprobar el valor predeterminado **Script Editor** está establecido en **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="9ecc4-209">Vaya a **Editar > Preferencias** y, a continuación, en la ventana nueva, vaya a **herramientas externas**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="9ecc4-210">Cambio **External Script Editor** a **de Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="9ecc4-211">Cerrar la **preferencias** ventana.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-211">Close the **Preferences** window.</span></span>

    ![Actualizar las preferencias del editor de secuencia de comandos.](images/AzureLabs-Lab1-10.png)

4.  <span data-ttu-id="9ecc4-213">A continuación, vaya a **archivo > configuración de compilación** y cambiar la plataforma a **Universal Windows Platform**, haciendo clic en el **Cambiar plataforma** botón.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-213">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Crear ventana de configuración de la plataforma del conmutador para UWP.](images/AzureLabs-Lab1-11.png)

5.  <span data-ttu-id="9ecc4-215">Vaya a **archivo > configuración de compilación** y asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-215">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="9ecc4-216">**Dispositivo de destino** está establecido en **cualquier dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-216">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="9ecc4-217">Para Microsoft HoloLens, establezca **dispositivo de destino** a *HoloLens*.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-217">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="9ecc4-218">**Tipo de compilación** está establecido en **D3D**</span><span class="sxs-lookup"><span data-stu-id="9ecc4-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="9ecc4-219">**SDK** está establecido en **instalada más reciente**</span><span class="sxs-lookup"><span data-stu-id="9ecc4-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="9ecc4-220">**Versión de Visual Studio** está establecido en **instalada más reciente**</span><span class="sxs-lookup"><span data-stu-id="9ecc4-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="9ecc4-221">**Compilar y ejecutar** está establecido en **máquina Local**</span><span class="sxs-lookup"><span data-stu-id="9ecc4-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="9ecc4-222">Guarde la escena y agregarlo a la compilación.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="9ecc4-223">Hacer esto seleccionando **agregar escenas abierto**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="9ecc4-224">Aparecerá el guardado de la ventana.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-224">A save window will appear.</span></span>

            ![Haga clic en Agregar botón de escenas abierto](images/AzureLabs-Lab1-12.png)

        2. <span data-ttu-id="9ecc4-226">Cree una nueva carpeta de esto y cualquier futuro, escena, a continuación, seleccione el **nueva carpeta** botón para crear una nueva carpeta y asígnele el nombre **escenas**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Crear nueva carpeta de scripts](images/AzureLabs-Lab1-13.png)

        3. <span data-ttu-id="9ecc4-228">Abra el recién creado **escenas** carpeta y, a continuación, en el *nombre de archivo*: campo de texto, escriba **MR_TranslationScene**, a continuación, presione **guardar**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_TranslationScene**, then press **Save**.</span></span>

            ![Asigne un nombre de nueva escena.](images/AzureLabs-Lab1-14.png)

            > <span data-ttu-id="9ecc4-230">Tenga en cuenta, debe guardar sus escenas de Unity dentro de la *activos* carpeta, ya que deben estar asociados al proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="9ecc4-231">Creación de la carpeta de segundo plano (y otras carpetas similares) es una forma habitual de estructurar un proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="9ecc4-232">El resto de la configuración, en *configuración de compilación*, debe dejarse como predeterminada por ahora.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="9ecc4-233">En el *configuración de compilación* ventana, haga clic en el **configuración del Reproductor** botón, se abrirá el panel relacionado en el espacio donde el *Inspector* se encuentra.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Abra Configuración del Reproductor.](images/AzureLabs-Lab1-15.png)

7. <span data-ttu-id="9ecc4-235">En este panel, es necesario comprobar algunas opciones de configuración:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="9ecc4-236">En el **otra configuración** pestaña:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="9ecc4-237">**Versión en tiempo de ejecución de secuencias de comandos** debe ser **estable** (.NET 3.5 equivalente).</span><span class="sxs-lookup"><span data-stu-id="9ecc4-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="9ecc4-238">**Scripting de back-end** debe ser **.NET**</span><span class="sxs-lookup"><span data-stu-id="9ecc4-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="9ecc4-239">**Nivel de compatibilidad de API** debe ser **.NET 4.6**</span><span class="sxs-lookup"><span data-stu-id="9ecc4-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Actualizar la configuración de otros.](images/AzureLabs-Lab1-16.png)
      
    2. <span data-ttu-id="9ecc4-241">Dentro de la **configuración de publicación** ficha **capacidades**, consulte:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="9ecc4-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="9ecc4-242">**InternetClient**</span></span>
        2. <span data-ttu-id="9ecc4-243">**Micrófono**</span><span class="sxs-lookup"><span data-stu-id="9ecc4-243">**Microphone**</span></span>

            ![Actualizando la configuración de publicación.](images/AzureLabs-Lab1-17.png)

    3. <span data-ttu-id="9ecc4-245">Más abajo el panel, en **XR configuración** (bajo **configuración de publicación**), graduación **admite la realidad Virtual**, asegúrese de que el **SDK de Windows Mixed Reality**  se agrega.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Actualice la configuración de R de X.](images/AzureLabs-Lab1-18.png)

8.  <span data-ttu-id="9ecc4-247">En **configuración de compilación**, *Unity C# proyectos* ya no está atenuada; Marque la casilla situada junto a esto.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-247">Back in **Build Settings**, *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="9ecc4-248">Cierre la ventana de configuración de compilación.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="9ecc4-249">Guarde la escena y el proyecto (**archivo > Guardar ESCENA / archivo > Guardar proyecto**).</span><span class="sxs-lookup"><span data-stu-id="9ecc4-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="9ecc4-250">Capítulo 3: configuración de cámara principal</span><span class="sxs-lookup"><span data-stu-id="9ecc4-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9ecc4-251">Si desea omitir la *configurar Unity* componente de este curso y continuar directamente en código, no dude en [descargar este .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), importarlo en el proyecto como un [ *Paquete personalizado*](https://docs.unity3d.com/Manual/AssetPackages.html)y, a continuación, continuar desde [capítulo 5](#chapter-5--create-the-results-class).</span><span class="sxs-lookup"><span data-stu-id="9ecc4-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), import it into your project as a [*Custom Package*](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-results-class).</span></span> <span data-ttu-id="9ecc4-252">Deberá crear un proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-252">You will still need to create a Unity Project.</span></span>

1.  <span data-ttu-id="9ecc4-253">En el *jerarquía Panel*, encontrará un objeto denominado **cámara principal**, este objeto representa el punto de vista de "head" una vez que esté "dentro" de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-253">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your “head” point of view once you are “inside” your application.</span></span>
2.  <span data-ttu-id="9ecc4-254">Con el panel de Unity delante de usted, seleccione el **Main cámara GameObject**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-254">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="9ecc4-255">Observará que el *Panel Inspector* (generalmente se encuentra a la derecha, en el panel) mostrará los distintos componentes de la que *GameObject*, con *transformar* en la parte superior, seguido por *cámara*y algunos otros componentes.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-255">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="9ecc4-256">Deberá restablecer la transformación de la cámara principal, por lo que está colocado correctamente.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-256">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>
3.  <span data-ttu-id="9ecc4-257">Para ello, seleccione el **engranaje** icono situado junto a la cámara *transformar* componente y seleccione **restablecer**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-257">To do this, select the **Gear** icon next to the Camera’s *Transform* component, and selecting **Reset**.</span></span> 

    ![Restablecer la transformación de la cámara principal.](images/AzureLabs-Lab1-19.png)
 
4.  <span data-ttu-id="9ecc4-259">El *transformar* componente debería entonces el aspecto siguiente:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-259">The *Transform* component should then look like:</span></span>

    1. <span data-ttu-id="9ecc4-260">El *posición* está establecido en **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="9ecc4-260">The *Position* is set to **0, 0, 0**</span></span>
    2. <span data-ttu-id="9ecc4-261">*Rotación* está establecido en **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="9ecc4-261">*Rotation* is set to **0, 0, 0**</span></span>
    3. <span data-ttu-id="9ecc4-262">Y *escala* está establecido en **1, 1, 1**</span><span class="sxs-lookup"><span data-stu-id="9ecc4-262">And *Scale* is set to **1, 1, 1**</span></span>

        ![Transformar la información de la cámara](images/AzureLabs-Lab1-20.png)

5.  <span data-ttu-id="9ecc4-264">A continuación, con el **cámara principal** seleccionado de objetos, consulte el **Agregar componente** situado en la parte inferior de la *Panel Inspector*.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-264">Next, with the **Main Camera** object selected, see the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span> 
6.  <span data-ttu-id="9ecc4-265">Seleccionar ese botón y buscar (escribiendo *origen Audio* en el campo de búsqueda o desplazarse por las secciones) para el componente denominado **origen Audio** tal como se muestra a continuación y selecciónelo (presione ENTRAR en ella También funciona).</span><span class="sxs-lookup"><span data-stu-id="9ecc4-265">Select that button, and search (by either typing *Audio Source* into the search field or navigating the sections) for the component called **Audio Source** as shown below and select it (pressing enter on it also works).</span></span>
7.  <span data-ttu-id="9ecc4-266">Un *origen Audio* componente se agregará a la **cámara principal**, tal y como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-266">An *Audio Source* component will be added to the **Main Camera**, as demonstrated below.</span></span>

    ![Agregar un componente de origen de Audio.](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > <span data-ttu-id="9ecc4-268">Para Microsoft HoloLens, deberá cambiar también los siguientes valores, que forman parte de la **cámara** componente en su **cámara principal**:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-268">For Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component on your **Main Camera**:</span></span>
    > - <span data-ttu-id="9ecc4-269">**Borrar las marcas de:** Color sólido.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-269">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="9ecc4-270">**En segundo plano** ' negro, alfa 0': código de color hexadecimal: #00000000.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-270">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

## <a name="chapter-4--setup-debug-canvas"></a><span data-ttu-id="9ecc4-271">Capítulo 4: lienzo de depuración del programa de instalación</span><span class="sxs-lookup"><span data-stu-id="9ecc4-271">Chapter 4 – Setup Debug Canvas</span></span>

<span data-ttu-id="9ecc4-272">Para mostrar la entrada y salida de la traducción, se debe crear una interfaz de usuario básica.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-272">To show the input and output of the translation, a basic UI needs to be created.</span></span> <span data-ttu-id="9ecc4-273">En este curso, creará un objeto de interfaz de usuario de Canvas, con varios objetos 'Texto' para mostrar los datos.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-273">For this course, you will create a Canvas UI object, with several ‘Text’ objects to show the data.</span></span>

1.  <span data-ttu-id="9ecc4-274">Haga clic en un área vacía de la *jerarquía Panel*, en **UI**, agregar un **lienzo**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-274">Right-click in an empty area of the *Hierarchy Panel*, under **UI**, add a **Canvas**.</span></span>

    ![Agregue el nuevo objeto de interfaz de usuario de Canvas.](images/AzureLabs-Lab1-22.png)

2.  <span data-ttu-id="9ecc4-276">Con el objeto de lienzo seleccionado, en el *Panel Inspector* (en el componente "Lienzo"), cambiar **modo de representar** a **espacio universal**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-276">With the Canvas object selected, in the *Inspector Panel* (within the ‘Canvas’ component), change **Render Mode** to **World Space**.</span></span> 
3.  <span data-ttu-id="9ecc4-277">A continuación, cambie los parámetros siguientes en el *Rect transformación del Panel del Inspector*:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-277">Next, change the following parameters in the *Inspector Panel’s Rect Transform*:</span></span>

    1. <span data-ttu-id="9ecc4-278">*PDV* -  **X** 0 **Y** 0 **Z** 40</span><span class="sxs-lookup"><span data-stu-id="9ecc4-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span></span>
    2. <span data-ttu-id="9ecc4-279">*Width* -    500</span><span class="sxs-lookup"><span data-stu-id="9ecc4-279">*Width* -    500</span></span>
    3. <span data-ttu-id="9ecc4-280">*Alto* : 300</span><span class="sxs-lookup"><span data-stu-id="9ecc4-280">*Height* -   300</span></span>
    4. <span data-ttu-id="9ecc4-281">*Escala* - **X** 0.13 **Y** 0.13 **Z** 0.13</span><span class="sxs-lookup"><span data-stu-id="9ecc4-281">*Scale* - **X** 0.13 **Y** 0.13  **Z** 0.13</span></span>

        ![Actualizar la transformación rect del lienzo.](images/AzureLabs-Lab1-23.png)
 
4.  <span data-ttu-id="9ecc4-283">Haga clic con el botón derecho en el **lienzo** en el *jerarquía Panel*, en **UI**y agregue un **Panel**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-283">Right click on the **Canvas** in the *Hierarchy Panel*, under **UI**, and add a **Panel**.</span></span> <span data-ttu-id="9ecc4-284">Esto **Panel** proporcionará un fondo para el texto que se va a mostrar en la escena.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-284">This **Panel** will provide a background to the text that you will be displaying in the scene.</span></span>
5.  <span data-ttu-id="9ecc4-285">Haga clic con el botón derecho en el **Panel** en el *jerarquía Panel*, en **UI**y agregue un **objeto de texto**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-285">Right click on the **Panel** in the *Hierarchy Panel*, under **UI**, and add a **Text object**.</span></span> <span data-ttu-id="9ecc4-286">Repita el mismo proceso hasta que haya creado cuatro objetos de texto de la interfaz de usuario en total (Sugerencia: si tiene el primer objeto de 'Text' seleccionado, puede simplemente presionar **'Ctrl' + tenía '**, duplicarla, hasta que haya cuatro en total).</span><span class="sxs-lookup"><span data-stu-id="9ecc4-286">Repeat the same process until you have created four UI Text objects in total (Hint: if you have the first ‘Text’ object selected, you can simply press **‘Ctrl’ + ‘D’**, to duplicate it, until you have four in total).</span></span> 
6.  <span data-ttu-id="9ecc4-287">Para cada **objeto texto**, selecciónelo y utilice el debajo de las tablas para definir los parámetros el *Panel Inspector*.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-287">For each **Text Object**, select it and use the below tables to set the parameters in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="9ecc4-288">Para el *Rect transformación* componente:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-288">For the *Rect Transform* component:</span></span>

        | <span data-ttu-id="9ecc4-289">Nombre</span><span class="sxs-lookup"><span data-stu-id="9ecc4-289">Name</span></span>                   | <span data-ttu-id="9ecc4-290">Transformar - *posición*</span><span class="sxs-lookup"><span data-stu-id="9ecc4-290">Transform - *Position*</span></span>             | <span data-ttu-id="9ecc4-291">Ancho</span><span class="sxs-lookup"><span data-stu-id="9ecc4-291">Width</span></span>      | <span data-ttu-id="9ecc4-292">Alto</span><span class="sxs-lookup"><span data-stu-id="9ecc4-292">Height</span></span>    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | <span data-ttu-id="9ecc4-293">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="9ecc4-293">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="9ecc4-294">**X** -80 **Y** 90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="9ecc4-294">**X** -80 **Y** 90 **Z** 0</span></span>         | <span data-ttu-id="9ecc4-295">300</span><span class="sxs-lookup"><span data-stu-id="9ecc4-295">300</span></span>        | <span data-ttu-id="9ecc4-296">30</span><span class="sxs-lookup"><span data-stu-id="9ecc4-296">30</span></span>        |
        | <span data-ttu-id="9ecc4-297">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="9ecc4-297">AzureResponseLabel</span></span>     | <span data-ttu-id="9ecc4-298">**X** -80 **Y** 30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="9ecc4-298">**X** -80 **Y** 30 **Z** 0</span></span>         | <span data-ttu-id="9ecc4-299">300</span><span class="sxs-lookup"><span data-stu-id="9ecc4-299">300</span></span>        | <span data-ttu-id="9ecc4-300">30</span><span class="sxs-lookup"><span data-stu-id="9ecc4-300">30</span></span>        |
        | <span data-ttu-id="9ecc4-301">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="9ecc4-301">DictationLabel</span></span>         | <span data-ttu-id="9ecc4-302">**X** -80 **Y** -30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="9ecc4-302">**X** -80 **Y** -30 **Z** 0</span></span>        | <span data-ttu-id="9ecc4-303">300</span><span class="sxs-lookup"><span data-stu-id="9ecc4-303">300</span></span>        | <span data-ttu-id="9ecc4-304">30</span><span class="sxs-lookup"><span data-stu-id="9ecc4-304">30</span></span>        |
        | <span data-ttu-id="9ecc4-305">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="9ecc4-305">TranslationResultLabel</span></span> | <span data-ttu-id="9ecc4-306">**X** -80 **Y** -90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="9ecc4-306">**X** -80 **Y** -90 **Z** 0</span></span>        | <span data-ttu-id="9ecc4-307">300</span><span class="sxs-lookup"><span data-stu-id="9ecc4-307">300</span></span>        | <span data-ttu-id="9ecc4-308">30</span><span class="sxs-lookup"><span data-stu-id="9ecc4-308">30</span></span>        |


    2. <span data-ttu-id="9ecc4-309">Para el **texto (Script)** componente:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-309">For the **Text (Script)** component:</span></span>


        | <span data-ttu-id="9ecc4-310">Nombre</span><span class="sxs-lookup"><span data-stu-id="9ecc4-310">Name</span></span>                   | <span data-ttu-id="9ecc4-311">Text</span><span class="sxs-lookup"><span data-stu-id="9ecc4-311">Text</span></span>               | <span data-ttu-id="9ecc4-312">Tamaño de fuente</span><span class="sxs-lookup"><span data-stu-id="9ecc4-312">Font Size</span></span>    |
        |:----------------------:|:------------------:|:------------:|
        | <span data-ttu-id="9ecc4-313">MicrophoneStatusLabel</span><span class="sxs-lookup"><span data-stu-id="9ecc4-313">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="9ecc4-314">Estado de micrófono:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-314">Microphone Status:</span></span> | <span data-ttu-id="9ecc4-315">20</span><span class="sxs-lookup"><span data-stu-id="9ecc4-315">20</span></span>           |
        | <span data-ttu-id="9ecc4-316">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="9ecc4-316">AzureResponseLabel</span></span>     | <span data-ttu-id="9ecc4-317">Respuesta Web de Azure</span><span class="sxs-lookup"><span data-stu-id="9ecc4-317">Azure Web Response</span></span> | <span data-ttu-id="9ecc4-318">20</span><span class="sxs-lookup"><span data-stu-id="9ecc4-318">20</span></span>           |
        | <span data-ttu-id="9ecc4-319">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="9ecc4-319">DictationLabel</span></span>         |   <span data-ttu-id="9ecc4-320">Acabamos de decir:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-320">You just said:</span></span>   | <span data-ttu-id="9ecc4-321">20</span><span class="sxs-lookup"><span data-stu-id="9ecc4-321">20</span></span>           |
        | <span data-ttu-id="9ecc4-322">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="9ecc4-322">TranslationResultLabel</span></span> |    <span data-ttu-id="9ecc4-323">Traducción:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-323">Translation:</span></span>    | <span data-ttu-id="9ecc4-324">20</span><span class="sxs-lookup"><span data-stu-id="9ecc4-324">20</span></span>           |

        ![Escriba los valores correspondientes para las etiquetas de interfaz de usuario.](images/AzureLabs-Lab1-24.png)

    3. <span data-ttu-id="9ecc4-326">Además, asegúrese del estilo de fuente **negrita**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-326">Also, make the Font Style **Bold**.</span></span> <span data-ttu-id="9ecc4-327">Esto hará que el texto más fácil de leer.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-327">This will make the text easier to read.</span></span>

        ![Fuente negrita.](images/AzureLabs-Lab1-25.png)

7.  <span data-ttu-id="9ecc4-329">Para cada *objeto de texto de la interfaz de usuario* creado en [capítulo 5](#chapter-5--create-the-results-class), cree un nuevo *secundarios* **objeto de texto de la interfaz de usuario**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-329">For each *UI Text object* created in [Chapter 5](#chapter-5--create-the-results-class), create a new *child* **UI Text object**.</span></span> <span data-ttu-id="9ecc4-330">Estos controles secundarios mostrarán el resultado de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-330">These children will display the output of the application.</span></span> <span data-ttu-id="9ecc4-331">Crear *secundarios* objetos a través con el botón secundario de su padre deseado (por ejemplo, *MicrophoneStatusLabel*) y, a continuación, seleccione **UI** y, a continuación, seleccione **texto**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-331">Create *child* objects through right-clicking your intended parent (e.g. *MicrophoneStatusLabel*) and then select **UI** and then select **Text**.</span></span>
8.  <span data-ttu-id="9ecc4-332">Para cada uno de estos controles secundarios, selecciónelo y utilice el debajo de las tablas para definir los parámetros en el Panel del Inspector.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-332">For each of these children, select it and use the below tables to set the parameters in the Inspector Panel.</span></span>

    1. <span data-ttu-id="9ecc4-333">Para el **Rect transformación** componente:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-333">For the **Rect Transform** component:</span></span>

        | <span data-ttu-id="9ecc4-334">Nombre</span><span class="sxs-lookup"><span data-stu-id="9ecc4-334">Name</span></span>                  | <span data-ttu-id="9ecc4-335">Transformar - *posición*</span><span class="sxs-lookup"><span data-stu-id="9ecc4-335">Transform - *Position*</span></span> | <span data-ttu-id="9ecc4-336">Ancho</span><span class="sxs-lookup"><span data-stu-id="9ecc4-336">Width</span></span>      | <span data-ttu-id="9ecc4-337">Alto</span><span class="sxs-lookup"><span data-stu-id="9ecc4-337">Height</span></span>    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | <span data-ttu-id="9ecc4-338">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="9ecc4-338">MicrophoneStatusText</span></span>  | <span data-ttu-id="9ecc4-339">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="9ecc4-339">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="9ecc4-340">300</span><span class="sxs-lookup"><span data-stu-id="9ecc4-340">300</span></span>        | <span data-ttu-id="9ecc4-341">30</span><span class="sxs-lookup"><span data-stu-id="9ecc4-341">30</span></span>        |
        | <span data-ttu-id="9ecc4-342">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="9ecc4-342">AzureResponseText</span></span>     | <span data-ttu-id="9ecc4-343">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="9ecc4-343">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="9ecc4-344">300</span><span class="sxs-lookup"><span data-stu-id="9ecc4-344">300</span></span>        | <span data-ttu-id="9ecc4-345">30</span><span class="sxs-lookup"><span data-stu-id="9ecc4-345">30</span></span>        |
        | <span data-ttu-id="9ecc4-346">DictationText</span><span class="sxs-lookup"><span data-stu-id="9ecc4-346">DictationText</span></span>         | <span data-ttu-id="9ecc4-347">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="9ecc4-347">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="9ecc4-348">300</span><span class="sxs-lookup"><span data-stu-id="9ecc4-348">300</span></span>        | <span data-ttu-id="9ecc4-349">30</span><span class="sxs-lookup"><span data-stu-id="9ecc4-349">30</span></span>        |
        | <span data-ttu-id="9ecc4-350">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="9ecc4-350">TranslationResultText</span></span> | <span data-ttu-id="9ecc4-351">X 0 Y -30 Z 0</span><span class="sxs-lookup"><span data-stu-id="9ecc4-351">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="9ecc4-352">300</span><span class="sxs-lookup"><span data-stu-id="9ecc4-352">300</span></span>        | <span data-ttu-id="9ecc4-353">30</span><span class="sxs-lookup"><span data-stu-id="9ecc4-353">30</span></span>        |

    2. <span data-ttu-id="9ecc4-354">Para el **texto (Script)** componente:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-354">For the **Text (Script)** component:</span></span>

        | <span data-ttu-id="9ecc4-355">Name</span><span class="sxs-lookup"><span data-stu-id="9ecc4-355">Name</span></span>                  | <span data-ttu-id="9ecc4-356">Text</span><span class="sxs-lookup"><span data-stu-id="9ecc4-356">Text</span></span>          | <span data-ttu-id="9ecc4-357">Tamaño de fuente</span><span class="sxs-lookup"><span data-stu-id="9ecc4-357">Font Size</span></span>    |
        |:---------------------:|:-------------:|:------------:|
        | <span data-ttu-id="9ecc4-358">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="9ecc4-358">MicrophoneStatusText</span></span>  |      <span data-ttu-id="9ecc4-359">??</span><span class="sxs-lookup"><span data-stu-id="9ecc4-359">??</span></span>       | <span data-ttu-id="9ecc4-360">20</span><span class="sxs-lookup"><span data-stu-id="9ecc4-360">20</span></span>           |
        | <span data-ttu-id="9ecc4-361">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="9ecc4-361">AzureResponseText</span></span>     |      <span data-ttu-id="9ecc4-362">??</span><span class="sxs-lookup"><span data-stu-id="9ecc4-362">??</span></span>       | <span data-ttu-id="9ecc4-363">20</span><span class="sxs-lookup"><span data-stu-id="9ecc4-363">20</span></span>           |
        | <span data-ttu-id="9ecc4-364">DictationText</span><span class="sxs-lookup"><span data-stu-id="9ecc4-364">DictationText</span></span>         |      <span data-ttu-id="9ecc4-365">??</span><span class="sxs-lookup"><span data-stu-id="9ecc4-365">??</span></span>       | <span data-ttu-id="9ecc4-366">20</span><span class="sxs-lookup"><span data-stu-id="9ecc4-366">20</span></span>           |
        | <span data-ttu-id="9ecc4-367">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="9ecc4-367">TranslationResultText</span></span> |      <span data-ttu-id="9ecc4-368">??</span><span class="sxs-lookup"><span data-stu-id="9ecc4-368">??</span></span>       | <span data-ttu-id="9ecc4-369">20</span><span class="sxs-lookup"><span data-stu-id="9ecc4-369">20</span></span>           |

9. <span data-ttu-id="9ecc4-370">A continuación, seleccione la opción de alineación de "centre" para cada componente de texto:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-370">Next, select the 'centre' alignment option for each text component:</span></span>

    ![Alinear el texto.](images/AzureLabs-Lab1-26.png)

10. <span data-ttu-id="9ecc4-372">Para garantizar la **texto de la interfaz de usuario secundario** objetos sean fácilmente legibles, cambie sus *Color*.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-372">To ensure the **child UI Text** objects are easily readable, change their *Color*.</span></span> <span data-ttu-id="9ecc4-373">Esto se realiza al hacer clic en la barra (actualmente ' negro") junto a *Color*.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-373">Do this by clicking on the bar (currently ‘Black’) next to *Color*.</span></span> 

    ![Entrada correspondiente a los valores de las salidas de texto de la interfaz de usuario.](images/AzureLabs-Lab1-27.png)
 
11. <span data-ttu-id="9ecc4-375">A continuación, en el nuevo, pequeño, *Color* ventana, cambie el *de Color hexadecimal* para: **0032EAFF**</span><span class="sxs-lookup"><span data-stu-id="9ecc4-375">Then, in the new, little, *Color* window, change the *Hex Color* to: **0032EAFF**</span></span>

    ![Actualice el color a azul.](images/AzureLabs-Lab1-28.png)
 
12. <span data-ttu-id="9ecc4-377">A continuación se presenta cómo la **UI** debe tener un aspecto.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-377">Below is how the **UI** should look.</span></span>
    1.  <span data-ttu-id="9ecc4-378">En el *jerarquía Panel*:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-378">In the *Hierarchy Panel*:</span></span>

        ![Tiene la jerarquía de la estructura proporcionada.](images/AzureLabs-Lab1-29.png)

    2.  <span data-ttu-id="9ecc4-380">En el *escena* y *juegos vistas*:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-380">In the *Scene* and *Game Views*:</span></span>

        ![Tiene las vistas de la escena y juego en la misma estructura.](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a><span data-ttu-id="9ecc4-382">Capítulo 5: crear la clase de resultados</span><span class="sxs-lookup"><span data-stu-id="9ecc4-382">Chapter 5 – Create the Results class</span></span>

<span data-ttu-id="9ecc4-383">Es el primer script, deberá crear el *resultados* (clase), que es responsable de proporcionar una manera de ver los resultados de la traducción.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-383">The first script you need to create is the *Results* class, which is responsible for providing a way to see the results of translation.</span></span> <span data-ttu-id="9ecc4-384">La clase almacena y muestra lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-384">The Class stores and displays the following:</span></span> 

- <span data-ttu-id="9ecc4-385">El resultado de la respuesta de Azure.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-385">The response result from Azure.</span></span>
- <span data-ttu-id="9ecc4-386">El estado de micrófono.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-386">The microphone status.</span></span> 
- <span data-ttu-id="9ecc4-387">El resultado de la dictado (voz a texto).</span><span class="sxs-lookup"><span data-stu-id="9ecc4-387">The result of the dictation (voice to text).</span></span>
- <span data-ttu-id="9ecc4-388">El resultado de la traducción.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-388">The result of the translation.</span></span>

<span data-ttu-id="9ecc4-389">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-389">To create this class:</span></span> 

1.  <span data-ttu-id="9ecc4-390">Haga clic en el *Panel del proyecto*, a continuación, **crear > carpeta**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-390">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="9ecc4-391">Nombre de la carpeta **Scripts**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-391">Name the folder **Scripts**.</span></span> 
 
    ![Crear carpeta de scripts.](images/AzureLabs-Lab1-31.png)

    ![Abra la carpeta de scripts.](images/AzureLabs-Lab1-32.png)
 
2.  <span data-ttu-id="9ecc4-394">Con el **Scripts** carpeta crear, haga doble clic en él para abrirlo.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-394">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="9ecc4-395">A continuación, dentro de esa carpeta, contextual y seleccione **crear >** , a continuación,  **C# Script**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-395">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="9ecc4-396">Nombre de la secuencia de comandos *resultados*.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-396">Name the script *Results*.</span></span> 

    ![Cree la primera secuencia de comandos.](images/AzureLabs-Lab1-33.png)
 
3.  <span data-ttu-id="9ecc4-398">Haga doble clic en el nuevo *resultados* script para abrirlo con **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-398">Double click on the new *Results* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="9ecc4-399">Inserte los espacios de nombres siguientes:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-399">Insert the following namespaces:</span></span>

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  <span data-ttu-id="9ecc4-400">Dentro de la clase inserte las siguientes variables:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-400">Inside the Class insert the following variables:</span></span>

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

6.  <span data-ttu-id="9ecc4-401">A continuación, agregue el *Awake()* método, que se llamará cuando se inicializa la clase.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-401">Then add the *Awake()* method, which will be called when the class initializes.</span></span> 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  <span data-ttu-id="9ecc4-402">Por último, agregue los métodos que son responsables de generar la diversa información de los resultados a la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-402">Finally, add the methods which are responsible for outputting the various results information to the UI.</span></span> 

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

8.  <span data-ttu-id="9ecc4-403">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-403">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-6--create-the-microphonemanager-class"></a><span data-ttu-id="9ecc4-404">Capítulo 6: crear el *MicrophoneManager* clase</span><span class="sxs-lookup"><span data-stu-id="9ecc4-404">Chapter 6 – Create the *MicrophoneManager* class</span></span>

<span data-ttu-id="9ecc4-405">La segunda clase va a crear es la *MicrophoneManager*.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-405">The second class you are going to create is the *MicrophoneManager*.</span></span>

<span data-ttu-id="9ecc4-406">Esta clase es responsable de:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-406">This class is responsible for:</span></span>

- <span data-ttu-id="9ecc4-407">Detectar el dispositivo de grabación conectado al equipo (lo que sea el valor predeterminado) o auriculares.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-407">Detecting the recording device attached to the headset or machine (whichever is the default).</span></span>
- <span data-ttu-id="9ecc4-408">Captura de audio (voces) y use el dictado para almacenarla como una cadena.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-408">Capture the audio (voice) and use dictation to store it as a string.</span></span>
- <span data-ttu-id="9ecc4-409">Una vez que se ha pausado la voz, enviar el dictado a la clase de traductor.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-409">Once the voice has paused, submit the dictation to the Translator class.</span></span>
- <span data-ttu-id="9ecc4-410">Hospedar un método que se puede detener la captura de voz si lo desea.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-410">Host a method that can stop the voice capture if desired.</span></span>

<span data-ttu-id="9ecc4-411">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-411">To create this class:</span></span> 
1.  <span data-ttu-id="9ecc4-412">Haga doble clic en el **Scripts** carpeta para abrirla.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-412">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="9ecc4-413">Haga clic en el **Scripts** carpeta, haga clic en **crear > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="9ecc4-414">Nombre de la secuencia de comandos *MicrophoneManager*.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-414">Name the script *MicrophoneManager*.</span></span> 
3.  <span data-ttu-id="9ecc4-415">Haga doble clic en el nuevo script para abrirlo con Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-415">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="9ecc4-416">Actualice los espacios de nombres para que sea igual a lo siguiente en la parte superior de la *MicrophoneManager* clase:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-416">Update the namespaces to be the same as the following, at the top of the *MicrophoneManager* class:</span></span>

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="9ecc4-417">A continuación, agregue las siguientes variables dentro de la *MicrophoneManager* clase:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-417">Then, add the following variables inside the *MicrophoneManager* class:</span></span>

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

6.  <span data-ttu-id="9ecc4-418">El código para el *Awake()* y *Start()* métodos ahora debe agregarse.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-418">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="9ecc4-419">Estos se llamará cuando se inicializa la clase:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-419">These will be called when the class initializes:</span></span>

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

7.  <span data-ttu-id="9ecc4-420">También puede *eliminar* el *Update()* método puesto que esta clase no lo usará.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-420">You can *delete* the *Update()* method since this class will not use it.</span></span>
8.  <span data-ttu-id="9ecc4-421">Ahora tiene los métodos que usa la aplicación para iniciar y detener la captura de voz y pasarlo a la *traductor* (clase), que se compila en breve.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-421">Now you need the methods that the App uses to start and stop the voice capture, and pass it to the *Translator* class, that you will build soon.</span></span> <span data-ttu-id="9ecc4-422">Copie el código siguiente y péguelo debajo de la *Start()* método.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-422">Copy the following code and paste it beneath the *Start()* method.</span></span>

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
    > <span data-ttu-id="9ecc4-423">Aunque no hará que esta aplicación use, el *StopCapturingAudio()* método también se ha proporcionado en este caso, si desea implementar la capacidad para detener la captura de audio en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-423">Though this application will not make use of it, the *StopCapturingAudio()* method has also been provided here, should you want to implement the ability to stop capturing audio in your application.</span></span>

9.  <span data-ttu-id="9ecc4-424">Ahora debe agregar un controlador de dictado que se invocará cuando se detiene la voz.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-424">You now need to add a Dictation Handler that will be invoked when the voice stops.</span></span> <span data-ttu-id="9ecc4-425">Este método, a continuación, pasará el texto dictado a la *traductor* clase.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-425">This method will then pass the dictated text to the *Translator* class.</span></span>

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

10. <span data-ttu-id="9ecc4-426">Asegúrese de guardar los cambios en Visual Studio antes de volver a Unity.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-426">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

> [!WARNING]  
> <span data-ttu-id="9ecc4-427">En este momento aparece un error que aparecen en la *consola del Editor de Unity* Panel ("el nombre 'Traductor' no existe …").</span><span class="sxs-lookup"><span data-stu-id="9ecc4-427">At this point you will notice an error appearing in the *Unity Editor Console* Panel (“The name ‘Translator’ does not exist...”).</span></span> <span data-ttu-id="9ecc4-428">Esto es porque el código hace referencia a la *traductor* (clase), que creará en el próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-428">This is because the code references the *Translator* class, which you will create in the next chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-translator-service"></a><span data-ttu-id="9ecc4-429">Capítulo 7: llamada al servicio de Azure y el traductor</span><span class="sxs-lookup"><span data-stu-id="9ecc4-429">Chapter 7 – Call to Azure and translator service</span></span>

<span data-ttu-id="9ecc4-430">Es el último script, deberá crear el *traductor* clase.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-430">The last script you need to create is the *Translator* class.</span></span> 

<span data-ttu-id="9ecc4-431">Esta clase es responsable de:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-431">This class is responsible for:</span></span>

-   <span data-ttu-id="9ecc4-432">Autenticar la aplicación con *Azure*, exchange para un **Auth Token**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-432">Authenticating the App with *Azure*, in exchange for an **Auth Token**.</span></span>
-   <span data-ttu-id="9ecc4-433">Use la **Token de autenticación** para enviar texto (recibidos desde el *MicrophoneManager* clase) que se deben traducir.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-433">Use the **Auth Token** to submit text (received from the *MicrophoneManager* Class) to be translated.</span></span>
-   <span data-ttu-id="9ecc4-434">Recibir el resultado traducido y páselo a la *resultados* clase que se visualizará en la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-434">Receive the translated result and pass it to the *Results* Class to be visualized in the UI.</span></span>

<span data-ttu-id="9ecc4-435">Para crear esta clase:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-435">To create this Class:</span></span> 
1.  <span data-ttu-id="9ecc4-436">Vaya a la **Scripts** carpeta que creó anteriormente.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-436">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="9ecc4-437">Haga clic en el **Panel del proyecto**, **crear > C# Script**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-437">Right-click in the **Project Panel**, **Create > C# Script**.</span></span> <span data-ttu-id="9ecc4-438">Llame al script *traductor*.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-438">Call the script *Translator*.</span></span>
3.  <span data-ttu-id="9ecc4-439">Haga doble clic en el nuevo *traductor* script para abrirlo **con Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-439">Double click on the new *Translator* script to open it **with Visual Studio**.</span></span>
4.  <span data-ttu-id="9ecc4-440">Agregue los siguientes espacios de nombres en la parte superior del archivo:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-440">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="9ecc4-441">A continuación, agregue las siguientes variables dentro de la *traductor* clase:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-441">Then add the following variables inside the *Translator* class:</span></span>

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
    > - <span data-ttu-id="9ecc4-442">Los idiomas que se insertan en los idiomas **enum** son solo ejemplos.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-442">The languages inserted into the languages **enum** are just examples.</span></span> <span data-ttu-id="9ecc4-443">Puede agregar más si lo desea; el [API admite más de 60 idiomas](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (incluido Klingon)!</span><span class="sxs-lookup"><span data-stu-id="9ecc4-443">Feel free to add more if you wish; the [API supports over 60 languages](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (including Klingon)!</span></span>
    > - <span data-ttu-id="9ecc4-444">Hay un [página más interactiva que cubre lenguajes disponibles](https://www.microsoft.com/translator/business/languages/), aunque tenga en la página solo aparece para que funcione cuando se establece el idioma del sitio en "en-us' (y el sitio de Microsoft le redireccionamiento probable para su idioma nativo).</span><span class="sxs-lookup"><span data-stu-id="9ecc4-444">There is a [more interactive page covering available languages](https://www.microsoft.com/translator/business/languages/), though be aware the page only appears to work when the site language is set to 'en-us' (and the Microsoft site will likely redirect to your native language).</span></span> <span data-ttu-id="9ecc4-445">Puede cambiar el idioma del sitio en la parte inferior de la página o modificando la dirección URL.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-445">You can change site language at the bottom of the page or by altering the URL.</span></span>
    > - <span data-ttu-id="9ecc4-446">El **authorizationKey** valor, en el fragmento de código anterior, debe ser el **clave** recibe al suscribirse a la *Azure Translator Text API*.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-446">The **authorizationKey** value, in the above code snippet, must be the **Key**  you received when you subscribed to the *Azure Translator Text API*.</span></span> <span data-ttu-id="9ecc4-447">Esto se trata en [capítulo 1](#chapter-1--the-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="9ecc4-447">This was covered in [Chapter 1](#chapter-1--the-azure-portal).</span></span>

6.  <span data-ttu-id="9ecc4-448">El código para el *Awake()* y *Start()* métodos ahora debe agregarse.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-448">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> 
7.  <span data-ttu-id="9ecc4-449">En este caso, el código hará que una llamada a *Azure* con la clave de autorización para obtener un *Token*.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-449">In this case, the code will make a call to *Azure* using the authorization Key, to get a *Token*.</span></span>

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
    > <span data-ttu-id="9ecc4-450">El token expirará transcurridos 10 minutos.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-450">The token will expire after 10 minutes.</span></span> <span data-ttu-id="9ecc4-451">Según el escenario de la aplicación, es posible que deba realizar la misma corrutina llamada varias veces.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-451">Depending on the scenario for your app, you might have to make the same coroutine call multiple times.</span></span>

8.  <span data-ttu-id="9ecc4-452">La corrutina para obtener el Token es la siguiente:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-452">The coroutine to obtain the Token is the following:</span></span>

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
    > <span data-ttu-id="9ecc4-453">Si edita el nombre del método IEnumerator **GetTokenCoroutine()**, deberá actualizar el *StartCoroutine* y *StopCoroutine* llamar a los valores de cadena en el código anterior.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-453">If you edit the name of the IEnumerator method **GetTokenCoroutine()**, you need to update the *StartCoroutine* and *StopCoroutine* call string values in the above code.</span></span> <span data-ttu-id="9ecc4-454">[Según la documentación de Unity](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), para detener un determinado *Corrutina*, deberá usar el método de valor de cadena.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-454">[As per Unity documentation](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), to Stop a specific *Coroutine*, you need to use the string value method.</span></span>

9.  <span data-ttu-id="9ecc4-455">A continuación, agregue la corrutina (con un método de secuencia "soporte técnico" situado debajo de ella) para obtener la traducción de texto recibida el *MicrophoneManager* clase.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-455">Next, add the coroutine (with a “support” stream method right below it) to obtain the translation of the text received by the *MicrophoneManager* class.</span></span> <span data-ttu-id="9ecc4-456">Este código crea una cadena de consulta para enviar a la *Azure Translator Text API*y, a continuación, utiliza la clase de Unity UnityWebRequest interna para realizar una llamada de 'Get' al punto de conexión con la cadena de consulta.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-456">This code creates a query string to send to the *Azure Translator Text API*, and then uses the internal Unity UnityWebRequest class to make a ‘Get’ call to the endpoint with the query string.</span></span> <span data-ttu-id="9ecc4-457">El resultado, a continuación, se usa para establecer la traducción en el objeto de resultados.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-457">The result is then used to set the translation in your Results object.</span></span> <span data-ttu-id="9ecc4-458">El código siguiente muestra la implementación:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-458">The code below shows the implementation:</span></span>

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

10. <span data-ttu-id="9ecc4-459">Asegúrese de guardar los cambios en *Visual Studio* antes de volver a *Unity*.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-459">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--configure-the-unity-scene"></a><span data-ttu-id="9ecc4-460">Capítulo 8: configurar la escena de Unity</span><span class="sxs-lookup"><span data-stu-id="9ecc4-460">Chapter 8 – Configure the Unity Scene</span></span>

1.  <span data-ttu-id="9ecc4-461">En el Editor de Unity, haga clic en Atrás y arrastre el *resultados* clase *desde* el **Scripts** carpeta para el **cámara principal** objeto en el  *Panel de la jerarquía*.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-461">Back in the Unity Editor, click and drag the *Results* class *from* the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="9ecc4-462">Haga clic en el **cámara principal** y examine el *Panel Inspector*.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-462">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="9ecc4-463">Observará que en la recién agregada *Script* , componente, hay cuatro campos con valores vacíos.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-463">You will notice that within the newly added *Script* component, there are four fields with empty values.</span></span> <span data-ttu-id="9ecc4-464">Estas son las referencias de salida a las propiedades en el código.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-464">These are the output references to the properties in the code.</span></span> 
3.  <span data-ttu-id="9ecc4-465">Arrastre adecuado **texto** objetos desde el *jerarquía Panel* para esas cuatro ranuras, tal como se muestra en la imagen siguiente.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-465">Drag the appropriate **Text** objects from the *Hierarchy Panel* to those four slots, as shown in the image below.</span></span>

    ![Actualice las referencias de destino con los valores especificados.](images/AzureLabs-Lab1-34.png)
  
4.  <span data-ttu-id="9ecc4-467">A continuación, haga clic y arrastre el *traductor* clase desde el **Scripts** carpeta a la **cámara principal** objeto en el *jerarquía Panel*.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-467">Next, click and drag the *Translator* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
5.  <span data-ttu-id="9ecc4-468">A continuación, haga clic y arrastre el *MicrophoneManager* clase desde el **secuencias de comandos** carpeta para el **cámara principal** objeto en el *jerarquía Panel*.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-468">Then, click and drag the *MicrophoneManager* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
6.  <span data-ttu-id="9ecc4-469">Por último, haga clic en el **cámara principal** y examine el *Panel Inspector*.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-469">Lastly, click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="9ecc4-470">Observará que en la secuencia de comandos que se arrastró en, hay dos cuadros desplegables de que le permitirá establecer los idiomas.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-470">You will notice that in the script you dragged on, there are two drop down boxes that will allow you to set the languages.</span></span>
 
    ![Asegúrese de que se introducen los idiomas de traducción previsto.](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a><span data-ttu-id="9ecc4-472">Capítulo 9: prueba de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="9ecc4-472">Chapter 9 – Test in mixed reality</span></span>

<span data-ttu-id="9ecc4-473">En este momento deberá comprobar que se ha implementado correctamente la escena.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-473">At this point you need to test that the Scene has been properly implemented.</span></span>

<span data-ttu-id="9ecc4-474">Asegúrate de lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-474">Ensure that:</span></span>

- <span data-ttu-id="9ecc4-475">Todas las configuraciones que se mencionan en [capítulo 1](#chapter-1--the-azure-portal) están establecidas correctamente.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-475">All the settings mentioned in [Chapter 1](#chapter-1--the-azure-portal) are set correctly.</span></span> 
- <span data-ttu-id="9ecc4-476">El *resultados*, *traductor*, y *MicrophoneManager*, secuencias de comandos están conectados a la **cámara principal** objeto.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-476">The *Results*, *Translator*, and *MicrophoneManager*, scripts are attached to the **Main Camera** object.</span></span> 
- <span data-ttu-id="9ecc4-477">Ha colocado su *Azure Translator Text API* servicio **clave** dentro de la **authorizationKey** variable dentro de la *traductor* Guión.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-477">You have placed your *Azure Translator Text API* Service **Key** within the **authorizationKey** variable within the *Translator* Script.</span></span>  
- <span data-ttu-id="9ecc4-478">Todos los campos de la *Panel de Inspector de cámara principal* se asignan correctamente.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-478">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
- <span data-ttu-id="9ecc4-479">El micrófono está funcionando cuando se ejecuta la escena (si no, compruebe que el micrófono conectado es el *predeterminada* dispositivo y que tiene [configurarlo correctamente dentro de Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span><span class="sxs-lookup"><span data-stu-id="9ecc4-479">Your microphone is working when running your scene (if not, check that your attached microphone is the *default* device, and that you have [set it up correctly within Windows](https://support.microsoft.com/en-au/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span></span>

<span data-ttu-id="9ecc4-480">Puede probar los auriculares envolventes presionando el **reproducir** situado en la *Editor de Unity*.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-480">You can test the immersive headset by pressing the **Play** button in the *Unity Editor*.</span></span>
<span data-ttu-id="9ecc4-481">La aplicación debe funcionar a través de los auriculares envolventes adjunto.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-481">The App should be functioning through the attached immersive headset.</span></span>

> [!WARNING]  
> <span data-ttu-id="9ecc4-482">Si ve un error en la consola de Unity sobre el dispositivo de audio predeterminado cambia, la escena podría no funcionar según lo previsto.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-482">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="9ecc4-483">Esto es debido al modo en que el portal de realidad mixta se ocupa de los micrófonos integrados para auriculares que disponen de ella.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-483">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="9ecc4-484">Si ve este error, basta con detener la escena y vuelva a iniciarlo y todo debería funcionar como se esperaba.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-484">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a><span data-ttu-id="9ecc4-485">Capítulo 10: crear la solución UWP y transferir localmente en el equipo local</span><span class="sxs-lookup"><span data-stu-id="9ecc4-485">Chapter 10 – Build the UWP solution and sideload on local machine</span></span>

<span data-ttu-id="9ecc4-486">Todo lo necesario para la sección de Unity de este proyecto ahora se completó, por lo que es el momento de crearla desde Unity.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-486">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="9ecc4-487">Vaya a **configuración de compilación**: **Archivo > configuración de compilación...**</span><span class="sxs-lookup"><span data-stu-id="9ecc4-487">Navigate to **Build Settings**: **File > Build Settings...**</span></span>
2.  <span data-ttu-id="9ecc4-488">Desde el **configuración de compilación** ventana, haga clic en **compilar**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-488">From the **Build Settings** window, click **Build**.</span></span>

    ![Compile la escena de Unity.](images/AzureLabs-Lab1-36.png)
  
3.  <span data-ttu-id="9ecc4-490">Si aún no marque **Unity C# proyectos**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-490">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="9ecc4-491">Haz clic en **Compilación**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-491">Click **Build**.</span></span> <span data-ttu-id="9ecc4-492">Unity se iniciará un *Explorador de archivos* ventana, donde se debe crear y, a continuación, seleccione una carpeta para compilar la aplicación en.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-492">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="9ecc4-493">Crear la carpeta y asígnele el nombre *aplicación*.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-493">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="9ecc4-494">A continuación, con el *aplicación* carpeta seleccionada, presione **seleccionar la carpeta**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-494">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="9ecc4-495">Unity empezará a compilar el proyecto para el *aplicación* carpeta.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-495">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="9ecc4-496">Una vez Unity ha finalizado la compilación (puede tardar algún tiempo), se abrirá un *Explorador de archivos* ventana en la ubicación de la compilación (comprobación de la barra de tareas, tal y como es posible que no siempre aparecen por encima de las ventanas, pero le informará de la adición de un nuevo ventana).</span><span class="sxs-lookup"><span data-stu-id="9ecc4-496">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11--deploy-your-application"></a><span data-ttu-id="9ecc4-497">Capítulo 11: implementar la aplicación</span><span class="sxs-lookup"><span data-stu-id="9ecc4-497">Chapter 11 – Deploy your application</span></span>

<span data-ttu-id="9ecc4-498">Para implementar la aplicación:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-498">To deploy your application:</span></span>

1.  <span data-ttu-id="9ecc4-499">Vaya a la nueva compilación de Unity (la *aplicación* carpeta) y abra el archivo de solución con *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-499">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
2.  <span data-ttu-id="9ecc4-500">En, seleccione la configuración de la solución **depurar**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-500">In the Solution Configuration select **Debug**.</span></span>
3.  <span data-ttu-id="9ecc4-501">En la plataforma de soluciones, seleccione **x86**, **máquina Local**.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-501">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="9ecc4-502">Para el Microsoft HoloLens, quizá le resulte más fácil establecer esto en *máquina remota*, de modo que no están atados a su equipo.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-502">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="9ecc4-503">Sin embargo, necesitará también hacer lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="9ecc4-503">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="9ecc4-504">Conocer el **dirección IP** de su HoloLens, que se encuentra dentro de la *configuración > red e Internet > Wi-Fi > Opciones avanzadas*; IPv4 es la dirección que debe usar.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-504">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="9ecc4-505">Asegúrese de *modo de programador* es **en**; se encuentra en *configuración > actualización y seguridad > para los desarrolladores*.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-505">Ensure *Developer Mode* is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Implementar la solución de Visual Studio.](images/AzureLabs-Lab1-37.png)
    
 
4.  <span data-ttu-id="9ecc4-507">Vaya a **menú compilar** y haga clic en **implementar solución** para transferir localmente la aplicación a su equipo.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-507">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>
5.  <span data-ttu-id="9ecc4-508">La aplicación debería aparecer ahora en la lista de las aplicaciones instaladas, listos para iniciarse.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-508">Your App should now appear in the list of installed apps, ready to be launched.</span></span>
6.  <span data-ttu-id="9ecc4-509">Una vez iniciado, la aplicación le pedirá que autorice el acceso al micrófono.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-509">Once launched, the App will prompt you to authorize access to the Microphone.</span></span> <span data-ttu-id="9ecc4-510">Asegúrese de hacer clic en el **Sí** botón.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-510">Make sure to click the **YES** button.</span></span>
7.  <span data-ttu-id="9ecc4-511">Ahora está listo para comenzar a traducir.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-511">You are now ready to start translating!</span></span>

## <a name="your-finished-translation-text-api-application"></a><span data-ttu-id="9ecc4-512">La aplicación finalizada de Text Translation API</span><span class="sxs-lookup"><span data-stu-id="9ecc4-512">Your finished Translation Text API application</span></span>

<span data-ttu-id="9ecc4-513">Enhorabuena, ha creado una aplicación de realidad mixta que aprovecha la API de texto de traducción de Azure para convertir voz en texto traducido.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-513">Congratulations, you built a mixed reality app that leverages the Azure Translation Text API to convert speech to translated text.</span></span>

![Producto final.](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="9ecc4-515">Ejercicios de bonificación</span><span class="sxs-lookup"><span data-stu-id="9ecc4-515">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="9ecc4-516">Ejercicio 1</span><span class="sxs-lookup"><span data-stu-id="9ecc4-516">Exercise 1</span></span>

<span data-ttu-id="9ecc4-517">¿Puede agregar texto a voz funcionalidad a la aplicación, por lo que se diga el texto devuelto?</span><span class="sxs-lookup"><span data-stu-id="9ecc4-517">Can you add text-to-speech functionality to the app, so that the returned text is spoken?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="9ecc4-518">Ejercicio 2</span><span class="sxs-lookup"><span data-stu-id="9ecc4-518">Exercise 2</span></span>

<span data-ttu-id="9ecc4-519">Permiten al usuario cambiar los idiomas de origen y de salida ('from' y 'to') dentro de la propia aplicación, por lo que la aplicación no necesitan volver a crearse cada vez desee cambiar los idiomas.</span><span class="sxs-lookup"><span data-stu-id="9ecc4-519">Make it possible for the user to change the source and output languages ('from' and 'to') within the app itself, so the app does not need to be rebuilt every time you want to change languages.</span></span>
