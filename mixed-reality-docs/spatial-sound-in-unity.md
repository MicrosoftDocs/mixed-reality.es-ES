---
title: Sonido espacial en Unity
description: Reproducir sonido espacial procede de un punto 3D específico dentro de la escena de Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, espacial de sonido, HRTF, tamaño de la sala
ms.openlocfilehash: e2b321d7086314a14a940d57aa17e67636c758b8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597517"
---
# <a name="spatial-sound-in-unity"></a>Sonido espacial en Unity

Este tema describe cómo usar sonido espacial en los proyectos de Unity. Trata los archivos de complemento, así como los componentes de Unity y propiedades que permiten sonido espacial.

## <a name="enabling-spatial-sound-in-unity"></a>Habilitar el sonido espacial en Unity

Sonido espacial, en Unity, se habilita mediante un complemento de audio espacial. Los archivos del complemento se agrupan directamente en Unity para habilitar el sonido espacial es tan fácil como va a **Editar > configuración del proyecto > Audio** y cambiando el **espacial complemento** en el Inspector de la  **MS HRTF espacial**. Puesto que el efecto de espacio de Microsoft solo admite actualmente 48000Hz, también se debe establecer la frecuencia de muestreo del sistema como 48000 para evitar un error HRTF en el caso excepcional de que el dispositivo de salida del sistema ya no se establece en 48000:

![Inspector de AudioManager](images/audio-250px.png)<br>
*Inspector de AudioManager*

El proyecto de Unity ahora está configurado para usar un sonido espacial.

>[!NOTE]
>Si no está utilizando un equipo con Windows 10 para el desarrollo, no obtendrá espacial sonido en el editor ni en el dispositivo (incluso si está usando el SDK de Windows 10).

## <a name="using-spatial-sound-in-unity"></a>Uso de sonido espacial en Unity

Sonido espacial se usa en su proyecto Unity mediante el ajuste de configuración de tres de los componentes de origen de Audio. Los pasos siguientes configurará los componentes de origen de Audio de sonido espacial.
* En el **jerarquía** del panel, seleccione el objeto de juego que tenga adjunta **origen Audio**.
* En el **Inspector** panel, en el **origen Audio** componente
    * Compruebe el **Spatialize** opción.
    * Establecer **Blend espacial** a **3D** (valor numérico 1).
    * Para obtener mejores resultados, expanda **configuración sonido 3D** y establecer **atenuación de volumen** a **personalizado atenuación**.

![Panel del inspector de Unity que muestra el origen de Audio](images/audiosource.png)<br>
*Panel del inspector de Unity que muestra el origen de Audio*

Ahora los sonidos de forma realista existen dentro del entorno del proyecto.

Se recomienda encarecidamente que se familiarice con la [instrucciones de diseño de sonido espacial](spatial-sound-design.md). Estas directrices ayudar a integrar el audio a la perfección en su proyecto y Sumergir aún más los usuarios en la experiencia que ha creado.

## <a name="setting-spatial-sound-settings"></a>Configuración de sonido espacial

El complemento de Microsoft Spatial Sound proporciona un parámetro adicional que se puede establecer en una por cada origen de Audio, para permitir que un control adicional de la simulación de audio. Este parámetro es el tamaño de la sala simulado.

### <a name="room-size"></a>Tamaño de la sala

El tamaño de la sala simulada mediante sonido espacial. El tamaño aproximado de las salas es: pequeño (una oficina en una sala de conferencias pequeño), mediano (una sala de conferencias de gran tamaño) y grande (un auditorio). También puede especificar un tamaño de la sala None para simular un entorno al aire libre. El tamaño del espacio predeterminado es pequeño.

### <a name="example"></a>Ejemplo

El MixedRealityToolkit para Unity proporciona una clase estática que hace que la configuración de sonido espacial fácil. Esta clase puede encontrarse en el [MixedRealityToolkit\SpatialSound carpeta](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialSound) y se puede llamar desde cualquier secuencia de comandos en el proyecto. Se recomienda establecer estos parámetros en cada componente de origen de Audio en el proyecto. El ejemplo siguiente muestra si selecciona el tamaño del espacio medio para un origen de Audio asociado.

```cs
AudioSource audioSource = gameObject.GetComponent<AudioSource>()

if (audioSource != null) {
    SpatialSoundSettings.SetRoomSize(audioSource, SpatialMappingRoomSizes.Medium);
}
```

### <a name="directly-accessing-parameters-from-unity"></a>Acceso directo a los parámetros de Unity

Si no desea utilizar las excelentes herramientas de Audio en el MixedRealityToolkit, mostramos cómo cambiaría la HRTF parámetros. Se puede copiar y pegar esto en un script denominado *SetHRTF.cs* que desea asociar a cada AudioSource HRTF. Permite cambiar los parámetros importantes para la HRTF.

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
### <a name="spatial-sound-in-mixed-reality-toolkit"></a>Sonido espacial en el Kit de herramientas de realidad mixta
- [HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/UAudioManagerTest.unity)

Los siguientes ejemplos desde el Kit de herramientas de realidad mixta son ejemplos de efecto de audio general que demuestran formas de hacer sus experiencias más envolventes mediante el uso de sonido.
- [HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioLoFiTest.unity)
- [HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/SpatialSound/Scenes/AudioOcclusionTest.unity)

## <a name="see-also"></a>Vea también
* [Sonido espacial](spatial-sound.md)
* [Diseño espacial de sonido](spatial-sound-design.md)
