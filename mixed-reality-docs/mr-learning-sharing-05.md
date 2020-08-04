---
title: 'Tutoriales sobre las funcionalidades multiusuario: 5. Integración de Azure Spatial Anchors en una experiencia compartida'
description: Completa este curso para aprender a implementar experiencias compartidas con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: fc8e20a9ddaa595db0a3d59975e7c785d01c0a6d
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376587"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="33175-105">5. Integración de Azure Spatial Anchors en una experiencia compartida</span><span class="sxs-lookup"><span data-stu-id="33175-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="33175-106">En este tutorial, aprenderás a integrar Azure Spatial Anchors (ASA) en la experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="33175-106">In this tutorial, you will learn how to integrate Azure Spatial Anchors (ASA) into the shared experience.</span></span> <span data-ttu-id="33175-107">ASA permite que varios dispositivos tengan una referencia común al mundo físico para que los usuarios se vean entre sí en su ubicación física real y vean la experiencia compartida en el mismo lugar.</span><span class="sxs-lookup"><span data-stu-id="33175-107">ASA allows multiple devices to have a common reference to the physical world so that the users see each other in their actual physical location and see the shared experience in the same place.</span></span>

## <a name="objectives"></a><span data-ttu-id="33175-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="33175-108">Objectives</span></span>

* <span data-ttu-id="33175-109">Integración de ASA en una experiencia compartida para la alineación de varios dispositivos</span><span class="sxs-lookup"><span data-stu-id="33175-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
* <span data-ttu-id="33175-110">Aprende los aspectos básicos del funcionamiento de ASA en el contexto de una experiencia compartida local.</span><span class="sxs-lookup"><span data-stu-id="33175-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="33175-111">Preparación de la escena</span><span class="sxs-lookup"><span data-stu-id="33175-111">Preparing the scene</span></span>

<span data-ttu-id="33175-112">En la ventana Jerarquía, expande el objeto **SharedPlayground** y, a continuación, expande el objeto **TableAnchor** para exponer sus objetos secundarios:</span><span class="sxs-lookup"><span data-stu-id="33175-112">In the Hierarchy window, expand the **SharedPlayground** object, then expand the **TableAnchor** object to expose its child objects:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section1-step1-1.png)

<span data-ttu-id="33175-114">En la ventana Proyecto, navegue hasta **Assets** (Recursos)  > **MRTK.Tutorials.MultiUserCapabilities** > carpeta **Prefabs** (Recursos prefabricados) y arrastre el elemento prefabricado **Buttons** para colocarlo encima del objeto secundario **TableAnchor** y agregarlo a la escena como elemento secundario del objeto TableAnchor:</span><span class="sxs-lookup"><span data-stu-id="33175-114">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **Buttons** prefab onto the **TableAnchor** child object to add it to your scene as a child of the TableAnchor object:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="33175-116">Configuración de los botones para el funcionamiento de la escena</span><span class="sxs-lookup"><span data-stu-id="33175-116">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="33175-117">En esta sección, configurará una serie de eventos de botón que muestran los aspectos básicos de cómo se puede usar Azure Spatial Anchors para lograr la alineación espacial en una experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="33175-117">In this section, you will configure a series of button events demonstrating the fundamentals of how Azure Spatial Anchors can be used to achieve spatial alignment in a shared experience.</span></span>

<span data-ttu-id="33175-118">En la ventana Jerarquía, expande el objeto **Button** y selecciona el primer objeto de botón secundario denominado **StartAzureSession**:</span><span class="sxs-lookup"><span data-stu-id="33175-118">In the Hierarchy window, expand the **Button** object and select the first child button object named **StartAzureSession**:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-1.png)

<span data-ttu-id="33175-120">En la ventana Inspector, busca el componente **Interactable (Script)** (Interactivo [script]) y configura el evento **OnClick ()** como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="33175-120">In the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="33175-121">En el campo **None (Object)** (Ninguno [objeto]), asigne el objeto **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="33175-121">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="33175-122">En el menú desplegable **Ninguna función**, seleccione la función **AnchorModuleScript** > **StartAzureSession ()** .</span><span class="sxs-lookup"><span data-stu-id="33175-122">From the **No Function** dropdown, select the **AnchorModuleScript** > **StartAzureSession ()** function</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-2.png)

