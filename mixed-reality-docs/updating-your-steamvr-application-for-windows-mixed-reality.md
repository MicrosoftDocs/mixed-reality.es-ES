---
title: Actualización de la aplicación SteamVR
description: Prácticas recomendadas para actualizar la aplicación SteamVR con el fin de maximizar la compatibilidad con auriculares de realidad mixta de Windows.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR, compatibilidad
ms.openlocfilehash: 6479130b14b8b50828ebecd3a648fd8a425aec15
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73438206"
---
# <a name="updating-your-steamvr-application"></a>Actualización de la aplicación SteamVR
Animamos a los desarrolladores a probar y optimizar sus experiencias de SteamVR para que se ejecuten en auriculares Windows Mixed Reality. En esta documentación se describen las mejoras comunes que los desarrolladores pueden hacer para asegurarse de que su experiencia se ejecute de manera excelente en Windows Mixed Reality.

## <a name="initial-setup-instructions"></a>Instrucciones de configuración inicial

Para empezar a probar su juego o aplicación en Windows Mixed Reality, asegúrese de que primero siga nuestra [Guía de introducción.](https://aka.ms/WindowsMixedRealitySteamVR)

## <a name="controller-models"></a>Modelos de controlador
1. Si la aplicación representa modelos de controlador:
    * Usar los [modelos de controlador de movimiento de Windows Mixed Reality](motion-controllers.md#rendering-the-motion-controller-model)
    * Use IVRRenderModel:: GetComponentState para obtener transformaciones locales a las partes del componente (por ejemplo, El puntero representa)
2. Las experiencias que tienen una noción de mano deben obtener sugerencias de las API de entrada para diferenciar los controladores [(ejemplo de Unity)](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)

## <a name="controls"></a>Controls

Al diseñar o ajustar el diseño del control, tenga en cuenta el siguiente conjunto de comandos reservados:
1. Hacer clic en el **stick analógico izquierdo y derecho** está reservado para el **Panel de vapor**.
2. El **botón Windows** siempre devolverá los usuarios a la Página principal de Windows Mixed Reality.

Si es posible, el valor predeterminado es la teleportabilidad basada en el control de posición para que coincida con el comportamiento de teleportabilidad [principal de Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) .

## <a name="tooltips-and-ui"></a>Información sobre herramientas e interfaz de usuario

Muchos juegos de VR aprovechan las superposiciones y la información sobre herramientas del controlador de movimiento para enseñar a los usuarios los comandos más importantes para su juego o aplicación. Al optimizar la aplicación para Windows Mixed Reality, se recomienda revisar esta parte de su experiencia para asegurarse de que la información sobre herramientas se asigna a los modelos de controlador de Windows.

Además, si hay algún punto en la experiencia en el que se muestren imágenes de los controladores, asegúrese de proporcionar imágenes actualizadas con los controladores de movimiento de Windows Mixed Reality.

## <a name="haptics"></a>Hápticos

A partir de la [actualización 2018 de abril de Windows 10](release-notes-april-2018.md), ahora se admiten hápticos para experiencias de SteamVR en Windows Mixed Reality. Si su aplicación o juego de SteamVR ya incluye compatibilidad con hápticos, ahora debería funcionar (sin trabajo adicional) con [los controladores de movimiento de Windows Mixed Reality](motion-controllers.md).

Los controladores de movimiento de Windows Mixed Reality usan un motor hápticos estándar, en contraposición a los accionadores lineales que se encuentran en otros controladores de movimiento SteamVR, lo que puede conducir a una experiencia de usuario ligeramente diferente a la esperada. Por lo tanto, se recomienda probar y ajustar el diseño de hápticos con los controladores de movimiento de Windows Mixed Reality. Por ejemplo, en ocasiones, los impulsores cortos cortos (5-10 ms) son menos perceptibles en los controladores de movimiento de Windows Mixed Reality. Para generar un pulso más perceptible, experimente con el envío de un "clic" más largo (40-70ms) para dar más tiempo al motor para que se ponga al día antes de que se le diga volver a desconectar.

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a>Inicio de aplicaciones de SteamVR desde el menú Inicio de Windows Mixed Reality

En el caso de las experiencias de VR distribuidas a través de vapor, hemos [actualizado Windows Mixed Reality para SteamVR beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) junto con los vuelos de [Windows Insider](https://insider.windows.com) RS5 más recientes para que los títulos de SteamVR ahora aparezcan en el menú Inicio de Windows Mixed Reality en "todas las aplicaciones". Mostrar automáticamente. Con estas versiones de software instaladas, los clientes ahora pueden iniciar títulos de SteamVR directamente desde la Página principal de Windows Mixed Reality sin necesidad de quitar los auriculares.

## <a name="windows-mixed-reality-logo"></a>Logotipo de Windows Mixed Reality

Para mostrar la compatibilidad con Windows Mixed Reality para su título, vaya al vínculo "editar página de la tienda" en la página de aterrizaje de la aplicación, haga clic en la pestaña "información básica" y desplácese hacia abajo hasta "realidad virtual". Desactive la casilla "ocultar Windows Mixed Reality" y, a continuación, publique en la tienda.

## <a name="bugs-and-feedback"></a>Errores y comentarios

Sus comentarios son invaluables cuando se trata de mejorar la experiencia SteamVR de Windows Mixed Reality. Envíe todos los comentarios y errores a través del [centro de comentarios de Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback). A continuación se muestran algunas [sugerencias sobre cómo hacer que los comentarios de SteamVR sean lo más útiles posible](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr).

Si tiene preguntas o comentarios para compartir, también puede ponerse en contacto con nosotros en nuestro [Foro de vapor](https://steamcommunity.com/app/719950/discussions/).

## <a name="faqs-and-troubleshooting"></a>Preguntas más frecuentes y solución de problemas

Si tiene problemas generales al configurar o reproducir su experiencia, [consulte los pasos de solución de problemas más recientes](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr).

## <a name="see-also"></a>Consulta también
* [Instalación de las herramientas](install-the-tools.md)
* [Historial de controladores de casco y controlador de movimiento](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [Instrucciones de compatibilidad de hardware de equipo mínima de Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
