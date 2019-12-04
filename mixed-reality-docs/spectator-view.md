---
title: Vista del espectador
description: Visualiza los hologramas desde un dispositivo externo a fin de demostrar una experiencia de realidad mixta en una pantalla externa o grabar un vídeo de una experiencia de realidad mixta.
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Vista del espectador, iPhone, iOS, iPad, OpenCV, cámara, ARKit, HoloLens, realidad mixta, MixedRealityToolkit, demo, grabar
ms.openlocfilehash: 9bc1c2809c7d780d439d9efb58f464b41de3dccd
ms.sourcegitcommit: 4d43a8f40e3132605cee9ece9229e67d985db645
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491164"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a>Vista del espectador para HoloLens y HoloLens 2

![Rotulador](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a>Introducción

Cuando llevamos puesto el dispositivo HoloLens, a menudo nos olvidamos de que alguien que no lo lleve no puede experimentar las mismas maravillas que nosotros. La vista del espectador permite a otros usuarios ver en una pantalla 2D lo que ve un usuario de HoloLens en su mundo.
Dicha vista ofrece un enfoque rápido y asequible para grabar hologramas en HD con dispositivos móviles. También ofrece una grabación de hologramas de calidad profesional con cámaras de vídeo.

## <a name="key-resources"></a>Recursos clave

* [**Vista del espectador en GitHub**](https://github.com/microsoft/MixedReality-SpectatorView)
* [**Documentación de la vista del espectador**](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [**Ejemplos de la vista del espectador**](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a>Casos de uso
* Puedes grabar una experiencia de realidad mixta mediante un dispositivo iPhone o Android. Graba en Full HD y aplica el suavizado de contorno a hologramas e incluso a sombras. Es una forma rentable y rápida de capturar vídeos de hologramas.
* Haz streaming de experiencias de realidad mixta en directo a Apple TV directamente desde tu iPhone o iPad y sin retrasos.
* Comparte la experiencia con los invitados: permite que los usuarios sin HoloLens experimenten los hologramas directamente desde sus teléfonos o tabletas.

## <a name="current-features"></a>Características actuales

* Sincronización espacial de los hologramas, para que todos los usuarios vean los hologramas exactamente en el mismo lugar.
* Compatibilidad con iOS (dispositivos habilitados para ARKit) y Android (dispositivos habilitados para ARCore).
Varios invitados de iOS.
Grabación de vídeo + hologramas + sonido de ambiente + sonido del holograma.
Hoja compartida para que puedas guardar un vídeo, enviarlo por correo electrónico o compartirlo con otras aplicaciones compatibles.

![Marcador](images/SpecViewPhoneDemo.jpg)
![Marcador](images/hololensspectatorview-500px.jpg) ![Marcador](images/spectatorview-300px.png)

En la tabla siguiente se muestran varias funcionalidades de la vista de espectador y sus características. Elige la opción que mejor se adapte a tus necesidades de grabación de vídeo:

|                                      | Móvil                  |                    Cámara de vídeo              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| Calidad HD                           |         Full HD         |        Filmación de calidad profesional (determinada por la cámara de vídeo)      |
| Movimiento de la cámara simplificado                 |            ✔            |                      ✔                      |
| Vista en tercera persona                    |            ✔            |                      ✔                      |
| Se puede hacer streaming a pantallas           |            ✔            |                      ✔                      |
| Portátil                             |            ✔            |                                             |
| Inalámbrico                             |            ✔            |                                             |
| Hardware adicional necesario         |     Teléfono Android, iPhone    | HoloLens + plataforma + trípode + cámara de vídeo + equipo + Unity |
| Inversión en hardware                  |           Bajo            |                     Alto                    |
| Multiplataforma                       |           Android, iOS   |                                             |
| Contenido sincronizado                 |            ✔            |                      ✔                      |
| Duración de la instalación en tiempo de ejecución               |         Instantánea          |                     Lenta                    |
## <a name="see-also"></a>Consulte también

* [Captura de realidad mixta](mixed-reality-capture.md) 
* [Captura de realidad mixta para desarrolladores](mixed-reality-capture-for-developers.md)
* [Experiencias compartidas en realidad mixta](shared-experiences-in-mixed-reality.md)
