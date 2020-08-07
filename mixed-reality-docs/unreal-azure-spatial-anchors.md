---
title: Azure Spatial Anchors en Unreal
description: Información general sobre la creación de Azure Spatial Anchors en Unreal Engine.
author: hferrone
services: azure-spatial-anchors
ms.author: v-haferr
ms.date: 07/01/2020
ms.topic: tutorial
ms.service: azure-spatial-anchors
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, azure, desarrollo de azure, anclajes espaciales, realidad mixta, desarrollo, características, nuevo proyecto, emulador, documentación, guías, hologramas, desarrollo de juegos
ms.openlocfilehash: c7189407bea4b38e7305f0dda7637b82d3325704
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87377350"
---
# <a name="azure-spatial-anchors-in-unreal"></a><span data-ttu-id="5482b-104">Azure Spatial Anchors en Unreal</span><span class="sxs-lookup"><span data-stu-id="5482b-104">Azure Spatial Anchors in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="5482b-105">Introducción</span><span class="sxs-lookup"><span data-stu-id="5482b-105">Overview</span></span>

<span data-ttu-id="5482b-106">Azure Spatial Anchors es un servicio de Microsoft Mixed Reality, que permite que los dispositivos de realidad aumentada detecten, compartan y conserven puntos de anclaje en el mundo físico.</span><span class="sxs-lookup"><span data-stu-id="5482b-106">Azure Spatial Anchors is a Microsoft Mixed Reality service, allowing augmented reality devices to discover, share, and persist anchor points in the physical world.</span></span> <span data-ttu-id="5482b-107">En la documentación siguiente se proporcionan instrucciones para integrar el servicio de Azure Spatial Anchors en un proyecto de Unreal.</span><span class="sxs-lookup"><span data-stu-id="5482b-107">Documentation below provides instructions for integrating the Azure Spatial Anchors service into an Unreal project.</span></span> <span data-ttu-id="5482b-108">Si busca más información, consulte el [servicio de Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/).</span><span class="sxs-lookup"><span data-stu-id="5482b-108">If you're looking for more information, check out the [Azure Spatial Anchors service](https://azure.microsoft.com/services/spatial-anchors/).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5482b-109">Los anclajes locales se almacenan en el dispositivo, mientras que los Azure Spatial Anchors se almacenan en la nube.</span><span class="sxs-lookup"><span data-stu-id="5482b-109">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="5482b-110">Si tiene pensado almacenar los anclajes localmente en un dispositivo, hay un documento de [Anclajes espaciales locales](unreal-spatial-anchors.md) que puede guiarle por el proceso.</span><span class="sxs-lookup"><span data-stu-id="5482b-110">If you're looking to store your anchors locally on a device, we have a [Local Spatial Anchors](unreal-spatial-anchors.md) document that can walk you through the process.</span></span> <span data-ttu-id="5482b-111">Tenga en cuenta que puede tener anclajes locales y de Azure en el mismo proyecto sin que existan conflictos.</span><span class="sxs-lookup"><span data-stu-id="5482b-111">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5482b-112">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="5482b-112">Prerequisites</span></span>

<span data-ttu-id="5482b-113">Para completar esta guía, asegúrese de tener:</span><span class="sxs-lookup"><span data-stu-id="5482b-113">To complete this guide, make sure you have:</span></span>

