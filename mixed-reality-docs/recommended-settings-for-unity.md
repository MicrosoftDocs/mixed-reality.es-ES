---
title: Configuración recomendada para Unity
description: Unity ofrece algunos comportamientos específicos de la realidad mixta que se pueden alternar a través de la configuración del proyecto.
author: troy-ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: Unity, configuración, realidad mixta
ms.openlocfilehash: 9b4e04e10e95f6c4f12a25a6f34236d9d2bf99a2
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278013"
---
# <a name="recommended-settings-for-unity"></a>Configuración recomendada para Unity

Unity proporciona un conjunto de opciones predeterminadas que suelen ser el caso promedio de todas las plataformas. Sin embargo, Unity ofrece algunos comportamientos específicos de la realidad mixta que se pueden alternar a través de la configuración del proyecto.

## <a name="performant-environment-set-up"></a>Configuración del entorno de rendimiento

### <a name="low-quality-settings"></a>Configuración de baja calidad

Es importante modificar la configuración de **calidad de Unity** de su entorno a **muy baja**. Esto ayudará a garantizar que la aplicación se ejecute de forma adecuada en la velocidad de fotogramas apropiada. Esto es muy importante para el desarrollo de HoloLens. Para el desarrollo en auriculares inmersivo, en función de las especificaciones del escritorio que se enciende en la experiencia de VR, todavía se puede lograr una velocidad de fotogramas sin los parámetros de calidad más bajos.

En Unity 2018 LTS +, el nivel de calidad del proyecto se puede establecer de la siguiente manera:

En **editar** > **configuración del proyecto** > **calidad** > establezca el **valor predeterminado** haciendo clic en la flecha hacia abajo hasta el nivel de calidad **muy bajo** .

### <a name="lighting-settings"></a>Configuración de iluminación

Similar a la configuración de la escena de calidad, es importante establecer una configuración de iluminación óptima para la aplicación de realidad mixta. En Unity, la configuración de iluminación que normalmente tendrá el mayor impacto en el rendimiento de la escena es la **iluminación global en tiempo real**. Para desactivarlo, vaya a **ventana** > **representación** de > **configuración de iluminación** > **iluminación global en tiempo real**.

Hay otro valor de iluminación, **iluminación global horneada**. Esta configuración puede proporcionar resultados visualmente impactantes y sorprendentes en auriculares envolventes, pero generalmente no es aplicable para el desarrollo de HoloLens. La **Illumniation global cocida** solo se calcula para GameObjects estáticas que normalmente no se encuentran en escenas de HoloLens debido a la naturaleza de un entorno desconocido y cambiante.

Lea la [iluminación global desde Unity](https://docs.unity3d.com/Manual/GIIntro.html) para obtener más información. 

>[!NOTE]
> La **iluminación global en tiempo real** se establece **por escena** y, por lo tanto, los desarrolladores deben guardar esta propiedad para cada escena de Unity en su proyecto.

### <a name="single-pass-instancing-rendering-path"></a>Ruta de representación de instancia de un solo paso

En las aplicaciones de realidad mixta, la escena se representa dos veces, una vez para cada ojo al usuario. En comparación con el desarrollo 3D tradicional, esto duplica efectivamente la cantidad de trabajo que se debe calcular. Por lo tanto, es importante seleccionar la ruta de acceso de representación más eficaz en Unity para ahorrar en el tiempo de CPU y GPU. La representación con instancia de un solo paso optimiza la canalización de representación de Unity para aplicaciones de realidad mixta y, por lo tanto, se recomienda habilitar esta opción de forma predeterminada para cada proyecto.

Para habilitar esta característica en el proyecto de Unity

1)  Abre **Player XR Settings** (Configuración del reproductor XR) (ve a **Editar** > **Configuración del proyecto** > **Reproductor** > **XR Settings** [Configuración de XR]).
2) Selecciona **Single Pass Instanced** (Con instancia de un solo paso) en el menú desplegable **Stereo Rendering Method** (Método de representación en estéreo) (la casilla **Virtual Reality Supported** [Compatibilidad con realidad virtual] debe estar marcada)

Lea los siguientes artículos de Unity para obtener más información sobre este enfoque de representación.

