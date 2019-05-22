---
title: Marco holográfica
description: Los usuarios ver el mundo de la realidad mixta a través del marco holográfica.
author: mavitazk
ms.author: mavitazk
ms.date: 03/21/2018
ms.topic: article
keywords: Marco de HoloLens, Windows Mixed Reality, holographic, campo de visión
ms.openlocfilehash: c505eadbc16bb59143313aa62dd7c9d95384e0c8
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974913"
---
# <a name="holographic-frame"></a>Marco holográfica

Los usuarios ver el mundo de la realidad mixta a través de una ventanilla rectangular con tecnología de sus auriculares. En el HoloLens, esta área rectangular se llama el marco holográfico y permite a los usuarios ver contenido digital superpuesto en el mundo real en torno a ellas. Diseñar experiencias optimizadas para el marco holográfico crea oportunidades, soluciona los desafíos y mejora la experiencia del usuario de aplicaciones de realidad mixta.

## <a name="designing-for-content"></a>Diseño para el contenido

A menudo diseñadores siente la necesidad de limitar el ámbito de su experiencia, lo que el usuario puede ver de inmediato, sacrificar la escala del mundo real para garantizar que el usuario ve un objeto en su totalidad. Del mismo modo diseñadores con aplicaciones complejas a menudo sobrecargan el marco holográfico con contenido, abrumar a los usuarios con interfaces confuso y difíciles interacciones. Los diseñadores de creación de realidad mixta contenido no necesitan limitar su experiencia a directamente delante del usuario y dentro de su vista inmediata. Si se asigna el mundo físico que rodea el usuario, a continuación, todas estas superficies deben considerarse un lienzo para contenido digital e interacciones posibles. El diseño adecuado de las interacciones y contenido dentro de una experiencia debe fomentar que usuario mover su espacio, dirigir su atención en contenido de clave y ayudan a ver todo el potencial de realidad mixta.

Quizás la técnica más importante para fomentar movimiento y la exploración dentro de una aplicación es **permiten a los usuarios ajustar a la experiencia**. Conceder a los usuarios un breve período de tiempo 'libre de tarea' con el dispositivo. Esto puede ser tan simple como poner un objeto en el espacio y permitir a los usuarios desplazarse por él o comentar una introducción a la experiencia. Esta vez debiese ser libre de las tareas críticas o gestos de específico (por ejemplo, el aire toque), el propósito para que los usuarios puedan acomodarse a ver el contenido a través del dispositivo antes de requerir interactividad o progresa a través de las fases de la aplicación en su lugar. Si esta es la primera vez que un usuario con el dispositivo, esto es especialmente importante que obtienen contenido ven cómodo a través del marco holográfico y la naturaleza de hologramas.

### <a name="large-objects"></a>Objetos grandes

A menudo el contenido requiere una experiencia, especialmente reales contenido, será mayor que el marco holográfico. Los objetos que normalmente no caben dentro del marco holográfico deben se encoge para ajustarse al que se introducen en primer lugar (en una escala menor o a una distancia). La clave es **permiten a los usuarios ver el tamaño completo del objeto** antes de la escala abruma del marco. Por ejemplo, se debe mostrar un holográfica elephant para ajustarse por completo dentro del marco, permitiendo a los usuarios formar una comprensión espacial de forma general de los animales antes de cambiar el tamaño a [reales escala](scale.md) cerca del usuario.

Con el tamaño completo del objeto en mente, los usuarios, a continuación, tienen una expectativa de dónde desea mover y buscar elementos específicos de ese objeto. De forma similar, una experiencia con contenido envolvente, lo puede ayudar a tener alguna manera para hacer referencia al tamaño total del contenido. Por ejemplo, si trata de la experiencia de caminar alrededor de un modelo de una casa virtual, puede ser útil tener una versión reducida de tamaño de la casa de muñecas de la experiencia que los usuarios pueden desencadenar para entender dónde están dentro de la casa.

