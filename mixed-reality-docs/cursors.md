---
title: Cursores
description: Un cursor, o indicador del vector de destino, proporciona comentarios continuos para que el usuario comprenda lo que HoloLens entiende sobre sus intenciones.
author: thetuvix
ms.author: alexturn, thgable
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (1ª generación), HoloLens 2, realidad mixta, cursores, destinatarios, mirados, gestos
ms.openlocfilehash: cdedcaffabe0f90e7956fdb19a7b85e202fcf403
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63526215"
---
# <a name="cursors"></a>Cursores

> [!NOTE]
> [Próximamente](index.md#news-and-notes) se ofrecerá orientación específica para HoloLens 2.


Un cursor, o indicador del vector de destino actual, proporciona comentarios continuos para que el usuario comprenda Dónde está el foco actual de HoloLens en ese momento. El cursor permite al usuario comprender su punto de destino actual y actúa como comentario para indicar qué área, holograma o punto responderá a la entrada. Es la representación digital de dónde el dispositivo entiende la atención del usuario (aunque es posible que no sea el mismo que determinar nada sobre sus intenciones).

Los comentarios proporcionados por el cursor ofrecen a los usuarios la posibilidad de anticiparse a cómo responderá el sistema, usar esa señal como comentario para comunicar mejor su intención al dispositivo y, en última instancia, tener más confianza sobre sus interacciones.

## <a name="hololens-1st-gen"></a>HoloLens (1.ª generación)

El destino del contenido de HoloLens (1ª generación) se realiza principalmente con el vector de [mirada](gaze.md) (un rayo controlado por la posición y la rotación del encabezado). Esto proporciona una forma de entrada directa para el usuario que necesita poca enseñanza. Sin embargo, los usuarios tienen dificultades para usar un centro de miración no marcado para orientaciones precisas, por lo que un cursor garantiza que los usuarios sepan el punto al que se dirigen actualmente. 


## <a name="positioning"></a>Posición

En general, el indicador debe moverse aproximadamente a una proporción 1:1 con movimiento de cabeza. Hay algunos casos en los que se puede usar la ganancia (aumento o disminución de la información de movimiento) como un mecánico intencionado, pero se producirá un problema para los usuarios si se usan de forma inesperada (tenga en cuenta que se recomienda un poco de retardo para que el cursor Evite problemas con contenido de visualización completamente bloqueado). Sin embargo, lo más importante es que las experiencias deben ser "honestos" en la representación de la posición del cursor: si se incluyen suavizado, magnetismo, ganancia u otros efectos, el sistema seguirá mostrando el cursor dondequiera que el sistema comprenda la posición, con los efectos incluidos. El cursor es la forma del sistema de indicar al usuario con qué puede interactuar o no, y no la forma de indicar al sistema.

Idealmente, el indicador debe bloquearse en profundidad a cualquier elemento al que el usuario pueda plausibly. Esto puede significar un bloqueo de superficie si hay una malla de [asignación espacial](spatial-mapping.md) o un bloqueo de la profundidad de cualquier elemento de interfaz de usuario "flotante", para ayudar al usuario a comprender con qué pueden interactuar en tiempo real.

## <a name="cursor-design-principles"></a>Principios de diseño de cursores

### <a name="always-present"></a>Siempre presente
* Se recomienda que el cursor esté siempre presente.
* Si el usuario no puede encontrar el cursor, se perderán.
* Las excepciones a esto son las instancias en las que tener un cursor proporciona una experiencia no óptima para el usuario. Un ejemplo es cuando un usuario ve un vídeo. El cursor no es deseable en este momento, ya que se encuentra en el centro del vídeo todo el tiempo. Se trata de un escenario en el que es posible que considere la posibilidad de hacer que el cursor solo esté visible cuando el usuario tenga su entrega, lo que indica que desea tomar medidas. De lo contrario, no está visible en el vídeo.

### <a name="cursor-scale"></a>Escala del cursor
* El cursor no debe ser mayor que los destinos disponibles, lo que permite a los usuarios interactuar fácilmente con el contenido y verlo.
* Dependiendo de la experiencia que cree, el escalado del cursor a medida que el usuario busca también es una consideración importante. Por ejemplo, a medida que el usuario mira más en su experiencia, es posible que el cursor no se convierta en demasiado pequeño para que se pierda.
* Al escalar el cursor, considere la posibilidad de aplicarle una animación de software a medida que le dé una sensación orgánica.
* Evite obstruir el contenido. Los hologramas son lo que hacen que la experiencia sea memorable y el cursor no debe apartarse de ellas.

### <a name="directionless-cursor"></a>Cursor no direccional
* Aunque no hay ninguna forma de cursor derecha, se recomienda usar una forma sin dirección como un toro u otra cosa. Un cursor que apunta en alguna dirección (por ejemplo, un cursor de flecha tradicional) puede confundir al usuario para que siempre mire ese modo.
* Una excepción a esto es cuando se usa el cursor para comunicar la instrucción de interacción al usuario. Por ejemplo, al escalar los hologramas en el shell de Windows Holographic, el cursor incluye de forma temporal flechas que ayudan a indicar al usuario Cómo trasladar la mano para escalar el holograma.

### <a name="look-and-feel"></a>Apariencia y funcionamiento
* Un anillo o cursor con forma de aro funciona con muchas aplicaciones.
* Elija un color y una forma que mejor represente la experiencia que va a crear.
* Los cursores son especialmente propensos a la [separación de colores](hologram-stability.md#color-separation).
* Un cursor pequeño con opacidad equilibrada mantiene informativa sin dominar la jerarquía visual.
* Tenga en Cognizant el uso de sombras o resaltados detrás del cursor, ya que podrían obstruir el contenido y distraerse del propósito.
* Los cursores deben alinearse con las superficies de la aplicación y Hug, lo que le dará la sensación de que el sistema puede ver dónde están buscando, pero también que el sistema es consciente de su entorno.
* Por ejemplo, en el sistema operativo Holographic de Windows, el cursor se alinea con las superficies del mundo del usuario, lo que crea un sentimiento de sensibilización del mundo incluso cuando el usuario no está mirando directamente a un holograma.
* Bloquear magnéticamente el cursor a un elemento interactivo cuando esté cerca de proximidad. Esto puede ayudar a mejorar la confianza de que el usuario interactuará con ese elemento cuando realice una acción de selección.

### <a name="visual-cues"></a>Indicaciones visuales
* Hay mucha información en nuestro mundo y con hologramas estamos agregando más información. Un cursor es una excelente manera de comunicarse con el usuario, lo que es importante.
* Si su experiencia se centra en un solo holograma, quizás el cursor Alinee y Hugs solo ese holograma y cambie de forma al mirar el holograma. Esto puede transmitir al usuario que el holograma es especial y que puede interactuar con él.
* Si la aplicación usa la asignación espacial, el cursor podría alinear y Hug cada superficie que ve. Esto proporciona comentarios a los usuarios de que HoloLens y su aplicación pueden ver su espacio.
* Estas cosas ayudan a reforzar el hecho de que los hologramas son reales y en nuestro mundo. Ayudan a salvar la brecha entre real y virtual.
* Tenga una idea de lo que debe hacer el cursor cuando no haya ningún holograma o superficie en la vista. Colocarlo a una distancia predeterminada delante del usuario es una opción.

## <a name="cursor-feedback"></a>Comentarios del cursor

Como hemos mencionado, es recomendable que el cursor esté siempre presente, ya que puede usar el cursor para transmitir algunos bits de información importantes.

### <a name="possible-actions"></a>Acciones posibles
* Como el usuario se Gazing en un holograma y el cursor se encuentra en ese holograma, podría usar el cursor para transmitir las acciones posibles en ese holograma.
* Podría mostrar un icono en el cursor por el que el usuario puede, por ejemplo, comprar ese elemento o quizás escalar ese holograma. O incluso algo tan sencillo como el holograma se puede aprovechar.
* Agregue solo información adicional sobre el cursor si significa algo al usuario. De lo contrario, es posible que los usuarios no perciban los cambios de estado u obtengan una confusión con el cursor.

### <a name="input-state"></a>Estado de entrada
* Podríamos usar el cursor para mostrar el estado de entrada del usuario. Por ejemplo, podríamos mostrar un icono que indica al usuario si el sistema ve su estado de mano. Esto le indicará al usuario que la aplicación sabe que el usuario está listo para realizar una acción.
* También podríamos usar el cursor para que el usuario tenga en cuenta que hay un comando de voz disponible. O quizás cambie el color del cursor momentáneamente para indicar al usuario que el sistema ha escuchado el comando de voz.

Estos Estados de cursor diferentes se pueden implementar de maneras diferentes. Puede implementar estos Estados diferentes modelando el cursor como una máquina de Estados. Por ejemplo:
* Estado de inactividad es donde se muestra el cursor predeterminado.
* El estado listo es cuando se ha detectado la mano del usuario en la posición listo.
* El estado de interacción es cuando el usuario realiza una interacción determinada.
* El estado de las acciones posibles es cuando se transmiten acciones posibles que se pueden realizar en un holograma.

También puede implementar estos Estados de forma que pueda mostrar distintos recursos artísticos cuando se detecten distintos Estados.

## <a name="going-cursor-free"></a>"Sin cursor"

Solo se recomienda diseñar sin un cursor cuando el sentido de la inmersión es un componente clave de una experiencia, y las interacciones que implican la finalización (a través de la mirada y el gesto) no requieren una gran precisión. Sin embargo, el sistema debe satisfacer las necesidades que normalmente se cumplen con un cursor, ya que proporciona a los usuarios comentarios continuos sobre el conocimiento de su destino y les ayuda a comunicar sus intenciones al sistema con confianza. Esto puede ser factible a través de otros cambios de estado perceptibles.

## <a name="see-also"></a>Vea también
* [Gestos](gestures.md)
* [Selección de destinos de la mirada](gaze-targeting.md)
