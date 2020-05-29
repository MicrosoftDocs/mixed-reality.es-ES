---
title: Movimiento de inicio
description: Iniciar el gesto para llamar al menú Inicio.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Realidad mixta, gestos, interacción, diseño
ms.openlocfilehash: 84088156d0c9cdacc421985b922d5e9370f6a87e
ms.sourcegitcommit: fd606e87e3c4785d3ca2a26632be3bb580e39afb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2020
ms.locfileid: "84152511"
---
# <a name="start-gesture"></a><span data-ttu-id="3cd95-104">Movimiento de inicio</span><span class="sxs-lookup"><span data-stu-id="3cd95-104">Start gesture</span></span>

<span data-ttu-id="3cd95-105">El gesto de inicio es un gesto de mano que se usa para invocar el menú Inicio.</span><span class="sxs-lookup"><span data-stu-id="3cd95-105">The Start gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="3cd95-106">Es el equivalente de presionar la tecla Windows en el teclado, el botón Xbox en un controlador Xbox o el botón Windows en el controlador de movimiento de auriculares envolvente.</span><span class="sxs-lookup"><span data-stu-id="3cd95-106">It is the equivalent of pressing the Windows key on the keyboard, the Xbox button on an Xbox controller, or the Windows button on the immersive headset motion controller.</span></span> <span data-ttu-id="3cd95-107">Es importante comprender qué gestos están reservados para el sistema en cada dispositivo de realidad mixta para evitar conflictos al diseñar las interacciones.</span><span class="sxs-lookup"><span data-stu-id="3cd95-107">It's important to understand which gestures are reserved for the system on each Mixed Reality device to prevent conflicts when designing your interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="3cd95-108">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="3cd95-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="3cd95-109"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="3cd95-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="3cd95-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="3cd95-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="3cd95-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="3cd95-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="3cd95-112"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="3cd95-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="3cd95-113">Eclosión</span><span class="sxs-lookup"><span data-stu-id="3cd95-113">Bloom</span></span></td>
        <td><span data-ttu-id="3cd95-114">✔️</span><span class="sxs-lookup"><span data-stu-id="3cd95-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="3cd95-115">Botón de muñeca</span><span class="sxs-lookup"><span data-stu-id="3cd95-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="3cd95-116">✔️</span><span class="sxs-lookup"><span data-stu-id="3cd95-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="3cd95-117">Mira fijamente y contacto con Palm up</span><span class="sxs-lookup"><span data-stu-id="3cd95-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="3cd95-118">✔️</span><span class="sxs-lookup"><span data-stu-id="3cd95-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="3cd95-119">Eclosión</span><span class="sxs-lookup"><span data-stu-id="3cd95-119">Bloom</span></span>
