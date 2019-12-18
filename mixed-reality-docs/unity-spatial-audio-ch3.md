---
title: 'Tutoriales de audio espacial: 3. Espacialización del audio de un vídeo'
description: Importe un recurso de vídeo en el proyecto de Unity y cospatiala el audio del vídeo.
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: realidad mixta, Unity, tutorial, hololens2, audio espacial
ms.openlocfilehash: 1e5c84fd7d14cc5edc78839bbdf91590cc7fd8e7
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2019
ms.locfileid: "75182752"
---
# <a name="spatializing-audio-from-a-video"></a><span data-ttu-id="e78ff-105">Espacialización del audio de un vídeo</span><span class="sxs-lookup"><span data-stu-id="e78ff-105">Spatializing audio from a video</span></span>
<span data-ttu-id="e78ff-106">En este tercer capítulo del módulo de audio espacial de los tutoriales de Unity de HoloLens 2, hará lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="e78ff-106">In this 3rd chapter of the spatial audio module of the HoloLens 2 Unity tutorials, you'll:</span></span>
* <span data-ttu-id="e78ff-107">Importar un vídeo y agregar un reproductor de vídeo</span><span class="sxs-lookup"><span data-stu-id="e78ff-107">Import a video and add a Video Player</span></span>
* <span data-ttu-id="e78ff-108">Reproducir el vídeo en un Quadrangle</span><span class="sxs-lookup"><span data-stu-id="e78ff-108">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="e78ff-109">Enrute el audio del vídeo al Quadrangle y Spatial el audio</span><span class="sxs-lookup"><span data-stu-id="e78ff-109">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player"></a><span data-ttu-id="e78ff-110">Importar un vídeo y agregar un reproductor de vídeo</span><span class="sxs-lookup"><span data-stu-id="e78ff-110">Import a video and add a Video Player</span></span>

<span data-ttu-id="e78ff-111">Arrastre un archivo de vídeo al panel **proyecto** del proyecto de Unity.</span><span class="sxs-lookup"><span data-stu-id="e78ff-111">Drag a video file into the **Project** pane in your Unity project.</span></span> <span data-ttu-id="e78ff-112">Puede usar [este vídeo](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) desde el proyecto de ejemplo de audio espacial.</span><span class="sxs-lookup"><span data-stu-id="e78ff-112">You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

![Carpeta assets con vídeo](images/spatial-audio/assets-folder-with-video.png)

<span data-ttu-id="e78ff-114">Ajustar la configuración de calidad en el clip de vídeo puede garantizar una reproducción fluida de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="e78ff-114">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="e78ff-115">Haga clic en el archivo de vídeo en el panel **proyecto** .</span><span class="sxs-lookup"><span data-stu-id="e78ff-115">Click on the video file in the **Project** pane.</span></span> <span data-ttu-id="e78ff-116">Después, en el panel **Inspector** del archivo de vídeo, invalide la configuración de las aplicaciones de la tienda Windows y:</span><span class="sxs-lookup"><span data-stu-id="e78ff-116">Then in the **Inspector** pane for the video file, override the settings for Windows Store Apps, and:</span></span>
* <span data-ttu-id="e78ff-117">Habilitar **Transcode**</span><span class="sxs-lookup"><span data-stu-id="e78ff-117">Enable **Transcode**</span></span>
* <span data-ttu-id="e78ff-118">Establecer **códec** en H264</span><span class="sxs-lookup"><span data-stu-id="e78ff-118">Set **Codec** to H264</span></span>
* <span data-ttu-id="e78ff-119">Establecer el **modo de velocidad de bits** en baja</span><span class="sxs-lookup"><span data-stu-id="e78ff-119">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="e78ff-120">Establecer **calidad espacial** en calidad espacial media</span><span class="sxs-lookup"><span data-stu-id="e78ff-120">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="e78ff-121">Después de estos ajustes, el panel del **Inspector** para el archivo de vídeo tendrá el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="e78ff-121">After these adjustments, the **Inspector** pane for the video file will look like this:</span></span>

![Panel de propiedades de vídeo](images/spatial-audio/video-property-pane.png)

<span data-ttu-id="e78ff-123">A continuación, agregue un objeto de **reproductor de vídeo** a la **jerarquía** haciendo clic con el botón derecho en el panel de **jerarquías** y eligiendo **vídeo > reproductor de**vídeo:</span><span class="sxs-lookup"><span data-stu-id="e78ff-123">Next, add a **Video Player** object to the **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **Video -> Video Player**:</span></span>

