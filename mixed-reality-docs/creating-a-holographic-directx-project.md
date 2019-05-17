---
title: Creación de un proyecto de DirectX holográfico
description: Explica cómo crear una nueva aplicación holográfica basada en la plantilla de aplicación de Windows Mixed Reality.
author: MikeRiches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, aplicación holográfica, nueva aplicación, aplicación de UWP, aplicación de la plantilla, hologramas, nuevo proyecto, tutorial, descarga, el código de ejemplo
ms.openlocfilehash: a7eac9d8056fe5f7bcc442d6441f71331fa96cf6
ms.sourcegitcommit: 19c9bff21061d485821b61c9f3498daef8fa8235
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65828125"
---
# <a name="creating-a-holographic-directx-project"></a>Creación de un proyecto de DirectX holográfico

Una aplicación holográfica crear pasarán a ser un HoloLens un <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">plataforma Universal de Windows (UWP) app</a>.  Si el destino es auriculares de realidad mixta de Windows desktop, puede crear una aplicación para UWP o una aplicación de Win32.

La plantilla de aplicación de DirectX 11 holográfica UWP es muy similar a la plantilla de aplicación para UWP de DirectX 11; incluye un bucle de programa (o "bucle de juego"), un **DeviceResources** clase para administrar el dispositivo Direct3D y el contexto y una clase de representador de contenido simplificada. También tiene un <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, al igual que cualquier otra aplicación UWP.

La aplicación de realidad mixta, sin embargo, tiene algunas capacidades adicionales que no están presentes en una aplicación típica de UWP de Direct3D 11. La plantilla de aplicación de Windows Holographic es capaz de:
* Controlar los recursos de dispositivo Direct3D asociados con las cámaras holográficas.
* Recuperación de búferes de reserva de la cámara del sistema.
* Controlar [que mirar](gaze.md) de entrada y reconocer un sencillo [gesto](gestures.md).
* ENTRAR en modo de representación estéreo de pantalla completa.

## <a name="how-do-i-get-started"></a>¿Cómo puedo comenzar?

Primera [instalar las herramientas de](install-the-tools.md), siguiendo las instrucciones sobre la descarga de Visual Studio 2017 y el emulador de Microsoft HoloLens. Las plantillas de aplicación holográfica se incluyen en el mismo instalador como el emulador de Microsoft HoloLens. Asegúrese de que está seleccionada la opción para instalar las plantillas antes de instalar.

Ahora está listo para crear la aplicación DirectX 11 Windows Mixed Reality. Tenga en cuenta que para quitar el contenido de ejemplo, convierta en comentario la **DRAW_SAMPLE_CONTENT** directiva de preprocesador en *pch.h*.

## <a name="creating-a-uwp-project"></a>Creación de un proyecto UWP

Una vez el [se instalan herramientas](install-the-tools.md) , a continuación, puede crear un proyecto de UWP de DirectX holográfico.

Para crear un nuevo proyecto:
1. Iniciar **Visual Studio**.
2. Desde el **archivo** menú, elija **New** y seleccione **proyecto** en el menú contextual. El **nuevo proyecto** abre el cuadro de diálogo.
3. Expanda **instalado** a la izquierda y expanda el **Visual C++**  nodo de lenguaje.
4. Navegue hasta la **Windows Universal > Holographic** nodo y seleccione **aplicación holográfica de 11 DirectX (Windows Universal) (C++/WinRT)**.
   ![Captura de pantalla de la versión de DirectX 11 holográfica C++plantilla de proyecto de aplicación de WinRT UWP en Visual Studio](images/holographic-directx-app-cpp-new-project.png)<br>
   *Holográfica DirectX 11 C++plantilla de proyecto de aplicación de WinRT UWP en Visual Studio*
   >[!IMPORTANT]
   >Asegúrese de que incluye el nombre de la plantilla de proyecto "(C++/WinRT)".  Si no, tiene una versión anterior de las plantillas de proyecto holográfica instaladas.  Para obtener las últimas plantillas de proyecto, [instalar el emulador de HoloLens más reciente](using-the-hololens-emulator.md).
