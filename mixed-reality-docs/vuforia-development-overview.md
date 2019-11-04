---
title: Uso de Vuforia con Unity
description: Aproveche Vuforia para compilar aplicaciones de Windows Mixed Reality en Unity.
author: thetuvix
ms.author: alexturn
ms.date: 01/28/2019
ms.topic: article
keywords: Vuforia, marcadores, coordenadas, marco de referencia, seguimiento
ms.openlocfilehash: 0ab87a6262cbe74fd116fdc0a7045961bf8695d9
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437141"
---
# <a name="using-vuforia-engine-with-unity"></a>Uso del motor Vuforia con Unity

El motor de Vuforia ofrece una funcionalidad importante para HoloLens: la capacidad de conectar experiencias de AR a imágenes y objetos específicos del entorno. Puede usar esta capacidad para superponer instrucciones paso a paso guiadas sobre maquinaria para la empresa industrial o para agregar características y experiencias digitales a un producto o juego físico. 

Para una mayor flexibilidad a la hora de desarrollar experiencias de AR, el motor de Vuforia ofrece una amplia gama de características y destinos. Una de nuestras características más recientes, objetivos del modelo Vuforia, es una capacidad clave para los usos comerciales y industriales. Los destinos de modelo permiten a las aplicaciones reconocer objetos físicos, como máquinas, automóviles o juguetes, y realizar un seguimiento de ellos en función de un modelo 3D de CAD o digital. En el caso de los usos industriales, esta característica puede proporcionar a los trabajadores de ensamblados y a los técnicos de servicios las instrucciones de trabajo de AR y la guía de procedimientos en la fábrica o en el campo. 

Las aplicaciones de Vuforia Engine existentes que se compilaron para teléfonos y tabletas se pueden configurar fácilmente en Unity para que se ejecuten en HoloLens. Incluso puede usar el motor Vuforia para realizar la nueva aplicación de HoloLens en tabletas con Windows 10, como Surface Pro 4 y Surface Book.

## <a name="get-the-tools"></a>Conseguir las herramientas

[Instale las versiones recomendadas](install-the-tools.md) de Visual Studio y Unity y, después, configure Unity para usar Visual Studio y el IDE y el compilador preferidos. 

Al instalar Unity, asegúrese de instalar el "backend de scripting .NET de la tienda Windows" o el "back-end de scripting de IL2CPP de la tienda Windows". Además, asegúrese de seleccionar "Vuforia de realidad aumentada" para habilitar el motor de Vuforia en Unity.


## <a name="getting-started-with-vuforia-engine"></a>Introducción al motor de Vuforia

Dado que el motor de Vuforia está integrado en Unity, los desarrolladores no necesitan descargar ni instalar ninguna herramienta adicional. La versión recomendada de Unity es la secuencia LTS que está actualmente en 2017,3 e incluye Vuforia Engine 7.0.57. El mejor punto de partida para aprender a usar el motor de Vuforia con HoloLens es el [ejemplo de hololens del motor de Vuforia](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) (disponible en el almacén de recursos de Unity). El ejemplo proporciona un proyecto de HoloLens completo que incluye escenas preconfiguradas que se pueden implementar en HoloLens.

Las escenas muestran cómo usar los destinos de imagen de Vuforia para reconocer una imagen y aumentarla con contenido digital en una experiencia de HoloLens. Los desarrolladores que usan versiones más recientes de Unity y Vuforia tienen acceso a los ejemplos actualizados que incluyen una escena que muestra el uso de los destinos del modelo en HoloLens. Puede sustituir fácilmente su propio contenido en segundo plano para experimentar con la creación de aplicaciones de HoloLens que usan el motor de Vuforia.


## <a name="configuring-a-vuforia-app-for-hololens"></a>Configuración de una aplicación de Vuforia para HoloLens

El desarrollo de una aplicación de motor de Vuforia para HoloLens es fundamentalmente el mismo que el desarrollo de aplicaciones de motor de Vuforia para otros dispositivos. Después, puede aplicar la configuración de compilación y las configuraciones que se describen en la sección siguiente. Eso es todo lo que se necesita para permitir que el motor de Vuforia funcione con la asignación espacial de HoloLens y los sistemas de seguimiento posicional.

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>Compilación y ejecución del ejemplo de Vuforia Engine para HoloLens
1.  Descargar el [ejemplo de Vuforia Engine para HoloLens](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) del almacén de recursos de Unity
2.  Aplicar las [Opciones de motor de Unity recomendadas para potencia y rendimiento](performance-recommendations-for-unity.md)
3.  Agregue escenas de ejemplo a escenas en la compilación.
4.  Establezca el destino de compilación de la plataforma para "Plataforma universal de Windows" en la configuración de compilación de > de archivo.
5.  Seleccione las siguientes opciones de configuración de compilación de plataforma: 
   * Dispositivo de destino = HoloLens
   * Tipo de compilación = D3D
   * SDK = última versión instalada
   * Versión de Visual Studio = instalada más reciente
   * Compilar y ejecutar en = equipo local
