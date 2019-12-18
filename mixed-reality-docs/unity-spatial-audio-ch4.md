---
title: 'Tutoriales de audio espacial: 4. Habilitar y deshabilitar el audio espacial en tiempo de ejecución'
description: Use un botón para habilitar y deshabilitar la espacialización del audio en tiempo de ejecución.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: realidad mixta, Unity, tutorial, hololens2, audio espacial
ms.openlocfilehash: 3fc9b56dc58d4c19f229d92f4562f04cbca0e7a6
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182872"
---
# <a name="enabling-and-disabling-spatialization-at-run-time"></a>Habilitar y deshabilitar la espacialización en tiempo de ejecución

## <a name="objectives"></a>Objetivos
En este cuarto capítulo, hará lo siguiente:
* Agregar un nuevo script para controlar la espacialización en un objeto de juego
* Controlar el script de control de la espacialización desde acciones de botón

## <a name="add-spatialization-control-script"></a>Agregar script de control de espacialización
Haga clic con el botón derecho en el panel **proyecto** y C# cree un nuevo script eligiendo **crear script de > C#** . Asigne el nombre "SpatializeOnOff" al script.

![Creación del script](images/spatial-audio/create-script.png)

Haga doble clic en el script en el panel **proyecto** para abrirlo en Visual Studio. Reemplace el contenido del script predeterminado por lo siguiente:

> [!NOTE]
> Se comentan varias líneas del script. En el [capítulo 5](unity-spatial-audio-ch5.md), se quitarán los comentarios de estas líneas.

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Audio;

[RequireComponent(typeof(AudioSource))]
public class SpatializeOnOff : MonoBehaviour
{
    public GameObject ButtonTextObject;
    //public AudioMixerGroup RoomEffectGroup;
    //public AudioMixerGroup MasterGroup;

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
        //m_SourceObject.outputAudioMixerGroup = RoomEffectGroup;
    }

    private void SetStereo()
    {
        m_IsSpatialized = false;
        m_SourceObject.spatialBlend = 0;
        m_TextMeshPro.SetText("Set Spatialized");
        //m_SourceObject.outputAudioMixerGroup = MasterGroup;
    }

}
```

> [!NOTE]
> Para habilitar o deshabilitar la espacialización, el script solo ajusta la propiedad **spatialBlend** , quedando la propiedad de la **espacialización** habilitada. En este modo, Unity sigue aplicando la curva de **volumen** . De lo contrario, si el usuario deshabilitara la espacialización desde el origen, se oíría el aumento brusco del volumen. <br> <br>
> Si prefiere deshabilitar completamente la espacialización, modifique el script para ajustar también la propiedad booleana de la **espacialización** de la variable **SourceObject** .

## <a name="attach-your-script-and-drive-it-from-the-button"></a>Adjunte el script y colóquelo en el botón
En el panel del **Inspector** de la **cuádruple**, haga clic en **Agregar componente** y agregue el espacio **de comandos de Spatial en OFF** :

![Agregar script a cuádruple](images/spatial-audio/add-script-to-quad.png)

En el componente de **Spatial en OFF** del **cuádruple**:
1. Busque el subobjeto **PressableButtonHoloLens2-> IconAndText-> TextMeshPro** en la **jerarquía**
2. Arrastre **TextMeshPro** suboject hasta el campo **ButtonTextObject** del componente **Spatial ON OFF** .

Después de estos cambios, el modo de **Spatial en OFF** del componente **cuádruple** tendrá el siguiente aspecto:

![Spatial en OFF Basic](images/spatial-audio/spatialize-on-off-basic.png)

Para establecer el botón para llamar al comando **Spatial ON OFF** cuando se suelta el botón, abra el panel **Inspector** del objeto **PressableButtonHoloLens2** , busque el componente **interactuable** y:
1. Buscar la región **OnClick ()** de la subsección **Events**
2. Arrastre la **cuádruple** desde la **jerarquía** hasta la ranura del objeto de destino.
3. Seleccione **SpatializeOnOff. SwapSpatialization** en el cuadro desplegable acción.

Después de estos cambios, el componente **interactuable** tendrá el siguiente aspecto:

![Configuración de acción de botón](images/spatial-audio/button-action-settings.png)

## <a name="next-steps"></a>Pasos siguientes
Pruebe la aplicación en HoloLens 2 o en el editor de Unity. En la aplicación, ahora puede tocar el botón para activar y desactivar la espacialización en el vídeo. Al realizar pruebas en el editor de Unity, presione la barra espaciadora y desplácese con la rueda de desplazamiento para activar la simulación de mano. 

Continúe con el [capítulo 5](unity-spatial-audio-ch5.md) para agregar la distancia percibida a las fuentes de sonido mediante reverberación.

