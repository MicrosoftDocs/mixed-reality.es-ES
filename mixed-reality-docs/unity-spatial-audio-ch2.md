---
title: 'Tutoriales de audio espacial: 2. Sonidos de interacción del botón de espacialización'
description: Agregue un botón al proyecto y Spatial los sonidos de interacción del botón.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: realidad mixta, Unity, tutorial, hololens2, audio espacial
ms.openlocfilehash: bd70e3bc88ee39b2c6257089ac3a2b93dfae0ad1
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182782"
---
# <a name="spatializing-button-interaction-sounds"></a><span data-ttu-id="5d3ea-105">Sonidos de interacción del botón de espacialización</span><span class="sxs-lookup"><span data-stu-id="5d3ea-105">Spatializing button interaction sounds</span></span>

## <a name="objectives"></a><span data-ttu-id="5d3ea-106">Objetivos</span><span class="sxs-lookup"><span data-stu-id="5d3ea-106">Objectives</span></span>
<span data-ttu-id="5d3ea-107">En este segundo capítulo del módulo de audio espacial de los tutoriales de HoloLens 2, hará lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="5d3ea-107">In this second chapter of the spatial audio module of the HoloLens 2 tutorials, you'll:</span></span>
* <span data-ttu-id="5d3ea-108">Adición de un botón</span><span class="sxs-lookup"><span data-stu-id="5d3ea-108">Add a button</span></span>
* <span data-ttu-id="5d3ea-109">Spatial los sonidos del clic del botón</span><span class="sxs-lookup"><span data-stu-id="5d3ea-109">Spatialize the button click sounds</span></span>

## <a name="add-a-button"></a><span data-ttu-id="5d3ea-110">Adición de un botón</span><span class="sxs-lookup"><span data-stu-id="5d3ea-110">Add a button</span></span>
<span data-ttu-id="5d3ea-111">En el panel **proyecto** , seleccione **recursos** y escriba "PressableButtonHoloLens2" en la barra de búsqueda:</span><span class="sxs-lookup"><span data-stu-id="5d3ea-111">In the **Project** pane, select **Assets** and type "PressableButtonHoloLens2" in the search bar:</span></span>

![Botón recurso prefabricado en activos](images/spatial-audio/button-prefab-in-assets.png)

<span data-ttu-id="5d3ea-113">El botón recurso prefabricado es la entrada representada por un icono azul, en lugar de un icono blanco.</span><span class="sxs-lookup"><span data-stu-id="5d3ea-113">The button prefab is the entry represented by a blue icon, rather than a white icon.</span></span> <span data-ttu-id="5d3ea-114">Arrastre recurso prefabricado con el nombre **PressableButtonHoloLens2** al panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="5d3ea-114">Drag the prefab named **PressableButtonHoloLens2** into the **Hierarchy** pane.</span></span> <span data-ttu-id="5d3ea-115">En el panel **Inspector** del nuevo botón, establezca la propiedad **Position** en (0,-0,4, 2) para que aparezca delante del usuario cuando se inicie la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5d3ea-115">In the **Inspector** pane for your new button, set the **Position** property to (0, -0.4, 2) so that it will appear in front of the user when the application starts.</span></span> <span data-ttu-id="5d3ea-116">El componente de **transformación** del botón tendrá el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="5d3ea-116">The **Transform** component of the button will look like this:</span></span>

![Transformación de botón](images/spatial-audio/button-transform.png)

## <a name="spatialize-button-feedback"></a><span data-ttu-id="5d3ea-118">Comentario del botón de Spatial</span><span class="sxs-lookup"><span data-stu-id="5d3ea-118">Spatialize button feedback</span></span>
<span data-ttu-id="5d3ea-119">En este paso, creará un espacial de los comentarios de audio para el botón.</span><span class="sxs-lookup"><span data-stu-id="5d3ea-119">In this step, you'll spatialize the audio feedback for the button.</span></span> <span data-ttu-id="5d3ea-120">Para obtener sugerencias de diseño relacionadas, consulte [diseño de sonido espacial](spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="5d3ea-120">For related design suggestions, see [spatial sound design](spatial-sound-design.md).</span></span> 

