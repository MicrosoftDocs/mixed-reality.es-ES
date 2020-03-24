---
title: 'Tutoriales de introducción: 7. Creación de una aplicación de ejemplo de módulo lunar'
description: En esta lección, agruparás varios conceptos aprendidos de lecciones anteriores para crear una experiencia de ejemplo única.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 7b432c5ba0ebee5199f5abb1c26715185fc0d70d
ms.sourcegitcommit: 5b2ba01aa2e4a80a3333bfdc850ab213a1b523b9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/10/2020
ms.locfileid: "79031563"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7. Creación de una aplicación de ejemplo de módulo lunar
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

En este tutorial, se combinan varios conceptos de lecciones anteriores para crear una experiencia de ejemplo. Aprenderás a crear una aplicación de ensamblado de piezas con la que el usuario tendrá que usar el seguimiento de manos para seleccionar las piezas e intentar ensamblar un módulo lunar. Usarás botones presionables para activar y desactivar las sugerencias de colocación, restablecer la experiencia y lanzar el módulo lunar al espacio.

En futuros tutoriales, continuarás ampliando esta experiencia, lo que incluye casos de uso multiusuario que aprovechan Azure Spatial Anchors para la alineación espacial.

## <a name="objectives"></a>Objetivos

* Agrupar varios conceptos de lecciones anteriores para crear una experiencia única
* Obtener información sobre cómo activar o desactivar los objetos
* Desencadenar eventos complejos mediante los botones presionables
* Usar la física y la fuerza de los cuerpos rígidos
* Explorar el uso de la información sobre herramientas

## <a name="lunar-module-parts-overview"></a>Introducción a las piezas del módulo lunar
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

En esta sección, crearás un desafío de ensamblado de piezas sencillo en que el objetivo del usuario será colocar cinco piezas distribuidas en la tabla en la ubicación correcta en el módulo lunar.

Los principales pasos que debes seguir para lograrlo son:

1. Agregar el objeto prefabricado del lanzacohetes a la escena
2. Habilitar la manipulación de objetos para todas las piezas
3. Agregar y configurar el componente Part Assembly Demo (Script) (Demostración de ensamblado de piezas [script])

> [!NOTE]
> El componente Part Assembly Demo (Script) (Demostración de ensamblado de piezas [script]) no forma parte de MRTK. Se proporcionó con los recursos de este tutorial.

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a>1. Agregar el objeto prefabricado del lanzacohetes a la escena

En la ventana Project (Proyecto), navega hasta la carpeta **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **RocketLauncher** (Recursos > MRTK.Tutorials.GettingStarted > carpeta Objetos prefabricados > RocketLauncher), arrastra el objeto prefabricado **RocketLauncher** a la ventana Hierarchy (Jerarquía) para agregarlo a la escena y, a continuación, colócalo en una ubicación adecuada; por ejemplo:

* Posición de transformación X = 1,5, Y = -0,4, Z = 0, a la derecha del usuario a la altura de la cintura
* Giro de transformación X = 0, Y = 180, Z = 0, para que las características principales de la experiencia estén orientadas al usuario

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a>2. Habilitar la manipulación de objetos para todas las piezas

En la ventana Hierarchy (Jerarquía), busca el objeto RocketLauncher > **LunarModuleParts** y selecciona todos los **objetos secundarios**, agrega el componente **Manipulation Handler (Script)** (Controlador de manipulación [script]) y el componente **Near Interaction Grabbable (Script)** (Interacción próxima de agarre [script]) y configura Manipulation Handler (Script) (Controlador de manipulación [script]) como se indica a continuación:

