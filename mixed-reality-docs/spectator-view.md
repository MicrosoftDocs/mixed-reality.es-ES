---
title: Vista Spectator
description: Visualice los hologramas de un dispositivo externo como un medio para demostrar una experiencia de realidad mixta en una pantalla externa o en una grabación de vídeo de una experiencia de realidad mixta.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
keywords: Spectator ver, iPhone, iOS, iPad, OpenCV, cámara, ARKit, HoloLens, Mixed Reality, MixedRealityToolkit, Demo, registro
ms.openlocfilehash: 135a566456f1000669d2033edcf0d0b4649ccdf3
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387668"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a>Vista de Spectator para HoloLens y HoloLens 2

![Rotulador](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a>Información general

Cuando se utiliza HoloLens, a menudo se olvida de que una persona que no la tiene en no puede experimentar las maravillas que podemos. Spectator vista permite a otros usuarios ver en una pantalla 2D lo que ve un usuario de HoloLens en su mundo.
Spectator View ofrece un enfoque rápido y asequible para grabar hologramas en HD con dispositivos móviles. También ofrece una grabación de calidad profesional de hologramas con cámaras de vídeo.

## <a name="key-resources"></a>Recursos clave

* [**Vista de Spectator en GitHub**](https://github.com/microsoft/MixedReality-SpectatorView)
* [**Arquitectura**](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Architecture.md)
* [**Assembl**](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)
* [**Instrucciones para la configuración de dispositivos móviles**](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Setup.md)
* [**Instrucciones de configuración de la cámara de vídeo**](https://github.com/microsoft/MixedReality-SpectatorView/blob/master/doc/SpectatorView.Setup.VideoCamera.md)

## <a name="use-cases"></a>Casos de uso
* Puede grabar una experiencia de realidad mixta mediante un dispositivo iPhone o Android. Grabe en HD completo y aplique suavizado de contorno a hologramas e incluso sombras. Es una forma rentable y rápida de capturar vídeo de hologramas.
* Transmita experiencias de realidad mixta en directo a Apple TV directamente desde su iPhone o iPad, sin retrasos.
* Compartir la experiencia con los invitados: Permita que los usuarios que no sean de HoloLens experimenten hologramas directamente desde sus teléfonos o tabletas.

## <a name="current-features"></a>Características actuales

* Sincronización espacial de hologramas, por lo que todos los usuarios ven los hologramas en el mismo lugar exacto.
* compatibilidad con iOS (dispositivos habilitados para ARKit) y Android (dispositivos habilitados para ARCore).
Varios invitados iOS.
Grabación de vídeo + hologramas + sonido ambiente + sonido de holograma.
Hoja compartida para que pueda guardar vídeo, enviarlo por correo electrónico o compartir con otras aplicaciones auxiliares.

![Marcador de marcador de marcador![](images/SpecViewPhoneDemo.jpg)
](images/hololensspectatorview-500px.jpg) ![](images/spectatorview-300px.png)

En la tabla siguiente se muestran la funcionalidad de la vista Spectator y sus capacidades. Elija la opción que mejor se adapte a sus necesidades de grabación de vídeo:

|                                      | Móvil                  |                    Cámara de vídeo              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| Calidad HD                           |         HD completo         |        Filmadora de calidad profesional (según lo determinado por la cámara de vídeo)      |
| Movimiento de cámara sencillo                 |            ✔            |                      ✔                      |
| Vista de terceros                    |            ✔            |                      ✔                      |
| Se puede transmitir a pantallas           |            ✔            |                      ✔                      |
| Portable                             |            ✔            |                                             |
| Conexión inalámbrica                             |            ✔            |                                             |
| Hardware necesario adicional         |     Teléfono Android, iPhone    | HoloLens + plataforma + trípode + cámara de vídeo + PC + Unity |
| Inversión en hardware                  |           Bajo            |                     Alto                    |
| Multiplataforma                       |           Android, iOS   |                                             |
| Contenido sincronizado                 |            ✔            |                      ✔                      |
| Duración de la instalación en tiempo de ejecución               |         Colabora          |                     Nivel lento                    |
## <a name="see-also"></a>Vea también

* [Captura de realidad mixta](mixed-reality-capture.md) 
* [Captura de realidad mixta para desarrolladores](mixed-reality-capture-for-developers.md)
* [Experiencias compartidas en realidad mixta](shared-experiences-in-mixed-reality.md)