<span data-ttu-id="3cd95-120">Para abrir el menú Inicio en HoloLens (1ª generación), hemos diseñado "floración", que es un gesto simbólico que imita el Blossom de la flor.</span><span class="sxs-lookup"><span data-stu-id="3cd95-120">To bring up the start menu in HoloLens (1st gen), we designed “Bloom”, which is a symbolic gesture mimicking the flower blossom.</span></span> <span data-ttu-id="3cd95-121">Es distintivo para la interacción con Surefooted, fácil de realizar y rápida recuperación.</span><span class="sxs-lookup"><span data-stu-id="3cd95-121">It's distinctive for surefooted interaction, easy to perform, and quick to recall.</span></span> <span data-ttu-id="3cd95-122">Para llevar a cabo el gesto de floración en HoloLens (1ª generación), mantenga su mano con su mano y cerca de la mano y, a continuación, abra la mano mediante la distribución de los dedos.</span><span class="sxs-lookup"><span data-stu-id="3cd95-122">To do the bloom gesture on HoloLens (1st gen), hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="3cd95-123">![Cierre del floración](images/bloom-close.png)</span><span class="sxs-lookup"><span data-stu-id="3cd95-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="3cd95-124">**Paso 1: Palm con las manos**</span><span class="sxs-lookup"><span data-stu-id="3cd95-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3cd95-125">![Floración abierto](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="3cd95-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="3cd95-126">**Paso 2: Palm up con la mano**</span><span class="sxs-lookup"><span data-stu-id="3cd95-126">**Step 2: Palm up with fingertips spread**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a><span data-ttu-id="3cd95-127">Movimiento de inicio</span><span class="sxs-lookup"><span data-stu-id="3cd95-127">Start gesture</span></span>
<span data-ttu-id="3cd95-128">En HoloLens 2, reemplazamos el gesto de floración con un botón de muñeca virtual que permite más interacciones de instinctual que no requieren ninguna enseñanza adicional.</span><span class="sxs-lookup"><span data-stu-id="3cd95-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button that allows for more instinctual interactions that require no additional teaching.</span></span> <span data-ttu-id="3cd95-129">Al mostrar a los usuarios el botón de la muñeca, pueden ponerse en contacto de forma intuitiva y presionarlo con la mano.</span><span class="sxs-lookup"><span data-stu-id="3cd95-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="3cd95-130">![Botón de pulsera listo](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="3cd95-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="3cd95-131">**Paso 1: Palm para mostrar el botón de muñeca**</span><span class="sxs-lookup"><span data-stu-id="3cd95-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3cd95-132">![Presionar el botón de muñeca](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="3cd95-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="3cd95-133">**Paso 2: presionar el botón de muñeca**</span><span class="sxs-lookup"><span data-stu-id="3cd95-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="one-handed-start-gesture"></a><span data-ttu-id="3cd95-134">Gesto de inicio con una sola mano</span><span class="sxs-lookup"><span data-stu-id="3cd95-134">One-handed Start gesture</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3cd95-135">Para que funcione el gesto de inicio con una sola mano:</span><span class="sxs-lookup"><span data-stu-id="3cd95-135">For the one-handed Start gesture to work:</span></span>
>
> 1. <span data-ttu-id="3cd95-136">Debe actualizar a la actualización de noviembre de 2019 (compilación 18363,1039) o posterior.</span><span class="sxs-lookup"><span data-stu-id="3cd95-136">You must update to the November 2019 update (build 18363.1039) or later.</span></span>
> 1. <span data-ttu-id="3cd95-137">Los ojos deben calibrarse en el dispositivo para que el seguimiento ocular funcione correctamente.</span><span class="sxs-lookup"><span data-stu-id="3cd95-137">Your eyes must be calibrated on the device so that eye tracking functions correctly.</span></span> <span data-ttu-id="3cd95-138">Si no ve puntos en órbita alrededor del icono de inicio al mirarlo, los ojos no se calibrarán en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3cd95-138">If you do not see orbiting dots around the Start icon when you look at it, your eyes are not calibrated on the device.</span></span>

<span data-ttu-id="3cd95-139">También puede realizar el gesto de inicio con una sola mano.</span><span class="sxs-lookup"><span data-stu-id="3cd95-139">You can also perform the Start gesture with only one hand.</span></span> <span data-ttu-id="3cd95-140">Para ello, mantenga su mano con la palma y mire el **icono de inicio** en su muñeca interna.</span><span class="sxs-lookup"><span data-stu-id="3cd95-140">To do this, hold out your hand with your palm facing you and look at the **Start icon** on your inner wrist.</span></span> <span data-ttu-id="3cd95-141">**Mientras mantiene el ojo del icono**, acerque el dedo y el dedo del índice.</span><span class="sxs-lookup"><span data-stu-id="3cd95-141">**While keeping your eye on the icon**, pinch your thumb and index finger together.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="3cd95-142">![Botón de pulsera listo](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="3cd95-142">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="3cd95-143">**Paso 1: Palm para mostrar el botón de muñeca**</span><span class="sxs-lookup"><span data-stu-id="3cd95-143">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3cd95-144">![Botón de muñeca](images/wrist-button-pinch.png)</span><span class="sxs-lookup"><span data-stu-id="3cd95-144">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="3cd95-145">**Paso 2: mira fijamente en el botón y luego en Pinch**</span><span class="sxs-lookup"><span data-stu-id="3cd95-145">**Step 2: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="3cd95-146">Consulte también</span><span class="sxs-lookup"><span data-stu-id="3cd95-146">See also</span></span>

* [<span data-ttu-id="3cd95-147">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="3cd95-147">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="3cd95-148">Control con los ojos</span><span class="sxs-lookup"><span data-stu-id="3cd95-148">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="3cd95-149">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="3cd95-149">Voice input</span></span>](voice-input.md)
