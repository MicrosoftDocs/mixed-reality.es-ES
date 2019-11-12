---
title: Prácticas recomendadas para trabajar con Unity y Visual Studio
description: Sugerencias y trucos para simplificar el flujo de trabajo de creación de una aplicación de realidad mixta con Unity y Visual Studio.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: implementación, Unity, Visual Studio, HoloLens, HoloLens 2, auriculares envolventes
ms.openlocfilehash: 88eaa69f1349e3303a93d9d634479d8265eb417c
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926551"
---
# <a name="best-practices-for-working-with-unity-and-visual-studio"></a>Prácticas recomendadas para trabajar con Unity y Visual Studio

Un desarrollador que cree una aplicación de realidad mixta con Unity tendrá que cambiar entre Unity y Visual Studio para compilar el paquete de aplicación que se implementa en HoloLens y/o un auricular envolvente. De forma predeterminada, se requieren dos instancias de Visual Studio (una para modificar los scripts de Unity y otra para la implementación en el dispositivo y en la depuración). El siguiente procedimiento permite el desarrollo mediante una única instancia de Visual Studio, reduce la frecuencia de exportación de proyectos de Unity y mejora la experiencia de depuración.

## <a name="improving-iteration-time"></a>Mejorar el tiempo de iteración

La compatibilidad con el back-end de scripting de .NET en Unity está en desuso en Unity 2018 y se quitó en Unity 2019 +. Por lo tanto, se recomienda cambiar a [IL2CPP](https://docs.unity3d.com/Manual/IL2CPP.html). Sin embargo, esto puede provocar tiempos de compilación más prolongados de Unity a Visual Studio. Para mejorar la iteración más rápida, debe configurar su entorno para obtener los mejores resultados de la compilación.

1) Aproveche las compilaciones incrementales compilando el proyecto en el mismo directorio cada vez, reutilizando los archivos creados previamente
2) Deshabilitar exámenes de software antimalware para el proyecto & carpetas de compilación
   - Abrir **protección contra amenazas de Virus &** en la aplicación de configuración de Windows 10
   - Seleccione **Administrar configuración** en **configuración de protección contra amenazas de virus &**
   - Seleccione **Agregar o quitar exclusiones** en la sección **exclusiones** .
   - Haga clic en **Agregar una exclusión** y seleccione la carpeta que contiene el código del proyecto de Unity y las salidas de compilación
3) Uso de SSD para compilar

Consulte optimización de los [tiempos de compilación de IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html) para obtener más información. Consulte también [depuración en el back-end de scripting de IL2CPP](https://docs.unity3d.com/Manual/windowsstore-debugging-il2cpp.html).

Además, considere la posibilidad de instalar la [extensión de Visual Studio *UnityScriptAnalyzer* ](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer). Esta herramienta analiza los scripts C# de Unity en busca de código que pueda escribirse de forma más optimizada.

## <a name="visual-studio-tools-for-unity"></a>Visual Studio Tools para Unity

Descargar [Visual Studio Tools para Unity](https://docs.microsoft.com/visualstudio/cross-platform/getting-started-with-visual-studio-tools-for-unity?view=vs-2019)

**Ventajas de Visual Studio Tools para Unity**
* Depure el modo de reproducción en el editor de Unity desde Visual Studio colocando puntos de interrupción, evaluando variables y expresiones complejas.
* Use el explorador de proyectos de Unity para buscar el script con la misma jerarquía que se muestra en Unity.
* Obtenga la consola de Unity directamente en Visual Studio.
* Use los asistentes para crear o navegar rápidamente por scripts.

## <a name="expose-c-class-variables-for-easy-tuning"></a>Exponer C# variables de clase para facilitar el ajuste

Hay dos maneras de exponer variables de clase. La manera recomendada de hacerlo es agregar el atributo [SerializeField] a las variables privadas. Esto permite tener acceso a ellos desde el editor pero no se exponen mediante programación.  La otra opción es hacer C# que las variables de clase sean públicas para exponerlas en la interfaz de usuario del editor. 

Ambos enfoques permiten ajustar fácilmente las variables mientras se reproducen en el editor. Esto es especialmente útil para ajustar las propiedades del mecánico de interacción.

## <a name="regenerate-uwp-visual-studio-solutions-after-windows-sdk-or-unity-upgrade"></a>Volver a generar soluciones de Visual Studio para UWP después de la actualización de Windows SDK o Unity

Las soluciones de Visual Studio de UWP protegidas en el control de código fuente pueden no estar actualizadas después de actualizar a un nuevo motor de Windows SDK o Unity. Puede resolver este paso después de la actualización. para ello, cree una nueva solución de UWP desde Unity y, luego, combine cualquier diferencia en la solución protegida.

## <a name="use-text-format-assets-for-easy-comparison-of-content-changes"></a>Usar recursos en formato de texto para facilitar la comparación de los cambios de contenido

El almacenamiento de recursos en formato de texto permite revisar más fácilmente las diferencias de cambio de contenido en Visual Studio. Puede habilitarlo en "Editar > configuración del proyecto > Editor" cambiando el modo de **serialización de activos** para **forzar el texto**. Sin embargo, la combinación de cambios en el archivo de recursos de texto es propensa a errores y no se recomienda, por lo que considere habilitar desprotecciones binarias exclusivas en el sistema de control de código fuente.

## <a name="see-also"></a>Consulta también
- [Visual Studio Tools para Unity](https://visualstudiogallery.msdn.microsoft.com/8d26236e-4a64-4d64-8486-7df95156aba9)
- [Optimizar los tiempos de compilación para IL2CPP](https://docs.unity3d.com/Manual/IL2CPP-OptimizingBuildTimes.html)
- [*UnityScriptAnalyzer* Extensión de Visual Studio](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/UnityScriptAnalyzer)