<span data-ttu-id="5d3ea-121">El panel **mezclador de audio** permite definir destinos, denominados grupos de **mezclador**, para la reproducción de audio de componentes de origen de **audio** .</span><span class="sxs-lookup"><span data-stu-id="5d3ea-121">The **Audio Mixer** pane is where you'll define destinations, called **Mixer Groups**, for audio playback from **Audio Source** components.</span></span> 
* <span data-ttu-id="5d3ea-122">Abra el panel del **mezclador de audio** en la barra de menús con el **mezclador de audio > Audio-> de Windows**</span><span class="sxs-lookup"><span data-stu-id="5d3ea-122">Open the **Audio Mixer** pane from the menu bar using **Window -> Audio -> Audio Mixer**</span></span>
* <span data-ttu-id="5d3ea-123">Para crear un **mezclador** , haga clic en el "+" junto a **mixers**.</span><span class="sxs-lookup"><span data-stu-id="5d3ea-123">Create a **Mixer** by clicking the '+' next to **Mixers**.</span></span> <span data-ttu-id="5d3ea-124">El nuevo mezclador incluirá un **Grupo** predeterminado denominado **maestro**.</span><span class="sxs-lookup"><span data-stu-id="5d3ea-124">The new mixer will include a default **Group** called **Master**.</span></span>

<span data-ttu-id="5d3ea-125">El panel del **mezclador** tendrá ahora el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="5d3ea-125">Your **Mixer** pane will now look like this:</span></span>

![Panel de mezclador con el primer mezclador](images/spatial-audio/mixer-panel-with-first-mixer.png)

> [!NOTE]
> <span data-ttu-id="5d3ea-127">Hasta que se habilita la reverberación en el [capítulo 5](unity-spatial-audio-ch5.md), el medidor de volumen del mezclador no muestra la actividad de los sonidos que se reproducen a través de Microsoft Spatializer</span><span class="sxs-lookup"><span data-stu-id="5d3ea-127">Until reverb is enabled in [Chapter 5](unity-spatial-audio-ch5.md), the mixer's volume meter doesn't show activity for sounds played through the Microsoft Spatializer</span></span>

<span data-ttu-id="5d3ea-128">Haga clic en **PressableButtonHoloLens2** en el panel **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="5d3ea-128">Click the **PressableButtonHoloLens2** in the **Hierarchy** pane.</span></span> <span data-ttu-id="5d3ea-129">En el panel **Inspector** :</span><span class="sxs-lookup"><span data-stu-id="5d3ea-129">In the **Inspector** pane:</span></span>
1. <span data-ttu-id="5d3ea-130">Buscar el componente de **origen de audio**</span><span class="sxs-lookup"><span data-stu-id="5d3ea-130">Find the **Audio Source** component</span></span>
2. <span data-ttu-id="5d3ea-131">En la propiedad **salida** , haga clic en el selector y elija el mezclador.</span><span class="sxs-lookup"><span data-stu-id="5d3ea-131">For the **Output** property, click the selector and choose your mixer</span></span>
3. <span data-ttu-id="5d3ea-132">Active la casilla **Spatial**</span><span class="sxs-lookup"><span data-stu-id="5d3ea-132">Check the **Spatialize** checkbox</span></span>
4. <span data-ttu-id="5d3ea-133">Mueva el control deslizante de **mezcla espacial** a 3D (1).</span><span class="sxs-lookup"><span data-stu-id="5d3ea-133">Move the **Spatial Blend** slider to 3D (1).</span></span>

> [!NOTE]
> <span data-ttu-id="5d3ea-134">En las versiones de Unity anteriores a 2019, la casilla ' Spatial ' está en la parte inferior del panel del **Inspector** para el **origen de audio**.</span><span class="sxs-lookup"><span data-stu-id="5d3ea-134">In versions of Unity prior to 2019, the 'Spatialize' checkbox is at the bottom of the **Inspector** pane for the **Audio Source**.</span></span>

<span data-ttu-id="5d3ea-135">Después de estos cambios, el componente de **origen de audio** de su **PressableButtonHoloLens2** tendrá el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="5d3ea-135">After these changes, the **Audio Source** component of your **PressableButtonHoloLens2** will look like this:</span></span>

![Origen de audio de botón](images/spatial-audio/button-audio-source.png)

> [!NOTE]
> <span data-ttu-id="5d3ea-137">Si mueve la **mezcla espacial** a 1 (3D) sin activar la casilla **Spatial** , Unity usará su spatializer de movimiento panorámico, en lugar de **spatializer de Microsoft** con HRTFs.</span><span class="sxs-lookup"><span data-stu-id="5d3ea-137">If you move **Spatial Blend** to 1 (3D) without checking the **Spatialize** checkbox, Unity will use its panning spatializer, instead of the **Microsoft Spatializer** with HRTFs.</span></span>

