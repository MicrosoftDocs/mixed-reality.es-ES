---
title: Audio en realidad mixta
description: El audio en realidad mixta puede aumentar la confianza de los usuarios en las interacciones de la interfaz de usuario y sumergir a los usuarios en la experiencia.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: sonido espacial, sonido envolvente, audio 3D, sonido 3D, audio espacial
ms.openlocfilehash: 1930017903439aee3ac53b6c4be344fdc44c356f
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641116"
---
# <a name="audio-in-mixed-reality"></a><span data-ttu-id="f4a17-104">Audio en realidad mixta</span><span class="sxs-lookup"><span data-stu-id="f4a17-104">Audio in Mixed Reality</span></span>
<span data-ttu-id="f4a17-105">El audio es una parte esencial del diseño y la productividad en la realidad mixta y puede:</span><span class="sxs-lookup"><span data-stu-id="f4a17-105">Audio is an essential part of design and productivity in mixed reality, and can:</span></span>
* <span data-ttu-id="f4a17-106">Aumentar la confianza del usuario en las interacciones basadas en gestos y en voz</span><span class="sxs-lookup"><span data-stu-id="f4a17-106">Increase user confidence in gesture- and voice-based interactions</span></span>
* <span data-ttu-id="f4a17-107">Guiar a los usuarios a pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="f4a17-107">Guide users to next steps</span></span>
* <span data-ttu-id="f4a17-108">Combinar objetos virtuales de forma eficaz con el mundo real</span><span class="sxs-lookup"><span data-stu-id="f4a17-108">Effectively combine virtual objects with the real world</span></span>

<span data-ttu-id="f4a17-109">El seguimiento de los cabezales de baja latencia de los auriculares de realidad mixta, incluido HoloLens, permite el uso de la espacialización basada en HRTF de alta calidad.</span><span class="sxs-lookup"><span data-stu-id="f4a17-109">The low-latency head tracking of mixed reality headsets, including HoloLens, enables the use of high quality HRTF-based spatialization.</span></span> <span data-ttu-id="f4a17-110">La espacialización del audio en la aplicación puede:</span><span class="sxs-lookup"><span data-stu-id="f4a17-110">Spatializing audio in your application can:</span></span>
* <span data-ttu-id="f4a17-111">Llamar la atención sobre los elementos visuales</span><span class="sxs-lookup"><span data-stu-id="f4a17-111">Call attention to visual elements</span></span>
* <span data-ttu-id="f4a17-112">Ayudar a los usuarios a mantener el conocimiento de su entorno del mundo real</span><span class="sxs-lookup"><span data-stu-id="f4a17-112">Help users maintain awareness of their real-world surroundings</span></span>

<span data-ttu-id="f4a17-113">La adición de acústicas conecta con mayor profundidad los hologramas al mundo mixto y puede proporcionar indicaciones sobre el entorno y el estado del objeto.</span><span class="sxs-lookup"><span data-stu-id="f4a17-113">Adding acoustics more deeply connects holograms to the mixed world, and can provide cues about the environment and object state.</span></span>

<span data-ttu-id="f4a17-114">Para obtener ejemplos más detallados de diseño con audio, consulte [diseño de sonido](spatial-sound-design.md).</span><span class="sxs-lookup"><span data-stu-id="f4a17-114">For more detailed examples of design using audio, see [sound design](spatial-sound-design.md).</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a><span data-ttu-id="f4a17-115">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="f4a17-115">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="f4a17-116"><strong>Ofrecen</strong></span><span class="sxs-lookup"><span data-stu-id="f4a17-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="f4a17-117"><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="f4a17-117"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="f4a17-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="f4a17-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="f4a17-119"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="f4a17-119"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f4a17-120">Espacialización</span><span class="sxs-lookup"><span data-stu-id="f4a17-120">Spatialization</span></span></td>
        <td><span data-ttu-id="f4a17-121">✔️</span><span class="sxs-lookup"><span data-stu-id="f4a17-121">✔️</span></span></td>
        <td><span data-ttu-id="f4a17-122">✔️</span><span class="sxs-lookup"><span data-stu-id="f4a17-122">✔️</span></span></td>
        <td><span data-ttu-id="f4a17-123">✔️</span><span class="sxs-lookup"><span data-stu-id="f4a17-123">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="f4a17-124">Aceleración de hardware de la espacialización</span><span class="sxs-lookup"><span data-stu-id="f4a17-124">Spatialization hardware acceleration</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="f4a17-125">✔️</span><span class="sxs-lookup"><span data-stu-id="f4a17-125">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="using-sounds-in-mixed-reality"></a><span data-ttu-id="f4a17-126">Usar sonidos en realidad mixta</span><span class="sxs-lookup"><span data-stu-id="f4a17-126">Using sounds in mixed reality</span></span>
