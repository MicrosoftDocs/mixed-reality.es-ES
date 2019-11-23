---
title: Controladores de movimiento
description: Detalles sobre los controladores de movimiento de realidad mixta.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: Controladores de 6DOF, controladores de movimiento
ms.openlocfilehash: 84ebc6c0d7c63e58346b6ee9e565811bc40571b5
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437859"
---
# <a name="motion-controllers"></a>Controladores de movimiento

:::row:::
    :::column:::
        Los controladores de movimiento son [accesorios de hardware](hardware-accessories.md) que permiten a los usuarios tomar medidas en realidad mixta. Una ventaja de los controladores de movimiento a través de [gestos](gaze-and-commit.md#composite-gestures) es que los controladores tienen una posición precisa en el espacio, lo que permite una interacción detallada con los objetos digitales. En el caso de los auriculares de la realidad mixta de Windows, los controladores de movimiento son la manera principal en que los usuarios realizarán acciones en su mundo.<br>
        <br>
        *Imagen: controlador de movimiento de Windows Mixed Reality*
    :::column-end:::
        :::column:::
       ![Controladores de movimiento de Windows Mixed Reality](images/winmr-ck-1080x1080-350px.jpg)<br> 
    :::column-end:::
:::row-end:::

<br>

---

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
     <td><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
</tr>
<tr>
     <td>Controladores de movimiento</td>
     <td>❌</td>
     <td>❌</td>
     <td>✔️</td>
</tr>
</table>

## <a name="hardware-details"></a>Detalles de hardware

<iframe width="940" height="530" src="https://www.youtube.com/embed/1nlcdDNOdm8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Los controladores de movimiento de Windows Mixed Reality ofrecen un seguimiento preciso y con capacidad de respuesta del movimiento en el campo de la vista con los sensores en el casco envolvente, lo que significa que no es necesario instalar hardware en las paredes del espacio. Estos controladores de movimiento ofrecen la misma facilidad de configuración y portabilidad que los auriculares de la realidad mixta de Windows. Nuestros asociados de dispositivos tienen previsto comercializar y vender estos controladores en las estanterías minoristas de este festivo.

![conocer el controlador](images/controllerimage-750px.png)<br>
*Conozca el controlador*

**Dispone**
* Seguimiento óptico
* Desencadenador
* Botón de arrastre
* Palanca
* Panel táctil

## <a name="setup"></a>Instalación

### <a name="before-you-begin"></a>Antes de comenzar

**Necesitará lo siguiente:**
* Un conjunto de dos controladores de movimiento.
* Cuatro baterías AA.
* Un equipo capaz de Bluetooth 4,0.

**Comprobar las actualizaciones de Windows, Unity y driver**
* Visite [instalar las herramientas](install-the-tools.md) para las versiones preferidas de Windows, Unity, etc. para el desarrollo de la realidad mixta.
* Asegúrese de que tiene los [controladores de dispositivo de movimiento y auriculares](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)más actualizados.

### <a name="pairing-controllers"></a>Controladores de emparejamiento

Los controladores de movimiento pueden estar enlazados con el equipo host mediante la configuración de Windows como cualquier otro dispositivo Bluetooth.

1. Inserte dos baterías AA en la parte posterior del controlador. Deje la tapa de la batería desactivada por ahora.
2. Si utiliza un adaptador Bluetooth USB externo en lugar de un radio Bluetooth integrado, revise los [procedimientos recomendados de Bluetooth](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) antes de continuar. Para la configuración de escritorio con radio integrada, asegúrese de que la antena esté conectada.
3. Abra **configuración de Windows** -> **dispositivos** -> **agregar Bluetooth u otro dispositivo** -> **Bluetooth** y quite las instancias anteriores de "controlador de movimiento: derecha" y "controlador de movimiento: izquierda". Compruebe también la categoría otros dispositivos en la parte inferior de la lista.
4. Seleccione **Agregar Bluetooth u otro dispositivo** y vea que empieza a detectar dispositivos Bluetooth.
5. Presione y mantenga presionado el botón de Windows del controlador para encender el controlador y liberarlo una vez que lo haga.
6. Mantenga presionado el botón de emparejamiento (pestaña en el compartimiento de la batería) hasta que los LED empiecen a parpadear.

:::row:::
    :::column:::
7. Espere "controlador de movimiento-izquierda" o "controlador de movimiento-derecha" para que aparezca en la parte inferior de la lista. Seleccione para emparejar. El controlador vibrará una vez cuando se conecte.<br>
        <br>
        *Imagen: seleccione "controlador de movimiento" para emparejar; Si hay varias instancias, seleccione una en la parte inferior de la lista.*
    :::column-end:::
        :::column:::
       ![Seleccione controlador de movimiento para emparejar si varias instancias seleccionan una de las que aparecen en la parte inferior de la lista](images/450px-bluetooth-add-a-device-300px.png)<br> 
    :::column-end:::
:::row-end:::
   
8. Verá que el controlador aparece en la configuración de Bluetooth en la **categoría "Mouse, teclado, & lápiz"** como **conectado**. Llegados a este punto, puede obtener una actualización de firmware (consulte la [sección siguiente](motion-controllers.md#updating-controller-firmware)).
9. Vuelva a adjuntar la cubierta de batería.
10. Repita los pasos 1-9 para el segundo controlador.

<br>

:::row:::
    :::column:::
        Después de emparejar ambos controladores correctamente, la configuración debería ser similar a la de la **categoría "Mouse, teclado, & pluma"** <br>
        <br>
        *Imagen: Controladores de movimiento conectados*
    :::column-end:::
        :::column:::
       ![Controladores de movimiento conectados](images/450px-motion-controller-connected-300px.png)<br>
    :::column-end:::
:::row-end:::

Si los controladores están desactivados después del emparejamiento, su estado se mostrará como emparejado. Si los controladores permanecen permanentemente en el emparejamiento de la categoría "otros dispositivos", es posible que se haya completado solo parcialmente y deba realizarse de nuevo para obtener la funcionalidad del controlador.

### <a name="updating-controller-firmware"></a>Actualizando el firmware del controlador

* Si hay un auricular envolvente conectado al equipo y hay disponible un nuevo firmware de controlador, el firmware se insertará automáticamente en los controladores de movimiento la próxima vez que se activen. Las actualizaciones de firmware del controlador se indican mediante un patrón de cuadrantes LED de iluminación en un movimiento circular y tardan 1-2 minutos.


:::row:::
    :::column:::
* Una vez finalizada la actualización del firmware, los controladores se reinician y se vuelven a conectar. Ambos controladores deben estar conectados ahora. <br>
        <br>
        *Imagen: Controladores conectados en la configuración de Bluetooth*
    :::column-end:::
        :::column:::
       ![Controladores conectados](images/cyk-connected-300px.jpg)<br>
    :::column-end:::
:::row-end:::


* Compruebe que los controladores funcionan correctamente:
    1. Inicie el **portal de realidad mixta** y escriba su hogar de realidad mixta.
    2. Mueva los controladores y compruebe el seguimiento, los botones de prueba y la comprobación de la [teleportabilidad](navigating-the-windows-mixed-reality-home.md#getting-around-your-home). Si no es así, consulte [solución de problemas del controlador de movimiento](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers).

## <a name="gazing-and-pointing"></a>Gazing y apuntando

Windows Mixed Reality admite dos modelos clave para la interacción, **mirarlas y confirmar** y **apuntar y confirmar**:
* Con las opciones de **mirar y confirmar**, los usuarios destinan un objeto con su [mirada](gaze-and-commit.md) y, a continuación, seleccionan objetos con pulsaciones aéreas, un controlador para juegos, un clic o la voz.
* Con **Point y commit**, un usuario puede dirigirse a un controlador de movimiento compatible con el puntero en el objeto de destino y, a continuación, seleccionar objetos con el desencadenador del controlador.

Las aplicaciones que admiten apuntar a controladores de movimiento también deben habilitar las interacciones basadas en la mirada siempre que sea posible, para ofrecer a los usuarios la posibilidad de elegir los dispositivos de entrada que usan.

### <a name="managing-recoil-when-pointing"></a>Administrar la rebobinado al apuntar

Al usar los controladores de movimiento para apuntar y confirmar, los usuarios usarán el controlador como destino y, a continuación, tomarán medidas al extraer su desencadenador. Los usuarios que extraen el desencadenador pueden acabar con el controlador más alto al final de la extracción del desencadenador del que querían.

Para administrar este tipo de rebobinado que se puede producir cuando los usuarios extraen el desencadenador, la aplicación puede ajustar su rayo de destino cuando el valor del eje analógico del desencadenador aumente por encima de 0,0. A continuación, puede realizar una acción mediante la destinación de un rayo a algunos fotogramas más adelante, una vez que el valor del desencadenador alcance 1,0, siempre que la última acción se realice en un período de tiempo corto. Cuando se usa el gesto de [punteo compuesto](gaze-and-commit.md#composite-gestures)de nivel superior, Windows administrará esta captura de rayo y el tiempo de espera de destino.

## <a name="grip-pose-vs-pointing-pose"></a>Replanteamiento de control frente a pose de puntero

Windows Mixed Reality admite controladores de movimiento en diversos factores de forma, con el diseño de cada controlador diferente en su relación entre la posición del usuario y la dirección de "avance" natural que deben usar las aplicaciones para apuntar al representar el módem.

Para representar mejor estos controladores, hay dos tipos de supuestos que puede investigar para cada origen de interacción, la representación del **control** y la representación del **puntero**.

### <a name="grip-pose"></a>Replanteamiento de control

El **puño** representa la ubicación de la palma de una mano detectada por una HoloLens o la palma que contiene un controlador de movimiento.

En los auriculares envolventes, la representación del puño es la que mejor se usa para representar **la mano del usuario** o **un objeto que se mantiene en la mano del usuario**, como un arma o un cañón. La representación de control también se usa al visualizar un controlador de movimiento, ya que el **modelo representable** proporcionado por Windows para un controlador de movimiento utiliza la representación del puño como su origen y el centro de rotación.

La pose de control se define específicamente de la siguiente manera:
* La **posición del puño**: Palm centroide cuando mantiene el controlador de forma natural, se ajusta hacia la izquierda o derecha para centrar la posición dentro del control. En el controlador de movimiento de Windows Mixed Reality, esta posición generalmente se alinea con el botón de agarre.
* **Eje derecho de la orientación del puño**: cuando se abre por completo la mano para formar una postura plana de 5 dedos, el rayo perpendicular a la palma (hacia delante de la mano izquierda y hacia atrás desde la mano derecha)
* El **eje hacia delante de la orientación del puño**: al cerrar la mano (como si contiene el controlador), el rayo que señala "reenviar" a través del tubo formado por los dedos no Thumb.
* **Eje hacia arriba de la orientación del puño**: el eje hacia arriba implícito por las definiciones derecha y hacia delante.

### <a name="pointer-pose"></a>Representar puntero

La **pose de puntero** representa la punta del controlador que señala hacia delante.

La representación de puntero proporcionada por el sistema se usa mejor para Raycast cuando se **representa el propio modelo de controlador**. Si está representando algún otro objeto virtual en lugar del controlador, como un cañón virtual, debe apuntar con un rayo más natural para ese objeto virtual, como un rayo que viaja a lo largo del barril del modelo de pistola definido por la aplicación. Dado que los usuarios pueden ver el objeto virtual y no el controlador físico, es probable que apunte con el objeto virtual sea más natural para los que usan su aplicación.

## <a name="controller-tracking-state"></a>Estado de seguimiento del controlador

Al igual que los auriculares, el controlador de movimiento de Windows Mixed Reality no requiere la configuración de sensores de seguimiento externos. En su lugar, el seguimiento de los controladores se realiza mediante sensores en el propio casco.

Si el usuario mueve los controladores fuera del campo de vista del casco, en la mayoría de los casos Windows seguirá inferencia de las posiciones del controlador y las proporcionará a la aplicación. Cuando el controlador ha perdido el seguimiento visual durante el tiempo suficiente, las posiciones del controlador se quitarán de las posiciones de precisión aproximada.

En este punto, el sistema bloqueará el controlador al usuario, realizará un seguimiento de la posición del usuario a medida que se mueven, mientras se expone la verdadera orientación del controlador mediante sus sensores de orientación internos. Muchas aplicaciones que usan Controladores para apuntar a los elementos de la interfaz de usuario y activarlos pueden funcionar con normalidad mientras tienen una precisión aproximada sin que el usuario lo note.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/rkDpRllbLII" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### <a name="reasoning-about-tracking-state-explicitly"></a>Razonamiento sobre el estado de seguimiento explícitamente

Las aplicaciones que quieren tratar las posiciones de manera diferente según el estado de seguimiento pueden ir más allá e inspeccionar las propiedades en el estado del controlador, como SourceLossRisk y PositionAccuracy:

<table>
<tr>
<th> Estado de seguimiento </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td>   de <b>alta precisión</b></td><td style="background-color: green; color: white"> &lt; 1,0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Alta precisión (riesgo de pérdida)</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Precisión aproximada</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: orange"> Aproximado </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Ninguna posición</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: orange"> Aproximado </td><td style="background-color: orange"> falso</td>
</tr>
</table>



Estos Estados de seguimiento del controlador de movimiento se definen de la siguiente manera:
* **Alta precisión:** Aunque el controlador de movimiento está en el campo de vista del casco, normalmente proporcionará posiciones de alta precisión en función del seguimiento visual. Tenga en cuenta que un controlador de movimiento que deja momentáneamente el campo de vista o que se oculta momentáneamente de los sensores de auriculares (por ejemplo, por la otra mano del usuario) seguirá devolviendo supuestos de alta precisión durante un breve período de tiempo, en función del seguimiento inerte del controlador. propio.
* **Alta precisión (riesgo de pérdida):** Cuando el usuario mueve el controlador de movimiento más allá del borde del campo de vista del casco, el casco pronto no podrá realizar un seguimiento visual de la posición del controlador. La aplicación sabe cuándo el controlador ha alcanzado este límite de hiperapartados; para ello, vea el **SourceLossRisk** Reach 1,0. En ese momento, la aplicación puede optar por pausar los gestos del controlador que requieren un flujo estable de planteamientos de alta calidad.
* **Precisión aproximada:** Cuando el controlador ha perdido el seguimiento visual durante el tiempo suficiente, las posiciones del controlador se quitarán de las posiciones de precisión aproximada. En este punto, el sistema bloqueará el controlador al usuario, realizará un seguimiento de la posición del usuario a medida que se mueven, mientras se expone la verdadera orientación del controlador mediante sus sensores de orientación internos. Muchas aplicaciones que usan Controladores para apuntar a los elementos de la interfaz de usuario y activarlos pueden funcionar de la manera normal, pero con una precisión aproximada sin que los usuarios lo noten. Las aplicaciones con requisitos de entrada más pesados pueden optar por detectar este descenso de **alta** precisión a una precisión **aproximada** mediante la inspección de la propiedad **PositionAccuracy** , por ejemplo, para proporcionar al usuario una hitbox más amplia en los destinos de la pantalla durante este tiempo.
* **Ninguna posición:** Aunque el controlador puede funcionar con una precisión aproximada durante mucho tiempo, a veces el sistema sabe que incluso una posición bloqueada por el cuerpo no es significativa en este momento. Por ejemplo, un controlador que se acaba de activar puede que nunca se haya observado visualmente, o que un usuario pueda poner un controlador que recoja otro usuario. En ese momento, el sistema no proporcionará ninguna posición a la aplicación y **TryGetPosition** devolverá FALSE.

## <a name="interactions-low-level-spatial-input"></a>Interacciones: entrada espacial de bajo nivel

Las interacciones principales entre los controladores de manos y de movimiento son **Select**, **Menu**, **agarre**, **touchpad**, **Stick**y **Home**.
* **Select** es la interacción principal para activar un holograma, que consta de una prensa seguida de una versión. En el caso de los controladores de movimiento, se realiza una presión Select mediante el desencadenador del controlador. Otras maneras de realizar una selección consisten en hablar del [comando de voz](voice-input.md) "Select". Se puede usar la misma interacción SELECT en cualquier aplicación. Piense en seleccionar como equivalente a un clic del mouse, una acción universal que aprenderá una vez y, a continuación, se aplicará a todas las aplicaciones.
* El **menú** es la interacción secundaria para actuar en un objeto, que se usa para extraer un menú contextual o realizar alguna otra acción secundaria. Con los controladores de movimiento, puede realizar una acción de menú mediante el botón de *menú* del controlador. (es decir, el botón con el icono "menú" de la hamburguesa)
* El **agarre** es el modo en que los usuarios pueden realizar acciones directamente en los objetos para manipularlos. Con los controladores de movimiento, puede llevar a cabo una acción de agarre al apretar el puño. Un controlador de movimiento puede detectar un agarre con un botón de agarre, un desencadenador de Palm u otro sensor.
* **Touchpad** permite al usuario ajustar una acción en dos dimensiones en la superficie del panel táctil de un controlador de movimiento, con lo que se confirma la acción haciendo clic en la parte inferior del panel táctil. Los Touchpads proporcionan un estado presionado, el estado tocado y las coordenadas XY normalizadas. X e y oscilan entre-1 y 1 en el intervalo del Touchpad circular, con un centro en (0,0). Para X,-1 está a la izquierda y 1 está a la derecha. En el caso de Y,-1 está en la parte inferior y 1 en la parte superior.
* El **Stick** le permite al usuario ajustar una acción en dos dimensiones moviendo el stick de un controlador de movimiento dentro de su intervalo circular y confirmando la acción haciendo clic en abajo en el stick. Thumbsticks también proporcionan un estado presionado y coordenadas XY normalizadas. X e y oscilan entre-1 y 1 en el intervalo del Touchpad circular, con un centro en (0,0). Para X,-1 está a la izquierda y 1 está a la derecha. En el caso de Y,-1 está en la parte inferior y 1 en la parte superior.
* **Inicio** es una acción especial del sistema que se usa para volver al menú Inicio. Es similar a presionar la tecla Windows en un teclado o el botón Xbox en un controlador Xbox. Para ir a la Página principal, presione el botón Windows en un controlador de movimiento. Tenga en cuenta que también puede volver a empezar por decir "Hola Cortana, ir a Inicio". Las aplicaciones no pueden reaccionar específicamente a las acciones de inicio, ya que las administra el sistema.

## <a name="composite-gestures-high-level-spatial-input"></a>Gestos compuestos: entrada espacial de alto nivel

Se puede realizar un seguimiento de los [gestos de mano](gaze-and-commit.md#composite-gestures) y los controladores de movimiento a lo largo del tiempo para detectar un conjunto común de **[gestos compuestos](gaze-and-commit.md#composite-gestures)** de alto nivel. Esto permite que la aplicación detecte gestos **de pulsación de alto nivel,** de **suspensión**, de **manipulación** y **navegación** , tanto si los usuarios acaban usando manos o controladores.

## <a name="rendering-the-motion-controller-model"></a>Representación del modelo de controlador de movimiento

**modelos de controlador 3D** Windows pone a disposición de las aplicaciones un modelo representable de cada controlador de movimiento activo actualmente en el sistema. Al hacer que la aplicación cargue dinámicamente y articular estos modelos de controlador proporcionados por el sistema en tiempo de ejecución, puede asegurarse de que la aplicación sea compatible con versiones posteriores a cualquier diseño de controlador futuro.

Estos modelos representables deben representarse en la representación del controlador, ya que el origen del modelo se alinea con este **punto del mundo** físico. Si está representando modelos de controlador, puede que desee Raycast en la escena desde la representación del **puntero**, que representa el rayo a lo largo del que los usuarios esperarán de forma natural, dado el diseño físico del controlador.

Para más información sobre cómo cargar modelos de controlador de forma dinámica en Unity, consulte la sección [representación del modelo de controlador de movimiento en Unity](gestures-and-motion-controllers-in-unity.md#rendering-the-motion-controller-model-in-unity) .

**arte de línea del controlador 2D** Aunque se recomienda asociar los comandos y las sugerencias de la controladora en la aplicación a los propios modelos de App Controller, es posible que algunos desarrolladores quieran usar representaciones de arte de línea 2D de los controladores de movimiento en la interfaz de usuario "Tutorial" o "cómo". Para esos desarrolladores, hemos hecho que los archivos de imagen del controlador de movimiento. png estén disponibles tanto en blanco como en blanco a continuación (haga clic con el botón derecho para guardarlos).

![Vista previa de los gráficos de líneas de los controladores de movimiento](images/motioncontrollers-black-preview-300px.png)

[Arte de línea de los controladores de movimiento de resolución completa en ' ' ' blanco ' ' '](images/motioncontrollers-white.png)
 
[Imagen de los controladores de movimiento de resolución completa en ' ' ' negro ' ' '](images/motioncontrollers-black.png)

## <a name="faq"></a>Preguntas más frecuentes

### <a name="can-i-pair-motion-controllers-to-multiple-pcs"></a>¿Puedo emparejar controladores de movimiento a varios equipos?

Los controladores de movimiento admiten el emparejamiento con un solo equipo. Siga las instrucciones de la [configuración del controlador de movimiento](motion-controllers.md#setup) para emparejar los controladores.

### <a name="how-do-i-update-motion-controller-firmware"></a>Cómo actualizar el firmware del controlador de movimiento

El firmware del controlador de movimiento forma parte del controlador de casco y se actualizará automáticamente al conectarse si es necesario. Las actualizaciones de firmware suelen tardar 1-2 minutos según la radio Bluetooth y la calidad de los vínculos. En raras ocasiones, las actualizaciones de firmware del controlador pueden tardar hasta 10 minutos, lo que puede indicar una mala conectividad Bluetooth o interferencias de radio. Consulte [prácticas recomendadas de Bluetooth en la guía de entusiastas](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) para solucionar problemas de conectividad. Después de una actualización de firmware, los controladores se reinician y se vuelven a conectar al equipo host (es posible que observe que los LED van brillantes para el seguimiento). Si se interrumpe una actualización de firmware (por ejemplo, los controladores pierden energía), se volverá a intentar la próxima vez que se enciendan los controladores.

### <a name="how-i-can-check-battery-level"></a>¿Cómo puedo comprobar el nivel de batería?

En la [Página principal de Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md), puede activar el controlador para ver el nivel de batería en el lado inverso del modelo virtual. No hay ningún indicador de nivel de batería físico.

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>¿Puede usar estos controladores sin un casco? Solo para la entrada joystick/Trigger/etc?

No para aplicaciones universales de Windows.

## <a name="troubleshooting"></a>Solución de problemas

Consulte [solución de problemas del controlador de movimiento](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers) en la guía de entusiastas.

## <a name="filing-motion-controller-feedbackbugs"></a>Archivado de comentarios y errores del controlador de movimiento

Envíenos [sus comentarios](give-us-feedback.md) en la central de comentarios, usando la categoría de entrada de > de realidad mixta.

## <a name="see-also"></a>Consulte también
* [Gestos y controladores de movimiento en Unity](gestures-and-motion-controllers-in-unity.md)
* [Manos y controladores de movimiento en DirectX](hands-and-motion-controllers-in-directx.md)
* [Gestos](gaze-and-commit.md#composite-gestures)
* [Entrada MR 213: Controladores de movimiento](mixed-reality-213.md)
* [Guía del entusiasta: su página principal de Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/your-mixed-reality-home)
* [Guía del entusiasta: uso de juegos & aplicaciones en Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-games-and-apps-in-windows-mixed-reality)
* [Cómo funciona el seguimiento interno](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/tracking-system)