<span data-ttu-id="33175-124">En la ventana Jerarquía, selecciona el segundo objeto de botón secundario denominado **CreateAzureAnchor** y, a continuación, en la ventana Inspector, busca el componente **Interactable (Script)** (Interactivo [script]) y configura el evento **OnClick ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="33175-124">In the Hierarchy window, select the second child button object named **CreateAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="33175-125">En el campo **None (Object)** (Ninguno [objeto]), asigne el objeto **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="33175-125">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="33175-126">En el menú desplegable **Ninguna función**, seleccione la función **AnchorModuleScript** > **CreateAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="33175-126">From the **No Function** dropdown, select the **AnchorModuleScript** > **CreateAzureAnchor ()** function</span></span>
* <span data-ttu-id="33175-127">En el nuevo campo **None (Game Object)** (Ninguno [objeto de juego]) que aparece, asigna el objeto **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="33175-127">To the new **None (Game Object)** field that appears, assign the **TableAnchor** object</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-3.png)

<span data-ttu-id="33175-129">En la ventana Jerarquía, selecciona el tercer objeto de botón secundario denominado **ShareAzureAnchor** y, a continuación, en la ventana Inspector, busca el componente **Interactable (Script)** (Interactivo [script]) y configura el evento **OnClick ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="33175-129">In the Hierarchy window, select the third child button object named **ShareAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="33175-130">En el campo **None (Object)** (Ninguno [objeto]), asigne el objeto **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="33175-130">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="33175-131">En el menú desplegable **Ninguna función**, seleccione **SharingModuleScript** > función **ShareAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="33175-131">From the **No Function** dropdown, select the **SharingModuleScript** > **ShareAzureAnchor ()** function</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-4.png)

<span data-ttu-id="33175-133">En la ventana Jerarquía, seleccione el cuarto objeto de botón secundario denominado **GetAzureAnchor** y, a continuación, en la ventana Inspector, busque el componente **Interactable (Script)** (Interactivo [script]) y configure el evento **OnClick ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="33175-133">In the Hierarchy window, select the fourth child button object named **GetAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="33175-134">En el campo **None (Object)** (Ninguno [objeto]), asigne el objeto **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="33175-134">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="33175-135">En el menú desplegable **Ninguna función**, seleccione **SharingModuleScript** > función **GetAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="33175-135">From the **No Function** dropdown, select the **SharingModuleScript** > **GetAzureAnchor ()** function</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="33175-137">Conexión de la escena al recurso de Azure</span><span class="sxs-lookup"><span data-stu-id="33175-137">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="33175-138">En la ventana Jerarquía, expande el objeto **SharedPlayground** y, a continuación, selecciona el objeto **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="33175-138">In the Hierarchy window, expand the **SharedPlayground** object and select the **TableAnchor** object.</span></span>

