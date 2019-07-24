---
title: Descripción del rendimiento de la realidad mixta
description: Temas avanzados y detalles sobre la optimización del rendimiento de las aplicaciones de Windows Mixed Reality
author: Troy-Ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, rendimiento, optimización, CPU, GPU
ms.openlocfilehash: ce59f9023c21dc7c981a2bb97d9fbd0c57622dbf
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548840"
---
# <a name="understanding-performance-for-mixed-reality"></a>Descripción del rendimiento de la realidad mixta

Este artículo es una introducción a la racionalización de la importancia del rendimiento para la aplicación de realidad mixta.  La experiencia del usuario se puede degradar considerablemente si la aplicación no se ejecuta con una velocidad de fotogramas óptima. Los hologramas aparecerán inestables y el seguimiento de los cabezales del entorno será inexacto, lo que dará lugar a una mala experiencia para el usuario. En realidad, el rendimiento se debe considerar como una característica de primera clase para el desarrollo de la realidad mixta y no para una tarea de finalización del ciclo.

Para la revisión, los valores de velocidad de fotogramas de rendimiento para cada plataforma de destino se enumeran a continuación.

| Plataforma | Velocidad de fotogramas de destino |
|----------|-------------------|
| [HoloLens](hololens-hardware-details.md) | 60 FPS |
| [Windows Mixed Reality ultra PC](immersive-headset-hardware-details.md) | 90 FPS |
| [Equipos con Windows Mixed Reality](immersive-headset-hardware-details.md) | 60 FPS |

En el marco siguiente se proporciona un esquema general de los procedimientos recomendados y se comprenden las velocidades de fotogramas de destino. Para profundizar más en los detalles, considere la posibilidad de leer el [artículo recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md). En concreto, en este artículo relacionado se explica cómo medir las velocidad de fotogramas de la aplicación de Windows Mixed Reality, así como los pasos que se deben llevar a cabo en el entorno de Unity para mejorar el rendimiento.

## <a name="understanding-performance-bottlenecks"></a>Descripción de los cuellos de botella de rendimiento

Si la aplicación tiene una velocidad de fotogramas que realiza un uso intensivo, el primer paso consiste en analizar y comprender en qué medida su aplicación es intensiva. Hay dos procesadores principales responsables del trabajo para representar la escena: la CPU y la GPU. Cada uno de estos dos componentes trata las distintas operaciones y fases de la aplicación de realidad mixta. Hay tres lugares principales en los que se pueden producir cuellos de botella. 

1. **Subproceso de aplicación-CPU** : este subproceso es responsable de la lógica de la aplicación. Esto incluye la entrada de procesamiento, las animaciones, la física y otra lógica o estado de la aplicación.
2. **Render Thread-CPU to GPU** : este subproceso es responsable de enviar las llamadas a Draw a la GPU. Cuando la aplicación desea representar un objeto como un cubo o un modelo, este subproceso envía una solicitud a la GPU, que tiene una arquitectura optimizada para la representación, para realizar estas operaciones.
3. **GPU** - 
    Normalmente, este procesador controla la canalización de gráficos de la aplicación para transformar datos 3D (modelos, texturas, etc.) en píxeles y, en última instancia, generar una imagen 2D para enviarla a la pantalla del dispositivo.

![Duración de un marco](images/lifetime-of-a-frame.png)

Por lo general, las aplicaciones de HoloLens estarán limitadas por GPU. Sin embargo, esto no es cierto en todas las aplicaciones y, por lo tanto, se recomienda usar las herramientas & técnicas siguientes para llegar a la realidad de una aplicación concreta.

## <a name="how-to-analyze-your-application"></a>Cómo analizar la aplicación

Hay muchas herramientas que le permiten como desarrollador comprender el perfil de rendimiento de la aplicación de realidad mixta. Esto le permitirá tener como destino los cuellos de botella y cómo se manifiestan para depurarlos.