5. Rellene el **nombre** y **ubicación** cuadros de texto y haga clic o pulse **Aceptar**. Se crea el proyecto de aplicación holográfica.
6. Para el desarrollo destinadas a solo 2 HoloLens, asegúrese de que el **versión de destino** y **versión mínima** se establecen en **Windows 10, versión 1903**.  Si desea usar también HoloLens (gen 1) o auriculares de realidad mixta de Windows desktop, puede establecer **versión mínima** a **Windows 10, versión 1809** en su lugar, aunque esto requerirá algunas <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank"> comprobaciones de versión adaptable</a> en el código al usar las nuevas características de HoloLens 2.
   ![Captura de pantalla de configuración de Windows 10, versión 1903 como las versiones de destino y mínima](images/new-uwp-project.png)<br>
   *Establecer **Windows 10, versión 1903** como las versiones de destino y mínima*
   >[!IMPORTANT]
   >Si no ve **Windows 10, versión 1903** como opción, no tiene el SDK de Windows 10 más recientes instalados.  Para obtener esta opción en aparecer, <a href="https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk" target="_blank">instalar la versión 10.0.18362.0 o posterior del SDK de Windows 10</a>.

La plantilla genera un proyecto con <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, una proyección de las APIs de tiempo de ejecución de Windows que admite cualquier conforme a los estándares C ++ 17 del compilador C ++ 17 lenguaje.  El proyecto muestra cómo crear un cubo bloqueado por el mundo que ha colocado dos metros del usuario. El usuario puede [pulsar en el aire](gestures.md#air-tap) o presione un botón en el controlador para colocar el cubo en una posición diferente en el que se especifica por el usuario [que mirar](gaze.md). Puede modificar este proyecto para crear cualquier aplicación de realidad mixta.

Como alternativa, puede crear un nuevo proyecto con el **Visual C#**  plantilla de proyecto holográfica, que se basa en SharpDX.  Si los holographic C# proyecto no se inició desde la plantilla de aplicación de Windows Holographic, deberá copiar el archivo ms.fxcompile.targets de un Windows Mixed Reality C# proyecto de plantilla y la importación en el archivo .csproj archivo con el fin de compilar HLSL archivos que agregue al proyecto.

Revisión [con Visual Studio para implementar y depurar](using-visual-studio.md) para obtener información sobre cómo compilar e implementar el ejemplo en su HoloLens, PC con envolvente dispositivo conectado o un emulador.

El resto de las instrucciones siguientes se presupone que está usando C++ para compilar la aplicación.

### <a name="uwp-app-entry-point"></a>Punto de entrada de aplicación UWP

Se inicia la aplicación UWP holográfica en el **wWinMain** función en AppView.cpp. El **wWinMain** función crea la aplicación <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> e inicia la <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> con él.

Desde **AppView.cpp**:

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

Desde ese momento, la clase AppView administra la interacción con los eventos de entrada básicos de Windows, eventos de CoreWindow y mensajería y así sucesivamente. También creará el HolographicSpace utilizado por la aplicación.

## <a name="creating-a-win32-project"></a>Crear un proyecto Win32

La manera más fácil para empezar a compilar Win32 holográfica proyecto consiste en adaptar la <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank"> *BasicHologram* ejemplo Win32</a>.

Este ejemplo Win32 utiliza <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, una proyección de las APIs de tiempo de ejecución de Windows que admite cualquier conforme a los estándares C ++ 17 del compilador C ++ 17 lenguaje.  El proyecto muestra cómo crear un cubo bloqueado por el mundo que ha colocado dos metros del usuario. El usuario puede presionar un botón en el controlador para colocar el cubo en una posición diferente en el que se especifica por el usuario [que mirar](gaze.md). Puede modificar este proyecto para crear cualquier aplicación de realidad mixta.

### <a name="win32-app-entry-point"></a>Punto de entrada de aplicación de Win32

Se inicia la aplicación Win32 holográfica en el **wWinMain** función en AppMain.cpp. El **wWinMain** función crea el HWND de la aplicación e inicia su bucle de mensajes.

Desde **AppMain.cpp**:

```cpp
int APIENTRY wWinMain(
    _In_     HINSTANCE hInstance,
    _In_opt_ HINSTANCE hPrevInstance,
    _In_     LPWSTR    lpCmdLine,
    _In_     int       nCmdShow)
{
    UNREFERENCED_PARAMETER(hPrevInstance);
    UNREFERENCED_PARAMETER(lpCmdLine);

    winrt::init_apartment();

    App app;

    // Initialize global strings, and perform application initialization.
    app.Initialize(hInstance);

    // Create the HWND and the HolographicSpace.
    app.CreateWindowAndHolographicSpace(hInstance, nCmdShow);

    // Main message loop:
    app.Run(hInstance);

    // Perform application teardown.
    app.Uninitialize();

    return 0;
}
```

Desde ese momento, la clase AppMain administra la interacción con los mensajes de ventana básico y así sucesivamente. También creará el HolographicSpace utilizado por la aplicación.

## <a name="render-holographic-content"></a>Representar el contenido holográfica

El proyecto **contenido** carpeta contiene clases para hologramas de representación en el [espacio holográfica](getting-a-holographicspace.md). El holograma de forma predeterminada en la plantilla es un cubo girando que ha colocado dos metros del usuario. Este cubo de dibujo se implementa en **SpinningCubeRenderer.cpp**, que tiene estos métodos claves:

|  Método  |  Explicación | 
|----------|----------|
|  `CreateDeviceDependentResources` |  Carga a los sombreadores y crea la malla del cubo. | 
|  `PositionHologram` |  Coloca el holograma en la ubicación especificada por el objeto <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>. | 
|  `Update` |  Gira el cubo y establece la matriz de modelo. | 
|  `Render` |  Representa un marco con los sombreadores de vértices y píxeles. | 

El **sombreadores** subcarpeta contiene cuatro implementaciones de sombreador predeterminado:

|  Shader  |  Explicación | 
|----------|----------|
|  `GeometryShader.hlsl` |  Un acceso directo que deja la geometría sin modificar. | 
|  `PixelShader.hlsl` |  Pasa a través de los datos de color. Los datos de color se interpolan y asignados a un píxel en el paso de la rasterización. | 
|  `VertexShader.hlsl` |  Sombreador sencillo para el procesamiento de vértices en la GPU. | 
|  `VPRTVertexShader.hlsl` |  Sombreador sencillo para el procesamiento de vértices en la GPU, que está optimizada para la representación de Windows Mixed Reality estéreo. | 

`VertexShaderShared.hlsl` contiene el código común compartido entre `VertexShader.hlsl` y `VPRTVertexShader.hlsl`.

Los sombreadores se compilan cuando se compila el proyecto y que están cargados en el **SpinningCubeRenderer::CreateDeviceDependentResources** método.

## <a name="interact-with-your-holograms"></a>Interactuar con sus hologramas

Se procesa la entrada del usuario en el **SpatialInputHandler** clase, que obtiene un <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> de instancia y se suscribe a la <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> eventos. Esto permite detectar el gesto de pulsar en el aire y otros eventos de entrada espaciales.

## <a name="update-holographic-content"></a>Actualizar contenido holográfica

Las actualizaciones de la aplicación de realidad mixta en un bucle de juego, que de forma predeterminada, se implementa en el **actualización** método `AppMain.cpp`. El **actualización** método actualiza los objetos de la escena, al igual que el cubo girando y devuelve un <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> objeto que se usa para obtener las matrices de proyección y de vista actualizadas y presentar la cadena de intercambio.

El **representar** método `AppMain.cpp` toma el <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> y presenta el marco actual a cada cámara holográfica, según la aplicación actual y el estado de posición espacial.

## <a name="see-also"></a>Vea también
* [Obtención de HolographicSpace](getting-a-holographicspace.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a>
* [Representación en DirectX](rendering-in-directx.md)
* [Uso de Visual Studio para implementar y depurar](using-visual-studio.md)
* [Uso del emulador HoloLens](using-the-hololens-emulator.md)
* [Uso de XAML con aplicaciones de DirectX holográficas](using-xaml-with-holographic-directx-apps.md)
