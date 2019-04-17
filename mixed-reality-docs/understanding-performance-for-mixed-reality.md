---
title: Análisis de rendimiento de la realidad mixta
description: Advanced temas y los detalles sobre cómo optimizar el rendimiento de aplicaciones de realidad mixta de Windows
author: Troy-Ferrell
ms.author: trferrel
ms.date: 3/26/2019
ms.topic: article
keywords: Windows mixto en realidad, la realidad mixta, en realidad Virtual, VR, MR, rendimiento, optimización, CPU, GPU
ms.openlocfilehash: ce59f9023c21dc7c981a2bb97d9fbd0c57622dbf
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605375"
---
# <a name="understanding-performance-for-mixed-reality"></a>Análisis de rendimiento de la realidad mixta

En este artículo es una introducción a racionalizar la importancia del rendimiento de la aplicación de realidad mixta.  Experiencia del usuario puede disminuir considerablemente si la aplicación no se ejecuta en la velocidad de fotogramas óptima. Hologramas aparecerán inestables y seguimiento principal del entorno puede ser impreciso, dando lugar a una mala experiencia para el usuario. De hecho, el rendimiento debe considerarse como una característica de primera clase para el desarrollo de realidad mixta y no una estabilización, al final de la tarea de ciclo.

Para su revisión, continuación se enumeran los valores de velocidad de fotogramas de alto rendimiento para cada plataforma de destino.

| Plataforma | Velocidad de fotogramas de destino |
|----------|-------------------|
| [HoloLens](hololens-hardware-details.md) | 60 FPS |
| [Windows Mixed Reality Ultra PCs](immersive-headset-hardware-details.md) | FPS 90 |
| [Windows mixto realidad PCs](immersive-headset-hardware-details.md) | 60 FPS |

El marco de trabajo siguiente proporciona una descripción general de los procedimientos recomendados y concepciones hacia alcanzar velocidades de fotogramas de destino. Para profundizar aún más en obtener más información, puede leer el [recomendaciones de rendimiento para el artículo de Unity](performance-recommendations-for-unity.md). En concreto, este artículo relacionado describe cómo medir la velocidad de fotogramas en la aplicación de Unity Windows Mixed Reality, así como los pasos en el entorno de Unity para mejorar el rendimiento.

## <a name="understanding-performance-bottlenecks"></a>Descripción de los cuellos de botella de rendimiento

Si la aplicación tiene una velocidad de fotogramas déficit de rendimiento, el primer paso es analizar y comprender donde la aplicación es computacionalmente intensiva. Hay dos procesadores principales responsable de trabajo para representar la escena: la CPU y la GPU. Cada uno de estos dos componentes controlar operaciones diferentes y las fases de la aplicación de realidad mixta. Hay tres lugares claves donde se produzcan cuellos de botella. 

1. **Subproceso de la aplicación - CPU** -este subproceso es responsable de la lógica de aplicación. Esto incluye el procesamiento de entrada, animaciones, física y otra lógica y estado de la aplicación
2. **Representar subproceso - CPU al GPU** -este subproceso es responsable de enviar las llamadas de dibujo a la GPU. Cuando la aplicación quiere presentar un objeto como un cubo o modelo, este subproceso envía una solicitud a la GPU, que tiene una arquitectura optimizada para la representación, para realizar estas operaciones.
3. **GPU** - 
    este procesador normalmente controla la canalización de gráficos de la aplicación para transformar datos 3D (modelos, las texturas, etcetera) en píxeles y, finalmente, producen una imagen 2D para enviar a la pantalla del dispositivo.

![Duración de un marco](images/lifetime-of-a-frame.png)

Por lo general, las aplicaciones de HoloLens estarán limitado de GPU. Sin embargo, esto no es cierta en todas las aplicaciones y, por tanto, se recomienda usar las herramientas y técnicas a continuación para ir a la verdad terreno para su aplicación en particular.

## <a name="how-to-analyze-your-application"></a>Cómo analizar la aplicación

