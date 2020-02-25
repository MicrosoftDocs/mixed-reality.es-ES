---
title: 'Tutoriales de introducción: 7. Crear una aplicación de ejemplo de módulo lunar'
description: En esta lección, combinará varios conceptos aprendidos en lecciones anteriores para crear una experiencia de ejemplo única.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 3a557be91bee9b98e750ae1546ea1c4b3103298e
ms.sourcegitcommit: bd536f4f99c71418b55c121b7ba19ecbaf6336bb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2020
ms.locfileid: "77555284"
---
# <a name="7-creating-a-lunar-module-sample-application"></a>7. crear una aplicación de ejemplo de módulo lunar
<!-- TODO: Rename to 'Creating a Rocket Launcher sample application' -->

En este tutorial, se combinan varios conceptos de lecciones anteriores para crear una experiencia de ejemplo única. Aprenderá a crear una aplicación de ensamblado de elementos en la que un usuario necesita usar manos con seguimiento para recoger piezas e intentar ensamblar un módulo lunar. Usará los botones que se puede presionar para activar o desactivar las sugerencias de colocación, para restablecer la experiencia y para iniciar el módulo lunar en el espacio.

En los tutoriales futuros, continuará teniendo en cuenta esta experiencia, que incluye eficaces casos de uso de varios usuarios que aprovechan los delimitadores espaciales de Azure para la alineación espacial.

## <a name="objectives"></a>Objetivos

* Agrupar varios conceptos de lecciones anteriores para crear una experiencia única
* Obtener información sobre cómo activar o desactivar los objetos
* Desencadenar eventos complejos mediante los botones presionables
* Usar la física y la fuerza de los cuerpos rígidos
* Explorar el uso de la información sobre herramientas

## <a name="lunar-module-parts-overview"></a>Información general sobre los elementos del módulo lunar
<!-- TODO: Rename to 'Implementing the part assembly functionality' -->

En esta sección, creará un desafío de ensamblado de elemento simple en el que el objetivo del usuario es colocar cinco partes que se distribuyen en la tabla en la ubicación correcta en el módulo lunar.

Los principales pasos que se deben seguir para lograrlo son:

1. Agregar el selector de Rocket recurso prefabricado a la escena
2. Habilitar la manipulación de objetos para todos los elementos
3. Agregar y configurar el componente de demostración (Script) del ensamblado de elementos

> [!NOTE]
> El componente de demostración del ensamblado de elementos (Script) no forma parte de MRTK. Se proporcionó con los recursos de este tutorial.

### <a name="1-add-the-rocket-launcher-prefab-to-the-scene"></a>1. agregar el selector de Rocket recurso prefabricado a la escena

En la ventana de proyecto, navegue a los **recursos** > **MRTK. Tutoriales. GettingStarted** > **Prefabs** > carpeta **RocketLauncher** , arrastre **RocketLauncher** recurso prefabricado a la ventana jerarquía para agregarlo a la escena y, a continuación, colóquelo en una ubicación adecuada, por ejemplo:

* Posición de transformación X = 1,5, Y =-0,4, Z = 0, por lo que se coloca a la derecha del usuario en Waist height
* Transformación de giro X = 0, Y = 180, Z = 0, por lo que las características principales de la experiencia enfrentan al usuario

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-1.png)

### <a name="2-enable-object-manipulation-for-all-the-parts"></a>2. habilitar la manipulación de objetos para todos los elementos

En la ventana de jerarquía, busque el objeto RocketLauncher > **LunarModuleParts** y seleccione todos los **objetos secundarios**, agregue el componente de **controlador de manipulación (Script)** y el componente de **captura de interacción cercana (Script)** y, a continuación, configure el controlador de manipulación (Script) como se indica a continuación:

* Desactive la casilla **permitir la manipulación lejana** para permitir solo la interacción aproximada
* Cambiar el **tipo de manipulación bidireccionales** para **pasar el giro** de modo que el escalado esté deshabilitado

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step1-2.png)

> [!TIP]
> Para obtener un recordatorio con instrucciones paso a paso sobre cómo implementar la manipulación de objetos, puede consultar las instrucciones de [manipulación de objetos 3D](mrlearning-base-ch4.md#manipulating-3d-objects) .

### <a name="3-add-and-configure-the-part-assembly-demo-script-component"></a>3. agregar y configurar el componente de demostración (Script) del ensamblado de elementos

Con todos los objetos secundarios de LunarModuleParts todavía seleccionados, agregue un componente de **origen de audio** y, a continuación, configúrelo como se indica a continuación:

* Asigne un clip de audio adecuado al campo **AudioClip** , por ejemplo, MRKT_Scale_Start
* Desactive la casilla **reproducir en activo** , de modo que el clip de audio no se reproduzca automáticamente cuando se cargue la escena.
* Cambiar la **mezcla espacial** a 1 para habilitar el audio espacial

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-1.png)

