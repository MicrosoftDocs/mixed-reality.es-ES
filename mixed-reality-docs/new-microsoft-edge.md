---
title: Windows Mixed Reality y el nuevo Microsoft Edge
description: Cómo contribuir a la documentación de Windows Mixed Reality.
author: mattzmsft
ms.author: mazeller
ms.date: 01/07/2020
ms.topic: article
keywords: Edge, nuevo, Web envolvente, Microsoft Edge, explorador, VR
ms.openlocfilehash: cb0f96069ffaa8f7d40b64bae55ab2749f5f02c6
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75727052"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Windows Mixed Reality y el nuevo Microsoft Edge

Como podría haber escuchado, pronto estará [disponible el nuevo Microsoft Edge](https://blogs.windows.com/windowsexperience/2019/11/04/introducing-the-new-microsoft-edge-and-bing/). Con la disponibilidad general destinada al 15 de enero de 2020, queríamos permitir que los clientes de Windows Mixed Reality VR con auriculares sepan qué esperar del nuevo Microsoft Edge e informarle de algunas actualizaciones pendientes que mejorarán la experiencia de exploración Web en Windows Mixed. Realidad.

## <a name="introducing-the-new-microsoft-edge"></a>Presentación del nuevo Microsoft Edge

El nuevo Microsoft Edge [adopta el proyecto de código abierto de cromo](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) en el escritorio para crear una mejor compatibilidad web para los clientes y menos fragmentación de la web para todos los desarrolladores Web. También admitirá WebXR en el lanzamiento, el nuevo estándar para crear experiencias Web envolventes para los auriculares VR en lugar de WebVR.

## <a name="getting-ready-for-the-new-microsoft-edge"></a>Preparación para el nuevo Microsoft Edge

Los auriculares Windows Mixed Reality VR con auriculares que desean usar el nuevo Microsoft Edge en la Página principal de la realidad mixta deben **actualizarse a la versión 1903 o posterior de Windows 10 para ofrecer compatibilidad nativa con aplicaciones Win32 (como el nuevo Microsoft Edge)** en la Página principal de la realidad mixta. Active Windows Update o [Instale manualmente la versión más reciente de Windows 10](https://www.microsoft.com/en-us/software-download/windows10).

Para obtener la mejor experiencia posible de Microsoft Edge en la Página principal de la realidad mixta, también se recomienda esperar **algunas optimizaciones clave de Windows Mixed Reality para que la nueva Microsoft Edge llegue a la actualización acumulativa 2020-01 para Windows 10, versión 1903 (o posterior)** , que debe estar disponible en Windows Update a finales de enero.

>[!IMPORTANT]
>Si opta por descargar el nuevo Microsoft Edge antes de realizar estas actualizaciones, habrá algunos problemas conocidos con su comportamiento en Windows Mixed Reality (que puede leer a continuación).

## <a name="known-issues"></a>Problemas conocidos

### <a name="known-issues-resolved-by-the-2020-01-cumulative-update-for-windows-10-version-1903-or-later"></a>Problemas conocidos resueltos por la actualización acumulativa 2020-01 para Windows 10, versión 1903 (o posterior)

- Iniciar cualquier aplicación de Win32, incluido el nuevo Microsoft Edge, hace que la pantalla del casco se incongele brevemente.
- El icono de Microsoft Edge desaparece del menú Inicio de Windows Mixed Reality (puede encontrarlo en la carpeta "aplicaciones clásicas").
- Las ventanas del Microsoft Edge anterior se siguen colocando en la Página principal de la realidad mixta, pero no se pueden usar. El intento de activar esas ventanas inicia el borde dentro de la aplicación de escritorio.
- Al seleccionar un hipervínculo en la Página principal de realidad mixta, se inicia un explorador Web en el escritorio en lugar de la Página principal de realidad mixta.
- La aplicación WebVR Showcase está presente en la Página principal de la realidad mixta, a pesar de que WebVR ya no se admite.
- Mejoras generales en el inicio del teclado y los objetos visuales.

### <a name="additional-known-issues"></a>Otros problemas conocidos

-   Los sitios web abiertos en Windows Mixed Reality se perderán cuando se cierre el portal de realidad mixta, aunque las ventanas de Microsoft Edge permanecerán donde se colocaron en la Página principal de la realidad mixta.
-   El audio de las ventanas de Microsoft Edge no está espacial.
-   Abrir un vídeo 360 de YouTube en Windows Mixed Reality puede dar lugar a que el vídeo se distorsione en el casco. Actualizar la página del vídeo de YouTube y volver a iniciar el vídeo 360 debe corregir el problema.
-   Durante las sesiones de realidad mixta de Windows, los monitores virtuales aparecerán como monitores físicos genéricos en Configuración > pantalla de > del sistema.



