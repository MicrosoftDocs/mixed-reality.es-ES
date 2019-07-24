---
title: 'Caso práctico: ampliación de las funcionalidades de asignación espacial de HoloLens'
description: Al crear las primeras aplicaciones para Microsoft HoloLens, estábamos ansiosos por ver hasta qué punto se podían introducir los límites de la asignación espacial en el dispositivo.
author: jevertt
ms.author: jevertt
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, asignación espacial
ms.openlocfilehash: 602b629afa5900ff34c28b3a3a32725af06590b7
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522710"
---
# <a name="case-study---expanding-the-spatial-mapping-capabilities-of-hololens"></a><span data-ttu-id="78411-104">Caso práctico: ampliación de las funcionalidades de asignación espacial de HoloLens</span><span class="sxs-lookup"><span data-stu-id="78411-104">Case study - Expanding the spatial mapping capabilities of HoloLens</span></span>

<span data-ttu-id="78411-105">Al crear las primeras aplicaciones para Microsoft HoloLens, estábamos ansiosos por ver hasta qué punto se podían introducir los límites de la asignación espacial en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="78411-105">When creating our first apps for Microsoft HoloLens, we were eager to see just how far we could push the boundaries of spatial mapping on the device.</span></span> <span data-ttu-id="78411-106">Jeff Evertt, Ingeniero de software en Microsoft Studios, explica cómo se desarrolló una nueva tecnología fuera de la necesidad de tener más control sobre cómo se colocan los hologramas en el entorno real de un usuario.</span><span class="sxs-lookup"><span data-stu-id="78411-106">Jeff Evertt, a software engineer at Microsoft Studios, explains how a new technology was developed out of the need for more control over how holograms are placed in a user's real-world environment.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="78411-107">Ver el vídeo</span><span class="sxs-lookup"><span data-stu-id="78411-107">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/iUmTi3_Ynus]

## <a name="beyond-spatial-mapping"></a><span data-ttu-id="78411-108">Más allá de la asignación espacial</span><span class="sxs-lookup"><span data-stu-id="78411-108">Beyond spatial mapping</span></span>

