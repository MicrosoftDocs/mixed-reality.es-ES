---
title: OpenXR
description: Cree un motor mediante el estándar portable OpenXR API e impleméntelo en Windows Mixed Reality y en auriculares de HoloLens 2.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, Native, aplicación nativa, motor personalizado, middleware
ms.openlocfilehash: 04b2404889dc74f191543466beb7ae1e516d0d42
ms.sourcegitcommit: 46bd1a56d272a5880f410751fa8429d65d816431
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2020
ms.locfileid: "80549378"
---
# <a name="openxr"></a>OpenXR

OpenXR es un estándar de API abierto sin derechos de autor de <a href="https://www.khronos.org/" target="_blank">Khronos</a> que proporciona a los motores acceso nativo a una amplia gama de dispositivos de muchos proveedores que abarcan todo el espectro de la [realidad mixta](mixed-reality.md).

Puede desarrollar con OpenXR en un casco con HoloLens 2 o Windows Mixed Reality en el escritorio.  Si no tiene acceso a un casco, puede usar el emulador de HoloLens 2 o el simulador de realidad mixta de Windows en su lugar.

## <a name="why-openxr"></a>¿Por qué OpenXR?

Con OpenXR, puede compilar motores que tienen como destino dispositivos holográficas (como HoloLens 2) que colocan contenido digital en el mundo real como si estuvieran realmente allí, así como dispositivos envolventes (como los auriculares de la realidad mixta de Windows para equipos de escritorio) que ocultan el y reemplácelo por una experiencia digital.  OpenXR le permite escribir código una vez que es portable a una amplia gama de plataformas de hardware.

La API de OpenXR usa un cargador que conecta la aplicación directamente a la compatibilidad con la plataforma nativa del casco.  Esto ofrece a los usuarios finales un rendimiento máximo y una latencia mínima, independientemente de si usan un casco de realidad mixta de Windows o cualquier otro casco.

## <a name="what-is-openxr"></a>¿Qué es OpenXR?

La API de OpenXR proporciona la predicción de postura básica, la temporización de fotogramas y la funcionalidad de entrada espacial que necesitará para crear un motor que pueda tener como destino dispositivos holográficas como HoloLens 2 y dispositivos envolventes, como los auriculares de realidad mixta de Windows.

Para obtener información sobre la API de OpenXR, consulte la <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">especificación</a>de la <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">api</a> de OpenXR 1,0, la referencia de API y la <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Guía de referencia rápida</a>.  Para obtener más información, consulte la <a href="https://www.khronos.org/openxr/" target="_blank">Página de OpenXR de Khronos</a>.

