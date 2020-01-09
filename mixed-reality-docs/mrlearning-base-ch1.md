---
title: 'Tutoriales de introducción: 2. Inicialización de tu proyecto y primera aplicación'
description: Haz este curso para aprender a implementar el reconocimiento facial de Azure en una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
ms.localizationpriority: high
keywords: realidad mixta, unity, tutorial, hololens
ms.openlocfilehash: d0c166f760884efab9719ecba1ff83285872e2ef
ms.sourcegitcommit: 23b130d03fea46a50a712b8301fe4e5deed6cf9c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/24/2019
ms.locfileid: "75334410"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. Inicialización de tu proyecto y primera aplicación

## <a name="overview"></a>Introducción

En esta primera lección, obtendrás información sobre algunas de las funcionalidades que ofrece <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a>, empezarás tu primera aplicación para HoloLens 2 y la implementarás en el dispositivo.

## <a name="objectives"></a>Objetivos

* Configurar Unity para el desarrollo de HoloLens.
* Importar recursos y configurar la escena.
* Visualización de la malla de asignación espacial, mallas de mano y el contador de velocidad de fotogramas.

## <a name="create-new-unity-project"></a>Creación de un nuevo proyecto de Unity

1. Inicia Unity.

2. Selecciona **New** (Nuevo).

    ![Lección1 Sección1 Paso2](images/mrlearning-base-ch1-1-step2.JPG)

3. Especifica un nombre de proyecto (por ejemplo, "MixedRealityBase").

    ![Lección1 Sección1 Paso3](images/mrlearning-base-ch1-1-step3.JPG)

4. Escribe una ubicación para guardar el proyecto.

    ![Lección1 Sección1 Paso4](images/mrlearning-base-ch1-1-step4.JPG)

5. Asegúrate de que el proyecto esté establecido en **3D** (3D).

    ![Lección1 Sección1 Paso5](images/mrlearning-base-ch1-1-step5.JPG)

6. Haz clic en **Create Project** (Crear proyecto).

    ![Lección1 Sección1 Paso6](images/mrlearning-base-ch1-1-step6.JPG)

## <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Configuración del proyecto de Unity para Windows Mixed Reality

1. Abre la ventana *Build Settings* (Configuración de compilación) en **Archivo** > **Build Settings** (Configuración de compilación).

    ![Lección1 Sección2 Paso1](images/mrlearning-base-ch1-2-step1.JPG)

2. Selecciona *Plataforma universal de Windows* y haz clic en el botón **Switch Platform** (Cambiar plataforma) para cambiar de plataforma. Las aplicaciones que se ejecutan en HoloLens 2 tienen que ser compatibles con la Plataforma universal de Windows (UWP).

    ![Lección1 Sección2 Paso2](images/mrlearning-base-ch1-2-step2.JPG)

3. Para habilitar la realidad virtual, haz clic en el botón **Configuración del Reproductor** de la ventana de compilación y, a continuación, en el panel del inspector, habilita la casilla *Virtual Reality Supported* (Se admite la realidad virtual) en XR Settings (Configuración de XR), tal como se muestra en la imagen siguiente. Ten en cuenta que es posible que necesites arrastrar la ventana *Build Settings* (Configuración de compilación) a un lado para ver el panel del inspector. La casilla *Virtual Reality Supported* (Se admite la realidad virtual) también se aplica a los cascos de realidad mixta y realidad aumentada porque hace referencia a la habilitación de la visión estereoscópica (representación de imágenes diferentes para cada ojo).

    ![Lección1 Sección2 Paso3](images/mrlearning-base-ch1-2-step3.JPG)

4. También en XR Settings (Configuración de XR), cambia *Stereo Rendering Mode* (Modo de representación estereoscópico) a *Single Pass Instanced* (Instancia de paso único). Este [estilo de canalización de representación](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) suele ofrecer el mejor rendimiento para HoloLens 2. Si te interesan otras configuraciones de rendimiento para tu entorno de Unity, sigue [estas instrucciones](recommended-settings-for-unity.md).

    ![Lección1 Sección2 Paso4](images/mrlearning-base-ch1-2-step4.jpg)

5. En el mismo panel del inspector, comprueba que la casilla *Spatial Perception* (Percepción espacial) en la sección de funcionalidades esté habilitada en *Configuración de publicación*. La percepción espacial nos permite ver la malla de asignación espacial en un dispositivo de realidad mixta, como HoloLens 2. La opción Configuración de publicación se encuentra en el panel del inspector, sobre de XR Settings (Configuración de XR) y bajo Otra configuración.

    ![Lección1 Sección2 Paso5](images/mrlearning-base-ch1-2-step5.JPG)

    >[!NOTE]
    >Aunque no se usan en esta sección, otras funcionalidades comunes que es posible que quieras habilitar incluyen *Micrófono* para comandos de voz e *InternetClient* para conectarte a los servicios que requieren una conexión de red.

