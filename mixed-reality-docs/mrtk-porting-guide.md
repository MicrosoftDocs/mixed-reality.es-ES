---
title: Preparar una aplicación existente para HoloLens 2
description: Diseñado para desarrolladores que ya tienen una aplicación en HoloLens (1.ª generación) o una versión anterior de MRTK, y quieren realizar la portabilidad a MRTK versión 2 y HoloLens 2.
author: grbury
ms.author: grbury
ms.date: 10/14/19
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, test, MRTK, MRTK version 2, HoloLens 2
ms.openlocfilehash: e1256cfaf9253a31161a836f75a90c64d17cf093
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438357"
---
# <a name="get-your-existing-app-ready-for-hololens-2"></a>Preparar una aplicación existente para HoloLens 2

Esta guía está diseñada específicamente para ayudar a los desarrolladores que tienen una aplicación existente de Unity para HoloLens (1.ª generación) para realizar la portabilidad de su aplicación al dispositivo HoloLens 2. Hay cuatro pasos clave para portar una aplicación de Unity de HoloLens (1.ª generación) a HoloLens 2. 

En las secciones siguientes se detalla la información de cada fase:

| Paso 1 | Paso 2 | Paso 3 | Paso 4 |
|----------|-------------------|-------------------|-------------------|
| ![Logotipo de Visual Studio](images/visualstudio_logo.png) | ![Logotipo de Unity](images/unity_logo.png)| ![Icono de Unity](images/hololens2_icon.jpg) | ![Logotipo de MRTK](images/MRTKIcon.jpg) |
| Descarga de las herramientas más recientes | Actualización del proyecto de Unity | Compilación para ARM | Migración a versión 2 de MRTK

Requisitos previos:

Es **muy recomendable** que, antes de iniciar el proceso de portabilidad, los desarrolladores usen control de código fuente para guardar una instantánea del estado original de la aplicación. Además, se recomienda *guardar* estados de punto de control en varios puntos durante el proceso. También puede ser muy útil tener otra instancia de Unity de la aplicación original que permita la comparación en paralelo durante el proceso de portabilidad. 

> [!NOTE]
> Antes de realizar la portabilidad, asegúrate de que tienes instaladas las herramientas más recientes para el desarrollo de Windows Mixed Reality. Para la mayoría de los desarrolladores de HoloLens existentes, esto implica principalmente actualizar a la versión más reciente de Visual Studio 2019 e instalar el SDK de Windows adecuado. El contenido siguiente profundiza más en las diferentes versiones de Unity y la versión 2 de Mixed Reality Toolkit (MRTK).
>
> Para más información, consulta [Instalar las herramientas](install-the-tools.md).

## <a name="migrate-project-to-the-latest-version-of-unity"></a>Migración del proyecto a la última versión de Unity

