---
title: 'Tutoriales de introducción: 2. Inicializar el proyecto y la primera aplicación'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 11/01/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 3bf218b42ea8abed45a80c0dd048e791cdd8372b
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926888"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. inicializar el proyecto y la primera aplicación

En esta primera lección, obtendrá información sobre algunas de las funcionalidades que el [Kit de herramientas de realidad mixta (MRTK)]() tiene que ofrecer, iniciar su primera aplicación para HoloLens 2 e implementarla en el dispositivo.

## <a name="objectives"></a>Objetivos

* Optimizar Unity para el desarrollo de HoloLens.
* Importar recursos y configurar la escena.
* Visualización de la malla de asignación espacial, las mallas de mano y el contador de velocidad de fotogramas.

## <a name="instructions"></a>Instrucciones

### <a name="create-new-unity-project"></a>Creación de un nuevo proyecto de Unity

1. Inicia Unity.
2. Selecciona **New** (Nuevo).
![Lesson1 Section1 paso 2](images/mrlearning-base-ch1-1-step2.JPG)

3. Escriba un nombre de proyecto (por ejemplo, "MixedRealityBase").
![Lesson1 Section1 Step3](images/mrlearning-base-ch1-1-step3.JPG)
4. Escribe una ubicación para guardar el proyecto.
![Lesson1 Section1 Paso4](images/mrlearning-base-ch1-1-step4.JPG)
5. Asegúrate de que el proyecto esté establecido en **3D** (3D).
![Lesson1 Section1 Paso5](images/mrlearning-base-ch1-1-step5.JPG)
6. Haz clic en **Create Project** (Crear proyecto).
![Lesson1 Section1 Paso6](images/mrlearning-base-ch1-1-step6.JPG)


### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Configuración del proyecto de Unity para Windows Mixed Reality

1. Para abrir la ventana *configuración de compilación* , vaya a **archivo** > **configuración de compilación**.
![Lesson1 Section2 paso 1](images/mrlearning-base-ch1-2-step1.JPG)
2. Seleccione la *plataforma universal de Windows* y haga clic en el botón **cambiar plataforma** para cambiar las plataformas. Las aplicaciones que se ejecutan en HoloLens 2 deben ser compatibles con Plataforma universal de Windows (UWP).
![Lesson1 Section2 paso 2](images/mrlearning-base-ch1-2-step2.JPG)
3. Para habilitar la realidad virtual, haga clic en el botón **configuración del reproductor** en la ventana compilar y active la casilla *compatibilidad con la realidad virtual* en la configuración de XR en el panel del inspector, tal y como se muestra en la imagen siguiente. Tenga en cuenta que es posible que tenga que arrastrar la ventana *configuración de compilación* fuera de la pantalla para ver el panel del inspector. La casilla *compatibilidad con la realidad virtual* también se aplica a los auriculares de realidad mixta y de realidad aumentada porque hace referencia a la habilitación de Stereoscopic Vision (representación de imágenes diferentes para cada ojo). ![Lesson1 Section2 Step3](images/mrlearning-base-ch1-2-step3.JPG)
4. También en configuración de XR, cambie el *modo de representación de estéreo* a instancia de *paso único*. Este [estilo de canalización de representación](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) suele ser más eficaz para HoloLens 2. Si está interesado en otras configuraciones de rendimiento para su entorno de Unity, siga [estas instrucciones](recommended-settings-for-unity.md).
![Lesson1 Section2 Paso4](images/mrlearning-base-ch1-2-step4.jpg)
5. En el mismo panel Inspector, asegúrese de que la casilla *percepción espacial* en la sección capacidades está habilitada en *configuración de publicación*. La percepción espacial nos permite visualizar la malla de asignación espacial en un dispositivo de realidad mixta, como HoloLens 2. La configuración de publicación se encuentra en el panel Inspector, encima de la configuración de XR y en otras opciones.
![Lesson1 Section2 Paso5](images/mrlearning-base-ch1-2-step5.JPG)

    > [!NOTE]
    > Aunque no se usa en esta sección, algunas otras funcionalidades comunes que podría desear habilitar incluyen el *micrófono* para comandos de voz y *InternetClient* para conectarse a los servicios que requieren una conexión de red.

### <a name="import-the-mixed-reality-toolkit"></a>Importación de Mixed Reality Toolkit

