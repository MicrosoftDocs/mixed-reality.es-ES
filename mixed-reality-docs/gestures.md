---
title: Gestos
description: Los gestos de mano permiten a los usuarios realizar una acción en la realidad mixta.
author: rwinj
ms.author: cmeekhof
ms.date: 02/24/2019
ms.topic: article
keywords: Realidad mixta, gestos, interacción, diseño
ms.openlocfilehash: 8094caaf8a5d805606e9dac11ece56bc50122e5d
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829773"
---
# <a name="gestures"></a>Gestos

Los gestos de mano permiten a los usuarios realizar una acción en la realidad mixta. Interacción se basa en **que mirar** al destino y **gesto** o **voz** para actuar en cualquier elemento es el destino. Los gestos de mano no proporcionan una ubicación exacta en el espacio, pero la simplicidad de colocar en un HoloLens e interactúan inmediatamente con contenido permite a los usuarios empezar a trabajar sin otros accesorios.

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
        <td><strong>Característica</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (gen 1)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></td>
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
> Obtener información más específica de HoloLens 2 [próximamente](index.md#news-and-notes).

## <a name="gaze-and-commit"></a>Mirada y confirmación

Para realizar acciones, use gestos de mano [mirada principal](gaze.md) como mecanismo de destinatarios. La combinación de **que mirar** y **en el aire** gestos da como resultado un **mirada y confirmación** interacción. Una alternativa a la mirada y confirmación es **punto y confirmación**, habilitada por [motion controladores](motion-controllers.md). Las aplicaciones que se ejecutan en HoloLens basta admitir mirada y confirmación ya HoloLens no es compatible con los controladores de movimiento. Las aplicaciones que se ejecutan en HoloLens e inmersivos deben admitir interacciones controladas por señalando y controlados por mirada, para dar a la elección de los usuarios en el dispositivo de entrada que usen.

## <a name="the-two-core-gestures-of-hololens"></a>Los dos principales gestos de HoloLens

HoloLens reconoce actualmente dos principales gestos de componente - **en el aire** y **Bloom**. Estas interacciones de dos núcleos son el nivel más bajo de los datos espaciales de entrada que puede tener acceso un desarrollador. Éstos forman la base para una variedad de posibles acciones del usuario.

### <a name="air-tap"></a>En el aire

En el aire es un gesto de pulsar con la mano vertical, de forma similar a un clic del mouse o seleccionar. Se usa en la mayoría de las experiencias de HoloLens para el equivalente de un "clic" en un elemento de interfaz de usuario después de seleccionar el destino con [que mirar](gaze.md). Es una acción universal que aprender una vez y, a continuación, se aplican en todas las aplicaciones. Otras formas de realizar select son presionando el botón solo un [HoloLens Clicker](hardware-accessories.md#hololens-clicker) o con la voz de la voz de comando "Select".

![Estado listo para los gestos de mano en HoloLens](images/image9.png)<br>
*Estado listo para pulsar en el aire en HoloLens.*

En el aire es un gesto discreto. O bien se ha completado una selección o no es así, una acción es o no se realiza dentro de una experiencia. Es posible, aunque no se recomienda sin algún propósito específico, para crear otros movimientos discretos de combinaciones de los componentes principales (por ejemplo, un gesto de doble punteo significa algo distinto a un punteo sencillo).

![Dedo en la posición de la lista y, a continuación, un movimiento puntear o hacer clic](images/readyandpress.jpg)<br>
*Cómo realizar aire: Elevar el dedo índice a la posición de la lista, presione el dedo hacia abajo hasta la acción de puntear o seleccione y, a continuación, realizar copias de seguridad para liberar.*

### <a name="bloom"></a>Bloom

Es el gesto de "inicio" de Bloom y está reservada para que por sí solo. Es una acción especial del sistema que se usa para volver al menú Inicio. Es equivalente a presionar la tecla de Windows en un teclado o el botón de Xbox en un controlador de Xbox. El usuario puede usar cualquier mano.

![Gesto de Bloom en HoloLens](images/image10-640px.png)

Para realizar el gesto de bloom en HoloLens, mantenga out de la mano, palm, conjuntamente con su alcance. A continuación, abra la mano. Tenga en cuenta que también siempre puede volver a inicio diciendo "Hola Cortana, Go Home". No pueden reaccionar ante las aplicaciones específicamente a una acción de inicio, tal como se administran por el sistema.

![Gesto de Bloom](images/bloom-giphy.gif)<br>
*Cómo realizar el gesto de bloom en HoloLens.*

## <a name="composite-gestures"></a>Gestos compuestos

Las aplicaciones pueden reconocer las derivaciones de más de simplemente individuales. Mediante la combinación tap, mantenga y liberar con el movimiento de la mano, se pueden realizar gestos compuestos más complejos. De compilación bajo nivel espaciales datos de entrada (de aire y Bloom) que los desarrolladores tienen acceso a estos gestos de alto nivel o compuestos.

<table>
<tr>
<th> Gesto compuesto</th><th> Cómo aplicar</th>
</tr><tr>
<td>En el aire</td><td>El gesto de pulsar aire (así como los gestos más abajo) responde sólo a una derivación específica. Para detectar otros grifos, como menús o comprender, la aplicación debe usar directamente las interacciones de nivel inferior que se describe en la sección de gestos de dos componentes clave anterior.</td>
</tr><tr>
<td>TAP y hold</td><td><p>Suspensión simplemente consiste en mantener la posición del dedo hacia abajo de la derivación de aire. La combinación de aire tap y hold permite una variedad de más complejos &quot;haga clic y arrastre&quot; interacciones cuando se combina con movimiento como un objeto en lugar de activarlo de selección para arm o &quot;mousedown&quot; interacciones secundaria como mostrar un menú contextual.</p><p>Debe tener precaución al diseñar para este gesto sin embargo, como los usuarios puede ser propensa a relajar sus posturas disponible durante el transcurso de los gestos extendido.</p></td>
</tr><tr>
<td>Manipulación</td><td><p>Los gestos de manipulación pueden usarse para mover, cambiar el tamaño o girar un holograma cuando desee que el holograma reaccionar 1:1 para el usuario&#39;movimientos de mano s. Es uno de los usos de estos movimientos de 1:1 permitir al usuario dibujar o pintar en el mundo.</p><p>Los destinos iniciales para un gesto de manipulación deben hacerse mirada o que apunta. Una vez que inicie tap y hold, cualquier manipulación del objeto, a continuación, se controla a mano los movimientos, liberando al usuario buscar en torno a mientras manipulan.</p></td>
</tr><tr>
<td>Navegación</td><td><p>Gestos de navegación funcionan como un joystick virtual y se pueden usar para navegar por los widgets de interfaz de usuario, como menús radiales. Pulse y mantenga presionado para iniciar el movimiento y, a continuación, mover la mano dentro de un cubo 3D normalizada, centrado en la prensa inicial. Puede mover la mano a lo largo del eje X, Y o Z de un valor de -1 a 1, siendo 0 el punto de partida.</p><p>Navegación puede utilizarse para generar los gestos de zoom, similares al desplazamiento de una interfaz de usuario 2D haciendo clic en el botón central del mouse y, a continuación, mover el mouse hacia arriba y abajo o basada en velocidad de desplazamiento continuo.</p><p>Navegación con rails hace referencia a la capacidad de reconocer los movimientos en determinado eje hasta que se alcanza cierto umbral de ese eje. Esto solo es útil, cuando el movimiento en más de un eje está habilitada en una aplicación por el desarrollador, por ejemplo, si una aplicación está configurada para reconocer gestos de navegación a través de X, eje Y pero también especifica X eje con rails. En este caso sistema reconocerá los movimientos de mano a través de eje X, siempre se encuentran dentro de un rails imaginaria (Guía de) en eje X si movimiento también produce el eje Y.</p><p>Dentro de las aplicaciones de 2D, los usuarios pueden usar gestos de navegación vertical para desplazarse, zoom o arrastre dentro de la aplicación. Esto inserta virtual dedo toca a la aplicación para simular los gestos de toque del mismo tipo. Los usuarios pueden seleccionar cuál de estas acciones tienen lugar alternando entre las herramientas en la barra encima de la aplicación, ya sea seleccionando el botón o diciendo &#39; &lt;arrastrar/desplazamiento y Zoom&gt; herramienta&#39;.</p></td>
</tr>
</table>



### <a name="gesture-recognizers"></a>Reconocedores de gestos

Una ventaja de usar el reconocimiento de gestos es que puede configurar un reconocedor de movimiento solo para los gestos que puede aceptar el holograma de destino actual. La plataforma hará la desambiguación necesario distinguir los gestos compatibles determinados. De este modo, un holograma que solo se admite en el aire puede aceptar cualquier intervalo de tiempo entre press y versión, mientras un holograma que admite tanto pulsado puede promocionar la derivación de una suspensión tras el umbral de tiempo de espera.

## <a name="hand-recognition"></a>Reconocimiento de mano

HoloLens reconoce los gestos de mano mediante el seguimiento de la posición de las manos de uno o ambos que son visibles para el dispositivo. HoloLens ve manos cuando están en uno el **listo estado** (parte posterior de la mano hacia arriba, con el dedo índice) o el **estado presionado** (parte posterior de la mano hacia abajo, con el dedo índice). Cuando las manos en otros puede causar, el HoloLens ignorará.

Para cada manecilla detecta ese HoloLens, puede tener acceso a su posición (sin orientación) y su estado presionado. Como el borde del marco de gesto se acerque a la mano, también se le ofrece un vector de dirección, puede mostrar al usuario para que sepan cómo trasladar su mano volver obtenerla donde pueden ver en HoloLens.

## <a name="gesture-frame"></a>Marco de movimiento

Para los gestos en HoloLens, debe ser la mano en un "período de gesto", en un intervalo que las cámaras de gesto de detección pueden ver adecuadamente (muy aproximadamente en la nariz cintura y entre los hombros). Los usuarios deben poder entrenarlos en esta área de reconocimiento (muchos usuarios inicialmente supondrá que el marco de movimiento debe estar dentro de su vista a través de HoloLens y almacenar las armas uncomfortably con el fin de interactuar) tanto para el éxito de acción para su comodidad. Cuando se usa al HoloLens Clicker, sus manos no es necesario ser dentro del marco de movimiento.

En el caso de gestos continua en concreto, hay algunos riesgos de los usuarios mover sus manos fuera del marco de gesto mientras se encuentra en medio gesto (mientras mueve algún objeto holográfica, por ejemplo) y perder su resultado previsto.

Hay tres cosas que debe considerar:
* Educación del usuario en el marco de gesto existencia y límites aproximados (enseñado durante la instalación de HoloLens).
* Notificar a los usuarios cuando sus movimientos son casi/separación de los límites del marco de gesto dentro de una aplicación, en la medida que un gesto pierde darán lugar a resultados no deseados. Investigación ha demostrado que las cualidades claves de este sistema de notificación y el shell de HoloLens proporciona un buen ejemplo de este tipo de notificación (en el cursor central, que indica la dirección en qué límites cruce lleva a cabo, visual).
* Se deben minimizar las consecuencias de los límites del marco de gesto de importantes. En general, esto significa que el resultado de un gesto debe ser detenido en el límite, pero no puede revertir. Por ejemplo, si un usuario está moviendo algún objeto holographic a través de una sala, movimiento debe detenerse cuando se supera el marco de movimiento, pero **no** devolverse al punto de partida. El usuario puede experimentar algunos frustración a continuación, pero puede entender más rápidamente los límites y no tenga que reiniciar sus acciones previstas completas cada vez.

## <a name="see-also"></a>Vea también
* [Control con la cabeza y permanencia](gaze-and-dwell.md)
* [Diseño de la voz](voice-design.md)
* [MR Input 211: gesto](holograms-211.md)
* [Gestos y controladores de movimiento en Unity](gestures-and-motion-controllers-in-unity.md)
* [Manos y controladores de movimiento en DirectX](hands-and-motion-controllers-in-directx.md)
* [Controladores de movimiento](motion-controllers.md)
