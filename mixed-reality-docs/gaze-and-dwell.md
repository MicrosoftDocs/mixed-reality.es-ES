---
title: Head mirada y permanencia
description: Información general sobre el modelo de entrada de mirada de head y permanencia
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
ms.localizationpriority: high
keywords: Diseñar la realidad, mirada, permanencia, interacción, mixta
ms.openlocfilehash: aa4713407f14e94c88e654ae6648c4949f98e580
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974865"
---
# <a name="head-gaze-and-dwell"></a>Head mirada y permanencia

Cuando las manos están ocupadas con herramientas y los elementos, gestos pueden ser tedioso o imposible. Comandos de voz, como los gestos, pueden ser poco confiables en determinados contextos, por ejemplo en condiciones excesivamente altos. Además, uso de voz a los equipos de control no es universalmente comunes, pero sin duda está ganando vapor! Head mirada y permanencia ofrece el mecanismo más familiar y fácil de patrón para trabajar en pantalla de datos y manos libres en HoloLens. Además, head-mirada y permanencia es 100% confiable independientemente de las restricciones de interferencias ni silencio de ruido en el entorno operativo.

## <a name="scenarios"></a>Escenarios

Head mirada y permanencia resulta muy útil en escenarios donde las manos de una persona están ocupadas con otras tareas y voz no es 100% fiable o disponibles debido a restricciones del entorno o sociales. Un buen ejemplo es una persona con un HoloLens para superponer la información de referencia durante la reparación de un motor de automóvil. Las manos están ocupadas con herramientas o que admite su cuerpo, según inclínese hacia el compartimiento del motor. El espacio de garaje es alto, con la constante trabajar intensamente y zumbidos de herramientas, dificultando los comandos de voz. Head mirada y permanencia permite a la persona en el HoloLens para navegar con confianza su material de referencia sin interupting su flujo de trabajo. 

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modelo de entrada</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (gen 1)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></td>
    </tr>
     <tr>
        <td>Head mirada y permanencia</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado</td>
    </tr>
</table>

## <a name="goals"></a>Objetivos

Proporcionan un mecanismo para interacciones totalmente en manos libres, sin utilizar la voz.

## <a name="design-principles"></a>Principios de diseño

1. Evitar "Observación como un arma"

    Head mirada y permanencia requiere comentarios visuales para ser intuitivo, pero pueden provocar la ansiedad demasiada comentarios. Los comentarios deben ayudan a los usuarios saber lo tiene como destino, pero la selección automática no lo contra su intención. Leer texto, iconos y etiquetas, requiere una consideración adicional para proporcionar un espacio de la persona para absorber la información antes de seleccionar.
    
2. Buscar la velocidad de Rubiales
    
    Interacciones de permanencia pueden tener temporizadores diferentes según el impacto de navegación: funciones utilizadas con más frecuencia generalmente se beneficiarán de tiempos más rápidos de relleno, mientras que las funciones más daños consecuenciales pueden beneficiarse de tiempos más largos de relleno. Cuando se usa un efecto de relleno para mostrar estos temporizadores, curvas de animación del color de relleno positivamente pueden influir en una sensación de tiempos más rápidos de relleno. Deben tener en cuenta consideraciones para habilitar la Decisión del usuario de fast/medium/lento invalidaciones de velocidad de relleno.
    
3. Diga definitivamente a efecto yo-yo

    El efecto de yo-yo es un patrón incómodo de movimiento que puede surgir cuando la colocación de controles de contenido y head mirada y permanencia fuerza a personas que revisen constantemente y reducir verticalmente varias veces. Por ejemplo, una barra de navegación de la lista con el botón principal mirada y permanencia en la parte inferior provoca un bucle de - vistazo abajo profundizaré, buscar en los resultados, busque hacia abajo para profundizaré, etcetera. Este patrón resultante no resulta cómodo y debe evitarse mediante la colocación de controles de navegación en una ubicación centralizada que requiere menos atrás y adelante. Selección de ubicación de los botones de permanencia en relación con sus efectos se vuelve importante para su comodidad.

## <a name="ux-guidelines-and-best-practices"></a>Directrices de experiencia de usuario y procedimientos recomendados

### <a name="target-sizes"></a>Tamaños de los destinos
  Para que sea fácilmente accesible, head mirada profundizaré destinos deben ser suficientemente grande como para el destino comforatably y mantenga stabily head de uno en el destino para el tiempo prescrito. Se recomienda un tamaño de destino mínimo de 2 grados para lograr la experiencia resulte más cómoda. 

### <a name="visual-feedback"></a>Información visual

