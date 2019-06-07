---
title: Uso de Vuforia con Unity
description: Aproveche Vuforia para compilar aplicaciones de Windows Mixed Reality en Unity.
author: ailyadis
ms.author: ''
ms.date: 01/28/2019
ms.topic: article
keywords: Vuforia, marcadores, las coordenadas, marco de referencia, seguimiento
ms.openlocfilehash: c0d2f6d0707e1ddd3ee00d3eb80af9fb459f252b
ms.sourcegitcommit: c2a5bff423feba7d29d5431c870b6017c2fe1bc2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2019
ms.locfileid: "66750351"
---
# <a name="using-vuforia-engine-with-unity"></a>Usar motor Vuforia con Unity

Vuforia motor aporta una capacidad importante a HoloLens: la posibilidad de conectar AR experiencias a imágenes específicas y objetos en el entorno. Puede usar esta capacidad para superponer guiadas instrucciones paso a paso sobre las máquinas para la empresa industrial o agregar características digitales y las experiencias de un producto físico o el juego. 

Para una mayor flexibilidad al desarrollar AR experiencias, Vuforia motor ofrece una amplia gama de características y destinos. Una de nuestras características más recientes, Vuforia destinos del modelo, es una capacidad clave para usos comerciales e industriales. Modelo destinos permiten a las aplicaciones reconocer objetos físicos como máquinas, automóviles o juguetes y realizar un seguimiento de ellos según un CAD o digital modelo 3D. Para usos industriales, esta característica puede proporcionar a los trabajadores de ensamblado y técnicos de servicio con AR trabajan las instrucciones y procedimientos necesarios, mientras que en la fábrica o out en el campo. 

Las aplicaciones de motor Vuforia existentes que se crearon para teléfonos y tabletas pueden configurarse fácilmente en Unity se ejecuta en HoloLens. Incluso puede usar el motor Vuforia para aprovechar la nueva aplicación de HoloLens para tabletas de Windows 10 como el 4 de Surface Pro y Surface Book.

## <a name="get-the-tools"></a>Conseguir las herramientas

[Instalar las versiones recomendadas](install-the-tools.md) de Visual Studio y Unity y, a continuación, configurar Unity para usar Visual Studio y el IDE preferido y el compilador. 

Al instalar Unity, asegúrese de instalar el "Windows Store .NET Scripting back-end" o "Windows Store IL2CPP Scripting back-end". Además, no olvide seleccionar "Vuforia soporte realidad aumentada" para habilitar Vuforia motor Unity.


## <a name="getting-started-with-vuforia-engine"></a>Introducción al motor Vuforia

Puesto que el motor de Vuforia está integrado en Unity, los desarrolladores no tienen que descargar ni instalar ninguna herramienta adicional. La versión recomendada de Unity es la secuencia LTS que está actualmente en 2017.3 e incluye el motor de Vuforia 7.0.57. El mejor punto de partida para aprender sobre el uso de motor Vuforia con HoloLens es con el [Vuforia motor HoloLens ejemplo](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) (disponible en el Store de activos de Unity). El ejemplo proporciona un proyecto de HoloLens completo incluido escenas preconfigurados que se pueden implementar en un HoloLens.

Segundo plano muestra cómo usar destinos de imagen Vuforia para reconocer una imagen y aumentarlo con contenido digital en una experiencia de HoloLens. Los desarrolladores que utilizan versiones más recientes de Unity y Vuforia tienen acceso a ejemplos actualizados que incluir una escena que muestra el uso de destinos de modelo en HoloLens. Puede sustituir fácilmente su propio contenido en segundo plano para experimentar con la creación de aplicaciones de HoloLens que usan el motor Vuforia.


## <a name="configuring-a-vuforia-app-for-hololens"></a>Configuración de una aplicación Vuforia para HoloLens

Desarrollar una aplicación de motor de Vuforia para HoloLens es fundamentalmente igual a desarrollo de aplicaciones de motor Vuforia para otros dispositivos. A continuación, puede aplicar la configuración de compilación y configuraciones que se describen en la sección siguiente. Eso es todo lo necesario para permitir que motor Vuforia funcionan con la asignación espacial HoloLens y posición de los sistemas de seguimiento.