![Reproductor de vídeo en jerarquía](images/spatial-audio/video-player-in-hierarchy.png)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="e78ff-125">Reproducir vídeo en un Quadrangle</span><span class="sxs-lookup"><span data-stu-id="e78ff-125">Play video onto a quadrangle</span></span>
<span data-ttu-id="e78ff-126">El objeto **reproductor de vídeo** necesita un objeto de juego con textura en el que representar el vídeo.</span><span class="sxs-lookup"><span data-stu-id="e78ff-126">The **Video Player** object needs a textured game object on which to render the video.</span></span> <span data-ttu-id="e78ff-127">En primer lugar, agregue un **cuádruple** a la **jerarquía** ; para ello, haga clic con el botón derecho en el panel de **jerarquías** y elija **objeto 3D > cuádruple**:</span><span class="sxs-lookup"><span data-stu-id="e78ff-127">First, add a **Quad** to your **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **3D Object -> Quad**:</span></span>

![Agregar cuatro a la jerarquía](images/spatial-audio/add-quad-to-hierarchy.png)

<span data-ttu-id="e78ff-129">Para asegurarse de que el **cuádruple** aparece delante del usuario cuando se inicia la aplicación, establezca la propiedad **posición** de **cuádruple** en (0, 0, 2) y la propiedad **escala** en (1,28, 0,72, 1).</span><span class="sxs-lookup"><span data-stu-id="e78ff-129">To ensure the **Quad** appears in front of the user when the application starts, set the **Position** property of the **Quad** to (0, 0, 2), and the **Scale** property to (1.28, 0.72, 1).</span></span> <span data-ttu-id="e78ff-130">Después de estos cambios, el componente de **transformación** en el panel del **Inspector** de la **cuádruple** tendrá el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="e78ff-130">After these changes, the **Transform** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Transformación cuádruple](images/spatial-audio/quad-transform.png)

<span data-ttu-id="e78ff-132">Para crear una textura entre el **cuádruple** y el vídeo, cree una nueva **textura de representación**.</span><span class="sxs-lookup"><span data-stu-id="e78ff-132">To texture the **Quad** with video, create a new **Render Texture**.</span></span> <span data-ttu-id="e78ff-133">En el panel **proyecto** , haga clic con el botón derecho y seleccione **crear-> Mostrar textura**:</span><span class="sxs-lookup"><span data-stu-id="e78ff-133">In the **Project** pane, right-click and choose **Create -> Render Texture**:</span></span>

![Crear textura de representación](images/spatial-audio/create-render-texture.png)

<span data-ttu-id="e78ff-135">En el panel **Inspector** de la **textura de representación**, establezca la propiedad **size** para que coincida con la resolución nativa del vídeo de 1280x720.</span><span class="sxs-lookup"><span data-stu-id="e78ff-135">On the **Inspector** pane of the **Render Texture**, set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="e78ff-136">A continuación, para garantizar un buen rendimiento de la representación en HoloLens 2, establezca la propiedad de **búfer de profundidad** en una **profundidad de 16 bits como mínimo**.</span><span class="sxs-lookup"><span data-stu-id="e78ff-136">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth**.</span></span> <span data-ttu-id="e78ff-137">Después de esta configuración, el panel del **Inspector** para la **textura de representación** tendrá el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="e78ff-137">After these settings, the **Inspector** pane for the **Render Texture** will look like this:</span></span>

![Representar propiedades de textura](images/spatial-audio/render-texture-properties.png)

<span data-ttu-id="e78ff-139">A continuación, use la nueva **textura de representación** como textura para la **cuádruple**:</span><span class="sxs-lookup"><span data-stu-id="e78ff-139">Next, use your new **Render Texture** as the texture for the **Quad**:</span></span>
1. <span data-ttu-id="e78ff-140">Arrastre la **textura de representación** desde el panel **proyecto** hasta el **cuádruple** de la **jerarquía** .</span><span class="sxs-lookup"><span data-stu-id="e78ff-140">Drag the **Render Texture** from the **Project** pane onto the **Quad** in the **Hierarchy**</span></span>
2. <span data-ttu-id="e78ff-141">Para garantizar un buen rendimiento en HoloLens 2, en el panel **Inspector** de la serie **, seleccione**el **sombreador estándar del kit de herramientas de realidad mixta**.</span><span class="sxs-lookup"><span data-stu-id="e78ff-141">To ensure good performance on HoloLens 2, on the **Inspector** pane for the **Quad**, select the **Mixed Reality Toolkit Standard Shader**.</span></span>

<span data-ttu-id="e78ff-142">Con esta configuración, el componente de **textura** en el panel del **Inspector** de la **cuádruple** tendrá el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="e78ff-142">With these settings, the **Texture** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Propiedades de textura cuádruple](images/spatial-audio/quad-texture-properties.png)

<span data-ttu-id="e78ff-144">Para establecer el nuevo **reproductor de vídeo** y **representar la textura** para reproducir el clip de vídeo, abra el panel del **Inspector** para el **reproductor de vídeo** y:</span><span class="sxs-lookup"><span data-stu-id="e78ff-144">To set your new **Video Player** and **Render Texture** to play your video clip, open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="e78ff-145">Establecer la propiedad **clip de vídeo** en el archivo de vídeo</span><span class="sxs-lookup"><span data-stu-id="e78ff-145">Set the **Video Clip** property to your video file</span></span>
* <span data-ttu-id="e78ff-146">Marque la casilla **bucle**</span><span class="sxs-lookup"><span data-stu-id="e78ff-146">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="e78ff-147">Establecer la **textura de destino** en la nueva textura de representación</span><span class="sxs-lookup"><span data-stu-id="e78ff-147">Set **Target Texture** to your new render texture</span></span>

