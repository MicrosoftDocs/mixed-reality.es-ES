---
title: Menú Mano
description: Los menús de mano permiten a los usuarios poner en marcha rápidamente la interfaz de usuario asociada a las funciones de uso frecuente. Estos son los procedimientos recomendados y las recomendaciones para los menús de la mano.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: mano, menú, botón, acceso rápido, diseño
ms.openlocfilehash: d1d15b36bab2ca2082ca4ba91b9c64862893f80c
ms.sourcegitcommit: fef42e2908e49822f2d13b05d2f9260bf0d72158
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2020
ms.locfileid: "86061177"
---
# <a name="hand-menu"></a>Menú Mano

![Ubicación del lado de ulnar](images/UX/UX_Hero_HandMenu.jpg)

El menú de la mano es uno de los patrones de experiencia de usuario más únicos de HoloLens 2. Permite abrir rápidamente la interfaz de usuario asociada a la mano. Dado que es accesible en cualquier momento y se puede mostrar y ocultar fácilmente, es excelente para acciones rápidas.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

Encontrará las prácticas recomendadas para trabajar con menús de mano en la lista siguiente. También puede encontrar una escena de ejemplo en la que se muestra el menú de la mano en [MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html).

<br>


---

## <a name="best-practices"></a>Procedimientos recomendados
**Mantener el número de botones pequeños** 

Debido a la distancia aproximada entre un menú bloqueado a mano y los ojos, y también la tendencia del usuario a centrarse en un área visual relativamente pequeña en cualquier momento (el cono de visión es aproximadamente de 10 grados), se recomienda mantener el número de botones pequeños. En función de la exploración, una columna con tres botones funciona bien manteniendo todo el contenido dentro del campo de vista (campo de visualización) incluso cuando un usuario mueve sus manos al centro del campo de contenido. 

**Uso del menú de la mano para una acción rápida** 

La elevación de una ARM y el mantenimiento de la posición pueden provocar una fatiga ARM. Use un método bloqueado manualmente para el menú que requiera una breve interacción. Si el menú es complejo y requiere tiempos de interacción extendidos, considere la posibilidad de usar en su lugar el uso de bloqueos internacionales o del cuerpo. 

**Ángulo de botón/panel**

Los menús deben encabezarse hacia el hombro opuesto y el centro del cabezal: Esto permite que un movimiento de mano normal interactúe con el menú con la mano opuesta y evite las posiciones de mano extrañas o inconvenientes al tocar botones. 

**Considere la posibilidad de admitir operaciones Monodireccionales o gratuitas**

No asuma que las dos manos del usuario están siempre disponibles. Tenga en cuenta una amplia gama de contextos cuando una o ambas manecillas no estén disponibles y asegúrese de que su diseño tiene en cuenta esas situaciones. Para admitir un menú de una mano, puede intentar realizar la transición de la ubicación del menú desde el bloque bloqueado a un mundo bloqueado cuando la mano se voltee (se desplace hacia abajo). En escenarios gratuitos, considere la posibilidad de usar un comando de voz para invocar el menú de la mano.

**Evitar agregar botones cerca de la muñeca (botón Inicio del sistema)**

Si los botones de menú de la mano se colocan demasiado cerca del botón Inicio, se puede desencadenar accidentalmente durante la interacción con el menú de la mano.

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a>Menú mano con controles de interfaz de usuario grandes y complejos
<img src="images/UX/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
Se recomienda limitar el número de botones o controles de interfaz de usuario en los menús conectados a mano. Esto se debe a que la interacción extendida con un gran número de elementos de la interfaz de usuario puede causar fatiga ARM. Si su experiencia requiere un menú grande, proporcione un método sencillo para que el usuario bloquee el menú. Una técnica que se recomienda es usar el menú de bloqueo internacional cuando la mano se coloca o se mueve fuera del usuario. Una segunda técnica consiste en permitir que el usuario capte directamente el menú con la otra mano. Cuando el usuario suelta el menú, el menú debe ser un bloqueo universal. De este modo, un usuario puede interactuar con varios elementos de la interfaz de usuario de forma cómoda y confiable durante un período de tiempo prolongado. 

Cuando el menú esté bloqueado mundialmente, asegúrese de proporcionar una manera de desplace el menú y cierre el menú cuando ya no se necesite. Haga que el menú sea móvil proporcionando controladores en los lados o en la parte superior del menú. Agregue un botón Cerrar para permitir que el menú se cierre. Permite que el menú se vuelva a adjuntar a la mano cuando el usuario se enfrente al usuario. También se recomienda requerir que los usuarios se vean a mano para evitar activaciones falsas (consulte a continuación).

**Menú grande que muestra un problema de facilidad de uso**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

**Descartado de la mano del menú con bloqueo mundial**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

**Extracción manual & extraer del menú**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]


## <a name="how-to-prevent-false-activation"></a>Cómo evitar la activación falsa

Si usa solo Palm como un evento para desencadenar el menú de la mano, puede aparecer accidentalmente cuando no lo necesite (falsos positivos), ya que los usuarios mueven sus manos intencionadamente (para la comunicación y la manipulación de objetos) y de forma involuntaria. Para reducir las activaciones falsas, agregue un paso adicional además del evento de mano para invocar el menú de la mano (como los dedos totalmente abiertos o el usuario intencionadamente Gazing en su mano).

**Requerir Palm plana**

