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
# <a name="using-reverb-to-add-distance-to-spatial-audio"></a><span data-ttu-id="f183c-105">Usar reverberación para agregar distancia al audio espacial</span><span class="sxs-lookup"><span data-stu-id="f183c-105">Using reverb to add distance to spatial audio</span></span>

## <a name="objectives"></a><span data-ttu-id="f183c-106">Objetivos</span><span class="sxs-lookup"><span data-stu-id="f183c-106">Objectives</span></span>
<span data-ttu-id="f183c-107">En los capítulos anteriores, agregamos la espacialización a los sonidos para darles sentido.</span><span class="sxs-lookup"><span data-stu-id="f183c-107">In previous chapters, we added spatialization to sounds to give them a sense of direction.</span></span> <span data-ttu-id="f183c-108">En este quinto capítulo, agregaremos un efecto de reverberación para que suene un sentido de distancia.</span><span class="sxs-lookup"><span data-stu-id="f183c-108">In this 5th chapter, we'll add a reverb effect to give sounds a sense of distance.</span></span> <span data-ttu-id="f183c-109">Nuestros objetivos son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="f183c-109">Our objectives are to:</span></span>
* <span data-ttu-id="f183c-110">Mejorar la distancia de fuentes de sonido percibida mediante la adición de reverberación</span><span class="sxs-lookup"><span data-stu-id="f183c-110">Improve perceived distance of sound sources by adding reverb</span></span>
* <span data-ttu-id="f183c-111">Controlar la distancia percibida del sonido con la distancia del agente de escucha al holograma</span><span class="sxs-lookup"><span data-stu-id="f183c-111">Control perceived distance of the sound using the listener's distance to the hologram</span></span>

## <a name="add-a-mixer-group-and-a-reverb-effect"></a><span data-ttu-id="f183c-112">Agregar un grupo de mezclador y un efecto de reverberación</span><span class="sxs-lookup"><span data-stu-id="f183c-112">Add a mixer group and a reverb effect</span></span>
<span data-ttu-id="f183c-113">En el [capítulo 2](unity-spatial-audio-ch2.md), agregamos un mezclador.</span><span class="sxs-lookup"><span data-stu-id="f183c-113">In [Chapter 2](unity-spatial-audio-ch2.md), we added a mixer.</span></span> <span data-ttu-id="f183c-114">El mezclador incluye un **Grupo** de forma predeterminada denominado **maestro**.</span><span class="sxs-lookup"><span data-stu-id="f183c-114">The mixer includes one **Group** by default called **Master**.</span></span> <span data-ttu-id="f183c-115">Dado que solo deseamos aplicar un efecto de reverberación a algunos sonidos, vamos a agregar un segundo **Grupo** para esos sonidos.</span><span class="sxs-lookup"><span data-stu-id="f183c-115">Because we'll only want to apply a reverb effect to some sounds, let's add a second **Group** for those sounds.</span></span> <span data-ttu-id="f183c-116">Para agregar un **Grupo**, haga clic con el botón derecho en el grupo **maestro** en el **mezclador de audio** y elija **Agregar grupo secundario**:</span><span class="sxs-lookup"><span data-stu-id="f183c-116">To add a **Group**, right click on the **Master** group in the **Audio Mixer** and choose **Add child group**:</span></span>

![Agregar grupo secundario](images/spatial-audio/add-child-group.png)

<span data-ttu-id="f183c-118">En este ejemplo, hemos denominado "efecto de sala" al nuevo grupo.</span><span class="sxs-lookup"><span data-stu-id="f183c-118">In this example, we've named the new group "Room Effect".</span></span>

<span data-ttu-id="f183c-119">Cada **Grupo** tiene su propio conjunto de efectos.</span><span class="sxs-lookup"><span data-stu-id="f183c-119">Each **Group** has its own set of effects.</span></span> <span data-ttu-id="f183c-120">Agregue un efecto de reverberación al nuevo grupo; para ello, haga clic en **Agregar...** en el nuevo grupo y elija **SFX reverberación**:</span><span class="sxs-lookup"><span data-stu-id="f183c-120">Add a reverb effect to the new group by clicking **Add...** on the new group, and choosing **SFX Reverb**:</span></span>

![Agregar reverberación de SFX](images/spatial-audio/add-sfx-reverb.png)

