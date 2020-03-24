---
title: 'Tutoriales de introducción: 6. Exploración de opciones avanzadas de entrada'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: ec078015304e1cddc9b042fb5e94cf1904a302cb
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2020
ms.locfileid: "79376092"
---
# <a name="6-exploring-advanced-input-options"></a>6. Exploración de opciones avanzadas de entrada

En este tutorial, explorarás varias opciones de entrada avanzadas para HoloLens 2, como el uso de comandos de voz, gestos panorámicos y seguimiento ocular.

## <a name="objectives"></a>Objetivos

* Desencadenar eventos mediante comandos de voz y palabras clave
* Usar el seguimiento de manos para desplazar lateralmente las texturas y objetos 3D
* Aprovechar las funcionalidades de seguimiento ocular de HoloLens 2 para seleccionar objetos

## <a name="enabling-voice-commands"></a>Habilitar comandos de voz
<!-- TODO: Consider changing to 'Enabling Speech Commands -->

En esta sección, implementarás un comando de voz para que el usuario pueda reproducir un sonido en el objeto Octa. Para ello, deberás crear un nuevo comando de voz y, a continuación, configurar el evento para que desencadene la acción deseada cuando se diga la palabra clave del comando de voz.

Los principales pasos que debes seguir para lograrlo son:

1. Clonar el perfil del sistema de entrada predeterminado
2. Clonar el perfil de los comandos de voz predeterminados
3. Crear un nuevo comando de voz
4. Agregar y configurar el componente Speech Input Handler (Script) (Controlador de entrada de voz [script])
5. Implementar el evento de respuesta para el comando de voz

### <a name="1-clone-the-default-input-system-profile"></a>1. Clonar el perfil del sistema de entrada predeterminado

En la ventana Hierarchy (Jerarquía), selecciona el objeto **MixedRealityToolkit**. A continuación, en la ventana Inspector, selecciona la pestaña **Input** (Entrada) y clona **DefaultHoloLens2InputSystemProfile** para sustituirlo por tu propio valor de **Input System Profile** (Perfil de sistema de entrada):

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step1-1.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo clonar perfiles de MRTK, puedes consultar las instrucciones de [Configuración de los perfiles de Mixed Reality Toolkit](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option).

### <a name="2-clone-the-default-speech-commands-profile"></a>2. Clonar el perfil de los comandos de voz predeterminados

Expande la sección **Speech** (Voz) y clona **DefaultMixedRealitySpeechCommandsProfile** para sustituirlo por tu propio valor personalizable de **Speech Commands Profile** (Perfil de comandos de voz):

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step2-1.png)

### <a name="3-create-a-new-speech-command"></a>3. Crear un nuevo comando de voz

En la sección **Speech Commands** (Comandos de voz), haz clic en el botón **+ Add a New Speech Command** (Agregar nuevo comando de voz) en la parte inferior de la lista de comandos de voz existentes y, a continuación, en el campo **Keyword** (Palabra clave), escribe una palabra o frase adecuada; por ejemplo, **Play Music** (Reproducir música):

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step3-1.png)

> [!TIP]
> Si el equipo no tiene micrófono y quieres probar el comando de voz con la simulación en el editor, puedes asignar un valor de KeyCode al comando de voz que te permitirá desencadenarlo cuando se presione la tecla correspondiente.

### <a name="4-add-and-configure-the-speech-input-handler-script-component"></a>4. Agregar y configurar el componente Speech Input Handler (Script) (Controlador de entrada de voz [script])

En la ventana Hierarchy (Jerarquía), selecciona el objeto **Octa** y agrega el componente **Speech Input Handler (Script)** (Controlador de entrada de voz [script]) al objeto Octa. A continuación, desactiva la casilla **Is Focus Required** (Se requiere foco) para que no sea necesario que el usuario observe objeto Octa para desencadenar el comando de voz:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step4-1.png)

### <a name="5-implement-the-response-event-for-the-speech-command"></a>5. Implementar el evento de respuesta para el comando de voz