Para obtener un ejemplo de diseño de objetos grandes, consulte [los automóviles Volvo](holographic-frame.md#volvo-cars).

### <a name="many-objects"></a>Muchos objetos

Deben considerar experiencias con muchos componentes u objetos usando el espacio total en el usuario para no colapsar el marco holográfico directamente delante del usuario. En general, es recomendable introducir contenido a una experiencia lentamente y esto es especialmente cierto con las experiencias que va a servir muchos objetos al usuario. Igual con objetos grandes, la clave es **permiten a los usuarios a comprender el diseño del contenido** en la experiencia, les ayuda a obtener una descripción de lo que es en torno a ellas como contenido se agrega a la experiencia espacial.

Una técnica para lograr esto es proporcionar puntos persistentes (también conocido como puntos de referencia) en la experiencia de ese contenido de anclaje en el mundo real. Por ejemplo, un punto de referencia podría ser un objeto físico en la realidad, como una tabla donde aparece el contenido digital, o un objeto digital, como un conjunto de pantallas donde el contenido aparece con frecuencia. También se pueden colocar objetos en la periferia del marco para promover a dirigir su mirada hacia la clave de contenido, mientras que la detección de contenido más allá de la periferia puede ser asistida por usuario holográfica [directores atención](holographic-frame.md#attention-directors).

Colocar objetos en la periferia puede animar a los usuarios pudieran buscar al lado y esto puede asistido por directores de atención, como se describe a continuación.

## <a name="user-comfort"></a>Comodidad del usuario

Para la experiencia de realidad mixta con objetos de gran tamaño o muchos objetos, es fundamental tener en cuenta cuántos head y movimiento cuello es necesario interactuar con el contenido. Experiencias pueden dividirse en tres categorías en términos de movimiento: **Horizontal** (lado a lado), **vertical** (vertical y horizontal), o **envolventes** (horizontales y verticales). Cuando sea posible, limite la mayoría de las interacciones de las categorías horizontales o verticales, lo ideal es que con la mayoría de experiencias lleva a cabo en el centro del marco holográfico mientras principal del usuario se encuentra en una posición neutra. Evite las interacciones que provocan el usuario que moverse constantemente su vista a un poco naturales posiciones principal (por ejemplo, buscar siempre para tener acceso a una interacción de la clave de menú).

![Región más óptima para el contenido es de 0 a 35 grados por debajo de horizonte](images/optimal-field-of-view-2-750px.png)<br>
*Región más óptima para el contenido es de 0 a 35 grados por debajo de horizonte*

Movimiento horizontal es más [cómodo](comfort.md) para interacciones frecuentes, mientras que los movimientos verticales se deben reservar para eventos infrecuentes. Por ejemplo, una experiencia que implican una escala de tiempo horizontal larga debe limitar el movimiento vertical para las interacciones (por ejemplo, mirar un menú).

Considere la posibilidad de fomentar el cuerpo completo movimiento, en lugar de simplemente movimiento, mediante la colocación de objetos alrededor de espacio del usuario. Experiencias con el movimiento de objetos u objetos grandes deben prestar atención especial a movimiento, especialmente donde requieren movimiento frecuente a lo largo de los ejes horizontales y verticales.

## <a name="interaction-considerations"></a>Consideraciones sobre la interacción

Al igual que con el contenido, las interacciones en una experiencia de realidad mixta sin limitarse a lo que el usuario puede ver inmediatamente. Interacciones pueden tener lugar en cualquier lugar en el espacio real-world alrededor del usuario y estas interacciones pueden ayudar a animar a los usuarios desplazarse y experiencias de exploración.

### <a name="attention-directors"></a>Directores de atención

Que indica puntos de interés o interacciones principales pueden ser cruciales para los usuarios avanza a través de una experiencia. Se pueden dirigir atención del usuario y el movimiento del marco holográfico de formas sutiles o abrumador. Recuerde que debe equilibrar los directores de atención con períodos de exploración libre en mixed reality (especialmente al principio de una experiencia) para evitar sobrecargar el usuario. En general, hay dos tipos de directores de atención:
* **Directores visuales:** La manera más fácil de informar al usuario que deben mover en una dirección concreta es proporcionar una indicación visual. Esto puede hacerse a través de un efecto visual (por ejemplo, una ruta de acceso el usuario puede seguir visualmente hacia la parte siguiente de la experiencia) o incluso como flechas direccionales simple. Tenga en cuenta que cualquier indicador visual debe se basa en el entorno del usuario, no 'conectado' en el marco holográfico o el cursor.
* **Directores de audio:** [Sonido espacial](spatial-sound-design.md) puede proporcionar una manera eficaz para establecer los objetos en una escena (los usuarios de los objetos que entran en una experiencia de alertas) o para dirigir la atención a un momento específico en el espacio (para mover la vista del usuario hacia los objetos de clave). Uso de directores de audio para guiar la atención del usuario puede ser más sutiles y menos intrusivo que directores visuales. En algunos casos, puede ser mejor empezar con un director de audio y, después, pasar a un director visual si el usuario no reconoce la pila. También se pueden emparejar los directores de audio con directores visuales para el énfasis se ha agregado.

### <a name="commanding-navigation-and-menus"></a>Los comandos, navegación y menús

Las interfaces en las experiencias de realidad mixta lo ideal es que se emparejan estrechamente con el contenido digital controlan. Por lo tanto, menús flotantes de 2D a menudo no son ideales para la interacción y pueden ser difíciles para los usuarios cómodamente con dentro del marco holográfico. Para las experiencias que requiere que los elementos de interfaz como menús o campos de texto, considere el uso de un [método tag-along](billboarding-and-tag-along.md) seguir el marco holográfico tras un breve retraso. Evitar el bloqueo de contenido en el marco como una visualización preliminar, como esto puede estar desorientado para el usuario y el sentido de inmersión en otros objetos digitales en la escena de salto.

Como alternativa, considere la posibilidad de colocar los elementos de la interfaz directamente en específico del contenido de control, lo que permite las interacciones que ocurra en forma natural alrededor de espacio físico del usuario. Por ejemplo, dividir un menú complejo en partes independientes. Con cada botón o un grupo de controles que se adjunta al objeto específico que afecta la interacción. Para aprovechar aún más este concepto, considere el uso de [interactuable objetos](interactable-object.md).

### <a name="gaze-and-gaze-targeting"></a>Mirada y destinatarios de mirada

El marco holográfico presenta una herramienta para el desarrollador a las interacciones del desencadenador, así como evaluar dónde dwells la atención del usuario. [Que mirar](gaze.md) es uno de los [clave interacciones en HoloLens](interaction-fundamentals.md), donde se puede emparejar mirada con [gestos](gestures.md) (como con aire toque) o [voz](voice-input.md) (lo que permite más corto las interacciones de voz más naturales). Por lo tanto, esto hace que el marco holográfico un espacio para observar el contenido digital, así como interactuar con él. Si se llama la experiencia para interactuar con varios objetos alrededor de espacio del usuario (por ejemplo, seleccionando varios objetos alrededor de espacio del usuario con la mirada + gesto), considere la posibilidad de limitar la cantidad de encabezado necesario o desconexión de esos objetos en la vista del usuario movimiento para promover [comodidad](comfort.md).

Mirada también puede usarse para realizar un seguimiento de la atención del usuario a través de una experiencia y ver qué objetos o la mayor atención a de pago de las partes de la escena, el usuario. Esto puede resultar especialmente uso para la depuración de una experiencia, lo que permite herramientas analíticas, como mapas térmicos para ver donde los usuarios dedican más tiempo o faltan determinados objetos o la interacción. Mirada seguimiento también puede proporcionar una herramienta eficaz para facilitadores en experiencias (consulte la [cocina del Lowe](holographic-frame.md#lowes-kitchen) ejemplo).

## <a name="performance"></a>Rendimiento

El uso correcto del marco holográfico es fundamental para la [calidad del rendimiento](understanding-performance-for-mixed-reality.md) experiencias. Un desafío común technical (y facilidad de uso) está sobrecargando el marco del usuario con el contenido digital, generando un rendimiento de representación a disminuir. Tenga en cuenta el espacio alrededor del usuario completo en lugar de utilizar para organizar el contenido digital, mediante las técnicas se ha descrito anteriormente, para reducir la carga de procesamiento y garantizar la calidad de una visualización óptima.

Contenido digital dentro del marco de la HoloLens holográfico también se puede emparejar con la [plano estabilización](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md) para un rendimiento óptimo y [estabilidad holograma](hologram-stability.md).

## <a name="examples"></a>Ejemplos

### <a name="volvo-cars"></a>Automóviles Volvo

>[!VIDEO https://www.youtube.com/embed/DilzwF90vec]

En la experiencia de la sala de exposición de los automóviles Volvo, se invita a los clientes para obtener información sobre las capacidades de un nuevo automóvil en una experiencia de HoloLens guiados por un socio de Volvo. Volvo enfrentado a un reto con el marco holográfico: un automóvil grande es demasiado grande para colocar justo al lado de un usuario. La solución fue comenzar la experiencia con un punto de interés física, una tabla central en la sala de exposición, con un modelo más pequeño digital del automóvil colocado por encima de la tabla. Esto garantiza que el usuario está viendo el automóvil completo cuando se lance, lo que permite una sensación de descripción espacial de una vez que el automóvil crece a su escala del mundo real más adelante en la experiencia.

Volvo experiencia también facilita el uso de directores visuales, creación de un efecto visual cuánto tiempo desde el modelo de coche a pequeña escala en la tabla a una pared en la sala. Esto conduce a un efecto de "ventana mágicas", que muestra la vista completa del automóvil a una distancia, que ilustra las características adicionales del automóvil a escala real-world. El movimiento es horizontal, sin la interacción directa del usuario (en su lugar recopilación indicaciones de narración del socio de Volvo de la experiencia y visualmente).

### <a name="lowes-kitchen"></a>Cocina del Lowe

Una experiencia de almacén desde del Lowe invita a los clientes en un boceto a gran escala de una cocina para presentar varias oportunidades de remodelación tal como se muestra a través de la HoloLens. La cocina en el almacén proporciona físico telón de fondo para objetos digitales, un lienzo en blanco de dispositivos, mostradores y armarios para expandir la experiencia de realidad mixta.

Las superficies físico actúan como puntos de referencia estáticos para el usuario en masa a sí mismos en la experiencia, como asociación de un Lowe guía al usuario a través de las opciones de producto diferente y finaliza. De esta manera, la asociación verbalmente puede dirigir la atención del usuario a la 'refrigerador' o 'centro de la cocina' para la presentación de contenido digital.

![Asociación de un Lowe utiliza un Tablet PC para guiar a clientes a través de la experiencia de HoloLens.](images/loweskitchen-750px.jpg)<br>
*Asociación de un Lowe utiliza un Tablet PC para guiar a clientes a través de la experiencia de HoloLens.*

En parte, la experiencia del usuario se administra mediante una experiencia de Tablet PC controlada por la asociación del Lowe. Parte del rol del socio en este caso también sería limitar un movimiento principal excesivo, dirigir su atención sin problemas a través de los puntos de interés en la cocina. La experiencia de Tablet PC también proporciona a asociado del Lowe mirada datos en forma de una vista de mapa térmico de la cocina, ayuda a entender que el usuario es reposo (por ejemplo, en un área específica de muebles de cocina) con más precisión proporcionarles orientación de remodelación.

Para conocer más profunda experiencia de cocina del Lowe, consulte [discurso de apertura de Microsoft en Ignite 2016](https://www.youtube.com/watch?v=gC_4JxF0e_k).

### <a name="fragments"></a>Fragmentos

En los fragmentos de juegos de HoloLens, sala de estar se transforma en escena crime virtual que muestra pistas y pruebas, así como una sala de reunión virtual, donde hable con los caracteres que se encuentran en sus sillas y depender de las paredes.

![Se diseñó fragmentos llevará a cabo en casa de un usuario, con caracteres de interactuar con superficies y los objetos reales.](images/fragments-750px.jpg)<br>
*Se diseñó fragmentos llevará a cabo en casa de un usuario, con caracteres de interactuar con superficies y los objetos reales.*

Cuando los usuarios empezar inicialmente a la experiencia, se dado un breve período de ajuste, donde muy poca interacción es necesario, en su lugar animándoles a mire. Esto también ayuda a garantizar que la sala está correctamente asignada para el contenido interactivo del juego.

A lo largo de la experiencia, los caracteres se conviertan en puntos focal y actúan como directores visuales (principales movimientos entre caracteres, la activación para buscar o de gestos hacia las áreas de interés). El juego también se basa en más destacadas indicaciones visuales cuando un usuario tarda demasiado tiempo para buscar un objeto o suceso y hace un uso intensivo de audio espacial (especialmente con las voces de caracteres al escribir una escena).

### <a name="destination-mars"></a>Destino: MARS

En el destino: Experiencia de MARS se destaquen en [centro espacial de la NASA Kennedy](https://blogs.windows.com/devices/2016/09/19/hololens-experience-destination-mars-now-open-at-kennedy-space-center-visitor-complex/), visitantes han sido invitados en un viaje envolvente a la superficie de Mars, guiado por representación virtual de astronautas legendario Buzz Aldrín.

![Un Aldrín Buzz virtual se convierte en el punto focal para los usuarios de destino: MARS.](images/destinationmars-750px.png)<br>
*Un Aldrín Buzz virtual se convierte en el punto focal para los usuarios de destino: MARS.*

Como una experiencia realmente cautivadora, estos usuarios se les aconsejaba a un vistazo alrededor, mover su cabeza en todas las direcciones para ver el panorama marciano virtual. Aunque para asegurarse de que la comodidad de los usuarios, Aldrín Buzz narración y presencia virtual proporcionan un punto focal a lo largo de la experiencia. Esta grabación virtual rumores (creado por [Mixed Reality capturar Studios de Microsoft](https://www.microsoft.com/mixed-reality/capture-studios)) puede levantar al tamaño real, humano, en la esquina de la sala de lo que permite que los usuarios vean en contacto con él en la vista casi completa. Narración de rumores dirigido a los usuarios centrarse en distintos puntos en el entorno (por ejemplo, un conjunto de marciano es impresionante en el suelo o un intervalo de montaña en la distancia) con los cambios de escena concreta o los objetos descritos por él.

![Los narradores virtuales pasará a seguir el movimiento de un usuario, creación de un punto focal eficaz a lo largo de la experiencia.](images/gazereset-750px.png)<br>
*Los narradores virtuales pasará a seguir el movimiento de un usuario, creación de un punto focal eficaz a lo largo de la experiencia.*

La representación realista rumores proporciona un punto focal eficaces, junto con técnicas sutiles para activar los rumores sobre hacia el usuario a sentir está allí, hablando a usted. Cuando el usuario se mueve sobre la experiencia, rumores desplazará hacia usted con un umbral antes de volver a un estado neutro, si el usuario se desplaza demasiado lejos más allá de su periferia. Si el usuario tiene el aspecto de rumores completamente (por ejemplo, para ver algo en otra parte de la escena), después, vuelve a rumores, will de posición direccional del Narrador una vez que vuelva a centrarse en el usuario. Técnicas así proporcionan una idea de inmersión eficaz y crear un punto focal dentro del marco holográfico, lo que reduce el movimiento excesivo y promover [comodidad](comfort.md).

## <a name="see-also"></a>Vea también
* [Interacciones instintivas](interaction-fundamentals.md)
* [Comodidad](comfort.md)
* [Escalar](scale.md)
* [Control con la cabeza y permanencia](gaze-and-dwell.md)
* [Estabilidad de hologramas](hologram-stability.md)
