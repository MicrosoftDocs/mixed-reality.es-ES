---
title: Solución de problemas de OpenXR
description: Solucionar problemas en las aplicaciones de OpenXR.
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR, Khronos, BasicXRApp, DirectX, Native, aplicación nativa, motor personalizado, middleware, solución de problemas
ms.openlocfilehash: 08ca671ded7230a4ba3cfcdc640233082af51040
ms.sourcegitcommit: 9de2cb11321e6517db69e8c93459a205900a2174
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163369"
---
# <a name="openxr-troubleshooting"></a>Solución de problemas de OpenXR

A continuación se muestran algunas sugerencias para la solución de problemas al desarrollar una aplicación de OpenXR mediante el tiempo de ejecución de Windows Mixed Reality OpenXR.  Si tiene alguna pregunta sobre la especificación de <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1,0</a>, visite los foros de <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR</a> o el <a href="https://khr.io/slack" target="_blank">margen de demora #openxr canal</a>.

>[!NOTE]
>Existen problemas conocidos en el tiempo de ejecución actual de Windows Mixed Reality OpenXR con las aplicaciones x86.  En este momento, debe compilar aplicaciones de escritorio OpenXR para x64.

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>La aplicación OpenXR no inicia Windows Mixed Reality

Si la aplicación de OpenXR no inicia Windows Mixed Reality al ejecutarla, es posible que el tiempo de ejecución de Windows Mixed Reality OpenXR no se establezca como el tiempo de ejecución activo.  Asegúrese de seguir las instrucciones anteriores para empezar a [trabajar con los auriculares de OpenXR para Windows Mixed Reality](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) para activar el tiempo de ejecución.

También puede ejecutar el [portal para desarrolladores de Windows Mixed Reality OpenXR](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-portal) para ayudarle a solucionar problemas en el estado del tiempo de ejecución de Windows Mixed Reality OpenXR en el sistema.

### <a name="mixed-reality-portal-not-showing-set-up-openxr-menu-item"></a>El portal de realidad mixta no muestra el elemento de menú "configurar OpenXR"

Asegúrese de que está ejecutando al menos la actualización 2018 de octubre de Windows 10 (1809).  Si se encuentra en una versión anterior de Windows 10, puede actualizar a la actualización de mayo de 2019 (1903) mediante el [Asistente de actualización de Windows 10](https://www.microsoft.com//software-download/windows10).

Es posible que el elemento de menú "configurar OpenXR" no esté disponible si tiene una versión anterior de la aplicación del portal de realidad mixta.  Busque una actualización de la [aplicación del portal de realidad mixta](https://www.microsoft.com/p/mixed-reality-portal/9ng1h8b3zc7m) para asegurarse de que tiene la versión más reciente.

Tenga en cuenta que el elemento de menú "configurar OpenXR" no se mostrará si el tiempo de ejecución de Windows Mixed Reality OpenXR ya está instalado y activo.  Puede instalar el [portal para desarrolladores de Windows Mixed Reality OpenXR](openxr-getting-started.md#getting-the-windows-mixed-reality-openxr-developer-portal) para determinar el estado actual del tiempo de ejecución de OpenXR en el sistema.