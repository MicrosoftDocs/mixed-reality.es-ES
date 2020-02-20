---
title: 'Tutoriales de introducción: 2. Inicialización de tu proyecto y primera aplicación'
description: Haz este curso para aprender a implementar el reconocimiento facial de Azure en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: d3392df9bfad5938d71d3a01999be51834a98a5d
ms.sourcegitcommit: 87aca9c2b73b0e83cb70a46443dcdb08c3621005
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/17/2020
ms.locfileid: "77373445"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. Inicialización de tu proyecto y primera aplicación

## <a name="overview"></a>Introducción

<!-- TODO: Consider expanding to include summary of each tutorial in this tutorial series -->
En este primero tutorial, obtendrás información sobre algunas de las funcionalidades que ofrece <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a>, empezarás tu primera aplicación para HoloLens 2 y la implementarás en el dispositivo.

## <a name="objectives"></a>Objetivos

* Configurar Unity para el desarrollo de HoloLens
* Importar recursos y configurar la escena
* Ver la malla de asignación espacial, mallas de mano y el contador de velocidad de fotogramas

## <a name="prerequisites"></a>Requisitos previos

* Un equipo Windows 10 configurado con las [herramientas instaladas](install-the-tools.md) correctas
* SDK de Windows 10 10.0.18362.0 o posterior
* Capacidad básica para programar con C#
* Un dispositivo HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode)
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X instalado y el módulo de compatibilidad con la compilación de la Plataforma universal de Windows agregado

> [!IMPORTANT]
> La versión de Unity recomendada para esta serie de tutoriales es Unity 2019.2.X. Esta sustituye los requisitos de versión de Unity o las recomendaciones descritas en los requisitos previos vinculados anteriormente.

## <a name="create-new-unity-project"></a>Creación de un nuevo proyecto de Unity

Inicia **Unity Hub**, selecciona la pestaña **Projects** (Proyectos) y haz clic en la **flecha hacia abajo** situada junto al botón **New** (Nuevo):

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-1.png)

Selecciona la versión de Unity especificada en la sección [Requisitos previos](#prerequisites) anterior:

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-2.png)

En la ventana Create a new project (Crear un proyecto nuevo):

* Asegúrate de que la opción **Templates** (Plantillas) está establecida como **3D**.
* Escribe un **nombre de proyecto** adecuado, por ejemplo, _Tutoriales MRTK_
* Elige una **ubicación** adecuada para almacenar el proyecto, por ejemplo, _D:\MixedRealityLearning_.
* Haz clic en el botón **Create** (Crear) para crear e iniciar el nuevo proyecto de Unity.

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-3.png)

> [!CAUTION]
> Cuando se trabaja en Windows, hay un límite de longitud de MAX_PATH de 255 caracteres. Unity se ve afectado por estos límites y puede producirse un error en la compilación si la ruta de acceso de un archivo tiene más de 255 caracteres. Por lo tanto, se recomienda encarecidamente almacenar el proyecto de Unity lo más cerca posible de la raíz de la unidad.

Espera a que Unity cree el proyecto:

![mrlearning-base](images/mrlearning-base/tutorial1-section1-step1-4.png)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Configuración del proyecto de Unity para Windows Mixed Reality

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

En esta sección, se cambiará la plataforma de compilación y se habilitará la realidad virtual y la percepción espacial.

### <a name="1-switch-build-platform"></a>1. Cambiar la plataforma de compilación

En el menú de Unity, selecciona **File** (Archivo) > **Build Settings...** (Configuración de compilación...) para abrir la ventana de configuración de compilación:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-1.png)

En la ventana de configuración de compilación, selecciona **Universal Windows Platform** (Plataforma universal de Windows) y haz clic en el botón **Switch Platform** (Cambiar plataforma):

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-2.png)

Espera a que Unity termine de cambiar la plataforma:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-3.png)

Cuando Unity haya terminado de cambiar la plataforma, haz clic en el icono rojo con la **x** para cerrar la ventana de configuración de compilación:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step1-4.png)

### <a name="2-enable-virtual-reality"></a>2. Habilitar la realidad virtual

> [!NOTE]
> La opción de habilitar la realidad virtual también se aplica a los cascos de realidad mixta y realidad aumentada, ya que hace referencia a la habilitación de la visión estereoscópica (p. ej., la representación de imágenes diferentes para cada ojo).

En el menú de Unity, selecciona **Edit** (Editar)  > **Project Settings...** (Configuración del proyecto) para abrir la ventana de configuración del proyecto:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-1.png)

En la ventana de configuración del proyecto, selecciona **Player** (Reproductor) > **XR Settings** (Configuración de XR) para expandir la configuración de XR:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-2.png)

En la configuración de XR, activa la casilla **Virtual Reality Supported** (Compatible con realidad virtual) para habilitar la realidad virtual y, a continuación, haz clic en el icono **+** y selecciona **Windows Mixed Reality** para agregar el SDK de Windows Mixed Reality:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-3.png)

Espera a que Unity termine de agregar el SDK:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-4.png)

Cuando Unity haya terminado de agregar el SDK, optimiza la configuración de XR de la siguiente manera:

