---
title: 'Módulo MR Learning Base: inicialización del proyecto y la primera aplicación'
description: Realice este curso para obtener información sobre cómo implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidad mixta, unity, tutorial, hololens
ms.openlocfilehash: 95ba00d68eb5fb6c990ddee343ac58ebe00dbb10
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993646"
---
# <a name="mr-learning-base-module---project-initialization-and-first-application"></a>Módulo MR Learning Base: inicialización del proyecto y la primera aplicación

En esta primera lección, obtendrá información sobre algunas de las funcionalidades que el Kit de herramientas de realidad mixta tiene que ofrecer, iniciar su primera aplicación para el 2 de HoloLens e implementarlo en el dispositivo.

## <a name="objectives"></a>Objetivos

* Optimizar el desarrollo de HoloLens Unity.
* Importar recursos y configuración de la escena.
* Visualización de la malla espacial, mallas de mano y el contador de velocidad de fotogramas.

## <a name="instructions"></a>Instrucciones

### <a name="create-new-unity-project"></a>Crear nuevo proyecto de Unity

1. Inicie Unity.
2. Selecciona **New**.
![Lección 1 Chapter1 Step2](images/Lesson1Chapter1Step2.JPG)
3. Escriba un nombre de proyecto (por ejemplo "MixedRealityBase").
![Lección 1 Chapter1 Step3](images/Lesson1Chapter1Step3.JPG)
4. Escriba una ubicación para guardar el proyecto.
![Lección 1 Chapter1 paso4](images/Lesson1Chapter1Step4.JPG)
5. Asegúrese de que el proyecto está establecido en **3D**.
![Lección 1 Chapter1 paso5](images/Lesson1Chapter1Step5.JPG)
6. Haga clic en **crear proyecto**.
![Lección 1 Chapter1 paso6](images/Lesson1Chapter1Step6.JPG)

### <a name="configure-the-unity-project-for-windows-mixed-reality"></a>Configurar el proyecto de Unity para Windows Mixed Reality

1. Abra la ventana de configuración de compilación, vaya a archivo > configuración de compilación.
![Lección 1 Capítulo4 Step1](images/Lesson1Chapter4Step1.JPG)
2. Cambie a "Universal Windows Platform" seleccionando "Plataforma Universal de Windows" y, a continuación, haga clic en el botón "Cambiar plataforma" para cambiar la plataforma. Aplicaciones que se ejecutan en HoloLens 2 tienen que ser la plataforma Universal de Windows (UWP).
![Lección 1 Capítulo4 Step2](images/Lesson1Chapter4Step2.JPG)
3. Habilitar la realidad virtual, haga clic en configuración del Reproductor en la ventana de compilación y, a continuación, en el panel del inspector habilite la casilla "Compatible de realidad Virtual" XR configuración, tal como se muestra en la imagen siguiente. Tenga en cuenta que es posible que necesite arrastrar la ventana de "Configuración de compilación" fuera de la vista para ver el panel del inspector. La casilla "Compatible de realidad Virtual" también se aplica a la realidad mixta / auriculares AR porque hace referencia a la habilitación de visión estereoscópica (representar imágenes diferentes para cada ojo). ![Lección 1 Capítulo4 Step3](images/Lesson1Chapter4Step3.JPG)
4. En el mismo panel del inspector, compruebe que la casilla de verificación "Percepción espacial" en la sección de capacidades está habilitada en la configuración de publicación. Percepción espacial nos permitirá visualizar la malla de asignación espacial en un dispositivo de realidad mixta, como el 2 de HoloLens. Configuración de publicación se encuentra en el panel del Inspector, "Configuración XR" anterior y en "Otras opciones."
![Lección 1 Capítulo4 paso4](images/Lesson1Chapter4Step4.JPG)

> Nota: Aunque no se usan en esta sección, otras funcionalidades comunes que desea habilitar incluyen micrófono (para los comandos de voz) y InternetClient (para conectarse a los servicios que requieren una conexión de red)

