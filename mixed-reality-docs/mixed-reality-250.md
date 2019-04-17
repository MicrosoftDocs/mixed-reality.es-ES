---
title: MR 250 - HoloLens e inmersivos de uso compartido
description: Siga este tutorial con auriculares de Unity, Visual Studio, HoloLens y Windows Mixed Reality para conocer los detalles de uso compartido hologramas entre dispositivos de realidad mixta de codificación.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, controlador, uso compartido, el mando de xbox, redes, entre dispositivos de unity mixedrealitytoolkit, envolvente, movimiento
ms.openlocfilehash: 9e1cb0d168b8bf830b4477190516cd19caef7972
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598047"
---
>[!NOTE]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.  Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.  Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.

<br>

# <a name="mr-sharing-250-hololens-and-immersive-headsets"></a>MR 250 de uso compartido: HoloLens e inmersivos

Con la flexibilidad de plataforma Universal de Windows (UWP), es fácil crear una aplicación que abarca varios dispositivos. Con esta flexibilidad, podemos crear experiencias que aprovechan los puntos fuertes de cada dispositivo. Este tutorial tratará de una experiencia básica compartida que se ejecuta en HoloLens y Windows Mixed Reality inmersivos. Este contenido se entregó originalmente en la conferencia Microsoft Build 2017 en Seattle, WA.

**En este tutorial, se hará lo siguiente:**

* Configurar una red mediante UNET.
* Comparta hologramas entre dispositivos de realidad mixta.
* Establecer una vista diferente de la aplicación dependiendo de qué se usa el dispositivo de realidad mixta.
* Crear una experiencia compartida donde los usuarios de HoloLens guiar a los usuarios de inmersivos a través de algunos rompecabezas simple.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td>MR 250 de uso compartido: HoloLens e inmersivos</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de empezar

### <a name="prerequisites"></a>Requisitos previos

* Un equipo con Windows 10 con el [herramientas de desarrollo necesario](install-the-tools.md) y [configurado para admitir un auricular envolvente de Windows Mixed Reality](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines).
* Un controlador de Xbox que funciona con su PC.
* Al menos un dispositivo HoloLens y un auricular envolvente.
* Una red que permite la difusión de UDP para la detección.

### <a name="project-files"></a>Archivos de proyecto

