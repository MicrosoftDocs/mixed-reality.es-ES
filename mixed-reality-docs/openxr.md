---
title: OpenXR
description: Pruebe la API OpenXR 0,90 provisional con la versión preliminar para desarrolladores de OpenXR de realidad mixta.
author: thetuvix
ms.author: alexturn
ms.date: 3/18/2019
ms.topic: article
keywords: Realidad mixta OpenXR Developer Preview
ms.openlocfilehash: 723b0b85785d4b6dd735430aa76a24b9ce05b5c7
ms.sourcegitcommit: 8d6e5723283c03f984f1fafef81afa5aab5d04bc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2019
ms.locfileid: "66039180"
---
# <a name="openxr"></a>OpenXR

OpenXR es un estándar abierto y libre de regalías de [Khronos](https://www.khronos.org/) que proporciona acceso nativo a una amplia gama de dispositivos de muchos proveedores que se distribuyen entre el [espectro de realidad mixta](mixed-reality.md).

Con OpenXR, puede compilar aplicaciones que tienen como destino dispositivos holográficas (por ejemplo, 2 de HoloLens) que incluyen contenido digital en el mundo real como si fuese realmente ahí, así como dispositivos envolventes (por ejemplo, auriculares de realidad mixta de Windows para los equipos de escritorio) que ocultan la mundo físico y reemplazarlo con una experiencia digital.  OpenXR le permite escribir código una vez, a continuación, es portátil entre una amplia gama de plataformas de hardware.

El estándar OpenXR está actualmente en una fase provisional, una especificación OpenXR 0,90 inicial publicado para comentarios.  Para obtener más información sobre OpenXR, incluido el acceso a la [provisional especificación 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html) y [encabezados](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr), consulte el [Khronos OpenXR página](https://www.khronos.org/openxr/). 

Puede probar la API OpenXR 0,90 provisional en un 2 HoloLens o un PC de escritorio mediante Mixed Reality OpenXR Developer Preview.  Este tiempo de ejecución anticipada permite que las aplicaciones destinadas a la API OpenXR 0,90 HoloLens 2 o inmersivos Windows Mixed Reality en el escritorio de destino.

Si no tiene acceso a los auriculares, puede usar el emulador de HoloLens 2 o el simulador de realidad mixta de Windows en su lugar.

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-hololens-2"></a>Configuración de Mixed Reality OpenXR Developer Preview para HoloLens 2

Para empezar a trabajar con la realidad mixta OpenXR Developer Preview en HoloLens 2:

1. Configurar un 2 HoloLens o siga las instrucciones para [instalar el emulador de HoloLens 2](using-the-hololens-emulator.md).
1. Inicie la aplicación Store en el dispositivo o emulador y asegúrese de que se actualizan todas las aplicaciones.  Esto instalará la realidad mixta OpenXR Developer Preview para su uso con aplicaciones en ese dispositivo.  Si usa el emulador, conviene que puede consultar el [emulador entrada instrucciones](using-the-hololens-emulator.md#basic-emulator-input) le ayudarán a usar la aplicación Store en el emulador.

## <a name="setting-up-the-mixed-reality-openxr-developer-preview-for-immersive-desktop-headsets"></a>Configuración de la realidad mixta OpenXR Developer Preview para escritorio inmersivos

Para empezar a trabajar con la realidad mixta OpenXR Developer Preview en un equipo de escritorio:

1. Asegúrese de que está ejecutando Windows 10 de octubre de 2018 Update (1809) o Windows 10 puede 2019 actualizar (1903).  Si se encuentra en una versión anterior de Windows 10, puede actualizar a la de mayo de 2019 actualizar mediante el [Asistente de actualización de Windows 10](https://www.microsoft.com/en-us/software-download/windows10).
1. Configurar un auricular Windows Mixed Reality o siga las instrucciones para [habilitar el simulador de Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md).
1. Instalar el [vista previa de desarrollador de realidad mixta OpenXR aplicación](https://www.microsoft.com/store/productId/9n5cvvl23qbt).  Esta aplicación le permite configurar con la versión preliminar en tiempo de ejecución OpenXR en Windows 10 de octubre de 2018 Update (1809) o una versión posterior.  Después de instalar esta aplicación, el Store Windows mantendrá el tiempo de ejecución actualizado.
1. Ejecute la aplicación Mixed Reality OpenXR Developer Preview desde el menú Inicio y siga las instrucciones para activar el tiempo de ejecución.  Pronto, esta aplicación le permitirá explorar otra información de depuración de OpenXR.

![Vista previa de desarrollador de realidad mixta OpenXR aplicación](images/mixed-reality-openxr-developer-preview.png)

### <a name="support-for-windows-10-october-2018-update"></a>Soporte técnico para Windows 10 de octubre de 2018 Update

Si está ejecutando Windows 10 de mayo de 2019 actualizar (1903) y seguido los pasos anteriores, debería estar listo para usar Mixed Reality OpenXR Developer Preview.

Si no está listo para [actualizar su PC de escritorio a la de mayo de 2019 actualización](https://www.microsoft.com/en-us/software-download/windows10), puede empezar a trabajar en Windows 10 de octubre de 2018. actualice (1809) siguiendo un paso más:

1. Siga los pasos anteriores para instalar la versión preliminar para desarrolladores de OpenXR de realidad mixta.
1. Para establecer el Mixed Reality OpenXR Developer Preview como active OpenXR en tiempo de ejecución de su sistema, instale el [mixto realidad OpenXR Developer Preview compatibilidad Pack](https://aka.ms/openxr-compat).

## <a name="building-a-sample-openxr-app"></a>Creación de una aplicación de ejemplo OpenXR

El [BasicXrApp](https://github.com/Microsoft/OpenXR-SDK-VisualStudio/tree/master/samples/BasicXrApp) proyecto muestra un ejemplo sencillo de OpenXR con dos archivos de proyecto de Visual Studio, uno para tanto una Win32 aplicación de escritorio y otro para una aplicación de UWP HoloLens 2.  Dado que la solución contiene un proyecto de UWP de HoloLens, necesitará la [carga de trabajo de desarrollo de plataforma Universal de Windows](install-the-tools.md#installation-checklist) instalado en Visual Studio para abrirlo por completo.

Tenga en cuenta que, aunque los archivos de proyecto de Win32 y UWP son independientes debido a diferencias en el empaquetado y la implementación, el código de aplicación dentro de cada proyecto es 100% el mismo.

## <a name="feedback"></a>Comentarios

Para enviar comentarios sobre el [especificación OpenXR Provisional 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html), visite la [Khronos OpenXR foros](https://community.khronos.org/c/openxr), [canal de Slack #openxr](https://khr.io/slack) y [especificación Rastreador de problemas](https://github.com/KhronosGroup/OpenXR-Docs/issues).

## <a name="troubleshooting"></a>Solución de problemas

Estas son algunas sugerencias de solución de problemas para la versión preliminar para desarrolladores de OpenXR de realidad mixta.  Si está alcanzando otros problemas, visite la [Khronos OpenXR foros](https://community.khronos.org/c/openxr) o [canal de Slack #openxr](https://khr.io/slack).

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>Aplicación OpenXR no inicia Windows Mixed Reality

Si la aplicación OpenXR no inicia Windows Mixed Reality al ejecutarlo, Mixed Reality OpenXR Developer Preview no puede establecerse como el tiempo de ejecución activo.  Asegúrese de ejecutar la aplicación Mixed Reality OpenXR Developer Preview y siga las instrucciones para activar el tiempo de ejecución.

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a>No se puede instalar la aplicación de mixed Reality OpenXR Developer Preview 

Asegúrese de que está ejecutando al menos Windows 10 de octubre de 2018 actualizar (1809).  Si se encuentra en una versión anterior de Windows 10, puede actualizar a la de mayo de 2019 actualizar (1903) mediante el [Asistente de actualización de Windows 10](https://www.microsoft.com/en-us/software-download/windows10).

Si la instalación de botón en la aplicación Mixed Reality OpenXR Developer Preview no hace nada en Windows 10 de octubre de 2018 se actualiza, el sistema es posible que hayan almacenado en caché los requisitos del sistema obsoletos de la aplicación.  Puede ejecutar el comando `wsreset.exe` desde un símbolo del sistema para borrar la caché.

## <a name="see-also"></a>Vea también

* [Obtener más información sobre OpenXR](https://www.khronos.org/openxr/)
* [Especificación OpenXR Provisional 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [Referencia de API provisionales OpenXR 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [Encabezados de OpenXR Provisional 0,90](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
* [Guía de referencia rápida de OpenXR Provisional 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/refguide/OpenXR-0.90-web.pdf)
