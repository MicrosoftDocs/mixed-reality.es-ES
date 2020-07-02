---
title: Recomendaciones de rendimiento para Unreal
description: Recomendaciones para un rendimiento óptimo de las aplicaciones de realidad mixta en Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, performance, optimization, settings, documentation
ms.openlocfilehash: 9f128a3ef09f29fc745c21b09b7ec97f5db33605
ms.sourcegitcommit: 7f50210b71a65631fd1bc3fdb215064e0db34333
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "84533127"
---
# <a name="performance-recommendations-for-unreal"></a>Recomendaciones de rendimiento para Unreal

## <a name="overview"></a>Introducción

Este artículo se basa en la explicación que se indica en las [recomendaciones de rendimiento para la realidad mixta](understanding-performance-for-mixed-reality.md), pero se centra en las características específicas de Unreal Engine. Le recomendamos que lea la información sobre los cuellos de botella de las aplicaciones, para analizar y generar perfiles de aplicaciones de realidad mixta, y las correcciones de rendimiento general antes de continuar.

## <a name="recommended-unreal-project-settings"></a>Configuración del proyecto de Unreal recomendada
Puede encontrar cada una de las siguientes opciones en **Edit > Project Settings** (Editar > Configuración del proyecto).

1. Uso el representador de VR móvil:
    * Desplácese hasta la sección **Project** (Proyecto), seleccione **Target Hardware** (Hardware de destino) y establezca la plataforma de destino en **Mobile/Tablet** (Móvil o tableta).

![Configuración de destino móvil](images/unreal/performance-recommendations-img-01.png)

2. Deshabilitación de la selección de la oclusión:
    * Desplácese hasta la sección **Engine** (Motor), seleccione **Rendering** (Representación), expanda la sección **Culling** (Selección) y quite la marca de **Occlusion Culling** (Selección de la oclusión).
        + Si necesita la selección de la oclusión para una escena detallada que se está representando, se recomienda que habilite **Support Software Occlusion Culling** (Compatibilidad de la selección de la oclusión del software) en **Engine > Rendering** (Motor > Representación). Esto permite que Unreal realice el trabajo en la CPU y evita las consultas de oclusión de GPU, que tienen un rendimiento bajo en HoloLens 2.

![Configuración de destino móvil](images/unreal/performance-recommendations-img-02.png)

3. Actualización de la representación VR:
    * Desplácese hasta la sección **Engine** (Motor), seleccione **Rendering** (Representación), expanda la sección **VR** y habilite ambas opciones, **Instanced Stereo** (Estéreo con instancias) y **Mobile Multi-View** (Multivista móvil).
        + Es posible que tenga que desactivar **Mobile Post-Processing** (Posprocesamiento móvil) para poder activar **Mobile Multi-View** (Multivista móvil).

![Configuración de destino móvil](images/unreal/performance-recommendations-img-03.png)
