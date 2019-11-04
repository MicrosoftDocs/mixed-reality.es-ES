---
title: Miras y confirmaciones
description: 'Información general sobre el modelo de entrada "mirar y confirmar": uso de la entrada de ojo o del cabezal.'
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Realidad mixta, premiración, destino, interacción, diseño, seguimiento ocular, seguimiento del cabezal
ms.openlocfilehash: df152f6a3a6e4ae2d6c32a0c56fbb615bcfa7aa8
ms.sourcegitcommit: a5dc182da237f63f0487d40a2e11894027208b6c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/02/2019
ms.locfileid: "73441127"
---
# <a name="gaze-and-commit"></a>Miras y confirmaciones

La acción de _mirar y confirmar_ es un modelo de entrada fundamental que está estrechamente relacionado con la forma en que estamos interactuando con nuestros equipos mediante el mouse: _punto & clic_.
En esta página, se presentan dos tipos de entradas de miradas (de encabezado y ojo) y distintos tipos de acciones de confirmación. 
La acción de _mirar y confirmar_ se considera un modelo de entrada lejano con manipulación indirecta.
Esto significa que es mejor usar para interactuar con el contenido holográfica que no está disponible.

Los auriculares de realidad mixta pueden usar la posición y la orientación del encabezado del usuario para determinar su vector de dirección principal. Se puede considerar como un láser que apunta en línea recta directamente desde el punto situado entre los ojos del usuario. Esto es una aproximación bastante general de dónde mira el usuario. La aplicación puede formar una intersección con este rayo con objetos virtuales o del mundo real, y dibujar un cursor en esa ubicación para que el usuario sepa lo que tienen como destino actualmente.

Además de los cabezales, algunos auriculares de realidad mixta, como HoloLens 2, incluyen sistemas de seguimiento ocular que producen un vector de mirada ocular. Esto proporciona una medida específica de adónde mira el usuario. En ambos casos, la mirada representa una señal importante para la intención del usuario. Cuanto mejor sea el sistema para interpretar y predecir las acciones previstas del usuario, aumentará la satisfacción del usuario y se mejorará el rendimiento.

A continuación se muestran algunos ejemplos de cómo puede beneficiarse de un desarrollador de realidad mixta con miras a la mirada:
* La aplicación puede intersectar con los hologramas de la escena para determinar dónde se encuentra la atención del usuario (con más precisión con miras).
* La aplicación puede encargarse de los gestos y las pulsaciones del controlador en función de la mirada del usuario, lo que permite al usuario seleccionar, activar, capturar, desplazarse o interactuar de otro modo con sus hologramas.
* La aplicación puede permitir que el usuario coloque hologramas en superficies del mundo real intersectando su rayo con la malla de asignación espacial.
* La aplicación puede saber si el usuario *no* está buscando la dirección de un objeto importante, lo que puede conducir a que la aplicación proporcione indicaciones visuales y de audio para activar dicho objeto.

<br>


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
        <td>Mirada con la cabeza y confirmación</td>
        <td>✔️ Se recomienda</td>
        <td>✔️ Recomendado (tercera opción: <a href="interaction-fundamentals.md">Ver las demás opciones</a>)</td>
        <td>➕ Opción alternativa</td>
    </tr>
         <tr>
        <td>Mirada con los ojos y confirmación</td>
        <td>❌ no disponible</td>
        <td>✔️ Recomendado (tercera opción: <a href="interaction-fundamentals.md">Ver las demás opciones</a>)</td>
        <td>❌ no disponible</td>
    </tr>
</table>


## <a name="gaze"></a>Mirar