6.  Defina un **nombre de producto**único, en **configuración del reproductor**, para que sirva como el nombre de la aplicación cuando esté instalado en HoloLens.
7.  Compruebe la **realidad aumentada de Vuforia** y la **realidad virtual compatible** con la **configuración del reproductor > configuración de XR**
8.  También en la **configuración de XR**, asegúrese de que "Windows Mixed Reality" se agrega a la lista de SDK de **realidad virtual** .
9.  Compruebe las siguientes funcionalidades en configuración del reproductor > configuración de publicación. 
   * InternetClient
   * Web
   * SpatialPerception: Si tiene previsto usar la API de observador de Surface
10. Seleccione compilar para generar un proyecto de Visual Studio
11. Compilar el archivo ejecutable desde Visual Studio e instalarlo en HoloLens

Nota: a partir de la versión 7,2, el ejemplo de Vuforia Engine para HoloLens incluye una escena de ejemplo que incluye el uso de ejemplo de destinos de modelo.

## <a name="the-vuforia-developer-portal"></a>Portal para desarrolladores de Vuforia

Los desarrolladores que quieran crear sus propias experiencias de AR con el motor de Vuforia y HoloLens deben registrarse en nuestro portal para desarrolladores de Vuforia en [Developer.Vuforia.com](https://developer.vuforia.com/). En el portal, los desarrolladores tienen acceso a los [foros del motor de Vuforia](https://developer.vuforia.com/forum) , donde pueden unirse a discusiones de la comunidad, una [biblioteca](https://library.vuforia.com/) con documentación detallada sobre todas las características del motor de Vuforia y el administrador de [destino de Vuforia](https://developer.vuforia.com/target-manager) , donde los usuarios pueden Cree sus propios destinos personalizados. Los desarrolladores también pueden registrarse para obtener una licencia de desarrollador gratuita mediante el [Administrador de licencias de Vuforia](https://developer.vuforia.com/license-manager).

## <a name="extended-tracking-with-vuforia"></a>Seguimiento extendido con Vuforia

El [seguimiento extendido](https://library.vuforia.com/articles/Training/Extended-Tracking) crea un mapa del entorno para mantener el seguimiento incluso cuando un destino ya no está en la vista. Es equivalente de los motores de Vuforia a la asignación espacial realizada por HoloLens. Al habilitar el seguimiento extendido en un destino, se habilita la suposición de ese destino para pasarlo al sistema de asignación espacial. De esta manera, los destinos pueden existir en el motor de Vuforia y en los sistemas de coordenadas espaciales de HoloLens, aunque no simultáneamente.

![ventana de configuración de Unity](images/vuforia-extendedtracking.png)<br>
*Ventana de configuración de Unity*

**Habilitar el seguimiento extendido en un destino**

El motor de Vuforia transformará automáticamente la suposición de un destino que utiliza el seguimiento extendido en el sistema de coordenadas espaciales de HoloLens. Esto permite que HoloLens asuma un seguimiento e integre cualquier contenido que aumente en la asignación espacial del entorno del destino. Este proceso se produce entre el motor de Vuforia y las API de realidad mixta en Unity y no requiere que el desarrollador realice ninguna programación, sino que se administra automáticamente.

**Esto es lo que sucede...**
1. El rastreador de destino de Vuforia reconoce el destino
2. A continuación, se inicializa el seguimiento de destino
3. La posición y la rotación del destino se analizan para proporcionar una estimación de postura sólida para que HoloLens lo use
4. Vuforia transforma el replanteamiento del destino en el espacio de coordenadas de asignación espacial de HoloLens
5. HoloLens realiza el seguimiento y se desactiva el Vuforia Tracker

El desarrollador puede controlar este proceso, para devolver el control a Vuforia, deshabilitando el seguimiento extendido en el TargetBehaviour.

**Nota:** A partir de Vuforia 7,2, el seguimiento extendido ya no se habilita para cada destino. En su lugar, los desarrolladores pueden activar el seguimiento de los dispositivos para habilitar una funcionalidad similar en todos los destinos de la escena.


## <a name="see-also"></a>Consulta también
* [Instalación de las herramientas](install-the-tools.md)
* [Sistemas de coordenadas](coordinate-systems.md)
* [Asignación espacial](spatial-mapping.md)
* [Cámara en Unity](camera-in-unity.md)
* [Exportación y creación de una solución de Visual Studio para Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Documentación de Vuforia: desarrollo para Windows 10 en Unity](https://library.vuforia.com/articles/Solution/Developing-for-Windows-10-in-Unity)
* [Documentación de Vuforia: instalación de la extensión Vuforia Unity](https://library.vuforia.com/articles/Solution/Installing-the-Unity-Extension)
* [Documentación de Vuforia: trabajar con el ejemplo de HoloLens en Unity](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity)
* [Documentación de Vuforia: seguimiento extendido en Vuforia](https://library.vuforia.com/articles/Training/Extended-Tracking)
