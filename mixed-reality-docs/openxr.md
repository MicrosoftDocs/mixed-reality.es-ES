---
title: OpenXR
description: Pruebe la API OpenXR 0,90 provisional con la versión preliminar para desarrolladores de OpenXR de realidad mixta.
author: thetuvix
ms.author: alexturn
ms.date: 3/18/2019
ms.topic: article
keywords: Realidad mixta OpenXR Developer Preview
ms.openlocfilehash: 0d8debf5c12cb88aaba402145c6a597f761491ee
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605468"
---
# <a name="openxr"></a>OpenXR

OpenXR es un estándar abierto y libre de regalías de [Khronos](https://www.khronos.org/) que proporciona acceso nativo a una amplia gama de dispositivos de muchos proveedores que se distribuyen entre el [espectro de realidad mixta](mixed-reality.md).

Con OpenXR, puede compilar aplicaciones que tienen como destino dispositivos holográficas (por ejemplo, 2 de HoloLens) que incluyen contenido digital en el mundo real como si fuese realmente ahí, así como dispositivos envolventes (por ejemplo, auriculares de realidad mixta de Windows para los equipos de escritorio) que ocultan la mundo físico y reemplazarlo con una experiencia digital.  OpenXR le permite escribir código una vez, a continuación, es portátil entre una amplia gama de plataformas de hardware.

El estándar OpenXR está actualmente en una fase provisional, una especificación OpenXR 0,90 inicial publicado para comentarios.  Para obtener más información sobre OpenXR, incluido el acceso a la [provisional especificación 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html) y [encabezados](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr), consulte el [Khronos OpenXR página](https://www.khronos.org/openxr/).

## <a name="setting-up-the-mixed-reality-openxr-developer-preview"></a>Configuración de la versión preliminar para desarrolladores de OpenXR de realidad mixta

Puede probar la API OpenXR 0,90 provisional hoy mismo con Mixed Reality OpenXR Developer Preview.  Este tiempo de ejecución anticipada permite que las aplicaciones destinadas a la API OpenXR 0,90 inmersivos Windows Mixed Reality destino en el escritorio.  Si no tiene acceso a los auriculares, puede usar el simulador de realidad mixta de Windows en su lugar.

Para empezar a trabajar con la versión preliminar para desarrolladores de OpenXR de realidad mixta:

1. Asegúrese de que está ejecutando al menos Windows Update 10 de octubre de 2018.  Si se encuentra en una versión anterior de Windows 10, puede actualizar a la de octubre de 2018 actualizar mediante el [Asistente de actualización de Windows 10](https://www.microsoft.com/en-us/software-download/windows10).  Si se siente aventurero, puede instalar un [compilación de Windows 10 Insider Preview](https://insider.windows.com).
1. Configurar un auricular Windows Mixed Reality o siga las instrucciones para [habilitar el simulador de Windows Mixed Reality](using-the-windows-mixed-reality-simulator.md).
1. Instalar el [vista previa de desarrollador de realidad mixta OpenXR aplicación](https://www.microsoft.com/store/productId/9n5cvvl23qbt).  Esta aplicación le permite configurar con la versión preliminar en tiempo de ejecución OpenXR en Windows 10 de octubre de 2018 Update o posterior.  Después de instalar esta aplicación, el Store Windows mantendrá el tiempo de ejecución actualizado.
1. Ejecute la aplicación Mixed Reality OpenXR Developer Preview desde el menú Inicio y siga las instrucciones para activar el tiempo de ejecución.  Pronto, esta aplicación le permitirá explorar otra información de depuración de OpenXR.

![Vista previa de desarrollador de realidad mixta OpenXR aplicación](images/mixed-reality-openxr-developer-preview.png)

## <a name="support-for-windows-10-october-2018-update"></a>Soporte técnico para Windows 10 de octubre de 2018 Update

Para empezar a utilizar Mixed Reality OpenXR Developer Preview en Windows 10 de octubre de 2018 actualización (la versión actual de Windows), deberá seguir unos pocos pasos más:

1. Siga los pasos anteriores para instalar la versión preliminar para desarrolladores de OpenXR de realidad mixta.
1. Para establecer el Mixed Reality OpenXR Developer Preview como active OpenXR en tiempo de ejecución de su sistema, instale el [mixto realidad OpenXR Developer Preview compatibilidad Pack](https://aka.ms/openxr-compat).

## <a name="building-a-test-openxr-app"></a>Creación de una prueba de la aplicación OpenXR

El [hello_xr](https://github.com/KhronosGroup/OpenXR-SDK/tree/master/src/tests/hello_xr) OpenXR prueba de la aplicación muestra el uso de varias partes de la API.  Puede seguir estas [instrucciones de compilación](https://github.com/KhronosGroup/OpenXR-SDK/blob/master/BUILDING.md), que compilará la aplicación de prueba y los encabezados de OpenXR ellos mismos.

## <a name="feedback"></a>Comentarios

Para enviar comentarios sobre el [especificación OpenXR Provisional 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html), visite la [Khronos OpenXR foros](https://community.khronos.org/c/openxr), [canal de Slack #openxr](https://khr.io/slack) y [especificación Rastreador de problemas](https://github.com/KhronosGroup/OpenXR-Docs/issues).

## <a name="troubleshooting"></a>Solución de problemas

Estas son algunas sugerencias de solución de problemas para la versión preliminar para desarrolladores de OpenXR de realidad mixta.  Si está alcanzando otros problemas, visite la [Khronos OpenXR foros](https://community.khronos.org/c/openxr) o [canal de Slack #openxr](https://khr.io/slack).

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>Aplicación OpenXR no inicia Windows Mixed Reality

Si la aplicación OpenXR no inicia Windows Mixed Reality al ejecutarlo, Mixed Reality OpenXR Developer Preview no puede establecerse como el tiempo de ejecución activo.  Asegúrese de ejecutar la aplicación Mixed Reality OpenXR Developer Preview y siga las instrucciones para activar el tiempo de ejecución.

### <a name="mixed-reality-openxr-developer-preview-app-cannot-be-installed"></a>No se puede instalar la aplicación de mixed Reality OpenXR Developer Preview 

Asegúrese de que está ejecutando al menos Windows Update 10 de octubre de 2018.  Si se encuentra en una versión anterior de Windows 10, puede actualizar a la de octubre de 2018 actualizar mediante el [Asistente de actualización de Windows 10](https://www.microsoft.com/en-us/software-download/windows10).

Si la instalación de botón en la aplicación Mixed Reality OpenXR Developer Preview no hace nada en Windows 10 de octubre de 2018 se actualiza, el sistema es posible que hayan almacenado en caché los requisitos del sistema obsoletos de la aplicación.  Puede ejecutar el comando `wsreset.exe` desde un símbolo del sistema para borrar la caché.

## <a name="see-also"></a>Vea también

* [Obtener más información sobre OpenXR](https://www.khronos.org/openxr/)
* [Especificación OpenXR Provisional 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/html/xrspec.html)
* [Referencia de API provisionales OpenXR 0,90](https://www.khronos.org/registry/OpenXR/specs/0.90/man/html/)
* [Encabezados de OpenXR Provisional 0,90](https://github.com/KhronosGroup/OpenXR-Docs/tree/master/include/openxr)