### <a name="eye--or-head-gaze"></a>¿Está atento o mira la cabeza?
Hay varias consideraciones que hay que tener en cuenta cuando se enfrenta a la pregunta si debe usar el modelo de entrada "mira fijamente y confirmar" o "mirarnos y confirmar". Si va a desarrollar para un casco envolvente o para HoloLens (1ª generación), la elección es sencilla: encabezado y confirmación. Si está desarrollando para HoloLens 2, la elección es un poco más difícil, por lo que es importante comprender las ventajas y los desafíos que acompañan a cada uno de ellos.
Hemos compilado algunos grandes Pro y con en la tabla siguiente para diferenciar las orientaciones de mirada y miradas. Esta información es muy completa y le sugerimos que obtenga más información sobre el objetivo de mirarnos en la realidad mixta aquí:
* [Seguimiento ocular de hololens 2](eye-tracking.md): introducción general de nuestra nueva funcionalidad de seguimiento ocular en hololens 2, que incluye algunas instrucciones para desarrolladores. 
* [Interacción ocular](eye-gaze-interaction.md): consideraciones de diseño y recomendaciones cuando se planea usar el seguimiento ocular como entrada.

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><strong>Apuntar a la mirada</strong></td>
        <td><strong>Destino de la mirada</strong></td>
    </tr>
    <tr>
        <td>Fast!</td>
        <td>Lentamente</td>
    </tr>
    <tr>
        <td>Bajo esfuerzo (apenas se necesitan movimientos del cuerpo)</td>
        <td>Puede ser fatiguing (por ejemplo, la presión del cuello)</td>
    </tr>
    <tr>
        <td>No requiere un cursor, pero se recomiendan comentarios sutiles</td>
        <td>Requiere para mostrar un cursor</td>
    </tr>
    <tr>
        <td>Sin movimientos sin problemas oculares (por ejemplo, no buenos para dibujar)</td>
        <td>Más controlado y explícito</td>
    </tr>
    <tr>
        <td>Difícil para destinos muy pequeños (por ejemplo, botones pequeños o weblinks)</td>
        <td>Estable! ¡ Gran retroceso!</td>
    </tr>
    <tr>
        <td>...</td>
        <td>...</td>
    </tr>
</table>

Tanto si usa la vista de encabezado o miras hacia abajo para el modelo de entrada de premiras y confirmaciones, incluye diferentes conjuntos de restricciones de diseño, que se tratarán por separado en los artículos de [mira](gaze-and-commit-eyes.md) y de la [mirada y el](gaze-and-commit-head.md) dedo.

<br>

---

### <a name="cursor"></a>Cursor

:::row:::
    :::column:::
        En el caso de la mirada, la mayoría de las aplicaciones deben usar un [cursor](cursors.md) (u otra indicación visual o de auditoría) para dar a la confianza del usuario en qué está a punto de interactuar. Normalmente, este cursor se coloca en el mundo en el que su rayo de miras hacia abajo intersecta primero con un objeto, que puede ser un holograma o una superficie del mundo real.<br>
        <br>
        En general, se recomienda *no* mostrar un cursor, ya que esto puede resultar más rápido y molesto para el usuario. En su lugar, resalte los destinos visuales de forma sutilmente o use un cursor de ojo muy débil para proporcionar confianza sobre lo que el usuario está a punto de interactuar. Para obtener más información, consulte nuestra [Guía de diseño para la entrada basada en ojo](eye-tracking.md) en HoloLens 2.
    :::column-end:::
        :::column:::
       ![un cursor visual de ejemplo para mostrar fijamente](images/cursor.jpg)<br>
       *Imagen: un cursor visual de ejemplo para mostrar la mirada*
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a>Confirmación
Después de hablar sobre las distintas formas de _mirarnos_ en un destino, vamos a hablar un poco más sobre la parte de _confirmación_ en la _mirada y la confirmación_.
Después de establecer como destino un objeto o un elemento de la interfaz de usuario, el usuario puede interactuar o hacer clic en él mediante una entrada secundaria. Esto se conoce como paso de confirmación del modelo de entrada. 

