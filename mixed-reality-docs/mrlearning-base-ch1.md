---
title: 'Módulo base de aprendizaje de MR: Inicialización del proyecto y primera aplicación'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 51cfc123f7da8d25a53eecfb730f60cf10fe7377
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387783"
---
# <a name="2-initializing-your-project-and-first-application"></a>2. Inicializar el proyecto y la primera aplicación

En esta primera lección, obtendrá información sobre algunas de las funcionalidades que el kit de herramientas de realidad mixta (MRTK) tiene que ofrecer, iniciar su primera aplicación para HoloLens 2 e implementarla en el dispositivo.

## <a name="objectives"></a>Objetivos

* Optimizar Unity para el desarrollo de HoloLens.
* Importar recursos y configurar la escena.
* Visualización de la malla espacial, mallas de mano y del contador de velocidad de fotogramas.

## <a name="instructions"></a>Instrucciones

### <a name="create-new-unity-project"></a>Creación de un nuevo proyecto de Unity

1. Inicia Unity.
2. Selecciona **New** (Nuevo).
![Lección 1, capítulo 1, paso 2](images/Lesson1Chapter1Step2.JPG)
3. Especifica un nombre de proyecto (por ejemplo, "MixedRealityBase").
![Lección 1, capítulo 1, paso 3](images/Lesson1Chapter1Step3.JPG)
4. Escribe una ubicación para guardar el proyecto.
![Lección 1, capítulo 1, paso 4](images/Lesson1Chapter1Step4.JPG)
5. Asegúrate de que el proyecto esté establecido en **3D** (3D).
![Lección 1, capítulo 1, paso 5](images/Lesson1Chapter1Step5.JPG)
6. Haz clic en **Create Project** (Crear proyecto).
![Lección 1, capítulo 1, paso 6](images/Lesson1Chapter1Step6.JPG)

### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Configuración del proyecto de Unity para Windows Mixed Reality

1. Para abrir la ventana Configuración de compilación, vaya a archivo > configuración de compilación.
![Lección 1, capítulo 4, paso 1](images/Lesson1Chapter4Step1.JPG)
2. Cambie a Plataforma universal de Windows seleccionando Plataforma universal de Windows. Haga clic en el botón cambiar plataforma para cambiar plataformas. Las aplicaciones que se ejecutan en HoloLens 2 deben ser compatibles con Plataforma universal de Windows (UWP).
![Lección 1, capítulo 4, paso 2](images/Lesson1Chapter4Step2.JPG)
3. Habilite la realidad virtual; para ello, haga clic en configuración del reproductor en la ventana compilar y active la casilla compatibilidad con la realidad virtual en la configuración de XR del panel Inspector, tal como se muestra en la imagen siguiente. Tenga en cuenta que es posible que tenga que arrastrar la ventana Configuración de compilación fuera de la pantalla para ver el panel del inspector. La casilla compatibilidad con la realidad virtual también se aplica a los auriculares de realidad mixta y de realidad aumentada porque hace referencia a la habilitación de Stereoscopic Vision (representación de imágenes diferentes para cada ojo). ![Lección 1, capítulo 4, paso3](images/Lesson1Chapter4Step3.JPG)
4. En el mismo panel Inspector, asegúrese de que la casilla percepción espacial en la sección capacidades está habilitada en configuración de publicación. La percepción espacial nos permite visualizar la malla de asignación espacial en un dispositivo de realidad mixta, como HoloLens 2. La configuración de publicación se encuentra en el panel Inspector, encima de la configuración de XR y en otras opciones.
![Lección 1, capítulo 4, paso 4](images/Lesson1Chapter4Step4.JPG)

> Nota: Aunque no se usa en esta sección, algunas otras funcionalidades comunes que podría desear habilitar incluyen el micrófono para comandos de voz y InternetClient para conectarse a los servicios que requieren una conexión de red.

### <a name="import-the-mixed-reality-toolkit"></a>Importación de Mixed Reality Toolkit

1. Descargue el paquete de Unity del [Kit de herramientas de realidad mixta](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1.unitypackage) y guárdelo en una carpeta de su equipo.

2. Para importar el paquete Mixed Reality Toolkit, haz clic en Assets>Import>Custom Package (Recursos>Importar>Paquete personalizado). Busca el paquete Mixed Reality Toolkit descargado en el paso 1 y ábrelo para comenzar el proceso de importación. Espera unos minutos hasta que termine el proceso de importación.
    ![Lección 1, capítulo 2, paso 2a](images/Lesson1Chapter2Step2a.JPG) ![Lección 1, capítulo 2, paso 2b](images/Lesson1Chapter2Step2b.JPG)

