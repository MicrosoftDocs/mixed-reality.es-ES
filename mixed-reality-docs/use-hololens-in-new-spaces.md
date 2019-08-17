---
title: Usar HoloLens en nuevos espacios
description: HoloLens aprende qué aspecto tiene un espacio a lo largo del tiempo. Los usuarios pueden facilitar este proceso moviendo el HoloLens de ciertas maneras a través del espacio.
author: dorreneb
ms.author: dobrown
ms.date: 08/16/2019
ms.topic: article
keywords: Windows Mixed Reality, diseño, asignación espacial, HoloLens, reconstrucción expuesta, malla, seguimiento de cabezales, asignación
ms.openlocfilehash: a6a83dfc2c883723e4cd79c0dc46a9cd78f1f604
ms.sourcegitcommit: 60f73ca23023c17c1da833c83d2a02f4dcc4d17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566024"
---
# <a name="use-hololens-in-new-spaces"></a><span data-ttu-id="97371-105">Usar HoloLens en nuevos espacios</span><span class="sxs-lookup"><span data-stu-id="97371-105">Use HoloLens in New Spaces</span></span>

<span data-ttu-id="97371-106">HoloLens *asigna*o aprende información sobre el entorno a medida que el usuario se desplaza por un espacio.</span><span class="sxs-lookup"><span data-stu-id="97371-106">HoloLens *maps*, or learns information about, its environment as the user moves around a space.</span></span> <span data-ttu-id="97371-107">Con el tiempo, HoloLens crea un *mapa espacial* de todas las partes del entorno que se han observado.</span><span class="sxs-lookup"><span data-stu-id="97371-107">Over time, the HoloLens builds up a *spatial map* of all parts of the environment that have been observed.</span></span> <span data-ttu-id="97371-108">HoloLens actualiza el mapa a medida que se observan los cambios en el entorno.</span><span class="sxs-lookup"><span data-stu-id="97371-108">HoloLens updates the map as changes in the environment are observed.</span></span> <span data-ttu-id="97371-109">Este examen se conservará automáticamente entre los lanzamientos de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="97371-109">This scan will automatically persist between app launches.</span></span>

<span data-ttu-id="97371-110">HoloLens creará y actualizará asignaciones siempre que el dispositivo esté encendido y un usuario haya iniciado sesión.</span><span class="sxs-lookup"><span data-stu-id="97371-110">HoloLens will create and update maps as long as the device is on and a user is logged in.</span></span> <span data-ttu-id="97371-111">Si mantiene presionado el dispositivo con las cámaras que apuntan a un espacio, el dispositivo intentará asignar el área.</span><span class="sxs-lookup"><span data-stu-id="97371-111">If you hold or wear the device with the cameras pointed at a space, the device will try to map the area.</span></span> <span data-ttu-id="97371-112">Aunque HoloLens aprenderá un espacio de forma natural a lo largo del tiempo, hay sugerencias y trucos disponibles para asignar el espacio de manera más rápida y eficaz.</span><span class="sxs-lookup"><span data-stu-id="97371-112">While the HoloLens will learn a space naturally over time, there are tips and tricks available to map the space faster and more efficiently.</span></span> 

<span data-ttu-id="97371-113">Si HoloLens no puede asignar espacio o está fuera de la calibración, puede entrar en modo limitado.</span><span class="sxs-lookup"><span data-stu-id="97371-113">If your HoloLens can’t map your space or is out of calibration, you may enter Limited mode.</span></span> <span data-ttu-id="97371-114">En el modo limitado, no podrá colocar hologramas en su entorno.</span><span class="sxs-lookup"><span data-stu-id="97371-114">In Limited mode, you won’t be able to place holograms in your surroundings.</span></span>

## <a name="tips-and-tricks-for-mapping-spaces"></a><span data-ttu-id="97371-115">Sugerencias y trucos para la asignación de espacios</span><span class="sxs-lookup"><span data-stu-id="97371-115">Tips and tricks for mapping spaces</span></span>

### <a name="make-sure-the-space-is-set-up-for-mixed-reality"></a><span data-ttu-id="97371-116">Asegúrese de que el espacio está configurado para la realidad mixta</span><span class="sxs-lookup"><span data-stu-id="97371-116">Make sure the space is set up for mixed reality</span></span>

