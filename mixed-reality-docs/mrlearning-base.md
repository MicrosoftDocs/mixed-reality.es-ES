---
title: 'Tutoriales de introducción: 1. Introducción y objetivos'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 36c12d82759b8ac2ba24aa9af37a096e0faf5fb5
ms.sourcegitcommit: ee8c7e821cb337cbccd8af64b13ee5f50109a776
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082046"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="795a9-105">1. Introducción y objetivos</span><span class="sxs-lookup"><span data-stu-id="795a9-105">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="795a9-106">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="795a9-106">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="795a9-107"><strong>Curso</strong></span><span class="sxs-lookup"><span data-stu-id="795a9-107"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="795a9-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="795a9-108"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="795a9-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="795a9-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="795a9-110"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="795a9-110"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td>❌</td>
        <td><span data-ttu-id="795a9-111">✔️</span><span class="sxs-lookup"><span data-stu-id="795a9-111">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="795a9-112">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="795a9-112">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="795a9-113">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="795a9-113">Prerequisites</span></span>

* <span data-ttu-id="795a9-114">Un equipo Windows 10 configurado con las [herramientas instaladas](install-the-tools.md) correctas</span><span class="sxs-lookup"><span data-stu-id="795a9-114">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="795a9-115">SDK de Windows 10 10.0.18362.0 o posterior</span><span class="sxs-lookup"><span data-stu-id="795a9-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="795a9-116">Capacidad básica para programar con C#</span><span class="sxs-lookup"><span data-stu-id="795a9-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="795a9-117">Un dispositivo HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode)</span><span class="sxs-lookup"><span data-stu-id="795a9-117">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="795a9-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> con Unity 2019.2.X instalado y el módulo de compatibilidad con la compilación de la Plataforma universal de Windows agregado</span><span class="sxs-lookup"><span data-stu-id="795a9-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="795a9-119">La versión de Unity recomendada para esta serie de tutoriales es Unity 2019.2.X.</span><span class="sxs-lookup"><span data-stu-id="795a9-119">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="795a9-120">Esta sustituye los requisitos de versión de Unity o las recomendaciones descritas en los requisitos previos vinculados anteriormente.</span><span class="sxs-lookup"><span data-stu-id="795a9-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="795a9-121">Siguiente lección: 2. Inicialización del proyecto y primera aplicación</span><span class="sxs-lookup"><span data-stu-id="795a9-121">Next lesson: 2. Initializing your project and first application</span></span>](mrlearning-base-ch1.md)
