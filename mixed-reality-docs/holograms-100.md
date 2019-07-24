---
title: Sr Basics 100-Introducción a Unity
description: Aprenda a crear su primera aplicación básica "Hola a todos" de realidad mixta.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: realidad mixta, Windows Mixed Reality, HoloLens, inmersivo, VR, Mr, introducción, holograma, Academia, tutorial
ms.openlocfilehash: fd3bed955e80ec18b7be500adbdb0fcb7062d129
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993621"
---
>[!NOTE]
>Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.  Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

<br>

# <a name="mr-basics-100-getting-started-with-unity"></a>Principios básicos 100: Introducción a Unity

Este tutorial le guiará a través de la creación de una aplicación básica de realidad mixta compilada con Unity.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td>Principios básicos 100: Introducción a Unity</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Requisitos previos

* Un equipo con Windows 10 configurado con las [herramientas](install-the-tools.md)correctas instaladas.

## <a name="chapter-1---create-a-new-project"></a>Capítulo 1: crear un nuevo proyecto

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

Para compilar una aplicación con Unity, primero debe crear un proyecto. Este proyecto está organizado en algunas carpetas, lo más importante es la carpeta assets. Se trata de la carpeta que contiene todos los recursos que se importan desde herramientas de creación de contenido digital como Maya, Max Cinema 4D o Photoshop, todo el código que se crea con Visual Studio o su editor de código favorito y cualquier número de archivos de contenido que Unity crea al crear escenas , animaciones y otros tipos de recursos de Unity en el editor.

Para compilar e implementar aplicaciones UWP, Unity puede exportar el proyecto como una solución de Visual Studio que contendrá todos los archivos de recursos y de código necesarios.

1. Iniciar Unity
2. Seleccionar **nuevo**
3. Especifica un nombre de proyecto (por ejemplo, "MixedRealityIntroduction")
4. Escriba una ubicación para guardar el proyecto
5. Asegúrese de que la opción alternancia **3D** está seleccionada
6. Seleccione **crear proyecto** .

Enhorabuena, todo está configurado para empezar a trabajar con las personalizaciones de realidad mixta ahora.

## <a name="chapter-2---setup-the-camera"></a>Capítulo 2: configuración de la cámara

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

La cámara principal de Unity controla el seguimiento de los cabezales y la representación de Stereoscopic. Hay algunos cambios que se deben realizar en la cámara principal para usarlo con la realidad mixta.
1. Seleccionar archivo > nueva escena

