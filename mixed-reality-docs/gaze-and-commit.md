---
title: Mirada con la cabeza y confirmación
description: Introducción al modelo de entrada de mirada con la cabeza y confirmación
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Mixed Reality, gaze, gaze targeting, interaction, design
ms.openlocfilehash: aeca5ceacf5ae350aa06cb58cc68162f885f6d78
ms.sourcegitcommit: b0b1b8e1182cce93929d409706cdaa99ff24fdee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2019
ms.locfileid: "68387681"
---
# <a name="head-gaze-and-commit"></a>Mirada con la cabeza y confirmación
La acción de mirar y confirmar es un modelo de entrada que implica apuntar a un objeto con la dirección del puntero hacia delante (dirección del encabezado) y, a continuación, actuar en él con una entrada secundaria, como la pulsación aérea de gestos de mano o la selección de comando de voz. Se considera un modelo de entrada Far con manipulación indirecta, lo que significa que es mejor usar para interactuar con el contenido que está más allá del alcance de los brazos.

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
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Mirada con la cabeza y confirmación</td>
        <td>✔️ Recomendado</td>
        <td>✔️ Recomendado (tercera opción: <a href="interaction-fundamentals.md">Ver las demás opciones</a>)</td>
        <td>➕ Opción alternativa</td>
    </tr>
</table>

## <a name="head-gaze"></a>Mirada con la cabeza
Los cascos de realidad mixta utilizan la posición y orientación de la cabeza del usuario para determinar el vector de dirección de la cabeza. Se puede considerar como un láser que apunta en línea recta directamente desde el punto situado entre los ojos del usuario. Esto es una aproximación bastante general de dónde mira el usuario. La aplicación puede formar una intersección con este rayo con objetos virtuales o del mundo real, y dibujar un cursor en esa ubicación para que el usuario sepa lo que tienen como destino actualmente.

Además de los cabezales, algunos auriculares de realidad mixta, como HoloLens 2, incluyen sistemas de seguimiento ocular que producen un vector de mirada ocular. Esto proporciona una medida específica de adónde mira el usuario. Es posible compilar las interacciones de Premira y de confirmación con la vista de ojo. Pero esto incluye un conjunto muy diferente de restricciones de diseño, que se tratarán por separado en el artículo de mirada [a la vista](eye-tracking.md).

## <a name="commit"></a>Confirmación
Después de establecer como destino un objeto o un elemento de la interfaz de usuario, el usuario puede interactuar o hacer clic en él mediante una entrada secundaria. Esto se conoce como el paso de confirmación del modelo. Se admiten los siguientes métodos de confirmación:

