---
title: 'Tutoriales de introducción: 6. Explorar opciones de entrada avanzadas'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 18bcbc95746a2e66b88d83f279603aa7f171bbcb
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77129666"
---
# <a name="6-exploring-advanced-input-options"></a>6. explorar opciones de entrada avanzadas

En este tutorial, explorará algunas opciones de entrada avanzadas para HoloLens 2, incluido el uso de comandos de voz, gestos de movimiento panorámico y seguimiento ocular.

## <a name="objectives"></a>Objetivos

* Desencadenar eventos mediante comandos de voz y palabras clave
* Usar manos con seguimiento para panorámicas y objetos 3D con manos con seguimiento
* Aproveche las capacidades de seguimiento ocular de HoloLens 2 para seleccionar objetos

## <a name="enabling-voice-commands"></a>Habilitar comandos de voz
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

En esta sección, implementará un comando de voz para que el usuario pueda reproducir un sonido en el objeto OCTA. Para ello, creará un nuevo comando de voz y, a continuación, configurará el evento para que desencadene la acción deseada cuando se pronuncia la palabra clave de comando de voz.

Los principales pasos que se deben seguir para lograrlo son:

1. Clonar el perfil del sistema de entrada predeterminado
2. Clonar el perfil predeterminado de comandos de voz
3. Crear un nuevo comando de voz
4. Agregar y configurar el componente de controlador de entrada de voz (Script)
5. Implementar el evento de respuesta para el comando de voz

### <a name="1-clone-the-default-input-system-profile"></a>1. clonar el perfil del sistema de entrada predeterminado

En la ventana jerarquía, seleccione el objeto **MixedRealityToolkit** y, a continuación, en la ventana del inspector, seleccione la pestaña **entrada** y Clone el **DefaultHoloLens2InputSystemProfile** para reemplazarlo por su propio perfil de **sistema de entrada**personalizable:

