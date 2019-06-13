---
title: Mirada con la cabeza y confirmación
description: Introducción al modelo de entrada de mirada con la cabeza y confirmación
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, gaze, gaze targeting, interaction, design
ms.openlocfilehash: d9eae3c0cfceba7c2c31425941dfce865f3aa609
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "66692305"
---
# <a name="head-gaze-and-commit"></a>Mirada con la cabeza y confirmación
El modelo de mirada con la cabeza y confirmación es un modelo de entrada que implica establecer un objeto como destino con la cabeza apuntando hacia adelante (dirección de la cabeza) y actuar sobre él con una entrada secundaria, como un gesto de pulsación en el aire con la mano o el comando de voz "Seleccionar". Se considera un modelo de entrada "lejano" con manipulación indirecta, lo que significa que se usa preferiblemente para interactuar con el contenido que está fuera del alcance de los brazos.

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
Los cascos de realidad mixta utilizan la posición y orientación de la cabeza del usuario para determinar el vector de dirección de la cabeza. Se puede considerar como un láser que apunta en línea recta directamente desde el punto situado entre los ojos del usuario. Esto es una aproximación bastante general de dónde mira el usuario. La aplicación puede intersecar este rayo con objetos reales o virtuales y dibujar un cursor en esa ubicación para que el usuario sepa adónde está apuntando en ese momento.

Además de la mirada con la cabeza, algunos cascos de realidad mixta, como HoloLens 2, incluyen sistemas de seguimiento de los ojos que generan un vector de la mirada con los ojos. Esto proporciona una medida específica de adónde mira el usuario. Es posible crear interacciones de mirada y confirmación utilizando la mirada con los ojos, pero tiene un conjunto muy diferente de restricciones de diseño, que se explicará por separado en el [artículo de seguimiento de los ojos](eye-tracking.md).

## <a name="commit"></a>Confirmación
Después de establecer como destino un objeto o un elemento de la interfaz de usuario, el usuario puede interactuar o hacer "clic" en el mismo con una entrada secundaria. Esto se conoce como el paso de confirmación del modelo. Se admiten los siguientes métodos de confirmación:

