---
title: 'Tutoriales sobre Azure Spatial Anchors: 4. Azure Spatial Anchors para iOS y Android'
description: Sigue este tutorial para aprender a implementar Azure Spatial Anchors dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/18/2020
ms.topic: article
keywords: realidad mixta, unity, tutorial, curso, hololens, azure, spatial anchors
ms.localizationpriority: high
ms.openlocfilehash: 78fa6a2cdd29bd424ec3016a5467760063b87a14
ms.sourcegitcommit: 7011ac6fde80e5c45f04192fa1db6e1eb559e3b0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/03/2020
ms.locfileid: "84327952"
---
# <a name="4-azure-spatial-anchors-for-android-and-ios"></a><span data-ttu-id="946d2-105">4. Azure Spatial Anchors para iOS y Android</span><span class="sxs-lookup"><span data-stu-id="946d2-105">4. Azure Spatial Anchors for Android and iOS</span></span>

<span data-ttu-id="946d2-106">En este tutorial, aprenderás a compilar un proyecto en dispositivos iOS y Android con AR Foundation, y los complementos ARCore XR y ARKit XR.</span><span class="sxs-lookup"><span data-stu-id="946d2-106">In this tutorial, you will learn how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

## <a name="objectives"></a><span data-ttu-id="946d2-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="946d2-107">Objectives</span></span>

* <span data-ttu-id="946d2-108">Aprender a compilar un proyecto en un dispositivo Android mediante AR Foundation y el complemento ARCore XR de Unity.</span><span class="sxs-lookup"><span data-stu-id="946d2-108">Learn how to build your project to Android device using Unity AR Foundation and ARCore XR Plugin.</span></span>
* <span data-ttu-id="946d2-109">Aprender a compilar un proyecto en un dispositivo iOS mediante AR Foundation y el complemento ARKit XR de Unity.</span><span class="sxs-lookup"><span data-stu-id="946d2-109">Learn how to build your project to an iOS device using Unity AR Foundation and ARKit XR Plugin.</span></span>

> [!NOTE]
> <span data-ttu-id="946d2-110">Para completar este tutorial, asegúrate de haber completado los tutoriales de Azure Spatial Anchors > [Introducción a Azure Spatial Anchors](mrlearning-asa-ch1.md).</span><span class="sxs-lookup"><span data-stu-id="946d2-110">To complete this tutorial, make sure you have completed Azure Spatial Anchors Tutorials -> [Getting started with Azure Spatial Anchors](mrlearning-asa-ch1.md).</span></span>

## <a name="adding-inbuilt-unity-packages"></a><span data-ttu-id="946d2-111">Adición de paquetes de Unity integrados</span><span class="sxs-lookup"><span data-stu-id="946d2-111">Adding inbuilt Unity packages</span></span>

<span data-ttu-id="946d2-112">En esta sección, instalará los paquetes integrados de AR Foundation, el complemento ARCore XR y el complemento ARKit XR de Unity necesarios para admitir dispositivos iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="946d2-112">In this section, you will install Unity inbuilt AR Foundation, ARCore XR Plugin, and ARKit XR Plugin packages required to support Android and iOS devices.</span></span>

<span data-ttu-id="946d2-113">Asegúrate de instalar la versión correcta de estos paquetes de Unity como se indica a continuación:</span><span class="sxs-lookup"><span data-stu-id="946d2-113">Make sure you install the correct version of these Unity packages as listed below:</span></span>

* <span data-ttu-id="946d2-114">**AR Foundation 2.1.4**</span><span class="sxs-lookup"><span data-stu-id="946d2-114">**AR Foundation 2.1.4**</span></span>
* <span data-ttu-id="946d2-115">**ARCore XR plugin 2.2.0, preview 2**</span><span class="sxs-lookup"><span data-stu-id="946d2-115">**ARCore XR plugin 2.2.0 preview 2**</span></span>
* <span data-ttu-id="946d2-116">**ARKit XR plugin 2.1.1**</span><span class="sxs-lookup"><span data-stu-id="946d2-116">**ARKit XR plugin 2.1.1**</span></span>

> [!NOTE]
> <span data-ttu-id="946d2-117">Si desarrollas este proyecto para Android, no es necesario instalar el paquete del complemento ARKit XR.</span><span class="sxs-lookup"><span data-stu-id="946d2-117">If you are developing this project for Android, there is no need to install the ARKit XR Plugin package.</span></span> <span data-ttu-id="946d2-118">Del mismo modo, si desarrollas este proyecto para iOS, no es necesario que instales el complemento de ARCore XR.</span><span class="sxs-lookup"><span data-stu-id="946d2-118">Similarly, if you are developing this project for iOS, you do not need to install the ARCore XR Plugin.</span></span>

