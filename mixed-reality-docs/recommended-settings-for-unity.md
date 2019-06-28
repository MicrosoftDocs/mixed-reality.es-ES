---
title: Configuración recomendada para Unity
description: Unity ofrece algunos comportamientos específicos de realidad mixta que puede alternar mediante la configuración del proyecto.
author: Troy-Ferrell
ms.author: trferrel
ms.date: 03/26/2019
ms.topic: article
keywords: Unity, la configuración, la realidad mixta
ms.openlocfilehash: 8afcefb49a860d66a372ebd3d0c4bcdb43038813
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67415449"
---
# <a name="recommended-settings-for-unity"></a>Configuración recomendada para Unity

Unity proporciona un conjunto de opciones predeterminadas que suelen ser el caso promedio para todas las plataformas. Sin embargo, Unity ofrece algunos comportamientos específicos de realidad mixta que puede alternar mediante la configuración del proyecto.

## <a name="performant-environment-set-up"></a>Configuración del entorno de alto rendimiento

### <a name="low-quality-settings"></a>Configuración de baja calidad

Es importante modificar el **configuración de calidad de Unity** de su entorno para **Very Low**. Esto le ayudará a asegurarse de que la aplicación se está ejecutando el modo más eficaz en la velocidad de fotogramas adecuada. Esto es muy importante para el desarrollo de Hololens. Para el desarrollo en inmersivos, según las especificaciones del escritorio potenciar la experiencia de realidad virtual, uno puede conseguir aún framerate sin los parámetros de calidad más bajos. 

En Unity 2018 LTS +, el nivel de calidad del proyecto puede establecerse mediante:

En **editar** > **configuración del proyecto** > **calidad** > Establezca el **predeterminado** haciendo clic en el la flecha hacia abajo a la **Very Low** nivel de calidad

### <a name="lighting-settings"></a>Configuración de iluminación

Al igual que la configuración de la escena de calidad, es importante establecer la configuración óptima de iluminación de la aplicación de realidad mixta. En Unity, la opción de iluminación que normalmente, tendrá el mayor impacto de rendimiento en su escena es **iluminación Global en tiempo real**. Esto se puede desactivar yendo **ventana** > **representación** > **iluminación configuración** > **en tiempo real Iluminación global**. 

Hay otra configuración de iluminación, **incorporada iluminación Global**. Esta configuración puede proporcionar un rendimiento y resultados visualmente sorprendente en inmersivos, pero generalmente no es aplicable para el desarrollo de HoloLens. **Incorporada Illumniation Global** solo se calcula para GameObjects estático que generalmente no se encuentran en segundo plano de HoloLens debido a la naturaleza de un entorno cambiante y desconocida.

Lea [iluminación Global de Unity](https://docs.unity3d.com/Manual/GIIntro.html) para obtener más información. 

>[!NOTE]
> **En tiempo real de iluminación Global** se establece **por escena** y, por tanto, los desarrolladores deben guardar esta propiedad para cada escena de Unity en su proyecto. 

### <a name="single-pass-instancing-rendering-path"></a>Ruta de representación de creación de instancias de paso único

En las aplicaciones de realidad mixta, la escena se representa dos veces, una vez para cada ojo al usuario. En comparación con el desarrollo tradicional en 3D, este doble eficazmente la cantidad de trabajo que debe calcularse. Por lo tanto, es importante seleccionar la ruta de acceso más eficaz de representación en Unity para guardar tanto en tiempo de CPU y GPU. Representación con instancias de paso único optimiza la canalización de representación de Unity para aplicaciones de realidad mixta y, por tanto, se recomienda habilitar esta configuración predeterminada para todos los proyectos. 

Para habilitar esta característica en el proyecto de Unity
1)  Abra **configuración del Reproductor XR** (vaya a **editar** > **configuración del proyecto** > **Reproductor**  >  **Configuración XR**)
2) Seleccione **pasar una instancia única** desde el **el método de representación estéreo** menú desplegable (**admite la realidad Virtual** casilla debe estar seleccionada)

