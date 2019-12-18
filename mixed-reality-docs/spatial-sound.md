---
title: Audio en realidad mixta
description: El audio en realidad mixta puede aumentar la confianza de los usuarios en las interacciones de la interfaz de usuario y sumergir a los usuarios en la experiencia.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: sonido espacial, sonido envolvente, audio 3D, sonido 3D, audio espacial
ms.openlocfilehash: b939433daf80a95a11bc0e1ac2ffd75dfe0cf299
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181985"
---
# <a name="audio-in-mixed-reality"></a><span data-ttu-id="fdde3-104">Audio en realidad mixta</span><span class="sxs-lookup"><span data-stu-id="fdde3-104">Audio in mixed reality</span></span>
<span data-ttu-id="fdde3-105">El audio es una parte esencial del diseño y la productividad en la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="fdde3-105">Audio is an essential part of design and productivity in mixed reality.</span></span> <span data-ttu-id="fdde3-106">El sonido puede:</span><span class="sxs-lookup"><span data-stu-id="fdde3-106">Sound can:</span></span>
* <span data-ttu-id="fdde3-107">Aumentar la confianza del usuario en las interacciones de gestos y voz.</span><span class="sxs-lookup"><span data-stu-id="fdde3-107">Increase user confidence in gesture and voice interactions.</span></span>
* <span data-ttu-id="fdde3-108">Guiar a los usuarios a pasos siguientes.</span><span class="sxs-lookup"><span data-stu-id="fdde3-108">Guide users to next steps.</span></span>
* <span data-ttu-id="fdde3-109">Combinar objetos virtuales de forma eficaz con el mundo real.</span><span class="sxs-lookup"><span data-stu-id="fdde3-109">Effectively combine virtual objects with the real world.</span></span>

<span data-ttu-id="fdde3-110">El seguimiento de los cabezales de baja latencia de los auriculares de realidad mixta, incluido HoloLens, admite la espacialización basada en HRTF de alta calidad.</span><span class="sxs-lookup"><span data-stu-id="fdde3-110">The low-latency head tracking of mixed reality headsets, including HoloLens, supports high-quality HRTF-based spatialization.</span></span> <span data-ttu-id="fdde3-111">Puede espacialar el audio de la aplicación para:</span><span class="sxs-lookup"><span data-stu-id="fdde3-111">You can spatialize audio in your application to:</span></span>
* <span data-ttu-id="fdde3-112">Llame la atención a los elementos visuales.</span><span class="sxs-lookup"><span data-stu-id="fdde3-112">Call attention to visual elements.</span></span>
* <span data-ttu-id="fdde3-113">Ayudar a los usuarios a mantener el conocimiento de su entorno real.</span><span class="sxs-lookup"><span data-stu-id="fdde3-113">Help users maintain awareness of their real-world surroundings.</span></span>

<span data-ttu-id="fdde3-114">Las acústicas conectan con mayor profundidad los hologramas al mundo de la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="fdde3-114">Acoustics more deeply connect holograms to the mixed-reality world.</span></span> <span data-ttu-id="fdde3-115">Proporciona indicaciones sobre el entorno y el estado de los objetos.</span><span class="sxs-lookup"><span data-stu-id="fdde3-115">It provides cues about the environment and object state.</span></span>

