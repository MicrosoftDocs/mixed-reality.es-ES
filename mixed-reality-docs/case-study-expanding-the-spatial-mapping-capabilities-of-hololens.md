---
title: 'Caso práctico: expandir las capacidades de asignación espacial de HoloLens'
description: Al crear nuestra primera aplicaciones para Microsoft HoloLens, estábamos ansiosos por ver hasta qué punto simplemente podríamos sobrepasamos los límites de asignación espacial en el dispositivo.
author: jevertt
ms.author: jevertt
ms.date: 03/21/2018
ms.topic: article
keywords: Asignación espacial Windows Mixed Reality, HoloLens,
ms.openlocfilehash: 602b629afa5900ff34c28b3a3a32725af06590b7
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602837"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a><span data-ttu-id="1cef7-104">Caso práctico: expandir las capacidades de asignación espacial de HoloLens</span><span class="sxs-lookup"><span data-stu-id="1cef7-104">Case study - Expanding the spatial mapping capabilities of HoloLens</span></span>

<span data-ttu-id="1cef7-105">Al crear nuestra primera aplicaciones para Microsoft HoloLens, estábamos ansiosos por ver hasta qué punto simplemente podríamos sobrepasamos los límites de asignación espacial en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1cef7-105">When creating our first apps for Microsoft HoloLens, we were eager to see just how far we could push the boundaries of spatial mapping on the device.</span></span> <span data-ttu-id="1cef7-106">Jeff Evertt, un ingeniero de software de Microsoft Studios, se explica cómo se desarrolló una nueva tecnología de fuera de la necesidad de tener más control sobre cómo hologramas se colocan en el entorno de un usuario real.</span><span class="sxs-lookup"><span data-stu-id="1cef7-106">Jeff Evertt, a software engineer at Microsoft Studios, explains how a new technology was developed out of the need for more control over how holograms are placed in a user's real-world environment.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="1cef7-107">Vea el vídeo</span><span class="sxs-lookup"><span data-stu-id="1cef7-107">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a><span data-ttu-id="1cef7-108">Más allá de la asignación espacial</span><span class="sxs-lookup"><span data-stu-id="1cef7-108">Beyond spatial mapping</span></span>

