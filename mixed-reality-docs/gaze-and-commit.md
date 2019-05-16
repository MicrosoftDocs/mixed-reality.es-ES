---
title: Mirada de encabezado y confirmación
description: Información general sobre el modelo de entrada de mirada de encabezado y confirmación
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
ms.localizationpriority: high
keywords: Diseñar la realidad, mirada, mirada como destino, interacción, mixta
ms.openlocfilehash: 95f2cef8c10ce3d0d2a218953613fef6f0a00362
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730816"
---
# <a name="head-gaze-and-commit"></a>Mirada de encabezado y confirmación
Mirada de encabezado y confirmación es un modelo de entrada que implica el destino es un objeto con la dirección de la cabeza hacia adelante (encabezado de dirección), y actuar sobre ellos con una base de datos secundaria de entrada, como el gesto de mano, puntee en el aire o la voz del comando "Select". Se considera un modelo con manipulación indirecta, lo que significa que se usa para interactuar con el contenido que está más allá de brazos llegar a "ahora" de entrada.

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
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (gen 1)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></td>
    </tr>
     <tr>
        <td>Mirada de encabezado y confirmación</td>
        <td>✔️ Recomendado</td>
        <td>Recomienda ✔️ (tercera opción - <a href="interaction-fundamentals.md">ver las demás opciones</a>)</td>
        <td>Opción alternativa ➕</td>
    </tr>
</table>

## <a name="head-gaze"></a>Head mirada
Auriculares de realidad mixta utilizar la posición y orientación de head del usuario para determinar su vector de dirección principal. Se puede considerar esto como una impresora láser que señala recta desde directamente entre la vista del usuario. Esto es un bastante aproximación de donde el usuario va a buscar. La aplicación puede forman una intersección con este ray con objetos reales o virtuales y dibuje un cursor en esa ubicación para hacer saber lo actualmente se dirige al usuario.

Además de mirada principal, algunos auriculares de realidad mixta, como el 2 de HoloLens incluyen sistemas que generan un vector mirada de seguimiento de los ojos. Esto proporciona una medida específica de donde el usuario va a buscar. Es posible crear mirada y confirmar las interacciones con mirada ojos, pero esto viene con un conjunto muy diferente de las restricciones de diseño, lo que se explicará por separado en el [artículo de rastreo ocular](eye-tracking.md).

## <a name="commit"></a>Confirmación
Después de destino es un objeto o elemento de interfaz de usuario, el usuario puede interactuar o "click" en ella con una entrada secundaria. Esto se conoce como el paso de confirmación del modelo. Se admiten los siguientes métodos de confirmación:

