---
title: Procedimientos recomendados para trabajar con Unity y Visual Studio
description: Sugerencias y trucos para agilizar el flujo de trabajo de creación de una aplicación de realidad mixta con Unity y Visual Studio.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: implementar, unity, auriculares envolventes de visual studio, HoloLens,
ms.openlocfilehash: 80a533851b3bee0d747a90dfececbaa558c4ec1f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605579"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>Procedimientos recomendados para trabajar con Unity y Visual Studio

Un desarrollador que crea una aplicación de realidad mixta con Unity se deberá cambiar entre Unity y Visual Studio para crear el paquete de aplicación que se implementa en HoloLens o un auricular envolvente. De forma predeterminada dos instancias de Visual Studio son necesario (uno para modificar los scripts de Unity) y otro para implementar en el dispositivo y la depuración. El siguiente procedimiento permite el desarrollo con instancia única de Visual Studio, reduce la frecuencia de exportación de los proyectos de Unity y mejora la experiencia de depuración.

## <a name="improving-iteration-time"></a>Mejora el tiempo de iteración

Un problema común de flujo de trabajo cuando se trabaja con Unity y Visual Studio tiene varias ventanas de Visual Studio abierto y la necesidad de cambiar constantemente entre Visual Studio y Unity para recorrer en iteración.
1. **Unity** : para modificar la escena y exportación de una solución de Visual Studio
2. **Visual Studio (1)** : para modificar las secuencias de comandos
3. **Visual Studio (2)** : para compilar e implementar el Unity exportan solución de Visual Studio al dispositivo

Por suerte, hay una manera de optimizar para una única instancia de Visual Studio y reducen las exportaciones frecuentes desde Unity.

Cuando [exportar el proyecto de Unity](exporting-and-building-a-unity-visual-studio-solution.md), compruebe la **Unity C# proyectos** casilla de verificación en el menú "Configuración de compilación del archivo >". Ahora, el proyecto que se exporta desde Unity incluye todo el proyecto C# secuencias de comandos y tiene varias ventajas:
* Usar la misma instancia de Visual Studio para escribir secuencias de comandos y la implementación y creación del proyecto
* Exportar desde Unity solo cuando la escena se cambia en el Editor de Unity; cambiar el contenido de secuencias de comandos puede hacerse en Visual Studio sin necesidad de volver a exportar.

Con **Unity C# proyectos** habilitada, es necesario abrir solo una instancia de cada programa:
1. **Unity** : para modificar la escena y exportación de una solución de Visual Studio
2. **Visual Studio** : para modificar los scripts, a continuación, compilar e implementar el Unity exportan solución de Visual Studio al dispositivo

## <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools para Unity

Descargar [Visual Studio Tools para Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)

**Ventajas de Visual Studio Tools para Unity**
* Depurar el modo de reproducción en el editor de Unity desde Visual Studio mediante la colocación de los puntos de interrupción, evaluar variables y expresiones complejas.
* Utilice el Unity Project Explorer para buscar la secuencia de comandos con la misma jerarquía que muestra Unity.
* Obtenga la consola de Unity directamente dentro de Visual Studio.
* Use asistentes para crear rápidamente o navegue hasta secuencias de comandos.

## <a name="expose-c-class-variables-for-easy-tuning"></a>Exponer C# clase variables para la optimización fácil

Hay dos maneras de exponer las variables de clase. La manera recomendada de hacerlo es agregar el atributo [SerializeField] a las variables privadas. Esto les permite acceder desde el editor pero no mediante programación expuestos.  La otra opción consiste en realizar C# público de las variables de clase para exponerlas en el editor de la interfaz de usuario. 

Ambos métodos permiten ajustar con facilidad las variables mientras se reproduce en el editor. Esto es especialmente útil para la optimización de las propiedades de interacción mecánico.

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Volver a generar soluciones de UWP de Visual Studio después de actualizar el SDK de Windows o de Unity

Soluciones de UWP de Visual Studio activadas en el control de código fuente pueden obtener obsoletas después de actualizar a un nuevo motor de Windows SDK o Unity. Puede resolver esto después de la actualización al crear una nueva solución UWP desde Unity y luego combinar cualquier diferencia en la solución activa en.

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>Usar recursos de formato de texto para facilitar la comparación de los cambios de contenido

Almacenar recursos en formato de texto facilita revisar las diferencias de cambio de contenido en Visual Studio. Puede habilitar en "Editar > Opciones > Editor del proyecto" cambiando **Asset serialización** modo a **forzar texto**. Sin embargo, combinar los cambios de archivo de texto activo propensas a errores y no se recomienda, por lo que puede habilitar desprotecciones exclusivas de binarias en el sistema de control de código fuente.
