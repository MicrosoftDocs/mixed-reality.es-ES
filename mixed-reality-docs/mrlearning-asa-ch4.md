---
title: 'Tutoriales sobre Azure Spatial Anchors: 4. Azure Spatial Anchors para iOS y Android'
description: Sigue este tutorial para aprender a implementar Azure Spatial Anchors dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/18/2020
ms.topic: article
keywords: realidad mixta, unity, tutorial, curso, hololens, azure, spatial anchors
ms.localizationpriority: high
ms.openlocfilehash: a35f73ae5aee493182f0f4990aa345d990c3f513
ms.sourcegitcommit: e65f1463aec3c040a1cd042e61fc2bd156a42ff8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/26/2020
ms.locfileid: "83867627"
---
# <a name="4-azure-spatial-anchors-for-android-and-ios"></a>4. Azure Spatial Anchors para iOS y Android

En este tutorial, aprenderás a compilar un proyecto en dispositivos iOS y Android con AR Foundation, y los complementos ARCore XR y ARKit XR.

## <a name="objectives"></a>Objetivos

* Aprender a compilar un proyecto en un dispositivo Android mediante AR Foundation y el complemento ARCore XR de Unity.
* Aprender a compilar un proyecto en un dispositivo iOS mediante AR Foundation y el complemento ARKit XR de Unity.

[!NOTE] Para completar este tutorial, asegúrate de haber completado los tutoriales de Azure Spatial Anchors > [Introducción a Azure Spatial Anchors](mrlearning-asa-ch1.md).

## <a name="adding-inbuilt-unity-packages"></a>Adición de paquetes de Unity integrados

En esta sección, instalarás los paquetes integrados de AR Foundation, el complemento ARCore XR y el complemento ARKit XR de Unity necesarios para admitir dispositivos iOS y Android.

Asegúrate de instalar la versión correcta de estos paquetes de Unity como se indica a continuación:

* **AR Foundation 2.1.4**
* **ARCore XR plugin 2.2.0, preview 2**
* **ARKit XR plugin 2.1.1**

[!NOTE] Si desarrollas este proyecto para Android, no es necesario instalar el paquete del complemento ARKit XR. Del mismo modo, si desarrollas este proyecto para iOS, no es necesario que instales el complemento de ARCore XR.

En el menú de Unity, selecciona **Window** > **Package Manager** (Ventana > Administrador de paquetes):

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-1.png)

Los paquetes pueden tardar unos segundos en aparecer en la lista. Para mostrar los paquetes de versión preliminar, haz clic en opción Advanced (Opciones avanzadas) y selecciona "**Show preview packages**" (Mostrar paquetes en versión preliminar).

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-2.png)

En la ventana Package Manager (Administrador de paquetes), selecciona **AR Foundation**, aquí verás muchas versiones y tendrás que seleccionar la versión 2.1.4 y actualizar el paquete haciendo clic en el botón **Update to 2.1.4** (Actualizar a 2.1.4):

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-3.png)

Para admitir dispositivos Android, sigue el mismo proceso para importar ARCore XR Plugin 2.2.0, preview 2.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-4.png)

Para admitir dispositivos iOS, tienes que importar el paquete **ARKit XR plugin 2.1.1** de Unity de Package Manager.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section1-step1-5.png)

## <a name="customize-mrtk-to-support-ar-foundation-camera"></a>Personalización de MRTK para admitir la cámara de AR Foundation

Para personalizar la configuración de MRTK para que admita AR Foundation, selecciona MixedRealityToolKit en la ventana Hierarchy (Jerarquía) y haz clic en el botón **Clone** (Clonar) en el kit de herramientas de realidad mixta en la ventana Inspector.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-1.png)

Al hacer clic en el botón **Clonar** (Clonar), aparecerá una nueva ventana Clone Profile (Clonar perfil), vuelve a hacer clic en el botón Clone para clonar DefaultMixedRealityToolkitProfile.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-2.png)

Del mismo modo, clone el perfil de la cámara en la ventana Inspector y cambia el nombre del perfil a "UnityARConfigurationProfile" y haz clic en el botón **Clone** (Clonar). En la ventana Inspector, busca MixedReality, selecciona la pestaña Camera (Cámara), expande los proveedores de configuración de la cámara en la ventana Inspector y haz clic en **+Add Camera Setting Provider** (+ Agregar proveedor de configuración de cámara) > expande **New data provider 1** (Nuevo proveedor de datos 1) > selecciona **None** (Ninguno) en Type (Tipo) > selecciona **Microsoft.MixedReality.Toolkit.Experimental.Unity** > selecciona **UnityARCameraSettings**.