<span data-ttu-id="f183c-122">En la terminología de audio, el audio original sin reverberar se denomina _trazado seco_y el audio después de filtrar con el filtro de reverberación se denomina _ruta húmeda_.</span><span class="sxs-lookup"><span data-stu-id="f183c-122">In audio terminology, the original, unreverberated audio is called the _dry path_, and the audio after filtering with the reverb filter is called the _wet path_.</span></span> <span data-ttu-id="f183c-123">Ambas rutas de acceso se envían a la salida de audio y sus puntos fuertes relativos en esta mezcla se denominan _mezcla húmeda/seco_.</span><span class="sxs-lookup"><span data-stu-id="f183c-123">Both paths are sent to the audio output, and their relative strengths in this mixture is called the _wet/dry mix_.</span></span> <span data-ttu-id="f183c-124">La mezcla húmeda/seco afecta de una granidad al sentido de la distancia.</span><span class="sxs-lookup"><span data-stu-id="f183c-124">The wet/dry mix strongly affects the sense of distance.</span></span>

<span data-ttu-id="f183c-125">La **reverberación de SFX** incluye controles para ajustar la mezcla húmeda/seco dentro del efecto.</span><span class="sxs-lookup"><span data-stu-id="f183c-125">The **SFX Reverb** includes controls to adjust the wet/dry mix within the effect.</span></span> <span data-ttu-id="f183c-126">Dado que el complemento **Spatializer de Microsoft** controla el trazado seco, usaremos la **reverberación SFX** solo para el trazado húmedo.</span><span class="sxs-lookup"><span data-stu-id="f183c-126">Because the **Microsoft Spatializer** plugin handles the dry path, we'll be using the **SFX Reverb** only for the wet path.</span></span> <span data-ttu-id="f183c-127">En el panel **Inspector** de la **reverberación SFX**:</span><span class="sxs-lookup"><span data-stu-id="f183c-127">On the **Inspector** pane of your **SFX Reverb**:</span></span>
* <span data-ttu-id="f183c-128">Establezca la propiedad nivel seco en la configuración más baja (-10000 mB)</span><span class="sxs-lookup"><span data-stu-id="f183c-128">Set the Dry Level property to the lowest setting (-10000 mB)</span></span>
* <span data-ttu-id="f183c-129">Establezca la propiedad Room en el valor más alto (0 mB)</span><span class="sxs-lookup"><span data-stu-id="f183c-129">Set the Room property to the highest setting (0 mB)</span></span>

<span data-ttu-id="f183c-130">Después de estos cambios, el panel del **Inspector** de la **reverberación SFX** tendrá el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="f183c-130">After these changes, the **Inspector** pane of the **SFX Reverb** will look like this:</span></span>

![Propiedades de reverberación de SFX](images/spatial-audio/sfx-reverb-properties.png)

<span data-ttu-id="f183c-132">Los demás valores controlan el funcionamiento del salón simulado.</span><span class="sxs-lookup"><span data-stu-id="f183c-132">The other settings control the feel of the simulated room.</span></span> <span data-ttu-id="f183c-133">En concreto, el **tiempo de caída** está relacionado con el tamaño de la sala percibida.</span><span class="sxs-lookup"><span data-stu-id="f183c-133">In particular, **Decay Time** is related to perceived room size.</span></span> 

## <a name="enable-reverb-on-the-video-playback"></a><span data-ttu-id="f183c-134">Habilitar reverberación en la reproducción de vídeo</span><span class="sxs-lookup"><span data-stu-id="f183c-134">Enable reverb on the video playback</span></span>
<span data-ttu-id="f183c-135">Hay dos pasos para habilitar la reverberación en un origen de audio:</span><span class="sxs-lookup"><span data-stu-id="f183c-135">There are two steps to enable reverb on an audio source:</span></span>
* <span data-ttu-id="f183c-136">Enrutar el **origen de audio** al **Grupo** adecuado</span><span class="sxs-lookup"><span data-stu-id="f183c-136">Route the **Audio Source** to the appropriate **Group**</span></span>
* <span data-ttu-id="f183c-137">Establecer el complemento de **Microsoft Spatializer** para pasar el audio al **Grupo** para su procesamiento</span><span class="sxs-lookup"><span data-stu-id="f183c-137">Set the **Microsoft Spatializer** plugin to pass audio into the **Group** for processing</span></span>

<span data-ttu-id="f183c-138">En los pasos siguientes, ajustaremos el script para controlar el enrutamiento de audio y adjuntaremos un script de control proporcionado con el complemento **Spatializer de Microsoft** para alimentar datos en la reverberación.</span><span class="sxs-lookup"><span data-stu-id="f183c-138">In the following steps, we'll adjust our script to control the audio routing, and attach a control script provided with the **Microsoft Spatializer** plugin to feed data into the reverb.</span></span>

<span data-ttu-id="f183c-139">En el panel **Inspector** del **cuádruple**, haga clic en **Agregar componente** y agregue el script de nivel de envío del efecto de **sala** :</span><span class="sxs-lookup"><span data-stu-id="f183c-139">On the **Inspector** pane for the **Quad**, click **Add Component** and add the **Room Effect Send Level** script:</span></span>

