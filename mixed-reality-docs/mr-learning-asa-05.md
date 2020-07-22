---
title: 'Tutoriales sobre Azure Spatial Anchors: 5. Azure Spatial Anchors para iOS y Android'
description: Complete este curso para aprender a implementar un proyecto de Unity con Mixed Reality Toolkit y Azure Spatial Anchors en Android e iOS.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens, android, ios
ms.localizationpriority: high
ms.openlocfilehash: e95b659eed3bfb406dcc41d5b3ad6e5e18c764a5
ms.sourcegitcommit: 96ae8258539b2f3edc104dd0dce8bc66f3647cdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/14/2020
ms.locfileid: "86305988"
---
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a><span data-ttu-id="ca4f0-105">5. Azure Spatial Anchors para iOS y Android</span><span class="sxs-lookup"><span data-stu-id="ca4f0-105">5. Azure Spatial Anchors for Android and iOS</span></span>

<span data-ttu-id="ca4f0-106">En este tutorial, aprenderás a compilar un proyecto en dispositivos iOS y Android con AR Foundation, y los complementos ARCore XR y ARKit XR.</span><span class="sxs-lookup"><span data-stu-id="ca4f0-106">In this tutorial, you will learn how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>

## <a name="objectives"></a><span data-ttu-id="ca4f0-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="ca4f0-107">Objectives</span></span>

* <span data-ttu-id="ca4f0-108">Aprender a compilar el proyecto en el dispositivo Android mediante AR Foundation y el complemento ARCore XR de Unity</span><span class="sxs-lookup"><span data-stu-id="ca4f0-108">Learn how to build your project to your Android device using Unity's AR Foundation and ARCore XR Plugin</span></span>
* <span data-ttu-id="ca4f0-109">Aprender a compilar el proyecto en su dispositivo iOS mediante AR Foundation y el complemento ARKit XR de Unity</span><span class="sxs-lookup"><span data-stu-id="ca4f0-109">Learn how to build your project to your iOS device using Unity's AR Foundation and ARKit XR Plugin</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="ca4f0-110">Instalación de paquetes de Unity integrados</span><span class="sxs-lookup"><span data-stu-id="ca4f0-110">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="ca4f0-111">En esta sección, actualizará e instalará los siguientes paquetes integrados:</span><span class="sxs-lookup"><span data-stu-id="ca4f0-111">In this section, you will upgrade and install the following inbuilt packages:</span></span>

* <span data-ttu-id="ca4f0-112">AR Foundation 3.1.3</span><span class="sxs-lookup"><span data-stu-id="ca4f0-112">AR Foundation 3.1.3</span></span>
* <span data-ttu-id="ca4f0-113">Legacy Input Helpers 2.1.4</span><span class="sxs-lookup"><span data-stu-id="ca4f0-113">Legacy Input Helpers 2.1.4</span></span>
* <span data-ttu-id="ca4f0-114">Complemento de ARCore XR 3.1.3 para la compatibilidad con Android</span><span class="sxs-lookup"><span data-stu-id="ca4f0-114">ARCore XR Plugin 3.1.3 for Android support</span></span>
* <span data-ttu-id="ca4f0-115">Complemento de ARKit XR 3.1.3 para la compatibilidad con iOS</span><span class="sxs-lookup"><span data-stu-id="ca4f0-115">ARKit XR plugin 3.1.3 for iOS support</span></span>

> [!CAUTION]
> <span data-ttu-id="ca4f0-116">No todas las versiones son compatibles con MRTK y solo algunas funcionan juntas, por lo que debe asegurarse de que instala las versiones exactas mencionadas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="ca4f0-116">Not all version are compatible with MRTK and only certain version works together, so make sure you install the exact versions listed above.</span></span>

<span data-ttu-id="ca4f0-117">En el menú de Unity, seleccione **Ventana** > **Administrador de paquetes** para abrir la ventana Package Manager (Administrador de paquetes) y, a continuación, seleccione **AR Foundation** > **3.1.3** y haga clic en el botón **Update to 3.1.3** (Actualizar a 3.1.3) para actualizar el paquete:</span><span class="sxs-lookup"><span data-stu-id="ca4f0-117">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** > **3.1.3** and click the **Update to 3.1.3** button to update the package:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section1-step1-1.png)

