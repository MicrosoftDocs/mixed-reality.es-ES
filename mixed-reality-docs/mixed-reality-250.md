---
title: MR Sharing 250-HoloLens y auriculares envolventes
description: Siga este tutorial de codificación con auriculares con Unity, Visual Studio, HoloLens y Windows Mixed Reality para obtener información detallada sobre el uso compartido de hologramas entre dispositivos de realidad mixta.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, inmersivo, controlador de movimiento, uso compartido, controladora Xbox, redes, dispositivos cruzados
ms.openlocfilehash: c8d341f75424887ca1b0994c8a4d16a0bded671e
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437864"
---
>[!NOTE]
>Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.  Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Se ha publicado [una nueva serie de tutoriales](mrlearning-base.md) para HoloLens 2.

<br>

# <a name="mr-sharing-250-hololens-and-immersive-headsets"></a>MR Sharing 250: HoloLens y auriculares envolventes

Con la flexibilidad de Plataforma universal de Windows (UWP), es fácil crear una aplicación que abarque varios dispositivos. Con esta flexibilidad, podemos crear experiencias que aprovechen las ventajas de cada dispositivo. En este tutorial se tratará una experiencia básica compartida que se ejecuta tanto en HoloLens como en Windows Mixed Reality. Este contenido se entregó originalmente en la Conferencia de Microsoft Build 2017 en Seattle, WA.

**En este tutorial, haremos lo siguiente:**

* Configure una red mediante UNET.
* Comparta hologramas en dispositivos de realidad mixta.
* Establezca una vista diferente de la aplicación en función del dispositivo de realidad mixta que se esté usando.
* Cree una experiencia compartida en la que los usuarios de HoloLens guíen a los auriculares a través de algunos rompecabezas sencillos.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td>MR Sharing 250: HoloLens y auriculares envolventes</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de empezar

### <a name="prerequisites"></a>Requisitos previos

* Un equipo con Windows 10 con las [herramientas de desarrollo necesarias](install-the-tools.md) y [configurada para admitir un casco con Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).
* Un controlador de Xbox que funcione con su PC.
* Al menos un dispositivo HoloLens y un casco envolvente.
* Una red que permite la difusión de UDP para la detección.

### <a name="project-files"></a>Archivos de proyecto