<span data-ttu-id="946d2-119">En el menú de Unity, selecciona **Window** > **Package Manager** (Ventana > Administrador de paquetes):</span><span class="sxs-lookup"><span data-stu-id="946d2-119">In the Unity menu, select **Window** > **Package Manager**:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-1.png)

<span data-ttu-id="946d2-121">Los paquetes pueden tardar unos segundos en aparecer en la lista.</span><span class="sxs-lookup"><span data-stu-id="946d2-121">It might take a few seconds before all packages appear in the list.</span></span> <span data-ttu-id="946d2-122">Para mostrar los paquetes de versión preliminar, haga clic en la opción de opciones avanzadas y seleccione **Show preview packages** (Mostrar paquetes en versión preliminar).</span><span class="sxs-lookup"><span data-stu-id="946d2-122">Display preview packages by clicking on Advanced option and select **Show preview packages.**</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-2.png)

<span data-ttu-id="946d2-124">En la ventana del administrador de paquetes, seleccione **AR Foundation**, aquí verá muchas versiones y tendrá que seleccionar la **versión 2.1.4** y actualizar el paquete haciendo clic en el botón **Update to 2.1.4** (Actualizar a 2.1.4):</span><span class="sxs-lookup"><span data-stu-id="946d2-124">In the Package Manager window, select **AR Foundation**, here you see many version and need to select **version 2.1.4** and update the package by clicking the **Update to 2.1.4** button:</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-3.png)

<span data-ttu-id="946d2-126">Para admitir dispositivos Android, siga el mismo proceso para importar **ARCore XR Plugin 2.2.0, preview 2**.</span><span class="sxs-lookup"><span data-stu-id="946d2-126">To support Android devices, follow the same process to import **ARCore XR Plugin 2.2.0 preview 2**.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-4.png)

<span data-ttu-id="946d2-128">Para admitir dispositivos iOS, tienes que importar el paquete **ARKit XR plugin 2.1.1** de Unity de Package Manager.</span><span class="sxs-lookup"><span data-stu-id="946d2-128">To support iOS devices, you should import the **ARKit XR plugin 2.1.1** Unity package from the Package Manager.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-5.png)

## <a name="customize-mrtk-to-support-ar-foundation-camera"></a><span data-ttu-id="946d2-130">Personalización de MRTK para admitir la cámara de AR Foundation</span><span class="sxs-lookup"><span data-stu-id="946d2-130">Customize MRTK to support AR Foundation camera</span></span>

<span data-ttu-id="946d2-131">Para personalizar la configuración de MRTK para que admita AR Foundation, selecciona MixedRealityToolKit en la ventana Hierarchy (Jerarquía) y haz clic en el botón **Clone** (Clonar) en el kit de herramientas de realidad mixta en la ventana Inspector.</span><span class="sxs-lookup"><span data-stu-id="946d2-131">Customize MRTK settings to support AR Foundation by selecting MixedRealityToolKit in the Hierarchy window and click the **Clone** button in Mixed Reality ToolKit in the Inspector window.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-1.png)

<span data-ttu-id="946d2-133">Al hacer clic en el botón **Clonar** (Clonar), aparecerá una nueva ventana para clonar perfiles, vuelva a hacer clic en el botón **Clone** (Clonar) para clonar **DefaultMixedRealityToolkitProfile**.</span><span class="sxs-lookup"><span data-stu-id="946d2-133">When you click the **Clone** button, a new clone Profile window will appear, click on the **Clone** button again to clone the **DefaultMixedRealityToolkitProfile**.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-2.png)

<span data-ttu-id="946d2-135">Del mismo modo, clone el **Camera Profile** (Perfil de cámara) en la ventana Inspector.</span><span class="sxs-lookup"><span data-stu-id="946d2-135">Similarly, clone the **Camera Profile** in the Inspector window.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-3.png)

<span data-ttu-id="946d2-137">En la ventana Inspector, busque MixedReality y seleccione la pestaña **Camera** (Cámara). Expanda los proveedores de configuración de la cámara en la ventana Inspector y haga clic en **+Add Camera Setting Provider** (+ Agregar proveedor de configuración de cámara) > expanda **New data provider 1** (Nuevo proveedor de datos 1) > seleccione el tipo **None** (Ninguno) > seleccione **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > seleccione **UnityARCameraSettings**.</span><span class="sxs-lookup"><span data-stu-id="946d2-137">In the Inspector window, locate the MixedReality, select the **Camera** tab. Expand the camera setting providers in the inspector window and click on **+ Add Camera Setting Provider** > expand **New data provider 1** > select type **None** > select **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > select **UnityARCameraSettings**.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-4.png)