- <span data-ttu-id="5482b-114">Instalado [Unreal versión 4.25](https://www.unrealengine.com/get-now) o posterior</span><span class="sxs-lookup"><span data-stu-id="5482b-114">Installed [Unreal version 4.25](https://www.unrealengine.com/get-now) or later</span></span>
- <span data-ttu-id="5482b-115">Un [proyecto de HoloLens 2](unreal-uxt-ch1.md) configurado en Unreal</span><span class="sxs-lookup"><span data-stu-id="5482b-115">A [HoloLens 2 project](unreal-uxt-ch1.md) setup in Unreal</span></span> 
- <span data-ttu-id="5482b-116">Leída la [información general de Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/overview)</span><span class="sxs-lookup"><span data-stu-id="5482b-116">Read through the [Azure Spatial Anchors overview](https://docs.microsoft.com/azure/spatial-anchors/overview)</span></span>
- <span data-ttu-id="5482b-117">Conocimientos básicos de C++ y Unreal</span><span class="sxs-lookup"><span data-stu-id="5482b-117">Basic knowledge on C++ and Unreal</span></span>

## <a name="getting-azure-spatial-anchors-account-info"></a><span data-ttu-id="5482b-118">Obtención de información de cuenta de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="5482b-118">Getting Azure Spatial Anchors account info</span></span>

<span data-ttu-id="5482b-119">Antes de usar Azure Spatial Anchors en un proyecto, debe:</span><span class="sxs-lookup"><span data-stu-id="5482b-119">Before using Azure Spatial Anchors in your project, you need to:</span></span>
* <span data-ttu-id="5482b-120">[Crear un recurso de anclajes espaciales](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) y copiar los campos de la cuenta que se enumeran a continuación.</span><span class="sxs-lookup"><span data-stu-id="5482b-120">[Create a spatial anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) and copy the account fields listed below.</span></span> <span data-ttu-id="5482b-121">Estos valores se usan para autenticar a los usuarios con la cuenta de la aplicación:</span><span class="sxs-lookup"><span data-stu-id="5482b-121">These values are used to authenticate users with your application's account:</span></span>
    * <span data-ttu-id="5482b-122">**Id. de cuenta**</span><span class="sxs-lookup"><span data-stu-id="5482b-122">**Account ID**</span></span>
    * <span data-ttu-id="5482b-123">**Clave de cuenta**</span><span class="sxs-lookup"><span data-stu-id="5482b-123">**Account Key**</span></span>

<span data-ttu-id="5482b-124">Para obtener más información, consulte los documentos de [autenticación de Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp).</span><span class="sxs-lookup"><span data-stu-id="5482b-124">Check out the [Azure Spatial Anchors authentication](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp) docs for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="5482b-125">Azure Spatial Anchors en Unreal 4.25 no admite tokens de autenticación de Azure AD, pero la compatibilidad con esta funcionalidad estará disponible en una versión posterior.</span><span class="sxs-lookup"><span data-stu-id="5482b-125">Azure Spatial Anchors in Unreal 4.25 does not support Azure AD authentication tokens, but support for this functionality will be coming in a later release.</span></span>

## <a name="adding-azure-spatial-anchors-plugins"></a><span data-ttu-id="5482b-126">Adición de complementos de Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="5482b-126">Adding Azure Spatial Anchors plugins</span></span>

<span data-ttu-id="5482b-127">Para habilitar los complementos de Azure Spatial Anchors en el editor de Unreal:</span><span class="sxs-lookup"><span data-stu-id="5482b-127">Enable the Azure Spatial Anchors plugins in the Unreal editor by:</span></span>
1. <span data-ttu-id="5482b-128">Haga clic en **Edit > Plugins** (Editar > Complementos) y busque **AzureSpatialAnchors** y **AzureSpatialAnchorsForWMR**.</span><span class="sxs-lookup"><span data-stu-id="5482b-128">Clicking **Edit > Plugins** and searching for **AzureSpatialAnchors** and **AzureSpatialAnchorsForWMR**.</span></span>
2. <span data-ttu-id="5482b-129">Active la casilla **Enabled** (Habilitado) en ambos complementos para permitir el acceso a las bibliotecas de planos técnicos de Azure Spatial Anchors en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5482b-129">Select the **Enabled** checkbox in both plugins to allow access to the Azure Spatial Anchors blueprint libraries in your application.</span></span>

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-01.png)

<span data-ttu-id="5482b-131">Una vez hecho esto, reinicie Unreal Editor para que los cambios de los complementos surtan efecto.</span><span class="sxs-lookup"><span data-stu-id="5482b-131">Once that's done, restart the Unreal Editor for the plugin changes to take effect.</span></span> <span data-ttu-id="5482b-132">El proyecto ahora está listo para usar Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="5482b-132">The project is now ready to use Azure Spatial Anchors.</span></span>

## <a name="starting-a-spatial-anchors-session"></a><span data-ttu-id="5482b-133">Inicio de una sesión en Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="5482b-133">Starting a Spatial Anchors session</span></span>
<span data-ttu-id="5482b-134">Una sesión de Azure Spatial Anchors permite que las aplicaciones cliente se comuniquen con el servicio de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="5482b-134">An Azure Spatial Anchors session allows client applications to communicate with the Azure Spatial Anchors service.</span></span> <span data-ttu-id="5482b-135">Deberá crear e iniciar una sesión de Azure Spatial Anchors para crear, conservar y compartir Azure Spatial Anchors:</span><span class="sxs-lookup"><span data-stu-id="5482b-135">You'll need to create and start an Azure Spatial Anchors session to create, persist, and share Azure Spatial Anchors:</span></span>

1. <span data-ttu-id="5482b-136">Abra el plano técnico del Pawn (Peón) que está usando en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5482b-136">Open the blueprint for the Pawn you're using in the application.</span></span>
2. <span data-ttu-id="5482b-137">Agregue dos variables de cadena para **Account ID** (ID. de cuenta) y **Account Key** (Clave de cuenta) y, a continuación, asigne los valores correspondientes de la cuenta de Azure Spatial Anchors para autenticar la sesión.</span><span class="sxs-lookup"><span data-stu-id="5482b-137">Add two string variables for the **Account ID** and **Account Key**, then assign the corresponding values from your Azure Spatial Anchors account to authenticate the session.</span></span>

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-02.png)

