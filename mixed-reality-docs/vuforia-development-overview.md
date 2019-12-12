---
title: Uso de Vuforia con Unity
description: Aproveche Vuforia para compilar aplicaciones de Windows Mixed Reality en Unity.
author: thetuvix
ms.author: alexturn
ms.date: 01/28/2019
ms.topic: article
keywords: Vuforia, marcadores, coordenadas, marco de referencia, seguimiento
ms.openlocfilehash: bae5d0eb04ab9434dd3e72674686743779a8f70c
ms.sourcegitcommit: 9005b3fdfa87ac8fdc18a594a681e25c00ac5ce1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/11/2019
ms.locfileid: "75003194"
---
# <a name="using-vuforia-engine-with-unity"></a>Uso del motor Vuforia con Unity

El motor de Vuforia ofrece una funcionalidad importante para HoloLens: la capacidad de conectar experiencias de AR a imágenes y objetos específicos del entorno. Puede usar esta capacidad para superponer instrucciones paso a paso guiadas sobre maquinaria para la empresa industrial o para agregar características y experiencias digitales a un producto o juego físico.

Para una mayor flexibilidad a la hora de desarrollar experiencias de AR, el motor de Vuforia ofrece una amplia gama de características y destinos. Una de nuestras características más recientes, objetivos del modelo Vuforia, es una capacidad clave para los usos comerciales y industriales. Los destinos de modelo permiten a las aplicaciones reconocer objetos físicos, como máquinas, automóviles o juguetes, y realizar un seguimiento de ellos en función de un modelo 3D de CAD o digital. En el caso de los usos industriales, esta característica puede proporcionar a los trabajadores de ensamblados y a los técnicos de servicios las instrucciones de trabajo de AR y la guía de procedimientos en la fábrica o en el campo.

Las aplicaciones de Vuforia Engine existentes que se compilaron para teléfonos y tabletas se pueden configurar fácilmente en Unity para que se ejecuten en HoloLens. Incluso puede usar el motor Vuforia para realizar la nueva aplicación de HoloLens en tabletas con Windows 10, como el libro de Surface Pro y Surface.


## <a name="get-the-tools"></a>取得工具

[Instale las versiones recomendadas](install-the-tools.md) de Visual Studio y Unity y, después, configure Unity para usar Visual Studio y el IDE y el compilador preferidos. 

Al instalar Unity, asegúrese de instalar el "back-end de scripting de la tienda Windows IL2CPP".

