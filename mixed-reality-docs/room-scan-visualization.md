---
title: Visualización del examen de salón
description: Las aplicaciones que requieren datos de asignación espacial se basan en el dispositivo para recopilar automáticamente estos datos a lo largo del tiempo y entre sesiones a medida que el usuario explora su entorno con el dispositivo activo.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, patrones de aplicaciones, diseño, HoloLens, examen de salón, asignación espacial, reconstrucción superficial, malla
ms.openlocfilehash: 09df4464ea4dac01dfad637886b07b861f468d4d
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829914"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="a4198-104">Visualización del examen de salón</span><span class="sxs-lookup"><span data-stu-id="a4198-104">Room scan visualization</span></span>

<span data-ttu-id="a4198-105">Las aplicaciones que requieren datos de asignación espacial se basan en el dispositivo para recopilar automáticamente estos datos a lo largo del tiempo y entre sesiones a medida que el usuario explora su entorno con el dispositivo activo.</span><span class="sxs-lookup"><span data-stu-id="a4198-105">Applications that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="a4198-106">La integridad y la calidad de estos datos dependen de una serie de factores, entre los que se incluye la cantidad de exploración que ha realizado el usuario, cuánto tiempo ha transcurrido desde la exploración y si los objetos como el mobiliario y las puertas se han trasladado desde que el dispositivo examinó la zona.</span><span class="sxs-lookup"><span data-stu-id="a4198-106">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="a4198-107">Para garantizar datos de asignación espacial útiles, los desarrolladores de aplicaciones tienen varias opciones:</span><span class="sxs-lookup"><span data-stu-id="a4198-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="a4198-108">Confíe en lo que ya se ha recopilado.</span><span class="sxs-lookup"><span data-stu-id="a4198-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="a4198-109">Estos datos pueden estar incompletos inicialmente.</span><span class="sxs-lookup"><span data-stu-id="a4198-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="a4198-110">Pida al usuario que use el gesto de floración para llegar a la Página principal de Windows Mixed Reality y, a continuación, explore el área que desean usar para la experiencia.</span><span class="sxs-lookup"><span data-stu-id="a4198-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="a4198-111">Pueden utilizar la pulsación aérea para confirmar que el dispositivo conoce todo el área necesaria.</span><span class="sxs-lookup"><span data-stu-id="a4198-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="a4198-112">Cree una experiencia de exploración personalizada en su propia aplicación.</span><span class="sxs-lookup"><span data-stu-id="a4198-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="a4198-113">Tenga en cuenta que en todos estos casos los datos reales recopilados durante la exploración se almacenan en el sistema y la aplicación no necesita hacerlo.</span><span class="sxs-lookup"><span data-stu-id="a4198-113">Note that in all these cases the actual data gathered during the exploration is stored by the system and the application does not need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="a4198-114">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="a4198-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="a4198-115"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="a4198-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="a4198-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="a4198-116"><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="a4198-117"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="a4198-117"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="a4198-118">Visualización del examen de salón</span><span class="sxs-lookup"><span data-stu-id="a4198-118">Room scan visualization</span></span></td>
        <td><span data-ttu-id="a4198-119">✔️</span><span class="sxs-lookup"><span data-stu-id="a4198-119">✔️</span></span></td>
        <td><span data-ttu-id="a4198-120">❌</span><span class="sxs-lookup"><span data-stu-id="a4198-120">❌</span></span></td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="a4198-121">Generar una experiencia de exploración personalizada</span><span class="sxs-lookup"><span data-stu-id="a4198-121">Building a custom scanning experience</span></span>

