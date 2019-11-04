---
title: Mirada con la cabeza y permanencia
description: Introducción al modelo de entrada de mirada con la cabeza y permanencia
author: liamartinez
ms.author: liamar
ms.date: 05/13/2019
ms.topic: article
keywords: Mixed Reality, gaze, dwell, interaction, design
ms.openlocfilehash: 6d209d3cc91ceecb4b9feef2925f093288c9f8ac
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73439316"
---
# <a name="head-gaze-and-dwell"></a>Mirada con la cabeza y permanencia

Si tienes las manos ocupadas con herramientas y piezas, hacer gestos puede ser engorroso o imposible. Los comandos de voz, al igual que los gestos, pueden ser poco fiables en determinados contextos, por ejemplo en condiciones de ruido excesivamente alto. Además, aún no se ha generalizado el uso de la voz para controlar equipos, aunque claramente está ganando popularidad. El mecanismo de mirada con la cabeza y permanencia es el más conocido y fácil de dominar para trabajar con visualización frontal y manos libres en HoloLens. Además, el modelo de mirada con la cabeza y permanencia es completamente fiable, independientemente de las interferencias de ruido o las restricciones de silencio del entorno operativo.

## <a name="scenarios"></a>Escenarios

En los casos en los que las manos de una persona están ocupados con otras tareas y la voz no es del 100% confiable o disponible debido a las restricciones ambientales o sociales, el uso de la mano y los de la vivienda. Un buen ejemplo sería el de una persona que lleva un dispositivo HoloLens para ver superpuesta información de referencia mientras repara el motor de un automóvil. Puede tener ocupadas las manos con herramientas o usarlas para sostenerse al reclinarse sobre el compartimento del motor. En la zona del garaje hay mucho ruido, con los constantes golpes y zumbidos de las herramientas, lo que dificulta el uso de comandos de voz. El encabezado y la vivienda permiten a la persona que usa HoloLens navegar por confianza su material de referencia sin interrumpir su flujo de trabajo. 

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
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Mirada con la cabeza y permanencia</td>
        <td>✔️ Se recomienda</td>
        <td>✔️ Se recomienda</td>
        <td>✔️ Se recomienda</td>
    </tr>
</table>


## <a name="design-principles"></a>Principios de diseño

**Evite "mirarnos como un arma"**

El modelo de mirada con la cabeza y permanencia requiere información visual para ser intuitivo, pero demasiada información puede resultar estresante. La información debe ayudar al usuario a saber qué está mirando, pero no seleccionar ese elemento automáticamente contra la voluntad del usuario. La lectura de texto, iconos y etiquetas requiere una consideración especial para dar tiempo al usuario a absorber la información antes de seleccionar.
    
**Velocidad de búsqueda de Goldilocks**
    
Las interacciones de permanencia pueden tener distintos temporizadores, en función del impacto de la navegación. Para las funciones frecuentes, suele ser mejor un tiempo de relleno más rápido, mientras que para las funciones relevantes suele resultar mejor un tiempo de relleno más prolongado. Si se usa un efecto de relleno para mostrar estos temporizadores, las curvas de animación del color de relleno pueden influir positivamente para transmitir una sensación de tiempo de relleno más rápido. Debe prestarse especial atención para permitir al usuario decidir si cambiar a velocidad de relleno rápida, media o lenta.
    
**Decir, efecto no-no a yo-yo**

El efecto yo-yo es un patrón incómodo de movimiento de la cabeza que puede surgir cuando la ubicación del contenido y los controles de mirada con la cabeza y permanencia obligan al usuario a mirar hacia arriba y hacia abajo constantemente. Por ejemplo, una lista de navegación con el botón de AvPág y el botón de permanencia en la parte inferior induce un bucle de-mirar a la vivienda, buscar en los resultados, buscar en la vivienda, etc. Este patrón resultante es incómodo y se debe evitar colocando los controles de navegación en una ubicación centralizada que requiere menos y después. La ubicación de los botones de permanencia en relación con sus efectos resulta importante para la comodidad.

<br>

---


## <a name="ux-guidelines-and-best-practices"></a>Directrices y procedimientos recomendados para la experiencia del usuario

### <a name="target-sizes"></a>Tamaños de los destinos
  Para que sea fácilmente accesible, los objetivos de la vista de cabeza y de la vivienda deben ser lo suficientemente grandes como para examinarlos de forma cómoda y mantener el cabezal estable en el destino durante el tiempo previsto. Se recomienda un tamaño mínimo de destino de 2 grados para lograr la experiencia más cómoda. 

### <a name="visual-feedback"></a>Comentarios visuales

Al utilizar un relleno radial para representar el temporizador de permanencia, empieza desde el centro del botón. Una respuesta coherente es menos confusa que si cada botón tiene una dirección distinta. 

  * No obstante, esta regla puede romperse para las interacciones direccionales (por ejemplo, navegar hacia arriba/abajo/izquierda/derecha, etc.). Por ejemplo, Microsoft Dynamics 365 Guides hace una excepción para los botones SIGUIENTE/ATRÁS, que son rellenos de izquierda y derecha.
  * Considera la posibilidad de invertir un relleno radial desde fuera, para escenarios como desactivar un botón. La sensación inversa a pulsar un botón es un patrón visual que resulta útil mantener. 