En el componente Speech Input Handler (Script) (Controlador de entrada de voz [script]), haz clic en el pequeño botón **+** para agregar un elemento de palabra clave a la lista de palabras clave:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-1.png)

Haz clic en el **elemento 0** recién creado para expandirlo y, a continuación, en la lista desplegable **Keyword** (Palabra clave), elige la palabra clave **Play Music** (Reproducir música) que creaste anteriormente:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-2.png)

> [!NOTE]
> Las palabras clave de la lista desplegable Keyword (Palabra clave) se rellenan en función de las palabras clave definidas en la lista Speech Commands (Comandos de voz) en el perfil de comandos de voz.

Crea un nuevo evento **Response ()** (Respuesta []), configura el objeto **Octa** para recibir el evento, define **AudioSource.PlayOneShot** como la acción que se desencadenará y asigna un clip de audio adecuado al campo **Audio Clip** (Clip de audio); por ejemplo, el clip de audio MRTK_Gem:

![mrlearning-base](images/mrlearning-base/tutorial5-section1-step5-3.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo implementar eventos y asignar un clip de audio, puedes consultar las instrucciones de [Implementar el evento On Touch Started](mrlearning-base-ch4.md#4-implement-the-on-touch-started-event) (Iniciado con el tacto []).

## <a name="the-pan-gesture"></a>Gesto de desplazamiento panorámico

El gesto de desplazamiento lateral es útil para desplazarse empleando un dedo o la mano para desplazarse por el contenido. En este ejemplo, primero aprenderás a desplazarte por una interfaz de usuario 2D y, a continuación, a desplazarte por una colección de objetos 3D.

Los principales pasos que debes seguir para lograrlo son:

1. Crear un objeto cuádruple que se pueda usar para el desplazamiento lateral
2. Agregar el componente Near Interaction Touchable (Script) (Interacción próxima táctil [script])
3. Agregar el componente Hand Interaction Pan Zoom (Script) (Interacción de mano de zoom de desplazamiento lateral [script])
4. Agregar contenido 2D que se desplazará
5. Agregar contenido 3D que se desplazará
6. Agregar el componente Move With Pan (Script) (Mover con desplazamiento lateral [script])

> [!NOTE]
> El componente Move With Pan (Script) (Mover con desplazamiento lateral [script]) no forma parte de MRTK. Se proporcionó con los recursos de este tutorial.

### <a name="1-create-a-quad-object-that-can-be-used-for-panning"></a>1. Crear un objeto cuádruple que se pueda usar para el desplazamiento lateral

En la ventana Hierarchy (Jerarquía), haz clic con el botón derecho en una área vacía y selecciona **3D Object** > **Quad** (Objeto 3D > Cuadrante) para agregar un cuadrante a la escena. Asígnale un nombre adecuado; por ejemplo, **PanGesture** y colócalo en una ubicación adecuada; por ejemplo, X = 0, Y = -0,2, Z = 2.

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-1.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo agregar objetos primitivos de Unity, como un cuadrante 3D, a la escena, consulta las instrucciones de [Agregar un cubo a la escena](mrlearning-base-ch2.md#2-add-a-cube-to-the-scene).

Como sucede con cualquier otra interacción, el gesto de desplazamiento lateral también requiere un colisionador. De forma predeterminada, un cuadrante tiene un colisionador de malla. Sin embargo, este no es el ideal, ya que es extremadamente fino. Para que al usuario le resulte más fácil interactuar con el colisionador, lo reemplazaremos con un colisionador de cuadro.

Con el objeto PanGesture aún seleccionado, haz clic en el icono de **configuración** del componente **Mesh Collider** (Colisionador de malla) y selecciona **Remove Component** (Quitar componente) para quitar este colisionador:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-2.png)

En la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar un elemento **Box Collider** (Colisionador de cuadro). A continuación, cambia su valor **Size** (Tamaño) Z a 0,15 para aumentar su espesor:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step1-3.png)

### <a name="2-add-the-near-interaction-touchable-script-component"></a>2. Agregar el componente Near Interaction Touchable (Script) (Interacción próxima táctil [script])

Con el objeto **PanGesture** todavía seleccionado, agrega el componente **Near Interaction Touchable (Script)** (Interacción próxima táctil [script]) al objeto PanGesture y, a continuación, haz clic en los botones **Fix Bounds** (Corregir límites) y **Fix Center** (Corregir centro) para actualizar el centro local y las propiedades de los límites de Near Interaction Touchable (Script) (Interacción próxima táctil [script]) para que coincidan con BoxCollider:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step2-1.png)

