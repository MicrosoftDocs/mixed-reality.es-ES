---
title: Mirada
description: Miramos la primera forma de entrada y es una forma principal de establecer como destino dentro de la realidad mixta.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Realidad mixta, mira, interacción, diseño
ms.openlocfilehash: 7e65d26d3e9edabbd01d35a887ffc8622a3c6337
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414367"
---
# <a name="gaze"></a><span data-ttu-id="d7fd6-104">Mirada</span><span class="sxs-lookup"><span data-stu-id="d7fd6-104">Gaze</span></span>

<span data-ttu-id="d7fd6-105">**Miramos** la primera forma de entrada y es una forma principal de establecer como destino dentro de la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="d7fd6-105">**Gaze** is the first form of input and is a primary form of targeting within mixed reality.</span></span> <span data-ttu-id="d7fd6-106">Le indica dónde está buscando el usuario en el mundo y le permite determinar su intención.</span><span class="sxs-lookup"><span data-stu-id="d7fd6-106">Gaze tells you where the user is looking in the world and lets you determine their intent.</span></span> <span data-ttu-id="d7fd6-107">En el mundo real, normalmente observará un objeto con el que desea interactuar.</span><span class="sxs-lookup"><span data-stu-id="d7fd6-107">In the real world, you'll typically look at an object that you intend to interact with.</span></span> <span data-ttu-id="d7fd6-108">Este es el mismo con miras.</span><span class="sxs-lookup"><span data-stu-id="d7fd6-108">This is the same with gaze.</span></span>

<span data-ttu-id="d7fd6-109">Los auriculares de realidad mixta usan la posición y la orientación del encabezado del usuario para determinar su vector de miras hacia abajo.</span><span class="sxs-lookup"><span data-stu-id="d7fd6-109">Mixed reality headsets use the position and orientation of your user's head to determine their head gaze vector.</span></span> <span data-ttu-id="d7fd6-110">Puede considerar este vector como un puntero láser directo directamente desde los ojos del usuario.</span><span class="sxs-lookup"><span data-stu-id="d7fd6-110">You can think of this vector as a laser pointer straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="d7fd6-111">A medida que el usuario mira el salón, la aplicación puede crear una intersección con este rayo, tanto con sus propios hologramas como con la malla de [asignación espacial](spatial-mapping.md) , para determinar qué objeto virtual o del mundo real puede estar mirando el usuario.</span><span class="sxs-lookup"><span data-stu-id="d7fd6-111">As the user looks around the room, your application can intersect this ray, both with its own holograms and with the [spatial mapping](spatial-mapping.md) mesh to determine what virtual or real-world object your user may be looking at.</span></span>