<span data-ttu-id="e78ff-148">El panel del **Inspector** del **reproductor de vídeo** tendrá ahora el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="e78ff-148">The **Inspector** pane for the **Video Player** will now look like this:</span></span>

![Propiedades del reproductor de vídeo](images/spatial-audio/video-player-properties.png)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="e78ff-150">Spatial el audio del vídeo</span><span class="sxs-lookup"><span data-stu-id="e78ff-150">Spatialize the audio from the video</span></span>
<span data-ttu-id="e78ff-151">En el panel **Inspector** del **cuádruple**, cree un **origen de audio** al que enrutará el audio desde el vídeo:</span><span class="sxs-lookup"><span data-stu-id="e78ff-151">In the **Inspector** pane for the **Quad**, create an **Audio Source** to which you'll route the audio from the video:</span></span>
* <span data-ttu-id="e78ff-152">Haga clic en **Agregar componente** en la parte inferior del panel.</span><span class="sxs-lookup"><span data-stu-id="e78ff-152">Click **Add Component** at the bottom of the pane</span></span>
* <span data-ttu-id="e78ff-153">Agregar un **origen de audio**</span><span class="sxs-lookup"><span data-stu-id="e78ff-153">Add an **Audio Source**</span></span>

<span data-ttu-id="e78ff-154">Después, en el **origen de audio**:</span><span class="sxs-lookup"><span data-stu-id="e78ff-154">Then, on the **Audio Source**:</span></span>
* <span data-ttu-id="e78ff-155">Establecer el **resultado** en el mezclador</span><span class="sxs-lookup"><span data-stu-id="e78ff-155">Set **Output** to your mixer</span></span>
* <span data-ttu-id="e78ff-156">Active la casilla **Spatial**</span><span class="sxs-lookup"><span data-stu-id="e78ff-156">Check the **Spatialize** box</span></span>
* <span data-ttu-id="e78ff-157">Mueve el control deslizante de **mezcla espacial** a 1 (3D)</span><span class="sxs-lookup"><span data-stu-id="e78ff-157">Move the **Spatial Blend** slider to 1 (3D)</span></span>

<span data-ttu-id="e78ff-158">Después de estos cambios, el componente **origen de audio** del panel **Inspector** de la **cuádruple** tendrá el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="e78ff-158">After these changes, the **Audio Source** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![Inspector de fuente de audio cuádruple](images/spatial-audio/quad-audio-source-inspector.png)

<span data-ttu-id="e78ff-160">Para configurar el **reproductor de vídeo** para que enrute su audio a la **fuente de audio** en el **cuádruple**, abra el panel del **Inspector** para el **reproductor de vídeo** y:</span><span class="sxs-lookup"><span data-stu-id="e78ff-160">To set the **Video Player** to route its audio to the **Audio Source** on the **Quad**, open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="e78ff-161">Establecer el **modo de salida de audio** en "origen de audio"</span><span class="sxs-lookup"><span data-stu-id="e78ff-161">Set the **Audio Output Mode** to 'Audio Source'</span></span>
* <span data-ttu-id="e78ff-162">Establezca la propiedad **origen de audio** en su cuádruple</span><span class="sxs-lookup"><span data-stu-id="e78ff-162">Set the **Audio Source** property to your Quad</span></span>

<span data-ttu-id="e78ff-163">Después de estos cambios, el panel del **Inspector** del **reproductor de vídeo** tendrá el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="e78ff-163">After these changes, the **Inspector** pane for the **Video Player** will look like this:</span></span>

![Reproductor de vídeo conjunto de audio origen](images/spatial-audio/video-player-set-audio-source.png)

## <a name="next-steps"></a><span data-ttu-id="e78ff-165">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="e78ff-165">Next steps</span></span>
<span data-ttu-id="e78ff-166">Pruebe la aplicación en HoloLens 2 o en el editor de Unity.</span><span class="sxs-lookup"><span data-stu-id="e78ff-166">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="e78ff-167">Verá y oirá el vídeo y el audio del vídeo se encontrará espacial.</span><span class="sxs-lookup"><span data-stu-id="e78ff-167">You'll see and hear the video, and the audio from the video will be spatialized.</span></span>

<span data-ttu-id="e78ff-168">Continúe con el [capítulo 4](unity-spatial-audio-ch4.md) para usar el botón para habilitar y deshabilitar la espacialización en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="e78ff-168">Continue to [Chapter 4](unity-spatial-audio-ch4.md) to use the button to enable and disable spatialization at run time.</span></span>