<span data-ttu-id="a4198-122">Las aplicaciones pueden decidir analizar los datos de asignación espacial al principio de la experiencia para juzgar si desean que el usuario realice pasos adicionales para mejorar su integridad y calidad.</span><span class="sxs-lookup"><span data-stu-id="a4198-122">Applications may decide to analyze the spatial mapping data at the start of the experience to judge whether they want the user to perform additional steps to improve its completeness and quality.</span></span> <span data-ttu-id="a4198-123">Si el análisis indica que se debe mejorar la calidad, los desarrolladores deben proporcionar una visualización de superposición en todo el mundo para indicar:</span><span class="sxs-lookup"><span data-stu-id="a4198-123">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="a4198-124">La cantidad del volumen total de los usuarios en proximidad debe formar parte de la experiencia</span><span class="sxs-lookup"><span data-stu-id="a4198-124">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="a4198-125">Dónde debe ir el usuario para mejorar los datos</span><span class="sxs-lookup"><span data-stu-id="a4198-125">Where the user should go to improve data</span></span>

<span data-ttu-id="a4198-126">Los usuarios no saben lo que realiza un análisis "correcto".</span><span class="sxs-lookup"><span data-stu-id="a4198-126">Users do not know what makes a "good" scan.</span></span> <span data-ttu-id="a4198-127">Es necesario que se muestren o se les indique lo que debe buscar si se les pide que evalúen un análisis, la distancia de las paredes reales, etc. El desarrollador debe implementar un bucle de comentarios que incluya la actualización de los datos de asignación espacial durante la fase de exploración o exploración.</span><span class="sxs-lookup"><span data-stu-id="a4198-127">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, etc. The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="a4198-128">En muchos casos, puede ser mejor indicar al usuario lo que necesita hacer (por ejemplo, mirar el límite superior, mirar detrás del mobiliario) para obtener la calidad de examen necesaria.</span><span class="sxs-lookup"><span data-stu-id="a4198-128">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="a4198-129">Asignación espacial en caché y continua</span><span class="sxs-lookup"><span data-stu-id="a4198-129">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="a4198-130">Los datos de asignación espacial son el peso más pesado que pueden consumir las aplicaciones de origen de datos.</span><span class="sxs-lookup"><span data-stu-id="a4198-130">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="a4198-131">Para evitar problemas de rendimiento, como fotogramas quitados o intermitencias, el consumo de estos datos debe realizarse con cuidado.</span><span class="sxs-lookup"><span data-stu-id="a4198-131">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="a4198-132">El análisis activo durante una experiencia puede ser beneficioso o perjudicial, y el desarrollador deberá decidir qué método usar en función de la experiencia.</span><span class="sxs-lookup"><span data-stu-id="a4198-132">Active scanning during an experience can be both beneficial or detrimental and the developer will need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="a4198-133">Asignación espacial almacenada en caché</span><span class="sxs-lookup"><span data-stu-id="a4198-133">Cached spatial mapping</span></span>

<span data-ttu-id="a4198-134">En el caso de la asignación espacial almacenada en caché, la aplicación normalmente toma una instantánea de los datos de asignación espacial y usa esta instantánea para la duración de la experiencia.</span><span class="sxs-lookup"><span data-stu-id="a4198-134">In the case of cached spatial mapping, the application typically takes a snapshot of the spatial mapping data and uses this snapshot for the duration of the experience.</span></span>

<span data-ttu-id="a4198-135">**Ventajas**</span><span class="sxs-lookup"><span data-stu-id="a4198-135">**Benefits**</span></span>
* <span data-ttu-id="a4198-136">Reducción de la sobrecarga en el sistema mientras se ejecuta la experiencia, lo que supone una mejora considerable en el rendimiento de la CPU, el térmico y la potencia.</span><span class="sxs-lookup"><span data-stu-id="a4198-136">Reduced overhead on the system while the experience is running leading to dramatic power, thermal and cpu performance gains.</span></span>
* <span data-ttu-id="a4198-137">Una implementación más sencilla de la experiencia principal, ya que no se ve interrumpida por los cambios en los datos espaciales.</span><span class="sxs-lookup"><span data-stu-id="a4198-137">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="a4198-138">Un único costo de tiempo en cualquier procesamiento posterior de los datos espaciales para la física, los gráficos y otros propósitos.</span><span class="sxs-lookup"><span data-stu-id="a4198-138">A single one time cost on any post processing of the spatial data for physics, graphics and other purposes.</span></span>

