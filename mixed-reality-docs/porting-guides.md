---
title: Guías de migración
description: Un tutorial paso a paso que explican cómo trasladar una aplicación envolvente existente a Windows Mixed Reality.
author: ChimeraScorn
ms.author: cwhite
ms.date: 10/02/2018
ms.topic: article
keywords: puerto, portabilidad, unity, middleware, motor, UWP
ms.openlocfilehash: a4a8c78f1c45fd8e3b85a767d139bae9f67540e0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602178"
---
# <a name="porting-guides"></a>Guías de migración

> [!NOTE]
> Obtener información más específica de HoloLens 2 [próximamente](index.md#news-and-notes).

Windows 10 incluye compatibilidad con auriculares envolventes y holográficas directamente. Si ha creado el contenido de otro dispositivo, como el ejemplo Oculus Rift o HTC Vive, estos tienen dependencias en las bibliotecas que existen por encima de la API de la plataforma del sistema operativo. Llevar el contenido existente de a Windows Mixed Reality implica el uso de estos otros SDK a la API de Windows de redestinación. El [API de plataforma de Windows para mixed reality](https://docs.microsoft.com/uwp/api/Windows.Perception) solo funcionan en el modelo de aplicación de plataforma Universal de Windows (UWP). Por lo que si ya no se compila la aplicación para UWP, portabilidad a UWP será parte de la experiencia de migración.

## <a name="porting-overview"></a>Información general de migración

En un nivel alto, estos son los pasos necesarios para migrar contenido existente:
1. **Asegúrese de que el equipo ejecuta el Windows 10 Fall Creators Update (16299).** Ya no recomendamos recibir la versión preliminar se basa en el anillo Insider Saltar adelante, como las compilaciones no será más estable para el desarrollo de realidad mixta.
2. **Actualice a la versión más reciente del motor de juego o gráficos.** Motores de juegos deberá ser compatible con el SDK de Windows 10 versión 10.0.15063.0 (lanzado en abril de 2017) o superior.
3. **Actualice cualquier software intermedio, complementos o componentes.** Si la aplicación contiene todos los componentes, es una buena idea actualizar a la versión más reciente. Las versiones más recientes de los complementos más comunes son compatibles con UWP.
4. **Quitar las dependencias de SDK duplicados**. Dependiendo de qué dispositivo estaba apuntando su contenido, deberá quitar o compilar condicionalmente ese SDK (por ejemplo, SteamVR) para poder dirigirlas a las API de Windows en su lugar.
5. **Trabajar con problemas de compilación.** En este momento, el ejercicio de migración es específico para la aplicación, el motor y las dependencias del componente que tiene.

## <a name="common-porting-steps"></a>Pasos comunes de migración

### <a name="common-step-1-make-sure-you-have-the-right-development-hardware"></a>Common paso 1: Asegúrese de que tiene el hardware de desarrollo correctas

El [instalar las herramientas de](install-the-tools.md#for-immersive-vr-headset-development) página enumera el hardware recomendado de desarrollo.

### <a name="common-step-2-upgrade-to-the-latest-flight-of-windows-10"></a>Common paso 2: Actualizar a la caja más reciente de Windows 10

La plataforma Windows Mixed Reality está aún en desarrollo activo, y para que sea más eficaz, se recomienda que se está en vuelo "Fast Insider de Windows". Para tener acceso a los vuelos de windows, deberá [Únase al programa de Windows Insider](https://insider.windows.com/).
1. Instalar el [Windows 10 Creators Update](https://www.microsoft.com/software-download/windows10)
2. [Únase a](https://insider.windows.com/) al programa Insider de Windows.
3. Habilitar [modo de programador](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)
4. Cambie a la [Windows Insider rápido vuelos](https://blogs.technet.microsoft.com/uktechnet/2016/07/01/joining-insider-preview) a través de configuración--> sección de seguridad y actualización

### <a name="common-step-3-upgrade-to-the-most-recent-build-of-visual-studio"></a>Common paso 3: Actualizar a la compilación más reciente de Visual Studio
* Consulte [instalar las herramientas de](install-the-tools.md#installation-checklist) página en Visual Studio 2017

### <a name="common-step-4-be-ready-for-the-store"></a>Common paso 4: Prepárese para el Store
* Use [Windows App Certification Kit](https://developer.microsoft.com/windows/develop/app-certification-kit) (también conocido como WACK) pronto y con frecuencia.
* Use [analizador de portabilidad](https://docs.microsoft.com/dotnet/standard/portability-analyzer) ([descargar](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer))

### <a name="common-step-5-choose-the-correct-adapter"></a>Common paso 5: Elija el adaptador correcto
* En sistemas como equipos portátiles con dos GPU, [tener como destino el adaptador correcto](rendering-in-directx.md#hybrid-graphics-pcs-and-mixed-reality-applications). Esto se aplica a las aplicaciones de Unity, además a las aplicaciones DirectX nativas, donde se crea un ID3D11Device, explícita o implícitamente (Media Foundation), para su funcionalidad.

## <a name="unity-porting-guidance"></a>Guía de portabilidad de Unity

### <a name="unity-step-1-follow-the-common-porting-steps"></a>Paso 1 de Unity: Siga los pasos de migración comunes

Siga todos los pasos comunes. En el paso 3 #, seleccione el **desarrollo de juegos con Unity** carga de trabajo. Puede anular la selección el componente opcional del Editor de Unity desde que se va a instalar una versión más reciente de Unity siguiendo las instrucciones.

### <a name="unity-step-2-upgrade-to-the-latest-public-build-of-unity-with-windows-mr-support"></a>Paso 2 de Unity: Actualizar a la compilación pública más reciente de Unity con el soporte técnico de Windows MR
1. Descargue la última versión [recomienda las compilación pública de Unity](install-the-tools.md) con la realidad mixta admite.
2. Guardar una copia del proyecto antes de comenzar
3. Revise el [documentación](https://docs.unity3d.com/Manual/UpgradeGuides.html) disponible desde Unity en la migración.
4. Siga el [instrucciones](https://docs.unity3d.com/Manual/APIUpdater.html) en el sitio de Unity para usar su actualizador automático de API
5. Compruebe si hay cambios adicionales que deba realizar para que el proyecto que está ejecutando y trabajar a través de los errores y advertencias restantes. Nota: Si tiene software intermedio que depende, deberá actualizar ese middleware para empezar a utilizar (más detalles en el paso 3 siguiente).

### <a name="unity-step-3-upgrade-your-middleware-to-the-latest-versions"></a>Paso 3 de Unity: Actualizar su middleware a las versiones más recientes

Con cualquier actualización de Unity, hay muchas posibilidades de que se deben actualizar uno o varios paquetes de software intermedio que depende de su juego o aplicación. Además, la versión más reciente de todos su middleware, aumentará la probabilidad de éxito en el resto del proceso de migración. Muchos paquetes de middleware recientemente han agregado compatibilidad para la plataforma Universal de Windows (UWP), y la actualización a las versiones más recientes le permitirá aprovechar ese trabajo.

### <a name="unity-step-4-target-your-application-to-run-on-universal-windows-platform-uwp"></a>Paso 4 de Unity: Destino de la aplicación se ejecute en la plataforma Universal de Windows (UWP)

Después de instalar las herramientas, deberá obtener la aplicación que se ejecuta como una aplicación Windows Universal.
* Siga el [tutorial paso a paso detallado](https://unity3d.com/partners/microsoft/porting-guides) proporcionado por Unity. Tenga en cuenta que deben permanecer en la versión más reciente de LTS (cualquier versión 20xx.4) para Windows MR.
* Para obtener más recursos de desarrollo de UWP, eche un vistazo a la [Guía de desarrollo de juegos de Windows 10](https://docs.microsoft.com/windows/uwp/gaming/e2e).
* Tenga en cuenta que Unity continúa mejorando la compatibilidad con IL2CPP; IL2CPP facilita algunas UWP puertos significativamente. Si desea usar el scripting de back-end de .net actualmente, considere la posibilidad de convertir para aprovechar el back-end IL2CPP en su lugar.

Nota: Si la aplicación tiene dependencias de servicios específicos del dispositivo, por ejemplo, coincidencia que hace de vapor, debe deshabilitarlo en este paso. En un momento posterior, puede enlazar a los servicios equivalente que proporciona Windows.

### <a name="unity-step-5-deprecated"></a>Paso 5 de Unity: (En desuso)

Paso 5 ya no es necesario. Nos estamos dejándolo aquí para que la indización de los pasos sigue siendo el mismo.

### <a name="unity-step-6-get-your-windows-mixed-reality-hardware-set-up"></a>Paso 6 de Unity: Obtener el configuración de hardware de Windows Mixed Reality
1. Lea los pasos [instalación auriculares envolventes](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/before-you-start
)
2. Obtenga información sobre [mediante el simulador de Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md) y [navegar por la página principal de Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)

### <a name="unity-step-7-target-your-application-to-run-on-windows-mixed-reality"></a>Paso 7 de Unity: Destino de la aplicación se ejecute en Windows Mixed Reality
1. En primer lugar, debe quitar o compilar condicionalmente compatibilidad de biblioteca específicas para un determinado VR SDK. Esos recursos cambian con frecuencia la configuración y las propiedades en el proyecto de maneras que no son compatibles con otros SDK de realidad virtual, como Windows Mixed Reality.
    * Por ejemplo, si el proyecto hace referencia al SDK de SteamVR, deberá actualizar el proyecto para excluir esas prefabricados y llamadas de API de secuencia de comandos al exportar para el destino de compilación de Windows Store.
    * Los pasos específicos para excluir condicionalmente otros SDK VR estará disponible próximamente.
2. En el proyecto de Unity, [tener como destino el SDK de Windows 10](holograms-100.md#target-windows-10-sdk)
3. Para cada escena, [programa de instalación de la cámara](holograms-100.md#chapter-2---setup-the-camera)

### <a name="unity-step-8-use-the-stage-to-place-content-on-the-floor"></a>Paso 8 de Unity: Use el escenario para colocar contenido en el suelo

Puede crear experiencias de realidad mixta en una amplia gama de [experimentar escalas](coordinate-systems.md).

Si está migrando un **escala asentada experiencia**, debe asegurarse de Unity se establece en el **estacionarios** tipo de espacio de seguimiento:

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

Esto establece el sistema de coordenadas de Unity para realizar un seguimiento el [marco estático de referencia](coordinate-systems.md#spatial-coordinate-systems). En el modo de seguimiento inmóvil, se coloca el contenido en el editor justo delante de la ubicación predeterminada de la cámara (hacia delante es -Z) aparecerá delante del usuario cuando se inicia la aplicación. Para volver a centrar el usuario del asentada origen, puede llamar a Unity [XR. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) método.

Si está migrando un **permanente escala experiencia** o **experiencia sala escala**, que se colocará contenido en relación con el límite inferior. Razonar el usuario floor utilizando el  **[fase espacial](coordinate-systems.md#spatial-coordinate-systems)**, que representa el usuario definidas por el origen del nivel del suelo y límite de espacio opcional, configurar durante la primera ejecución. Para estas experiencias, debe asegurarse de Unity se establece en el **RoomScale** tipo de espacio de seguimiento. Aunque RoomScale es el valor predeterminado, querrá establecer de forma explícita y asegurarse de que obtendrá atrás es true, para detectar situaciones donde el usuario desplazó a su equipo fuera de la sala que calibran:

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

Una vez que la aplicación establece correctamente el tipo de espacio, contenido colocado en la y de seguimiento de RoomScale = 0 plano aparecerá en el suelo. El origen en (0, 0, 0) será la ubicación específica en el suelo donde puede levantar el usuario durante la instalación de la sala, con -Z que representa la dirección de avance que se enfrentan durante la instalación.

En el código de script, puede, a continuación, llame al método TryGetGeometry para usted es el tipo de UnityEngine.Experimental.XR.Boundary para obtener un polígono límites, especificar un tipo de límite de TrackedArea. Si el usuario ha definido un límite (obtener una lista de vértices), sabrá que es segura entregar un **experiencia sala escala** al usuario, donde puede guían por la escena crear.

Tenga en cuenta que el sistema automáticamente se representará el límite cuando el usuario se aproxima a él. La aplicación no necesita usar este polígono para representar el límite de sí mismo.

Para obtener más información, consulte el [sistemas de coordenadas en Unity](coordinate-systems-in-unity.md) página.

Algunas aplicaciones usan un rectángulo para restringir su interacción. Recuperar el rectángulo más grande inscrito no es directamente compatible en la API de UWP o Unity. El código de ejemplo vinculada a siguiente se muestra cómo buscar un rectángulo dentro de los límites se realiza el seguimiento. Es heurística según por lo que no se puede encontrar la solución óptima, sin embargo, los resultados son coherentes con las expectativas. Para obtener resultados más precisos a costa de tiempo de procesamiento se pueden ajustar parámetros en el algoritmo. El algoritmo que se encuentra en una bifurcación del Kit de herramientas realidad mixta que usa la versión MRTP de Unity 5.6 la versión preliminar. Esto no está disponible públicamente. El código debe ser utilizable en las versiones de Unity 2017.2 y versiones posteriores. El código se puede portar al MRTK actual en un futuro próximo.

[archivo zip de código en GitHub](https://github.com/KevinKennedy/MixedRealityToolkit-Unity/releases/tag/5.6.MRTP20) archivos importantes:
* Assets/HoloToolkit/Stage/Scripts/StageManager.cs: ejemplo de uso
* Assets/HoloToolkit/Stage/Scripts/LargestRectangle.cs - implementación del algoritmo
* Assets/HoloToolkit-UnitTests/Editor/Stage/LargestRectangleTest.cs - prueba trivial del algoritmo

Ejemplo de resultados:

![Ejemplo de resultados](images/largestrectangle-400px.jpg)

Algoritmo se basa en un blog por Daniel Smilkov: [Rectángulo más grande en un polígono](https://d3plus.org/blog/behind-the-scenes/2014/07/08/largest-rect/)

### <a name="unity-step-9-work-through-your-input-model"></a>Paso 9 de Unity: Trabajar con el modelo de entrada

Cada juego o aplicación destinada a un HMD existente tendrá un conjunto de entradas que controla, tipos de entradas que necesita para la experiencia y las API específicas que llama para obtener esas entradas. Hemos invertido en intentar que resulte como simple y sencillo como sea posible para aprovechar las ventajas de las entradas disponibles en Windows Mixed Reality.
1. Lea la **[entrada trasladar guía para Unity](input-porting-guide-for-unity.md)** para obtener más información sobre cómo Windows Mixed Reality expone la entrada, y cómo se asignan a acciones de la aplicación puede hacerlo hoy mismo.
2. Elija si va a aprovechar la API de entrada de Unity entre-VR-SDK o API de entrada específico del SR. Las API de Input.GetButton/Input.GetAxis general se usan hoy en día para las aplicaciones de Unity VR [Oculus entrada](https://docs.unity3d.com/Manual/OculusControllers.html) y [OpenVR entrada](https://docs.unity3d.com/Manual/OpenVRControllers.html). Si las aplicaciones ya usan estas API para los controladores de movimiento, ésta es la ruta más sencilla: que deba volver a asignar los botones y los ejes en el Administrador de entrada.
    * Puede tener acceso a los datos del controlador de movimiento en Unity utilizando general entre-VR-SDK Input.GetButton/Input.GetAxis API o el Sr. UnityEngine.XR.WSA.Input APIs específicas. (anteriormente en el espacio de nombres UnityEngine.XR.WSA.Input Unity 5.6)
    * Consulte la [ejemplo Kit de herramientas de](https://github.com/Microsoft/HoloToolkit-Unity/pull/572) que combina los controladores de gamepad y movimiento.

### <a name="unity-step-10-performance-testing-and-tuning"></a>Paso 10 de Unity: Las pruebas de rendimiento y optimización

Windows Mixed Reality se esté disponible en una clase amplio de dispositivos, que abarcan desde alta terminar los PC de juegos, hasta amplio mercado estándar en los equipos. Dependiendo de qué mercado tiene como destino, hay una diferencia significativa en los presupuestos de proceso y gráficos disponibles para su aplicación. Durante este ejercicio de migración, es probable que aprovecha un PC premium y han tenido significativo presupuestos de proceso y gráficos disponibles para la aplicación. Si desea que su aplicación esté disponible para un público más amplio, debe probar y generar perfiles de la aplicación en [el hardware representativo que desee para target](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).

Ambos [Unity](https://docs.unity3d.com/Manual/Profiler.html) y [Visual Studio](https://docs.microsoft.com/visualstudio/profiling/index) incluyen los generadores de perfiles de rendimiento y ambos [Microsoft](understanding-performance-for-mixed-reality.md) y [Intel](https://software.intel.com/articles/vr-content-developer-guide) publicar instrucciones en generación de perfiles de rendimiento y optimización. Hay una amplia información de rendimiento en [análisis de rendimiento para Mixed Reality](understanding-performance-for-mixed-reality.md). Además, hay detalles específicos para Unity en [recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md).

## <a name="see-also"></a>Vea también
* [Entrada de portabilidad de guía para Unity](input-porting-guide-for-unity.md)
* [Directrices para compatibilidad de hardware mínimas PC de Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
* [Análisis de rendimiento de la realidad mixta](understanding-performance-for-mixed-reality.md)
* [Recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md)
* [Agregar compatibilidad de Xbox Live a Unity para UWP](https://docs.microsoft.com/windows/uwp/xbox-live/get-started-with-partner/partner-add-xbox-live-to-unity-uwp)
