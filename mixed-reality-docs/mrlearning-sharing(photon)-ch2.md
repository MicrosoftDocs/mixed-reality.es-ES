---
title: 'Tutoriales sobre las funcionalidades multiusuario: 3. Conexión de varios usuarios'
description: Completa este curso para aprender a implementar experiencias compartidas con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: a597aadbddb49fefc824d8c5b5193585fa9476a5
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2020
ms.locfileid: "81610931"
---
# <a name="2-connecting-multiple-users"></a><span data-ttu-id="6cc2e-105">2. Conexión de varios usuarios</span><span class="sxs-lookup"><span data-stu-id="6cc2e-105">2. Connecting multiple users</span></span>

<span data-ttu-id="6cc2e-106">En este tutorial, aprenderás a conectar varios usuarios como parte de una experiencia compartida en directo.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-106">In this tutorial, you will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="6cc2e-107">Al final del tutorial, podrás ejecutar la aplicación en varios dispositivos y hacer que todos los usuarios vean cómo se mueve el avatar de los demás en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-107">By the end of the tutorial you will be able to run the application on multiple devices and have each user see the avatar of other users move in real-time.</span></span>

## <a name="objectives"></a><span data-ttu-id="6cc2e-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="6cc2e-108">Objectives</span></span>

* <span data-ttu-id="6cc2e-109">Aprender a conectar varios usuarios en una experiencia compartida</span><span class="sxs-lookup"><span data-stu-id="6cc2e-109">Learn how to connect multiple users in a shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="6cc2e-110">Preparación de la escena</span><span class="sxs-lookup"><span data-stu-id="6cc2e-110">Preparing the scene</span></span>

<span data-ttu-id="6cc2e-111">En esta sección, agregarás algunos objetos prefabricados del tutorial para preparar la escena.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-111">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="6cc2e-112">En la ventana Proyecto, navega hasta la carpeta **Recursos** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** (Elementos prefabricados).</span><span class="sxs-lookup"><span data-stu-id="6cc2e-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder.</span></span> <span data-ttu-id="6cc2e-113">Mientras mantienes presionado el botón CTRL, haz clic en **DebugWindow**, **NetworkLobby** y **SharedPlayground** para seleccionar los tres elementos prefabricados:</span><span class="sxs-lookup"><span data-stu-id="6cc2e-113">While holding down the CTRL button, click on **DebugWindow**, **NetworkLobby**, and **SharedPlayground** to select the three prefabs:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section1-step1-1.png)

<span data-ttu-id="6cc2e-115">Con los tres elementos prefabricados aún seleccionados, arrástralos a la ventana Jerarquía para agregarlos a la escena:</span><span class="sxs-lookup"><span data-stu-id="6cc2e-115">With the three prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a><span data-ttu-id="6cc2e-117">Creación del elemento prefabricado del usuario</span><span class="sxs-lookup"><span data-stu-id="6cc2e-117">Creating the user prefab</span></span>

<span data-ttu-id="6cc2e-118">En esta sección, crearás un elemento prefabricado que se usará para representar a los usuarios en la experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-118">In this section, you will create a prefab that will be used to represent the users in the shared experience.</span></span>

### <a name="1-create-and-configure-the-user"></a><span data-ttu-id="6cc2e-119">1. Creación y configuración del usuario</span><span class="sxs-lookup"><span data-stu-id="6cc2e-119">1. Create and configure the user</span></span>

<span data-ttu-id="6cc2e-120">En la ventana Jerarquía, haz clic con el botón derecho en un área vacía y selecciona **Create Empty** (Crear vacío) para agregar un objeto vacío a la escena. Asigna al objeto el nombre **PhotonUser** y configúralo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="6cc2e-120">In the Hierarchy window, right-click on an empty area and select **Create Empty** to add an empty object to your scene, name the object **PhotonUser**, and configure it as follows:</span></span>

* <span data-ttu-id="6cc2e-121">Asegúrate de que el valor **Posición** de Transformación esté establecido en X = 0, Y = 0 y Z = 0:</span><span class="sxs-lookup"><span data-stu-id="6cc2e-121">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-1.png)

