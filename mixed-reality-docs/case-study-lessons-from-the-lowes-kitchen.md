---
title: 'Caso práctico: lecciones de cocina del Lowe'
description: El equipo de HoloLens desea compartir algunos de los procedimientos recomendados que se derivan de proyecto de HoloLens del Lowe.
author: BrandonBray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, del Lowe, HoloLens, cocina, caso práctico
ms.openlocfilehash: 24759f90b8b84ec19e644fb8dff44f64c3ab81d2
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599847"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a><span data-ttu-id="40e96-104">Caso práctico: lecciones de cocina del Lowe</span><span class="sxs-lookup"><span data-stu-id="40e96-104">Case study - Lessons from the Lowe's kitchen</span></span>

<span data-ttu-id="40e96-105">El equipo de HoloLens desea compartir algunos de los procedimientos recomendados que se derivan de proyecto de HoloLens del Lowe.</span><span class="sxs-lookup"><span data-stu-id="40e96-105">The HoloLens team wants to share some of the best practices that were derived from the Lowe's HoloLens project.</span></span> <span data-ttu-id="40e96-106">A continuación se muestra un vídeo de HoloLens del Lowe proyectadas en la conferencia de Ignite 2016 de Satya.</span><span class="sxs-lookup"><span data-stu-id="40e96-106">Below is a video of the Lowe's HoloLens projected demonstrated at Satya's 2016 Ignite keynote.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a><span data-ttu-id="40e96-107">Prácticas recomendadas de HoloLens del Lowe</span><span class="sxs-lookup"><span data-stu-id="40e96-107">Lowe's HoloLens Best Practices</span></span>

<span data-ttu-id="40e96-108">Los dos vídeos abarcan las prácticas recomendadas que se derivan HoloLens piloto del Lowe que ha estado en almacenes de dos Lowe desde abril de 2016.</span><span class="sxs-lookup"><span data-stu-id="40e96-108">The two videos cover best practices that were derived from the Lowe's HoloLens Pilot that has been in two Lowe's stores since April 2016.</span></span> <span data-ttu-id="40e96-109">Los temas claves son:</span><span class="sxs-lookup"><span data-stu-id="40e96-109">The key topics are:</span></span>
* <span data-ttu-id="40e96-110">Maximizar el rendimiento de un dispositivo móvil</span><span class="sxs-lookup"><span data-stu-id="40e96-110">Maximize performance for a mobile device</span></span>
* <span data-ttu-id="40e96-111">Crear métodos de la experiencia del usuario con un marco completo holográfico (2nd talk)</span><span class="sxs-lookup"><span data-stu-id="40e96-111">Create UX methods with a full holographic frame (2nd talk)</span></span>
* <span data-ttu-id="40e96-112">Alineación de precisión (2nd talk)</span><span class="sxs-lookup"><span data-stu-id="40e96-112">Precision alignment (2nd talk)</span></span>
* <span data-ttu-id="40e96-113">Compartir experiencias holográficas (2nd talk)</span><span class="sxs-lookup"><span data-stu-id="40e96-113">Shared holographic experiences (2nd talk)</span></span>
* <span data-ttu-id="40e96-114">Interactuar con los clientes (2nd talk)</span><span class="sxs-lookup"><span data-stu-id="40e96-114">Interacting with customers (2nd talk)</span></span>

## <a name="video-1"></a><span data-ttu-id="40e96-115">Vídeo 1</span><span class="sxs-lookup"><span data-stu-id="40e96-115">Video 1</span></span>

<span data-ttu-id="40e96-116">**Maximizar el rendimiento de un dispositivo móvil** HoloLens es un dispositivo sin restricción con todo el procesamiento que lleva a cabo en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="40e96-116">**Maximize performance for a mobile device** HoloLens is an untethered device with all the processing taking place in the device.</span></span> <span data-ttu-id="40e96-117">Esto requiere una plataforma móvil y requiere una mentalidad similar a la creación de aplicaciones móviles.</span><span class="sxs-lookup"><span data-stu-id="40e96-117">This requires a mobile platform and requires a mindset similar to creating mobile applications.</span></span> <span data-ttu-id="40e96-118">Microsoft recomienda que la aplicación de HoloLens mantienen 60FPS para proporcionar una experiencia deliciosa para los usuarios.</span><span class="sxs-lookup"><span data-stu-id="40e96-118">Microsoft recommends that your HoloLens application maintain 60FPS to provide a delicious experience for your users.</span></span> <span data-ttu-id="40e96-119">Tener FPS bajo puede dar lugar a hologramas inestables.</span><span class="sxs-lookup"><span data-stu-id="40e96-119">Having low FPS can result in unstable holograms.</span></span>