* Desactiva la casilla **Allow Far Manipulation** (Permitir la manipulación lejana) para permitir solo la interacción cercana.
* Cambia **Two Handed Manipulation Type**(Tipo de manipulación de dos manos) a **Move Rotate** (Movimiento de giro) para deshabilitar el escalado.

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> Para obtener un recordatorio con instrucciones detalladas sobre cómo implementar la manipulación de objetos, puedes consultar las instrucciones de [Manipulación de objetos 3D](mrlearning-base-ch4.md#manipulating-3d-objects).

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a>3. Agregar y configurar el componente Part Assembly Demo (Script) (Demostración de ensamblado de piezas [script])

Con todos los objetos secundarios de LunarModuleParts todavía seleccionados, agrega un componente de **Audio Source** (Origen de audio) y, a continuación, configúralo como se indica a continuación:

* Asigna un clip de audio adecuado al campo **AudioClip**; por ejemplo, MRKT_Scale_Start.
* Desactiva la casilla **Play On Awake** (Reproducir al reactivar) para que el clip de audio no se reproduzca automáticamente cuando se cargue la escena.
* Cambia la opción **Spatial Blend** (Combinación espacial) a 1 para habilitar el audio espacial.

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

Con todos los objetos secundarios de LunarModuleParts todavía seleccionados, agrega el componente **Part Assembly Demo (Script)** (Demostración de ensamblado de piezas [script]):

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

En la ventana Hierarchy (Jerarquía), selecciona el objeto **RoverEnclosure** y configura su componente **Part Assembly Demo (Script)** (Demostración de ensamblado de piezas [script]) como se indica a continuación:

* En el campo **Object To Place** (Objeto que colocar), asigna el **propio** objeto; en este caso, el objeto RoverEnclosure.
* En el campo **Location To Place** (Ubicación para colocar), asigna el objeto **PlacementHints** correspondiente; en este caso, el objeto RoverEnclosure_PlacementHint.
* En el campo **Tool Tip Object** (Objeto de información sobre herramientas), asigna el valor de **ToolTip** (Información sobre herramientas) correspondiente. En este caso, el objeto RoverEnclosure_ToolTip.
* En el campo **Audio Source** (Origen de audio), asigna el **propio** objeto; en este caso, el objeto RoverEnclosure.

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

**Repite** para cada uno de los demás objetos secundarios de LunarModuleParts; por ejemplo, FuelTank, EnergyCell, DockingPortal y ExternalSensor.

Si ahora entras en el modo de juego y mueve un objeto que colocar cerca de su ubicación para colocar correspondiente, observarás lo siguiente:

* El objeto se ajustará en su lugar y se colocará bajo el objeto principal LunarModule para que forme parte del módulo lunar.
* El origen de audio del objeto reproducirá el clip de audio asignado en la ubicación del objeto.
* Se ocultará el objeto de información sobre herramientas correspondiente.

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo usar la simulación de entrada del editor, puedes consultar la guía [Uso de la simulación de entrada de mano en el editor para probar una escena](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) del [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="configuring-the-lunar-module"></a>Configuración del módulo lunar

En esta sección, agregarás características adicionales a la aplicación del lanzacohetes para que el usuario pueda:

* Interactuar con el módulo lunar
* Lanzar el módulo lunar al espacio y reproducir un sonido al hacerlo
* Restablecer la aplicación para que el módulo lunar y todas sus partes vuelvan a su posición original
* Oculta las sugerencias de selección de ubicación para dificultar el desafío del ensamblado de piezas.

Los principales pasos que debes seguir para lograrlo son:

1. Habilitar la manipulación de objetos
2. Habilitar la física
3. Agregar un componente de origen de audio
4. Agregar y configurar el componente Launch Lunar Module (Script) (Lanzar módulo lunar [script])
5. Agregar y configurar el componente Toggle Placement Hints (Script) (Activar o desactivar sugerencias de colocación [script])

> [!NOTE]
> Los componentes Launch Lunar Module (Script) (Lanzar módulo lunar [script]) y Toggle Placement Hints (Script) (Activar o desactivar sugerencias de colocación [script]) no forman parte de MRTK. Se proporcionaron con los recursos de este tutorial.

### <a name="1-enable-object-manipulation"></a>1. Habilitar la manipulación de objetos

En la ventana Hierarchy (Jerarquía), selecciona el objeto RocketLauncher > **LunarModule**, agrega el componente **Manipulation Handler (Script)** (Controlador de manipulación [script]) y el componente **Near Interaction Grabbable (Script)** (Interacción próxima de agarre [script]) y configura Manipulation Handler (Script) (Controlador de manipulación [script]) como se indica a continuación:

* Desactiva la casilla **Allow Far Manipulation** (Permitir la manipulación lejana) para permitir solo la interacción cercana.
* Cambia **Two Handed Manipulation Type**(Tipo de manipulación de dos manos) a Move Rotate (Movimiento de giro) para deshabilitar el escalado.

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a>2. Habilitar la física

Con el objeto RocketLauncher > **LunarModule** todavía seleccionado, agrega un componente **Rigidbody** y configúralo como se indica a continuación:

* Desactiva la casilla **Use Gravity** (Usar gravedad) para que el módulo lunar no se vea afectado por la gravedad.
* Activa la casilla **Is Kinematic** (Es cinemático) para que el módulo lunar no se vea inicialmente afectado por las fuerzas físicas.

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a>3. Agregar un componente de origen de audio

Con el objeto RocketLauncher > **LunarModule** todavía seleccionado, agrega un componente de **Audio Source** (Origen de audio) y configúralo como se indica a continuación:

* Cambia la opción **Spatial Blend** (Combinación espacial) a 1 para habilitar el audio espacial.

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a>4. Agregar y configurar el componente Launch Lunar Module (Script) (Lanzar módulo lunar [script])

Con el objeto RocketLauncher > **LunarModule** todavía seleccionado, agrega el componente **Launch Lunar Module (Script)** (Lanzar módulo lunar [script]) y configúralo como se indica a continuación:

* Cambia el valor de **Thrust** (Impulso) para que el módulo lunar vuele correctamente cuando se lance; por ejemplo, a 0,01.

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a>5. Agregar y configurar el componente Toggle Placement Hints (Script) (Activar o desactivar sugerencias de colocación [script])

Con el objeto RocketLauncher > **LunarModule** todavía seleccionado, agrega el componente **Toggle Placement Hints (Script)** (Activar o desactivar sugerencias de colocación [script]) y configúralo como se indica a continuación:

* Establece la propiedad **Size** (Tamaño) de la matriz de objetos de juego en 5.
* Asigna cada uno de los **objetos secundarios** del objeto **PlacementHints** a un campo **Element** (Elemento) de la matriz de objetos de juego:

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a>Configuración del botón Launch (Lanzar)

En la ventana Hierarchy (Jerarquía), selecciona RocketLauncher > Buttons (Botones) > objeto **LaunchButton**. A continuación, en el componente **Pressable Button (Script)** (Botón presionable [script]), crea un nuevo evento **Button Pressed ()** (Botón presionado []), configura el objeto **LunarModule** para recibir el evento y define **LaunchLunarModule.StartThruster** como la acción que se desencadenará:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo implementar eventos, puedes hacer referencia a las instrucciones sobre [gestos de seguimiento de manos y botones interactuables](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons).

Con el objeto RocketLauncher > Buttons (Botones) > **LaunchButton** aún seleccionado, en el componente **Pressable Button (Script)** (Botón presionable [script]), crea un nuevo evento **Button Pressed ()** (Botón presionado []), configura el objeto **LunarModule** para recibir el evento, define **AudioSource.PlayOneShot** como acción que se desencadenará y asigna un clip de audio adecuado al campo **Audio Clip** (Clip de audio); por ejemplo, el clip de audio MRTK_Gem:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

Con el objeto RocketLauncher > Buttons (Botones) > **LaunchButton** aún seleccionado, en el componente **Pressable Button (Script)** (Botón presionable [script]), crea un nuevo evento **Touch End ()** (Fin del toque []), configura el objeto **LunarModule** para recibir el evento y define **LaunchLunarModule.StopThruster** como la acción que se desencadenará:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

Si ahora entras en el modo de juego y presionas el botón Launch (Iniciar), oirás el clip de audio reproduciéndose y, si mantienes presionado el botón Launch (Lanzar) un segundo o más, verás el lanzamiento del módulo lunar al espacio:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a>Configuración del botón Reset (Restablecer)

En la ventana Hierarchy (Jerarquía), selecciona RocketLauncher > Buttons (Botones) > objeto **ResetButton**. A continuación, en el componente **Pressable Button (Script)** (Botón presionable [script]), crea un nuevo evento **Button Pressed ()** (Botón presionado []), configura el objeto **LunarModule** para recibir el evento y define **LaunchLunarModule.ResetModule** como la acción que se desencadenará:

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

Con el objeto RocketLauncher > Buttons (Botones) > **ResetButton** aún seleccionado, en el componente **Pressable Button (Script)** (Botón presionable [script]), crea un nuevo evento **Button Pressed ()** (Botón presionado []), configura el objeto **RocketLauncher** para recibir el evento, define **GameObject.BroadcastMessage** como acción que se debe desencadenar y escribe **ResetPlacement** en el campo de mensaje:

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> La acción GameObject.BroadcastMessage envía el mensaje ResetPlacement del objeto RocketLauncher a todos sus objetos secundarios. Cualquier objeto secundario que tenga la función ResetPlacement, que se define en el componente Part Assembly Demo (Script) (Demostración de ensamblado de piezas [script]) que has agregado a todos los objetos secundarios de LunarModuleParts, invocará la función ResetPlacement, que restablece la posición del objeto secundario.

Si ahora entras en modo de juego, mueves algunas piezas o lanzas el módulo lunar y, a continuación, presionas el botón Reset (Restablecer), verás que se restaura la posición original de las piezas o el módulo lunar:

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a>Configuración del botón Placement Hints (Sugerencias de selección de ubicación)
<!-- TODO: Rename to 'Configuring the Hints button'-->

En la ventana Hierarchy (Jerarquía), selecciona RocketLauncher > Buttons (Botones) > objeto **HintsButton**. A continuación, en el componente **Pressable Button (Script)** (Botón presionable [script]), crea un nuevo evento **Button Pressed ()** (Botón presionado []), configura el objeto **LunarModule** para recibir el evento y define **TogglePlacementHints.ToggleGameObjects** como la acción que se desencadenará:

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

Si ahora entras en el modo de juego, observarás que las sugerencias de selección de ubicación están deshabilitadas de forma predeterminada, pero puedes activarlas y desactivarlas presionando el botón Hints (Sugerencias):

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a>Enhorabuena

Ya has configurado totalmente esta aplicación. Ahora, la aplicación permite a los usuarios ensamblar completamente el módulo lunar, lanzarlo, activar o desactivar las sugerencias y reiniciar la aplicación para volver a empezar
