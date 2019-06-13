---
title: Mirada con la cabeza y permanencia
description: Introducción al modelo de entrada de mirada con la cabeza y permanencia
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, gaze, dwell, interaction, design
ms.openlocfilehash: 70b25949380679d2edc81b07ab54f24fa20e3f3d
ms.sourcegitcommit: 9b6949d7cd2e67e6bde9b32aebeaeea325baa6c4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2019
ms.locfileid: "66516013"
---
# <a name="head-gaze-and-dwell"></a>Mirada con la cabeza y permanencia

Si tienes las manos ocupadas con herramientas y piezas, hacer gestos puede ser engorroso o imposible. Los comandos de voz, al igual que los gestos, pueden ser poco fiables en determinados contextos, por ejemplo en condiciones de ruido excesivamente alto. Además, aún no se ha generalizado el uso de la voz para controlar equipos, aunque claramente está ganando popularidad. El mecanismo de mirada con la cabeza y permanencia es el más conocido y fácil de dominar para trabajar con visualización frontal y manos libres en HoloLens. Además, el modelo de mirada con la cabeza y permanencia es completamente fiable, independientemente de las interferencias de ruido o las restricciones de silencio del entorno operativo.

## <a name="scenarios"></a>Escenarios

El modelo de mirada con la cabeza y permanencia destaca en escenarios en los que una persona tiene las manos ocupadas con otras tareas y el control por voz no está disponible o no resulta totalmente fiable debido a restricciones ambientales o sociales. Un buen ejemplo sería el de una persona que lleva un dispositivo HoloLens para ver superpuesta información de referencia mientras repara el motor de un automóvil. Puede tener ocupadas las manos con herramientas o usarlas para sostenerse al reclinarse sobre el compartimento del motor. En la zona del garaje hay mucho ruido, con los constantes golpes y zumbidos de las herramientas, lo que dificulta el uso de comandos de voz. El modelo de mirada con la cabeza y permanencia permite que la persona que lleva el dispositivo HoloLens se desplace sin problema por el material de referencia sin interrumpir su flujo de trabajo. 

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
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1ª generación)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Mirada con la cabeza y permanencia</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado</td>
    </tr>
</table>

## <a name="goals"></a>Objetivos

Proporcionar un mecanismo para interacciones totalmente con manos libres, sin utilizar la voz.

## <a name="design-principles"></a>Principios de diseño

1. Evitar miradas a discreción

    El modelo de mirada con la cabeza y permanencia requiere información visual para ser intuitivo, pero demasiada información puede resultar estresante. La información debe ayudar al usuario a saber qué está mirando, pero no seleccionar ese elemento automáticamente contra la voluntad del usuario. La lectura de texto, iconos y etiquetas requiere una consideración especial para dar tiempo al usuario a absorber la información antes de seleccionar.
    
2. Buscar una velocidad adecuada
    
    Las interacciones de permanencia pueden tener distintos temporizadores, en función del impacto de la navegación. Para las funciones frecuentes, suele ser mejor un tiempo de relleno más rápido, mientras que para las funciones relevantes suele resultar mejor un tiempo de relleno más prolongado. Si se usa un efecto de relleno para mostrar estos temporizadores, las curvas de animación del color de relleno pueden influir positivamente para transmitir una sensación de tiempo de relleno más rápido. Debe prestarse especial atención para permitir al usuario decidir si cambiar a velocidad de relleno rápida, media o lenta.
    
3. Evitar el efecto yo-yo

    El efecto yo-yo es un patrón incómodo de movimiento de la cabeza que puede surgir cuando la ubicación del contenido y los controles de mirada con la cabeza y permanencia obligan al usuario a mirar hacia arriba y hacia abajo constantemente. Por ejemplo, al navegar por una lista con el botón de mirada con la cabeza y permanencia en la parte inferior, se provoca un bucle de mirada hacia abajo para la permanencia, mirada hacia arriba para ver los resultados, mirada hacia abajo para la permanencia, etc. Este patrón resultante es incómodo y debe evitarse mediante la colocación de controles de navegación en una ubicación centralizada que requiera menos movimientos de un lado a otro. La ubicación de los botones de permanencia en relación con sus efectos resulta importante para la comodidad.

## <a name="ux-guidelines-and-best-practices"></a>Directrices y procedimientos recomendados para la experiencia del usuario

### <a name="target-sizes"></a>Tamaños de los destinos
  Para que los objetivos de mirada con la cabeza y permanencia sean fácilmente accesibles, deben ser lo suficientemente grandes como para poder enfocarlos cómodamente y mantener estable la cabeza sobre el objetivo durante el tiempo necesario. Se recomienda un tamaño de objetivo mínimo de 2 grados para lograr la experiencia más cómoda posible. 

### <a name="visual-feedback"></a>Información visual

Al utilizar un relleno radial para representar el temporizador de permanencia, empieza desde el centro del botón. Una respuesta coherente es menos confusa que si cada botón tiene una dirección distinta. 

  * No obstante, esta regla puede romperse para las interacciones direccionales (por ejemplo, navegar hacia arriba/abajo/izquierda/derecha, etc.). Por ejemplo, Microsoft Dynamics 365 Guides hace una excepción para los botones SIGUIENTE/ATRÁS, que son rellenos de izquierda y derecha.
  * Considera la posibilidad de invertir un relleno radial desde fuera, para escenarios como desactivar un botón. La sensación inversa a pulsar un botón es un patrón visual que resulta útil mantener. 

