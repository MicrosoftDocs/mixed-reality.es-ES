---
title: OpenXR
description: Cree un motor mediante el estándar portable OpenXR API e impleméntelo en Windows Mixed Reality y en auriculares de HoloLens 2.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, Native, aplicación nativa, motor personalizado, middleware
ms.openlocfilehash: 170ce0b55990158940692db25b925a1e79d7cf39
ms.sourcegitcommit: 3c32f45fd941767d408cccc5a76f1ff1cec763da
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "86879170"
---
# <a name="openxr"></a>OpenXR

<img align="right" src="images/openxr.png" alt="OpenXR logo">

OpenXR es un estándar de API abierto sin derechos de autor de <a href="https://www.khronos.org/" target="_blank">Khronos</a> que proporciona a los motores acceso nativo a una amplia gama de dispositivos de muchos proveedores que abarcan todo el espectro de la [realidad mixta](mixed-reality.md).

Puede desarrollar con OpenXR en un casco con HoloLens 2 o Windows Mixed Reality en el escritorio.  Si no tiene acceso a un casco, puede usar el emulador de HoloLens 2 o el simulador de realidad mixta de Windows en su lugar.

## <a name="why-openxr"></a>¿Por qué OpenXR?

Con OpenXR, puede compilar motores que tienen como destino dispositivos holográficas (como HoloLens 2) que colocan contenido digital en el mundo real como si estuvieran realmente allí, así como dispositivos envolventes (como los auriculares de realidad mixta de Windows para equipos de escritorio) que ocultan el mundo físico y lo reemplazan por una experiencia digital.  OpenXR le permite escribir código una vez que es portable a una amplia gama de plataformas de hardware.

La API de OpenXR usa un cargador que conecta la aplicación directamente a la compatibilidad con la plataforma nativa del casco.  Esto ofrece a los usuarios finales un rendimiento máximo y una latencia mínima, independientemente de si usan un casco de realidad mixta de Windows o cualquier otro casco.

## <a name="what-is-openxr"></a>¿Qué es OpenXR?

La API de OpenXR proporciona la predicción de postura básica, la temporización de fotogramas y la funcionalidad de entrada espacial que necesitará para crear un motor que pueda tener como destino dispositivos holográficas como HoloLens 2 y dispositivos envolventes, como los auriculares de realidad mixta de Windows.

Para obtener información sobre la API de OpenXR, consulte la <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">especificación</a>de la <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">api</a> de OpenXR 1,0, la referencia de API y la <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Guía de referencia rápida</a>.  Para obtener más información, consulte la <a href="https://www.khronos.org/openxr/" target="_blank">Página de OpenXR de Khronos</a>.