3. En la siguiente ventana emergente, haga clic en importar para empezar a importar el kit de herramientas de realidad mixta. Asegúrese de que todos los elementos se comprueban como se muestra en la imagen. Si ve un cuadro de diálogo emergente que le pide aplicar la configuración predeterminada del kit de herramientas de realidad mixta, haga clic en aplicar.
    ![Lección 1, capítulo 2, paso 3](images/Lesson1Chapter2Step3.JPG) ![Lección 1, capítulo 2, paso 3](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>Configuración de Mixed Reality Toolkit

1. Configure el MRTK seleccionando el kit de herramientas de realidad mixta > configurar en la barra de menús. Si no ves este elemento de menú después de importar Mixed Reality Toolkit, reinicia Unity.
  ![Lección 1, capítulo 3, paso 1](images/Lesson1Chapter3Step1.JPG)

  > Nota: Es posible que vea un cuadro de diálogo emergente en el que se le pide que seleccione un perfil para el kit de herramientas de realidad mixta. Si es así, seleccione Aceptar y elija el perfil denominado "DefaultMixedRealityToolkitConfigurationProfile".

2. La escena tendrá varios elementos nuevos y modificaciones en ella desde MRTK. Guarde la escena en un nombre diferente; para ello, haga clic en archivo > Guardar como y asigne un nombre a la escena, como BaseScene. Mantenga la escena organizada guardándola en la carpeta Scenes de la carpeta assets del proyecto.
  ![Lección 1, capítulo 3, paso 2a](images/Lesson1Chapter3Step2a.JPG)
  ![Lección 1, capítulo 3, paso 2b](images/Lesson1Chapter3Step2b.JPG)

### <a name="build-your-application-to-your-device"></a>Compilación de la aplicación para el dispositivo

1. Si ha cerrado la ventana de configuración de compilación de las secciones anteriores, vuelva a abrir la ventana de configuración de compilación. para ello, vaya a archivo > configuración de compilación.
    ![Lección 1, capítulo 5, paso 1](images/Lesson1Chapter5Step1.JPG)

2. Asegúrese de que la escena que desea probar está en la lista de escenas de la compilación haciendo clic en el botón Agregar escenas abiertas.

3. Presiona el botón Build (Compilar) para comenzar el proceso de compilación.
    ![Lección 1, capítulo 5, paso 3](images/Lesson1Chapter5Step3.JPG)

4. Crea y asigna un nombre a una nueva carpeta para la aplicación. En la imagen siguiente, se creó una carpeta con el nombre app que contiene la aplicación. Haga clic en Seleccionar carpeta para empezar a compilar en la carpeta que acaba de crear. Una vez completada la compilación, puede cerrar la ventana de configuración de la compilación en Unity. 
    ![Lección 1, capítulo 5, paso 4](images/Lesson1Chapter5Step4.JPG)

  > Nota: Si se produce un error en la compilación, intenta volver a compilar o reinicia Unity y vuelve a compilar. Si ve un error, como "error: CS0246 = no se pudo encontrar el tipo o el nombre de espacio de nombres "XX" (¿falta una directiva using o una referencia de ensamblado?). Si es así, es posible que deba instalar el [SDK de Windows 10 (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>) .
  >

5. Una vez finalizada la compilación, abre la carpeta recién creada que contiene los archivos de la aplicación que acabas de crear. Haga doble clic en la solución MixedRealityBase. sln o en el nombre correspondiente, si usó un nombre alternativo para el proyecto, para abrir el archivo de solución en Visual Studio.

  > Nota: Asegúrese de abrir la carpeta recién creada (es decir, la carpeta de la aplicación, si sigue las convenciones de nomenclatura de los pasos anteriores), ya que habrá un archivo. sln con el nombre similar fuera de esa carpeta que no debe confundirse con el archivo. sln dentro de la carpeta de compilación. 

![Lección 1, capítulo 5, paso 5](images/Lesson1Chapter5Step5.JPG)

  > Nota: Si Visual Studio te pide que instales nuevos componentes, dedica un momento a comprobar que todos los componentes de requisitos previos estén instalados, tal como se especifica en la [página "Instalación de las herramientas"](install-the-tools.md).

6. Conecte HoloLens 2 a su equipo. Aunque estas instrucciones suponen que va a implementar una prueba con un dispositivo HoloLens 2, también puede optar por implementarla en el emulador de [hololens 2](using-the-hololens-emulator.md) o elegir crear un [paquete de aplicación para la instalación de prueba](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>) .

7. Antes de compilar en el dispositivo, comprueba que el dispositivo está en modo de desarrollador. Si esta es la primera vez que implementa en HoloLens 2, es posible que Visual Studio le pida que empareje su HoloLens 2 con un PIN. Sigue [estas instrucciones](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) si tienes que habilitar el modo de desarrollador o emparejar con Visual Studio.

8. Configure Visual Studio para compilar en HoloLens 2 seleccionando la configuración de lanzamiento y la arquitectura ARM.
    ![Lección 1, capítulo 5, paso 8](images/Lesson1Chapter5Step8.JPG)

9. El paso final consiste en compilar en el dispositivo seleccionando Depurar > iniciar sin depurar. Al seleccionar iniciar sin depurar, la aplicación se inicia inmediatamente en el dispositivo tras una compilación correcta, pero sin la información de depuración que aparece en Visual Studio. Esto también significa que puedes desconectar el cable USB mientras la aplicación se ejecuta en HoloLens 2 sin detener la aplicación. También puede seleccionar compilar > implementar solución para implementar en el dispositivo sin que la aplicación se inicie automáticamente.
    ![Lección 1, capítulo 5, paso 9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>Enhorabuena

Ya ha implementado su primera aplicación de HoloLens 2. A medida que recorra, debería ver una malla espacial que cubre todas las superficies percibidas por HoloLens 2. Además, debe ver indicadores sobre las manos y los dedos para el seguimiento de mano y un contador de velocidad de fotogramas para vigilar el rendimiento de la aplicación. Estos son solo algunas de las partes fundamentales, incluidas de fábrica en Mixed Reality Toolkit. En las lecciones que hay que seguir, empiece a agregar más contenido e interactividad a su escena para que pueda explorar completamente las funcionalidades de HoloLens 2 y el kit de herramientas de la realidad mixta.

>Nota: Verás cómo alternar el contador de velocidad de fotogramas mediante un comando de voz en la [Lección 5](mrlearning-base-ch5.md)

[Próxima lección: Interfaz de usuario, seguimiento con la mano y configuración de Mixed Reality Toolkit](mrlearning-base-ch2.md)
