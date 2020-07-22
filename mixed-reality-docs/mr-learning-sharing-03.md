---
title: 'Tutoriales sobre las funcionalidades multiusuario: 3. Conexión de varios usuarios'
description: Completa este curso para aprender a implementar experiencias compartidas con varios usuarios en una aplicación de HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 56bd4e251d11e39d5495d3fcaf4e3c5fc4e087de
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/14/2020
ms.locfileid: "86306731"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="5f25a-105">3. Conexión de varios usuarios</span><span class="sxs-lookup"><span data-stu-id="5f25a-105">3. Connecting multiple users</span></span>

<span data-ttu-id="5f25a-106">En este tutorial, aprenderás a conectar varios usuarios como parte de una experiencia compartida en directo.</span><span class="sxs-lookup"><span data-stu-id="5f25a-106">In this tutorial, you will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="5f25a-107">Al final del tutorial, podrá ejecutar la aplicación en varios dispositivos y hacer que todos los usuarios vean cómo se mueve el avatar de los demás en tiempo real.</span><span class="sxs-lookup"><span data-stu-id="5f25a-107">By the end of the tutorial, you will be able to run the app on multiple devices and have each user see the avatar of other users move in real-time.</span></span>

## <a name="objectives"></a><span data-ttu-id="5f25a-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="5f25a-108">Objectives</span></span>

* <span data-ttu-id="5f25a-109">Aprender a conectar varios usuarios en una experiencia compartida</span><span class="sxs-lookup"><span data-stu-id="5f25a-109">Learn how to connect multiple users in a shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="5f25a-110">Preparación de la escena</span><span class="sxs-lookup"><span data-stu-id="5f25a-110">Preparing the scene</span></span>

<span data-ttu-id="5f25a-111">En esta sección, agregarás algunos objetos prefabricados del tutorial para preparar la escena.</span><span class="sxs-lookup"><span data-stu-id="5f25a-111">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="5f25a-112">En la ventana Proyecto, navegue hasta **Assets** (Recursos)  > **MRTK.Tutorials.MultiUserCapabilities** > carpeta **Prefabs** (Recursos prefabricados) y, a continuación, haga clic y arrastre el siguiente objeto prefabricado a la ventana Jerarquía para agregarlos a la escena:</span><span class="sxs-lookup"><span data-stu-id="5f25a-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="5f25a-113">Objeto prefabricado **NetworkLobby**</span><span class="sxs-lookup"><span data-stu-id="5f25a-113">**NetworkLobby** prefab</span></span>
* <span data-ttu-id="5f25a-114">Objeto prefabricado **SharedPlayground**</span><span class="sxs-lookup"><span data-stu-id="5f25a-114">**SharedPlayground** prefab</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

<span data-ttu-id="5f25a-116">En la ventana Proyecto, desplácese hasta **Assets** (Recursos)  > **MRTK.Tutorials.AzureSpatialAnchors** > carpeta **Prefabs** (Recursos prefabricados) y haga clic y arrastre el siguiente objeto prefabricado a la ventana Jerarquía para agregarlo a la escena:</span><span class="sxs-lookup"><span data-stu-id="5f25a-116">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefab into the Hierarchy window to add it to your scene:</span></span>

* <span data-ttu-id="5f25a-117">Objeto prefabricado **DebugWindow**</span><span class="sxs-lookup"><span data-stu-id="5f25a-117">**DebugWindow** prefab</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a><span data-ttu-id="5f25a-119">Creación del elemento prefabricado del usuario</span><span class="sxs-lookup"><span data-stu-id="5f25a-119">Creating the user prefab</span></span>

<span data-ttu-id="5f25a-120">En esta sección, crearás un elemento prefabricado que se usará para representar a los usuarios en la experiencia compartida.</span><span class="sxs-lookup"><span data-stu-id="5f25a-120">In this section, you will create a prefab that will be used to represent the users in the shared experience.</span></span>

### <a name="1-create-and-configure-the-user"></a><span data-ttu-id="5f25a-121">1. Creación y configuración del usuario</span><span class="sxs-lookup"><span data-stu-id="5f25a-121">1. Create and configure the user</span></span>

<span data-ttu-id="5f25a-122">En la ventana Jerarquía, haz clic con el botón derecho en un área vacía y selecciona **Create Empty** (Crear vacío) para agregar un objeto vacío a la escena. Asigna al objeto el nombre **PhotonUser** y configúralo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="5f25a-122">In the Hierarchy window, right-click on an empty area and select **Create Empty** to add an empty object to your scene, name the object **PhotonUser**, and configure it as follows:</span></span>

