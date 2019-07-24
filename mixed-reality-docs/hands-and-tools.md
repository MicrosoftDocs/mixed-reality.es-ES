---
title: Controladores de manos y de movimiento
description: Información general sobre la interacción de las manos y los controladores de movimiento
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: Realidad mixta, manos, controles de movimiento, interacción, diseño
ms.openlocfilehash: d0e54c71ab42a09f2f9c6063a85441b98e729af1
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039166"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="97ab8-104">Controladores de manos y de movimiento</span><span class="sxs-lookup"><span data-stu-id="97ab8-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="97ab8-105">Escenarios</span><span class="sxs-lookup"><span data-stu-id="97ab8-105">Scenarios</span></span>
<span data-ttu-id="97ab8-106">Si decide adoptar este modelo de interacción después de leer las [directrices de diseño](interaction-fundamentals.md), significa que está desarrollando una aplicación que requiere que los usuarios usen dos manos para interactuar con el mundo holográfica.</span><span class="sxs-lookup"><span data-stu-id="97ab8-106">If you choose to adopt this interaction model after reading the [design guidelines](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="97ab8-107">La aplicación va a lograr el objetivo de quitar el límite entre virtual y física.</span><span class="sxs-lookup"><span data-stu-id="97ab8-107">Your application is going to achieve the goal of removing the boundry between virtual and physical.</span></span>

<span data-ttu-id="97ab8-108">Algunos escenarios específicos pueden ser:</span><span class="sxs-lookup"><span data-stu-id="97ab8-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="97ab8-109">Proporcionar a los trabajadores de la información pantallas y interfaces de virtuales de 2D para mostrar y controlar el contenido</span><span class="sxs-lookup"><span data-stu-id="97ab8-109">Providing information workers 2D vitual screens and UIs to display and control contents</span></span>
* <span data-ttu-id="97ab8-110">Proporcionar tutoriales y guías de primera línea en líneas de montaje de fábrica</span><span class="sxs-lookup"><span data-stu-id="97ab8-110">Providing first line workers tutorials and guides in factory assembly lines</span></span>
* <span data-ttu-id="97ab8-111">Desarrollo de herramientas profesionales para ayudar y educar a los profesionales médicos</span><span class="sxs-lookup"><span data-stu-id="97ab8-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="97ab8-112">Uso de objetos virtuales 3D para decorar el mundo real o crear un segundo mundo</span><span class="sxs-lookup"><span data-stu-id="97ab8-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="97ab8-113">Creación de servicios y juegos basados en ubicaciones con el mundo real como fondo</span><span class="sxs-lookup"><span data-stu-id="97ab8-113">Creating location based services and games using the real world as background</span></span>

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="97ab8-114">Modalidades de los controladores de manos y de movimiento</span><span class="sxs-lookup"><span data-stu-id="97ab8-114">Hands and motion controllers modalities</span></span>
### <a name="direct-manipulation-with-handsdirect-manipulationmd"></a>[<span data-ttu-id="97ab8-115">Manipulación directa con las manos</span><span class="sxs-lookup"><span data-stu-id="97ab8-115">Direct manipulation with hands</span></span>](direct-manipulation.md)
<span data-ttu-id="97ab8-116">Se trata de una moda que aprovecha la eficacia de las manos, con las que los usuarios pueden tocar y manipular directamente los hologramas.</span><span class="sxs-lookup"><span data-stu-id="97ab8-116">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="97ab8-117">Al leaveraging de la vida diaria de las experiencias y proporcionar prestaciones visuales adecuadas, los usuarios pueden usar la misma manera de manipular objetos del mundo real para interactuar con los virtuales.</span><span class="sxs-lookup"><span data-stu-id="97ab8-117">By leaveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>   

### <a name="point-and-commit-with-handspoint-and-commitmd"></a>[<span data-ttu-id="97ab8-118">Apuntar y confirmar con las manos</span><span class="sxs-lookup"><span data-stu-id="97ab8-118">Point and commit with hands</span></span>](point-and-commit.md)
<span data-ttu-id="97ab8-119">Esta modalidad permite a los usuarios interactuar con los hologramas en una distancia.</span><span class="sxs-lookup"><span data-stu-id="97ab8-119">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="97ab8-120">Permite a los usuarios hacer el mejor uso de los entornos.</span><span class="sxs-lookup"><span data-stu-id="97ab8-120">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="97ab8-121">Los usuarios pueden colocar hologramas en cualquier lugar y todavía pueden acceder a ellos desde cualquier distancia.</span><span class="sxs-lookup"><span data-stu-id="97ab8-121">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="97ab8-122">Los modelos y gestos mentales para controlar y manipular los hologramas 2D y 3D están muy sincronizados con los de manipulación directa.</span><span class="sxs-lookup"><span data-stu-id="97ab8-122">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>

### <a name="motion-controllersmotion-controllersmd"></a>[<span data-ttu-id="97ab8-123">Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="97ab8-123">Motion controllers</span></span>](motion-controllers.md)
<span data-ttu-id="97ab8-124">Los controladores de movimiento son herramientas que amplían las capacidades físicas de los usuarios proporcionando interacciones precisas en una gran variedad de distancias al usar una o ambas manos.</span><span class="sxs-lookup"><span data-stu-id="97ab8-124">Motion controllers are tools that extend the users' physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="97ab8-125">Estos accesorios de hardware proporcionan accesos directos a muchas interacciones usadas con frecuencia y ofrecen comentarios Surefooted y táctiles para una variedad de acciones.</span><span class="sxs-lookup"><span data-stu-id="97ab8-125">These hardware accessories provide shortcuts to many commonly-used interactions and gives surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="97ab8-126">Actualmente, los controladores de movimiento solo están disponibles para los escenarios de WMR.</span><span class="sxs-lookup"><span data-stu-id="97ab8-126">Currently, motion controllers are only available for WMR scenarios.</span></span> 

![](images/Hands-and-controllers-720px.jpg)<br>

## <a name="see-also"></a><span data-ttu-id="97ab8-127">Vea también</span><span class="sxs-lookup"><span data-stu-id="97ab8-127">See also</span></span>
* [<span data-ttu-id="97ab8-128">Mirada-cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="97ab8-128">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="97ab8-129">Control con la cabeza y permanencia</span><span class="sxs-lookup"><span data-stu-id="97ab8-129">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="97ab8-130">Manipulación directa con las manos</span><span class="sxs-lookup"><span data-stu-id="97ab8-130">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="97ab8-131">Apuntar y confirmar con las manos</span><span class="sxs-lookup"><span data-stu-id="97ab8-131">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="97ab8-132">Manos libres</span><span class="sxs-lookup"><span data-stu-id="97ab8-132">Hands-free</span></span>](hands-free.md)
