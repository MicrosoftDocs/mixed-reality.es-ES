---
title: Cursores
description: Un cursor, o un indicador de su vector de destinatarios, proporciona comentarios continuos para el usuario a entender lo que comprende HoloLens sobre sus intenciones.
author: thetuvix
ms.author: alexturn, thgable
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (gen 1), 2 de HoloLens, Mixed Reality, cursores, como destino, mirada, gestos
ms.openlocfilehash: cdedcaffabe0f90e7956fdb19a7b85e202fcf403
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605695"
---
# <a name="cursors"></a>Cursores

> [!NOTE]
> Obtener información más específica de HoloLens 2 [próximamente](index.md#news-and-notes).


Un cursor, o un indicador de su vector de destino actual, proporciona comentarios continuos para el usuario a entender dónde cree HoloLens que centran actualmente está en ese momento. El cursor permite que los usuarios comprender su destino actual de punto y responderá actúa como comentarios para indicar qué área, holograma o punto de entrada. Es el digital representación en forma de que el dispositivo entiende la atención del usuario para ser (aunque no puede ser el mismo que determinar nada acerca de sus intenciones).

La información proporcionada por el cursor ofrece a los usuarios la capacidad para prever cómo responderá con el sistema, use esa señal como comentarios para comunicar mejor su propósito para el dispositivo y en última instancia puedan confiar más en sus interacciones.

## <a name="hololens-1st-gen"></a>HoloLens (gen 1)

Destinos del contenido en HoloLens (gen 1) se realiza principalmente con la [que mirar](gaze.md) vector (un rayo controlado por la posición y rotación de la cabeza). Esto proporciona un formulario de entrada directa del usuario que necesita en la docencia poco. Sin embargo, los usuarios tienen dificultades para usar un centro de mirada no marca para el destino preciso para que un cursor garantiza que los usuarios sepan lo que actualmente como destino. 


## <a name="positioning"></a>Posición

En general, debe mover el indicador en aproximadamente una proporción 1:1 con un movimiento principal. Hay algunos casos donde la ganancia (aumentar o disminuir notablemente movimiento) podría usarse como un mecánico intencionado, pero provocará problemas cuando los usuarios si se usa de forma inesperada (tenga en cuenta que hay una pequeña cantidad de recomendado para que el cursor evitar problemas con 'lag' totalmente bloqueado para mostrar contenido). Lo más importante experiencias deben ser "honestos" en la representación de la posición del cursor - si suavizado magnética, obtención, sin embargo, o se incluyen otros efectos, el sistema debe mostrar siempre que sea descripción del sistema de posición, con los que el cursor incluidos los efectos. El cursor de forma del sistema de indicarle al usuario lo pueden o no puede interactuar con forma de no del usuario de indicando al sistema.

Lo ideal es que debe bloquear el indicador en profundidad para los elementos que posiblemente puede tener como destino el usuario. Esto puede significar la superficie de bloqueo si hubiera alguna [asignación espacial](spatial-mapping.md) malla o bloqueo de la profundidad de los elementos de interfaz de usuario "flotantes", para ayudar al usuario a entender lo que pueden interactuar en tiempo real.

## <a name="cursor-design-principles"></a>Principios de diseño de cursor

### <a name="always-present"></a>Siempre presente
* Se recomienda que el cursor siempre está presente.
* Si el usuario no encuentra el cursor, está perdidos.
* Excepciones a esto son las instancias donde tiene un cursor, proporciona una experiencia poco óptimo para el usuario. Un ejemplo es cuando un usuario está viendo un vídeo. El cursor se convierte en no deseado en este punto se encuentra en medio de vídeo de todo el tiempo. Este es un escenario donde puede hacer que el cursor solo es visible cuando el usuario tiene su mano señalar un deseo de actuar. En caso contrario, no es visible en el vídeo.

### <a name="cursor-scale"></a>Escala de cursor
* El cursor debe ser mayor que los destinos disponibles, lo que permite a los usuarios interactuar con facilidad y ver el contenido.
* Dependiendo de la experiencia de que crear, el escalado del cursor, ya que el usuario busca en torno a también es una consideración importante. Por ejemplo, como el usuario busca más alejada de su experiencia quizás el cursor debe no resultar demasiado pequeño tal que su pérdida.
* Cuando el cursor de ajuste de escala, considere la posibilidad de aplicar una animación suave a él mientras se escala a lo que ofrece una sensación orgánica.
* Evite obstrucción de contenido. Hologramas son lo que la experiencia fácil de recordar y no se debe tomar el cursor fuera de ellas.

### <a name="directionless-cursor"></a>Cursor sin rumbo
* Aunque no hay ninguna forma cursor derecho, se recomienda que utilice una forma indirecta, como un toro o algo más. Un cursor que señala en alguna dirección (p. ej.: un cursor de flecha tradicionales) puede confundir al usuario siempre se ve igual.
* Una excepción a esto es cuando se usa el cursor para comunicar instrucciones de interacción para el usuario. Por ejemplo, al escalar hologramas en el shell de Windows Holographic, el cursor incluye temporalmente las flechas que ayudan a indicar al usuario sobre cómo mover la mano para escalar el holograma.

### <a name="look-and-feel"></a>Apariencia y comportamiento
* Un anillo o ARO en forma de cursor funciona para muchas aplicaciones.
* Elija un color y la forma que mejor represente la experiencia que se va a crear.
* Los cursores son especialmente proclives a [separación de colores](hologram-stability.md#color-separation).
* Un pequeño cursor con opacidad equilibrada mantiene informativo sin que dominan a la jerarquía visual.
* Estar al corriente de usar sombras o resaltados detrás de su cursor, ya que podrían obstruirá el contenido y distraer el propósito.
* Los cursores deben alinearse con y Abrazo las superficies de la aplicación, esto dará al usuario una sensación de que el sistema puede ver que busca, sino también que el sistema tiene constancia de su entorno.
* Por ejemplo, en el SO Windows Holographic, el cursor se alinea con las superficies del mundo del usuario, crear una sensación de reconocimiento del mundo, incluso cuando el usuario no está mirando directamente un holograma...
* Bloqueo magnéticamente el cursor a un elemento interactivo cuando está dentro de cerca. Esto puede ayudar a aumentar la confianza que el usuario interactuará con ese elemento cuando realicen una acción de selección.

### <a name="visual-cues"></a>Indicaciones visuales
* Hay mucha información en nuestro mundo y con hologramas estamos agregando más información. Un cursor es una excelente manera de comunicar al usuario, lo que es importante.
* Si su experiencia se centra en un único holograma, a continuación, quizás el cursor alinea y bloquea sólo la que los cambios y holograma forma al examinar fuera de ese holograma. Esto puede indicar al usuario que el holograma es especial y pueden interactuar con él.
* Si la aplicación utiliza la asignación espacial, el cursor se pudo alinear y Abrazo a cada superficie ve. Esto proporciona comentarios a los usuarios que HoloLens y la aplicación puede ver su espacio.
* Estas cosas ayudan a reforzar el hecho de que hologramas son reales y en nuestro mundo. Ayudan a salvar la brecha entre reales y virtuales.
* Tener una idea de lo que debe hacer el cursor cuando no hay hologramas o superficies en la vista. Colocarlo a una distancia delante del usuario predeterminada es una opción.

## <a name="cursor-feedback"></a>Comentarios del cursor

Como hemos mencionado, es recomendable que el cursor esté siempre presente, que se puede usar el cursor para transmitir algunos fragmentos de información importantes.

### <a name="possible-actions"></a>Acciones posibles
* Como el usuario es gazing en un holograma y el cursor está en esa holograma, podría utilizar el cursor para transmitir las acciones posibles en esa holograma.
* Podría mostrar un icono en el cursor que el usuario puede comprar como elemento o quizás escalables que holograma. O incluso algo tan sencillo como el holograma puede ser puntea en.
* Agregar sólo la información adicional en el cursor si significa algo al usuario. En caso contrario, los usuarios pueden o no tenga en cuenta los cambios de estado o confundirán el cursor.

### <a name="input-state"></a>Estado de entrada
* Podríamos usar el cursor para mostrar el estado de la entrada del usuario. Por ejemplo, podríamos mostramos un icono que indica al usuario si el sistema ve su estado de la mano. Esto indicará al usuario que la aplicación sepa que el usuario está preparado para tomar medidas.
* También podríamos usar el cursor para que el usuario tenga en cuenta que hay un comando de voz. O quizás cambiar el color del cursor momentáneamente para indicar al usuario que el comando de voz se ha oído por el sistema.

Estos estados diferentes de cursor pueden implementarse de maneras diferentes. Podría implementar estos estados diferentes al modelar el cursor, como una máquina de Estados. Por ejemplo:
* Estado de inactividad es que muestra el cursor predeterminado.
* Estado listo es cuando se ha detectado la mano del usuario en la posición de la lista.
* Estado de interacción es cuando el usuario realiza una interacción determinada.
* Estado de las acciones posibles es cuando transmiten las posibles acciones que se pueden realizar en un holograma.

También puede implementar estos Estados de una manera capaz de máscara de forma que puede mostrar activos gráficos diferentes cuando se detectan los estados diferentes.

## <a name="going-cursor-free"></a>Vaya a "libre de cursor"

Se recomienda diseñar sin un cursor sólo cuando el sentido de inmersión es un componente clave de una experiencia y las interacciones que implican destinatarios (a través de mirada y gesto) no requieren una precisión excelente. El sistema debe cumplir las necesidades que se cumplen, normalmente mediante un cursor aunque - proporcionar comentarios continuos en la descripción del sistema de sus destinatarios a los usuarios y ayudarles a comunicarse con confianza sus intenciones al sistema. Esto puede lograrse a través de otros cambios de estado apreciable.

## <a name="see-also"></a>Vea también
* [Gestos](gestures.md)
* [Mirada destinadas a](gaze-targeting.md)