<span data-ttu-id="ca4f0-119">Siga el mismo proceso para importar los paquetes restantes según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="ca4f0-119">Follow the same process to import the remaining packages as needed.</span></span>

> [!NOTE]
> <span data-ttu-id="ca4f0-120">Si desarrollas este proyecto para Android, no es necesario instalar el paquete del complemento ARKit XR.</span><span class="sxs-lookup"><span data-stu-id="ca4f0-120">If you are developing this project for Android, there is no need to install the ARKit XR Plugin package.</span></span> <span data-ttu-id="ca4f0-121">Del mismo modo, si desarrollas este proyecto para iOS, no es necesario que instales el complemento de ARCore XR.</span><span class="sxs-lookup"><span data-stu-id="ca4f0-121">Similarly, if you are developing this project for iOS, you do not need to install the ARCore XR Plugin.</span></span>

## <a name="configure-mrtk-for-ar-foundation-camera"></a><span data-ttu-id="ca4f0-122">Configuración de MRTK para la cámara de AR Foundation</span><span class="sxs-lookup"><span data-stu-id="ca4f0-122">Configure MRTK for AR Foundation Camera</span></span>

<span data-ttu-id="ca4f0-123">En esta sección, obtendrá información sobre cómo configurar MRTK para realizar la implementación en un dispositivo móvil.</span><span class="sxs-lookup"><span data-stu-id="ca4f0-123">In this section, you will learn how to configure MRTK for deploying to a mobile device.</span></span>

<span data-ttu-id="ca4f0-124">En la ventana Hierarchy (Jerarquía), seleccione el objeto **MixedRealityToolkit**.</span><span class="sxs-lookup"><span data-stu-id="ca4f0-124">In the Hierarchy window, select the **MixedRealityToolkit** object.</span></span> <span data-ttu-id="ca4f0-125">A continuación, en la ventana Inspector, seleccione la pestaña **Camera** (Cámara), clone el perfil de la cámara y asígnele un nombre adecuado, por ejemplo, **AzureSpatialAnchors_ARCameraProfile**:</span><span class="sxs-lookup"><span data-stu-id="ca4f0-125">Then in the Inspector window, select the **Camera** tab, clone the camera profile, and give it a suitable name, for example, **AzureSpatialAnchors_ARCameraProfile**:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="ca4f0-127">Para obtener un recordatorio sobre cómo clonar perfiles de MRTK, puede consultar las instrucciones del artículo [Configuración de los perfiles de Mixed Reality Toolkit](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="ca4f0-127">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the Mixed Reality Toolkit profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="ca4f0-128">Con la pestaña **Camera** (Cámara) aún seleccionada en la ventana Inspector, expanda la opción **Camera Setting Providers** (Proveedores de configuración de la cámara), haga clic en el botón **+ Add Camera Setting Provider** (+ Agregar proveedor de configuración de la cámara) y, luego, expanda la opción **New data provider 1** (Nuevo proveedor de datos 1) recién agregada.</span><span class="sxs-lookup"><span data-stu-id="ca4f0-128">With the **Camera** tab still selected in the Inspector window, expand the **Camera Setting Providers** and click the **+ Add Camera Setting Provider** button, then expand the newly added **New data provider 1**:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-2.png)

<span data-ttu-id="ca4f0-130">Con la lista desplegable **Typo** (Tipo), cambie el tipo a **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:</span><span class="sxs-lookup"><span data-stu-id="ca4f0-130">Using the **Type** dropdown, change the type to **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-3.png)

<span data-ttu-id="ca4f0-132">En la ventana Hierarchy (Jerarquía), seleccione el objeto **RoverExplorer** y, a continuación, en la ventana Inspector, use el botón **Agregar componente** para agregar los componentes siguientes:</span><span class="sxs-lookup"><span data-stu-id="ca4f0-132">With the **MixedRealityToolkit** object still selected in the Hierarchy window, use the **Add Component** button in the Inspector window to add the following components:</span></span>