## <a name="adjust-the-volume-curve"></a><span data-ttu-id="5d3ea-138">Ajustar la curva del volumen</span><span class="sxs-lookup"><span data-stu-id="5d3ea-138">Adjust the Volume curve</span></span>
<span data-ttu-id="5d3ea-139">De forma predeterminada, Unity atenúa los sonidos espaciales a medida que se alejan del agente de escucha.</span><span class="sxs-lookup"><span data-stu-id="5d3ea-139">By default, Unity will attenuate spatialized sounds as they get farther from the listener.</span></span> <span data-ttu-id="5d3ea-140">Cuando se aplica esta atenuación a los sonidos de interacción, la interfaz puede resultar más difícil de usar.</span><span class="sxs-lookup"><span data-stu-id="5d3ea-140">When this attenuation is applied to interaction feedback sounds, the interface can become more difficult to use.</span></span>

<span data-ttu-id="5d3ea-141">Para deshabilitar esta atenuación, ajuste la curva del **volumen** .</span><span class="sxs-lookup"><span data-stu-id="5d3ea-141">To disable this attenuation, adjust the **Volume** curve.</span></span> <span data-ttu-id="5d3ea-142">En el componente **origen de audio** del panel **Inspector** de **PressableButtonHoloLens2**, hay una sección denominada configuración de **sonido 3D**.</span><span class="sxs-lookup"><span data-stu-id="5d3ea-142">In the **Audio Source** component of the **Inspector** pane for the **PressableButtonHoloLens2**, there is a section called **3D Sound Settings**.</span></span> <span data-ttu-id="5d3ea-143">En esa sección:</span><span class="sxs-lookup"><span data-stu-id="5d3ea-143">In that section:</span></span>
1. <span data-ttu-id="5d3ea-144">Establezca la propiedad **Volume rolloff** en lineal.</span><span class="sxs-lookup"><span data-stu-id="5d3ea-144">Set the **Volume Rolloff** property to Linear</span></span>
2. <span data-ttu-id="5d3ea-145">Arrastre el punto de conexión en la curva de **volumen** (la curva roja) desde ' 0 ' en el eje y hasta ' 1 '</span><span class="sxs-lookup"><span data-stu-id="5d3ea-145">Drag the endpoint on the **Volume** curve (the red curve) from '0' on the y axis up to '1'</span></span>
3. <span data-ttu-id="5d3ea-146">Para ajustar la forma de la curva de **volumen** para que sea plana, arrastre el control de forma de curva blanca para que sea paralelo al eje X.</span><span class="sxs-lookup"><span data-stu-id="5d3ea-146">To adjust the shape of the **Volume** curve to be flat, drag the white curve shape control to be parallel to the X axis</span></span>

<span data-ttu-id="5d3ea-147">Después de estos cambios, la sección **configuración de sonido 3D** de las propiedades de **origen de audio** del **PressableButtonHoloLens2** tendrá el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="5d3ea-147">After these changes, the **3D Sound Settings** section of the **Audio Source** properties of the **PressableButtonHoloLens2** will look like this:</span></span>

![Configuración de sonido 3D del botón](images/spatial-audio/button-3d-sound-settings.png)

## <a name="next-steps"></a><span data-ttu-id="5d3ea-149">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="5d3ea-149">Next steps</span></span>

<span data-ttu-id="5d3ea-150">Pruebe la aplicación en HoloLens 2 o en el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="5d3ea-150">Try out your app on a HoloLens 2, or in the Unity editor.</span></span> <span data-ttu-id="5d3ea-151">En la aplicación, puede tocar el botón y oír los sonidos de interacción del botón espacial.</span><span class="sxs-lookup"><span data-stu-id="5d3ea-151">In the app, you can touch the button and hear the spatialized button interaction sounds.</span></span>

<span data-ttu-id="5d3ea-152">Al realizar pruebas en el editor de Unity, presione la barra espaciadora y desplácese con la rueda de desplazamiento para activar la simulación de mano.</span><span class="sxs-lookup"><span data-stu-id="5d3ea-152">When testing in the Unity editor, press the space bar and scroll with the scroll wheel to activate hand simulation.</span></span> <span data-ttu-id="5d3ea-153">Para obtener más información, consulte la [documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).</span><span class="sxs-lookup"><span data-stu-id="5d3ea-153">For more info, see the [MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene).</span></span>

<span data-ttu-id="5d3ea-154">Continúe con el [capítulo 3](unity-spatial-audio-ch3.md) para agregar un vídeo a la aplicación y Spatial el audio del vídeo.</span><span class="sxs-lookup"><span data-stu-id="5d3ea-154">Continue to [Chapter 3](unity-spatial-audio-ch3.md) to add a video to your app, and spatialize the audio from the video.</span></span>