<span data-ttu-id="5482b-139">Para iniciar una sesión de Azure Spatial Anchors:</span><span class="sxs-lookup"><span data-stu-id="5482b-139">Start an Azure Spatial Anchors session by:</span></span>
1. <span data-ttu-id="5482b-140">Compruebe que se está ejecutando una **AR Session** (Sesión de AR) en la aplicación de HoloLens, ya que la sesión de Azure Spatial Anchors no puede iniciarse mientras no se esté ejecutando una sesión de AR.</span><span class="sxs-lookup"><span data-stu-id="5482b-140">Checking that an **AR Session** is running in the HoloLens application, as the Azure Spatial Anchors session can't start until an AR Session is running.</span></span> <span data-ttu-id="5482b-141">Si no tiene una configurada, [cree un recurso de AR Session](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span><span class="sxs-lookup"><span data-stu-id="5482b-141">If you don't have one setup, [create an AR Session asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>
2. <span data-ttu-id="5482b-142">Agregue el evento personalizado **Start Azure Spatial Anchors Session** (Iniciar sesión de Azure Spatial Anchors) y configúrelo como se muestra en la captura de pantalla siguiente.</span><span class="sxs-lookup"><span data-stu-id="5482b-142">Adding the **Start Azure Spatial Anchors Session** custom event and configure it as shown in the screenshot below.</span></span>
    * <span data-ttu-id="5482b-143">Al crear una sesión no se inicia la sesión de forma predeterminada, lo que permite que el desarrollador configure la sesión para la autenticación en el servicio de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="5482b-143">Creating a session doesn't start the session by default, which allows the developer to configure the session for authentication with the Azure Spatial Anchors service.</span></span>

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-03.png)

3. <span data-ttu-id="5482b-145">Configure la sesión de Azure Spatial Anchors para que proporcione **Account ID** (Id. de cuenta) y **Account Key** (Clave de cuenta).</span><span class="sxs-lookup"><span data-stu-id="5482b-145">Configure the Azure Spatial Anchors session to provide the **Account ID** and **Account Key**.</span></span>

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-04.png)

4. <span data-ttu-id="5482b-147">Inicie la sesión de Azure Spatial Anchors, lo que permite a la aplicación crear y ubicar los Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="5482b-147">Start the Azure Spatial Anchors session, allowing the application to create and locate Azure Spatial Anchors.</span></span>

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-05.png)

<span data-ttu-id="5482b-149">Se recomienda limpiar los recursos de Azure Spatial Anchors en el plano técnico Event Graph (Gráfico de eventos) cuando ya no use el servicio:</span><span class="sxs-lookup"><span data-stu-id="5482b-149">It's good practice to clean up Azure Spatial Anchors resources in your Event Graph blueprint when you're no longer using the service:</span></span>

1. <span data-ttu-id="5482b-150">Detenga la sesión de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="5482b-150">Stop the Azure Spatial Anchors session.</span></span> <span data-ttu-id="5482b-151">La sesión ya no estará en ejecución, pero sus recursos asociados seguirán existiendo en el complemento de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="5482b-151">The session will no longer be running, but its associated resources will still exist in the Azure Spatial Anchors plugin.</span></span>

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-06.png)

2. <span data-ttu-id="5482b-153">Destruya la sesión de Azure Spatial Anchors para limpiar los recursos de la sesión de Azure Spatial Anchors aún conocidos por el complemento de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="5482b-153">Destroy the Azure Spatial Anchors session to clean up any Azure Spatial Anchors session resources still known to the Azure Spatial Anchors plugin.</span></span>

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-07.png)

<span data-ttu-id="5482b-155">El plano técnico Event Graph (Gráfico de eventos) debe ser similar a la siguiente captura de pantalla:</span><span class="sxs-lookup"><span data-stu-id="5482b-155">Your Event Graph blueprint should look like the screenshot below:</span></span>

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-08.png)


