---
title: 'Tutoriales sobre las funcionalidades multiusuario: 5. Integración de Azure Spatial Anchors en una experiencia compartida'
description: Completa este curso para aprender a implementar experiencias compartidas con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: c27ed7327cfe0a61f2b63e309348bdea1a535ea1
ms.sourcegitcommit: 92ff5478a5c55b4e2c5cc2f44f1588702f4ec5d1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2020
ms.locfileid: "82604976"
---
# <a name="4-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="afbbb-105">4. Integración de Azure Spatial Anchors en una experiencia compartida</span><span class="sxs-lookup"><span data-stu-id="afbbb-105">4. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="afbbb-106">En este tutorial, aprenderás a integrar Azure Spatial Anchors (ASA) en la experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="afbbb-106">In this tutorial, you will learn how to integrate Azure Spatial Anchors (ASA) into the shared experience.</span></span> <span data-ttu-id="afbbb-107">ASA permite que varios dispositivos tengan una referencia común al mundo físico para que los usuarios se vean entre sí en su ubicación física real y vean la experiencia compartida en el mismo lugar.</span><span class="sxs-lookup"><span data-stu-id="afbbb-107">ASA allows multiple devices to have a common reference to the physical world so that the users see each other in their actual physical location and see the shared experience in the same place.</span></span>

## <a name="objectives"></a><span data-ttu-id="afbbb-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="afbbb-108">Objectives</span></span>

* <span data-ttu-id="afbbb-109">Integración de ASA en una experiencia compartida para la alineación de varios dispositivos</span><span class="sxs-lookup"><span data-stu-id="afbbb-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
* <span data-ttu-id="afbbb-110">Aprende los aspectos básicos del funcionamiento de ASA en el contexto de una experiencia compartida local.</span><span class="sxs-lookup"><span data-stu-id="afbbb-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="afbbb-111">Preparación de la escena</span><span class="sxs-lookup"><span data-stu-id="afbbb-111">Preparing the scene</span></span>

<span data-ttu-id="afbbb-112">En la ventana Jerarquía, expande el objeto **SharedPlayground** y, a continuación, expande el objeto **TableAnchor** para exponer sus objetos secundarios:</span><span class="sxs-lookup"><span data-stu-id="afbbb-112">In the Hierarchy window, expand the **SharedPlayground** object, then expand the **TableAnchor** object to expose its child objects:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section1-step1-1.png)

<span data-ttu-id="afbbb-114">En la ventana Proyecto, navega hasta la carpeta **Recursos** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Elementos prefabricados) y arrastra el elemento prefabricado **Buttons** para colocarlo encima del objeto secundario **TableAnchor** de la ventana Jerarquía y agregarlo a la escena como elemento secundario del objeto TableAnchor:</span><span class="sxs-lookup"><span data-stu-id="afbbb-114">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **Buttons** prefab on top of the **TableAnchor** child object in the Hierarchy window to add it to your scene as a child of the TableAnchor object:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="afbbb-116">Configuración de los botones para el funcionamiento de la escena</span><span class="sxs-lookup"><span data-stu-id="afbbb-116">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="afbbb-117">En esta sección, configurarás una serie de eventos de botón que muestran los aspectos básicos de cómo se puede usar Azure Spatial Anchors para lograr la alineación espacial en una experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="afbbb-117">In this section, you will configure a series of button events that demonstrate the fundamentals of how Azure Spatial Anchors can be used to achieve spatial alignment in a shared experience.</span></span>

<span data-ttu-id="afbbb-118">En la ventana Jerarquía, expande el objeto **Button** y selecciona el primer objeto de botón secundario denominado **StartAzureSession**:</span><span class="sxs-lookup"><span data-stu-id="afbbb-118">In the Hierarchy window, expand the **Button** object and select the first child button object named **StartAzureSession**:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-1.png)