## <a name="import-the-mixed-reality-toolkit"></a>Importación de Mixed Reality Toolkit

1. Descarga la [versión 2.1.0 del paquete base](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) para Unity de [Mixed Reality Toolkit](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) y guárdalo en una carpeta de tu equipo.

2. Importa el paquete de *Mixed Reality Toolkit* que descargaste en el paso anterior. Para empezar, haz clic en **Recursos** > **Importar** > **Custom Package** (Paquete personalizado), selecciona *Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage* y ábrelo para comenzar el proceso de importación. Espera unos minutos hasta que termine el proceso de importación.

    ![Lección1 Sección3 Paso2a](images/mrlearning-base-ch1-3-step2a.JPG)

    ![Lección1 Sección3 Paso2b](images/mrlearning-base-ch1-3-step2b.JPG)

3. En la siguiente ventana emergente, haz clic en **Importar** para comenzar a importar el paquete seleccionado en el proyecto de Unity. Comprueba que estén seleccionados todos los elementos tal como se muestra en la imagen.

    ![Lección1 Sección3 Paso3](images/mrlearning-base-ch1-3-step3.JPG)

    > [!NOTE]
    > Si ves un cuadro de diálogo emergente que solicita que apliques la configuración predeterminada de Mixed Reality Toolkit, haz clic en **Aplicar**. MRTK analiza el proyecto para buscar la configuración recomendada que falta cuando se importa para la configuración automatizada. En función de la configuración, el elemento emergente podría ser diferente del de la imagen siguiente.

    ![Lección1 Sección3 Paso4 Nota1](images/mrlearning-base-ch1-3-step4-note1.JPG)

## <a name="configure-the-mixed-reality-toolkit"></a>Configuración de Mixed Reality Toolkit

1. Para agregar *Mixed Reality Toolkit* a la escena actual, selecciona **Mixed Reality Toolkit** > **Add to Scene and Configure...** (Agregar a la escena y configurar...) en la barra de menús. Si no ves este elemento de menú después de importar el kit de herramientas de realidad virtual, reinicia Unity.

    ![Lección1 Sección4 Paso1](images/mrlearning-base-ch1-4-step1.JPG)

    > [!NOTE]
    > Es posible que veas un cuadro de diálogo emergente para seleccionar un [perfil para Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html). Haz doble clic en el perfil llamado *DefaultHoloLens2ConfigurationProfile* para elegirlo.

2. La escena tendrá varios elementos nuevos y modificaciones. Guarda la escena con un nombre diferente. Para ello, haz clic en **Archivo** > **Guardar como** y asígnale un nombre, por ejemplo, *BaseScene*. Para mantener la escena organizada, guárdala en la carpeta *Escenas* de la carpeta *Recursos* del proyecto.

    ![Lección1 Sección4 Paso2a](images/mrlearning-base-ch1-4-step2a.JPG)

    ![Lección1 Sección4 Paso2b](images/mrlearning-base-ch1-4-step2b.JPG)

## <a name="build-your-application-to-your-device"></a>Compilación de la aplicación para el dispositivo

1. Si has cerrado la ventana *Build Settings* (Configuración de compilación) de las secciones anteriores, ábrela de nuevo en **Archivo** > **Build Settings** (Configuración de compilación).

    ![Lección1 Sección5 Paso1](images/mrlearning-base-ch1-5-step1.JPG)

2. Comprueba que la escena que acabas de crear está en la lista *Scenes in Build* (Escenas en compilación). Para ello, haz clic en el botón **Add Open Scenes** (Agregar escenas abiertas) mientras tu escena está abierta en Unity.

3. Presiona el botón **Compilar** para comenzar el proceso de compilación.

    ![Lección1 Sección5 Paso3](images/mrlearning-base-ch1-5-step3.JPG)

4. Crea y asigna un nombre a una nueva carpeta para la aplicación. En la imagen siguiente, se ha creado una carpeta con el nombre Aplicación para contener la aplicación. Haz clic en **Seleccionar carpeta** para empezar a compilar la carpeta recién creada. Una vez finalizada la compilación, puedes cerrar la ventana *Build Settings* (Configuración de compilación) en Unity.

    ![Lección1 Sección5 Paso4](images/mrlearning-base-ch1-5-step4.JPG)

    >[!IMPORTANT]
    >Si se produce un error en la compilación, intenta volver a compilar o reinicia Unity y vuelve a compilar. Es posible que veas un error como "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?)" [Error: CS0246 = No se encontró el nombre de espacio de nombres o tipo "XX" (¿te falta una directiva de uso o una referencia de ensamblado?)]". Si es el caso, es posible que debas instalar el [SDK de Windows 10 (10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk).