## <a name="creating-an-anchor"></a><span data-ttu-id="5482b-157">Creación de un anclaje</span><span class="sxs-lookup"><span data-stu-id="5482b-157">Creating an anchor</span></span>
<span data-ttu-id="5482b-158">Un Azure Spatial Anchor representa un lugar del mundo físico en el espacio de la aplicación de realidad aumentada, que fija el contenido de la realidad aumentada a ubicaciones del mundo físico.</span><span class="sxs-lookup"><span data-stu-id="5482b-158">An Azure Spatial Anchor represents a physical world pose in the augmented reality application space, which locks augmented reality content to locations in the physical world.</span></span> <span data-ttu-id="5482b-159">Los Azure Spatial Anchors también se pueden compartir entre distintos usuarios.</span><span class="sxs-lookup"><span data-stu-id="5482b-159">Azure Spatial Anchors can also be shared among different users.</span></span> <span data-ttu-id="5482b-160">Este uso compartido permite que el contenido de la realidad aumentada dibujado en diferentes dispositivos se coloque en la misma ubicación del mundo físico.</span><span class="sxs-lookup"><span data-stu-id="5482b-160">This sharing allows augmented reality content drawn on different devices to be positioned in the same location in the physical world.</span></span> 

<span data-ttu-id="5482b-161">Para crear un nuevo Azure Spatial Anchor:</span><span class="sxs-lookup"><span data-stu-id="5482b-161">To create a new Azure Spatial Anchor:</span></span>
1. <span data-ttu-id="5482b-162">Compruebe que haya una sesión de Azure Spatial Anchors en ejecución.</span><span class="sxs-lookup"><span data-stu-id="5482b-162">Check that an Azure Spatial Anchors session is running.</span></span> <span data-ttu-id="5482b-163">La aplicación no puede crear o conservar un Azure Spatial Anchor cuando no se está ejecutando ninguna sesión de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="5482b-163">The application can't create or persist an Azure Spatial Anchor when no Azure Spatial Anchors session is running.</span></span>

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-09.png)

2. <span data-ttu-id="5482b-165">Cree u obtenga un **[Scene Component](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** (Componente de escena) de Unreal cuya ubicación deba conservarse.</span><span class="sxs-lookup"><span data-stu-id="5482b-165">Create or obtain an Unreal **[Scene Component](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** that should have its location persisted.</span></span> 
    * <span data-ttu-id="5482b-166">En la imagen siguiente, el componente **Scene Component Needing Anchor** se usa como variable.</span><span class="sxs-lookup"><span data-stu-id="5482b-166">In the below image, the **Scene Component Needing Anchor** component is used as a variable.</span></span> <span data-ttu-id="5482b-167">Se necesita un componente de escena de Unreal para establecer una transformación del mundo de la aplicación para un [AR Pin](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) (Marca de AR) y Azure Spatial Anchor.</span><span class="sxs-lookup"><span data-stu-id="5482b-167">An Unreal Scene Component is needed to establish an application world transform for an [AR Pin](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) and Azure Spatial Anchor.</span></span>

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-10.png)

<span data-ttu-id="5482b-169">Para construir y guardar un Azure Spatial Anchor para un componente de escena de Unreal:</span><span class="sxs-lookup"><span data-stu-id="5482b-169">To construct and save an Azure Spatial Anchor for an Unreal Scene Component:</span></span>
1. <span data-ttu-id="5482b-170">Llame al [Pin Component](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html) (Componente de marca) para el componente de escena de Unreal y especifique la **World Transform** (Transformación de mundos) del componente de escena como la transformación de mundos que se usa para AR Pin (Marca de AR).</span><span class="sxs-lookup"><span data-stu-id="5482b-170">Call the [Pin Component](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html) for the Unreal Scene Component and specify the Scene Component's **World Transform** as the World Transform used for the AR Pin.</span></span>
    * <span data-ttu-id="5482b-171">Unreal realiza un seguimiento de los puntos de AR en el espacio de la aplicación mediante AR Pins (Marcas de AR), que se usan para crear un Azure Spatial Anchor.</span><span class="sxs-lookup"><span data-stu-id="5482b-171">Unreal tracks AR points in the application space using AR Pins, which are used to create an Azure Spatial Anchor.</span></span> <span data-ttu-id="5482b-172">En Unreal, una AR Pin (Marca de AR) es análoga a SpatialAnchor en HoloLens.</span><span class="sxs-lookup"><span data-stu-id="5482b-172">In Unreal, an AR Pin is analogous to a SpatialAnchor on HoloLens.</span></span>

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-11.png)

