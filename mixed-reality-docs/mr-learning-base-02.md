---
title: 'Tutoriales de introducción: 2. Inicialización de su proyecto e implementación de su primera aplicación'
description: En este curso le mostramos cómo usar Mixed Reality Toolkit (MRTK) para crear una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 5cac7d6f776619cbc2a0e0891b7915b656708726
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376657"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a>2. Inicialización de su proyecto e implementación de su primera aplicación

## <a name="overview"></a>Introducción

En este tutorial, aprenderá a crear un nuevo proyecto de Unity, configurarlo para el desarrollo con <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> e importar MRTK. También le guiará a través de la configuración, la compilación y la implementación de la escena de ejemplo básica de Unity desde Visual Studio a HoloLens 2 o el emulador.

## <a name="objectives"></a>Objetivos

* Aprender a configurar Unity para el desarrollo de HoloLens
* Aprender a compilar e implementar la aplicación en HoloLens
* Ver la malla de asignación espacial, las mallas de mano y el contador de velocidad de fotogramas

## <a name="creating-the-unity-project"></a>Creación del proyecto de Unity

Inicia **Unity Hub**, selecciona la pestaña **Projects** (Proyectos) y haz clic en la **flecha hacia abajo** situada junto al botón **New** (Nuevo):

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-1.png)

En el desplegable, seleccione la **versión** de Unity especificada en los [Requisitos previos](mr-learning-base-01.md#prerequisites):

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> Si la versión de Unity determinada no está disponible en Unity Hub, puede iniciar la instalación desde el <a href="https://unity3d.com/get-unity/download/archive" target="_blank">archivo de descarga</a> de Unity.

En la ventana Create a new project (Crear un proyecto nuevo):

* Asegúrate de que la opción **Templates** (Plantillas) está establecida como **3D**.
* Escribe un **nombre de proyecto** adecuado, por ejemplo, _Tutoriales MRTK_
* Elige una **ubicación** adecuada para almacenar el proyecto, por ejemplo, _D:\MixedRealityLearning_.
* Haz clic en el botón **Create** (Crear) para crear e iniciar el nuevo proyecto de Unity.

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> Cuando se trabaja en Windows, hay un límite de longitud de MAX_PATH de 255 caracteres. Por lo tanto, debe guardar el proyecto de Unity cerca de la raíz de la unidad.

Espera a que Unity cree el proyecto:

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a>Cambio de la plataforma de compilación

En el menú de Unity, selecciona **File** > **Build Settings...** (Archivo > Configuración de compilación...) para abrir la ventana de configuración de compilación:

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-1.png)

En la ventana de configuración de compilación, selecciona **Universal Windows Platform** (Plataforma universal de Windows) y haz clic en el botón **Switch Platform** (Cambiar plataforma):

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-2.png)

Espera a que Unity termine de cambiar la plataforma:

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-3.png)

Cuando Unity haya terminado de cambiar la plataforma, haz clic en el icono rojo con la **x** para cerrar la ventana de configuración de compilación:

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a>Importación de los recursos esenciales de TextMeshPro

En el menú de Unity, seleccione **Window** > **TextMeshPro** > **Import TMP Essential Resources** (Ventana > TextMeshPro > Importar recursos esenciales de TMP) para abrir la ventana Import Unity Package (Importar paquete de Unity):

![mr-learning-base](images/mr-learning-base/base-02-section3-step1-1.png)

En la ventana Import Unity Package (Importar paquete de Unity), haz clic en el botón **All** (Todos) para asegurarte de que todos los recursos están seleccionados y, a continuación, haz clic en el botón **Import** (Importar) para importar los recursos:

![mr-learning-base](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> Los elementos de la interfaz de usuario de MRTK requieren los recursos esenciales de TextMeshPro. Puede omitir este paso si no va a usar los elementos de la interfaz de usuario de MRTK en el proyecto.

## <a name="importing-the-mixed-reality-toolkit"></a>Importación de Mixed Reality Toolkit

Descarga el paquete personalizado de Unity:

* [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

En el menú de Unity, selecciona **Assets** > **Import Package** > **Custom Package...** (Recursos > Importar paquete > Paquete personalizado...) para abrir la ventana Import package... (Importar paquete...):

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-1.png)

En la ventana Import package... (Importar paquete...), seleccione el paquete **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage** que descargó y haga clic en el botón **Open** (Abrir):

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-2.png)

En la ventana Import Unity Package (Importar paquete de Unity), haz clic en el botón **All** (Todos) para asegurarte de que todos los recursos están seleccionados y, a continuación, haz clic en el botón **Import** (Importar) para importar los recursos:

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-3.png)

## <a name="configuring-the-unity-project"></a>Configuración del proyecto de Unity