### <a name="progressive-disclosure"></a>Muestra progresiva

La muestra progresiva significa que solo se muestran los detalles pertinentes en cada etapa de una interacción. En el caso de la permanencia, esto significa que el objetivo de permanencia se muestra resaltado (por ejemplo, en un control de lista).

 ### <a name="oversized-targets"></a>Objetivos demasiado grandes
La región de permanencia puede ser mayor que el icono inactivo para que resulte más fácil de usar, al igual que el botón Atrás en Microsoft Dynamics 365 Guides.

### <a name="prevent-flickering-with-delayed-feedback"></a>Evitar el parpadeo con información retrasada
Utiliza un breve retraso antes de iniciar la información visual para evitar el parpadeo cuando un usuario pase sobre un objetivo de permanencia.
* Para botones accionados con frecuencia, usa un retraso muy breve para que la aplicación dé sensación de reaccionar rápido.
* En el caso de los botones que se accionan con menos frecuencia, un retraso más prolongado puede ser adecuado para evitar que la interfaz parezca dar tirones.

## <a name="ui-patterns"></a>Patrones de la interfaz de usuario

### <a name="high-frequency-buttons"></a>Botones de alta frecuencia
![Botón Siguiente de Microsoft Dynamics 365 Guides](images/GuideNextButton.png "Botón Siguiente de Microsoft Dynamics 365 Guides") Los botones de alta frecuencia son aquellos que se usan habitualmente en una aplicación. Un buen ejemplo son los botones Siguiente y Atrás de Microsoft Dynamics 365 Guides.

Los botones de alta frecuencia deben...
* ser botones más grandes, más fáciles de seleccionar con la mirada con la cabeza;
* permanecer cerca de la altura de los ojos para evitar el agotamiento ergonómico.

### <a name="low-frequency-buttons"></a>Botones de baja frecuencia
Los botones de baja frecuencia son aquellos que no se accionan en la aplicación con demasiada frecuencia. Un buen ejemplo podría ser un botón para acceder al menú de configuración o un botón para borrar todo el trabajo.

* Intenta mantener estos botones apartados de las rutas frecuentes de la mirada con la cabeza para evitar activarlos accidentalmente. 

### <a name="confirmations"></a>Confirmaciones
![Cuadro de diálogo de confirmación de Microsoft Dynamics 365 Guides](images/GuidesConfirmation.png "Cuadro de diálogo de confirmación de Microsoft Dynamics 365 Guides")

Cuando una acción tiene un impacto significativo, como cobrar dinero, eliminar trabajo o iniciar un proceso largo, resulta útil confirmar que el usuario realmente quiere seleccionar ese botón. En las interfaces de usuario de mirada con la cabeza y permanencia, deben tenerse en cuenta algunos aspectos para los cuadros de diálogo:

  * Muestra el resaltado de la selección en el botón principal.
  * Muestra el objetivo de permanencia al mismo tiempo que el resaltado de selección.
  * Para el botón secundario, muestra el objetivo de permanencia al mirar con la cabeza.
        
### <a name="toggle-buttons"></a>Botones de alternancia
Los botones de alternancia requieren una lógica matizada para que funcionen correctamente. Cuando una persona permanece sobre un botón de alternancia y lo activa, debe salir del botón y, a continuación, volver para reiniciar la lógica de permanencia. Es importante que se distinga claramente el estado activo del inactivo de los botones de alternancia. 

### <a name="list-views"></a>Vistas de lista
![Cuadro de diálogo de confirmación de Microsoft Dynamics 365 Guides](images/GuidesListView.png "Microsoft Dynamics 365 Guides Confirmation Dialog") Las vistas de lista presentan un desafío particular para la entrada de mirada con la cabeza y permanencia. Los usuarios deben poder recorrer el contenido sin la sensación de tener que ir pasando de puntillas por los distintos objetivos de permanencia. 

A continuación se indican algunos consejos para diseñar vistas de lista:
* Haz que toda la fila se resalte al mirarla con la cabeza, pero no inicies la permanencia hasta que la mirada con la cabeza se sitúe en el objetivo de permanencia específico.
* Muestra el objetivo de permanencia solo cuando se resalte la fila para reducir el ruido visual.
* Sé claro y coherente con la posición de los objetivos de permanencia.
* No muestres todos los objetivos de permanencia al mismo tiempo para evitar que la interfaz de usuario resulte repetitiva.
* Vuelve a usar el mismo patrón siempre que sea posible para que la experiencia del usuario resulte familiar.
 
 ## <a name="see-also"></a>Consulte también
* [Manipulación directa con las manos](direct-manipulation.md)
* [Apuntar y confirmar con las manos](point-and-commit.md)
* [Interacciones instintivas](interaction-fundamentals.md)
* [Mirada-cabeza y confirmación](gaze-and-commit.md)
* [Comandos de voz](voice-design.md)
