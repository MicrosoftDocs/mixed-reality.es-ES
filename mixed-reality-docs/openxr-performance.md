---
title: Rendimiento de OpenXR
description: Depure el rendimiento de la GPU de las aplicaciones de OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, Native, aplicación nativa, motor personalizado, middleware, rendimiento, optimización, depuración de GPU, RenderDoc, PIX
ms.openlocfilehash: 717dc2d534773bd28f5ad2d5c3720bf4177a1480
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163349"
---
# <a name="openxr-performance"></a>Rendimiento de OpenXR

En HoloLens 2, hay varias formas de enviar datos de composición a través de `xrEndFrame`, lo que dará lugar a un procesamiento posterior que tendrá una penalización notable en el rendimiento.
Para evitar las penalizaciones de rendimiento, [envíe un solo `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) con las siguientes características:
* [Usar una matriz de textura intercambio](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [Usar el formato intercambio de color principal](openxr-best-practices.md#select-a-swapchain-format)
* [Usar las dimensiones de vista recomendadas](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* No establezca la marca de `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT`
* Establezca la `XrCompositionLayerDepthInfoKHR` `minDepth` en 0.0 f y `maxDepth` en 1,0 f.

Otras consideraciones darán lugar a un mejor rendimiento:
* [Usar el formato de profundidad de 16 bits](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [Realizar llamadas a Draw con instancias](openxr-best-practices.md#render-with-texture-array-and-vprt)