Lea los artículos siguientes de Unity para obtener más detalles con este enfoque de representación.
- [Cómo maximizar el rendimiento de AR y VR con representación estéreo avanzada](https://blogs.unity3d.com/2017/11/21/how-to-maximize-ar-and-vr-performance-with-advanced-stereo-rendering/)
- [Creación de instancias de un solo paso](https://docs.unity3d.com/Manual/SinglePassInstancing.html) 

>[!NOTE]
> Se produce un problema común con solo pasar una instancia de representación si los desarrolladores ya tienen sombreadores personalizados existentes no escritos para creación de instancias. Después de habilitar esta característica, los desarrolladores que observe algún procesamiento solo GameObjects en un ojo. Esto es porque los sombreadores personalizados asociados no tienen las propiedades adecuadas para la creación de instancias.
>
> Consulte [solo pasar estéreo de representación de HoloLens](https://docs.unity3d.com/Manual/SinglePassStereoRenderingHoloLens.html) desde Unity para abordar este problema

### <a name="enable-depth-buffer-sharing"></a>Habilitar el uso compartido de búfer de profundidad

Para lograr una mayor estabilidad holograma desde la percepción del usuario, se recomienda habilitar el **uso compartido de búfer de profundidad** propiedad en Unity. Al activar esto, Unity compartirán el mapa de profundidad producido por la aplicación con la plataforma Windows Mixed Reality. La plataforma, a continuación, podrá optimizar mejor estabilidad holograma específicamente para su escena cualquier período determinado que se procesa la aplicación.

Para habilitar esta característica en el proyecto de Unity
1) Abra **configuración del Reproductor XR** (vaya a **editar** > **configuración del proyecto** > **Reproductor**  >  **Configuración XR**)
2) Seleccione la casilla de verificación **Habilitar uso compartido de búfer de profundidad** en **SDK de realidad Virtual** > **Windows Mixed Reality** expansión (**Virtual Admite la realidad** casilla debe estar seleccionada)

Además, se recomienda seleccionar **profundidad de 16 bits** bajo el **formato profundidad** configuración en este panel, especialmente para el desarrollo de Hololens. Selección de 16 bits en comparación con 24 bits reducirá significativamente los requisitos de ancho de banda ya deberán mover o procesar menos datos.

En orden para la plataforma Windows Mixed Reality optimizar la estabilidad holograma, se basa en el búfer de profundidad sea precisa y coincide con cualquier hologramas representados en la pantalla. Por lo tanto, con el uso compartido en el búfer de profundidad, es importante al representar el color, también representar profundidad. En Unity, mayoría opaco o TransparentCutout materiales representarán en profundidad de forma predeterminada pero transparente y los objetos de texto por lo general no representarán profundidad aunque se trata de sombreador dependiente, etcetera. 

Si utiliza al sombreador Mixed Reality Kit de herramientas estándar, para representar la profundidad de los objetos transparentes:
1) Seleccione el material transparente que está usando al sombreador MRTK estándar y abra la ventana del editor de Inspector
2) Establecer **modo de representación** a **personalizado** , a continuación, establezca **modo** a **transparente** y, por último, establezca **profundidad escribir**a **en**

>[!NOTE]
> Los desarrolladores deben tenga cuidado con luchas Z al cambiar estos valores junto con la configuración de plano de cerca y lejos de la cámara. Luchas Z se produce cuando dos gameobjects intenta procesar al mismo píxel y debido a limitaciones en la fidelidad del búfer de profundidad (como) profundidad de la z), Unity no puede discernir qué objeto está encima del otro. Observarán a los desarrolladores un parpadeo entre dos objetos del juego cuanto *luchar contra* para el mismo valor de profundidad de z. Esto puede solucionarse al cambiar a formato de 24 bits profundidad tal como habrá un mayor intervalo de valores para cada objeto calcular tras su profundidad z de la cámara.
>
> Sin embargo, se recomienda, especialmente para Hololens desarrollo, para modificar la cámara cerca de la y planos mucho a un intervalo más pequeño en su lugar y conserva la profundidad de 16 bits en formato. La profundidad de z no lineales se asigna al intervalo de valores a lo largo de la cámara far y near planos. Esto se puede modificar mediante la selección la *cámara principal* en la escena y, en **Inspector**, cambiar el **plano de recorte cercano & mucho** valores para reducir su intervalo (como) desde 1000 m en 100 m u otro valor x, etcetera.)

### <a name="building-for-il2cpp"></a>Creación de aplicaciones para IL2CPP

