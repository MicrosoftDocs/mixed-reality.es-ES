---
title: OpenXR
description: Pruebe la API OpenXR 0,90 provisional con la versión de vista previa de OpenXR para desarrolladores de realidad mixta.
author: thetuvix
ms.author: alexturn
ms.date: 3/18/2019
ms.topic: article
keywords: Mixed reality OpenXR Developer Preview
ms.openlocfilehash: 723b0b85785d4b6dd735430aa76a24b9ce05b5c7
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039180"
---
# <a name="openxr"></a>OpenXR

OpenXR es un estándar abierto sin derechos de autor de [Khronos](https://www.khronos.org/) que proporciona acceso nativo a una amplia gama de dispositivos de muchos proveedores que abarcan todo el [espectro de realidad mixta](mixed-reality.md).

Con OpenXR, puede compilar aplicaciones destinadas a dispositivos holográficas (como HoloLens 2) que colocan contenido digital en el mundo real como si estuvieran realmente allí, así como dispositivos envolventes (como los auriculares de la realidad mixta de Windows para equipos de escritorio) que ocultan la mundo físico y reemplácelo por una experiencia digital.  OpenXR le permite escribir código una vez que es portable a una amplia gama de plataformas de hardware.

El estándar OpenXR se encuentra actualmente en una fase provisional, con una especificación OpenXR 0,90 inicial publicada para los comentarios.  Para obtener más información sobre OpenXR, incluido el acceso a los [encabezados](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)y la [especificación provisional 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html) , consulte la [Página OpenXR de Khronos](https://www.khronos.org/openxr/). 

Puede probar la API OpenXR 0,90 provisional en una HoloLens 2 o un equipo de escritorio mediante la versión preliminar de Mixed Reality OpenXR Developer Preview.  Este tiempo de ejecución temprano permite a las aplicaciones que tienen como destino la API de OpenXR 0,90 destinadas a HoloLens 2 o Windows Mixed Reality en el escritorio.

Si no tiene acceso a un casco, puede usar el emulador de HoloLens 2 o el simulador de realidad mixta de Windows en su lugar.

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-hololens-2"></a>Configuración de Mixed Reality OpenXR Developer Preview para HoloLens 2

Para empezar a trabajar con Mixed Reality OpenXR Developer Preview en HoloLens 2:

1. Configure un HoloLens 2 o siga las instrucciones para [instalar el emulador de hololens 2](using-the-hololens-emulator.md).
1. Inicie la aplicación de la tienda desde el dispositivo o el emulador y asegúrese de que todas las aplicaciones estén actualizadas.  De este modo, se instalará la versión preliminar de Mixed Reality OpenXR Developer para su uso con aplicaciones en ese dispositivo.  Si usa el emulador, querrá consultar las instrucciones de [entrada](using-the-hololens-emulator.md#basic-emulator-input) del emulador para ayudarle a usar la aplicación de la tienda en el emulador.

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-immersive-desktop-headsets"></a>Configuración de Mixed Reality OpenXR Developer Preview para auriculares de escritorio envolventes

Para empezar a usar Mixed Reality OpenXR Developer Preview en un equipo de escritorio:

1. Asegúrese de que está ejecutando la actualización 2018 de octubre de Windows 10 (1809) o la actualización de Windows 10 May 2019 (1903).  Si se encuentra en una versión anterior de Windows 10, puede actualizar a la actualización de mayo de 2019 mediante el [Asistente de actualización de Windows 10](https://www.microsoft.com/en-us/software-download/windows10).
1. Configure un casco de realidad mixta de Windows o siga las instrucciones para [Habilitar el simulador de realidad mixta de Windows](using-the-windows-mixed-reality-simulator.md).
1. Instale la [aplicación Mixed Reality OpenXR Developer Preview](https://www.microsoft.com/store/productId/9n5cvvl23qbt).  Esta aplicación le permite configurar el tiempo de ejecución de la versión preliminar de OpenXR en Windows 10 de octubre de 2018 (1809) o posterior.  Después de instalar esta aplicación, la tienda Windows mantendrá el tiempo de ejecución actualizado.
1. Ejecute la aplicación Mixed Reality OpenXR Developer Preview en el menú Inicio y siga las instrucciones para activar el tiempo de ejecución.  Pronto, esta aplicación le permitirá explorar también otra información de depuración de OpenXR.

![Aplicación de la versión preliminar para desarrolladores de realidad mixta OpenXR](images/mixed-reality-openxr-developer-preview.png)

### <a name="support-for-windows-10-october-2018-update"></a>Compatibilidad con la actualización 2018 de octubre de Windows 10

Si está ejecutando la actualización 2019 de Windows 10 (1903) y ha seguido los pasos anteriores, debería estar listo para usar la versión de Mixed Reality OpenXR Developer Preview.

Si no está listo para [actualizar el equipo de escritorio a la actualización de mayo de 2019](https://www.microsoft.com/en-us/software-download/windows10), puede empezar a trabajar en la actualización de Windows 10 de octubre de 2018 (1809) siguiendo un paso más:

1. Siga los pasos anteriores para instalar la versión preliminar de Mixed Reality OpenXR Developer Preview.
1. Para establecer la versión de vista previa del desarrollador de OpenXR Mixed Reality como el entorno de ejecución de OpenXR de su sistema, instale el paquete de compatibilidad de la [versión Mixed Reality OpenXR Developer Preview](https://aka.ms/openxr-compat).

## <a name="building-a-sample-openxr-app"></a>Compilación de una aplicación de OpenXR de ejemplo

El proyecto [BasicXrApp](https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp) muestra un sencillo ejemplo de OpenXR con dos archivos de proyecto de Visual Studio, uno para una aplicación de escritorio de Win32 y otro para una aplicación de UWP de HoloLens 2.  Dado que la solución contiene un proyecto de UWP de HoloLens, necesitará la [carga de trabajo de desarrollo de plataforma universal de Windows](install-the-tools.md#installation-checklist) instalada en Visual Studio para abrirla por completo.

Tenga en cuenta que aunque los archivos de proyecto de UWP y Win32 son independientes debido a las diferencias de empaquetado e implementación, el código de la aplicación dentro de cada proyecto es 100% del mismo.

## <a name="feedback"></a>Comentarios

Para proporcionar comentarios sobre la [especificación OpenXR Provisional 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html), visite los [foros de Khronos OpenXR](https://community.khronos.org/c/openxr), el [margen de demora #openxr canal](https://khr.io/slack) y el seguimiento de problemas de [Especificaciones](https://github.com/KhronosGroup/OpenXR-Docs/issues).

## <a name="troubleshooting"></a>Solución de problemas

A continuación se ofrecen algunas sugerencias para la solución de problemas de la versión preliminar para desarrolladores de OpenXR Mixed Reality.  Si está llegando a otros problemas, visite los foros de [Khronos OpenXR](https://community.khronos.org/c/openxr) o el [margen de demora #openxr canal](https://khr.io/slack).

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>La aplicación OpenXR no inicia Windows Mixed Reality

Si la aplicación de OpenXR no está iniciando Windows Mixed Reality al ejecutarla, es posible que la versión preliminar de OpenXR para desarrolladores de realidad mixta no esté establecida como tiempo de ejecución activo.  Asegúrese de ejecutar la aplicación Mixed Reality OpenXR Developer Preview y siga las instrucciones para activar el tiempo de ejecución.

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a>No se puede instalar la aplicación Mixed Reality OpenXR Developer Preview 

Asegúrese de que está ejecutando al menos la actualización 2018 de octubre de Windows 10 (1809).  Si se encuentra en una versión anterior de Windows 10, puede actualizar a la actualización de mayo de 2019 (1903) mediante el [Asistente de actualización de Windows 10](https://www.microsoft.com/en-us/software-download/windows10).

Si el botón instalar de la aplicación Mixed Reality OpenXR Developer Preview no hace nada en la actualización 2018 de octubre de Windows 10, es posible que el sistema tenga requisitos de sistema obsoletos en la aplicación.  Puede ejecutar el comando `wsreset.exe` desde un símbolo del sistema para borrar la memoria caché.

## <a name="see-also"></a>Vea también

* [Más información sobre OpenXR](https://www.khronos.org/openxr/)
* [OpenXR especificación 0,90 provisional](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [Referencia de la API OpenXR provisional 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [OpenXR encabezados provisionales 0,90](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
* [Guía de referencia rápida 0,90 provisional de OpenXR](https://www.khronos.org/registry/OpenXR/specs/0.90/refguide/OpenXR-0.90-web.pdf)