<span data-ttu-id="afbbb-120">En la ventana Inspector, busca el componente **Interactable (Script)** (Interactivo [script]) y configura el evento **OnClick ()** como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="afbbb-120">In the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="afbbb-121">En el campo **None (Object)** (Ninguno [objeto]), asigna el objeto **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="afbbb-121">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="afbbb-122">En el menú desplegable **Ninguna función**, selecciona la función **AnchorModuleScript** > **StartAzureSession ()** .</span><span class="sxs-lookup"><span data-stu-id="afbbb-122">From **No Function** dropdown, select the **AnchorModuleScript** > **StartAzureSession ()** function</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-2.png)

<span data-ttu-id="afbbb-124">En la ventana Jerarquía, selecciona el segundo objeto de botón secundario denominado **CreateAzureAnchor** y, a continuación, en la ventana Inspector, busca el componente **Interactable (Script)** (Interactivo [script]) y configura el evento **OnClick ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="afbbb-124">In the Hierarchy window, select the second child button object named **CreateAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="afbbb-125">En el campo **None (Object)** (Ninguno [objeto]), asigna el objeto **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="afbbb-125">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="afbbb-126">En el menú desplegable **Ninguna función**, selecciona la función **AnchorModuleScript** > **CreateAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="afbbb-126">From **No Function** dropdown, select the **AnchorModuleScript** > **CreateAzureAnchor ()** function</span></span>
* <span data-ttu-id="afbbb-127">En el nuevo campo **None (Game Object)** (Ninguno [objeto de juego]) que aparece, asigna el objeto **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="afbbb-127">To the new **None (Game Object)** field that appears, assign the **TableAnchor** object</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-3.png)

<span data-ttu-id="afbbb-129">En la ventana Jerarquía, selecciona el tercer objeto de botón secundario denominado **ShareAzureAnchor** y, a continuación, en la ventana Inspector, busca el componente **Interactable (Script)** (Interactivo [script]) y configura el evento **OnClick ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="afbbb-129">In the Hierarchy window, select the third child button object named **ShareAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="afbbb-130">En el campo **None (Object)** (Ninguno [objeto]), asigna el objeto **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="afbbb-130">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="afbbb-131">En el menú desplegable **Ninguna función**, selecciona la función **SharingModuleScript** > **ShareAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="afbbb-131">From **No Function** dropdown, select the **SharingModuleScript** > **ShareAzureAnchor ()** function</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-4.png)

