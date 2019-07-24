---
title: Sonido espacial en Unity
description: Reproducir un sonido espacial procedente de un punto 3D específico dentro de la escena de Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, sonido espacial, HRTF, tamaño de sala
ms.openlocfilehash: e2b321d7086314a14a940d57aa17e67636c758b8
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63549079"
---
# <a name="spatial-sound-in-unity"></a>Sonido espacial en Unity

En este tema se describe cómo usar el sonido espacial en los proyectos de Unity. Trata los archivos de complemento necesarios, así como los componentes y propiedades de Unity que permiten el sonido espacial.

## <a name="enabling-spatial-sound-in-unity"></a>Habilitación del sonido espacial en Unity

El sonido espacial, en Unity, se habilita mediante un complemento de spatializer de audio. Los archivos de complemento se agrupan directamente en Unity, por lo que habilitar el sonido espacial es tan sencillo como **editar > configuración del proyecto > audio** y cambiar el **complemento Spatializer** en el inspector al **Spatializer MS HRTF**. Dado que Microsoft spatializer solo admite 48000Hz actualmente, también debe establecer la velocidad de muestra del sistema en 48000 para evitar un error de HRTF en el caso excepcional de que el dispositivo de salida del sistema no esté establecido en 48000 ya:

![Inspector para AudioManager](images/audio-250px.png)<br>
*Inspector para AudioManager*

El proyecto de Unity ya está configurado para usar el sonido espacial.

>[!NOTE]
>Si no usa un equipo con Windows 10 para el desarrollo, no obtendrá sonido espacial en el editor ni en el dispositivo (incluso si usa el SDK de Windows 10).

## <a name="using-spatial-sound-in-unity"></a>Uso de sonido espacial en Unity

El sonido espacial se usa en el proyecto de Unity ajustando tres opciones en los componentes de origen de audio. En los pasos siguientes se configurarán los componentes de origen de audio para el sonido espacial.
* En el panel **jerarquía** , seleccione el objeto de juego que tiene un **origen de audio**conectado.
* En el panel **Inspector** , en el componente **origen de audio**
    * Active la opción **Spatial** .
    * Establezca **Blend espacial** en **3D** (valor numérico 1).
    * Para obtener los mejores resultados, expanda la **opción Configuración de sonido 3D** y establezca el **volumen rolloff** en **rolloff personalizado**.

![Panel de inspector en Unity que muestra el origen de audio](images/audiosource.png)<br>
*Panel de inspector en Unity que muestra el origen de audio*

Sus sonidos ahora existen en el entorno del proyecto.

Se recomienda encarecidamente que se familiarice con las [directrices de diseño de sonido espacial](spatial-sound-design.md). Estas instrucciones ayudan a integrar el audio sin problemas en el proyecto y a sumergir aún más a los usuarios en la experiencia que ha creado.

## <a name="setting-spatial-sound-settings"></a>Establecer la configuración de sonido espacial

El complemento de sonido espacial de Microsoft proporciona un parámetro adicional que se puede establecer en cada origen de audio para permitir un control adicional de la simulación de audio. Este parámetro es el tamaño del salón simulado.

### <a name="room-size"></a>Tamaño de sala

El tamaño de la habitación que simula el sonido espacial. Los tamaños aproximados de los salones son; pequeña (una oficina a una pequeña sala de conferencias), mediana (una gran sala de conferencias) y grande (un auditorio). También puede especificar un tamaño de sala de ninguno para simular un entorno exterior. El tamaño predeterminado de la sala es pequeño.

### <a name="example"></a>Ejemplo

MixedRealityToolkit para Unity proporciona una clase estática que facilita el establecimiento de la configuración de sonido espacial. Esta clase se puede encontrar en la [carpeta MixedRealityToolkit\SpatialSound](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) y se puede llamar desde cualquier script del proyecto. Se recomienda establecer estos parámetros en cada componente de origen de audio del proyecto. En el ejemplo siguiente se muestra cómo seleccionar el tamaño de la sala mediana para un origen de audio conectado.

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a>Acceso directo a los parámetros desde Unity

Si no desea usar las excelentes herramientas de audio de MixedRealityToolkit, aquí se indica cómo cambiar los parámetros de HRTF. Puede copiarlo y pegarlo en un script denominado *SetHRTF.CS* que quiera asociar a cada AUDIOSOURCE de HRTF. Permite cambiar los parámetros importantes a HRTF.

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a>Sonido espacial en el kit de herramientas de realidad mixta
- [HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest. Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

Los ejemplos siguientes del kit de herramientas de realidad mixta son ejemplos de efectos de audio generales que muestran formas de hacer que sus experiencias sean más envolventes mediante el uso de sonido.
- [HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest. Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest. Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a>Vea también
* [Sonido espacial](spatial-sound.md)
* [Diseño de sonido espacial](spatial-sound-design.md)