### <a name="import-the-mixed-reality-toolkit"></a>Importar el Kit de herramientas de realidad mixta

1. Descargue el [Kit de herramientas de realidad mixta](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/download/v2.0.0-RC1/Microsoft.MixedReality.Toolkit.Unity.Foundation-v2.0.0-RC1.unitypackage) unity del paquete y guárdelo en una carpeta en su PC.

2. Importar el paquete del Kit de herramientas de realidad mixta haciendo clic en los activos > Importar > paquete personalizado. Busque el paquete del Kit de herramientas de realidad mixta descargado en el paso 1 y ábralo para comenzar el proceso de importación. Espere unos minutos para el proceso de importación.
    ![Lección 1 Chapter2 Step2a](images/Lesson1Chapter2Step2a.JPG) ![Lesson1 Chapter2 Step2b](images/Lesson1Chapter2Step2b.JPG)

3. En la siguiente ventana emergente, haga clic en "Importar" para comenzar a importar el Kit de herramientas de realidad mixta. Asegúrese de se comprueban todos los elementos, como se muestra en la imagen. Si ve un cuadro de diálogo emergente que pregunta si desea aplicar la configuración predeterminada de Kit de herramientas de realidad mixta, haga clic en "Aplicar".
    ![Lección 1 Chapter2 Step3](images/Lesson1Chapter2Step3.JPG) ![Lesson1 Chapter2 Step3](images/Lesson1Chapter2Step3b.JPG)

### <a name="configure-the-mixed-reality-toolkit"></a>Configurar el Kit de herramientas de realidad mixta

1. Configurar el Kit de herramientas mixto mediante la selección en el Kit de herramientas de realidad mixta de la barra de menús > Configurar. Si no ve este elemento de menú después de importar el Kit de herramientas de realidad mixta, reinicie Unity.
![Paso 1 del capítulo 3 de lección 1](images/Lesson1Chapter3Step1.JPG)
2. La escena ahora tendrá varios elementos nuevos y modificaciones en ella desde el Kit de herramientas de realidad mixta. Guardar la escena con un nombre diferente, haga clic en archivo > Guardar como y asigne un nombre, por ejemplo, BaseScene a la escena. Mantenga su escena organizada por guardarlo en la carpeta de "Plano" en la carpeta del proyecto activos.
![Lección 1 capítulo 3 Step2a](images/Lesson1Chapter3Step2a.JPG)
![Lesson1 capítulo 3 Step2b](images/Lesson1Chapter3Step2b.JPG)

### <a name="build-your-application-to-your-device"></a>Compile la aplicación para el dispositivo

1. Si cierra la ventana de configuración de compilación de las secciones anteriores, la ventana de configuración de compilación vuelva a abrir, vaya a archivo > configuración de compilación.
    ![Lección 1 Chapter5 Step1](images/Lesson1Chapter5Step1.JPG)

2. Asegúrese de que la escena que desea probar está en la lista "Escenas en compilación" haciendo clic en el botón "Agregar escenas abierto".

3. Presione el botón Generar para comenzar el proceso de compilación.
    ![Lección 1 Chapter5 Step3](images/Lesson1Chapter5Step3.JPG)

4. Cree y asigne el nombre de una nueva carpeta para la aplicación. En la imagen siguiente, una carpeta con el nombre "App" se creó para que contenga la aplicación. Haga clic en "Seleccionar la carpeta" para empezar a crear la carpeta recién creada. Una vez finalizada la compilación, puede cerrar la ventana de "Configuración de compilación" en Unity. 
    ![Lección 1 Chapter5 paso4](images/Lesson1Chapter5Step4.JPG)

  > Nota: Si se produce un error en la compilación, intente volver a compilar o reiniciar Unity y volver a compilar. Si ve un error "Error: CS0246 = "XX" no se encontró el nombre de tipo o espacio de nombres (¿falta un uso de directiva o una referencia de ensamblado?) ", a continuación, es posible que deba instalar [Windows 10 SDK (10.0.18362.0)](<https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk>)
  >

