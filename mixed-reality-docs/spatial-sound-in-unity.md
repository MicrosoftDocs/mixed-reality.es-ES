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
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="2a09a-104">Sonido espacial en Unity</span><span class="sxs-lookup"><span data-stu-id="2a09a-104">Spatial Sound in Unity</span></span>

<span data-ttu-id="2a09a-105">En esta página se incluyen vínculos a recursos que le ayudarán a usar y diseñar con Microsoft HRTF spatializer en sus proyectos de realidad mixta de Unity.</span><span class="sxs-lookup"><span data-stu-id="2a09a-105">This page links to resources to help you use and design with the Microsoft HRTF spatializer in your Unity mixed reality projects.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="2a09a-106">Habilitar la espacialización</span><span class="sxs-lookup"><span data-stu-id="2a09a-106">Enable spatialization</span></span>

<span data-ttu-id="2a09a-107">Habilite **MS HRTF Spatializer** en la configuración de audio del proyecto.</span><span class="sxs-lookup"><span data-stu-id="2a09a-107">Enable the **MS HRTF Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="2a09a-108">Para obtener más información, consulte [la documentación de spatializer de Unity](https://docs.unity3d.com/Manual/VRAudioSpatializer.html).</span><span class="sxs-lookup"><span data-stu-id="2a09a-108">For more details, see [Unity's spatializer documentation](https://docs.unity3d.com/Manual/VRAudioSpatializer.html).</span></span> 

<span data-ttu-id="2a09a-109">Adjunte un **origen de audio** a un objeto de la jerarquía y habilite la espacialización activando la casilla habilitar la **espacialización** y moviendo el control deslizante de **mezcla espacial** a "1".</span><span class="sxs-lookup"><span data-stu-id="2a09a-109">Attach an **Audio Source** to an object in the hierarchy, and enable spatialization by checking the **Enable spatialization** checkbox and moving the **Spatial Blend** slider to '1'.</span></span> <span data-ttu-id="2a09a-110">Para más información, consulte [la documentación de origen de audio de Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html).</span><span class="sxs-lookup"><span data-stu-id="2a09a-110">For more details, see [Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html).</span></span> 

## <a name="design-with-spatialization"></a><span data-ttu-id="2a09a-111">Diseño con espacialización</span><span class="sxs-lookup"><span data-stu-id="2a09a-111">Design with spatialization</span></span>

### <a name="distance-based-attenuation"></a><span data-ttu-id="2a09a-112">Atenuación basada en distancia</span><span class="sxs-lookup"><span data-stu-id="2a09a-112">Distance-based attenuation</span></span>
<span data-ttu-id="2a09a-113">La decadencia basada en la distancia predeterminada de Unity tiene una distancia mínima de 1 metro y una distancia máxima de 500 metros, con una rolloff logarítmica.</span><span class="sxs-lookup"><span data-stu-id="2a09a-113">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="2a09a-114">Esto puede funcionar para su escenario, o puede que los orígenes desplazarse demasiado rápido o demasiado despacio.</span><span class="sxs-lookup"><span data-stu-id="2a09a-114">This may work for your scenario, or you may find sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="2a09a-115">Para obtener información sobre cómo establecer estas curvas en Unity, consulte [diseño de sonido en la realidad mixta](spatial-sound-design.md) para obtener la configuración recomendada para las curvas de decadencia de distancia y [la documentación de origen de audio de Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) .</span><span class="sxs-lookup"><span data-stu-id="2a09a-115">See [sound design in mixed reality](spatial-sound-design.md) for recommended settings for distance decay curves, and see [Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for information on setting these curves in Unity.</span></span>

### <a name="environment"></a><span data-ttu-id="2a09a-116">Entorno</span><span class="sxs-lookup"><span data-stu-id="2a09a-116">Environment</span></span>
<span data-ttu-id="2a09a-117">**MS HRTF Spatializer** incluye un componente de reverberación de habitación con [cuatro configuraciones de reverberación](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment) y un valor predeterminado de ' Small '.</span><span class="sxs-lookup"><span data-stu-id="2a09a-117">The **MS HRTF Spatializer** includes a room reverb component with [four reverb settings](https://docs.microsoft.com/windows/win32/api/hrtfapoapi/ne-hrtfapoapi-hrtfenvironment) and a default of 'small'.</span></span> <span data-ttu-id="2a09a-118">La configuración del salón se puede cambiar mediante programación para cada origen de audio adjuntando C# el script siguiente a cada objeto de Unity que tenga un origen de audio espacial:</span><span class="sxs-lookup"><span data-stu-id="2a09a-118">The room setting can be changed programmatically for each audio source by attaching the following C# script to each object in Unity that has a spatialized Audio Source:</span></span>

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

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="2a09a-119">Ejemplos de sonido espacial de Unity</span><span class="sxs-lookup"><span data-stu-id="2a09a-119">Unity spatial sound examples</span></span>
<span data-ttu-id="2a09a-120">El kit de herramientas de realidad mixta (MRTK) incluye ejemplos de formas de aplicar efectos de audio en realidad mixta: [demostraciones de MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio).</span><span class="sxs-lookup"><span data-stu-id="2a09a-120">The Mixed Reality Toolkit (MRTK) includes examples of ways to apply audio effects in mixed reality: [MRTK demos](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio).</span></span>