Al utilizar un relleno radial para representar el temporizador de permanencia, inicie desde el centro del botón. Una respuesta coherente es menos confusa que todas las direcciones diferentes en los botones diferentes. 

  * Esta regla puede interrumpirse aunque interacciones direccionales (p. ej., nav arriba/abajo/izquierda/derecha, etcetera.). Por ejemplo, Microsoft Dynamics 365 guías hace una excepción en la siguiente y atrás ha dejado rellenos derechos.
  * Considere la posibilidad de invertir radial relleno desde fuera, para escenarios como si activa o desactiva un botón de cierre. Inversa sensación de pulsar un botón es un práctico patrón visual para mantener. 

### <a name="progressive-disclosure"></a>Revelación progresiva

Revelación progresiva significa que solo se muestran toda la información que es relevante en cada etapa de una interacción. De permanencia, que significa que el destino de permanencia se revela en resaltado (por ejemplo, en un control de lista).

 ### <a name="oversized-targets"></a>Destinos demasiado grandes
Región de permanencia puede ser mayor que el icono inactivo que resulte más fácil de usar, al igual que el botón Atrás en las guías de Microsoft Dynamics 365.

### <a name="prevent-flickering-with-delayed-feedback"></a>Evitar el parpadeo con comentarios retrasada
Use un breve retraso antes de iniciar los comentarios visuales para evitar el parpadeo cuando alguien se desplaza sobre un destino de permanencia.
* Para botones inteacted con frecuencia, mantenga el retraso breve para que la aplicación se siente reactiva.
* Para los botones que se va a interactuar con infrequenctly un retraso más largo puede ser approprate para evitar la interfaz se siente twitchy.

## <a name="ui-patterns"></a>Patrones de la interfaz de usuario

### <a name="high-frequency-buttons"></a>Botones de alta frecuencia
![Microsoft Dynamics 365 guías siguiente botón](images/GuideNextButton.png "Microsoft Dynamics 365 guías siguiente botón") botones de alta frecuencia son que se usan con frecuencia en toda una aplicación. Un buen ejemplo de estos son los botones siguiente y atrás en las guías de Microsoft Dynamics 365.

Botones de alta frecuencia deben...
* ser botones más grandes, sea más fáciles seleccionar con head mirada
* Manténgase cerca de la altura del ojo para evitar agotar ergonómico.

### <a name="low-frequency-buttons"></a>Botones de baja frecuencia
Botones de baja frecuencia son que no son interactúe con él como con regularidad a lo largo de la aplicación. Un buen ejemplo podría ser un botón para acceder al menú de configuración o un botón para borrar todo el trabajo.

* Intente mantener estos botones interfiera rutas head mirada frecuentes para evitar la activación accidental. 

### <a name="confirmations"></a>Confirmaciones
![Cuadro de diálogo de confirmación de Microsoft Dynamics 365 guías](images/GuidesConfirmation.png "cuadro de diálogo de confirmación de las guías de Microsoft Dynamics 365")

Cuando una acción tiene un impacto significativo, como a cobrar dinero, eliminando el trabajo o iniciar un proceso largo, resulta útil confirmar que una persona diseñada para seleccionar un botón. Head mirada y permanencia hay interfaces de usuario son algunos patrones y consideraciones para los cuadros de diálogo de confirmación:

  * Mostrar resaltado de la selección en el botón principal.
  * Revelar permanencia destino al mismo tiempo que resalte de la selección.
  * Para el botón secundario, revele el destino de permanencia en la cabeza mirada.
        
### <a name="toggle-buttons"></a>Botones de alternancia
Botones de alternancia requieren cierta lógica matizado funcione correctamente. Cuando una persona dwells en un botón de alternancia y activos, necesitan para salir del botón y, a continuación, volver para reiniciar la lógica de permanencia. Es importante que los botones que se puedan alternar tienen una clara activo frente a estado inactivo. 

### <a name="list-views"></a>Vistas de lista
![Diálogo de confirmación de Microsoft Dynamics 365 guías](images/GuidesListView.png "diálogo de confirmación de Microsoft Dynamics 365 guías") presentan un desafío particular para head mirada de vistas de lista y profundizaré entrada. Gente necesita ser capaz de analizar el contenido sin la sensación de deba tiptoe en torno a los destinos de permanencia. 

Algunas sugerencias para diseñar vistas de lista:
* tiene toda la fila resaltar cuando gazed de cabeza, pero no comienza la permanencia a menos que sea head mirada en el destino de permanencia específico.
* Mostrar solo el destino de permanencia cuando se resalta la fila para reducir el ruido visual.
* ser claro y coherente con la posición de los destinos de permanencia.
* No se muestran que todos profundizaré destinos al mismo tiempo para evitar la interfaz de usuario repetitivo
* volver a usar el mismo patrón de tantas veces como sea posible para establecer la familiaridad de la experiencia del usuario
 
 ## <a name="see-also"></a>Vea también
* [Manipulación directa con las manos](direct-manipulation.md)
* [Apuntar y confirmar con las manos](point-and-commit.md)
* [Interacciones instintivas](interaction-fundamentals.md)
* [Mirada-cabeza y confirmación](gaze-and-commit.md)
* [Comandos de voz](voice-design.md)
