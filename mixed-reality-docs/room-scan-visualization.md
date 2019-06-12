---
title: Visualización de análisis de sala
description: Las aplicaciones que requieren datos de asignación espacial se basan en el dispositivo para recopilar estos datos automáticamente con el tiempo y en las sesiones como el usuario explora su entorno con el dispositivo activo.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, patrones de aplicaciones, diseño, HoloLens, examen de sala, espacial de asignación, superficie reconstrucción, Live mesh
ms.openlocfilehash: 09df4464ea4dac01dfad637886b07b861f468d4d
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829914"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="189c1-104">Visualización de análisis de sala</span><span class="sxs-lookup"><span data-stu-id="189c1-104">Room scan visualization</span></span>

<span data-ttu-id="189c1-105">Las aplicaciones que requieren datos de asignación espacial se basan en el dispositivo para recopilar estos datos automáticamente con el tiempo y en las sesiones como el usuario explora su entorno con el dispositivo activo.</span><span class="sxs-lookup"><span data-stu-id="189c1-105">Applications that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="189c1-106">La integridad y la calidad de los datos depende de varios factores como la cantidad de exploración, el usuario ha hecho, ¿cuánto tiempo ha transcurrido desde la exploración y si objetos como muebles y puertas movido desde que el dispositivo había analizado el área.</span><span class="sxs-lookup"><span data-stu-id="189c1-106">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="189c1-107">Para asegurarse de datos de asignación espacial útiles, los desarrolladores de aplicaciones tienen varias opciones:</span><span class="sxs-lookup"><span data-stu-id="189c1-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="189c1-108">Se basan en lo que es posible que ya se han recopilado.</span><span class="sxs-lookup"><span data-stu-id="189c1-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="189c1-109">Estos datos pueden estar incompletos inicialmente.</span><span class="sxs-lookup"><span data-stu-id="189c1-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="189c1-110">Pida al usuario usar el gesto de bloom para llegar a Windows Mixed Reality principal y, a continuación, explore el área que desean usar para la experiencia.</span><span class="sxs-lookup"><span data-stu-id="189c1-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="189c1-111">Pulsar en el aire pueden usar para confirmar que se conoce toda el área es necesario para el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="189c1-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="189c1-112">Crear una experiencia de exploración personalizada en su propia aplicación.</span><span class="sxs-lookup"><span data-stu-id="189c1-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="189c1-113">Tenga en cuenta que en todos estos casos se almacenan los datos reales recopilados durante la exploración por el sistema y la aplicación no necesita hacerlo.</span><span class="sxs-lookup"><span data-stu-id="189c1-113">Note that in all these cases the actual data gathered during the exploration is stored by the system and the application does not need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="189c1-114">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="189c1-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="189c1-115"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="189c1-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="189c1-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="189c1-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="189c1-117"><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="189c1-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="189c1-118">Visualización de análisis de sala</span><span class="sxs-lookup"><span data-stu-id="189c1-118">Room scan visualization</span></span></td>
        <td><span data-ttu-id="189c1-119">✔️</span><span class="sxs-lookup"><span data-stu-id="189c1-119">✔️</span></span></td>
        <td><span data-ttu-id="189c1-120">❌</span><span class="sxs-lookup"><span data-stu-id="189c1-120">❌</span></span></td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="189c1-121">Creación de una experiencia de exploración personalizada</span><span class="sxs-lookup"><span data-stu-id="189c1-121">Building a custom scanning experience</span></span>

<span data-ttu-id="189c1-122">Pueden decidir analizar los datos de asignación espacial al principio de la experiencia para decidir si desean que el usuario realice pasos adicionales para mejorar su integridad y la calidad de las aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="189c1-122">Applications may decide to analyze the spatial mapping data at the start of the experience to judge whether they want the user to perform additional steps to improve its completeness and quality.</span></span> <span data-ttu-id="189c1-123">Si el análisis indica que se debe mejorar la calidad, los desarrolladores deben proporcionar una visualización a superponer en el mundo para indicar:</span><span class="sxs-lookup"><span data-stu-id="189c1-123">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="189c1-124">¿Cuánto volumen total, en la proximidad de los usuarios debe formar parte de la experiencia</span><span class="sxs-lookup"><span data-stu-id="189c1-124">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="189c1-125">Donde el usuario debe ir para mejorar los datos</span><span class="sxs-lookup"><span data-stu-id="189c1-125">Where the user should go to improve data</span></span>

<span data-ttu-id="189c1-126">Los usuarios no saben lo que hace que un examen "bueno".</span><span class="sxs-lookup"><span data-stu-id="189c1-126">Users do not know what makes a "good" scan.</span></span> <span data-ttu-id="189c1-127">Deben mostrarse o dijo lo que se debe buscar si le pide que evaluar un examen: aplanamiento, distancia de las paredes reales, etcetera. El desarrollador debe implementar un bucle de comentarios que incluye la actualización de los datos de asignación espacial durante la fase de análisis o exploración.</span><span class="sxs-lookup"><span data-stu-id="189c1-127">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, etc. The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="189c1-128">En muchos casos, puede ser mejor indicar que el usuario lo que necesitan (por ejemplo, examine el límite superior, busque detrás de muebles), con el fin de obtener la calidad del análisis necesarios.</span><span class="sxs-lookup"><span data-stu-id="189c1-128">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="189c1-129">En la caché frente a asignación espacial continua</span><span class="sxs-lookup"><span data-stu-id="189c1-129">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="189c1-130">Los datos de asignación espacial están el peso más pesado pueden consumir las aplicaciones del origen de datos.</span><span class="sxs-lookup"><span data-stu-id="189c1-130">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="189c1-131">Para evitar problemas de rendimiento, como fotogramas eliminados o repetir, consumo de los datos debe realizarse con cuidado.</span><span class="sxs-lookup"><span data-stu-id="189c1-131">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="189c1-132">Análisis activo durante una experiencia pueden ser beneficioso o perjudicial y el desarrollador tendrá que decidir qué método utilizar según la experiencia.</span><span class="sxs-lookup"><span data-stu-id="189c1-132">Active scanning during an experience can be both beneficial or detrimental and the developer will need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="189c1-133">Asignación espacial en caché</span><span class="sxs-lookup"><span data-stu-id="189c1-133">Cached spatial mapping</span></span>