* Descargue el [archivos](https://github.com/Microsoft/MixedReality250/archive/master.zip) requerida por el proyecto. Extraiga los archivos en una forma sencilla de recordar la ubicación.
* Este proyecto requiere el [una versión recomendada de Unity con el soporte técnico de Windows Mixed Reality](install-the-tools.md).

>[!NOTE]
>Si desea buscar en el código de origen antes de descargar, tiene [disponible en GitHub](https://github.com/Microsoft/MixedReality250).

## <a name="chapter-1---holo-world"></a>Capítulo 1: Holo World

>[!VIDEO https://www.youtube.com/embed/IC0rp6rLiEc]

### <a name="objectives"></a>Objetivos

Asegúrese de que el entorno de desarrollo está listo para funcionar con un proyecto simple.

### <a name="what-we-will-build"></a>Vamos a crear

Una aplicación que se muestra un holograma en HoloLens o auriculares Windows Mixed Reality envolventes.

### <a name="steps"></a>Pasos
* Abra Unity.
    * Seleccione **abierto**.
    * Vaya a la que extrajo los archivos del proyecto.
    * Haga clic en **Seleccionar carpeta**.
    * *Se tardará un poco mientras que para que Unity procesar el proyecto por primera vez.*
* Compruebe que está habilitada la realidad mixta en Unity.
    * Abra el cuadro de diálogo de configuración de compilación (**Control + Mayús + B** o **archivo > configuración de compilación...** ).
    * Seleccione **Universal Windows Platform** , a continuación, haga clic en **Cambiar plataforma**.
    * Seleccione **Editar > configuración del Reproductor**.
    * En el **Inspector** en el lado derecho del panel, expanda **XR configuración**.
    * Compruebe el **admite la realidad Virtual** cuadro.
    * *Windows Mixed Reality debe ser el SDK de realidad Virtual.*
* Crear una escena.
    * En el **jerarquía** haga **cámara principal** seleccione **eliminar**.
    * Desde **HoloToolkit > entrada > prefabricados** arrastre **MixedRealityCameraParent** a la **jerarquía**.
* Agregar hologramas a la escena
    * Desde **AppPrefabs** arrastre **Skybox** a la **vista de escena**.
    * Desde **AppPrefabs** arrastre **administradores** a la **jerarquía**.
    * Desde **AppPrefabs** arrastre **isla** a la **jerarquía**.
* Guarde y compile
    * Guardar (ya sea **Control + S** o **archivo > Guardar escena**)
    * Puesto que se trata de una nueva escena, deberá asígnele el nombre. Nombre no importa, pero utilizamos SharedMixedReality.
* Exportar a Visual Studio
    * Abra el menú de la compilación (**Control + Mayús + B** o **archivo > configuración de compilación**)
    * Haga clic en **agregar escenas abiertos.**
    * Comprobar **Unity C# proyectos**
    * Haz clic en **Compilación**.
    * En la ventana del explorador de archivos que aparece, cree una carpeta nueva denominada **aplicación**.
    * Solo haga clic en el **aplicación** carpeta.
    * Presione **Seleccionar carpeta.**
    * **Espere a que finalice la compilación**
    * En la ventana del explorador de archivos que aparece, vaya a la **aplicación** carpeta.
    * Haga doble clic en **SharedMixedReality.sln** para iniciar Visual Studio
* Construido a partir de Visual Studio
    * Mediante la barra de herramientas superior cambie destino a **versión** y **x86**.
    * Haga clic en la flecha situada junto a **máquina Local** y seleccione **dispositivo** para implementar en HoloLens
    * Haga clic en la flecha situada junto a **dispositivo** y seleccione **máquina Local** implementar para los auriculares de realidad mixta.
    * Haga clic en **Depurar -> Iniciar sin depurar** o **Control + F5** para iniciar la aplicación.

### <a name="digging-into-the-code"></a>Descripción detallada del código

En el panel proyecto, vaya a **Assets\HoloToolkit\Input\Scripts\Utilities** y haga doble clic en **MixedRealityCameraManager.cs** para abrirlo.

**Información general:** MixedRealityCameraManager.cs es un sencillo script que ajusta la configuración en segundo plano y de nivel de calidad basándose en el dispositivo. Clave aquí es HolographicSettings.IsDisplayOpaque, que permite que un script detectar si el dispositivo es un HoloLens (IsDisplayOpaque devuelve false) o un auricular envolvente (IsDisplayOpaque devuelve true).

### <a name="enjoy-your-progress"></a>Disfrute de su progreso

En este momento la aplicación solo representará un holograma. Se agregará interacción para el holograma más adelante. Ambos dispositivos representarán el holograma el mismo. Los auriculares envolventes también representarán un fondo azul cielo y nubes.

## <a name="chapter-2---interaction"></a>Capítulo 2: interacción

>[!VIDEO https://www.youtube.com/embed/Lrb1y4sQRvI]

### <a name="objectives"></a>Objetivos

Muestra cómo controlar la entrada para una aplicación de Windows Mixed Reality.

### <a name="what-we-will-build"></a>Vamos a crear

A partir de la aplicación desde el capítulo 1, se agregará funcionalidad para permitir al usuario recoger el holograma y colóquelo en una superficie del mundo real en HoloLens o en una tabla virtual de un auricular envolvente.

**Actualizador de entrada:** En HoloLens el gesto de select es el **en el aire**. En inmersivos, usaremos el **A** botón en el controlador de Xbox. Para obtener más información en la entrada [comience aquí](gestures.md).

### <a name="steps"></a>Pasos
* Agregar administrador de entrada
    * Desde **HoloToolkit > entrada > prefabricados** arrastre **InputManager** a **jerarquía** como elemento secundario de **administradores**.
    * Desde **HoloToolkit > entrada > prefabricados > Cursor** arrastre **Cursor** a **jerarquía**.
* Agregar asignación espacial
    * Desde **HoloToolkit > SpatialMapping > prefabricados** arrastre **SpatialMapping** a **jerarquía**.
* Agregar Playspace Virtual
    * En **jerarquía** expanda **MixedRealityCameraParent** seleccione **límite**
    * En **Inspector** panel Active la casilla para habilitar **límite**
    * Desde **AppPrefabs** arrastre **VRRoom** a **jerarquía**.
* Agregar WorldAnchorManager
    * En **jerarquía**, seleccione **administradores**.
    * En **Inspector**, haga clic en **Agregar componente**.
    * Tipo **World delimitador Manager**.
    * Seleccione **World delimitador Manager** para agregarlo.
* Agregar TapToPlace a la isla
    * En **jerarquía**, expanda **isla**.
    * Seleccione **MixedRealityLand**.
    * En **Inspector**, haga clic en **Agregar componente**.
    * Tipo **pulse a otro** y selecciónelo.
    * Comprobar **colocar primario al pulsar**.
    * Establecer **colocación desplazamiento** a **(0, 0.1, 0)**.
* Guarde y compile como antes

### <a name="digging-into-the-code"></a>Descripción detallada del código

**Script 1 - GamepadInput.cs**

En el panel proyecto, vaya a **Assets\HoloToolkit\Input\Scripts\InputSources** y haga doble clic en **GamepadInput.cs** para abrirlo. Desde la misma ruta de acceso en el panel proyecto, hacer doble clic en **InteractionSourceInputSource.cs**.

Tenga en cuenta que ambos scripts tienen una clase base común, BaseInputSource.

BaseInputSource mantiene una referencia a un InputManager, que permite que un script para desencadenar eventos. En este caso, el evento InputClicked es relevante. Esto será importante recordar cuando llegamos a la secuencia de comandos 2, TapToPlace. En el caso de GamePadInput, nos sondear en busca de en el controlador de presionar el botón, a continuación, se genera el evento InputClicked. En el caso de InteractionSourceInputSource, se genera el evento de InputClicked en respuesta a la TappedEvent.

**Secuencia de comandos 2 - TapToPlace.cs**

En el panel proyecto, vaya a **Assets\HoloToolkit\SpatialMapping\Scripts** y haga doble clic en **TapToPlace.cs** para abrirlo.

Lo primero que muchos programadores desean implementar al crear una aplicación holográfica refiere a hologramas con la entrada del gesto. Por lo tanto, nos hemos esforzado por exhaustivamente comentar esta secuencia de comandos. Algunas cosas merecen la pena destacar en este tutorial.

En primer lugar, tenga en cuenta que TapToPlace implementa IInputClickHandler. IInputClickHandler expone las funciones que controlan el evento InputClicked por GamePadInput.cs o InteractionSourceInputSource.cs. OnInputClicked se llama cuando un BaseInputSource detecta un clic, mientras que el objeto con TapToPlace tiene el foco. Ser airtapping en HoloLens o al presionar el botón en el controlador de Xbox desencadenará el evento.

En segundo lugar está el código se ejecuta en update para comprobar si una superficie se está examinando por lo que podemos aplicar el objeto de juego en una superficie, como una tabla. Los auriculares envolvente no tienen un concepto de superficies real, por lo que el objeto que representa la parte superior de la tabla (Vroom > TableThingy > cubo) se ha marcado con la capa física SpatialMapping, por lo que el rayo tinte Update entran en conflicto con la parte superior de la tabla virtual.

### <a name="enjoy-your-progress"></a>Disfrute de su progreso

Esta vez puede seleccionar la isla de moverla. Puede mover la isla a una superficie real en HoloLens. En los auriculares envolventes puede mover la isla a la tabla virtual que se ha agregado.

## <a name="chapter-3---sharing"></a>Capítulo 3: uso compartido

>[!VIDEO https://www.youtube.com/embed/1diycJvxfDc]

### <a name="objectives"></a>Objetivos

Asegúrese de que la red está configurada correctamente y de detalle cómo delimitadores espaciales se comparten entre dispositivos.

### <a name="what-we-will-build"></a>Vamos a crear

Nuestro proyecto se convertirá a un proyecto de varios jugadores. Se agregará la interfaz de usuario y la lógica para sesiones de host o combinación. HoloLens verán los usuarios entre sí en la sesión con nubes abrumados y los usuarios de auriculares envolventes tienen nubes cerca de donde es el delimitador. Los usuarios en el inmersivos verán los usuarios de HoloLens en relación con el origen de la escena. Todos los usuarios de HoloLens verán el holograma de la isla en el mismo lugar. Es la clave a tener en cuenta que los usuarios de la inmersivos no estará en la isla durante este capítulo, pero se comportarán de forma muy similar a HoloLens, con una vista de la isla de pájaros.

### <a name="steps"></a>Pasos
* Isla de quitar y VRRoom
    * En **jerarquía** haga **isla** seleccione **eliminar**
    * En **jerarquía** haga **VRRoom** seleccione **eliminar**
* Agregar Usland
    * Desde **AppPrefabs** arrastre **Usland** a **jerarquía**.
* Desde **AppPrefabs** arrastre cada uno de los procedimientos siguientes para **jerarquía**:
    * **UNETSharingStage**
    * **UNetAnchorRoot**
    * **UIContainer**
    * **DebugPanelButton**
* Guarde y compile como antes

### <a name="digging-into-the-code"></a>Descripción detallada del código

En el panel proyecto, vaya a **Assets\AppPrefabs\Support\SharingWithUnet\Scripts** y haga doble clic en **UnetAnchorManager.cs**. La capacidad de uno HoloLens compartir información de seguimiento con otro HoloLens tal que los dispositivos pueden compartir el mismo espacio es casi mágica. La eficacia de la realidad mixta cobra vida cuando dos o más personas pueden colaborar mediante los mismos datos digitales.

Algunos aspectos que debe señalar en esta secuencia de comandos:

En la función de inicio, tenga en cuenta la comprobación de **IsDisplayOpaque**. En este caso, hemos fingir que se ha establecido el delimitador. Esto es porque el inmersivos no exponen una manera de importar o exportar los delimitadores. Sin embargo, si se está ejecutando en un HoloLens, este script implementa los anclajes de uso compartidos entre los dispositivos. El dispositivo que se inicia la sesión, creará un delimitador para la exportación. El dispositivo que se une a una sesión solicitará el delimitador del dispositivo que se inició la sesión.

**Exportar:**

Cuando un usuario crea una sesión, NetworkDiscoveryWithAnchors llamará a la función UNETAnchorManagers CreateAnchor. Vamos a seguir CreateAnchor flujo.

Empezaremos por realizar algunas tareas de mantenimiento, borrarlos de todos los datos que se han podemos recopilados para delimitadores anteriores. A continuación, comprobamos si hay un anclaje en caché para cargar. Los datos de anclaje tienden a ser entre 5 y 20 MB, por lo que puede guardar la reutilización de los anclajes en caché en la cantidad de datos que se necesitan para transferir a través de la red. Veremos cómo funciona un poco más adelante. Aunque estamos usando nuevamente el delimitador, debemos obtener el delimitador de datos listos en caso de que une a un nuevo cliente que no tienen el delimitador.

Hablando de preparar los datos de anclaje, la clase WorldAnchorTransferBatch expone la funcionalidad para preparar los datos de anclaje para enviar a otro dispositivo o aplicación y la funcionalidad para importar los datos de anclaje. Puesto que estamos en la ruta de acceso de exportación, agregaremos nuestro delimitador para el WorldAnchorTransferBatch y llamar a la función ExportAsync. ExportAsync, a continuación, llamará a la devolución de llamada WriteBuffer cuando genera datos para la exportación. Cuando todos los datos se ha exportado se llamará ExportComplete. En WriteBuffer se agrega el fragmento de datos a una lista que se mantenga para la exportación. En ExportComplete se convierta la lista en una matriz. La variable AnchorName también se establece, lo que activará otros dispositivos para solicitar el anclaje si no lo tienen.

En algunos casos, el delimitador no exportar o creará tan pocos datos que se volverá a intentarlo. Aquí simplemente llamamos CreateAnchor nuevo.

Una función final en la ruta de acceso de exportación es AnchorFoundRemotely. Cuando otro dispositivo encuentra el delimitador, ese dispositivo le indicará que el host y el host usará como una señal de que el delimitador es un "buena delimitador" y puede almacenarse en caché.

**Importar:**

Cuando un HoloLens une a una sesión, debe importar un delimitador. En función de actualización del UNETAnchorManager, se sondea el AnchorName. Cuando se cambia el nombre del delimitador, comienza el proceso de importación. En primer lugar, se intenta cargar el delimitador con el nombre especificado del almacén local del delimitador. Si se dispone de él, se puede usar sin volver a descargar los datos. Si no lo tenemos, a continuación, llamamos al WaitForAnchor que iniciará la descarga.

Cuando se completa la descarga, se denomina NetworkTransmitter_dataReadyEvent. Esto señalará el bucle de actualización para llamar a ImportAsync con los datos descargados. ImportAsync llamará a ImportComplete cuando se completa el proceso de importación. Si la importación se realiza correctamente, el delimitador se guardarán en el almacén local del Reproductor. PlayerController.cs realmente realiza la llamada a AnchorFoundRemotely para que el host sepa que se ha establecido un anclaje de buena.

### <a name="enjoy-your-progress"></a>Disfrute de su progreso

Esta vez un usuario con un HoloLens va a hospedar una sesión mediante el **iniciar sesión** botón en la interfaz de usuario. Otros usuarios, tanto en HoloLens o un auricular envolvente, se selecciona la sesión y, a continuación, seleccione el **unirse a sesión** botón en la interfaz de usuario. Si tiene varias personas con dispositivos HoloLens, tendrán nubes rojo abrumados. También habrá una nube azul para cada auriculares envolventes, pero las nubes azules no estará por encima de los auriculares, los auriculares no intenta buscar el mismo espacio de coordenadas universales como los dispositivos HoloLens.

En este punto en el proyecto es una aplicación de uso compartida independiente; no hace mucho y puede servir como base. En los capítulos siguientes, comenzaremos a crear una experiencia de las personas a disfrutar. Para obtener más instrucciones sobre diseño de la experiencia compartido, vaya aquí.

## <a name="chapter-4---immersion-and-teleporting"></a>Capítulo 4: inmersión y teleporting

>[!VIDEO https://www.youtube.com/embed/kUHZ5tCOfvY]

### <a name="objectives"></a>Objetivos

Satisfaga las necesidades de la experiencia de cada tipo de dispositivo de realidad mixta.

### <a name="what-we-will-build"></a>Vamos a crear

Actualizaremos la aplicación para poner los auriculares envolventes de usuarios en la isla de una vista envolventes. HoloLens a los usuarios seguirán teniendo la visión general de la isla. Pueden ver a otros usuarios a los usuarios de cada tipo de dispositivo tal y como aparecen en el mundo. Por ejemplo, los usuarios de auriculares envolventes pueden ver los demás avatares en otras rutas de acceso de la isla y verán los usuarios de HoloLens como enorme nubes por encima de la isla. Los usuarios de auriculares envolventes también verán el cursor de ray mirada de HoloLens del usuario si el usuario HoloLens está mirando la isla. Los usuarios de HoloLens verán un avatar en la isla para representar a cada usuario auriculares envolventes.

**Entrada actualizada para el dispositivo envolvente:**
* Los botones izquierdos paragolpes y paragolpes directamente en el controlador de Xbox girar el Reproductor
* Que contiene el botón Y en el controlador de Xbox permitirá un [teleport](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) cursor. Si el cursor tiene un indicador de flecha de giro al soltar el botón Y, será teleported a la posición del cursor.

### <a name="steps"></a>Pasos
* Agregar MixedRealityTeleport a MixedRealityCameraParent
    * En **jerarquía**, seleccione **Usland**.
    * En **Inspector**, habilitar **Control de nivel de**.
    * En **jerarquía**, seleccione **MixedRealityCameraParent**.
    * En **Inspector**, haga clic en **Agregar componente**.
    * Tipo **Teleport de realidad mixta** y selecciónelo.

### <a name="digging-into-the-code"></a>Descripción detallada del código

Los usuarios de auriculares envolventes se se bloqueado en sus equipos con un cable, pero nuestro isla es mayor que el cable es largo. Para compensar, necesitamos la capacidad para mover la cámara con independencia del movimiento del usuario. Consulte la [página de progreso](comfort.md) para obtener más información sobre el diseño de la aplicación de realidad mixta (movimiento propio en particular y desplazamiento).

Con el fin de describir este proceso será útil definir dos términos. Primero, **plataforma de mantenimiento** será el objeto que se mueve la cámara de forma independiente del usuario. Un objeto de juego secundarios de la **plataforma de mantenimiento** será el **cámara principal**. La cámara principal está conectada a la cabeza del usuario.

En el panel proyecto, vaya a **Assets\AppPrefabs\Support\Scripts\GameLogic** y haga doble clic en **MixedRealityTeleport.cs**.

MixedRealityTeleport tiene dos trabajos. En primer lugar, controla la rotación mediante la paragolpes. En la función update se sondean de 'ButtonUp' en LeftBumper y RightBumper. GetButtonUp solo devuelve true en el primer fotograma de que un botón no está presionado después de haber estado inactivo. Si se hubiese producido cualquiera de los botones, sabremos entonces que el usuario debe girar.

Cuando se gira no atenuación y se atenúan mediante un sencillo script denominado "atenuación control". Hacemos esto para evitar que el usuario vea un movimiento no natural que podría provocar malestar. El fundido de entrada y salida efecto es bastante sencillo. Tenemos un cuadrado negro francesa delante de la **cámara principal**. Cuando atenúa, podemos cambiar el valor alfa de 0 a 1. Esto hace que gradualmente los píxeles negros de lo cuatro se representará y ocultar nada detrás de ellos. Cuando difuminación en transición el valor alfa en cero.

Cuando se calcula la rotación, tenga en cuenta que nos estamos girar nuestro **plataforma de mantenimiento** pero calcular la rotación alrededor de la **cámara principal**. Esto es importante que cuanto más lejos el **cámara principal** es lejos 0,0,0, menos preciso se convertiría en un giro alrededor de la plataforma de mantenimiento desde el punto de vista del usuario. De hecho, si no gira en torno a la posición de la cámara, el usuario se moverá en un arco en torno a la **plataforma de mantenimiento** en lugar de la rotación.

El segundo trabajo de MixedRealityTeleport consiste en tratar de mover el **plataforma de mantenimiento**. Esto se hace en SetWorldPosition. SetWorldPosition toma la posición deseada del mundo, la posición donde el usuario desea percieve que ocupan. Debemos poner nuestros **plataforma de mantenimiento** en esa posición menos la posición local de la **cámara principal**, ya que el desplazamiento se agregarán cada fotograma.

Un segundo script llama a SetWorldPosition. Echemos un vistazo a ese script. En el panel proyecto, vaya a **Assets\AppPrefabs\Support\Scripts\GameLogic** y haga doble clic en **TeleportScript.cs**.

Este script es un poco más complicado que MixedRealityTeleport. Está comprobando la secuencia de comandos para que se mantiene presionado el botón Y en el controlador de Xbox. Mientras se mantiene el botón hacia abajo un teleport se representa el cursor y la secuencia de comandos convierte un rayo desde la posición del usuario mirada. Si ese ray está en conflicto con una superficie que es más o menos que apunta hacia arriba, se considera una buena superficie a teleport a la superficie de y se habilitará la animación en el cursor teleport. Si el rayo no entren en conflicto con una superficie señalador más o menos, a continuación, se deshabilitará la animación en el cursor. Cuando se suelta el botón Y y el punto del rayo calculado es una posición válida, el script llama a SetWorldPosition con la posición que se intersecan con el rayo.

### <a name="enjoy-your-progress"></a>Disfrute de su progreso

Esta vez deberá buscar a un amigo.

Una vez más, un usuario con el HoloLens va a hospedar una sesión. Otros usuarios unirán a la sesión. La aplicación colocará los tres primeros usuarios de un auricular envolvente en una de las tres rutas de acceso de la isla al que unirse. No dude en explorar la isla de esta sección.

Detalles a tener en cuenta:
1. Puede ver las caras en las nubes, lo que ayuda a un usuario sumergido ver en qué dirección mira un usuario de HoloLens.
2. Los avatares en la isla tienen que gira el cuello. No siguen lo que el usuario está haciendo es realidad real (no tenemos esa información), pero resulta una buena experiencia.
3. Si el usuario HoloLens está buscando en la isla, los usuarios sumergidos pueden ver su cursor.
4. Las nubes que representan a los usuarios de HoloLens proyectar sombras.

## <a name="chapter-5---finale"></a>Capítulo 5: filtrar

>[!VIDEO https://www.youtube.com/embed/n_HDWJbfpNg]

### <a name="objectives"></a>Objetivos

Crear una experiencia interactiva de colaboración entre los tipos de dos dispositivo.

### <a name="what-we-will-build"></a>Vamos a crear

Los usuarios de HoloLens compilando en el capítulo 4, cuando un usuario con un auricular envolvente obtiene cerca de un rompecabezas de la isla, obtendrá una información sobre herramientas con una pista para el rompecabezas. Una vez más allá de sus rompecabezas y en el "panel de listo" todos los usuarios de auriculares envolventes obtención en la sala de rocket, se iniciará el cohete.

### <a name="steps"></a>Pasos
* En **jerarquía**, seleccione **Usland**.
* En **Inspector**, en **Control nivel**, comprobar **habilitar colaboración**.

### <a name="digging-into-the-code"></a>Descripción detallada del código

Ahora examinemos LevelControl.cs. Este script es el núcleo de la lógica del juego y mantiene el estado del juego. Puesto que se trata de un juego multijugador con UNET es necesario comprender cómo fluyen los datos, por lo menos tan bien para modificar este tutorial. Para obtener una introducción más completa de UNET, consulte la documentación de Unity.

En el panel proyecto, vaya a **Assets\AppPrefabs\Support\Scripts\GameLogic** y haga doble clic en **LevelControl.cs**.

Vamos a explicar cómo un auricular envolvente indica que están listos para el lanzamiento de cohete. Preparación de lanzamiento de cohete se comunica estableciendo uno de tres bools en una lista de bools que corresponden a las tres rutas de acceso de la isla. Bool de una ruta de acceso se establecerá cuando el usuario asignado a la ruta de acceso está en la parte superior del panel marrón dentro de la sala de rocket. Bien, ahora los detalles.

Comenzamos en la función Update(). Puede observar que hay una función 'de referencia rápida'. Se usa en el desarrollo para probar el inicio de cohete y restablecer la secuencia. Esto no funcionará en la experiencia de usuario múltiple. Espero que en el momento que internalizar la siguiente información puede hacerlo funcionar. Después, comprobamos si hacemos deberíamos trampa, comprobamos si el Reproductor local se sumerja. Queremos centrarse en cómo encontramos que estamos en el objetivo. Dentro de if (sumerja) Compruebe que hay una llamada a CheckGoal oculta detrás de la **EnableCollaboration** bool. Esto corresponde a la casilla de verificación que se ha activado al completar los pasos de este capítulo. Dentro de EnableCollaboration vemos una llamada a CheckGoal().

CheckGoal realiza un cálculo matemático para ver si se están más o menos permanente en el panel. Cuando estamos, nos Debug.Log "Entregada en objetivo" y, a continuación, llamar a 'SendAtGoalMessage()'. En SendAtGoalMessage llamamos playerController.SendAtGoal. Para ahorrar tiempo, este es el código:

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

Tenga en cuenta que SendAtGoalMessage llama CmdSendAtGoal, qué levelState.SetGoalIndex llamadas, que es nuevo en LevelControl.cs. A primera vista parece extraño. ¿Por qué no simplemente llamar SetGoalIndex en lugar de esto extraño de enrutamiento mediante el controlador player? El motivo es que nos estamos conforme al modelo de datos que UNET se usa para mantener sincronizados los datos. Para evitar la trampa y paginación excesiva, UNET requiere que cada objeto tiene un usuario que tenga autoridad para cambiar las variables sincronizadas. Además, el host (es decir, el usuario que inició la sesión) puede cambiar los datos directamente. Los usuarios que no son el host, pero tienen autoridad, necesitan enviar 'command' en el host que cambiará la variable. De forma predeterminada el host tiene autoridad sobre todos los objetos, excepto para el objeto generado para representar al usuario. En nuestro caso, este objeto tiene el script playercontroller. Hay una manera de solicitar la autoridad de un objeto y, a continuación, realizar cambios, pero se decide aprovechar el hecho de que el controlador player tiene comandos propios de autoridad y ruta mediante el controlador player.

Dicho de otro modo, cuando nosotros mismos nos hemos encontrado en nuestro objetivo, el jugador necesita indicar al host y el host le dirá a todo el mundo.

En LevelControl.cs mirada SetGoalIndex. Aquí nos estamos establecer el valor de un valor en un synclist (AtGoal). Recuerde que estamos en el contexto del host mientras lo hacemos. Una llamada RPC es similar a un comando, es algo puede emitir el host que hará que todos los clientes ejecutar el código. Aquí utilizamos 'RpcCheckAllGoals'. Cada cliente individualmente comprobamos si se establecen todas tres AtGoals y si es así, inicie el cohete.

### <a name="enjoy-your-progress"></a>Disfrute de su progreso

Compilar en el capítulo anterior, se iniciará la sesión como antes. Esta vez que los usuarios en get auriculares envolventes a la "puerta principal" en su ruta de acceso, una información sobre herramientas aparecerá que pueden ver solo los usuarios de HoloLens. Los usuarios de HoloLens son responsables de comunicar esta pista a los usuarios en los auriculares envolventes. Una vez cada avatar ha entrado en su panel marrón correspondiente dentro de los volcanes, se iniciará el cohete al espacio. La escena se restablecerá después de 60 segundos, por lo que puede realizar de nuevo.

## <a name="see-also"></a>Vea también
* [Entrada MR 213: Controladores de movimiento](mixed-reality-213.md)