* <span data-ttu-id="5f25a-123">Asegúrate de que el valor **Posición** de Transformación esté establecido en X = 0, Y = 0 y Z = 0:</span><span class="sxs-lookup"><span data-stu-id="5f25a-123">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-1.png)

<span data-ttu-id="5f25a-125">En la ventana Jerarquía, seleccione el objeto **PhotonUser**; después, en la ventana Inspector, usa el botón **Agregar componente** para agregar el componente **Photon User (Script)** (Usuario de Photon [script]) al objeto PhotonUser:</span><span class="sxs-lookup"><span data-stu-id="5f25a-125">In the Hierarchy window, select the **PhotonUser** object, then in the Inspector window, use the **Add Component** button to add the **Photon User (Script)** component to the PhotonUser object:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-2.png)

<span data-ttu-id="5f25a-127">En la ventana Inspector, usa el botón **Agregar componente** para agregar el componente **Generic Net Sync (Script)** (Sincronización neta genérica [script]) al objeto PhotonUser y configúralo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="5f25a-127">In the Inspector window, use the **Add Component** button to add the **Generic Net Sync (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="5f25a-128">Selecciona la casilla **Is User** (Es el usuario).</span><span class="sxs-lookup"><span data-stu-id="5f25a-128">Check the **Is User** checkbox</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-3.png)

<span data-ttu-id="5f25a-130">En la ventana Inspector, usa el botón **Agregar componente** para agregar el componente **Photon View (Script)** (Vista de Photon [script]) al objeto PhotonUser y configúralo de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="5f25a-130">In the Inspector window, use the **Add Component** button to add the **Photon View (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="5f25a-131">En el campo **Observed Components** (Componentes observados), asigne el componente **Generic Net Sync (Script)** (Sincronización neta genérica [script]).</span><span class="sxs-lookup"><span data-stu-id="5f25a-131">To the **Observed Components** field, assign the **Generic Net Sync (Script)** component</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step1-4.png)

### <a name="2-create-the-avatar"></a><span data-ttu-id="5f25a-133">2. Creación del avatar</span><span class="sxs-lookup"><span data-stu-id="5f25a-133">2. Create the avatar</span></span>

<span data-ttu-id="5f25a-134">En la ventana Proyecto, navegue hasta **Assets** (Recursos)  > **MRTK** > **SDK** > **StandardAssets** > carpeta **Materials** (Materiales) para buscar los materiales de MRTK.</span><span class="sxs-lookup"><span data-stu-id="5f25a-134">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Materials** folder to locate the MRTK materials.</span></span>

<span data-ttu-id="5f25a-135">Después, en la ventana Jerarquía, haga clic con el botón derecho en el objeto **PhotonUser** y seleccione **Objeto 3D** > **Esfera** para crear un objeto con forma de esfera como elemento secundario del objeto PhotonUser, y configúrelo de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="5f25a-135">Then, in the Hierarchy window, right-click on the **PhotonUser** object and select **3D Object** > **Sphere** to create a sphere object as a child of the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="5f25a-136">Asegúrate de que el valor **Posición** de Transformación esté establecido en X = 0, Y = 0 y Z = 0.</span><span class="sxs-lookup"><span data-stu-id="5f25a-136">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="5f25a-137">Cambia el valor **Escala** de Transformación a un tamaño adecuado; por ejemplo, X = 0,15, Y = 0,15 y Z = 0,15.</span><span class="sxs-lookup"><span data-stu-id="5f25a-137">Change the Transform **Scale** to a suitable size, for example, X = 0.15, Y = 0.15, Z = 0.15</span></span>
* <span data-ttu-id="5f25a-138">En el campo MeshRenderer > Materials (Materiales) > **Elemento 0**, asigne el material **MRTK_Standard_White**.</span><span class="sxs-lookup"><span data-stu-id="5f25a-138">To the MeshRenderer > Materials > **Element 0** field, assign the **MRTK_Standard_White** material</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step2-1.png)

### <a name="3-create-the-prefab"></a><span data-ttu-id="5f25a-140">3. Creación del elemento prefabricado</span><span class="sxs-lookup"><span data-stu-id="5f25a-140">3. Create the prefab</span></span>

<span data-ttu-id="5f25a-141">En la ventana Proyecto, navega hasta la carpeta **Recursos** > **MRTK.Tutorials.MultiUserCapabilities** > **Recursos**:</span><span class="sxs-lookup"><span data-stu-id="5f25a-141">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-1.png)

