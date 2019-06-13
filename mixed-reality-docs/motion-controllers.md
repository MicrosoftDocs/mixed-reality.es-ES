---
title: Controladores de movimiento
description: Obtener más información sobre los controladores de movimiento de realidad mixta.
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: 6GDL controladores, los controladores de movimiento
ms.openlocfilehash: fc6b0dcf7f338224af9ea9bc59e07187c33adda2
ms.sourcegitcommit: 150d258a23130026c8792da383a3993657841fb4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2019
ms.locfileid: "67024556"
---
# <a name="motion-controllers"></a>Controladores de movimiento

Los controladores de movimiento son [accesorios de hardware](hardware-accessories.md) que permiten a los usuarios realizar una acción en la realidad mixta. Una ventaja de los controladores de movimiento a través de [gestos](gestures.md) es que los controladores tienen una posición exacta en el espacio, lo que permite una interacción específica con objetos digitales. Para inmersivos Windows Mixed Reality, controladores de movimiento son la principal manera que los usuarios actuará en su mundo.

![Controladores de movimiento Windows Mixed Reality](images/winmr-ck-1080x1080-350px.jpg)


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
     <td>Controladores de movimiento</td>
     <td>❌</td>
     <td>❌</td>
     <td>✔️</td>
</tr>
</table>

## <a name="hardware-details"></a>Detalles del hardware