- [Cómo maximizar el rendimiento de AR y VR con la representación en estéreo avanzada](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [Creación de instancias de un solo paso](https://docs.unity3d.com/Manual/SinglePassInstancing.html)

>[!NOTE]
> Un problema común con la representación con instancia de un solo paso se produce si los desarrolladores ya tienen sombreadores personalizados no escritos para la creación de instancias. Después de habilitar esta característica, los desarrolladores pueden observar que algunos objetos GameObjects solo se representan en un ojo. Esto se debe a que los sombreadores personalizados asociados no tienen las propiedades adecuadas para la creación de instancias.
>
> Consulta [Representación en estéreo de un solo paso para HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) de Unity para solucionar este problema.

### <a name="enable-depth-buffer-sharing"></a>Habilitar uso compartido de búfer de profundidad

Para lograr una mejor estabilidad del holograma a partir de la percepción del usuario, se recomienda habilitar la propiedad de **uso compartido del búfer de profundidad** en Unity. Al activar esta función, Unity compartirá el mapa de profundidad producido por la aplicación con la plataforma Windows Mixed Reality. La plataforma podrá optimizar mejor la estabilidad de los hologramas específicamente para la escena de cualquier fotograma determinado que se represente en la aplicación.

Para habilitar esta característica en el proyecto de Unity

1) Abre **Player XR Settings** (Configuración del reproductor XR) (ve a **Editar** > **Configuración del proyecto** > **Reproductor** > **XR Settings** [Configuración de XR]).
2) Active la casilla **Habilitar uso compartido de búfer de profundidad** en SDK de **realidad virtual** > la expansión de la **realidad mixta de Windows** (se debe activar la casilla se admite la**realidad virtual** )

Además, se recomienda seleccionar profundidad de **16 bits** en la configuración de **formato de profundidad** de este panel, especialmente para el desarrollo de HoloLens. Si selecciona 16 bits en comparación con 24 bits, se reducirán significativamente los requisitos de ancho de banda, ya que será necesario desplace o procese menos datos.

Para que la plataforma Windows Mixed Reality optimice la estabilidad del holograma, se basa en el búfer de profundidad para que sea preciso y coincida con cualquier holograma representado en la pantalla. Por lo tanto, con el uso compartido de búfer de profundidad en, es importante al representar el color, para representar también la profundidad. En Unity, la mayoría de los materiales opacos o TransparentCutouts representarán la profundidad de forma predeterminada, pero los objetos transparentes y de texto no suelen representar la profundidad, aunque esto es dependiente del sombreador, etc.

Si usa el [sombreador estándar del kit de herramientas de realidad mixta](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md), para representar la profundidad de los objetos transparentes:

1) Seleccione el material transparente que usa el sombreador estándar de MRTK y abra la ventana del editor del inspector.
2) Seleccione el botón **corregir ahora** dentro de la advertencia de uso compartido de búfer de profundidad. Esto también puede realizarse manualmente si se establece el **modo de representación** en **personalizado**; a continuación, establezca el **modo** en **transparente** y, por último, establezca **escritura de profundidad** en **activado** .

> [!IMPORTANT]
> Los desarrolladores deben tener cuidado con las supuestos Z al cambiar estos valores junto con la configuración de plano Near/Far de la cámara. La lucha por Z se produce cuando dos GameObjects intentan representarse en el mismo píxel y debido a las limitaciones de la fidelidad del búfer de profundidad (es decir, profundidad z), Unity no puede discernir qué objeto está delante del otro. Los desarrolladores notarán un parpadeo entre dos objetos de juego mientras *luchan* por el mismo valor de profundidad z. Esto se puede resolver cambiando al formato de profundidad de 24 bits, ya que habrá un intervalo mayor de valores para cada objeto que se va a calcular en función de la profundidad de z de la cámara.
>
> Sin embargo, se recomienda, especialmente para el desarrollo de HoloLens, modificar los planos cercanos y alejados de la cámara a un intervalo más pequeño en su lugar y conservar el formato de profundidad de 16 bits. La profundidad z no se asigna linealmente al intervalo de valores de los planos de cámara cercanos y alejados. Para modificarlo, seleccione la *cámara principal* de la escena y, en **Inspector**, cambie los valores **cercanos & plano de recorte lejano** para reducir su rango (es decir, de 1000 a 100m u otro valor x, etc.)