* <span data-ttu-id="ca4f0-133">AR Anchor Manager (Script) (Administrador de delimitadores de AR [script])</span><span class="sxs-lookup"><span data-stu-id="ca4f0-133">AR Anchor Manager (Script)</span></span>
* <span data-ttu-id="ca4f0-134">DisableDiagnosticsSystem (Script)</span><span class="sxs-lookup"><span data-stu-id="ca4f0-134">DisableDiagnosticsSystem (Script)</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="ca4f0-136">Cuando se agregue el componente AR Reference Point Manager (Script) (Administrador de puntos de referencia de AR [script]), se agregará automáticamente el componente AR Session Origin (Script) (Origen de la sesión de AR [script]) según lo requiere el componente AR Reference Point Manager (Script) (Administrador de puntos de referencia de AR [script]).</span><span class="sxs-lookup"><span data-stu-id="ca4f0-136">When you add the AR Reference Point Manager (Script) component, the AR Session Origin (Script) component is automatically added because it is required by the AR Reference Point Manager (Script) component.</span></span>

## <a name="building-your-application-to-your-android-device"></a><span data-ttu-id="ca4f0-137">Compilación de la aplicación en el dispositivo Android</span><span class="sxs-lookup"><span data-stu-id="ca4f0-137">Building your application to your Android device</span></span>

<span data-ttu-id="ca4f0-138">En esta sección, aprenderá a configurar el proyecto para compilarlo e implementarlo en un dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="ca4f0-138">In this section, you will learn how to configure your project to build and deploy it to an Android device.</span></span>

<span data-ttu-id="ca4f0-139">En el menú de Unity, seleccione **File** > **Build Settings...** (Archivo > Configuración de compilación) para abrir la ventana Build Settings (Configuración de compilación) y, luego, cambie la plataforma a Android.</span><span class="sxs-lookup"><span data-stu-id="ca4f0-139">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and then switch the platform to Android:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="ca4f0-141">Para obtener un recordatorio sobre cómo cambiar la plataforma de compilación, puede consultar las instrucciones del artículo [Cambio de la plataforma de compilación](mr-learning-base-02.md#switching-the-build-platform).</span><span class="sxs-lookup"><span data-stu-id="ca4f0-141">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="ca4f0-142">Cierre la ventana Build Settings (Configuración de compilación).</span><span class="sxs-lookup"><span data-stu-id="ca4f0-142">Close the Build Settings window.</span></span>

<span data-ttu-id="ca4f0-143">En el menú de Unity, seleccione **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality Toolkit > Utilidades > Configurar proyecto de Unity) para abrir la ventana **MRTK Project Configurator** (Configurador del proyecto MRTK). Asegúrese de que todas las opciones estén seleccionadas y, a continuación, haga clic en el botón **Apply** (Aplicar) para aplicar la configuración:</span><span class="sxs-lookup"><span data-stu-id="ca4f0-143">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-2.png)

<span data-ttu-id="ca4f0-145">En el menú de Unity, seleccione **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana Player Settings (Configuración del jugador). A continuación, busque la sección **Player** >  **Other Settings** (Jugador > Otra configuración), seleccione **Vulkan** y quítelo haciendo clic en el símbolo **"-"** .</span><span class="sxs-lookup"><span data-stu-id="ca4f0-145">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, select **Vulkan** and remove it by clicking the **"-"** symbol:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-3.png)

<span data-ttu-id="ca4f0-147">Cierra la ventana Player Settings (Configuración del reproductor) y vuelva a abrir la ventana Build Settings (Configuración de compilación).</span><span class="sxs-lookup"><span data-stu-id="ca4f0-147">Close the Player Settings window and open the Build Settings window again.</span></span>

