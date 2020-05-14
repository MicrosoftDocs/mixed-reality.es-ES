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
# <a name="performance-recommendations-for-unreal"></a>Recomendaciones de rendimiento para Unreal

Este artículo se basa en la explicación que se indica en las [recomendaciones de rendimiento para la realidad mixta](understanding-performance-for-mixed-reality.md), pero se centra en los conocimientos específicos del entorno de Unreal Engine.

## <a name="recommended-unreal-project-settings"></a>Configuración del proyecto de Unreal recomendada

- Usa el representador de VR: en la configuración del proyecto, comprueba que la plataforma de destino sea "Mobile/Tablet" (Móvil/tablet) en "Project – Target Hardware" (Proyecto: hardware de destino).
- Deshabilita la selección: en "Engine – Rendering" (Motor: representación), en la sección "Culling" (Selección), desmarca "Occlusion Culling" (Selección de oclusión).
    + Si la selección de oclusión es necesaria porque se debe representar una escena muy detallada, es recomendable habilitar "Support Software Occlusion Culling" (Admitir selección de oclusión de software) en "Engine – Rendering" (Motor: representación). Esto permite que Unreal realice la selección de oclusión en la CPU y evita las consultas de oclusión de GPU, que tienen un rendimiento bajo en HoloLens 2.
- Habilita "Instanced Stereo" (Estéreo con instancias) y "Mobile Multi-View" (Multivista móvil) en "Engine – Rendering" (Motor:representación), en la categoría "VR". Es posible que tengas que desactivar "Mobile Post-Processing" (Posprocesamiento móvil) para poder activar "Mobile Multi-View" (Multivista móvil).