>[!IMPORTANT]
> [Unity no crea un búfer de estarcido](https://docs.unity3d.com/ScriptReference/RenderTexture-depth.html) cuando se usa el formato de profundidad de 16 bits. Por lo tanto, algunos efectos de la interfaz de usuario de Unity y otros efectos necesarios de la galería de símbolos no funcionarán a menos que se seleccione formato de profundidad de 24 bits, lo que creará un [búfer de estarcido de 8 bits](https://docs.unity3d.com/Manual/SL-Stencil.html).

### <a name="building-for-il2cpp"></a>Compilar para IL2CPP

Unity ha dejado de admitir el back-end de scripting de .NET y, por tanto, recomienda que los desarrolladores usen **IL2CPP** para sus compilaciones de Visual Studio de UWP. Aunque esto aporta varias ventajas, la compilación de la solución de Visual Studio desde Unity para **Il2CPP** puede ser significativamente más lenta que el anterior método de .net. Por lo tanto, se recomienda encarecidamente seguir los procedimientos recomendados para crear **IL2CPP** para ahorrar en el tiempo de iteración de desarrollo.

1) Aproveche las compilaciones incrementales compilando el proyecto en el mismo directorio cada vez, reutilizando los archivos creados previamente
2) Deshabilitar exámenes de software antimalware para el proyecto & carpetas de compilación
   - Abrir **protección contra amenazas de Virus &** en la aplicación de configuración de Windows 10
   - Seleccione **Administrar configuración** en **configuración de protección contra amenazas de virus &**
   - Seleccione **Agregar o quitar exclusiones** en la sección **exclusiones** .
   - Haga clic en **Agregar una exclusión** y seleccione la carpeta que contiene el código del proyecto de Unity y las salidas de compilación.
3) Uso de SSD para compilar

Consulte optimización de los [tiempos de compilación de IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) para obtener más información.

> [!NOTE]
> Además, puede resultar útil configurar un [servidor de caché](https://docs.unity3d.com/Manual/CacheServer.html), especialmente para los proyectos de Unity con una gran cantidad de activos (sin contar con los archivos de script), o que cambien constantemente de escenas o activos. Al abrir un proyecto, Unity almacena los activos aplicables en un formato de la memoria caché interna en la máquina del desarrollador. Los elementos se tienen que volver a importar y, por tanto, volver a procesar cuando se modifican. Este proceso se puede realizar una vez y guardar en un servidor de caché, de esta forma se comparte con otros desarrolladores, lo que ahorra tiempo al evitar que cada desarrollador tenga que procesar localmente los nuevos cambios que reimporte.

## <a name="publishing-properties"></a>Propiedades de publicación

### <a name="holographic-splash-screen"></a>Pantalla de presentación holográfica

HoloLens tiene una CPU y una GPU de clase móvil, lo que significa que las aplicaciones pueden tardar un poco más en cargarse. Mientras se carga la aplicación, los usuarios solo verán el color negro y, por lo tanto, se les preguntará lo que está ocurriendo. Para garantizar la carga, puede Agregar una pantalla de presentación holográfica.

Para alternar la pantalla de presentación de Holographic:

1) Vaya a **editar** > **configuración del proyecto** > página del **reproductor**
2) Haga clic en la pestaña **tienda Windows** y abra la sección **imagen de bienvenida** .
3) Aplique la imagen deseada en la propiedad **imagen de bienvenida de Windows holographic > Holographic** .
    - Al alternar la opción **Mostrar pantalla de presentación de Unity** , se habilitará o deshabilitará la pantalla de presentación con la marca Unity. Si no tiene una licencia de Unity Pro, siempre se mostrará la pantalla de presentación con la marca Unity.
    - Si se aplica una **imagen de bienvenida holográfica** , se mostrará siempre independientemente de si la casilla Mostrar la pantalla de presentación de Unity está habilitada o deshabilitada. La especificación de una imagen de bienvenida holográfica personalizada solo está disponible para los desarrolladores con una licencia de la versión Pro de Unity.

|  Pantalla de presentación de mostrar Unity  |  Imagen de bienvenida holográfica  |  Comportamiento |
|----------|----------|----------|
|  Activado  |  Ninguno  |  Mostrar la pantalla de presentación predeterminada de Unity durante 5 segundos o hasta que se cargue la aplicación, lo que sea más largo. |
|  Activado  |  Personalizar  |  Mostrar la pantalla de presentación personalizada durante 5 segundos o hasta que se cargue la aplicación, lo que sea más largo. |
|  Desactivar  |  Ninguno  |  Mostrar negro transparente (nada) hasta que se cargue la aplicación. |
|  Desactivar  |  Personalizar  |  Mostrar la pantalla de presentación personalizada durante 5 segundos o hasta que se cargue la aplicación, lo que sea más largo. |

