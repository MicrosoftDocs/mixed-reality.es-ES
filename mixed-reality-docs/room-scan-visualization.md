---
title: Visualización de análisis de sala
description: Las aplicaciones que requieren datos de asignación espacial se basan en el dispositivo para recopilar estos datos automáticamente con el tiempo y en las sesiones como el usuario explora su entorno con el dispositivo activo.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, patrones de aplicaciones, diseño, HoloLens, examen de sala, espacial de asignación, superficie reconstrucción, Live mesh
ms.openlocfilehash: 8ffde9d476e25016f986321377dce8125ee3a596
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605693"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="0273f-104">Visualización de análisis de sala</span><span class="sxs-lookup"><span data-stu-id="0273f-104">Room scan visualization</span></span>

<span data-ttu-id="0273f-105">Las aplicaciones que requieren datos de asignación espacial se basan en el dispositivo para recopilar estos datos automáticamente con el tiempo y en las sesiones como el usuario explora su entorno con el dispositivo activo.</span><span class="sxs-lookup"><span data-stu-id="0273f-105">Applications that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="0273f-106">La integridad y la calidad de los datos depende de varios factores como la cantidad de exploración, el usuario ha hecho, ¿cuánto tiempo ha transcurrido desde la exploración y si objetos como muebles y puertas movido desde que el dispositivo había analizado el área.</span><span class="sxs-lookup"><span data-stu-id="0273f-106">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="0273f-107">Para asegurarse de datos de asignación espacial útiles, los desarrolladores de aplicaciones tienen varias opciones:</span><span class="sxs-lookup"><span data-stu-id="0273f-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="0273f-108">Se basan en lo que es posible que ya se han recopilado.</span><span class="sxs-lookup"><span data-stu-id="0273f-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="0273f-109">Estos datos pueden estar incompletos inicialmente.</span><span class="sxs-lookup"><span data-stu-id="0273f-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="0273f-110">Pida al usuario usar el gesto de bloom para llegar a Windows Mixed Reality principal y, a continuación, explore el área que desean usar para la experiencia.</span><span class="sxs-lookup"><span data-stu-id="0273f-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="0273f-111">Pulsar en el aire pueden usar para confirmar que se conoce toda el área es necesario para el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0273f-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="0273f-112">Crear una experiencia de exploración personalizada en su propia aplicación.</span><span class="sxs-lookup"><span data-stu-id="0273f-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="0273f-113">Tenga en cuenta que en todos estos casos se almacenan los datos reales recopilados durante la exploración por el sistema y la aplicación no necesita hacerlo.</span><span class="sxs-lookup"><span data-stu-id="0273f-113">Note that in all these cases the actual data gathered during the exploration is stored by the system and the application does not need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="0273f-114">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="0273f-114">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="0273f-115">Característica</span><span class="sxs-lookup"><span data-stu-id="0273f-115">Feature</span></span></th><th style="width:150px"> <span data-ttu-id="0273f-116"><a href="hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="0273f-116"><a href="hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="0273f-117"><a href="immersive-headset-hardware-details.md">Inmersivos</a></span><span class="sxs-lookup"><span data-stu-id="0273f-117"><a href="immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="0273f-118">Visualización de análisis de sala</span><span class="sxs-lookup"><span data-stu-id="0273f-118">Room scan visualization</span></span></td><td style="text-align: center;"> <span data-ttu-id="0273f-119">✔️</span><span class="sxs-lookup"><span data-stu-id="0273f-119">✔️</span></span></td><td style="text-align: center;"></td>
</tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="0273f-120">Creación de una experiencia de exploración personalizada</span><span class="sxs-lookup"><span data-stu-id="0273f-120">Building a custom scanning experience</span></span>