### <a name="1-apply-the-mrtk-project-configurator-settings"></a>1. Aplicación de la configuración del configurador del proyecto de MRTK

Una vez que Unity haya terminado de importar el paquete de la sección anterior, debe aparecer la ventana MRTK Project Configurator (Configurador del proyecto de MRTK). Si no es así, abra la ventana Configurator (Configurador); para ello, vaya al menú de Unity y seleccione **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** (Mixed Reality Toolkit > Utilidades > Configurar proyecto de Unity):

![mr-learning-base](images/mr-learning-base/base-02-section5-step1-1.png)

En la ventana MRTK Project Configurator (Configurador del proyecto de MRTK), expanda la sección **Modify Configurations (Modificar configuraciones)** , asegúrese de que todas las demás opciones están seleccionadas y haga clic en el botón **Apply** (Aplicar) para aplicar la configuración:

![mr-learning-base](images/mr-learning-base/base-02-section5-step1-2.png)

### <a name="2-configure-additional-project-settings"></a>2. Configuración de valores adicionales del proyecto

En el menú de Unity, selecciona **Edit** > **Project Settings...** (Editar > Configuración del proyecto...) para abrir la ventana de configuración del proyecto:

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-1.png)

En la ventana Project Settings (Configuración del proyecto), seleccione **Player** > **XR Settings** (Reproductor > Configuración de XR), haga clic en el icono **+** y seleccione Windows Mixed Reality para agregar el SDK de Windows Mixed Reality:

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-2.png)

Una vez que Unity haya terminado de importar el SDK de Windows Mixed Reality, debe volver a aparecer la ventana MRTK Project Configurator (Configurador del proyecto de MRTK). Si no es así, use el menú de Unity para abrirla.

En la ventana MRTK Project Configurator (Configurador del proyecto de MRTK), use la lista desplegable **Audio spatializer** (Espacializador de audio) para seleccionar **MS HRTF Spatializer** (Espacializador de audio MS HRTF) y, a continuación, haga clic en el botón **Apply** (Aplicar) para aplicar la configuración:

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-3.png)

En la ventana Project Settings (Configuración del proyecto), seleccione **Player** > **XR Settings** (Reproductor > Configuración de XR) y, a continuación, use la lista desplegable **Depth Format** (Formato de profundidad) para seleccionar **16-bit depth** (Profundidad de 16 bits):

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-4.png)

En la ventana Project Settings (Configuración del proyecto), seleccione **Player** > **Publishing Settings** (Reproductor > Configuración de publicación) y en el campo **Package name** (Nombre del paquete), escriba un nombre adecuado, por ejemplo, _TutorialesDeMRTK-Introducción_:

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-5.png)

> [!NOTE]
> "Package name" es el identificador único para la aplicación. Debe cambiar este identificador antes de implementar la aplicación para evitar sobrescribir aplicaciones instaladas anteriormente.

> [!TIP]
> "Product Name" es el nombre que se muestra en el menú Inicio de HoloLens. Para facilitar la búsqueda de la aplicación durante el desarrollo, agregue un carácter de subrayado delante del nombre para ordenarlo a la parte superior.

## <a name="creating-and-configuring-the-scene"></a>Creación y configuración de la escena

En el menú de Unity, seleccione **File** > **New Scene** (Archivo > Nueva escena) para crear una nueva escena:

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-1.png)

En el menú de Unity, seleccione **Mixed Reality Toolkit** > **Add to Scene and Configure...** (Agregar a escena y configurar...) para agregar MRTK a la escena actual:

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-2.png)

Con el objeto **MixedRealityToolkit** seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, compruebe que el perfil de configuración **MixedRealityToolkit** se haya definido como **DefaultMixedRealityToolkitConfigurationProfile**:

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-3.png)

> [!IMPORTANT]
> Normalmente, se usa el perfil DefaultHoloLens2ConfigurationProfile para desarrollar para HoloLens. Sin embargo, para este tutorial, usará DefaultMixedRealityToolkitConfigurationProfile y, a continuación, en el siguiente tutorial, [Configuración de los perfiles de MRTK](mr-learning-base-03.md), cambiará a DefaultHoloLens2ConfigurationProfile.

En el menú de Unity, selecciona **File** > **Save As...** (Archivo > Guardar como...) para abrir la ventana Save Scene (Guardar escena):

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-4.png)

En la ventana Save Scene (Guardar escena), desplázate hasta la carpeta **Scenes** (Escenas) del proyecto, asígnale un nombre adecuado (por ejemplo, _GettingStarted_), y haz clic en el botón **Save** (Guardar) para guardar la escena:

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a>Compilación de la aplicación a HoloLens 2

### <a name="1-build-the-unity-project"></a>1. Compilar el proyecto de Unity