Esta es una lista de las herramientas más populares y eficaces para obtener información de generación de perfiles profunda para su aplicación.
- [Analizadores de rendimiento de gráficos Intel](https://software.intel.com/gpa)
- [Depuradores de gráficos de Visual Studio](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [Generador de perfiles de Unity](https://docs.unity3d.com/Manual/Profiler.html)
- [Depurador de fotogramas de Unity](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a>Cómo generar perfiles en cualquier entorno

Hay una prueba sencilla para determinar rápidamente si es probable que el límite de GPU o la CPU estén limitados en la aplicación. Si reduce la resolución de la salida del destino de representación, hay menos píxeles para calcular y, por lo tanto, menos trabajo debe realizar la GPU para representar una imagen. El escalado de la ventanilla (escala de resolución dinámica) es la práctica de representar la imagen en un destino de representación más pequeño y, después, se puede mostrar el dispositivo de salida. El dispositivo se muestra en el conjunto más pequeño de píxeles para mostrar la imagen final.

Después de reducir la resolución de representación, si:
1) La velocidad de fotogramas de aplicación **aumenta**, es probable que la **GPU** esté enlazada
1) Velocidad de la aplicación **sin cambios**, es probable que la **CPU esté limitada**

>[!NOTE]
>Unity proporciona la capacidad de modificar fácilmente la resolución del destino de representación de la aplicación en tiempo de ejecución a través de la propiedad *[XRSettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* . La imagen final presentada en el dispositivo tiene una resolución fija. La plataforma muestreará el resultado de la resolución inferior para crear una imagen de resolución más alta para la representación de las pantallas. 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>Cómo mejorar la aplicación

### <a name="cpu-performance-recommendations"></a>Recomendaciones de rendimiento de CPU

En general, la mayoría del trabajo en una aplicación de realidad mixta en la CPU implica la realización de la "simulación" de la escena y el procesamiento de una lógica de aplicación única. Por lo tanto, las áreas siguientes suelen tener como destino la optimización.

- Animaciones
- Simplificar la física
- Asignaciones de memoria
- Algoritmos complejos (es decir, cinemática inversa, búsqueda de rutas de acceso)

### <a name="gpu-performance-recommendations"></a>Recomendaciones de rendimiento de GPU

#### <a name="understanding-bandwidth-vs-fill-rate"></a>Descripción del ancho de banda y la velocidad de relleno
Al representar un fotograma en la GPU, una aplicación suele estar limitada por el ancho de banda de memoria o la velocidad de relleno.

- El **ancho de banda de memoria** es la velocidad de lecturas y escrituras que la GPU puede realizar desde la memoria
    - Para identificar las limitaciones de ancho de banda, reduzca la calidad de las texturas y compruebe si las velocidad de fotogramas
    - En Unity, esto se puede hacer cambiando la **calidad** de la textura en **Editar** > configuración de **[calidad configuración](https://docs.unity3d.com/Manual/class-QualitySettings.html)** de**proyecto** > .
- La **velocidad de relleno** hace referencia al rendimiento de los píxeles representados que la GPU puede dibujar por segundo.
    - Para identificar las limitaciones de la velocidad de relleno, reduzca la resolución de pantalla y compruebe si se ha mejorado la velocidad de fotogramas. 
    - En Unity, esto se puede hacer a través de la propiedad *[XRSettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)*

Generalmente, el ancho de banda de memoria implica optimizaciones para
1) reducir resoluciones de textura
2) Use menos texturas (es decir, normalización, especular, etc.)

La velocidad de relleno se centra principalmente en reducir el número de operaciones que se deben calcular para un píxel representado final. Algunos ejemplos de esto suelen reducirse
1) número de objetos que se van a representar o procesar
2) número de operaciones por sombreador
3) número de fases de GPU en el resultado final (sombreadores de geometría, efectos de procesamiento posterior, etc.)
4) número de píxeles que se van a representar (es decir, resolución de pantalla)