Para tener como destino el conjunto completo de características de HoloLens 2, también usará extensiones de OpenXR específicas entre proveedores y proveedores que habilitan características adicionales más allá del OpenXR 1,0 núcleo, como el seguimiento de mano articulado, el seguimiento ocular, la asignación espacial y los delimitadores espaciales.  Consulte la [sección](#roadmap) de la guía a continuación para obtener más información sobre las extensiones que entrarán más adelante este año.

Tenga en cuenta que OpenXR no es en sí mismo un motor de realidad mixta.  En su lugar, OpenXR habilita motores como Unity y nonreal para escribir código portable una vez que pueda acceder a las características de la plataforma nativa del dispositivo Holographic o inmersivo del usuario, independientemente del proveedor que haya compilado esa plataforma.

## <a name="roadmap"></a>Guía básica

La especificación OpenXR define un mecanismo de extensión que permite a los implementadores de tiempo de ejecución exponer funcionalidad adicional más allá de las [características principales](#what-is-openxr) definidas en la <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">especificación 1,0 base OpenXR</a>.

Hay tres tipos de extensiones de OpenXR:
* **Extensiones de proveedor (por ejemplo, `MSFT`):** Habilita la innovación por proveedor en características de hardware o software.  Cualquier proveedor en tiempo de ejecución puede introducir y enviar una extensión de proveedor en cualquier momento.
  * **Extensiones de proveedor experimentales (por ejemplo, `MSFT_preview`):** Se está realizando una vista previa de las extensiones de proveedor experimental para recopilar comentarios.  `MSFT_preview` extensiones solo son para dispositivos de desarrollador y se quitarán cuando se distribuya la extensión real.  Para experimentar con ellos, puede [habilitar las extensiones de vista previa en el dispositivo del desarrollador](openxr-getting-started.md#using-preview-extensions).
* **Extensiones de `EXT` entre proveedores:** Extensiones entre proveedores que varias empresas definen e implementan.  Los grupos de compañías interesadas pueden introducir extensiones EXT en cualquier momento.
* **Extensiones de `KHR` oficiales:** Extensiones oficiales de Khronos ratificadas como parte de una versión de especificación básica.  Las extensiones KHR están contempladas por la misma licencia que la propia especificación principal.

En julio de 2020, el tiempo de ejecución de OpenXR mixed reality de Windows admitirá un conjunto de extensiones de `MSFT` y `EXT` que aportan todo el conjunto de características de HoloLens 2 a las aplicaciones de OpenXR:

| Área de características | Disponibilidad de la extensión |
|--------------|------------------------|
| Sistemas + sesiones | **Especificaciones básicas de OpenXR 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#instance" target="_blank">XrInstance</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#system" target="_blank">XrSystemId</a></code>, <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#session" target="_blank">XrSession</a></code> |
| [Espacios de referencia (ver, local, fase)](coordinate-systems.md) | **Especificaciones básicas de OpenXR 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#spaces" target="_blank">XrSpace</a></code> |
| Configuraciones de vista (mono, estéreo) | **Especificaciones básicas de OpenXR 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#view_configurations" target="_blank">XrView...</a></code> |
| Tiempo de [intercambio](rendering.md) + [fotogramas](understanding-performance-for-mixed-reality.md) | **Especificaciones básicas de OpenXR 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#rendering" target="_blank">XrSwapchain...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-synchronization" target="_blank">xrWaitFrame</a></code> |
| Capas de composición<br />(proyección, cuádruple) | **Especificaciones básicas de OpenXR 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#compositing" target="_blank">XrCompositionLayer...</a></code> + <code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#frame-submission" target="_blank">xrEndFrame</a></code> |
| [Entrada y hápticos](interaction-fundamentals.md) | **Especificaciones básicas de OpenXR 1,0:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#input" target="_blank">XrAction...</a></code> |
| Integración de Direct3D 11 | **Versión oficial de `KHR` publicada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D11_enable" target="_blank">XR_KHR_D3D11_enable</a></code><br /> |
| Integración de Direct3D 12 | **Extensión de `KHR` oficial definida:** *(aún no se admite)*<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_KHR_D3D12_enable" target="_blank">XR_KHR_D3D12_enable</a></code><br /><p>**Compatibilidad con vista previa**: 2020 de abril *(planeada)*</p><p>**Compatibilidad completa**: mayo 2020 *(planeada)*</p> |
| [Espacio de referencia sin enlazar<br />(experiencias de escala mundial)](coordinate-systems.md#building-a-world-scale-experience) | **`MSFT` extensión publicada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_unbounded_reference_space" target="_blank">XR_MSFT_unbounded_reference_space</a></code> |
| [Delimitadores espaciales](spatial-anchors.md) | **`MSFT` extensión publicada:**<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_MSFT_spatial_anchor">XR_MSFT_spatial_anchor</a></code> |
| [<br />de interacción de mano (replanteamiento/objetivo, toque de aire, agarre)](hands-and-tools.md) | **`MSFT_preview` extensión disponible:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_hand_interaction_preview">XR_MSFT_hand_interaction_preview</a></code><p>**`MSFT` versión**: abril 2020 *(planeada)*</p> |
| [Articulation de mano + malla de mano](hands-and-tools.md) | **`MSFT_preview` extensión disponible:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_hand_tracking_preview">XR_MSFT_hand_tracking_preview</a></code><br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_hand_tracking_mesh_preview">XR_MSFT_hand_tracking_mesh_preview</a></code><p>**versión de`MSFT`** : 2020 de mayo *(planeada)*</p> |
| Interoperabilidad con otros SDK de HoloLens (por ejemplo, [QR](qr-code-tracking.md)) | **`MSFT_preview` extensión disponible:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_spatial_graph_bridge_preview">XR_MSFT_spatial_graph_bridge_preview</a></code><p>**versión de`MSFT`** : 2020 de mayo *(planeada)*</p> |
| [Mirada con ojo](eye-tracking.md) | <p>**`EXT` extensión definida**: *(aún no se admite)*<br /><code><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#XR_EXT_eye_gaze_interaction" target="_blank">XR_EXT_eye_gaze_interaction</a></code><p>**Compatibilidad con vista previa**: 2020 de abril *(planeada)*</p><p>**Compatibilidad completa**: mayo 2020 *(planeada)*</p> |
| [<br />de captura de realidad mixta (tercera representación de la cámara PV)](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) | **`MSFT_preview` extensión disponible:**<br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_secondary_view_configuration_preview">XR_MSFT_secondary_view_configuration_preview</a></code><br /><code><a href="https://microsoft.github.io/OpenXR-MixedReality/openxr_preview/specs/openxr.html#XR_MSFT_first_person_observer_preview">XR_MSFT_first_person_observer_preview</a></code><br /><p>**`MSFT` versión**: junio 2020 *(planeada)*</p> |
| [Modelos de representación de controlador de movimiento](motion-controllers.md#rendering-the-motion-controller-model) | <p>**`MSFT_preview`** : abril 2020 *(planeada)*</p><p>**versión de`MSFT`** : 2020 de julio *(planeada)*</p> |
| [Comprensión de escenas (planos, mallas)](scene-understanding.md) | <p>**`MSFT_preview`** : 2020 de mayo *(planeada)*</p><p>**versión de`MSFT`** : 2020 de julio *(planeada)*</p> |

Aunque algunas de estas extensiones pueden comenzar como extensiones de `MSFT` específicas del proveedor, Microsoft y otros proveedores de tiempo de ejecución de OpenXR trabajan juntos para diseñar `EXT` de proveedor entre proveedores o `KHR` para muchas de estas áreas de características.  Esto permitirá que el código que escriba para esas características sea portable a los proveedores en tiempo de ejecución, al igual que con la especificación básica.

## <a name="get-started-with-openxr"></a>Introducción a OpenXR

Puede desarrollar con OpenXR en un casco con HoloLens 2 o Windows Mixed Reality en el escritorio.  Si no tiene acceso a un casco, puede usar el emulador de HoloLens 2 o el simulador de realidad mixta de Windows en su lugar.

Para empezar a desarrollar aplicaciones de OpenXR para los auriculares de la realidad de HoloLens 2 o Windows, consulte [Cómo empezar a usar OpenXR Development](openxr-getting-started.md).

## <a name="see-also"></a>Vea también

* <a href="https://www.khronos.org/openxr/" target="_blank">Más información sobre OpenXR</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Especificación de OpenXR 1,0</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">Referencia de la API de OpenXR 1,0</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Guía de referencia rápida de OpenXR 1,0</a>
