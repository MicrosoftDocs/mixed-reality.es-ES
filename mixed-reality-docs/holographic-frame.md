---
title: Marco holográfica
description: Los usuarios ven el mundo de la realidad mixta a través del marco holográfica.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, Windows Mixed Reality, marco holográfica, campo de vista
ms.openlocfilehash: 2145ba3b13bbd903299ad342292dfa8f5c05c023
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434645"
---
# <a name="holographic-frame"></a>Marco holográfica

Los usuarios ven el mundo de la realidad mixta a través de una ventanilla rectangular que funciona con el casco. En el dispositivo HoloLens, esta área rectangular se denomina trama holográfica y permite a los usuarios ver contenido digital superpuesto en el mundo real que les rodea. El diseño de experiencias optimizadas para el marco holográfica crea oportunidades, mitiga los desafíos y mejora la experiencia del usuario de las aplicaciones de realidad mixta.

## <a name="designing-for-content"></a>Diseño de contenido

A menudo, los diseñadores sienten la necesidad de limitar el ámbito de su experiencia a lo que el usuario puede ver de inmediato, sacrificando el escalado real para asegurarse de que el usuario ve un objeto en su totalidad. De igual forma, los diseñadores con aplicaciones complejas suelen sobrecargar el fotograma holográfica con contenido, abrumar a los usuarios con interacciones difíciles e interfaces abarrotadas. No es necesario que los diseñadores que crean contenido de realidad mixta limiten su experiencia directamente frente al usuario y en su vista inmediata. Si se asigna el mundo físico alrededor del usuario, todas estas superficies deben considerarse un lienzo potencial para interacciones y contenido digital. Un diseño adecuado de las interacciones y el contenido de una experiencia debe animar al usuario a desplazarse por el espacio, dirigir su atención al contenido clave y ayudar a ver todo el potencial de la realidad mixta.

Quizás la técnica más importante para animar el movimiento y la exploración dentro de una aplicación consiste en **permitir que los usuarios se ajusten a la experiencia**. Proporcione a los usuarios un breve período de tiempo de ' tarea ' sin el dispositivo. Esto puede ser tan sencillo como colocar un objeto en el espacio y permitir a los usuarios desplazarse por él o narrar una introducción a la experiencia. Este tiempo debe ser gratuito de cualquier tarea crítica o de gestos específicos (como el punteo aéreo), en su lugar para permitir que los usuarios puedan ver el contenido a través del dispositivo antes de requerir la interactividad o avanzar por las fases de la aplicación. Si se trata de la primera vez que el usuario tiene el dispositivo, esto es especialmente importante, ya que se siente cómodo viendo el contenido a través del marco holográfica y la naturaleza de los hologramas.

### <a name="large-objects"></a>Objetos grandes

A menudo, el contenido al que llama una experiencia, especialmente el contenido del mundo real, será mayor que el fotograma holográfica. Los objetos que normalmente no caben en el marco holográfica deben reducirse para ajustarse cuando se introducen por primera vez (ya sea a una escala más pequeña o a una distancia). La clave consiste en **permitir a los usuarios ver el tamaño completo del objeto** antes de que la escala desborda el fotograma. Por ejemplo, se debe mostrar un elefante de holográfica para que quepa completamente dentro del marco, lo que permite a los usuarios formar una comprensión espacial de la forma global del animal, antes de ajustarla a la [escala del mundo real](scale.md) cerca del usuario.

Teniendo en cuenta el tamaño completo del objeto, los usuarios tienen una expectativa de dónde desplazarse y buscar partes concretas de ese objeto. Del mismo modo, en una experiencia con contenido envolvente, puede resultar útil tener alguna manera de volver a consultar el tamaño completo de ese contenido. Por ejemplo, si la experiencia implica caminar en torno a un modelo de una casa virtual, puede ayudar a tener una versión más pequeña del tamaño de la casa de las muñecas de la experiencia que los usuarios pueden desencadenar para entender dónde se encuentran dentro de la casa.