Al requerir una mano abierta plana, puede evitar la activación falsa que se puede producir cuando el usuario manipula objetos o gestos mientras se comunica dentro de un entorno. 

**Requerir mira**

Al solicitar al usuario que se ponga en mano (ya sea con miras hacia abajo o hacia abajo), se evitan las activaciones falsas debido a que el usuario tiene que dirigir intencionadamente su atención a la mano como un paso de activación secundario (con un umbral de distancia ajustable que se usa para permitir la comodidad del usuario).  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a>Procedimientos recomendados de selección de ubicación de menús

En la anatomía humana, el ulnar Nerve es un Nerve que se ejecuta cerca del hueso de Ulna. Ulna es un hueso largo que se encuentra en el Forearm que se estira desde el codo hasta el dedo más pequeño.

A continuación se muestran dos ubicaciones recomendadas basadas en nuestras exploraciones:


:::row:::
    :::column:::
        ![Ubicación del lado de ulnar](images/UlnarSideHandMenu.gif)<br>
        **A. ulnar en Palm**<br>
        Esta posición es confiable porque las manos no se superponen entre sí. Esto es fundamental para la detección y el seguimiento precisos de la mano.
    :::column-end:::
    :::column:::
        ![Ubicación del lado de ulnar](images/UlnarAboveHandMenu.gif)<br>
        **B. ulnar por encima de la mano**<br>
        Esta ubicación es cómoda para los usuarios porque no necesitan aumentar demasiado el brazo para interactuar con el menú de la mano. Se recomienda colocar los menús **13cm** sobre la palma y alinear los botones dentro de la palma de ulnar. [Obtenga más información sobre el tamaño óptimo del botón](interactable-object.md)<br>
        <br>
        Por motivos técnicos, recomendamos esta ubicación con una implementación necesaria: el desarrollador deberá inmovilizar el menú cuando la mano del usuario se acerque a la interacción con él. Esto evitará la vibración de las manos superpuestas y también permite un destino más rápido de los botones.<br>
        <br>
        Las cámaras de HoloLens 2 identifican las manos con precisión cuando son independientes entre sí. Las manos superpuestas pueden provocar que los menús de la mano se alejen de la ubicación del delimitador.<br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a>Posiciones de menú no recomendadas
Hemos realizado una investigación de usuario con distintos diseños y ubicaciones de menús; **no se recomiendan**las siguientes ubicaciones de menú:


:::row:::
    :::column:::
        ![Anterior ARM](images/AboveArm.gif)<br>
        **Por encima del brazo**<br>
        1-difícil de mantener un buen seguimiento de la mano<br>
        2-causa fatiga del usuario debido a una posición no natural
    :::column-end:::
    :::column:::
        ![Los dedos anteriores](images/AboveFingers.gif)<br>
        **Los dedos anteriores**<br>
        la fatiga de 1 mano debido a la falta de mano durante mucho tiempo<br>
        2-problemas de seguimiento en el índice y los dedos del centro
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Por encima del centro Palm](images/handCenter.gif)<br>
        **Anterior: Palm del centro**<br>
        1-problemas de seguimiento debidos a manos superpuestas<br>
        fatiga de 2 a mano debido a la conservación de las manos durante mucho tiempo para interactuar con los menús
    :::column-end:::
    :::column:::
        ![Primer dedo ](images/TopFingerTip.gif) **principal**<br>
        1-problemas de seguimiento de la mano<br>
        la fatiga de 2 manos desde la mano por encima de la postura normal<br>
        3-problemas al presionar botones con otros dedos por accidente debido a un espacio limitado entre los dedos
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Parte posterior del brazo](images/BackOfTheArm.gif)<br>
        **Parte posterior del brazo**<br>
        1-puede desencadenar el botón Inicio por accidente<br>
        2-no es una posición natural o cómoda
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a>Menú de la mano en MRTK (kit de herramientas de realidad mixta) para Unity
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** proporciona scripts y escenas de ejemplo para el menú de la mano. El script de Solver de HandConstraintPalmUp le permite adjuntar cualquier objeto a las manos con varias opciones configurables. Los ejemplos de los menús de MRTK incluyen opciones útiles como el requisito plano de Palm y fijamente para evitar la activación falsa.

* [Documentación del menú de la mano](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)
* [Escenario de ejemplo de menú de mano](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

Puede probar ejemplos de menú de la mano en HoloLens 2 con la aplicación Hub de ejemplos de MRTK. 
* [Escenario de menú de mano en el concentrador de ejemplos de MRTK](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---


## <a name="see-also"></a>Vea también

* [Cursores](cursors.md)
* [Haces de mano](point-and-commit.md)
* [Botón](button.md)
* [Objeto con el que se puede interactuar](interactable-object.md)
* [Cuadro de límite y barra de la aplicación](app-bar-and-bounding-box.md)
* [Manipulación](direct-manipulation.md)
* [Menú Mano](hand-menu.md)
* [Menú Cerca](near-menu.md)
* [Colección de objetos](object-collection.md)
* [Comando de voz](voice-input.md)
* [Teclado](keyboard.md)
* [Información sobre herramientas](tooltip.md)
* [Claqueta](slate.md)
* [Control deslizante](slider.md)
* [Sombreador](shader.md)
* [Etiquetado y vista frontal continua](billboarding-and-tag-along.md)
* [Indicación del progreso](progress.md)
* [Magnetismo de superficie](surface-magnetism.md)
