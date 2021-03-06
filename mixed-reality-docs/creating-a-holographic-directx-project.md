---
title: Creación de un proyecto de DirectX holográfica
description: Explica cómo crear una nueva aplicación holográfica basada en la plantilla de aplicación de Windows Mixed Reality.
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, aplicación holográfica, nueva aplicación, aplicación para UWP, aplicación de plantilla, hologramas, nuevo proyecto, tutorial, descarga, código de ejemplo
ms.openlocfilehash: 30f2c630b2919fbc304dc96d13cab74e22ed4adc
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81277923"
---
# <a name="creating-a-holographic-directx-project"></a>Creación de un proyecto de DirectX holográfica

Una aplicación holográfica que cree para HoloLens será una <a href="https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide" target="_blank">aplicación plataforma universal de Windows (UWP)</a>.  Si el destino es una aplicación de escritorio con auriculares de realidad mixta, puede crear una aplicación para UWP o una aplicación de Win32.

La plantilla de aplicación para UWP DirectX 11 Holographic es muy similar a la de la aplicación UWP de DirectX 11; incluye un bucle de programa (o "bucle de juego"), una clase **DeviceResources** para administrar el dispositivo y el contexto de Direct3D, y una clase de representador de contenido simplificada. También tiene un <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a>, al igual que cualquier otra aplicación de UWP.