- Gesto de tocar el aire
- Diga el comando de voz, seleccione o uno de los comandos de voz de destino.
- Presionar un solo botón en un [clic de HoloLens](hardware-accessories.md#hololens-clicker)
- Presione el botón ' A ' en un controlador para juegos de Xbox
- Presione el botón ' A ' en un controlador adaptable de Xbox

### <a name="head-gaze-and-air-tap-gesture"></a>Mirada con la cabeza y gesto de pulsación en el aire
Pulsar en el aire es hacer el gesto de pulsar con la mano vertical. Para realizar una pulsación de aire, eleve el dedo del índice a la posición listo y, a continuación, acerque el dedo y vuelva a colocar el dedo de índice en la versión. En HoloLens (1ª generación), Air TAP es la entrada secundaria más común.

![Dedo en posición vertical y movimiento de pulsar o hacer clic](images/readyandpress.jpg)<br>

Air TAP también está disponible en HoloLens 2. Se ha relajado de la versión original. Ahora se admiten casi todos los tipos de gestos, siempre y cuando la mano esté en vertical y manteniendo todavía. Esto facilita a los usuarios aprender y realizar el gesto. Esta nueva derivación de aire reemplaza a la antigua a través de la misma API, por lo que las aplicaciones existentes tendrán el nuevo comportamiento automáticamente después de volver a compilar para HoloLens 2.

### <a name="head-gaze-and-select-voice-command"></a>Mirada con la cabeza y comando de voz "Seleccionar"
Los comandos de voz son uno de los métodos de interacción principales en la realidad mixta. Proporciona un mecanismo gratuito muy eficaz para controlar el sistema. Hay diferentes tipos de modelos de interacción de voz:

- El comando genérico SELECT que realiza una acción de hacer clic o confirmar como entrada secundaria.
- Los comandos de objeto como Close o hacen que sea más grande realiza y se confirma en una acción como entrada secundaria.
- La commnads global como ir a Inicio no requiere un destino.
- Las interfaces o entidades de usuario de conversación como Cortana tienen una capacidad de lenguaje natural de AI.
- Los comandos personalizados.

Para encontrar más detalles, así como una lista de comprenhesive de comandos disponibles y cómo usarlos, consulte nuestra guía de [comandos de voz](voice-design.md) .


### <a name="head-gaze-and-hololens-clicker"></a>Mirada con la cabeza y HoloLens Clicker
El clic de HoloLens es el primer dispositivo periférico creado específicamente para HoloLens. Se incluye en la edición de desarrollo de HoloLens (1º gen). El clic de HoloLens permite que un usuario haga clic con el movimiento mínimo de mano y se confirme como una entrada secundaria. El clic de HoloLens se conecta a HoloLens (1º gen) o a HoloLens 2 con Bluetooth de baja energía (BTLE).

![HoloLens Clicker](images/hololens-clicker-500px.jpg)<br>
*HoloLens Clicker*

[Aquí](hardware-accessories.md#pairing-bluetooth-accessories) encontrarás más información e instrucciones para emparejar el dispositivo.




### <a name="head-gaze-and-xbox-wireless-controller"></a>Mirada con la cabeza y controlador inalámbrico de Xbox
La controladora inalámbrica Xbox realiza una acción de clic como entrada secundaria mediante el botón "A". El dispositivo se asigna a un conjunto predeterminado de acciones que ayudan a desplazarse por el sistema y controlarlo. Si desea personalizar el controlador, use la aplicación Xbox Accesories para configurar el controlador inalámbrico de Xbox.

![Controlador inalámbrico de Xbox](images/xboxcontroller.jpg)<br>
*Controlador inalámbrico de Xbox*

[Emparejamiento de un controlador de Xbox con el PC](hardware-accessories.md#pairing-bluetooth-accessories)


### <a name="head-gaze-and-xbox-adaptive-controller"></a>Mirada con la cabeza y Xbox Adaptive Controller
Diseñado principalmente para satisfacer las necesidades de los jugadores con movilidad limitada, el controlador adaptable Xbox es un concentrador unificado para dispositivos que ayuda a hacer que la realidad mixta sea más accesible.

El controlador adaptable de la Xbox realiza una acción de clic como entrada secundaria mediante el botón "A". El dispositivo se asigna a un conjunto predeterminado de acciones que ayudan a navegar y controlar el sistema. Si desea personalizar el controlador, use la aplicación Xbox Accesories para configurar el controlador adaptable de la Xbox.

![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)<br>
*Xbox Adaptive Controller*

Conecte dispositivos externos como conmutadores, botones, montajes y joysticks para crear una experiencia de controlador personalizada que sea suya exclusiva. Las entradas de los botones, el stick analógico y el desencadenador se controlan con dispositivos de asistencia conectados a través de conectores de 3,5 mm y puertos USB.

![Puertos del Xbox Adaptive Controller](images/xbox-adaptive-controller-ports.jpg)<br>
*Puertos del Xbox Adaptive Controller*

[Instrucciones para emparejar el dispositivo](hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/en-US/xbox-one/accessories/controllers/xbox-adaptive-controller>Más información disponible en el sitio de Xbox</a>


## <a name="design-guidelines"></a>Directrices de diseño
> [!NOTE]
> [Próximamente](index.md) habrá disponible más información específica para el diseño de la mirada.

## <a name="head-gaze-targeting"></a>Establecer el destino de la mirada con la cabeza
Todas las interacciones se basan en la capacidad de un usuario de establecer como destino el elemento con el que desea interactuar, independientemente de la modalidad de entrada. En Windows Mixed Reality, esto se hace mediante la mirada del usuario por lo general.
Para que un usuario pueda trabajar correctamente con una experiencia, el conocimiento calculado del sistema de la intención de un usuario y la intención real del usuario debe alinearse lo más cerca posible. En la medida que el sistema interpreta las intenciones del usuario correctamente, la satisfacción aumenta y el rendimiento mejora.


## <a name="target-sizing-and-feedback"></a>Ajuste de tamaño del destino y comentarios
El vector de miras se ha mostrado varias veces para que se pueda usar para lograr objetivos más precisos, pero a menudo funciona mejor para la segmentación bruta: adquisición de destinos de un modo más grande. Los tamaños mínimos de destino de 1 a 1,5 grados permiten acciones de usuario correctas en la mayoría de los escenarios, aunque los destinos de 3 grados a menudo permiten una mayor velocidad. Tenga en cuenta que el tamaño que el usuario establece como destino es realmente un área 2D incluso para los elementos 3D (cualquier proyección de ellos debe ser un área potencial de destino). Proporcionar alguna indicación destacada de que un elemento está "activo" (que el usuario tiene como destino) es muy útil. Esto puede incluir tratamientos como efectos visibles de "mantener el mouse", resaltados de audio o clics o alineación clara de un cursor con un elemento.

![Tamaño de objetivo óptimo a una distancia de 2 metros](images/gazetargeting-size-1000px.jpg)<br>
*Tamaño de objetivo óptimo a una distancia de 2 metros*

![Ejemplo de resaltado de un objeto establecido como destino de la mirada](images/gazetargeting-highlighting-640px.jpg)<br>
*Ejemplo de resaltado de un objeto establecido como destino de la mirada*

## <a name="target-placement"></a>Situación del destino
A menudo, los usuarios no pueden encontrar los elementos de la interfaz de usuario que están colocados muy altos o muy bajos en su campo de vista, centrándose en la mayor parte de su atención en áreas en torno a su enfoque principal, que es aproximadamente en el nivel de ojo. Quizás resulte útil colocar la mayoría de los destinos en una banda razonable a la altura de los ojos. Dada la tendencia de los usuarios de centrarse en un área visual relativamente pequeña en todo momento (el cono de atención de la visión es de 10 grados aproximadamente), agrupar los elementos de la interfaz de usuario según su relación conceptual puede producir comportamientos de llamada de atención de un elemento a otro, ya que un usuario mueve su mirada dentro de un área. Al diseñar la interfaz de usuario, se deben tener en cuenta las posibles grandes variaciones en el campo de visión entre HoloLens y los cascos envolventes.

![Ejemplo de elementos de la interfaz de usuario agrupados para facilitar el establecimiento del destino con la mirada en Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)<br>
*Ejemplo de elementos de la interfaz de usuario agrupados para facilitar el establecimiento del destino con la mirada en Galaxy Explorer*

## <a name="improving-targeting-behaviors"></a>Mejora de los comportamientos de establecimiento de destino
Si la intención del usuario de destinar algo puede determinarse (o aproximarse de cerca), puede resultar muy útil aceptar los intentos de pérdida en la interacción como si estuviesen dirigidos correctamente. Estos son algunos de los métodos correctos que se pueden incorporar en experiencias de realidad mixta:

### <a name="head-gaze-stabilization-gravity-wells"></a>Estabilización de la mirada con la cabeza ("pozos de gravedad")
Esto se debe activar la mayoría o la totalidad del tiempo. Esta técnica elimina las vibraciones de cabeza natural y cuello que los usuarios podrían tener como movimiento debido a comportamientos de mirar y hablar.

### <a name="closest-link-algorithms"></a>Algoritmos de vínculo más cercano
Funcionan mejor en áreas con un contenido interactivo disperso. Si hay una probabilidad alta de que pueda determinar con qué un usuario estaba intentando interactuar, puede complementar sus capacidades de destino suponiendo cierto nivel de intento.

### <a name="backdating-and-postdating-actions"></a>Acciones de la
Este mecanismo es útil en las tareas que requieren velocidad. Cuando un usuario pasa por una serie de maniobras de destino y activación a velocidad, resulta útil asumir algún intento y permitir que los pasos perdidos actúen en los destinos en los que el usuario tenía el foco ligeramente antes o ligeramente después de la pulsación (50 ms antes/después era efectiva en EA pruebas de RLY).

### <a name="smoothing"></a>Suavizado
Este mecanismo es útil para los movimientos de las acciones, lo que reduce la ligera vibración y Wobble debido a las características de movimiento de cabeza natural. Al suavizar los movimientos de las acciones, smoothándose por el tamaño y la distancia de los movimientos en lugar de a lo largo del tiempo.

### <a name="magnetism"></a>Magnetismo
Este mecanismo puede considerarse como una versión más general de los algoritmos de vínculo más cercanos: dibujar un cursor hacia un destino o simplemente aumentar hitboxes, ya sea visible o no, a medida que los usuarios se aproximan a los objetivos probables mediante el uso de algún conocimiento del diseño interactivo para mejorar enfoque del intento del usuario. Esto puede resultar especialmente eficaz para destinos pequeños.

### <a name="focus-stickiness"></a>Permanencia del foco
Al determinar los elementos interactivos cercanos en los que se va a dar el foco, el ajuste de enfoque proporciona una inclinación al elemento que está enfocado actualmente. Esto ayuda a reducir los comportamientos de cambio de foco errático al flotar en un punto medio entre dos elementos con ruido natural.


## <a name="composite-gestures"></a>Gestos compuestos

### <a name="air-tap"></a>Pulsar en el aire
El gesto de pulsación de aire (así como los demás gestos que aparecen a continuación) reacciona solo a una derivación específica. Para detectar otras pulsaciones, como menú o agarre, la aplicación debe usar directamente las interacciones de nivel inferior descritas en la sección dos gestos de componentes clave anteriores.

### <a name="tap-and-hold"></a>Mantener pulsado
Mantener pulsado simplemente consiste en mantener la posición del dedo hacia abajo al pulsar en el aire. La combinación de la pulsación de aire y la suspensión permite una gran variedad de interacciones "hacer clic y arrastrar" más complejas al combinarse con el movimiento de ARM, como la selección de un objeto en lugar de activarlo o la interacción secundaria de MouseDown, como mostrar un menú contextual.
No obstante, se debe tener precaución al diseñar para este gesto, porque los usuarios pueden ser propensos a relajar las posturas de la mano en el caso de gestos prolongados.

### <a name="manipulation"></a>Manipulación
Los gestos de manipulación se pueden usar para desplazar, cambiar de tamaño o girar un holograma cuando se desea que el holograma reaccione 1:1 a los movimientos del usuario. Uno de los usos de estos movimientos 1:1 es permitir al usuario dibujar o pintar en el mundo.
El destino inicial de un gesto de manipulación debe establecerse con la mirada o apuntando. Una vez que se inicia la acción de pulsar y mantener, cualquier manipulación del objeto se controla a través de los movimientos manuales, lo que libera al usuario para que mire mientras manipula.

### <a name="navigation"></a>Navegación
Los gestos de navegación funcionan como un joystick virtual y se pueden usar para navegar por los widgets de la interfaz de usuario, como los menús circulares. Se mantiene pulsado para iniciar el gesto y, después, se mueve la mano dentro de un cubo 3D normalizado centrado alrededor de la pulsación inicial. Se puede mover la mano a lo largo del eje X, Y o Z desde un valor de -1 hasta 1, siendo 0 el punto de partida.
La navegación se puede utilizar para crear gestos de zoom o desplazamiento continuo basado en la velocidad, similares al desplazamiento en una interfaz de usuario 2D cuando se hace clic con el botón central del ratón para después mover el ratón hacia arriba y abajo.

La navegación con raíles se refiere a la capacidad de reconocer movimientos en cierto eje hasta que se alcanza un umbral determinado en dicho eje. Esto solo es útil cuando el desarrollador habilita el movimiento en más de un eje en una aplicación, por ejemplo, si una aplicación está configurada para reconocer los gestos de navegación por el eje X, Y, pero también especifica el eje X con raíles. En este caso, el sistema reconocerá los movimientos de mano en el eje X siempre y cuando permanezcan dentro de un raíl imaginario (guía) en el eje X, si el movimiento de mano también se produce en el eje Y.

En las aplicaciones 2D, los usuarios pueden usar gestos de navegación vertical para desplazarse, hacer zoom o arrastrar dentro de la aplicación. Esto inserta entradas táctiles virtuales en la aplicación para simular gestos táctiles del mismo tipo. Los usuarios pueden seleccionar cuál de estas acciones tienen lugar alternando entre las herramientas de la barra situada encima de la aplicación, ya sea seleccionando el botón o diciendo ' < herramienta de desplazamiento/arrastrar/zoom > '.

[Más información sobre los gestos compuestos](gestures.md#composite-gestures)

## <a name="gesture-recognizers"></a>Reconocedores de gestos

Una ventaja de usar el reconocimiento de gestos es que puede configurar un reconocedor de gestos solo para los gestos que el holograma de destino actual puede aceptar. La plataforma solo realiza la desambiguación según sea necesario para distinguir los gestos admitidos en particular. De esta manera, un holograma que solo admita Air TAP puede aceptar cualquier período de tiempo entre la prensa y la versión, mientras que un holograma que admita tanto tap como Hold puede promover la derivación a una retención después del umbral de tiempo de espera.

## <a name="hand-recognition"></a>Reconocimiento de la mano
HoloLens reconoce los gestos de la mano mediante el seguimiento de la posición de una o ambas manos si son visibles para el dispositivo. HoloLens ve las manos cuando están en el estado preparado (parte posterior de la mano hacia ti con el dedo índice arriba) o el estado presionado (parte posterior de la mano hacia ti con el dedo índice hacia abajo). Cuando las manos están en otras poses, HoloLens omite themz.
Para cada mano que HoloLens detecta, puede tener acceso a su posición sin orientación y su estado presionado. A medida que la mano se acerca al borde del marco gestual, obtendrás un vector de dirección que puedes mostrar al usuario para que sepa cómo mover la mano para volver a ponerla donde HoloLens pueda verla.

## <a name="gesture-frame"></a>Marco gestual
En el caso de los gestos en HoloLens, la mano debe estar dentro de un marco de gestos, en un intervalo en el que las cámaras de detección de gestos pueden ver adecuadamente, de la nariz a la waist y entre los hombros. Los usuarios deben estar entrenados en esta área de reconocimiento tanto para el éxito de la acción como para su comodidad. En principio, muchos usuarios suponen que el marco de gestos debe estar en su vista a través de HoloLens y mantener sus ramas de forma no cómoda para interactuar. Al usar el clic de HoloLens, no es necesario que las manos estén dentro del marco de gestos.

En el caso de los gestos continuos en concreto, hay un riesgo de que los usuarios muevan sus manos fuera del marco de gestos mientras se mueven al mover un objeto holográfica, por ejemplo, y se pierde el resultado previsto.

Hay tres cosas que hay que tener en cuenta:

- Educación del usuario sobre la existencia y los límites aproximados del marco de gestos. Esto se enseña durante la instalación de HoloLens.

- Notificar a los usuarios cuando sus gestos están próximos o rompiendo los límites del marco de gestos dentro de una aplicación hasta el grado en que un movimiento perdido conduce a resultados no deseados. La investigación ha mostrado las cualidades clave de este sistema de notificación. El shell de HoloLens proporciona un buen ejemplo de este tipo de notificación: visual, en el cursor central, que indica la dirección en la que se está llevando a cabo el cruce de límites.

- Se deben minimizar las consecuencias de traspasar los límites del marco gestual. En general, esto significa que el resultado de un gesto debe detenerse en el límite y no revertirse. Por ejemplo, si un usuario mueve algún objeto holográfica a través de una habitación, el movimiento debe detenerse cuando se infrinja el marco de gestos y no se devuelva al punto inicial. El usuario puede experimentar cierta frustración, pero es posible que comprenda más rápidamente los límites y no tenga que reiniciar todas las acciones previstas en cada momento.


## <a name="see-also"></a>Vea también
* [Manipulación directa con las manos](direct-manipulation.md)
* [Apuntar y confirmar con las manos](point-and-commit.md)
* [Interacciones instintivas](interaction-fundamentals.md)
* [Control con la cabeza y permanencia](gaze-and-dwell.md)
* [Comandos de voz](voice-design.md)





