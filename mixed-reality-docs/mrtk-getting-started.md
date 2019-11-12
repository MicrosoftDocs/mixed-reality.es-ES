---
title: Introducción a la versión 2 de MRTK
description: Para los nuevos desarrolladores interesados en aprovechar MRTK
author: cre8ivepark
ms.author: dongpark
ms.date: 05/15/2019
ms.topic: article
keywords: Windows Mixed Reality, test, kit de herramientas de realidad mixta, MRTK versión 2, MRTK, herramientas, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: bb958543aa68586dd689a2048665b233d6be7064
ms.sourcegitcommit: b6b76275fad90df6d9645dd2bc074b7b2168c7c8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2019
ms.locfileid: "73913127"
---
# <a name="getting-started-with-mrtk-v2"></a>Introducción a MRTK V2

## <a name="mrtk-getting-started-guide"></a>Guía de Introducción de MRTK
Vea la [Guía de introducción a MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) para obtener información detallada sobre cómo empezar a usar MRTK V2.

## <a name="what-is-mixed-reality-toolkit-mrtk"></a>¿Qué es el kit de herramientas de realidad mixta (MRTK)?
MRTK es un increíble kit de herramientas de código abierto que ha estado de la primera vez que se lanzó HoloLens, y no sería el lugar en el que se encontraba hoy sin el trabajo de nuestra comunidad de desarrolladores que ha contribuido. Durante los últimos 3 años, hemos escuchado los comentarios de nuestra comunidad de desarrolladores y hemos creado MRTK v2 para tener en cuenta las preocupaciones más importantes.  

MRTK v2 con Unity es un kit de desarrollo multiplataforma de código abierto para aplicaciones de realidad mixta.  MRTK versión 2 está diseñado para acelerar el desarrollo de aplicaciones destinadas a Microsoft HoloLens, cascos envolventes (VR) de Windows Mixed Reality y la plataforma OpenVR. El proyecto está destinado a reducir las barreras para la entrada, crear aplicaciones de realidad mixta y contribuir de nuevo a la comunidad a medida que crezcan. 

Consulte el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html) para obtener más información.

## <a name="new-with-mrtk-v2"></a>Novedad con MRTK V2
Queremos someter nuestro compromiso a estas herramientas de plataforma.  De hecho, aprovechamos la versión 2 de MRTK para desarrollar nuestras experiencias de bandeja de entrada, como la experiencia de instalación (OOBE) y nuestra aplicación de aprendizaje de realidad mixta.  También puede esperar ver las nuevas funcionalidades de HoloLens 2 que se exponen por primera vez a través de MRTK porque creemos que es la mejor manera de desarrollar en nuestra plataforma. 

### <a name="modular"></a>Módulos
Lo hemos creado de una manera modular, por lo que no es necesario llevar todos los bits del kit de herramientas al proyecto.  En realidad, hay algunas ventajas.  Mantiene el tamaño del proyecto más pequeño y facilita su administración.  Además, dado que se crea con objetos que admiten scripts y está orientado a la interfaz, también es posible reemplazar los componentes que se incluyen por su cuenta, para admitir otros servicios, sistemas y plataformas.

### <a name="cross-platform"></a>Multiplataforma
Hablando de otras plataformas, tiene compatibilidad entre plataformas.  Y aunque esto no significa que todas las plataformas se admitan de forma preestablecida, nos hemos asegurado de que ninguno de los códigos del kit de herramientas se interrumpa al cambiar el destino de compilación a otras plataformas.  La robustez y la extensibilidad con el diseño modular le establecen una buena ruta de acceso para poder admitir varias plataformas, como ARCore, ARKit y OpenVR.

### <a name="performant"></a>Rendimiento
Al trabajar con plataformas móviles, se construyó pensando en el rendimiento.  Esto es muy importante y queríamos asegurarnos de que las herramientas no vayan a trabajar con usted.

## <a name="see-also"></a>Consulta también
* [Guía de introducción a MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [Página principal de la documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [Instalación de las herramientas](install-the-tools.md)
* [Migración de HTK/MRTK a MRTK versión 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