<span data-ttu-id="78411-109">Mientras estábamos trabajando en [fragmentos](https://www.microsoft.com/p/fragments/9nblggh5ggm8) y [conkers jóvenes](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), dos de los primeros juegos de HoloLens, encontramos que cuando estábamos realizando la selección de ubicación de los hologramas en el mundo físico, necesitábamos un nivel más alto de comprensión sobre el entorno.</span><span class="sxs-lookup"><span data-stu-id="78411-109">While we were working on [Fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8) and [Young Conker](https://www.microsoft.com/p/young-conker/9nblggh5ggk1), two of the first games for HoloLens, we found that when we were doing procedural placement of holograms in the physical world, we needed a higher level of understanding about the user's environment.</span></span> <span data-ttu-id="78411-110">Cada juego tenía sus propias necesidades específicas de selección de Ubicación: Por ejemplo, en los fragmentos queríamos poder distinguir entre diferentes superficies (como el piso o una tabla) para colocar pistas en las ubicaciones correspondientes.</span><span class="sxs-lookup"><span data-stu-id="78411-110">Each game had its own specific placement needs: In Fragments, for example, we wanted to be able to distinguish between different surfaces—such as the floor or a table—to place clues in relevant locations.</span></span> <span data-ttu-id="78411-111">También queríamos poder identificar las superficies en las que podrían sentarse los caracteres holográficas de tamaño real, como un sofá o una silla.</span><span class="sxs-lookup"><span data-stu-id="78411-111">We also wanted to be able to identify surfaces that life-size holographic characters could sit on, such as a couch or a chair.</span></span> <span data-ttu-id="78411-112">En jóvenes Conker, queríamos que Conker y sus oponentes pudieran usar superficies levantadas en el salón de un jugador como plataformas.</span><span class="sxs-lookup"><span data-stu-id="78411-112">In Young Conker, we wanted Conker and his opponents to be able to use raised surfaces in a player's room as platforms.</span></span>

<span data-ttu-id="78411-113">[Asobo Studios](http://www.asobostudio.com/index.html), nuestro asociado de desarrollo para estos juegos, se enfrentó a este problema y creaba una tecnología que amplía las capacidades de asignación espacial de HoloLens.</span><span class="sxs-lookup"><span data-stu-id="78411-113">[Asobo Studios](http://www.asobostudio.com/index.html), our development partner for these games, faced this problem head-on and created a technology that extends the spatial mapping capabilities of HoloLens.</span></span> <span data-ttu-id="78411-114">Con esto, podríamos analizar la habitación de un jugador e identificar superficies como paredes, mesas, sillas y suelos.</span><span class="sxs-lookup"><span data-stu-id="78411-114">Using this, we could analyze a player's room and identify surfaces such as walls, tables, chairs, and floors.</span></span> <span data-ttu-id="78411-115">También nos permitió optimizar con respecto a un conjunto de restricciones para determinar la mejor ubicación de los objetos holográficas.</span><span class="sxs-lookup"><span data-stu-id="78411-115">It also gave us the ability to optimize against a set of constraints to determine the best placement for holographic objects.</span></span>

## <a name="the-spatial-understanding-code"></a><span data-ttu-id="78411-116">Código espacial de comprensión</span><span class="sxs-lookup"><span data-stu-id="78411-116">The spatial understanding code</span></span>

<span data-ttu-id="78411-117">Hemos tomado el código original de Asobo y hemos creado una biblioteca que encapsula esta tecnología.</span><span class="sxs-lookup"><span data-stu-id="78411-117">We took Asobo's original code and created a library that encapsulates this technology.</span></span> <span data-ttu-id="78411-118">Microsoft y Asobo ahora tienen código abierto y lo ponen a disposición de [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) para que pueda usarlos en sus propios proyectos.</span><span class="sxs-lookup"><span data-stu-id="78411-118">Microsoft and Asobo have now open-sourced this code and made it available on [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialMapping) for you to use in your own projects.</span></span> <span data-ttu-id="78411-119">Se incluye todo el código fuente, lo que le permite personalizarlo según sus necesidades y compartir sus mejoras con la comunidad.</span><span class="sxs-lookup"><span data-stu-id="78411-119">All the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="78411-120">El código de C++ Solver se ha encapsulado en un archivo dll de UWP y expuesto a Unity con un [recurso prefabricado de colocación incluido en MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).</span><span class="sxs-lookup"><span data-stu-id="78411-120">The code for the C++ solver has been wrapped into a UWP DLL and exposed to Unity with a [drop-in prefab contained within MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/SpatialUnderstanding).</span></span>

<span data-ttu-id="78411-121">En el ejemplo de Unity se incluyen muchas consultas útiles que le permitirán buscar espacios vacíos en las paredes, colocar objetos en el límite superior o en espacios grandes en el suelo, identificar los lugares en los que se colocan los caracteres y una gran cantidad de consultas espaciales.</span><span class="sxs-lookup"><span data-stu-id="78411-121">There are many useful queries included in the Unity sample that will allow you to find empty spaces on walls, place objects on the ceiling or on large spaces on the floor, identify places for characters to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="78411-122">Aunque la solución de asignación espacial proporcionada por HoloLens está diseñada para ser lo suficientemente genérica como para satisfacer las necesidades de la gama completa de espacios problemáticos, el módulo de comprensión espacial se creó para admitir las necesidades de dos juegos específicos.</span><span class="sxs-lookup"><span data-stu-id="78411-122">While the spatial mapping solution provided by HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="78411-123">Como tal, su solución está estructurada en torno a un proceso específico y un conjunto de suposiciones:</span><span class="sxs-lookup"><span data-stu-id="78411-123">As such, its solution is structured around a specific process and set of assumptions:</span></span>
* <span data-ttu-id="78411-124">**Playspace de tamaño fijo**: El usuario especifica el tamaño máximo de Playspace en la llamada init.</span><span class="sxs-lookup"><span data-stu-id="78411-124">**Fixed size playspace**: The user specifies the maximum playspace size in the init call.</span></span>
* <span data-ttu-id="78411-125">**Proceso de examen único**: El proceso requiere una fase de detección discreta en la que el usuario se desplazará, definiendo el Playspace.</span><span class="sxs-lookup"><span data-stu-id="78411-125">**One-time scan process**: The process requires a discrete scanning phase where the user walks around, defining the playspace.</span></span> <span data-ttu-id="78411-126">Las funciones de consulta no funcionarán hasta que se haya finalizado el examen.</span><span class="sxs-lookup"><span data-stu-id="78411-126">Query functions will not function until after the scan has been finalized.</span></span>
* <span data-ttu-id="78411-127">**Playspace controlado por el usuario "Painting"** : Durante la fase de examen, el usuario se mueve y busca en torno a Playspace, con lo que se pintan de forma eficaz las áreas que se deben incluir.</span><span class="sxs-lookup"><span data-stu-id="78411-127">**User driven playspace “painting”**: During the scanning phase, the user moves and looks around the playspace, effectively painting the areas which should be included.</span></span> <span data-ttu-id="78411-128">La malla generada es importante para proporcionar comentarios de los usuarios durante esta fase.</span><span class="sxs-lookup"><span data-stu-id="78411-128">The generated mesh is important to provide user feedback during this phase.</span></span>
* <span data-ttu-id="78411-129">**Instalación en casa o en Office**: Las funciones de consulta están diseñadas en torno a superficies planas y paredes en los ángulos rectos.</span><span class="sxs-lookup"><span data-stu-id="78411-129">**Indoors home or office setup**: The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="78411-130">Se trata de una limitación flexible.</span><span class="sxs-lookup"><span data-stu-id="78411-130">This is a soft limitation.</span></span> <span data-ttu-id="78411-131">Sin embargo, durante la fase de examen, se completa un análisis de eje principal para optimizar la teselación de malla junto con el eje principal y el secundario.</span><span class="sxs-lookup"><span data-stu-id="78411-131">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="78411-132">Proceso de detección de salas</span><span class="sxs-lookup"><span data-stu-id="78411-132">Room Scanning Process</span></span>

<span data-ttu-id="78411-133">Al cargar el módulo de comprensión espacial, lo primero que hará es examinar el espacio, de modo que todas las superficies que se pueden usar (por ejemplo, el piso, el techo y las paredes) se identifican y se etiquetan.</span><span class="sxs-lookup"><span data-stu-id="78411-133">When you load the spatial understanding module, the first thing you'll do is scan your space, so all the usable surfaces—such as the floor, ceiling, and walls—are identified and labeled.</span></span> <span data-ttu-id="78411-134">Durante el proceso de digitalización, mire el salón y "pinte" las áreas que deben incluirse en el análisis.</span><span class="sxs-lookup"><span data-stu-id="78411-134">During the scanning process, you look around your room and "paint' the areas that should be included in the scan.</span></span>

<span data-ttu-id="78411-135">La malla que se ha detectado durante esta fase es una parte importante de los comentarios visuales que permite a los usuarios saber qué partes del salón se están analizando.</span><span class="sxs-lookup"><span data-stu-id="78411-135">The mesh seen during this phase is an important piece of visual feedback that lets users know what parts of the room are being scanned.</span></span> <span data-ttu-id="78411-136">El archivo DLL del módulo espacial Understanding almacena internamente Playspace como una cuadrícula de cubos voxel de 8cm de tamaño.</span><span class="sxs-lookup"><span data-stu-id="78411-136">The DLL for the spatial understanding module internally stores the playspace as a grid of 8cm sized voxel cubes.</span></span> <span data-ttu-id="78411-137">Durante la parte inicial del análisis, se completa un análisis de componentes principales para determinar los ejes de la habitación.</span><span class="sxs-lookup"><span data-stu-id="78411-137">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="78411-138">Internamente, almacena su espacio voxel alineado con estos ejes.</span><span class="sxs-lookup"><span data-stu-id="78411-138">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="78411-139">Una malla se genera aproximadamente cada segundo mediante la extracción de la isosuperficie del volumen voxel.</span><span class="sxs-lookup"><span data-stu-id="78411-139">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span>

![Malla espacial de asignación en blanco y descripción de la malla Playspace en verde](images/spatial-mapping-500px.png)

<span data-ttu-id="78411-141">Malla espacial de asignación en blanco y descripción de la malla Playspace en verde</span><span class="sxs-lookup"><span data-stu-id="78411-141">Spatial mapping mesh in white and understanding playspace mesh in green</span></span>



<span data-ttu-id="78411-142">El archivo SpatialUnderstanding.cs incluido administra el proceso de la fase de análisis.</span><span class="sxs-lookup"><span data-stu-id="78411-142">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="78411-143">Llama a las siguientes funciones:</span><span class="sxs-lookup"><span data-stu-id="78411-143">It calls the following functions:</span></span>
* <span data-ttu-id="78411-144">**SpatialUnderstanding_Init**: Se llama una vez al inicio.</span><span class="sxs-lookup"><span data-stu-id="78411-144">**SpatialUnderstanding_Init**: Called once at the start.</span></span>
* <span data-ttu-id="78411-145">**GeneratePlayspace_InitScan**: Indica que debe comenzar la fase de análisis.</span><span class="sxs-lookup"><span data-stu-id="78411-145">**GeneratePlayspace_InitScan**: Indicates that the scan phase should begin.</span></span>
* <span data-ttu-id="78411-146">**GeneratePlayspace_UpdateScan_DynamicScan**: Se llama cada fotograma para actualizar el proceso de examen.</span><span class="sxs-lookup"><span data-stu-id="78411-146">**GeneratePlayspace_UpdateScan_DynamicScan**: Called each frame to update the scanning process.</span></span> <span data-ttu-id="78411-147">La posición y orientación de la cámara se pasa y se usa para el proceso de dibujo de Playspace, descrito anteriormente.</span><span class="sxs-lookup"><span data-stu-id="78411-147">The camera position and orientation is passed in and is used for the playspace painting process, described above.</span></span>
* <span data-ttu-id="78411-148">**GeneratePlayspace_RequestFinish**: Se llama para finalizar Playspace.</span><span class="sxs-lookup"><span data-stu-id="78411-148">**GeneratePlayspace_RequestFinish**: Called to finalize the playspace.</span></span> <span data-ttu-id="78411-149">Se usarán las áreas "pintadas" durante la fase de análisis para definir y bloquear el Playspace.</span><span class="sxs-lookup"><span data-stu-id="78411-149">This will use the areas “painted” during the scan phase to define and lock the playspace.</span></span> <span data-ttu-id="78411-150">La aplicación puede consultar las estadísticas durante la fase de análisis, así como consultar la malla personalizada para proporcionar los comentarios de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="78411-150">The application can query statistics during the scanning phase as well as query the custom mesh for providing user feedback.</span></span>
* <span data-ttu-id="78411-151">**Import_UnderstandingMesh**: Durante el examen, el comportamiento de **SpatialUnderstandingCustomMesh** proporcionado por el módulo y colocado en la descripción de recurso prefabricado periódicamente consultará la malla personalizada generada por el proceso.</span><span class="sxs-lookup"><span data-stu-id="78411-151">**Import_UnderstandingMesh**: During scanning, the **SpatialUnderstandingCustomMesh** behavior provided by the module and placed on the understanding prefab will periodically query the custom mesh generated by the process.</span></span> <span data-ttu-id="78411-152">Además, esto se realiza una vez más después de haber finalizado el examen.</span><span class="sxs-lookup"><span data-stu-id="78411-152">In addition, this is done once more after scanning has been finalized.</span></span>

<span data-ttu-id="78411-153">El flujo de análisis, controlado por el comportamiento de **SpatialUnderstanding** llama a **InitScan**y **UpdateScan** cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="78411-153">The scanning flow, driven by the **SpatialUnderstanding** behavior calls **InitScan**, then **UpdateScan** each frame.</span></span> <span data-ttu-id="78411-154">Cuando la consulta de estadísticas notifica una cobertura razonable, el usuario puede airtap para llamar a **RequestFinish** para indicar el final de la fase de análisis.</span><span class="sxs-lookup"><span data-stu-id="78411-154">When the statistics query reports reasonable coverage, the user can airtap to call **RequestFinish** to indicate the end of the scanning phase.</span></span> <span data-ttu-id="78411-155">**UpdateScan** sigue siendo llamado hasta que su valor devuelto indica que el archivo DLL ha finalizado el procesamiento.</span><span class="sxs-lookup"><span data-stu-id="78411-155">**UpdateScan** continues to be called until it’s return value indicates that the DLL has completed processing.</span></span>

## <a name="the-queries"></a><span data-ttu-id="78411-156">Las consultas</span><span class="sxs-lookup"><span data-stu-id="78411-156">The queries</span></span>

<span data-ttu-id="78411-157">Una vez completado el análisis, podrá tener acceso a tres tipos diferentes de consultas en la interfaz:</span><span class="sxs-lookup"><span data-stu-id="78411-157">Once the scan is complete, you'll be able to access three different types of queries in the interface:</span></span>
* <span data-ttu-id="78411-158">**Consultas de topología**: Se trata de consultas rápidas basadas en la topología de la sala digitalizada.</span><span class="sxs-lookup"><span data-stu-id="78411-158">**Topology queries**: These are fast queries that are based on the topology of the scanned room.</span></span>
* <span data-ttu-id="78411-159">**Consultas de forma**: Estos usan los resultados de las consultas de topología para buscar superficies horizontales que sean una buena coincidencia con las formas personalizadas que defina.</span><span class="sxs-lookup"><span data-stu-id="78411-159">**Shape queries**: These utilize the results of your topology queries to find horizontal surfaces that are a good match to custom shapes that you define.</span></span>
* <span data-ttu-id="78411-160">**Consultas de selección de ubicación de objetos**: Se trata de consultas más complejas que buscan la ubicación con ajuste perfecto en función de un conjunto de reglas y restricciones para el objeto.</span><span class="sxs-lookup"><span data-stu-id="78411-160">**Object placement queries**: These are more complex queries that find the best-fit location based on a set of rules and constraints for the object.</span></span>

<span data-ttu-id="78411-161">Además de las tres consultas principales, hay una interfaz raycasting que se puede usar para recuperar tipos de superficie etiquetada y se puede copiar una malla de sala de estancos personalizada.</span><span class="sxs-lookup"><span data-stu-id="78411-161">In addition to the three primary queries, there is a raycasting interface which can be used to retrieve tagged surface types and a custom watertight room mesh can be copied out.</span></span>

### <a name="topology-queries"></a><span data-ttu-id="78411-162">Consultas de topología</span><span class="sxs-lookup"><span data-stu-id="78411-162">Topology queries</span></span>

<span data-ttu-id="78411-163">En el archivo DLL, el administrador de topología controla el etiquetado del entorno.</span><span class="sxs-lookup"><span data-stu-id="78411-163">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="78411-164">Como se mencionó anteriormente, gran parte de los datos se almacenan en surfels, que están incluidos en un volumen de voxel.</span><span class="sxs-lookup"><span data-stu-id="78411-164">As mentioned above, much of the data is stored within surfels, which are contained within a voxel volume.</span></span> <span data-ttu-id="78411-165">Además, la estructura **PlaySpaceInfos** se usa para almacenar información sobre Playspace, incluida la alineación del mundo (más detalles a continuación), Floor y height.</span><span class="sxs-lookup"><span data-stu-id="78411-165">In addition, the **PlaySpaceInfos** structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span>

<span data-ttu-id="78411-166">La heurística se usa para determinar el piso, el techo y las paredes.</span><span class="sxs-lookup"><span data-stu-id="78411-166">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="78411-167">Por ejemplo, la superficie horizontal más grande y más baja con un área de superficie superior a 1 m2 se considera el piso.</span><span class="sxs-lookup"><span data-stu-id="78411-167">For example, the largest and lowest horizontal surface with greater than 1 m2 surface area is considered the floor.</span></span> <span data-ttu-id="78411-168">Tenga en cuenta que la ruta de acceso de la cámara durante el proceso de digitalización también se usa en este proceso.</span><span class="sxs-lookup"><span data-stu-id="78411-168">Note that the camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="78411-169">Un subconjunto de las consultas expuestas por el administrador de topología se expone a través de la DLL.</span><span class="sxs-lookup"><span data-stu-id="78411-169">A subset of the queries exposed by the Topology manager are exposed out through the DLL.</span></span> <span data-ttu-id="78411-170">Las consultas de topologías expuestas son las siguientes:</span><span class="sxs-lookup"><span data-stu-id="78411-170">The exposed topology queries are as follows:</span></span>
* <span data-ttu-id="78411-171">QueryTopology_FindPositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="78411-171">QueryTopology_FindPositionsOnWalls</span></span>
* <span data-ttu-id="78411-172">QueryTopology_FindLargePositionsOnWalls</span><span class="sxs-lookup"><span data-stu-id="78411-172">QueryTopology_FindLargePositionsOnWalls</span></span>
* <span data-ttu-id="78411-173">QueryTopology_FindLargestWall</span><span class="sxs-lookup"><span data-stu-id="78411-173">QueryTopology_FindLargestWall</span></span>
* <span data-ttu-id="78411-174">QueryTopology_FindPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="78411-174">QueryTopology_FindPositionsOnFloor</span></span>
* <span data-ttu-id="78411-175">QueryTopology_FindLargestPositionsOnFloor</span><span class="sxs-lookup"><span data-stu-id="78411-175">QueryTopology_FindLargestPositionsOnFloor</span></span>
* <span data-ttu-id="78411-176">QueryTopology_FindPositionsSittable</span><span class="sxs-lookup"><span data-stu-id="78411-176">QueryTopology_FindPositionsSittable</span></span>

<span data-ttu-id="78411-177">Cada una de las consultas tiene un conjunto de parámetros, específico del tipo de consulta.</span><span class="sxs-lookup"><span data-stu-id="78411-177">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="78411-178">En el ejemplo siguiente, el usuario especifica el alto mínimo & ancho del volumen deseado, el alto mínimo de la ubicación por encima del piso y la cantidad mínima de holgura delante del volumen.</span><span class="sxs-lookup"><span data-stu-id="78411-178">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="78411-179">Todas las medidas están en metros.</span><span class="sxs-lookup"><span data-stu-id="78411-179">All measurements are in meters.</span></span>




```
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
          _In_ float minHeightOfWallSpace,
          _In_ float minWidthOfWallSpace,
          _In_ float minHeightAboveFloor,
          _In_ float minFacingClearance,
          _In_ int locationCount,
          _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="78411-180">Cada una de estas consultas toma una matriz preasignada de estructuras **TopologyResult** .</span><span class="sxs-lookup"><span data-stu-id="78411-180">Each of these queries takes a pre-allocated array of **TopologyResult** structures.</span></span> <span data-ttu-id="78411-181">El parámetro **locationCount** especifica la longitud de la matriz pasada.</span><span class="sxs-lookup"><span data-stu-id="78411-181">The **locationCount** parameter specifies the length of the passed-in array.</span></span> <span data-ttu-id="78411-182">El valor devuelto informa del número de ubicaciones devueltas.</span><span class="sxs-lookup"><span data-stu-id="78411-182">The return value reports the number of returned locations.</span></span> <span data-ttu-id="78411-183">Este número nunca es mayor que el parámetro **locationCount** pasado.</span><span class="sxs-lookup"><span data-stu-id="78411-183">This number is never greater than the passed-in **locationCount** parameter.</span></span>

<span data-ttu-id="78411-184">**TopologyResult** contiene la posición central del volumen devuelto, la dirección orientada (es decir, normal) y las dimensiones del espacio encontrado.</span><span class="sxs-lookup"><span data-stu-id="78411-184">The **TopologyResult** contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>




```
struct TopologyResult
     {
          DirectX::XMFLOAT3 position;
          DirectX::XMFLOAT3 normal;
          float width;
          float length;
     };
```

<span data-ttu-id="78411-185">Tenga en cuenta que en el ejemplo de Unity, cada una de estas consultas está vinculada a un botón en el panel de interfaz de usuario virtual.</span><span class="sxs-lookup"><span data-stu-id="78411-185">Note that in the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="78411-186">En el ejemplo se codifican los parámetros de cada una de estas consultas en valores razonables.</span><span class="sxs-lookup"><span data-stu-id="78411-186">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="78411-187">Vea *SpaceVisualizer.CS* en el código de ejemplo para obtener más ejemplos.</span><span class="sxs-lookup"><span data-stu-id="78411-187">See *SpaceVisualizer.cs* in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="78411-188">Consultas de forma</span><span class="sxs-lookup"><span data-stu-id="78411-188">Shape queries</span></span>

<span data-ttu-id="78411-189">Dentro de la DLL, el analizador de formas (**ShapeAnalyzer_W**) utiliza el analizador de topología para buscar coincidencias con las formas personalizadas definidas por el usuario.</span><span class="sxs-lookup"><span data-stu-id="78411-189">Inside of the DLL, the shape analyzer (**ShapeAnalyzer_W**) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="78411-190">El ejemplo de Unity tiene un conjunto predefinido de formas que se muestran en el menú consulta, en la pestaña forma.</span><span class="sxs-lookup"><span data-stu-id="78411-190">The Unity sample has a pre-defined set of shapes which are shown in the query menu, on the shape tab.</span></span>

<span data-ttu-id="78411-191">Tenga en cuenta que el análisis de formas solo funciona en superficies horizontales.</span><span class="sxs-lookup"><span data-stu-id="78411-191">Note that the shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="78411-192">Por ejemplo, un sofá se define mediante la superficie de asiento plana y la parte superior plana del sofá.</span><span class="sxs-lookup"><span data-stu-id="78411-192">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="78411-193">La consulta de forma busca dos superficies de un tamaño, alto y intervalo de aspecto específicos, con las dos superficies alineadas y conectadas.</span><span class="sxs-lookup"><span data-stu-id="78411-193">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="78411-194">Con la terminología de las API, el asiento del sofá y la parte superior del sofá son componentes de forma y los requisitos de alineación son restricciones de componentes de forma.</span><span class="sxs-lookup"><span data-stu-id="78411-194">Using the APIs terminology, the couch seat and the top of the back of the couch are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="78411-195">A continuación se muestra una consulta de ejemplo definida en el ejemplo de Unity (**ShapeDefinition.CS**) para objetos "sittable":</span><span class="sxs-lookup"><span data-stu-id="78411-195">An example query defined in the Unity sample (**ShapeDefinition.cs**), for “sittable” objects is as follows:</span></span>




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

<span data-ttu-id="78411-196">Cada consulta de forma se define mediante un conjunto de componentes de forma, cada uno con un conjunto de restricciones de componentes y un conjunto de restricciones de forma que enumera las dependencias entre los componentes.</span><span class="sxs-lookup"><span data-stu-id="78411-196">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which lists dependencies between the components.</span></span> <span data-ttu-id="78411-197">En este ejemplo se incluyen tres restricciones en una definición de componente único y no hay restricciones de forma entre los componentes (como solo hay un componente).</span><span class="sxs-lookup"><span data-stu-id="78411-197">This example includes three constraints in a single component definition and no shape constraints between components (as there is only one component).</span></span>

<span data-ttu-id="78411-198">En cambio, la forma sofá tiene dos componentes de forma y cuatro restricciones de forma.</span><span class="sxs-lookup"><span data-stu-id="78411-198">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="78411-199">Tenga en cuenta que los componentes se identifican por su índice en la lista de componentes del usuario (0 y 1 en este ejemplo).</span><span class="sxs-lookup"><span data-stu-id="78411-199">Note that components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>




```
shapeConstraints = new List<ShapeConstraint>()
        {
              ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
              ShapeConstraint.Create_RectanglesParallel(0, 1),
              ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
              ShapeConstraint.Create_AtBackOf(1, 0),
        };
```

<span data-ttu-id="78411-200">Las funciones de contenedor se proporcionan en el módulo Unity para facilitar la creación de definiciones de formas personalizadas.</span><span class="sxs-lookup"><span data-stu-id="78411-200">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="78411-201">La lista completa de restricciones de componente y forma se puede encontrar en **SpatialUnderstandingDll.CS** dentro de las estructuras **ShapeComponentConstraint** y **ShapeConstraint** .</span><span class="sxs-lookup"><span data-stu-id="78411-201">The full list of component and shape constraints can be found in **SpatialUnderstandingDll.cs** within the **ShapeComponentConstraint** and the **ShapeConstraint** structures.</span></span>

![El rectángulo azul resalta los resultados de la consulta de forma de silla.](images/chair-shape-query-500px.png)

<span data-ttu-id="78411-203">El rectángulo azul resalta los resultados de la consulta de forma de silla.</span><span class="sxs-lookup"><span data-stu-id="78411-203">The blue rectangle highlights the results of the chair shape query.</span></span>



### <a name="object-placement-solver"></a><span data-ttu-id="78411-204">Selección de ubicación de objetos</span><span class="sxs-lookup"><span data-stu-id="78411-204">Object placement solver</span></span>

<span data-ttu-id="78411-205">Las consultas de selección de ubicación de objetos se pueden usar para identificar las ubicaciones ideales en la habitación física para colocar los objetos.</span><span class="sxs-lookup"><span data-stu-id="78411-205">Object placement queries can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="78411-206">El Solver encontrará la ubicación con ajuste perfecto en función de las reglas y restricciones del objeto.</span><span class="sxs-lookup"><span data-stu-id="78411-206">The solver will find the best-fit location given the object rules and constraints.</span></span> <span data-ttu-id="78411-207">Además, las consultas de objeto se conservan hasta que el objeto se quita con llamadas a **Solver_RemoveObject** o **Solver_RemoveAllObjects** , lo que permite la selección de ubicación de varios objetos restringidos.</span><span class="sxs-lookup"><span data-stu-id="78411-207">In addition, object queries persist until the object is removed with **Solver_RemoveObject** or **Solver_RemoveAllObjects** calls, allowing constrained multi-object placement.</span></span>

<span data-ttu-id="78411-208">Las consultas de selección de ubicación de objetos constan de tres partes: tipo de selección de ubicación con parámetros, una lista de reglas y una lista de restricciones.</span><span class="sxs-lookup"><span data-stu-id="78411-208">Object placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="78411-209">Para ejecutar una consulta, use la siguiente API:</span><span class="sxs-lookup"><span data-stu-id="78411-209">To run a query, use the following API:</span></span>




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
<span data-ttu-id="78411-210">Esta función toma un nombre de objeto, una definición de ubicación y una lista de reglas y restricciones.</span><span class="sxs-lookup"><span data-stu-id="78411-210">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="78411-211">Los C# contenedores proporcionan funciones auxiliares de construcción para facilitar la creación de reglas y restricciones.</span><span class="sxs-lookup"><span data-stu-id="78411-211">The C# wrappers provide construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="78411-212">La definición de ubicación contiene el tipo de consulta, es decir, uno de los siguientes:</span><span class="sxs-lookup"><span data-stu-id="78411-212">The placement definition contains the query type — that is, one of the following:</span></span>




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

<span data-ttu-id="78411-213">Cada uno de los tipos de ubicación tiene un conjunto de parámetros únicos para el tipo.</span><span class="sxs-lookup"><span data-stu-id="78411-213">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="78411-214">La estructura **ObjectPlacementDefinition** contiene un conjunto de funciones auxiliares estáticas para crear estas definiciones.</span><span class="sxs-lookup"><span data-stu-id="78411-214">The **ObjectPlacementDefinition** structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="78411-215">Por ejemplo, para encontrar un lugar donde colocar un objeto en el piso, puede usar la función siguiente:</span><span class="sxs-lookup"><span data-stu-id="78411-215">For example, to find a place to put an object on the floor, you can use the following function:</span></span> 


```
public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims)
```

<span data-ttu-id="78411-216">Además del tipo de selección de ubicación, puede proporcionar un conjunto de reglas y restricciones.</span><span class="sxs-lookup"><span data-stu-id="78411-216">In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="78411-217">No se pueden infringir las reglas.</span><span class="sxs-lookup"><span data-stu-id="78411-217">Rules cannot be violated.</span></span> <span data-ttu-id="78411-218">Las ubicaciones de ubicación posibles que satisfacen el tipo y las reglas se optimizan con el conjunto de restricciones para seleccionar la ubicación de colocación óptima.</span><span class="sxs-lookup"><span data-stu-id="78411-218">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints to select the optimal placement location.</span></span> <span data-ttu-id="78411-219">Cada una de las reglas y restricciones se pueden crear mediante las funciones de creación estáticas proporcionadas.</span><span class="sxs-lookup"><span data-stu-id="78411-219">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="78411-220">A continuación se proporciona una función de ejemplo y una función de construcción de restricciones.</span><span class="sxs-lookup"><span data-stu-id="78411-220">An example rule and constraint construction function is provided below.</span></span>




```
public static ObjectPlacementRule Create_AwayFromPosition(
                    Vector3 position, float minDistance)
               public static ObjectPlacementConstraint Create_NearPoint(
                    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="78411-221">En la consulta de selección de ubicación de objetos siguiente se busca un lugar donde colocar un cubo de media metro en el borde de una superficie, lejos de otros objetos colocados anteriormente y cerca del centro de la habitación.</span><span class="sxs-lookup"><span data-stu-id="78411-221">The object placement query below is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>




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

<span data-ttu-id="78411-222">Si se realiza correctamente, se devuelve una estructura **ObjectPlacementResult** que contiene la posición de colocación, las dimensiones y la orientación.</span><span class="sxs-lookup"><span data-stu-id="78411-222">If successful, an **ObjectPlacementResult** structure containing the placement position, dimensions and orientation is returned.</span></span> <span data-ttu-id="78411-223">Además, la selección de ubicación se agrega a la lista interna de objetos colocados del archivo DLL.</span><span class="sxs-lookup"><span data-stu-id="78411-223">In addition, the placement is added to the DLL’s internal list of placed objects.</span></span> <span data-ttu-id="78411-224">Las consultas de selección de ubicación posteriores tendrán en cuenta este objeto.</span><span class="sxs-lookup"><span data-stu-id="78411-224">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="78411-225">El archivo **LevelSolver.CS** en el ejemplo de Unity contiene más consultas de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="78411-225">The **LevelSolver.cs** file in the Unity sample contains more example queries.</span></span>

![Los cuadros azules muestran el resultado de las consultas de tres lugares en el suelo con las reglas "fuera de la posición de la cámara".](images/away-from-camera-position-500px.png)

<span data-ttu-id="78411-227">Los cuadros azules muestran el resultado de las consultas de tres lugares en el suelo con las reglas "fuera de la posición de la cámara".</span><span class="sxs-lookup"><span data-stu-id="78411-227">The blue boxes show the result from three Place On Floor queries with "away from camera position" rules.</span></span>


<span data-ttu-id="78411-228">**Útiles**</span><span class="sxs-lookup"><span data-stu-id="78411-228">**Tips:**</span></span>
* <span data-ttu-id="78411-229">En la resolución de ubicación de varios objetos necesarios para un escenario de nivel o aplicación, primero se resuelven los objetos disposibles y grandes para maximizar la probabilidad de que se pueda encontrar un espacio.</span><span class="sxs-lookup"><span data-stu-id="78411-229">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects to maximize the probability that a space can be found.</span></span>
* <span data-ttu-id="78411-230">El orden de la ubicación es importante.</span><span class="sxs-lookup"><span data-stu-id="78411-230">Placement order is important.</span></span> <span data-ttu-id="78411-231">Si no se encuentran colocaciones de objeto, pruebe con menos configuraciones restringidas.</span><span class="sxs-lookup"><span data-stu-id="78411-231">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="78411-232">Tener un conjunto de configuraciones de reserva es fundamental para admitir la funcionalidad en muchas configuraciones de salón.</span><span class="sxs-lookup"><span data-stu-id="78411-232">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="78411-233">Conversión de rayos</span><span class="sxs-lookup"><span data-stu-id="78411-233">Ray casting</span></span>

<span data-ttu-id="78411-234">Además de las tres consultas principales, se puede usar una interfaz de conversión de rayos para recuperar tipos de superficie etiquetada y se puede copiar una malla de Playspace estanco personalizada después de que se haya analizado y finalizado el salón; las etiquetas se generan internamente para superficies como la piso, techo y paredes.</span><span class="sxs-lookup"><span data-stu-id="78411-234">In addition to the three primary queries, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out After the room has been scanned and finalized, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="78411-235">La función **PlayspaceRaycast** toma un rayo y devuelve si el rayo entra en conflicto con una superficie conocida y, en caso afirmativo, información sobre esa superficie en forma de **RaycastResult**.</span><span class="sxs-lookup"><span data-stu-id="78411-235">The **PlayspaceRaycast** function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a **RaycastResult**.</span></span> 


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

<span data-ttu-id="78411-236">Internamente, el Raycast se calcula con la representación calculada de 8cm con cubo voxel de Playspace.</span><span class="sxs-lookup"><span data-stu-id="78411-236">Internally, the raycast is computed against the computed 8cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="78411-237">Cada voxel contiene un conjunto de elementos Surface con datos de topología procesados (también conocidos como surfels).</span><span class="sxs-lookup"><span data-stu-id="78411-237">Each voxel contains a set of surface elements with processed topology data (also known as surfels).</span></span> <span data-ttu-id="78411-238">Se comparan los surfels contenidos en la celda voxel intersectada y la mejor coincidencia utilizada para buscar la información de la topología.</span><span class="sxs-lookup"><span data-stu-id="78411-238">The surfels contained within the intersected voxel cell are compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="78411-239">Estos datos de topología contienen la etiqueta devuelta en el formulario de la enumeración **SurfaceTypes** , así como el área expuesta de la superficie intersectada.</span><span class="sxs-lookup"><span data-stu-id="78411-239">This topology data contains the labeling returned in the form of the **SurfaceTypes** enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="78411-240">En el ejemplo de Unity, el cursor convierte un rayo en cada fotograma.</span><span class="sxs-lookup"><span data-stu-id="78411-240">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="78411-241">En primer lugar, con los colisionadores de Unity; en segundo lugar, en la representación mundial del módulo de comprensión; y, por último, con los elementos de la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="78411-241">First, against Unity’s colliders; second, against the understanding module’s world representation; and finally, against the UI elements.</span></span> <span data-ttu-id="78411-242">En esta aplicación, la interfaz de usuario obtiene prioridad, después el resultado de comprensión y, por último, los colisionadores de Unity.</span><span class="sxs-lookup"><span data-stu-id="78411-242">In this application, UI gets priority, then the understanding result, and finally, Unity’s colliders.</span></span> <span data-ttu-id="78411-243">El **SurfaceType** se muestra como texto junto al cursor.</span><span class="sxs-lookup"><span data-stu-id="78411-243">The **SurfaceType** is reported as text next to the cursor.</span></span>

![Raycast resultado de la intersección de informes con el piso.](images/raycast-result-500px.jpg)

<span data-ttu-id="78411-245">Raycast resultado de la intersección de informes con el piso.</span><span class="sxs-lookup"><span data-stu-id="78411-245">Raycast result reporting intersection with the floor.</span></span>


## <a name="get-the-code"></a><span data-ttu-id="78411-246">Obtener el código</span><span class="sxs-lookup"><span data-stu-id="78411-246">Get the code</span></span>

<span data-ttu-id="78411-247">El código de código abierto está disponible en [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span><span class="sxs-lookup"><span data-stu-id="78411-247">The open-source code is available in [MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity).</span></span> <span data-ttu-id="78411-248">Háganoslo saber en los [foros para desarrolladores de HoloLens](https://forums.hololens.com/) si usa el código en un proyecto.</span><span class="sxs-lookup"><span data-stu-id="78411-248">Let us know on the [HoloLens Developer Forums](https://forums.hololens.com/) if you use the code in a project.</span></span> <span data-ttu-id="78411-249">No podemos esperar para ver lo que hace con él.</span><span class="sxs-lookup"><span data-stu-id="78411-249">We can't wait to see what you do with it!</span></span>

## <a name="about-the-author"></a><span data-ttu-id="78411-250">Acerca del autor</span><span class="sxs-lookup"><span data-stu-id="78411-250">About the author</span></span>

<table style="border:0;width:800px">
<tr>
<td style="border:0"> <img alt="Jeff Evertt, Software Engineering Lead at Microsoft" width="200" height="205" src="images/jeff-evertt-200px.jpg" /></td><td style="border:0"> <span data-ttu-id="78411-251"><b>Jeff Evertt</b> es un responsable de ingeniería de software que ha trabajado en HoloLens desde los primeros días, desde la incubación hasta la experiencia de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="78411-251"><b>Jeff Evertt</b> is a software engineering lead who has worked on HoloLens since the early days, from incubation to experience development.</span></span> <span data-ttu-id="78411-252">Antes de HoloLens, trabajó en el Kinect de Xbox y en el sector de juegos en una amplia variedad de plataformas y juegos.</span><span class="sxs-lookup"><span data-stu-id="78411-252">Before HoloLens, he worked on the Xbox Kinect and in the games industry on a wide variety of platforms and games.</span></span> <span data-ttu-id="78411-253">Juan es apasionante de robóticas, gráficos y cosas con luces Flash que emiten sonido.</span><span class="sxs-lookup"><span data-stu-id="78411-253">Jeff is passionate about robotics, graphics, and things with flashy lights that go beep.</span></span> <span data-ttu-id="78411-254">Disfruta aprendiendo nuevas cosas y trabajando en software, hardware y, en especial, en el espacio en el que se intersecan dos.</span><span class="sxs-lookup"><span data-stu-id="78411-254">He enjoys learning new things and working on software, hardware, and particularly in the space where the two intersect.</span></span></td>
</tr>
</table>



## <a name="see-also"></a><span data-ttu-id="78411-255">Vea también</span><span class="sxs-lookup"><span data-stu-id="78411-255">See also</span></span>
* [<span data-ttu-id="78411-256">Asignación espacial</span><span class="sxs-lookup"><span data-stu-id="78411-256">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="78411-257">Diseño de asignaciones espaciales</span><span class="sxs-lookup"><span data-stu-id="78411-257">Spatial mapping design</span></span>](spatial-mapping-design.md)
* [<span data-ttu-id="78411-258">Visualización de la exploración de la sala</span><span class="sxs-lookup"><span data-stu-id="78411-258">Room scan visualization</span></span>](room-scan-visualization.md)
* [<span data-ttu-id="78411-259">MixedRealityToolkit: Unity</span><span class="sxs-lookup"><span data-stu-id="78411-259">MixedRealityToolkit-Unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [<span data-ttu-id="78411-260">Asobo Studio: Lecciones de la vanguardia del desarrollo de HoloLens</span><span class="sxs-lookup"><span data-stu-id="78411-260">Asobo Studio: Lessons from the frontline of HoloLens development</span></span>](http://www.gamesindustry.biz/articles/2016-05-12-asobo-lessons-from-the-frontline-of-ar-development)
