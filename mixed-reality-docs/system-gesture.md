---
title: Gestos del sistema
description: Gesto del sistema para llamar al menú Inicio.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Realidad mixta, gestos, interacción, diseño
ms.openlocfilehash: ba543ffe0802d0b95cc539fb0e73c0b4e51fc186
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926727"
---
# <a name="system-gesture"></a><span data-ttu-id="1e2b9-104">Gestos del sistema</span><span class="sxs-lookup"><span data-stu-id="1e2b9-104">System gesture</span></span>

<span data-ttu-id="1e2b9-105">El gesto del sistema es un gesto de mano que se usa para invocar el menú Inicio.</span><span class="sxs-lookup"><span data-stu-id="1e2b9-105">The system gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="1e2b9-106">Es el equivalente de presionar la tecla Windows en el teclado, el botón Xbox en un controlador Xbox o el botón Windows en el controlador de movimiento de auriculares envolvente.</span><span class="sxs-lookup"><span data-stu-id="1e2b9-106">It is the equivalent of pressing the Windows key on the keyboard, the Xbox button on an Xbox controller, or the Windows button on the immersive headset motion controller.</span></span> <span data-ttu-id="1e2b9-107">Es importante comprender qué gestos están reservados para el sistema en cada dispositivo de realidad mixta para evitar conflictos al diseñar las interacciones.</span><span class="sxs-lookup"><span data-stu-id="1e2b9-107">It's important to understand which gestures are reserved for the system on each Mixed Reality device to prevent conflicts when designing your interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="1e2b9-108">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="1e2b9-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="1e2b9-109"><strong>Ofrecen</strong></span><span class="sxs-lookup"><span data-stu-id="1e2b9-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="1e2b9-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="1e2b9-110"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="1e2b9-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="1e2b9-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="1e2b9-112"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="1e2b9-112"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="1e2b9-113">Flores</span><span class="sxs-lookup"><span data-stu-id="1e2b9-113">Bloom</span></span></td>
        <td><span data-ttu-id="1e2b9-114">✔️</span><span class="sxs-lookup"><span data-stu-id="1e2b9-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="1e2b9-115">Botón de muñeca</span><span class="sxs-lookup"><span data-stu-id="1e2b9-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="1e2b9-116">✔️</span><span class="sxs-lookup"><span data-stu-id="1e2b9-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="1e2b9-117">Mira fijamente y contacto con Palm up</span><span class="sxs-lookup"><span data-stu-id="1e2b9-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="1e2b9-118">✔️</span><span class="sxs-lookup"><span data-stu-id="1e2b9-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="1e2b9-119">Flores</span><span class="sxs-lookup"><span data-stu-id="1e2b9-119">Bloom</span></span>
<span data-ttu-id="1e2b9-120">Para abrir el menú Inicio en HoloLens (1ª generación), hemos diseñado "floración", que es un gesto simbólico que imita el Blossom de la flor.</span><span class="sxs-lookup"><span data-stu-id="1e2b9-120">To bring up the start menu in HoloLens (1st gen), we designed “Bloom”, which is a symbolic gesture mimicking the flower blossom.</span></span> <span data-ttu-id="1e2b9-121">Es distintivo para la interacción con Surefooted, fácil de realizar y rápida recuperación.</span><span class="sxs-lookup"><span data-stu-id="1e2b9-121">It's distinctive for surefooted interaction, easy to perform, and quick to recall.</span></span> <span data-ttu-id="1e2b9-122">Para llevar a cabo el gesto de floración en HoloLens (1ª generación), mantenga su mano con su mano y cerca de la mano y, a continuación, abra la mano mediante la distribución de los dedos.</span><span class="sxs-lookup"><span data-stu-id="1e2b9-122">To do the bloom gesture on HoloLens (1st gen), hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="1e2b9-123">](images/bloom-close.png) de cierre de ![floración</span><span class="sxs-lookup"><span data-stu-id="1e2b9-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="1e2b9-124">**Paso 1: Palm con las manos**</span><span class="sxs-lookup"><span data-stu-id="1e2b9-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="1e2b9-125">![abierto con floración](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="1e2b9-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="1e2b9-126">**Paso 2: Palm up con la mano**</span><span class="sxs-lookup"><span data-stu-id="1e2b9-126">**Step 2: Palm up with fingertips spread**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="wrist-button"></a><span data-ttu-id="1e2b9-127">Botón de muñeca</span><span class="sxs-lookup"><span data-stu-id="1e2b9-127">Wrist button</span></span>
<span data-ttu-id="1e2b9-128">En HoloLens 2, reemplazamos el gesto de floración con un botón de muñeca virtual que permite más interacciones de instinctual que no requieren ninguna enseñanza adicional.</span><span class="sxs-lookup"><span data-stu-id="1e2b9-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button that allows for more instinctual interactions that require no additional teaching.</span></span> <span data-ttu-id="1e2b9-129">Al mostrar a los usuarios el botón de la muñeca, pueden ponerse en contacto de forma intuitiva y presionarlo con la mano.</span><span class="sxs-lookup"><span data-stu-id="1e2b9-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="1e2b9-130">![botón de muñeca listo](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="1e2b9-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="1e2b9-131">**Paso 1: Palm para mostrar el botón de muñeca**</span><span class="sxs-lookup"><span data-stu-id="1e2b9-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="1e2b9-132">![presionar el botón de muñeca](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="1e2b9-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="1e2b9-133">**Paso 2: presionar el botón de muñeca**</span><span class="sxs-lookup"><span data-stu-id="1e2b9-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="eye-gaze-and-palm-up-pinch"></a><span data-ttu-id="1e2b9-134">Mira fijamente y contacto con Palm up</span><span class="sxs-lookup"><span data-stu-id="1e2b9-134">Eye-gaze and palm up pinch</span></span>
<span data-ttu-id="1e2b9-135">También hemos diseñado una solución de una sola mano para facilitar el acceso en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1e2b9-135">We have also designed a one-handed solution for ease of access in HoloLens 2.</span></span> <span data-ttu-id="1e2b9-136">Este gesto requiere que los usuarios miren el botón de la muñeca y, a continuación, usar la misma mano para realizar un toque de mano con el dedo y el dedo del índice.</span><span class="sxs-lookup"><span data-stu-id="1e2b9-136">This gesture requires users to eye gaze at the wrist button, then use the same hand to perform a palm up pinch using their thumb and index finger.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="1e2b9-137">![botón de muñeca listo](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="1e2b9-137">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="1e2b9-138">**Paso 1: Palm para mostrar el botón de muñeca**</span><span class="sxs-lookup"><span data-stu-id="1e2b9-138">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="1e2b9-139">![botón de la muñeca](images/wrist-button-pinch.png)</span><span class="sxs-lookup"><span data-stu-id="1e2b9-139">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="1e2b9-140">**Paso: mire fijamente en el botón y luego en Pinch**</span><span class="sxs-lookup"><span data-stu-id="1e2b9-140">**Step: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="1e2b9-141">Consulta también</span><span class="sxs-lookup"><span data-stu-id="1e2b9-141">See also</span></span>

* [<span data-ttu-id="1e2b9-142">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="1e2b9-142">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="1e2b9-143">Control con los ojos</span><span class="sxs-lookup"><span data-stu-id="1e2b9-143">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="1e2b9-144">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="1e2b9-144">Voice input</span></span>](voice-input.md)
