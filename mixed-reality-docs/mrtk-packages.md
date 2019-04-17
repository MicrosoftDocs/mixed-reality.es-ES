---
title: Paquetes MRTK
description: En este artículo describe los paquetes que componen el Toollkit de realidad mixta de Microsoft.
author: davidkline-ms
ms.author: davidkl
ms.date: 02/12/19
ms.topic: article
keywords: Windows Mixed Reality, MRTK, componente, paquete
ms.openlocfilehash: 7e44d75e1c267cff0ba67dd86dabfaa51bce659d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605692"
---
# <a name="mrtk-packages"></a>Paquetes MRTK

El Kit de herramientas de realidad mixta (MRTK) es una colección de paquetes que permiten el desarrollo de aplicaciones de realidad mixta multiplataforma al proporcionar soporte para el hardware de realidad mixta y plataformas de manera formada por componentes.

Hay tres categorías de paquetes MRTK: 

* [Foundation](#foundation-packages)
* [Extensión](#extension-packages)
* [Experimental](#experimental-packages)

## <a name="foundation-packages"></a>Paquetes de Windows Foundation

La base de Kit de herramientas de realidad mixta es el conjunto de paquetes que se habilite la aplicación para aprovechar la funcionalidad común entre plataformas de realidad mixta. Estos paquetes se libera y compatible con Microsoft desde el código fuente en el [mrtk_release](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release) bifurcación en GitHub.

![MRTK Foundation paquetes](images/mrtk-foundation.jpg)

*Paquetes de Foundation del Kit de herramientas de realidad mixtos*

La base de MRTK consta de:

* [Core Package](#core-package)
* [Proveedores de plataformas](#platform-providers)
* [Servicios del sistema](#system-services)
* [Característica activos](#feature-assets)

Las siguientes secciones describen los tipos de paquetes en cada categoría.

### <a name="core-package"></a>Paquete de Core

El paquete principal es un _requiere_ componente y se toma como una dependencia por todos los paquetes MRTK foundation.

El paquete MRTK Core incluye:

* [Tipos comunes de las interfaces, clases y datos](#common-interfaces-clases-and-data-types)
* [Componente de escena MixedRealityToolkit](#mixedrealitytoolkit-scene-component)
* [Sombreador MRTK estándar](#mrtk-standard-shader)
* [Proveedor de entrada de Unity](#unity-input-provider)
* [Administración de paquetes](#package-management)

#### <a name="common-interfaces-classes-and-data-types"></a>Tipos comunes de las interfaces, clases y datos

El paquete principal de Kit de herramientas de realidad mixta contiene las definiciones para todas las interfaces comunes, las clases y tipos de datos que se usan por todos los demás componentes. Se recomienda encarecidamente que las aplicaciones tener acceso a componentes MRTK exclusivamente a través de las interfaces definidas para permitir el máximo nivel de compatibilidad entre plataformas.

#### <a name="mixedrealitytoolkit-scene-component"></a>Componente de escena MixedRealityToolkit

El componente de la escena MixedRealityToolkit es el Administrador de recursos único y centralizado para el Kit de herramientas de realidad mixta. Este componente carga y administra la duración de los módulos de plataforma y el servicio y proporciona recursos para los sistemas tener acceso a sus valores de configuración. 

#### <a name="mrtk-standard-shader"></a>Sombreador MRTK estándar

El sombreador estándar MRTK proporciona la base para prácticamente todos los materiales proporcionados por el MRTK. Este sombreador es extremadamente flexible y optimizado para la variedad de plataformas que admiten MRTK. Es _altamente_ recomienda materiales de la aplicación que utilice el sombreador MRTK estándar para un rendimiento óptimo.

#### <a name="unity-input-provider"></a>Proveedor de entrada de Unity

El proveedor de entrada de Unity proporciona acceso a los dispositivos de entrada común como dispositivos de juego, pantallas táctiles y un mouse espacial en 3D.

#### <a name="package-management"></a>Administración del paquete

_Próximamente_

El paquete principal de Kit de herramientas de realidad mixta proporciona compatibilidad para detectar y administrar la foundation opcional, extensión y paquetes MRTK experimentales.

### <a name="platform-providers"></a>Proveedores de plataformas

Los paquetes de proveedor de la plataforma MRTK son los componentes que habilitan la funcionalidad de plataforma y el Kit de herramientas de realidad mixta para hardware de realidad mixta de destino.

Plataformas compatibles incluyen:

* [Windows Mixed Reality](#windows-mixed-reality)
* [OpenVR](#openvr)
* [Voz de Windows](#windows-voice)

#### <a name="windows-mixed-reality"></a>Windows Mixed Reality

El paquete de Windows Mixed Reality proporciona compatibilidad para dispositivos de Microsoft HoloLens y Windows Mixed Reality envolventes. El paquete contiene compatibilidad de plataforma completa, incluidos:

* Mirada destinadas a
* Gestos
* Controladores de movimiento de realidad mixta de Windows
* Asignación espacial

#### <a name="openvr"></a>OpenVR

El paquete OpenVR proporciona compatibilidad con hardware y plataforma para dispositivos con la plataforma OpenVR.

#### <a name="windows-voice"></a>Voz de Windows

El paquete de voz de Windows proporciona compatibilidad para la funcionalidad de reconocimiento y el dictado de palabra clave en los dispositivos de Microsoft Windows 10.

### <a name="system-services"></a>Servicios del sistema

Servicios de plataforma principales se muestran en los paquetes de servicio de sistema. Estos paquetes contienen las implementaciones predeterminadas de Mixed Reality del Kit de herramientas de las interfaces de servicio de sistema, definidas en el [core](#core-package) paquete.

La base MRTK incluye los siguientes servicios del sistema:

* [Sistema de límite](#boundary-system)
* [Sistema de diagnóstico](#diagnostic-system)
* [Sistema de entrada](#input-system)
* [Sistema de reconocimiento espacial](#spatial-awareness-system)
* [Sistema Teleport](#teleport-system)

#### <a name="boundary-system"></a>Sistema de límite

El sistema de límite MRTK proporciona datos sobre la realidad virtual a playspace. En los sistemas para el que el usuario ha configurado el límite, el sistema puede proporcionar un plano floor, playspace rectangular, área sometidas a seguimiento y mucho más.

#### <a name="diagnostic-system"></a>Sistema de diagnóstico

El sistema de diagnóstico MRTK proporciona datos de rendimiento en tiempo real dentro de su experiencia de aplicación. En una vista, podrá ver la velocidad de fotogramas, tiempo de procesador y otras métricas de rendimiento clave que usa la aplicación.

#### <a name="input-system"></a>Sistema de entrada

Los sistemas de entrada MRTK permite que las aplicaciones tener acceso a la entrada de una manera multiplataforma especificando las acciones del usuario y asignar esas acciones a los botones más adecuados y ejes en los controladores de destino.

#### <a name="spatial-awareness-system"></a>Sistema de reconocimiento espacial

El sistema de reconocimiento MRTK espacial permite el acceso a datos del entorno del mundo real desde dispositivos, como el Microsoft HoloLens.

#### <a name="teleport-system"></a>Sistema Teleport

El sistema de Teleport MRTK proporciona compatibilidad de desplazamiento de realidad virtual.

### <a name="feature-assets"></a>Característica activos

Característica activos son colecciones de funcionalidad relacionada que se entregan como secuencias de comandos y activos de Unity. Algunas de estas características incluyen:

* Controles de interfaz de usuario
* Recursos estándar
* more

## <a name="extension-packages"></a>Paquetes de extensión

Los paquetes de extensión MRTK son una colección de paquetes por Microsoft y la Comunidad que amplían y mejoran la funcionalidad del Kit de herramientas de realidad mixta. Los autores de extensiones se las dependencias necesarias de estado, marcar el paquete como compatible con el Kit de herramientas de realidad mixta y proporcionar las licencias y admite las instrucciones.

Los paquetes de extensión pueden proporcionar las nuevas características y compatibilidad con la plataforma nueva. Con el tiempo, las extensiones, con la Ayuda y la aprobación de los autores, se pueden migrar a la base de MRTK en qué momento se libera y compatible con Microsoft.

![Paquete de extensión MRTK](images/mrtk-extensions.jpg)

*Paquetes de extensión del Kit de herramientas de realidad mixtos*

## <a name="experimental-packages"></a>Paquetes experimentales

Paquetes experimentales proporcionan la capacidad de las características de prototipo de vuelo, versiones preliminares y emocionantes nuevas ideas. El objetivo de los paquetes más experimentales es probar algo nuevo y para medir el interés del cliente. Muchos, aunque no todos los paquetes experimentales estarán vuelto a publicar como extensiones una vez completada la creación de prototipos y la fase de pruebas.

![Paquetes Experimental MRTK](images/mrtk-experimental.jpg)

*Paquetes Experimental del Kit de herramientas de realidad mixtos*

## <a name="conclusion"></a>Conclusión

Los paquetes de Kit de herramientas de realidad mixta y el sistema de administración de paquetes están diseñados para habilitar un método simple y limpio para que pueda crear aditivamente características en sus experiencias sin necesidad de componentes innecesarios que se incluirán en el proyecto.

Con el tiempo, se agregará compatibilidad con administración de paquetes y mejorado en el Kit de herramientas de realidad mixta. Si tiene comentarios o desea participar, visite la [proyecto del Kit de herramientas de realidad mixta](https://github.com/Microsoft/MixedRealityToolkit-Unity) en GitHub. 

## <a name="see-also"></a>Vea también

* [MixedRealityToolkit-Unity (GitHub)](https://github.com/Microsoft/MixedRealityToolkit-Unity)

