---
title: 'Notas de la versión: mayo 2020'
description: Notas de la versión Windows Mixed Reality para la actualización 2020 de Windows 10 (también conocida como 2004).
author: tmlyon
ms.author: tmlyon
ms.date: 05/27/2020
ms.topic: article
keywords: Notas de la versión, versión, Windows 10, compilación, 20H1, so, 2020 de mayo de 2004
ms.openlocfilehash: ec92259662109001c02cf631eb6b9948d61ba9de
ms.sourcegitcommit: b0d15083ec1095e08c9d776e5bae66b4449383bb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/27/2020
ms.locfileid: "84124142"
---
# <a name="release-notes---may-2020"></a>Notas de la versión: mayo 2020

La **actualización 2020 de Windows 10 de mayo (v2004)** incluye nuevas características para los auriculares de Windows Mixed Reality (VR), como la capacidad de iniciar aplicaciones Win32 en la Página principal de la realidad mixta. HoloLens (1ª generación) está en el servicio a largo plazo (LTS), con actualizaciones de servicio que se publican mensualmente.

Para actualizar a la versión más reciente en el equipo para auriculares con Windows Mixed Reality (VR), abra la aplicación de **configuración** , vaya a **Actualizar & seguridad**y, luego, seleccione el botón **Buscar actualizaciones** . En un equipo con Windows 10, también puede instalar manualmente la **actualización de Windows 10 de mayo de 2020** mediante la [herramienta de creación de Windows Media](https://www.microsoft.com/software-download/windows10).

**Versión más reciente del escritorio**: Windows 10 v2004 (10.0.19041.264)

## <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>Actualizaciones para auriculares con Windows Mixed Reality

### <a name="introducing-the-new-microsoft-edge"></a>Presentación del nuevo Microsoft Edge
Como se [anunció anteriormente](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge), hemos realizado actualizaciones para mejorar la compatibilidad con el nuevo explorador Microsoft Edge en Windows Mixed Reality. El nuevo Microsoft Edge adopta el proyecto de código abierto de cromo para crear una mejor compatibilidad web para los clientes y menos fragmentación de la web para todos los desarrolladores Web. También es compatible con WebXR, el nuevo estándar para crear experiencias Web envolventes para auriculares VR en lugar de WebVR.

### <a name="improved-settings-for-wmr"></a>Configuración mejorada de WMR
Gracias a sus comentarios, hemos agregado y aclarado la configuración de la página de visualización de los auriculares:

* **Calidad visual de mi hogar** : el cambio de esta configuración solo afecta al entorno de inicio de la realidad mixta (acantilado House y Skyloft):

* **Ajuste el nivel de detalle y la calidad de los efectos en la Página principal de la realidad mixta** ; esto cambia algunos de los efectos de representación que usamos en el hogar. En concreto, la calidad visual de materiales diferentes (madera, hormigón, etc.) se escalará a medida que cambie esta configuración de baja a alta.

* **Cambiar la resolución** de la ventana de la aplicación: de forma predeterminada, la mayoría de las ventanas de 2D iniciadas en el hogar se inician con una resolución 720p. Aunque puede cambiar el tamaño de forma manual horizontalmente & verticalmente, también puede hacer que todos se inicien en 1080p en su lugar. Anteriormente, esta opción estaba disponible como la opción muy alta (beta) en calidad visual. Lo hemos dividido correctamente como una configuración independiente.

* **Opciones de experiencia** : estas opciones ajustan la experiencia de realidad mixta para reducir la carga en los sistemas en los que es posible que el hardware tenga dificultades para mantenerse al día con 90 fps sin restricciones. Puede optar por habilitar o deshabilitar explícitamente esta configuración adicional o elegir dejar que Windows decida y dejar que nuestra heurística siga decidiendo Cuándo activarlas y desactivarlas.

* **Resolución** : Si tiene auriculares de alta resolución como la reverberación de HP, admitimos su ejecución en su resolución nativa o con una resolución reducida por motivos de rendimiento. Los auriculares anteriores, como Samsung Odyssey y Odyssey +, solo admiten una resolución única, por lo que no podrá cambiar esta configuración en esos auriculares.

* **Velocidad de fotogramas** : ahora puede establecer manualmente la velocidad de fotogramas de la pantalla del casco o continuar para que Windows use su heurística para determinar si los 60 hz o 90 Hz son más adecuados.

* **Calibración** : como antes, puede ajustar el IPD (distancia interpupillary) si lo admiten los auriculares.

* **Cambio de entrada** : alterne el comportamiento de cambio de foco de entrada (Win + Y) para que sea automático (según los comentarios del sensor de presencia) o manual.

### <a name="new-cortana-app"></a>Nueva aplicación de Cortana
Esta actualización a Windows incluye la versión más reciente de la aplicación Cortana, que actualmente es solo en inglés y ya no es compatible con determinados comandos específicos de realidad mixta, como "tomar una imagen" y "tomar un vídeo". Todavía podrá usar el nuevo Cortana para iniciar aplicaciones y también se admiten los nuevos comandos de productividad, como "¿Cuándo es mi próxima reunión?" o bien, "enviar un correo electrónico a <name> que estoy ejecutando tarde".

#### <a name="please-help-us-improve"></a>Ayúdenos a mejorar.
Veremos continuamente cómo mejorar la compatibilidad.  Si encuentra que su aplicación favorita de Win32 clásica no se comporta correctamente en Windows Mixed Reality, envíe sus comentarios a través de nuestro [centro de opiniones](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub).

## <a name="prior-release-notes"></a>Notas de la versión anterior

* [Notas de la versión: mayo 2019](release-notes-may-2019.md)
* [Notas de la versión (octubre de 2018)](release-notes-october-2018.md)
* [Notas de la versión: abril 2018](release-notes-april-2018.md)
* [Notas de la versión (octubre de 2017)](release-notes-october-2017.md)
* [Notas de la versión (agosto de 2016)](release-notes-august-2016.md)
* [Notas de la versión (mayo de 2016)](release-notes-may-2016.md)
* [Notas de la versión (marzo de 2016)](release-notes-march-2016.md)

## <a name="see-also"></a>Consulte también
* [Compatibilidad con auriculares envolvente (vínculo externo)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [Compatibilidad con HoloLens (vínculo externo)](https://support.microsoft.com/products/hololens)
* [Instalación de las herramientas](install-the-tools.md)
* [Envíenos sus comentarios](give-us-feedback.md)