### <a name="3-add-the-hand-interaction-pan-zoom-script-component"></a>3. Agregar el componente Hand Interaction Pan Zoom (Script) (Interacción de mano de zoom de desplazamiento lateral [script])

Con el objeto **PanGesture** todavía seleccionado, agrega el componente **Hand Interaction Pan Zoom (Script)** (Interacción de mano de zoom de deslizamiento horizontal [script]) al objeto PanGesture y, a continuación, activa la casilla **Lock Horizontal** (Bloquear horizontalmente) para permitir solo el desplazamiento vertical:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step3-1.png)

### <a name="4-add-2d-content-to-be-scrolled"></a>4. Agregar contenido 2D que se desplazará

En el panel Project (Proyecto), busca el material de **PanContent** y, a continuación, haz clic y arrástralo hasta la propiedad 0 del elemento **Material** del representador de malla del objeto **PanGesture**:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-1.png)

En la ventana Inspector, expande el componente de material **PanContent** recién agregado y, a continuación, cambia su valor Y de **Tiling** (Disposición en mosaico) Y a 0,5 para que coincida con el valor de X y los iconos sean cuadrados:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-2.png)

Si entras en el modo de juego, puedes probar el desplazamiento del contenido 2D mediante el gesto de desplazamiento lateral en la simulación en el editor:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step4-3.png)

### <a name="5-add-3d-content-to-be-scrolled"></a>5. Agregar contenido 3D que se desplazará

En la ventana Hierarchy (Jerarquía), **crea cuatro cubos** como objetos secundarios del objeto **PanGesture** y define su **escala** de transformación como X = 0,15, Y = 0,15, Z = 0,15:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-1.png)

Para espaciar los cubos de forma uniforme y ahorrar tiempo, agrega el componente **Grid Object Collection (Script)** (Colección de objetos de cuadrícula [script]) al objeto principal de los cubos (p. ej., el objeto **PanGesture**) y configura Grid Object Collection (Script) (Colección de objetos de cuadrícula [script]) como se indica a continuación:

* Cambia **Num Rows** (Número de filas) a 1 para que todos los cubos estén alineados en una sola fila.
* Cambia **Cell Width** (Ancho de celda) a 0,25 para espaciar los cubos dentro de la fila.

A continuación, haz clic en el botón **Actualizar colección** para aplicar la nueva configuración:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step5-2.png)

### <a name="6-add-the-move-with-pan-script-component"></a>6. Agregar el componente Move With Pan (Script) (Mover con desplazamiento lateral [script])

En la ventana Hierarchy (Jerarquía), selecciona todos los **objetos secundarios del cubo** y, a continuación, en la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar el componente **Move With Pan (Script)** (Mover con desplazamiento lateral [script]) a todos los cubos:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-1.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo seleccionar varios objetos en la ventana Hierarchy (Jerarquía), consulta las instrucciones de [Agregar el componente Manipulation Handler (Script) (Controlador de manipulación [script]) a todos los objetos](mrlearning-base-ch4.md#1-add-the-manipulation-handler-script-component-to-all-the-objects).

Con todos los cubos aún seleccionados, haz clic en el objeto **PanGesture** y arrástralo al campo **Pan Input Source** (Origen de entrada de desplazamiento lateral):

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-2.png)

