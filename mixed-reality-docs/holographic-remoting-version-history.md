---
title: Historial de versiones de Holographic Remoting
description: Historial de versiones de Holographic Remoting en HoloLens 2.
author: NPohl-MSFT
ms.author: nopohl
ms.date: 10/21/2019
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota de Holographic
ms.openlocfilehash: 75e7c276560b4efbbdcbf2ea7579ed5ad7aadb4d
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439236"
---
# <a name="holographic-remoting-version-history"></a>Historial de versiones de Holographic Remoting

> [!IMPORTANT]
> Esta guía es específica de Holographic Remoting en HoloLens 2.

## Versión 2.0.14 (26 de octubre de 2019)<a name="v2.0.14"></a>
* Compatibilidad con las nuevas API de PerceptionDevice (actualización 2019 de noviembre de Windows 10).
* Se corrigió un problema que impide que SpatialGestureRecognizer Active los eventos de gestos.
* Se corrigió el problema de theading al usar SpatialSurfaceObserver. SetBoundingVolume.

## Versión 2.0.12 (18 de octubre de 2019)<a name="v2.0.12"></a>
* Se corrigió el bloqueo en SpatialGestureRecognizer al usar NavigationRail (X/Y/Z).

## Versión 2.0.10 (10 de octubre de 2019)<a name="v2.0.10"></a>
* Se corrigió un bloqueo al usar el botón desencadenador de controladores de VR. Holographic Remoting no es totalmente compatible con los controladores, solo el botón desencadenador y el botón Windows funcionan si se emparejan con HoloLens 2.

## Versión 2.0.9 (19 de septiembre de 2019)<a name="v2.0.9"></a>
* Compatibilidad agregada para [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)
* Agregada nueva ```IPlayerContext2``` de interfaz (implementada por ```PlayerContext```) que proporciona los siguientes miembros:
  - Propiedad [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) .
* Se agregó ```Failed_RemoteFrameTooOld``` valor a ```BlitResult```
* Mejoras en la estabilidad y confiabilidad

## Versión 2.0.8 (20 de agosto de 2019)<a name="v2.0.8"></a>

* Se corrigió un bloqueo al llamar a [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) con un parámetro [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) como.
* Mejoras en la estabilidad y confiabilidad

## Versión 2.0.7 (26 de julio de 2019)<a name="v2.0.7"></a>

* Primera versión pública de Holographic Remoting para HoloLens 2.

## <a name="see-also"></a>Consulta también
* [Escritura de una aplicación de reproductor remoto holográfica personalizada](holographic-remoting-create-player.md)
* [Escritura de una aplicación de host de Holographic Remoting](holographic-remoting-create-host.md)
* [Solución de problemas y limitaciones de la comunicación remota holográfica](holographic-remoting-troubleshooting.md)
* [Términos de licencia del software de control remoto de holografías](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)