Con todos los objetos secundarios LunarModuleParts todavía seleccionados, agregue el componente **Demo (Script) del ensamblado de elementos** :

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-2.png)

En la ventana jerarquía, seleccione el objeto **RoverEnclosure** y configure su componente **Demo (Script) de ensamblado de elementos** como se indica a continuación:

* En el campo **objeto que se va a colocar** , asigne **el objeto en este caso, el**objeto RoverEnclosure
* En el campo **Ubicación para colocar** , asigne el objeto **PlacementHints** correspondiente, en este caso, el objeto RoverEnclosure_PlacementHint
* En el campo **objeto de información sobre herramientas** , asigne la **información sobre herramientas**correspondiente, en este caso, el objeto RoverEnclosure_ToolTip
* En el campo **origen de audio** , asigne el **propio**objeto, en este caso, el objeto RoverEnclosure

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-3.png)

**Repita el procedimiento** para cada uno de los demás objetos secundarios LunarModuleParts, es decir, Fueltank, EnergyCell, DockingPortal y ExternalSensor.

Si ahora entra en el modo de juego y mueve un "objeto que se va a colocar" cerca de su correspondiente "ubicación para colocar", observará lo siguiente:

* El objeto se ajustará en su lugar y será primario en el objeto LunarModule para que se convierta en parte del módulo lunar.
* El origen de audio del objeto reproducirá el clip de audio asignado en la ubicación del objeto.
* Se ocultará el objeto de información sobre herramientas correspondiente

![mrlearning-base](images/mrlearning-base/tutorial6-section1-step2-4.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo usar la simulación de entrada en el editor, puede consultar el [uso de la simulación de entrada de la mano del editor para probar una](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guía de escenas en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="configuring-the-lunar-module"></a>Configuración del módulo lunar

En esta sección, agregará características adicionales a la aplicación Rocket Launcher para que el usuario pueda:

* Interacción con el módulo lunar
* Iniciar el módulo lunar en el espacio y reproducir un sonido cuando se inicie
* Restablecer la aplicación para que el módulo lunar y todas las partes se vuelvan a colocar en su posición original
* Oculte las sugerencias de selección de ubicación para dificultar el desafío del ensamblado de elementos.

Los principales pasos que se deben seguir para lograrlo son:

1. Habilitar la manipulación de objetos
2. Habilitar física
3. Agregar un componente de origen de audio
4. Agregar y configurar el componente de módulo lunar de inicio (Script)
5. Agregar y configurar el componente de alternar sugerencias de colocación (Script)

> [!NOTE]
> El componente módulo lunar de inicio (Script) y el componente sugerencias de selección de ubicación de alternancia (Script) no forman parte de MRTK. Se proporcionaron con los recursos de este tutorial.

### <a name="1-enable-object-manipulation"></a>1. habilitar la manipulación de objetos

En la ventana jerarquía, seleccione el objeto RocketLauncher > **LunarModule** , agregue el componente de **controlador de manipulación (Script)** y el componente de **captura de interacción cercana (Script)** y, a continuación, configure el controlador de manipulación (Script) como sigue:

* Desactive la casilla **permitir la manipulación lejana** para permitir solo la interacción aproximada
* Cambiar el **tipo de manipulación bidireccionales** para pasar el giro de modo que el escalado esté deshabilitado

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step1-1.png)

### <a name="2-enable-physics"></a>2. habilitar la física

Con el objeto RocketLauncher > **LunarModule** todavía seleccionado, agregue un componente **cuerpo rígido** y, a continuación, configúrelo de la siguiente manera:

* Desactive la casilla **usar gravedad** para que el módulo lunar no se vea afectado por la gravedad
* Active la casilla **es cinemático** para que el módulo lunar inicialmente no se vea afectado por las fuerzas preparadas.

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step2-1.png)

### <a name="3-add-an-audio-source-component"></a>3. agregar un componente de origen de audio

Con el objeto RocketLauncher > **LunarModule** todavía seleccionado, agregue un componente de **origen de audio** y, a continuación, configúrelo de la siguiente manera:

* Cambiar la **mezcla espacial** a 1 para habilitar el audio espacial

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step3-1.png)

### <a name="4-add-and-configure-the-launch-lunar-module-script-component"></a>4. agregar y configurar el componente de módulo lunar de inicio (Script)

Con el objeto RocketLauncher > **LunarModule** todavía seleccionado, agregue el componente **iniciar el módulo lunar (Script)** y, a continuación, configúrelo de la siguiente manera:

* Cambiar el valor de **empuje** para que el módulo lunar se vuele correctamente cuando se inicie, por ejemplo, en 0,01

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step4-1.png)

### <a name="5-add-and-configure-the-toggle-placement-hints-script-component"></a>5. agregar y configurar el componente sugerencias de colocación de alternancia (Script)