* Descargue los [archivos](https://github.com/Microsoft/MixedReality250/archive/master.zip) requeridos por el proyecto. Extraiga los archivos a una ubicación fácil de recordar.
* Este proyecto requiere [una versión recomendada de Unity con compatibilidad con Windows Mixed Reality](install-the-tools.md).

>[!NOTE]
>Si desea examinar el código fuente antes de la descarga, está [disponible en github](https://github.com/Microsoft/MixedReality250).

## <a name="chapter-1---holo-world"></a>Capítulo 1: Hololens World

>[!VIDEO https://www.youtube.com/embed/IC0rp6rLiEc]

### <a name="objectives"></a>Objetivos

Asegúrese de que el entorno de desarrollo está listo para usar un proyecto sencillo.

### <a name="what-we-will-build"></a>Lo que se va a crear

Una aplicación que muestra un holograma en HoloLens o en un auricular envolvente de Windows Mixed Reality.

### <a name="steps"></a>Pasos

* Abra Unity.
    * Seleccione **abrir**.
    * Vaya a la ubicación donde extrajo los archivos del proyecto.
    * Haga clic en **Seleccionar carpeta**.
    * *Para que Unity procese el proyecto por primera vez, se tardará un poco.*
* Compruebe que la realidad mixta está habilitada en Unity.
    * Abra el cuadro de diálogo Configuración de compilación (**Control + Mayús + B** o **configuración de compilación de > de archivos...** ).
    * Seleccione **plataforma universal de Windows** , a continuación, haga clic en **cambiar plataforma**.
    * Seleccione **editar > configuración del reproductor**.
    * En el panel **Inspector** , en el lado derecho, expanda la **configuración de XR**.
    * Active la casilla se **admite Virtual Reality** .
    * *Windows Mixed Reality debe ser el SDK de realidad virtual.*
* Cree una escena.
    * En la **jerarquía** , haga clic con el botón secundario en **cámara principal** y seleccione **eliminar**.
    * En **HoloToolkit > entrada > Prefabs** arrastre **MixedRealityCameraParent** hasta la **jerarquía**.
* Agregar hologramas a la escena
    * En **AppPrefabs** , arrastre **SKYBOX** hasta la **vista escena**.
    * Desde **AppPrefabs** , arrastre los **administradores** a la **jerarquía**.
    * En **AppPrefabs** , arrastre **isla** hasta la **jerarquía**.
* Guardar y compilar
    * Guardar ( **control + S** o **archivo > Guardar escena**)
    * Dado que se trata de una nueva escena, deberá asignarle un nombre. El nombre no importa, pero usamos SharedMixedReality.
* Exportar a Visual Studio
    * Abrir el menú compilar (**Control + Mayús + B** o **configuración de compilación de > de archivos**)
    * Haga clic en **Agregar escenas abiertas.**
    * Comprobación **de C# proyectos de Unity**
    * Haz clic en **Compilación**.
    * En la ventana del explorador de archivos que aparece, cree una nueva carpeta denominada **App**.
    * Haga clic en la carpeta de la **aplicación** .
    * Presione **Seleccionar carpeta.**
    * **Esperar a que se complete la compilación**
    * En la ventana del explorador de archivos que aparece, navegue a la carpeta de la **aplicación** .
    * Haga doble clic en **SharedMixedReality. sln** para iniciar Visual Studio
* Compilación desde Visual Studio
    * El uso de la barra de herramientas superior cambia el destino a **Release** y **x86**.
    * Haga clic en la flecha situada junto a **equipo local** y seleccione el **dispositivo** que desea implementar en HoloLens.
    * Haga clic en la flecha situada junto a **dispositivo** y seleccione **equipo local** para implementar el casco de realidad mixta.
    * Haga clic en **depurar-> iniciar sin depurar** o **Ctrl + F5** para iniciar la aplicación.

### <a name="digging-into-the-code"></a>Profundizar en el código

En el panel Proyecto, desplácese a **Assets\HoloToolkit\Input\Scripts\Utilities** y haga doble clic en **MixedRealityCameraManager.CS** para abrirlo.

**Información general:** MixedRealityCameraManager.cs es un script sencillo que ajusta la configuración de nivel de calidad y de fondo en función del dispositivo. La clave aquí es HolographicSettings. IsDisplayOpaque, que permite que un script detecte si el dispositivo es un HoloLens (IsDisplayOpaque devuelve false) o un auricular envolvente (IsDisplayOpaque devuelve true).

### <a name="enjoy-your-progress"></a>Disfrute de su progreso

En este momento, la aplicación solo presentará un holograma. Más adelante se agregará la interacción con el holograma. Ambos dispositivos representarán el holograma. Los auriculares inmersivo también representarán un fondo azul cielo y nubes.

## <a name="chapter-2---interaction"></a>Capítulo 2: interacción

>[!VIDEO https://www.youtube.com/embed/Lrb1y4sQRvI]

### <a name="objectives"></a>Objetivos

Muestra cómo controlar la entrada de una aplicación de Windows Mixed Reality.

### <a name="what-we-will-build"></a>Lo que se va a crear

Al basarse en la aplicación del capítulo 1, agregaremos funcionalidad para que el usuario pueda seleccionar el holograma y colocarlo en una superficie real de HoloLens o en una tabla virtual en un casco envolvente.

**Actualizador de entrada:** En HoloLens, el gesto de selección es la **TAP del aire**. En los auriculares inmersivo, usaremos el botón **a** del controlador Xbox. Para obtener más información, consulte la información [General sobre el modelo de interacción](interaction-fundamentals.md).

### <a name="steps"></a>Pasos

* Agregar administrador de entrada
    * En **HoloToolkit > entrada > Prefabs** arrastre **InputManager** hasta **jerarquía** como elemento secundario de **Managers**.
    * En **HoloToolkit > entrada > Prefabs >** **cursor de arrastre** del cursor a la **jerarquía**.
* Agregar asignación espacial
    * En **HoloToolkit > SpatialMapping > Prefabs** arrastre **SpatialMapping** hasta **jerarquía**.
* Agregar Playspace virtuales
    * En la **jerarquía** , expanda **MixedRealityCameraParent** seleccionar **límite**
    * En el panel **Inspector** , active la casilla para habilitar el **límite** .
    * En **AppPrefabs** , arrastre **VRRoom** hasta **jerarquía**.
* Agregar WorldAnchorManager
    * En **jerarquía**, seleccione **administradores**.
    * En **Inspector**, haga clic en **Agregar componente**.
    * Escriba **World Limit Manager**.
    * Seleccione **World Anchor Manager** para agregarlo.
* Agregar TapToPlace a la isla
    * En **jerarquía**, expanda **isla**.
    * Seleccione **MixedRealityLand**.
    * En **Inspector**, haga clic en **Agregar componente**.
    * Escriba **TAP para colocarlo** y selecciónelo.
    * Active **colocar primario al pulsar**.
    * Establezca **desplazamiento de selección de ubicación** en **(0, 0,1, 0)** .
* Guardar y compilar como antes

### <a name="digging-into-the-code"></a>Profundizar en el código

**Script 1: GamepadInput.cs**

En el panel Proyecto, vaya a **Assets\HoloToolkit\Input\Scripts\InputSources** y haga doble clic en **GamepadInput.CS** para abrirlo. En la misma ruta de acceso del panel Proyecto, haga doble clic en **InteractionSourceInputSource.CS**.

Tenga en cuenta que ambos scripts tienen una clase base común, BaseInputSource.

BaseInputSource mantiene una referencia a un InputManager, que permite a un script desencadenar eventos. En este caso, el evento InputClicked es relevante. Esto será importante recordar cuando lleguemos al script 2, TapToPlace. En el caso de GamePadInput, se sondea la presencia de un botón en el controlador que se va a presionar y, a continuación, se genera el evento InputClicked. En el caso de InteractionSourceInputSource, se genera el evento InputClicked en respuesta a TappedEvent.

**Script 2: TapToPlace.cs**

En el panel Proyecto, vaya a **Assets\HoloToolkit\SpatialMapping\Scripts** y haga doble clic en **TapToPlace.CS** para abrirlo.

Lo primero que muchos desarrolladores desean implementar al crear una aplicación holográfica es mover hologramas con entrada de gestos. Por lo tanto, hemos hechonos comentar este script minuciosamente. Hay algunas cosas que merece la pena resaltar en este tutorial.

En primer lugar, tenga en cuenta que TapToPlace implementa IInputClickHandler. IInputClickHandler expone las funciones que controlan el evento InputClicked generado por GamePadInput.cs o InteractionSourceInputSource.cs. Se llama a OnInputClicked cuando un BaseInputSource detecta un clic mientras el objeto con TapToPlace está en el foco. Si puntea en HoloLens o si presiona el botón A del controlador Xbox, se desencadenará el evento.

Segundo es el código que se ejecuta en la actualización para ver si se está examinando una superficie para que podamos colocar el objeto de juego en una superficie, como una tabla. El casco envolvente no tiene un concepto de superficies reales, por lo que el objeto que representa la tabla superior (Vroom > TableThingy > Cube) se ha marcado con la capa física SpatialMapping, por lo que la conversión de rayo en la actualización entrará en conflicto con la tabla virtual superior.

### <a name="enjoy-your-progress"></a>Disfrute de su progreso

Esta vez puede seleccionar la isla para moverla. En HoloLens puede trasladar la isla a una superficie real. En el casco envolvente puede trasladar la isla a la tabla virtual que hemos agregado.

## <a name="chapter-3---sharing"></a>Capítulo 3: compartir

>[!VIDEO https://www.youtube.com/embed/1diycJvxfDc]

### <a name="objectives"></a>Objetivos

Asegúrese de que la red está configurada correctamente y detalle cómo se comparten los anclajes espaciales entre los dispositivos.

### <a name="what-we-will-build"></a>Lo que se va a crear

Convertiremos el proyecto en un proyecto de varios jugadores. Agregaremos la interfaz de usuario y la lógica para hospedar o unirse a sesiones. Los usuarios de HoloLens se verán entre sí en la sesión con nubes a través de sus cabezales y los auriculares de un casco envolventes tienen nubes cerca de donde se encuentra el delimitador. Los usuarios de los auriculares envolventes verán los usuarios de HoloLens en relación con el origen de la escena. Todos los usuarios de HoloLens verán el holograma de la isla en el mismo lugar. Es importante tener en cuenta que los usuarios de los auriculares envolventes no estarán en la isla durante este capítulo, pero se comportarán de forma similar a HoloLens, con una vista de pájaros de la isla.

### <a name="steps"></a>Pasos

* Quitar isla y VRRoom
    * En **jerarquía** , haga clic con el botón derecho en **isla** seleccionar **eliminar**
    * En **jerarquía** , haga clic con el botón derecho en **VRRoom** seleccionar **eliminar**
* Agregar Usland
    * En **AppPrefabs** , arrastre **Usland** hasta **jerarquía**.
* En **AppPrefabs** , arrastre cada una de las siguientes a la **jerarquía**:
    * **UNETSharingStage**
    * **UNetAnchorRoot**
    * **UIContainer**
    * **DebugPanelButton**
* Guardar y compilar como antes

### <a name="digging-into-the-code"></a>Profundizar en el código

En el panel Proyecto, desplácese a **Assets\AppPrefabs\Support\SharingWithUnet\Scripts** y haga doble clic en **UnetAnchorManager.CS**. La capacidad de un HoloLens de compartir información de seguimiento con otro HoloLens, de modo que ambos dispositivos puedan compartir el mismo espacio es un punto mágico. La eficacia de la realidad mixta se pone en conexión cuando dos o más personas pueden colaborar con los mismos datos digitales.

Algunos aspectos que se deben señalar en este script:

En la función de inicio, observe la comprobación de **IsDisplayOpaque**. En este caso, supondremos que se establece el delimitador. Esto se debe a que los auriculares envolventes no exponen una manera de importar o exportar delimitadores. Sin embargo, si se ejecuta en HoloLens, este script implementa los delimitadores de uso compartido entre los dispositivos. El dispositivo que inicia la sesión creará un delimitador para la exportación. El dispositivo que se une a una sesión solicitará el delimitador del dispositivo que inició la sesión.

**Exportador**

Cuando un usuario crea una sesión, NetworkDiscoveryWithAnchors llamará a la función UNETAnchorManagers CreateAnchor. Vamos a seguir el flujo de CreateAnchor.

Comenzaremos llevando a cabo algún mantenimiento, borrando los datos que podamos haber recopilado para los delimitadores anteriores. A continuación, se comprueba si hay un delimitador en caché para cargar. Los datos del delimitador suelen tener entre 5 y 20 MB, por lo que reutilizar los delimitadores en caché puede ahorrar en la cantidad de datos que necesitamos transferir a través de la red. Veremos cómo funciona un poco más adelante. Aunque se vuelva a usar el delimitador, es necesario que los datos del delimitador estén listos en caso de que un nuevo cliente se unan que no tenga el delimitador.

Hablando de la preparación de los datos de delimitador, la clase WorldAnchorTransferBatch expone la funcionalidad para preparar los datos de delimitador para el envío a otro dispositivo o aplicación y la funcionalidad para importar los datos de delimitador. Como estamos en la ruta de acceso de exportación, agregaremos el delimitador a WorldAnchorTransferBatch y llamaremos a la función ExportAsync. ExportAsync llamará a la devolución de llamada WriteBuffer a medida que genera datos para la exportación. Cuando todos los datos se hayan exportado, se llamará a ExportComplete. En WriteBuffer, se agrega el fragmento de datos a una lista que se conserva para la exportación. En ExportComplete, la lista se convierte en una matriz. También se establece la variable AnchorName, que desencadenará que otros dispositivos soliciten el delimitador si no lo tienen.

En algunos casos, el anclaje no se exportará o creará demasiados datos que se volverán a intentar. Aquí simplemente llamaremos a CreateAnchor de nuevo.

Una función final de la ruta de acceso de exportación es AnchorFoundRemotely. Cuando otro dispositivo encuentra el delimitador, ese dispositivo indicará al host y el host lo usará como señal de que el delimitador es un "buen anclaje" y se puede almacenar en caché.

**Importa**

Cuando una HoloLens se une a una sesión, debe importar un delimitador. En la función de actualización de UNETAnchorManager, el AnchorName se sondea. Cuando cambia el nombre del delimitador, comienza el proceso de importación. En primer lugar, se intenta cargar el delimitador con el nombre especificado desde el almacén de delimitadores local. Si ya lo tenemos, podemos usarlo sin descargar los datos de nuevo. Si no lo tenemos, llamamos a WaitForAnchor, que iniciará la descarga.

Una vez completada la descarga, se llama a NetworkTransmitter_dataReadyEvent. Esto indicará al bucle de actualización que llame a ImportAsync con los datos descargados. ImportAsync llamará a ImportComplete cuando se complete el proceso de importación. Si la importación se realiza correctamente, el delimitador se guardará en el almacén del reproductor local. PlayerController.cs realmente realiza la llamada a AnchorFoundRemotely para que el host sepa que se ha establecido un buen anclaje.

### <a name="enjoy-your-progress"></a>Disfrute de su progreso

Esta vez, un usuario con HoloLens hospedará una sesión mediante el botón **iniciar sesión** en la interfaz de usuario. Otros usuarios, tanto en HoloLens como en un casco envolvente, seleccionarán la sesión y, después, seleccionarán el botón unirse a la **sesión** en la interfaz de usuario. Si tiene varias personas con dispositivos HoloLens, tendrán nubes rojas sobre sus cabezales. También habrá una nube azul para cada casco envolvente, pero las nubes azules no estarán por encima de los auriculares, ya que los auriculares no intentan encontrar el mismo espacio de coordenadas universal que los dispositivos HoloLens.

Este punto del proyecto es una aplicación de uso compartido independiente; no hace mucho y podría actuar como línea base. En los capítulos siguientes comenzaremos a crear una experiencia para que los usuarios disfruten. Para obtener más información sobre el diseño de la experiencia compartida, vaya aquí.

## <a name="chapter-4---immersion-and-teleporting"></a>Capítulo 4: inmersión y teletraslado

>[!VIDEO https://www.youtube.com/embed/kUHZ5tCOfvY]

### <a name="objectives"></a>Objetivos

Disfrute de la experiencia en cada tipo de dispositivo de realidad mixta.

### <a name="what-we-will-build"></a>Lo que se va a crear

Actualizaremos la aplicación para poner a los usuarios con auriculares envolvente en la isla con una vista envolvente. Los usuarios de HoloLens seguirán teniendo la vista de pájaro de la isla. Los usuarios de cada tipo de dispositivo pueden ver a otros usuarios a medida que aparecen en el mundo. Por ejemplo, los auriculares envolventes pueden ver los demás avatares en otras rutas de acceso de la isla y ven a los usuarios de HoloLens como nubes gigantes por encima de la isla. Los auriculares envolventes también verán el cursor del rayo fijamente del usuario de HoloLens si el usuario de HoloLens mira la isla. Los usuarios de HoloLens verán un avatar en la isla para representar cada usuario de auriculares envolvente.

**Entrada actualizada para el dispositivo envolvente:**

* Los botones del parachoques izquierdo y derecho del controlador Xbox giran el reproductor
* Si mantiene presionado el botón Y en el controlador de Xbox, se habilitará un cursor [teletranspórtate](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) . Si el cursor tiene un indicador de flecha giratoria al soltar el botón Y, se teletransporta a la ubicación del cursor.

### <a name="steps"></a>Pasos

* Agregar MixedRealityTeleport a MixedRealityCameraParent
    * En **jerarquía**, seleccione **Usland**.
    * En **Inspector**, habilite el **control de nivel**.
    * En **jerarquía**, seleccione **MixedRealityCameraParent**.
    * En **Inspector**, haga clic en **Agregar componente**.
    * Escriba la **realidad mixta teletranspórtate** y selecciónela.

### <a name="digging-into-the-code"></a>Profundizar en el código

Los auriculares envolventes se anclarán a sus equipos con cable, pero nuestra isla es mayor que el cable es largo. Para compensar, necesitamos la capacidad de trasladar la cámara independientemente del movimiento del usuario. Vea la [Página de confort](comfort.md) para obtener más información sobre el diseño de la aplicación de realidad mixta (en particular, Automotion y Locomotion).

Para describir este proceso, será útil definir dos términos. En primer lugar, **Dolly** será el objeto que mueve la cámara independientemente del usuario. Un objeto de juego secundario de **Dolly** será la **cámara principal**. La cámara principal se adjunta al encabezado del usuario.

En el panel Proyecto, desplácese a **Assets\AppPrefabs\Support\Scripts\GameLogic** y haga doble clic en **MixedRealityTeleport.CS**.

MixedRealityTeleport tiene dos trabajos. En primer lugar, controla la rotación mediante los reboteadores. En la función de actualización, se sondea "ButtonUp" en LeftBumper y RightBumper. GetButtonUp solo devuelve true en el primer fotograma en el que se encuentra un botón después de haber estado inactivo. Si se ha producido algún botón, sabemos que el usuario necesita girar.

Cuando giramos, hacemos un fundido y atenúan el uso de un script simple denominado ' Desvanecer control '. Hacemos esto para evitar que el usuario vea un movimiento no natural que podría dar lugar a molestias. Los efectos de fundido y salida son bastante sencillos. Tenemos un fondo negro en la parte delantera de la **cámara principal**. Cuando se atenúa, se pasa el valor alfa de 0 a 1. Esto hace que los píxeles negros de la cuádruple se representen y oculten todo lo que quede detrás. Al retroceder en, la transición del valor alfa vuelve a ser cero.

Al calcular la rotación, tenga en cuenta que estamos rotando nuestro **Dolly** pero calculando el giro alrededor de la **cámara principal**. Esto es importante, ya que el más alejado de la **cámara principal** está fuera de 0, 0, 0, con menos precisión un giro alrededor de la Dolly se pasaría del punto de vista del usuario. De hecho, si no gira alrededor de la posición de la cámara, el usuario se desplazará por el **Dolly** en lugar de girar.

El segundo trabajo para MixedRealityTeleport es controlar el movimiento de **Dolly**. Esto se hace en SetWorldPosition. SetWorldPosition toma la posición mundial deseada, la posición en la que el usuario desea percieve que inhabit. Necesitamos colocar el **Dolly** en esa posición menos la posición local de la **cámara principal**, ya que ese desplazamiento se agregará a cada fotograma.

Un segundo script llama a SetWorldPosition. Echemos un vistazo a ese script. En el panel Proyecto, desplácese a **Assets\AppPrefabs\Support\Scripts\GameLogic** y haga doble clic en **TeleportScript.CS**.

Este script es un poco más complicado que MixedRealityTeleport. El script está comprobando si el botón Y del controlador Xbox debe mantenerse inactivo. Mientras se mantiene presionado el botón, se representa un cursor teletranspórtate y el script convierte un rayo de la posición de AvPág del usuario. Si ese rayo entra en conflicto con una superficie que señala más o menos, se considerará que la superficie es una buena superficie para teletranspórtate y se habilitará la animación en el cursor teletranspórtate. Si el rayo no entra en conflicto con una superficie más o menos apuntando, se deshabilitará la animación del cursor. Cuando se suelta el botón y y el punto calculado del rayo es una posición válida, el script llama a SetWorldPosition con la posición en la que se intersecó el rayo.

### <a name="enjoy-your-progress"></a>Disfrute de su progreso

Esta vez necesitará encontrar un amigo.

Una vez más, un usuario con HoloLens hospedará una sesión. Otros usuarios se unirán a la sesión. La aplicación colocará los tres primeros usuarios para unirse desde un casco inmersivo en una de las tres rutas de acceso de la isla. No dude en explorar la isla en esta sección.

Detalles que se deben tener en cuenta:

1. Puede ver caras en las nubes, lo que ayuda a un usuario sumergido a ver la dirección que está buscando un usuario de HoloLens.
2. Los avatares de la isla tienen cuellos que giran. No se van a seguir lo que el usuario está haciendo es realidad real (no tenemos esa información), pero es una buena experiencia.
3. Si el usuario de HoloLens mira la isla, los usuarios sumergidos pueden ver su cursor.
4. Las nubes que representan a los usuarios de HoloLens proyectan sombras.

## <a name="chapter-5---finale"></a>Capítulo 5: finalización

>[!VIDEO https://www.youtube.com/embed/n_HDWJbfpNg]

### <a name="objectives"></a>Objetivos

Cree una experiencia interactiva colaborativa entre los dos tipos de dispositivos.

### <a name="what-we-will-build"></a>Lo que se va a crear

Basándose en el capítulo 4, cuando un usuario con un casco envolvente se acerque a un rompecabezas de la isla, los usuarios de HoloLens obtendrán una información sobre herramientas con una pista sobre el rompecabezas. Una vez que todos los auriculares envolventes se colocan por encima de sus rompecabezas y en el "panel listo" del salón, se lanzará el cohete.

### <a name="steps"></a>Pasos

* En **jerarquía**, seleccione **Usland**.
* En **Inspector**, en **control de nivel**, Active **Habilitar colaboración**.

### <a name="digging-into-the-code"></a>Profundizar en el código

Ahora, echemos un vistazo a LevelControl.cs. Este script es el núcleo de la lógica del juego y mantiene el estado del juego. Dado que se trata de un juego multijugador que usa UNET, necesitamos comprender cómo fluyen los datos, al menos lo suficientemente bien como para modificar este tutorial. Para obtener una introducción más completa de UNET, consulte la documentación de Unity.

En el panel Proyecto, desplácese a **Assets\AppPrefabs\Support\Scripts\GameLogic** y haga doble clic en **LevelControl.CS**.

Vamos a entender cómo un casco inmersivo indica que están preparados para el lanzamiento de Rocket. Rocket Launch Readiness se comunica mediante la configuración de uno de los tres booleanos de una lista de bool que corresponden a las tres rutas de acceso de la isla. El valor booleano de una ruta de acceso se establecerá cuando el usuario asignado a la ruta de acceso se encuentre en la parte superior del panel marrón dentro de la habitación. Bien, ahora a los detalles.

Comenzaremos en la función Update (). Observará que hay una función de "trampa". Lo usamos en desarrollo para probar la secuencia de inicio y restablecimiento de Rocket. No funcionará en la experiencia de varios usuarios. Afortunadamente, en el momento en que internalizar la siguiente desactivación, puede hacer que funcione. Después de comprobar si debemos hacernos trampas, comprobamos si el reproductor local está sumergido. Queremos centrarnos en cómo encontramos que estamos en el objetivo. Dentro de la comprobación if (sumergida), hay una llamada a CheckGoal que oculta detrás de **EnableCollaboration** bool. Esto corresponde a la casilla que activó al completar los pasos de este capítulo. Dentro de EnableCollaboration, vemos una llamada a CheckGoal ().

CheckGoal realiza algunas operaciones matemáticas para ver si estamos más o menos en el panel. Cuando somos, depure. log "llegó en el objetivo" y, a continuación, llamamos a "SendAtGoalMessage ()". En SendAtGoalMessage se llama a playerController. SendAtGoal. Para ahorrar tiempo, este es el código:

```cs
private void CmdSendAtGoal(int GoalIndex)
{
    levelState.SetGoalIndex(GoalIndex);
}
```

```cs
public void SendAtGoal(int GoalIndex)
{
    if (isLocalPlayer)
    {
        Debug.Log("sending at goal " + GoalIndex);
        CmdSendAtGoal(GoalIndex);
    }
}
```

Tenga en cuenta que SendAtGoalMessage llama a CmdSendAtGoal, que llama a levelState. SetGoalIndex, que vuelve a LevelControl.cs. A primera vista, parece extraño. ¿Por qué no simplemente llamar a SetGoalIndex en lugar de a este enrutamiento extraño a través del controlador del reproductor? La razón es que estamos conformes al modelo de datos que UNET usa para mantener los datos sincronizados. Para evitar la mejora y la paginación, UNET requiere que cada objeto tenga un usuario que tenga autoridad para cambiar las variables sincronizadas. Además, solo el host (el usuario que inició la sesión) puede cambiar los datos directamente. Los usuarios que no son el host, pero que tienen autoridad, deben enviar un comando al host que cambiará la variable. De forma predeterminada, el host tiene autoridad sobre todos los objetos, salvo el objeto generado para representar al usuario. En nuestro caso, este objeto tiene el script playercontroller. Hay una manera de solicitar la autoridad para un objeto y, a continuación, realizar cambios, pero optamos por aprovechar el hecho de que el controlador del reproductor tiene autoautoridad y enrutar los comandos a través del controlador del reproductor.

Dicho de otro modo, cuando nos encontramos en nuestro objetivo, el jugador debe indicar al host y el host indicará a todos los demás usuarios.

De nuevo en LevelControl.cs, consulte SetGoalIndex. Aquí se establece el valor de un valor en synclist (AtGoal). Recuerde que estamos en el contexto del host mientras hacemos esto. De forma similar a un comando, una RPC es algo que el host puede emitir y que hará que todos los clientes ejecuten código. Aquí llamamos a ' RpcCheckAllGoals '. Cada cliente comprobará individualmente si se han establecido los tres AtGoals y, si es así, iniciará el Rocket.

### <a name="enjoy-your-progress"></a>Disfrute de su progreso

En el capítulo anterior, se iniciará la sesión como antes. Esta vez, a medida que los usuarios del casco envolvente lleguen a la "puerta" en su ruta de acceso, aparecerá una información sobre herramientas que solo pueden ver los usuarios de HoloLens. Los usuarios de HoloLens son responsables de comunicar esta pista a los usuarios en el casco envolvente. El cohete se iniciará en el espacio una vez que cada Avatar esté escalonado en su correspondiente controlador marrón dentro de la Volcano. La escena se restablecerá después de 60 segundos para que pueda volver a hacerlo.

## <a name="see-also"></a>Consulta también

* [Entrada MR 213: Controladores de movimiento](mixed-reality-213.md)
