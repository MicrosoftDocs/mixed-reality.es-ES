---
title: Uso de WebVR en Microsoft Edge con Windows Mixed Reality
description: Información general de uso y desarrollo de WebVR en Windows Mixed Reality
author: YashMaster
ms.author: yabahman
ms.date: 03/21/2018
ms.topic: article
keywords: WebVR, WebXR, WinMR, WebAR, web vr, web xr, web mr, web ar, 360, 360 vídeo 360 vídeos, fotografías 360, 360 fotos, contenido 360, envolvente, web immersiveweb, IW
ms.openlocfilehash: fab17f4dcecc34d8f1ca4836dce6de90522899cd
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605691"
---
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a>Uso de WebVR en Microsoft Edge con Windows Mixed Reality

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a>Creación de contenido de WebVR para Windows Mixed reality inmersivos

WebVR 1.1 está disponible en el Windows 10 Fall Creators Update a partir de Microsoft Edge. Los desarrolladores ahora pueden usar esta API para crear experiencias envolventes de realidad virtual en la web.

La API de WebVR proporciona datos de la postura HMD a la página que se puede usar para representar un escena WebGL estéreo el HMD. Obtener más información sobre la compatibilidad con la API está disponible en el [página de estado de la plataforma de Microsoft Edge](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/). El área expuesta de API WebVR está presente en todo momento dentro de Microsoft Edge. Sin embargo, una llamada a getVRDisplays() solo devolverá un auricular si está conectado auriculares o se ha activado el simulador.

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a>Visualización de contenido de WebVR en inmersivos Windows Mixed Reality

Puede encontrar instrucciones para tener acceso al contenido de WebVR en los auriculares envolventes en la [guía entusiastas](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).

## <a name="see-also"></a>Vea también
* [Información de WebVR](http://webvr.info)
* [Especificación de WebVR](https://w3c.github.io/webvr/)
* [WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)
* [WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)
* [Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) y [Gamepad extensiones](https://w3c.github.io/gamepad/extensions.html)
* [Control que pierde el contexto en WebGL](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](http://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [Uso de Babylon.js para habilitar WebVR](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)

