---
title: OpenXR
description: Cree un motor mediante el estándar portable OpenXR API e impleméntelo en Windows Mixed Reality y en auriculares de HoloLens 2.
author: thetuvix
ms.author: alexturn
ms.date: 7/29/2019
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, Mixed Reality OpenXR Developer Portal, DirectX, Native, motor personalizado de aplicación nativa, middleware
ms.openlocfilehash: cf8795e6fed7db9fd0743d0902ce1585d56fa5e0
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438132"
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
* [Asignación espacial](spatial-mapping.md)
* Interoperabilidad con API de Windows SDK

Aunque algunas de estas extensiones pueden comenzar como extensiones de MSFT específicas del proveedor, Microsoft y otros proveedores de tiempo de ejecución de OpenXR trabajan juntos para diseñar extensiones EXT o KHR entre proveedores para muchas de estas áreas de características.  Esto permitirá que el código que escriba para esas características sea portable a los proveedores en tiempo de ejecución, al igual que con la especificación básica.

## <a name="troubleshooting"></a>de solución de problemas

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

## <a name="see-also"></a>Consulta también

* <a href="https://www.khronos.org/openxr/" target="_blank">Más información sobre OpenXR</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">Especificación de OpenXR 1,0</a>
* <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/man/html/openxr.html" target="_blank">Referencia de la API de OpenXR 1,0</a>
* <a href="https://www.khronos.org/files/openxr-10-reference-guide.pdf" target="_blank">Guía de referencia rápida de OpenXR 1,0</a>