En primer lugar, será más fácil diseñar la aplicación si imagina la posición inicial del usuario como (**X**: 0, **Y**: 0, **Z**: 0). Dado que la cámara principal está realizando el seguimiento del movimiento del usuario, la posición inicial del usuario se puede establecer estableciendo la posición inicial de la cámara principal.
1. Seleccionar **cámara principal** en el panel **jerarquía**
2. En el panel **Inspector** , busque el componente de **transformación** y cambie la **posición** de (**X**: 0, **Y**: 1, **Z**:-10) a (**X**: 0, **Y**: 0, **Z**: 0,1

En segundo lugar, hay que pensar en el fondo de la cámara predeterminada.

**En el caso de las aplicaciones de HoloLens**, el mundo real debe aparecer detrás de todo lo que representa la cámara, no una textura SKYBOX.
1. Con la **cámara principal** aún seleccionada en el **Panel jerarquía** , busque el **componente cámara** en el panel **Inspector** y cambie la lista desplegable **Borrar marcas** de **SKYBOX** a **color sólido**.
2. Seleccione el selector de colores de **fondo** y cambie los valores **RGBA** a (0, 0, 0, 0)

**En el caso de las aplicaciones de realidad mixta destinadas a auriculares**envolventes, podemos usar la textura SKYBOX predeterminada que proporciona Unity.
1. Con la **cámara principal** aún seleccionada en el panel **jerarquía** , busque el componente **cámara** en el panel **Inspector** y mantenga la lista desplegable **Borrar marcas** en **SKYBOX**.

En tercer lugar, permítanos considerar el plano de recorte cercano en Unity y evitar que los objetos se representen demasiado cerca de los ojos de los usuarios cuando un usuario se aproxime a un objeto o un objeto se aproxime a un usuario.

**En el caso de las aplicaciones de hololens**, el plano de recorte cercano se puede establecer en los contadores de 0,85 [recomendados de hololens](camera-in-unity.md#clip-planes) .
1. Con la **cámara principal** aún seleccionada en el panel **jerarquía** , busque el componente **cámara** en el panel **Inspector** y cambie el campo **Near Clip plano** del valor predeterminado **0,3** a HoloLens recomendado **0,85** .

**En el caso de las aplicaciones de realidad mixta destinadas a auriculares**envolventes, podemos usar la configuración predeterminada que proporciona Unity.
1. Con la **cámara principal** aún seleccionada en el  panel de jerarquías, busque el componente de **cámara** en el panel **Inspector** y mantenga el campo de **plano de clip cercano** al valor predeterminado **0,3**.

Por último, permítanos ahorrar nuestro progreso hasta ahora. Para guardar los cambios de la escena, seleccione **archivo > guardar escena como**, asigne un nombre a la escena **principal**y seleccione **Guardar**.

## <a name="chapter-3---setup-the-project-settings"></a>Capítulo 3: configuración del proyecto

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

En este capítulo, se establecerá una configuración de proyecto de Unity que nos ayude a dirigirse al SDK de Windows Holographic para el desarrollo. También estableceremos algunos valores de calidad para nuestra aplicación. Por último, se asegurará de que los destinos de compilación estén establecidos en tienda Windows.

### <a name="unity-performance-and-quality-settings"></a>Configuración de rendimiento y calidad de Unity

**Configuración de calidad de Unity para HoloLens**

![Configuración de calidad de Unity para HoloLens](images/qualitysettings.png) 

Dado que mantener una velocidad de fotogramas elevada en HoloLens es tan importante, queremos que la configuración de calidad esté optimizada para un rendimiento más rápido. Para obtener información más detallada sobre el rendimiento, [recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md).
1. Seleccione **editar > configuración del proyecto > calidad**
2. Seleccione la **lista desplegable** en el logotipo de la **tienda Windows** y seleccione **muy baja**. Sabrá que la configuración se aplica correctamente cuando el cuadro de la columna tienda Windows y la fila **muy baja** es verde.

En el **caso de las aplicaciones de realidad mixta destinadas a ocluidos**, puede dejar la configuración de calidad a sus valores predeterminados.

### <a name="target-windows-10-sdk"></a>SDK de Windows 10 de destino

**SDK de Windows Holographic de destino**

![SDK de Windows Holographic de destino](images/xrsettings.png) 

Necesitamos que Unity sepa que la aplicación que se está intentando exportar debe crear una [vista envolvente](app-views.md) en lugar de una vista 2D. Para ello, se habilita la compatibilidad con la realidad virtual en Unity que tiene como destino el SDK de Windows 10.
1. Vaya a **editar > configuración del proyecto > Player**.
2. En el **panel Inspector** de configuración del reproductor, seleccione el icono de la **tienda Windows** .
3. Expanda el grupo de **configuración de XR** .
4. En la sección **representación** , active la casilla **compatibilidad con realidad virtual** para agregar una nueva lista de **SDK de realidad virtual** .
5. Compruebe que **Windows Mixed Reality** aparece en la lista. Si no es así, **+** Seleccione el botón situado en la parte inferior de la lista y elija **Windows Mixed Reality**.

>[!NOTE]
>Si no ve el icono de la **tienda Windows** , asegúrese de que ha seleccionado el back-end de scripting .net de la tienda Windows antes de la instalación. Si no es así, es posible que tenga que volver a instalar Unity con la instalación de Windows correcta.

**Comprobar la configuración de .NET**

![Comprobar la configuración de .NET](images/configoptions-375px.png)

1. Vaya a **editar > configuración del proyecto > Player** (es posible que todavía lo tenga en el paso anterior).
2. En el **panel Inspector** de configuración del reproductor, seleccione el icono de la **tienda Windows** .
3. En la sección configuración de **otros valores** , asegúrese de que el **back-end** de scripting está establecido en **.net.**

Trabajo maravilla en la obtención de la configuración del proyecto aplicada. A continuación, vamos a agregar un holograma.

## <a name="chapter-4---create-a-cube"></a>Capítulo 4: crear un cubo

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

La creación de un cubo en el proyecto de Unity es igual que crear cualquier otro objeto en Unity. Colocar un cubo delante del usuario es fácil porque el sistema de coordenadas de Unity está asignado al mundo real, donde un medidor en Unity es aproximadamente un medidor del mundo real.
1. En la esquina superior izquierda del panel  de jerarquías, seleccione la lista desplegable **crear** y elija **objeto 3D > cubo**.
2. Seleccionar el **cubo** recién creado en el panel **jerarquía**
3. En el **Inspector** , busque el componente de **transformación** y cambie la **posición** a (**X**: 0, **Y**: 0, **Z**: 2). *Esto coloca los medidores del cubo 2 delante de la posición inicial del usuario.*
4. En el componente de **transformación** , cambie **rotación** a (**X**: 45, **Y**: 45, **Z**: 45) y cambie la **escala** a (**X**: 0,25, **Y**: 0,25, **Z**: 0,25). *Esto escala el cubo a 0,25 metros.*
5. Para guardar los cambios de la escena, seleccione **archivo > guardar escena**.

## <a name="chapter-5---verify-on-device-from-unity-editor"></a>Capítulo 5: comprobar en el dispositivo desde el editor de Unity

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

Ahora que hemos creado el cubo, es el momento de realizar una comprobación rápida del dispositivo. Puede hacerlo directamente desde el editor de Unity.

### <a name="initial-setup"></a>Configuración inicial
1. En el equipo de desarrollo, en Unity, Abra **archivo >** ventana de configuración de compilación.
2. Cambie **plataforma** a **plataforma universal de Windows** y haga clic en **cambiar Platform**

### <a name="for-hololens-use-unity-remoting"></a>Para HoloLens, use Unity Remoting
1. En HoloLens, instale y ejecute el [reproductor de comunicación remota holográfica](holographic-remoting-player.md), disponible en la tienda Windows. Inicie la aplicación en el dispositivo y se especificará un estado de espera y se mostrará la dirección IP del dispositivo. Anote la dirección IP.
2. Abra **Window > XR > la emulación holográfica**.
3. Cambiar el **modo** de emulación de **ninguno** a **remoto a dispositivo**.
4. En **equipo remoto**, escriba la dirección IP de su HoloLens indicada anteriormente.
5. Haga clic en **Conectar**.
6. Asegúrese de que el estado de la **conexión** cambia a verde **conectado**.
7. Ahora puede hacer clic en **reproducir** en el editor de Unity.

Ahora podrá ver el cubo en el dispositivo y en el editor. Puede pausar, inspeccionar objetos y depurar del mismo modo que está ejecutando una aplicación en el editor, ya que esto es esencialmente lo que está ocurriendo, pero con vídeo, audio y entrada de dispositivo transmitidos entre la red entre el equipo host y el dispositivo.

### <a name="for-other-mixed-reality-supported-headsets"></a>Para otros auriculares compatibles con la realidad mixta

1. Conecte los auriculares a su equipo de desarrollo con el cable USB y el cable de puerto de pantalla o HDMI.
2. Inicie el **portal de realidad mixta** y asegúrese de que ha completado la primera experiencia de ejecución.
3. Desde Unity, ahora puede hacer clic en el botón reproducir.

Ahora podrá ver la representación del cubo en el casco de la realidad mixta y en el editor.

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a>Capítulo 6: compilar e implementar en el dispositivo desde Visual Studio

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

Ahora estamos listos para compilar el proyecto en Visual Studio e implementarlo en nuestro dispositivo de destino.

### <a name="export-to-the-visual-studio-solution"></a>Exportar a la solución de Visual Studio
1.  Abra el **archivo > ventana Configuración de compilación** .
2.  Haga clic en **Agregar escenas abiertas** para agregar la escena.
3.  Cambie **plataforma** a **plataforma universal de Windows** y haga clic en **cambiar plataforma**.
4.  En configuración de la **tienda Windows** , asegúrese de que el **SDK** es **universal 10**.
5.  En dispositivo de destino, deje en **cualquier dispositivo** para ocluidos muestra o cambie a **HoloLens**.
6.  El **tipo de compilación de UWP** debe ser **D3D**.
7.  El **SDK de UWP** podría dejarse en la **versión más reciente instalada**.
8.  Compruebe **los C# proyectos de Unity** en depuración.
9.  Haz clic en **Compilación**.
10. En el explorador de archivos, haga clic en **nueva carpeta** y asigne el nombre **"app"** a la carpeta.
11. Con la carpeta de **aplicaciones** seleccionada, haga clic en el botón **Seleccionar carpeta** .
12. Cuando Unity termine de compilar, aparecerá una ventana del explorador de archivos de Windows.
13. Abra la carpeta de la **aplicación** en el explorador de archivos.
14. Abra la solución de Visual Studio generada (MixedRealityIntroduction. sln en este ejemplo).

### <a name="compile-the-visual-studio-solution"></a>Compilar la solución de Visual Studio

Por último, se compilará la solución de Visual Studio exportada, se implementará y se probará en el dispositivo.
1. Con la barra de herramientas superior de Visual Studio, cambie el destino de **Debug** a **Release** y de **ARM** a **x86**.

Las instrucciones difieren en cuanto a la implementación en un dispositivo frente al emulador. Siga las instrucciones que coincidan con la configuración.

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a>Implementación en dispositivo de realidad mixta a través de Wi-Fi
1. Haga clic en la flecha situada junto al botón **equipo local** y cambie el destino de implementación a **equipo remoto**.
2. Escriba la dirección IP del dispositivo de realidad mixta y cambie el **modo de autenticación** a universal (protocolo sin cifrar) para HoloLens y **Windows** para otros dispositivos.
3. Haga clic en depurar **> iniciar sin**depurar.

**En el caso de HoloLens**, si esta es la primera vez que se implementa en el dispositivo, tendrá que emparejar [con Visual Studio](using-visual-studio.md).

### <a name="deploy-to-mixed-reality-device-over-usb"></a>Implementación en dispositivo de realidad mixta a través de USB

Asegúrese de que el dispositivo está conectado a través del cable USB.
1. **Para HoloLens**, haga clic en la flecha situada junto al botón **equipo local** y cambie el destino de implementación a **dispositivo**.
2. **Para dirigirse a dispositivos ocluidos conectados al equipo**, mantenga la configuración en equipo local. Asegúrese de que tiene el **portal de realidad mixta** en ejecución.
3. Haga clic en depurar **> iniciar sin**depurar.

### <a name="deploy-to-emulator"></a>Implementar en el emulador
1. Haga clic en la flecha situada junto al botón **dispositivo** y, en la lista desplegable, seleccione emulador de **HoloLens**.
2. Haga clic en depurar **> iniciar sin**depurar.

### <a name="try-out-your-app"></a>Probar la aplicación

Ahora que la aplicación está implementada, intente mover todo el cubo y observe que permanece en todo el mundo.

## <a name="see-also"></a>Vea también
* [Introducción al desarrollo de Unity](unity-development-overview.md)
* [Procedimientos recomendados para trabajar con Unity y Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Principios de MR 101](holograms-101.md)
* [Aspectos básicos de MR 101E](holograms-101e.md)
