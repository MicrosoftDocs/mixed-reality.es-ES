---
title: 'Tutoriales de audio espacial: 5. Usar reverberación para agregar distancia al audio espacial'
description: Agregue un efecto de reverberación para mejorar el sentido de la variación de distancia al audio espacial.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: realidad mixta, Unity, tutorial, hololens2, audio espacial
ms.openlocfilehash: abe78417dc231e6228d1942e03418ba699bc0938
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182742"
---
# <a name="using-reverb-to-add-distance-to-spatial-audio"></a>Usar reverberación para agregar distancia al audio espacial

## <a name="objectives"></a>Objetivos
En los capítulos anteriores, agregamos la espacialización a los sonidos para darles sentido. En este quinto capítulo, agregaremos un efecto de reverberación para que suene un sentido de distancia. Nuestros objetivos son los siguientes:
* Mejorar la distancia de fuentes de sonido percibida mediante la adición de reverberación
* Controlar la distancia percibida del sonido con la distancia del agente de escucha al holograma

## <a name="add-a-mixer-group-and-a-reverb-effect"></a>Agregar un grupo de mezclador y un efecto de reverberación
En el [capítulo 2](unity-spatial-audio-ch2.md), agregamos un mezclador. El mezclador incluye un **Grupo** de forma predeterminada denominado **maestro**. Dado que solo deseamos aplicar un efecto de reverberación a algunos sonidos, vamos a agregar un segundo **Grupo** para esos sonidos. Para agregar un **Grupo**, haga clic con el botón derecho en el grupo **maestro** en el **mezclador de audio** y elija **Agregar grupo secundario**:

![Agregar grupo secundario](images/spatial-audio/add-child-group.png)

En este ejemplo, hemos denominado "efecto de sala" al nuevo grupo.

Cada **Grupo** tiene su propio conjunto de efectos. Agregue un efecto de reverberación al nuevo grupo; para ello, haga clic en **Agregar...** en el nuevo grupo y elija **SFX reverberación**:

![Agregar reverberación de SFX](images/spatial-audio/add-sfx-reverb.png)

En la terminología de audio, el audio original sin reverberar se denomina _trazado seco_y el audio después de filtrar con el filtro de reverberación se denomina _ruta húmeda_. Ambas rutas de acceso se envían a la salida de audio y sus puntos fuertes relativos en esta mezcla se denominan _mezcla húmeda/seco_. La mezcla húmeda/seco afecta de una granidad al sentido de la distancia.

La **reverberación de SFX** incluye controles para ajustar la mezcla húmeda/seco dentro del efecto. Dado que el complemento **Spatializer de Microsoft** controla el trazado seco, usaremos la **reverberación SFX** solo para el trazado húmedo. En el panel **Inspector** de la **reverberación SFX**:
* Establezca la propiedad nivel seco en la configuración más baja (-10000 mB)
* Establezca la propiedad Room en el valor más alto (0 mB)

Después de estos cambios, el panel del **Inspector** de la **reverberación SFX** tendrá el siguiente aspecto:

![Propiedades de reverberación de SFX](images/spatial-audio/sfx-reverb-properties.png)

Los demás valores controlan el funcionamiento del salón simulado. En concreto, el **tiempo de caída** está relacionado con el tamaño de la sala percibida. 

## <a name="enable-reverb-on-the-video-playback"></a>Habilitar reverberación en la reproducción de vídeo
Hay dos pasos para habilitar la reverberación en un origen de audio:
* Enrutar el **origen de audio** al **Grupo** adecuado
* Establecer el complemento de **Microsoft Spatializer** para pasar el audio al **Grupo** para su procesamiento

En los pasos siguientes, ajustaremos el script para controlar el enrutamiento de audio y adjuntaremos un script de control proporcionado con el complemento **Spatializer de Microsoft** para alimentar datos en la reverberación.

En el panel **Inspector** del **cuádruple**, haga clic en **Agregar componente** y agregue el script de nivel de envío del efecto de **sala** :

![Agregar script de nivel de envío](images/spatial-audio/add-send-level-script.png)

> [!NOTE]
> A menos que habilite la característica de **nivel de envío de efecto de sala** del complemento Spatializer de **Microsoft** , no enviará ningún audio al motor de audio de Unity para que el procesamiento surta efecto.

El componente de **nivel de envío de efecto de sala** incluye un control de gráfico que establece el nivel de audio que se envía al motor de audio de Unity para el procesamiento de reverberación. Haga clic y arrastre la curva hacia abajo para establecer el nivel en about-30dB:

![Ajustar curva de reverberación](images/spatial-audio/adjust-reverb-curve.png)

A continuación, quite las marcas de comentario de las cuatro líneas comentadas en el script **SpatializeOnOff** . El script tendrá ahora el siguiente aspecto:
```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    public AudioMixerGroup RoomEffectGroup;
    public AudioMixerGroup MasterGroup;

    private AudioSource m_SourceObject;
    private bool m_IsSpatialized;
    private TMPro.TextMeshPro m_TextMeshPro;

    public void Start()
    {
        m_SourceObject = gameObject.GetComponent<AudioSource>();
        m_TextMeshPro = ButtonTextObject.GetComponent<TMPro.TextMeshPro>();
        SetSpatialized();
    }

    public void SwapSpatialization()
    {
        if (m_IsSpatialized)
        {
            SetStereo();
        }
        else
        {
            SetSpatialized();
        }
    }

    private void SetSpatialized()
    {
        m_IsSpatialized = true;
        m_SourceObject.spatialBlend = 1;
        m_TextMeshPro.SetText("Set Stereo");
        m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

Al quitar los comentarios de estas líneas, se agregan dos propiedades al panel **Inspector** del script. Para establecerlos, en el panel **Inspector** del componente **Spatial ON OFF** de la serie **cuádruple**:
* Establecer la propiedad de **grupo de efectos de sala** en el nuevo grupo de mezcla de efectos de sala
* Establecer la propiedad del **Grupo maestro** en el grupo de mezclador principal

Después de estos cambios, las propiedades **de Spatial en OFF** tendrán el siguiente aspecto:

![Spatial en OFF extendido](images/spatial-audio/spatialize-on-off-extended.png)

## <a name="next-steps"></a>Pasos siguientes

Pruebe la aplicación en HoloLens 2 o en el editor de Unity. Ahora, cuando toque el botón en la aplicación para activar la espacialización, el script enrutará el audio del vídeo al grupo de efectos de la habitación para agregar la reverberación. Al cambiar a estéreo, enrutará el audio al grupo maestro y evitará que se agregue la reverberación.

Ha completado los tutoriales de audio espacial de HoloLens 2 para Unity. Enhorabuena.


