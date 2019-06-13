---
title: 'Módulo base de aprendizaje de MR: Inicialización del proyecto y primera aplicación'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
ms.localizationpriority: high
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: c5490e6a3b542a5ca677b309e5ed1171f8666fe7
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "65814009"
---
# <a name="mr-learning-base-module---project-initialization-and-first-application"></a>Módulo base de aprendizaje de MR: Inicialización del proyecto y primera aplicación

En esta primera lección, obtendrás información sobre algunas de las funcionalidades que ofrece Mixed Reality Toolkit, iniciarás tu primera aplicación para HoloLens 2 y la implementarás en el dispositivo.

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

1. Abre la ventana de configuración de compilación en File>Build Settings (Archivo>Configuración de compilación).
![Lección 1, capítulo 4, paso 1](images/Lesson1Chapter4Step1.JPG)
2. Cambia a "Plataforma universal de Windows" seleccionando "Universal Windows Platform" (Plataforma universal de Windows) y, después, haz clic en el botón "Switch Platform" (Cambiar plataforma) para cambiar de plataforma. Las aplicaciones que se ejecutan en HoloLens 2 tienen que ser de la plataforma universal de Windows (UWP).
![Lección 1, capítulo 4, paso 2](images/Lesson1Chapter4Step2.JPG)
3. Para habilitar la realidad virtual, haz clic en Player Settings (Configuración del Reproductor) en la ventana de compilación, a continuación, en el panel del inspector habilita la casilla "Virtual Reality Supported" (Se admite Virtual Reality) en XR Settings (Configuración de XR), tal como se muestra en la imagen siguiente. Ten en cuenta que es posible que necesites arrastrar la ventana "Build Settings" (Configuración de compilación) a un lado para ver el panel del inspector. La casilla "Virtual Reality Supported"(Se admite Virtual Reality) también se aplica a los cascos de Mixed Reality / AR porque hace referencia a la habilitación de la visión estereoscópica (representa imágenes diferentes para cada ojo). ![Lección 1, capítulo 4, paso3](images/Lesson1Chapter4Step3.JPG)
4. En el mismo panel del inspector, comprueba que la casilla "Spatial Perception" (Percepción espacial) en la sección de funcionalidades esté habilitada, en Publishing Settings (Configuración de publicación). La percepción espacial nos permitirá ver la malla de asignación espacial en un dispositivo de realidad mixta, como HoloLens 2. La configuración de publicación se encuentra en el panel del inspector, sobre "XR Settings" (Configuración de XR) y bajo "Other Settings" (Otra configuración).
![Lección 1, capítulo 4, paso 4](images/Lesson1Chapter4Step4.JPG)

> Nota: Aunque no se usan en esta sección, otras funcionalidades comunes que es posible que desees habilitar incluyen Micrófono (para comandos de voz) e InternetClient (para conectarse a los servicios que requieren una conexión de red)

### <a name="import-the-mixed-reality-toolkit"></a>Importación de Mixed Reality Toolkit

1. Descarga el paquete de Unity [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1.unitypackage) y guárdalo en una carpeta de tu equipo.

2. Para importar el paquete Mixed Reality Toolkit, haz clic en Assets>Import>Custom Package (Recursos>Importar>Paquete personalizado). Busca el paquete Mixed Reality Toolkit descargado en el paso 1 y ábrelo para comenzar el proceso de importación. Espera unos minutos hasta que termine el proceso de importación.
    ![Lección 1, capítulo 2, paso 2a](images/Lesson1Chapter2Step2a.JPG) ![Lección 1, capítulo 2, paso 2b](images/Lesson1Chapter2Step2b.JPG)