La aplicación de realidad mixta, sin embargo, tiene algunas funcionalidades adicionales que no están presentes en una aplicación típica de UWP de Direct3D. La plantilla de aplicación de Windows Mixed Reality es capaz de:
* Controlar los recursos de dispositivo de Direct3D asociados a las cámaras holográficas.
* Recupere los búferes de retroceso de la cámara del sistema o (en el caso de Direct3D12) cree recursos de búfer de retroceso holográfica y administre la duración de los recursos.
* Controle la entrada de [mirada](gaze-and-commit.md) y reconozca un [gesto](gaze-and-commit.md#composite-gestures)sencillo.
* Entrar en el modo de representación estéreo de pantalla completa.

## <a name="how-do-i-get-started"></a>¿Cómo comenzar?

En primer lugar, [Instale las herramientas](install-the-tools.md)siguiendo las instrucciones de descarga de Visual Studio 2019 y las plantillas de aplicación de Windows Mixed Reality. Las plantillas de aplicación de realidad mixta están disponibles en Visual Studio Marketplace como [descarga web](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)o mediante su instalación como extensión a través de la interfaz de usuario de Visual Studio.

Ya está listo para crear la aplicación Windows mixed reality de DirectX 11. Tenga en cuenta que, para quitar el contenido de ejemplo, conviene comentar la Directiva de preprocesador **DRAW_SAMPLE_CONTENT** en *PCH. h*.

## <a name="creating-a-uwp-project"></a>Crear un proyecto de UWP

Una vez [instaladas las herramientas](install-the-tools.md) , puede crear un proyecto holográfica de DirectX para UWP.

Para crear un nuevo proyecto en Visual Studio 2019:
1. Inicie **Visual Studio**.
2. En la sección **Introducción** de la derecha, seleccione **crear un nuevo proyecto**.
3. En los menús desplegables del cuadro de diálogo **crear un nuevo proyecto** , **C++** seleccione, **Windows Mixed Reality**y **UWP**.
4. Seleccione **aplicación holográfica DirectX 11 (Windows universal) (C++/WinRT)** .
   ![captura de pantalla de la plantilla C++de proyecto de aplicación para UWP de Holographic DirectX 11/WinRT en Visual Studio 2019](images/holographic-directx-app-cpp-new-project-2019.png)<br>
   *Plantilla de proyecto C++de aplicación para UWP de Holographic DirectX 11/WinRT en Visual Studio 2019*
   >[!IMPORTANT]
   >Asegúrese de que el nombre de la plantilla de proyecto incluyeC++"(/WinRT)".  Si no es así, tiene instalada una versión anterior de las plantillas de proyecto holográfica.  Para obtener las plantillas de proyecto más recientes, [instálela](install-the-tools.md) como una extensión de Visual Studio 2019.
5. Haga clic en **Siguiente**.
5. Rellene los cuadros de texto **nombre de proyecto** y **Ubicación** , y pulse o haga clic en **crear**. Se crea el proyecto de aplicación holográfica.
6. Para el desarrollo dirigido solo a HoloLens 2, asegúrese de que la versión de **destino** y la **versión mínima** están establecidas en **Windows 10, versión 1903**.  Si también tiene como destino HoloLens (1º gen) o auriculares de escritorio mixto de la realidad, puede establecer la **versión mínima** en **Windows 10, versión 1809** , aunque esto requerirá algunas <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">comprobaciones adaptables</a> de la versión en el código al usar las nuevas características de HoloLens 2.
   ![captura de pantalla de la configuración de Windows 10, versión 1903 como destino y versiones mínimas](images/new-uwp-project.png)<br>
   *Establecimiento de la **versión 1903 de Windows 10** como destino y versiones mínimas*
   >[!IMPORTANT]
   >Si no ve **Windows 10, versión 1903** como opción, no tiene instalado el SDK más reciente de Windows 10.  Para que aparezca esta opción, <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">Instale la versión 10.0.18362.0 o posterior del SDK de Windows 10</a>.

Para crear un nuevo proyecto en Visual Studio 2017:
1. Inicie **Visual Studio**.
2. En el menú **archivo** , elija **nuevo** y seleccione **proyecto** en el menú contextual. Se abre el cuadro de diálogo **Nuevo proyecto**.
3. Expanda **instalado** a la izquierda y expanda el nodo del lenguaje **Visual C++**  .
4. Vaya al nodo **Windows Universal > Holographic** y seleccione **aplicación holográfica DirectX 11 (Windows universal) (C++/WinRT)** .
   ![captura de pantalla de la plantilla C++de proyecto de aplicación para UWP de Holographic DirectX 11/WinRT en Visual Studio 2017](images/holographic-directx-app-cpp-new-project.png)<br>
   *Plantilla de proyecto C++de aplicación para UWP de Holographic DirectX 11/WinRT en Visual Studio 2017*
   >[!IMPORTANT]
   >Asegúrese de que el nombre de la plantilla de proyecto incluyeC++"(/WinRT)".  Si no es así, tiene instalada una versión anterior de las plantillas de proyecto holográfica.  Para obtener las plantillas de proyecto más recientes, [instálela](install-the-tools.md) como una extensión de Visual Studio 2017.
5. Rellene los cuadros de texto **nombre** y **Ubicación** , y pulse o haga clic en **Aceptar**. Se crea el proyecto de aplicación holográfica.
6. Para el desarrollo dirigido solo a HoloLens 2, asegúrese de que la versión de **destino** y la **versión mínima** están establecidas en **Windows 10, versión 1903**.  Si también tiene como destino HoloLens (1º gen) o auriculares de escritorio mixto de la realidad, puede establecer la **versión mínima** en **Windows 10, versión 1809** , aunque esto requerirá algunas <a href="https://docs.microsoft.com/windows/uwp/debug-test-perf/version-adaptive-code" target="_blank">comprobaciones adaptables</a> de la versión en el código al usar las nuevas características de HoloLens 2.
   ![captura de pantalla de la configuración de Windows 10, versión 1903 como destino y versiones mínimas](images/new-uwp-project.png)<br>
   *Establecimiento de la **versión 1903 de Windows 10** como destino y versiones mínimas*
   >[!IMPORTANT]
   >Si no ve **Windows 10, versión 1903** como opción, no tiene instalado el SDK más reciente de Windows 10.  Para que aparezca esta opción, <a href="https://developer.microsoft.com/windows/downloads/windows-10-sdk" target="_blank">Instale la versión 10.0.18362.0 o posterior del SDK de Windows 10</a>.

La plantilla genera un proyecto con <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, una proyección de lenguaje c++ 17 de las API Windows Runtime que admite cualquier compilador de c++ 17 compatible con los estándares.  En el proyecto se muestra cómo crear un cubo con bloqueo mundial que esté colocado dos metros del usuario. El usuario puede pulsar en el [aire](gaze-and-commit.md#composite-gestures) o presionar un botón en el controlador para colocar el cubo en una posición diferente especificada por el [usuario.](gaze-and-commit.md) Puede modificar este proyecto para crear cualquier aplicación de realidad mixta.

También puede crear un nuevo proyecto con la plantilla de proyecto **de C# visual** Holographic, que se basa en SharpDX.  Si el proyecto C# holográfica no se inició desde la plantilla de aplicación de Windows Holographic, deberá copiar el archivo MS. fxcompile. targets de un proyecto de plantilla C# de realidad mixta de Windows e importarlo en el archivo. csproj para compilar los archivos HLSL que agregue al proyecto. También se proporciona una plantilla de Direct3D 12 en la extensión de plantillas de aplicaciones de Windows Mixed Reality a Visual Studio.

Revise el [uso de Visual Studio para implementar y depurar](using-visual-studio.md) para obtener información sobre cómo compilar e implementar el ejemplo en su HoloLens, el equipo con un dispositivo inmersivo conectado o un emulador.

En el resto de las instrucciones siguientes se asumirá que está C++ usando para compilar la aplicación.

### <a name="uwp-app-entry-point"></a>Punto de entrada de aplicación de UWP

La aplicación holográfica UWP se inicia en la función **wWinMain** en AppView. cpp. La función **wWinMain** crea el <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkview" target="_blank">IFrameworkView</a> de la aplicación e inicia <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.coreapplication" target="_blank">CoreApplication</a> con él.

Desde **AppView. cpp**:

```cpp
// The main function bootstraps into the IFrameworkView.
int __stdcall wWinMain(HINSTANCE, HINSTANCE, PWSTR, int)
{
    winrt::init_apartment();
    CoreApplication::Run(AppViewSource());
    return 0;
}
```

A partir de ese momento, la clase AppView controla la interacción con los eventos de entrada básicos de Windows, los eventos y la mensajería de CoreWindow, etc. También creará el HolographicSpace que usa la aplicación.

## <a name="creating-a-win32-project"></a>Crear un proyecto de Win32

La manera más sencilla de empezar a crear un proyecto de Win32 Holographic es adaptar el <a href="https://github.com/Microsoft/Windows-classic-samples/tree/master/Samples/BasicHologram" target="_blank">ejemplo de Win32 *BasicHologram* </a>.

En este ejemplo de Win32 se usa <a href="https://docs.microsoft.com/windows/uwp/cpp-and-winrt-apis/" target="_blank"> C++/WinRT</a>, una proyección de lenguaje c++ 17 de las API Windows Runtime que admite cualquier compilador de c++ 17 compatible con los estándares.  En el proyecto se muestra cómo crear un cubo con bloqueo mundial que esté colocado dos metros del usuario. El usuario puede presionar un botón en el controlador para colocar el cubo en una posición diferente especificada por el [usuario.](gaze-and-commit.md) Puede modificar este proyecto para crear cualquier aplicación de realidad mixta.

### <a name="win32-app-entry-point"></a>Punto de entrada de la aplicación Win32

La aplicación holográfica Win32 se inicia en la función **wWinMain** en AppMain. cpp. La función **wWinMain** crea el HWND de la aplicación e inicia su bucle de mensajes.

Desde **AppMain. cpp**:

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

A partir de ese momento, la clase AppMain controla la interacción con los mensajes básicos de la ventana, etc. También creará el HolographicSpace que usa la aplicación.

## <a name="render-holographic-content"></a>Representación de contenido holográfica

La carpeta de **contenido** del proyecto contiene clases para representar hologramas en el [espacio holográfica](getting-a-holographicspace.md). El holograma predeterminado de la plantilla es un cubo giratorio que se coloca dos metros fuera del usuario. El dibujo de este cubo se implementa en **SpinningCubeRenderer. cpp**, que tiene estos métodos clave:

|  Método  |  Explicación | 
|----------|----------|
|  `CreateDeviceDependentResources` |  Carga los sombreadores y crea la malla del cubo. | 
|  `PositionHologram` |  Coloca el holograma en la ubicación especificada por el <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose" target="_blank">SpatialPointerPose</a>proporcionado. | 
|  `Update` |  Gira el cubo y establece la matriz del modelo. | 
|  `Render` |  Representa un marco con los sombreadores de píxeles y vértices. | 

La subcarpeta **shaders** contiene cuatro implementaciones de sombreador predeterminadas:

|  Sombreador  |  Explicación | 
|----------|----------|
|  `GeometryShader.hlsl` |  Un paso a través que deja la geometría sin modificar. | 
|  `PixelShader.hlsl` |  Pasa por los datos de color. Los datos de color se interpolan y se asignan a un píxel en el paso de rasterización. | 
|  `VertexShader.hlsl` |  Sombreador simple para realizar el procesamiento de vértices en la GPU. | 
|  `VPRTVertexShader.hlsl` |  Sombreador simple para realizar el procesamiento de vértices en la GPU, que está optimizado para la representación estéreo de realidad mixta de Windows. | 

`VertexShaderShared.hlsl` contiene código común compartido entre `VertexShader.hlsl` y `VPRTVertexShader.hlsl`.

Nota: la plantilla de aplicación de Direct3D 12 también incluye `ViewInstancingVertexShader.hlsl`. Esta variante usa características opcionales de D3D12 para representar imágenes estéreo de forma más eficaz.

Los sombreadores se compilan cuando se compila el proyecto y se cargan en el método **SpinningCubeRenderer:: CreateDeviceDependentResources** .

## <a name="interact-with-your-holograms"></a>Interactúe con los hologramas

La entrada del usuario se procesa en la clase **SpatialInputHandler** , que obtiene una instancia de <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager" target="_blank">SpatialInteractionManager</a> y se suscribe al evento <a href="https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed" target="_blank">SourcePressed</a> . Esto permite detectar el gesto de punteo de aire y otros eventos de entrada espacial.

## <a name="update-holographic-content"></a>Actualización del contenido holográfica

Las actualizaciones de la aplicación de realidad mixta en un bucle de juego, que se implementa de forma predeterminada en el método de **actualización** en `AppMain.cpp`. El método **Update** actualiza los objetos de la escena, como el cubo giratorio, y devuelve un objeto <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> que se usa para obtener las matrices de la vista y la proyección actualizadas y para presentar la cadena de intercambio.

El método **Render** de `AppMain.cpp` toma el <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> y representa el marco actual en cada cámara holográfica, según la aplicación actual y el estado de posicionamiento espacial.

## <a name="notes"></a>Notas

La plantilla de aplicación de Windows Mixed Reality ahora admite la compilación con la marca de mitigación de Spectre habilitada (/Qspectre). Asegúrese de instalar la versión mitigada Spectre de las bibliotecas en tiempo de C++ ejecución de Microsoft Visual (MSVC) antes de compilar una configuración con la mitigación de Spectre habilitada. Para instalar las C++ bibliotecas mitigadas Spectre, inicie el instalador de Visual Studio y seleccione **modificar**. Vaya a **componentes individuales** y busque "Spectre". Seleccione las casillas correspondientes a las plataformas de destino y la versión de MSVC que necesita para compilar el código de Spectre mitigado para y haga clic en **modificar** para iniciar la instalación.

## <a name="see-also"></a>Vea también
* [Obtención de HolographicSpace](getting-a-holographicspace.md)
* <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspaceh" target="_blank">HolographicSpace</a>
* [Representación en DirectX](rendering-in-directx.md)
* [Uso de Visual Studio para implementar y depurar](using-visual-studio.md)
* [Uso del emulador HoloLens](using-the-hololens-emulator.md)
* [Uso de XAML con aplicaciones de DirectX holográficas](using-xaml-with-holographic-directx-apps.md)
