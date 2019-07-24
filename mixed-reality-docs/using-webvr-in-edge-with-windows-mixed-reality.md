---
title: Uso de WebVR en Microsoft Edge con Windows Mixed Reality
description: Información general sobre el uso y desarrollo para WebVR en Windows Mixed Reality
author: YashMaster
ms.author: yabahman
ms.date: 03/21/2018
ms.topic: article
keywords: WebVR, WebXR, WinMR, WebAR, Web VR, webxr, Web Mr, WebAr, 360, 360 vídeo, 360 vídeos, 360 Photo, 360 photos, 360 Content, Web inmersivo, immersiveweb, IW
ms.openlocfilehash: fab17f4dcecc34d8f1ca4836dce6de90522899cd
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63548758"
---
# <a name="using-webvr-in-microsoft-edge-with-windows-mixed-reality"></a>Uso de WebVR en Microsoft Edge con Windows Mixed Reality

## <a name="creating-webvr-content-for-windows-mixed-reality-immersive-headsets"></a>Creación de contenido de WebVR para auriculares con Windows Mixed Reality

WebVR 1,1 está disponible en Microsoft Edge a partir de Windows 10 Fall Creators Update. Los desarrolladores ahora pueden usar esta API para crear experiencias de VR envolventes en la Web.

La API WebVR proporciona datos de representación de HMD a la página que se puede usar para volver a presentar una escena WebGL de estéreo a la HMD. Los detalles sobre la compatibilidad con la API están disponibles en la [Página estado de la plataforma Microsoft Edge](https://developer.microsoft.com/microsoft-edge/platform/status/webvr/). El área expuesta de la API de WebVR está presente en todo momento dentro de Microsoft Edge. Sin embargo, una llamada a getVRDisplays () solo devolverá un auricular Si se enchufa un casco o si se ha activado el simulador.

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a>Visualización del contenido de WebVR en auriculares Windows Mixed Reality

Las instrucciones para obtener acceso al contenido de WebVR en los auriculares que se encuentran en el casco se pueden encontrar en la [Guía del entusiasta](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).

## <a name="see-also"></a>Vea también
* [Información de WebVR](http://webvr.info)
* [Especificación de WebVR](https://w3c.github.io/webvr/)
* [API de WebVR](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)
* [API de WebGL](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)
* [API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) y [extensiones de controlador](https://w3c.github.io/gamepad/extensions.html) para juegos
* [Controlar el contexto perdido en WebGL](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [Pointerlock](http://www.w3.org/TR/pointerlock/)
* [glTF](https://www.khronos.org/gltf)
* [Uso de Babylon. js para habilitar WebVR](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)