<span data-ttu-id="40e96-120">Algunas de las cosas más importantes que se consulten al desarrollo de HoloLens está activo optimización/diezmado con sombreadores personalizados (disponible gratuitamente en el [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)).</span><span class="sxs-lookup"><span data-stu-id="40e96-120">Some of the most important things to look at when developing on HoloLens is asset optimization/decimation, using custom shaders (available for free in the [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)).</span></span> <span data-ttu-id="40e96-121">Otra consideración importante es medir la velocidad de fotogramas desde el principio del proyecto.</span><span class="sxs-lookup"><span data-stu-id="40e96-121">Another important consideration is to measure the frame rate from the very beginning of your project.</span></span> <span data-ttu-id="40e96-122">Según el proyecto, el orden de presentación de los recursos también puede ser un gran colaborador</span><span class="sxs-lookup"><span data-stu-id="40e96-122">Depending on the project, the order of displaying your assets can also be a big contributor</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a><span data-ttu-id="40e96-123">Vídeo 2</span><span class="sxs-lookup"><span data-stu-id="40e96-123">Video 2</span></span>

<span data-ttu-id="40e96-124">**Crear métodos de la experiencia del usuario con un marco completo holográfico** es importante comprender la colocación de hologramas en un mundo físico.</span><span class="sxs-lookup"><span data-stu-id="40e96-124">**Create UX methods with a full holographic frame** It's important to understand the placement of holograms in a physical world.</span></span> <span data-ttu-id="40e96-125">Con la del Lowe hablamos distintos métodos de experiencia de usuario que ayudan a los usuarios hologramas experiencia de cierre mientras sigue apareciendo en el entorno de hologramas mayor.</span><span class="sxs-lookup"><span data-stu-id="40e96-125">With Lowe's we talk about different UX methods that help users experience holograms up close while still seeing the larger environment of holograms.</span></span>

<span data-ttu-id="40e96-126">**Alineación de precisión** escenario para el Lowe, era primordial para la experiencia de tener alineación de precisión de la hologramas a la cocina física.</span><span class="sxs-lookup"><span data-stu-id="40e96-126">**Precision alignment** For the Lowe's scenario, it was paramount to the experience to have precision alignment of the holograms to the physical kitchen.</span></span> <span data-ttu-id="40e96-127">Se describen técnicas que ayuda a garantiza una experiencia que convence a los usuarios que ha cambiado su entorno físico.</span><span class="sxs-lookup"><span data-stu-id="40e96-127">We discuss techniques helps ensure an experience that convinces users that their physical environment has changed.</span></span>

<span data-ttu-id="40e96-128">**Compartir experiencias holográficas** asocia es la forma principal que se consume la experiencia del Lowe.</span><span class="sxs-lookup"><span data-stu-id="40e96-128">**Shared holographic experiences** Couples are the primary way that the Lowe's experience is consumed.</span></span> <span data-ttu-id="40e96-129">Una persona puede cambiar la encimera y la otra persona pueda ver los cambios.</span><span class="sxs-lookup"><span data-stu-id="40e96-129">One person can change the countertop and the other person will see the changes.</span></span> <span data-ttu-id="40e96-130">Se llama a este "experiencias compartidas".</span><span class="sxs-lookup"><span data-stu-id="40e96-130">We called this "shared experiences".</span></span>

<span data-ttu-id="40e96-131">**Interactuar con los clientes** diseñadores de Lowe no utilizan un HoloLens, pero que tienen que ver lo que están viendo los clientes.</span><span class="sxs-lookup"><span data-stu-id="40e96-131">**Interacting with customers** Lowe's designers are not using a HoloLens, but they need to see what the customers are seeing.</span></span> <span data-ttu-id="40e96-132">Se muestra cómo capturar lo que está experimentando el cliente en una aplicación de UWP.</span><span class="sxs-lookup"><span data-stu-id="40e96-132">We show how to capture what the customer is seeing on a UWP application.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