Unity desusado soporte técnico para .NET de back-end y, por tanto, se recomienda a los desarrolladores usar scripting **IL2CPP** para su UWP de visual studio compila. Aunque esto aporta varias ventajas, compilar la solución de visual studio desde Unity para **Il2CPP** puede ser significativamente más lento que el método de .NET anterior. Por lo tanto, se recomienda encarecidamente seguir los procedimientos recomendados para la compilación **IL2CPP** para ahorrar en tiempo de iteración de desarrollo.

1) Compilación incremental de sacar provecho mediante la creación de su proyecto en el mismo directorio cada vez, volver a usar los archivos compilados previamente allí
2) Deshabilitar el análisis de software antimalware para su proyecto y carpetas de compilación
   - Abra **protección de Virus y amenazas** en su aplicación de configuración de Windows 10
   - Seleccione **Administrar configuración** en **configuración de protección de Virus y amenazas**
   - Seleccione **exclusiones Add o remove** bajo el **exclusiones** sección
   - Haga clic en **agregue una exclusión** y seleccione la carpeta contiene el código del proyecto Unity y generar salidas
3) Usar una SSD para la compilación

Lea [optimizar tiempos de compilación para IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) para obtener más información.

> [!NOTE]
> Además, puede resultar útil configurar un [servidor de caché](https://docs.unity3d.com/Manual/CacheServer.html), especialmente para los proyectos de Unity con una gran cantidad de activos (sin contar con los archivos de script), o que cambien constantemente de escenas o activos. Al abrir un proyecto, Unity almacena los activos aplicables en un formato de la memoria caché interna en la máquina del desarrollador. Los elementos se tienen que volver a importar y, por tanto, volver a procesar cuando se modifican. Este proceso se puede realizar una vez y guardar en un servidor de caché, de esta forma se comparte con otros desarrolladores, lo que ahorra tiempo al evitar que cada desarrollador tenga que procesar localmente los nuevos cambios que reimporte.

## <a name="publishing-properties"></a>Propiedades de publicación

### <a name="holographic-splash-screen"></a>Pantalla de presentación holográfica

HoloLens tiene una clase de mobile CPU y GPU, lo que significa que las aplicaciones pueden tardar un poco más en cargarse. Mientras se carga la aplicación, los usuarios solo verán negro y, por lo que quizás se pregunte qué está ocurriendo. Para confirmar a ellos durante la carga, que puede agregar una pantalla de presentación holográfica.

Para activar o desactivar la pantalla de presentación holográfica:
1) Vaya a **editar** > **configuración del proyecto** > **Reproductor** página
2) Haga clic en el **Windows Store** pestaña y abra el **imagen presentación** sección
3) Aplicar la imagen deseada en el **Windows Holographic > imagen presentación holográfica** propiedad.
    - Si activa o desactiva el **mostrar la pantalla de presentación de Unity** opción habilitará o deshabilitará la pantalla de presentación con marca de Unity. Si no tiene una licencia de Pro de Unity, siempre se mostrará la pantalla de presentación de la marca de Unity.
    - Si un **Holographic de presentación de imagen** está aplicado, siempre se mostrará, independientemente de si se habilita o deshabilita la casilla de verificación Mostrar la pantalla de presentación de Unity. Especificar una imagen personalizada de presentación holográfica solo está disponible para los desarrolladores con una licencia de Pro de Unity.

|  Mostrar la pantalla de presentación de Unity  |  Imagen de la presentación holográfica  |  Comportamiento |
|----------|----------|----------|
|  Activado  |  Ninguno  |  Mostrar la pantalla de presentación predeterminada Unity durante 5 segundos o hasta que se cargue la aplicación, lo que sea más largo. | 
|  Activado  |  Personalizado  |  Mostrar la pantalla de presentación personalizado durante 5 segundos o hasta que se cargue la aplicación, lo que sea más largo. | 
|  Desactivado  |  Ninguno  |  Mostrar negro transparente (nothing) hasta que se cargue la aplicación. | 
|  Desactivado  |  Personalizado  |  Mostrar la pantalla de presentación personalizado durante 5 segundos o hasta que se cargue la aplicación, lo que sea más largo. | 