- Gesto de pulsar el aire
- Diga el comando de voz "Select" o uno de los comandos de voz de destino
- Presione el botón solo en un [HoloLens Clicker](hardware-accessories.md#hololens-clicker)
- Presione el botón 'A' en un Xbox Gamepad
- Presione el botón 'A' en un controlador de Xbox adaptable

### <a name="head-gaze-and-air-tap-gesture"></a>Head mirada y aire gesto
En el aire es un gesto de pulsar con la mano vertical. Para llevar a cabo aire, elevar el dedo índice a la posición de la lista, a continuación, acercar con el pulgar y elevar el dedo índice de copia de seguridad para liberar. En el 1 de HoloLens, en el aire es la entrada secundaria más comunes.

![Dedo en la posición de la lista y, a continuación, un movimiento puntear o hacer clic](images/readyandpress.jpg)<br>

En el aire también está disponible en HoloLens 2, y se disminuyó de la versión original. Ahora se admiten casi todos los tipos de pinches, siempre que la mano sea vertical y explotación todavía. Esto facilita mucho más fácil para los usuarios obtener información y realice el gesto.  Este nuevo en el aire reemplaza al antiguo a través de la misma API, por lo que las aplicaciones existentes obtendrán automáticamente el nuevo comportamiento después de volver a compilar para HoloLens 2.

### <a name="head-gaze-and-select-voice-command"></a>Head mirada y "Select" comando de voz
Comandos de voz es uno de los métodos de interacción principal en la realidad mixta. Proporciona un mecanismo de "Manos libres" muy eficaz para controlar el sistema. Hay un diseño diferente tipos de modelos de interacción de voz:

- El comando genérico "Select", que permite para realizar una "click" accionamiento o confirmación como una entrada secundaria.
- Comandos de objeto, como "Cerrar" o "Aumentar su tamaño" que permiten realizar y una acción como una entrada secundaria de confirmación.
- Comandos globales, como "Ir a iniciar" que no requieren un destino.
- Interfaces de usuario de la conversación o entidades, como Cortana que tienen una capacidad de lenguaje Natural de inteligencia artificial.
- Comandos personalizados

Para obtener más información y una lista de comprenhesive de comandos disponibles y su uso, consulte nuestra [voz diseño](voice-design.md) orientación.


### <a name="head-gaze-and-hololens-clicker"></a>Head mirada y HoloLens Clicker
El HoloLens Clicker es el primer dispositivo periférico creado específicamente para HoloLens y se incluye con el 1 de HoloLens Development Edition. El HoloLens Clicker permite a un usuario haga clic con el movimiento de mano mínimo y como una entrada secundaria de confirmación. El clicker HoloLens se conecta a la 1 HoloLens o 2 con Bluetooth baja energía (BTLE).

![](images/hololens-clicker-500px.jpg)<br>
HoloLens Clicker

Encontrará más información e instrucciones para emparejar el dispositivo [aquí](hardware-accessories.md#pairing-bluetooth-accessories)




### <a name="head-gaze-and-xbox-wireless-controller"></a>Head mirada y controlador inalámbrico Xbox
El controlador de Xbox Wireless permite para realizar un accionamiento "click" como entrada mediante el botón secundario. El dispositivo se asigna a un conjunto predeterminado de las acciones que ayudan a navegar y controlar el sistema. Si desea personalizar el controlador, utilice el App Accesories Xbox para configurar el controlador de Xbox inalámbrica.

![](images/xboxcontroller.jpg)<br>
Controlador inalámbrico Xbox

[Emparejamiento de un controlador Xbox con su PC](hardware-accessories.md#pairing-bluetooth-accessories)


### <a name="head-gaze-and-xbox-adaptive-controller"></a>Controlador adaptable HEAD mirada y Xbox
Ha diseñado principalmente para satisfacer las necesidades de jugadores con movilidad limitada, el controlador de Xbox adaptable es un centro unificado para dispositivos que le ayuda a hacer realidad mixta sea más accesible.

El controlador de Xbox adaptable permite para realizar un accionamiento "haga clic en" como un elemento secundario de entrada mediante el botón. El dispositivo se asigna a un conjunto predeterminado de las acciones que ayudan a navegar y controlar el sistema. Si desea personalizar el controlador, utilice el App Accesories Xbox para configurar el controlador adaptable de Xbox.

![](images/xbox-adaptive-controller-devices.jpg)<br>
Mando de Xbox adaptable

Conectar dispositivos externos, como conmutadores, botones, montajes y joysticks para crear una experiencia de controladores personalizada es exclusivamente suya. Las entradas de botón, la tecla de navegación y desencadenador se controlan con los dispositivos conectados a través de conectores de 3,5 mm y puertos USB de asistencia.

![](images/xbox-adaptive-controller-ports.jpg)<br>
Puertos de mando de Xbox adaptable

[Instrucciones para emparejar el dispositivo](hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/en-US/xbox-one/accessories/controllers/xbox-adaptive-controller>Más información disponible en el sitio de Xbox</a>


# <a name="head-gaze-design-guidelines"></a>Instrucciones de diseño de Head mirada
> [!NOTE]
> Obtener información más específica de diseño que mirar [próximamente](index.md).

## <a name="head-gaze-targeting"></a>Head-mirada destinadas a
Todas las interacciones se basan en la capacidad de un usuario para el elemento que desean interactuar, independientemente de la modalidad de entrada de destino. En Windows Mixed Reality, por lo general esto se hace mediante la mirada del usuario.
Para que los usuarios puedan trabajar con una experiencia correctamente, debe alinear comprensión calculado del sistema de la intención del usuario y la intención del usuario real, como lo máximo posible. En la medida que el sistema interpreta las acciones del usuario previsto correctamente, aumenta la satisfacción y el rendimiento mejora.


## <a name="target-sizing-and-feedback"></a>Comentarios y ajuste de tamaño de destino
El vector mirada demostraron varias veces que se pueda usar para dirigirse a correcto, pero a menudo funciona mejor para brutos destinatarios (al adquirir un poco mayores destinos). Tamaños de destino mínimo de 1 a 1,5 grados deben permitir acciones de usuario correctamente en la mayoría de los escenarios, aunque los destinos de grados de 3 a menudo permiten mayor velocidad. Tenga en cuenta que el tamaño que los destinos de usuario es realmente un área 2D incluso para los elementos 3D--cualquier proyección está orientado a ellos debe ser el área de destino. Que proporciona alguna indicación más destacada que un elemento es "activo" (que el usuario está destinado a él) es extremadamente útil, esto puede incluir tratamientos como efectos visible "desplazar el puntero", información destacada de audio o hace clic en, o desactive la alineación de un cursor con un elemento.

![Tamaño de destino óptimo a distancia de medidor 2](images/gazetargeting-size-1000px.jpg)<br>
*Tamaño de destino óptimo a distancia de medidor 2*

![Un ejemplo de resaltado de un objeto de destino de mirada](images/gazetargeting-highlighting-640px.jpg)<br>
*Un ejemplo de resaltado de un objeto de destino de mirada*

## <a name="target-placement"></a>Selección de ubicación de destino
Los usuarios a menudo producirá un error buscar elementos de interfaz de usuario que se colocan muy alto o muy baja en su campo de visión, centrándose en la mayoría de su atención en las áreas en torno a su enfoque principal (normalmente más o menos el nivel de ojo). Puede ayudar colocar la mayoría de los destinos en algunos banda razonable en torno a nivel de los ojos. Dada la tendencia de los usuarios para centrarse en un área visual relativamente pequeña en cualquier momento (attentional cono de visión es aproximadamente 10 grados), agrupar los elementos de interfaz de usuario para el grado que están relacionadas conceptualmente puede aprovechar los comportamientos de encadenamiento de atención de un elemento a otro como un usuario se mueve a su mirada a través de un área. Al diseñar la interfaz de usuario, tenga en cuenta los posibles grandes variaciones en el campo de visión entre HoloLens e inmersivos.

![Un ejemplo de los elementos de interfaz de usuario agrupados para mirada más fácil seleccionar como destino en el Explorador de Galaxy](images/gazetargeting-grouping-1000px.jpg)<br>
*Un ejemplo de los elementos de interfaz de usuario agrupados para mirada más fácil seleccionar como destino en el Explorador de Galaxy*

## <a name="improving-targeting-behaviors"></a>Mejora de los comportamientos de destinatarios
Si intención del usuario para tener como destino algo puede ser determinado (o estrechamente de forma aproximada), puede ser muy útil aceptar intentos "near miss" en la interacción como si se destinen a correctamente. Hay una serie de métodos correctas que se pueden incorporar en las experiencias de realidad mixta:

### <a name="head-gaze-stabilization-gravity-wells"></a>Estabilización de Head mirada ("wells gravedad")
Esto debe activarse la mayor parte o todo el tiempo. Esta técnica quita el a las vibraciones head/cuello natural que los usuarios pueden tener. También movimiento debido a los comportamientos de búsqueda de términos.

### <a name="closest-link-algorithms"></a>Algoritmos más cercano de vínculo
Estos funcionan mejor en áreas con dispersa contenido interactivo. Si hay una alta probabilidad de que puede determinar lo que un usuario intentó interactuar con, puede complementar sus capacidades de destinatarios, simplemente suponiendo cierto nivel de calidad.

### <a name="backdatingpostdating-actions"></a>Acciones backdating/postdating
Este mecanismo es útil en las tareas que requieren velocidad. Cuando un usuario está moviendo a través de una serie de maniobras/activación como destino a la velocidad, puede resultar útil supone algunos intención y permitir que los pasos que faltan actuar en los destinos que el usuario tenía foco ligeramente antes o un poco después de la derivación (50 ms antes o después estuvo en vigor en al principio de prueba).

### <a name="smoothing"></a>Suavizado
Este mecanismo es útil para los movimientos de rutas, lo que reduce la vibración/oscilante pequeña debido a las características de movimiento natural. Cuando el suavizado de los movimientos de rutas, smooth por distancia/tamaño de los movimientos en lugar de con el tiempo

### <a name="magnetism"></a>Magnética
Este mecanismo puede considerarse como una versión más general de algoritmos de "Vínculo más cercano": dibujar un cursor hacia un destino, o simplemente incrementar hitboxes (ya sea visible o no) como destinos es probable que aproximan a los usuarios, uso de cierto conocimiento del diseño interactivo a intención del usuario de un mejor enfoque. Esto puede ser especialmente eficaz para los destinos pequeño.

### <a name="focus-stickiness"></a>Permanencia de foco
Al determinar qué cercanas a elementos interactivos para dar el foco a, proporcionar un sesgo en el elemento que se centra actualmente. Esto ayudará a reducir el enfoque errático conmutación comportamientos cuando flota en un punto medio entre dos elementos con ruido natural.


## <a name="composite-gestures"></a>Gestos compuestos
Las aplicaciones pueden reconocer las derivaciones de más de simplemente individuales. Mediante la combinación tap, mantenga y liberar con el movimiento de la mano, se pueden realizar gestos compuestos más complejos. De compilación bajo nivel espaciales datos de entrada (de aire y Bloom) que los desarrolladores tienen acceso a estos gestos de alto nivel o compuestos.

### <a name="air-tap"></a>En el aire
El gesto de pulsar aire (así como los gestos más abajo) responde sólo a una derivación específica. Para detectar otros grifos, como menús o comprender, la aplicación debe usar directamente las interacciones de nivel inferior que se describe en la sección de gestos de dos componentes clave anterior.

### <a name="tap-and-hold"></a>TAP y hold
Suspensión simplemente consiste en mantener la posición del dedo hacia abajo de la derivación de aire. La combinación de aire tap y hold permite una variedad de interacciones más complejas de "hacer clic y arrastrar" cuando se combina con el movimiento de arm como recoger un objeto en lugar de activar, o "mousedown" interacciones secundaria como mostrar un menú contextual.
Debe tener precaución al diseñar para este gesto sin embargo, como los usuarios puede ser propensa a relajar sus posturas disponible durante el transcurso de los gestos extendido.

### <a name="manipulation"></a>Manipulación
Los gestos de manipulación pueden utilizarse para mover, cambiar el tamaño o girar un holograma cuando desee que el holograma reaccionar 1:1 para el movimiento de las manos del usuario. Es uno de los usos de estos movimientos de 1:1 permitir al usuario dibujar o pintar en el mundo.
Los destinos iniciales para un gesto de manipulación deben hacerse mirada o que apunta. Una vez que inicie tap y hold, cualquier manipulación del objeto, a continuación, se controla a mano los movimientos, liberando al usuario buscar en torno a mientras manipulan.

### <a name="navigation"></a>Navegación
Gestos de navegación funcionan como un joystick virtual y se pueden usar para navegar por los widgets de interfaz de usuario, como menús radiales. Pulse y mantenga presionado para iniciar el movimiento y, a continuación, mover la mano dentro de un cubo 3D normalizada, centrado en la prensa inicial. Puede mover la mano a lo largo del eje X, Y o Z de un valor de -1 a 1, siendo 0 el punto de partida.
Navegación puede utilizarse para generar los gestos de zoom, similares al desplazamiento de una interfaz de usuario 2D haciendo clic en el botón central del mouse y, a continuación, mover el mouse hacia arriba y abajo o basada en velocidad de desplazamiento continuo.

Navegación con rails hace referencia a la capacidad de reconocer los movimientos en determinado eje hasta que se alcanza cierto umbral de ese eje. Esto solo es útil, cuando el movimiento en más de un eje está habilitada en una aplicación por el desarrollador, por ejemplo, si una aplicación está configurada para reconocer gestos de navegación a través de X, eje Y pero también especifica X eje con rails. En este caso sistema reconocerá los movimientos de mano a través de eje X, siempre se encuentran dentro de un rails imaginaria (Guía de) en eje X si movimiento también produce el eje Y.

Dentro de las aplicaciones de 2D, los usuarios pueden usar gestos de navegación vertical para desplazarse, zoom o arrastre dentro de la aplicación. Esto inserta virtual dedo toca a la aplicación para simular los gestos de toque del mismo tipo. Los usuarios pueden seleccionar cuál de estas acciones tienen lugar alternando entre las herramientas en la barra encima de la aplicación, ya sea seleccionando el botón o que dice 'Herramienta < desplazamiento/arrastre/alejar >'.

[Obtener más información sobre los gestos compuestos](gestures.md#composite-gestures)

## <a name="gesture-recognizers"></a>Reconocedores de gestos

Una ventaja de usar el reconocimiento de gestos es que puede configurar un reconocedor de movimiento solo para los gestos que puede aceptar el holograma de destino actual. La plataforma hará la desambiguación necesario distinguir los gestos compatibles determinados. De este modo, un holograma que solo se admite en el aire puede aceptar cualquier intervalo de tiempo entre press y versión, mientras un holograma que admite tanto pulsado puede promocionar la derivación de una suspensión tras el umbral de tiempo de espera.

## <a name="hand-recognition"></a>Reconocimiento de mano
HoloLens reconoce los gestos de mano mediante el seguimiento de la posición de las manos de uno o ambos que son visibles para el dispositivo. HoloLens ve manos cuando están en estado preparada (parte posterior de la mano hacia arriba, con el dedo índice) o el estado presionado (parte posterior de la mano hacia abajo, con el dedo índice). Cuando las manos en otros puede causar, el HoloLens ignorará.
Para cada manecilla detecta ese HoloLens, puede tener acceso a su posición (sin orientación) y su estado presionado. Como el borde del marco de gesto se acerque a la mano, también se le ofrece un vector de dirección, puede mostrar al usuario para que sepan cómo trasladar su mano volver obtenerla donde pueden ver en HoloLens.

## <a name="gesture-frame"></a>Marco de movimiento
Para los gestos en HoloLens, debe ser la mano en un "período de gesto", en un intervalo que las cámaras de gesto de detección pueden ver adecuadamente (muy aproximadamente en la nariz cintura y entre los hombros). Los usuarios deben poder entrenarlos en esta área de reconocimiento (muchos usuarios inicialmente supondrá que el marco de movimiento debe estar dentro de su vista a través de HoloLens y almacenar las armas uncomfortably con el fin de interactuar) tanto para el éxito de acción para su comodidad. Cuando se usa al HoloLens Clicker, sus manos no es necesario ser dentro del marco de movimiento.

En el caso de gestos continua en concreto, hay algunos riesgos de los usuarios mover sus manos fuera del marco de gesto mientras se encuentra en medio gesto (mientras mueve algún objeto holográfica, por ejemplo) y perder su resultado previsto.

Hay tres cosas que debe considerar:

- Educación del usuario en el marco de gesto existencia y límites aproximados (enseñado durante la instalación de HoloLens).

- Notificar a los usuarios cuando sus movimientos son casi/separación de los límites del marco de gesto dentro de una aplicación, en la medida que un gesto pierde darán lugar a resultados no deseados. Investigación ha demostrado que las cualidades claves de este sistema de notificación y el shell de HoloLens proporciona un buen ejemplo de este tipo de notificación (en el cursor central, que indica la dirección en qué límites cruce lleva a cabo, visual).

- Se deben minimizar las consecuencias de los límites del marco de gesto de importantes. En general, esto significa que el resultado de un gesto debe ser detenido en el límite, pero no puede revertir. Por ejemplo, si un usuario está moviendo algún objeto holographic a través de una sala, movimiento debe detenerse cuando se supera el marco de movimiento, pero no pueden devolverse en punto de partida. El usuario puede experimentar algunos frustración a continuación, pero puede entender más rápidamente los límites y no tenga que reiniciar sus acciones previstas completas cada vez.


## <a name="see-also"></a>Vea también
* [Manipulación directa](direct-manipulation.md)
* [Señalar y confirmar](point-and-commit.md)
* [Conceptos básicos de la interacción](interaction-fundamentals.md)
* [Mirada y permanencia](gaze-targeting.md)
* [Mirada y voz](voice-design.md)