Con el objeto RocketLauncher > **LunarModule** todavía seleccionado, agregue el componente **sugerencias de colocación de alternancia (Script)** y, a continuación, configúrelo de la siguiente manera:

* Establezca la propiedad **tamaño** de la matriz de objetos de juego en 5.
* Asigne cada uno de los **objetos secundarios** del objeto RocketLauncher > LunarModule > **PlacementHints** al campo un **elemento** de la matriz de objetos de juego:

![mrlearning-base](images/mrlearning-base/tutorial6-section2-step5-1.png)

## <a name="configuring-the-launch-button"></a>Configuración del botón Launch

En la ventana jerarquía, seleccione los botones de RocketLauncher > > objeto **LaunchButton** y, a continuación, en el componente de **botón (Script)** que se puede presionar, cree un nuevo **botón pressed ()** , configure el objeto **LunarModule** para recibir el evento y defina **LaunchLunarModule. StartThruster** como la acción que se va a desencadenar:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-1.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo implementar eventos, puede consultar las instrucciones de [gestos de seguimiento de mano e](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) interactivos.

Con los botones de > RocketLauncher > objeto **LaunchButton** todavía seleccionado, en el componente de **botón (Script)** que se puede presionar, cree un nuevo **botón ()** , configure el objeto **LunarModule** para recibir el evento, defina **AudioSource. PlayOneShot** como la acción que se va a desencadenar y asigne un clip de audio adecuado al campo **clip** de audio, por ejemplo, el clip de audio MRTK_Gem:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-2.png)

Con los botones de > RocketLauncher > objeto **LaunchButton** todavía seleccionado, en el componente de **botón (Script)** que se puede presionar, cree un nuevo evento **Touch end ()** , configure el objeto **LunarModule** para recibir el evento y defina **LaunchLunarModule. StopThruster** como la acción que se va a desencadenar:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-3.png)

Si ahora entra en el modo de juego y presiona el botón Launch (iniciar), oirá el recorte de audio y, si mantiene presionado el botón Launch (iniciar) durante aproximadamente un segundo o más, verá el lanzamiento del módulo lunar en el espacio:

![mrlearning-base](images/mrlearning-base/tutorial6-section3-step1-4.png)

## <a name="configuring-the-reset-button"></a>Configuración del botón restablecer

En la ventana jerarquía, seleccione los botones de RocketLauncher > > objeto **ResetButton** y, a continuación, en el componente de **botón (Script)** que se puede presionar, cree un nuevo **botón pressed ()** , configure el objeto **LunarModule** para recibir el evento y defina **LaunchLunarModule. ResetModule** como la acción que se va a desencadenar:

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-1.png)

Con los botones de > RocketLauncher > objeto **ResetButton** todavía seleccionado, en el componente de **botón (Script)** que se puede presionar, cree un nuevo **botón ()** , configure el objeto **RocketLauncher** para recibir el evento, defina **GameObject. BroadcastMessage** como la acción que se va a desencadenar y escriba **ResetPlacement** en el campo de mensaje:

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-2.png)

> [!TIP]
> La acción GameObject. BroadcastMessage envía el mensaje ResetPlacement desde el objeto RocketLauncher a todos sus objetos secundarios. Cualquier objeto secundario que tenga la función ResetPlacement, que se define en el componente de demostración (Script) del ensamblado de elementos que ha agregado a todos los objetos secundarios LunarModuleParts, invocará a la función ResetPlacement que restablece la posición del objeto secundario.

Si ahora entra en el modo de juego, mueve algunas partes o inicia el módulo lunar y, a continuación, presiona el botón de restablecimiento, verá que las partes y/o el módulo lunar se restablecen a su posición original:

![mrlearning-base](images/mrlearning-base/tutorial6-section4-step1-3.png)

## <a name="configuring-the-placement-hints-button"></a>Configuración del botón sugerencias de selección de ubicación
<!-- TODO: Rename to 'Configuring the Hints button'-->

En la ventana jerarquía, seleccione los botones de RocketLauncher > > objeto **HintsButton** y, a continuación, en el componente de **botón (Script)** que se puede presionar, cree un nuevo **botón pressed ()** , configure el objeto **LunarModule** para recibir el evento y defina **TogglePlacementHints. ToggleGameObjects** como la acción que se va a desencadenar:

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-1.png)

Si ahora entra en el modo de juego, observará que las sugerencias de colocación translúcida están deshabilitadas de forma predeterminada, pero que puede activarlas y desactivarlas si presiona el botón sugerencias:

![mrlearning-base](images/mrlearning-base/tutorial6-section5-step1-2.png)

## <a name="congratulations"></a>Enhorabuena

Ha configurado completamente esta aplicación. Ahora, la aplicación permite a los usuarios ensamblar completamente el módulo lunar, iniciar el módulo lunar, alternar sugerencias y restablecer la aplicación para que se inicie de nuevo.