#### <a name="reduce-poly-count"></a>Reducir el número de poli
Los recuentos de polígonos más altos producen más operaciones para la GPU y la reducción del número de polígonos de la escena reduce la cantidad de tiempo que se tarda en representar esa geometría. También hay otros factores implicados en el sombreado de la geometría que puede seguir siendo caro pero el recuento de polígonos es la métrica base para determinar el costo que se representará una escena.

#### <a name="limit-overdraw"></a>Sobredibujar límite

El sobredibujo alto se produce cuando se representan varios objetos, pero no se emiten en la pantalla, ya que están ocultos por otro objeto, por lo general, más cerca de occluding. Imagine que mira una pared que tenía varios salones y geometría detrás. Todas las geometrías se procesarían para la representación, pero solo el muro opaco realmente debe representarse, ya que occludes la vista de todo el contenido. Esto produce operaciones imprecisas que no son necesarias para la vista actual.

#### <a name="shaders"></a>Sombreadores

Los sombreadores son pequeños programas que se ejecutan en la GPU y, por lo general, determinan dos pasos importantes en la representación:
1) Qué vértices del objeto se deben dibujar en la pantalla y dónde se encuentran en el espacio de pantalla (es decir, sombreador de vértices)
    - El sombreador de vértices se ejecuta generalmente por vértice para cada GameObject
2) cómo colorear esos píxeles (es decir, sombreador de píxeles)
    - El sombreador de píxeles se ejecuta por píxel para la textura que se representa para el dispositivo presente

Normalmente, los sombreadores realizan muchas transformaciones y cálculos de iluminación. Aunque los modelos de iluminación complejos, las sombras y otras operaciones pueden generar resultados fantásticos, también tienen un precio. Reducir el número de operaciones calculadas en los sombreadores puede reducir en gran medida el trabajo general necesario para que lo realice una GPU por fotograma.

##### <a name="shader-coding-recommendations"></a>Recomendaciones de codificación del sombreador

- Usar el filtrado bilineal siempre que sea posible
- Reorganizar expresiones para usar funciones intrínsecas de MAD con el fin de realizar una multiplicación y agregar al mismo tiempo
- Calcular el precálculo tanto como sea posible en la CPU y pasar como constantes al material
- **Favorecer el movimiento de las operaciones desde el sombreador de píxeles hasta el sombreador de vértices**
    - Por lo general, el número de vértices < < número de píxeles (es decir, 720p = = 921.600 píxeles, 1080p = = 2.073.600 píxeles, etc.)

#### <a name="remove-gpu-stages"></a>Quitar fases de GPU
Los efectos posteriores al procesamiento pueden ser muy costosos y, por lo general, impedir la velocidad de relleno de la aplicación. Esto también incluye técnicas de suavizado de contorno como MSAA. En HoloLens, se recomienda evitar estas técnicas por completo. Además, las fases adicionales del sombreador, como la geometría, el casco y los sombreadores de cálculo, deben evitarse cuando sea posible.

## <a name="memory-recommendations"></a>Recomendaciones de memoria
Una asignación excesiva de memoria & operaciones de desasignación puede tener efectos negativos en la aplicación holográfica, lo que produce un rendimiento incoherente, fotogramas inmovilizados y otro comportamiento perjudicial. Es especialmente importante comprender las consideraciones de memoria al desarrollar en Unity, ya que la administración de la memoria se controla mediante el recolector de elementos no utilizados.

#### <a name="object-pooling"></a>Agrupación de objetos

La agrupación de objetos es una técnica popular para reducir el costo de las asignaciones continuas & desasignaciones de objetos. Para ello, se asigna un grupo grande de objetos idénticos y se reutilizan instancias disponibles inactivas de este grupo en lugar de generar y destruir objetos constantemente a lo largo del tiempo. Los grupos de objetos son excelentes para los componentes reutilizables que tienen una duración variable durante una aplicación.

## <a name="see-also"></a>Vea también
- [Recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md)
- [Configuración recomendada para Unity](recommended-settings-for-unity.md)
