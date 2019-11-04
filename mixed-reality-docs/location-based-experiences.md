---
title: Entretenimiento basado en la ubicación con Windows Mixed Reality
description: Obtenga acceso a los objetos nativos holográficas subyacentes en Unity.
author: jessemcculloch
ms.author: ishitak
ms.date: 08/22/2019
ms.topic: article
keywords: realidad mixta, VR, LBE, ubicación
ms.openlocfilehash: de9cfdaca77574bbbbec96c2e94fddeaa2712c33
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437932"
---
# <a name="location-based-entertainment-with-windows-mixed-reality"></a>Entretenimiento basado en la ubicación con Windows Mixed Reality

En el último par de años, hemos testigo una cantidad increíble de crecimiento e innovación en la categoría de ocio basada en la ubicación. Los lugares tradicionales, como los parques de tema y los quirófanos, han empezado a ofrecer experiencias envolventes y multijugador como experiencias gratuitas en los viajes e instalaciones existentes. Los nuevos operadores y lugares aportan experiencias únicas de varios jugadores y multisensorial a un precio atractivo para las masas. Todas estas experiencias están empujando el sobre en lo que es posible con la realidad mixta.

Este documento es una guía para empezar a trabajar con Windows Mixed Reality en la categoría de entretenimiento basada en la ubicación. Las instrucciones siguientes pueden aplicarse además a experiencias basadas en la ubicación más allá del entretenimiento, como el entrenamiento, el diseño del producto u otros casos de uso.

## <a name="engineering-faq"></a>Preguntas más frecuentes sobre ingeniería

### <a name="hardware"></a>Hardware

**P: ¿Qué hardware está disponible en Microsoft y sus asociados que puedo usar en mi instalación?**

R: Microsoft y sus asociados OEM ofrecen una amplia cartera de dispositivos para elegir en función de sus necesidades.  

Si las experiencias que va a proporcionar a sus clientes requieren auriculares de realidad virtual, los siguientes auriculares en el mercado de HP, Samsung y Acer son una buena opción. Cada casco tiene sus propios atributos diferenciados. Más información sobre cada uno de ellos.

