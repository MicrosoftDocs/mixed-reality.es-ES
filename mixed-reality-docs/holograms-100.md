---
title: Conceptos básicos de MR 100 - Introducción a Unity
description: Aprenda a crear su primera aplicación de realidad mixta básica "Hola mundo".
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, la realidad mixta HoloLens, envolvente, vr, mr, empezar a trabajar, holograma, academy, tutorial
ms.openlocfilehash: fd3bed955e80ec18b7be500adbdb0fcb7062d129
ms.sourcegitcommit: aa88f6b42aa8d83e43104b78964afb506a368fb4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/02/2019
ms.locfileid: "64993621"
---
>[!NOTE]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.  Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.  Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.

<br>

# <a name="mr-basics-100-getting-started-with-unity"></a>Conceptos básicos de MR 100: Introducción a Unity

Este tutorial le guiará a través de la creación de una aplicación básica de realidad mixta creada con Unity.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td>Conceptos básicos de MR 100: Introducción a Unity</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="prerequisites"></a>Requisitos previos

* Un equipo con Windows 10 configurado con el valor correcto [herramientas instaladas](install-the-tools.md).

## <a name="chapter-1---create-a-new-project"></a>Capítulo 1: crear un nuevo proyecto

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

Para compilar una aplicación con Unity, primero deberá crear un proyecto. Este proyecto está organizado en algunas carpetas, el más importante es la carpeta de recursos. Esta es la carpeta que contiene todos los recursos de que importar desde herramientas de creación de contenido digital, como Maya, Máx cine 4D o Photoshop, todo el código que cree con Visual Studio o el editor de código favorito y cualquier número de archivos de contenido que Unity crea al crear escenas , animaciones y otros tipos de activos de Unity en el editor.

Para compilar e implementar aplicaciones para UWP, Unity puede exportar el proyecto como una solución de Visual Studio que contendrá todos los activos necesarios y los archivos de código.

1. Inicie Unity
2. Seleccione **nuevo**
3. Escriba un nombre de proyecto (por ejemplo "MixedRealityIntroduction")
4. Especifique una ubicación para guardar el proyecto
5. Asegúrese del **3D** se selecciona el botón de alternancia
6. Seleccione **crear un proyecto**

Enhorabuena, son toda la configuración para empezar a trabajar con las personalizaciones de realidad mixta ahora.

## <a name="chapter-2---setup-the-camera"></a>Capítulo 2: instalación de la cámara

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

La cámara principal de Unity controla la cabeza de seguimiento y representación estereoscópica. Hay pocos cambios que realice en la cámara principal se usa con la realidad mixta.
1. Seleccione Archivo > nueva escena

En primer lugar, será más fácil diseñar la aplicación si imaginar la posición inicial del usuario como (**X**: 0, **Y**: 0, **Z**: 0). Puesto que la cámara principal está realizando el seguimiento movimiento del encabezado del usuario, se puede establecer la posición inicial del usuario al establecer la posición inicial de la cámara principal.
1. Seleccione **cámara principal** en el **jerarquía** panel
2. En el **Inspector** panel, busque el **transformar** componente y cambie el **posición** desde (**X**: 0, **Y**: 1, **Z**: -10) a (**X**: 0, **Y**: 0, **Z**: 0)

En segundo lugar, el fondo predeterminado de la cámara necesita un gran esfuerzo.

**Para las aplicaciones de HoloLens**, debería aparecer el mundo real detrás de todo lo que la cámara representa, no una textura Skybox.
1. Con el **cámara principal** aún seleccionado en el **jerarquía** panel, busque el **cámara** componente en el **Inspector** panel y cambiar la **Borrar las marcas** lista desplegable de **Skybox** a **Color sólido**.
2. Seleccione el **en segundo plano** selector de color y cambie el **RGBA** valores en (0, 0, 0, 0)

**Para aplicaciones de realidad mixta dirigidas a inmersivos**, podemos usar la textura Skybox predeterminado que proporciona Unity.
1. Con el **cámara principal** aún seleccionado en el **jerarquía** panel, busque el **cámara** componente en el **Inspector** panel y mantener la **Borrar las marcas** lista desplegable para **Skybox**.