![mrlearning: base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo clonar perfiles de MRTK, puede consultar las instrucciones de [configuración de los perfiles de el kit de herramientas de realidad mixta](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) .

### <a name="2-clone-the-default-speech-commands-profile"></a>2. clonar el perfil predeterminado de comandos de voz

Expanda la sección **voz** y Clone el **DefaultMixedRealitySpeechCommandsProfile** para reemplazarlo por su perfil personalizado de **comandos de voz**.

![mrlearning: base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a>3. crear un nuevo comando de voz

En la **sección comandos de voz** , haga clic en el botón **+ Agregar un nuevo comando de voz** para agregar un nuevo comando de voz a la parte inferior de la lista de comandos de voz existentes y, a continuación, en el campo **palabra clave** escriba una palabra o frase adecuada, por ejemplo **reproducir música**:

![mrlearning: base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> Si el equipo no tiene micrófono y desea probar el comando de voz mediante la simulación en el editor, puede asignar un KeyCode al comando de voz que le permitirá desencadenarlo cuando se presione la tecla correspondiente.

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a>4. agregar y configurar el componente de controlador de entrada de voz (Script)

En la ventana jerarquía, seleccione el objeto **OCTA** y agregue el componente **controlador de entrada de voz (Script)** al objeto OCTA. A continuación, desactive la casilla **se requiere el foco** para que el usuario no tenga que ver el objeto OCTA para desencadenar el comando de voz:

![mrlearning: base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a>5. implementar el evento de respuesta para el comando de voz

En el componente de controlador de entrada de voz (Script), haga clic en el botón Small **+** para agregar una palabra clave y, a continuación, en la lista desplegable **palabra** clave, elija la palabra clave **Play Music** que creó anteriormente:

![mrlearning: base](images/mrlearning-base/tutorial5-section1-step5-1.png)

> [!NOTE]
> Las palabras clave de la lista desplegable palabra clave se rellenan en función de las palabras clave definidas en la lista comandos de voz en el perfil comandos de voz.

Cree un nuevo evento **Response ()** , configure el objeto **OCTA** para recibir el evento, defina **AudioSource. PlayOneShot** como la acción que se va a desencadenar y asigne un clip de audio adecuado al campo **clip de audio** , por ejemplo, el MRTK_Gem clip de audio:

![mrlearning: base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo implementar eventos y asignar un clip de audio, puede hacer referencia a las instrucciones para [implementar el evento on Touch Started](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) .

## <a name="the-pan-gesture"></a>Gesto de desplazamiento panorámico

El movimiento panorámico es útil para desplazarse por el dedo o la mano para desplazarse por el contenido. En este ejemplo, primero aprenderá a desplazarse por una interfaz de usuario 2D y, a continuación, a expandir esa para poder desplazarse por una colección de objetos 3D.

Los principales pasos que se deben seguir para lograrlo son:

1. Crear un objeto cuádruple que se puede usar para la panorámica
2. Adición del componente de la interacción táctil (Script) de Near Interaction
3. Adición del componente de zoom de pan de interacción manual (Script)
4. Agregar contenido 2D que se va a desplazar
5. Agregar contenido 3D que se va a desplazar
6. Agregar el componente mover con pan (Script)

> [!NOTE]
> El componente de movimiento con pan (Script) no forma parte de MRTK. Se proporcionó con los recursos de este tutorial.

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a>1. crear un objeto cuádruple que se puede usar para la panorámica

En la ventana jerarquía, haga clic con el botón secundario en un área vacía y seleccione **objeto 3d** > **cuádruple** para agregar un cuádruple a la escena. Asígnele un nombre adecuado, por ejemplo, **PanGesture**, y colóquelo en una ubicación adecuada, por ejemplo, X = 0, y =-0,2, Z = 2.

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo agregar primitivas de Unity, como un 3D cuádruple, a la escena, puede hacer referencia a las instrucciones para [Agregar un cubo a la escena](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene) .

Como con cualquier otra interacción, el movimiento panorámico también requiere un Colisionador. De forma predeterminada, un cuádruple tiene un Colisionador de malla. Sin embargo, el Colisionador de malla no es idóneo porque es extremadamente fino. Para que sea más fácil para el usuario interactuar con el Colisionador, se reemplazará el Colisionador de malla por un Colisionador de caja.

Con el objeto PanGesture aún seleccionado, haga clic en el icono de **configuración** del componente de **Colisionador de malla** y seleccione **quitar componente** para quitar el Colisionador de malla:

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step1-2.png)

En la ventana del inspector, use el botón **Agregar componente** para agregar un **Colisionador de cuadro**y, a continuación, cambie el **tamaño** de colisionador de caja Z a 0,15 para aumentar el grosor del Colisionador de caja:

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a>2. agregar el componente de secuencia de comandos táctil de interacción cercana

Con el objeto **PanGesture** aún seleccionado, agregue el componente de **secuencia de comandos táctil (Script) cerca** de la interacción al objeto PanGesture y, a continuación, haga clic en los botones **corregir límites** y **centro de corrección** para actualizar el centro local y las propiedades de los límites del elemento táctil de interacción cercana (Script) para que coincida con BoxCollider:

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a>3. agregar el componente zoom de pan de interacción (Script)

Con el objeto **PanGesture** aún seleccionado, agregue el componente **zoom de pan de interacción a mano (Script)** al objeto PanGesture y, a continuación, active la casilla **bloquear horizontalmente** para permitir solo el desplazamiento vertical:

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a>4. agregar el contenido 2D que se va a desplazar

En el panel Proyecto, busque el material **PanContent** y, a continuación, haga clic en-y arrástrelo hasta la propiedad 0 del elemento de **material** del representador de malla del objeto **PanGesture** :

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step4-1.png)

En la ventana del inspector, expanda el componente material de **PanContent** recién agregado y, a continuación, cambie su valor y de **mosaico** a 0,5 para que coincida con el valor X y los mosaicos aparezcan cuadrados:

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step4-2.png)

Si ahora entra en el modo de juego, puede probar el desplazamiento del contenido 2D mediante el gesto de panorámica en la simulación en el editor:

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a>5. agregar contenido 3D que se va a desplazar

En la ventana de jerarquía, **cree cuatro cubos** como objetos secundarios de **PanContent** y establezca su **escala** de transformación en X = 0,15, y = 0,15, Z = 0,15:

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step5-1.png)

Para espaciar los cubos de forma uniforme y ahorrar tiempo, agregue el componente de la colección de objetos de cuadrícula (Script) al objeto primario de los cubos, es decir, el objeto PanGesture y configure la colección de objetos Grid (Script) de la manera siguiente:

* Cambie **NUM Rows** a 1 para que todos los cubos estén alineados en una sola fila.
* Cambiar el **ancho de celda** a 0,25 para espaciar los cubos dentro de la fila

A continuación, haga clic en el botón **Actualizar colección** para aplicar la nueva configuración:

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a>6. agregar el componente de movimiento con pan (Script)

En la ventana jerarquía, seleccione todos los **objetos secundarios del cubo**y, a continuación, en la ventana del inspector, use el botón **Agregar componente** para agregar el componente **mover con pan (Script)** a todos los cubos:

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> En el caso de un recordatorio sobre cómo seleccionar varios objetos en la ventana jerarquía, las CDU pueden hacer referencia al [componente agregar el controlador de manipulación (Script) a todas las](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects) instrucciones de objetos.

Con todos los cubos aún seleccionados, haga clic y arrastre el objeto **PanGesture** al campo **origen de entrada de pan** :

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> El componente mover con pan (Script) de cada cubo realiza escuchas para el evento de panorámica actualizado enviado por el componente HandInteractionPanZoom (Script) en el objeto PanGesture, que se asignó como el origen de entrada de pan en el paso anterior, y actualiza la posición de cada cubo. cambia.

En la ventana jerarquía, seleccione el objeto **PanGesture** y, a continuación, en el inspector, **desactive** la casilla **representador de malla** para deshabilitar el componente de representador de malla:

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step6-3.png)