En el menú de Unity, selecciona **File** (Archivo) > **Build Settings...** (Configuración de compilación) para abrir la ventana Build Settings (Configuración de compilación).

En la ventana Build Settings (Configuración de compilación), haz clic en el botón **Add Open Scenes** (Agregar escenas abiertas) para agregar la escena actual a la lista **Scenes In Build** (Escenas de la compilación) y, a continuación, haz clic en el botón **Build** (Compilar) para abrir la ventana Build Universal Windows Platform (Compilar la Plataforma universal de Windows):

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-1.png)

En la ventana Build Universal Windows Platform (Compilar la Plataforma universal de Windows), elige una ubicación adecuada para almacenar la compilación, por ejemplo, _D:\MixedRealityLearning\Builds_, crea una carpeta nueva y asígnale un nombre adecuado, por ejemplo, _Introducción_, y haz clic en el botón **Select Folder** (Seleccionar carpeta) para iniciar el proceso de compilación:

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-2.png)

Espera a que Unity finalice el proceso de compilación:

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2. Compilar e implementar la aplicación

Cuando se complete el proceso de compilación, Unity solicitará al Explorador de archivos de Windows que abra la ubicación en la que almacenó la compilación. Navega dentro de la carpeta y haz doble clic en el archivo de solución para abrirlo en Visual Studio:

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> Si Visual Studio solicita que instale nuevos componentes, dedique un momento a comprobar que tiene todos los componentes de requisitos previos de la documentación **[Instalación de herramientas](install-the-tools.md)** .

Configure Visual Studio para HoloLens 2. Para ello, selecciona la configuración **Maestro** o **Publicación**, la arquitectura **ARM64** y la opción **Dispositivo** como destino:

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> Si va a realizar la implementación en HoloLens (1ª. generación), seleccione la arquitectura **x86**.

> [!NOTE]
> En el caso de HoloLens, normalmente se compilará para la arquitectura ARM. Sin embargo, hay un <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>problema conocido</strong></a> en Unity 2019.3 que produce errores al seleccionar ARM como arquitectura de compilación en Visual Studio. La solución recomendada es compilar para ARM64. Si no es una opción, vaya a **Edit > Project Settings > Player > Other Settings** (Editar > Configuración del proyecto > Reproductor > Otras opciones) y deshabilite **Graphics Jobs** (Trabajos de gráficos).

> [!NOTE]
> Si no ve Dispositivo como opción de destino, es posible que deba cambiar el proyecto de inicio de la solución de Visual Studio del proyecto de IL2CPP al proyecto de UWP. Para ello, en el Explorador de soluciones, haga clic con el botón derecho en NombreDelProyecto (Windows Universal) y seleccione **Establecer como proyecto de inicio**.

Conecte su HoloLens al equipo y, a continuación, seleccione **Depurar** > **Iniciar sin depurar** para compilar e realizar la implementación en el dispositivo:

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> Antes de realizar una compilación en el dispositivo, el dispositivo debe estar en Modo de desarrollador y emparejado con el equipo de desarrollo. Ambos pasos pueden completarse siguiendo [estas instrucciones](using-visual-studio.md).

> [!TIP]
> También puede realizar la implementación en el [emulador de HoloLens](using-the-hololens-emulator.md) o crear un [paquete de aplicación](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) para la instalación de prueba.

Al usar Iniciar sin depurar, la aplicación se inicia automáticamente en el dispositivo sin el depurador de Visual Studio adjunto.

Seleccione **Compilar > Implementar solución** para realizar una implementación en el dispositivo sin que se inicie automáticamente la aplicación.

> [!NOTE]
>Es posible que veas el generador de perfiles de diagnóstico en la aplicación, que puedes activar y desactivar mediante el comando de voz **Toogle Diagnostics** (Alternar diagnóstico). Se recomienda que mantenga el generador de perfiles visible la mayor parte del tiempo durante el desarrollo para comprender cuándo los cambios en la aplicación pueden afectar al rendimiento. Por ejemplo, las aplicaciones de HoloLens deben [ejecutarse continuamente a 60 FPS](understanding-performance-for-mixed-reality.md).

## <a name="congratulations"></a>Enhorabuena

Ya ha implementado su primera aplicación de HoloLens 2. A medida que avance, debería ver una malla de asignación espacial que cubre todas las superficies que HoloLens ha percibido. Además, deberías ver los indicadores en las manos y los dedos para el seguimiento con la mano, así como un contador de velocidad de fotogramas para vigilar el rendimiento de la aplicación. Estas características son solo algunas partes fundamentales incluidas en MRTK. En los próximos tutoriales, agregará contenido a su escena para explorar las funcionalidades de HoloLens y MRTK.

[Tutorial siguiente: 3. Configuración de los perfiles de MRTK](mr-learning-base-03.md)