<span data-ttu-id="189c1-134">En el caso de asignación espacial en caché, la aplicación normalmente toma una instantánea de los datos de asignación espacial y utiliza esta instantánea para la duración de la experiencia.</span><span class="sxs-lookup"><span data-stu-id="189c1-134">In the case of cached spatial mapping, the application typically takes a snapshot of the spatial mapping data and uses this snapshot for the duration of the experience.</span></span>

<span data-ttu-id="189c1-135">**Ventajas**</span><span class="sxs-lookup"><span data-stu-id="189c1-135">**Benefits**</span></span>
* <span data-ttu-id="189c1-136">Reducción de la sobrecarga en el sistema mientras la experiencia ejecuta líder a potencia espectacular, térmico y mejoras de rendimiento de cpu.</span><span class="sxs-lookup"><span data-stu-id="189c1-136">Reduced overhead on the system while the experience is running leading to dramatic power, thermal and cpu performance gains.</span></span>
* <span data-ttu-id="189c1-137">Una implementación más sencilla de la experiencia principal, ya que no se interrumpa por los cambios en los datos espaciales.</span><span class="sxs-lookup"><span data-stu-id="189c1-137">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="189c1-138">Una sola una vez costo en cualquier procesamiento posterior de los datos espaciales de leyes físicas, gráficos y otros fines.</span><span class="sxs-lookup"><span data-stu-id="189c1-138">A single one time cost on any post processing of the spatial data for physics, graphics and other purposes.</span></span>

<span data-ttu-id="189c1-139">**Inconvenientes**</span><span class="sxs-lookup"><span data-stu-id="189c1-139">**Drawbacks**</span></span>
* <span data-ttu-id="189c1-140">El movimiento de objetos del mundo real o personas no se refleja en los datos en caché.</span><span class="sxs-lookup"><span data-stu-id="189c1-140">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="189c1-141">P. ej.</span><span class="sxs-lookup"><span data-stu-id="189c1-141">E.g.</span></span> <span data-ttu-id="189c1-142">la aplicación podría considerar una puerta abierta cuando en realidad está cerrado ahora.</span><span class="sxs-lookup"><span data-stu-id="189c1-142">the application might consider a door open when it is actually closed now.</span></span>
* <span data-ttu-id="189c1-143">Potencialmente más memoria de la aplicación para mantener la versión en caché de los datos.</span><span class="sxs-lookup"><span data-stu-id="189c1-143">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="189c1-144">Un buen caso de este método es un juego de la tabla superior o de un entorno controlado.</span><span class="sxs-lookup"><span data-stu-id="189c1-144">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="189c1-145">Asignación espacial continua</span><span class="sxs-lookup"><span data-stu-id="189c1-145">Continuous spatial mapping</span></span>

<span data-ttu-id="189c1-146">Algunas aplicaciones pueden confiar en continúa analizando para actualizar los datos de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="189c1-146">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="189c1-147">**Ventajas**</span><span class="sxs-lookup"><span data-stu-id="189c1-147">**Benefits**</span></span>
* <span data-ttu-id="189c1-148">No es necesario que se compilarán en una independiente análisis de exploración experiencia o por adelantado en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="189c1-148">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="189c1-149">El movimiento de objetos del mundo real puede reflejarse en el juego, aunque con cierto retraso.</span><span class="sxs-lookup"><span data-stu-id="189c1-149">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="189c1-150">**Inconvenientes**</span><span class="sxs-lookup"><span data-stu-id="189c1-150">**Drawbacks**</span></span>
* <span data-ttu-id="189c1-151">Una mayor complejidad en la implementación de la experiencia del principal.</span><span class="sxs-lookup"><span data-stu-id="189c1-151">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="189c1-152">Sobrecarga potencial del procesamiento adicional para el gráfico o físicas, como los cambios deben ser ingeridos incrementalmente estos sistemas.</span><span class="sxs-lookup"><span data-stu-id="189c1-152">Potential overhead of the additional processing for graphic or physics as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="189c1-153">Mayor capacidad, térmico y el impacto en la CPU.</span><span class="sxs-lookup"><span data-stu-id="189c1-153">Higher power, thermal and CPU impact.</span></span>

<span data-ttu-id="189c1-154">Un buen caso de este método es uno donde se esperan hologramas para interactuar con el movimiento de objetos, por ejemplo, un automóvil holográfico que las unidades en el suelo pueden toparse con una puerta dependiendo de si es abierto o cerrado correctamente.</span><span class="sxs-lookup"><span data-stu-id="189c1-154">A good case for this method is one where holograms are expected to interact with moving objects, e.g. a holographic car that drives on the floor may want to correctly bump into a door depending on whether it is open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="189c1-155">Vea también</span><span class="sxs-lookup"><span data-stu-id="189c1-155">See also</span></span>
* [<span data-ttu-id="189c1-156">Diseño de asignaciones espaciales</span><span class="sxs-lookup"><span data-stu-id="189c1-156">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="189c1-157">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="189c1-157">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="189c1-158">Diseño de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="189c1-158">Spatial sound design</span></span>](spatial-sound-design.md)