* Establece el valor **Depth Format** (Formato de profundidad) de Windows Mixed Reality en **16-bit depth** (Profundidad de 16 bits).
* Activa la casilla **Enable Depth Sharing** (Habilitar el uso compartido de profundidad) de Windows Mixed Reality
* Establece el valor **Rendering Mode\* (Modo de representación) estéreo**  en **Single Pass Instanced** (Instancia de paso único)

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step2-5.png)

> [!TIP]
> Para obtener más información sobre cómo optimizar Unity para Windows Mixed Reality, puedes consultar la página de ayuda [Configuración recomendada para Unity](recommended-settings-for-unity.md) en la documentación.

### <a name="3-enable-spatial-perception"></a>3. Habilitar la percepción espacial

> [!NOTE]
> La percepción espacial permite ver la malla de asignación espacial en dispositivos Windows Mixed Reality.

En la ventana de configuración del proyecto, selecciona **Player** (Reproductor) > **Publishing Settings** (Configuración de publicación) para expandir la configuración de publicación:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-1.png)

En la configuración de publicación, desplázate hacia abajo hasta la sección **Capabilities** (Funcionalidades) y activa la casilla **SpatialPerception**:

![mrlearning-base](images/mrlearning-base/tutorial1-section2-step3-2.png)

<!-- TODO: Consider adding info about audio spatializer plugin setting -->

Cierra la ventana Project Settings (Configuración del proyecto).

## <a name="import-textmesh-pro-essential-resources"></a>Importación de recursos esenciales de TextMesh Pro

> [!NOTE]
> Importamos este paquete porque los elementos de la UI de Mixed Reality Toolkit lo requieren.

En el menú de Unity, selecciona **Window** (Ventana) > **TextMeshPro** > **Import TMP Essential Resources** (Importar recursos esenciales de TMP):

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-1.png)

En la ventana Import Unity Package (Importar paquete de Unity), haz clic en el botón **All** (Todos) para asegurarte de que todos los recursos están seleccionados y, a continuación, haz clic en el botón **Import** (Importar) para importar los recursos:

![mrlearning-base](images/mrlearning-base/tutorial1-section3-step1-2.png)

## <a name="import-the-mixed-reality-toolkit"></a>Importación de Mixed Reality Toolkit

Descarga el paquete personalizado de Unity:

* [Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.2.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage)

En el menú de Unity, selecciona **Assets** (Recursos) > **Import Package** (Importar paquete) > **Custom Package...** (Paquete personalizado) para abrir la ventana Importar paquete...:

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-1.png)

En la ventana de importación de paquetes, selecciona el paquete **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.2.0.unitypackage** que descargaste y haz clic en el botón **Open** (Abrir):

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-2.png)

En la ventana Import Unity Package (Importar paquete de Unity), haz clic en el botón **All** (Todos) para asegurarte de que todos los recursos están seleccionados y, a continuación, haz clic en el botón **Import** (Importar) para importar los recursos:

![mrlearning-base](images/mrlearning-base/tutorial1-section4-step1-3.png)

## <a name="configure-the-unity-project-for-the-mixed-reality-toolkit"></a>Configuración del proyecto de Unity para Mixed Reality Toolkit

<!-- TODO: Consider adding info about configuring Unity for WMR vs MRTK, or removing WMR section -->

Una vez importado el paquete, debe aparecer la ventana MRTK Project Configurator (Configurador del proyecto MRTK). Si no aparece, se puede abrir seleccionando la opción **Mixed Reality Toolkit** > **Utilities** (Utilidades) > **Configure Unity Project** (Configurar proyecto de Unity) en el menú de Unity.

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-1.png)

En la ventana MRTK Project Configurator, expande la sección **Modify Configurations** (Modificar configuraciones), <u>desactiva</u> la casilla **Enable MSBuild for Unity** (Habilitar MSBuild para Unity), asegúrate de que todas las demás opciones están seleccionadas y haz clic en el botón **Apply** (Aplicar) para aplicar la configuración:

![mrlearning-base](images/mrlearning-base/tutorial1-section5-step1-2.png)

> [!CAUTION]
> Es posible que MSBuild para Unity no admita todos los SDK que vas a usar y puede ser difícil de deshabilitar una vez que se haya habilitado. Por lo tanto, se recomienda encarecidamente no habilitar MSBuild para Unity.

## <a name="configure-the-mixed-reality-toolkit"></a>Configuración de Mixed Reality Toolkit
<!-- TODO: Consider renaming to 'Add the Mixed Reality Toolkit to the Unity scene' -->

En el menú de Unity, selecciona **Mixed Reality Toolkit** > **Add to Scene and Configure...** (Agregar a escena y configurar) para agregar Mixed Reality Toolkit a la escena actual:

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-1.png)

Con el objeto MixedRealityToolkit seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, cambia el perfil de configuración de Mixed Reality Toolkit a **DefaultHoloLens2ConfigurationProfile**:

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-2.png)

En el menú de Unity, selecciona **File** (Archivo) > **Save As...** (Guardar como...) para abrir la ventana Save Scene (Guardar escena):

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-3.png)

