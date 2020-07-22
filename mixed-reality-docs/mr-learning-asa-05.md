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
# <a name="5-azure-spatial-anchors-for-android-and-ios"></a>5. Azure Spatial Anchors para iOS y Android

En este tutorial, aprenderás a compilar un proyecto en dispositivos iOS y Android con AR Foundation, y los complementos ARCore XR y ARKit XR.

## <a name="objectives"></a>Objetivos

* Aprender a compilar el proyecto en el dispositivo Android mediante AR Foundation y el complemento ARCore XR de Unity
* Aprender a compilar el proyecto en su dispositivo iOS mediante AR Foundation y el complemento ARKit XR de Unity

## <a name="installing-inbuilt-unity-packages"></a>Instalación de paquetes de Unity integrados

En esta sección, actualizará e instalará los siguientes paquetes integrados:

* AR Foundation 3.1.3
* Legacy Input Helpers 2.1.4
* Complemento de ARCore XR 3.1.3 para la compatibilidad con Android
* Complemento de ARKit XR 3.1.3 para la compatibilidad con iOS

> [!CAUTION]
> No todas las versiones son compatibles con MRTK y solo algunas funcionan juntas, por lo que debe asegurarse de que instala las versiones exactas mencionadas anteriormente.

En el menú de Unity, seleccione **Ventana** > **Administrador de paquetes** para abrir la ventana Package Manager (Administrador de paquetes) y, a continuación, seleccione **AR Foundation** > **3.1.3** y haga clic en el botón **Update to 3.1.3** (Actualizar a 3.1.3) para actualizar el paquete:

![mr-learning-asa](images/mr-learning-asa/asa-05-section1-step1-1.png)

Siga el mismo proceso para importar los paquetes restantes según sea necesario.

> [!NOTE]
> Si desarrollas este proyecto para Android, no es necesario instalar el paquete del complemento ARKit XR. Del mismo modo, si desarrollas este proyecto para iOS, no es necesario que instales el complemento de ARCore XR.

## <a name="configure-mrtk-for-ar-foundation-camera"></a>Configuración de MRTK para la cámara de AR Foundation

En esta sección, obtendrá información sobre cómo configurar MRTK para realizar la implementación en un dispositivo móvil.

En la ventana Hierarchy (Jerarquía), seleccione el objeto **MixedRealityToolkit**. A continuación, en la ventana Inspector, seleccione la pestaña **Camera** (Cámara), clone el perfil de la cámara y asígnele un nombre adecuado, por ejemplo, **AzureSpatialAnchors_ARCameraProfile**:

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-1.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo clonar perfiles de MRTK, puede consultar las instrucciones del artículo [Configuración de los perfiles de Mixed Reality Toolkit](mr-learning-base-03.md).

Con la pestaña **Camera** (Cámara) aún seleccionada en la ventana Inspector, expanda la opción **Camera Setting Providers** (Proveedores de configuración de la cámara), haga clic en el botón **+ Add Camera Setting Provider** (+ Agregar proveedor de configuración de la cámara) y, luego, expanda la opción **New data provider 1** (Nuevo proveedor de datos 1) recién agregada.

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-2.png)

Con la lista desplegable **Typo** (Tipo), cambie el tipo a **Microsoft.MixedReality.Toolkit.Experimental.UnityAR** > **UnityARCameraSettings**:

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-3.png)

En la ventana Hierarchy (Jerarquía), seleccione el objeto **RoverExplorer** y, a continuación, en la ventana Inspector, use el botón **Agregar componente** para agregar los componentes siguientes:

* AR Anchor Manager (Script) (Administrador de delimitadores de AR [script])
* DisableDiagnosticsSystem (Script)

![mr-learning-asa](images/mr-learning-asa/asa-05-section2-step1-4.png)

> [!NOTE]
> Cuando se agregue el componente AR Reference Point Manager (Script) (Administrador de puntos de referencia de AR [script]), se agregará automáticamente el componente AR Session Origin (Script) (Origen de la sesión de AR [script]) según lo requiere el componente AR Reference Point Manager (Script) (Administrador de puntos de referencia de AR [script]).

## <a name="building-your-application-to-your-android-device"></a>Compilación de la aplicación en el dispositivo Android

En esta sección, aprenderá a configurar el proyecto para compilarlo e implementarlo en un dispositivo Android.

En el menú de Unity, seleccione **File** > **Build Settings...** (Archivo > Configuración de compilación) para abrir la ventana Build Settings (Configuración de compilación) y, luego, cambie la plataforma a Android.

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-1.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo cambiar la plataforma de compilación, puede consultar las instrucciones del artículo [Cambio de la plataforma de compilación](mr-learning-base-02.md#switching-the-build-platform).

Cierre la ventana Build Settings (Configuración de compilación).

En el menú de Unity, seleccione **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality Toolkit > Utilidades > Configurar proyecto de Unity) para abrir la ventana **MRTK Project Configurator** (Configurador del proyecto MRTK). Asegúrese de que todas las opciones estén seleccionadas y, a continuación, haga clic en el botón **Apply** (Aplicar) para aplicar la configuración:

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-2.png)