Si usas [MRTK v2](https://github.com/microsoft/MixedRealityToolkit-Unity), [Unity 2018 LTS](https://unity3d.com/unity/qa/lts-releases) será la mejor vía de compatibilidad a largo plazo sin cambios importantes en Unity o en MRTK. Además, la versión 2 de MRTK siempre garantiza la compatibilidad con Unity 2018 LTS, aunque no necesariamente garantiza la compatibilidad con cada iteración de Unity 2019.x. 

Para ayudar a aclarar otras diferencias entre [Unity 2018 LTS](https://unity3d.com/unity/qa/lts-releases) y Unity 2019.x, a continuación, se describen las ventajas e inconvenientes de ambas versiones. La principal diferencia entre ambas es la posibilidad de compilar para ARM64 en Unity 2019. 

Los desarrolladores deben evaluar cualquier [ dependencia de complemento](https://docs.unity3d.com/Manual/Plugins.html) que exista actualmente en su proyecto y determinar si estos archivos DLL pueden compilarse para ARM64. Si no se puede compilar un complemento de dependencia fuerte para ARM64, tienes que usar Unity 2018 LTS.


| Unity 2018 LTS | Unity 2019.x |
|----------|-------------------|
| Compatibilidad con la compilación ARM32 | Compatibilidad con la compilación ARM32 y ARM64 |
| Versión de la compilación LTS estable | Estabilidad beta |
| [Back-end del scripting de .NET](https://docs.unity3d.com/2018.4/Documentation/Manual/windowsstore-dotnet.html) *en desuso* | [Back-end del scripting de .NET](https://docs.unity3d.com/2018.4/Documentation/Manual/windowsstore-dotnet.html) *eliminado* |
| Redes UNET *en desuso* | Redes UNET *en desuso* |

## <a name="update-sceneproject-settings-in-unity"></a>Actualización de la configuración de la escena o proyecto en Unity

Después de actualizar a [Unity 2018 LTS](https://unity3d.com/unity/qa/lts-releases) o Unity 2019 +, se recomienda actualizar valores concretos en Unity para obtener los mejores resultados en el dispositivo. Estos valores se describen en detalle en **[Configuración recomendada para Unity](Recommended-settings-for-Unity.md)** .

Es necesario reiterar que el [back-end de scripting de .NET](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) estará en desuso en Unity 2018 y se habrá *eliminado* en Unity 2019. Es muy recomendable que los desarrolladores consideren la posibilidad de cambiar su proyecto a [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html). 

> [!NOTE]
> El back-end del scripting de IL2CPP puede aumentar los tiempos de compilación de Unity a Visual Studio, y los desarrolladores deben configurar la máquina de desarrollo para [optimizar los tiempos de compilación de IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html).
> También puede resultar útil configurar un [servidor de caché](https://docs.unity3d.com/Manual/CacheServer.html), especialmente para los proyectos de Unity con una gran cantidad de activos (sin contar con los archivos de script), o que cambien constantemente de escenas y activos. Al abrir un proyecto, Unity almacena los activos aplicables en un formato de la memoria caché interna en la máquina del desarrollador. Los elementos se tienen que volver a importar y a procesar cuando se modifican. Este proceso se puede realizar una vez y guardar en un servidor de caché, de esta forma se comparte con otros desarrolladores, lo que ahorra tiempo, en lugar de que cada desarrollador tenga que procesar localmente la reimportación de los nuevos cambios.

Después de solucionar los cambios importantes tras el cambio a la versión actualizada de Unity, los desarrolladores deben compilar y probar sus aplicaciones actuales en HoloLens (1.ª generación). Este es un buen momento para crear y guardar una confirmación en el control de código fuente. 

## <a name="compile-dependenciesplugins-for-arm-processor"></a>Compilación de dependencias/complementos para procesadores ARM

HoloLens (1.ª generación) ejecuta las aplicaciones en un procesador x86, mientras que el dispositivo HoloLens 2 usa un procesador ARM. Por lo tanto, las aplicaciones de HoloLens existentes se tienen que portar para admitir ARM. Como se indicó anteriormente, Unity 2018 LTS admite la compilación para las aplicaciones de ARM32, mientras que Unity 2019.x admite la compilación para las aplicaciones de ARM32 y ARM64. Normalmente es preferible desarrollar para aplicaciones de ARM64 porque hay una diferencia en el rendimiento. Sin embargo, esto requiere que todas [las dependencias de complemento](https://docs.unity3d.com/Manual/Plugins.html) se compilen también para ARM64. 

Revisa todas las dependencias DLL en la aplicación. Es aconsejable quitar cualquier dependencia que ya no sea necesaria del proyecto. Para el resto de complementos que son necesarios, se deben ingerir los respectivos archivos binarios de ARM32 o ARM64 en el proyecto de Unity. 

Tras la ingesta de los archivos DLL pertinentes, crea una solución de Visual Studio desde Unity y, a continuación, compila un AppX para ARM en Visual Studio para probar que la aplicación se puede compilar para procesadores ARM. Se recomienda guardar la aplicación como una confirmación en la solución de control de código fuente.

## <a name="update-to-mrtk-version-2"></a>Actualización a la versión 2 de MRTK

[MRTK versión 2](https://github.com/microsoft/MixedRealityToolkit-Unity) es el nuevo kit de herramientas además de Unity que admite tanto HoloLens (1.ª generación) como HoloLens 2. También es donde se han agregado todas las nuevas funcionalidades de HoloLens 2, como las interacciones de mano y el seguimiento de los ojos.

Lee la documentación siguiente para obtener más información sobre el uso de la versión 2 de MRTK:
- [Página de aterrizaje de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
- [Introducción a MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
- [Manos de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSystem/HandTracking.html)
- [Seguimiento de los ojos de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_Main.html)

### <a name="prepare-for-the-migration"></a>Preparación para la migración

Antes de realizar la ingesta de los nuevos [archivos *.unitypackage para la versión 2 de MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases), se recomienda realizar un inventario de **1) cualquier código personalizado que se integre con la versión 1 de MRTK** y **2) cualquier código personalizado para las interacciones de entrada o componentes de la experiencia de usuario**. El conflicto más común y que se da con más frecuencia para un desarrollador de realidad mixta en relación con la ingesta de la versión 2 de MRTK tiene que ver con las entradas y las interacciones. Se recomienda comenzar con la lectura y comprensión del [modelo de entrada de la versión 2 de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html).

Por último, la nueva [versión 2 de MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity) ha pasado de un modelo de scripts y objetos de administrador en la escena a una arquitectura de configuración y proveedor de servicios. Esto da como resultado un modelo de arquitectura y jerarquía de escena más limpio, pero requiere una curva de aprendizaje para comprender los nuevos perfiles de configuración. Por ello, debes leer [Mixed Reality Toolkit Configuration Guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) (Guía de configuración de Mixed Reality Toolkit) para comenzar a familiarizarte con los perfiles y opciones importantes para ajustar a las necesidades de tu aplicación. 

### <a name="perform-the-migration"></a>Realización de la migración

Después de importar la [versión 2 de MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity), el proyecto de Unity probablemente tenga muchos errores relacionados con el compilador. Generalmente estos errores se deben a la nueva estructura de espacio de nombres y los nuevos nombres de componente. Resuelve estos errores mediante la modificación de los scripts con los nuevos espacios de nombres y componentes. 

Para más información sobre las diferencias de API específicas entre HTK/MRTK y MRTK v2, consulta la guía de migración en la [wiki de la versión 2 de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html).

### <a name="best-practices"></a>Procedimiento recomendado

- Da preferencia al uso del [sombreador MRTK Standard](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html).
- Trabaja en un solo tipo de cambio importante a la vez (por ejemplo: IFocusable a [IMixedRealityFocusHandler](https://microsoft.github.io/MixedRealityToolkit-Unity/api/Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler.html)).
- Haz una prueba después de cada cambio y usa el control de código fuente.
- Usa experiencias de usuario de MRTK predeterminadas (botones, tabletas táctiles, etc.) cuando sea posible.
- Intenta evitar la modificación de los archivos de MRTK directamente; en su lugar, crea contenedores en torno a los componentes de MRTK.
    - Esta acción facilita las futuras ingestas y actualizaciones de MRTK.
- Revisa y explora escenas de ejemplo proporcionadas en MRTK (especialmente *HandInteractionExamples.scene*).
- Vuelve a generar la interfaz de usuario basada en lienzo con cuadrángulos, colisionadores y texto TextMeshPro.
- Habilita el [uso compartido del búfer de profundidad](camera-in-unity.md#sharing-your-depth-buffers-with-windows) o [establece el punto de enfoque](focus-point-in-unity.md); es preferible usar un búfer de profundidad de 16 bits para mejorar el rendimiento. Al representar el color, asegúrate de representar también la profundidad. Por lo general, Unity no escribe la profundidad de objetos GameObject de texto y transparentes. 
- Establece la ruta de representación de instancia de paso único.
- Usa el [perfil de configuración de HoloLens 2 para MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html#hololens-2-profile)

### <a name="testing-your-application"></a>Prueba de la aplicación

En MRTK versión 2, puedes simular las interacciones con las manos directamente en Unity, así como desarrollar con las nuevas API para las interacciones con las manos y el seguimiento de los ojos. El dispositivo HoloLens 2 es necesario para crear una experiencia de usuario satisfactoria. Se recomienda empezar examinando la documentación y las herramientas para mejorar la comprensión. La [versión 2 de MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity) admite el desarrollo en HoloLens (1.ª generación) y los modelos de entrada tradicionales, como la selección mediante pulsación en el aire, se pueden probar en los dispositivos HoloLens (1.ª generación). 

## <a name="updating-your-interaction-model-for-hololens-2"></a>Actualización del modelo de interacción para HoloLens 2

Una vez que la aplicación está portada y preparada para HoloLens 2, ya estás listo para considerar la actualización de las ubicaciones del diseño del holograma y del modelo.
En HoloLens (1ª generación), es muy posible que tu aplicación tenga un modelo de interacción de mirada y confirmación con hologramas relativamente lejanos para encajar en el campo de visión.

Pasos para actualizar el diseño de la aplicación al diseño más adecuado para HoloLens 2:
1.  Componentes de MRTK: por el trabajo previo, si agregas la [versión 2 de MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity), hay varios componentes o scripts para aprovechar que se han diseñado y optimizado para HoloLens 2.

2.  Modelo de interacción: Plantéate la posibilidad de actualizar el modelo de interacción. Para la mayoría de los escenarios, se recomienda cambiar de mirada y confirmación a interacciones con las manos. Con tus hologramas normalmente fuera del alcance de la mano, el cambio a las entradas de interacción con las manos produce gestos de agarre y haces apuntadores de interacción lejana.

3.  Ubicación de hologramas: después de cambiar a un modelo de interacción con las manos, considera la posibilidad de acercar algunos hologramas para interactuar directamente con ellos, utilizando gestos de agarre de interacción cercana con las manos. Los tipos de hologramas recomendados para el acercamiento que te permita agarrar o interactuar directamente, son los menús de destino pequeños, controles, botones y los hologramas más pequeños que caben dentro del campo de visión de HoloLens 2 al agarrar e inspeccionar el holograma.
<br>
Cada aplicación y escenario son diferentes, y vamos a seguir mejorando y publicando instrucciones para el diseño basadas en comentarios y en lo que vamos aprendiendo cada día.


## <a name="additional-caveats-and-learnings-about-moving-applications-from-x86-to-arm"></a>Advertencias y aprendizajes adicionales sobre cómo mover aplicaciones de x86 a ARM

- Las aplicaciones directas de Unity son sencillas porque puedes compilar un paquete de aplicaciones de ARM o realizar la implementación directamente en el dispositivo para que se ejecute la agrupación. Algunos complementos nativos de Unity pueden presentar ciertos desafíos de desarrollo. Por este motivo, debes actualizar todos los complementos nativos de Unity a Visual Studio 2019 y, a continuación, volver a generarlos para ARM.

- Una aplicación usó el complemento AudioKinetic Wwise de Unity y esa versión de Unity no tenía un complemento de ARM para UWP, lo que exigió un esfuerzo considerable para volver a crear las funcionalidades de sonido en la aplicación en cuestión para su ejecución en ARM. Asegúrate de que todos los complementos necesarios para tus planes de desarrollo están instalados y disponibles en Unity.

- En algunos casos, puede que no exista un complemento de UWP/ARM para los complementos necesarios para la aplicación, lo que bloquea la capacidad de portar la aplicación y ejecutarla en HoloLens 2. Ponte en contacto con tu proveedor de complementos para resolver el problema y obtener compatibilidad con ARM.

- El comando minfloat (y sus variantes, como min16float, minint, etc.) puede comportarse en los sombreadores de manera diferente en HoloLens 2 a como lo hacía en HoloLens (1.ª generación). En concreto, estos garantizan que se utilizará al menos el número especificado de bits. En las GPU de Nvidia/Intel, se tratan generalmente como de 32 bits. En ARM, el número de bits especificado se respeta. En la práctica, esto significa que estos números pueden tener menos precisión o rango en HoloLens 2 del que tenían en HoloLens (1.ª generación).

- Las instrucciones _asm no parecen funcionar en ARM, lo que significa que cualquier código con instrucciones _asm tiene que volverse a escribir.

- La instrucción SIMD establecida no se admite en ARM porque diferentes encabezados, como xmmintrin.h, emmintrin.h, tmmintrin.h e immintrin.h, no están disponibles en ARM.

- El compilador del sombreador en ARM se ejecuta durante la primera llamada draw, después de que el sombreador se haya cargado, o algo en lo que se basa sombreador haya cambiado, no en el tiempo de carga de sombreador. El impacto en la velocidad de fotogramas puede ser muy notable, dependiendo de cuántos sombreadores tengan que compilarse. Esto cambia la forma de controlar, empaquetar o actualizar los sombreadores en HoloLens 2 en comparación con HoloLens (1.ª generación).

## <a name="see-also"></a>Consulte también
* [Instalación de las herramientas](install-the-tools.md)
* [Introducción a MRTK v2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [API de HTK para las API de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
* [Configuración recomendada para Unity](recommended-settings-for-unity.md)
* [Análisis de rendimiento de la realidad mixta](understanding-performance-for-mixed-reality.md)

