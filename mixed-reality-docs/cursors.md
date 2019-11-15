---
title: Cursores
description: Un cursor, o indicador del vector de destino, proporciona comentarios continuos para que el usuario comprenda lo que HoloLens entiende sobre sus intenciones.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (1ª generación), HoloLens 2, realidad mixta, cursores, destinatarios, mirados, gestos
ms.openlocfilehash: 719e7a573e8c8bc682ec0f960d9f3c8f8c8e5a4a
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105742"
---
# <a name="cursors"></a>Cursores

![Cursores](images/UX/UX_Hero_Cursor.jpg)

Un cursor, o indicador del vector de destinatarios actual, proporciona comentarios continuos para que el usuario comprenda Dónde está el foco actual en ese momento. El cursor permite al usuario comprender su punto de destino actual y actúa como comentario para indicar qué área, holograma o punto responderá a la entrada. Es la representación digital de dónde el dispositivo entiende la atención del usuario (aunque es posible que no sea el mismo que determinar nada sobre sus intenciones).

Los comentarios proporcionados por el cursor ofrecen a los usuarios la posibilidad de anticiparse a cómo responderá el sistema, usar esa señal como comentario para comunicar mejor su intención al dispositivo y, en última instancia, tener más confianza sobre sus interacciones.

Hay 3 tipos de cursores: **Finger, Ray**y **Head-mirate**. Estos cursores de señalización funcionan con diferentes modalidades de entrada en HoloLens, HoloLens 2 y auriculares envolvente. A continuación se ofrecen instrucciones sobre qué tipo de cursor se debe utilizar para cada tipo de auriculares y modelo de interacción. En el kit de herramientas de realidad mixta (MRTK), hemos creado módulos de cursores de arrastrar y colocar para ayudarle a crear la experiencia adecuada.


## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Ofrecen</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Cursor de dedo</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>Cursor de rayo</td>
        <td>❌</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td>Cursor de miras hacia abajo</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="finger-cursor"></a>Cursor de dedo
El cursor de dedo solo está disponible en HoloLens 2 para mejorar el modo de interacción "[manipulación directa con manos](direct-manipulation.md)". Para comprender mejor dónde apunta el dedo, hemos adjuntado anillos a las propinas de ambos dedos del índice. El tamaño del anillo se basa en la proximidad del dedo a la superficie de la interfaz de usuario (cuanto más cerca del dedo, menor es el anillo) y se reducirá a una forma de punto cuando el dedo se ponga en contacto con la interfaz de usuario. <br>

![](images/finger-cursor.png) de cursor de dedo<br>
**Estados de comentarios visuales del cursor de dedo** 1: el anillo se reduce a un punto. 2: el anillo se alinea con la superficie. 3: el anillo es perpendicular al vector de dedo. 4: sin anillo.

## <a name="ray-cursor"></a>Cursor de rayo
Los cursores de rayo se adjuntan al final de los rayos que apuntan mucho para permitir la manipulación de objetos que no están disponibles. En los auriculares envolventes, los rayos salen de los controladores de movimiento y finalizan los cursores de punto. En HoloLens 2, aprovechamos el modelo mental de estos rayos de controlador de movimiento y los rayos de mano diseñados que se originan a partir de las palmeras y acaban en cursores en forma de anillo que son coherentes con los cursores de dedo utilizados en la manipulación directa. <br>
:::row:::
    :::column:::
        ![controlador de cursor de rayo](images/ray-cursor-controller.png)<br>
        **Cursores de rayo de controladores de movimiento**<br>
    :::column-end:::
    :::column:::
        ![mano de cursor de rayo](images/ray-cursor-hand.png)<br>
        **Cursores de rayo de manos**<br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="head-gaze-cursor"></a>Cursor de miras hacia abajo
El cursor de mira hacia abajo es un punto que se adjunta al final de un vector de miras hacia arriba invisible que usa la posición y la rotación del encabezado al punto. Para ejecutar acciones, este cursor señalador se empareja con varias entradas de confirmación, como la pulsación de aire, los comandos de voz, la permanencia y la pulsación de botones. En HoloLens 2, el encabezado de la mirada es mejor con cualquier entrada de confirmación que no se pulse en el aire, ya que habrá un conflicto de interacción entre la derivación del aire y los rayos de mano. <br>
:::row:::
    :::column:::
        ![mano del cursor de mira hacia abajo](images/head-gaze-cursor-hand.png)<br>
        **Cursor de mira hacia abajo con el gesto de mano**<br>
    :::column-end:::
    :::column:::
        ![](images/head-gaze-cursor-voice.png) de voz de cursor de mira<br>
        **Cursor de mira hacia abajo con el comando de voz**<br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="cursor-customization-recommendations"></a>Recomendaciones de personalización de cursores
Si desea personalizar los comportamientos y los aspectos de los comentarios del cursor, estas son algunas recomendaciones de diseño:

### <a name="cursor-scale"></a>Escala del cursor
* El cursor no debe ser mayor que los destinos disponibles, lo que permite a los usuarios interactuar fácilmente con el contenido y verlo.
* Dependiendo de la experiencia que cree, el escalado del cursor a medida que el usuario busca también es una consideración importante. Por ejemplo, a medida que el usuario mira más en su experiencia, el cursor no debe ser demasiado pequeño, por lo que se pierde.
* Al escalar el cursor, considere la posibilidad de aplicarle una animación de software a medida que se escale para darle una sensación orgánica.
* Evite obstruir el contenido. Los hologramas son lo que hacen que la experiencia sea memorable y el cursor no debe apartarse de ellas.

