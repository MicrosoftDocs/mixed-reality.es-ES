---
title: 'Caso práctico: lecciones de la cocina de Lowe'
description: El equipo de HoloLens quiere compartir algunas de las prácticas recomendadas que se derivaron del proyecto HoloLens de Lowe.
author: BrandonBray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, Lowe, HoloLens, cocina, caso práctico
ms.openlocfilehash: 24759f90b8b84ec19e644fb8dff44f64c3ab81d2
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522344"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a><span data-ttu-id="b5c3c-104">Caso práctico: lecciones de la cocina de Lowe</span><span class="sxs-lookup"><span data-stu-id="b5c3c-104">Case study - Lessons from the Lowe's kitchen</span></span>

<span data-ttu-id="b5c3c-105">El equipo de HoloLens quiere compartir algunas de las prácticas recomendadas que se derivaron del proyecto HoloLens de Lowe.</span><span class="sxs-lookup"><span data-stu-id="b5c3c-105">The HoloLens team wants to share some of the best practices that were derived from the Lowe's HoloLens project.</span></span> <span data-ttu-id="b5c3c-106">A continuación se muestra un vídeo de HoloLens previsto de Lowe en el discurso de encendido 2016 de Satya.</span><span class="sxs-lookup"><span data-stu-id="b5c3c-106">Below is a video of the Lowe's HoloLens projected demonstrated at Satya's 2016 Ignite keynote.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a><span data-ttu-id="b5c3c-107">Procedimientos recomendados de HoloLens de Lowe</span><span class="sxs-lookup"><span data-stu-id="b5c3c-107">Lowe's HoloLens Best Practices</span></span>

<span data-ttu-id="b5c3c-108">Los dos vídeos cubren los procedimientos recomendados que se derivaron del piloto de HoloLens de Lowe, que se ha realizado en dos almacenes de Lowe desde abril de 2016.</span><span class="sxs-lookup"><span data-stu-id="b5c3c-108">The two videos cover best practices that were derived from the Lowe's HoloLens Pilot that has been in two Lowe's stores since April 2016.</span></span> <span data-ttu-id="b5c3c-109">Los temas clave son:</span><span class="sxs-lookup"><span data-stu-id="b5c3c-109">The key topics are:</span></span>
* <span data-ttu-id="b5c3c-110">Maximizar el rendimiento de un dispositivo móvil</span><span class="sxs-lookup"><span data-stu-id="b5c3c-110">Maximize performance for a mobile device</span></span>
* <span data-ttu-id="b5c3c-111">Crear métodos de experiencia del usuario con un marco holográfica completo (segunda charla)</span><span class="sxs-lookup"><span data-stu-id="b5c3c-111">Create UX methods with a full holographic frame (2nd talk)</span></span>
* <span data-ttu-id="b5c3c-112">Alineación de precisión (segunda conversación)</span><span class="sxs-lookup"><span data-stu-id="b5c3c-112">Precision alignment (2nd talk)</span></span>
* <span data-ttu-id="b5c3c-113">Experiencias de Holographic compartidas (segunda charla)</span><span class="sxs-lookup"><span data-stu-id="b5c3c-113">Shared holographic experiences (2nd talk)</span></span>
* <span data-ttu-id="b5c3c-114">Interacción con los clientes (segunda charla)</span><span class="sxs-lookup"><span data-stu-id="b5c3c-114">Interacting with customers (2nd talk)</span></span>

## <a name="video-1"></a><span data-ttu-id="b5c3c-115">Vídeo 1</span><span class="sxs-lookup"><span data-stu-id="b5c3c-115">Video 1</span></span>

<span data-ttu-id="b5c3c-116">**Maximizar el rendimiento de un dispositivo móvil** HoloLens es un dispositivo untethered con todo el procesamiento que se lleva a cabo en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b5c3c-116">**Maximize performance for a mobile device** HoloLens is an untethered device with all the processing taking place in the device.</span></span> <span data-ttu-id="b5c3c-117">Esto requiere una plataforma móvil y requiere una mentalidad similar a la creación de aplicaciones móviles.</span><span class="sxs-lookup"><span data-stu-id="b5c3c-117">This requires a mobile platform and requires a mindset similar to creating mobile applications.</span></span> <span data-ttu-id="b5c3c-118">Microsoft recomienda que la aplicación HoloLens mantenga 60FPS para proporcionar una experiencia de deliciosa a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="b5c3c-118">Microsoft recommends that your HoloLens application maintain 60FPS to provide a delicious experience for your users.</span></span> <span data-ttu-id="b5c3c-119">Tener pocos FPS puede producir hologramas inestables.</span><span class="sxs-lookup"><span data-stu-id="b5c3c-119">Having low FPS can result in unstable holograms.</span></span>

