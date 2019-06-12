---
title: Mirada
description: Mirada es el primer formulario de entrada y un formulario principal de destino es en realidad mixta.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Mixed reality, mirada, interacción, diseñar
ms.openlocfilehash: e0c1a925f6faeb37ec35e511cef36f9c06672c8a
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829741"
---
# <a name="gaze"></a><span data-ttu-id="3dc62-104">Mirada</span><span class="sxs-lookup"><span data-stu-id="3dc62-104">Gaze</span></span>

<span data-ttu-id="3dc62-105">**Observación** es el primer formulario de entrada y es un formulario principal de destino es en realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="3dc62-105">**Gaze** is the first form of input and is a primary form of targeting within mixed reality.</span></span> <span data-ttu-id="3dc62-106">Mirada indica que el usuario está buscando en el mundo y permite determinar su intención.</span><span class="sxs-lookup"><span data-stu-id="3dc62-106">Gaze tells you where the user is looking in the world and lets you determine their intent.</span></span> <span data-ttu-id="3dc62-107">En el mundo real, normalmente obtendrá información en un objeto que se va a interactuar con.</span><span class="sxs-lookup"><span data-stu-id="3dc62-107">In the real world, you'll typically look at an object that you intend to interact with.</span></span> <span data-ttu-id="3dc62-108">Esto es lo mismo con la mirada.</span><span class="sxs-lookup"><span data-stu-id="3dc62-108">This is the same with gaze.</span></span>

<span data-ttu-id="3dc62-109">Auriculares de realidad mixta utilizar la posición y orientación de head del usuario para determinar su vector mirada principal.</span><span class="sxs-lookup"><span data-stu-id="3dc62-109">Mixed reality headsets use the position and orientation of your user's head to determine their head gaze vector.</span></span> <span data-ttu-id="3dc62-110">De este vector se puede considerar como un puntero láser recta desde directamente entre la vista del usuario.</span><span class="sxs-lookup"><span data-stu-id="3dc62-110">You can think of this vector as a laser pointer straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="3dc62-111">Como el usuario busca en torno a la sala de reuniones, la aplicación puede forman una intersección con este ray, con su propio hologramas tanto con el [asignación espacial](spatial-mapping.md) malla para determinar qué objeto reales o virtual que esté mirando el usuario.</span><span class="sxs-lookup"><span data-stu-id="3dc62-111">As the user looks around the room, your application can intersect this ray, both with its own holograms and with the [spatial mapping](spatial-mapping.md) mesh to determine what virtual or real-world object your user may be looking at.</span></span>