### <a name="directionless-cursor-shape"></a>Forma cursor no direccional
* Aunque no hay ninguna forma de cursor derecha, se recomienda usar una forma sin dirección como un toro. Un cursor que apunta en alguna dirección (por ejemplo, un cursor de flecha tradicional) puede confundir al usuario para que siempre mire ese modo.
* Una excepción a esto es cuando se usa el cursor para comunicar la instrucción de interacción al usuario. Por ejemplo, al escalar los hologramas en el sistema operativo de realidad mixta, el cursor incluye de forma temporal flechas que indican al usuario Cómo trasladar la mano para escalar el holograma.

### <a name="look-and-feel"></a>Apariencia y funcionamiento
* Un anillo o cursor con forma de aro funciona con muchas aplicaciones.
* Elija un color y una forma que mejor represente la experiencia que va a crear.
* Los cursores son especialmente propensos a la [separación de colores](hologram-stability.md#color-separation).
* Un cursor pequeño con opacidad equilibrada mantiene informativa sin dominar la jerarquía visual.
* Tenga en Cognizant el uso de sombras o resaltados detrás del cursor, ya que podrían obstruir el contenido y distraerse de la tarea a mano.
* Los cursores deben alinearse con las superficies de la aplicación y Hug, lo que le dará la sensación de que el sistema puede ver dónde están buscando, pero también que el sistema es consciente de su entorno. Por ejemplo, en el sistema operativo de realidad mixta, el cursor se alinea con las superficies del mundo del usuario, lo que crea un sentimiento de sensibilización del mundo incluso cuando el usuario no está mirando directamente a un holograma.
* El bloqueo magnético del cursor en un elemento interactivo cuando está dentro de proximidad puede ayudar a mejorar la confianza de que el usuario interactuará con ese elemento cuando realice una acción de selección.

### <a name="visual-cues"></a>Indicaciones visuales
* Si su experiencia se centra en un solo holograma, el cursor debe alinearse y Hug solo ese holograma y cambiar de forma cuando mira el holograma. Esto puede transmitir al usuario que el holograma es accionable y puede interactuar con él.
* Si la aplicación usa la asignación espacial, el cursor podría alinear y Hug cada superficie que ve. Esto proporciona comentarios a los usuarios de que HoloLens y su aplicación pueden ver su espacio. Esto refuerza el hecho de que los hologramas son reales y en nuestro mundo y ayudan a salvar la brecha entre real y virtual.
* Tenga una idea de lo que debe hacer el cursor cuando no haya ningún holograma o superficie en la vista. Colocarlo a una distancia predeterminada delante del usuario es una opción.

### <a name="possible-actions"></a>Acciones posibles
* El cursor se puede representar mediante iconos diferentes para transmitir posibles acciones que puede realizar un holograma, como el escalado o la rotación.
* Agregue solo información adicional sobre el cursor si significa algo al usuario. De lo contrario, es posible que los usuarios no perciban los cambios de estado u obtengan una confusión con el cursor.

### <a name="input-state"></a>Estado de entrada
* Podríamos usar el cursor para mostrar el estado de entrada o la intención del usuario. Por ejemplo, podríamos mostrar un icono que indica al usuario que el sistema ve su estado de mano y que la aplicación sabe que está listo para tomar medidas.
* También podríamos usar el cursor para mostrar a los usuarios que el sistema ha escuchado comandos de voz a través de un Change de color momentáneo

* Los siguientes Estados de cursor se pueden implementar de maneras diferentes. Puede implementar estos Estados diferentes modelando el cursor como una máquina de Estados. Por ejemplo:
    * Estado de inactividad es donde se muestra el cursor predeterminado.
    * El estado listo es cuando se ha detectado la mano del usuario en la posición listo.
    * El estado de interacción es cuando el usuario realiza una interacción determinada.
    * El estado de las acciones posibles o el estado de desplazamiento es cuando se transmiten las posibles acciones que se pueden realizar en un holograma.

También puede implementar estos Estados de forma que pueda mostrar distintos recursos artísticos cuando se detecten distintos Estados.

<br>

---


## <a name="going-cursor-free"></a>"Sin cursor"
Se recomienda diseñar sin un cursor cuando el sentido de la inmersión es un componente clave de una experiencia y cuando las interacciones que señalan (a través de la mirada y el gesto) no requieren una gran precisión. El sistema debe seguir cumpliendo las necesidades que normalmente cumple un cursor al proporcionar a los usuarios comentarios continuos sobre el conocimiento del sistema y ayudarles a comunicar sus intenciones al sistema de forma segura. Esto puede ser factible a través de otros cambios de estado perceptibles.

<br>

---

## <a name="cursor-in-mrtkmixed-reality-toolkit-for-unity"></a>Cursor en MRTK (kit de herramientas de realidad mixta) para Unity
De forma predeterminada, **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** proporciona un cursor recurso prefabricado ([DefaultCursor. recurso prefabricado](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) que tiene el mismo estado visual que el cursor del sistema del shell. Se asigna en el perfil de entrada de MRTK, en punteros. Puede reemplazar o personalizar este cursor para su experiencia. Para la experiencia con la entrada de seguimiento ocular, MRTK también proporciona EyeGazeCursor que tiene un efecto visual sutil para minimizar la distracción.

* [MRTK: Perfil de puntero](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [MRTK: sistema de entrada](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [MRTK: punteros](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)


---

## <a name="see-also"></a>Consulta también
* [Gestos](gaze-and-commit.md#composite-gestures)
* [Mirada-cabeza y confirmación](gaze-and-commit.md)