2. <span data-ttu-id="5482b-174">Llame a **Create Cloud Anchor** (Crear anclaje de nube) con la AR Pin (Marca de AR) recién creada.</span><span class="sxs-lookup"><span data-stu-id="5482b-174">Call **Create Cloud Anchor** using the newly created AR Pin.</span></span>
    * <span data-ttu-id="5482b-175">Create Cloud Anchor crea un Azure Spatial Anchor de forma local, pero no en el servicio de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="5482b-175">Create Cloud Anchor creates an Azure Spatial Anchor locally but not in the Azure Spatial Anchor service.</span></span> <span data-ttu-id="5482b-176">Los parámetros del Azure Spatial Anchor, como una fecha de expiración, se pueden establecer antes de crear el Azure Spatial Anchor con el servicio.</span><span class="sxs-lookup"><span data-stu-id="5482b-176">Parameters for the Azure Spatial Anchor, such as an expiration date, can be set before creating the Azure Spatial Anchor with the service.</span></span>

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-12.png)

3. <span data-ttu-id="5482b-178">Establezca la expiración del Azure Spatial Anchor.</span><span class="sxs-lookup"><span data-stu-id="5482b-178">Set the Azure Spatial Anchor expiration.</span></span> <span data-ttu-id="5482b-179">El parámetro Lifetime (Duración) de la función permite al desarrollador especificar en segundos cuánto tiempo debe el servicio mantener el anclaje.</span><span class="sxs-lookup"><span data-stu-id="5482b-179">This function's Lifetime parameter allows the developer to specify in seconds how long the anchor should be maintained by the service.</span></span>
    * <span data-ttu-id="5482b-180">Por ejemplo, una expiración de una semana tomaría un valor de 60 segundos x 60 minutos x 24 horas x 7 días = 604 800 segundos.</span><span class="sxs-lookup"><span data-stu-id="5482b-180">For example, a week long expiration would take a value of 60 seconds x 60 minutes x 24 hours x seven days = 604,800 seconds.</span></span>

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-13.png)

<span data-ttu-id="5482b-182">Después de establecer los parámetros de los anclajes, declare el anclaje como listo para guardarse.</span><span class="sxs-lookup"><span data-stu-id="5482b-182">After setting anchor parameters, declare the anchor as ready to save.</span></span> <span data-ttu-id="5482b-183">En el ejemplo siguiente, el Azure Spatial Anchor recién creado se agrega a un conjunto de Azure Spatial Anchors que debe guardarse.</span><span class="sxs-lookup"><span data-stu-id="5482b-183">In the example below, the newly created Azure Spatial Anchor is added to a set of Azure Spatial Anchors needing saving.</span></span> <span data-ttu-id="5482b-184">Este conjunto se declara como variable para el plano técnico del Pawn (Peón).</span><span class="sxs-lookup"><span data-stu-id="5482b-184">This set is declared as a variable for the Pawn blueprint.</span></span>

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-14.png)

## <a name="saving-an-anchor"></a><span data-ttu-id="5482b-186">Guardado de un anclaje</span><span class="sxs-lookup"><span data-stu-id="5482b-186">Saving an Anchor</span></span>

<span data-ttu-id="5482b-187">Después de configurar el Azure Spatial Anchor con sus parámetros, llame a **Save Cloud Anchor** (Guardar anclaje de nube).</span><span class="sxs-lookup"><span data-stu-id="5482b-187">After configuring the Azure Spatial Anchor with your parameters, call **Save Cloud Anchor**.</span></span> <span data-ttu-id="5482b-188">Save Cloud Anchor declara el anclaje en el servicio de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="5482b-188">Save Cloud Anchor declares the anchor to the Azure Spatial Anchors service.</span></span> <span data-ttu-id="5482b-189">Cuando la llamada a Save Cloud Anchor se realiza correctamente, el Azure Spatial Anchor está disponible para otros usuarios del servicio de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="5482b-189">When the call to Save Cloud Anchor succeeds, the Azure Spatial Anchor is available to other users of the Azure Spatial Anchor service.</span></span>  

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-15.png)

> [!NOTE]
> <span data-ttu-id="5482b-191">Save Cloud Anchor es una función asincrónica y solo se puede llamar desde un evento de subproceso de juego, como **EventTick**.</span><span class="sxs-lookup"><span data-stu-id="5482b-191">Save Cloud Anchor is an asynchronous function and can only be called on a game thread event such as **EventTick**.</span></span> <span data-ttu-id="5482b-192">Es posible que Save Cloud Anchor no aparezca como una función de plano técnico en el plano técnico personalizado Functions (Funciones).</span><span class="sxs-lookup"><span data-stu-id="5482b-192">Save Cloud Anchor may not appear as an available blueprint function in custom blueprint Functions.</span></span> <span data-ttu-id="5482b-193">Sin embargo, debe estar disponible en el editor de planos técnicos Event Graph (Gráfico de eventos) del Pawn (Peón).</span><span class="sxs-lookup"><span data-stu-id="5482b-193">However, it should be available in the Pawn Event Graph blueprint editor.</span></span>