<span data-ttu-id="3dc62-112">En 2 HoloLens, interacciones mirada de principal del usuario, mirada ojo pueden tener como destino o a través de cerca o mucho entregar las interacciones.</span><span class="sxs-lookup"><span data-stu-id="3dc62-112">On HoloLens 2, interactions can be targeted by either the user's head gaze, eye gaze or through near or far hand interactions.</span></span>
<span data-ttu-id="3dc62-113">En HoloLens (gen 1), por lo general deben derivar las interacciones de sus destinatarios de mirada principal del usuario, en lugar de intentar para representar o interactuar directamente en la ubicación de la mano.</span><span class="sxs-lookup"><span data-stu-id="3dc62-113">On HoloLens (1st gen), interactions should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="3dc62-114">Una vez que se ha iniciado una interacción, movimientos relativos de la mano pueden utilizarse para controlar la [gesto](gestures.md), igual que con el [manipulación o navegación](gestures.md#composite-gestures) gesto.</span><span class="sxs-lookup"><span data-stu-id="3dc62-114">Once an interaction has started, relative motions of the hand may be used to control the [gesture](gestures.md), as with the [manipulation or navigation](gestures.md#composite-gestures) gesture.</span></span> <span data-ttu-id="3dc62-115">Con inmersivos, puede tener como destino con una mirada principal o señalando capaz [motion controladores](motion-controllers.md).</span><span class="sxs-lookup"><span data-stu-id="3dc62-115">With immersive headsets, you can target using either head gaze or pointing-capable [motion controllers](motion-controllers.md).</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a><span data-ttu-id="3dc62-116">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="3dc62-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="3dc62-117"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="3dc62-117"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="3dc62-118"><a href="hololens-hardware-details.md"><strong>HoloLens (gen 1)</strong></a></span><span class="sxs-lookup"><span data-stu-id="3dc62-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="3dc62-119"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="3dc62-119"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="3dc62-120"><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="3dc62-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="3dc62-121">Mirada HEAD</span><span class="sxs-lookup"><span data-stu-id="3dc62-121">Head gaze</span></span></td>
        <td><span data-ttu-id="3dc62-122">✔️</span><span class="sxs-lookup"><span data-stu-id="3dc62-122">✔️</span></span></td>
        <td><span data-ttu-id="3dc62-123">✔️</span><span class="sxs-lookup"><span data-stu-id="3dc62-123">✔️</span></span></td>
        <td><span data-ttu-id="3dc62-124">✔️</span><span class="sxs-lookup"><span data-stu-id="3dc62-124">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="3dc62-125">Mirada ojo</span><span class="sxs-lookup"><span data-stu-id="3dc62-125">Eye gaze</span></span></td>
        <td><span data-ttu-id="3dc62-126">❌</span><span class="sxs-lookup"><span data-stu-id="3dc62-126">❌</span></span></td>
        <td><span data-ttu-id="3dc62-127">✔️</span><span class="sxs-lookup"><span data-stu-id="3dc62-127">✔️</span></span></td>
        <td><span data-ttu-id="3dc62-128">❌</span><span class="sxs-lookup"><span data-stu-id="3dc62-128">❌</span></span></td>
    </tr>
</table>

> [!NOTE]
> <span data-ttu-id="3dc62-129">Obtener información más específica de HoloLens 2 [próximamente](index.md#news-and-notes).</span><span class="sxs-lookup"><span data-stu-id="3dc62-129">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>


## <a name="uses-of-gaze"></a><span data-ttu-id="3dc62-130">Usos de mirada</span><span class="sxs-lookup"><span data-stu-id="3dc62-130">Uses of gaze</span></span>

<span data-ttu-id="3dc62-131">Como desarrollador de realidad mixta, puede hacer muchas cosas con mirada head u ojos:</span><span class="sxs-lookup"><span data-stu-id="3dc62-131">As a mixed reality developer, you can do a lot with head or eye gaze:</span></span>
* <span data-ttu-id="3dc62-132">La aplicación puede intersectar mirada con el hologramas en su escena para determinar dónde se encuentra la atención del usuario.</span><span class="sxs-lookup"><span data-stu-id="3dc62-132">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is.</span></span>
* <span data-ttu-id="3dc62-133">La aplicación puede tener como destino los gestos y pulsaciones de controlador según mirada del usuario, que permite que el usuario seleccione, activar, tomar, desplácese o interactuar con sus hologramas de otro modo.</span><span class="sxs-lookup"><span data-stu-id="3dc62-133">Your app can target gestures and controller presses based on the user's gaze, letting the user select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="3dc62-134">La aplicación puede permitir que el usuario coloque hologramas en superficies del mundo real, mediante la intersección de su ray mirada a la malla de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="3dc62-134">Your app can let the user place holograms on real-world surfaces, by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="3dc62-135">La aplicación puede saber cuando el usuario es *no* buscando en la dirección de un objeto importante, lo que puede provocar que la aplicación para proporcionar indicaciones visuales y de audio para activar hacia ese objeto.</span><span class="sxs-lookup"><span data-stu-id="3dc62-135">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

## <a name="cursor"></a><span data-ttu-id="3dc62-136">Cursor</span><span class="sxs-lookup"><span data-stu-id="3dc62-136">Cursor</span></span>

<span data-ttu-id="3dc62-137">Para la mirada principal, debe usar la mayoría de las aplicaciones una [cursor](cursors.md) (u otra indicación visual de auditorio /) para proporcionar a la confianza de los usuarios en lo que va a interactuar con.</span><span class="sxs-lookup"><span data-stu-id="3dc62-137">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="3dc62-138">Normalmente, se coloque este cursor en el mundo donde su ray mirada principal primero forma una intersección con un objeto, que puede ser un holograma o una superficie del mundo real.</span><span class="sxs-lookup"><span data-stu-id="3dc62-138">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span>

<span data-ttu-id="3dc62-139">![Un cursor visual de ejemplo para mostrar la mirada](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="3dc62-139">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
<span data-ttu-id="3dc62-140">*Un cursor visual de ejemplo para mostrar la mirada*</span><span class="sxs-lookup"><span data-stu-id="3dc62-140">*An example visual cursor to show gaze*</span></span>

<span data-ttu-id="3dc62-141">Para la mirada ojo, generalmente recomendamos *no* para mostrar un cursor, como esto puede volverse rápidamente que distraen y molesta para el usuario.</span><span class="sxs-lookup"><span data-stu-id="3dc62-141">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="3dc62-142">En su lugar sutilmente resaltar destinos visuales o utilizar un cursor de ojos muy débil para proporcionar confiabilidad sobre cuál es el usuario a interactuar con.</span><span class="sxs-lookup"><span data-stu-id="3dc62-142">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="3dc62-143">Para obtener más información, consulte nuestra [instrucciones de diseño para la entrada de ojo](eye-tracking.md) en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="3dc62-143">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>

## <a name="giving-action-to-the-users-gaze"></a><span data-ttu-id="3dc62-144">Acción de la concesión en mirada del usuario</span><span class="sxs-lookup"><span data-stu-id="3dc62-144">Giving action to the user's gaze</span></span>

<span data-ttu-id="3dc62-145">Una vez que el usuario destina un holograma o un objeto del mundo real mediante su mirada, su siguiente paso es realizar la acción en ese objeto.</span><span class="sxs-lookup"><span data-stu-id="3dc62-145">Once the user has targeted a hologram or real-world object using their gaze, their next step is to take action on that object.</span></span> <span data-ttu-id="3dc62-146">Las formas principales de un usuario para tomar medidas son a través de [gestos](gestures.md), [controladores de movimiento](motion-controllers.md) y [voz](voice-input.md).</span><span class="sxs-lookup"><span data-stu-id="3dc62-146">The primary ways for a user to take action are through [gestures](gestures.md), [motion controllers](motion-controllers.md) and [voice](voice-input.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3dc62-147">Vea también</span><span class="sxs-lookup"><span data-stu-id="3dc62-147">See also</span></span>
* [<span data-ttu-id="3dc62-148">MR Input 210: Mirada HEAD</span><span class="sxs-lookup"><span data-stu-id="3dc62-148">MR Input 210: Head gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="3dc62-149">Control con la cabeza y los ojos de DirectX</span><span class="sxs-lookup"><span data-stu-id="3dc62-149">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="3dc62-150">Mirada HEAD en Unity</span><span class="sxs-lookup"><span data-stu-id="3dc62-150">Head gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="3dc62-151">Ojo de seguimiento en 2 HoloLens</span><span class="sxs-lookup"><span data-stu-id="3dc62-151">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="3dc62-152">Efecto de ojos mirada en Unity mediante el Kit de herramientas de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="3dc62-152">Eye gaze in Unity using Mixed Reality Toolkit</span></span>](https://aka.ms/mrtk-eyes)