<span data-ttu-id="fdde3-116">Vea ejemplos detallados [de diseño que usa audio](spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="fdde3-116">See detailed [examples of design that uses audio](spatial-sound-design.md).</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a><span data-ttu-id="fdde3-117">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="fdde3-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="fdde3-118"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="fdde3-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="fdde3-119"><a href="hololens-hardware-details.md"><strong>HoloLens (primera generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="fdde3-119"><a href="hololens-hardware-details.md"><strong>HoloLens (first gen)</strong></a></span></span></td>
        <td><span data-ttu-id="fdde3-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="fdde3-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="fdde3-121"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="fdde3-121"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="fdde3-122">Espacialización</span><span class="sxs-lookup"><span data-stu-id="fdde3-122">Spatialization</span></span></td>
        <td><span data-ttu-id="fdde3-123">✔️</span><span class="sxs-lookup"><span data-stu-id="fdde3-123">✔️</span></span></td>
        <td><span data-ttu-id="fdde3-124">✔️</span><span class="sxs-lookup"><span data-stu-id="fdde3-124">✔️</span></span></td>
        <td><span data-ttu-id="fdde3-125">✔️</span><span class="sxs-lookup"><span data-stu-id="fdde3-125">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="fdde3-126">Aceleración de hardware de la espacialización</span><span class="sxs-lookup"><span data-stu-id="fdde3-126">Spatialization hardware acceleration</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="fdde3-127">✔️</span><span class="sxs-lookup"><span data-stu-id="fdde3-127">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="use-of-sounds-in-mixed-reality"></a><span data-ttu-id="fdde3-128">Uso de sonidos en realidad mixta</span><span class="sxs-lookup"><span data-stu-id="fdde3-128">Use of sounds in mixed reality</span></span>
<span data-ttu-id="fdde3-129">El [uso de sonidos en la realidad mixta](spatial-sound-design.md) requiere un enfoque diferente que en aplicaciones táctiles y de teclado y de mouse.</span><span class="sxs-lookup"><span data-stu-id="fdde3-129">[Use of sounds in mixed reality](spatial-sound-design.md) requires a different approach than in touch and keyboard-and-mouse applications.</span></span> <span data-ttu-id="fdde3-130">Entre las decisiones clave de diseño sólido se incluyen los sonidos que se deben espaciales y las interacciones que se van a sonify.</span><span class="sxs-lookup"><span data-stu-id="fdde3-130">Key sound design decisions include which sounds to spatialize and which interactions to sonify.</span></span> <span data-ttu-id="fdde3-131">Estas decisiones afectan seriamente a la confianza de los usuarios, la productividad y la curva de aprendizaje.</span><span class="sxs-lookup"><span data-stu-id="fdde3-131">These decisions strongly effect user confidence, productivity, and learning curve.</span></span>

### <a name="case-studies"></a><span data-ttu-id="fdde3-132">Casos prácticos</span><span class="sxs-lookup"><span data-stu-id="fdde3-132">Case studies</span></span>
<span data-ttu-id="fdde3-133">HoloTour virtualmente lleva a los usuarios a sitios turísticos e históricos en todo el mundo.</span><span class="sxs-lookup"><span data-stu-id="fdde3-133">HoloTour virtually takes users to tourist and historical sites around the world.</span></span> <span data-ttu-id="fdde3-134">Vea el caso práctico [de diseño de sonido para HoloTour](case-study-spatial-sound-design-for-holotour.md) .</span><span class="sxs-lookup"><span data-stu-id="fdde3-134">See the [Sound design for HoloTour](case-study-spatial-sound-design-for-holotour.md) case study.</span></span> <span data-ttu-id="fdde3-135">Se usó un micrófono y una configuración de representación especiales para capturar los espacios de asunto.</span><span class="sxs-lookup"><span data-stu-id="fdde3-135">A special microphone and rendering setup were used to capture the subject spaces.</span></span>

<span data-ttu-id="fdde3-136">RoboRaid es un Reactivador de alta energía para HoloLens.</span><span class="sxs-lookup"><span data-stu-id="fdde3-136">RoboRaid is a high-energy shooter for HoloLens.</span></span> <span data-ttu-id="fdde3-137">En el caso práctico [de diseño de RoboRaid](case-study-using-spatial-sound-in-roboraid.md) , se describen las opciones de diseño que se realizaron para garantizar el uso del audio espacial al efecto más drástico.</span><span class="sxs-lookup"><span data-stu-id="fdde3-137">The [Sound design for RoboRaid](case-study-using-spatial-sound-in-roboraid.md) case study describes the design choices that were made to ensure spatial audio was used to the fullest dramatic effect.</span></span>

## <a name="spatialization"></a><span data-ttu-id="fdde3-138">Espacialización</span><span class="sxs-lookup"><span data-stu-id="fdde3-138">Spatialization</span></span>
<span data-ttu-id="fdde3-139">La espacialización es el componente direccional del audio espacial.</span><span class="sxs-lookup"><span data-stu-id="fdde3-139">Spatialization is the directional component of spatial audio.</span></span> <span data-ttu-id="fdde3-140">En el caso de una instalación de 7,1 Home Theater, la espacialización es tan sencilla como la panorámica entre los altavoces.</span><span class="sxs-lookup"><span data-stu-id="fdde3-140">For a 7.1 home theater setup, spatialization is as simple as panning between loudspeakers.</span></span> <span data-ttu-id="fdde3-141">Sin embargo, en el caso de los auriculares mixtos, es fundamental usar una tecnología basada en HRTF para obtener precisión y comodidad.</span><span class="sxs-lookup"><span data-stu-id="fdde3-141">But for headphones in mixed reality, it's essential to use an HRTF-based technology for accuracy and comfort.</span></span> <span data-ttu-id="fdde3-142">Windows ofrece la espacialización basada en HRTF y esta compatibilidad se acelera mediante hardware en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="fdde3-142">Windows offers HRTF-based spatialization, and this support is hardware-accelerated on HoloLens 2.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a><span data-ttu-id="fdde3-143">¿Se debe Spatial?</span><span class="sxs-lookup"><span data-stu-id="fdde3-143">Should I spatialize?</span></span>
<span data-ttu-id="fdde3-144">La espacialización puede mejorar muchos sonidos en aplicaciones de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="fdde3-144">Spatialization can improve many sounds in mixed-reality applications.</span></span> <span data-ttu-id="fdde3-145">La espacialización saca un sonido del encabezado del agente de escucha y lo coloca en el mundo.</span><span class="sxs-lookup"><span data-stu-id="fdde3-145">Spatialization takes a sound out of the listener's head and places it in the world.</span></span> <span data-ttu-id="fdde3-146">Para obtener sugerencias sobre el uso eficaz de la espacialización en la aplicación, consulte [diseño de sonido espacial](spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="fdde3-146">For suggestions on effective use of spatialization in your application, see [Spatial sound design](spatial-sound-design.md).</span></span>

### <a name="spatializer-personalization"></a><span data-ttu-id="fdde3-147">Personalización de Spatializer</span><span class="sxs-lookup"><span data-stu-id="fdde3-147">Spatializer personalization</span></span>
<span data-ttu-id="fdde3-148">HRTFs manipulan las diferencias de nivel y fase entre los oídos en el espectro de frecuencias.</span><span class="sxs-lookup"><span data-stu-id="fdde3-148">HRTFs manipulate the level and phase differences between ears across the frequency spectrum.</span></span> <span data-ttu-id="fdde3-149">Se basan en modelos físicos y medidas de las formas de cabeza humana, torso y EAR (pinnae).</span><span class="sxs-lookup"><span data-stu-id="fdde3-149">They're based on physical models and measurements of human head, torso, and ear shapes (pinnae).</span></span> <span data-ttu-id="fdde3-150">Nuestro cerebro responde a estas diferencias para proporcionar una dirección perceptible en el sonido.</span><span class="sxs-lookup"><span data-stu-id="fdde3-150">Our brains respond to these differences to provide perceived direction in sound.</span></span>

<span data-ttu-id="fdde3-151">Cada persona tiene una forma de EAR única, el tamaño del cabezal y la posición del oído.</span><span class="sxs-lookup"><span data-stu-id="fdde3-151">Every individual has a unique ear shape, head size, and ear position.</span></span> <span data-ttu-id="fdde3-152">Por lo tanto, el mejor HRTFs es su utilidad.</span><span class="sxs-lookup"><span data-stu-id="fdde3-152">So the best HRTFs conform to you.</span></span> <span data-ttu-id="fdde3-153">Para aumentar la precisión de la espacialización, HoloLens usa la distancia entre pupilary (IPD) del casco que se muestra para ajustar el HRTFs para el tamaño de la cabeza.</span><span class="sxs-lookup"><span data-stu-id="fdde3-153">To increase spatialization accuracy, HoloLens uses your inter-pupilary distance (IPD) from the headset displays to adjust the HRTFs for your head size.</span></span>

### <a name="spatializer-platform-support"></a><span data-ttu-id="fdde3-154">Compatibilidad con la plataforma Spatializer</span><span class="sxs-lookup"><span data-stu-id="fdde3-154">Spatializer platform support</span></span>
<span data-ttu-id="fdde3-155">Windows ofrece la espacialización, incluido HRTFs, a través de la [API de ISpatialAudioClient](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound).</span><span class="sxs-lookup"><span data-stu-id="fdde3-155">Windows offers spatialization, including HRTFs, via the [ISpatialAudioClient API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound).</span></span> <span data-ttu-id="fdde3-156">Esta API expone la aceleración de hardware de HoloLens 2 HRTF a las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="fdde3-156">This API exposes the HoloLens 2 HRTF hardware acceleration to applications.</span></span>

### <a name="spatializer-middleware-support"></a><span data-ttu-id="fdde3-157">Compatibilidad con middleware de Spatializer</span><span class="sxs-lookup"><span data-stu-id="fdde3-157">Spatializer middleware support</span></span>
<span data-ttu-id="fdde3-158">La compatibilidad con Windows ' HRTFs está disponible para los siguientes motores de audio de terceros.</span><span class="sxs-lookup"><span data-stu-id="fdde3-158">Support for Windows' HRTFs is available for the following third-party audio engines.</span></span>
* <span data-ttu-id="fdde3-159">Un [complemento de motor de audio de Unity](spatial-sound-in-unity.md)</span><span class="sxs-lookup"><span data-stu-id="fdde3-159">A [Unity audio engine plugin](spatial-sound-in-unity.md)</span></span>
* <span data-ttu-id="fdde3-160">Un [complemento de Wwise Audio Engine](https://www.audiokinetic.com/products/plug-ins/msspatial/)</span><span class="sxs-lookup"><span data-stu-id="fdde3-160">A [Wwise audio engine plugin](https://www.audiokinetic.com/products/plug-ins/msspatial/)</span></span>

## <a name="acoustics"></a><span data-ttu-id="fdde3-161">Acústicas</span><span class="sxs-lookup"><span data-stu-id="fdde3-161">Acoustics</span></span>
<span data-ttu-id="fdde3-162">El audio espacial está sobre más que la dirección.</span><span class="sxs-lookup"><span data-stu-id="fdde3-162">Spatial audio is about more than direction.</span></span> <span data-ttu-id="fdde3-163">Otras dimensiones incluyen las oclusión, los obstáculos, la reverberación, el portal y el modelado de origen.</span><span class="sxs-lookup"><span data-stu-id="fdde3-163">Other dimensions include occlusion, obstruction, reverb, portalling, and source modeling.</span></span> <span data-ttu-id="fdde3-164">Colectivamente, estas dimensiones se denominan *acústicas*.</span><span class="sxs-lookup"><span data-stu-id="fdde3-164">Collectively these dimensions are referred to as *acoustics*.</span></span> <span data-ttu-id="fdde3-165">Sin acústica, los sonidos espaciales carecen de distancia aparente.</span><span class="sxs-lookup"><span data-stu-id="fdde3-165">Without acoustics, spatialized sounds lack perceived distance.</span></span>

<span data-ttu-id="fdde3-166">Los tratamientos acústicos van desde simple a muy complejo.</span><span class="sxs-lookup"><span data-stu-id="fdde3-166">Acoustics treatments range from simple to very complex.</span></span> <span data-ttu-id="fdde3-167">Puede usar una reverberación simple compatible con cualquier motor de audio para enviar sonidos espaciales en el entorno del agente de escucha.</span><span class="sxs-lookup"><span data-stu-id="fdde3-167">You can use a simple reverb that's supported by any audio engine to push spatialized sounds into the environment of the listener.</span></span> <span data-ttu-id="fdde3-168">Los sistemas acústicos, como los [acústicos del proyecto](https://aka.ms/acoustics) , proporcionan un tratamiento acústico más rico y atractivo.</span><span class="sxs-lookup"><span data-stu-id="fdde3-168">Acoustics systems such as [Project Acoustics](https://aka.ms/acoustics)  provide richer and more compelling acoustics treatment.</span></span> <span data-ttu-id="fdde3-169">Los sonidos acústicos del proyecto pueden modelar el efecto de las paredes, las puertas y otras geometrías de la escena en un sonido.</span><span class="sxs-lookup"><span data-stu-id="fdde3-169">Project Acoustics can model the effect of walls, doors, and other scene geometry on a sound.</span></span> <span data-ttu-id="fdde3-170">Es una opción eficaz para los casos en los que la geometría de la escena pertinente se conoce en tiempo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="fdde3-170">It's an effective option for cases where the relevant scene geometry is known at development time.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fdde3-171">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="fdde3-171">Next steps</span></span>
- [<span data-ttu-id="fdde3-172">Sonido espacial en Unity</span><span class="sxs-lookup"><span data-stu-id="fdde3-172">Spatial sound in Unity</span></span>](spatial-sound-in-unity.md)
- [<span data-ttu-id="fdde3-173">Cómo usar sonido en aplicaciones de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="fdde3-173">How to use sound in mixed-reality applications</span></span>](spatial-sound-design.md)