Hay muchas herramientas que permiten los desarrolladores comprender el perfil de rendimiento de la aplicación de realidad mixta. Estos le permitirá a ambas destino donde haya cuellos de botella y cómo se se manifiesta a sí mismos para depurarlos.

Se trata de una lista de las herramientas más populares y eficaces para obtener información sobre los perfiles profundo para la aplicación.
- [Analizadores de rendimiento de gráficos de Intel](https://software.intel.com/gpa)
- [Depuradores de gráficos de Visual Studio](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics?view=vs-2017)
- [Profiler de Unity](https://docs.unity3d.com/Manual/Profiler.html)
- [Depurador de marco de Unity](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a>Cómo generar perfiles en cualquier entorno

Hay una prueba sencilla para determinar rápidamente que si es probable que delimitado GPU o CPU limitada en la aplicación. Si reduce la resolución de la salida del destino de representación, hay menos píxeles para calcular y por lo tanto, menos trabajo la GPU debe llevar a cabo para representar una imagen. Ventanilla escalado (escalado de resolución dinámica) es la práctica de representar la imagen a un menor destino de representación, a continuación, puede mostrar el dispositivo de salida. El dispositivo se muestra a arriba desde el conjunto más pequeño de píxeles para mostrar la imagen final.

Después de disminuir la resolución de representación, si:
1) Velocidad de fotogramas de aplicación **aumenta**, es probable **limitado de GPU**
1) Velocidad de fotogramas de aplicación **sin cambios**, es probable **CPU limitada**

>[!NOTE]
>Unity ofrece la posibilidad de modificar fácilmente la resolución de destino de representación de la aplicación en tiempo de ejecución a través de la *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* propiedad. La imagen final que se presentan en el dispositivo tiene una resolución fija. La plataforma realizará una muestra la resolución más baja para crear una imagen de resolución superior para la representación en pantallas de salida. 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a>Cómo mejorar la aplicación

### <a name="cpu-performance-recommendations"></a>Recomendaciones de rendimiento de CPU

Por lo general, la mayoría del trabajo en una aplicación de realidad mixta en la CPU implica realizar la simulación de"" de la escena y lógica de aplicación único de forma exhaustiva de procesamiento. Por lo tanto, las áreas siguientes normalmente están destinadas para la optimización.

- Animaciones
- Simplificar la física
- Asignaciones de memoria
- Algoritmos complejos (como) cinemática inversa, búsqueda de ruta de acceso)

### <a name="gpu-performance-recommendations"></a>Recomendaciones de rendimiento de GPU

#### <a name="understanding-bandwidth-vs-fill-rate"></a>Tasa de relleno de vs de ancho de banda de descripción
Al representar un fotograma en la GPU, una aplicación es generalmente limitado por la tasa de relleno o el ancho de banda de memoria.

- **Ancho de banda de memoria** es la velocidad de lecturas y escrituras puede realizar la GPU de la memoria
    - Para identificar las limitaciones de ancho de banda, reducir la calidad de textura y compruebe si ha mejorado la velocidad de fotogramas.
    - En Unity, esto puede hacerse cambiando **Texture Quality** en **editar** > **configuración del proyecto**  >   **[ Configuración de calidad](https://docs.unity3d.com/Manual/class-QualitySettings.html)**.
- **Velocidad de relleno** se refiere al rendimiento de los píxeles representados que se pueden dibujar por segundo por la GPU.
    - Para identificar las limitaciones de velocidad de relleno, disminuir la resolución de pantalla y compruebe si ha mejorado la velocidad de fotogramas. 
    - En Unity, esto puede hacerse a través de la *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* propiedad

Ancho de banda de memoria, normalmente hay optimizaciones para cualquiera
1) disminuir las resoluciones de textura
2) utilizar menos texturas (como) etcetera de reflexión especular, Normals)

Tasa de relleno se centra principalmente en lo que reduce el número de operaciones que deben calcularse para un píxel final representado. Ejemplos de esto normalmente se dividen en reducir
1) número de objetos para representar y procesar
2) número de operaciones por sombreador
3) número de fases GPU para el resultado final (sombreadores de geometría, posteriores al procesamiento efectos, etcetera)
4) número de píxeles para representar (como) resolución de pantalla)

