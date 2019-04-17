---
title: Introducción a MRTK versión 2
description: Para los nuevos desarrolladores interesados en aprovechar MRTK
author: grbury
ms.author: grbury
ms.date: 02/22/19
ms.topic: article
keywords: Windows Mixed Reality, prueba, MRTK versión 2, MRTK, herramientas, SDK, HoloLens, HoloLens 2
ms.openlocfilehash: 44e5fe0fd4384af68922eda4bcb0594d39a1c1b7
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600028"
---
# <a name="getting-started-with-mrtk-version-2"></a>Introducción a MRTK versión 2

El MRTK es un Kit de herramientas increíbles de código abierto que ha estado presente desde el HoloLens publicó por primera vez y no sería donde se encuentra hoy sin el trabajo duro de nuestra comunidad de desarrolladores que han contribuido a él. Durante los últimos 3 años, hemos tenido en cuenta los comentarios de nuestra comunidad de desarrolladores y generado MRTK versión 2 para las principales preocupaciones de tener en cuenta.  

La versión 2 MRTK con Unity es un kit de desarrollo multiplataforma de código abierto para las aplicaciones de realidad mixta.  MRTK versión 2 está diseñado para acelerar el desarrollo de aplicaciones destinadas a Microsoft HoloLens, inmersivos (VR) Windows Mixed Reality y OpenVR plataforma. El proyecto está destinado a reducir las barreras de entrada para crear aplicaciones de realidad mixta y contribuir a la Comunidad que todos a medida que crecen. 


Consulte la <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/wiki/Getting-Started-with-MRTK-v2" target="_blank">MRTK versión 2 wiki</a> para empezar a trabajar y obtenga más información.

## <a name="new-with-mrtk-version-2"></a>Nuevo con MRTK versión 2
Queremos hacer hincapié en nuestro compromiso con estas herramientas de plataforma.  De hecho, hemos aprovechado MRTK versión 2 para desarrollar nuestras experiencias de bandeja de entrada, como la experiencia de instalación (OOBE) y nuestra aplicación de aprendizaje de realidad mixta.  También puede esperar ver nuevas capacidades de HoloLens 2 que primero se expone a través de MRTK porque creemos que es la mejor manera de desarrollar en nuestra plataforma. 

### <a name="modular"></a>Modular
Hemos creado, de manera modular, por lo que no es necesario tener cada bit del Kit de herramientas en el proyecto.  Existen realmente algunas ventajas a este.  Mantiene el tamaño del proyecto más pequeños, así como hace que sea más fácil de administrar.  En él, porque se ha creado teniendo objetos programables y está controlada de interfaz, también es posible para reemplazar los componentes que se incluyen con su propio para admitir otros servicios, sistemas y plataformas.


### <a name="cross-platform"></a>Multiplataforma
Hablando de otras plataformas, tiene la compatibilidad multiplataforma.  Y aunque esto no significa que todas las plataformas solo es compatible de fábrica, nos hemos asegurado de que ninguno de los códigos de Kit de herramientas se interrumpirá cuando cambie su destino de compilación para otras plataformas.  La solidez y la extensibilidad con el diseño modular configura en una ruta de acceso válida para poder admitir varias plataformas, como ARCore, ARKit y OpenVR.


### <a name="performant"></a>Alto rendimiento
Trabajar con las plataformas móviles, se construyó con miras al rendimiento.  Esto es muy importante, y deseamos asegurarnos de que las herramientas no se van a funcionar en su contra.


## <a name="see-also"></a>Vea también
* [Instalar las herramientas](install-the-tools.md)
* [Portabilidad de HTK/MRTK a MRTK versión 2](mrtk-porting-guide.md)