5. Una vez finalizada la compilación, abre la carpeta recién creada que contiene los archivos de la aplicación que acabas de crear. Haz doble clic en la solución *MixedRealityBase.sln* (o el nombre correspondiente, si has utilizado un nombre alternativo para el proyecto) para abrir el archivo de la solución en Visual Studio.

    >[!NOTE]
    >Asegúrate de abrir la carpeta recién creada (es decir, la carpeta *Aplicación*, si has seguido las convenciones de nomenclatura de los pasos anteriores), ya que habrá un archivo .sln con un nombre similar fuera de esa carpeta que no debes confundir con el archivo .sln de dentro de la carpeta de compilación. La estructura de carpetas debería tener un aspecto similar a la imagen siguiente.
    >
    >Si Visual Studio te pide que instales nuevos componentes, dedica un momento a comprobar que todos los componentes de los requisitos previos estén instalados, tal como se especifica en la [página "Instalación de las herramientas"](install-the-tools.md).

    ![Lección1 Sección5 Paso5](images/mrlearning-base-ch1-5-step5.JPG)

6. Conecta HoloLens 2 a tu equipo. Aunque en estas instrucciones se supone que vas a realizar la implementación a un dispositivo HoloLens 2, también puedes optar por realizar la implementación en el [emulador de HoloLens 2](using-the-hololens-emulator.md) o decidir crear un [paquete de la aplicación para una instalación de prueba](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>).

    >[!IMPORTANT]
    >Antes de realizar una compilación en el dispositivo, el dispositivo debe estar en *Modo de desarrollador* y emparejado con la máquina de desarrollo. Ambos pasos pueden completarse siguiendo [estas instrucciones](using-visual-studio.md).

7. Configura Visual Studio para realizar una compilación en HoloLens 2. Para ello, selecciona la configuración *Publicación* o *Maestro*, la arquitectura *ARM* y la opción *Dispositivo* como destino.

    ![Lección1 Sección5 Paso8](images/mrlearning-base-ch1-5-step7.JPG)

8. El último paso consiste en compilar y realizar la implementación en el dispositivo seleccionando **Depurar** > **Iniciar sin depurar**. Al seleccionar *Iniciar sin depurar*, la aplicación se iniciará de inmediato en el dispositivo tras una compilación correcta, pero sin que el depurador esté asociado ni que la información de depuración aparezca en Visual Studio. Esto también significa que puedes desconectar el cable USB mientras la aplicación se ejecuta en HoloLens 2 sin detener la aplicación.

    > [!NOTE]
    > También puedes seleccionar **Compilar** > **Implementar solución** para realizar una implementación en el dispositivo sin que se inicie automáticamente la aplicación.

    ![Lección1 Sección5 Paso9](images/mrlearning-base-ch1-5-step8.JPG)

## <a name="congratulations"></a>Enhorabuena

Ya has implementado tu primera aplicación de HoloLens 2. A medida que avances, deberías ver una malla de asignación espacial que cubre todas las superficies que HoloLens 2 ha percibido. Además, deberías ver los indicadores en las manos y los dedos para el seguimiento de manos, así como un contador de velocidad de fotogramas para supervisar el rendimiento de la aplicación. Estos son solo algunas de las partes fundamentales, incluidas de fábrica en Mixed Reality Toolkit. En las lecciones siguientes, comenzarás a agregar más contenido e interactividad a la escena, para que puedas explorar por completo las funcionalidades de HoloLens 2 y Mixed Reality Toolkit.

> [!NOTE]
> En la aplicación, es posible que veas el generador de perfiles visual. Verás cómo alternar el contador de velocidad de fotogramas mediante un comando de voz en la [Lección 5](mrlearning-base-ch5.md). Por lo general, te recomendamos tener el generador de perfiles visual visible en todo momento durante el desarrollo a fin de comprender cuándo los cambios de código pueden haber afectado al rendimiento. La aplicación de HoloLens 2 debe [ejecutarse continuamente a 60 FPS](understanding-performance-for-mixed-reality.md).

[Siguiente lección: 3. Creación de la interfaz de usuario y configuración de Mixed Reality Toolkit](mrlearning-base-ch2.md)