<span data-ttu-id="97371-117">Las características de un entorno pueden dificultar que HoloLens interprete un espacio.</span><span class="sxs-lookup"><span data-stu-id="97371-117">Features in an environment can make it difficult for the HoloLens to interpret a space.</span></span> <span data-ttu-id="97371-118">Los niveles de luz, los materiales del espacio, el diseño de los objetos, etc. pueden afectar a la forma en que HoloLens asigna un área.</span><span class="sxs-lookup"><span data-stu-id="97371-118">Light levels, materials in the space, the layout of objects, and more can all affect how HoloLens maps an area.</span></span>

<span data-ttu-id="97371-119">Puede encontrar sugerencias para configurar el espacio de HoloLens y otros dispositivos de realidad mixta en [consideraciones de entorno para hololens](environment-considerations-for-hololens.md).</span><span class="sxs-lookup"><span data-stu-id="97371-119">Tips for setting up your space for HoloLens and other mixed reality devices can be found in [Environment considerations for HoloLens](environment-considerations-for-hololens.md).</span></span>

### <a name="understand-the-scenarios-for-the-area"></a><span data-ttu-id="97371-120">Comprender los escenarios del área</span><span class="sxs-lookup"><span data-stu-id="97371-120">Understand the scenarios for the area</span></span>

<span data-ttu-id="97371-121">Es importante dedicar el tiempo más en el que vaya a usar HoloLens para que el mapa sea relevante y completo.</span><span class="sxs-lookup"><span data-stu-id="97371-121">It is important to spend the most time where you will be using the HoloLens so that the map is relevant and complete.</span></span> 

<span data-ttu-id="97371-122">Por ejemplo, si un escenario de usuario de HoloLens implica pasar del punto a al punto B, desplazarse por la ruta de acceso dos a tres veces, buscando en todas las direcciones mientras se mueven.</span><span class="sxs-lookup"><span data-stu-id="97371-122">For example, if a user scenario for HoloLens involves moving from Point A to Point B, walk that path two to three times, looking in all directions as you move.</span></span> 

### <a name="walk-slowly-around-the-space"></a><span data-ttu-id="97371-123">Recorrer lentamente el espacio</span><span class="sxs-lookup"><span data-stu-id="97371-123">Walk slowly around the space</span></span>

<span data-ttu-id="97371-124">Si recorre demasiado rápidamente el área, es probable que HoloLens pierda las áreas de asignación.</span><span class="sxs-lookup"><span data-stu-id="97371-124">If you walk too quickly around the area, it's likely that the HoloLens will miss mapping areas.</span></span> <span data-ttu-id="97371-125">Desplácese lentamente alrededor del espacio, deteniéndose cada 5-8 metros para buscar en todo el entorno.</span><span class="sxs-lookup"><span data-stu-id="97371-125">Walk slowly around the space, stopping every 5-8 feet to look around at your surroundings.</span></span>

<span data-ttu-id="97371-126">Los movimientos suaves también ayudan a la asignación de HoloLens más effeciently.</span><span class="sxs-lookup"><span data-stu-id="97371-126">Smooth movements also help the HoloLens map more effeciently.</span></span>

### <a name="look-in-all-directions"></a><span data-ttu-id="97371-127">Buscar en todas las direcciones</span><span class="sxs-lookup"><span data-stu-id="97371-127">Look in all directions</span></span>

<span data-ttu-id="97371-128">Al mirar el espacio, se proporciona a HoloLens más datos sobre dónde se relacionan entre sí los puntos.</span><span class="sxs-lookup"><span data-stu-id="97371-128">Looking around as you map the space gives the HoloLens more data on where points are relative to each other.</span></span> 

<span data-ttu-id="97371-129">Si no busca, por ejemplo, es posible que HoloLens no sepa dónde está el límite superior de una habitación.</span><span class="sxs-lookup"><span data-stu-id="97371-129">If you don't look up, for example, the HoloLens may not know where the ceiling in a room is.</span></span> 

<span data-ttu-id="97371-130">No olvide mirar el suelo mientras asigna el espacio.</span><span class="sxs-lookup"><span data-stu-id="97371-130">Don't forget to look down at the floor as you map the space.</span></span>