Lea [documentación de pantalla de presentación de Unity](https://docs.unity3d.com/Manual/class-PlayerSettingsSplashScreen.html) para obtener más información.

### <a name="tracking-loss"></a>Pérdida de seguimiento

Auriculares de realidad mixta depende de ver el entorno a su alrededor para construir [bloqueado por el mundo de sistemas de coordenadas](coordinate-systems-in-unity.md), que permiten hologramas permanezca en posición. Cuando los auriculares no puede encontrarse en el mundo, se dice que los auriculares tienen *perdido seguimiento*. En estos casos, la funcionalidad dependiente en sistemas de coordenadas bloqueado por el mundo, como fases espaciales, los anclajes espaciales y asignación espacial, no funcionan.

Si se produce una pérdida de seguimiento, comportamiento predeterminado de Unity es hologramas de representación de detener, pausar la [bucle de juego](http://docs.unity3d.com/Manual/ExecutionOrder.html), y mostrar un seguimiento perdido notificación cómodamente que sigue la mirada a los usuarios. También se pueden proporcionar notificaciones personalizadas en el formulario de seguimiento de un imagen de pérdida. Las aplicaciones que dependen de seguimiento de su experiencia completa, es suficiente para dejar que Unity controlarlo completamente hasta que se ha recuperado el seguimiento. Los programadores pueden suministrar una imagen personalizada que se mostrará durante el seguimiento de la pérdida. 

Para personalizar la imagen de pérdida de seguimiento:
1) Vaya a **editar** > **configuración del proyecto** > **Reproductor** página
2) Haga clic en el **Windows Store** pestaña y abra el **imagen presentación** sección
3) Aplicar la imagen deseada en el **Windows Holographic > seguimiento pérdida imagen** propiedad.

#### <a name="opt-out-of-automatic-pause"></a>Desactivación de pausa automática

Es posible que algunas aplicaciones no requieren seguimiento (por ejemplo, [aplicaciones sólo orientación](coordinate-systems-in-unity.md) como visores de vídeo de 360 grados) o que deba continuar sin interrupciones durante el seguimiento del procesamiento se pierde. En estos casos, las aplicaciones pueden rechazar la pérdida de valor predeterminado de seguimiento del comportamiento. Los desarrolladores que elija esta opción son responsables de ocultar y deshabilitar todos los objetos que no se presenten correctamente en un escenario de pérdida de seguimiento. En la mayoría de los casos, el único contenido que se recomienda que se puede representar en que el caso está bloqueado por el cuerpo de contenido, se centra en torno a la cámara principal.

Para dejar de participar en el comportamiento de pausa automática:
1) Vaya a **editar** > **configuración del proyecto** > **Reproductor** página
2) Haga clic en el **Windows Store** pestaña y abra el **imagen presentación** sección
3) Modificar el **Windows Holographic > en pérdida de pausa de seguimiento y mostrar imagen** casilla de verificación.

#### <a name="tracking-loss-events"></a>Seguimiento de eventos de pérdida

Para definir el comportamiento personalizado cuando el seguimiento se pierde, controlar global [seguimiento de eventos de pérdida](tracking-loss-in-unity.md).

### <a name="capabilities"></a>Funcionalidades

Para que una aplicación aprovechar las ventajas de cierta funcionalidad, deben declarar las capacidades adecuadas en su manifiesto. Las declaraciones del manifiesto se pueden realizar en Unity, por lo que se incluyen en cada exportación proyecto posterior. 

Las capacidades se pueden habilitar para una aplicación de realidad mixta:
1) Vaya a **editar** > **configuración del proyecto** > **Reproductor** página
2) Haga clic en el **Windows Store** pestaña y abra el **configuración de publicación** sección y busque el **capacidades** lista

Las capacidades para habilitar las API utilizadas para las aplicaciones holográficas aplicables son:
<br>

|  Capacidad  |  API que requieren la capacidad |
|----------|----------|
|  SpatialPerception  |  SurfaceObserver | 
|  WebCam  |  PhotoCapture y VideoCapture | 
|  PicturesLibrary o VideosLibrary  |  PhotoCapture o VideoCapture, respectivamente (al almacenar el contenido capturado) | 
|  Micrófono  |  VideoCapture (cuando la captura de audio), DictationRecognizer, GrammarRecognizer y KeywordRecognizer | 
|  InternetClient  |  DictationRecognizer (y utilizar el Profiler de Unity) | 

## <a name="see-also"></a>Vea también
* [Introducción al desarrollo de Unity](unity-development-overview.md)
* [Análisis de rendimiento de la realidad mixta](understanding-performance-for-mixed-reality.md)
* [Recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md)