3. En la siguiente ventana emergente, haz clic en "Import" (Importar) para comenzar a importar Mixed Reality Toolkit. Comprueba que estén seleccionados todos los elementos, tal como se muestra en la imagen. Si ves un cuadro de diálogo emergente que solicita si deseas aplicar la configuración predeterminada de Mixed Reality Toolkit, haz clic en "Apply" (Aplicar).
    ![Lección 1, capítulo 2, paso 3](images/Lesson1Chapter2Step3.JPG) ![Lección 1, capítulo 2, paso 3](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>Configuración de Mixed Reality Toolkit

1. Configura Mixed Reality Toolkit seleccionando en la barra de menús Mixed Reality Toolkit>Configure (Configurar). Si no ves este elemento de menú después de importar Mixed Reality Toolkit, reinicia Unity.
![Lección 1, capítulo 3, paso 1](images/Lesson1Chapter3Step1.JPG)
2. La escena tendrá ahora varios elementos nuevos y modificaciones en ella procedentes de Mixed Reality Toolkit. Guarda la escena con un nombre diferente haciendo clic en File>Save As (Archivo>Guardar como) y asígnale un nombre, por ejemplo, BaseScene. Mantén la escena organizada guardándola en la carpeta "Scenes" (Escenas) de la carpeta Assets (Recursos) del proyecto.
![Lección 1, capítulo 3, paso 2a](images/Lesson1Chapter3Step2a.JPG)
![Lección 1, capítulo 3, paso 2b](images/Lesson1Chapter3Step2b.JPG)

### <a name="build-your-application-to-your-device"></a>Compilación de la aplicación para el dispositivo

1. Si has cerrado la ventana Build Settings (Configuración de compilación) de las secciones anteriores, abre de nuevo la ventana de configuración de compilación en File>Build Settings (Archivo>Configuración de compilación).
    ![Lección 1, capítulo 5, paso 1](images/Lesson1Chapter5Step1.JPG)

2. Comprueba que la escena que deseas probar está en la lista "Scenes in Build" (Escenas en compilación) haciendo clic en el botón "Add Open Scenes" (Agregar escenas abiertas).

3. Presiona el botón Build (Compilar) para comenzar el proceso de compilación.
    ![Lección 1, capítulo 5, paso 3](images/Lesson1Chapter5Step3.JPG)

4. Crea y asigna un nombre a una nueva carpeta para la aplicación. En la imagen siguiente, se ha creado una carpeta con el nombre "App" (Aplicación) para contener la aplicación. Haz clic en "Select Folder" (Seleccionar carpeta) para empezar a compilar la carpeta recién creada. Una vez finalizada la compilación, puedes cerrar la ventana "Build Settings" (Configuración de compilación) en Unity. 
    ![Lección 1, capítulo 5, paso 4](images/Lesson1Chapter5Step4.JPG)

  > Nota: Si se produce un error en la compilación, intenta volver a compilar o reinicia Unity y vuelve a compilar. Si ves un error como "Error: CS0246 = The type or namespace name “XX” could not be found (are you missing a using directive or an assembly reference?)" [Error: CS0246 = No se encontró el nombre de tipo o de espacio de nombres "XX" (¿te falta una directiva de uso o una referencia de ensamblado?)", es posible que debas instalar [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)]
  >

5. Una vez finalizada la compilación, abre la carpeta recién creada que contiene los archivos de la aplicación que acabas de crear. Haz doble clic en la solución "MixedRealityBase.sln" (o el nombre correspondiente, si has utilizado un nombre alternativo para el proyecto) para abrir el archivo de la solución en Visual Studio.

  > Nota: Asegúrate de abrir la carpeta recién creada [es decir, la carpeta "App" (Aplicaciones), si ha seguido las convenciones de nomenclatura de los pasos anteriores], ya que habrá un archivo .sln con el mismo nombre fuera de esa carpeta que no debes confundir con el archivo .sln dentro de la carpeta de compilación. 

![Lección 1, capítulo 5, paso 5](images/Lesson1Chapter5Step5.JPG)

  > Nota: Si Visual Studio te pide que instales nuevos componentes, dedica un momento a comprobar que todos los componentes de requisitos previos estén instalados, tal como se especifica en la [página "Instalación de las herramientas"](install-the-tools.md).

6. Conecta HoloLens 2 a tu equipo con el cable USB. Aunque en estas instrucciones de la lección se supone que vas a implementar una prueba con un dispositivo HoloLens 2, también puedes optar por realizar la implementación en el [emulador de HoloLens 2](using-the-hololens-emulator.md) o decidir crear un [paquete de la aplicación para una transferencia local](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>).

7. Antes de compilar en el dispositivo, comprueba que el dispositivo está en modo de desarrollador. Si es la primera vez que estás realizando una implementación en HoloLens 2, Visual Studio puede pedirte que emparejes HoloLens 2 con un PIN. Sigue [estas instrucciones](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) si tienes que habilitar el modo de desarrollador o emparejar con Visual Studio.

8. Configura Visual Studio para compilar HoloLens 2 seleccionando la configuración "Release" (Liberar) y la arquitectura "ARM".
    ![Lección 1, capítulo 5, paso 8](images/Lesson1Chapter5Step8.JPG)

9. El último paso es compilar en el dispositivo seleccionando Depurar>Iniciar sin depurar. Al seleccionar "Iniciar sin depurar", la aplicación se iniciará de inmediato en el dispositivo tras una compilación correcta, pero sin que la información de depuración aparezca en Visual Studio. Esto también significa que puedes desconectar el cable USB mientras la aplicación se ejecuta en HoloLens 2 sin detener la aplicación. También puedes seleccionar Compilar>Implementar solución para realizar una implementación en el dispositivo sin necesidad de que se reinicie automáticamente la aplicación.
    ![Lección 1, capítulo 5, paso 9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>Enhorabuena

Ya has implementado tu primera aplicación de HoloLens 2. Al ir avanzando, deberías ver una malla espacial que cubre todas las superficies que HoloLens 2 ha percibido. Además, deberías ver los indicadores en las manos y los dedos para el seguimiento con la mano, así como un contador de velocidad de fotogramas para vigilar el rendimiento de la aplicación. Estos son solo algunas de las partes fundamentales, incluidas de fábrica en Mixed Reality Toolkit. En las lecciones siguientes, comenzarás a agregar más contenido e interactividad a la escena, para que puedas explorar totalmente las funcionalidades de HoloLens 2 y Mixed Reality Toolkit.

>Nota: Verás cómo alternar el contador de velocidad de fotogramas mediante un comando de voz en la [Lección 5](mrlearning-base-ch5.md)

[Próxima lección: Interfaz de usuario, seguimiento con la mano y configuración de Mixed Reality Toolkit](mrlearning-base-ch2.md)