> [!TIP]
> El componente Move With Pan (Script) (Mover con desplazamiento lateral [script]) de cada cubo realiza escuchas del evento Pan Updated (Actualizado con desplazamiento lateral) que envía el componente Hand Interaction Pan Zoom (Script) (Interacción de mano de zoom de desplazamiento lateral [script]) en el objeto PanGesture, que se asignó como Origen de entrada de desplazamiento lateral en el paso anterior, y actualiza la posición de cada cubo según corresponde.

En la ventana Hierarchy (Jerarquía), selecciona el objeto **PanGesture** y, a continuación, en el inspector, **desactiva** la casilla **Mesh Renderer** (Representador de malla) para deshabilitar el componente del representador de malla:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-3.png)

Si entras en el modo de juego, puedes probar el desplazamiento del contenido 3D mediante el gesto de desplazamiento lateral en la simulación en el editor:

![mrlearning-base](images/mrlearning-base/tutorial5-section2-step6-4.png)

## <a name="eye-tracking"></a>Seguimiento de los ojos

En esta sección, explorarás cómo habilitar el seguimiento ocular en el proyecto. En este ejemplo, implementarás la funcionalidad para hacer que cada objeto de 3DObjectCollection gire lentamente mientras la mirada del usuario lo observa. Además, cuando el objeto observado se seleccione pulsando en el aire o mediante un comando de voz, se desencadenará un efecto de parpadeo.

Los principales pasos que debes seguir para lograrlo son:

1. Agrega el componente Eye Tracking Target (Script) (Destino del seguimiento ocular [script]) a todos los objetos de destino.
2. Agrega el componente Eye Tracking Tutorial Demo (Script) (Demostración de tutorial de seguimiento ocular [script]) a todos los objetos de destino.
3. Implementa el evento While Looking At Target (Al mirar el objetivo).
4. Implementa el evento On Selected (En selección).
5. Habilita el seguimiento ocular simulado para las simulaciones en el editor.
6. Habilita la entrada de mirada en las funcionalidades de la aplicación del proyecto de Visual Studio

### <a name="1-add-the-eye-tracking-target-script-component-to-all-target-objects"></a>1. Agrega el componente Eye Tracking Target (Script) (Destino del seguimiento ocular [script]) a todos los objetos de destino.

En la ventana Hierarchy (Jerarquía), expande el objeto **3DObjectCollection** y selecciona todos los **objetos secundarios**. A continuación, en la ventana Inspector, usa el botón **Add Component** (Agregar componente) para agregar el componente **Eye Tracking Target (Script)** (Destino del seguimiento ocular [script]) a todos los objetos secundarios:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-1.png)

Con todos los **objetos secundarios** todavía seleccionados, configura el componente **Eye Tracking Target (Script)** (Destino del seguimiento ocular [script]) como se indica a continuación:

* Cambia **Select Action** (Seleccionar acción) a **Select** (Seleccionar) para definir la acción de punteo en el aire para este objeto como selección.
* Expande **Voice Select** (Selección de voz) y establece el valor de **Size** (Tamaño) de la lista de comandos de voz en 1. A continuación, en la lista de nuevos elementos que aparece, cambia **Element 0** (Elemento 0) a **Select** (Seleccionar) para definir la acción de comando de voz para este objeto como selección.

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step1-2.png)

### <a name="2-add-the-eye-tracking-tutorial-demo-script-component--to-all-target-objects"></a>2. Agrega el componente Eye Tracking Tutorial Demo (Script) (Demostración de tutorial de seguimiento ocular [script]) a todos los objetos de destino.

Con todos los **objetos secundarios** todavía seleccionados, usa el botón **Add Component** (Agregar componente) para agregar el componente **Eye Tracking Tutorial Demo (Script)** (Demostración de tutorial de seguimiento ocular [script]) a todos los objetos secundarios:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step2-1.png)

> [!NOTE]
> El componente Eye Tracking Target (Script) (Destino del seguimiento ocular [script]) no forma parte de MRTK. Se proporcionó con los recursos de este tutorial.

### <a name="3-implement-the-while-looking-at-target-event"></a>3. Implementa el evento While Looking At Target (Al mirar el objetivo).

