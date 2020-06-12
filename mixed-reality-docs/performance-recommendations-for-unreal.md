---
title: Recomendaciones de rendimiento para Unreal
description: Recomendaciones para un rendimiento óptimo de las aplicaciones de realidad mixta en Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, performance, optimization, settings, documentation
ms.openlocfilehash: 3c65eb519b57457e6c9e9747af0ad75e6a5e1b4d
ms.sourcegitcommit: 1b8090ba6aed9ff128e4f32d40c96fac2e6a220b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/03/2020
ms.locfileid: "84330209"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="9528e-104">Recomendaciones de rendimiento para Unreal</span><span class="sxs-lookup"><span data-stu-id="9528e-104">Performance recommendations for Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="9528e-105">Introducción</span><span class="sxs-lookup"><span data-stu-id="9528e-105">Overview</span></span>

<span data-ttu-id="9528e-106">Este artículo se basa en la explicación que se indica en las [recomendaciones de rendimiento para la realidad mixta](understanding-performance-for-mixed-reality.md), pero se centra en las características específicas de Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="9528e-106">This article builds on the discussion outlined in [performance recommendations for mixed reality](understanding-performance-for-mixed-reality.md), but focuses on features specific to Unreal Engine.</span></span> <span data-ttu-id="9528e-107">Le recomendamos que lea la información sobre los cuellos de botella de las aplicaciones, para analizar y generar perfiles de aplicaciones de realidad mixta, y las correcciones de rendimiento general antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="9528e-107">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="9528e-108">Configuración del proyecto de Unreal recomendada</span><span class="sxs-lookup"><span data-stu-id="9528e-108">Recommended Unreal project settings</span></span>
<span data-ttu-id="9528e-109">Puede encontrar cada una de las siguientes opciones en **Edit > Project Settings** (Editar > Configuración del proyecto).</span><span class="sxs-lookup"><span data-stu-id="9528e-109">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="9528e-110">Uso el representador de VR móvil:</span><span class="sxs-lookup"><span data-stu-id="9528e-110">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="9528e-111">Desplácese hasta la sección **Project** (Proyecto), seleccione **Target Hardware** (Hardware de destino) y establezca la plataforma de destino en **Mobile/Tablet** (Móvil o tableta).</span><span class="sxs-lookup"><span data-stu-id="9528e-111">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![Configuración de destino móvil](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="9528e-113">Deshabilitación de la selección de la oclusión:</span><span class="sxs-lookup"><span data-stu-id="9528e-113">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="9528e-114">Desplácese hasta la sección **Engine** (Motor), seleccione **Rendering** (Representación), expanda la sección **Culling** (Selección) y quite la marca de **Occlusion Culling** (Selección de la oclusión).</span><span class="sxs-lookup"><span data-stu-id="9528e-114">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="9528e-115">Si necesita la selección de la oclusión para una escena detallada que se está representando, se recomienda que habilite **Support Software Occlusion Culling** (Compatibilidad de la selección de la oclusión del software) en **Engine > Rendering** (Motor > Representación).</span><span class="sxs-lookup"><span data-stu-id="9528e-115">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Cullin** in **Engine > Rendering**.</span></span> <span data-ttu-id="9528e-116">Esto permite que Unreal realice el trabajo en la CPU y evita las consultas de oclusión de GPU, que tienen un rendimiento bajo en HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="9528e-116">This lets Unreal to do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>

![Configuración de destino móvil](images/unreal/performance-recommendations-img-02.png)

3. <span data-ttu-id="9528e-118">Actualización de la representación VR:</span><span class="sxs-lookup"><span data-stu-id="9528e-118">Updating VR rendering:</span></span>
    * <span data-ttu-id="9528e-119">Desplácese hasta la sección **Engine** (Motor), seleccione **Rendering** (Representación), expanda la sección **VR** y habilite ambas opciones, **Instanced Stereo** (Estéreo con instancias) y **Mobile Multi-View** (Multivista móvil).</span><span class="sxs-lookup"><span data-stu-id="9528e-119">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span>
        + <span data-ttu-id="9528e-120">Es posible que tenga que desactivar **Mobile Post-Processing** (Posprocesamiento móvil) para poder activar **Mobile Multi-View** (Multivista móvil).</span><span class="sxs-lookup"><span data-stu-id="9528e-120">You may need to uncheck **Mobile Post-Processing** in order to be able to check **Mobile Multi-View**</span></span>

![Configuración de destino móvil](images/unreal/performance-recommendations-img-03.png)