1. Descargue el paquete de la [versión 2.1.0](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.1.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.1.0.unitypackage) del [Kit de herramientas de realidad mixta](https://github.com/microsoft/MixedRealityToolkit-Unity/releases) y guárdelo en una carpeta de su equipo.

2. Importe el paquete del *Kit de herramientas de realidad mixta* que descargó en el paso anterior. Para empezar, haga clic en **activos** > **importar** > **paquete personalizado** y seleccione *Microsoft. MixedReality. Toolkit. Unity. Foundation. 2.1.0. unitypackage Tools* y ábralo para comenzar el proceso de importación. Espere unos minutos a que se complete el proceso de importación.
    ![Lesson1 Section3 Step2a](images/mrlearning-base-ch1-3-step2a.JPG) ![Lesson1 Section3 Step2b](images/mrlearning-base-ch1-3-step2b.JPG)

3. En la siguiente ventana emergente, haga clic en **importar** para iniciar la importación del paquete seleccionado en el proyecto de Unity. Asegúrese de que todos los elementos se comprueban como se muestra en la imagen.
    ![Lesson1 Section3 Step3](images/mrlearning-base-ch1-3-step3.JPG)

    > [!NOTE]
    > Si ve un cuadro de diálogo emergente que le pide aplicar la configuración predeterminada del kit de herramientas de realidad mixta, haga clic en **aplicar**. MRTK analiza el proyecto para encontrar la configuración recomendada que falta cuando se importa para la configuración automatizada. En función de la configuración, el elemento emergente podría ser diferente de la imagen siguiente.

    ![Lesson1 Section3 Paso4 NOTE1](images/mrlearning-base-ch1-3-step4-note1.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>Configuración de Mixed Reality Toolkit

1. Agregue el *Kit de herramientas de realidad mixta* a la escena actual seleccionando el **Kit de herramientas de realidad mixta** > **Agregar a la escena y configurar.** en la barra de menús. Si no ves este elemento de menú después de importar Mixed Reality Toolkit, reinicia Unity.
    ![Lesson1 Section4 paso 1](images/mrlearning-base-ch1-4-step1.JPG)

    > [!NOTE]
    > Es posible que vea un cuadro de diálogo emergente para seleccionar un [perfil para el kit de herramientas de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html). Elija el perfil denominado *DefaultHoloLens2ConfigurationProfile* haciendo doble clic en él.

2. La escena tendrá varios elementos nuevos y modificaciones. Guarde la escena en un nombre diferente; para ello, haga clic en **archivo** > **Guardar como...** y asigne un nombre a la escena, como *BaseScene*. Mantenga la escena organizada guardándola en la carpeta *Scenes* de la carpeta *assets* del proyecto.
    ![Lesson1 Section4 Step2a](images/mrlearning-base-ch1-4-step2a.JPG) ![Lesson1 Section4 Step2b](images/mrlearning-base-ch1-4-step2b.JPG)

### <a name="build-your-application-to-your-device"></a>Compilación de la aplicación para el dispositivo

1. Si ha cerrado la ventana de *configuración de compilación* de las secciones anteriores, vuelva a abrir la ventana de *configuración* de compilación. para ello, vaya a **archivo** > **configuración de compilación**.
    ![Lesson1 Section5 paso 1](images/mrlearning-base-ch1-5-step1.JPG)

2. Asegúrese de que la escena que acaba de crear se encuentra en la lista *de escenas de la compilación* haciendo clic en el botón **Agregar escenas abiertas** mientras la escena está abierta en Unity.

3. Presione el botón **compilar** para comenzar el proceso de compilación.
    ![Lesson1 Section5 Step3](images/mrlearning-base-ch1-5-step3.JPG)

4. Crea y asigna un nombre a una nueva carpeta para la aplicación. En la imagen siguiente, se creó una carpeta con el nombre app que contiene la aplicación. Haga clic en **Seleccionar carpeta** para empezar a compilar en la carpeta que acaba de crear. Una vez completada la compilación, puede cerrar la ventana de configuración de la *compilación* en Unity.
    ![Lesson1 Section5 Paso4](images/mrlearning-base-ch1-5-step4.JPG)

  > [!IMPORTANT]
  > Si se produce un error en la compilación, intenta volver a compilar o reinicia Unity y vuelve a compilar. Si ve un error, como "error: CS0246 = no se encontró el tipo o el nombre de espacio de nombres" XX "(¿falta una directiva using o una referencia de ensamblado?). Si es así, es posible que deba instalar el [SDK de Windows 10 (10.0.18362.0)](https://developer.microsoft.com//windows/downloads/windows-10-sdk) .

5. Una vez finalizada la compilación, abre la carpeta recién creada que contiene los archivos de la aplicación que acabas de crear. Haga doble clic en la solución *MixedRealityBase. sln* o en el nombre correspondiente, si usó un nombre alternativo para el proyecto, para abrir el archivo de solución en Visual Studio.

    > [!NOTE]
    > Asegúrese de abrir la carpeta recién creada (es decir, la carpeta de la *aplicación* , si sigue las convenciones de nomenclatura de los pasos anteriores), ya que habrá un archivo. sln con el nombre similar fuera de esa carpeta que no debe confundirse con el archivo. sln dentro de la carpeta de compilación. La estructura de carpetas debe ser similar a la de la siguiente imagen.
    >
    > Si Visual Studio te pide que instales nuevos componentes, dedica un momento a comprobar que todos los componentes de requisitos previos estén instalados, tal como se especifica en la [página "Instalación de las herramientas"](install-the-tools.md).

    ![Lesson1 Section5 Paso5](images/mrlearning-base-ch1-5-step5.JPG)

6. Conecte HoloLens 2 a su equipo. Aunque estas instrucciones suponen que se va a implementar en un dispositivo HoloLens 2, también puede optar por implementar en el [emulador de hololens 2](using-the-hololens-emulator.md) o elegir crear un [paquete de aplicación para la instalación de prueba](<https://docs.microsoft.com//windows/uwp/packaging/packaging-uwp-apps>) .

    > [!IMPORTANT]
    > Antes de compilar en el dispositivo, el dispositivo debe estar en *modo de desarrollador* y emparejarse con el equipo de desarrollo. Estos dos pasos se pueden completar siguiendo [estas instrucciones](using-visual-studio.md) .

7. Configure Visual Studio para compilar en HoloLens 2 seleccionando la configuración de *lanzamiento* o *maestra* , la arquitectura de *ARM* y el *dispositivo* como destino.
    ![Lesson1 Section5 Step8](images/mrlearning-base-ch1-5-step7.JPG)

8. El paso final consiste en compilar e implementar en el dispositivo seleccionando **Depurar** > **iniciar sin depurar**. Al seleccionar *iniciar sin depurar* , la aplicación se inicia inmediatamente en el dispositivo tras una compilación correcta, pero sin el depurador adjunto y la información que aparece en Visual Studio. Esto también significa que puedes desconectar el cable USB mientras la aplicación se ejecuta en HoloLens 2 sin detener la aplicación.

    > [!NOTE]
    > También puede seleccionar **Compilar** > **implementar solución** para implementar en el dispositivo sin que la aplicación se inicie automáticamente.

    ![Lesson1 Section5 Step9](images/mrlearning-base-ch1-5-step8.JPG)

## <a name="congratulations"></a>Enhorabuena

Ya ha implementado su primera aplicación de HoloLens 2. A medida que recorra, debería ver una malla de asignación espacial que cubre todas las superficies que ha percibido por HoloLens 2. Además, debe ver indicadores sobre las manos y los dedos para el seguimiento de mano y un contador de velocidad de fotogramas para vigilar el rendimiento de la aplicación. Estos son solo algunas de las partes fundamentales, incluidas de fábrica en Mixed Reality Toolkit. En las lecciones que hay que seguir, comenzará a agregar más contenido e interactividad a su escena para que pueda explorar completamente las funcionalidades de HoloLens 2 y el kit de herramientas de realidad mixta.

> [!NOTE]
> En la aplicación, es posible que vea el generador de perfiles visual. Tratará cómo alternar el contador de velocidad de fotogramas mediante un comando de voz en la [Lección 5](mrlearning-base-ch5.md). Por lo general, se recomienda que el generador de perfiles visuales esté visible en todo momento durante el desarrollo para comprender cuándo los cambios de código pueden haber afectado al rendimiento. La aplicación HoloLens 2 se debe [Ejecutar continuamente a 60 fps](understanding-performance-for-mixed-reality.md).

[Lección siguiente: 3. crear la interfaz de usuario y configurar el kit de herramientas de realidad mixta](mrlearning-base-ch2.md)