En el menú de Unity, seleccione **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana Player Settings (Configuración del jugador). A continuación, busque la sección **Player** >  **Other Settings** (Jugador > Otra configuración), seleccione **Vulkan** y quítelo haciendo clic en el símbolo **"-"** .

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-3.png)

Cierra la ventana Player Settings (Configuración del reproductor) y vuelva a abrir la ventana Build Settings (Configuración de compilación).

En la ventana Configuración de compilación, haga clic en el botón **Add Open Scenes** (Agregar escenas abiertas) para agregar la escena actual a la lista **Scenes In Build** (Escenas de la compilación). A continuación, use un cable USB, conecte el dispositivo Android al equipo y selecciónelo en la lista desplegable **Run Device** (Ejecutar dispositivo):

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-4.png)

>[!NOTE]
> Si el dispositivo no aparece en la lista desplegable Run Device (Ejecutar dispositivo), puede que tenga que presionar el botón Refresh (Actualizar) situado junto a dicha lista.

En la ventana Configuración de compilación, haga clic en el botón **Build and Run** (Compilar y ejecutar) para abrir la ventana Build Android (Compilar Android).

Elija una ubicación adecuada para almacenar la compilación, por ejemplo, _D:\MixedRealityLearning\Builds_, asigne a apk un nombre adecuado, por ejemplo, _MRTKTutorials-AzureSpatialAnchors_ y haga clic en el botón **Save** (Guardar) para iniciar el proceso de compilación:

![mr-learning-asa](images/mr-learning-asa/asa-05-section3-step1-5.png)

> [!NOTE]
Si se produce algún error en la ventana Console (Consola) de Unity relacionado con los módulos SDK, NDK o JDK de Android, tienes que abrir Unity Hub e instalar los módulos asociados de compatibilidad con la compilación de Android.

Una vez que se complete el proceso de compilación, las aplicaciones deberían cargarse automáticamente en el dispositivo Android.

## <a name="building-your-application-to-your-ios-device"></a>Compilación de la aplicación en el dispositivo iOS

En esta sección, aprenderá a configurar el proyecto para compilarlo e implementarlo en su dispositivo iOS.

En el menú de Unity, seleccione **File** > **Build Settings...** (Archivo > Configuración de compilación...) para abrir la ventana Build Settings (Configuración de compilación) y, luego, cambie la plataforma a iOS.

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-1.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo cambiar la plataforma de compilación, puede consultar las instrucciones del artículo [Cambio de la plataforma de compilación](mr-learning-base-02.md#switching-the-build-platform).

Cierre la ventana Build Settings (Configuración de compilación).

En el menú de Unity, seleccione **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality Toolkit > Utilidades > Configurar proyecto de Unity) para abrir la ventana **MRTK Project Configurator** (Configurador del proyecto MRTK). Asegúrese de que todas las opciones estén seleccionadas y, a continuación, haga clic en el botón **Apply** (Aplicar) para aplicar la configuración:

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-2.png)

En el menú de Unity, seleccione **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana Player Settings (Configuración del jugador). A continuación, busque la sección **Player** >  **Other Settings** (Jugador > Otra configuración) y desactive la casilla **Strip Engine Code** (Código del motor de franja).

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-3.png)

Cierre la ventana Player Settings (Configuración del reproductor) y vuelva a abrir la ventana **Build Settings** (Configuración de compilación).

En la ventana Configuración de compilación, haga clic en el botón **Add Open Scenes** (Agregar escenas abiertas) para agregar la escena actual a la lista **Scenes In Build** (Escenas de la compilación):

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-4.png)

En la ventana Configuración de compilación, haga clic en el botón **Build** (Compilar) para abrir la ventana Build iOS (Compilar iOS).

Elija una ubicación adecuada para almacenar el proyecto Xcode, por ejemplo, _D:\MixedRealityLearning\Builds_, cree una carpeta nueva y asígnale un nombre adecuado, por ejemplo, _MRTKTutorials-AzureSpatialAnchors_ y, luego, haga clic en el botón **Select Folder** (Seleccionar carpeta) para iniciar el proceso de compilación:

![mr-learning-asa](images/mr-learning-asa/asa-05-section4-step1-5.png)

Una vez completado el proceso de compilación, siga las instrucciones del artículo [Exportación del proyecto de Xcode](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) para aprender a implementar el proyecto de Xcode en el dispositivo iOS.

## <a name="congratulations"></a>Enhorabuena

En este tutorial, ha aprendido a compilar un proyecto en dispositivos iOS y Android con AR Foundation, y los complementos ARCore XR y ARKit XR.
