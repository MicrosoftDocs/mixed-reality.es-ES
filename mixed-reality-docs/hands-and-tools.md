---
title: Las manos y los controladores de movimiento
description: Información general de las manos y la interacción de los controladores de movimiento
author: shengkait
ms.author: shengkait
ms.date: 04/26/2019
ms.topic: article
keywords: Diseñar la realidad, manos, los controladores de movimiento, interacción, mixta
ms.openlocfilehash: d0e54c71ab42a09f2f9c6063a85441b98e729af1
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039166"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="1ad5c-104">Las manos y los controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="1ad5c-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="1ad5c-105">Escenarios</span><span class="sxs-lookup"><span data-stu-id="1ad5c-105">Scenarios</span></span>
<span data-ttu-id="1ad5c-106">Si decide adoptar este modelo de interacción después de leer el [directrices de diseño](interaction-fundamentals.md), significa que está desarrollando una aplicación que requieren los usuarios para usar dos manos para interactuar con el mundo holográfico.</span><span class="sxs-lookup"><span data-stu-id="1ad5c-106">If you choose to adopt this interaction model after reading the [design guidelines](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="1ad5c-107">La aplicación se va a lograr el objetivo de eliminar el límite entre físicas y virtuales.</span><span class="sxs-lookup"><span data-stu-id="1ad5c-107">Your application is going to achieve the goal of removing the boundry between virtual and physical.</span></span>

<span data-ttu-id="1ad5c-108">Podrían ser algunos escenarios concretos:</span><span class="sxs-lookup"><span data-stu-id="1ad5c-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="1ad5c-109">Proporcionar las pantallas de virtual 2D de los trabajadores de información y las interfaces de usuario para mostrar y controlar el contenido</span><span class="sxs-lookup"><span data-stu-id="1ad5c-109">Providing information workers 2D vitual screens and UIs to display and control contents</span></span>
* <span data-ttu-id="1ad5c-110">Proporciona tutoriales de los trabajadores de primera línea y las guías de montaje de fábrica</span><span class="sxs-lookup"><span data-stu-id="1ad5c-110">Providing first line workers tutorials and guides in factory assembly lines</span></span>
* <span data-ttu-id="1ad5c-111">Desarrollar herramientas profesionales para ayudar a y educar a los profesionales médicos</span><span class="sxs-lookup"><span data-stu-id="1ad5c-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="1ad5c-112">Uso de objetos virtuales 3D para decorar el mundo real o para crear un mundo de segundo</span><span class="sxs-lookup"><span data-stu-id="1ad5c-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="1ad5c-113">Creación de ubicación y servicios basado en juegos con el mundo real como fondo</span><span class="sxs-lookup"><span data-stu-id="1ad5c-113">Creating location based services and games using the real world as background</span></span>

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="1ad5c-114">Las manos y las modalidades de controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="1ad5c-114">Hands and motion controllers modalities</span></span>
### <a name="direct-manipulation-with-handsdirect-manipulationmd"></a>[<span data-ttu-id="1ad5c-115">Manipulación directa con las manos</span><span class="sxs-lookup"><span data-stu-id="1ad5c-115">Direct manipulation with hands</span></span>](direct-manipulation.md)
<span data-ttu-id="1ad5c-116">Se trata de una modalidad aprovechando la eficacia de las manos, con el que los usuarios son capaces de tocar y manipular el hologramas directamente.</span><span class="sxs-lookup"><span data-stu-id="1ad5c-116">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="1ad5c-117">De forma leaveraging experiencias de la vida diaria y proporcionar factibilidad visual adecuado, los usuarios pueden usar la misma manera de manipular objetos del mundo real para interactuar con las virtuales.</span><span class="sxs-lookup"><span data-stu-id="1ad5c-117">By leaveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>   

### <a name="point-and-commit-with-handspoint-and-commitmd"></a>[<span data-ttu-id="1ad5c-118">Apuntar y confirmar con las manos</span><span class="sxs-lookup"><span data-stu-id="1ad5c-118">Point and commit with hands</span></span>](point-and-commit.md)
<span data-ttu-id="1ad5c-119">Esta modalidad permite a los usuarios interactuar con hologramas en una distancia.</span><span class="sxs-lookup"><span data-stu-id="1ad5c-119">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="1ad5c-120">Permite a los usuarios hacer el mejor uso de su entorno.</span><span class="sxs-lookup"><span data-stu-id="1ad5c-120">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="1ad5c-121">Los usuarios pueden colocar en cualquier parte hologramas y pueden aún tener acceso a ellos desde cualquier distancias.</span><span class="sxs-lookup"><span data-stu-id="1ad5c-121">Users can place holograms anywhere and can still access them from any distances.</span></span> <span data-ttu-id="1ad5c-122">Los modelos mentales y gestos para controlar y manipular hologramas 2D y 3D son altamente sincronizados con los de la manipulación directa.</span><span class="sxs-lookup"><span data-stu-id="1ad5c-122">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>

### <a name="motion-controllersmotion-controllersmd"></a>[<span data-ttu-id="1ad5c-123">Controladores de movimiento</span><span class="sxs-lookup"><span data-stu-id="1ad5c-123">Motion controllers</span></span>](motion-controllers.md)
<span data-ttu-id="1ad5c-124">Los controladores de movimiento son herramientas que amplían las capacidades físicas de los usuarios proporcionando interacciones precisas en una gran variedad de distancias al usar las manos de uno o ambos.</span><span class="sxs-lookup"><span data-stu-id="1ad5c-124">Motion controllers are tools that extend the users' physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="1ad5c-125">Estos accesorios de hardware proporcionan accesos directos a muchos usadas con frecuencia las interacciones y proporciona al tacto, surefooted los comentarios para una variedad de acciones.</span><span class="sxs-lookup"><span data-stu-id="1ad5c-125">These hardware accessories provide shortcuts to many commonly-used interactions and gives surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="1ad5c-126">Actualmente, solo están disponibles para escenarios WMR los controladores de movimiento.</span><span class="sxs-lookup"><span data-stu-id="1ad5c-126">Currently, motion controllers are only available for WMR scenarios.</span></span> 

![](images/Hands-and-controllers-720px.jpg)<br>

## <a name="see-also"></a><span data-ttu-id="1ad5c-127">Vea también</span><span class="sxs-lookup"><span data-stu-id="1ad5c-127">See also</span></span>
* [<span data-ttu-id="1ad5c-128">Mirada-cabeza y confirmación</span><span class="sxs-lookup"><span data-stu-id="1ad5c-128">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="1ad5c-129">Control con la cabeza y permanencia</span><span class="sxs-lookup"><span data-stu-id="1ad5c-129">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="1ad5c-130">Manipulación directa con las manos</span><span class="sxs-lookup"><span data-stu-id="1ad5c-130">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="1ad5c-131">Apuntar y confirmar con las manos</span><span class="sxs-lookup"><span data-stu-id="1ad5c-131">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="1ad5c-132">Manos libres</span><span class="sxs-lookup"><span data-stu-id="1ad5c-132">Hands-free</span></span>](hands-free.md)