Lea [la documentación de la pantalla de presentación de Unity](https://docs.unity3d.com/Manual/class-PlayerSettingsSplashScreen.html) para obtener más información.

### <a name="tracking-loss"></a>Pérdida de seguimiento

Un casco de realidad mixta depende de ver el entorno que lo rodea para construir [sistemas de coordenadas de bloqueo mundial](coordinate-systems-in-unity.md), que permiten que los hologramas permanezcan en la posición. Cuando el casco no puede encontrarse en el mundo, se dice que el casco ha *perdido el seguimiento*. En estos casos, la funcionalidad que depende de los sistemas de coordenadas de bloque mundial, como las fases espaciales, los delimitadores espaciales y la asignación espacial, no funcionan.

Si se produce una pérdida de seguimiento, el comportamiento predeterminado de Unity es detener la representación de los hologramas, pausar el [bucle de juego](https://docs.unity3d.com/Manual/ExecutionOrder.html)y mostrar una notificación de pérdida de seguimiento que siga de forma cómoda a los usuarios. También se pueden proporcionar notificaciones personalizadas en forma de una imagen de pérdida de seguimiento. En el caso de las aplicaciones que dependen del seguimiento de toda su experiencia, es suficiente para que Unity la controle completamente hasta que se recupere el seguimiento. Los desarrolladores pueden proporcionar una imagen personalizada que se mostrará durante la pérdida de seguimiento.

Para personalizar la imagen de seguimiento perdida:

1) Vaya a **editar** > **configuración del proyecto** > página del **reproductor**
2) Haga clic en la pestaña **tienda Windows** y abra la sección **imagen de bienvenida** .
3) Aplique la imagen deseada en la propiedad **imagen de pérdida de seguimiento de > de Windows Holographic** .

#### <a name="opt-out-of-automatic-pause"></a>No participar en la pausa automática

Es posible que algunas aplicaciones no requieran seguimiento (por ejemplo, [aplicaciones solo de orientación](coordinate-systems-in-unity.md) como los visores de vídeo de 360 bits) o que necesiten continuar el procesamiento sin interrupciones mientras se pierde el seguimiento. En estos casos, las aplicaciones pueden rechazar la pérdida predeterminada del comportamiento de seguimiento. Los desarrolladores que elijan esto son responsables de ocultar o deshabilitar los objetos que no se representarán correctamente en un escenario de pérdida de seguimiento. En la mayoría de los casos, el único contenido que se recomienda que se represente en ese caso es contenido bloqueado por el cuerpo, centrado en torno a la cámara principal.

Para no participar en el comportamiento de pausa automática:

1) Vaya a la página **editar** > **configuración del proyecto** > **Player** .
2) Haga clic en la pestaña **tienda Windows** y abra la sección **imagen de bienvenida** .
3) Modifique la casilla **de verificación de Windows Holographic > en el seguimiento de pérdida y Mostrar imagen** .

#### <a name="tracking-loss-events"></a>Seguimiento de eventos de pérdida

Para definir el comportamiento personalizado cuando se pierde el seguimiento, controle los [eventos de pérdida de seguimiento](tracking-loss-in-unity.md)global.

### <a name="capabilities"></a>Capacidades

Para que una aplicación aproveche ciertas funciones, debe declarar las capacidades adecuadas en su manifiesto. Las declaraciones de manifiesto se pueden realizar en Unity para que se incluyan en cada exportación de proyecto subsiguiente.

Las capacidades se pueden habilitar para una aplicación de realidad mixta:

1) Vaya a **editar** > **configuración del proyecto** > página del **reproductor**
2) Haga clic en la pestaña **tienda Windows** , abra la sección **configuración de publicación** y busque la lista de **capacidades** .

Las funcionalidades aplicables para habilitar las API de uso frecuente para aplicaciones holográficas son:
<br>

|  Capability  |  API que requieren funcionalidad |
|----------|----------|
|  SpatialPerception  |  SurfaceObserver |
|  Web  |  Fotocaptura y videocaptura |
|  PicturesLibrary/VideosLibrary  |  Fotocaptura o videocaptura, respectivamente (al almacenar el contenido capturado) |
|  Micrófono  |  VideoCapture (al capturar audio), DictationRecognizer, GrammarRecognizer y KeywordRecognizer |
|  InternetClient  |  DictationRecognizer (y para usar el generador de perfiles de Unity) |

## <a name="see-also"></a>Vea también

* [Introducción al desarrollo de Unity](unity-development-overview.md)
* [Análisis de rendimiento de la realidad mixta](understanding-performance-for-mixed-reality.md)
* [Recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md)