<span data-ttu-id="946d2-139">Con el objeto MixedRealityToolKit seleccionado en la ventana de jerarquía, en la ventana Inspector, adjunte scripts auxiliares haciendo clic en el botón **Add component** (Agregar componente) y escriba "AR Reference Point Manager" y seleccione el script.</span><span class="sxs-lookup"><span data-stu-id="946d2-139">With the MixedRealityToolKit object selected in the Hierarchy window, In the Inspector window, attach supporting scripts by clicking on the **Add component** button and type in AR reference Point manager and select the script.</span></span>

<span data-ttu-id="946d2-140">Al agregar el script **AR Reference Point Manager**, se agregará automáticamente **AR session origin** a la ventana Inspector.</span><span class="sxs-lookup"><span data-stu-id="946d2-140">Adding the  **AR Reference Point Manager** script will automatically add **AR session origin** to the Inspector window.</span></span> <span data-ttu-id="946d2-141">Después de agregar los scripts auxiliares, la ventana Inspector debería tener este aspecto.</span><span class="sxs-lookup"><span data-stu-id="946d2-141">After adding the supporting scripts, the Inspector window should look like this.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-5.png)

## <a name="build-an-application-to-an-android-device"></a><span data-ttu-id="946d2-143">Compilación de una aplicación en un dispositivo Android</span><span class="sxs-lookup"><span data-stu-id="946d2-143">Build an application to an Android device</span></span>

<span data-ttu-id="946d2-144">Para compilar esta aplicación en un dispositivo Android, haz clic en **File** (Archivo) en la parte superior de la ventana y selecciona **Build Settings** (Configuración de compilación).</span><span class="sxs-lookup"><span data-stu-id="946d2-144">To build this application to your Android device, click on **File** at the top of the window and select **Build Settings.**</span></span> <span data-ttu-id="946d2-145">Aparecerá una nueva ventana en la pantalla, seleccione **Android** y haga clic en **Switch Platform** (Cambiar plataforma).</span><span class="sxs-lookup"><span data-stu-id="946d2-145">A new window will appear on the screen, select **Android**, and click on the **Switch Platform**.</span></span> <span data-ttu-id="946d2-146">La plataforma tardará unos minutos en cambiar.</span><span class="sxs-lookup"><span data-stu-id="946d2-146">It will take a few minutes to switch platform.</span></span> <span data-ttu-id="946d2-147">Después de cambiar a la plataforma Android, haz clic en **Add Open Scenes** (Agregar escenas abiertas) y asegúrate de que la escena actual sea la única seleccionada en la lista **Scenes In Build** (Escenas de la compilación).</span><span class="sxs-lookup"><span data-stu-id="946d2-147">After switching to the Android platform, click on **Add Open Scenes** and make sure your current scene is the only selected scene in the **Scenes In Build** list.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-1.png)

<span data-ttu-id="946d2-149">Cierra la ventana **Build Settings** (Configuración de compilación).</span><span class="sxs-lookup"><span data-stu-id="946d2-149">Close the **Build Settings** window.</span></span> <span data-ttu-id="946d2-150">En el menú de Unity, seleccione Mixed Reality Toolkit > Utilities > Configure Unity Project (Mixed Reality Toolkit > Utilidades > Configurar proyecto de Unity) y haga clic en **Apply** (Aplicar) para configurar el proyecto de Unity para la plataforma Android.</span><span class="sxs-lookup"><span data-stu-id="946d2-150">In the Unity menu, select Mixed Reality Toolkit > Utilities > Configure Unity Project and click on **Apply** to configure the Unity project for the Android platform.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-2.png)

<span data-ttu-id="946d2-152">En el menú de Unity, selecciona **Edit** > **Project Settings** (Editar > Configuración del proyecto) para abrir la ventana Project Settings (Configuración del proyecto):</span><span class="sxs-lookup"><span data-stu-id="946d2-152">In the Unity menu, select **Edit** > **Project Settings** to open the Project Settings window.</span></span> <span data-ttu-id="946d2-153">En la ventana de configuración del proyecto, seleccione la pestaña **Player** (Reproductor), expanda la sección **Other Settings** (Otras opciones de configuración), seleccione **Vulkan**, y quítela haciendo clic en el símbolo " **-** ".</span><span class="sxs-lookup"><span data-stu-id="946d2-153">In the Project Settings, window selects the **Player** tab, expand the **Other Settings** section, select **Vulkan**, and remove it by clicking the "**-**" symbol.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-3.png)