<span data-ttu-id="1cef7-109">Mientras que estábamos trabajando [fragmentos](https://www.microsoft.com/p/fragments/9nblggh5ggm8) y [Conker Young](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), dos de los juegos de la primera para HoloLens, descubrimos que cuando se estaba realizando la colocación de procedimientos de hologramas en el mundo físico, es necesario un nivel más alto de conocimiento sobre el entorno del usuario.</span><span class="sxs-lookup"><span data-stu-id="1cef7-109">While we were working on [Fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8) and [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), two of the first games for HoloLens, we found that when we were doing procedural placement of holograms in the physical world, we needed a higher level of understanding about the user's environment.</span></span> <span data-ttu-id="1cef7-110">Cada juego tenía sus propias necesidades específicas de la selección de ubicación: En fragmentos, por ejemplo, deseamos poder distinguir entre diferentes tipos de superficies, como el límite inferior o una tabla, colocar pistas en ubicaciones importantes.</span><span class="sxs-lookup"><span data-stu-id="1cef7-110">Each game had its own specific placement needs: In Fragments, for example, we wanted to be able to distinguish between different surfaces—such as the floor or a table—to place clues in relevant locations.</span></span> <span data-ttu-id="1cef7-111">También deseamos ser capaz de identificar las superficies que podrían se colocan caracteres holográficas tamaño real, por ejemplo, un sofá o una silla.</span><span class="sxs-lookup"><span data-stu-id="1cef7-111">We also wanted to be able to identify surfaces that life-size holographic characters could sit on, such as a couch or a chair.</span></span> <span data-ttu-id="1cef7-112">Conker Young, quisimos Conker y sus oponentes para que pueda usar superficies se genera en la sala de un jugador que las plataformas.</span><span class="sxs-lookup"><span data-stu-id="1cef7-112">In Young Conker, we wanted Conker and his opponents to be able to use raised surfaces in a player's room as platforms.</span></span>

<span data-ttu-id="1cef7-113">[Estudios Asobo](http://www.asobostudio.com/index.html), nuestro socio de desarrollo de estos juegos, que se enfrentan este problema toro por las astas y creó una tecnología que amplía las capacidades de asignación espacial de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="1cef7-113">[Asobo Studios](http://www.asobostudio.com/index.html), our development partner for these games, faced this problem head-on and created a technology that extends the spatial mapping capabilities of HoloLens.</span></span> <span data-ttu-id="1cef7-114">Con esto, podríamos analizar sala de un jugador y superficies como paredes, tablas, sillas y plantas de identificar.</span><span class="sxs-lookup"><span data-stu-id="1cef7-114">Using this, we could analyze a player's room and identify surfaces such as walls, tables, chairs, and floors.</span></span> <span data-ttu-id="1cef7-115">También nos da la capacidad de optimizar con un conjunto de restricciones para determinar la mejor ubicación para los objetos holográficas.</span><span class="sxs-lookup"><span data-stu-id="1cef7-115">It also gave us the ability to optimize against a set of constraints to determine the best placement for holographic objects.</span></span>

## <a name="the-spatial-understanding-code"></a><span data-ttu-id="1cef7-116">El código de comprensión espacial</span><span class="sxs-lookup"><span data-stu-id="1cef7-116">The spatial understanding code</span></span>

<span data-ttu-id="1cef7-117">Se tardó el código original de Asobo y había creado una biblioteca que encapsula esta tecnología.</span><span class="sxs-lookup"><span data-stu-id="1cef7-117">We took Asobo's original code and created a library that encapsulates this technology.</span></span> <span data-ttu-id="1cef7-118">Microsoft y Asobo tiene ahora este código abierto y disponible en [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) para su uso en sus propios proyectos.</span><span class="sxs-lookup"><span data-stu-id="1cef7-118">Microsoft and Asobo have now open-sourced this code and made it available on [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) for you to use in your own projects.</span></span> <span data-ttu-id="1cef7-119">Todo el código fuente se incluye, por lo que permite personalizar según sus necesidades y compartir sus mejoras con la Comunidad.</span><span class="sxs-lookup"><span data-stu-id="1cef7-119">All the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="1cef7-120">El código para el C++ solver se ha ajustado en una DLL de UWP y expuestos a Unity con una [prefabricado de orden dentro de MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).</span><span class="sxs-lookup"><span data-stu-id="1cef7-120">The code for the C++ solver has been wrapped into a UWP DLL and exposed to Unity with a [drop-in prefab contained within MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).</span></span>

<span data-ttu-id="1cef7-121">Hay muchas consultas útiles incluidas en el ejemplo de Unity que le permitirá encontrar espacios vacíos en las paredes, colocar objetos en el límite superior o en espacios de gran tamaño en el suelo, identificar los lugares de caracteres que se encuentran y un sinnúmero de otras consultas espaciales descripción.</span><span class="sxs-lookup"><span data-stu-id="1cef7-121">There are many useful queries included in the Unity sample that will allow you to find empty spaces on walls, place objects on the ceiling or on large spaces on the floor, identify places for characters to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="1cef7-122">Mientras la solución de asignación espacial proporcionada por HoloLens está diseñada para ser lo suficientemente genéricos como para satisfacer las necesidades de toda la gama de espacios del problema, el módulo de comprensión espaciales se generó para admitir las necesidades de dos juegos específicos.</span><span class="sxs-lookup"><span data-stu-id="1cef7-122">While the spatial mapping solution provided by HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="1cef7-123">Por lo tanto, su solución está estructurada en torno a un proceso específico y un conjunto de supuestos:</span><span class="sxs-lookup"><span data-stu-id="1cef7-123">As such, its solution is structured around a specific process and set of assumptions:</span></span>
* <span data-ttu-id="1cef7-124">**Se ha corregido tamaño playspace**: El usuario especifica el tamaño máximo playspace en la llamada de init.</span><span class="sxs-lookup"><span data-stu-id="1cef7-124">**Fixed size playspace**: The user specifies the maximum playspace size in the init call.</span></span>
* <span data-ttu-id="1cef7-125">**Proceso de examen único**: El proceso requiere un discretos fase donde el usuario le guía en torno al análisis, definir el playspace.</span><span class="sxs-lookup"><span data-stu-id="1cef7-125">**One-time scan process**: The process requires a discrete scanning phase where the user walks around, defining the playspace.</span></span> <span data-ttu-id="1cef7-126">Funciones de consulta no funcionará hasta que una vez se ha finalizado el examen.</span><span class="sxs-lookup"><span data-stu-id="1cef7-126">Query functions will not function until after the scan has been finalized.</span></span>
* <span data-ttu-id="1cef7-127">**Usuario controlado por playspace "pintar"**: Durante la fase de análisis, el usuario se mueve y mira alrededor del playspace, pintar las áreas que deben incluirse de forma eficaz.</span><span class="sxs-lookup"><span data-stu-id="1cef7-127">**User driven playspace “painting”**: During the scanning phase, the user moves and looks around the playspace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="1cef7-128">La malla generada es importante para proporcionar comentarios de los usuarios durante esta fase.</span><span class="sxs-lookup"><span data-stu-id="1cef7-128">The generated mesh is important to provide user feedback during this phase.</span></span>
* <span data-ttu-id="1cef7-129">**En el interior el programa de instalación de casa u oficina**: Las funciones de consulta están diseñadas en torno a las superficies planas y paredes ángulos rectos.</span><span class="sxs-lookup"><span data-stu-id="1cef7-129">**Indoors home or office setup**: The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="1cef7-130">Esta es una limitación temporal.</span><span class="sxs-lookup"><span data-stu-id="1cef7-130">This is a soft limitation.</span></span> <span data-ttu-id="1cef7-131">Sin embargo, durante la fase de análisis, se completa un análisis del eje principal para optimizar la teselación de malla a lo largo del eje principal y secundaria.</span><span class="sxs-lookup"><span data-stu-id="1cef7-131">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="1cef7-132">Proceso de exploración de sala</span><span class="sxs-lookup"><span data-stu-id="1cef7-132">Room Scanning Process</span></span>

<span data-ttu-id="1cef7-133">Al cargar el módulo de comprensión espacial, lo primero que haré es examinar el espacio, por lo que todas las superficies utilizables, como paredes, ceiling y floor, se identifican y con la etiqueta.</span><span class="sxs-lookup"><span data-stu-id="1cef7-133">When you load the spatial understanding module, the first thing you'll do is scan your space, so all the usable surfaces—such as the floor, ceiling, and walls—are identified and labeled.</span></span> <span data-ttu-id="1cef7-134">Durante el proceso de digitalización, echa un vistazo alrededor de la sala y "paint" las áreas que deben incluirse en el examen.</span><span class="sxs-lookup"><span data-stu-id="1cef7-134">During the scanning process, you look around your room and "paint' the areas that should be included in the scan.</span></span>

<span data-ttu-id="1cef7-135">La malla vista durante esta fase es una parte importante de los comentarios visuales que permiten a los usuarios saber qué partes de la sala se están analizando.</span><span class="sxs-lookup"><span data-stu-id="1cef7-135">The mesh seen during this phase is an important piece of visual feedback that lets users know what parts of the room are being scanned.</span></span> <span data-ttu-id="1cef7-136">El archivo DLL para el módulo espacial descripción almacena internamente el playspace como una cuadrícula de 8cm tamaño voxel cubos.</span><span class="sxs-lookup"><span data-stu-id="1cef7-136">The DLL for the spatial understanding module internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="1cef7-137">Durante la parte inicial del análisis, se completa un análisis del componente principal para determinar los ejes de la sala.</span><span class="sxs-lookup"><span data-stu-id="1cef7-137">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="1cef7-138">Internamente, almacena su espacio voxel alineado para estos ejes.</span><span class="sxs-lookup"><span data-stu-id="1cef7-138">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="1cef7-139">Una malla se genera aproximadamente cada segundo mediante la extracción de la isosuperficie desde el volumen voxel.</span><span class="sxs-lookup"><span data-stu-id="1cef7-139">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span>

![Espacial de asignación de malla en blanco y entender playspace de malla en verde](images/spatial-mapping-500px.png)

<span data-ttu-id="1cef7-141">Espacial de asignación de malla en blanco y entender playspace de malla en verde</span><span class="sxs-lookup"><span data-stu-id="1cef7-141">Spatial mapping mesh in white and understanding playspace mesh in green</span></span>



<span data-ttu-id="1cef7-142">El archivo SpatialUnderstanding.cs incluido administra el proceso de la fase de análisis.</span><span class="sxs-lookup"><span data-stu-id="1cef7-142">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="1cef7-143">Llama a las funciones siguientes:</span><span class="sxs-lookup"><span data-stu-id="1cef7-143">It calls the following functions:</span></span>
* <span data-ttu-id="1cef7-144">**SpatialUnderstanding_Init**: Se llama una vez al principio.</span><span class="sxs-lookup"><span data-stu-id="1cef7-144">**SpatialUnderstanding_Init**: Called once at the start.</span></span>
* <span data-ttu-id="1cef7-145">**GeneratePlayspace_InitScan**: Indica que debería comenzar la fase de análisis.</span><span class="sxs-lookup"><span data-stu-id="1cef7-145">**GeneratePlayspace_InitScan**: Indicates that the scan phase should begin.</span></span>
* <span data-ttu-id="1cef7-146">**GeneratePlayspace_UpdateScan_DynamicScan**: Llama a cada fotograma para actualizar el proceso de detección.</span><span class="sxs-lookup"><span data-stu-id="1cef7-146">**GeneratePlayspace_UpdateScan_DynamicScan**: Called each frame to update the scanning process.</span></span> <span data-ttu-id="1cef7-147">La posición de la cámara y la orientación se pasa y se usa para el proceso de dibujo playspace, se ha descrito anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1cef7-147">The camera position and orientation is passed in and is used for the playspace painting process, described above.</span></span>
* <span data-ttu-id="1cef7-148">**GeneratePlayspace_RequestFinish**: Se llama para finalizar la playspace.</span><span class="sxs-lookup"><span data-stu-id="1cef7-148">**GeneratePlayspace_RequestFinish**: Called to finalize the playspace.</span></span> <span data-ttu-id="1cef7-149">Se usarán las áreas que "pintadas" durante la fase de análisis para definir y bloquear el playspace.</span><span class="sxs-lookup"><span data-stu-id="1cef7-149">This will use the areas “painted” during the scan phase to define and lock the playspace.</span></span> <span data-ttu-id="1cef7-150">La aplicación puede consultar las estadísticas durante el análisis fase, así como consultar la malla personalizada para proporcionar comentarios del usuario.</span><span class="sxs-lookup"><span data-stu-id="1cef7-150">The application can query statistics during the scanning phase as well as query the custom mesh for providing user feedback.</span></span>
* <span data-ttu-id="1cef7-151">**Import_UnderstandingMesh**: Durante la detección, la **SpatialUnderstandingCustomMesh** comportamiento proporcionado por el módulo y se coloca en el prefabricado verá descripción consultará periódicamente la malla personalizada generada por el proceso.</span><span class="sxs-lookup"><span data-stu-id="1cef7-151">**Import_UnderstandingMesh**: During scanning, the **SpatialUnderstandingCustomMesh** behavior provided by the module and placed on the understanding prefab will periodically query the custom mesh generated by the process.</span></span> <span data-ttu-id="1cef7-152">Además, esto se hace una vez más después de que se ha finalizado el análisis.</span><span class="sxs-lookup"><span data-stu-id="1cef7-152">In addition, this is done once more after scanning has been finalized.</span></span>

<span data-ttu-id="1cef7-153">El flujo de análisis, controlado por la **SpatialUnderstanding** comportamiento llamadas **InitScan**, a continuación, **UpdateScan** cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="1cef7-153">The scanning flow, driven by the **SpatialUnderstanding** behavior calls **InitScan**, then **UpdateScan** each frame.</span></span> <span data-ttu-id="1cef7-154">Cuando informa de la consulta de estadísticas de cobertura razonable, el usuario puede airtap para llamar a **RequestFinish** para indicar el final de la fase de análisis.</span><span class="sxs-lookup"><span data-stu-id="1cef7-154">When the statistics query reports reasonable coverage, the user can airtap to call **RequestFinish** to indicate the end of the scanning phase.</span></span> <span data-ttu-id="1cef7-155">**UpdateScan** continúa llamada hasta que devueltos es el valor indica que el archivo DLL ha completado el procesamiento.</span><span class="sxs-lookup"><span data-stu-id="1cef7-155">**UpdateScan** continues to be called until it’s return value indicates that the DLL has completed processing.</span></span>

## <a name="the-queries"></a><span data-ttu-id="1cef7-156">Las consultas</span><span class="sxs-lookup"><span data-stu-id="1cef7-156">The queries</span></span>

<span data-ttu-id="1cef7-157">Una vez completado el análisis, podrá tener acceso a tres tipos diferentes de las consultas en la interfaz:</span><span class="sxs-lookup"><span data-stu-id="1cef7-157">Once the scan is complete, you'll be able to access three different types of queries in the interface:</span></span>
* <span data-ttu-id="1cef7-158">**Las consultas de topología**: Estas son las consultas que se basan en la topología de la sala digitalizada.</span><span class="sxs-lookup"><span data-stu-id="1cef7-158">**Topology queries**: These are fast queries that are based on the topology of the scanned room.</span></span>
* <span data-ttu-id="1cef7-159">**Las consultas de forma**: Estos usan los resultados de las consultas de topología para buscar las superficies horizontales que son una coincidencia acertada a formas personalizadas que defina.</span><span class="sxs-lookup"><span data-stu-id="1cef7-159">**Shape queries**: These utilize the results of your topology queries to find horizontal surfaces that are a good match to custom shapes that you define.</span></span>
* <span data-ttu-id="1cef7-160">**Consultas de selección de ubicación de objeto**: Estas son las consultas más complejas que buscar la ubicación de ajuste perfecto basándose en un conjunto de reglas y restricciones para el objeto.</span><span class="sxs-lookup"><span data-stu-id="1cef7-160">**Object placement queries**: These are more complex queries that find the best-fit location based on a set of rules and constraints for the object.</span></span>

<span data-ttu-id="1cef7-161">Además de las tres consultas principales, hay una interfaz de detalles que se puede utilizar para recuperar tipos de superficie etiquetados y se puede copiar una malla de sala estanca personalizado.</span><span class="sxs-lookup"><span data-stu-id="1cef7-161">In addition to the three primary queries, there is a raycasting interface which can be used to retrieve tagged surface types and a custom watertight room mesh can be copied out.</span></span>

### <a name="topology-queries"></a><span data-ttu-id="1cef7-162">Consultas de topología</span><span class="sxs-lookup"><span data-stu-id="1cef7-162">Topology queries</span></span>

<span data-ttu-id="1cef7-163">En el archivo DLL, el Administrador de la topología controla etiquetado del entorno.</span><span class="sxs-lookup"><span data-stu-id="1cef7-163">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="1cef7-164">Como se mencionó anteriormente, gran parte de los datos se almacena en surfels, que están dentro de un volumen voxel.</span><span class="sxs-lookup"><span data-stu-id="1cef7-164">As mentioned above, much of the data is stored within surfels, which are contained within a voxel volume.</span></span> <span data-ttu-id="1cef7-165">Además, el **PlaySpaceInfos** estructura se usa para almacenar información sobre la playspace, incluida la alineación del mundo (más detalles en este tema), floor y ceiling de alto.</span><span class="sxs-lookup"><span data-stu-id="1cef7-165">In addition, the **PlaySpaceInfos** structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span>

<span data-ttu-id="1cef7-166">Se utiliza la heurística para determinar las paredes, ceiling y floor.</span><span class="sxs-lookup"><span data-stu-id="1cef7-166">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="1cef7-167">Por ejemplo, la superficie más grande y más baja horizontal con más de 1 área expuesta de m2 se considera el suelo.</span><span class="sxs-lookup"><span data-stu-id="1cef7-167">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="1cef7-168">Tenga en cuenta que la ruta de acceso de la cámara durante el proceso de análisis también se usa en este proceso.</span><span class="sxs-lookup"><span data-stu-id="1cef7-168">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="1cef7-169">Un subconjunto de consultas expuestas por el Administrador de topología se exponen fuera a través de la DLL.</span><span class="sxs-lookup"><span data-stu-id="1cef7-169">A subset of the queries exposed by the Topology manager are exposed out through the DLL.</span></span> <span data-ttu-id="1cef7-170">Las consultas de topología expuestas son las siguientes:</span><span class="sxs-lookup"><span data-stu-id="1cef7-170">The exposed topology queries are as follows:</span></span>
* <span data-ttu-id="1cef7-171">QueryTopology_FindPositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="1cef7-171">QueryTopology_FindPositionsOnWalls</span></span>
* <span data-ttu-id="1cef7-172">QueryTopology_FindLargePositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="1cef7-172">QueryTopology_FindLargePositionsOnWalls</span></span>
* <span data-ttu-id="1cef7-173">QueryTopology_FindLargestWall</span><span class="sxs-lookup"><span data-stu-id="1cef7-173">QueryTopology_FindLargestWall</span></span>
* <span data-ttu-id="1cef7-174">QueryTopology_FindPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="1cef7-174">QueryTopology_FindPositionsOnFloor</span></span>
* <span data-ttu-id="1cef7-175">QueryTopology_FindLargestPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="1cef7-175">QueryTopology_FindLargestPositionsOnFloor</span></span>
* <span data-ttu-id="1cef7-176">QueryTopology_FindPositionsSittable</span><span class="sxs-lookup"><span data-stu-id="1cef7-176">QueryTopology_FindPositionsSittable</span></span>

<span data-ttu-id="1cef7-177">Cada una de las consultas tiene un conjunto de parámetros, el tipo de consulta específicos.</span><span class="sxs-lookup"><span data-stu-id="1cef7-177">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="1cef7-178">En el ejemplo siguiente, el usuario especifica el alto mínimo anc & ho del volumen deseado, el alto mínimo de la selección de ubicación por encima el suelo y la cantidad mínima de limpieza delante el volumen.</span><span class="sxs-lookup"><span data-stu-id="1cef7-178">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="1cef7-179">Todas las medidas son en metros.</span><span class="sxs-lookup"><span data-stu-id="1cef7-179">All measurements are in meters.</span></span>




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="1cef7-180">Cada una de estas consultas toma una matriz asignada previamente de **TopologyResult** estructuras.</span><span class="sxs-lookup"><span data-stu-id="1cef7-180">Each of these queries takes a pre-allocated array of **TopologyResult** structures.</span></span> <span data-ttu-id="1cef7-181">El **locationCount** parámetro especifica la longitud de la matriz pasada.</span><span class="sxs-lookup"><span data-stu-id="1cef7-181">The **locationCount** parameter specifies the length of the passed-in array.</span></span> <span data-ttu-id="1cef7-182">El valor devuelto indica el número de ubicaciones devueltas.</span><span class="sxs-lookup"><span data-stu-id="1cef7-182">The return value reports the number of returned locations.</span></span> <span data-ttu-id="1cef7-183">Este número nunca es mayor que en el pasado **locationCount** parámetro.</span><span class="sxs-lookup"><span data-stu-id="1cef7-183">This number is never greater than the passed-in **locationCount** parameter.</span></span>

<span data-ttu-id="1cef7-184">El **TopologyResult** contiene la posición central de las dimensiones del espacio se encuentra, la dirección opuesta (es decir, normal) y el volumen devuelto.</span><span class="sxs-lookup"><span data-stu-id="1cef7-184">The **TopologyResult** contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

<span data-ttu-id="1cef7-185">Tenga en cuenta que en el ejemplo de Unity, cada una de estas consultas está vinculado a un botón en el panel de interfaz de usuario virtual.</span><span class="sxs-lookup"><span data-stu-id="1cef7-185">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="1cef7-186">El disco duro de ejemplo códigos de los parámetros para cada una de estas consultas para valores razonables.</span><span class="sxs-lookup"><span data-stu-id="1cef7-186">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="1cef7-187">Consulte *SpaceVisualizer.cs* en el código de ejemplo para obtener más ejemplos.</span><span class="sxs-lookup"><span data-stu-id="1cef7-187">See *SpaceVisualizer.cs* in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="1cef7-188">Consultas de forma</span><span class="sxs-lookup"><span data-stu-id="1cef7-188">Shape queries</span></span>

<span data-ttu-id="1cef7-189">Dentro de la DLL, el analizador de forma (**ShapeAnalyzer_W**) usa el analizador de topología para coincidir con las formas personalizadas definidas por el usuario.</span><span class="sxs-lookup"><span data-stu-id="1cef7-189">Inside of the DLL, the shape analyzer (**ShapeAnalyzer_W**) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="1cef7-190">El ejemplo de Unity tiene un conjunto predefinido de formas que se muestran en el menú de la consulta, en la pestaña de la forma.</span><span class="sxs-lookup"><span data-stu-id="1cef7-190">The Unity sample has a pre-defined set of shapes which are shown in the query menu, on the shape tab.</span></span>

<span data-ttu-id="1cef7-191">Tenga en cuenta que el análisis de forma funciona en las superficies horizontales.</span><span class="sxs-lookup"><span data-stu-id="1cef7-191">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="1cef7-192">Por ejemplo, un sofá, se define por la superficie del asiento sin formato y la parte superior plana de vuelta el sofá.</span><span class="sxs-lookup"><span data-stu-id="1cef7-192">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="1cef7-193">La consulta shape busca dos superficies de un intervalo de tamaño, el alto y el aspecto específico, con las dos superficies alineado y conectado.</span><span class="sxs-lookup"><span data-stu-id="1cef7-193">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="1cef7-194">Con la terminología de API, el asiento del sofá y la parte superior de la parte posterior del sofá son dar forma a los componentes y la alineación de los requisitos son las restricciones de componentes de forma.</span><span class="sxs-lookup"><span data-stu-id="1cef7-194">Using the APIs terminology, the couch seat and the top of the back of the couch are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="1cef7-195">Una consulta de ejemplo que se define en el ejemplo de Unity (**ShapeDefinition.cs**), para objetos "sittable" es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="1cef7-195">An example query defined in the Unity sample (**ShapeDefinition.cs**), for “sittable” objects is as follows:</span></span>




```
shapeComponents = new List<ShapeComponent>()
     {
          new ShapeComponent(
               new List<ShapeComponentConstraint>()
               {
                    ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
                    ShapeComponentConstraint.Create_SurfaceCount_Min(1),
                    ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
               }),
     };
     AddShape("Sittable", shapeComponents);
```

<span data-ttu-id="1cef7-196">Cada consulta shape se define mediante un conjunto de componentes de forma, cada uno con un conjunto de restricciones de componente y un conjunto de restricciones de forma que se enumera las dependencias entre los componentes.</span><span class="sxs-lookup"><span data-stu-id="1cef7-196">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which lists dependencies between the components.</span></span> <span data-ttu-id="1cef7-197">En este ejemplo incluye tres restricciones en una definición de componente único y sin restricciones de forma entre los componentes (como hay solo un componente).</span><span class="sxs-lookup"><span data-stu-id="1cef7-197">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="1cef7-198">En cambio, la forma del sofá tiene dos componentes de la forma y cuatro de las restricciones de forma.</span><span class="sxs-lookup"><span data-stu-id="1cef7-198">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="1cef7-199">Tenga en cuenta que los componentes se identifican por su índice en la lista de componentes del usuario (0 y 1 en este ejemplo).</span><span class="sxs-lookup"><span data-stu-id="1cef7-199">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

<span data-ttu-id="1cef7-200">Se proporcionan funciones de contenedor en el módulo de Unity para la creación fácil de definiciones de forma personalizada.</span><span class="sxs-lookup"><span data-stu-id="1cef7-200">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="1cef7-201">Encontrará la lista completa de las restricciones de componente y la forma en **SpatialUnderstandingDll.cs** dentro de la **ShapeComponentConstraint** y **ShapeConstraint** estructuras.</span><span class="sxs-lookup"><span data-stu-id="1cef7-201">The full list of component and shape constraints can be found in **SpatialUnderstandingDll.cs** within the **ShapeComponentConstraint** and the **ShapeConstraint** structures.</span></span>

![El rectángulo azul resalta los resultados de la consulta shape silla.](images/chair-shape-query-500px.png)

<span data-ttu-id="1cef7-203">El rectángulo azul resalta los resultados de la consulta shape silla.</span><span class="sxs-lookup"><span data-stu-id="1cef7-203">The blue rectangle highlights the results of the chair shape query.</span></span>



### <a name="object-placement-solver"></a><span data-ttu-id="1cef7-204">Solucionador de selección de ubicación del objeto</span><span class="sxs-lookup"><span data-stu-id="1cef7-204">Object placement solver</span></span>

<span data-ttu-id="1cef7-205">Las consultas de selección de ubicación del objeto pueden utilizarse para identificar las ubicaciones ideales en la sala física para colocar los objetos.</span><span class="sxs-lookup"><span data-stu-id="1cef7-205">Object placement queries can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="1cef7-206">El solucionador encontrará la ubicación de ajuste perfecto dada las restricciones y reglas de objetos.</span><span class="sxs-lookup"><span data-stu-id="1cef7-206">The solver will find the best-fit location given the object rules and constraints.</span></span> <span data-ttu-id="1cef7-207">Además, las consultas de objeto conservan hasta que se quita el objeto con **Solver_RemoveObject** o **Solver_RemoveAllObjects** llamadas, lo que permite restringida la colocación de varios objetos.</span><span class="sxs-lookup"><span data-stu-id="1cef7-207">In addition, object queries persist until the object is removed with **Solver_RemoveObject** or **Solver_RemoveAllObjects** calls, allowing constrained multi-object placement.</span></span>

<span data-ttu-id="1cef7-208">Las consultas de selección de ubicación del objeto constan de tres partes: un tipo de colocación con parámetros, una lista de reglas y una lista de restricciones.</span><span class="sxs-lookup"><span data-stu-id="1cef7-208">Object placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="1cef7-209">Para ejecutar una consulta, use la siguiente API:</span><span class="sxs-lookup"><span data-stu-id="1cef7-209">To run a query, use the following API:</span></span>




```
public static int Solver_PlaceObject(
                [In] string objectName,
                [In] IntPtr placementDefinition,    // ObjectPlacementDefinition
                [In] int placementRuleCount,
                [In] IntPtr placementRules,         // ObjectPlacementRule
                [In] int constraintCount,
                [In] IntPtr placementConstraints,   // ObjectPlacementConstraint
                [Out] IntPtr placementResult)
```
<span data-ttu-id="1cef7-210">Esta función toma un nombre de objeto, definición de la selección de ubicación y una lista de reglas y restricciones.</span><span class="sxs-lookup"><span data-stu-id="1cef7-210">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="1cef7-211">El C# contenedores proporciona funciones auxiliares para facilitar la construcción de la regla y la restricción de construcción.</span><span class="sxs-lookup"><span data-stu-id="1cef7-211">The C# wrappers provide construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="1cef7-212">La definición de la selección de ubicación contiene el tipo de consulta, es decir, uno de los siguientes:</span><span class="sxs-lookup"><span data-stu-id="1cef7-212">The placement definition contains the query type — that is, one of the following:</span></span>




```
public enum PlacementType
                {
                    Place_OnFloor,
                    Place_OnWall,
                    Place_OnCeiling,
                    Place_OnShape,
                    Place_OnEdge,
                    Place_OnFloorAndCeiling,
                    Place_RandomInAir,
                    Place_InMidAir,
                    Place_UnderFurnitureEdge,
                };
```

<span data-ttu-id="1cef7-213">Cada uno de los tipos de posición tiene un conjunto de parámetros únicos para el tipo.</span><span class="sxs-lookup"><span data-stu-id="1cef7-213">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="1cef7-214">El **ObjectPlacementDefinition** estructura contiene un conjunto de funciones auxiliares estáticos para crear estas definiciones.</span><span class="sxs-lookup"><span data-stu-id="1cef7-214">The **ObjectPlacementDefinition** structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="1cef7-215">Por ejemplo, para encontrar un lugar para colocar un objeto en el suelo, puede usar la función siguiente:</span><span class="sxs-lookup"><span data-stu-id="1cef7-215">For example, to find a place to put an object on the floor, you can use the following function:</span></span> 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

<span data-ttu-id="1cef7-216">Además del tipo de selección de ubicación, puede proporcionar un conjunto de reglas y restricciones.</span><span class="sxs-lookup"><span data-stu-id="1cef7-216">In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="1cef7-217">No se puede infringir las reglas.</span><span class="sxs-lookup"><span data-stu-id="1cef7-217">Rules cannot be violated.</span></span> <span data-ttu-id="1cef7-218">Ubicaciones de posible selección de ubicación que cumplen el tipo y las reglas están optimizadas, a continuación, en el conjunto de restricciones para seleccionar la ubicación de la ubicación óptima.</span><span class="sxs-lookup"><span data-stu-id="1cef7-218">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints to select the optimal placement location.</span></span> <span data-ttu-id="1cef7-219">Cada una de las reglas y restricciones se puede crear las funciones de creación estático proporcionado.</span><span class="sxs-lookup"><span data-stu-id="1cef7-219">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="1cef7-220">A continuación, se proporciona una función de construcción de restricción y regla de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="1cef7-220">An example rule and constraint construction function is provided below.</span></span>




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="1cef7-221">La siguiente consulta de selección de ubicación de objeto está buscando un lugar para colocar un cubo de la mitad del medidor en el borde de una superficie, fuera otro previamente colocar objetos y cerca del centro de la sala.</span><span class="sxs-lookup"><span data-stu-id="1cef7-221">The object placement query below is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>




```
List<ObjectPlacementRule> rules = 
          new List<ObjectPlacementRule>() {
               ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
          };

     List<ObjectPlacementConstraint> constraints = 
          new List<ObjectPlacementConstraint> {
               ObjectPlacementConstraint.Create_NearCenter(),
          };

     Solver_PlaceObject(
          “MyCustomObject”,
          new ObjectPlacementDefinition.Create_OnEdge(
          new Vector3(0.25f, 0.25f, 0.25f), 
          new Vector3(0.25f, 0.25f, 0.25f)),
          rules.Count,
          UnderstandingDLL.PinObject(rules.ToArray()),
          constraints.Count,
          UnderstandingDLL.PinObject(constraints.ToArray()),
          UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

<span data-ttu-id="1cef7-222">Si es correcto, un **ObjectPlacementResult** se devuelve la estructura que contiene la posición de colocación, dimensiones y la orientación.</span><span class="sxs-lookup"><span data-stu-id="1cef7-222">If successful, an **ObjectPlacementResult** structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="1cef7-223">Además, la selección de ubicación se agrega a la lista interna de la DLL de objetos colocados.</span><span class="sxs-lookup"><span data-stu-id="1cef7-223">In addition, the placement is added to the DLL’s internal list of placed objects.</span></span> <span data-ttu-id="1cef7-224">Las consultas posteriores de la selección de ubicación tendrá este objeto en la cuenta.</span><span class="sxs-lookup"><span data-stu-id="1cef7-224">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="1cef7-225">El **LevelSolver.cs** archivo en el ejemplo de Unity contiene más de las consultas de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="1cef7-225">The **LevelSolver.cs** file in the Unity sample contains more example queries.</span></span>

![Los cuadros azules muestran el resultado de tres consultas del lugar en el piso con reglas de "fuera de la posición de la cámara".](images/away-from-camera-position-500px.png)

<span data-ttu-id="1cef7-227">Los cuadros azules muestran el resultado de tres consultas del lugar en el piso con reglas de "fuera de la posición de la cámara".</span><span class="sxs-lookup"><span data-stu-id="1cef7-227">The blue boxes show the result from three Place On Floor queries with "away from camera position" rules.</span></span>


<span data-ttu-id="1cef7-228">**Sugerencias:**</span><span class="sxs-lookup"><span data-stu-id="1cef7-228">**Tips:**</span></span>
* <span data-ttu-id="1cef7-229">Al resolver para la ubicación de colocación de varios objetos necesarios para un escenario de aplicación o nivel, solucione primero objetos grandes e indispensables para maximizar la probabilidad de que se puede encontrar un espacio.</span><span class="sxs-lookup"><span data-stu-id="1cef7-229">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects to maximize the probability that a space can be found.</span></span>
* <span data-ttu-id="1cef7-230">Es importante el orden de selección de ubicación.</span><span class="sxs-lookup"><span data-stu-id="1cef7-230">Placement order is important.</span></span> <span data-ttu-id="1cef7-231">Si no se puede encontrar las selecciones de ubicación del objeto, intente configuraciones menos restringidas.</span><span class="sxs-lookup"><span data-stu-id="1cef7-231">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="1cef7-232">Tener un conjunto de configuraciones de reserva es fundamental para admitir la funcionalidad en muchas configuraciones de espacio.</span><span class="sxs-lookup"><span data-stu-id="1cef7-232">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="1cef7-233">Ray conversión</span><span class="sxs-lookup"><span data-stu-id="1cef7-233">Ray casting</span></span>

<span data-ttu-id="1cef7-234">Además de las tres consultas principales, una interfaz de la conversión de ray puede usarse para recuperar tipos de superficie etiquetados y se puede copiar una malla playspace estanca personalizado espera después de haber analizado y finaliza, la sala de etiquetas se hayan generado internamente para superficies como el Floor, ceiling y paredes.</span><span class="sxs-lookup"><span data-stu-id="1cef7-234">In addition to the three primary queries, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="1cef7-235">El **PlayspaceRaycast** función toma un rayo y devuelve si el rayo entra en conflicto con una superficie conocida y si es así, obtener información acerca de la que se muestran en forma de un **RaycastResult**.</span><span class="sxs-lookup"><span data-stu-id="1cef7-235">The **PlayspaceRaycast** function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a **RaycastResult**.</span></span> 


```
struct RaycastResult
     {
          enum SurfaceTypes
          {
               Invalid, // No intersection
               Other,
               Floor,
               FloorLike,         // Not part of the floor topology, 
                                  //     but close to the floor and looks like the floor
               Platform,          // Horizontal platform between the ground and 
                                  //     the ceiling
               Ceiling,
               WallExternal,
               WallLike,          // Not part of the external wall surface, 
                                  //     but vertical surface that looks like a 
                                  //    wall structure
               };
               SurfaceTypes SurfaceType;
               float SurfaceArea;   // Zero if unknown 
                                        //  (i.e. if not part of the topology analysis)
               DirectX::XMFLOAT3 IntersectPoint;
               DirectX::XMFLOAT3 IntersectNormal;
     };
```

<span data-ttu-id="1cef7-236">Internamente, el raycast es calculado con respecto a la representación de voxel calculada 8cm al cubo de la playspace.</span><span class="sxs-lookup"><span data-stu-id="1cef7-236">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="1cef7-237">Cada voxel contiene un conjunto de elementos de superficie con datos de la topología procesados (también conocido como surfels).</span><span class="sxs-lookup"><span data-stu-id="1cef7-237">Each voxel contains a set of surface elements with processed topology data (also known as surfels).</span></span> <span data-ttu-id="1cef7-238">Se comparan los surfels dentro de la celda voxel intersectado y la mejor coincidencia utilizada para buscar la información de topología.</span><span class="sxs-lookup"><span data-stu-id="1cef7-238">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="1cef7-239">Estos datos de la topología contienen el etiquetado que se devuelve en forma de la **SurfaceTypes** enum, así como el área expuesta de la superficie de intersección.</span><span class="sxs-lookup"><span data-stu-id="1cef7-239">This topology data contains the labeling returned in the form of the **SurfaceTypes** enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="1cef7-240">En el ejemplo de Unity, el cursor convierte un rayo cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="1cef7-240">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="1cef7-241">En primer lugar, con colisionadores de Unity; en segundo lugar, con representación de mundo del módulo descripción; y por último, frente a los elementos de interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="1cef7-241">First, against Unity’s colliders; second, against the understanding module’s world representation; and finally, against the UI elements.</span></span> <span data-ttu-id="1cef7-242">En esta aplicación, la interfaz de usuario obtiene la prioridad, a continuación, el resultado de la descripción y por último, colisionadores de Unity.</span><span class="sxs-lookup"><span data-stu-id="1cef7-242">In this application, UI gets priority, then the understanding result, and finally, Unity’s colliders.</span></span> <span data-ttu-id="1cef7-243">El **SurfaceType** se notifica como texto situado junto al cursor.</span><span class="sxs-lookup"><span data-stu-id="1cef7-243">The **SurfaceType** is reported as text next to the cursor.</span></span>

![Resultado de Raycast reporting intersección con el límite inferior.](images/raycast-result-500px.jpg)

<span data-ttu-id="1cef7-245">Resultado de Raycast reporting intersección con el límite inferior.</span><span class="sxs-lookup"><span data-stu-id="1cef7-245">Raycast result reporting intersection with the floor.</span></span>


## <a name="get-the-code"></a><span data-ttu-id="1cef7-246">Obtener el código</span><span class="sxs-lookup"><span data-stu-id="1cef7-246">Get the code</span></span>

<span data-ttu-id="1cef7-247">El código abierto y está disponible en [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span><span class="sxs-lookup"><span data-stu-id="1cef7-247">The open-source code is available in [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span></span> <span data-ttu-id="1cef7-248">Háganoslo saber en el [foros para desarrolladores de HoloLens](https://forums.hololens.com/) si usa el código en un proyecto.</span><span class="sxs-lookup"><span data-stu-id="1cef7-248">Let us know on the [HoloLens Developer Forums](https://forums.hololens.com/) if you use the code in a project.</span></span> <span data-ttu-id="1cef7-249">Estamos ansiosos por ver qué hace con él.</span><span class="sxs-lookup"><span data-stu-id="1cef7-249">We can't wait to see what you do with it!</span></span>

## <a name="about-the-author"></a><span data-ttu-id="1cef7-250">Acerca del autor</span><span class="sxs-lookup"><span data-stu-id="1cef7-250">About the author</span></span>

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <span data-ttu-id="1cef7-251"><b>Jeff Evertt</b> es director de ingeniería de software que ha trabajado en HoloLens desde los primeros días de incubación a la experiencia de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="1cef7-251"><b>Jeff Evertt</b> is a software engineering lead who has worked on HoloLens since the early days, from incubation to experience development.</span></span> <span data-ttu-id="1cef7-252">Antes de HoloLens, trabajó en el Xbox Kinect y en el sector de juegos en una amplia variedad de plataformas y juegos.</span><span class="sxs-lookup"><span data-stu-id="1cef7-252">Before HoloLens, he worked on the Xbox Kinect and in the games industry on a wide variety of platforms and games.</span></span> <span data-ttu-id="1cef7-253">Juan es un apasionado de las cosas con luces parpadeantes que vaya Bip, gráficos y robótica.</span><span class="sxs-lookup"><span data-stu-id="1cef7-253">Jeff is passionate about robotics, graphics, and things with flashy lights that go beep.</span></span> <span data-ttu-id="1cef7-254">Le encanta aprender cosas nuevas y trabajar en software, hardware y especialmente en el espacio de intersección de los dos.</span><span class="sxs-lookup"><span data-stu-id="1cef7-254">He enjoys learning new things and working on software, hardware, and particularly in the space where the two intersect.</span></span></td>
</tr>
</table>



## <a name="see-also"></a><span data-ttu-id="1cef7-255">Vea también</span><span class="sxs-lookup"><span data-stu-id="1cef7-255">See also</span></span>
* [<span data-ttu-id="1cef7-256">Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="1cef7-256">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="1cef7-257">Diseño de la asignación espacial</span><span class="sxs-lookup"><span data-stu-id="1cef7-257">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="1cef7-258">Visualización de análisis de sala</span><span class="sxs-lookup"><span data-stu-id="1cef7-258">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="1cef7-259">MixedRealityToolkit-Unity</span><span class="sxs-lookup"><span data-stu-id="1cef7-259">MixedRealityToolkit-Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="1cef7-260">Asobo Studio: Lecciones desde la primera línea de desarrollo de HoloLens</span><span class="sxs-lookup"><span data-stu-id="1cef7-260">Asobo Studio: Lessons from the frontline of HoloLens development</span></span>](http://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
