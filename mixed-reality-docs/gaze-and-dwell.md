---
title: Mira fijamente y viviendas
description: Información general sobre el modelo de entrada de mira y disponibilidad (ojo)
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Realidad mixta, mirada, permanencia, interacción, diseño, seguimiento ocular, seguimiento de encabezado
ms.openlocfilehash: d87406d0b2695cd86c40f27cb132af54ed525b25
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435357"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="cf29c-104">Mira fijamente y viviendas</span><span class="sxs-lookup"><span data-stu-id="cf29c-104">Gaze and dwell</span></span>

<span data-ttu-id="cf29c-105">Si tienes las manos ocupadas con herramientas y piezas, hacer gestos puede ser engorroso o imposible.</span><span class="sxs-lookup"><span data-stu-id="cf29c-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="cf29c-106">Los comandos de voz también pueden ser poco confiables en determinados contextos, por ejemplo, en condiciones excesivamente altas.</span><span class="sxs-lookup"><span data-stu-id="cf29c-106">Voice commands may also be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="cf29c-107">La mirada y la vivienda ofrecen un mecanismo familiar y fácil de usar para los directivos de trabajo y las manos libres de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cf29c-107">Gaze and dwell offers a familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="cf29c-108">Además, la mirada y la permanencia son una gran reserva que es independiente de las interferencias de ruido o las restricciones de silencio en el entorno operativo.</span><span class="sxs-lookup"><span data-stu-id="cf29c-108">Additionally, gaze and dwell is a great fallback which is independent of noise interference or silence constraints in the operating environment.</span></span>
<span data-ttu-id="cf29c-109">Se distinguen dos variantes de _miradas y_de la vivienda: [miran hacia la cabeza y la vivienda](gaze-and-dwell-head.md) , y [miran](gaze-and-dwell-eyes.md)y se superponen.</span><span class="sxs-lookup"><span data-stu-id="cf29c-109">We distinguish two variants of _gaze and dwell_: [Head-gaze and dwell](gaze-and-dwell-head.md) and [Eye-gaze and dwell](gaze-and-dwell-eyes.md).</span></span>

## <a name="scenarios"></a><span data-ttu-id="cf29c-110">Escenarios</span><span class="sxs-lookup"><span data-stu-id="cf29c-110">Scenarios</span></span>

<span data-ttu-id="cf29c-111">Miran y colaboran en escenarios en los que las manos de una persona están ocupados con otras tareas y la voz no es 100% confiable o disponible debido a restricciones ambientales o sociales.</span><span class="sxs-lookup"><span data-stu-id="cf29c-111">Gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or available due to environmental or social constraints.</span></span> <span data-ttu-id="cf29c-112">Un buen ejemplo sería el de una persona que lleva un dispositivo HoloLens para ver superpuesta información de referencia mientras repara el motor de un automóvil.</span><span class="sxs-lookup"><span data-stu-id="cf29c-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="cf29c-113">Puede tener ocupadas las manos con herramientas o usarlas para sostenerse al reclinarse sobre el compartimento del motor.</span><span class="sxs-lookup"><span data-stu-id="cf29c-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="cf29c-114">En la zona del garaje hay mucho ruido, con los constantes golpes y zumbidos de las herramientas, lo que dificulta el uso de comandos de voz.</span><span class="sxs-lookup"><span data-stu-id="cf29c-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="cf29c-115">La mirada y la vivienda permiten a la persona que usa HoloLens navegar por confianza su material de referencia sin interrumpir su flujo de trabajo.</span><span class="sxs-lookup"><span data-stu-id="cf29c-115">Gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="cf29c-116">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="cf29c-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="cf29c-117"><strong>Modelo de entrada</strong></span><span class="sxs-lookup"><span data-stu-id="cf29c-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="cf29c-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="cf29c-118"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="cf29c-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="cf29c-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="cf29c-120"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="cf29c-120"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="cf29c-121">Mirada con la cabeza y permanencia</span><span class="sxs-lookup"><span data-stu-id="cf29c-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="cf29c-122">✔️ Se recomienda</span><span class="sxs-lookup"><span data-stu-id="cf29c-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="cf29c-123">✔️ Se recomienda</span><span class="sxs-lookup"><span data-stu-id="cf29c-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="cf29c-124">✔️ Se recomienda</span><span class="sxs-lookup"><span data-stu-id="cf29c-124">✔️ Recommended</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="cf29c-125">Ojo y viviendas</span><span class="sxs-lookup"><span data-stu-id="cf29c-125">Eye-gaze and dwell</span></span></td>
        <td><span data-ttu-id="cf29c-126">❌ no disponible</span><span class="sxs-lookup"><span data-stu-id="cf29c-126">❌ Not available</span></span></td>
        <td><span data-ttu-id="cf29c-127">✔️ Se recomienda</span><span class="sxs-lookup"><span data-stu-id="cf29c-127">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="cf29c-128">❌ no disponible</span><span class="sxs-lookup"><span data-stu-id="cf29c-128">❌ Not available</span></span></td>
    </tr>
</table>


<br>

---
 
 ## <a name="see-also"></a><span data-ttu-id="cf29c-129">Consulta también</span><span class="sxs-lookup"><span data-stu-id="cf29c-129">See also</span></span>
* [<span data-ttu-id="cf29c-130">Interacción basada en ojos</span><span class="sxs-lookup"><span data-stu-id="cf29c-130">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="cf29c-131">Seguimiento ocular en HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="cf29c-131">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="cf29c-132">Miras y confirmaciones</span><span class="sxs-lookup"><span data-stu-id="cf29c-132">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="cf29c-133">Manipulación práctica directa</span><span class="sxs-lookup"><span data-stu-id="cf29c-133">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="cf29c-134">Gestos prácticos</span><span class="sxs-lookup"><span data-stu-id="cf29c-134">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="cf29c-135">Manos y confirmación</span><span class="sxs-lookup"><span data-stu-id="cf29c-135">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="cf29c-136">Interacciones instintivas</span><span class="sxs-lookup"><span data-stu-id="cf29c-136">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="cf29c-137">Entrada de voz</span><span class="sxs-lookup"><span data-stu-id="cf29c-137">Voice input</span></span>](voice-input.md)
