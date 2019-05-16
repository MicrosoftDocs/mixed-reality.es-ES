---
title: Preparación de la aplicación para HoloLens 2
description: Dirigido a desarrolladores que tienen una aplicación existente en HoloLens (gen 1) o anterior MRTK y busca en el puerto a MRTK versión 2 y 2 de HoloLens.
author: grbury
ms.author: grbury
ms.date: 04/12/19
ms.topic: article
ms.localizationpriority: high
keywords: Windows Mixed Reality, probar, MRTK, MRTK versión 2, 2 de HoloLens
ms.openlocfilehash: 98fde1a597bcc20b14037176748258d35ef99ab9
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730867"
---
# <a name="getting-your-existing-app-ready-for-hololens-2"></a>Preparación de la aplicación existente para HoloLens 2

Esta guía está diseñada específicamente para ayudar a los desarrolladores que tienen una aplicación existente de Unity para HoloLens (gen 1) para portar su aplicación para el nuevo dispositivo HoloLens 2. Hay cuatro pasos principales para migrar un HoloLens (gen 1) la aplicación de Unity a HoloLens 2. Las siguientes secciones detallan la información para cada fase. 

| Paso 1 | Paso 2 | Paso 3 | Paso 4 |
|----------|-------------------|-------------------|-------------------|
| ![Logotipo de Visual Studio](images/visualstudio_logo.png) | ![Logotipo de Unity](images/unity_logo.png)| ![Icono de Unity](images/hololens2_icon.jpg) | ![Logotipo MRTK](images/MRTKIcon.jpg) |
| Descargue herramientas más recientes | Actualizar proyecto de Unity | Compilar para ARM | Migrar a MRTK v2

Es **recomienda** que, antes de comenzar el proceso de portabilidad, los desarrolladores usar control de código fuente para guardar una instantánea del estado original de su aplicación. Además, se recomienda *guardar* Estados de punto de comprobación en varios puntos durante el proceso. También puede ser muy útil tener otra instancia de Unity de la aplicación original para permitir la comparación en paralelo durante el proceso de puerto. 

> [!NOTE]
> Antes de migrar, asegúrese de que tiene las últimas herramientas instaladas para el desarrollo de Windows Mixed Reality. Para los desarrolladores del HoloLens, esto implicará principalmente actualizando a la más reciente de Visual Studio 2017 e instalar el SDK de Windows adecuado. El contenido siguiente profundiza más en diferentes versiones de Unity y la versión 2 de Kit de herramientas de realidad mixta.
>
> Para obtener más información, consulte [instalar las herramientas de](install-the-tools.md).

## <a name="migrate-project-to-latest-version-of-unity"></a>Migrar el proyecto a la versión más reciente de Unity

Si usa la versión 2 MRTK, Unity 2018 LTS será la ruta de acceso de soporte técnico a largo plazo con ningún cambio importante en Unity o en MRTK.  La compilación de Unity recomendada, por el anterior "instalar las herramientas" es 2018.3 de Unity, que se convertirá en la versión LTS de 2018 de Unity.  Además, el v2 MRTK se siempre garantiza la compatibilidad con Unity 2018 LTS pero no necesariamente garantizar la compatibilidad con cada iteración de Unity 2019.x. 

Para ayudar a aclarar las diferencias adicionales entre Unity 2018.3.x o Unity 2019.1.x siguiente se describen las ventajas y desventajas entre estas dos versiones, con la principal diferencia de importancia que se va a la capacidad de compilar para ARM64 en Unity 2019. 