### <a name="cover-key-areas-multiple-times"></a><span data-ttu-id="97371-131">Portadas varias veces de las áreas clave</span><span class="sxs-lookup"><span data-stu-id="97371-131">Cover key areas multiple times</span></span>

<span data-ttu-id="97371-132">Desplazarse por un área varias veces le ayudará a recoger características que puede que haya perdido en el primer tutorial.</span><span class="sxs-lookup"><span data-stu-id="97371-132">Moving through an area multiple times will help pick up features you may have missed on the first walkthrough.</span></span> <span data-ttu-id="97371-133">Intente recorrer un área dos o tres veces para crear un mapa ideal.</span><span class="sxs-lookup"><span data-stu-id="97371-133">Try traversing an area two to three times to build an ideal map.</span></span>

<span data-ttu-id="97371-134">Si es posible, mientras se repiten estos movimientos, dedique tiempo a recorrer un área en una dirección y, a continuación, desactive y recorra la forma en que lo hizo.</span><span class="sxs-lookup"><span data-stu-id="97371-134">If possible, while repeating these movements, spend time walking through an area in one direction, then turn around and walk back the way you came.</span></span>

### <a name="take-your-time-mapping-the-area"></a><span data-ttu-id="97371-135">Dedique su tiempo a asignar el área</span><span class="sxs-lookup"><span data-stu-id="97371-135">Take your time mapping the area</span></span>

<span data-ttu-id="97371-136">Puede tardar entre 15 y 20 minutos para que HoloLens se asigne completamente y se ajuste a su entorno.</span><span class="sxs-lookup"><span data-stu-id="97371-136">It can take between 15 and 20 minutes for the HoloLens to fully map and adjust itself to its surroundings.</span></span> <span data-ttu-id="97371-137">Si tiene un espacio en el que piensa usar una HoloLens con frecuencia, tardará ese tiempo en realizarse por adelantado para asignar el espacio puede evitar problemas más adelante.</span><span class="sxs-lookup"><span data-stu-id="97371-137">If you have a space in which you plan to use a HoloLens frequently, taking that time up front to map the space can prevent issues later on.</span></span> 

## <a name="possible-errors-in-the-spatial-map"></a><span data-ttu-id="97371-138">Posibles errores en el mapa espacial</span><span class="sxs-lookup"><span data-stu-id="97371-138">Possible errors in the spatial map</span></span>

<span data-ttu-id="97371-139">Los errores en los datos de asignación espacial se dividen en una de estas tres categorías:</span><span class="sxs-lookup"><span data-stu-id="97371-139">Errors in spatial mapping data fall into one of three categories:</span></span>

* <span data-ttu-id="97371-140">*Agujeros*: Faltan las superficies del mundo real en los datos de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="97371-140">*Holes*: Real-world surfaces are missing from the spatial mapping data.</span></span>
* <span data-ttu-id="97371-141">*Hallucinations*: Existen superficies en los datos de asignación espacial que no existen en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="97371-141">*Hallucinations*: Surfaces exist in the spatial mapping data that do not exist in the real world.</span></span>
* <span data-ttu-id="97371-142">*Túneles espaciales*: La parte de HoloLens ' pierde ' del mapa espacial al pensar que está en una parte diferente del mapa que realmente es.</span><span class="sxs-lookup"><span data-stu-id="97371-142">*Wormholes*: HoloLens 'loses' part of the spatial map by thinking it is in a different part of the map than it actually is.</span></span>
* <span data-ttu-id="97371-143">*Bias*: Las superficies en los datos de asignación espacial se alinean imperfectamente con las superficies del mundo real, ya sean insertadas o extraídas.</span><span class="sxs-lookup"><span data-stu-id="97371-143">*Bias*: Surfaces in the spatial mapping data are imperfectly aligned with real-world surfaces, either pushed in or pulled out.</span></span>

<span data-ttu-id="97371-144">Muchos de estos errores se pueden mitigar si se [eliminan los hologramas](environment-considerations-for-hololens.md) y se vuelve a asignar el espacio.</span><span class="sxs-lookup"><span data-stu-id="97371-144">Many of these errors can be mitigated by [deleting your holograms](environment-considerations-for-hololens.md) and re-mapping the space.</span></span>