<span data-ttu-id="afbbb-133">En la ventana Jerarquía, selecciona el cuarto objeto de botón secundario denominado **GetAzureAnchor** y, a continuación, en la ventana Inspector, busca el componente **Interactable (Script)** (Interactivo [script]) y configura el evento **OnClick ()** de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="afbbb-133">In the Hierarchy window, select the forth child button object named **GetAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="afbbb-134">En el campo **None (Object)** (Ninguno [objeto]), asigna el objeto **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="afbbb-134">To **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="afbbb-135">En el menú desplegable **Ninguna función**, selecciona la función **SharingModuleScript** > **GetAzureAnchor ()** .</span><span class="sxs-lookup"><span data-stu-id="afbbb-135">From **No Function** dropdown, select the **SharingModuleScript** > **GetAzureAnchor ()** function</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="afbbb-137">Conexión de la escena al recurso de Azure</span><span class="sxs-lookup"><span data-stu-id="afbbb-137">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="afbbb-138">En la ventana Jerarquía, expande el objeto **SharedPlayground** y, a continuación, selecciona el objeto **TableAnchor**.</span><span class="sxs-lookup"><span data-stu-id="afbbb-138">In the Hierarchy window, expand the **SharedPlayground** object and select the **TableAnchor** object.</span></span> <span data-ttu-id="afbbb-139">A continuación, en la ventana Inspector, busca el componente **Spatial Anchor Manager (Script)** (Administrador de anclaje espacial [script]) y configura la sección **Credenciales** con las credenciales de la cuenta de Azure Spatial Anchors creada como parte de los [requisitos previos](mrlearning-sharing(photon)-ch1.md#prerequisites) de esta serie de tutoriales:</span><span class="sxs-lookup"><span data-stu-id="afbbb-139">Then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component and configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mrlearning-sharing(photon)-ch1.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="afbbb-140">En el campo **Spatial Anchors Account ID** (Id. de la cuenta de Spatial Anchors), pega el valor **Id. de cuenta** de la cuenta de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="afbbb-140">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="afbbb-141">En el campo **Spatial Anchors Account ID** (Id. de la cuenta de Spatial Anchors), pega la **clave de acceso** primaria o secundaria de la cuenta de Azure Spatial Anchors.</span><span class="sxs-lookup"><span data-stu-id="afbbb-141">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section3-step1-1.png)

<span data-ttu-id="afbbb-143">Con el objeto **TableAnchor** todavía seleccionado, en la ventana Inspector, asegúrate de que todos los componentes de script estén habilitados:</span><span class="sxs-lookup"><span data-stu-id="afbbb-143">With the **TableAnchor** object still selected, in the Inspector window, make sure all the script components are enabled:</span></span>

* <span data-ttu-id="afbbb-144">Selecciona la casilla situada junto a **Spatial Anchor Manager (Script)** (Spatial Anchor Manager [script]) para habilitarla.</span><span class="sxs-lookup"><span data-stu-id="afbbb-144">Check the checkbox next to the **Spatial Anchor Manager (Script)** components to enable it</span></span>
* <span data-ttu-id="afbbb-145">Selecciona la casilla situada junto al componente **Anchor Module Script (Script)** (Script del módulo de anclaje [script]) para habilitarla.</span><span class="sxs-lookup"><span data-stu-id="afbbb-145">Check the checkbox next to the **Anchor Module Script (Script)** components to enable it</span></span>
* <span data-ttu-id="afbbb-146">Selecciona la casilla situada junto al componente **Sharing Module Script (Script)** (Script del módulo de uso compartido [script]) para habilitarla.</span><span class="sxs-lookup"><span data-stu-id="afbbb-146">Check the checkbox next to the **Sharing Module Script (Script)** components to enable it</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial4-section3-step1-2.png)

## <a name="trying-the-experience-with-spatial-alignment"></a><span data-ttu-id="afbbb-148">Prueba de la experiencia con la alineación espacial</span><span class="sxs-lookup"><span data-stu-id="afbbb-148">Trying the experience with spatial alignment</span></span>

> [!NOTE]
> <span data-ttu-id="afbbb-149">Azure Spatial Anchors no se puede ejecutar en Unity.</span><span class="sxs-lookup"><span data-stu-id="afbbb-149">Azure Spatial Anchors can not run in Unity.</span></span> <span data-ttu-id="afbbb-150">Por este motivo, para probar la funcionalidad de Azure Spatial Anchors, debes implementar el proyecto en un mínimo de dos dispositivos HoloLens.</span><span class="sxs-lookup"><span data-stu-id="afbbb-150">Consequently, to test the Azure Spatial Anchors functionality, you need to deploy the project to a minimum of two HoloLens devices.</span></span>

