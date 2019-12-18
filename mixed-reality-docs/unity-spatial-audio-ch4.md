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
# <a name="enabling-and-disabling-spatialization-at-run-time"></a><span data-ttu-id="79dec-105">Habilitar y deshabilitar la espacialización en tiempo de ejecución</span><span class="sxs-lookup"><span data-stu-id="79dec-105">Enabling and disabling spatialization at run time</span></span>

## <a name="objectives"></a><span data-ttu-id="79dec-106">Objetivos</span><span class="sxs-lookup"><span data-stu-id="79dec-106">Objectives</span></span>
<span data-ttu-id="79dec-107">En este cuarto capítulo, hará lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="79dec-107">In this 4th chapter, you'll:</span></span>
* <span data-ttu-id="79dec-108">Agregar un nuevo script para controlar la espacialización en un objeto de juego</span><span class="sxs-lookup"><span data-stu-id="79dec-108">Add a new script to control spatialization on a game object</span></span>
* <span data-ttu-id="79dec-109">Controlar el script de control de la espacialización desde acciones de botón</span><span class="sxs-lookup"><span data-stu-id="79dec-109">Drive the spatialization control script from button actions</span></span>

## <a name="add-spatialization-control-script"></a><span data-ttu-id="79dec-110">Agregar script de control de espacialización</span><span class="sxs-lookup"><span data-stu-id="79dec-110">Add spatialization control script</span></span>
<span data-ttu-id="79dec-111">Haga clic con el botón derecho en el panel **proyecto** y C# cree un nuevo script eligiendo **crear script de > C#** .</span><span class="sxs-lookup"><span data-stu-id="79dec-111">Right-click in the **Project** pane and create a new C# script by choosing **Create -> C# Script**.</span></span> <span data-ttu-id="79dec-112">Asigne el nombre "SpatializeOnOff" al script.</span><span class="sxs-lookup"><span data-stu-id="79dec-112">Name your script "SpatializeOnOff".</span></span>

![Creación del script](images/spatial-audio/create-script.png)

<span data-ttu-id="79dec-114">Haga doble clic en el script en el panel **proyecto** para abrirlo en Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="79dec-114">Double-click the script in the **Project** pane to open it in Visual Studio.</span></span> <span data-ttu-id="79dec-115">Reemplace el contenido del script predeterminado por lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="79dec-115">Replace the default script contents with the following:</span></span>

> [!NOTE]
> <span data-ttu-id="79dec-116">Se comentan varias líneas del script. En el [capítulo 5](unity-spatial-audio-ch5.md), se quitarán los comentarios de estas líneas.</span><span class="sxs-lookup"><span data-stu-id="79dec-116">Several lines of the script are commented out. These lines will be uncommented in [Chapter 5](unity-spatial-audio-ch5.md).</span></span>

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
> <span data-ttu-id="79dec-117">Para habilitar o deshabilitar la espacialización, el script solo ajusta la propiedad **spatialBlend** , quedando la propiedad de la **espacialización** habilitada.</span><span class="sxs-lookup"><span data-stu-id="79dec-117">To enable or disable spatialization, the script only adjusts the **spatialBlend** property, leaving the **spatialization** property enabled.</span></span> <span data-ttu-id="79dec-118">En este modo, Unity sigue aplicando la curva de **volumen** .</span><span class="sxs-lookup"><span data-stu-id="79dec-118">In this mode, Unity still applies the **Volume** curve.</span></span> <span data-ttu-id="79dec-119">De lo contrario, si el usuario deshabilitara la espacialización desde el origen, se oíría el aumento brusco del volumen.</span><span class="sxs-lookup"><span data-stu-id="79dec-119">Otherwise, if the user were to disable spatialization when far from the source, they would hear the volume increase abruptly.</span></span> <br> <br>
> <span data-ttu-id="79dec-120">Si prefiere deshabilitar completamente la espacialización, modifique el script para ajustar también la propiedad booleana de la **espacialización** de la variable **SourceObject** .</span><span class="sxs-lookup"><span data-stu-id="79dec-120">If you prefer to fully disable spatialization, modify the script to also adjust the **spatialization** boolean property of the **SourceObject** variable.</span></span>

