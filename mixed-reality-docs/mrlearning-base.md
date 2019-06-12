---
title: Introducción del módulo MR Learning Base
description: Realice este curso para obtener información sobre cómo implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: realidad mixta, unity, tutorial, hololens
ms.openlocfilehash: 2fe07efe87086e9a8c06e1953fcef8544b03c80a
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829883"
---
# <a name="mr-learning-base-module-overview--objectives"></a><span data-ttu-id="e3fca-104">Información general del módulo MR Learning Base & de objetivos</span><span class="sxs-lookup"><span data-stu-id="e3fca-104">MR Learning Base Module Overview & Objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="e3fca-105">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="e3fca-105">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="e3fca-106"><strong>Curso</strong></span><span class="sxs-lookup"><span data-stu-id="e3fca-106"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="e3fca-107"><a href="hololens-hardware-details.md"><strong>HoloLens (gen 1)</strong></a></span><span class="sxs-lookup"><span data-stu-id="e3fca-107"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="e3fca-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="e3fca-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="e3fca-109"><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="e3fca-109"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td><span data-ttu-id="e3fca-110">❌</span><span class="sxs-lookup"><span data-stu-id="e3fca-110">❌</span></span></td>
        <td><span data-ttu-id="e3fca-111">✔️</span><span class="sxs-lookup"><span data-stu-id="e3fca-111">✔️</span></span></td>
        <td><span data-ttu-id="e3fca-112">❌</span><span class="sxs-lookup"><span data-stu-id="e3fca-112">❌</span></span></td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="e3fca-113">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="e3fca-113">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="e3fca-114">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="e3fca-114">Prerequisites</span></span>

* <span data-ttu-id="e3fca-115">Un equipo con Windows 10 configurado con el valor correcto [herramientas instaladas](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="e3fca-115">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="e3fca-116">10.0.18362.0 del SDK de Windows 10 o posterior</span><span class="sxs-lookup"><span data-stu-id="e3fca-116">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="e3fca-117">Básica C# capacidad de programación.</span><span class="sxs-lookup"><span data-stu-id="e3fca-117">Some basic C# programming ability.</span></span>
* <span data-ttu-id="e3fca-118">Un dispositivo HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="e3fca-118">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>