<span data-ttu-id="f4a17-127">El [uso de sonidos en la realidad mixta](spatial-sound-design.md) puede requerir un enfoque diferente que en las aplicaciones táctiles y de teclado y de mouse.</span><span class="sxs-lookup"><span data-stu-id="f4a17-127">[Using sounds in mixed reality](spatial-sound-design.md) can require a different approach than in touch and keyboard-and-mouse applications.</span></span> <span data-ttu-id="f4a17-128">Entre las decisiones clave de diseño sólido se incluyen los sonidos que se deben espaciales y las interacciones que se van a sonify.</span><span class="sxs-lookup"><span data-stu-id="f4a17-128">Key sound design decisions include which sounds to spatialize and which interactions to sonify.</span></span> <span data-ttu-id="f4a17-129">Estas decisiones pueden tener un efecto fuerte en la confianza de los usuarios, la productividad y la curva de aprendizaje.</span><span class="sxs-lookup"><span data-stu-id="f4a17-129">These decisions can have a strong effect on user confidence, productivity, and learning curve.</span></span>

### <a name="case-studies"></a><span data-ttu-id="f4a17-130">Casos prácticos</span><span class="sxs-lookup"><span data-stu-id="f4a17-130">Case studies</span></span>
<span data-ttu-id="f4a17-131">HoloTour virtualmente lleva a los usuarios a sitios turísticos e históricos en todo el mundo.</span><span class="sxs-lookup"><span data-stu-id="f4a17-131">HoloTour virtually takes users to tourist and historical sites around the world.</span></span> <span data-ttu-id="f4a17-132">En el siguiente caso práctico se describe el diseño de sonido de HoloTour: [diseño de sonido para HoloTour](case-study-spatial-sound-design-for-holotour.md).</span><span class="sxs-lookup"><span data-stu-id="f4a17-132">The following case study describes the sound design for HoloTour: [Sound design for HoloTour](case-study-spatial-sound-design-for-holotour.md).</span></span> <span data-ttu-id="f4a17-133">Se usó un micrófono y una configuración de representación especiales para capturar los espacios de asunto.</span><span class="sxs-lookup"><span data-stu-id="f4a17-133">A special microphone and rendering setup were used to capture the subject spaces.</span></span>

<span data-ttu-id="f4a17-134">RoboRaid es un Reactivador de alta energía para HoloLens.</span><span class="sxs-lookup"><span data-stu-id="f4a17-134">RoboRaid is a high-energy shooter for HoloLens.</span></span> <span data-ttu-id="f4a17-135">En el caso práctico siguiente se describen las opciones de diseño que se han realizado para garantizar que el audio espacial se ha usado para obtener el máximo efecto drástico: [diseño de sonido para RoboRaid](case-study-using-spatial-sound-in-roboraid.md).</span><span class="sxs-lookup"><span data-stu-id="f4a17-135">The following case study describes the design choices made to ensure spatial audio was used to fullest dramatic effect: [Sound design for RoboRaid](case-study-using-spatial-sound-in-roboraid.md).</span></span>