## <a name="attach-your-script-and-drive-it-from-the-button"></a><span data-ttu-id="79dec-121">Adjunte el script y colóquelo en el botón</span><span class="sxs-lookup"><span data-stu-id="79dec-121">Attach your script and drive it from the button</span></span>
<span data-ttu-id="79dec-122">En el panel del **Inspector** de la **cuádruple**, haga clic en **Agregar componente** y agregue el espacio **de comandos de Spatial en OFF** :</span><span class="sxs-lookup"><span data-stu-id="79dec-122">On the **Inspector** pane of the **Quad**, click **Add Component** and add the **Spatialize On Off** script:</span></span>

![Agregar script a cuádruple](images/spatial-audio/add-script-to-quad.png)

<span data-ttu-id="79dec-124">En el componente de **Spatial en OFF** del **cuádruple**:</span><span class="sxs-lookup"><span data-stu-id="79dec-124">On the **Spatialize On Off** component of the **Quad**:</span></span>
1. <span data-ttu-id="79dec-125">Busque el subobjeto **PressableButtonHoloLens2-> IconAndText-> TextMeshPro** en la **jerarquía**</span><span class="sxs-lookup"><span data-stu-id="79dec-125">Find the **PressableButtonHoloLens2 -> IconAndText -> TextMeshPro** subobject in the **Hierarchy**</span></span>
2. <span data-ttu-id="79dec-126">Arrastre **TextMeshPro** suboject hasta el campo **ButtonTextObject** del componente **Spatial ON OFF** .</span><span class="sxs-lookup"><span data-stu-id="79dec-126">Drag the **TextMeshPro** suboject onto the **ButtonTextObject** field of the **Spatialize On Off** component</span></span>

<span data-ttu-id="79dec-127">Después de estos cambios, el modo de **Spatial en OFF** del componente **cuádruple** tendrá el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="79dec-127">After these changes, the **Spatialize On Off** component of the **Quad** will look like this:</span></span>

![Spatial en OFF Basic](images/spatial-audio/spatialize-on-off-basic.png)

<span data-ttu-id="79dec-129">Para establecer el botón para llamar al comando **Spatial ON OFF** cuando se suelta el botón, abra el panel **Inspector** del objeto **PressableButtonHoloLens2** , busque el componente **interactuable** y:</span><span class="sxs-lookup"><span data-stu-id="79dec-129">To set the button to call the **Spatialize On Off** script when the button is released, open the **Inspector** pane of the **PressableButtonHoloLens2** object, find the **Interactable** component, and:</span></span>
1. <span data-ttu-id="79dec-130">Buscar la región **OnClick ()** de la subsección **Events**</span><span class="sxs-lookup"><span data-stu-id="79dec-130">Find the **OnClick ()** region of the **Events** subsection</span></span>
2. <span data-ttu-id="79dec-131">Arrastre la **cuádruple** desde la **jerarquía** hasta la ranura del objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="79dec-131">Drag the **Quad** from the **Hierarchy** into the target object slot.</span></span>
3. <span data-ttu-id="79dec-132">Seleccione **SpatializeOnOff. SwapSpatialization** en el cuadro desplegable acción.</span><span class="sxs-lookup"><span data-stu-id="79dec-132">Select **SpatializeOnOff.SwapSpatialization** from the action drop-down box.</span></span>

<span data-ttu-id="79dec-133">Después de estos cambios, el componente **interactuable** tendrá el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="79dec-133">After these changes, the **Interactable** component will look like this:</span></span>

![Configuración de acción de botón](images/spatial-audio/button-action-settings.png)

## <a name="next-steps"></a><span data-ttu-id="79dec-135">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="79dec-135">Next steps</span></span>
<span data-ttu-id="79dec-136">Pruebe la aplicación en HoloLens 2 o en el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="79dec-136">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="79dec-137">En la aplicación, ahora puede tocar el botón para activar y desactivar la espacialización en el vídeo.</span><span class="sxs-lookup"><span data-stu-id="79dec-137">In the app, you can now touch the button to activate and deactivate spatialization on the video.</span></span> <span data-ttu-id="79dec-138">Al realizar pruebas en el editor de Unity, presione la barra espaciadora y desplácese con la rueda de desplazamiento para activar la simulación de mano.</span><span class="sxs-lookup"><span data-stu-id="79dec-138">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> 

<span data-ttu-id="79dec-139">Continúe con el [capítulo 5](unity-spatial-audio-ch5.md) para agregar la distancia percibida a las fuentes de sonido mediante reverberación.</span><span class="sxs-lookup"><span data-stu-id="79dec-139">Continue on to [Chapter 5](unity-spatial-audio-ch5.md) to add perceived distance to sound sources using reverb.</span></span>