<span data-ttu-id="0273f-121">Pueden decidir analizar los datos de asignación espacial al principio de la experiencia para decidir si desean que el usuario realice pasos adicionales para mejorar su integridad y la calidad de las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="0273f-121">Applications may decide to analyze the spatial mapping data at the start of the experience to judge whether they want the user to perform additional steps to improve its completeness and quality.</span></span> <span data-ttu-id="0273f-122">Si el análisis indica que se debe mejorar la calidad, los desarrolladores deben proporcionar una visualización a superponer en el mundo para indicar:</span><span class="sxs-lookup"><span data-stu-id="0273f-122">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="0273f-123">¿Cuánto volumen total, en la proximidad de los usuarios debe formar parte de la experiencia</span><span class="sxs-lookup"><span data-stu-id="0273f-123">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="0273f-124">Donde el usuario debe ir para mejorar los datos</span><span class="sxs-lookup"><span data-stu-id="0273f-124">Where the user should go to improve data</span></span>

<span data-ttu-id="0273f-125">Los usuarios no saben lo que hace que un examen "bueno".</span><span class="sxs-lookup"><span data-stu-id="0273f-125">Users do not know what makes a "good" scan.</span></span> <span data-ttu-id="0273f-126">Deben mostrarse o dijo lo que se debe buscar si le pide que evaluar un examen: aplanamiento, distancia de las paredes reales, etcetera. El desarrollador debe implementar un bucle de comentarios que incluye la actualización de los datos de asignación espacial durante la fase de análisis o exploración.</span><span class="sxs-lookup"><span data-stu-id="0273f-126">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, etc. The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="0273f-127">En muchos casos, puede ser mejor indicar que el usuario lo que necesitan (por ejemplo, examine el límite superior, busque detrás de muebles), con el fin de obtener la calidad del análisis necesarios.</span><span class="sxs-lookup"><span data-stu-id="0273f-127">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="0273f-128">En la caché frente a asignación espacial continua</span><span class="sxs-lookup"><span data-stu-id="0273f-128">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="0273f-129">Los datos de asignación espacial están el peso más pesado pueden consumir las aplicaciones del origen de datos.</span><span class="sxs-lookup"><span data-stu-id="0273f-129">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="0273f-130">Para evitar problemas de rendimiento, como fotogramas eliminados o repetir, consumo de los datos debe realizarse con cuidado.</span><span class="sxs-lookup"><span data-stu-id="0273f-130">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="0273f-131">Análisis activo durante una experiencia pueden ser beneficioso o perjudicial y el desarrollador tendrá que decidir qué método utilizar según la experiencia.</span><span class="sxs-lookup"><span data-stu-id="0273f-131">Active scanning during an experience can be both beneficial or detrimental and the developer will need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="0273f-132">Asignación espacial en caché</span><span class="sxs-lookup"><span data-stu-id="0273f-132">Cached spatial mapping</span></span>

<span data-ttu-id="0273f-133">En el caso de asignación espacial en caché, la aplicación normalmente toma una instantánea de los datos de asignación espacial y utiliza esta instantánea para la duración de la experiencia.</span><span class="sxs-lookup"><span data-stu-id="0273f-133">In the case of cached spatial mapping, the application typically takes a snapshot of the spatial mapping data and uses this snapshot for the duration of the experience.</span></span>

<span data-ttu-id="0273f-134">**Ventajas**</span><span class="sxs-lookup"><span data-stu-id="0273f-134">**Benefits**</span></span>
* <span data-ttu-id="0273f-135">Reducción de la sobrecarga en el sistema mientras la experiencia ejecuta líder a potencia espectacular, térmico y mejoras de rendimiento de cpu.</span><span class="sxs-lookup"><span data-stu-id="0273f-135">Reduced overhead on the system while the experience is running leading to dramatic power, thermal and cpu performance gains.</span></span>
* <span data-ttu-id="0273f-136">Una implementación más sencilla de la experiencia principal, ya que no se interrumpa por los cambios en los datos espaciales.</span><span class="sxs-lookup"><span data-stu-id="0273f-136">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="0273f-137">Una sola una vez costo en cualquier procesamiento posterior de los datos espaciales de leyes físicas, gráficos y otros fines.</span><span class="sxs-lookup"><span data-stu-id="0273f-137">A single one time cost on any post processing of the spatial data for physics, graphics and other purposes.</span></span>