Si ahora entra en el modo de juego, puede probar el desplazamiento del contenido 3D con el gesto de panorámica en la simulación en el editor:

![mrlearning: base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a>Seguimiento de los ojos

En esta sección, aprenderá a habilitar el seguimiento ocular en el proyecto. En este ejemplo, implementará la funcionalidad para hacer que cada objeto del 3DObjectCollection gire lentamente mientras se mira en el ojo del usuario, así como en desencadenar un efecto de señal cuando el objeto que se está buscando está seleccionado por el comando TAP o Speech.

Los principales pasos que se deben seguir para lograrlo son:

1. Agregar el componente de destino de seguimiento ocular (Script) a todos los objetos de destino
2. Agregar el componente de demostración del tutorial de seguimiento de ojo (Script) a todos los objetos de destino
3. Implementar mientras se examina el evento de destino
4. Implementar el en el evento seleccionado
5. Habilitación del seguimiento ocular simulado para simulaciones en el editor
6. Habilitar la entrada de fijamente en las funcionalidades de la aplicación del proyecto de Visual Studio

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a>1. agregar el componente de destino de seguimiento ocular (Script) a todos los objetos de destino

En la ventana de jerarquía, expanda el objeto **3DObjectCollection** y seleccione todos los **objetos secundarios**y, a continuación, en la ventana del inspector, use el botón **Agregar componente** para agregar el componente de **destino de seguimiento ocular (Script)** a todos los objetos secundarios:

![mrlearning: base](images/mrlearning-base/tutorial5-section3-step1-1.png)

Con todos los **objetos secundarios** todavía seleccionados, configure el componente de **destino de seguimiento ocular (Script)** como se indica a continuación:

* Cambie **Seleccionar acción** a **seleccionar**para definir la acción de punteo de aire para este objeto como SELECT.
* Expanda **Voice seleccione** y establezca el **tamaño** de la lista de comandos de voz en 1 y, a continuación, en la lista de nuevos elementos que aparece, cambie el **elemento 0** a **Select**para definir la acción de comando de voz para este objeto como SELECT.

![mrlearning: base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a>2. agregar el componente de demostración del tutorial de seguimiento de ojo (Script) a todos los objetos de destino

Con todos los **objetos secundarios** todavía seleccionados, use el botón **Agregar componente** para agregar el componente de **demostración del tutorial de seguimiento de ojo (Script)** a todos los objetos secundarios:

![mrlearning: base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> El componente objetivo de seguimiento ocular (Script) no forma parte de MRTK. Se proporcionó con los recursos de este tutorial.

### <a name="3-implement-the-while-looking-at-target-event"></a>3. implementar mientras se examina el evento de destino

En la ventana jerarquía, seleccione el objeto de **queso** , cree un nuevo **mientras mira el evento () de destino** , configure el objeto de **queso** para recibir el evento y defina **EyeTrackingTutorialDemo. RotateTarget** como la acción que se va a desencadenar:

![mrlearning: base](images/mrlearning-base/tutorial5-section3-step3-1.png)

**Repita el procedimiento** para cada uno de los objetos secundarios de 3DObjectCollection.

> [!TIP]
> Para obtener un recordatorio sobre cómo implementar eventos, puede consultar las instrucciones de [gestos de seguimiento de mano e](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) interactivos.

### <a name="4-implement-the-on-selected-event"></a>4. implementar el en el evento seleccionado

En la ventana jerarquía, seleccione el objeto **queso** y, a continuación, cree un nuevo en el evento **seleccionado ()** , configure el objeto **queso** para recibir el evento y defina **EyeTrackingTutorialDemo. RotateTarget** como la acción que se va a desencadenar:

![mrlearning: base](images/mrlearning-base/tutorial5-section3-step4-1.png)

**Repita el procedimiento** para cada uno de los objetos secundarios de 3DObjectCollection.

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a>5. habilitar el seguimiento ocular simulado para simulaciones en el editor

En la ventana jerarquía, seleccione el objeto **MixedRealityToolkit** y, a continuación, en la ventana del inspector, seleccione la pestaña **entrada** , expanda la sección proveedores de **datos de entrada** y, a continuación, la sección servicio de simulación de **entrada** y Clone el **DefaultMixedRealityInputSimulationProfile** para reemplazarlo por su propio perfil de **simulación de entrada**personalizable:

![mrlearning: base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo clonar perfiles de MRTK, puede consultar las instrucciones de [configuración de los perfiles de el kit de herramientas de realidad mixta](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option) .

En la sección **simulación ocular** , active la casilla **simular posición ocular** para habilitar la simulación de seguimiento ocular:

![mrlearning: base](images/mrlearning-base/tutorial5-section3-step5-2.png)

Si ahora entra en el modo de juego, puede probar los efectos de giro y señalización que ha implementado ajustando la vista para que el cursor toque uno de los objetos y use la interacción a mano o el comando de voz para seleccionar el objeto:

![mrlearning: base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> Si no usó DefaultHoloLens2ConfigurationProfile para clonar el perfil de configuración de MRTK personalizable, como se indica en las instrucciones de configuración [del kit de herramientas de realidad mixta](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit) , puede que el seguimiento ocular no esté habilitado en el proyecto y deberá habilitarse. Para ello, puede consultar las instrucciones [Getting Started with Eye Tracking en MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html) .

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a>6. habilitar la entrada fijamente en las funcionalidades de la aplicación del proyecto de Visual Studio

Antes de compilar e implementar la aplicación desde Visual Studio en el dispositivo, se debe habilitar la entrada de mirada en las funcionalidades de la aplicación del proyecto. Para ello, puede seguir la prueba de la [aplicación de Unity en las instrucciones de HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2) .

## <a name="congratulations"></a>Enhorabuena

Ha agregado correctamente las funciones básicas de seguimiento de los ojos a la aplicación. Estas acciones son solo el comienzo de un mundo lleno de posibilidades relacionadas con el seguimiento de los ojos. En este tutorial, también aprendió sobre otras características de entrada avanzadas, como comandos de voz y gestos de movimiento panorámico.

[Lección siguiente: 7. crear una aplicación de ejemplo de módulo lunar](mrlearning-base-ch6.md)
