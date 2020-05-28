---
title: Descripción del rendimiento de la realidad mixta
description: Temas avanzados y detalles sobre la optimización del rendimiento de las aplicaciones de Windows Mixed Reality
author: troy-ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: Windows Mixed Reality, realidad mixta, realidad virtual, VR, MR, rendimiento, optimización, CPU, GPU
ms.openlocfilehash: 4a0f4cd9caea5dd601ad663801e760261980c429
ms.sourcegitcommit: b0d15083ec1095e08c9d776e5bae66b4449383bb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2020
ms.locfileid: "84111024"
---
# <a name="understanding-performance-for-mixed-reality"></a>Descripción del rendimiento en la realidad mixta

Este artículo es una introducción a la comprensión del significado del rendimiento de la aplicación de realidad mixta.  La experiencia del usuario se puede degradar considerablemente si la aplicación no se ejecuta con una velocidad de fotogramas óptima. Los hologramas aparecerán inestables y el seguimiento de los cabezales del entorno no será preciso, lo que conduce a una mala experiencia para el usuario. El rendimiento se debe considerar como una característica de primera clase para el desarrollo de la realidad mixta y no para una tarea fina.

A continuación se enumeran los valores de velocidad de fotogramas de rendimiento para cada plataforma de destino.

| Plataforma | Velocidad de fotogramas de destino |
|----------|-------------------|
| [HoloLens](hololens-hardware-details.md) | 60 FPS |
| [Windows Mixed Reality ultra PC](immersive-headset-hardware-details.md) | 90 FPS |
| [Equipos con Windows Mixed Reality](immersive-headset-hardware-details.md) | 60 FPS |

En el marco siguiente se describen los procedimientos recomendados para alcanzar las velocidades de fotogramas de destino. Si está desarrollando en Unity, considere la posibilidad de leer el [artículo recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md) para obtener sugerencias sobre cómo medir y mejorar las velocidad de fotogramas en el entorno de Unity.

## <a name="understanding-performance-bottlenecks"></a>Descripción de los cuellos de botella de rendimiento

Si la aplicación tiene una velocidad de fotogramas que realiza un uso intensivo, el primer paso consiste en analizar y comprender en qué medida su aplicación es intensiva. Hay dos procesadores principales responsables del trabajo para representar la escena: la CPU y la GPU. Cada una de estas administra diferentes aspectos de la aplicación de realidad mixta. Existen tres lugares principales en los que se pueden producir cuellos de botella: 

1. **Subproceso de aplicación-CPU** : este subproceso es responsable de la lógica de la aplicación. Esto incluye la entrada de procesamiento, las animaciones, la física y otras lógicas de aplicación.
2. **Render Thread-CPU to GPU** : este subproceso es responsable de enviar las llamadas a Draw a la GPU. Cuando la aplicación desea representar un objeto como un cubo o un modelo, este subproceso envía una solicitud a la GPU para realizar estas operaciones.
3. **GPU** : este procesador normalmente controla la canalización de gráficos de la aplicación para transformar datos 3D (modelos, texturas, etc.) en píxeles. En última instancia, genera una imagen 2D para enviarla a la pantalla del dispositivo.

![Duración de un marco](images/lifetime-of-a-frame.png)

Por lo general, las aplicaciones de HoloLens estarán enlazadas por GPU, pero no siempre. Use las herramientas y técnicas siguientes para entender dónde se encuentra un cuello de botella en la aplicación en particular.

## <a name="how-to-analyze-your-application"></a>Cómo analizar la aplicación

Hay muchas herramientas que le permiten comprender el perfil de rendimiento de la aplicación de realidad mixta. Esto le permitirá encontrar dónde y por qué tiene cuellos de botella, por lo que puede solucionarlos.

A continuación se muestran algunas herramientas comunes para obtener información detallada sobre la generación de perfiles para la aplicación:
- [Analizadores de rendimiento de gráficos Intel](https://software.intel.com/gpa)
- [Depuradores de gráficos de Visual Studio](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [Generador de perfiles de Unity](https://docs.unity3d.com/Manual/Profiler.html)
- [Depurador de fotogramas de Unity](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a>Cómo generar perfiles en cualquier entorno

Una manera de determinar si está enlazada a la GPU o la CPU en la aplicación es reducir la resolución de la salida del destino de representación. Al reducir el número de píxeles que se van a calcular, se reducirá la carga de la GPU. El dispositivo se representará en una textura más pequeña y, luego, se mostrará como ejemplo para mostrar la imagen final.

Después de reducir la resolución de representación, si:
1) La velocidad de fotogramas de aplicación **aumenta**, es probable que esté **enlazada a GPU**
1) Velocidad de la aplicación **inalterada**, es probable que esté **enlazada** a la CPU

>[!NOTE]
>Unity proporciona la capacidad de modificar fácilmente la resolución del destino de representación de la aplicación en tiempo de ejecución a través de la propiedad *[XRSettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* . La imagen final presentada en el dispositivo tiene una resolución fija. La plataforma muestreará el resultado de la resolución inferior para crear una imagen de resolución más alta para la representación de las pantallas. 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>Cómo mejorar la aplicación

### <a name="cpu-performance-recommendations"></a>Recomendaciones de rendimiento de CPU

En general, la mayoría del trabajo en una aplicación de realidad mixta en la CPU implica la realización de la "simulación" de la escena y el procesamiento de la lógica de la aplicación. Las siguientes áreas suelen tener como destino la optimización:

- Animaciones
- Efectos
- Asignaciones de memoria
- Algoritmos complejos (es decir, cinemática inversa, búsqueda de rutas de acceso)

### <a name="gpu-performance-recommendations"></a>Recomendaciones de rendimiento de GPU

#### <a name="understanding-bandwidth-vs-fill-rate"></a>Descripción del ancho de banda y la velocidad de relleno
Al representar un fotograma en la GPU, una aplicación suele estar enlazada por el ancho de banda de memoria o la velocidad de relleno.

- El **ancho de banda de memoria** es la velocidad de lecturas y escrituras que la GPU puede realizar desde la memoria
    - Para identificar las limitaciones de ancho de banda, reduzca la calidad de la textura y compruebe si la velocidad de fotogramas ha mejorado.
    - En Unity, esto se puede hacer cambiando la **calidad** de la textura en **Editar**configuración de  >  **Project Settings**  >  **[calidad configuración](https://docs.unity3d.com/Manual/class-QualitySettings.html)** de proyecto.
- La **velocidad de relleno** hace referencia a los píxeles que la GPU puede dibujar por segundo.
    - Para identificar las limitaciones de la velocidad de relleno, reduzca la resolución de pantalla y compruebe si se ha mejorado la velocidad de fotogramas. 
    - En Unity, esto se puede hacer a través de la propiedad *[XRSettings. renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)*

Generalmente, el ancho de banda de memoria implica optimizaciones para:
1) Reducir resoluciones de textura
2) Use menos texturas (normalización, reflejo, etc.).

La velocidad de relleno se centra en reducir el número de operaciones que se deben calcular para un píxel representado final. Esto incluye reducir:
1) Número de objetos que se van a representar o procesar
2) Número de operaciones por sombreador
3) Número de fases de GPU para el resultado final (sombreadores de geometría, efectos de procesamiento posterior, etc.)
4) Número de píxeles que se van a representar (resolución de pantalla)