<span data-ttu-id="ca4f0-148">En la ventana Configuración de compilación, haga clic en el botón **Add Open Scenes** (Agregar escenas abiertas) para agregar la escena actual a la lista **Scenes In Build** (Escenas de la compilación).</span><span class="sxs-lookup"><span data-stu-id="ca4f0-148">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list.</span></span> <span data-ttu-id="ca4f0-149">A continuación, use un cable USB, conecte el dispositivo Android al equipo y selecciónelo en la lista desplegable **Run Device** (Ejecutar dispositivo):</span><span class="sxs-lookup"><span data-stu-id="ca4f0-149">Then, use a USB cable, connect your Android device to your computer and select it from the **Run Device** dropdown:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> <span data-ttu-id="ca4f0-151">Si el dispositivo no aparece en la lista desplegable Run Device (Ejecutar dispositivo), puede que tenga que presionar el botón Refresh (Actualizar) situado junto a dicha lista.</span><span class="sxs-lookup"><span data-stu-id="ca4f0-151">If your device does not appear in the Run Device dropdown, you might need to press the Refresh button next to the dropdown.</span></span>

<span data-ttu-id="ca4f0-152">En la ventana Configuración de compilación, haga clic en el botón **Build and Run** (Compilar y ejecutar) para abrir la ventana Build Android (Compilar Android).</span><span class="sxs-lookup"><span data-stu-id="ca4f0-152">In the Build Settings window, click the **Build And Run** button to open the Build Android window.</span></span>

<span data-ttu-id="ca4f0-153">Elija una ubicación adecuada para almacenar la compilación, por ejemplo, _D:\MixedRealityLearning\Builds_, asigne a apk un nombre adecuado, por ejemplo, _MRTKTutorials-AzureSpatialAnchors_ y haga clic en el botón **Save** (Guardar) para iniciar el proceso de compilación:</span><span class="sxs-lookup"><span data-stu-id="ca4f0-153">Choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, then give the apk a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and click the **Save** button to start the build process:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
<span data-ttu-id="ca4f0-155">Si se produce algún error en la ventana Console (Consola) de Unity relacionado con los módulos SDK, NDK o JDK de Android, tienes que abrir Unity Hub e instalar los módulos asociados de compatibilidad con la compilación de Android.</span><span class="sxs-lookup"><span data-stu-id="ca4f0-155">If you get any error in the Unity Console window related to Android SDK, NDK, or JDK modules, you need to open Unity Hub and install the associated Android Build Support modules.</span></span>

<span data-ttu-id="ca4f0-156">Una vez que se complete el proceso de compilación, las aplicaciones deberían cargarse automáticamente en el dispositivo Android.</span><span class="sxs-lookup"><span data-stu-id="ca4f0-156">When the build process is complete, your apps should automatically load on your Android device.</span></span>

## <a name="building-your-application-to-your-ios-device"></a><span data-ttu-id="ca4f0-157">Compilación de la aplicación en el dispositivo iOS</span><span class="sxs-lookup"><span data-stu-id="ca4f0-157">Building your application to your iOS device</span></span>

<span data-ttu-id="ca4f0-158">En esta sección, aprenderá a configurar el proyecto para compilarlo e implementarlo en su dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="ca4f0-158">In this section, you will learn how to configure your project, to build and deploy it to your iOS device.</span></span>