<span data-ttu-id="afbbb-151">Si ahora compilas e implementas el proyecto de Unity en dos dispositivos HoloLens, puedes lograr la alineación espacial entre ellos al compartir el identificador de anclaje de Azure.</span><span class="sxs-lookup"><span data-stu-id="afbbb-151">If you now build and deploy the Unity project to two HoloLens devices, you can achieve spatial alignment between the devices by sharing the Azure Anchor ID.</span></span> <span data-ttu-id="afbbb-152">Para probarlo, puedes seguir estos pasos:</span><span class="sxs-lookup"><span data-stu-id="afbbb-152">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="afbbb-153">En el dispositivo HoloLens 1: **Inicia la aplicación** (se crea una instancia del iniciador de Rocket y se coloca en la tabla).</span><span class="sxs-lookup"><span data-stu-id="afbbb-153">On HoloLens device 1: **Start the application** (the Rocket Launcher is instantiated and placed on the table)</span></span>
2. <span data-ttu-id="afbbb-154">En el dispositivo HoloLens 2: **Inicia la aplicación** (los dos usuarios ven la tabla con el iniciador de Rocket, sin embargo, la tabla no aparece en el mismo lugar y los avatares del usuario no se muestran donde se encuentran los usuarios).</span><span class="sxs-lookup"><span data-stu-id="afbbb-154">On HoloLens device 2: **Start the application** (both users see the table with the Rocket Launcher, however, the table does not appear in the same place and the user avatars do not appear where the users are)</span></span>
3. <span data-ttu-id="afbbb-155">En el dispositivo HoloLens 1: Presiona el botón **Start Azure Session** (Iniciar sesión de Azure).</span><span class="sxs-lookup"><span data-stu-id="afbbb-155">On HoloLens device 1: Press the **Start Azure Session** button</span></span>
4. <span data-ttu-id="afbbb-156">En el dispositivo HoloLens 1: Presiona el botón **Create Azure Anchor** (Crear anclaje de Azure) (crea el anclaje en la ubicación del objeto TableAnchor y almacena la información de dicho anclaje en el recurso de Azure).</span><span class="sxs-lookup"><span data-stu-id="afbbb-156">On HoloLens device 1: Press the **Create Azure Anchor** button (creates anchor at the location of the TableAnchor object and stores the anchor information in the Azure resource).</span></span>
5. <span data-ttu-id="afbbb-157">En el dispositivo HoloLens 1: Presiona el botón **Share Azure Anchor** (Compartir anclaje de Azure) (comparte el id. del anclaje con otros usuarios en tiempo real).</span><span class="sxs-lookup"><span data-stu-id="afbbb-157">On HoloLens device 1: Press the **Share Azure Anchor** button (shares the anchor ID with other users in real-time)</span></span>
6. <span data-ttu-id="afbbb-158">En el dispositivo HoloLens 2: Presiona el botón **Start Azure Session** (Iniciar sesión de Azure).</span><span class="sxs-lookup"><span data-stu-id="afbbb-158">On HoloLens device 2: Press the **Start Azure Session** button</span></span>
7. <span data-ttu-id="afbbb-159">En el dispositivo HoloLens 2: Presiona el botón **Get Azure Anchor** (Obtener el anclaje de Azure) (se conecta al recurso de Azure para recuperar la información del anclaje del identificador del anclaje compartido y, a continuación, mueve el objeto TableAnchor a la ubicación en la que se creó el anclaje con el dispositivo HoloLens 1).</span><span class="sxs-lookup"><span data-stu-id="afbbb-159">On HoloLens device 2: Press the **Get Azure Anchor** button (connects to the Azure resource to retrieve the anchor information for the shared anchor ID, then moves the TableAnchor object to the location where the anchor was created with the HoloLens device 1)</span></span>

## <a name="congratulations"></a><span data-ttu-id="afbbb-160">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="afbbb-160">Congratulations</span></span>

<span data-ttu-id="afbbb-161">En este tutorial, has aprendido a integrar la instancia de Spatial Anchors eficaz de Azure para alinear dispositivos en una experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="afbbb-161">In this tutorial, you learned how to integrate Azure's powerful Spatial Anchors to align devices in a shared experience.</span></span> <span data-ttu-id="afbbb-162">Con esto, damos por concluida la serie de tutoriales, en la que has aprendido a configurar una cuenta y una aplicación de Photon, integrar Photon y PUN en una aplicación de Unity, configurar los avatares de usuario y los objetos compartidos y, por último, alinear varios participantes con ASA.</span><span class="sxs-lookup"><span data-stu-id="afbbb-162">This also concludes this tutorial series where you have learned how to set up a Photon account and application, integrate Photon and PUN into a Unity application, configure user avatars and shared objects, and finally align multiple participants using ASA.</span></span>