<span data-ttu-id="6cc2e-123">Con el objeto **PhotonUser** aún seleccionado, en la ventana Inspector, usa el botón **Agregar componente** para agregar el componente **Photon User (Script)** (Usuario de Photon [script]) al objeto PhotonUser:</span><span class="sxs-lookup"><span data-stu-id="6cc2e-123">With the **PhotonUser** object still selected, in the Inspector window, use the **Add Component** button to add the **Photon User (Script)** component to the PhotonUser object:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-2.png)

<span data-ttu-id="6cc2e-125">En la ventana Inspector, usa el botón **Agregar componente** para agregar el componente **Generic Net Sync (Script)** (Sincronización neta genérica [script]) al objeto PhotonUser y configúralo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="6cc2e-125">In the Inspector window, use the **Add Component** button to add the **Generic Net Sync (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="6cc2e-126">Selecciona la casilla **Is User** (Es el usuario).</span><span class="sxs-lookup"><span data-stu-id="6cc2e-126">Check the **Is User** checkbox</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-3.png)

<span data-ttu-id="6cc2e-128">En la ventana Inspector, usa el botón **Agregar componente** para agregar el componente **Photon View (Script)** (Vista de Photon [script]) al objeto PhotonUser y configúralo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="6cc2e-128">In the Inspector window, use the **Add Component** button to add the **Photon View (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="6cc2e-129">En el campo **Observed Components** (Componentes observados), asigna el componente Generic Net Sync (Script) (Sincronización neta genérica [script]).</span><span class="sxs-lookup"><span data-stu-id="6cc2e-129">To the **Observed Components** field, assign the Generic Net Sync (Script) component</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step1-4.png)

### <a name="2-create-the-avatar"></a><span data-ttu-id="6cc2e-131">2. Creación del avatar</span><span class="sxs-lookup"><span data-stu-id="6cc2e-131">2. Create the avatar</span></span>

<span data-ttu-id="6cc2e-132">En la ventana Jerarquía, haz clic con el botón derecho en el objeto **PhotonUser**, selecciona **Objeto 3D** > **Esfera** para crear un objeto con forma de esfera como elemento secundario del objeto PhotonUser, y configúralo de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="6cc2e-132">In the Hierarchy window, right-click on the **PhotonUser** object and select **3D Object** > **Sphere** to create a sphere object as a child of the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="6cc2e-133">Asegúrate de que el valor **Posición** de Transformación esté establecido en X = 0, Y = 0 y Z = 0.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-133">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="6cc2e-134">Cambia el valor **Escala** de Transformación a un tamaño adecuado; por ejemplo, X = 0,15, Y = 0,15 y Z = 0,15.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-134">Change the Transform **Scale** to a suitable size, for example, X = 0.15, Y = 0.15, Z = 0.15</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step2-1.png)

### <a name="3-create-the-prefab"></a><span data-ttu-id="6cc2e-136">3. Creación del elemento prefabricado</span><span class="sxs-lookup"><span data-stu-id="6cc2e-136">3. Create the prefab</span></span>

<span data-ttu-id="6cc2e-137">En la ventana Proyecto, navega hasta la carpeta **Recursos** > **MRTK.Tutorials.MultiUserCapabilities** > **Recursos**:</span><span class="sxs-lookup"><span data-stu-id="6cc2e-137">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-1.png)

<span data-ttu-id="6cc2e-139">Con la carpeta Recursos todavía seleccionada, **haz clic y arrastra** el objeto **PhotonUser** desde la ventana Jerarquía a la carpeta **Recursos** para convertir el objeto PhotonUser en un elemento prefabricado:</span><span class="sxs-lookup"><span data-stu-id="6cc2e-139">With the Resources folder still selected, **click-and-drag** the **PhotonUser** object from the Hierarchy window into the **Resources** folder to make the PhotonUser object a prefab:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-2.png)