## <a name="spatialization"></a><span data-ttu-id="f4a17-136">Espacialización</span><span class="sxs-lookup"><span data-stu-id="f4a17-136">Spatialization</span></span>
<span data-ttu-id="f4a17-137">La espacialización es el componente direccional del audio espacial.</span><span class="sxs-lookup"><span data-stu-id="f4a17-137">Spatialization is the directional component of spatial audio.</span></span> <span data-ttu-id="f4a17-138">Cuando se usa una instalación de 7,1 Home Theater, la espacialización es tan sencilla como la panorámica entre altavoces de alta intensidad.</span><span class="sxs-lookup"><span data-stu-id="f4a17-138">When using a 7.1 home theater setup, spatialization is as simple as panning between loud speakers.</span></span> <span data-ttu-id="f4a17-139">Pero con los auriculares en realidad mixta es fundamental usar una tecnología basada en HRTF para obtener precisión y comodidad.</span><span class="sxs-lookup"><span data-stu-id="f4a17-139">But with headphones in mixed reality it's essential to use an HRTF-based technology for accuracy and comfort.</span></span> <span data-ttu-id="f4a17-140">Windows ofrece la espacialización basada en HRTF y esta compatibilidad se acelera mediante hardware en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="f4a17-140">Windows offers HRTF-based spatialization, and this support is hardware-accelerated on HoloLens 2.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a><span data-ttu-id="f4a17-141">¿Se debe Spatial?</span><span class="sxs-lookup"><span data-stu-id="f4a17-141">Should I spatialize?</span></span>
<span data-ttu-id="f4a17-142">Muchos sonidos en aplicaciones de realidad mixta se benefician de la espacialización, lo que saca un sonido del encabezado del agente de escucha y lo coloca en el mundo.</span><span class="sxs-lookup"><span data-stu-id="f4a17-142">Many sounds in mixed reality applications benefit from spatialization, which takes a sound out of the listener's head and places it in the world.</span></span> <span data-ttu-id="f4a17-143">Consulte [diseño de sonido espacial](spatial-sound-design.md) para obtener sugerencias sobre los usos más efectivos de la espacialización en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f4a17-143">Refer to [Spatial Sound Design](spatial-sound-design.md) for suggestions on the most effective uses of spatialization in your application.</span></span>

### <a name="spatializer-personalization"></a><span data-ttu-id="f4a17-144">Personalización de Spatializer</span><span class="sxs-lookup"><span data-stu-id="f4a17-144">Spatializer personalization</span></span>
<span data-ttu-id="f4a17-145">HRTFs manipulan las diferencias de nivel y fase entre los oídos en el espectro de frecuencias.</span><span class="sxs-lookup"><span data-stu-id="f4a17-145">HRTFs manipulate the level and phase differences between ears across the frequency spectrum.</span></span> <span data-ttu-id="f4a17-146">Se basan en modelos físicos y medidas de las formas de cabeza humana, torso y EAR (pinnae).</span><span class="sxs-lookup"><span data-stu-id="f4a17-146">They're based on physical models and measurements of human head, torso, and ear shapes (pinnae).</span></span> <span data-ttu-id="f4a17-147">Nuestro cerebro responde a estas diferencias para dar lugar a una percepción de la dirección en sonido.</span><span class="sxs-lookup"><span data-stu-id="f4a17-147">Our brains respond to these differences to give rise to a perception of direction in sound.</span></span> 

<span data-ttu-id="f4a17-148">Cada persona tiene una forma de lengüeta única, el tamaño del cabezal y la posición del oído, por lo que los mejores HRTFs son los que se ajustan a usted.</span><span class="sxs-lookup"><span data-stu-id="f4a17-148">Every individual has a unique ear shape, head size, and ear position, so the best HRTFs are those that conform to you.</span></span> <span data-ttu-id="f4a17-149">HoloLens aumenta la precisión de la espacialización mediante el uso de la distancia entre pupilary (IPD) del casco que se muestra para ajustar el HRTFs para el tamaño de la cabeza.</span><span class="sxs-lookup"><span data-stu-id="f4a17-149">HoloLens increases spatialization accuracy by using your inter-pupilary distance (IPD) from the headset displays to adjust the HRTFs for your head size.</span></span>

### <a name="spatializer-platform-support"></a><span data-ttu-id="f4a17-150">Compatibilidad con la plataforma Spatializer</span><span class="sxs-lookup"><span data-stu-id="f4a17-150">Spatializer platform support</span></span>
<span data-ttu-id="f4a17-151">Windows ofrece la espacialización, incluido HRTFs, a través de la [API de ISpatialAudioClient](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound).</span><span class="sxs-lookup"><span data-stu-id="f4a17-151">Windows offers spatialization, including HRTFs, via the [ISpatialAudioClient API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound).</span></span> <span data-ttu-id="f4a17-152">Esta API expone la aceleración de hardware de HoloLens 2 HRTF a las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="f4a17-152">This API exposes the HoloLens 2 HRTF hardware acceleration to applications.</span></span>