5. Una vez completada la compilación, abra la carpeta recién creada que contiene los archivos de aplicación recién creada. Haga doble clic en la solución "MixedRealityBase.sln" (o el nombre correspondiente, si ha usado un nombre alternativo para el proyecto) para abrir el archivo de solución en Visual Studio.

  > Nota: Asegúrese de abrir el recién creada (es decir, la carpeta "App", si sigue las convenciones de nomenclatura de los pasos anteriores), tal como habrá un archivo .sln con el mismo nombre fuera de esa carpeta que no debe confundirse con el archivo .sln dentro de la carpeta de compilación. 

![Lección 1 Chapter5 paso5](images/Lesson1Chapter5Step5.JPG)

  > Nota: Si Visual Studio le pide que instale los nuevos componentes, dedique un momento para asegurarse de que todos los componentes de requisitos previos se instalan como se especifica en [la página "Instalar las herramientas"](install-the-tools.md)

6. Conecte el 2 de HoloLens en su PC con el cable USB. Aunque estas instrucciones de la lección se suponen que va a implementar una prueba con un dispositivo HoloLens 2, también puede optar por implementar en el [emulador de HoloLens 2](using-the-hololens-emulator.md) o elegir crear un [paquete de aplicación de instalación de prueba](<https://docs.microsoft.com/en-us/windows/uwp/packaging/packaging-uwp-apps>)

7. Antes de compilar para el dispositivo, asegúrese de que el dispositivo está en modo de programador. Si se trata de la primera vez que la implementación en el 2 de HoloLens, Visual Studio puede pedirle que emparejar el 2 de HoloLens con un pin. Siga [estas instrucciones](https://docs.microsoft.com/en-us/windows/mixed-reality/using-visual-studio) si tiene que habilitar el modo de programador o emparejarse con Visual Studio.

8. Configurar Visual Studio para compilar el 2 de HoloLens seleccionando la configuración "Release" y la arquitectura de "ARM".
    ![Lección 1 Chapter5 Step8](images/Lesson1Chapter5Step8.JPG)

9. El último paso es crear en el dispositivo seleccionando Depurar > Iniciar sin depurar. Seleccione "Iniciar sin depurar" hará que la aplicación iniciar inmediatamente en el dispositivo tras una compilación correcta, pero sin información de depuración que aparece en Visual Studio. Esto también significa que puede desconectar el cable USB mientras la aplicación se ejecuta en el 2 de HoloLens sin detener la aplicación. También puede seleccionar compilación > implementar la solución para implementar en el dispositivo sin necesidad de la aplicación se inicie automáticamente.
    ![Lección 1 Chapter5 Step9](images/Lesson1Chapter5Step9.JPG)

## <a name="congratulations"></a>Enhorabuena

Ahora ha implementado su primera aplicación de HoloLens 2. Como andar, debería ver una malla espacial cubrir todas las superficies que han sido percibe el 2 de HoloLens. Además, debería ver los indicadores en las manos y los dedos para seguimiento de mano y un contador de velocidad de fotogramas para perder de vista en el rendimiento de la aplicación. Estos son sólo algunas de las partes fundamentales, incluidas de fábrica, con el Kit de herramientas de realidad mixta. En las lecciones para proceder, se iniciará agregar más contenido e interactividad a la escena, por lo que puede explorar completamente las capacidades de los 2 HoloLens y el Kit de herramientas de realidad mixta.

>Nota: Se explica cómo activar o desactivar el contador de velocidad de fotogramas mediante un comando de voz en [lección 5](mrlearning-base-ch5.md)

[Próxima lección: Interfaz de usuario, realiza el seguimiento y mixto realidad configuración del Kit de herramientas de mano](mrlearning-base-ch2.md)
