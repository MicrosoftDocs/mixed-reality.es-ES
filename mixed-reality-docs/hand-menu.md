---
title: Menú de la mano
description: Los menús de mano permiten a los usuarios poner en marcha rápidamente la interfaz de usuario asociada a las funciones de uso frecuente. Estos son los procedimientos recomendados y las recomendaciones para los menús de la mano.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: mano, menú, botón, acceso rápido, diseño
ms.openlocfilehash: c0e1800be69a15706e17f40b1601fc79d05e5d75
ms.sourcegitcommit: 6844930427b658ae31f642c395cd8a3b3cdbf857
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75723264"
---
# <a name="hand-menu"></a>Menú de la mano

![Ubicación del lado de ulnar](images/UX/UX_Hero_HandMenu.jpg)

Los menús de mano permiten a los usuarios poner en marcha rápidamente la interfaz de usuario asociada a las funciones de uso frecuente. 

A continuación se muestran los procedimientos recomendados para los menús de la mano. También puede encontrar una escena de ejemplo en la que se muestra el menú de la mano en [MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup).

<br>

---

## <a name="behavior-best-practices"></a>Prácticas recomendadas de comportamiento
**A. mantener el número de botones pequeños:** debido a la distancia de cierre entre un menú bloqueado a mano y los ojos, y también la tendencia del usuario a centrarse en un área visual relativamente pequeña en cualquier momento (el cono de visión es aproximadamente de 10 grados), se recomienda mantener el número de botones pequeños. En función de la exploración, una columna con tres botones funciona bien manteniendo todo el contenido dentro del campo de vista (campo de contenido) incluso cuando los usuarios mueven sus manos al centro del campo de campo. 

**B. usar el menú de la mano para una acción rápida:** la elevación de un brazo y el mantenimiento de la posición pueden provocar una fatiga ARM. Use un método bloqueado manualmente para el menú que requiera una breve interacción. Si el menú es complejo y requiere tiempos de interacción extendidos, considere la posibilidad de usar en su lugar el uso de bloqueos internacionales o del cuerpo. 

**C. botón/ángulo del panel:** los menús deben encabezarse hacia el hombro opuesto y el centro del cabezal: Esto permite que un movimiento de mano natural interactúe con el menú con la mano opuesta y evite las posiciones de mano extrañas o inconvenientes al tocar botones. 

**D. considere la posibilidad de admitir operaciones Monodireccionales o gratuitas:** no asuma que las dos manos del usuario están siempre disponibles. Tenga en cuenta una amplia gama de contextos cuando una o ambas manecillas no estén disponibles y asegúrese de que su diseño tiene en cuenta esas situaciones. Para admitir un menú de una mano, puede intentar realizar la transición de la ubicación del menú desde el bloque bloqueado a un mundo bloqueado cuando la mano se voltee (se desplace hacia abajo). En escenarios gratuitos, considere la posibilidad de usar un comando de voz para invocar los botones de menú de la mano.

**E. invocación en dos pasos:** si usa solo Palm como un evento para desencadenar el menú de la mano, puede aparecer accidentalmente cuando no lo necesite (falsos positivos), ya que los usuarios mueven las manos de forma intencionada (para la comunicación y la manipulación de objetos) y de manera no intencionada. Si experimenta falsos positivos en la aplicación, considere la posibilidad de agregar un paso adicional además del evento de mano para invocar el menú de la mano, como los dedos completamente abiertos.

**F. evitar agregar botones cerca de la muñeca (botón Inicio del sistema):** si los botones del menú mano se colocan demasiado cerca del botón Inicio, puede que se desencadene accidentalmente al interactuar con el menú de la mano.

**G. test, test, test:** los usuarios tienen cuerpos distintos, con distintos umbrales de comodidad y comodidad, etc. Asegúrese de probar el diseño y obtener comentarios de varias personas.

<br>

---

## <a name="hand-menu-placement-best-practices"></a>Procedimientos recomendados de selección de ubicación de menús

En la anatomía humana, el ulnar Nerve es un Nerve que se ejecuta cerca del hueso de Ulna. Ulna es un hueso largo que se encuentra en el Forearm que se estira desde el codo hasta el dedo más pequeño.

A continuación se muestran dos ubicaciones recomendadas basadas en nuestras exploraciones:


:::row:::
    :::column:::
        ![Ubicación del lado ulnar](images/UlnarSideHandMenu.gif)<br>
        **A. ulnar en Palm**<br>
        Esta posición es confiable porque las manos no se superponen entre sí. Esto es fundamental para la detección y el seguimiento precisos de la mano.
    :::column-end:::
    :::column:::
        ![Ubicación del lado ulnar](images/UlnarAboveHandMenu.gif)<br>
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
        ![sobre ARM](images/AboveArm.gif)<br>
        **Por encima del brazo**<br>
        1-difícil de mantener un buen seguimiento de la mano<br>
        2-causa fatiga del usuario debido a una posición no natural
    :::column-end:::
    :::column:::
        ![sobre los dedos](images/AboveFingers.gif)<br>
        **Los dedos anteriores**<br>
        fatiga de 1 mano debido a la entrega de la mano durante mucho tiempo<br>
        2-problemas de seguimiento en el índice y el dedo central
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![por encima del centro Palm](images/handCenter.gif)<br>
        **Anterior: Palm del centro**<br>
        1-problemas de seguimiento debidos a manos superpuestas<br>
        fatiga de 2 a mano debido a la conservación de las manos durante mucho tiempo para interactuar con los menús
    :::column-end:::
    :::column:::
        ![primera mano](images/TopFingerTip.gif) **primera mano**<br>
        1-problemas de seguimiento de la mano<br>
        fatiga de 2 manos manteniendo la mano por encima de la postura normal<br>
        3-problemas al presionar botones con otros dedos por accidente debido a un espacio limitado entre los dedos
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![parte posterior del brazo](images/BackOfTheArm.gif)<br>
        **Parte posterior del brazo**<br>
        1-puede desencadenar el botón Inicio por accidente<br>
        2-no es una posición natural o cómoda para los usuarios
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a>Menú de la mano en MRTK (kit de herramientas de realidad mixta) para Unity
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** proporciona scripts y escenas de ejemplo para el menú de la mano. HandConstraintPalmUp el script de Solver le permite adjuntar fácilmente cualquier objeto a las manos con varias opciones configurables.

* [Menú MRTK con HandConstraint y HandConstraintPalmUp](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_Solver.md#hand-menu-with-handconstraint-and-handconstraintpalmup)


<br>

---


## <a name="see-also"></a>Consulta también

* [Cursores](cursors.md)
* [Haces de mano](point-and-commit.md)
* [Button](button.md)
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