>[!VIDEO https://www.youtube.com/embed/1nlcdDNOdm8]

Los controladores de Windows Mixed Reality movimiento ofrecen seguimiento precisa y con capacidad de respuesta de movimiento en el campo de visión con los sensores en los auriculares envolventes, lo que significa que no es necesario instalar hardware de los planos laterales en su espacio. Estos controladores de movimiento ofrecerá la misma facilidad de instalación y la portabilidad como inmersivos Windows Mixed Reality. Plan de nuestros asociados de dispositivos comercializar y vender este vacaciones de estos controladores en las estanterías de venta directa.

![Familiarícese con el controlador](images/controllerimage-750px.png)<br>
*Familiarícese con el controlador*

**Funciones:**
* Seguimiento de medios óptico
* desencadenador
* Botón de captura
* Tecla de navegación
* Panel táctil

## <a name="setup"></a>Programa de instalación

### <a name="before-you-begin"></a>Antes de comenzar

**Necesitará:**
* Un conjunto de dos controladores de movimiento.
* Cuatro baterías AA.
* Un equipo capaz de Bluetooth 4.0.

**Compruebe si hay actualizaciones de Windows, Unity y controlador**
* Visite [instalar las herramientas de](install-the-tools.md) para las versiones preferidas de Windows, Unity, etc. para el desarrollo de realidad mixta.
* Asegúrese de que tiene la copia más actualizada [controladores del controlador de auriculares y movimiento](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software).

### <a name="pairing-controllers"></a>Controladores de emparejamiento

Los controladores de movimiento pueden conectarse con el equipo host mediante la configuración de Windows como cualquier otro dispositivo Bluetooth.

1. Insertar 2 pilas AA en la parte posterior del controlador. Omita la portada de la batería por ahora.
2. Si usa un adaptador de Bluetooth USB externo en lugar de una radio Bluetooth integrada, revise el [prácticas recomendadas de Bluetooth](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) antes de continuar. Para la configuración de escritorio con radio integrado, asegúrese que está conectada la antena.
3. Abra **Windows configuración** -> **dispositivos** -> **agregar Bluetooth u otro dispositivo** -> **Bluetooth** y quite las instancias anteriores de "Controlador de movimiento: derecha" y "Controlador de movimiento: Left". Compruebe también otra categoría de dispositivos en la parte inferior de la lista.
4. Seleccione **agregar Bluetooth u otro dispositivo** y ver cómo comenzar a detectar dispositivos Bluetooth.
5. Presione y mantenga el botón de Windows del controlador para activar el controlador, liberarlo una vez zumbido.
6. Presionar y mantener presionado el botón de emparejamiento (pestaña en el compartimiento de la batería) hasta que los LED comienzan pulso.
7. Espere "Controlador de movimiento - izquierda" o "Controlador de movimiento - derecha" aparezca en la parte inferior de la lista. Seleccione esta opción para par. Controlador se Vibrar una vez cuando se conecta.

   ![Seleccione el controlador de movimiento para par, si selecciona varias instancias de uno de abajo que aparece de la lista](images/450px-bluetooth-add-a-device-300px.png)<br>
   *Seleccione "Controlador de movimiento" al par; Si hay varias instancias, seleccione uno en la parte inferior de la lista*
   
8. Verá que el controlador aparecen en la configuración de Bluetooth en **"Lápiz, teclado y Mouse" categoría** como **conectado**. En este momento, es posible que obtenga una actualización de firmware: vea [siguiente sección](motion-controllers.md#updating-controller-firmware).
9. Volver a adjuntar portada de la batería.
10. Repita los pasos 1 a 9 para el segundo controlador.

Después del emparejamiento correctamente ambos controladores, la configuración debería ser similar al siguiente en **"Lápiz, teclado y Mouse" categoría** 

   ![Controladores de movimiento conectados](images/450px-motion-controller-connected-300px.png)<br>
   *Controladores de movimiento conectados*

Si los controladores están desactivados después del emparejamiento, su estado se mostrará como emparejada. Si los controladores de forma permanente permanecen dentro de "Otros dispositivos" categoría emparejamiento puede haberse solo parcialmente completado y la necesidad de realizar de nuevo para obtener el controlador funcional.

### <a name="updating-controller-firmware"></a>Actualización de firmware del controlador

* Si un auricular envolvente está conectado a su equipo y nuevo firmware del controlador está disponible, el firmware se insertarán en los controladores de movimiento automáticamente la próxima vez que están activados. Las actualizaciones de firmware del controlador se indican mediante un modelo de iluminación de LED de cuadrantes en un movimiento circular y tardar entre 1 y 2 minutos.
* Una vez finalizada la actualización del firmware, los controladores se reinicie y volver a conectar. Ambos controladores deben estar conectados ahora. 
    
    ![Controladores conectados](images/cyk-connected-300px.jpg)<br>
    *Controladores conectados en la configuración de Bluetooth*

* Comprobar correctamente el trabajo de controladores:
    1. Iniciar **Portal de realidad mixta** y escriba su casa de realidad mixta.
    2. Mueva los controladores y compruebe el seguimiento de los botones de la prueba y compruebe [teleportation](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) funciona. Si no, a continuación, salen [solución de problemas de controlador de movimiento](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers).

## <a name="gazing-and-pointing"></a>Gazing y señalando

Windows Mixed Reality admite dos modelos claves para la interacción, **que mirar y confirmar** y **elija y confirme**:
* Con **que mirar y confirmar**, los usuarios de destino un objeto con su [que mirar](gaze.md) y, a continuación, seleccionar objetos con derivaciones de aire de mano, un controlador para juegos, un clicker o su propia voz.
* Con **elija y confirme**, un usuario puede tener como objetivo un controlador de movimiento capaz señalando en el objeto de destino y, a continuación, seleccione los objetos con el desencadenador del controlador.

Las aplicaciones que soporte técnico que señala con los controladores de movimiento también debería permiten interacciones controladas por mirada siempre que sea posible, proporcionar a los usuarios de elección en lo que entrada dispositivos que usan.

### <a name="managing-recoil-when-pointing"></a>Administrar recoil al que apunta

Al usar controladores de movimiento de punto y confirmar, los usuarios utilizarán el controlador de destino y, a continuación, tomar medidas mediante la extracción su desencadenador. Los usuarios que el desencadenador de extracción enérgicamente pueden acabar apuntando el controlador superior al final de su extracción de desencadenador que pretendía.

Para administrar cualquier tal recoil que puede producirse cuando el desencadenador de extracción de los usuarios, la aplicación puede ajustar su ray destinatarios al valor de eje analógico del desencadenador está por encima de 0,0. A continuación, actuar con ese destino ray unos marcos más adelante una vez que el valor desencadenador alcanza el valor 1,0, siempre y cuando se produce la acción de presionar final dentro de un período de tiempo breve. Cuando se usa el nivel más alto [compuesto gesto de pulsar](gestures.md#composite-gestures), Windows administrará destinadas a ray captura y tiempo de espera para usted.

## <a name="grip-pose-vs-pointing-pose"></a>Postura de control frente a la postura señalador

Windows Mixed Reality es compatible con controladores de movimiento en una variedad de factores de forma, con el diseño de cada controlador que se diferencia en su relación entre la posición del usuario mano y natural "Reenviar" dirección de que las aplicaciones debe utilizar para que apunte al representar el controlador.

Para representar mejor estos controladores, hay dos tipos de plantea puede investigar para cada origen de interacción, el **control postura** y el **puntero postura**.

### <a name="grip-pose"></a>Postura de control

El **control postura** representa la ubicación de la palma de una mano detectada por un HoloLens, o bien la palma que contiene un controlador de movimiento.

En inmersivos, la postura de control se utiliza mejor para representar **la mano del usuario** o **mantiene un objeto en la mano del usuario**, como una Espada o filo. La postura de control también se utiliza al visualizar un controlador de movimiento, como el **modelo representable** proporcionados por Windows para un movimiento controlador utiliza la postura de control como su origen y el centro de rotación.

La postura de control se define específicamente como sigue:
* El **sujete posición**: El centroide de palm cuando se mantiene el controlador de forma natural, ajustar izquierda o derecha para centrar la posición dentro del control. En el controlador de movimiento Windows Mixed Reality, esta posición generalmente se alinea con el botón de entender.
* El **sujete eje derecho de orientación**: Cuando se abre completamente la mano para formar una postura plano 5-dedo, el rayo que es normal que la palma (hacia delante desde la palma de izquierdo, con versiones anteriores desde la palma derecha)
* El **sujete eje hacia delante de orientación**: Cuando cierre la mano parcialmente (como si mantiene el controlador), el rayo que señala "forward" a través del tubo formado por los dedos no thumb.
* El **sujete orientación de eje**: El eje vertical implicado en las definiciones de la derecha y hacia delante.

### <a name="pointer-pose"></a>Postura de puntero

El **puntero postura** representa la punta del controlador que señala hacia delante.

La postura de puntero proporcionado por el sistema se utiliza mejor para raycast cuando esté **el propio modelo de controlador de representación**. Si está representando algún otro objeto virtual en lugar del controlador, como un cañón virtual, debe señalar con un radio que es más natural para ese objeto virtual, como un radio que recorre el Cañón del modelo filo definido por la aplicación. Dado que los usuarios pueden ver el objeto virtual y no en el controlador físico, que apunta con el objeto virtual probablemente será más natural para aquellos que usen la aplicación.

## <a name="controller-tracking-state"></a>Estado del controlador de seguimiento

Al igual que los auriculares, el controlador de movimiento de Windows Mixed Reality no requiere ninguna configuración de los sensores de seguimiento externas. En su lugar, se realiza un seguimiento de los controladores de sensores en los auriculares en sí mismo.

Si el usuario mueve los controladores de campo de la vista de los auriculares, en la mayoría de los casos Windows seguirá deducir las posiciones de controlador y le proporciona a la aplicación. Cuando el controlador ha perdido un seguimiento visual de tiempo suficiente, se quitarán las posiciones del controlador a las posiciones de precisión aproximado.

En este momento, el sistema las eliminará bloqueo del cuerpo del controlador para el usuario, la posición del usuario de seguimiento a medida que se mueven, mientras se sigue manteniendo la orientación del controlador de true mediante sus sensores de orientación interna. Muchas aplicaciones que usen controladores para apuntar al y activar los elementos de interfaz de usuario pueden funcionar normalmente aunque aproximado con una precisión de sin que el usuario lo advierta.

&nbsp;

>[!VIDEO https://www.youtube.com/embed/rkDpRllbLII]

### <a name="reasoning-about-tracking-state-explicitly"></a>Seguimiento del estado de forma explícita el razonamiento

Las aplicaciones que desea tratar las posiciones de manera diferente en función de seguimiento del estado pueden ir más allá e inspeccionar las propiedades en el estado del controlador, como SourceLossRisk y PositionAccuracy:

<table>
<tr>
<th> Estado de seguimiento </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>Alta precisión</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Alta precisión (corre el riesgo de perder)</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Precisión aproximado</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Aproximado </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Ninguna posición</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Aproximado </td><td style="background-color: orange"> falso</td>
</tr>
</table>



Estos Estados de seguimiento del controlador de movimiento se definen como sigue:
* **Alta precisión:** Mientras el controlador de movimiento está dentro de campo de la vista de los auriculares, generalmente entregará las posiciones de alta precisión, en función de seguimiento visual. Tenga en cuenta que un controlador de movimiento que momentáneamente deja el campo de visión o se oculta temporalmente de los sensores de auriculares (por ejemplo, por otro lado del usuario) continuará devolviendo plantea de alta precisión durante un breve período, en función de seguimiento inercial del controlador Sí.
* **Alta precisión (corre el riesgo de perder):** Cuando el usuario mueve el controlador de movimiento más allá del borde de campo de la vista de los auriculares, los auriculares pronto podrá realizar un seguimiento visual de la posición del dispositivo. La aplicación conoce cuando el controlador ha alcanzado este límite FOV viendo el **SourceLossRisk** llegar a 1.0. En ese momento, la aplicación puede optar por pausar los gestos de controlador que requieren un flujo constante de plantea muy alta calidad.
* **Precisión aproximado:** Cuando el controlador ha perdido un seguimiento visual de tiempo suficiente, se quitarán las posiciones del controlador a las posiciones de precisión aproximado. En este momento, el sistema las eliminará bloqueo del cuerpo del controlador para el usuario, la posición del usuario de seguimiento a medida que se mueven, mientras se sigue manteniendo la orientación del controlador de true mediante sus sensores de orientación interna. Muchas aplicaciones que usen controladores para apuntar al y activar los elementos de interfaz de usuario pueden funcionar como while normal con una precisión aproximada de sin que el usuario lo advierta. Pueden elegir sentido esta lista de aplicaciones con requisitos de entrada más **alta** precisión a **aproximado** precisión inspeccionando el **PositionAccuracy** propiedad, para ejemplo para otorgar al usuario un hitbox más generosa en destinos fuera de la pantalla durante este tiempo.
* **Ninguna posición:** Mientras que el controlador puede operar en una precisión aproximada durante mucho tiempo, en ocasiones, el sistema sepa que incluso una posición bloqueada de cuerpo no es significativa en este momento. Por ejemplo, un controlador que ha estado encendido solo es posible que nunca se han observado visualmente, o un usuario puede dejar un controlador que, a continuación, se recoge por otra persona. En esos momentos, el sistema no proporcionará cualquier posición a la aplicación, y **TryGetPosition** devolverá false.

## <a name="interactions-low-level-spatial-input"></a>Interacciones: Entrada de espacial de bajo nivel

Las interacciones principales entre manos y los controladores de movimiento son **seleccione**, **menú**, **sujete**, **panel táctil**,  **Tecla de navegación**, y **inicio**.
* **Seleccione** es la interacción principal para activar un holograma, que consta de un presione seguido de una versión. Para los controladores de movimiento, realizar un Select presione con el desencadenador del controlador. Otras formas de realizar una operación Select están hablando el [comandos de voz](voice-input.md) "Select". La misma interacción select puede usarse dentro de cualquier aplicación. Pensar en Seleccione clic en el equivalente de un mouse, una acción universal que aprender una vez y, a continuación, se aplican en todas las aplicaciones.
* **Menú** es la interacción secundaria para actuar sobre un objeto que se usa para extraer un menú contextual o realizar alguna otra acción secundaria. Con los controladores de movimiento, puede realizar una acción de menú con el controlador *menú* botón. (es decir, el botón con el icono de "menú" hamburguesa)
* **Sujete** es cómo los usuarios directamente pueden realizar acciones en los objetos en su mano para manipularlos. Con los controladores de movimiento, puede hacer una acción de comprensión contrayendo estrechamente el puño. Un controlador de movimiento puede detectar una idea con un botón de captura, un desencadenador de palm u otro sensor.
* **Panel táctil** permite al usuario ajustar una acción en dos dimensiones a lo largo de la superficie de pantalla táctil de un controlador de movimiento, confirmar la acción, haga clic abajo en el panel táctil. Touchpads proporcionan un estado presionado tocar y normalizadas coordenadas XY. Rango X e Y de -1 a 1 entre el intervalo de la pantalla táctil circular, con un centro en (0, 0). Para X, -1 está a la izquierda y 1 está a la derecha. Y, es -1 en la parte inferior y 1 es la parte superior.
* **Tecla de navegación** permite al usuario ajustar una acción en dos dimensiones moviendo la tecla de navegación de un controlador de movimiento dentro de su intervalo circular, confirmar la acción, haga clic abajo en la tecla de navegación. Sticks analógicos también proporcionan un estado presionado y normalizan las coordenadas XY. Rango X e Y de -1 a 1 entre el intervalo de la pantalla táctil circular, con un centro en (0, 0). Para X, -1 está a la izquierda y 1 está a la derecha. Y, es -1 en la parte inferior y 1 es la parte superior.
* **Inicio** es una acción especial del sistema que se usa para volver al menú Inicio. Es similar a presionar la tecla de Windows en un teclado o el botón de Xbox en un controlador de Xbox. Puede ir inicio presionando el botón de Windows en un controlador de movimiento. Tenga en cuenta que también siempre puede volver a inicio diciendo "Hola Cortana, Go Home". No pueden reaccionar ante las aplicaciones específicamente a las acciones de inicio, tal como se administran por el sistema.

## <a name="composite-gestures-high-level-spatial-input"></a>Gestos compuestos: Entrada de espacial de alto nivel

Ambos [gestos de mano](gestures.md) y se pueden realizar el seguimiento de los controladores de movimiento con el tiempo para detectar un conjunto común de alto nivel  **[gestos compuestos](gestures.md#composite-gestures)** . Esto permite que la aplicación detectar de alto nivel **pulse**, **mantenga**, **manipulación** y **navegación** gestos, si los usuarios terminen con las manos o controladores.

## <a name="rendering-the-motion-controller-model"></a>Representación del modelo de controlador de movimiento

**Los modelos 3D controlador** Windows pone a disposición de las aplicaciones de un modelo puede presentar de cada controlador de movimiento actualmente activo en el sistema. Al tener la aplicación carga dinámicamente y explicar estos modelos de controlador proporcionado por el sistema en tiempo de ejecución, puede asegurarse de que la aplicación es diseños compatibles con el reenvío a futuras cualquier controlador.

Estos modelos representables deben representarse en el **control postura** del controlador, como el origen del modelo se alinea con este punto en el mundo físico. Si está representando los modelos de controlador, es posible que, a continuación, desea raycast en la escena de la **puntero postura**, que representa el rayo a lo largo de que los usuarios naturalmente esperará para que apunte, dado el diseño físico de ese controlador.

Para obtener más información acerca de cómo cargar modelos de controlador dinámicamente en Unity, vea el [representar el modelo de controlador de movimiento en Unity](gestures-and-motion-controllers-in-unity.md#rendering-the-motion-controller-model-in-unity) sección.

**Dibujos de líneas de controlador 2D** aunque se recomienda asociar sugerencias de controlador de la aplicación y los comandos a los propios modelos de controlador de la aplicación, algunos desarrolladores desear utilizar representaciones de material gráfico 2D de línea de los controladores de movimiento en el plano "tutorial" o "procedimientos" INTERFAZ DE USUARIO. Para aquellos desarrolladores, hemos realizado .png movimiento controlador línea archivos de imágenes prediseñadas disponibles en ambas blanco y negro a continuación (clic derecho para guardar).

![Vista previa del material gráfico de línea de los controladores de movimiento](images/motioncontrollers-black-preview-300px.png)

 [Líneas de los controladores de movimiento de alta resolución en ''' blanco '''](images/motioncontrollers-white.png)
 
 [Líneas de los controladores de movimiento de alta resolución en ''' negro '''](images/motioncontrollers-black.png)

## <a name="faq"></a>Preguntas más frecuentes

### <a name="can-i-pair-motion-controllers-to-multiple-pcs"></a>¿Puedo par motion controladores para varios equipos?

Los controladores de movimiento admiten el emparejamiento con un solo equipo. Siga las instrucciones de [el programa de instalación del controlador de movimiento](motion-controllers.md#setup) para emparejar los controladores.

### <a name="how-do-i-update-motion-controller-firmware"></a>¿Cómo se puede actualizar el firmware del controlador de movimiento?

El firmware del controlador de movimiento es parte del controlador auriculares y se actualizará automáticamente en la conexión si es necesario. Actualizaciones de firmware suelen tardar entre 1 y 2 minutos dependiendo de la calidad de radio y vínculo de Bluetooth. En raras ocasiones, las actualizaciones de firmware del controlador pueden tardar hasta 10 minutos, lo que puede indicar conectividad Bluetooth deficiente o interferencias. Consulte [Bluetooth prácticas recomendadas en la guía entusiasta](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#bluetooth-best-practices) para solucionar problemas de conectividad. Después de una actualización de firmware, los controladores se reinicia y volver a conectar con el host de PC (verá que los LED vaya brillante de seguimiento). Si se interrumpe una actualización de firmware (por ejemplo, los controladores apague), se volverá a intentar la próxima vez que los controladores estén encendidos.

### <a name="how-i-can-check-battery-level"></a>¿Cómo comprobar el nivel de la batería?

En el [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md), puede activar el controlador a través de para ver su nivel de batería en el reverso del modelo virtual. No hay ningún indicador de nivel de batería físico.

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>¿Puede usar estos controladores sin un auricular? ¿Solo para la entrada de desencadenador/joystick/etcetera?

No para aplicaciones universales de Windows.

## <a name="troubleshooting"></a>Solución de problemas

Consulte [solución de problemas de controlador de movimiento](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#motion-controllers) en la Guía de entusiastas.

## <a name="filing-motion-controller-feedbackbugs"></a>Archivar errores y comentarios de controlador de movimiento

[Envíenos sus comentarios](give-us-feedback.md) en el centro de opiniones, usando la categoría "Mixed Reality -> entrada".

## <a name="see-also"></a>Vea también
* [Gestos y controladores de movimiento en Unity](gestures-and-motion-controllers-in-unity.md)
* [Manos y controladores de movimiento en DirectX](hands-and-motion-controllers-in-directx.md)
* [Gestos](gestures.md)
* [MR Input 213: controladores de movimiento](mixed-reality-213.md)
* [Guía de entusiastas: El inicio de Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/your-mixed-reality-home)
* [Guía de entusiastas: Uso de juegos y aplicaciones en Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-games-and-apps-in-windows-mixed-reality)
* [Cómo funciona el seguimiento por completo](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/tracking-system)
