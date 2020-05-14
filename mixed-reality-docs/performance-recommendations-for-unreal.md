---
title: Recomendaciones de rendimiento para Unreal
description: Recomendaciones para un rendimiento óptimo de las aplicaciones de realidad mixta en Unreal
author: sw5813
ms.author: suwu
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, performance, optimization, settings, documentation
ms.openlocfilehash: 1fab2f714628f61a518d89795cf644e90130200a
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82840204"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="ab859-104">Recomendaciones de rendimiento para Unreal</span><span class="sxs-lookup"><span data-stu-id="ab859-104">Performance recommendations for Unreal</span></span>

<span data-ttu-id="ab859-105">Este artículo se basa en la explicación que se indica en las [recomendaciones de rendimiento para la realidad mixta](understanding-performance-for-mixed-reality.md), pero se centra en los conocimientos específicos del entorno de Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="ab859-105">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md) but focuses on learnings specific to the Unreal Engine environment.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="ab859-106">Configuración del proyecto de Unreal recomendada</span><span class="sxs-lookup"><span data-stu-id="ab859-106">Recommended Unreal project settings</span></span>

- <span data-ttu-id="ab859-107">Usa el representador de VR: en la configuración del proyecto, comprueba que la plataforma de destino sea "Mobile/Tablet" (Móvil/tablet) en "Project – Target Hardware" (Proyecto: hardware de destino).</span><span class="sxs-lookup"><span data-stu-id="ab859-107">Use the mobile VR renderer- in your project settings, ensure your target platform is set to "Mobile/Tablet" under "Project – Target Hardware"</span></span>
- <span data-ttu-id="ab859-108">Deshabilita la selección: en "Engine – Rendering" (Motor: representación), en la sección "Culling" (Selección), desmarca "Occlusion Culling" (Selección de oclusión).</span><span class="sxs-lookup"><span data-stu-id="ab859-108">Disable occlusion culling- under "Engine – Rendering" in the "Culling" section, uncheck "Occlusion Culling"</span></span>
    + <span data-ttu-id="ab859-109">Si la selección de oclusión es necesaria porque se debe representar una escena muy detallada, es recomendable habilitar "Support Software Occlusion Culling" (Admitir selección de oclusión de software) en "Engine – Rendering" (Motor: representación).</span><span class="sxs-lookup"><span data-stu-id="ab859-109">If occlusion culling is required because a very detailed scene needs to be rendered, it is recommended that "Support Software Occlusion Culling" is enabled Under "Engine – Rendering".</span></span> <span data-ttu-id="ab859-110">Esto permite que Unreal realice la selección de oclusión en la CPU y evita las consultas de oclusión de GPU, que tienen un rendimiento bajo en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ab859-110">This allows Unreal to do occlusion culling on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
- <span data-ttu-id="ab859-111">Habilita "Instanced Stereo" (Estéreo con instancias) y "Mobile Multi-View" (Multivista móvil) en "Engine – Rendering" (Motor:representación), en la categoría "VR".</span><span class="sxs-lookup"><span data-stu-id="ab859-111">Enable both "Instanced Stereo" and "Mobile Multi-View" under "Engine – Rendering" in the "VR" category.</span></span> <span data-ttu-id="ab859-112">Es posible que tengas que desactivar "Mobile Post-Processing" (Posprocesamiento móvil) para poder activar "Mobile Multi-View" (Multivista móvil).</span><span class="sxs-lookup"><span data-stu-id="ab859-112">You may need to uncheck "Mobile Post-Processing" in order to be able to check "Mobile Multi-View"</span></span>
