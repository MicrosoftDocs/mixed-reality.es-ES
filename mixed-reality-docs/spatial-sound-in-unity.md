---
title: Sonido espacial en Unity
description: Reproducir sonido espacial desde un punto 3D específico dentro de la escena de Unity.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: Unity, sonido espacial, HRTF, tamaño de sala
ms.openlocfilehash: af3f1486c3e931ad93d7b8960d822653ec740c12
ms.sourcegitcommit: ee8c7e821cb337cbccd8af64b13ee5f50109a776
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082039"
---
# <a name="spatial-sound-in-unity"></a><span data-ttu-id="c0092-104">Sonido espacial en Unity</span><span class="sxs-lookup"><span data-stu-id="c0092-104">Spatial sound in Unity</span></span>

<span data-ttu-id="c0092-105">Esta página contiene vínculos a recursos de sonido espacial en Unity.</span><span class="sxs-lookup"><span data-stu-id="c0092-105">This page links to resources for spatial sound in Unity.</span></span>

## <a name="spatializer-options"></a><span data-ttu-id="c0092-106">Opciones de Spatializer</span><span class="sxs-lookup"><span data-stu-id="c0092-106">Spatializer options</span></span>
<span data-ttu-id="c0092-107">Las opciones de Spatializer para aplicaciones de realidad mixta incluyen:</span><span class="sxs-lookup"><span data-stu-id="c0092-107">Spatializer options for mixed reality applications include:</span></span>
* <span data-ttu-id="c0092-108">*MS HRTF Spatializer*.</span><span class="sxs-lookup"><span data-stu-id="c0092-108">The *MS HRTF Spatializer*.</span></span> <span data-ttu-id="c0092-109">Unity lo proporciona como parte del paquete opcional de *Windows Mixed Reality* .</span><span class="sxs-lookup"><span data-stu-id="c0092-109">Unity provides this as part of the *Windows Mixed Reality* optional package.</span></span>
  * <span data-ttu-id="c0092-110">Esto se ejecuta en la CPU en una arquitectura de "origen único" de mayor costo.</span><span class="sxs-lookup"><span data-stu-id="c0092-110">This runs on CPU in a higher-cost 'single-source' architecture.</span></span>
  * <span data-ttu-id="c0092-111">Esto se proporciona por compatibilidad con versiones anteriores con las aplicaciones de HoloLens originales.</span><span class="sxs-lookup"><span data-stu-id="c0092-111">This is provided for backwards compatibility with original HoloLens applications.</span></span>