### <a name="progressive-disclosure"></a>Muestra progresiva

La muestra progresiva significa que solo se muestran los detalles pertinentes en cada etapa de una interacción. En el caso de la permanencia, esto significa que el objetivo de permanencia se muestra resaltado (por ejemplo, en un control de lista).

 ### <a name="oversized-targets"></a>Objetivos demasiado grandes
La región de permanencia puede ser mayor que el icono inactivo para que resulte más fácil de usar, al igual que el botón Atrás en Microsoft Dynamics 365 Guides.

### <a name="prevent-flickering-with-delayed-feedback"></a>Evitar el parpadeo con información retrasada
Utiliza un breve retraso antes de iniciar la información visual para evitar el parpadeo cuando un usuario pase sobre un objetivo de permanencia.
* En el caso de los botones INTERACTUADOS con frecuencia, mantenga el retraso muy breve para que la aplicación se sienta reactiva.
* En el caso de los botones que se interactúan con poca frecuencia, un retraso más largo puede ser adecuado para evitar la sensación de interfaz twitchy.


<br>

---

## <a name="ui-patterns"></a>Patrones de la interfaz de usuario

### <a name="high-frequency-buttons"></a>Botones de alta frecuencia

:::row:::
    :::column:::
        Los botones de alta frecuencia son botones que se usan habitualmente en una aplicación. Un buen ejemplo son los botones Siguiente y Atrás de Microsoft Dynamics 365 Guides.<br>
        <br>
        **Tenida**<br>
  * Los botones de alta frecuencia deben ser grandes y más fáciles de visitar
  * Manténgase cerca de la altura para evitar una presión ergonómica.<br>
        <br>
*Imagen: botón siguiente de las guías de Microsoft Dynamics 365*
    :::column-end:::
        :::column:::
       ![Botón siguiente de las guías de Microsoft Dynamics 365](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a>Botones de baja frecuencia
Los botones de baja frecuencia son aquellos que no se accionan en la aplicación con demasiada frecuencia. Un buen ejemplo podría ser un botón para acceder al menú de configuración o un botón para borrar todo el trabajo.

* Intenta mantener estos botones apartados de las rutas frecuentes de la mirada con la cabeza para evitar activarlos accidentalmente. 

<br>

---

### <a name="confirmations"></a>Confirmaciones

:::row:::
    :::column:::
        Cuando una acción tiene un impacto significativo, como cobrar dinero, eliminar trabajo o iniciar un proceso largo, resulta útil confirmar que el usuario realmente quiere seleccionar ese botón.<br>
        <br>
        **Tenida**<br>
  * Muestra el resaltado de la selección en el botón principal.
  * Muestra el objetivo de permanencia al mismo tiempo que el resaltado de selección.
  * Para el botón secundario, muestra el objetivo de permanencia al mirar con la cabeza.<br>
        <br>
*Imagen: cuadro de diálogo de confirmación de las guías de Microsoft Dynamics 365*
    :::column-end:::
        :::column:::
       ![Cuadro de diálogo de confirmación de las guías de Microsoft Dynamics 365](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a>Botones de alternancia
Los botones de alternancia requieren una lógica matizada para que funcionen correctamente. Cuando una persona permanece sobre un botón de alternancia y lo activa, debe salir del botón y, a continuación, volver para reiniciar la lógica de permanencia. Es importante que se distinga claramente el estado activo del inactivo de los botones de alternancia. 

<br>

---

### <a name="list-views"></a>Vistas de lista

:::row:::
    :::column:::
        Las vistas de lista presentan un desafío determinado para la entrada de encabezado y de continuación. Los usuarios deben poder recorrer el contenido sin la sensación de tener que ir pasando de puntillas por los distintos objetivos de permanencia.<br>
        <br>
**Tenida**<br>
  * Hacer que la fila completa se resalte cuando se mira por la cabeza, pero no comienza la permanencia, a menos que la punta de la mirada esté en el destino de vivienda específico.
  * Muestre solo el destino de permanencia cuando la fila esté resaltada para reducir el ruido visual.
  * Ser claros y coherentes con la posición de los objetivos de la vivienda.
  * No muestre todos los destinos de permanencia a la vez para evitar la interfaz de usuario repetida.
  * Vuelva a usar el mismo patrón tantas veces como sea posible para establecer la familiaridad con la experiencia del usuario.<br>
        <br>
*Imagen: lista de guías de Microsoft Dynamics 365*
    :::column-end:::
        :::column:::
       ![Lista de guías de Microsoft Dynamics 365](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a>Consulta también
* [Miras y confirmaciones](gaze-and-commit.md)
* [Manipulación práctica directa](direct-manipulation.md)
* [Gestos prácticos](gaze-and-commit.md#composite-gestures)
* [Manos y confirmación](point-and-commit.md)
* [Interacciones instintivas](interaction-fundamentals.md)
* [Entrada de voz](voice-input.md)