<span data-ttu-id="5482b-194">En el ejemplo siguiente, el Azure Spatial Anchor se almacena en un conjunto durante una devolución de llamada del evento de entrada.</span><span class="sxs-lookup"><span data-stu-id="5482b-194">In the example below, the Azure Spatial Anchor is stored in a set during an input event callback.</span></span> <span data-ttu-id="5482b-195">Después, el elemento se guarda en EventTick.</span><span class="sxs-lookup"><span data-stu-id="5482b-195">The anchor is then saved on the EventTick.</span></span> <span data-ttu-id="5482b-196">Se pueden necesitar varios intentos para guardar un Azure Spatial Anchor, en función de la cantidad de datos espaciales que se hayan creado en la sesión de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="5482b-196">Saving an Azure Spatial Anchor may take multiple attempts depending on the amount of spatial data that your Azure Spatial Anchors session has created.</span></span> <span data-ttu-id="5482b-197">Por eso es conveniente comprobar si la llamada de guardado se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="5482b-197">That's why it's a good idea to check whether the save call succeeded.</span></span>

<span data-ttu-id="5482b-198">Si el anclaje no se guarda, vuelva a agregarlo al conjunto de anclajes que todavía deben guardarse.</span><span class="sxs-lookup"><span data-stu-id="5482b-198">If the anchor doesn't save, re-add it to the set of anchors still needing to be saved.</span></span> <span data-ttu-id="5482b-199">Los EventTicks futuros intentarán guardar el anclaje hasta que se almacene correctamente en el servicio de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="5482b-199">Future EventTicks will try to save the anchor until it's successfully stored in the Azure Spatial Anchor service.</span></span>

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-16.png)

<span data-ttu-id="5482b-201">Una vez que se guarde el anclaje, puede usar la transformación de AR Pins (Marcas de AR) como transformación de referencia para colocar contenido en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5482b-201">Once the anchor saves, you can use the AR Pins' transform as a reference transform for placing content in the application.</span></span> <span data-ttu-id="5482b-202">Otros usuarios pueden detectar este anclaje y alinear el contenido de AR para diferentes dispositivos del mundo físico.</span><span class="sxs-lookup"><span data-stu-id="5482b-202">Other users can detect this anchor and align AR content for different devices in the physical world.</span></span>

## <a name="deleting-an-anchor"></a><span data-ttu-id="5482b-203">Eliminación de un anclaje</span><span class="sxs-lookup"><span data-stu-id="5482b-203">Deleting an Anchor</span></span>

<span data-ttu-id="5482b-204">Puede eliminar los anclajes del servicio Azure Spatial Anchors llamando a **Delete Cloud Anchor** (Eliminar anclaje de nube).</span><span class="sxs-lookup"><span data-stu-id="5482b-204">You can delete anchors from the Azure Spatial Anchor service by calling **Delete Cloud Anchor**.</span></span>

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-17.png)

> [!NOTE]
> <span data-ttu-id="5482b-206">Delete Cloud Anchor es una función latente y solo se puede llamar desde un evento de subproceso de juego, como EventTick.</span><span class="sxs-lookup"><span data-stu-id="5482b-206">Delete Cloud Anchor is a latent function and can only be called on a game thread event, such as EventTick.</span></span> <span data-ttu-id="5482b-207">Es posible que Delete Cloud Anchor no aparezca como una función de plano técnico en el plano técnico personalizado Functions (Funciones).</span><span class="sxs-lookup"><span data-stu-id="5482b-207">Delete Cloud Anchor may not appear as an available blueprint function in custom blueprint Functions.</span></span> <span data-ttu-id="5482b-208">Sin embargo, debe estar disponible en el editor de planos técnicos Event Graph (Gráfico de eventos) del Pawn (Peón).</span><span class="sxs-lookup"><span data-stu-id="5482b-208">It should however be available in the Pawn Event Graph blueprint editor.</span></span>

