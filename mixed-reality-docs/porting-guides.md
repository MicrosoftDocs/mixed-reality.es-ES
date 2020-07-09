---
title: Guías de migración
description: Un tutorial paso a paso que explica cómo migrar una aplicación envolvente existente a Windows Mixed Reality.
author: JBrentJ
ms.author: alexturn
ms.date: 07/07/2020
ms.topic: article
keywords: puerto, portabilidad, Unity, middleware, motor, UWP, Win32
ms.openlocfilehash: a1e3cd47096d728091d62d6c038bf6b2eb6bab16
ms.sourcegitcommit: 0eb99fae933d4374af2c032af4e9ceda1807e532
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/09/2020
ms.locfileid: "86156776"
---
# <a name="porting-guides"></a>Guías de migración

## <a name="overview"></a>Información general

Windows 10 incluye compatibilidad directa con auriculares envolventes y holográficas. Si ha creado contenido para otros dispositivos, como Oculus Rift o HTC Naopak, tienen dependencias en las bibliotecas que existen por encima de la API de la plataforma del sistema operativo. Incorporar contenido existente a Windows Mixed Reality implica redestinar el uso de estos otros SDK a las API de Windows. Las [API de la plataforma Windows para la realidad mixta](https://docs.microsoft.com/uwp/api/Windows.Perception) funcionan con el modelo de aplicación de Win32 y del plataforma universal de Windows (UWP). Si la aplicación aún no está compilada para UWP, cambiar a UWP formará parte de la experiencia de migración.

## <a name="porting-overview"></a>Introducción a la migración

En un nivel alto, los siguientes pasos están relacionados con el traslado de contenido existente:
1. **Asegúrese de que el equipo ejecuta Windows 10 Fall Creators Update (16299).** Ya no se recomienda recibir compilaciones de vista previa del anillo de Insider SKIP Preview, ya que esas compilaciones no serán las más estables para el desarrollo de realidad mixta.
2. **Actualice a la versión más reciente de los gráficos o del motor de juegos.** Los motores de juegos deberán admitir la versión 10.0.15063.0 del SDK de Windows 10 (Publicada en el 2017 de abril) o superior.
3. **Actualice cualquier middleware, complemento o componente.** Si la aplicación contiene componentes, es una buena idea actualizar a la versión más reciente. Las versiones más recientes de los complementos más comunes son compatibles con UWP.
4. **Quite las dependencias de los SDK duplicados**. En función del dispositivo al que se dirija el contenido, deberá quitar o compilar condicionalmente ese SDK (por ejemplo, SteamVR) para que pueda establecer como destino las API de Windows en su lugar.
5. **Trabaje con problemas de compilación.** En este momento, el ejercicio de portabilidad es específico de la aplicación, el motor y las dependencias de componentes que tiene.

## <a name="common-porting-steps"></a>Pasos de portabilidad comunes

### <a name="common-step-1-make-sure-you-have-the-right-development-hardware"></a>Paso 1: asegurarse de que tiene el hardware de desarrollo correcto

En la página [instalar las herramientas](install-the-tools.md#for-immersive-vr-headset-development) se muestra el hardware de desarrollo recomendado.

### <a name="common-step-2-upgrade-to-the-latest-flight-of-windows-10"></a>Paso 2 común: actualizar al vuelo más reciente de Windows 10

La plataforma Windows Mixed Reality todavía está en desarrollo activo. Se recomienda [unirse al programa Windows Insider](https://insider.windows.com/) para tener acceso al vuelo "Windows Insider Fast".
1. Instalación de [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10)
2. [Únase](https://insider.windows.com/) al programa Windows Insider.
3. Habilitar el [modo de desarrollador](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
4. Cambiar a los [vuelos rápidos de Windows Insider](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview) a través de la **configuración > actualización & sección de seguridad**

### <a name="common-step-3-upgrade-to-the-most-recent-build-of-visual-studio-uwp-only"></a>Paso 3 común: actualizar a la compilación más reciente de Visual Studio (solo UWP)
* Vea [instalar la](install-the-tools.md#installation-checklist) página de herramientas en Visual Studio 2019

### <a name="common-step-4-be-ready-for-the-store-uwp-only"></a>Paso 4 común: estar listo para la tienda (solo UWP)
* Use el kit para la [certificación de aplicaciones de Windows](https://developer.microsoft.com/windows/develop/app-certification-kit) (también conocido como Wack) pronto y con frecuencia.
* Usar el [analizador de portabilidad](https://docs.microsoft.com/dotnet/standard/portability-analyzer) ([Descargar](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer))

### <a name="common-step-5-choose-the-correct-adapter"></a>Paso 5 común: elegir el adaptador correcto
* En sistemas como notebooks con dos GPU, [el destino es el adaptador correcto](rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications). Esto se aplica a las aplicaciones de Unity y de DirectX nativas donde se crea un ID3D11Device, ya sea de forma explícita o implícita (Media Foundation), para su funcionalidad.

## <a name="unity-porting-guidance"></a>Guía de portabilidad de Unity

### <a name="unity-step-1-follow-the-common-porting-steps"></a>Unity paso 1: siga los pasos de migración habituales.

Siga todos los pasos comunes. En el paso #3, seleccione la carga de trabajo **desarrollo de juegos con Unity** . Puede anular la selección del componente opcional del editor de Unity, ya que va a instalar una versión más reciente de Unity en las siguientes instrucciones.

### <a name="unity-step-2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>Unity paso 2: actualización a la compilación pública más reciente de Unity con compatibilidad con Windows MR
1. Descargue la última [compilación pública recomendada de Unity](install-the-tools.md) con compatibilidad de realidad mixta.
2. Guarde una copia del proyecto antes de empezar.
3. Revise la [documentación](https://docs.unity3d.com/Manual/UpgradeGuides.html) disponible en Unity en portabilidad.
4. Siga las [instrucciones](https://docs.unity3d.com/Manual/APIUpdater.html) del sitio de Unity para usar su actualizador de API automática.
5. Compruebe si hay cambios adicionales que necesite realizar para que el proyecto se ejecute y, a continuación, trabaje con los errores y advertencias restantes. 

> [!Note] 
> Si tiene un middleware del que depende, compruebe que está usando la versión más reciente (más información en el paso 3 a continuación).

### <a name="unity-step-3-upgrade-your-middleware-to-the-latest-versions"></a>Unity paso 3: actualización del middleware a las versiones más recientes

Con cualquier actualización de Unity, existe la posibilidad de actualizar uno o más paquetes de middleware de los que depende su juego o aplicación. Además, al estar al día con el middleware más reciente, se aumenta la probabilidad de éxito a lo largo del resto del proceso de portabilidad. Muchos paquetes de middleware han agregado recientemente compatibilidad con Plataforma universal de Windows (UWP) y la actualización a las versiones más recientes le permitirá aprovechar ese trabajo.

### <a name="unity-step-4-target-your-application-to-run-on-universal-windows-platform-uwp"></a>Unity paso 4: dirigir la aplicación para que se ejecute en Plataforma universal de Windows (UWP)

Si el destino es Win32, puede omitir este paso y continuar con el paso 5.

Después de instalar las herramientas, debe ejecutar la aplicación como una aplicación universal de Windows.

* Siga los pasos [detallados paso a paso a través](https://unity3d.com/partners/microsoft/porting-guides) del proporcionado por Unity. Debe permanecer en la versión más reciente de LTS (cualquier versión de 20xx. 4) para Windows MR.
* Para obtener más recursos de desarrollo para UWP, eche un vistazo a la [Guía de desarrollo de juegos de Windows 10](https://docs.microsoft.com/windows/uwp/gaming/e2e).

> [!NOTE]
> Unity continúa mejorando la compatibilidad con IL2CPP; IL2CPP facilita algunos puertos UWP. Si tiene como destino actualmente el back-end de scripting de .NET, considere la posibilidad de convertir para aprovechar el back-end de IL2CPP.

* Puede omitir "Unity STEP 5", ya que tiene como destino UWP en lugar de Win32.

> [!NOTE] 
> Si la aplicación tiene dependencias en servicios específicos del dispositivo, como la realización de una coincidencia de vapor, deberá deshabilitarlos en este paso. Puede enlazar a los servicios equivalentes que Windows proporciona más adelante.

### <a name="unity-step-5-target-your-application-to-run-on-win32"></a>Unity paso 5: dirigir la aplicación para que se ejecute en Win32

Desde dentro de la aplicación Unity:

* Vaya a archivo-> configuración de compilación
* Seleccione "PC, Mac, Linux independiente"
* Establecer la plataforma de destino en "Windows"
* Establecer la arquitectura en "x86" seleccionar "cambiar plataforma"


### <a name="unity-step-6-setup-your-windows-mixed-reality-hardware"></a>Unity paso 6: configuración del hardware de Windows Mixed Reality
1. Revisión de los pasos de la [configuración de auriculares inmersivo](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/before-you-start
)
2. Obtener información sobre cómo [usar el simulador de realidad mixta de Windows](using-the-windows-mixed-reality-simulator.md) y [navegar por la Página principal de Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)

### <a name="unity-step-7-target-your-application-to-run-on-windows-mixed-reality"></a>Unity paso 7: dirigir la aplicación para que se ejecute en Windows Mixed Reality
1. En primer lugar, debe quitar o compilar condicionalmente cualquier otra compatibilidad de biblioteca específica de un SDK de VR determinado. Esos activos cambian con frecuencia la configuración y las propiedades del proyecto de manera que sean incompatibles con otros SDK de VR, como Windows Mixed Reality.
    * Por ejemplo, si el proyecto hace referencia al SDK de SteamVR, deberá actualizar el proyecto para excluir esas llamadas de API de Prefabs y script al exportar para el destino de compilación de la tienda Windows.
    * Pronto estarán disponibles los pasos específicos para excluir condicionalmente otros SDK de VR.
2. En el proyecto de Unity, [el destino es el SDK de Windows 10](holograms-100.md#target-windows-10-sdk) .
3. Para cada escena, [Configure la cámara](holograms-100.md#chapter-2---setup-the-camera) .

### <a name="unity-step-8-use-the-stage-to-place-content-on-the-floor"></a>Unity paso 8: uso de la fase para colocar contenido en el piso

Puede crear experiencias de realidad mixta en una amplia gama de [escalas de experiencia](coordinate-systems.md).

Si va a migrar una **experiencia de escalado de**una instalación, debe asegurarse de que Unity está establecido en el tipo de espacio de seguimiento **estacionario** :

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

En el código anterior se establece el sistema de coordenadas universal de Unity para realizar el seguimiento del [marco estacionario de referencia](coordinate-systems.md#spatial-coordinate-systems). En el modo de seguimiento estacional, el contenido colocado en el editor justo delante de la ubicación predeterminada de la cámara (el avance es-Z) aparece delante del usuario cuando se inicia la aplicación. Para recentrar el origen del usuario, puede llamar a la XR de Unity [. Método InputTracking. recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) .

Si va a migrar una experiencia **de escalado permanente** o una **experiencia a escala de habitación**, colocará contenido en relación con el piso. Por lo tanto, se trata del piso del usuario mediante la **[fase espacial](coordinate-systems.md#spatial-coordinate-systems)**, que representa el origen del nivel de suelo definido por el usuario y el límite de sala opcional, configurado durante la primera ejecución. Para estas experiencias, debe asegurarse de que Unity está establecido en el tipo de espacio de seguimiento de **RoomScale** . Aunque RoomScale es el valor predeterminado, querrá establecerlo explícitamente y asegurarse de que se devuelve true para detectar situaciones en las que el usuario ha desplazado el equipo fuera del salón que han calibrado:

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```

Una vez que la aplicación establece correctamente el tipo de espacio de seguimiento de RoomScale, el contenido colocado en el plano y = 0 aparecerá en el suelo. El origen en (0,0) será el lugar específico en el piso en el que se encuentra el usuario durante la configuración de la habitación, con-Z que representa la dirección de avance que estaban teniendo lugar durante la instalación.

En el código de script, puede llamar al método TryGetGeometry en el tipo UnityEngine. experimental. XR. Boundary para obtener un polígono de límite, especificando un tipo de límite de TrackedArea. Si el usuario definía un límite (se obtiene una lista de vértices), es seguro ofrecer una experiencia de **escalado** a la habitación al usuario, donde puede recorrer la escena que cree.

El sistema representará automáticamente el límite cuando el usuario lo aproxime. No es necesario que la aplicación use este polígono para representar el límite.

Para obtener más información, consulte la página [de los sistemas de coordenadas en Unity](coordinate-systems-in-unity.md) .

Algunas aplicaciones usan un rectángulo para restringir su interacción. La recuperación del rectángulo inscrito más grande no se admite directamente en la API de UWP o Unity. El código de ejemplo vinculado a la siguiente muestra cómo buscar un rectángulo dentro de los límites de seguimiento. Por lo tanto, es posible que no encuentre la solución óptima, sin embargo, los resultados son coherentes con las expectativas. Los parámetros del algoritmo se pueden optimizar para buscar resultados más precisos a costa del tiempo de procesamiento. El algoritmo está en una bifurcación del kit de herramientas de realidad mixta que usa la versión 5,6 de MRTP Preview de Unity. Esto no está disponible públicamente. El código debe usarse directamente en 2017,2 y versiones posteriores de Unity. El código se trasladará al MRTK actual en un futuro próximo.

[archivo zip de código en github](https://github.com/KevinKennedy/MixedRealityToolkit-Unity/releases/tag/5.6.MRTP20) Archivos importantes:
* Assets/HoloToolkit/Stage/scripts/StageManager. CS-ejemplo de uso
* Assets/HoloToolkit/Stage/scripts/LargestRectangle. CS-implementación del algoritmo
* Assets/HoloToolkit-UnitTests/editor/Stage/LargestRectangleTest. CS: prueba trivial del algoritmo

Ejemplo de resultados:

![Ejemplo de resultados](images/largestrectangle-400px.jpg)

El algoritmo se basa en un blog de Daniel Smilkov: [el rectángulo más grande de un polígono](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)

### <a name="unity-step-9-work-through-your-input-model"></a>Unity paso 9: trabajar a través del modelo de entrada

Cada juego o aplicación que tiene como destino un HMD existente tendrá un conjunto de entradas que controla, los tipos de entradas que necesita para la experiencia y las API específicas a las que llama para obtener esas entradas. Hemos invertido en intentar que sea tan sencillo y sencillo como sea posible para aprovechar las ventajas de las entradas disponibles en Windows Mixed Reality.
1. Lea la **[Guía de portabilidad de entrada para Unity](input-porting-guide-for-unity.md)** para obtener más información sobre cómo Windows Mixed Reality expone entradas y cómo se asigna a lo que la aplicación puede hacer hoy.
2. Decida si va a usar la API de entrada de SDK entre las plataformas de la de Unity o la API de entrada específica de la MR. Las API Input. GetButton/Input. GetAxis generales se usan en las aplicaciones de Unity VR hoy en día para [Oculus INPUT](https://docs.unity3d.com/Manual/OculusControllers.html) y [OpenVR INPUT](https://docs.unity3d.com/Manual/OpenVRControllers.html). Si las aplicaciones ya usan estas API para los controladores de movimiento, esta es la ruta más sencilla; debe volver a asignar botones y ejes en el administrador de entrada.
    * Puede tener acceso a los datos del controlador de movimiento en Unity mediante las API de entrada. GetButton/Input. GetAxis generales de la unidad de vídeo, o bien las API UnityEngine. XR. WSA.. (anteriormente en el espacio de nombres UnityEngine. XR. WSA. Input en Unity 5,6)
    * Vea el [ejemplo del kit de herramientas](https://github.com/Microsoft/HoloToolkit-Unity/pull/572) que combina controladores de mandos y de movimiento.

### <a name="unity-step-10-performance-testing-and-tuning"></a>Unity paso 10: pruebas y ajuste del rendimiento

Windows Mixed Reality estará disponible en una amplia gama de dispositivos, que abarcan desde equipos de juegos de alta gama, hasta grandes equipos estándar de mercado. En función del mercado de destino, hay una diferencia significativa en los presupuestos de proceso y gráficos disponibles para la aplicación. Durante este proceso de migración, es probable que se esté aprovechando un equipo Premium y que haya presupuestos de cálculo y gráficos significativos disponibles para la aplicación. Si quiere que la aplicación esté disponible para un público más amplio, debe probar y generar el perfil de la aplicación en [el hardware representativo que](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)quiere usar como destino.

Tanto [Unity](https://docs.unity3d.com/Manual/Profiler.html) como [Visual Studio](https://docs.microsoft.com/visualstudio/profiling/index) incluyen los generadores de rendimiento y las directrices de publicación de [Microsoft](understanding-performance-for-mixed-reality.md) e [Intel](https://software.intel.com/articles/vr-content-developer-guide) sobre la optimización y la generación de perfiles de rendimiento. Hay una explicación exhaustiva del rendimiento disponible al [comprender el rendimiento de la realidad mixta](understanding-performance-for-mixed-reality.md). Además, hay detalles específicos para Unity en [recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md).

## <a name="see-also"></a>Consulte también
* [Guía de portabilidad de entrada para Unity](input-porting-guide-for-unity.md)
* [Instrucciones de compatibilidad de hardware de equipo mínima de Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Descripción del rendimiento de la realidad mixta](understanding-performance-for-mixed-reality.md)
* [Recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md)
* [Incorporación del soporte técnico de Xbox Live a Unity para UWP](https://docs.microsoft.com/windows/uwp/xbox-live/get-started-with-partner/partner-add-xbox-live-to-unity-uwp)