![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-3.png)

Con el objeto MixedRealityToolKit seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, adjunta scripts auxiliares haciendo clic en el botón **Add component** (Agregar componente) y escribe "AR Reference Point Manager" y selecciona el script.

Al agregar el script "AR Reference Point Manager", se agregará automáticamente "AR session origin" junto con él en la ventana Inspector. Después de agregar los scripts auxiliares, la ventana Inspector debería tener este aspecto.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section2-step1-4.png)

## <a name="build-application-to-android-device"></a>Compilación de la aplicación en un dispositivo Android

Para compilar esta aplicación en un dispositivo Android, haz clic en **File** (Archivo) en la parte superior de la ventana y selecciona **Build Settings** (Configuración de compilación). Aparecerá una nueva ventana en la pantalla, selecciona **Android** y haz clic en **Switch Platform** (Cambiar plataforma). La plataforma tardará unos minutos en cambiar. Después de cambiar a la plataforma Android, haz clic en **Add Open Scenes** (Agregar escenas abiertas) y asegúrate de que la escena actual sea la única seleccionada en la lista **Scenes In Build** (Escenas de la compilación).

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-1.png)

Cierra la ventana **Build Settings** (Configuración de compilación). En el menú de Unity, selecciona **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Kit de herramientas de realidad mixta > Utilidades > Configurar proyecto de Unity) y haz clic en **Apply** (Aplicar) para configurar el proyecto de Unity para la plataforma Android.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-2.png)

En el menú de Unity, selecciona **Edit** > **Project Settings** (Editar > Configuración del proyecto) para abrir la ventana Project Settings (Configuración del proyecto): En la ventana Project Settings (Configuración del proyecto), selecciona la pestaña **Player** (Reproductor), expande la sección Other Settings (Otras opciones de configuración), selecciona **Vulkan**, y quítala haciendo clic en el símbolo "-".

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-3.png)

Cierra la ventana Player Settings (Configuración del reproductor) y vuelva a abrir la ventana Build Settings (Configuración de compilación). A continuación, con un cable USB, conecta el dispositivo Android al equipo y selecciona el dispositivo en la lista desplegable **Build and Run** (Compilar y ejecutar) y, a continuación, haz clic en **Build and Run**. Se te pedirá que guardes un archivo .apk, para el cual puedes elegir cualquier nombre.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section3-step1-4.png)

> [!NOTE]
> Si se produce algún error en la ventana Console (Consola) de Unity relacionado con los módulos SDK, NDK o JDK de Android, tienes que abrir Unity Hub e instalar los módulos SDK, NDK y JDK asociados para el módulo de compatibilidad con la compilación de Android.

Una vez que se complete el proceso de compilación, las aplicaciones deberían cargarse automáticamente en el dispositivo Android.

## <a name="build-application-to-ios-device"></a>Compilación de la aplicación en un dispositivo iOS

Para compilar esta aplicación en un dispositivo iOS, haz clic en **File** (Archivo) en la parte superior de la ventana y selecciona **Build Settings** (Configuración de compilación). Aparecerá una nueva ventana en la pantalla, selecciona **iOS** y haz clic en **Switch Platform** (Cambiar plataforma).

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-1.png)

Cierra la ventana **Build Settings** (Configuración de compilación). En el menú de Unity, selecciona **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Kit de herramientas de realidad mixta > Utilidades > Configurar proyecto de Unity) y haz clic en **Apply** (Aplicar) para configurar el proyecto de Unity para la plataforma iOS.

![mrlearning-asa](images/mrlearning-asa/tutorial4-section4-step1-2.png)

Para compilar el proyecto XCode de iOS, ve a Build Settings (Configuración de compilación) y haz clic en **Build** (Compilar).

Sigue [esta guía](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-ios#export-the-xcode-project) para aprender a implementar este proyecto en tu dispositivo iOS.

## <a name="congratulations"></a>Enhorabuena

En este tutorial, has aprendido a compilar un proyecto para dispositivos iOS y Android. También has aprendido a usar AR Foundation, el complemento ARCore XR y el complemento ARKit XR para que tu proyecto funcione en dispositivos iOS y Android.