### <a name="spatializer-middleware-support"></a><span data-ttu-id="f4a17-153">Compatibilidad con middleware de Spatializer</span><span class="sxs-lookup"><span data-stu-id="f4a17-153">Spatializer middleware support</span></span>
<span data-ttu-id="f4a17-154">La compatibilidad con Windows ' HRTFs está disponible para algunos motores de audio de terceros:</span><span class="sxs-lookup"><span data-stu-id="f4a17-154">Support for Windows' HRTFs is available for some 3rd-party audio engines:</span></span>
* <span data-ttu-id="f4a17-155">Un complemento del [motor de audio de Unity](spatial-sound-in-unity.md) llama a la HRTF XAPO</span><span class="sxs-lookup"><span data-stu-id="f4a17-155">A [Unity audio engine](spatial-sound-in-unity.md) plugin calls the HRTF XAPO</span></span>
* <span data-ttu-id="f4a17-156">Un [complemento de Wwise Audio Engine](https://www.audiokinetic.com/products/plug-ins/msspatial/) llama a la API ISpatialAudioClient</span><span class="sxs-lookup"><span data-stu-id="f4a17-156">A [Wwise audio engine plugin](https://www.audiokinetic.com/products/plug-ins/msspatial/) calls the ISpatialAudioClient API</span></span>

## <a name="acoustics"></a><span data-ttu-id="f4a17-157">Acústicas</span><span class="sxs-lookup"><span data-stu-id="f4a17-157">Acoustics</span></span>
<span data-ttu-id="f4a17-158">El audio espacial puede ser más que una dirección.</span><span class="sxs-lookup"><span data-stu-id="f4a17-158">Spatial audio can be about more than direction.</span></span> <span data-ttu-id="f4a17-159">Otras dimensiones, como oclusión, obstrucción, reverberación, agrupación en el portal y modelos de origen, se conocen colectivamente como ' acústicas '.</span><span class="sxs-lookup"><span data-stu-id="f4a17-159">Other dimensions, including occlusion, obstruction, reverb, portalling, and source modelling, are collectively referred to as 'acoustics'.</span></span> <span data-ttu-id="f4a17-160">Sin acústica, los sonidos espaciales carecen de una distancia percibida.</span><span class="sxs-lookup"><span data-stu-id="f4a17-160">Without acoustics, spatialized sounds lack a perceived distance.</span></span>

<span data-ttu-id="f4a17-161">El tratamiento acústico puede oscilar entre simple y muy complejo.</span><span class="sxs-lookup"><span data-stu-id="f4a17-161">Acoustics treatment can range from simple to very complex.</span></span> <span data-ttu-id="f4a17-162">Mediante el uso de una reverberación simple, como la que se admite en cualquier motor de audio, se pueden introducir sonidos espaciales en el entorno que rodea al agente de escucha.</span><span class="sxs-lookup"><span data-stu-id="f4a17-162">By using a simple reverb, such as that supported by any audio engine, you can push spatialized sounds out into the environment surrounding the listener.</span></span> <span data-ttu-id="f4a17-163">Los sistemas acústicos, como los [acústicos del proyecto](https://aka.ms/acoustics), ofrecen un tratamiento acústico más completo y atractivo.</span><span class="sxs-lookup"><span data-stu-id="f4a17-163">Richer and more compelling acoustics treatment is available from acoustics systems such as [Project Acoustics](https://aka.ms/acoustics).</span></span> <span data-ttu-id="f4a17-164">La acústica del proyecto puede modelar el efecto de las paredes, las puertas y otras geometrías de la escena en un sonido, y es una opción eficaz para los casos en los que se conoce la geometría de la escena correspondiente en tiempo de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="f4a17-164">Project Acoustics can model the effect of walls, doors, and other scene geometry on a sound, and is an effective option for cases where the relevant scene geometry is known at development time.</span></span>

