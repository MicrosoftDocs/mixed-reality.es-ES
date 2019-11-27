---
title: OpenXR
description: Cree un motor mediante el estándar portable OpenXR API e impleméntelo en Windows Mixed Reality y en auriculares de HoloLens 2.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, Mixed Reality OpenXR Developer Portal, DirectX, Native, aplicación nativa, motor personalizado, middleware
ms.openlocfilehash: aa91918e20b4276b7453bae1a05ad18df9d8ab0e
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491137"
---
# <a name="openxr"></a>OpenXR

OpenXR es un estándar de API abierto sin derechos de autor de <a href="https://www.khronos.org/" target="_blank">Khronos</a> que proporciona a los motores acceso nativo a una amplia gama de dispositivos de muchos proveedores que abarcan todo el espectro de la [realidad mixta](mixed-reality.md).

Puede desarrollar con OpenXR en un casco con HoloLens 2 o Windows Mixed Reality en el escritorio.  Si no tiene acceso a un casco, puede usar el emulador de HoloLens 2 o el simulador de realidad mixta de Windows en su lugar.

## <a name="why-openxr"></a>¿Por qué OpenXR?

Con OpenXR, puede compilar motores que tienen como destino dispositivos holográficas (como HoloLens 2) que colocan contenido digital en el mundo real como si estuvieran realmente allí, así como dispositivos envolventes (como los auriculares de la realidad mixta de Windows para equipos de escritorio) que ocultan el y reemplácelo por una experiencia digital.  OpenXR le permite escribir código una vez que es portable a una amplia gama de plataformas de hardware.

La API de OpenXR usa un cargador que conecta la aplicación directamente a la compatibilidad con la plataforma nativa del casco.  Esto ofrece a los usuarios finales un rendimiento máximo y una latencia mínima, independientemente de si usan un casco de realidad mixta de Windows o cualquier otro casco.

## <a name="what-is-openxr"></a>¿Qué es OpenXR?

La API Core OpenXR 1,0 proporciona la funcionalidad básica que necesitará para compilar un motor que puede tener como destino dispositivos holográficas como HoloLens 2 y dispositivos envolventes, como los auriculares Windows Mixed Reality:
* Sistemas + sesiones
* Espacios de referencia (ver, local, fase)
* Configuraciones de vista (mono, estéreo)
* Intercambio + intervalos de fotogramas
* Capas de composición
* Entrada y hápticos
* API de gráficos + integración de la plataforma

Para obtener información sobre la API de OpenXR, consulte la <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">especificación</a>de la <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">api</a> de OpenXR 1,0, la referencia de API y la <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Guía de referencia rápida</a>.  Para obtener más información, consulte la <a href="https://www.khronos.org/openxr/" target="_blank">Página de OpenXR de Khronos</a>.