#### <a name="reduce-polygon-count"></a>Reducir el número de polígonos

Los recuentos de polígonos más altos producen más operaciones para la GPU; al [reducir el número de polígonos](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets) de la escena, se reducirá el tiempo de representación. Hay otros factores implicados en el sombreado de la geometría que puede ser caro, pero el recuento de polígonos es la métrica más simple para determinar el costo que una escena va a representar.

#### <a name="limit-overdraw"></a>Sobredibujar límite

El sobredibujo alto se produce cuando se representan varios objetos, pero no se muestran en la pantalla, ya que están ocultos por un objeto occluding. Imagine que mira una pared que tiene objetos detrás. Toda la geometría se procesaría para la representación, pero solo es necesario representar la pared opaca. Esto produce operaciones innecesarias.

#### <a name="shaders"></a>Sombreadores

Los sombreadores son pequeños programas que se ejecutan en la GPU y realizan dos pasos importantes en la representación:
1) Determinar qué vértices se deben dibujar y dónde se encuentran en el espacio de pantalla (el sombreador de vértices)
    - El sombreador de vértices se ejecuta generalmente por vértice para cada malla.
2) Determinar el color de cada píxel (el sombreador de píxeles)
    - El sombreador de píxeles se ejecuta por píxel representado por el objeto Geometry en la textura que se representa en.

Normalmente, los sombreadores realizan muchas transformaciones y cálculos de iluminación. Aunque los modelos de iluminación complejos, las sombras y otras operaciones pueden generar resultados fantásticos, también tienen un precio. Reducir el número de operaciones calculadas en los sombreadores puede reducir en gran medida el trabajo necesario para la GPU por fotograma.

##### <a name="shader-coding-recommendations"></a>Recomendaciones de codificación del sombreador

- Usar el filtrado bilineal, siempre que sea posible
- Reorganizar expresiones para usar funciones intrínsecas de MAD con el fin de realizar una multiplicación y agregar al mismo tiempo
- Calcular el precálculo tanto como sea posible en la CPU y pasar como constantes al material
- **Favorecer el movimiento de las operaciones desde el sombreador de píxeles hasta el sombreador de vértices**
    - Por lo general, el número de vértices es mucho menor que el número de píxeles (720p es de 921.600 píxeles, 1080p es 2.073.600 píxeles, etc.)

#### <a name="remove-gpu-stages"></a>Quitar fases de GPU

Los efectos posteriores al procesamiento pueden ser muy costosos y aumentar la velocidad de relleno de la aplicación. Esto incluye técnicas de suavizado de contorno como MSAA. En HoloLens, se recomienda evitar estas técnicas por completo, así como otras fases del sombreador, como la geometría, el casco y los sombreadores de cálculo.

## <a name="memory-recommendations"></a>Recomendaciones de memoria

Las operaciones de asignación y desasignación de memoria excesiva pueden dar lugar a un rendimiento incoherente, marcos inmovilizados y otro comportamiento perjudicial. Es especialmente importante comprender las consideraciones de memoria al desarrollar en Unity, ya que la administración de la memoria se controla mediante el recolector de elementos no utilizados.

#### <a name="object-pooling"></a>Agrupación de objetos

La agrupación de objetos es una técnica popular para reducir el costo de las asignaciones continuas y desasignaciones de objetos. Para ello, se asigna un grupo grande de objetos idénticos y se reutilizan instancias disponibles inactivas de este grupo en lugar de generar y destruir objetos constantemente a lo largo del tiempo. Los grupos de objetos son excelentes para los componentes reutilizables que tienen una duración variable durante una aplicación.

## <a name="see-also"></a>Consulte también
- [Recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md)
- [Configuración recomendada para Unity](recommended-settings-for-unity.md)
- [Optimizar modelos 3D](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [Prácticas recomendadas para convertir y optimizar modelos 3D en tiempo real](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/best-practices)

