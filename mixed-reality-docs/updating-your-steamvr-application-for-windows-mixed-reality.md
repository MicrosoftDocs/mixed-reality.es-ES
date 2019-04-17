---
title: Actualiza la aplicación SteamVR para Windows Mixed Reality
description: Procedimientos recomendados para actualizar la aplicación SteamVR para maximizar la compatibilidad con auriculares de realidad mixta de Windows.
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR, compatibilidad
ms.openlocfilehash: db21651df8e586edf500f0d05def4b1ea5474284
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597857"
---
# <a name="updating-your-steamvr-application-for-windows-mixed-reality"></a>Actualiza la aplicación SteamVR para Windows Mixed Reality

Animamos a los desarrolladores para probar y optimizar sus experiencias SteamVR para ejecutarse en auriculares de realidad mixta de Windows. Esta documentación trata mejoras comunes a los desarrolladores pueden realizar para asegurarse de que su experiencia funcione perfectamente en Windows Mixed Reality.

## <a name="initial-setup-instructions"></a>Instrucciones de configuración inicial

Para empezar a probar su juego o aplicación en la marca Windows Mixed Reality claro a primera siga nuestro [Guía de introducción.](http://aka.ms/WindowsMixedRealitySteamVR)

## <a name="controller-models"></a>Modelos de controlador
1. Si la aplicación procesa los modelos de controlador:
    * Use el [modelos de controlador de movimiento de Windows Mixed Reality](motion-controllers.md#rendering-the-motion-controller-model)
    * Use IVRRenderModel::GetComponentState obtener local se transforma en componentes (p ej. Postura de puntero)
2. Experiencias que tienen una noción de diestro o zurdo deben obtener las sugerencias de la API para diferenciar los controladores de entrada [(ejemplo de Unity)](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)

## <a name="controls"></a>Controls

Al diseñar o ajustar el diseño del control tenga en cuenta el siguiente conjunto de comandos reservados:
1. Al hacer clic en hacia abajo el **tecla de navegación izquierda y derecha analógica** está reservado para el **vapor panel**.
2. El **botón Windows** siempre volverá a los usuarios a Windows Mixed Reality principal.

Si es posible, valor predeterminado para thumb stick basado teleportation para que coincida con el [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) teleportation comportamiento

## <a name="tooltips-and-ui"></a>Información sobre herramientas e interfaz de usuario

Muchos juegos de realidad virtual sacar partido de la información sobre herramientas de controlador de movimiento y superposiciones a enseñar a los usuarios de los comandos más importantes para su juego o aplicación. Al optimizar la aplicación para Windows Mixed reality se recomienda revisar esta parte de su experiencia para asegurarse de que la información sobre herramientas se asignan a los modelos de controlador de Windows.

Además si existen los puntos en su experiencia donde se muestran imágenes de los controladores asegúrese de que proporcionar imágenes actualizadas con los controladores de Windows Mixed Reality movimiento.

## <a name="haptics"></a>Haptics

A partir del [Windows 10 de abril de 2018 Update](release-notes-april-2018.md), haptics ahora se admiten para SteamVR experiencias con Windows Mixed Reality. Si su aplicación SteamVR o juego ya incluye compatibilidad para haptics, ahora debería funcionar (sin ningún trabajo adicional) con [los controladores de Windows Mixed Reality movimiento](motion-controllers.md).

Los controladores de Windows Mixed Reality movimiento utilizan un motor haptics estándar, en lugar de la accionadores lineales que se encuentra en algunos otros SteamVR movimiento controladores, lo que pueden provocar una experiencia de usuario ligeramente diferente que el previsto. Por lo tanto, se recomienda probar y ajustar el diseño haptics con los controladores de Windows Mixed Reality movimiento. Por ejemplo, pulsos hápticos cortos a veces (entre 5 y 10 ms) son menos visibles en los controladores de Windows Mixed Reality movimiento. Para generar un pulso más evidente, experimentar con el envío de una mayor "click" (40-70ms) para dar más tiempo para poner en marcha motor antes de que se le indica que power off nuevo.

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a>Ejecución de aplicaciones de SteamVR desde el menú Inicio de Windows Mixed Reality

Para experiencias VR distribuidas a través de vapor, hemos [actualiza Windows Mixed Reality para SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) junto con la versión más reciente [Windows Insider](https://insider.windows.com) RS5 vuelos para que los títulos de SteamVR ahora se muestran en la Menú de inicio de realidad mixta de Windows en el "todas las aplicaciones" lista automáticamente. Con estas versiones de software instaladas, los clientes ahora pueden iniciar SteamVR títulos directamente desde dentro de Windows Mixed Reality doméstica sin quitar los auriculares.

## <a name="windows-mixed-reality-logo"></a>Logotipo de Windows Mixed Reality

Para mostrar para el título del soporte técnico de Windows Mixed Reality, vaya al vínculo "Editar página de Store" en la página de aterrizaje de la aplicación, haga clic en la pestaña "Información básica" y desplácese hacia abajo hasta "Virtual Reality". Desactive el "Ocultar Windows Mixed Reality" y, a continuación, publicar en el almacén.

## <a name="bugs-and-feedback"></a>Errores y comentarios

Sus comentarios son muy útil cuando se trata de mejorar la experiencia de Windows Mixed Reality SteamVR. Envíe todos los comentarios y los errores a través de la [centro de comentarios de Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback). Estas son algunas [sugerencias sobre cómo hacer que sus comentarios SteamVR resulta tan útil como sea posible](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr).

Si tiene preguntas o comentarios para compartir, se puede también en contacto con nosotros en nuestro [foro de vapor](http://steamcommunity.com/app/719950/discussions/).

## <a name="faqs-and-troubleshooting"></a>Preguntas más frecuentes y solución de problemas

Si experimenta problemas generales de configuración o su propia experiencia, la reproducción [consulte los pasos de solución de problemas más reciente](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr).

## <a name="see-also"></a>Vea también
* [Instalar las herramientas](install-the-tools.md)
* [Historial de los controladores controlador auriculares y movimiento](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [Directrices para compatibilidad de hardware mínimas PC de Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
