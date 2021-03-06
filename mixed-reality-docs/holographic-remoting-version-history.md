---
title: Historial de versiones de Holographic Remoting
description: Historial de versiones de Holographic Remoting en HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota de Holographic
ms.openlocfilehash: 1f4d463ab734cbb627f251486b0058fbf295d2ed
ms.sourcegitcommit: b392847529961ac36bbff154ce0830f8b2dbd766
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/14/2020
ms.locfileid: "86300527"
---
# <a name="holographic-remoting-version-history"></a>Historial de versiones de Holographic Remoting

> [!IMPORTANT]
> Esta guía es específica de Holographic Remoting en HoloLens 2.

## <a name="version-222-july-10-2020"></a>Versión 2.2.2 (10 de julio de 2020)<a name="v2.2.2"></a>
* Se corrigió un problema con [HolographicCamera. LeftViewportParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.leftviewportparameters?view=winrt-19041#Windows_Graphics_Holographic_HolographicCamera_LeftViewportParameters) y [HolographicCamera. RightViewportParameters](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.rightviewportparameters?view=winrt-19041#Windows_Graphics_Holographic_HolographicCamera_RightViewportParameters) que no devuelve ningún vértice de malla de área oculta cuando se transmite desde un casco de realidad mixta de Windows.
* Se ha corregido un bloqueo que puede producirse cuando la conexión de red es deficiente.

## <a name="version-221-july-6-2020"></a>Versión 2.2.1 (6 de julio de 2020)<a name="v2.2.1"></a>
> [!IMPORTANT]
> La validación del [Kit de certificación de aplicaciones de Windows](https://developer.microsoft.com/windows/downloads/app-certification-kit/) con la versión [2.2.0](holographic-remoting-version-history.md#v2.2.0) producirá un error. En caso de que se encuentre en la versión [2.2.0](holographic-remoting-version-history.md#v2.2.0) y desee enviar su aplicación a Microsoft Store, actualice al menos la versión 2.2.1.
* Problemas de compatibilidad con el [Kit de certificación de aplicaciones de Windows](https://developer.microsoft.com/windows/downloads/app-certification-kit/) .

## <a name="version-220-july-1-2020"></a>Versión 2.2.0 (1 de julio de 2020)<a name="v2.2.0"></a>
* El reproductor de comunicación remota holográfica ahora se puede instalar en equipos que ejecutan [Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md), lo que permite la transmisión por secuencias a auriculares envolventes.
* [Los controladores de movimiento](motion-controllers.md) ahora son compatibles con la comunicación remota holográfica y los datos específicos del controlador se pueden recuperar a través de [SpatialInteractionSource. Controller](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller).
* Ahora se admite [SpatialStageFrameOfReference](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference) y la fase actual se puede recuperar a través de [SpatialStageFrameOfReference. Current](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current). Además, se puede solicitar una nueva fase a través de [SpatialStageFrameOfReference. RequestNewStageAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync).
* En las versiones anteriores, la predicción de supuestos se administraba completamente en el reproductor de Holographic Remoting. A partir de la versión 2.2.0, Holographic Remoting tiene sincronización de hora y la aplicación remota realiza la predicción por completo. Los usuarios también deben esperar una mejor estabilidad del holograma en situaciones de red difíciles.

## <a name="version-213-may-25-2020"></a>Versión 2.1.3 (25 de mayo de 2020)<a name="v2.1.3"></a>
* Se ha cambiado el comportamiento del evento [HolographicSpace. CameraAdded](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.cameraadded?view=winrt-18362) . En versiones anteriores **no** se garantizaba que un [HolographicCamera](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera?view=winrt-18362) agregado también tenga un [HolographicCameraPose](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose?view=winrt-18362) válido al crear el siguiente fotograma a través de [HolographicSpace. CreateNextFrame](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createnextframe?view=winrt-18362#Windows_Graphics_Holographic_HolographicSpace_CreateNextFrame). A partir de la versión 2.1.3, [HolographicSpace. CameraAdded](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.cameraadded?view=winrt-18362) se sincroniza con los datos de pose procedentes del reproductor de comunicación remota holográfica y los usuarios pueden esperar que cuando se agrega una cámara, también haya una [HolographicCameraPose](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose?view=winrt-18362) válida disponible para esa cámara en el siguiente fotograma.
* Se ha agregado **deshabilitado** a DepthBufferStreamResolution, que se puede usar para deshabilitar el streaming de búfer de profundidad a través de RemoteContext.ConfigureDepthVideoStream. Tenga en cuenta que, si se usa [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer?view=winrt-18362#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) , se producirá un error con *E_ILLEGAL_METHOD_CALL*.
* La pantalla de inicio del reproductor remoto Holographic se ha rediseñado y ahora no bloquea la vista de usuarios.
* Mejoras de estabilidad y correcciones de errores.

## <a name="version-212-april-5-2020"></a>Versión 2.1.2 (5 de abril de 2020)<a name="v2.1.2"></a>
* Se corrigió el problema de compatibilidad con versiones anteriores de audio entre el reproductor remoto Holographic y las aplicaciones remotas con una versión inferior a la 2.1.0.
* Problema fijo de delimitador espacial que cerró inesperadamente el reproductor de comunicación remota holográfica. Este problema también afecta a los reproductores personalizados.

## <a name="version-211-march-20-2020"></a>Versión 2.1.1 (20 de marzo de 2020)<a name="v2.1.1"></a>
* Se corrigió el problema de codificación de vídeo con las aplicaciones remotas al usar GPU AMD.
* Mejoras en el rendimiento del reproductor remoto holográfica.

## <a name="version-210-march-11-2020"></a>Versión 2.1.0 (11 de marzo de 2020)<a name="v2.1.0"></a>
* Transporte de red conmutada para usar [RTP](https://en.wikipedia.org/wiki/Real-time_Transport_Protocol) a través de UDP. Conexiones seguras use [SRTP](https://en.wikipedia.org/wiki/Secure_Real-time_Transport_Protocol) ahora. Tenga en cuenta que el [reproductor de comunicación remota holográfica](holographic-remoting-player.md) todavía es compatible con todas las versiones anteriores de Holographic Remoting. Para beneficiarse del nuevo transporte de red, el reproductor de comunicación remota holográfica y la aplicación remota en cuestión deben usar la versión 2.1.0.
* Compatibilidad agregada para [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_). 

## <a name="version-2020-february-2-2020"></a>Versión 2.0.20 (2 de febrero de 2020)<a name="v2.0.20"></a>
* Se corrigieron varios errores que provocan bloqueos.

## <a name="version-2018-december-17-2019"></a>Versión 2.0.18 (17 de diciembre de 2019)<a name="v2.0.18"></a>
* Compatibilidad agregada para [HolographicViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration)
* Se corrigieron varios errores que provocan bloqueos.
* Se corrigió un error en el que se necesitaba una devolución de llamada HolographicSpace. CameraAdded para que un HolographicCamera se aceptara y se mostrara como una cámara agregada en el HolographicFrame.

## <a name="version-2016-november-11-2019"></a>Versión 2.0.16 (11 de noviembre de 2019)<a name="2.0.16"></a>
* Se corrigió el interbloqueo en el seguimiento del código QR.
* Excepción de unhandeled corregida debido a una espera de bloqueo en el subproceso principal.

## <a name="version-2014-october-26-2019"></a>Versión 2.0.14 (26 de octubre de 2019)<a name="v2.0.14"></a>
* Compatibilidad con las nuevas API de PerceptionDevice (actualización 2019 de noviembre de Windows 10).
* Se corrigió un problema que impide que SpatialGestureRecognizer Active los eventos de gestos.
* Problema de subprocesos corregido al usar SpatialSurfaceObserver. SetBoundingVolume.

## <a name="version-2012-october-18-2019"></a>Versión 2.0.12 (18 de octubre de 2019)<a name="v2.0.12"></a>
* Se corrigió el bloqueo en SpatialGestureRecognizer al usar NavigationRail (X/Y/Z).

## <a name="version-2010-october-10-2019"></a>Versión 2.0.10 (10 de octubre de 2019)<a name="v2.0.10"></a>
* Se corrigió un bloqueo al usar el botón desencadenador de controladores de VR. Holographic Remoting no es totalmente compatible con los controladores, solo el botón desencadenador y el botón Windows funcionan si se emparejan con HoloLens 2.

## <a name="version-209-september-19-2019"></a>Versión 2.0.9 (19 de septiembre de 2019)<a name="v2.0.9"></a>
* Compatibilidad agregada para [SpatialAnchorExporter](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter)
* Nueva interfaz agregada ```IPlayerContext2``` (implementada por ```PlayerContext``` ) que proporciona los siguientes miembros:
  - Propiedad [BlitRemoteFrameTimeout](holographic-remoting-create-player.md#BlitRemoteFrameTimeout) .
* ```Failed_RemoteFrameTooOld```Valor agregado a```BlitResult```
* Mejoras en la estabilidad y confiabilidad

## <a name="version-208-august-20-2019"></a>Versión 2.0.8 (20 de agosto de 2019)<a name="v2.0.8"></a>

* Se corrigió un bloqueo al llamar a [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer) con un parámetro [IDXGISurface2](https://docs.microsoft.com/windows/win32/api/dxgi1_2/nn-dxgi1_2-idxgisurface2) como.
* Mejoras en la estabilidad y confiabilidad

## <a name="version-207-july-26-2019"></a>Versión 2.0.7 (26 de julio de 2019)<a name="v2.0.7"></a>

* Primera versión pública de Holographic Remoting para HoloLens 2.

## <a name="see-also"></a>Consulte también
* [Escritura de una aplicación de reproductor de control remoto de holografías personalizada](holographic-remoting-create-player.md)
* [Escritura de una aplicación de host de Holographic Remoting](holographic-remoting-create-host.md)
* [Solución de problemas y limitaciones de la comunicación remota holográfica](holographic-remoting-troubleshooting.md)
* [Términos de licencia del software de control remoto de holografías](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