HP reverberación: [detalles](https://hp.com/go/Reverbpro)

Samsung Odyssey +: [detalles](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)

Acer: [detalles](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)

Si su ubicación se especializa en experiencias de realidad mixtas o aumentadas que requieren el uso de un casco de un See, puede adquirir Microsoft HoloLens 2 (ahora abierto para el interés por preorden).  

HoloLens 2: [interés previo al pedido](https://www.microsoft.com//hololens/buy)

Si está experimentando con experiencias que requieren visión avanzada de equipos, voz y seguimiento de cuerpos, es posible que encuentre el Kinect de Azure de la parte DK que mejor se adapte a sus necesidades.  

Azure Kinect: [detalles](https://azure.microsoft.com//services/kinect-dk/)

**P: ¿Cuál es la cartera de equipos Backpack que puedo usar para ejecutar las experiencias de VR con tethering PC?**

En el caso de las experiencias de VR con tethering de PC, nuestros OEM ofrecen una increíble selección de equipos de mochila creados exactamente para esa necesidad.

HP acaba de lanzar su mochila de HP VR de la versión G2, el equipo portátil más eficaz del mundo, optimizado para experiencias de movilidad gratuita, ahora con un 30% más de energía con una GPU de RTX 2080 dentro de. [Detalles](https://www8.hp.com/us/en/vr/vr-backpack.html)

### <a name="setup"></a>Configuración

**P: ¿Cómo puedo configurar más fácilmente el programa de instalación y personalizar el portal de realidad mixta para LBE?**

>[!NOTE]
>Esta característica requiere la versión 2000.19061.1011.0 o posterior.  

Es posible que necesite más personalización del portal de realidad mixta que normalmente está disponible a través de la aplicación para la implementación de aplicaciones en quioscos o experiencias personalizadas. La actualización más reciente de julio del portal de realidad mixta admite varias opciones de configuración avanzadas que pueden ser a través de un archivo de configuración para hacer lo siguiente:  

Permitir comprobaciones del sistema con error: normalmente, el proceso de instalación comprueba si el equipo es compatible con Windows Mixed Reality antes de completar la instalación. Si se omite esto, se pueden producir problemas al intentar ejecutar Windows Mixed Reality si hay problemas de compatibilidad.  

Omitir aplicación complementaria de dispositivo: el DCA proporciona pasos de configuración específicos del casco que proporciona el fabricante y permite actualizar el firmware del casco.  

Omitir configuración de la habitación: en lugar de que se le pida que cree un límite de habitación, puede continuar directamente con el casco en el modo sentado/permanente.  

Omitir la instalación de aplicaciones desde la tienda: el programa de instalación normal instala varias aplicaciones de la tienda, como el visor 3D y el complemento Edge 360 Viewer. Se omitirá la instalación de estas aplicaciones, pero es posible que falte funcionalidad de dispositivo.  

Mostrar vista previa en pantalla completa: el portal de realidad mixta mostrará de forma predeterminada la vista previa del casco en la pantalla completa en el equipo de escritorio mientras el casco está en uso.  

Ocultar nuevo en el panel lateral: no se puede ampliar el panel nuevo en el inicio del portal de realidad mixta.  

#### <a name="how-to-configure"></a>Cómo configurar:  

Para establecer cualquiera de estas configuraciones, debe crear un archivo denominado _userconfig. JSON_ en este directorio: _$env: LOCALAPPDATA\Packages\Microsoft.MixedReality.Portal_8wekyb3d8bbwe\LocalState\\_

Para la mayoría de los usuarios, tendrá un aspecto como _C:\Users\<nombredeusuario > \AppData\Local\Packages\microsoft.mixedreality.portal_8wekyb3d8bbwe\LocalState\\_

El archivo JSON debe tener el siguiente contenido con el valor "true" establecido para cualquiera de las opciones anteriores que desee habilitar:  

```
{

  "shouldAllowFailedSystemChecks": true,

  "shouldSkipDcaApp": true,

  "shouldSkipRoomSetup": true,

  "shouldSkipStoreAppInstall": true,

  "shouldShowPreviewFullScreen": true,

  "shouldHideEngagementPane": true

}
```
 
**P: ¿hay alguna orientación sobre la configuración de Playspace?**

R: la configuración de un Playspace debe realizarse tal como lo haría con una experiencia de instalación del consumidor. El proceso de configuración del salón también le permitirá definir los límites de la habitación. Puede leer [aquí](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)más detalles sobre la configuración de los límites de la habitación.

Como se explicó en el documento anterior, el Playspace de coordenada única razonable máximo está alrededor de 5mx5m. Si desea tener un área más grande, puede usar la funcionalidad de anclajes espaciales en la pila de la API de Windows Holographic. El uso de esta API requerirá ingeniería personalizada en las experiencias que está generando.  

Puede leer [aquí](https://docs.microsoft.com//windows/mixed-reality/coordinate-systems)más detalles sobre cómo optimizar el contenido de los distintos tamaños de espacio.
 

**P: mi espacio es demasiado grande y se están ejecutando errores al intentar configurar una experiencia permanente con límites. ¿Qué debo hacer para configurar mi trabajo de gran experiencia de movilidad gratuita?**

R: para configurar un espacio mayor que ~ 18x18ft, no podrá usar la experiencia de límite que proporciona el sistema.  Los sistemas de límites se basan en el uso de un único "anclaje" de coordenadas fijas, que puede volverse inestable cuando un usuario está demasiado lejos del delimitador de la fase central. 

En su lugar, puede configurar el modo "sentado", que no mostrará el límite ni configurará límites de fase o Playspace.  A continuación, deberá configurar varios delimitadores espaciales dentro de la aplicación para hacer referencia a áreas de límite físico. 

El desarrollador de la aplicación es responsable de mostrar las medidas de seguridad necesarias para que los usuarios no entren en conflicto con el entorno físico.  Podrían ser paredes digitales dentro de la experiencia o un visual de límite de juego personalizado. 

Puede encontrar instrucciones sobre cómo configurar el límite de la habitación con WMR [aquí](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).

**P: ¿Dónde está el origen de Playspace?**

R: el origen de Playspace viene determinado por la experiencia de instalación del salón, más específicamente la posición de HMD cuando se presiona el botón central durante la instalación. 

### <a name="multi-player-setup"></a>CONFIGURACIÓN DE VARIOS JUGADORES

**P: estoy implementando una experiencia de varios jugadores en mi lugar. ¿Es compatible con Windows Mixed Reality?**

R: la herramienta de empaquetado de datos espaciales de realidad mixta es una característica beta que permite localizar varios reproductores en el mismo espacio habilitando la migración de los datos espaciales de un equipo a otro. Puede obtener acceso a la herramienta y obtener más información [aquí](mixedrealityspatialdatapackager.md).

Si opta por las compilaciones de Windows 20H1 o posterior (a través de nuestro programa [Insider](https://docs.microsoft.com//windows-insider/at-home/get-started) ), puede acceder a una nueva interfaz para el uso compartido de mapas. Esta nueva funcionalidad está disponible a través de la interfaz del administrador de mapas del portal de dispositivos de Windows. Para usar esta herramienta, siga estos pasos:
- Asegúrese de participar en 20H1 o posterior (a partir del 2019 de septiembre, esto significa usar nuestro programa Insider).
- Habilitar Windows Device portal (WDP). [aquí](https://docs.microsoft.com//windows/uwp/debug-test-perf/device-portal-desktop) se indican las instrucciones
- Conecte una HMD de realidad mixta de Windows que quiera descargar una asignación existente desde o importar una nueva asignación.
- Navegue hasta el WDP en el explorador que prefiera mediante la dirección URL proporcionada en la pantalla Configuración. 
  - Una vez que haya navegado a la sección "Mixed Reality" y seleccione "Administrador de mapas". 
  - Ahora puede usar el botón "Descargar" para exportar una asignación existente desde la máquina. 
  - Puede usar el botón "cargar un archivo de asignación" para importar un mapa de una exportación anterior (quizás en otro equipo). 
  - Puede usar "importar" para permitir que el sistema use esa asignación para este HMD en este equipo.
  
### <a name="tracking"></a>LLEVAR

P: ¿Cómo funciona la tecnología de seguimiento de los auriculares Windows Mixed Reality?  

La realidad mixta comparte la misma tecnología de seguimiento que la HoloLens. Para obtener más información sobre el sistema de seguimiento interno, consulte la documentación [aquí](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/tracking-system).

Para obtener una descripción de cómo funciona el sistema de asignación espacial de nivel superior, puede leer nuestra descripción [aquí](spatial-mapping.md).

**P: ¿existen procedimientos recomendados para obtener un volumen de seguimiento confiable?**

Para configurar mejor el entorno para el seguimiento correcto, puede leer los procedimientos recomendados en esta [publicación](environment-considerations-for-hololens.md).

**P: ¿existen matices específicos con el seguimiento de los espacios de escala de almacenamiento o de las optimizaciones que se deben tener en cuenta?**

R: las siguientes prácticas pueden ayudarle a obtener un volumen de seguimiento más confiable:  

Proporcionar una variedad de características en el salón que se superponen en varias posiciones ayudará al sistema de seguimiento a obtener un bloqueo sólido. Piense en la Splatters de pintura aleatoria y en el sombreado en lugar de usar líneas de estilo de contorno sólido. 

Minimice el intervalo dinámico de iluminación en el área donde sea posible. Las cámaras de seguimiento de nuestras HMDss de realidad mixta no son HDR y tienen AGC (ganancia automática) y AEC (exposición automática) para tratar con la iluminación diferente. En función de la distribución de la luz de superficie, los patrones y el contraste, el AGC o AEC pueden concluir que está en una habitación prácticamente en blanco o negro que puede descolorar las características que pueden estar en el "color" opuesto. Si intenta tomar una imagen interior delante de una ventana exterior con el horario de verano brillante y ajusta la exposición para que pueda ver los detalles fuera, todo el interior está subexpuesto y negro. O bien, si se establece para dentro de, todo lo que se encuentra fuera se sobreexpone y todo el blanco.  

Spotlight en una habitación (incluso en la sobrecarga) que están en la vista si las cámaras de seguimiento pueden ser a veces culpables que confunden el AEC/AGC de las cámaras de seguimiento. La iluminación plana/difusa ayuda a.  

### <a name="mixed-reality-cloud-services-and-azure"></a>SERVICIOS EN LA NUBE DE REALIDAD MIXTA Y AZURE 

**P: ¿Cómo puede Microsoft Azure ayudar a mi escala empresarial?**

R: la administración remota y en el sitio de Azure puede ayudar a su empresa a controlar los datos, reducir los costos operativos y escalar la implementación en las ubicaciones nuevas y existentes. Los servicios en la nube de Azure, como Azure Storage, Azure Functions, App Service, Azure networking y IOT Hub pueden ayudar con los siguientes casos de uso:  

Administración de & de implementación de dispositivos remotos 

Análisis in situ en tiempo real 

Juego LBE adaptable inteligente 

Transmisión e implementación de contenido de LBE 

Preferencias de LBE Player mapa térmico 

Sistema de reserva y reserva de LBE 

**P: estoy desarrollando un MMOG espacial para implementarlo en una superficie masiva. ¿Todos los servicios que me ayudan a administrar mi contenido y persistencia de objetos?**

R: los delimitadores espaciales de Azure son un nuevo servicio de realidad mixta que permite experiencias de realidad mixta multiusuario y con reconocimiento espacial en dispositivos de HoloLens, iOS y Android. Puede obtener más información sobre los anclajes espaciales de Azure [aquí](https://azure.microsoft.com//services/spatial-anchors/).

**P. nuestro lugar está especializado en experiencias con varios jugadores y me gustaría centrarnos en el tiempo de desarrollo en el contenido y el desarrollo de front-end. ¿Hay ofertas que puedan ayudarme a arrancar o descargar el desarrollo de back-end?**

R: Azure PlayFab es una plataforma de back-end completa para juegos en vivo. Puede obtener más información al respecto [aquí](https://playfab.com/).

### <a name="misc"></a>Variada

**P: uso SteamVR para implementar mis experiencias. ¿Funciona Windows Mixed Reality con SteamVR?**

R: Windows Mixed Reality para SteamVR permite a los usuarios ejecutar experiencias de SteamVR en auriculares con micrófonos de realidad con Windows Mixed Reality. [Aquí](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)encontrará más información sobre STEAMVR con WMR.

### <a name="support-and-community"></a>Soporte técnico y comunidad  

A continuación se muestran algunos recursos útiles para ponerse en contacto con expertos en la materia en nuestro equipo, obtener soporte técnico de solución de problemas y contribuir a la mayor comunidad de desarrollo de realidad mixta.  

Si surgen problemas con características publicadas públicamente, envíe un error con el centro de comentarios. para obtener instrucciones, consulte esta [Página](https://docs.microsoft.com//windows/mixed-reality/enthusiast-guide/filing-feedback).

Para obtener ayuda adicional sobre la solución de problemas con WMR, póngase en contacto con nuestro equipo de soporte técnico para que le envíe una [solicitud de soporte técnico](https://support.microsoft.com//supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782).

Únase a nuestro canal de margen de demora de HoloDevelopers para interactuar con los desarrolladores que trabajan con la realidad mixta y expertos en la materia del equipo: [aka.ms/holodevelopers](https://aka.ms/holodevelopers)

Twitter: siga nuestro equipo de relaciones con el desarrollador de realidad mixta para obtener noticias, eventos y actualizaciones @MxdRealityDev 

En caso de que se encuentre en San Francisco, siempre habrá algo en marcha en el reactor de Microsoft. [Aquí](https://developer.microsoft.com//reactor/Location/San%20Francisco)puede ver el calendario de eventos.
