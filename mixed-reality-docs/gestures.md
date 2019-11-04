---
title: Gestos
description: Los gestos de mano permiten a los usuarios tomar medidas en realidad mixta.
author: rwinj
ms.author: cmeekhof
ms.date: 02/24/2019
ms.topic: article
keywords: Realidad mixta, gestos, interacción, diseño
ms.openlocfilehash: ae8af8fdb0bd224d127092c6636d473f383ab6f9
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73435211"
---
# <a name="gestures"></a>Gestos

Los gestos de mano permiten a los usuarios tomar medidas en realidad mixta. La interacción se basa en la **mirada** hacia el destino y el **gesto** o la **voz** para actuar sobre el elemento al que se ha destinado. Los gestos de mano no proporcionan una ubicación precisa en el espacio, pero la simplicidad de colocar en HoloLens e interactuar inmediatamente con el contenido permite a los usuarios trabajar sin ningún otro accesorio.

<br>

>[!VIDEO https://www.youtube.com/embed/kwn9Lh0E_vU]

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
        <td>Gestos</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>Manos articuladas</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

> [!NOTE]
> [Próximamente](news.md)se ofrecerá orientación específica para HoloLens 2.

## <a name="gaze-and-commit"></a>Miras y confirmaciones

Para realizar acciones, los gestos de mano usan la punta de la [mirada](gaze-and-commit.md) como mecanismo de destino. La combinación de **miras** y el gesto de **pulsación de aire** da como resultado una interacción de **mira y confirmación** . Una alternativa a la función de mirar y confirmar es el **punto y la confirmación**, habilitada por [los controladores de movimiento](motion-controllers.md). Las aplicaciones que se ejecutan en HoloLens solo deben admitir las funciones de miración y confirmación, ya que HoloLens no admite controladores de movimiento. Las aplicaciones que se ejecutan tanto en HoloLens como en auriculares envolvente deben admitir interacciones orientadas a mano y controladas por la mirada para ofrecer a los usuarios la posibilidad de elegir el dispositivo de entrada que usan.

## <a name="the-two-core-gestures-of-hololens"></a>Los dos gestos principales de HoloLens

HoloLens actualmente reconoce dos gestos de componentes principales: Pulse y **floración** **en el aire** . Estas dos interacciones de núcleo son el nivel más bajo de datos de entrada espacial a los que puede tener acceso un desarrollador. Forman la base de una serie de acciones de usuario posibles.

### <a name="air-tap"></a>Pulsar en el aire

La pulsación aérea es un gesto de puntear con la mano presionada, similar a un clic del mouse o seleccionar. Esto se usa en la mayoría de las experiencias de HoloLens para el equivalente de un "clic" en un elemento de la interfaz de usuario después de destinarla con [mirarnos](gaze-and-commit.md). Se trata de una acción universal que se aprende una vez y luego se aplica en todas las aplicaciones. Otras maneras de realizar la selección son presionando el botón único en un [clic de HoloLens](hardware-accessories.md#hololens-clicker) o hablando el comando de voz "seleccionar".

![estado listo para los gestos de mano en HoloLens](images/image9.png)<br>
*Estado listo para la pulsación de Air en HoloLens.*

Air TAP es un gesto discreto. Una selección se completa o no, una acción se realiza o no en una experiencia. Aunque no se recomienda sin ningún propósito específico, es posible crear otros gestos discretos a partir de combinaciones de los componentes principales (por ejemplo, un gesto de doble punteo para indicar algo diferente a una sola pulsación).

![dedo en la posición listo y, después, pulse o haga clic en movimiento](images/readyandpress.jpg)<br>
*Cómo realizar una pulsación de aire: eleve el dedo del índice a la posición listo, presione el dedo para pulsar o seleccionar y, después, haga una copia de seguridad en el lanzamiento.*

### <a name="bloom"></a>Flores

El floración es el gesto de "Inicio" y se reserva por sí solo. Se trata de una acción especial del sistema que se usa para volver al menú Inicio. Equivale a presionar la tecla Windows en un teclado o el botón Xbox en un controlador Xbox. El usuario puede usar cualquiera de las manos.

![Gesto de floración en HoloLens](images/image10-640px.png)

Para llevar a cabo el gesto de floración en HoloLens, Manténgase al alcance de la mano, con sus dedos juntos. A continuación, abra la mano. Tenga en cuenta que también puede volver a empezar por decir "Hola Cortana, ir a Inicio". Las aplicaciones no pueden reaccionar específicamente a una acción de inicio, ya que las administra el sistema.

gesto ![floración](images/bloom-giphy.gif)<br>
*Cómo realizar el gesto de floración en HoloLens.*

## <a name="composite-gestures"></a>Gestos compuestos

Las aplicaciones pueden reconocer algo más que simples pulsaciones individuales. Combinando los gestos de pulsar, mantener pulsado y soltar con el movimiento de la mano, se pueden realizar gestos compuestos más complejos. Estos gestos compuestos o de alto nivel se basan en los datos de entrada espaciales de bajo nivel (de Air tap y Bloom) a los que los desarrolladores tienen acceso.

<table>
<tr>
<th> Movimiento compuesto</th><th> Cómo aplicar</th>
</tr><tr>
<td>Pulsar en el aire</td><td>El gesto de pulsación en el aire (así como los siguientes gestos) responden solo a una pulsación específica. Para detectar otras pulsaciones, como Menú o Agarrar, la aplicación debe usar directamente las interacciones de nivel inferior que se describen en la sección de dos gestos de componentes clave anterior.</td>
</tr><tr>
<td>Mantener pulsado</td><td><p>Mantener pulsado simplemente consiste en mantener la posición del dedo hacia abajo al pulsar en el aire. La combinación de la pulsación de aire y la suspensión permiten una variedad de interacciones más complejas &quot;hacer clic y arrastrar&quot; al combinarse con el movimiento de ARM, como la selección de un objeto en lugar de activarlo o &quot;MouseDown&quot; las interacciones secundarias. como mostrar un menú contextual.</p><p>No obstante, se debe tener precaución al diseñar para este gesto, porque los usuarios pueden ser propensos a relajar las posturas de la mano en el caso de gestos prolongados.</p></td>
</tr><tr>
<td>Manipulación</td><td><p>Los gestos de manipulación se pueden usar para desplazar, cambiar de tamaño o girar un holograma cuando se desea que el holograma&#39;reaccione 1:1 a los movimientos de la mano del usuario. Uno de los usos de estos movimientos 1:1 es permitir al usuario dibujar o pintar en el mundo.</p><p>El destino inicial de un gesto de manipulación debe establecerse con la mirada o apuntando. Una vez que se inicia la acción de mantener pulsado, cualquier manipulación del objeto se controla con los movimientos de la mano, lo que permite al usuario mirar a su alrededor mientras manipula.</p></td>
</tr><tr>
<td>Navegación</td><td><p>Los gestos de navegación funcionan como un joystick virtual y se pueden usar para navegar por los widgets de la interfaz de usuario, como los menús circulares. Se mantiene pulsado para iniciar el gesto y, después, se mueve la mano dentro de un cubo 3D normalizado centrado alrededor de la pulsación inicial. Se puede mover la mano a lo largo del eje X, Y o Z desde un valor de -1 hasta 1, siendo 0 el punto de partida.</p><p>La navegación se puede utilizar para crear gestos de zoom o desplazamiento continuo basado en la velocidad, similares al desplazamiento en una interfaz de usuario 2D cuando se hace clic con el botón central del ratón para después mover el ratón hacia arriba y abajo.</p><p>La navegación con carriles hace referencia a la capacidad de reconocer los movimientos en un determinado eje hasta que se alcanza cierto umbral en ese eje. Esto solo es útil cuando el desarrollador ha habilitado el movimiento en más de un eje en una aplicación; por ejemplo, si una aplicación está configurada para reconocer gestos de navegación en el eje X y el eje Y pero también se especifica el eje X con carriles. En este caso, el sistema reconocerá los movimientos de la mano en el eje X siempre que permanezcan dentro de un carril imaginario (guía) en el eje X si también se produce movimiento en el eje Y.</p><p>En las aplicaciones 2D, los usuarios pueden usar gestos de navegación vertical para desplazarse, hacer zoom o arrastrar dentro de la aplicación. Esto inserta entradas táctiles virtuales en la aplicación para simular gestos táctiles del mismo tipo. Los usuarios pueden seleccionar cuál de estas acciones tienen lugar alternando entre las herramientas de la barra situada encima de la aplicación, ya sea seleccionando el &#39; botón o diciendo&lt;herramienta&#39;de desplazamiento/arrastrar/zoom&gt;.</p></td>
</tr>
</table>



### <a name="gesture-recognizers"></a>Reconocedores de gestos

Una ventaja de usar el reconocimiento de gestos es que se puede configurar un reconocedor de gestos solo para los gestos que puede aceptar el holograma de destino actual. La plataforma hará la desambiguación necesaria para distinguir esos gestos admitidos en particular. De este modo, un holograma que solo admite pulsar en el aire puede aceptar cualquier intervalo de tiempo entre pulsar y soltar, mientras que un holograma que también admite mantener pulsado puede promover la transición de pulsar a mantener pulsado una vez transcurrido el tiempo de espera.

## <a name="hand-recognition"></a>Reconocimiento de la mano

HoloLens reconoce los gestos de la mano mediante el seguimiento de la posición de una o ambas manos si son visibles para el dispositivo. HoloLens ve las manos cuando están en el **estado listo** (la parte posterior de la mano con el dedo del índice) o el **estado presionado** (parte posterior de la mano con el dedo del índice hacia abajo). Cuando las manos están en otra postura, HoloLens las ignorará.

Para cada mano que HoloLens detecta, puedes acceder a su posición (sin orientación) y a su estado presionado. A medida que la mano se acerca al borde del marco gestual, obtendrás un vector de dirección que puedes mostrar al usuario para que sepa cómo mover la mano para volver a ponerla donde HoloLens pueda verla.

## <a name="gesture-frame"></a>Marco gestual

Para los gestos en HoloLens, la mano debe estar dentro de un "marco gestual", en un intervalo donde las cámaras de detección de gestos la puedan ver correctamente (de forma muy aproximada, desde la nariz a la cintura y entre los hombros). Los usuarios deben entrenarse en este área de reconocimiento para realizar una acción correcta y por su propia comodidad (muchos usuarios asumirán inicialmente que el marco gestual está dentro de su visión con HoloLens y subirán sus brazos de un modo incómodo para interactuar). Cuando se usa HoloLens Clicker, las manos no necesitan estar dentro del marco gestual.

En el caso de gestos continuos, existe el riesgo de que los usuarios muevan las manos fuera del marco gestual mientras se encuentran en medio del gesto (mientras mueven algún objeto holográfico, por ejemplo) y pierdan el resultado previsto.

Hay tres cosas que hay que tener en cuenta:
* La educación del usuario en la existencia del marco gestual y sus límites aproximados (esto se enseña durante la instalación de HoloLens).
* Notificar a los usuarios cuando sus movimientos se aproximan a los límites del marco gestual o se salen de él en una aplicación, en la medida que un gesto perdido dará lugar a resultados no deseados. Las investigaciones han demostrado las ventajas de este sistema de notificación y el shell de HoloLens es un buen ejemplo de este tipo de notificación (visual, en el cursor central, indicando la dirección en la que se están traspasando los límites).
* Se deben minimizar las consecuencias de traspasar los límites del marco gestual. En general, esto significa que el resultado de un gesto se debe en el límite, pero no se debe revertir. Por ejemplo, si un usuario mueve algún objeto holográfica a través de una habitación, el movimiento debe detenerse cuando se infrinja el marco de gestos, pero **no** se devolverá al punto inicial. El usuario podría experimentar alguna frustración, pero comprenderá más rápidamente los límites y no tendrá que reiniciar las acciones previstas completas cada vez.

## <a name="see-also"></a>Consulta también
* [Control con la cabeza y permanencia](gaze-and-dwell.md)
* [Diseño de la voz](voice-design.md)
* [Entrada MR 211: gesto](holograms-211.md)
* [Gestos y controladores de movimiento en Unity](gestures-and-motion-controllers-in-unity.md)
* [Manos y controladores de movimiento en DirectX](hands-and-motion-controllers-in-directx.md)
* [Controladores de movimiento](motion-controllers.md)