## <a name="build-and-run-the-vuforia-engine-sample-for-hololens"></a>Compilar y ejecutar el ejemplo motor Vuforia para HoloLens
1.  Descargue el [ejemplo motor Vuforia para HoloLens](https://assetstore.unity.com/packages/templates/packs/vuforia-hololens-sample-101553) desde el Store de activos de Unity
2.  Aplicar el [las opciones de motor de Unity para la potencia y rendimiento recomendadas](performance-recommendations-for-unity.md)
3.  Agregue el segundo plano de ejemplo para escenas en compilación.
4.  Establecer la plataforma de destino de compilación para "Plataforma Universal de Windows" en archivo > configuración de compilación.
5.  Seleccione las siguientes opciones de configuración de compilación de plataforma: 
   * Dispositivo de destino = HoloLens
   * Tipo de compilación = D3D
   * SDK = la versión más reciente instalada
   * Versión de Visual Studio = la versión más reciente instalada
   * Compilar y ejecutar on = máquina Local
6.  Definir un único **Product Name**, en **configuración del Reproductor**, para que actúe como el nombre de la aplicación cuando se instala en el HoloLens.
7.  Comprobar **Vuforia aumentada realidad** y **de realidad Virtual admitida** en **configuración del Reproductor > configuración XR**
8.  También en **XR configuración**, asegúrese de que "Windows Mixed Reality" se agrega a la **SDK de realidad Virtual** lista
9.  Compruebe las siguientes capacidades de configuración del Reproductor > configuración de publicación 
   * InternetClient
   * WebCam
   * SpatialPerception - si va a usar la API de observador de superficie
10. Seleccione la compilación para generar un proyecto de Visual Studio
11. Compile el archivo ejecutable desde Visual Studio e instálelo en su HoloLens

Nota: Comenzando con la versión 7.2, el ejemplo de motor de Vuforia para HoloLens incluye una escena de ejemplo como ejemplo de uso de destinos de modelo

## <a name="the-vuforia-developer-portal"></a>El Portal para desarrolladores de Vuforia

Los desarrolladores que desean para crear sus propias cuentas por cobrar experiencias con motor Vuforia y HoloLens deberían registrarse en nuestro Portal para desarrolladores de Vuforia en [developer.vuforia.com](https://developer.vuforia.com/). En el portal, los desarrolladores tienen acceso a la [Vuforia motor foros](https://developer.vuforia.com/forum) donde puede participar en discusiones de la Comunidad, un [biblioteca](https://library.vuforia.com/) con la documentación detallada sobre todas las características del motor de Vuforia y el [ Vuforia destino Manager](https://developer.vuforia.com/target-manager) donde los usuarios pueden crear sus propios destinos personalizados. Los desarrolladores también pueden registrarse para un uso de licencia de desarrollador gratuita el [Vuforia License Manager](https://developer.vuforia.com/license-manager).

## <a name="extended-tracking-with-vuforia"></a>Seguimiento extendido con Vuforia

[Seguimiento extendido](https://library.vuforia.com/articles/Training/Extended-Tracking) crea un mapa del entorno para mantener el seguimiento incluso cuando un destino ya no está en la vista. Es equivalente de los motores Vuforia para la asignación espacial realizada por HoloLens. Al habilitar seguimiento extendido en un destino, habilite la postura de pasarse al sistema de asignación espacial que tienen como destino. De esta manera, los destinos pueden existir en el motor de Vuforia y HoloLens sistemas de coordenadas espaciales, aunque no de forma simultánea.

![Ventana de configuración de Unity](images/vuforia-extendedtracking.png)<br>
*Ventana de configuración de Unity*

**Habilitar seguimiento extendido en un destino**

Vuforia motor transformará automáticamente la postura de un destino que usa el seguimiento extendido en el sistema de coordenadas espacial HoloLens. Esto permite HoloLens para tomar el control de seguimiento y para integrar el contenido de cualquier aumento en la asignación espacial de su entorno de destino. Este proceso tiene lugar entre el motor de Vuforia y realidad mixta las API de Unity y no requiere ninguna programación por el desarrollador: se administra automáticamente.

**Aquí está lo que ocurre...**
1. Destino del Vuforia Tracker reconoce el destino
2. A continuación, se inicializa el destino de seguimiento
3. La posición y giro de destino se analizan para proporcionar una estimación de la postura sólida de HoloLens usar
4. Vuforia transforma la postura del destino en el espacio de coordenadas de HoloLens asignación espacial
5. HoloLens se ocupa de seguimiento y se desactiva el seguimiento de Vuforia

El desarrollador puede controlar este proceso, para devolver el control al Vuforia, al deshabilitar el seguimiento extendido en la TargetBehaviour.

**NOTA:** A partir de Vuforia 7.2, extendido seguimiento dejaría de estar habilitada en una base por destino. En su lugar, los desarrolladores pueden activar el seguimiento de dispositivos para habilitar una funcionalidad similar en todos los destinos de la escena.


## <a name="see-also"></a>Vea también
* [Instalación de las herramientas](install-the-tools.md)
* [Sistemas de coordenadas](coordinate-systems.md)
* [Asignación espacial](spatial-mapping.md)
* [Cámara en Unity](camera-in-unity.md)
* [Exportación y creación de una solución de Visual Studio para Unity](exporting-and-building-a-unity-visual-studio-solution.md)
* [Vuforia documentación: Desarrollar para Windows 10 en Unity](https://library.vuforia.com/articles/Solution/Developing-for-Windows-10-in-Unity)
* [Vuforia documentación: Cómo instalar la extensión de Vuforia Unity](https://library.vuforia.com/articles/Solution/Installing-the-Unity-Extension)
* [Vuforia documentación: Trabajar con el ejemplo de HoloLens en Unity](https://library.vuforia.com/articles/Solution/Working-with-the-HoloLens-sample-in-Unity)
* [Vuforia documentación: Seguimiento extendido en Vuforia](https://library.vuforia.com/articles/Training/Extended-Tracking)