<span data-ttu-id="a4198-139">**Desventajas**</span><span class="sxs-lookup"><span data-stu-id="a4198-139">**Drawbacks**</span></span>
* <span data-ttu-id="a4198-140">El movimiento de objetos o personas reales no se refleja en los datos almacenados en caché.</span><span class="sxs-lookup"><span data-stu-id="a4198-140">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="a4198-141">Por ejemplo,</span><span class="sxs-lookup"><span data-stu-id="a4198-141">E.g.</span></span> <span data-ttu-id="a4198-142">es posible que la aplicación considere una puerta abierta cuando realmente está cerrada.</span><span class="sxs-lookup"><span data-stu-id="a4198-142">the application might consider a door open when it is actually closed now.</span></span>
* <span data-ttu-id="a4198-143">Posiblemente más memoria de la aplicación para mantener la versión en caché de los datos.</span><span class="sxs-lookup"><span data-stu-id="a4198-143">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="a4198-144">Un buen caso para este método es un entorno controlado o una tabla principal del juego.</span><span class="sxs-lookup"><span data-stu-id="a4198-144">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="a4198-145">Asignación espacial continua</span><span class="sxs-lookup"><span data-stu-id="a4198-145">Continuous spatial mapping</span></span>

<span data-ttu-id="a4198-146">Algunas aplicaciones pueden basarse en el análisis continuo para actualizar los datos de asignación espacial.</span><span class="sxs-lookup"><span data-stu-id="a4198-146">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="a4198-147">**Ventajas**</span><span class="sxs-lookup"><span data-stu-id="a4198-147">**Benefits**</span></span>
* <span data-ttu-id="a4198-148">No es necesario compilar en una experiencia de exploración o exploración independiente de antemano en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a4198-148">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="a4198-149">El movimiento de objetos del mundo real puede reflejarse en el juego, aunque con algún retraso.</span><span class="sxs-lookup"><span data-stu-id="a4198-149">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="a4198-150">**Desventajas**</span><span class="sxs-lookup"><span data-stu-id="a4198-150">**Drawbacks**</span></span>
* <span data-ttu-id="a4198-151">Mayor complejidad en la implementación de la experiencia principal.</span><span class="sxs-lookup"><span data-stu-id="a4198-151">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="a4198-152">Sobrecarga potencial del procesamiento adicional de gráficos o física, ya que estos sistemas deben ingerir los cambios de forma incremental.</span><span class="sxs-lookup"><span data-stu-id="a4198-152">Potential overhead of the additional processing for graphic or physics as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="a4198-153">Mayor potencia, térmico y impacto de la CPU.</span><span class="sxs-lookup"><span data-stu-id="a4198-153">Higher power, thermal and CPU impact.</span></span>

<span data-ttu-id="a4198-154">Un buen caso para este método es aquél en el que se espera que los hologramas interactúen con los objetos de movimiento, por ejemplo, un coche holográfica que las unidades del piso quieran golpear correctamente en una puerta en función de si está abierto o cerrado.</span><span class="sxs-lookup"><span data-stu-id="a4198-154">A good case for this method is one where holograms are expected to interact with moving objects, e.g. a holographic car that drives on the floor may want to correctly bump into a door depending on whether it is open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="a4198-155">Vea también</span><span class="sxs-lookup"><span data-stu-id="a4198-155">See also</span></span>
* [<span data-ttu-id="a4198-156">Diseño de asignaciones espaciales</span><span class="sxs-lookup"><span data-stu-id="a4198-156">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="a4198-157">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="a4198-157">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="a4198-158">Diseño de sonido espacial</span><span class="sxs-lookup"><span data-stu-id="a4198-158">Spatial sound design</span></span>](spatial-sound-design.md)