En tercer lugar, nos gustaría que considere el plano de recorte cercano en Unity e impedir que los objetos que se va a representar demasiado cerca a los usuarios los ojos como un objeto aproxima a un usuario o un usuario aproxima a un objeto.

**Para las aplicaciones de HoloLens**, se puede establecer el plano de recorte cercano la [HoloLens recomendadas](camera-in-unity.md#clip-planes) 0,85 metros.
1. Con el **cámara principal** aún seleccionado en el **jerarquía** panel, busque el **cámara** componente en el **Inspector** panel y cambiar la **Cerca del plano de recorte** arrastrándolo desde el valor predeterminado **0.3** a la HoloLens recomendadas **0,85**.

**Para aplicaciones de realidad mixta dirigidas a inmersivos**, podemos usar la configuración predeterminada que Unity proporciona.
1. Con el **cámara principal** aún seleccionado en el **jerarquía** panel, busque el **cámara** componente en el **Inspector** panel y mantener la **Cerca del plano de recorte** campo en el valor predeterminado **0.3**.

Por último, nos gustaría guardar nuestro progreso hasta ahora. Para guardar los cambios de escena, seleccione **archivo > Guardar escena como**, asigne el nombre de la escena **Main**y seleccione **guardar**.

## <a name="chapter-3---setup-the-project-settings"></a>Capítulo 3: configuración de la configuración del proyecto

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

En este capítulo, se establecerá a algunas configuraciones de proyecto de Unity que nos ayudan a los SDK de Windows Holographic para el desarrollo de destino. También se establecerá algunas opciones de calidad para nuestra aplicación. Por último, se garantizará que nuestros objetivos de compilación se establecen en Windows Store.

### <a name="unity-performance-and-quality-settings"></a>Configuración de rendimiento y calidad de Unity

**Configuración de calidad de Unity para HoloLens**

![Configuración de calidad de Unity para HoloLens](images/qualitysettings.png) 

Puesto que es tan importante mantener la alta velocidad de fotogramas en HoloLens, queremos que la configuración de calidad, optimizada para rendimiento más rápido. Para obtener más información de rendimiento, [recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md).
1. Seleccione **Editar > configuración del proyecto > calidad**
2. Seleccione el **desplegable** bajo el **Windows Store** logotipo y seleccione **Very Low**. Sabrá que la configuración se aplique correctamente cuando la casilla de la columna de Windows Store y **Very Low** fila es verde.

**Para aplicaciones de realidad mixta dirigidas a las pantallas de ocluidos**, puede dejar la configuración de calidad a sus valores predeterminados.

### <a name="target-windows-10-sdk"></a>Tener como destino Windows 10 SDK

**SDK de destino Windows Holographic**

![SDK de destino Windows Holographic](images/xrsettings.png) 

Es necesario informar a Unity que se debe crear la aplicación que estamos intentando exportar una [vista envolvente](app-views.md) en lugar de una vista 2D. Para ello habilitando la compatibilidad con la realidad Virtual en Unity como destino el SDK de Windows 10.
1. Vaya a **Editar > configuración del proyecto > Reproductor**.
2. En el **Panel Inspector** para la configuración del Reproductor, seleccione la **Windows Store** icono.
3. Expanda el **configuración XR** grupo.
4. En el **representación** sección, compruebe el **admite la realidad Virtual** casilla de verificación para agregar un nuevo **SDK de realidad Virtual** lista.
5. Compruebe que **Windows Mixed Reality** aparece en la lista. Si no, seleccione el **+** situado en la parte inferior de la lista y elija **Windows Mixed Reality**.

>[!NOTE]
>Si no ve el **Windows Store** icono, compruebe lo siguiente para asegurarse de que ha seleccionado el Backend de Scripting de Windows Store .NET antes de la instalación. De lo contrario, es posible que deba volver a instalar Unity con la correcta instalación de Windows.

**Compruebe la configuración de .NET**

![Compruebe la configuración de .NET](images/configoptions-375px.png)

1. Vaya a **Editar > configuración del proyecto > Reproductor** (todavía puede tener esta en el paso anterior).
2. En el **Panel Inspector** para la configuración del Reproductor, seleccione la **Windows Store** icono.
3. En el **otra configuración** configuración sección, asegúrese de que **back-end de Scripting** está establecido en **.NET**

Magnífico trabajo sobre cómo obtener toda la configuración de proyecto que se aplica. A continuación, nos gustaría agregar un holograma!

## <a name="chapter-4---create-a-cube"></a>Capítulo 4: crear un cubo

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

Creación de un cubo en el proyecto de Unity es igual que crear cualquier otro objeto en Unity. Colocación de un cubo delante del usuario es fácil porque el sistema de coordenadas de Unity se asigna a la del mundo real, donde un medidor en Unity es aproximadamente un medidor en el mundo real.
1. En la esquina superior izquierda de la **jerarquía** panel, seleccione el **crear** lista desplegable y elija **objeto 3D > cubo**.
2. Seleccione el recién creado **cubo** en el **jerarquía** panel
3. En el **Inspector** encontrar el **transformar** componente y cambio **posición** a (**X**: 0, **Y**: 0, **Z**: 2). *2 metros del cubo se coloca delante de la posición inicial del usuario.*
4. En el **transformar** componente, cambio **rotación** a (**X**: 45, **Y**: 45, **Z**: 45) y cambiar **escala** a (**X**: 0.25, **Y**: 0.25, **Z**: 0.25). *Esto se puede escalar el cubo a medidores 0,25.*
5. Para guardar los cambios de escena, seleccione **archivo > Guardar escena**.

## <a name="chapter-5---verify-on-device-from-unity-editor"></a>Capítulo 5: comprobar en el dispositivo desde el editor de Unity

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

Ahora que hemos creado el cubo, es hora de hacer una comprobación rápida en el dispositivo. Puede hacerlo directamente desde dentro del editor de Unity.

### <a name="initial-setup"></a>Instalación inicial
1. En el equipo, de desarrollo en Unity, abra **archivo > configuración de compilación** ventana.
2. Cambio **plataforma** a **Universal Windows Platform** y haga clic en **plataforma del conmutador**

### <a name="for-hololens-use-unity-remoting"></a>Para HoloLens usar la comunicación remota de Unity
1. En su HoloLens, instalar y ejecutar el [holográfica Reproductor Remoting](holographic-remoting-player.md), disponible en el Store de Windows. Inicie la aplicación en el dispositivo y escribirá un estado de espera y muestran la dirección IP del dispositivo. Anote la dirección IP.
2. Abra **Ventana > XR > emulación holográfica**.
3. Cambio **en modo de emulación** desde **ninguno** a **remota al dispositivo**.
4. En **máquina remota**, escriba la dirección IP de su HoloLens se indicó anteriormente.
5. Haga clic en **Conectar**.
6. Asegúrese del **estado de la conexión** cambia a verde **conectado**.
7. Ahora puede hacer clic **reproducir** en el editor de Unity.

Ahora podrá ver el cubo en el dispositivo y en el editor. Puede pausar, inspeccionar los objetos y, al igual que ejecutan una aplicación en el editor, ya que es básicamente lo que sucede, pero con vídeo, audio y transmitidos y hacia atrás a través de la red entre el equipo host y el dispositivo de entrada de dispositivo de depuración.

### <a name="for-other-mixed-reality-supported-headsets"></a>Para otro mixed reality admite auriculares

1. Conectar los auriculares con su equipo de desarrollo con el cable USB y el HDMI o mostrar el cable del puerto.
2. Iniciar el **Portal de realidad mixta** y asegúrese de haber completado la primera experiencia de ejecución.
3. Desde Unity, ahora puede presionar el botón de reproducción.

Ahora podrá ver la representación en los auriculares de realidad mixta y en el editor de cubos.

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a>Capítulo 6: compilar e implementar en dispositivos desde Visual Studio

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

Ahora estamos preparados para compilar nuestro proyecto de Visual Studio e implementar en el dispositivo de destino.

### <a name="export-to-the-visual-studio-solution"></a>Exportar a la solución de Visual Studio
1.  Abra **archivo > configuración de compilación** ventana.
2.  Haga clic en **agregar escenas abierto** para agregar la escena.
3.  Cambio **plataforma** a **Universal Windows Platform** y haga clic en **Cambiar plataforma**.
4.  En **Windows Store** asegurarse de configuración, **SDK** es **10 Universal**.
5.  Para el dispositivo de destino, deje a **cualquier dispositivo** para ocluidos muestra o cambie a **HoloLens**.
6.  **Tipo de compilación UWP** debe ser **D3D**.
7.  **UWP SDK** podría quedar en **más reciente instalado**.
8.  Comprobar **Unity C# proyectos** en la depuración.
9.  Haz clic en **Compilación**.
10. En el Explorador de archivos, haga clic en **nueva carpeta** y el nombre de la carpeta **"App"**.
11. Con el **aplicación** carpeta seleccionada, haga clic en el **Seleccionar carpeta** botón.
12. Cuando se hace Unity compilar, aparecerá una ventana del explorador de archivos de Windows.
13. Abra el **aplicación** carpeta en el Explorador de archivos.
14. Abra la solución de Visual Studio generada (MixedRealityIntroduction.sln en este ejemplo)

### <a name="compile-the-visual-studio-solution"></a>Compile la solución de Visual Studio

Por último, se compile la solución de Visual Studio exportada, implementarlo y probarlo en el dispositivo.
1. Uso de la barra de herramientas superior en Visual Studio, cambiar el destino de **depurar** a **versión** y desde **ARM** a **X86**.

Difieren de las instrucciones para implementar en un dispositivo en comparación con el emulador. Siga las instrucciones que coincidan con su configuración.

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a>Implementar en dispositivos de realidad mixta a través de Wi-Fi
1. Haga clic en la flecha situada junto a la **máquina Local** botón y cambiar el destino de implementación para **máquina remota**.
2. Escriba la dirección IP del dispositivo de realidad mixta y cambiar **modo de autenticación** a Universal (protocolo sin cifrar) para HoloLens y **Windows** para otros dispositivos.
3. Haga clic en **Depurar > Iniciar sin depurar**.

**Para HoloLens**, si se trata de la primera vez que la implementación en su dispositivo, tendrá que par [con Visual Studio](using-visual-studio.md).

### <a name="deploy-to-mixed-reality-device-over-usb"></a>Implementar en dispositivos de realidad mixta a través de USB

Asegúrese de que el dispositivo está conectado a través de un cable USB.
1. **Para HoloLens**, haga clic en la flecha situada junto a la **máquina Local** botón y cambiar el destino de implementación para **dispositivo**.
2. **Para dirigirse a ocluidos dispositivos conectados a su equipo**, mantenga la configuración en el equipo Local. Asegúrese de que tiene el **Portal de realidad mixta** ejecutando.
3. Haga clic en **Depurar > Iniciar sin depurar**.

### <a name="deploy-to-emulator"></a>Implementar en el emulador
1. Haga clic en la flecha situada junto a la **dispositivo** botón y desde la lista desplegable seleccione **emulador de HoloLens**.
2. Haga clic en **Depurar > Iniciar sin depurar**.

### <a name="try-out-your-app"></a>Pruebe la aplicación

Ahora que la aplicación se implementa, intente mover todo el cubo y observe que se mantiene en el mundo delante de usted.

## <a name="see-also"></a>Vea también
* [Introducción al desarrollo de Unity](unity-development-overview.md)
* [Procedimientos recomendados para trabajar con Unity y Visual Studio](best-practices-for-working-with-unity-and-visual-studio.md)
* [Conceptos básicos de MR 101](holograms-101.md)
* [Conceptos básicos de MR 101E](holograms-101e.md)