<span data-ttu-id="946d2-155">Cierre la ventana **Player Settings** (Configuración del reproductor) y vuelva a abrir la ventana **Build Settings** (Configuración de compilación).</span><span class="sxs-lookup"><span data-stu-id="946d2-155">Close the **Player Settings** window and open the **Build Settings** window again.</span></span> <span data-ttu-id="946d2-156">A continuación, con un cable USB, conecte el dispositivo Android al equipo y seleccione el dispositivo en la lista desplegable **Build and Run** (Compilar y ejecutar) y, a continuación, haga clic en **Build and Run** (Compilar y ejecutar).</span><span class="sxs-lookup"><span data-stu-id="946d2-156">Then, using a USB cable, connect your Android device to your computer and select your device in the **Build and Run** on the dropdown, then click **Build And Run**.</span></span> <span data-ttu-id="946d2-157">Se te pedirá que guardes un archivo .apk, para el cual puedes elegir cualquier nombre.</span><span class="sxs-lookup"><span data-stu-id="946d2-157">You will be asked to save a .apk file, which you can pick any name.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-4.png)

> [!NOTE]
> <span data-ttu-id="946d2-159">Si se produce algún error en la ventana Console (Consola) de Unity relacionado con los módulos SDK, NDK o JDK de Android, tienes que abrir Unity Hub e instalar los módulos SDK, NDK y JDK asociados para el módulo de compatibilidad con la compilación de Android.</span><span class="sxs-lookup"><span data-stu-id="946d2-159">If you get any error in the Unity Console window related to Android SDK, NDK, and or JDK modules, you need to open Unity Hub and install the associated SDK, NDK, and JDK modules for the Android Build Support module.</span></span>

<span data-ttu-id="946d2-160">Una vez que se complete el proceso de compilación, las aplicaciones deberían cargarse automáticamente en el dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="946d2-160">When the build process is complete, your applications should automatically load on your Android device.</span></span>

## <a name="build-an-application-to-ios-device"></a><span data-ttu-id="946d2-161">Compilación de una aplicación en un dispositivo iOS</span><span class="sxs-lookup"><span data-stu-id="946d2-161">Build an application to iOS Device</span></span>

<span data-ttu-id="946d2-162">Para compilar esta aplicación en un dispositivo iOS, haz clic en **File** (Archivo) en la parte superior de la ventana y selecciona **Build Settings** (Configuración de compilación).</span><span class="sxs-lookup"><span data-stu-id="946d2-162">To build this application to your iOS device, click on **File** at the top of the window and select **Build Settings.**</span></span> <span data-ttu-id="946d2-163">Aparecerá una nueva ventana en la pantalla, selecciona **iOS** y haz clic en **Switch Platform** (Cambiar plataforma).</span><span class="sxs-lookup"><span data-stu-id="946d2-163">A new window will appear on the screen, then select **iOS** and click on the **Switch Platform**.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-1.png)

<span data-ttu-id="946d2-165">Cierra la ventana **Build Settings** (Configuración de compilación).</span><span class="sxs-lookup"><span data-stu-id="946d2-165">Close the **Build Settings** window.</span></span> <span data-ttu-id="946d2-166">En el menú de Unity, seleccione Mixed Reality Toolkit > Utilities > Configure Unity Project (Mixed Reality Toolkit > Utilidades > Configurar proyecto de Unity) y haga clic en **Apply** (Aplicar) para configurar el proyecto de Unity para la plataforma iOS.</span><span class="sxs-lookup"><span data-stu-id="946d2-166">In the Unity menu, select Mixed Reality Toolkit > Utilities > Configure Unity Project, and click on **Apply** to configure the Unity project for the iOS platform.</span></span>

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-2.png)

<span data-ttu-id="946d2-168">Para compilar el proyecto XCode de iOS, vaya a la configuración de la compilación y haga clic en **Build** (Compilar).</span><span class="sxs-lookup"><span data-stu-id="946d2-168">To build the iOS XCode project, go to Build Settings, and click on **Build**.</span></span>

<span data-ttu-id="946d2-169">Sigue [esta guía](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) para aprender a implementar este proyecto en tu dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="946d2-169">Follow [this guide](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) to learn how to deploy this project to your iOS device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="946d2-170">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="946d2-170">Congratulations</span></span>

<span data-ttu-id="946d2-171">En este tutorial, has aprendido a compilar un proyecto para dispositivos iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="946d2-171">In this tutorial, you learned how to build your project for Android and iOS devices.</span></span> <span data-ttu-id="946d2-172">También has aprendido a usar AR Foundation, el complemento ARCore XR y el complemento ARKit XR para que tu proyecto funcione en dispositivos iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="946d2-172">You also learned how to use AR Foundation, ARCore XR Plugin, and ARKit XR Plugin to make your project work for Android and iOS devices.</span></span>