La adición de compatibilidad con el motor de Vuforia funciona de forma diferente en función de la versión de Unity:
*   Unity 2018,4: descargar el instalador del motor de Vuforia para Unity 2018,4 del portal para desarrolladores de Vuforia
*   Unity 2019,2: obtener el [paquete del motor de Vuforia](https://library.vuforia.com/content/vuforia-library/en/articles/Solution/vuforia-engine-package-hosting-for-unity.html) más reciente 

## <a name="getting-started-with-vuforia-engine"></a>Introducción al motor de Vuforia

El mejor punto de partida para aprender a usar el motor de Vuforia con HoloLens es el [ejemplo de hololens del motor de Vuforia](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) (disponible en el almacén de recursos de Unity). El ejemplo proporciona un proyecto de HoloLens completo que incluye escenas preconfiguradas que se pueden implementar en HoloLens.

Las escenas muestran cómo usar los destinos de imagen de Vuforia para reconocer una imagen y aumentarla con contenido digital en una experiencia de HoloLens. El ejemplo de Hololens del motor de Vuforia también incluye una escena que muestra el uso de los destinos del modelo y VuMarks en HoloLens. Puede sustituir fácilmente su propio contenido en segundo plano para experimentar con la creación de aplicaciones de HoloLens que usan el motor de Vuforia.



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

Los desarrolladores que quieran crear sus propias experiencias de AR con el motor de Vuforia y HoloLens deben registrarse en nuestro portal para desarrolladores de Vuforia en [Developer.Vuforia.com](https://developer.vuforia.com/). En el portal, los desarrolladores tienen acceso a los [foros del motor de Vuforia](https://developer.vuforia.com/forum) , donde pueden unirse a discusiones de la comunidad, una [biblioteca](https://library.vuforia.com/) con documentación detallada sobre todas las características del motor de Vuforia y el administrador de [destino de Vuforia](https://developer.vuforia.com/target-manager) , donde los usuarios pueden crear sus propios destinos personalizados. Los desarrolladores también pueden registrarse para obtener una licencia de desarrollador gratuita mediante el [Administrador de licencias de Vuforia](https://developer.vuforia.com/license-manager).

## <a name="extended-tracking-with-vuforia"></a>Seguimiento extendido con Vuforia

El [seguimiento extendido](https://library.vuforia.com/articles/Training/Extended-Tracking) mantiene el seguimiento incluso cuando un destino ya no está en la vista. Se habilita automáticamente para todos los destinos cuando está habilitado el seguimiento de dispositivos posicionales. En el caso de las aplicaciones de HoloLens, el seguimiento de dispositivos posicionales se inicia automáticamente en Unity.

El motor de Vuforia funde automáticamente las supuestos del seguimiento de la cámara y el seguimiento espacial de HoloLens para proporcionar un objetivo estable con independencia de si el destino es visible o no en la cámara.

Dado que el proceso se controla automáticamente, no requiere que el desarrollador programe ninguna programación.


**Esto es lo que sucede...**
1. El rastreador de destino de Vuforia reconoce el destino
2. A continuación, se inicializa el seguimiento de destino
3. La posición y la rotación del destino se analizan para proporcionar una estimación de postura sólida para HoloLens
4. El motor de Vuforia transforma la postura del destino en el espacio de coordenadas de asignación espacial de HoloLens
5. HoloLens realiza el seguimiento si el destino ya no está en la vista. Siempre que vuelva a mirar el destino, Vuforia continuará realizando el seguimiento de las imágenes y los objetos con precisión.

Los destinos que se detectan, pero que ya no están en la vista, se muestran como EXTENDED_TRACKED. En estos casos, el script DefaultTrackableEventHandler que se usa en todos los destinos continúa representando el contenido de aumento. El desarrollador puede controlar este comportamiento implementando un script de controlador de eventos de seguimiento personalizado.


## <a name="performance-mode-with-vuforia-engine"></a>Modo de rendimiento con el motor de Vuforia 

Es posible a través del motor de Vuforia administrar el rendimiento de HoloLens para las experiencias de AR y reducir la carga de trabajo en la CPU. El motor de Vuforia ofrece tres modos que se pueden seleccionar: predeterminado, para optimizar la velocidad y para optimizar la calidad. 

*   MODE_OPTIMIZE_SPEED le permite minimizar la carga de trabajo en el dispositivo HoloLens y es ideal para ampliar las experiencias de AR. Se recomienda en situaciones en las que la aplicación realiza el seguimiento de objetos o destinos estáticos.
*   MODE_DEFAULT es el modo normal que se puede usar en la mayoría de los escenarios.
*   MODE_OPTIMIZE_QUALITY es mejor para realizar un seguimiento de los destinos móviles o los destinos de modelo que espera que se recojan.

**Establecer el modo**

Para cambiar el modo de rendimiento en Unity, vaya a configuración de Vuforia (Ctrl + Mayús + V/Cmd + Mayús + V) que se encuentra como componente en el GameObject de ARCamera. 
*   Seleccione el menú desplegable para el modo de dispositivo de cámara y seleccione una de las tres opciones.


## <a name="see-also"></a>請參閱
* [Instalación de las herramientas](install-the-tools.md)
* [Sistemas de coordenadas](coordinate-systems.md)
* [Asignación espacial](spatial-mapping.md)
* [Cámara en Unity](camera-in-unity.md)
* [Exportación y creación de una solución de Visual Studio para Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Documentación de Vuforia: desarrollo para Windows 10 en Unity](https://library.vuforia.com/articles/Solution/Developing-for-Windows-10-in-Unity)
* [Documentación de Vuforia: instalación de la extensión Vuforia Unity](https://library.vuforia.com/articles/Solution/Installing-the-Unity-Extension)
* [Documentación de Vuforia: trabajar con el ejemplo de HoloLens en Unity](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity)
* [Documentación de Vuforia: seguimiento extendido en Vuforia](https://library.vuforia.com/articles/Training/Extended-Tracking)