<span data-ttu-id="b5c3c-120">Algunos de los aspectos más importantes que se deben tener en cuentan al desarrollar en HoloLens son la optimización o la diezmación de recursos, el uso de sombreadores personalizados (disponibles de forma gratuita en el [Kit de herramientas de hololens](https://github.com/Microsoft/HoloToolkit-Unity)).</span><span class="sxs-lookup"><span data-stu-id="b5c3c-120">Some of the most important things to look at when developing on HoloLens is asset optimization/decimation, using custom shaders (available for free in the [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)).</span></span> <span data-ttu-id="b5c3c-121">Otra consideración importante es medir la velocidad de fotogramas desde el principio del proyecto.</span><span class="sxs-lookup"><span data-stu-id="b5c3c-121">Another important consideration is to measure the frame rate from the very beginning of your project.</span></span> <span data-ttu-id="b5c3c-122">Dependiendo del proyecto, el orden de visualización de los activos también puede ser un gran colaborador</span><span class="sxs-lookup"><span data-stu-id="b5c3c-122">Depending on the project, the order of displaying your assets can also be a big contributor</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a><span data-ttu-id="b5c3c-123">Vídeo 2</span><span class="sxs-lookup"><span data-stu-id="b5c3c-123">Video 2</span></span>

<span data-ttu-id="b5c3c-124">**Creación de métodos de experiencia del usuario con un marco holográfica completo** Es importante comprender la colocación de los hologramas en un mundo físico.</span><span class="sxs-lookup"><span data-stu-id="b5c3c-124">**Create UX methods with a full holographic frame** It's important to understand the placement of holograms in a physical world.</span></span> <span data-ttu-id="b5c3c-125">Con Lowe, hablamos de distintos métodos de la experiencia del usuario que ayudan a los usuarios a experimentar cerca de los hologramas mientras siguen viendo el entorno más grande de los hologramas.</span><span class="sxs-lookup"><span data-stu-id="b5c3c-125">With Lowe's we talk about different UX methods that help users experience holograms up close while still seeing the larger environment of holograms.</span></span>

<span data-ttu-id="b5c3c-126">**Alineación de precisión** En el escenario de Lowe, era primordial para la experiencia tener una alineación de precisión de los hologramas en la cocina física.</span><span class="sxs-lookup"><span data-stu-id="b5c3c-126">**Precision alignment** For the Lowe's scenario, it was paramount to the experience to have precision alignment of the holograms to the physical kitchen.</span></span> <span data-ttu-id="b5c3c-127">Se describen técnicas que ayudan a garantizar una experiencia que convenci a los usuarios de que su entorno físico ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="b5c3c-127">We discuss techniques helps ensure an experience that convinces users that their physical environment has changed.</span></span>

<span data-ttu-id="b5c3c-128">**Experiencias de Holographic** compartidas Los acoplados son la forma principal en que se consume la experiencia del Lowe.</span><span class="sxs-lookup"><span data-stu-id="b5c3c-128">**Shared holographic experiences** Couples are the primary way that the Lowe's experience is consumed.</span></span> <span data-ttu-id="b5c3c-129">Una persona puede cambiar la encimera y la otra persona verá los cambios.</span><span class="sxs-lookup"><span data-stu-id="b5c3c-129">One person can change the countertop and the other person will see the changes.</span></span> <span data-ttu-id="b5c3c-130">Hemos llamado a este "experiencias compartidas".</span><span class="sxs-lookup"><span data-stu-id="b5c3c-130">We called this "shared experiences".</span></span>

<span data-ttu-id="b5c3c-131">**Interactuar con los clientes** Los diseñadores de Lowe no usan HoloLens, pero necesitan ver lo que ven los clientes.</span><span class="sxs-lookup"><span data-stu-id="b5c3c-131">**Interacting with customers** Lowe's designers are not using a HoloLens, but they need to see what the customers are seeing.</span></span> <span data-ttu-id="b5c3c-132">Mostramos cómo capturar lo que el cliente está viendo en una aplicación de UWP.</span><span class="sxs-lookup"><span data-stu-id="b5c3c-132">We show how to capture what the customer is seeing on a UWP application.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