Para tener como destino el conjunto completo de características de HoloLens 2, también usará extensiones de OpenXR específicas entre proveedores y proveedores que habilitan características adicionales más allá del OpenXR 1,0 núcleo, como el seguimiento de mano articulado, el seguimiento ocular, la asignación espacial y los delimitadores espaciales.  Consulte la sección de la [Guía básica](openxr.md#roadmap) más adelante para obtener más información sobre las extensiones que entrarán más tarde este año.

Tenga en cuenta que OpenXR no es en sí mismo un motor de realidad mixta.  En su lugar, OpenXR habilita motores como Unity y nonreal para escribir código portable una vez que pueda acceder a las características de la plataforma nativa del dispositivo Holographic o inmersivo del usuario, independientemente del proveedor que haya compilado esa plataforma.

## <a name="getting-started-with-openxr-for-hololens-2"></a>Introducción a OpenXR para HoloLens 2

Para empezar a desarrollar aplicaciones de OpenXR para HoloLens 2:

1. Configure un HoloLens 2 o siga las instrucciones para [instalar el emulador de hololens 2](using-the-hololens-emulator.md).
1. Inicie la aplicación de la tienda desde el dispositivo o el emulador y asegúrese de que todas las aplicaciones estén actualizadas.  Esto garantizará que el tiempo de ejecución de OpenXR en HoloLens se actualice a OpenXR 1,0.  Si usa el emulador, querrá consultar las instrucciones de [entrada del emulador](using-the-hololens-emulator.md#basic-emulator-input) para ayudarle a usar la aplicación de la tienda en el emulador.

## <a name="getting-started-with-openxr-for-windows-mixed-reality-headsets"></a>Introducción a OpenXR para auriculares con Windows Mixed Reality

Para empezar a desarrollar aplicaciones de OpenXR para auriculares con Windows de realidad mixta:

1. Asegúrese de que está ejecutando la actualización 2019 de mayo de Windows 10 (1903), que es el requisito mínimo para que los usuarios finales de Windows Mixed Reality ejecuten aplicaciones OpenXR.  Si se encuentra en una versión anterior de Windows 10, puede actualizar a la actualización de mayo de 2019 mediante el <a href="https://www.microsoft.com//software-download/windows10" target="_blank">Asistente de actualización de Windows 10</a>.  Si no puede actualizar su equipo, también es posible [desarrollar la aplicación OpenXR con la actualización 2018 de octubre de Windows 10 (1809)](openxr.md#developing-on-windows-10-october-2018-update), aunque puede experimentar un rendimiento inferior u otros problemas.
2. Configure un casco de realidad mixta de Windows o siga las instrucciones para [Habilitar el simulador de realidad mixta de Windows](using-the-windows-mixed-reality-simulator.md).  Después de configurar Windows Mixed Reality, el portal de realidad mixta instalará automáticamente el tiempo de ejecución de Windows Mixed Reality OpenXR.  El Microsoft Store mantendrá el tiempo de ejecución actualizado.
3. Active el tiempo de ejecución de Windows Mixed Reality OpenXR ejecutando el portal de realidad mixta en el menú Inicio y haga clic en... en la parte inferior izquierda y seleccione "configurar OpenXR".<br>
![configuración de OpenXR en el portal de realidad mixta](images/mixed-reality-portal-set-up-openxr.png)

Si alguna vez necesita volver a activar el tiempo de ejecución de OpenXR de Windows Mixed Reality, repita el paso 3.

> [!NOTE]
> El tiempo de ejecución de OpenXR de Windows Mixed Reality pronto se configurará automáticamente para todos los usuarios finales de Windows Mixed Reality.

## <a name="getting-the-mixed-reality-openxr-developer-portal"></a>Obtención del portal para desarrolladores de OpenXR de realidad mixta

Para probar el tiempo de ejecución de OpenXR mixed reality de Windows, puede instalar la <a href="https://www.microsoft.com/store/productId/9n5cvvl23qbt" target="_blank">aplicación del portal para desarrolladores de [Mixed Reality OpenXR</a>.  Esta aplicación proporciona una escena de demostración que ejercita varias características de OpenXR, junto con una página de estado del sistema que proporciona información clave sobre el tiempo de ejecución activo y el casco actual.

![Aplicación del portal para desarrolladores de realidad mixta OpenXR](images/mixed-reality-openxr-developer-portal.png)

## <a name="building-a-sample-openxr-app"></a>Compilación de una aplicación de OpenXR de ejemplo

El proyecto <a href="https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a> muestra un sencillo ejemplo de OpenXR con dos archivos de proyecto de Visual Studio, uno para una aplicación de escritorio de Win32 y otro para una aplicación de UWP de HoloLens 2.  Dado que la solución contiene un proyecto de UWP de HoloLens, necesitará la [carga de trabajo de desarrollo de plataforma universal de Windows](install-the-tools.md#installation-checklist) instalada en Visual Studio para abrirla por completo.

Tenga en cuenta que aunque los archivos de proyecto de UWP y Win32 son independientes debido a las diferencias de empaquetado e implementación, el código de la aplicación dentro de cada proyecto es 100% del mismo.

Después de crear un escritorio de Win32 de OpenXR. EXE, puede usarlo con un casco de VR en cualquier plataforma de escritorio VR que admita OpenXR, ya sea un casco de realidad mixta de Windows o cualquier otro casco.

Después de compilar un paquete de aplicación de UWP para OpenXR, puede [implementarlo](using-visual-studio.md) en un dispositivo hololens 2 o en el emulador de hololens 2.

## <a name="openxr-app-best-practices-for-hololens-2"></a>Prácticas recomendadas de aplicaciones de OpenXR para HoloLens 2

Puede ver un ejemplo de los procedimientos recomendados que se indican a continuación en el archivo [OpenXRProgram. cpp](https://github.com/microsoft/OpenXR-SDK-VisualStudio/blob/master/samples/BasicXrApp/OpenXrProgram.cpp) de BasicXrApp. La función Run () al principio captura un flujo de código de la aplicación OpenXR típico desde la inicialización hasta el bucle de representación y evento.

### <a name="select-a-pixel-format"></a>Seleccionar un formato de píxel

Enumere siempre los formatos de píxel admitidos mediante `xrEnumerateSwapchainFormats`y elija el primer formato de píxeles de color y profundidad desde el tiempo de ejecución que admita la aplicación, ya que es lo que el tiempo de ejecución prefiere. Tenga en cuenta que, en HoloLens 2, `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` y `DXGI_FORMAT_D16_UNORM` suele ser la primera opción para lograr un mejor rendimiento de la representación. Esta preferencia puede ser diferente en los auriculares de VR que se ejecutan en un equipo de escritorio.  
  
**Advertencia de rendimiento:** El uso de un formato distinto del formato de color de intercambio principal dará como resultado un procesamiento posterior en tiempo de ejecución que conlleva una reducción significativa del rendimiento.

### <a name="gamma-correct-rendering"></a>Representación gamma-correcta

Aunque esto se aplica a todos los tiempos de ejecución de OpenXR, se debe tener cuidado para asegurarse de que la canalización de representación sea correcta. Al representar en un intercambio, el formato de vista de destino de representación debe coincidir con el formato intercambio (por ejemplo, DXGI_FORMAT_B8G8R8A8_UNORM_SRGB para el formato intercambio y la vista representación-destino).
La excepción es si la canalización de representación de la aplicación realiza una conversión sRGB manual en el código del sombreador, en cuyo caso la aplicación debe solicitar un formato sRGB intercambio pero usar el formato lineal para la vista de representación-destino (por ejemplo, solicitar DXGI_FORMAT_B8G8R8A8_UNORM_SRGB como el el formato intercambio, pero usa DXGI_FORMAT_B8G8R8A8_UNORM como vista de destino de representación) para evitar que el contenido se corrija con doble gamma.

### <a name="use-a-single-projection-layer"></a>Usar una sola capa de proyección

HoloLens 2 tiene una potencia de GPU limitada para que las aplicaciones presenten contenido y un compositor de hardware optimizado para una sola capa de proyección.
El uso de una sola capa de proyección puede ayudar a la velocidad de fotogramas de la aplicación, la estabilidad del holograma y la calidad visual.  
  
**Advertencia de rendimiento:** El envío de cualquier elemento, pero con un solo nivel de protección, dará lugar a un procesamiento posterior en tiempo de ejecución que conlleva una reducción significativa del rendimiento.

### <a name="render-with-texture-array-and-vprt"></a>Representar con la matriz de textura y VPRT

Cree una `xrSwapchain` para el ojo izquierdo y derecho con `arraySize=2` para intercambio de color y otra para profundidad.
Representar el ojo izquierdo en el segmento 0 y el ojo derecho en el segmento 1.
Use un sombreador con VPRT y llamadas de dibujo con instancias para la representación de Stereoscopic a fin de minimizar la carga de la GPU.
Esto también permite la optimización del tiempo de ejecución para lograr el mejor rendimiento en HoloLens 2.
Las alternativas al uso de una matriz de textura, como la representación de doble ancho o una intercambio independiente por ojo, darán lugar a un procesamiento posterior en tiempo de ejecución que conlleva una penalización significativa del rendimiento.

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a>Representar con los parámetros de representación recomendados y los intervalos de fotogramas

Siempre se representa con el ancho/alto de configuración de vista recomendado (`recommendedImageRectWidth` y `recommendedImageRectHeight` de `XrViewConfigurationView`) y use siempre la API de `xrLocateViews` para consultar el pose de vista recomendado, el subproceso y otros parámetros de representación antes de la representación.
Use siempre el `XrFrameEndInfo.predictedDisplayTime` de la llamada `xrWaitFrame` más reciente al consultar las vistas y las vistas.
Esto permite a HoloLens ajustar la representación y optimizar la calidad visual de la persona que posee HoloLens.

### <a name="submit-depth-buffer-for-projection-layers"></a>Enviar búfer de profundidad para capas de proyección

Use siempre `XR_KHR_composition_layer_depth` extensión y envíe el búfer de profundidad junto con la capa de proyección al enviar un fotograma a `xrEndFrame`.
Esto mejora la estabilidad del holograma al habilitar la reproyección de profundidad de hardware en HoloLens 2.

### <a name="choose-a-reasonable-depth-range"></a>Elegir un intervalo de profundidad razonable

Prefiera un intervalo de profundidad más estrecho para definir el ámbito del contenido virtual para ayudar a la estabilidad del holograma en HoloLens.
Por ejemplo, el ejemplo OpenXrProgram. cpp usa de 0,1 a 20 metros.
Use [invertida-Z](https://developer.nvidia.com/content/depth-precision-visualized) para una resolución de profundidad más uniforme.
Tenga en cuenta que, en HoloLens 2, el uso del formato de profundidad de `DXGI_FORMAT_D16_UNORM` preferida ayudará a conseguir una velocidad de fotogramas y un rendimiento mejores, aunque los búferes de profundidad de 16 bits proporcionan una resolución menos profunda que los búferes de profundidad de 24 bits.
Por lo tanto, seguir estas prácticas recomendadas para hacer el mejor uso de la resolución de profundidad es más importante.

### <a name="prepare-for-different-environment-blend-modes"></a>Preparación para diferentes modos de fusión de entornos

Si la aplicación también se ejecutará en auriculares envolventes que bloqueen completamente el mundo, asegúrese de enumerar los modos de Blend de entorno admitidos mediante `xrEnumerateEnvironmentBlendModes` API y prepare el contenido de representación en consecuencia.
Por ejemplo, para un sistema con `XR_ENVIRONMENT_BLEND_MODE_ADDITIVE` como HoloLens, la aplicación debe usar transparente como color sin cifrar, mientras que en el caso de un sistema con `XR_ENVIRONMENT_BLEND_MODE_OPAQUE`, la aplicación debe representar algún color opaco o algún espacio virtual en segundo plano.

### <a name="choose-unbounded-reference-space-as-applications-root-space"></a>Elegir espacio de referencia sin enlazar como espacio de la raíz de la aplicación

Normalmente, las aplicaciones establecen algún espacio de coordenadas del mundo raíz para conectar las vistas, las acciones y los hologramas juntos.
Use `XR_REFERENCE_SPACE_TYPE_UNBOUNDED_MSFT` cuando se admita la extensión para establecer un [sistema de coordenadas de escala mundial](coordinate-systems.md#building-a-world-scale-experience), lo que permite a la aplicación evitar el desfase de hologramas no deseados cuando el usuario se desplaza lejos (por ejemplo, 5 metros de distancia) desde donde se inicia la aplicación.
Use `XR_REFERENCE_SPACE_TYPE_LOCAL` como reserva si no existe la extensión de espacio sin enlazar.

### <a name="associate-hologram-with-spatial-anchor"></a>Asociar holograma con delimitador espacial

Cuando se usa un espacio de referencia sin enlazar, los hologramas colocados directamente en ese espacio de referencia pueden desplazarse [a medida que el usuario dirige a habitaciones lejanas y, a continuación,](coordinate-systems.md#building-a-world-scale-experience)vuelve.
En el caso de los usuarios de hologramas que se colocan en una ubicación discreta del mundo, [cree un delimitador espacial](spatial-anchors.md#best-practices) con la función de extensión `xrCreateSpatialAnchorSpaceMSFT` y coloque el holograma en su origen.
De este modo, el holograma será estable de manera independiente con el tiempo.

### <a name="support-mixed-reality-capture"></a>Compatibilidad con la captura de realidad mixta

Aunque la pantalla principal de HoloLens 2 usa la combinación de entornos aditivos, cuando el usuario inicia una [captura de realidad mixta](mixed-reality-capture-for-developers.md), el contenido de representación de la aplicación se combinará alfa con el flujo de vídeo del entorno.
Para lograr la mejor calidad visual en vídeos de captura de realidad mixta, es mejor establecer el `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT` en el `layerFlags`de la capa de proyección.  

**Advertencia de rendimiento:** Si se omite la marca de `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT` en la capa de proyección única, se producirá un procesamiento posterior en tiempo de ejecución que conlleva una reducción significativa del rendimiento.

### <a name="avoid-quad-layers"></a>Evite las cuatro capas

En lugar de enviar cuatro capas como capas de composición con `XrCompositionLayerQuad`, represente el contenido cuádruple directamente en la proyección intercambio.

**Advertencia de rendimiento:** Proporcionar capas adicionales más allá de una sola capa de proyección, como las capas de cuatro, dará como resultado un procesamiento posterior en tiempo de ejecución que conlleva una penalización significativa del rendimiento.

## <a name="openxr-app-performance-on-hololens-2"></a>Rendimiento de la aplicación OpenXR en HoloLens 2

En HoloLens 2, hay varias formas de enviar datos de composición a través de `xrEndFrame`, lo que dará lugar a un procesamiento posterior que tendrá una penalización notable en el rendimiento.
Para evitar las penalizaciones de rendimiento, [envíe un solo `XrCompositionProjectionLayer`](#use-a-single-projection-layer) con las siguientes características:
* [Usar una matriz de textura intercambio](#render-with-texture-array-and-vprt)
* [Usar el formato intercambio de color principal](#select-a-pixel-format)
* [Establecer la marca de combinación Texture-Source-Alpha](#support-mixed-reality-capture)
* [Usar las dimensiones de vista recomendadas](#render-with-recommended-rendering-parameters-and-frame-timing)
* No establezca la marca de `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT`
* Establezca la `XrCompositionLayerDepthInfoKHR` `minDepth` en 0.0 f y `maxDepth` en 1,0 f.

Otras consideraciones darán lugar a un mejor rendimiento:
* [Usar el formato de profundidad de 16 bits](#choose-a-reasonable-depth-range)
* [Realizar llamadas a Draw con instancias](#render-with-texture-array-and-vprt)

## <a name="roadmap"></a>Guía básica

La especificación OpenXR define un mecanismo de extensión que permite a los implementadores de tiempo de ejecución exponer funcionalidad adicional más allá de las [características principales](openxr.md#what-is-openxr) definidas en la <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">especificación 1,0 base OpenXR</a>.

Hay tres tipos de extensiones de OpenXR:
* **Extensiones de proveedor (por ejemplo, MSFT):** Habilita la innovación por proveedor en características de hardware o software.  Cualquier proveedor en tiempo de ejecución puede introducir y enviar una extensión de proveedor en cualquier momento.
* **Extensiones EXT:** Extensiones entre proveedores que varias empresas definen e implementan.  Los grupos de compañías interesadas pueden introducir extensiones EXT en cualquier momento.
* **Extensiones de KHR:** Extensiones oficiales de Khronos ratificadas como parte de una versión de especificación básica.  Las extensiones KHR están contempladas por la misma licencia que la propia especificación principal.

Al final del año, el tiempo de ejecución de OpenXR mixed reality de Windows admitirá un conjunto de extensiones de MSFT y EXT que lleven el conjunto completo de características de HoloLens 2 a las aplicaciones de OpenXR:
* [Espacio de referencia sin enlazar (experiencias a escala mundial)](coordinate-systems.md#building-a-world-scale-experience)
* [Anclajes espaciales y almacenamiento](spatial-anchors.md)
* [Articulation de mano + malla de mano](hands-and-tools.md)
* [Mirada con ojo](eye-tracking.md)
* [Configuraciones de vista secundaria (captura de realidad mixta)](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)
* [Descripción de escenas](scene-understanding.md)
* Interoperabilidad con API de Windows SDK

Aunque algunas de estas extensiones pueden comenzar como extensiones de MSFT específicas del proveedor, Microsoft y otros proveedores de tiempo de ejecución de OpenXR trabajan juntos para diseñar extensiones EXT o KHR entre proveedores para muchas de estas áreas de características.  Esto permitirá que el código que escriba para esas características sea portable a los proveedores en tiempo de ejecución, al igual que con la especificación básica.

## <a name="troubleshooting"></a>Solución de problemas

A continuación se muestran algunas sugerencias para la solución de problemas en tiempo de ejecución de Windows Mixed Reality OpenXR.  Si tiene alguna pregunta sobre la especificación de <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1,0</a>, visite los foros de <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR</a> o el <a href="https://khr.io/slack" target="_blank">margen de demora #openxr canal</a>.

### <a name="developing-on-windows-10-october-2018-update"></a>Desarrollo en la actualización 2018 de octubre de Windows 10

Si no puede [actualizar el equipo de desarrollo a la actualización de mayo de 2019](https://www.microsoft.com//software-download/windows10), puede configurar el equipo de Windows 10 octubre 2018 (1809) para el desarrollo siguiendo un paso más:

1. Siga los pasos anteriores para empezar a trabajar con OpenXR en el equipo de escritorio.
1. Para establecer el tiempo de ejecución de Windows Mixed Reality OpenXR como el tiempo de ejecución de OpenXR de su sistema, instale el [paquete de compatibilidad para desarrolladores de Windows Mixed Reality OpenXR](https://aka.ms/openxr-compat).

> [!NOTE]
> Aunque se puede usar la actualización 2018 de octubre de Windows 10 (1809) al desarrollar aplicaciones de OpenXR, la actualización de Windows 10 May 2019 (1903) es el requisito mínimo para que los usuarios finales usen OpenXR con Windows Mixed Reality.  Puede experimentar un menor rendimiento u otros problemas al ejecutar la aplicación de OpenXR en la actualización de octubre de 2018.  Se recomienda encarecidamente que actualice el equipo de desarrollo a la actualización 2019 de Windows 10 (1903).

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>La aplicación OpenXR no inicia Windows Mixed Reality

Si la aplicación de OpenXR no inicia Windows Mixed Reality al ejecutarla, es posible que el tiempo de ejecución de Windows Mixed Reality OpenXR no se establezca como el tiempo de ejecución activo.  Asegúrese de seguir las instrucciones anteriores para empezar a [trabajar con los auriculares de OpenXR para Windows Mixed Reality](#getting-started-with-openxr-for-windows-mixed-reality-headsets) para activar el tiempo de ejecución.

También puede ejecutar el [portal para desarrolladores de Mixed Reality OpenXR](#getting-the-mixed-reality-openxr-developer-portal) para ayudarle a solucionar problemas relacionados con el estado del tiempo de ejecución de Windows Mixed Reality OpenXR en el sistema.

### <a name="mixed-reality-portal-not-showing-set-up-openxr-menu-item"></a>El portal de realidad mixta no muestra el elemento de menú "configurar OpenXR"

Asegúrese de que está ejecutando al menos la actualización 2018 de octubre de Windows 10 (1809).  Si se encuentra en una versión anterior de Windows 10, puede actualizar a la actualización de mayo de 2019 (1903) mediante el [Asistente de actualización de Windows 10](https://www.microsoft.com//software-download/windows10).

Es posible que el elemento de menú "configurar OpenXR" no esté disponible si tiene una versión anterior de la aplicación del portal de realidad mixta.  Busque una actualización de la [aplicación del portal de realidad mixta](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m) para asegurarse de que tiene la versión más reciente.

Tenga en cuenta que el elemento de menú "configurar OpenXR" no se mostrará si el tiempo de ejecución de Windows Mixed Reality OpenXR ya está instalado y activo.  Puede instalar el [portal para desarrolladores de Mixed Reality OpenXR](#getting-the-mixed-reality-openxr-developer-portal) para determinar el estado actual del tiempo de ejecución de OpenXR en el sistema.

## <a name="see-also"></a>Consulte también

* <a href="https://www.khronos.org/openxr/" target="_blank">Más información sobre OpenXR</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Especificación de OpenXR 1,0</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">Referencia de la API de OpenXR 1,0</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Guía de referencia rápida de OpenXR 1,0</a>