<span data-ttu-id="ca4f0-159">En el menú de Unity, seleccione **File** > **Build Settings...** (Archivo > Configuración de compilación...) para abrir la ventana Build Settings (Configuración de compilación) y, luego, cambie la plataforma a iOS.</span><span class="sxs-lookup"><span data-stu-id="ca4f0-159">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window and switch platform to iOS:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="ca4f0-161">Para obtener un recordatorio sobre cómo cambiar la plataforma de compilación, puede consultar las instrucciones del artículo [Cambio de la plataforma de compilación](mr-learning-base-02.md#switching-the-build-platform).</span><span class="sxs-lookup"><span data-stu-id="ca4f0-161">For a reminder on how to switch build platform, you can refer to the [Switching the build platform](mr-learning-base-02.md#switching-the-build-platform) instructions.</span></span>

<span data-ttu-id="ca4f0-162">Cierre la ventana Build Settings (Configuración de compilación).</span><span class="sxs-lookup"><span data-stu-id="ca4f0-162">Close the Build Settings window.</span></span>

<span data-ttu-id="ca4f0-163">En el menú de Unity, seleccione **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality Toolkit > Utilidades > Configurar proyecto de Unity) para abrir la ventana **MRTK Project Configurator** (Configurador del proyecto MRTK). Asegúrese de que todas las opciones estén seleccionadas y, a continuación, haga clic en el botón **Apply** (Aplicar) para aplicar la configuración:</span><span class="sxs-lookup"><span data-stu-id="ca4f0-163">In the Unity menu, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open the **MRTK Project Configurator** window, ensure all options are selected, then click the **Apply** button to apply the settings:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-2.png)

<span data-ttu-id="ca4f0-165">En el menú de Unity, seleccione **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana Player Settings (Configuración del jugador). A continuación, busque la sección **Player** >  **Other Settings** (Jugador > Otra configuración) y desactive la casilla **Strip Engine Code** (Código del motor de franja).</span><span class="sxs-lookup"><span data-stu-id="ca4f0-165">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Other Settings** section, uncheck the **Strip Engine Code** checkbox to disable it:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-3.png)

<span data-ttu-id="ca4f0-167">Cierre la ventana Player Settings (Configuración del reproductor) y vuelva a abrir la ventana **Build Settings** (Configuración de compilación).</span><span class="sxs-lookup"><span data-stu-id="ca4f0-167">Close the Player Settings window and open the **Build Settings** window again.</span></span>

<span data-ttu-id="ca4f0-168">En la ventana Configuración de compilación, haga clic en el botón **Add Open Scenes** (Agregar escenas abiertas) para agregar la escena actual a la lista **Scenes In Build** (Escenas de la compilación):</span><span class="sxs-lookup"><span data-stu-id="ca4f0-168">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-4.png)

<span data-ttu-id="ca4f0-170">En la ventana Configuración de compilación, haga clic en el botón **Build** (Compilar) para abrir la ventana Build iOS (Compilar iOS).</span><span class="sxs-lookup"><span data-stu-id="ca4f0-170">In the Build Settings window, click the **Build** button to open the Build iOS window.</span></span>

<span data-ttu-id="ca4f0-171">Elija una ubicación adecuada para almacenar el proyecto Xcode, por ejemplo, _D:\MixedRealityLearning\Builds_, cree una carpeta nueva y asígnale un nombre adecuado, por ejemplo, _MRTKTutorials-AzureSpatialAnchors_ y, luego, haga clic en el botón **Select Folder** (Seleccionar carpeta) para iniciar el proceso de compilación:</span><span class="sxs-lookup"><span data-stu-id="ca4f0-171">Choose a suitable location to store your Xcode project, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _MRTKTutorials-AzureSpatialAnchors_, and then click the **Select Folder** button to start the build process:</span></span>

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-5.png)

<span data-ttu-id="ca4f0-173">Una vez completado el proceso de compilación, siga las instrucciones del artículo [Exportación del proyecto de Xcode](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) para aprender a implementar el proyecto de Xcode en el dispositivo iOS.</span><span class="sxs-lookup"><span data-stu-id="ca4f0-173">When the build process is complete, follow the [Export the Xcode project](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) instructions to learn to deploy your Xcode project to your iOS device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="ca4f0-174">Enhorabuena</span><span class="sxs-lookup"><span data-stu-id="ca4f0-174">Congratulations</span></span>

<span data-ttu-id="ca4f0-175">En este tutorial, ha aprendido a compilar un proyecto en dispositivos iOS y Android con AR Foundation, y los complementos ARCore XR y ARKit XR.</span><span class="sxs-lookup"><span data-stu-id="ca4f0-175">In this tutorial, you learned how to build your project to Android and iOS devices using AR Foundation, ARCore XR Plugin, and ARKit XR Plugin.</span></span>
