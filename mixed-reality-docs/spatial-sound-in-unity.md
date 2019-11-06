---
title: Sonido espacial en Unity
description: Reproducir un sonido espacial procedente de un punto 3D específico dentro de la escena de Unity.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, sonido espacial, HRTF, tamaño de sala
ms.openlocfilehash: c96717d9df9b89fbb09f0b4466ee3a9bf5c8a149
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641069"
---
# <a name="spatial-sound-in-unity"></a>Sonido espacial en Unity

En esta página se incluyen vínculos a recursos que le ayudarán a usar y diseñar con Microsoft HRTF spatializer en sus proyectos de realidad mixta de Unity.

## <a name="enable-spatialization"></a>Habilitar la espacialización

Habilite **MS HRTF Spatializer** en la configuración de audio del proyecto. Para obtener más información, consulte [la documentación de spatializer de Unity](https://docs.unity3d.com/Manual/VRAudioSpatializer.html). 

Adjunte un **origen de audio** a un objeto de la jerarquía y habilite la espacialización activando la casilla habilitar la **espacialización** y moviendo el control deslizante de **mezcla espacial** a "1". Para más información, consulte [la documentación de origen de audio de Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html). 

## <a name="design-with-spatialization"></a>Diseño con espacialización

### <a name="distance-based-attenuation"></a>Atenuación basada en distancia
La decadencia basada en la distancia predeterminada de Unity tiene una distancia mínima de 1 metro y una distancia máxima de 500 metros, con una rolloff logarítmica. Esto puede funcionar para su escenario, o puede que los orígenes desplazarse demasiado rápido o demasiado despacio. Para obtener información sobre cómo establecer estas curvas en Unity, consulte [diseño de sonido en la realidad mixta](spatial-sound-design.md) para obtener la configuración recomendada para las curvas de decadencia de distancia y [la documentación de origen de audio de Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) .

### <a name="environment"></a>Entorno
**MS HRTF Spatializer** incluye un componente de reverberación de habitación con [cuatro configuraciones de reverberación](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment) y un valor predeterminado de ' Small '. La configuración del salón se puede cambiar mediante programación para cada origen de audio adjuntando C# el script siguiente a cada objeto de Unity que tenga un origen de audio espacial:

```cs
using UnityEngine;
   using System.Collections;
   public class SetHRTF : MonoBehaviour    {
       public enum ROOMSIZE { Small, Medium, Large, None };
       public ROOMSIZE room = ROOMSIZE.Small;  // Small is regarded as the "most average"
       // defaults and docs from MSDN
       // https://msdn.microsoft.com/library/windows/desktop/mt186602(v=vs.85).aspx
       AudioSource audiosource;
       void Awake()
       {
           audiosource = this.gameObject.GetComponent<AudioSource>();
           if (audiosource == null)
           {
               print("SetHRTFParams needs an audio source to do anything.");
               return;
           }
           audiosource.spatialize = 1; // we DO want spatialized audio
           audiosource.spread = 0; // we dont want to reduce our angle of hearing
           audiosource.spatialBlend = 1;   // we do want to hear spatialized audio
           audiosource.SetSpatializerFloat(1, (float)room);    // 1 is the roomsize param
       }
   }
```

## <a name="unity-spatial-sound-examples"></a>Ejemplos de sonido espacial de Unity
El kit de herramientas de realidad mixta (MRTK) incluye ejemplos de formas de aplicar efectos de audio en realidad mixta: [demostraciones de MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio).