<span data-ttu-id="5f25a-143">Con la carpeta Recursos todavía seleccionada, **haz clic y arrastra** el objeto **PhotonUser** desde la ventana Jerarquía a la carpeta **Recursos** para convertir el objeto PhotonUser en un elemento prefabricado:</span><span class="sxs-lookup"><span data-stu-id="5f25a-143">With the Resources folder still selected, **click-and-drag** the **PhotonUser** object from the Hierarchy window into the **Resources** folder to make the PhotonUser object a prefab:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-2.png)

<span data-ttu-id="5f25a-145">En la ventana Jerarquía, haz clic con el botón derecho en el objeto **PhotonUser** y selecciona **Eliminar** para quitarlo de la escena:</span><span class="sxs-lookup"><span data-stu-id="5f25a-145">In the Hierarchy window, right-click on the **PhotonUser** object and select **Delete** to remove it from the scene:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a><span data-ttu-id="5f25a-147">Configuración de PUN para crear una instancia del elemento prefabricado del usuario</span><span class="sxs-lookup"><span data-stu-id="5f25a-147">Configuring PUN to instantiate the user prefab</span></span>

<span data-ttu-id="5f25a-148">En esta sección, configurarás el proyecto para usar el elemento prefabricado PhotonUser que creaste en la sección anterior.</span><span class="sxs-lookup"><span data-stu-id="5f25a-148">In this section, you will configure the project to use the PhotonUser prefab you created in the previous section.</span></span>

<span data-ttu-id="5f25a-149">En la ventana Proyecto, navega hasta la carpeta **Recursos** > **MRTK.Tutorials.MultiUserCapabilities** > **Recursos**.</span><span class="sxs-lookup"><span data-stu-id="5f25a-149">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="5f25a-150">En la ventana Jerarquía, expande el objeto **NetworkLobby** y selecciona el objeto secundario **NetworkRoom**. A continuación, en la ventana Inspector, busca el componente **Photon Room (Script)** (Sala de Photon [script]) y configúralo de la manera siguiente:</span><span class="sxs-lookup"><span data-stu-id="5f25a-150">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="5f25a-151">En el campo **Photon User Prefab** (Elemento prefabricado de usuario de Photon), asigna el elemento **PhotonUser** de la carpeta Recursos.</span><span class="sxs-lookup"><span data-stu-id="5f25a-151">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a><span data-ttu-id="5f25a-153">Prueba de la experiencia con varios usuarios</span><span class="sxs-lookup"><span data-stu-id="5f25a-153">Trying the experience with multiple users</span></span>

<span data-ttu-id="5f25a-154">Si ahora compila e implementa el proyecto de Unity en su dispositivo HoloLens, vuelva a Unity y entre en el Modo Juego. Mientras la aplicación se ejecuta en HoloLens, verá que el avatar de usuario de HoloLens se mueve cuando mueve la cabeza (HoloLens):</span><span class="sxs-lookup"><span data-stu-id="5f25a-154">If you now build and deploy the Unity project to your HoloLens, then, back in Unity, enter Game mode while the app is running on your HoloLens, you will see the HoloLens user avatar move when you move your head (HoloLens) around:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> <span data-ttu-id="5f25a-156">Para obtener un recordatorio sobre cómo compilar e implementar el proyecto de Unity en HoloLens 2, puede consultar las instrucciones de [Compilación de la aplicación para el HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="5f25a-156">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

> [!CAUTION]
> <span data-ttu-id="5f25a-157">La aplicación necesita conectarse a Photon, por lo que debe asegurarse de que el equipo o dispositivo esté conectado a Internet.</span><span class="sxs-lookup"><span data-stu-id="5f25a-157">The app needs to connect to Photon, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="5f25a-158">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="5f25a-158">Congratulations</span></span>

<span data-ttu-id="5f25a-159">Has configurado correctamente el proyecto para permitir que varios usuarios se conecten a la misma experiencia y vean los movimientos de los demás.</span><span class="sxs-lookup"><span data-stu-id="5f25a-159">You have successfully configured your project to allow multiple users to connect to the same experience and see each other's movements.</span></span> <span data-ttu-id="5f25a-160">En el siguiente tutorial, implementarás la funcionalidad para que los movimientos de objetos también se compartan entre varios dispositivos.</span><span class="sxs-lookup"><span data-stu-id="5f25a-160">In the next tutorial, you will implement functionality so that the movements of objects are also shared across multiple devices.</span></span>

[<span data-ttu-id="5f25a-161">Tutorial siguiente: 4. Uso compartido de movimientos de objetos con varios usuarios</span><span class="sxs-lookup"><span data-stu-id="5f25a-161">Next Tutorial: 4. Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
