---
title: Introducción al desarrollo de la realidad mixta de JavaScript
description: Información general sobre el desarrollo de realidad mixta con JavaScript para auriculares Web, móviles y de Windows.
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR, WinMR, WebAR, WebVR, WindowsMixedReality, HoloLens, Windows Mixed Reality, Web VR, webxr, Web Mr, ar website, 360, 360 video, 360 videos, 360 Photo, 360 fotos, 360 contenido, Web envolvente, inmersivo-Web, IW, immersiveweb
ms.openlocfilehash: 5756af9f48f4bb25477e75fb1f7c09e7239bdab9
ms.sourcegitcommit: d6ac8f1f545fe20cf1e36b83c0e7998b82fd02f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278486"
---
# <a name="mixed-reality-development-with-javascript-overview"></a>Información general sobre el desarrollo de realidad mixta con JavaScript

## <a name="mixed-reality-applications-on-the-web"></a>Aplicaciones de realidad mixta en la web

Las características de realidad mixta están disponibles en la web mediante el uso de las [API de dispositivo WebXR](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API) y [API de WebVR en desuso] ([información general de WebXR](webxr-overview.md). En el caso de los exploradores que no son compatibles con las características de WebXR completas, puede agregar [rellenos de WebXR](https://github.com/immersive-web/webxr-polyfill) a su sitio Web.

## <a name="what-is-webxr-polyfill"></a>Qué es WebXR polyfill

Una implementación de JavaScript de la API de dispositivo de WebXR, así como el módulo de controlador de juegos de WebXR. Este polyfill permite a los desarrolladores escribir con la especificación más reciente, lo que proporciona compatibilidad cuando se ejecuta en exploradores que implementan la especificación de WebVR 1,1 o en dispositivos móviles sin compatibilidad con WebVR/WebXR.

## <a name="javascript-libraries-to-build-mixed-reality-applications-on-the-web"></a>Bibliotecas de JavaScript para compilar aplicaciones de realidad mixta en la web

## <a name="babylonjs"></a>Babylon. js

Babylon es un motor 3D de JavaScript que facilita el desarrollo de contenido 3D y aplicaciones envolventes. Antes de empezar a trabajar con aplicaciones envolventes, se recomienda conocer los aspectos básicos del desarrollo de Babylon. js.

Obtenga información sobre cómo compilar una aplicación de realidad mixta con Babylon en la [Sección Introducción](https://doc.babylonjs.com/). Juegue con ejemplos 3D y su código fuente mediante el Babylon de la [animación](https://doc.babylonjs.com/examples/). Profundice en el desarrollo de la realidad mixta en la [sección WebXR](https://doc.babylonjs.com/how_to/introduction_to_webxr) de la documentación. 

## <a name="a-frame"></a>A-marco

A-Frame es un marco de JavaScript declarativo para empezar a trabajar con la realidad virtual en la Web. Consulte la [documentación del marco](https://aframe.io/) a para obtener más información.

## <a name="threejs"></a>Tres. js

Tres. js es una popular biblioteca 3D para crear experiencias envolventes. Obtenga más información sobre [tres. js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) en la página de documentación y explore los [ejemplos](https://threejs.org/examples/#webgl_animation_cloth).

## <a name="webgl"></a>WebGL

Puede acceder a las API del dispositivo WebXR directamente mediante las API de WebGL. WebGL (biblioteca de gráficos Web) es una API de JavaScript para representar gráficos 2D y 3D interactivos de alto rendimiento en cualquier explorador Web compatible sin el uso de complementos. Obtenga más información sobre las [API de WebGL](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API).

## <a name="mixed-reality-native-mobile-applications-using-javascript"></a>Aplicaciones móviles nativas de realidad mixta con JavaScript

Con la ayuda de algunas bibliotecas de JavaScript, puede escribir una vez las experiencias de realidad mixta y implementarlas en la web y en plataformas nativas, como los auriculares de realidad mixta de Windows, los dispositivos iOS y Android.

## <a name="babylon-native"></a>Babylon nativo

La plataforma [nativa Babylon](https://www.babylonjs.com/native/) permite a cualquier persona tomar su código Babylon. js y compilar una aplicación nativa con él, desbloqueando la eficacia de las tecnologías nativas. Puede descargar [Babylon Native en github](https://github.com/BabylonJS/BabylonNative) y obtener más información sobre él en el [blog de Babylon. js](https://medium.com/@babylonjs/babylon-native-821f1694fffc).

## <a name="react-native"></a>React Native

[ReAct Native](https://reactnative.dev/) es otra biblioteca de código abierto que permite a los desarrolladores compilar con JavaScript e implementar en varias plataformas. Puede descargar [reAct Native en github](https://github.com/facebook/react-native) y obtener más información en el [blog de reAct Native](https://reactnative.dev/blog/).

## <a name="see-also"></a>Consulta también

* [Información general de WebXR](webxr-overview.md)
* [Especificación de la API de dispositivo WebXR](https://immersive-web.github.io/webxr/)
* [Documentación de la API del dispositivo WebXR](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [Immersiveweb. dev](https://immersiveweb.dev/)
* [Ejemplos de WebXR](https://immersive-web.github.io/webxr-samples/)
* [Uso de Babylon. js para crear experiencias de WebXR](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [Windows Mixed Reality y el nuevo Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [GitHub Web de W3C envolvente](https://github.com/immersive-web)
* [API de WebGL](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)
* [API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) y [extensiones de controlador](https://w3c.github.io/gamepad/extensions.html) para juegos
* [Información general de WebVR](webvr-overview.md)
