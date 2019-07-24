---
title: Cuadro de límite y barra de la aplicación
description: La barra de la aplicación es un menú de nivel de objeto que contiene una serie de botones que se muestran en el borde inferior de los límites de un holograma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, barra de aplicaciones, cuadro de límite
ms.openlocfilehash: d289be31129324c6ff419b69dbce52bd8f62eb64
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829682"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="15f56-104">Cuadro de límite y barra de la aplicación</span><span class="sxs-lookup"><span data-stu-id="15f56-104">Bounding box and App bar</span></span>
![El límite es la interfaz estándar para la manipulación de objetos en la realidad mixta.](images/640px-boundingbox-hero.jpg)<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="15f56-106">¿Cuál es el cuadro de límite?</span><span class="sxs-lookup"><span data-stu-id="15f56-106">What is the Bounding box?</span></span>

<span data-ttu-id="15f56-107">El límite es la interfaz estándar para la manipulación de objetos en la realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="15f56-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="15f56-108">Proporciona al usuario una asequibilidad de que el objeto es ajustable actualmente.</span><span class="sxs-lookup"><span data-stu-id="15f56-108">It provides the user an affordance that the object is currently adjustable.</span></span> <span data-ttu-id="15f56-109">Las esquinas indican al usuario que el objeto también se puede escalar.</span><span class="sxs-lookup"><span data-stu-id="15f56-109">The corners tell the user that the object can also scale.</span></span> <span data-ttu-id="15f56-110">Esta prestación visual muestra a los usuarios el área total del objeto, aunque no sea visible fuera de un modo de ajuste.</span><span class="sxs-lookup"><span data-stu-id="15f56-110">This visual affordance shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="15f56-111">Esto es especialmente importante porque, si no estuviera allí, es posible que un objeto ajustado a otro objeto o superficie parezca que se comporte como si hubiera espacio alrededor que no debiera estar ahí.</span><span class="sxs-lookup"><span data-stu-id="15f56-111">This is especially important because if it weren’t there, an object snapped to another object or surface may appear to behave as if there was space around it that shouldn’t be there.</span></span> <span data-ttu-id="15f56-112">En HoloLens 2, el cuadro de límite funciona con la manipulación directa y responde a la proximidad del finger's del usuario.</span><span class="sxs-lookup"><span data-stu-id="15f56-112">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="15f56-113">Muestra comentarios visuales para ayudar al usuario a percibir la distancia desde el objeto.</span><span class="sxs-lookup"><span data-stu-id="15f56-113">It shows visual feedback to help the user perceive the distance from the object.</span></span> 

