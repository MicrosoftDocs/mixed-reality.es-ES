---
title: Introducción del módulo MR Learning Base
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 389a23129d4dfc5819cdc45d071b678e3792089d
ms.sourcegitcommit: cf9f8ebbca0301e9d277853771ff6e47701ba1c1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2019
ms.locfileid: "67523153"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="e0359-104">1. Información general y objetivos</span><span class="sxs-lookup"><span data-stu-id="e0359-104">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="e0359-105">Compatibilidad con dispositivos</span><span class="sxs-lookup"><span data-stu-id="e0359-105">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="e0359-106"><strong>Curso</strong></span><span class="sxs-lookup"><span data-stu-id="e0359-106"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="e0359-107"><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></span><span class="sxs-lookup"><span data-stu-id="e0359-107"><a href="hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="e0359-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="e0359-108"><a href="https://www.microsoft.com/en-us/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="e0359-109"><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></span><span class="sxs-lookup"><span data-stu-id="e0359-109"><a href="immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td><span data-ttu-id="e0359-110">❌</span><span class="sxs-lookup"><span data-stu-id="e0359-110">❌</span></span></td>
        <td><span data-ttu-id="e0359-111">✔️</span><span class="sxs-lookup"><span data-stu-id="e0359-111">✔️</span></span></td>
        <td><span data-ttu-id="e0359-112">❌</span><span class="sxs-lookup"><span data-stu-id="e0359-112">❌</span></span></td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="e0359-113">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="e0359-113">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="e0359-114">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="e0359-114">Prerequisites</span></span>

* <span data-ttu-id="e0359-115">Un equipo con Windows 10 configurado con el valor correcto [herramientas instaladas](install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="e0359-115">A Windows 10 PC configured with the correct [tools installed](install-the-tools.md)</span></span>
* <span data-ttu-id="e0359-116">10.0.18362.0 del SDK de Windows 10 o posterior</span><span class="sxs-lookup"><span data-stu-id="e0359-116">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="e0359-117">Básica C# capacidad de programación.</span><span class="sxs-lookup"><span data-stu-id="e0359-117">Some basic C# programming ability.</span></span>
* <span data-ttu-id="e0359-118">Un dispositivo HoloLens 2 [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).</span><span class="sxs-lookup"><span data-stu-id="e0359-118">A HoloLens 2 device [configured for development](using-visual-studio.md#enabling-developer-mode).</span></span>