En la ventana Hierarchy (Jerarquía), selecciona el objeto **Cheese** y, a continuación, crea un nuevo evento **While Looking At Target ()** (Al observar el destino []), configura el objeto **Cheese** para recibir el evento y define **EyeTrackingTutorialDemo.RotateTarget** como la acción que se va a desencadenar:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step3-1.png)

**Repite** esta acción para cada uno de los objetos secundarios de 3DObjectCollection.

> [!TIP]
> Para obtener un recordatorio sobre cómo implementar eventos, consulta las instrucciones de [Gestos de seguimiento de manos y botones interactuables](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons).

### <a name="4-implement-the-on-selected-event"></a>4. Implementa el evento On Selected (En selección).

En la ventana Hierarchy (Jerarquía), selecciona el objeto **Cheese** y, a continuación, crea un nuevo evento **On Selected ()** (En la selección []), configura el objeto **Cheese** para recibir el evento y define **EyeTrackingTutorialDemo.BlipTarget** como la acción que se va a desencadenar:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step4-1.png)

**Repite** esta acción para cada uno de los objetos secundarios de 3DObjectCollection.

### <a name="5-enable-simulated-eye-tracking-for-in-editor-simulations"></a>5. Habilita el seguimiento ocular simulado para las simulaciones en el editor.

En la ventana Hierarchy (Jerarquía), selecciona el objeto **MixedRealityToolkit**. A continuación, en la ventana Inspector, selecciona la pestaña **Input** (Entrada), expande la sección **Input Data Providers** (Proveedores de datos de entrada) y, a continuación, la sección **Input Simulation Service** (Servicio de simulación de entrada) y clona **DefaultMixedRealityInputSimulationProfile** para reemplazarlo con tu propio **Input Simulation Profile** (Perfil de simulación de entrada):

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-1.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo clonar perfiles de MRTK, puedes consultar las instrucciones de [Configuración de los perfiles de Mixed Reality Toolkit](mrlearning-base-ch2.md#how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option).

En la sección **Eye Simulation** (Simulación ocular), activa la casilla **Simulate Eye Position** (Simular posición ocular) para habilitar la simulación del seguimiento ocular:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-2.png)

Si ahora entras en el modo de juego, puedes probar los efectos de giro y parpadeo que has implementado ajustando la vista para que el cursor toque uno de los objetos y usando la interacción con la mano o el comando de voz para seleccionar el objeto:

![mrlearning-base](images/mrlearning-base/tutorial5-section3-step5-3.png)

> [!NOTE]
> Si no usaste DefaultHoloLens2ConfigurationProfile para clonar el perfil de configuración de MRTK personalizable, como se indica en las instrucciones de [Configuración de Mixed Reality Toolkit](mrlearning-base-ch1.md#configure-the-mixed-reality-toolkit), puede que el seguimiento ocular no esté habilitado en el proyecto y que se deba habilitar. Para ello, puedes consultar las instrucciones de [Introducción al seguimiento ocular en MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html).

### <a name="6-enable-gaze-input-in-the-visual-studio-projects-app-capabilities"></a>6. Habilita la entrada de mirada en las funcionalidades de la aplicación del proyecto de Visual Studio

Antes de compilar e implementar la aplicación desde Visual Studio en el dispositivo, se debe habilitar la entrada de mirada en las funcionalidades de la aplicación del proyecto. Para hacerlo, puedes seguir las instrucciones de [Probar la aplicación de Unity en HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/EyeTracking/EyeTracking_BasicSetup.html#testing-your-unity-app-on-a-hololens-2).

## <a name="congratulations"></a>Enhorabuena

Has conseguido agregar las funcionalidades básicas de seguimiento ocular a la aplicación. Estas acciones son solo el comienzo de un mundo lleno de posibilidades relacionadas con el seguimiento de los ojos. En este tutorial, también has obtenido información sobre otras características de entrada avanzadas, como los comandos de voz y los gestos de desplazamiento lateral.

[Siguiente lección: 7. Creación de una aplicación de ejemplo de módulo lunar](mrlearning-base-ch6.md)
