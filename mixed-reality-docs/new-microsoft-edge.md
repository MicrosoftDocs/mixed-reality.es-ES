---
title: Windows Mixed Reality y el nuevo Microsoft Edge
description: Prepárese para el nuevo Microsoft Edge en Windows Mixed Reality. Incluye los cambios que se esperan, las actualizaciones que se deben tener en cuenta y los problemas conocidos.
author: mattzmsft
ms.author: mazeller
ms.date: 01/15/2020
ms.topic: article
keywords: Edge, nuevo, Web envolvente, Microsoft Edge, explorador, VR
ms.openlocfilehash: 2576762786c9234377308f226036c830e01d9133
ms.sourcegitcommit: d73d9012941fa1b13eb7d2f45ccc481d6365827a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76885623"
---
# <a name="windows-mixed-reality-and-the-new-microsoft-edge"></a>Windows Mixed Reality y el nuevo Microsoft Edge

El [nuevo Microsoft Edge ya está disponible para su descarga](https://blogs.windows.com/windowsexperience/?p=173496), pero los clientes también pueden [esperar a que se instale en una actualización futura de Windows 10](https://blogs.windows.com/msedgedev/2020/01/15/upgrading-new-microsoft-edge-79-chromium/), siguiendo un enfoque de implementación medido en los próximos meses. 

Con esta noticia, **queríamos que los clientes de Windows Mixed Reality VR con auriculares sepan qué esperar del nuevo Microsoft Edge y le informan de algunas actualizaciones pendientes que mejorarán la experiencia de exploración Web en Windows Mixed Reality**.

## <a name="introducing-the-new-microsoft-edge"></a>Presentación del nuevo Microsoft Edge

El nuevo Microsoft Edge [adopta el proyecto de código abierto de cromo](https://blogs.windows.com/windowsexperience/2018/12/06/microsoft-edge-making-the-web-better-through-more-open-source-collaboration/) en el escritorio para crear una mejor compatibilidad web para los clientes y menos fragmentación de la web para todos los desarrolladores Web. También admitirá WebXR en el lanzamiento, el nuevo estándar para crear experiencias Web envolventes para los auriculares VR en lugar de WebVR.

>[!IMPORTANT]
>Al instalar Microsoft Edge en un dispositivo de Windows 10 actualizado, se reemplazará la versión anterior (heredada) del equipo.

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

### <a name="additional-known-issues"></a>Problemas conocidos adicionales

-   Los sitios web abiertos en Windows Mixed Reality se perderán cuando se cierre el portal de realidad mixta, aunque las ventanas de Microsoft Edge permanecerán donde se colocaron en la Página principal de la realidad mixta.
-   El audio de las ventanas de Microsoft Edge no está espacial.
-   Se **corrigió en la versión de extensión de 360 Viewer 2.3.8**: abrir un vídeo de 360 desde YouTube en Windows Mixed Reality puede dar lugar a que el vídeo se distorsione en el casco. El reinicio de Edge debe actualizar de manera invisible la extensión del visor de 360 para resolver este problema. Puede confirmar qué versión de la extensión tiene escribiendo `edge://system/` en la barra de direcciones y seleccionando el botón de **expansión** junto a "extensiones".
-   Durante las sesiones de realidad mixta de Windows, los monitores virtuales aparecerán como monitores físicos genéricos en Configuración > pantalla de > del sistema.



