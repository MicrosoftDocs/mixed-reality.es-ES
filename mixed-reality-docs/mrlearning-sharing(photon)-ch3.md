---
title: 'Tutoriales sobre las funcionalidades multiusuario: 4. Uso compartido de movimientos de objetos con varios usuarios'
description: Completa este curso para aprender a implementar experiencias compartidas con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 41b62eb2d9f400d0af341c9fcce887c72af7a3aa
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610618"
---
# <a name="3-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="5308d-105">3. Uso compartido de movimientos de objetos con varios usuarios</span><span class="sxs-lookup"><span data-stu-id="5308d-105">3. Sharing object movements with multiple users</span></span>

<span data-ttu-id="5308d-106">En este tutorial, aprenderás a compartir los movimientos de objetos para que todos los participantes de una experiencia compartida puedan colaborar y ver las interacciones de los demás.</span><span class="sxs-lookup"><span data-stu-id="5308d-106">In this tutorial, you will learn how to share the movements of objects so that all participants of a shared experience can collaborate and view each others' interactions.</span></span>

## <a name="objectives"></a><span data-ttu-id="5308d-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="5308d-107">Objectives</span></span>

* <span data-ttu-id="5308d-108">Configurar el proyecto para compartir los movimientos de los objetos</span><span class="sxs-lookup"><span data-stu-id="5308d-108">Configure your project to share the movements of objects</span></span>
* <span data-ttu-id="5308d-109">Aprender a crear una aplicación de colaboración de varios usuarios básica</span><span class="sxs-lookup"><span data-stu-id="5308d-109">Learn how to build a basic multi-user collaborative application</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="5308d-110">Preparación de la escena</span><span class="sxs-lookup"><span data-stu-id="5308d-110">Preparing the scene</span></span>

<span data-ttu-id="5308d-111">En esta sección, agregaras elementos prefabricados del tutorial para preparar la escena.</span><span class="sxs-lookup"><span data-stu-id="5308d-111">In this section, you will prepare the scene by adding the tutorial prefab.</span></span>

<span data-ttu-id="5308d-112">En la ventana Proyecto, navega hasta la carpeta **Recursos** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Elementos prefabricados) y arrastra el elemento prefabricado **TableAnchor** para colocarlo encima del objeto **SharedPlayground** de la ventana Jerarquía y agregarlo a la escena como elemento secundario del objeto SharedPlayground:</span><span class="sxs-lookup"><span data-stu-id="5308d-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **TableAnchor** prefab on top of the **SharedPlayground** object in the Hierarchy window to add it to your scene as a child of the SharedPlayground object:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a><span data-ttu-id="5308d-114">Configuración de PUN para crear instancias de los objetos</span><span class="sxs-lookup"><span data-stu-id="5308d-114">Configuring PUN to instantiate the objects</span></span>

<span data-ttu-id="5308d-115">En esta sección, configurarás el proyecto para usar el elemento prefabricado RocketLauncher_Complete_Variant creado en la sección anterior y definir el lugar en el que se creará una instancia de este.</span><span class="sxs-lookup"><span data-stu-id="5308d-115">In this section, you will configure the project to use the RocketLauncher_Complete_Variant prefab you created in the previous section and define where it will be instantiated.</span></span>

<span data-ttu-id="5308d-116">En la ventana Proyecto, navega hasta la carpeta **Recursos** > **MRTK.Tutorials.MultiUserCapabilities** > **Recursos**.</span><span class="sxs-lookup"><span data-stu-id="5308d-116">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="5308d-117">En la ventana Jerarquía, expande el objeto **NetworkLobby** y selecciona el objeto secundario **NetworkRoom**. A continuación, en la ventana Inspector, busca el componente **Photon Room (Script)** (Sala de Photon [script]) y configúralo de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="5308d-117">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="5308d-118">En el campo **Photon User Prefab** (Elemento prefabricado de usuario de Photon), asigna el elemento **PhotonUser** de la carpeta Recursos.</span><span class="sxs-lookup"><span data-stu-id="5308d-118">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-1.png)

<span data-ttu-id="5308d-120">Con el objeto secundario **NetworkLobby** seleccionado, en la ventana Jerarquía, expande el objeto **TableAnchor**. A continuación, en la ventana Inspector, busca el componente **Photon Room (Script)** (Sala de Photon [script]) y configúralo de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="5308d-120">With the **NetworkRoom** child object still selected, in the Hierarchy window, expand the **TableAnchor** object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="5308d-121">En el campo **Rocket Launcher Location** (Ubicación del iniciador de Rocket), asigna el objeto secundario **Table** desde la ventana Jerarquía.</span><span class="sxs-lookup"><span data-stu-id="5308d-121">To the **Rocket Launcher Location** field, assign the **Table** child object from the Hierarchy window</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a><span data-ttu-id="5308d-123">Prueba de la experiencia con el movimiento de objetos compartidos</span><span class="sxs-lookup"><span data-stu-id="5308d-123">Trying the experience with shared object movement</span></span>

<span data-ttu-id="5308d-124">Si ahora compilas e implementas el proyecto de Unity en tu dispositivo HoloLens y, después, vuelves a Unity, presiona el botón Reproducir para entrar en el Modo Juego. Mientras la aplicación se ejecuta en HoloLens, verás que el objeto se mueve en Unity cuando lo mueves en HoloLens:</span><span class="sxs-lookup"><span data-stu-id="5308d-124">If you now build and deploy the Unity project to your HoloLens, and then, back in Unity, press the Play button to enter Game mode while the application is running on your HoloLens, you will see the object move in Unity when you move the object in HoloLens:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial3-section3-step1-1.gif)

## <a name="congratulations"></a><span data-ttu-id="5308d-126">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="5308d-126">Congratulations</span></span>

<span data-ttu-id="5308d-127">Has configurado correctamente el proyecto para que los movimientos de los objetos se sincronicen y los usuarios puedan ver cuándo otros usuarios mueven los objetos.</span><span class="sxs-lookup"><span data-stu-id="5308d-127">You have successfully configured your project so object movements are synchronized and users can see the objects move when other users move the objects.</span></span> <span data-ttu-id="5308d-128">En el siguiente tutorial, implementarás la funcionalidad para que la experiencia compartida se alinee con el mundo físico y los usuarios se vean entre sí en su ubicación física real, y para que los objetos se muestren en la misma posición física y rotación para todos los usuarios.</span><span class="sxs-lookup"><span data-stu-id="5308d-128">In the next tutorial, you will implement functionality so the shared experience is aligned in the physical world and the users see each other in their actual physical location and so the objects appear in the same physical position and rotation for all users.</span></span>

<span data-ttu-id="5308d-129">[Tutorial siguiente: 4. Integración de Azure Spatial Anchors en una experiencia compartida](mrlearning-sharing(photon)-ch4.md)</span><span class="sxs-lookup"><span data-stu-id="5308d-129">[Next tutorial: 4. Integrating Azure Spatial Anchors into a shared experience](mrlearning-sharing(photon)-ch4.md)</span></span>