<span data-ttu-id="5482b-209">En el ejemplo siguiente, el anclaje está marcado para su eliminación en un evento de entrada personalizado.</span><span class="sxs-lookup"><span data-stu-id="5482b-209">In the example below, the anchor is flagged for deletion on a custom input event.</span></span> <span data-ttu-id="5482b-210">A continuación, se intenta la eliminación en EventTick.</span><span class="sxs-lookup"><span data-stu-id="5482b-210">The deletion is then attempted on the EventTick.</span></span> <span data-ttu-id="5482b-211">Si se produce un error en la eliminación del anclaje, agregue el Azure Spatial Anchor al conjunto de anclajes marcados para su eliminación y vuelva a intentarlo en EventTicks posteriores.</span><span class="sxs-lookup"><span data-stu-id="5482b-211">If the anchor deletion fails, add the Azure Spatial Anchor to the set of anchors flagged for deletion and tries again on later EventTicks.</span></span>

<span data-ttu-id="5482b-212">El plano técnico Event Graph (Gráfico de eventos) ahora debe ser similar a la siguiente captura de pantalla:</span><span class="sxs-lookup"><span data-stu-id="5482b-212">Your Event Graph blueprint should now look like the screenshot below:</span></span>

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-18.png)


## <a name="locating-pre-existing-anchors"></a><span data-ttu-id="5482b-214">Detección de anclajes preexistentes</span><span class="sxs-lookup"><span data-stu-id="5482b-214">Locating pre-existing anchors</span></span>

<span data-ttu-id="5482b-215">Además de crear Azure Spatial Anchors, puede detectar anclajes creados por pares con el servicio de Azure Spatial Anchors:</span><span class="sxs-lookup"><span data-stu-id="5482b-215">In addition to creating Azure Spatial Anchors, you can detect anchors created by peers with the Azure Spatial Anchors service:</span></span>

1. <span data-ttu-id="5482b-216">Obtenga un identificador de Azure Spatial Anchor para el anclaje que desea detectar.</span><span class="sxs-lookup"><span data-stu-id="5482b-216">Obtain an Azure Spatial Anchor identifier for the anchor that you would like to detect.</span></span>
    * <span data-ttu-id="5482b-217">Se puede obtener un identificador de anclaje para un anclaje creado por el mismo dispositivo en una sesión anterior de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="5482b-217">An anchor identifier can be obtained for an anchor created by the same device in a previous Azure Spatial Anchors session.</span></span> <span data-ttu-id="5482b-218">También se puede crear y compartir mediante dispositivos del mismo nivel que interactúen con el servicio de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="5482b-218">It can also be created and shared by peer devices interacting with the Azure Spatial Anchors service.</span></span>

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-24.png)

2. <span data-ttu-id="5482b-220">Agregue un componente **AzureSpatialAnchorsEvent** al plano técnico del Pawn (Peón).</span><span class="sxs-lookup"><span data-stu-id="5482b-220">Add an **AzureSpatialAnchorsEvent** component to your Pawn blueprint.</span></span>
    * <span data-ttu-id="5482b-221">Este componente le permite suscribirse a varios eventos de Azure Spatial Anchors, como los eventos a los que se llama cuando se detectan Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="5482b-221">This component allows you to subscribe to various Azure Spatial Anchors events, such as events called when Azure Spatial Anchors are located.</span></span>

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-19.png)

3. <span data-ttu-id="5482b-223">Suscríbase a **ASAAnchor Located Delegate** (Delegado detectado de ASAAnchor) para el componente **AzureSpatialAnchorsEvent**.</span><span class="sxs-lookup"><span data-stu-id="5482b-223">Subscribe to the **ASAAnchor Located Delegate** for the **AzureSpatialAnchorsEvent** component.</span></span>
    * <span data-ttu-id="5482b-224">El delegado permite que la aplicación sepa cuándo se han encontrado nuevos anclajes asociados con la cuenta de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="5482b-224">The delegate lets the application know when new anchors associated with the Azure Spatial Anchors account have been located.</span></span>
    * <span data-ttu-id="5482b-225">Con la devolución de llamada del evento, no se crearán de forma predeterminada AR Pins (Marcas de AR) para los Azure Spatial Anchors creados por pares mediante la sesión de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="5482b-225">With the event callback, Azure Spatial Anchors created by peers using the Azure Spatial Anchors session won't have AR Pins created by default.</span></span> <span data-ttu-id="5482b-226">Para crear una AR Pin (Marca de AR) para el Spatial Anchor de Azure detectado, los desarrolladores pueden llamar a **Create ARPin Around Azure Cloud Spatial Anchor** (Crear ARPin en función del anclaje espacial en la nube de Azure).</span><span class="sxs-lookup"><span data-stu-id="5482b-226">To create an AR Pin for the detected Azure Spatial Anchor, developers can call **Create ARPin Around Azure Cloud Spatial Anchor**.</span></span>

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-20.png)