<span data-ttu-id="15f56-114">![Punto de vista de HoloLens de escalado de un objeto a través del cuadro de límite](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="15f56-114">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
<span data-ttu-id="15f56-115">*Escalado de un objeto a través del cuadro de límite*</span><span class="sxs-lookup"><span data-stu-id="15f56-115">*Scaling an object via bounding box*</span></span>

<span data-ttu-id="15f56-116">Los manipuladores de las esquinas del cuadro de límite siguen un patrón muy entendido para ajustar la escala.</span><span class="sxs-lookup"><span data-stu-id="15f56-116">The handles in the corners of the bounding box follow a widely understood pattern for adjusting scale.</span></span> 

<span data-ttu-id="15f56-117">![Punto de vista de HoloLens de girar un objeto a través del cuadro de límite](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="15f56-117">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
<span data-ttu-id="15f56-118">*Girar un objeto a través del cuadro de límite*</span><span class="sxs-lookup"><span data-stu-id="15f56-118">*Rotating an object via bounding box*</span></span>


<span data-ttu-id="15f56-119">![Comentarios visuales en proximidad](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="15f56-119">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
<span data-ttu-id="15f56-120">*Comentarios visuales basados en la proximidad*</span><span class="sxs-lookup"><span data-stu-id="15f56-120">*Visual feedback based on the proximity*</span></span>

<span data-ttu-id="15f56-121">Las prestaciones rectangulares verticales en los bordes del cuadro de límite son indicadores de rotación.</span><span class="sxs-lookup"><span data-stu-id="15f56-121">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="15f56-122">Esto proporciona al usuario un ajuste más preciso sobre sus hologramas colocados.</span><span class="sxs-lookup"><span data-stu-id="15f56-122">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="15f56-123">No solo se pueden ajustar y escalar, sino que ahora giran.</span><span class="sxs-lookup"><span data-stu-id="15f56-123">Not only can they adjust and scale, but now rotate as well.</span></span>

* <span data-ttu-id="15f56-124">Para el desarrollo de aplicaciones de Unity, consulte [cuadro de límite en el kit de herramientas de realidad mixta (Unity)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) .</span><span class="sxs-lookup"><span data-stu-id="15f56-124">For Unity app development, see [Bounding box on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)</span></span>



## <a name="what-is-the-app-bar"></a><span data-ttu-id="15f56-125">¿Qué es la barra de la aplicación?</span><span class="sxs-lookup"><span data-stu-id="15f56-125">What is the App bar?</span></span>

<span data-ttu-id="15f56-126">La barra de la aplicación es un menú de nivel de objeto que contiene una serie de botones que se muestran en el borde inferior de los límites de un holograma.</span><span class="sxs-lookup"><span data-stu-id="15f56-126">The App bar is a object-level menu containing a series of buttons that displays on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="15f56-127">Este patrón se usa normalmente para proporcionar a los usuarios la capacidad de quitar y ajustar los hologramas.</span><span class="sxs-lookup"><span data-stu-id="15f56-127">This pattern is commonly used to give users the ability to remove and adjust holograms.</span></span>

<span data-ttu-id="15f56-128">Puesto que este patrón se usa con objetos que están bloqueados por todo el mundo, a medida que un usuario se desplaza por el objeto, la barra de la aplicación siempre se mostrará en el lado de los objetos más cercano al usuario.</span><span class="sxs-lookup"><span data-stu-id="15f56-128">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="15f56-129">Aunque esto no se está desformando, se consigue el mismo resultado; impedir que la posición de un usuario tapaba o bloquee la funcionalidad que, de otro modo, estará disponible desde una ubicación diferente en su entorno.</span><span class="sxs-lookup"><span data-stu-id="15f56-129">While this isn't billboarding, it effectively achieves the same result; preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span>

<span data-ttu-id="15f56-130">![Recorrer un holograma.</span><span class="sxs-lookup"><span data-stu-id="15f56-130">![Walking around a hologram.</span></span> <span data-ttu-id="15f56-131">A continuación se muestra la barra de la aplicación.](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="15f56-131">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
<span data-ttu-id="15f56-132">*Desplazarse por un holograma, la barra de la aplicación sigue*</span><span class="sxs-lookup"><span data-stu-id="15f56-132">*Walking around a hologram, the App bar follows*</span></span>

<span data-ttu-id="15f56-133">La barra de la aplicación se diseñó principalmente como una manera de administrar objetos colocados en el entorno de un usuario.</span><span class="sxs-lookup"><span data-stu-id="15f56-133">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="15f56-134">Junto con el cuadro de límite, un usuario tiene control total sobre dónde y cómo se orientan los objetos en realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="15f56-134">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

* <span data-ttu-id="15f56-135">Para el desarrollo de aplicaciones de Unity, consulte [App bar en el kit de herramientas de realidad mixta (Unity)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html) .</span><span class="sxs-lookup"><span data-stu-id="15f56-135">For Unity app development, see [App bar on Mixed Reality Toolkit-Unity](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_AppBar.html)</span></span>

## <a name="see-also"></a><span data-ttu-id="15f56-136">Vea también</span><span class="sxs-lookup"><span data-stu-id="15f56-136">See also</span></span>
* [<span data-ttu-id="15f56-137">Objeto con el que se puede interactuar</span><span class="sxs-lookup"><span data-stu-id="15f56-137">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="15f56-138">Texto en Unity</span><span class="sxs-lookup"><span data-stu-id="15f56-138">Text in Unity</span></span>](text-in-unity.md)
* [<span data-ttu-id="15f56-139">Colección de objetos</span><span class="sxs-lookup"><span data-stu-id="15f56-139">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="15f56-140">Indicación del progreso</span><span class="sxs-lookup"><span data-stu-id="15f56-140">Displaying progress</span></span>](progress.md)
