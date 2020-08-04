---
title: 'Tutoriales de introducción: 1. Introducción'
description: En este curso le mostramos cómo usar Mixed Reality Toolkit (MRTK) para crear una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 330863d36abe051e8fe17b87ce913b1b110e2d3d
ms.sourcegitcommit: 2f5f95a9ca1b02d94eb9163f0f4ff6b1e4126de2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/29/2020
ms.locfileid: "87376437"
---
# <a name="1-introduction"></a><span data-ttu-id="4d305-105">1. Introducción</span><span class="sxs-lookup"><span data-stu-id="4d305-105">1. Introduction</span></span>

## <a name="overview"></a><span data-ttu-id="4d305-106">Introducción</span><span class="sxs-lookup"><span data-stu-id="4d305-106">Overview</span></span>

<span data-ttu-id="4d305-107">¡Le damos la bienvenida a la serie de tutoriales de introducción!</span><span class="sxs-lookup"><span data-stu-id="4d305-107">Welcome to the Getting Started tutorial series!</span></span> <span data-ttu-id="4d305-108">En el transcurso de estos tutoriales, aprenderá sobre Mixed Reality Toolkit (MRTK) y algunas de las características que ofrece.</span><span class="sxs-lookup"><span data-stu-id="4d305-108">Over the course of these tutorials, you'll learn about the Mixed Reality Toolkit (MRTK) and some of the features it has to offer.</span></span> <span data-ttu-id="4d305-109">También creará una experiencia de realidad mixta en la que el usuario podrá explorar un holograma basado en el vehículo explorador de Marte Curiosity de la NASA.</span><span class="sxs-lookup"><span data-stu-id="4d305-109">You'll also build a mixed reality experience where the user can explore a hologram modeled after NASA's Mars Curiosity Rover.</span></span> <span data-ttu-id="4d305-110">Al final de esta serie, tendrá un buen dominio de MRTK y de cómo puede acelerar el proceso de desarrollo.</span><span class="sxs-lookup"><span data-stu-id="4d305-110">By the end of this series, you'll have a firm grasp of MRTK and how it can speed up your development process.</span></span>

<span data-ttu-id="4d305-111">Los tutoriales de esta serie están diseñados para realizarse de forma secuencial, por lo que debe repasarlos en el orden correcto:</span><span class="sxs-lookup"><span data-stu-id="4d305-111">Tutorials in this series are meant to be sequential, so please go through them in the correct order:</span></span>

1. [<span data-ttu-id="4d305-112">Introducción</span><span class="sxs-lookup"><span data-stu-id="4d305-112">Introduction</span></span>](mr-learning-base-01.md)
2. [<span data-ttu-id="4d305-113">Inicialización de su proyecto e implementación de su primera aplicación</span><span class="sxs-lookup"><span data-stu-id="4d305-113">Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
3. [<span data-ttu-id="4d305-114">Configuración de los perfiles de MRTK</span><span class="sxs-lookup"><span data-stu-id="4d305-114">Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
4. [<span data-ttu-id="4d305-115">Posicionamiento de los objetos en la escena</span><span class="sxs-lookup"><span data-stu-id="4d305-115">Positioning objects in the scene</span></span>](mr-learning-base-04.md)
5. [<span data-ttu-id="4d305-116">Creación de contenido dinámico mediante solucionadores</span><span class="sxs-lookup"><span data-stu-id="4d305-116">Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
6. [<span data-ttu-id="4d305-117">Creación de interfaces de usuario</span><span class="sxs-lookup"><span data-stu-id="4d305-117">Creating user interfaces</span></span>](mr-learning-base-06.md)
7. [<span data-ttu-id="4d305-118">Interacción con objetos 3D</span><span class="sxs-lookup"><span data-stu-id="4d305-118">Interacting with 3D objects</span></span>](mr-learning-base-07.md)
8. [<span data-ttu-id="4d305-119">Uso del seguimiento ocular</span><span class="sxs-lookup"><span data-stu-id="4d305-119">Using eye-tracking</span></span>](mr-learning-base-08.md)
9. [<span data-ttu-id="4d305-120">Uso de los comandos de voz</span><span class="sxs-lookup"><span data-stu-id="4d305-120">Using voice commands</span></span>](mr-learning-base-09.md)

## <a name="objectives"></a><span data-ttu-id="4d305-121">Objetivos</span><span class="sxs-lookup"><span data-stu-id="4d305-121">Objectives</span></span>

* <span data-ttu-id="4d305-122">Aprender a configurar Unity para MRTK</span><span class="sxs-lookup"><span data-stu-id="4d305-122">Learn how to configure Unity for MRTK</span></span>
* <span data-ttu-id="4d305-123">Aprender a crear e implementar en su dispositivo</span><span class="sxs-lookup"><span data-stu-id="4d305-123">Learn how to build and deploy to your device</span></span>
* <span data-ttu-id="4d305-124">Aprender a usar algunas de las características importantes de MRTK</span><span class="sxs-lookup"><span data-stu-id="4d305-124">Learn how to use some of MRTK's key features</span></span>
* <span data-ttu-id="4d305-125">Crear una experiencia de realidad mixta completa</span><span class="sxs-lookup"><span data-stu-id="4d305-125">Create a complete mixed reality experience</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4d305-126">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="4d305-126">Prerequisites</span></span>

* <span data-ttu-id="4d305-127">Un equipo Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="4d305-127">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="4d305-128">[SDK de Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) versión 10.0.18362.0 o posterior</span><span class="sxs-lookup"><span data-stu-id="4d305-128">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 or later</span></span>
* <span data-ttu-id="4d305-129">Un dispositivo HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="4d305-129">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="4d305-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.3.15 instalado y el módulo de compatibilidad de la compilación de la Plataforma universal de Windows agregado</span><span class="sxs-lookup"><span data-stu-id="4d305-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="4d305-131">La versión de MRTK recomendada para esta serie de tutoriales es MRTK 2.4.0.</span><span class="sxs-lookup"><span data-stu-id="4d305-131">The recommended MRTK version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="4d305-132">La versión de Unity recomendada para esta serie de tutoriales es Unity 2019.3.15.</span><span class="sxs-lookup"><span data-stu-id="4d305-132">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="4d305-133">Esta sustituye los requisitos de versión de Unity descritas en los requisitos previos vinculados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="4d305-133">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="4d305-134">Tutorial siguiente: 2. Inicialización de su proyecto e implementación de su primera aplicación</span><span class="sxs-lookup"><span data-stu-id="4d305-134">Next Tutorial: 2. Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