<span data-ttu-id="0273f-138">**Inconvenientes**</span><span class="sxs-lookup"><span data-stu-id="0273f-138">**Drawbacks**</span></span>
* <span data-ttu-id="0273f-139">El movimiento de objetos del mundo real o personas no se refleja en los datos en caché.</span><span class="sxs-lookup"><span data-stu-id="0273f-139">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="0273f-140">P. ej.</span><span class="sxs-lookup"><span data-stu-id="0273f-140">E.g.</span></span> <span data-ttu-id="0273f-141">la aplicación podría considerar una puerta abierta cuando en realidad está cerrado ahora.</span><span class="sxs-lookup"><span data-stu-id="0273f-141">the application might consider a door open when it is actually closed now.</span></span>
* <span data-ttu-id="0273f-142">Potencialmente más memoria de la aplicación para mantener la versión en caché de los datos.</span><span class="sxs-lookup"><span data-stu-id="0273f-142">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="0273f-143">Un buen caso de este método es un juego de la tabla superior o de un entorno controlado.</span><span class="sxs-lookup"><span data-stu-id="0273f-143">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="0273f-144">Asignación espacial continua</span><span class="sxs-lookup"><span data-stu-id="0273f-144">Continuous spatial mapping</span></span>

<span data-ttu-id="0273f-145">Algunas aplicaciones pueden confiar en continúa analizando para actualizar los datos de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="0273f-145">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="0273f-146">**Ventajas**</span><span class="sxs-lookup"><span data-stu-id="0273f-146">**Benefits**</span></span>
* <span data-ttu-id="0273f-147">No es necesario que se compilarán en una independiente análisis de exploración experiencia o por adelantado en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="0273f-147">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="0273f-148">El movimiento de objetos del mundo real puede reflejarse en el juego, aunque con cierto retraso.</span><span class="sxs-lookup"><span data-stu-id="0273f-148">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="0273f-149">**Inconvenientes**</span><span class="sxs-lookup"><span data-stu-id="0273f-149">**Drawbacks**</span></span>
* <span data-ttu-id="0273f-150">Una mayor complejidad en la implementación de la experiencia del principal.</span><span class="sxs-lookup"><span data-stu-id="0273f-150">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="0273f-151">Sobrecarga potencial del procesamiento adicional para el gráfico o físicas, como los cambios deben ser ingeridos incrementalmente estos sistemas.</span><span class="sxs-lookup"><span data-stu-id="0273f-151">Potential overhead of the additional processing for graphic or physics as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="0273f-152">Mayor capacidad, térmico y el impacto en la CPU.</span><span class="sxs-lookup"><span data-stu-id="0273f-152">Higher power, thermal and CPU impact.</span></span>

<span data-ttu-id="0273f-153">Un buen caso de este método es uno donde se esperan hologramas para interactuar con el movimiento de objetos, por ejemplo, un automóvil holográfico que las unidades en el suelo pueden toparse con una puerta dependiendo de si es abierto o cerrado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0273f-153">A good case for this method is one where holograms are expected to interact with moving objects, e.g. a holographic car that drives on the floor may want to correctly bump into a door depending on whether it is open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="0273f-154">Vea también</span><span class="sxs-lookup"><span data-stu-id="0273f-154">See also</span></span>
* [<span data-ttu-id="0273f-155">Diseño de la asignación espacial</span><span class="sxs-lookup"><span data-stu-id="0273f-155">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="0273f-156">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="0273f-156">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="0273f-157">Diseño espacial de sonido</span><span class="sxs-lookup"><span data-stu-id="0273f-157">Spatial sound design</span></span>](spatial-sound-design.md)