<span data-ttu-id="5482b-228">Para buscar los Azure Spatial Anchors creados por los pares mediante el servicio de Azure Spatial Anchors, la aplicación tendrá que crear un **Azure Spatial Anchors Watcher** (Monitor de Azure Spatial Anchors):</span><span class="sxs-lookup"><span data-stu-id="5482b-228">In order to locate Azure Spatial Anchors created by peers using the Azure Spatial Anchor service, the application will have to create an **Azure Spatial Anchors Watcher**:</span></span>
1. <span data-ttu-id="5482b-229">Compruebe que haya una sesión de Azure Spatial Anchors en ejecución.</span><span class="sxs-lookup"><span data-stu-id="5482b-229">Check that an Azure Spatial Anchors session is running.</span></span>
2. <span data-ttu-id="5482b-230">Cree un **AzureSpatialAnchorsLocateCriteria**.</span><span class="sxs-lookup"><span data-stu-id="5482b-230">Create an **AzureSpatialAnchorsLocateCriteria**.</span></span>
    * <span data-ttu-id="5482b-231">Puede especificar varios parámetros de ubicación, como la distancia desde el usuario o la distancia desde otro anclaje.</span><span class="sxs-lookup"><span data-stu-id="5482b-231">You can specify various location parameters like distance from the user or distance from another anchor.</span></span>
3. <span data-ttu-id="5482b-232">Declare el identificador del Azure Spatial Anchor que desee en **AzureSpatialAnchorsLocateCritieria**.</span><span class="sxs-lookup"><span data-stu-id="5482b-232">Declare your desired Azure Spatial Anchor identifier in the **AzureSpatialAnchorsLocateCritieria**.</span></span>
4. <span data-ttu-id="5482b-233">Llame a **Create Watcher** (Crear monitor).</span><span class="sxs-lookup"><span data-stu-id="5482b-233">Call **Create Watcher**.</span></span>

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-21.png)

<span data-ttu-id="5482b-235">Ahora, la aplicación comienza a buscar los Azure Spatial Anchors que conoce el servicio de Azure Spatial Anchors, lo que significa que los usuarios pueden localizar los Azure Spatial Anchors creados por sus pares.</span><span class="sxs-lookup"><span data-stu-id="5482b-235">The application now begins looking for Azure Spatial Anchors known to the Azure Spatial Anchors service, meaning that users can locate Azure Spatial Anchors created by their peers.</span></span>

<span data-ttu-id="5482b-236">Después de localizar el Azure Spatial Anchor, llame a **Stop Watcher** (Detener monitor) para detener Azure Spatial Anchors Watcher (Monitor de Azure Spatial Anchors) y limpie los recursos del monitor.</span><span class="sxs-lookup"><span data-stu-id="5482b-236">After locating the Azure Spatial Anchor, call **Stop Watcher** to stop the Azure Spatial Anchors Watcher and clean up watcher resources.</span></span>

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-22.png)

<span data-ttu-id="5482b-238">El plano técnico Event Graph (Gráfico de eventos) final ahora debe ser similar a la siguiente captura de pantalla:</span><span class="sxs-lookup"><span data-stu-id="5482b-238">Your final Event Graph blueprint should now look like the screenshot below:</span></span>

![Complementos de Spatial Anchors](images/asa-unreal/unreal-spatial-anchors-img-23.png)


## <a name="next-steps"></a><span data-ttu-id="5482b-240">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="5482b-240">Next steps</span></span>
* [<span data-ttu-id="5482b-241">Anclajes espaciales locales</span><span class="sxs-lookup"><span data-stu-id="5482b-241">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)
* [<span data-ttu-id="5482b-242">Documentación sobre anclajes espaciales</span><span class="sxs-lookup"><span data-stu-id="5482b-242">Spatial Anchors documentation</span></span>](https://docs.microsoft.com/azure/spatial-anchors/)
* [<span data-ttu-id="5482b-243">Características de Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="5482b-243">Spatial Anchor features</span></span>](https://azure.microsoft.com/services/spatial-anchors/#features)
* [<span data-ttu-id="5482b-244">Instrucciones sobre una experiencia de anclaje efectiva</span><span class="sxs-lookup"><span data-stu-id="5482b-244">Effective anchor experience guidelines</span></span>](https://docs.microsoft.com/azure/spatial-anchors/concepts/guidelines-effective-anchor-experiences)