En la ventana Save Scene (Guardar escena), desplázate hasta la carpeta **Scenes** (Escenas) del proyecto, asígnale un nombre adecuado (por ejemplo, _Introducción_), y haz clic en el botón **Save** (Guardar) para guardar la escena:

![mrlearning-base](images/mrlearning-base/tutorial1-section6-step1-4.png)

## <a name="build-your-application-to-your-device"></a>Compilación de la aplicación para el dispositivo

### <a name="1-build-the-unity-project"></a>1. Compilar el proyecto de Unity

En el menú de Unity, selecciona **File** (Archivo) > **Build Settings...** (Configuración de compilación) para abrir la ventana Build Settings (Configuración de compilación).

En la ventana Build Settings (Configuración de compilación), haz clic en el botón **Add Open Scenes** (Agregar escenas abiertas) para agregar la escena actual a la lista **Scenes In Build** (Escenas de la compilación) y, a continuación, haz clic en el botón **Build** (Compilar) para abrir la ventana Build Universal Windows Platform (Compilar la Plataforma universal de Windows):

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-1.png)

En la ventana Build Universal Windows Platform (Compilar la Plataforma universal de Windows), elige una ubicación adecuada para almacenar la compilación, por ejemplo, _D:\MixedRealityLearning\Builds_, crea una carpeta nueva y asígnale un nombre adecuado, por ejemplo, _Introducción_, y haz clic en el botón **Select Folder** (Seleccionar carpeta) para iniciar el proceso de compilación:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-2.png)

Espera a que Unity finalice el proceso de compilación:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a>2. Compilar e implementar la aplicación

Cuando se complete el proceso de compilación, Unity solicitará al Explorador de archivos de Windows que abra la ubicación en la que almacenó la compilación. Navega dentro de la carpeta y haz doble clic en el archivo de solución para abrirlo en Visual Studio:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-1.png)

> [!NOTE]
> Si Visual Studio solicita que instales nuevos componentes, dedica un momento a comprobar que todos los componentes de los requisitos previos estén instalados, tal como se especifica en la documentación [Instalación de herramientas](install-the-tools.md).

Configura Visual Studio para HoloLens 2. Para ello, selecciona la configuración **Maestro** o **Publicación**, la arquitectura **ARM** y la opción **Dispositivo** como destino:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-2.png)

Conecta HoloLens 2 a tu equipo.

> [!IMPORTANT]
> Antes de realizar una compilación en el dispositivo, el dispositivo debe estar en Modo de desarrollador y emparejado con el equipo de desarrollo. Ambos pasos pueden completarse siguiendo [estas instrucciones](using-visual-studio.md).

El último paso consiste en compilar y realizar la implementación en el dispositivo seleccionando las opciones **Depurar** > **Iniciar sin depurar**:

![mrlearning-base](images/mrlearning-base/tutorial1-section7-step2-3.png)

Aunque en estas instrucciones se supone que vas a realizar la implementación a un dispositivo HoloLens 2, también puedes realizar la implementación en el [emulador de HoloLens 2](using-the-hololens-emulator.md) o crear un [paquete de la aplicación para una instalación de prueba](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>).

Al seleccionar Iniciar sin depurar, la aplicación se iniciará de inmediato en el dispositivo tras una compilación correcta, pero sin que el depurador esté asociado ni que la información de depuración aparezca en Visual Studio. Esto también significa que puedes desconectar el cable USB mientras la aplicación se ejecuta en HoloLens 2 sin detener la aplicación.

Para realizar una implementación en el dispositivo sin necesidad de que se inicie automáticamente la aplicación, puedes seleccionar Compilar > Implementar solución.

## <a name="congratulations"></a>Enhorabuena

<!-- TODO: Consider cleanup and adding in app screenshots -->
Ya has implementado tu primera aplicación de HoloLens 2. A medida que avances, deberías ver una malla de asignación espacial que cubre todas las superficies que HoloLens 2 ha percibido. Además, deberías ver los indicadores en las manos y los dedos para el seguimiento de manos, así como un contador de velocidad de fotogramas para supervisar el rendimiento de la aplicación. Estos son solo algunas de las partes fundamentales, incluidas de fábrica en Mixed Reality Toolkit. En los tutoriales siguientes, comenzarás a agregar más contenido e interactividad a la escena, para que puedas explorar por completo las funcionalidades de HoloLens 2 y Mixed Reality Toolkit.

> [!NOTE]
> Es posible que veas el generador de perfiles de diagnóstico en la aplicación. Puedes activar y desactivar su visibilidad mediante el comando de voz **Toogle Diagnostics** (Activar el diagnóstico). Sin embargo, por lo general es recomendable mantener siempre visible el generador de perfiles durante el desarrollo para saber si los cambios a la aplicación pueden haber tenido un impacto en el rendimiento (por ejemplo, la aplicación HoloLens 2 debería [ejecutarse continuamente a 60 FPS](understanding-performance-for-mixed-reality.md)).

[Tutorial siguiente: 3. Creación de la interfaz de usuario y configuración de Mixed Reality Toolkit](mrlearning-base-ch2.md)
