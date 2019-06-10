---
title: Barra de la aplicación y el rectángulo de selección
description: La barra de la aplicación es un menú de nivel de objeto que contiene una serie de botones que se muestra en la parte inferior de los límites de un holograma.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, barra, cuadro de límite de aplicaciones
ms.openlocfilehash: ab472e1c988e6bdfb0a69d90e90280082b3db759
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813861"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="4f990-104">Barra de la aplicación y de cuadro de límite</span><span class="sxs-lookup"><span data-stu-id="4f990-104">Bounding box and App bar</span></span>
![Rectángulo de selección es la interfaz estándar para la manipulación del objeto en la realidad mixta.](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="4f990-106">¿Qué es el cuadro de límite?</span><span class="sxs-lookup"><span data-stu-id="4f990-106">What is the Bounding box?</span></span>

<span data-ttu-id="4f990-107">Rectángulo de selección es la interfaz estándar para la manipulación del objeto en la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="4f990-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="4f990-108">Proporciona al usuario una prestación que el objeto está actualmente ajustable.</span><span class="sxs-lookup"><span data-stu-id="4f990-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="4f990-109">Las esquinas indican al usuario que también puede escalar el objeto.</span><span class="sxs-lookup"><span data-stu-id="4f990-109">The corners tell the user that the object can also scale.</span></span> <span data-ttu-id="4f990-110">Esta prestación visual muestra a los usuarios la superficie total del objeto, incluso si no está visible fuera de un modo de ajuste.</span><span class="sxs-lookup"><span data-stu-id="4f990-110">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="4f990-111">Esto es especialmente importante porque si no fuese allí, puede aparecer un objeto que se ajustan a otro objeto o la superficie se comporte como si no hay espacio alrededor de ella que no debería estar allí.</span><span class="sxs-lookup"><span data-stu-id="4f990-111">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span> <span data-ttu-id="4f990-112">En HoloLens 2, el rectángulo de selección funciona con la manipulación directa de mano y responde a la proximidad del dedo del usuario.</span><span class="sxs-lookup"><span data-stu-id="4f990-112">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="4f990-113">Muestra los comentarios visuales para ayudar al usuario percibir la distancia desde el objeto.</span><span class="sxs-lookup"><span data-stu-id="4f990-113">It shows visual feedback to help the user perceive the distance from the object.</span></span> 

<span data-ttu-id="4f990-114">![HoloLens punto de vista de un objeto mediante el cuadro de límite de escalado](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="4f990-114">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
<span data-ttu-id="4f990-115">*Escalar un objeto mediante el cuadro de límite*</span><span class="sxs-lookup"><span data-stu-id="4f990-115">*Scaling an object via bounding box*</span></span>

<span data-ttu-id="4f990-116">Los identificadores en las esquinas del cuadro de límite siguen un patrón ampliamente conocido por el ajuste de escala.</span><span class="sxs-lookup"><span data-stu-id="4f990-116">The handles in the corners of the bounding box follow a widely understood pattern for adjusting scale.</span></span> 

<span data-ttu-id="4f990-117">![HoloLens punto de vista de girar un objeto mediante el cuadro de límite](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="4f990-117">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
<span data-ttu-id="4f990-118">*Girar un objeto mediante el cuadro de límite*</span><span class="sxs-lookup"><span data-stu-id="4f990-118">*Rotating an object via bounding box*</span></span>


<span data-ttu-id="4f990-119">![Comentarios visuales en la proximidad de mano](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="4f990-119">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
<span data-ttu-id="4f990-120">*Comentarios visuales basados en la proximidad*</span><span class="sxs-lookup"><span data-stu-id="4f990-120">*Visual feedback based on the proximity*</span></span>

<span data-ttu-id="4f990-121">La factibilidad rectangular vertical de los bordes del cuadro de límite es indicadores de rotación.</span><span class="sxs-lookup"><span data-stu-id="4f990-121">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="4f990-122">Esto proporciona al usuario más ajuste fino sobre sus hologramas colocados.</span><span class="sxs-lookup"><span data-stu-id="4f990-122">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="4f990-123">No sólo pueden ajustar y escalar, pero ahora también girar.</span><span class="sxs-lookup"><span data-stu-id="4f990-123">Not only can they adjust and scale, but now rotate as well.</span></span>

* <span data-ttu-id="4f990-124">Para el desarrollo de aplicaciones de Unity, vea [caja en Kit de herramientas de Unity de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span><span class="sxs-lookup"><span data-stu-id="4f990-124">For Unity app development, see [Bounding box on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span></span>



## <a name="what-is-the-app-bar"></a><span data-ttu-id="4f990-125">¿Qué es la barra de aplicaciones?</span><span class="sxs-lookup"><span data-stu-id="4f990-125">What is the App bar?</span></span>

<span data-ttu-id="4f990-126">La barra de la aplicación es un menú de nivel de objeto que contiene una serie de botones que se muestra en la parte inferior de los límites de un holograma.</span><span class="sxs-lookup"><span data-stu-id="4f990-126">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="4f990-127">Este patrón normalmente se usa para proporcionar a los usuarios la capacidad de quitar y ajustar hologramas.</span><span class="sxs-lookup"><span data-stu-id="4f990-127">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span>

<span data-ttu-id="4f990-128">Puesto que este patrón se usa con objetos que son world bloqueado, como un usuario se mueve alrededor del objeto en que la barra de la aplicación siempre se mostrará en el lado de los objetos más cercano al usuario.</span><span class="sxs-lookup"><span data-stu-id="4f990-128">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="4f990-129">Aunque esto no es vallas publicitarias, consigue eficazmente el mismo resultado; impide la posición a occlude de un usuario o la funcionalidad de bloqueo que podría estar disponible desde una ubicación diferente en su entorno.</span><span class="sxs-lookup"><span data-stu-id="4f990-129">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span>

<span data-ttu-id="4f990-130">![Desplazarse un holograma.</span><span class="sxs-lookup"><span data-stu-id="4f990-130">![Walking around a hologram.</span></span> <span data-ttu-id="4f990-131">Sigue la barra de la aplicación.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="4f990-131">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
<span data-ttu-id="4f990-132">*Desplazarse un holograma, sigue la barra de aplicaciones*</span><span class="sxs-lookup"><span data-stu-id="4f990-132">*Walking around a hologram, the App bar follows*</span></span>

<span data-ttu-id="4f990-133">La barra de la aplicación se diseñó principalmente como una manera de administrar los objetos colocados en el entorno de un usuario.</span><span class="sxs-lookup"><span data-stu-id="4f990-133">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="4f990-134">Junto con el cuadro de límite, un usuario tiene control total sobre dónde y cómo están orientadas a objetos en la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="4f990-134">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

* <span data-ttu-id="4f990-135">Para el desarrollo de aplicaciones de Unity, vea [barra de la aplicación en Kit de herramientas de Unity de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span><span class="sxs-lookup"><span data-stu-id="4f990-135">For Unity app development, see [App bar on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span></span>

## <a name="see-also"></a><span data-ttu-id="4f990-136">Vea también</span><span class="sxs-lookup"><span data-stu-id="4f990-136">See also</span></span>
* [<span data-ttu-id="4f990-137">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="4f990-137">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="4f990-138">Texto en Unity</span><span class="sxs-lookup"><span data-stu-id="4f990-138">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="4f990-139">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="4f990-139">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="4f990-140">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="4f990-140">Displaying progress</span></span>](progress.md)
