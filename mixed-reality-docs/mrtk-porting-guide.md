---
title: Preparación de una aplicación para HoloLens 2
description: Dirigido a desarrolladores que ya tienen una aplicación en HoloLens (1ª generación) o una versión anterior de MRTK, y quieren realizar la portabilidad a la versión 2 de MRTK y HoloLens 2.
author: grbury
ms.author: grbury
ms.date: 04/12/19
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, test, MRTK, MRTK version 2, HoloLens 2
ms.openlocfilehash: 02dabd21b7a6add2ce53fe291a447e49057184d0
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "66270393"
---
# <a name="getting-your-existing-app-ready-for-hololens-2"></a>Preparación de una aplicación existente para HoloLens 2

Esta guía está diseñada específicamente para ayudar a los desarrolladores que tienen una aplicación existente de Unity para HoloLens (1ª generación) para realizar la portabilidad de su aplicación al nuevo dispositivo HoloLens 2. Hay cuatro pasos claves para portar una aplicación Unity de HoloLens (1ª generación) a HoloLens 2. Las secciones a continuación detallan la información para cada fase. 

| Paso 1 | Paso 2 | Paso 3 | Paso 4 |
|----------|-------------------|-------------------|-------------------|
| ![Logotipo de Visual Studio](images/visualstudio_logo.png) | ![Logotipo de Unity](images/unity_logo.png)| ![Icono de Unity](images/hololens2_icon.jpg) | ![Logotipo de MRTK](images/MRTKIcon.jpg) |
| Descarga de las herramientas más recientes | Actualización del proyecto de Unity | Compilación para ARM | Migración a versión 2 de MRTK

Es **muy recomendable** que, antes de iniciar el proceso de portabilidad, los desarrolladores usen control de código fuente para guardar una instantánea del estado original de la aplicación. Además, se recomienda *guardar* estados de punto de control en varios puntos durante el proceso. También puede ser muy útil tener otra instancia de Unity de la aplicación original que permita la comparación en paralelo durante el proceso de portabilidad. 

> [!NOTE]
> Antes de realizar la portabilidad, asegúrate de que tienes instaladas las herramientas más recientes para el desarrollo de Windows Mixed Reality. Para la mayoría de los desarrolladores de una instancia ya existente de HoloLens, esto implica principalmente actualizar a la versión más reciente de Visual Studio 2017 e instalar el SDK de Windows adecuado. El contenido siguiente profundiza más en las diferentes versiones de Unity y la versión 2 de Mixed Reality Toolkit.
>
> Para más información, consulta [Instalar las herramientas](install-the-tools.md).

## <a name="migrate-project-to-latest-version-of-unity"></a>Migración del proyecto a la última versión de Unity

Si usas la versión 2 de MRTK, Unity 2018 LTS será la mejor vía de compatibilidad a largo plazo sin cambios importantes en Unity o en MRTK.  La compilación de Unity recomendada en la referencia "Instalar las herramientas" citada anteriormente es Unity 2018.3, que será la versión LTS para Unity 2018.  Además, la versión 2 de MRTK siempre garantiza la compatibilidad con Unity 2018 LTS, aunque no necesariamente garantiza la compatibilidad con cada iteración de Unity 2019.x. 

Para ayudar a aclarar las diferencias adicionales entre Unity 2018.3.x o Unity 2019.1.x, a continuación se describen las ventajas y desventajas de estas dos versiones, siendo la principal diferencia de importancia la capacidad de compilar para ARM64 en Unity 2019. 