Para tener como destino el conjunto completo de características de HoloLens 2, también usará extensiones de OpenXR específicas entre proveedores y proveedores que habilitan características adicionales más allá del OpenXR 1,0 núcleo, como el seguimiento de mano articulado, el seguimiento ocular, la asignación espacial y los delimitadores espaciales.  Consulte la [sección](#roadmap) de la guía a continuación para obtener más información sobre las extensiones que entrarán más adelante este año.

Tenga en cuenta que OpenXR no es en sí mismo un motor de realidad mixta.  En su lugar, OpenXR habilita motores como Unity y nonreal para escribir código portable una vez que pueda acceder a las características de la plataforma nativa del dispositivo Holographic o inmersivo del usuario, independientemente del proveedor que haya compilado esa plataforma.

## <a name="roadmap"></a>Plan de desarrollo

La especificación OpenXR define un mecanismo de extensión que permite a los implementadores de tiempo de ejecución exponer funcionalidad adicional más allá de las [características principales](#what-is-openxr) definidas en la <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">especificación 1,0 base OpenXR</a>.

Hay tres tipos de extensiones de OpenXR:
* **Extensiones de proveedor (por ejemplo, `MSFT` ):** permite la innovación por proveedor en características de hardware o software.  Cualquier proveedor en tiempo de ejecución puede introducir y enviar una extensión de proveedor en cualquier momento.
  * **Extensiones de proveedor experimentales (p. ej. `MSFT_preview` ):** se muestra una vista previa de las extensiones de proveedor experimental para recopilar comentarios.  `MSFT_preview`las extensiones son solo para dispositivos de desarrollador y se quitarán cuando se distribuya la extensión real.  Para experimentar con ellos, puede [habilitar las extensiones de vista previa en el dispositivo del desarrollador](openxr-getting-started.md#using-preview-extensions).
* **Extensiones entre proveedores `EXT` :** extensiones entre proveedores que varias empresas definen e implementan.  Los grupos de compañías interesadas pueden introducir extensiones EXT en cualquier momento.
* ** `KHR` Extensiones oficiales:** extensiones oficiales de Khronos ratificadas como parte de una versión de especificación básica.  Las extensiones KHR están contempladas por la misma licencia que la propia especificación principal.

A partir del 2020 de julio, el tiempo de ejecución de OpenXR mixed reality de Windows admite un conjunto de `MSFT` `EXT` extensiones y que proporciona el conjunto completo de características de HoloLens 2 a las aplicaciones de OpenXR:

| Área de función | Disponibilidad de la extensión |
|--------------|------------------------|
| Sistemas + sesiones | **Especificaciones básicas de OpenXR 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#instance" target="_blank">XrInstance</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#system" target="_blank">XrSystemId</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#session" target="_blank">XrSession</a></code> |
| [Espacios de referencia (ver, local, fase)](coordinate-systems.md) | **Especificaciones básicas de OpenXR 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#spaces" target="_blank">XrSpace</a></code> |
| Configuraciones de vista (mono, estéreo) | **Especificaciones básicas de OpenXR 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#view_configurations" target="_blank">XrView...</a></code> |
| [Intercambio](rendering.md)  +  [temporización de fotogramas](understanding-performance-for-mixed-reality.md) | **Especificaciones básicas de OpenXR 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#rendering" target="_blank">XrSwapchain...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-synchronization" target="_blank">xrWaitFrame</a></code> |
| Capas de composición<br />(proyección, cuádruple) | **Especificaciones básicas de OpenXR 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#compositing" target="_blank">XrCompositionLayer...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-submission" target="_blank">xrEndFrame</a></code> |
| [Entrada y hápticos](interaction-fundamentals.md) | **Especificaciones básicas de OpenXR 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#input" target="_blank">XrAction...</a></code> |
| Integración de Direct3D 11 | **`KHR`Extensión oficial publicada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D11_enable" target="_blank">XR_KHR_D3D11_enable</a></code> |
| Integración de Direct3D 12 | **`KHR`Extensión oficial publicada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D12_enable" target="_blank">XR_KHR_D3D12_enable</a></code> |
| [Espacio de referencia sin enlazar <br /> (experiencias a escala mundial)](coordinate-systems.md#building-a-world-scale-experience) | **`MSFT`extensión publicada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_unbounded_reference_space" target="_blank">XR_MSFT_unbounded_reference_space</a></code> |
| [Delimitadores espaciales](spatial-anchors.md) | **`MSFT`extensión publicada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code> |
| [Interacción con la mano <br /> (replanteamiento/objetivo, toque de aire, agarre)](hands-and-tools.md)<p>*Solo HoloLens 2*</p> | **`MSFT`extensión publicada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_interaction">XR_MSFT_hand_interaction</a></code> |
| [Articulation de mano + malla de mano](hands-and-tools.md)<p>*Solo HoloLens 2*</p> | <p>**`EXT`extensión Publicada en tiempo de ejecución 102:**<code><br /><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_hand_tracking">XR_EXT_hand_tracking</a></code></p>**`MSFT`extensión Publicada en tiempo de ejecución 102:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_hand_tracking_mesh">XR_MSFT_hand_tracking_mesh</a></code> |
| [Mirada con ojo](eye-tracking.md)<p>*Solo HoloLens 2*</p> | **`EXT`extensión publicada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_eye_gaze_interaction" target="_blank">XR_EXT_eye_gaze_interaction</a></code> |
| Interoperabilidad con otros SDK de HoloLens<br />(por ejemplo, [QR](qr-code-tracking.md))<p>*Solo HoloLens 2*</p> | **`MSFT`extensión Publicada en tiempo de ejecución 102:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code> |
| [Captura de realidad mixta <br /> (tercera representación de la cámara PV)](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)<p>*Solo HoloLens 2*</p> | **`MSFT`extensiones publicadas en tiempo de ejecución 102:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_secondary_view_configuration">XR_MSFT_secondary_view_configuration</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_first_person_observer">XR_MSFT_first_person_observer</a></code> |
| Interoperabilidad con la API de CoreWindow de UWP<br />(por ejemplo, para el teclado o el mouse) | **`MSFT_preview`extensión en [tiempo de ejecución de vista previa 102](openxr-getting-started.md#using-preview-extensions):**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_holographic_window_attachment_preview">XR_MSFT_holographic_window_attachment_preview</a></code><p>** `MSFT` extensión en tiempo de ejecución de vista previa**: agosto 2020 *(planeada)*</p>
| [Modelos de representación de controlador de movimiento](motion-controllers.md#rendering-the-motion-controller-model) | **`MSFT_preview`extensión en [tiempo de ejecución de vista previa](openxr-getting-started.md#using-preview-extensions):**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_controller_model_preview">XR_MSFT_controller_model_preview</a></code><p>** `MSFT` extensión en tiempo de ejecución de vista previa**: 2020 de septiembre *(planeada)*</p> |
| [Comprensión de escenas (planos, mallas)](scene-understanding.md)<p>*Solo HoloLens 2*</p> | <p>**En el [tiempo de ejecución de vista previa 102](openxr-getting-started.md#using-preview-extensions):**<br />Usar <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_graph_bridge">XR_MSFT_spatial_graph_bridge</a></code> con el [SDK de comprensión de escenas](scene-understanding-sdk.md)</p><p>** `MSFT_preview` extensión en tiempo de ejecución de vista previa futura** *(planeada)*</p> |
| Otras extensiones entre proveedores | <p>**`KHR`Extensiones oficiales publicadas:**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_composition_layer_depth" target="_blank">XR_KHR_composition_layer_depth</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_visibility_mask" target="_blank">XR_KHR_visibility_mask</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_win32_convert_performance_counter_time" target="_blank">XR_KHR_win32_convert_performance_counter_time</a></code><p>**`EXT`extensiones publicadas:**</p><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_win32_appcontainer_compatible" target="_blank">XR_EXT_win32_appcontainer_compatible</a></code><br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_debug_utils" target="_blank">XR_EXT_debug_utils</a></code> |

Aunque algunas de estas extensiones pueden comenzar como extensiones específicas del proveedor `MSFT` , Microsoft y otros proveedores de tiempo de ejecución de OpenXR trabajan juntos para diseñar `EXT` varios proveedores o `KHR` extensiones para muchas de estas áreas de características.  Esto permitirá que el código que escriba para esas características sea portable a los proveedores en tiempo de ejecución, al igual que con la especificación básica.

## <a name="get-started-with-openxr"></a>Introducción a OpenXR

Puede desarrollar con OpenXR en un casco con HoloLens 2 o Windows Mixed Reality en el escritorio.  Si no tiene acceso a un casco, puede usar el emulador de HoloLens 2 o el simulador de realidad mixta de Windows en su lugar.

Para empezar a desarrollar aplicaciones de OpenXR para los auriculares de la realidad de HoloLens 2 o Windows, consulte [Cómo empezar a usar OpenXR Development](openxr-getting-started.md).

## <a name="see-also"></a>Consulte también

* <a href="https://www.khronos.org/openxr/" target="_blank">Más información sobre OpenXR</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Especificación de OpenXR 1,0</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">Referencia de la API de OpenXR 1,0</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Guía de referencia rápida de OpenXR 1,0</a>