Los desarrolladores deben evaluar cualquier [las dependencias de complemento](https://docs.unity3d.com/Manual/Plugins.html) que existen actualmente en su proyecto y si estos archivos DLL pueden compilarse para ARM64. Si no se puede generar un complemento de dependencia fuerte para ARM64, uno tendrá que usar Unity 2018 LTS.


| Unity 2018.3.x | Unity 2019.1 + |
|----------|-------------------|
| Compatibilidad de generación de ARM32 | Soporte técnico de compilación de ARM32 y ARM64 |
| Versión de compilación de LTS estables | Estabilidad beta |
| [Secuencias de comandos de .NET de back-end](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) *en desuso* | [Secuencias de comandos de .NET de back-end](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) *quitado* |
| Redes UNET *en desuso* | Redes UNET *quitado* |

## <a name="update-sceneproject-settings-in-unity"></a>Actualizar la configuración de la escena o proyecto de Unity

Después de actualizar a Unity 2018.3.x o Unity 2019 +, se recomienda actualizar la configuración concreta en Unity para obtener resultados óptimos en el dispositivo. Estas opciones se describen en detalle en  **[configuración recomendada para Unity](Recommended-settings-for-Unity.md)**.

Se debe volver a repetidos que la [back-end .NET Scripting](https://docs.unity3d.com/Manual/windowsstore-dotnet.html) está en desuso en Unity 2018 y *quitado* en Unity 2019 y por lo tanto, los desarrolladores considerar seriamente cambiando su proyecto a [ IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html). 

> [!NOTE]
> Scripting back-end IL2CPP puede provocar tiempos de compilación de Unity a Visual Studio y, por tanto, los desarrolladores deben configurar su máquina de desarrollador para [optimizar los tiempos de compilación IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html).

Tras solucionar los cambios de última hora después de mover a la versión actualizada de Unity, los desarrolladores deben compilar y probar sus aplicaciones actuales en HoloLens (gen 1). Además, esto es un buen punto para crear y guardar una confirmación para el control de código fuente. 

## <a name="compile-dependenciesplugins-for-arm-processor"></a>Compile las dependencias/complementos para procesadores ARM

HoloLens (gen 1) ejecuta aplicaciones en un x86 procesador mientras el nuevo dispositivo HoloLens 2 usa un procesador ARM. Por lo tanto, las aplicaciones existentes deben ser transferido para admitir ARM. Como se indicó anteriormente, Unity 2018 admite la compilación para las aplicaciones de ARM32 mientras Unity 2019 + admite la compilación para las aplicaciones ARM64. Desarrollo para aplicaciones ARM64 normalmente es preferible porque no hay una diferencia de material en el rendimiento. Sin embargo, esto requiere que todos [las dependencias de complemento](https://docs.unity3d.com/Manual/Plugins.html) también van a compilar en ARM64. 

Revise todas las dependencias DLL en la aplicación actualmente. Si ya no se necesita una dependencia, es aconsejable quitarlo del proyecto. Para los complementos restantes que son necesarios, introducir los respectivos archivos binarios de ARM32 o ARM64 en su proyecto de Unity. 

Tras la ingesta de los archivos DLL pertinentes, crear una solución de Visual Studio desde Unity y, a continuación, compile un AppX de ARM en Visual Studio para probar que la aplicación se puede compilar para procesadores ARM. Este otro punto donde se recomienda guardar una confirmación de la solución de control de código fuente. 

## <a name="update-to-mrtk-version-2"></a>Actualizar a MRTK versión 2

MRTK versión 2 es el nuevo kit de herramientas encima de Unity que admiten ambos HoloLens (gen 1) y 2 de HoloLens, y donde todas las nuevas capacidades de HoloLens 2 se han agregado, como entregar las interacciones y seguimiento de la vista.

### <a name="prepare-for-the-migration"></a>Preparar la migración

Antes de introducir el nuevo [*.unitypackage archivos para la versión 2 MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases), se recomienda realizar un inventario de **(1) ningún código personalizada que se integra con MRTK v1** y **(2) cualquier código personalizada para las interacciones de entrada o componentes de la experiencia de usuario**. Conflicto más comunes y frecuente para un desarrollador de realidad mixta ingerir el nuevo v2 MRTK implicará la entrada e interacciones. Por lo tanto, se recomienda comenzar la lectura y comprensión del [modelo de entrada de v2 MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html).

Por último, la nueva versión de MRTK 2 ha pasado desde un modelo de objetos de administrador en la escena y scripts para una configuración y la arquitectura de proveedor de servicios. Esto da como resultado un modelo de arquitectura y la jerarquía escena más limpio, pero requiere una curva de aprendizaje para comprender los nuevos perfiles de configuración. Por lo tanto, lea el [Guía de configuración de Kit de herramientas de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) para comenzar a familiarizarse con los perfiles y opciones importantes para ajustar a las necesidades de su aplicación. 

### <a name="perform-the-migration"></a>Realizar la migración

Después de importar MRTK v2, el proyecto de Unity probablemente tendrá muchos errores relacionados con el compilador. Se trata con más frecuencia debido a la nueva estructura de espacio de nombres y los nuevos nombres de componente. Continúe para resolver estos errores mediante la modificación de los scripts para los nuevos espacios de nombres y componentes. 

Para obtener más información sobre las diferencias de API específicas entre HTK/MRTK y MRTK versión 2, consulte la Guía de migración en el [MRTK versión 2 wiki](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html).

### <a name="best-practices"></a>Procedimiento recomendado

- Prefiera usar el sombreador MRTK estándar
- Trabajo en una importante cambiar el tipo a la vez (p. ej.: IFocusable a IMixedRealityFocusHandler)
- Después de cada cambio de prueba y utilizar el control de código fuente
- Usar predeterminada MRTK UX (botones, pizarras, etcetera) cuando sea posible
- Intenta evitar modificar archivos MRTK directamente, en su lugar, crear contenedores en torno a los componentes MRTK
    - Esto protegerá contra futuros ingestions MRTK y actualizaciones
- Revise y exploración de segundo plano de ejemplo proporcionado en MRTK (especialmente *HandInteractionExamples.scene*)
- Volver a generar la interfaz de usuario basada en lienzo con cuadrantes, colisionadores y TextMeshPro texto en su lugar

### <a name="testing-your-application"></a>Probar la aplicación

Ahora que están disponibles en la versión 2, MRTK componentes 2 de HoloLens y capacidades de [RC1](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases/tag/v2.0.0-RC1), puede simular las interacciones de mano directamente en Unity y desarrollar con las nuevas API para las interacciones de mano y seguimiento de los ojos.  El dispositivo HoloLens 2 es necesario para crear una gran experiencia, pero al menos uno podría comenzar el aprendizaje en las herramientas y documentación. Además, MRTK v2 admite el desarrollo en HoloLens (gen 1) y por lo tanto, los modelos de entrada tradicionales, como select a través de pulsar en el aire todavía se puede probar en HoloLens (gen 1) los dispositivos. 

## <a name="updating-interaction-model-for-hololens-2"></a>Actualizar el modelo de interacción para HoloLens 2

Una vez que la aplicación portar y esté preparado para HoloLens 2, está listo para considerar la actualización de la interacción modelo y holograma diseños o la ubicación.
Procedentes de HoloLens (gen 1), probablemente su aplicación tiene un modelo de interacción mirada y confirmación, con hologramas relativamente lejos para caber en el campo de visión.

Pasos para actualizar el diseño de su aplicación sea más adecuado para HoloLens 2:
1.  Componentes MRTK: Por el trabajo previo, si agrega MRTK v2, hay varios componentes/secuencias de comandos para aprovechar que se han diseñado y optimizado para HoloLens 2.

2.  Modelo de interacción: Considere la posibilidad de actualizar el modelo de interacción.  Para la mayoría de los escenarios, se recomienda cambiar de mirada y se confirme en las manos.  Con sus hologramas alcanzar normalmente está fuera de brazos, cambiar a manos se con rayos señalador lejano interacción y captar los gestos.
Nota: hay escenarios donde es necesario, como un trabajo de tarea que contiene las herramientas de un modelo de interacción de manos libres y hay una guía de diseño específicas para estos casos. 

3.  Selección de ubicación holograma: Después de cambiar a un modelo de interacción de manos, considere mover algunos hologramas más cercanos para interactuar directamente con el hologramas con las manos, con cerca de los gestos de agarre de interacción.  Los tipos de hologramas recomendadas acercarse a captar directamente o interactuar son hologramas más pequeños que caben dentro de 2 HoloLens campo de visión al tomar e inspeccionando el holograma, botones, controles y menús de destino pequeños.
<br>
Cada aplicación y el escenario son diferente, y vamos a seguir refinar y exponer instrucciones según los comentarios y continuaron aprendizajes de diseño.


## <a name="additional-learnings-from-moving-apps-from-x86-to-arm"></a>Aprendizajes adicionales de traslado de aplicaciones de x86 a ARM

- Las aplicaciones de Unity rectas son simples como puede generar un paquete appx ARM o implementar directamente en el dispositivo y se ejecuta.
El desafío se genera cuando la aplicación de Unity usa complementos nativo.  Todos los complementos nativos deben actualizar a VS2017 y vuelve a generar para ARM y con Unity 2019, ARM64.

- Una aplicación usa el complemento AudioKinetic Wwise para Unity y la versión usada no tenía un complemento de ARM de UWP. Se tardaron varios días para volver a trabajar el sonido en la aplicación para que funcione en ARM.

- En otros casos, un complemento UWP/ARM no exista para complementos requeridos por la aplicación, bloqueando la capacidad de puerto y ejecutar en HoloLens 2.  Puede ser necesaria la interacción con el proveedor del complemento para desbloquear y admitir ARM.

- El minfloat (y variantes, como min16float, minint, etc.) en los sombreadores pueden comportarse de manera diferente en 2 HoloLen que en HoloLens (gen 1). En concreto, estos garantizan que "al menos el especificado se utilizará el número de bits". En las GPU de Nvidia/Intel, se tratan en gran medida sólo de 32 bits. En ARM, realmente se respeta el número de bits especificado. Esto significa que en la práctica, estos números pueden tener menos precisión o rango en HoloLens 2 tenían en HoloLens (gen 1).

- Las instrucciones _asm no parecen funcionar en ARM, lo que significa que cualquier código con instrucciones de _asm tendrá que volver a escribir.

- El conjunto de instrucciones SIMD no se admite en ARM. Esto significa que diferentes encabezados como xmmintrin.h, emmintrin.h, tmmintrin.h y immintrin.h no están disponibles en ARM.

- Ha cambiado el compilador del sombreador en las ejecuciones durante la primera llamada de dibujo después de que el sombreador se ha cargado o algo del sombreador se basa en ARM, no en tiempo de carga de sombreador. El impacto en la velocidad de fotogramas puede ser muy notable, dependiendo de cuántos sombreadores deben compilarse. Esto tiene varias implicaciones para cómo sombreadores deben ser controlado o empaquetado/actualizados diferente en comparación con 2 HoloLens HoloLens (gen 1).

## <a name="see-also"></a>Vea también
* [Introducción a MRTK versión 2](mrtk-getting-started.md)
* [MRTK versión 2 HowTo](https://microsoft.github.io/MixedRealityToolkit-Unity/External/HowTo/README.html)
* [Instalación de las herramientas](install-the-tools.md)
* [Configuración recomendada para Unity](recommended-settings-for-unity.md)
* [Análisis de rendimiento para Mixed Reality](understanding-performance-for-mixed-reality.md)