Para ver un ejemplo del diseño de objetos grandes, consulte [Volvo Cars](holographic-frame.md#volvo-cars).

### <a name="many-objects"></a>Muchos objetos

Las experiencias con muchos objetos o componentes deben considerar la posibilidad de usar el espacio completo alrededor del usuario para evitar abarrotar el marco holográfica directamente delante del usuario. En general, se recomienda introducir el contenido en una experiencia lentamente y esto es especialmente cierto con experiencias que tienen previsto atender muchos objetos al usuario. Al igual que con los objetos grandes, la clave consiste en **permitir que los usuarios conozcan el diseño del contenido** de la experiencia, lo que les ayuda a obtener una comprensión espacial de lo que están alrededor de ellos, ya que el contenido se agrega a la experiencia.

Una técnica para lograrlo es proporcionar puntos persistentes (también conocidos como puntos de referencia) en la experiencia que delimita el contenido en el mundo real. Por ejemplo, un punto de referencia podría ser un objeto físico en el mundo real, como una tabla en la que aparece contenido digital, o un objeto digital, como un conjunto de pantallas digitales donde aparece el contenido con frecuencia. Los objetos también se pueden colocar en el periferia del marco holográfica para animar al usuario a buscar contenido clave, mientras que la detección de contenido más allá de la periferia puede ser asistida por [directores de atención](holographic-frame.md#attention-directors).

La colocación de objetos en la periferia puede animar a los usuarios a mirar al lado y esto puede ser asistido por directores de atención, como se describe a continuación.

<br>

---

## <a name="user-comfort"></a>Comodidad del usuario

En el caso de experiencias de realidad mixta con objetos grandes o muchos objetos, es fundamental tener en cuenta la cantidad de movimiento de cabeza y cuello necesaria para interactuar con el contenido. Las experiencias pueden dividirse en tres categorías en términos de movimiento principal: **horizontal** (lateral a lado), **vertical** (arriba y abajo) o **envolvente** (horizontal y vertical). Siempre que sea posible, limite la mayoría de las interacciones a las categorías horizontal o vertical, idealmente con la mayoría de las experiencias que tienen lugar en el centro del marco holográfica mientras el encabezado del usuario está en una posición neutra. Evite las interacciones que hagan que el usuario mueva su vista constantemente a una posición de encabezado no natural (por ejemplo, siempre buscando tener acceso a una interacción del menú clave).

![región óptima del contenido es de 0 a 35 grados por debajo del horizonte](images/optimal-field-of-view-2.png)<br>
*La región óptima del contenido es de 0 a 35 grados por debajo del horizonte*

El movimiento horizontal del cabezal es más [cómodo](comfort.md) para interacciones frecuentes, mientras que los movimientos verticales se deben reservar para eventos poco comunes. Por ejemplo, una experiencia que implique una escala de tiempo horizontal larga debe limitar el movimiento del cabezal vertical para las interacciones (como la búsqueda en un menú).

Considere la posibilidad de promover el movimiento del cuerpo completo, en lugar de simplemente el movimiento del encabezado, colocando objetos alrededor del espacio del usuario. Las experiencias con objetos móviles o de gran tamaño deben prestar especial atención al movimiento principal, sobre todo cuando requieren un movimiento frecuente a lo largo de los ejes horizontal y vertical.

<br>

---

## <a name="interaction-considerations"></a>Consideraciones sobre la interacción

Como sucede con el contenido, las interacciones en una experiencia de realidad mixta no deben limitarse a lo que el usuario puede ver inmediatamente. Las interacciones pueden tener lugar en cualquier parte del espacio real del usuario y estas interacciones pueden ayudar a animar a los usuarios a desplazarse y explorar experiencias.

### <a name="attention-directors"></a>Directores de atención

Indicar puntos de interés o interacciones clave puede ser fundamental para progresar a los usuarios a través de una experiencia. La atención del usuario y el movimiento del marco holográfica se pueden dirigir de maneras sutiles o pesadas. Recuerde equilibrar los directores de atención con períodos de exploración gratuita en realidad mixta (especialmente al principio de una experiencia) para evitar abrumar al usuario. En general, hay dos tipos de directores de atención:
* **Directores visuales:** La manera más sencilla de dejar que el usuario sepa que deben moverse en una dirección específica es proporcionar una indicación visual. Esto puede hacerse a través de un efecto visual (por ejemplo, una ruta de acceso que el usuario puede seguir visualmente hacia la siguiente parte de la experiencia) o incluso como flechas direccionales simples. Tenga en cuenta que cualquier indicador visual debe basarse en el entorno del usuario, no en "conectado" al fotograma holográfica o al cursor.
* **Directores de audio:** el [sonido espacial](spatial-sound-design.md) puede proporcionar una manera eficaz de establecer objetos en una escena (avisar a los usuarios de los objetos que entran en una experiencia) o dirigir la atención a un punto específico en el espacio (para trasladar la vista del usuario hacia los objetos clave). El uso de los directores de audio para guiar la atención del usuario puede ser más sutil y menos intrusivo que los directores visuales. En algunos casos, puede ser mejor empezar con un director de audio y, a continuación, pasar a un director visual si el usuario no reconoce la pila. Los directores de audio también se pueden emparejar con los directores visuales para enfatizar.

### <a name="commanding-navigation-and-menus"></a>Comandos, navegación y menús

Idealmente, las interfaces de experiencias de realidad mixta se emparejan con el contenido digital que controlan. Como tal, los menús de 2D flotantes a menudo no son ideales para la interacción y pueden resultar difíciles de usar en el interior del marco holográfica. En el caso de experiencias que requieren elementos de interfaz como menús o campos de texto, considere la posibilidad de usar un [método de etiqueta](billboarding-and-tag-along.md) para seguir el marco holográfica tras un breve retraso. Evite el bloqueo del contenido en el marco como una pantalla emergente, ya que esto se puede desorientar al usuario e interrumpir el sentido de inmersión para otros objetos digitales de la escena.

Como alternativa, considere la posibilidad de colocar los elementos de la interfaz directamente en el contenido específico que controlan, lo que permite que las interacciones se realicen de forma natural en torno al espacio físico del usuario. Por ejemplo, divida un menú complejo en partes independientes. Con cada botón o grupo de controles adjuntos al objeto específico al que afecta la interacción. Para seguir este concepto, considere el uso de [objetos](interactable-object.md)interactivos.

### <a name="gaze-and-gaze-targeting"></a>Destinar y mirar hacia abajo

El marco holográfica presenta una herramienta para que el desarrollador desencadene las interacciones, así como evaluar dónde se encuentra la atención de un usuario. [Mira](gaze-and-commit.md) una de las [interacciones clave de HoloLens](interaction-fundamentals.md), en la que la mirada se puede emparejar con [gestos](gaze-and-commit.md#composite-gestures) (por ejemplo, con el toque de aire) o con la [voz](voice-input.md) (lo que permite realizar interacciones más cortas y naturales basadas en voz). Por lo tanto, esto hace que el marco holográfica sea un espacio para observar el contenido digital, así como para interactuar con él. Si la experiencia llama para interactuar con varios objetos en torno al espacio del usuario (por ejemplo, selección múltiple de objetos alrededor del espacio del usuario con el gesto de miras +), considere la posibilidad de colocar dichos objetos en la vista del usuario o limitar la cantidad de encabezado necesaria. movimiento para promover la [comodidad del usuario](comfort.md).

Fijamente también puede usarse para realizar un seguimiento de la atención del usuario a través de una experiencia y ver los objetos o partes de la escena a los que el usuario pagó más la atención. Esto puede usarse especialmente para depurar una experiencia, lo que permite herramientas analíticas como mapas térmicos para ver dónde los usuarios están gastando más tiempo o faltan determinados objetos o interacción. El seguimiento de la mirada también puede proporcionar una herramienta eficaz para facilitar la experiencia (vea el ejemplo de [cocina de Lowe](holographic-frame.md#lowes-kitchen) ).

<br>

---

## <a name="performance"></a>Rendimiento

El uso correcto del marco holográfica es fundamental para las experiencias de [calidad del rendimiento](understanding-performance-for-mixed-reality.md) . Un desafío técnico (y facilidad de uso) común es la sobrecarga del marco del usuario con contenido digital, lo que hace que se reduzca el rendimiento de la representación. En su lugar, considere la posibilidad de usar el espacio completo alrededor del usuario para organizar el contenido digital, con las técnicas descritas anteriormente, para reducir la carga de representación y garantizar una calidad de visualización óptima.

El contenido digital dentro del marco holográfica de HoloLens también se puede emparejar con el [plano de estabilización](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md) para obtener un rendimiento óptimo y una [estabilidad de holograma](hologram-stability.md).

<br>

---

## <a name="examples"></a>Ejemplos

### <a name="volvo-cars"></a>Volvo automóviles

<iframe width="940" height="530" src="https://www.youtube.com/embed/DilzwF90vec" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

En la experiencia de la sala de exposición de Volvo Cars, se invita a los clientes a obtener información sobre las capacidades de un automóvil nuevo en una experiencia de HoloLens guiada por un Volvo Associate. Volvo se enfrentó a un reto con el marco holográfica: un coche de tamaño completo es demasiado grande para colocarlo justo junto a un usuario. La solución era comenzar la experiencia con un punto de referencia físico, una tabla central en la sala de exposición, con un modelo digital más pequeño del coche colocado en la parte superior de la tabla. Esto garantiza que el usuario vea el coche completo cuando se introduce, lo que permite una idea de la comprensión espacial una vez que el coche crece hasta su escala real más adelante en la experiencia.

La experiencia de Volvo también hace uso de los directores visuales, lo que crea un efecto visual largo a partir del modelo de automóvil a pequeña escala de la tabla en una pared del salón. Esto conduce a un efecto de "ventana mágica", que muestra la vista completa del coche a una distancia, con lo que se ilustran otras características del coche a escala real. El movimiento del cabezal es horizontal, sin ninguna interacción directa del usuario (en lugar de recopilar las indicaciones visualmente y de la narración de Volvo Associate de la experiencia).

<br>

---

### <a name="lowes-kitchen"></a>Cocina de Lowe

Una experiencia del almacén de Lowe invita a los clientes a un boceto a gran escala de una cocina para presentar varias oportunidades de remodelado, como se muestra a través de HoloLens. La cocina de la tienda proporciona un telón de fondo físico para objetos digitales, un lienzo en blanco de dispositivos, contrapartes y archivadores para que la experiencia de realidad mixta se desmezcle.

Las superficies físicas actúan como puntos de referencia estáticos para el usuario en la experiencia, ya que la Asociación de un Lowe guía al usuario a través de diferentes opciones de producto y finaliza. De esta manera, el asociado puede dirigir verbalmente la atención del usuario al "frigorífico" o "centro de la cocina" para presentar el contenido digital.

![una asociación de Lowe usa una tableta para guiar a los clientes a través de la experiencia de HoloLens.](images/loweskitchen-750px.jpg)<br>
*Una asociación de Lowe usa una tableta para guiar a los clientes a través de la experiencia de HoloLens.*

La experiencia del usuario se administra, en parte, mediante una experiencia de tableta controlada por el asociado de Lowe. En este caso, parte del rol del asociado también sería limitar el movimiento excesivo del cabezal y dirigir su atención sin problemas a través de los puntos de interés de la cocina. La experiencia de Tablet PC también proporciona la Asociación del Lowe con los datos de fijamente en forma de una vista mapa térmico de la cocina, lo que ayuda a comprender dónde está el usuario (por ejemplo, en un área concreta de armario) para proporcionarle instrucciones de remodelado con más precisión.

Para obtener una visión más profunda de la experiencia de cocina de Lowe, consulte el [discurso de Microsoft en encendido 2016](https://www.youtube.com/watch?v=gC_4JxF0e_k).

<br>

---

### <a name="fragments"></a>Fragmentos

En los fragmentos de juegos de HoloLens, el salón se transforma en una escena de crímenes virtuales que muestra pistas y evidencias, así como en una sala de reuniones virtual, en la que se habla de caracteres que se encuentran en sus sillas y que se inclinan en las paredes.

![fragmentos se diseñaron para que se realizaran en el inicio de un usuario, con caracteres que interactúan con superficies y objetos del mundo real.](images/fragments-750px.jpg)<br>
*Los fragmentos se diseñaron para que se realizaran en el inicio de un usuario, con caracteres que interactúan con superficies y objetos del mundo real.*

Cuando los usuarios inician la experiencia inicialmente, se les da un breve período de ajuste, donde se requiere muy poca interacción, en su lugar para que se examinen. Esto también ayuda a garantizar que el salón está correctamente asignado para el contenido interactivo del juego.

A lo largo de la experiencia, los caracteres se convierten en puntos focales y actúan como directores visuales (movimientos principales entre caracteres, lo que se centra en la apariencia o el movimiento hacia las áreas de interés). El juego también se basa en indicaciones visuales más destacadas cuando un usuario tarda demasiado tiempo en encontrar un objeto o un evento y hace un uso intensivo del audio espacial (especialmente con voces de caracteres al escribir una escena).

<br>

---

### <a name="destination-mars"></a>Destino: Mars

En el destino: la experiencia de Mars destacada en el [centro de espacio](https://blogs.windows.com/devices/2016/09/19/hololens-experience-destination-mars-now-open-at-kennedy-space-center-visitor-complex/)de la NASA, los visitantes fueron invitados a una carrera envolvente hacia la superficie de Mars, guiada por la representación virtual de legendarias Astronaut.

![un Aldrin de rumores virtual se convierte en el punto focal de los usuarios en el destino: Mars.](images/destinationmars-750px.png)<br>
*Un Aldrin de rumores virtual se convierte en el punto focal de los usuarios en el destino: Mars.*

Como experiencia envolvente, se recomienda que estos usuarios examinen, moviendo su cabeza en todas las direcciones para ver el panorama de la Martian virtual. Aunque para garantizar la comodidad de los usuarios, la narración de Aldrin y la presencia virtual ofrecían un punto focal a lo largo de la experiencia. Esta grabación virtual de los rumores (creados por los [estudios de captura de realidad mixta de Microsoft](https://www.microsoft.com/mixed-reality/capture-studios)) se encuentra en el tamaño real y humano, en la esquina de la habitación, lo que permite a los usuarios verlos en vista casi completa. La narración de los rumores dirige a los usuarios para que se centren en diferentes puntos del entorno (por ejemplo, un conjunto de Rocks Martian en el piso o en una gama de montaña de la distancia) con cambios de escenas específicos u objetos introducidos por él.

![los narradores virtuales van a seguir el movimiento de un usuario, creando un punto focal eficaz a lo largo de la experiencia.](images/gazereset-750px.png)<br>
*Los narradores virtuales se convertirán a seguir el movimiento de un usuario, creando un punto focal eficaz a lo largo de la experiencia.*

La representación realista de los rumores proporcionó un punto focal eficaz, junto con técnicas sutiles para convertir los rumores al usuario como si estuviera allí, hablando. A medida que el usuario se mueve sobre la experiencia, los zumbidos pasarán a un umbral antes de volver a un estado neutro si el usuario se mueve demasiado allá de la periferia. Si el usuario mira por los rumores por completo (por ejemplo, para ver algo en otro lugar de la escena) y, a continuación, vuelve a rumores, la posición direccional del narrador volverá a centrarse en el usuario. Las técnicas como esta proporcionan una gran sensación de inmersión y creación de un punto focal dentro del marco holográfica, lo que reduce el movimiento excesivo y promueve la [comodidad del usuario](comfort.md).

## <a name="see-also"></a>Consulta también
* [Interacciones instintivas](interaction-fundamentals.md)
* [Comodidad](comfort.md)
* [Escalar](scale.md)
* [Control con la cabeza y permanencia](gaze-and-dwell.md)
* [Estabilidad de hologramas](hologram-stability.md)