#### <a name="reduce-poly-count"></a>Reducir el número de poli
Polígono mayor cuenta resultado en más operaciones de la GPU y reducir el número de polígonos de la escena se reducirá la cantidad de tiempo para representar ese geometry. Hay otros factores implicados también en el sombreado de la geometría que todavía puede ser costosa, pero recuento polígono es la métrica de base para determinar cuánto cuesta será representar una escena.

#### <a name="limit-overdraw"></a>Límite de sobredibujo

Alto sobredibujan se produce cuando varios objetos se representan pero no va a producir en la pantalla como están ocultos de manera occluding, generalmente más cerca de otro objeto. Imagine que examina una pared que tenía varias salas y geometría detrás de él. Todos de la geometría se procesarán para la representación, pero sólo la pared opaca realmente debe representarse como lo occludes la vista de todo el contenido. Esto da como resultado una pérdida de tiempo operaciones que no son necesarios para la vista actual.

#### <a name="shaders"></a>Sombreadores

Los sombreadores son pequeños programas que se ejecutan en la GPU y generalmente determinan dos pasos importantes en la representación:
1) los vértices de qué objeto se deben dibujar en la pantalla y donde se encuentran en el espacio de pantalla (como) el sombreador de vértices)
    - El sombreador de vértices por lo general se ejecuta por vértice para cada GameObject
2) ¿Qué colorear los píxeles (como) el sombreador de píxeles)
    - Se ejecuta el sombreador de píxeles por píxel de la textura que se va a representar para el dispositivo presente

Normalmente, los sombreadores realizan muchas transformaciones y cálculos de iluminación. Aunque los modelos de iluminación complejas, sombras y otras operaciones pueden generar resultados fantásticos, también vienen con un precio. Reducir el número de operaciones calculadas en los sombreadores puede reducir considerablemente el trabajo total que se debe realizar una GPU por fotograma.

##### <a name="shader-coding-recommendations"></a>Sombreador de recomendaciones de codificación

- Usar el filtrado bilineal siempre que sea posible
- Reorganizar las expresiones para usar funciones intrínsecas DESENFRENADAS con el fin de realizar una multiplicación y una adición al mismo tiempo
- Precalculan tanto como sea posible en la CPU y pasar como constantes al material
- **Favorecer mover las operaciones desde el sombreador de píxeles para el sombreador de vértices**
    - Por lo general, el número de vértices << número de píxeles (como) 720p == 921,600 pixels, 1080p == 2,073,600 pixels, etc)

#### <a name="remove-gpu-stages"></a>Quitar fases GPU
Posprocesamiento efectos puede resultar muy caro y normalmente inhibir la tasa de relleno de la aplicación. Esto también incluye técnicas de suavizado de contorno como MSAA. En HoloLens, se recomienda para evitar estas técnicas completamente. Además, fases del sombreador adicionales como la geometría, casco y los sombreadores de cálculo deben evitarse siempre que sea posible.

## <a name="memory-recommendations"></a>Recomendaciones de memoria
Las operaciones de asignación y desasignación de memoria excesivo pueden tener efectos adversos sobre su aplicación holográfica, dando como resultado un rendimiento incoherente, marcos inmovilizados y otro comportamiento perjudicial. Es especialmente importante entender las consideraciones de memoria al desarrollar en Unity, puesto que la administración de memoria se controla mediante el recolector de elementos no utilizados.

#### <a name="object-pooling"></a>Agrupación de objetos

Agrupación de objetos es una técnica popular para reducir el costo de las asignaciones continua y las cancelaciones de asignación de objetos. Esto se hace mediante la asignación de un grupo grande de objetos idénticos y volver a usar las instancias inactivas, disponibles desde este grupo en lugar de generar constantemente y destruir objetos con el tiempo. Los grupos de objetos son excelentes para los componentes puedan volver a utilizar con duración de la variable durante una aplicación.

## <a name="see-also"></a>Vea también
- [Recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md)
- [Configuración recomendada para Unity](recommended-settings-for-unity.md)