<span data-ttu-id="d7fd6-112">En HoloLens 2, las interacciones pueden tener como destino las interacciones de la cabeza del usuario, el ojo o la intersección de la mano.</span><span class="sxs-lookup"><span data-stu-id="d7fd6-112">On HoloLens 2, interactions can be targeted by either the user's head gaze, eye gaze or through near or far hand interactions.</span></span>
<span data-ttu-id="d7fd6-113">En HoloLens (1ª generación), las interacciones generalmente deben derivar sus destinatarios del encabezado del usuario, en lugar de intentar representarlas o interactuar directamente en la ubicación de la mano.</span><span class="sxs-lookup"><span data-stu-id="d7fd6-113">On HoloLens (1st gen), interactions should generally derive their targeting from the user's head gaze, rather than trying to render or interact at the hand's location directly.</span></span> <span data-ttu-id="d7fd6-114">Una vez que se ha iniciado una interacción, se pueden usar movimientos relativos de la mano para controlar el [gesto](gestures.md), al igual que con la [manipulación o](gestures.md#composite-gestures) el gesto de navegación.</span><span class="sxs-lookup"><span data-stu-id="d7fd6-114">Once an interaction has started, relative motions of the hand may be used to control the [gesture](gestures.md), as with the [manipulation or navigation](gestures.md#composite-gestures) gesture.</span></span> <span data-ttu-id="d7fd6-115">Con auriculares envolventes, puede dirigirse a través de [los controladores de movimiento](motion-controllers.md)de mira hacia abajo o con capacidad de puntero.</span><span class="sxs-lookup"><span data-stu-id="d7fd6-115">With immersive headsets, you can target using either head gaze or pointing-capable [motion controllers](motion-controllers.md).</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a><span data-ttu-id="d7fd6-116">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="d7fd6-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d7fd6-117"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="d7fd6-117"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="d7fd6-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="d7fd6-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="d7fd6-119"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="d7fd6-119"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="d7fd6-120"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="d7fd6-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d7fd6-121">Mira hacia abajo</span><span class="sxs-lookup"><span data-stu-id="d7fd6-121">Head gaze</span></span></td>
        <td><span data-ttu-id="d7fd6-122">✔️</span><span class="sxs-lookup"><span data-stu-id="d7fd6-122">✔️</span></span></td>
        <td><span data-ttu-id="d7fd6-123">✔️</span><span class="sxs-lookup"><span data-stu-id="d7fd6-123">✔️</span></span></td>
        <td><span data-ttu-id="d7fd6-124">✔️</span><span class="sxs-lookup"><span data-stu-id="d7fd6-124">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d7fd6-125">Ojo mirado</span><span class="sxs-lookup"><span data-stu-id="d7fd6-125">Eye gaze</span></span></td>
        <td><span data-ttu-id="d7fd6-126">❌</span><span class="sxs-lookup"><span data-stu-id="d7fd6-126">❌</span></span></td>
        <td><span data-ttu-id="d7fd6-127">✔️</span><span class="sxs-lookup"><span data-stu-id="d7fd6-127">✔️</span></span></td>
        <td><span data-ttu-id="d7fd6-128">❌</span><span class="sxs-lookup"><span data-stu-id="d7fd6-128">❌</span></span></td>
    </tr>
</table>

> [!NOTE]
> <span data-ttu-id="d7fd6-129">[Próximamente](index.md#news-and-notes) se ofrecerá orientación específica para HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d7fd6-129">More guidance specific to HoloLens 2 [coming soon](index.md#news-and-notes).</span></span>


## <a name="uses-of-gaze"></a><span data-ttu-id="d7fd6-130">Usos de fijamente</span><span class="sxs-lookup"><span data-stu-id="d7fd6-130">Uses of gaze</span></span>

<span data-ttu-id="d7fd6-131">Como desarrollador de realidad mixta, puede hacer muchas cosas con miras hacia arriba o hacia abajo:</span><span class="sxs-lookup"><span data-stu-id="d7fd6-131">As a mixed reality developer, you can do a lot with head or eye gaze:</span></span>
* <span data-ttu-id="d7fd6-132">La aplicación puede intersectar con los hologramas de la escena para determinar dónde está la atención del usuario.</span><span class="sxs-lookup"><span data-stu-id="d7fd6-132">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is.</span></span>
* <span data-ttu-id="d7fd6-133">La aplicación puede tener como destino gestos y pulsaciones del controlador en función de la mirada del usuario, lo que permite que el usuario seleccione, active, grabe, desplace o interactúe con sus hologramas.</span><span class="sxs-lookup"><span data-stu-id="d7fd6-133">Your app can target gestures and controller presses based on the user's gaze, letting the user select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="d7fd6-134">La aplicación puede permitir que el usuario coloque hologramas en superficies del mundo real, intersectando su rayo con la malla de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="d7fd6-134">Your app can let the user place holograms on real-world surfaces, by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="d7fd6-135">La aplicación puede saber si el usuario *no* está buscando la dirección de un objeto importante, lo que puede conducir a que la aplicación proporcione indicaciones visuales y de audio para activar dicho objeto.</span><span class="sxs-lookup"><span data-stu-id="d7fd6-135">Your app can know when the user is *not* looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

## <a name="cursor"></a><span data-ttu-id="d7fd6-136">Cursor</span><span class="sxs-lookup"><span data-stu-id="d7fd6-136">Cursor</span></span>

<span data-ttu-id="d7fd6-137">En el caso de la mirada, la mayoría de las aplicaciones deben usar un [cursor](cursors.md) (u otra indicación visual o de auditoría) para dar a la confianza del usuario en qué está a punto de interactuar.</span><span class="sxs-lookup"><span data-stu-id="d7fd6-137">For head gaze, most apps should use a [cursor](cursors.md) (or other auditory/visual indication) to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="d7fd6-138">Normalmente, este cursor se coloca en el mundo en el que su rayo de miras hacia abajo intersecta primero con un objeto, que puede ser un holograma o una superficie del mundo real.</span><span class="sxs-lookup"><span data-stu-id="d7fd6-138">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span>

<span data-ttu-id="d7fd6-139">![Un cursor visual de ejemplo para mostrar la mirada](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="d7fd6-139">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
<span data-ttu-id="d7fd6-140">*Un cursor visual de ejemplo para mostrar la mirada*</span><span class="sxs-lookup"><span data-stu-id="d7fd6-140">*An example visual cursor to show gaze*</span></span>

<span data-ttu-id="d7fd6-141">En general, se recomienda *no* mostrar un cursor, ya que esto puede resultar más rápido y molesto para el usuario.</span><span class="sxs-lookup"><span data-stu-id="d7fd6-141">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="d7fd6-142">En su lugar, resalte los destinos visuales de forma sutilmente o use un cursor de ojo muy débil para proporcionar confianza sobre lo que el usuario está a punto de interactuar.</span><span class="sxs-lookup"><span data-stu-id="d7fd6-142">Instead subtly highlight visual targets or use a very faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="d7fd6-143">Para obtener más información, consulte nuestra [Guía de diseño para la entrada basada en ojo](eye-tracking.md) en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="d7fd6-143">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>

## <a name="giving-action-to-the-users-gaze"></a><span data-ttu-id="d7fd6-144">Realizar una acción en la mirada del usuario</span><span class="sxs-lookup"><span data-stu-id="d7fd6-144">Giving action to the user's gaze</span></span>

<span data-ttu-id="d7fd6-145">Una vez que el usuario ha dirigido un holograma o un objeto del mundo real con su mirada, el siguiente paso es tomar medidas en ese objeto.</span><span class="sxs-lookup"><span data-stu-id="d7fd6-145">Once the user has targeted a hologram or real-world object using their gaze, their next step is to take action on that object.</span></span> <span data-ttu-id="d7fd6-146">Las principales formas de que un usuario tome medidas a través de [gestos](gestures.md), [controladores de movimiento](motion-controllers.md) y [voz](voice-input.md).</span><span class="sxs-lookup"><span data-stu-id="d7fd6-146">The primary ways for a user to take action are through [gestures](gestures.md), [motion controllers](motion-controllers.md) and [voice](voice-input.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d7fd6-147">Vea también</span><span class="sxs-lookup"><span data-stu-id="d7fd6-147">See also</span></span>
* [<span data-ttu-id="d7fd6-148">MR Input 210: Mira hacia abajo</span><span class="sxs-lookup"><span data-stu-id="d7fd6-148">MR Input 210: Head gaze</span></span>](holograms-210.md)
* [<span data-ttu-id="d7fd6-149">Control con la cabeza y los ojos de DirectX</span><span class="sxs-lookup"><span data-stu-id="d7fd6-149">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="d7fd6-150">Mira hacia abajo en Unity</span><span class="sxs-lookup"><span data-stu-id="d7fd6-150">Head gaze in Unity</span></span>](gaze-in-unity.md)
* [<span data-ttu-id="d7fd6-151">Miras a la vista de HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="d7fd6-151">Eye-gaze on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="d7fd6-152">Mira fijamente en Unity con el kit de herramientas de realidad mixta</span><span class="sxs-lookup"><span data-stu-id="d7fd6-152">Eye gaze in Unity using Mixed Reality Toolkit</span></span>](https://aka.ms/mrtk-eyes)