<span data-ttu-id="33175-139">En la ventana Inspector, busque el componente **Spatial Anchor Manager (Script)** (Administrador de anclaje espacial [script]) y configure la sección **Credenciales** con las credenciales de la cuenta de Azure Spatial Anchors que se creó como parte de los [requisitos previos](mr-learning-sharing-01.md#prerequisites) de esta serie de tutoriales:</span><span class="sxs-lookup"><span data-stu-id="33175-139">In the Inspector window, locate the **Spatial Anchor Manager (Script)** component and configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-sharing-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="33175-140">En el campo **Spatial Anchors Account ID** (Id. de la cuenta de Spatial Anchors), pega el valor **Id. de cuenta** de la cuenta de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="33175-140">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="33175-141">En el campo **Spatial Anchors Account ID** (Id. de la cuenta de Spatial Anchors), pega la **clave de acceso** primaria o secundaria de la cuenta de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="33175-141">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="33175-143">En lugar de configurar el id. y la clave de la cuenta de Spatial Anchors en la escena, puede establecerlos para todo el proyecto, lo que puede resultar ventajoso si tiene varias escenas con ASA.</span><span class="sxs-lookup"><span data-stu-id="33175-143">Instead of setting the Spatial Anchors Account ID and Key in the scene, you can set it for your entire project, this can be advantageous if you have multiple scenes using ASA.</span></span> <span data-ttu-id="33175-144">Para ello, en la ventana Proyecto, desplácese a Assets (Recursos) > AzureSpatialAnchors.SDK > Resources (Recursos) > recurso **SpatialAnchorConfig**, y después establezca los valores en la ventana Inspector.</span><span class="sxs-lookup"><span data-stu-id="33175-144">To do this, in the Project window, navigate to the Assets > AzureSpatialAnchors.SDK > Resources > **SpatialAnchorConfig** asset, then set the values in the Inspector window.</span></span>

<span data-ttu-id="33175-145">En la ventana Jerarquía, seleccione el objeto **TableAnchor**. A continuación, en la ventana Inspector, busque el componente **Anchor Module (Script)** (Módulo de anclaje [script]) y configúrelo de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="33175-145">In the Hierarchy window, select the **TableAnchor** object, then in the Inspector window, locate the **Anchor Module (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="33175-146">Cambie algunos dígitos en el campo **Public Sharing Pin** (PIN de uso compartido público), de modo que el PIN sea único para el proyecto.</span><span class="sxs-lookup"><span data-stu-id="33175-146">In the **Public Sharing Pin** field, change a few digits, so the pin becomes unique to your project</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-2.png)

<span data-ttu-id="33175-148">Con el objeto **TableAnchor** aún seleccionado, en la ventana Inspector, asegúrese de que todos los componentes de script estén **habilitados**:</span><span class="sxs-lookup"><span data-stu-id="33175-148">With the **TableAnchor** object still selected, in the Inspector window, make sure all the script components are **enabled**:</span></span>

* <span data-ttu-id="33175-149">Selecciona la casilla situada junto a **Spatial Anchor Manager (Script)** (Spatial Anchor Manager [script]) para habilitarla.</span><span class="sxs-lookup"><span data-stu-id="33175-149">Check the checkbox next to the **Spatial Anchor Manager (Script)** components to enable it</span></span>
* <span data-ttu-id="33175-150">Selecciona la casilla situada junto al componente **Anchor Module Script (Script)** (Script del módulo de anclaje [script]) para habilitarla.</span><span class="sxs-lookup"><span data-stu-id="33175-150">Check the checkbox next to the **Anchor Module Script (Script)** components to enable it</span></span>
* <span data-ttu-id="33175-151">Selecciona la casilla situada junto al componente **Sharing Module Script (Script)** (Script del módulo de uso compartido [script]) para habilitarla.</span><span class="sxs-lookup"><span data-stu-id="33175-151">Check the checkbox next to the **Sharing Module Script (Script)** components to enable it</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-05-section3-step1-3.png)

## <a name="trying-the-experience-with-spatial-alignment"></a><span data-ttu-id="33175-153">Prueba de la experiencia con la alineación espacial</span><span class="sxs-lookup"><span data-stu-id="33175-153">Trying the experience with spatial alignment</span></span>

> [!NOTE]
> <span data-ttu-id="33175-154">Azure Spatial Anchors no se puede ejecutar en Unity.</span><span class="sxs-lookup"><span data-stu-id="33175-154">Azure Spatial Anchors can not run in Unity.</span></span> <span data-ttu-id="33175-155">Por este motivo, para probar la funcionalidad de Azure Spatial Anchors, debe implementar el proyecto en un mínimo de dos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="33175-155">Consequently, to test the Azure Spatial Anchors functionality, you need to deploy the project to a minimum of two devices.</span></span>