Se admiten los siguientes métodos de confirmación:
- Gesto de puntear en el aire (es decir, levantar la mano del usuario y reunir el dedo del índice y el control de posición)
- Decir _"seleccionar"_ o uno de los comandos de voz de destino
- Presionar un solo botón en un [clic de HoloLens](hardware-accessories.md#hololens-clicker)
- Presione el botón ' A ' en un controlador para juegos de Xbox
- Presione el botón ' A ' en un controlador adaptable de Xbox

### <a name="gaze-and-air-tap-gesture"></a>Gesto de puntear y tocar el aire
Pulsar en el aire es hacer el gesto de pulsar con la mano vertical. Para realizar una pulsación de aire, eleve el dedo del índice a la posición listo y, a continuación, acerque el dedo y vuelva a colocar el dedo de índice en la versión. En HoloLens (1ª generación), Air TAP es la entrada secundaria más común.


:::row:::
    :::column:::
       ![dedo en la posición preparada](images/readyandpress-ready.jpg)<br>
       **Dedo en la posición listo**<br>
    :::column-end:::
    :::column:::
       ![Presione el dedo para pulsar o hacer clic en](images/readyandpress-press.jpg)<br>
        **Presione el dedo para pulsar o hacer clic en**<br>
    :::column-end:::
:::row-end:::


Air TAP también está disponible en HoloLens 2. Se ha relajado de la versión original. Ahora se admiten casi todos los tipos de gestos, siempre y cuando la mano esté en vertical y manteniendo todavía. Esto facilita a los usuarios aprender y realizar el gesto. Esta nueva derivación de aire reemplaza a la antigua a través de la misma API, por lo que las aplicaciones existentes tendrán el nuevo comportamiento automáticamente después de volver a compilar para HoloLens 2.

<br>

---

### <a name="gaze-and-select-voice-command"></a>Mira y "selecciona" comando de voz
Los comandos de voz son uno de los métodos de interacción principales en la realidad mixta. Proporciona un mecanismo gratuito muy eficaz para controlar el sistema. Existen diferentes tipos de modelos de interacción de voz:

- Comando genérico "Select" que realiza una acción de hacer clic o confirmar como entrada secundaria.
- Los comandos de objeto (por ejemplo, "cerrar" o "hacer que sean más grandes") realizan y confirman una acción como entrada secundaria.
- Los comandos globales (por ejemplo, "ir a Inicio") no requieren un destino.
- Las interfaces o entidades de usuario de conversación como Cortana tienen una capacidad de lenguaje natural de AI.
- Comandos de voz personalizados

Para obtener más información, así como una lista completa de los comandos de voz disponibles y cómo usarlos, consulte nuestra guía de [comandos de voz](voice-design.md) .

<br>

---


### <a name="gaze-and-hololens-clicker"></a>Clic en fijamente y HoloLens

:::row:::
    :::column:::
        El clic de HoloLens es el primer dispositivo periférico creado específicamente para HoloLens. Se incluye en la edición de desarrollo de HoloLens (1º gen). El clic de HoloLens permite que un usuario haga clic con el movimiento mínimo de mano y se confirme como una entrada secundaria. El clic de HoloLens se conecta a HoloLens (1º gen) o a HoloLens 2 con Bluetooth de baja energía (BTLE).<br>
        <br>
        [Más información e instrucciones para emparejar el dispositivo](hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *Imagen: clic de HoloLens*
    :::column-end:::
        :::column:::
       ![Clic en HoloLens](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a>Controlador inalámbrico de mira y Xbox

:::row:::
    :::column:::
        La controladora inalámbrica Xbox realiza una acción de clic como entrada secundaria mediante el botón "A". El dispositivo se asigna a un conjunto predeterminado de acciones que ayudan a navegar y controlar el sistema. Si desea personalizar el controlador, use la aplicación accesorios de Xbox para configurar el controlador inalámbrico de Xbox.<br>
        <br>
        [Cómo emparejar un controlador Xbox con su PC](hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        *Imagen: controlador inalámbrico Xbox*
    :::column-end:::
        :::column:::
       ![Controlador inalámbrico Xbox](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a>Mira el controlador adaptable de la consola Xbox
Diseñado principalmente para satisfacer las necesidades de los jugadores con movilidad limitada, el controlador adaptable Xbox es un concentrador unificado para dispositivos que ayuda a hacer que la realidad mixta sea más accesible.

El controlador adaptable de la Xbox realiza una acción de clic como entrada secundaria mediante el botón "A". El dispositivo se asigna a un conjunto predeterminado de acciones que ayudan a navegar y controlar el sistema. Si desea personalizar el controlador, use la aplicación accesorios de Xbox para configurar el controlador adaptable de Xbox.

![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)<br>
*Xbox Adaptive Controller*

Conecte dispositivos externos como conmutadores, botones, montajes y joysticks para crear una experiencia de controlador personalizada que sea suya exclusiva. Las entradas de los botones, el stick analógico y el desencadenador se controlan con dispositivos de asistencia conectados a través de conectores de 3,5 mm y puertos USB.

![Puertos del Xbox Adaptive Controller](images/xbox-adaptive-controller-ports.jpg)<br>
*Puertos del Xbox Adaptive Controller*

[Instrucciones para emparejar el dispositivo](hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Más información disponible en el sitio de Xbox</a>

<br>

---

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

[Más información sobre los gestos compuestos](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a>Reconocedores de gestos

Una ventaja de usar el reconocimiento de gestos es que puede configurar un reconocedor de gestos solo para los gestos que el holograma de destino actual puede aceptar. La plataforma solo realiza la desambiguación según sea necesario para distinguir los gestos admitidos en particular. De esta manera, un holograma que solo admita Air TAP puede aceptar cualquier período de tiempo entre la prensa y la versión, mientras que un holograma que admita tanto tap como Hold puede promover la derivación a una retención después del umbral de tiempo de espera.

## <a name="hand-recognition"></a>Reconocimiento de la mano
HoloLens reconoce los gestos de la mano mediante el seguimiento de la posición de una o ambas manos si son visibles para el dispositivo. HoloLens ve las manos cuando están en el estado preparado (parte posterior de la mano hacia ti con el dedo índice arriba) o el estado presionado (parte posterior de la mano hacia ti con el dedo índice hacia abajo). Cuando las manos están en otras, HoloLens las omite.
Para cada mano que HoloLens detecta, puede tener acceso a su posición sin orientación y su estado presionado. A medida que la mano se acerca al borde del marco gestual, obtendrás un vector de dirección que puedes mostrar al usuario para que sepa cómo mover la mano para volver a ponerla donde HoloLens pueda verla.

## <a name="gesture-frame"></a>Marco gestual
En el caso de los gestos en HoloLens, la mano debe estar dentro de un marco de gestos, en un intervalo en el que las cámaras de detección de gestos pueden ver adecuadamente, de la nariz a la waist y entre los hombros. Los usuarios deben estar entrenados en esta área de reconocimiento tanto para el éxito de la acción como para su comodidad. En principio, muchos usuarios suponen que el marco de gestos debe estar en su vista a través de HoloLens y mantener sus ramas de forma no cómoda para interactuar. Al usar el clic de HoloLens, no es necesario que las manos estén dentro del marco de gestos.

En el caso de los gestos continuos en concreto, hay un riesgo de que los usuarios muevan sus manos fuera del marco de gestos mientras se mueven al mover un objeto holográfica, por ejemplo, y se pierde el resultado previsto.

Hay tres cosas que hay que tener en cuenta:

- Educación del usuario sobre la existencia y los límites aproximados del marco de gestos. Esto se enseña durante la instalación de HoloLens.

- Notificar a los usuarios cuando sus gestos están próximos o rompiendo los límites del marco de gestos dentro de una aplicación hasta el grado en que un movimiento perdido conduce a resultados no deseados. La investigación ha mostrado las cualidades clave de este sistema de notificación. El shell de HoloLens proporciona un buen ejemplo de este tipo de notificación: visual, en el cursor central, que indica la dirección en la que se está llevando a cabo el cruce de límites.

- Se deben minimizar las consecuencias de traspasar los límites del marco gestual. En general, esto significa que el resultado de un gesto debe detenerse en el límite y no revertirse. Por ejemplo, si un usuario mueve algún objeto holográfica a través de una habitación, el movimiento debe detenerse cuando se infrinja el marco de gestos y no se devuelva al punto inicial. El usuario puede experimentar cierta frustración, pero es posible que comprenda más rápidamente los límites y no tenga que reiniciar todas las acciones previstas en cada momento.



## <a name="see-also"></a>Consulta también
* [Interacción basada en ojos](eye-gaze-interaction.md)
* [Seguimiento ocular en HoloLens 2](eye-tracking.md)
* [Mirada y permanencia](gaze-and-dwell.md)
* [Manipulación práctica directa](direct-manipulation.md)
* [Gestos prácticos](gaze-and-commit.md#composite-gestures)
* [Manos y confirmación](point-and-commit.md)
* [Interacciones instintivas](interaction-fundamentals.md)
* [Entrada de voz](voice-input.md)

