---
title: Sonido espacial en Unity
description: Reproducir sonido espacial desde un punto 3D específico dentro de la escena de Unity.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, sonido espacial, HRTF, tamaño de sala
ms.openlocfilehash: af3f1486c3e931ad93d7b8960d822653ec740c12
ms.sourcegitcommit: ee8c7e821cb337cbccd8af64b13ee5f50109a776
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082039"
---
# <a name="spatial-sound-in-unity"></a>Sonido espacial en Unity

Esta página contiene vínculos a recursos de sonido espacial en Unity.

## <a name="spatializer-options"></a>Opciones de Spatializer
Las opciones de Spatializer para aplicaciones de realidad mixta incluyen:
* *MS HRTF Spatializer*. Unity lo proporciona como parte del paquete opcional de *Windows Mixed Reality* .
  * Esto se ejecuta en la CPU en una arquitectura de "origen único" de mayor costo.
  * Esto se proporciona por compatibilidad con versiones anteriores con las aplicaciones de HoloLens originales.
* *Microsoft Spatializer*. Está disponible en el [repositorio de github de Microsoft spatializer](https://github.com/microsoft/spatialaudio-unity).
  * Usa una arquitectura de "varios orígenes" de menor costo.
  * En HoloLens 2, se descarga en un acelerador de hardware.

En el caso de las nuevas aplicaciones, se recomienda *Microsoft Spatializer*.

## <a name="enable-spatialization"></a>Habilitar la espacialización

Use [NuGet para Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) para instalar _Microsoft. SpatialAudio. Spatializer. Unity_ y elija **Microsoft Spatializer** en la configuración de audio del proyecto. A continuación:
* Adjuntar un **origen de audio** a un objeto de la jerarquía
* Active la casilla **Habilitar la espacialización**
* Mueve el control deslizante de **mezcla espacial** a ' 1 '
* Asegúrese de que el audio espacial está habilitado en la estación de trabajo del desarrollador. Habilítelo haciendo clic con el botón derecho en el icono de volumen en la barra de tareas y asegurándose de que el sonido espacial esté establecido en un valor distinto de "desactivado". Para obtener la mejor representación de lo que escuchará en HoloLens 2, elija **Windows Sonic para auriculares**.

>[!NOTE]
>Si recibe un error en Unity que le permite cargar el complemento Microsoft. SpatialAudio. Spatializer. Unity porque falta una de sus dependencias, compruebe que dispone de la versión más reciente de [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) instalada en su equipo.

Para obtener más información, vea:
* [Repositorio de GitHub de Microsoft spatializer](https://github.com/microsoft/spatialaudio-unity)
* [Tutorial de spatializer de Microsoft](unity-spatial-audio-ch1.md)
* [Documentación del origen de audio de Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [Documentación de spatializer de Unity](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a>Atenuación basada en distancia
La decadencia basada en la distancia predeterminada de Unity tiene una distancia mínima de 1 metro y una distancia máxima de 500 metros, con una rolloff logarítmica. Es posible que esta configuración funcione para su escenario, o puede que los orígenes se expongan demasiado rápido o demasiado lentamente. Para obtener más información, vea:
* [Diseño sonoro en la realidad mixta](spatial-sound-design.md) para la configuración recomendada.
* [Documentación de origen de audio de Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) para obtener instrucciones sobre cómo establecer estas curvas.

## <a name="reverb"></a>Reverbera
De forma predeterminada, el _Spatializer de Microsoft_ deshabilita los efectos posteriores a Spatializer. Para habilitar la reverberación y otros efectos para los orígenes espaciales:
* Asociar el componente de **nivel de envío del efecto de sala** a cada origen
* Ajuste la curva de nivel de envío de cada origen para controlar la ganancia del audio que se devuelve al gráfico para el procesamiento de efectos

Consulte [el capítulo 5 del tutorial de spatializer](unity-spatial-audio-ch5.md) para obtener más información.

## <a name="unity-spatial-sound-examples"></a>Ejemplos de sonido espacial de Unity
Para ver ejemplos de sonido espacial en Unity, consulte:
* [Demostraciones de MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* [Proyecto de ejemplo de Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)

## <a name="next-steps"></a>Pasos siguientes
* [Diseño sonoro en realidad mixta](spatial-sound-design.md)
* [Tutorial de spatializer de Microsoft](unity-spatial-audio-ch1.md)