![Agregar script de nivel de envío](images/spatial-audio/add-send-level-script.png)

> [!NOTE]
> <span data-ttu-id="f183c-141">A menos que habilite la característica de **nivel de envío de efecto de sala** del complemento Spatializer de **Microsoft** , no enviará ningún audio al motor de audio de Unity para que el procesamiento surta efecto.</span><span class="sxs-lookup"><span data-stu-id="f183c-141">Unless you enable **Room Effect Send Level** feature of the **Microsoft Spatializer** plugin, it doesn't send any audio back to the Unity audio engine for effect processing.</span></span>

<span data-ttu-id="f183c-142">El componente de **nivel de envío de efecto de sala** incluye un control de gráfico que establece el nivel de audio que se envía al motor de audio de Unity para el procesamiento de reverberación.</span><span class="sxs-lookup"><span data-stu-id="f183c-142">The **Room Effect Send Level** component includes a graph control that sets the level of the audio sent to the Unity audio engine for reverb processing.</span></span> <span data-ttu-id="f183c-143">Haga clic y arrastre la curva hacia abajo para establecer el nivel en about-30dB:</span><span class="sxs-lookup"><span data-stu-id="f183c-143">Click and drag the curve downwards to set the level to about -30dB:</span></span>

![Ajustar curva de reverberación](images/spatial-audio/adjust-reverb-curve.png)

<span data-ttu-id="f183c-145">A continuación, quite las marcas de comentario de las cuatro líneas comentadas en el script **SpatializeOnOff** .</span><span class="sxs-lookup"><span data-stu-id="f183c-145">Next, uncomment the 4 commented lines in the **SpatializeOnOff** script.</span></span> <span data-ttu-id="f183c-146">El script tendrá ahora el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="f183c-146">The script will now look like this:</span></span>
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

<span data-ttu-id="f183c-147">Al quitar los comentarios de estas líneas, se agregan dos propiedades al panel **Inspector** del script.</span><span class="sxs-lookup"><span data-stu-id="f183c-147">Uncommenting these lines adds two properties to the **Inspector** pane for the script.</span></span> <span data-ttu-id="f183c-148">Para establecerlos, en el panel **Inspector** del componente **Spatial ON OFF** de la serie **cuádruple**:</span><span class="sxs-lookup"><span data-stu-id="f183c-148">To set these, on the **Inspector** pane of the **Spatialize On Off** component of the **Quad**:</span></span>
* <span data-ttu-id="f183c-149">Establecer la propiedad de **grupo de efectos de sala** en el nuevo grupo de mezcla de efectos de sala</span><span class="sxs-lookup"><span data-stu-id="f183c-149">Set the **Room Effect Group** property to your new Room Effect mixer group</span></span>
* <span data-ttu-id="f183c-150">Establecer la propiedad del **Grupo maestro** en el grupo de mezclador principal</span><span class="sxs-lookup"><span data-stu-id="f183c-150">Set the **Master Group** property to the Master mixer group</span></span>

<span data-ttu-id="f183c-151">Después de estos cambios, las propiedades **de Spatial en OFF** tendrán el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="f183c-151">After these changes, the **Spatialize On Off** properties will look like this:</span></span>

![Spatial en OFF extendido](images/spatial-audio/spatialize-on-off-extended.png)

## <a name="next-steps"></a><span data-ttu-id="f183c-153">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="f183c-153">Next steps</span></span>

<span data-ttu-id="f183c-154">Pruebe la aplicación en HoloLens 2 o en el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="f183c-154">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="f183c-155">Ahora, cuando toque el botón en la aplicación para activar la espacialización, el script enrutará el audio del vídeo al grupo de efectos de la habitación para agregar la reverberación.</span><span class="sxs-lookup"><span data-stu-id="f183c-155">Now, when touching the button in the app to activate spatialization, the script will route the video's audio to the Room Effect Group to add reverb.</span></span> <span data-ttu-id="f183c-156">Al cambiar a estéreo, enrutará el audio al grupo maestro y evitará que se agregue la reverberación.</span><span class="sxs-lookup"><span data-stu-id="f183c-156">When switching to stereo, it will route the audio to the Master group, and avoid adding reverb.</span></span>

<span data-ttu-id="f183c-157">Ha completado los tutoriales de audio espacial de HoloLens 2 para Unity.</span><span class="sxs-lookup"><span data-stu-id="f183c-157">You've completed the HoloLens 2 spatial audio tutorials for Unity.</span></span> <span data-ttu-id="f183c-158">Enhorabuena.</span><span class="sxs-lookup"><span data-stu-id="f183c-158">Congratulations!</span></span>