Los desarrolladores deben evaluar cualquier [ dependencia de complemento](https://docs.unity3d.com/Manual/Plugins.html) que exista actualmente en su proyecto, y si estos archivos DLL pueden compilarse para ARM64. Si no se puede compilar un complemento de dependencia fuerte para ARM64, uno tendrá que usar Unity 2018 LTS.


| Unity 2018.3.x | Unity 2019.1+ |
|----------|-------------------|
| Compatibilidad con la compilación ARM32 | Compatibilidad con la compilación ARM32 y ARM64 |
| Versión de la compilación LTS estable | Estabilidad beta |
| [Back-end del scripting de .NET](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) *en desuso* | [Back-end del scripting de .NET](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) *eliminado* |
| Redes UNET *en desuso* | Redes UNET *eliminadas* |

## <a name="update-sceneproject-settings-in-unity"></a>Actualización de la configuración de la escena o proyecto en Unity

Después de actualizar a Unity 2018.3.x o Unity 2019 +, se recomienda actualizar valores concretos en Unity para obtener los mejores resultados en el dispositivo. Estos valores se describen en detalle en **[Configuración recomendada para Unity](Recommended-settings-for-Unity.md)** .

Es necesario reiterar que el [back-end del scripting de .NET](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) está en desuso en Unity 2018 y se ha *eliminado* en Unity 2019, por lo tanto, los desarrolladores deberían considerar seriamente cambiar su proyecto a [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html). 

> [!NOTE]
> El back-end del scripting de IL2CPP puede aumentar los tiempos de compilación de Unity a Visual Studio y, por ello, los desarrolladores deben configurar las máquina de desarrollador para [optimizar los tiempos de compilación de IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html).
> Además, puede resultar útil configurar un [servidor de caché](https://docs.unity3d.com/Manual/CacheServer.html), especialmente para los proyectos de Unity con una gran cantidad de activos (sin contar con los archivos de script), o que cambien constantemente de escenas o activos. Al abrir un proyecto, Unity almacena los activos aplicables en un formato de la memoria caché interna en la máquina del desarrollador. Los elementos se tienen que volver a importar y, por tanto, volver a procesar cuando se modifican. Este proceso se puede realizar una vez y guardar en un servidor de caché, de esta forma se comparte con otros desarrolladores, lo que ahorra tiempo al evitar que cada desarrollador tenga que procesar localmente los nuevos cambios que reimporte.

Después de solucionar cualquier cambio importante tras el cambio a la versión actualizada de Unity, los desarrolladores deben compilar y probar sus aplicaciones actuales en HoloLens (1ª generación). Además, este es un buen momento para crear y guardar una confirmación para el control de código fuente. 

## <a name="compile-dependenciesplugins-for-arm-processor"></a>Compilación de dependencias/complementos para procesadores ARM

HoloLens (1ª generación) ejecutaba las aplicaciones en un procesador x86, mientras que el nuevo dispositivo HoloLens 2 usa un procesador ARM. Por lo tanto, las aplicaciones existentes se tienen que migrar para admitir ARM. Como se indicó anteriormente, Unity 2018 admite la compilación para las aplicaciones de ARM32, mientras Unity 2019 + admite la compilación para las aplicaciones de ARM64. Normalmente es preferible desarrollar para aplicaciones de ARM64 porque hay una diferencia en el rendimiento. Sin embargo, esto requiere que todas [las dependencias de complemento](https://docs.unity3d.com/Manual/Plugins.html) se compilen también para ARM64. 

Revisa todas las dependencias DLL actuales en la aplicación. Si ya no se necesita una dependencia, es aconsejable quitarla del proyecto. Para el resto de complementos que son necesarios, se deben ingerir los respectivos archivos binarios de ARM32 o ARM64 en el proyecto de Unity. 

Tras la ingesta de los archivos DLL pertinentes, crea una solución de Visual Studio desde Unity y, a continuación, compila un AppX para ARM en Visual Studio para probar que la aplicación se puede compilar para procesadores ARM. Este es otro punto en el que se recomienda guardar una confirmación en la solución de control de código fuente. 

## <a name="update-to-mrtk-version-2"></a>Actualización a la versión 2 de MRTK

La versión 2 de MRTK es el nuevo kit de herramientas a partir de Unity que admite tanto HoloLens (1ª generación) como HoloLens 2, y en el que se han agregado todas las nuevas funcionalidades de HoloLens 2, como interacciones con las manos y el seguimiento de los ojos.

### <a name="prepare-for-the-migration"></a>Preparación para la migración

Antes de realizar la ingesta de los nuevos [archivos *.unitypackage para la versión 2 de MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases), se recomienda realizar un inventario de **1) cualquier código personalizado que se integre con la versión 1 de MRTK** y **2) cualquier código personalizado para las interacciones de entrada o componentes de la experiencia de usuario**. Los conflictos más comunes y que aparecen con más frecuencia para un desarrollador de Mixed Reality realizando la ingesta de la nueva versión 2 de MRTK, tiene que ver con entradas e interacciones. Por lo tanto, se recomienda comenzar con la lectura y comprensión del [modelo de entrada de la versión 2 de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html).

Por último, la nueva versión 2 de MRTK ha pasado desde un modelo de scripts y objetos de administrador en la escena, a una arquitectura de configuración y proveedor de servicios. Esto da como resultado un modelo de arquitectura y jerarquía de escena más limpio, pero requiere una curva de aprendizaje para comprender los nuevos perfiles de configuración. Por ello, debes leer [Mixed Reality Toolkit Configuration Guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) (Guía de configuración de Mixed Reality Toolkit) para comenzar a familiarizarte con los perfiles y opciones importantes para ajustar a las necesidades de tu aplicación. 

### <a name="perform-the-migration"></a>Realización de la migración

Después de importar la versión 2 de MRTK, el proyecto de Unity probablemente tendrá muchos errores relacionados con el compilador. Generalmente estos errores se deben a la nueva estructura de espacio de nombres y los nuevos nombres de componente. Resuelve estos errores mediante la modificación de los scripts con los nuevos espacios de nombres y componentes. 

Para más información sobre las diferencias de API específicas entre HTK/MRTK y la versión 2 de MRTK, consulta la guía de migración en la [wiki de la versión 2 de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html).

### <a name="best-practices"></a>Procedimiento recomendado

- Da preferencia al uso del sombreador MRTK Standard.
- Trabaja en un solo tipo de cambio importante a la vez (por ejemplo: IFocusable a IMixedRealityFocusHandler).
- Haz una prueba después de cada cambio y usa el control de código fuente.
- Usa experiencias del usuario de MRTK predeterminadas (botones, tabletas táctiles, etc.) cuando sea posible.
- Intenta evitar la modificación de los archivos de MRTK directamente, en su lugar, crea contenedores en torno a los componentes de MRTK.
    - Esto actuará de protección contra futuras ingestas y actualizaciones de MRTK.
- Revisa y explora escenas de ejemplo proporcionadas en MRTK (especialmente *HandInteractionExamples.scene*).
- Vuelve a generar la interfaz de usuario basada en lienzo con cuadrángulos, colisionadores y texto TextMeshPro en su lugar.

### <a name="testing-your-application"></a>Prueba de la aplicación

Ahora que ya están disponibles los componentes y funcionalidades de HoloLens 2 en la versión 2 de MRTK, a partir de [RC1](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/tag/v2.0.0-RC1), puedes simular las interacciones con las manos directamente en Unity, y desarrollar con las nuevas API para las interacciones con las manos y el seguimiento de los ojos.  El dispositivo HoloLens 2 es necesario para crear una gran experiencia, pero al menos uno debe empezar el aprendizaje en las herramientas y la documentación. Además, la versión 2 de MRTK admite el desarrollo en HoloLens (1ª generación) y por lo tanto, los modelos de entrada tradicionales, como la selección mediante pulsación en el aire, todavía se puede probar en los dispositivos HoloLens (1ª generación). 

## <a name="updating-interaction-model-for-hololens-2"></a>Actualización del modelo de interacción para HoloLens 2

Una vez que la aplicación está migrada y preparada para HoloLens 2, ya estás listo para considerar la actualización del modelo de interacción y los diseños o ubicación del holograma.
Viniendo de HoloLens (1ª generación), es muy posible que tu aplicación tenga un modelo de interacción de mirada y confirmación, con hologramas relativamente lejanos parar encajar en el campo de visión.

Pasos para actualizar el diseño de la aplicación al diseño más adecuado para HoloLens 2:
1.  Componentes de MRTK: Por el trabajo previo, si agregas la versión 2 de MRTK, hay varios componentes o scripts para aprovechar que se han diseñado y optimizado para HoloLens 2.

2.  Modelo de interacción: Plantéate la posibilidad de actualizar el modelo de interacción.  Para la mayoría de los escenarios, se recomienda cambiar de mirada y confirmación a interacciones con las manos.  Como tus hologramas normalmente estarán fuera del alcance de la mano, el cambio a las entradas de interacción con las manos dará como resultado gestos de agarre y rayos apuntadores de interacción lejana.
Nota: Hay escenarios donde es necesario un modelo de interacción de manos libres, como un trabajador de tarea que sujeta las herramientas, para estos casos existe una guía de diseño específica. 

3.  Ubicación de hologramas: Después de cambiar a un modelo de interacción con las manos, considera la posibilidad de acercar algunos hologramas para interactuar directamente con las manos en el holograma, utilizando gestos de agarre de interacción cercana.  Los tipos de hologramas recomendados para el acercamiento que te permita agarrar o interactuar directamente, son los menús de destino pequeños, controles, botones y los hologramas más pequeños que caben dentro del campo de visión de HoloLens 2 al agarrar e inspeccionar el holograma.
<br>
Cada aplicación y escenario son diferentes, y vamos a seguir mejorando y publicando instrucciones para el diseño basadas en comentarios e informaciones y en lo que vamos aprendiendo cada día.


## <a name="additional-learnings-from-moving-apps-from-x86-to-arm"></a>Aprendizajes adicionales del traslado de aplicaciones de x86 a ARM

- Las aplicaciones de Unity convencionales son simples, ya que puedes compilar un lote de aplicaciones ARM o implementar directamente en el dispositivo, y se ejecutan.
El desafío aparece cuando la aplicación de Unity usa complementos nativos.  Todos los complementos nativos tienen que actualizarse a VS2017 y regenerarse para ARM y con Unity 2019, ARM64.

- Una aplicación usó el complemento AudioKinetic Wwise para Unity y la versión usada no tenía un complemento de ARM de Plataforma universal de Windows. Se tardaron varios días para encontrar la forma de que el sonido de la aplicación funcionará en ARM.

- En otros casos, puede no haber un complemento UWP/ARM para complementos requeridos por la aplicación, con lo que se bloquea la capacidad de portar y ejecutar en HoloLens 2.  Puede ser necesaria la interacción con el proveedor del complemento para desbloquear y que el complemento admita ARM.

- Minfloat (y sus variantes, como min16float, minint, etc.) puede comportarse en los sombreadores de manera diferente en HoloLen 2 a como lo hacían en HoloLens (1ª generación). En concreto, estos garantizan que "se utilizará al menos el número especificado de bits". En las GPU de Nvidia/Intel, se tratan generalmente como de 32 bits. En ARM, el número de bits especificado se respeta. Esto significa que en la práctica, estos números pueden tener menos precisión o rango en HoloLens 2 del que tenían en HoloLens (1ª generación).

- Las instrucciones _asm no parecen funcionar en ARM, lo que significa que cualquier código con instrucciones _asm tendrá que volverse a escribir.

- El conjunto de instrucciones SIMD no se admite en ARM. Esto significa que diferentes encabezados como xmmintrin.h, emmintrin.h, tmmintrin.h y immintrin.h no están disponibles en ARM.

- El compilador del sombreador en ARM se ejecuta durante la primera llamada draw, después de que el sombreador se haya cargado, o algo en lo que se basa sombreador haya cambiado, no en el tiempo de carga de sombreador. El impacto en la velocidad de fotogramas puede ser muy notable, dependiendo de cuántos sombreadores tengan que compilarse. Esto tiene varias implicaciones en la forma diferente en la que se deben controlar, empaquetar o actualizar los sombreadores en HoloLens 2 en comparación con HoloLens (1ª generación).

## <a name="see-also"></a>Consulte también
* [Introducción a MRTK v2](mrtk-getting-started.md)
* [Procedimientos de la versión 2 de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/External/HowTo/README.html)
* [Instalación de las herramientas](install-the-tools.md)
* [Configuración recomendada para Unity](recommended-settings-for-unity.md)
* [Análisis de rendimiento de la realidad mixta](understanding-performance-for-mixed-reality.md)