- Gesto de pulsación en el aire
- Pronunciar el comando de voz "Seleccionar" o uno de los comandos de voz de destino
- Presionar el único botón de [HoloLens Clicker](hardware-accessories.md#hololens-clicker)
- Presionar el botón "A" del mando de Xbox
- Presionar el botón "A" del Xbox Adaptive Controller

### <a name="head-gaze-and-air-tap-gesture"></a>Mirada con la cabeza y gesto de pulsación en el aire
Pulsar en el aire es hacer el gesto de pulsar con la mano vertical. Para pulsar en el aire, coloca el dedo índice en posición vertical, acerca el dedo al pulgar y levántalo de nuevo para liberar el clic. En HoloLens 1, pulsar en el aire es la entrada secundaria más común.

![Dedo en posición vertical y movimiento de pulsar o hacer clic](images/readyandpress.jpg)<br>

El gesto de pulsación en el aire también está disponible en HoloLens 2 y se ha relajado con respecto a la versión original. Ahora se admiten casi todos los tipos de movimientos de acercar los dedos, siempre que la mano esté vertical y permanezca quieta. Esto facilita a los usuarios aprender y realizar el gesto.  Este nuevo gesto de pulsación en el aire reemplaza al antiguo en la misma API, por lo que las aplicaciones existentes obtendrán automáticamente el nuevo comportamiento después de recompilar para HoloLens 2.

### <a name="head-gaze-and-select-voice-command"></a>Mirada con la cabeza y comando de voz "Seleccionar"
Los comandos de voz son uno de los principales métodos de interacción en la realidad mixta. Proporcionan un mecanismo de "manos libres" muy eficaz para controlar el sistema. Hay diferentes tipos de modelos de interacción de voz:

- El comando genérico "Seleccionar", que equivale a confirmar o accionar un "clic" como una entrada secundaria.
- Los comandos de objetos, como "Cerrar" o "Ampliar", que permiten realizar y confirmar una acción como una entrada secundaria.
- Los comandos globales, como "Ir al principio", que no requieren un destino.
- Las interfaces de usuario o entidades de conversación, como Cortana, que tienen una funcionalidad de lenguaje natural basada en inteligencia artificial.
- Los comandos personalizados.

Para obtener más información y una lista completa de los comandos disponibles y cómo usarlos, consulta nuestra guía de [comandos de voz](voice-design.md).


### <a name="head-gaze-and-hololens-clicker"></a>Mirada con la cabeza y HoloLens Clicker
HoloLens Clicker es el primer dispositivo periférico creado específicamente para HoloLens y se incluye en HoloLens 1 Development Edition. HoloLens Clicker permite a un usuario hacer clic con un movimiento de la mano mínimo y confirmar como una entrada secundaria. HoloLens Clicker se conecta a HoloLens 1 o 2 mediante Bluetooth de bajo consumo (BTLE).

![HoloLens Clicker](images/hololens-clicker-500px.jpg)<br>
*HoloLens Clicker*

[Aquí](hardware-accessories.md#pairing-bluetooth-accessories) encontrarás más información e instrucciones para emparejar el dispositivo.




### <a name="head-gaze-and-xbox-wireless-controller"></a>Mirada con la cabeza y controlador inalámbrico de Xbox
El controlador inalámbrico de Xbox permite realizar una acción de "clic" como entrada secundaria con el botón A. El dispositivo se asigna a un conjunto predeterminado de acciones que ayudan a desplazarse por el sistema y controlarlo. Si deseas personalizar el controlador, utiliza la aplicación de accesorios de Xbox para configurar el controlador inalámbrico de Xbox.

![Controlador inalámbrico de Xbox](images/xboxcontroller.jpg)<br>
*Controlador inalámbrico de Xbox*

[Emparejamiento de un controlador de Xbox con el PC](hardware-accessories.md#pairing-bluetooth-accessories)


### <a name="head-gaze-and-xbox-adaptive-controller"></a>Mirada con la cabeza y Xbox Adaptive Controller
Diseñado principalmente para satisfacer las necesidades de los jugadores con movilidad limitada, el Xbox Adaptive Controller es un centro unificado para dispositivos que hace la realidad mixta más accesible.

Xbox Adaptive Controller permite realizar una acción de "clic" como entrada secundaria con el botón A. El dispositivo se asigna a un conjunto predeterminado de acciones que ayudan a desplazarse por el sistema y controlarlo. Si deseas personalizar el controlador, utiliza la aplicación de accesorios de Xbox para configurar el Xbox Adaptive Controller.

![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)<br>
*Xbox Adaptive Controller*

Conecta dispositivos externos como conmutadores, botones, soportes y joysticks para crear una experiencia de controladores personalizada exclusivamente para ti. Las entradas de botones, palancas de control y activadores se controlan mediante dispositivos de asistencia que se conectan a las tomas de 3,5 mm y los puertos USB.

![Puertos del Xbox Adaptive Controller](images/xbox-adaptive-controller-ports.jpg)<br>
*Puertos del Xbox Adaptive Controller*

[Instrucciones para emparejar el dispositivo](hardware-accessories.md#pairing-bluetooth-accessories)

<a href=https://www.xbox.com/en-US/xbox-one/accessories/controllers/xbox-adaptive-controller>Más información disponible en el sitio de Xbox</a>


## <a name="design-guidelines"></a>Directrices de diseño
> [!NOTE]
> [Próximamente](index.md) habrá disponible más información específica para el diseño de la mirada.

## <a name="head-gaze-targeting"></a>Establecer el destino de la mirada con la cabeza
Todas las interacciones se basan en la capacidad de un usuario de establecer como destino el elemento con el que desea interactuar, independientemente de la modalidad de entrada. En Windows Mixed Reality, esto se hace mediante la mirada del usuario por lo general.
Para que los usuarios puedan trabajar con una experiencia correctamente, la comprensión de la intención del usuario calculada por el sistema y la intención real del usuario deben estar lo más alineadas como sea posible. En la medida que el sistema interpreta las intenciones del usuario correctamente, la satisfacción aumenta y el rendimiento mejora.


## <a name="target-sizing-and-feedback"></a>Ajuste de tamaño del destino y comentarios
Se ha demostrado repetidamente que el vector de mirada se puede usar para establecer el destino de forma precisa, pero suele funcionar mejor para destinos de mayor tamaño (adquisición de destinos algo mayores). Los destinos con un tamaño mínimo de entre 1 y 1,5 grados deberían permitir acciones de usuario correctas en la mayoría de los escenarios, aunque los destinos de 3 grados suelen permitir mayor velocidad. Tenga en cuenta que el tamaño que el usuario establece como destino es realmente un área 2D incluso para los elementos 3D (cualquier proyección de ellos debe ser un área potencial de destino). Resulta muy útil proporcionar alguna indicación destacada de que un elemento está "activo" (que el usuario lo está estableciendo como destino). Esto puede incluir tratamientos como los efectos visibles de "mantener el puntero", señales auditivas o clics, o la alineación clara de un cursor con un elemento.

![Tamaño de destino óptimo a una distancia de 2 metros](images/gazetargeting-size-1000px.jpg)<br>
*Tamaño de objetivo óptimo a una distancia de 2 metros*

![Ejemplo de resaltado de un objeto establecido como destino de la mirada](images/gazetargeting-highlighting-640px.jpg)<br>
*Ejemplo de resaltado de un objeto establecido como destino de la mirada*

## <a name="target-placement"></a>Situación del destino
Con frecuencia, los usuarios no podrán encontrar elementos de la interfaz de usuario que estén situados muy arriba o muy abajo en su campo de visión, y centrarán la mayoría de su atención en las áreas en torno al foco principal (normalmente al nivel de los ojos aproximadamente). Quizás resulte útil colocar la mayoría de los destinos en una banda razonable a la altura de los ojos. Dada la tendencia de los usuarios de centrarse en un área visual relativamente pequeña en todo momento (el cono de atención de la visión es de 10 grados aproximadamente), agrupar los elementos de la interfaz de usuario según su relación conceptual puede producir comportamientos de llamada de atención de un elemento a otro, ya que un usuario mueve su mirada dentro de un área. Al diseñar la interfaz de usuario, se deben tener en cuenta las posibles grandes variaciones en el campo de visión entre HoloLens y los cascos envolventes.

![Ejemplo de elementos de la interfaz de usuario agrupados para facilitar el establecimiento del destino con la mirada en Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)<br>
*Ejemplo de elementos de la interfaz de usuario agrupados para facilitar el establecimiento del destino con la mirada en Galaxy Explorer*

## <a name="improving-targeting-behaviors"></a>Mejora de los comportamientos de establecimiento de destino
Si se puede determinar (o aproximar) la intención del usuario de establecer algo como destino, puede ser muy útil aceptar intentos "casi incorrectos" en la interacción como si se hubiesen establecido correctamente. Hay una serie de métodos correctos que se pueden incorporar en las experiencias de realidad mixta:

### <a name="head-gaze-stabilization-gravity-wells"></a>Estabilización de la mirada con la cabeza ("pozos de gravedad")
Debería estar activada la mayor parte o todo el tiempo. Esta técnica elimina las vibraciones naturales del cuello o la cabeza que los usuarios puedan tener. También existe un movimiento debido a los comportamientos de la mirada o el habla.

### <a name="closest-link-algorithms"></a>Algoritmos de vínculo más cercano
Funcionan mejor en áreas con un contenido interactivo disperso. Si hay una alta probabilidad de poder determinar con qué intentaba interactuar un usuario, sus habilidades de establecimiento de destino se pueden complementar simplemente suponiendo cierto nivel de intención.

### <a name="backdatingpostdating-actions"></a>Anticipar y posponer acciones
Este mecanismo es útil en las tareas que requieren velocidad. Cuando un usuario se mueve en una serie de maniobras de establecimiento de destino o activación con velocidad, puede resultar útil suponer alguna intención y permitir que los pasos no correctos puedan actuar sobre los destinos que el usuario ha tenido en su foco ligeramente antes o después de la acción de pulsar (50 ms antes o después ha resultado eficaz en las primeras pruebas).

### <a name="smoothing"></a>Suavizado
Este mecanismo es útil para el trazado de movimientos y reduce la vibración u oscilación debidas a las características de los movimientos naturales de la cabeza. En el suavizado del trazado de movimientos, se debe realizar un suavizado en función del tamaño o la distancia de los movimientos y no en función del tiempo.

### <a name="magnetism"></a>Magnetismo
Este mecanismo puede considerarse como una versión más general de los algoritmos de "vínculo más cercano": dibujar un cursor hacia un destino o simplemente aumentar los indicadores de acierto (visibles o no) a medida que los usuarios se aproximan a los destinos usando conocimientos sobre el diseño interactivo para aproximar mejor la intención del usuario. Esto puede resultar especialmente eficaz para destinos pequeños.

### <a name="focus-stickiness"></a>Permanencia del foco
Al determinar a qué elementos interactivos cercanos se dará el foco, se produce un sesgo hacia el elemento que está actualmente en el foco. Esto ayudará a reducir comportamientos de cambio errático del foco cuando se flota en un punto intermedio entre dos elementos con ruido natural.


## <a name="composite-gestures"></a>Gestos compuestos
Las aplicaciones pueden reconocer algo más que simples pulsaciones individuales. Combinando los gestos de pulsar, mantener pulsado y soltar con el movimiento de la mano, se pueden realizar gestos compuestos más complejos. Estos gestos compuestos o de alto nivel se basan en los datos de entrada espaciales de bajo nivel (de Air tap y Bloom) a los que los desarrolladores tienen acceso.

### <a name="air-tap"></a>Pulsar en el aire
El gesto de pulsación en el aire (así como los siguientes gestos) responden solo a una pulsación específica. Para detectar otras pulsaciones, como Menú o Agarrar, la aplicación debe usar directamente las interacciones de nivel inferior que se describen en la sección de dos gestos de componentes clave anterior.

### <a name="tap-and-hold"></a>Mantener pulsado
Mantener pulsado simplemente consiste en mantener la posición del dedo hacia abajo al pulsar en el aire. La combinación de pulsar en el aire y mantener pulsado permite una variedad de interacciones de "hacer clic y arrastrar" más complejas cuando se combina con el movimiento del brazo, como recoger un objeto en lugar de activarlo o interacciones secundarias del tipo "pulsación del mouse" tales como mostrar un menú contextual.
No obstante, se debe tener precaución al diseñar para este gesto, porque los usuarios pueden ser propensos a relajar las posturas de la mano en el caso de gestos prolongados.

### <a name="manipulation"></a>Manipulación
Los gestos de manipulación se pueden utilizar para mover, cambiar el tamaño o girar un holograma cuando se desea que el holograma reaccione 1:1 con el movimiento de las manos del usuario. Uno de los usos de estos movimientos 1:1 es permitir al usuario dibujar o pintar en el mundo.
El destino inicial de un gesto de manipulación debe establecerse con la mirada o apuntando. Una vez que se inicia la acción de mantener pulsado, cualquier manipulación del objeto se controla con los movimientos de la mano, lo que permite al usuario mirar a su alrededor mientras manipula.

### <a name="navigation"></a>Navegación
Los gestos de navegación funcionan como un joystick virtual y se pueden usar para navegar por los widgets de la interfaz de usuario, como los menús circulares. Se mantiene pulsado para iniciar el gesto y, después, se mueve la mano dentro de un cubo 3D normalizado centrado alrededor de la pulsación inicial. Se puede mover la mano a lo largo del eje X, Y o Z desde un valor de -1 hasta 1, siendo 0 el punto de partida.
La navegación se puede utilizar para crear gestos de zoom o desplazamiento continuo basado en la velocidad, similares al desplazamiento en una interfaz de usuario 2D cuando se hace clic con el botón central del ratón para después mover el ratón hacia arriba y abajo.

La navegación con carriles hace referencia a la capacidad de reconocer los movimientos en un determinado eje hasta que se alcanza cierto umbral en ese eje. Esto solo es útil cuando el desarrollador ha habilitado el movimiento en más de un eje en una aplicación; por ejemplo, si una aplicación está configurada para reconocer gestos de navegación en el eje X y el eje Y pero también se especifica el eje X con carriles. En este caso, el sistema reconocerá los movimientos de la mano en el eje X siempre que permanezcan dentro de un carril imaginario (guía) en el eje X si también se produce movimiento en el eje Y.

En las aplicaciones 2D, los usuarios pueden usar gestos de navegación vertical para desplazarse, hacer zoom o arrastrar dentro de la aplicación. Esto inserta entradas táctiles virtuales en la aplicación para simular gestos táctiles del mismo tipo. Los usuarios pueden seleccionar cuál de estas acciones tendrá lugar alternando entre las herramientas de la barra situada encima de la aplicación, ya sea seleccionando el botón o diciendo "Herramienta <desplazar/arrastrar/zoom>".

[Más información sobre los gestos compuestos](gestures.md#composite-gestures)

## <a name="gesture-recognizers"></a>Reconocedores de gestos

Una ventaja de usar el reconocimiento de gestos es que se puede configurar un reconocedor de gestos solo para los gestos que puede aceptar el holograma de destino actual. La plataforma hará la desambiguación necesaria para distinguir esos gestos admitidos en particular. De este modo, un holograma que solo admite pulsar en el aire puede aceptar cualquier intervalo de tiempo entre pulsar y soltar, mientras que un holograma que también admite mantener pulsado puede promover la transición de pulsar a mantener pulsado una vez transcurrido el tiempo de espera.

## <a name="hand-recognition"></a>Reconocimiento de la mano
HoloLens reconoce los gestos de la mano mediante el seguimiento de la posición de una o ambas manos si son visibles para el dispositivo. HoloLens ve las manos cuando están en el estado preparado (parte posterior de la mano hacia ti con el dedo índice arriba) o el estado presionado (parte posterior de la mano hacia ti con el dedo índice hacia abajo). Cuando las manos están en otra postura, HoloLens las ignorará.
Para cada mano que HoloLens detecta, puedes acceder a su posición (sin orientación) y a su estado presionado. A medida que la mano se acerca al borde del marco gestual, obtendrás un vector de dirección que puedes mostrar al usuario para que sepa cómo mover la mano para volver a ponerla donde HoloLens pueda verla.

## <a name="gesture-frame"></a>Marco gestual
Para los gestos en HoloLens, la mano debe estar dentro de un "marco gestual", en un intervalo donde las cámaras de detección de gestos la puedan ver correctamente (de forma muy aproximada, desde la nariz a la cintura y entre los hombros). Los usuarios deben entrenarse en este área de reconocimiento para realizar una acción correcta y por su propia comodidad (muchos usuarios asumirán inicialmente que el marco gestual está dentro de su visión con HoloLens y subirán sus brazos de un modo incómodo para interactuar). Cuando se usa HoloLens Clicker, las manos no necesitan estar dentro del marco gestual.

En el caso de gestos continuos, existe el riesgo de que los usuarios muevan las manos fuera del marco gestual mientras se encuentran en medio del gesto (mientras mueven algún objeto holográfico, por ejemplo) y pierdan el resultado previsto.

Hay tres cosas que hay que tener en cuenta:

- La educación del usuario en la existencia del marco gestual y sus límites aproximados (esto se enseña durante la instalación de HoloLens).

- Notificar a los usuarios cuando sus movimientos se aproximan a los límites del marco gestual o se salen de él en una aplicación, en la medida que un gesto perdido dará lugar a resultados no deseados. Las investigaciones han demostrado las ventajas de este sistema de notificación y el shell de HoloLens es un buen ejemplo de este tipo de notificación (visual, en el cursor central, indicando la dirección en la que se están traspasando los límites).

- Se deben minimizar las consecuencias de traspasar los límites del marco gestual. En general, esto significa que el resultado de un gesto se debe en el límite, pero no se debe revertir. Por ejemplo, si un usuario está moviendo algún objeto holográfico por una sala, el movimiento debe detenerse cuando se traspasa el marco gestual, pero no debe devolverse al punto de partida. El usuario podría experimentar alguna frustración, pero comprenderá más rápidamente los límites y no tendrá que reiniciar las acciones previstas completas cada vez.


## <a name="see-also"></a>Consulte también
* [Manipulación directa con las manos](direct-manipulation.md)
* [Apuntar y confirmar con las manos](point-and-commit.md)
* [Interacciones instintivas](interaction-fundamentals.md)
* [Control con la cabeza y permanencia](gaze-and-dwell.md)
* [Comandos de voz](voice-design.md)