<span data-ttu-id="6cc2e-141">En la ventana Jerarquía, haz clic con el botón derecho en el objeto **PhotonUser** y selecciona **Eliminar** para quitarlo de la escena:</span><span class="sxs-lookup"><span data-stu-id="6cc2e-141">In the Hierarchy window, right-click on the **PhotonUser** object and select **Delete** to remove it from the scene:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a><span data-ttu-id="6cc2e-143">Configuración de PUN para crear una instancia del elemento prefabricado del usuario</span><span class="sxs-lookup"><span data-stu-id="6cc2e-143">Configuring PUN to instantiate the user prefab</span></span>

<span data-ttu-id="6cc2e-144">En esta sección, configurarás el proyecto para usar el elemento prefabricado PhotonUser que creaste en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-144">In this section, you will configure the project to use the PhotonUser prefab you created in the previous section.</span></span>

<span data-ttu-id="6cc2e-145">En la ventana Proyecto, navega hasta la carpeta **Recursos** > **MRTK.Tutorials.MultiUserCapabilities** > **Recursos**.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-145">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="6cc2e-146">En la ventana Jerarquía, expande el objeto **NetworkLobby** y selecciona el objeto secundario **NetworkRoom**. A continuación, en la ventana Inspector, busca el componente **Photon Room (Script)** (Sala de Photon [script]) y configúralo de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="6cc2e-146">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="6cc2e-147">En el campo **Photon User Prefab** (Elemento prefabricado de usuario de Photon), asigna el elemento **PhotonUser** de la carpeta Recursos.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-147">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a><span data-ttu-id="6cc2e-149">Prueba de la experiencia con varios usuarios</span><span class="sxs-lookup"><span data-stu-id="6cc2e-149">Trying the experience with multiple users</span></span>

<span data-ttu-id="6cc2e-150">Si ahora compilas e implementas el proyecto de Unity en tu dispositivo HoloLens y, después, vuelves a Unity, presiona el botón Reproducir para entrar en el Modo Juego. Mientras la aplicación se ejecuta en HoloLens, verás que el avatar de usuario de HoloLens se mueve cuando mueves la cabeza (HoloLens):</span><span class="sxs-lookup"><span data-stu-id="6cc2e-150">If you now build and deploy the Unity project to your HoloLens, and then, back in Unity, press the Play button to enter Game mode while the application is running on your HoloLens, you will see the HoloLens user avatar move when you move your head (HoloLens) around:</span></span>

![mrlearning-sharing](images/mrlearning-sharing/tutorial2-section4-step1-1.gif)

> [!TIP]
> <span data-ttu-id="6cc2e-152">Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puedes consultar las instrucciones de [Compilación de la aplicación para el dispositivo](mrlearning-base-ch1.md#build-your-application-to-your-device).</span><span class="sxs-lookup"><span data-stu-id="6cc2e-152">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Build your application to your device](mrlearning-base-ch1.md#build-your-application-to-your-device) instructions.</span></span>

> [!CAUTION]
> <span data-ttu-id="6cc2e-153">La aplicación necesita conectarse a Photon, por lo que debes asegurarte de que el equipo o dispositivo está conectado a Internet.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-153">The application needs to connect to Photon, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="6cc2e-154">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="6cc2e-154">Congratulations</span></span>

<span data-ttu-id="6cc2e-155">Has configurado correctamente el proyecto para permitir que varios usuarios se conecten a la misma experiencia y vean los movimientos de los demás.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-155">You have successfully configured your project to allow multiple users to connect to the same experience and see each other's movements.</span></span> <span data-ttu-id="6cc2e-156">En el siguiente tutorial, implementarás la funcionalidad para que los movimientos de objetos también se compartan entre varios dispositivos.</span><span class="sxs-lookup"><span data-stu-id="6cc2e-156">In the next tutorial, you will implement functionality so that the movements of objects are also shared across multiple devices.</span></span>

<span data-ttu-id="6cc2e-157">[Tutorial siguiente: 2. Uso compartido de movimientos de objetos con varios usuarios](mrlearning-sharing(photon)-ch3.md)</span><span class="sxs-lookup"><span data-stu-id="6cc2e-157">[Next tutorial: 2. Sharing object movements with multiple users](mrlearning-sharing(photon)-ch3.md)</span></span>