* <span data-ttu-id="c0092-112">*Microsoft Spatializer*.</span><span class="sxs-lookup"><span data-stu-id="c0092-112">The *Microsoft Spatializer*.</span></span> <span data-ttu-id="c0092-113">Está disponible en el [repositorio de github de Microsoft spatializer](https://github.com/microsoft/spatialaudio-unity).</span><span class="sxs-lookup"><span data-stu-id="c0092-113">This is available from the [Microsoft spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity).</span></span>
  * <span data-ttu-id="c0092-114">Usa una arquitectura de "varios orígenes" de menor costo.</span><span class="sxs-lookup"><span data-stu-id="c0092-114">This uses a lower-cost 'multi-source' architecture.</span></span>
  * <span data-ttu-id="c0092-115">En HoloLens 2, se descarga en un acelerador de hardware.</span><span class="sxs-lookup"><span data-stu-id="c0092-115">On HoloLens 2, this is offloaded to a hardware accelerator.</span></span>

<span data-ttu-id="c0092-116">En el caso de las nuevas aplicaciones, se recomienda *Microsoft Spatializer*.</span><span class="sxs-lookup"><span data-stu-id="c0092-116">For new applications, we recommend the *Microsoft Spatializer*.</span></span>

## <a name="enable-spatialization"></a><span data-ttu-id="c0092-117">Habilitar la espacialización</span><span class="sxs-lookup"><span data-stu-id="c0092-117">Enable spatialization</span></span>

<span data-ttu-id="c0092-118">Use [NuGet para Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) para instalar _Microsoft. SpatialAudio. Spatializer. Unity_ y elija **Microsoft Spatializer** en la configuración de audio del proyecto.</span><span class="sxs-lookup"><span data-stu-id="c0092-118">Use [NuGet for Unity](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest) to install _Microsoft.SpatialAudio.Spatializer.Unity_ and choose **Microsoft Spatializer** in your project's audio settings.</span></span> <span data-ttu-id="c0092-119">A continuación:</span><span class="sxs-lookup"><span data-stu-id="c0092-119">Then:</span></span>
* <span data-ttu-id="c0092-120">Adjuntar un **origen de audio** a un objeto de la jerarquía</span><span class="sxs-lookup"><span data-stu-id="c0092-120">Attach an **Audio Source** to an object in the hierarchy</span></span>
* <span data-ttu-id="c0092-121">Active la casilla **Habilitar la espacialización**</span><span class="sxs-lookup"><span data-stu-id="c0092-121">Check the **Enable spatialization** checkbox</span></span>
* <span data-ttu-id="c0092-122">Mueve el control deslizante de **mezcla espacial** a ' 1 '</span><span class="sxs-lookup"><span data-stu-id="c0092-122">Move the **Spatial Blend** slider to '1'</span></span>
* <span data-ttu-id="c0092-123">Asegúrese de que el audio espacial está habilitado en la estación de trabajo del desarrollador.</span><span class="sxs-lookup"><span data-stu-id="c0092-123">Ensure spatial audio is enabled on your developer workstation.</span></span> <span data-ttu-id="c0092-124">Habilítelo haciendo clic con el botón derecho en el icono de volumen en la barra de tareas y asegurándose de que el sonido espacial esté establecido en un valor distinto de "desactivado".</span><span class="sxs-lookup"><span data-stu-id="c0092-124">Enable it by right-clicking on the volume icon in the task bar and making sure that Spatial Sound is set to something other than "off."</span></span> <span data-ttu-id="c0092-125">Para obtener la mejor representación de lo que escuchará en HoloLens 2, elija **Windows Sonic para auriculares**.</span><span class="sxs-lookup"><span data-stu-id="c0092-125">To get the best representation of what you'll hear on HoloLens 2, choose **Windows Sonic for Headphones**.</span></span>

>[!NOTE]
><span data-ttu-id="c0092-126">Si recibe un error en Unity que le permite cargar el complemento Microsoft. SpatialAudio. Spatializer. Unity porque falta una de sus dependencias, compruebe que dispone de la versión más reciente de [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) instalada en su equipo.</span><span class="sxs-lookup"><span data-stu-id="c0092-126">If you get an error in Unity about not being able to load plugin Microsoft.SpatialAudio.Spatializer.Unity because one of its dependencies is missing, check that you have the latest version of the [Microsoft Visual C++ Redistributable](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) installed on your PC.</span></span>

<span data-ttu-id="c0092-127">Para obtener más información, vea:</span><span class="sxs-lookup"><span data-stu-id="c0092-127">For more details, see:</span></span>
* [<span data-ttu-id="c0092-128">Repositorio de GitHub de Microsoft spatializer</span><span class="sxs-lookup"><span data-stu-id="c0092-128">Microsoft spatializer GitHub repository</span></span>](https://github.com/microsoft/spatialaudio-unity)
* [<span data-ttu-id="c0092-129">Tutorial de spatializer de Microsoft</span><span class="sxs-lookup"><span data-stu-id="c0092-129">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)
* [<span data-ttu-id="c0092-130">Documentación del origen de audio de Unity</span><span class="sxs-lookup"><span data-stu-id="c0092-130">Unity's audio source documentation</span></span>](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [<span data-ttu-id="c0092-131">Documentación de spatializer de Unity</span><span class="sxs-lookup"><span data-stu-id="c0092-131">Unity's spatializer documentation</span></span>](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a><span data-ttu-id="c0092-132">Atenuación basada en distancia</span><span class="sxs-lookup"><span data-stu-id="c0092-132">Distance-based attenuation</span></span>
<span data-ttu-id="c0092-133">La decadencia basada en la distancia predeterminada de Unity tiene una distancia mínima de 1 metro y una distancia máxima de 500 metros, con una rolloff logarítmica.</span><span class="sxs-lookup"><span data-stu-id="c0092-133">Unity's default distance-based decay has a minimum distance of 1 meter and a maximum distance of 500 meters, with a logarithmic rolloff.</span></span> <span data-ttu-id="c0092-134">Es posible que esta configuración funcione para su escenario, o puede que los orígenes se expongan demasiado rápido o demasiado lentamente.</span><span class="sxs-lookup"><span data-stu-id="c0092-134">These settings may work for your scenario, or you may find that sources attenuate too quickly or too slowly.</span></span> <span data-ttu-id="c0092-135">Para obtener más información, vea:</span><span class="sxs-lookup"><span data-stu-id="c0092-135">For more details, see:</span></span>
* <span data-ttu-id="c0092-136">[Diseño sonoro en la realidad mixta](spatial-sound-design.md) para la configuración recomendada.</span><span class="sxs-lookup"><span data-stu-id="c0092-136">[Sound design in mixed reality](spatial-sound-design.md) for recommended settings.</span></span>
* <span data-ttu-id="c0092-137">[Documentación de origen de audio de Unity](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) para obtener instrucciones sobre cómo establecer estas curvas.</span><span class="sxs-lookup"><span data-stu-id="c0092-137">[Unity's audio source documentation](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html) for instructions on setting these curves.</span></span>

## <a name="reverb"></a><span data-ttu-id="c0092-138">Reverbera</span><span class="sxs-lookup"><span data-stu-id="c0092-138">Reverb</span></span>
<span data-ttu-id="c0092-139">De forma predeterminada, el _Spatializer de Microsoft_ deshabilita los efectos posteriores a Spatializer.</span><span class="sxs-lookup"><span data-stu-id="c0092-139">The _Microsoft Spatializer_ disables post-spatializer effects by default.</span></span> <span data-ttu-id="c0092-140">Para habilitar la reverberación y otros efectos para los orígenes espaciales:</span><span class="sxs-lookup"><span data-stu-id="c0092-140">To enable reverb and other effects for spatialized sources:</span></span>
* <span data-ttu-id="c0092-141">Asociar el componente de **nivel de envío del efecto de sala** a cada origen</span><span class="sxs-lookup"><span data-stu-id="c0092-141">Attach the **Room Effect Send Level** component to each source</span></span>
* <span data-ttu-id="c0092-142">Ajuste la curva de nivel de envío de cada origen para controlar la ganancia del audio que se devuelve al gráfico para el procesamiento de efectos</span><span class="sxs-lookup"><span data-stu-id="c0092-142">Adjust the send level curve for each source, to control the gain on the audio sent back to the graph for effects processing</span></span>

<span data-ttu-id="c0092-143">Consulte [el capítulo 5 del tutorial de spatializer](unity-spatial-audio-ch5.md) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="c0092-143">See [Chapter 5 of the spatializer tutorial](unity-spatial-audio-ch5.md) for details.</span></span>

## <a name="unity-spatial-sound-examples"></a><span data-ttu-id="c0092-144">Ejemplos de sonido espacial de Unity</span><span class="sxs-lookup"><span data-stu-id="c0092-144">Unity spatial sound examples</span></span>
<span data-ttu-id="c0092-145">Para ver ejemplos de sonido espacial en Unity, consulte:</span><span class="sxs-lookup"><span data-stu-id="c0092-145">For examples of spatial sound in Unity, see:</span></span>
* [<span data-ttu-id="c0092-146">Demostraciones de MRTK</span><span class="sxs-lookup"><span data-stu-id="c0092-146">MRTK demos</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* <span data-ttu-id="c0092-147">[Proyecto de ejemplo de Microsoft Spatializer](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span><span class="sxs-lookup"><span data-stu-id="c0092-147">The [Microsoft Spatializer sample project](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)</span></span>

## <a name="next-steps"></a><span data-ttu-id="c0092-148">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="c0092-148">Next steps</span></span>
* [<span data-ttu-id="c0092-149">Diseño sonoro en realidad mixta</span><span class="sxs-lookup"><span data-stu-id="c0092-149">Sound design in mixed reality</span></span>](spatial-sound-design.md)
* [<span data-ttu-id="c0092-150">Tutorial de spatializer de Microsoft</span><span class="sxs-lookup"><span data-stu-id="c0092-150">Microsoft's spatializer tutorial</span></span>](unity-spatial-audio-ch1.md)

