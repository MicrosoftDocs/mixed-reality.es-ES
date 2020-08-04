---
title: 'Tutoriales sobre las funcionalidades multiusuario: 4. Uso compartido de movimientos de objetos con varios usuarios'
description: Completa este curso para aprender a implementar experiencias compartidas con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7dbe25cd1b0329e366fcbd567074018025032f9e
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376567"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="896da-105">4. Uso compartido de movimientos de objetos con varios usuarios</span><span class="sxs-lookup"><span data-stu-id="896da-105">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="896da-106">En este tutorial, aprenderá a compartir los movimientos de objetos para que todos los participantes de una experiencia compartida puedan colaborar y ver las interacciones de los demás.</span><span class="sxs-lookup"><span data-stu-id="896da-106">In this tutorial, you will learn how to share the movements of objects so that all participants of a shared experience can collaborate and view each other's interactions.</span></span>

## <a name="objectives"></a><span data-ttu-id="896da-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="896da-107">Objectives</span></span>

* <span data-ttu-id="896da-108">Configurar el proyecto para compartir los movimientos de los objetos</span><span class="sxs-lookup"><span data-stu-id="896da-108">Configure your project to share the movements of objects</span></span>
* <span data-ttu-id="896da-109">Aprender a crear una aplicación de colaboración de varios usuarios básica</span><span class="sxs-lookup"><span data-stu-id="896da-109">Learn how to build a basic multi-user collaborative app</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="896da-110">Preparación de la escena</span><span class="sxs-lookup"><span data-stu-id="896da-110">Preparing the scene</span></span>

<span data-ttu-id="896da-111">En esta sección, agregaras elementos prefabricados del tutorial para preparar la escena.</span><span class="sxs-lookup"><span data-stu-id="896da-111">In this section, you will prepare the scene by adding the tutorial prefab.</span></span>

<span data-ttu-id="896da-112">En la ventana Project (Proyecto), vaya a la carpeta **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** y arrastre el elemento prefabricado **TableAnchor** para colocarlo encima del objeto **SharedPlayground** de la ventana Hierarchy (Jerarquía) y agregarlo a la escena como elemento secundario del objeto SharedPlayground:</span><span class="sxs-lookup"><span data-stu-id="896da-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **TableAnchor** prefab onto the **SharedPlayground** object in the Hierarchy window to add it to your scene as a child of the SharedPlayground object:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a><span data-ttu-id="896da-114">Configuración de PUN para crear instancias de los objetos</span><span class="sxs-lookup"><span data-stu-id="896da-114">Configuring PUN to instantiate the objects</span></span>

<span data-ttu-id="896da-115">En esta sección, configurará el proyecto para usar la experiencia Rover Explorer creada durante los [tutoriales de introducción](mr-learning-base-01.md) y definirá dónde se crearán las instancias.</span><span class="sxs-lookup"><span data-stu-id="896da-115">In this section, you will configure the project to use the Rover Explorer experience created during the [Getting started tutorials](mr-learning-base-01.md) and define where it will be instantiated.</span></span>

<span data-ttu-id="896da-116">En la ventana Proyecto, navega hasta la carpeta **Recursos** > **MRTK.Tutorials.MultiUserCapabilities** > **Recursos**.</span><span class="sxs-lookup"><span data-stu-id="896da-116">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="896da-117">En la ventana Jerarquía, expande el objeto **NetworkLobby** y selecciona el objeto secundario **NetworkRoom**. A continuación, en la ventana Inspector, busca el componente **Photon Room (Script)** (Sala de Photon [script]) y configúralo de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="896da-117">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="896da-118">En el campo **Rover Explorer Prefab** (Elemento prefabricado de explorador rover), asigne el elemento prefabricado **RoverExplorer_Complete_Variant** desde la carpeta de recursos.</span><span class="sxs-lookup"><span data-stu-id="896da-118">To the **Rover Explorer Prefab** field, assign the **RoverExplorer_Complete_Variant** prefab from the Resources folder</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section2-step1-1.png)

<span data-ttu-id="896da-120">Con el objeto secundario **NetworkLobby** seleccionado, en la ventana Jerarquía, expande el objeto **TableAnchor**. A continuación, en la ventana Inspector, busca el componente **Photon Room (Script)** (Sala de Photon [script]) y configúralo de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="896da-120">With the **NetworkRoom** child object still selected, in the Hierarchy window, expand the **TableAnchor** object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="896da-121">En el campo **Rover Explorer Location** (Ubicación del explorador rover), asigne el objeto secundario TableAnchor > **Table** (Tabla) desde la ventana Hierarchy (Jerarquía).</span><span class="sxs-lookup"><span data-stu-id="896da-121">To the **Rover Explorer Location** field, assign the TableAnchor > **Table** child object from the Hierarchy window</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a><span data-ttu-id="896da-123">Prueba de la experiencia con el movimiento de objetos compartidos</span><span class="sxs-lookup"><span data-stu-id="896da-123">Trying the experience with shared object movement</span></span>

<span data-ttu-id="896da-124">Si ahora compila e implementa el proyecto de Unity en su dispositivo HoloLens y, después, vuelve a Unity, presione el botón Reproducir para entrar en el modo de juego. Mientras la aplicación se ejecuta en HoloLens, verá que el objeto se mueve en Unity cuando lo mueve en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="896da-124">If you now build and deploy the Unity project to your HoloLens, and then, back in Unity, press the Play button to enter Game mode while the app is running on your HoloLens, you will see the object move in Unity when you move the object in HoloLens:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section3-step1-1.gif)

## <a name="congratulations"></a><span data-ttu-id="896da-126">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="896da-126">Congratulations</span></span>

<span data-ttu-id="896da-127">Ha configurado correctamente el proyecto para que los movimientos de los objetos se sincronicen y los usuarios puedan ver que los objetos se mueven cuando otros usuarios los mueven.</span><span class="sxs-lookup"><span data-stu-id="896da-127">You have successfully configured your project to synchronize object movements so users can see the objects move when other users move them.</span></span> <span data-ttu-id="896da-128">En el siguiente tutorial, implementará la funcionalidad para alinear la experiencia en el mundo físico.</span><span class="sxs-lookup"><span data-stu-id="896da-128">In the next tutorial, you will implement functionality to align the experience in the physical world.</span></span> <span data-ttu-id="896da-129">Esto garantizará que los usuarios se vean entre sí en su ubicación física real y, por tanto, los objetos aparezcan en la misma posición y rotación física para todos los usuarios.</span><span class="sxs-lookup"><span data-stu-id="896da-129">This will ensure the users see each other in their actual physical location, and so the objects appear in the same physical position and rotation for all users.</span></span>

[<span data-ttu-id="896da-130">Tutorial siguiente: 5. Integración de Azure Spatial Anchors en una experiencia compartida</span><span class="sxs-lookup"><span data-stu-id="896da-130">Next Tutorial: 5. Integrating Azure Spatial Anchors into a shared experience</span></span>](mr-learning-sharing-05.md)