<span data-ttu-id="33175-156">Si ahora compila e implementa el proyecto de Unity en dos dispositivos, puede lograr la alineación espacial entre ellos al compartir el id. de anclaje de Azure.</span><span class="sxs-lookup"><span data-stu-id="33175-156">If you now build and deploy the Unity project to two devices, you can achieve spatial alignment between the devices by sharing the Azure Anchor ID.</span></span> <span data-ttu-id="33175-157">Para probarlo, puedes seguir estos pasos:</span><span class="sxs-lookup"><span data-stu-id="33175-157">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="33175-158">En el dispositivo 1: **Inicie la aplicación** (se crea una instancia de Rover Explorer y se coloca en la tabla).</span><span class="sxs-lookup"><span data-stu-id="33175-158">On device 1: **Start the app** (the Rover Explorer is instantiated and placed on the table)</span></span>
2. <span data-ttu-id="33175-159">En el dispositivo 2: **Inicie la aplicación** (los dos usuarios ven la tabla con Rover Explorer, pero la tabla no aparece en el mismo lugar y los avatares del usuario no se muestran donde se encuentran los usuarios).</span><span class="sxs-lookup"><span data-stu-id="33175-159">On device 2: **Start the app** (both users see the table with the Rover Explorer, but the table does not appear in the same place, and the user avatars do not appear where the users are)</span></span>
3. <span data-ttu-id="33175-160">En el dispositivo 1: Presiona el botón **Start Azure Session** (Iniciar sesión de Azure).</span><span class="sxs-lookup"><span data-stu-id="33175-160">On device 1: Press the **Start Azure Session** button</span></span>
4. <span data-ttu-id="33175-161">En el dispositivo 1: Presiona el botón **Create Azure Anchor** (Crear anclaje de Azure) (crea el anclaje en la ubicación del objeto TableAnchor y almacena la información de dicho anclaje en el recurso de Azure).</span><span class="sxs-lookup"><span data-stu-id="33175-161">On device 1: Press the **Create Azure Anchor** button (creates anchor at the location of the TableAnchor object and stores the anchor information in the Azure resource).</span></span>
5. <span data-ttu-id="33175-162">En el dispositivo 1: Presiona el botón **Share Azure Anchor** (Compartir anclaje de Azure) (comparte el id. del anclaje con otros usuarios en tiempo real).</span><span class="sxs-lookup"><span data-stu-id="33175-162">On device 1: Press the **Share Azure Anchor** button (shares the anchor ID with other users in real-time)</span></span>
6. <span data-ttu-id="33175-163">En el dispositivo 2: Presiona el botón **Start Azure Session** (Iniciar sesión de Azure).</span><span class="sxs-lookup"><span data-stu-id="33175-163">On device 2: Press the **Start Azure Session** button</span></span>
7. <span data-ttu-id="33175-164">En el dispositivo 2: Presione el botón **Get Azure Anchor** (Obtener anclaje de Azure) (se conecta al recurso de Azure para recuperar la información del anclaje del identificador de anclaje compartido y, a continuación, mueve el objeto TableAnchor a la ubicación en la que se creó el anclaje con el dispositivo 1).</span><span class="sxs-lookup"><span data-stu-id="33175-164">On device 2: Press the **Get Azure Anchor** button (connects to the Azure resource to retrieve the anchor information for the shared anchor ID, then moves the TableAnchor object to the location where the anchor was created with the device 1)</span></span>

> [!TIP]
> <span data-ttu-id="33175-165">Si no tiene acceso a dos dispositivos de HoloLens, puede seguir el tutorial [Creación de instancias de Azure Spatial Anchors para dispositivos móviles](mr-learning-asa-05.md) para implementar el proyecto en su dispositivo móvil.</span><span class="sxs-lookup"><span data-stu-id="33175-165">If you don't have access to two HoloLens devices, you may follow the [Building Azure Spatial Anchors for mobile devices](mr-learning-asa-05.md) to deploy the project to your mobile device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="33175-166">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="33175-166">Congratulations</span></span>

<span data-ttu-id="33175-167">En este tutorial, has aprendido a integrar la instancia de Spatial Anchors eficaz de Azure para alinear dispositivos en una experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="33175-167">In this tutorial, you learned how to integrate Azure's powerful Spatial Anchors to align devices in a shared experience.</span></span>

<span data-ttu-id="33175-168">Con esto, damos por concluida la serie de tutoriales, en la que aprendió a configurar una cuenta de Photon, crear una aplicación de PUN, integrar PUN en un proyecto de Unity, configurar los avatares de usuario y los objetos compartidos y, por último, alinear varios participantes con Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="33175-168">This also concludes this tutorial series where you learned how to set up a Photon account, create a PUN app, integrate PUN into the Unity project, configure user avatars and shared objects, and finally align multiple participants using Azure Spatial Anchors.</span></span>
