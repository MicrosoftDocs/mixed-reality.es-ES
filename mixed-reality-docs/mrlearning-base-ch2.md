---
title: 'Tutoriales de introducción: 3. Creación de la interfaz de usuario y configuración de Mixed Reality Toolkit'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: c389c7a3d16770dcbf57d9acdcfd81c6507f7cd6
ms.sourcegitcommit: 9df82dba06a91a8d2cedbe38a4328f8b86bb2146
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/29/2020
ms.locfileid: "79376142"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3. Creación de la interfaz de usuario y configuración de Mixed Reality Toolkit
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

En el tutorial anterior, descubriste algunas de las funcionalidades que ofrece Mixed Reality Toolkit (MRTK) e iniciaste tu primera aplicación para HoloLens 2. En este tutorial, aprenderás a crear y organizar los botones junto con los paneles de texto de la interfaz de usuario, y a usar la interacción predeterminada (táctil) para interactuar con cada botón. También explorarás la incorporación de acciones y efectos sencillos, como cambiar el tamaño, el sonido y color de los objetos. En este módulo se presentan los conceptos básicos sobre cómo modificar los perfiles de MRTK. Para empezar, se desactiva la visualización de malla de [asignación espacial](spatial-mapping.md).

## <a name="objectives"></a>Objetivos

* Personalizar y configurar los perfiles de Mixed Reality Toolkit
* Interacción con hologramas mediante botones y elementos de la interfaz de usuario
* Entrada e interacciones básicas del seguimiento de la mano

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Configuración de los perfiles de Mixed Reality Toolkit (opción para cambiar la visualización de reconocimiento espacial)
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

En esta sección, aprenderás a personalizar y configurar los perfiles predeterminados de MRTK.

En este ejemplo concreto se muestra cómo ocultar la malla de reconocimiento espacial cambiando la configuración del observador de la malla espacial. Puedes seguir estos mismos principios para personalizar cualquier parámetro o valor de los perfiles de MRTK.

Los principales pasos que se deben seguir para ocultar la malla de reconocimiento espacial son los siguientes:

1. Clonar el perfil de configuración predeterminado
2. Habilitar el sistema de reconocimiento espacial.
3. Clonar el perfil del sistema de reconocimiento espacial predeterminado.
4. Clonar el perfil del observador de la malla de reconocimiento espacial predeterminado.
5. Cambiar la visibilidad de la malla de reconocimiento espacial.

> [!NOTE]
> De forma predeterminada, los perfiles de MRTK no son editables. Estas son las plantillas de perfil predeterminadas que se deben clonar para poder editarse. Hay varias capas anidadas de perfiles. Por lo tanto, es habitual clonar y editar varios perfiles al configurar uno o varios parámetros.

### <a name="1-clone-the-default-configuration-profile"></a>1. Clonar el perfil de configuración predeterminado

> [!NOTE]
> El perfil de configuración es el perfil de nivel superior. Por lo tanto, para poder editar cualquier otro perfil, antes debe clonar el perfil de configuración.

Con el objeto **MixedRealityToolkit** seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, cambia el valor de **Configuration Profile** (Perfil de configuración) de Mixed Reality Toolkit a **DefaultHoloLens2ConfigurationProfile**:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-1.png)

Con el objeto **MixedRealityToolkit** todavía seleccionado, en la ventana Inspector, haz clic en el botón **Copy & Customize** (Copiar y personalizar) para abrir la ventana Clone Profile (Clonar perfil):

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-2.png)

En la ventana Clone Profile (Clonar perfil), haz clic en el botón **Clone** (Clonar) para crear una copia modificable de **DefaultHololens2ConfigurationProfile**:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-3.png)

El perfil de configuración recién creado se asigna ahora como perfil de configuración de la escena:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step1-4.png)

En el menú de Unity, selecciona **File** > **Save** (Archivo > Guardar) para guardar la escena.

> [!TIP]
> Recuerda guardar el trabajo a lo largo del tutorial.

### <a name="2-enable-the-spatial-awareness-system"></a>2. Habilitar el sistema de reconocimiento espacial

Con el objeto **MixedRealityToolkit** todavía seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, selecciona la pestaña **Reconocimiento espacial** y, a continuación, activa la casilla **Enable Spatial Awareness System** (Habilitar el sistema de reconocimiento espacial):

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. Clonar el perfil del sistema de reconocimiento espacial predeterminado

En la pestaña **Spatial Awareness** (Reconocimiento espacial), haz clic en el botón **Clone** (Clonar) para abrir la ventana Clone Profile (Clonar perfil):

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-1.png)

En la ventana Clone Profile (Clonar perfil), haz clic en el botón **Clone** (Clonar) para crear una copia modificable de **DefaultMixedRealitySpatialAwarenessSystemProfile**:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-2.png)

Ahora, el perfil del sistema de reconocimiento espacial recién creado se asigna automáticamente al perfil de configuración:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. Clonar el perfil del observador de la malla de reconocimiento espacial predeterminado

Con la pestaña **Spatial Awareness** (Reconocimiento espacial) aún seleccionada, expande la sección **Windows Mixed Reality Spatial Mesh Observer** (Observador de malla espacial de Windows Mixed Reality) y, a continuación, haz clic en el botón **Clone** (Clonar) para abrir la ventana Clone Profile (Clonar perfil):

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-1.png)

En la ventana Clone Profile (Clonar perfil), haz clic en el botón **Clone** (Clonar) para crear una copia modificable de **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-2.png)

Ahora, el perfil del observador de malla de reconocimiento espacial recién creado se asigna automáticamente al perfil del sistema de reconocimiento espacial:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. Cambiar la visibilidad de la malla de reconocimiento espacial

En **Spatial Mesh Observer Settings** (Configuración del observador de malla espacial), cambia **Display Option** (Opción de visualización) a **Occlusion** (Oclusión) para que la malla de asignación espacial sea invisible y, al mismo tiempo, funcional:

![mrlearning-base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> Aunque la malla de asignación espacial no está visible, sigue existiendo y es funcional. Por ejemplo, los hologramas situados detrás de la malla de asignación espacial, como un holograma detrás de un muro físico, no estarán visibles.

Acabas de aprender a modificar una configuración en el perfil de MRTK. Como puedes ver, para personalizar la configuración de MRTK, debes crear copias de los perfiles predeterminados. Dado que los perfiles predeterminados no son editables, siempre los tendrás como referencia si quieres revertir la configuración predeterminada. Para obtener más información sobre los perfiles de MRTK y su arquitectura, puedes visitar la [guía de configuración de perfiles de Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="hand-tracking-gestures-and-interactable-buttons"></a>Botones de interacción y gestos de seguimiento de la mano

En esta sección, aprenderás a usar el seguimiento de manos para presionar un botón y desencadenar eventos para provocar una acción al presionar el botón.

En este ejemplo concreto, se muestra cómo cambiar el color de un cubo cuando se presiona el botón y cambiarlo a su color original cuando se suelta. Sin embargo, puedes seguir estos mismos principios para crear otros eventos.

Los principales pasos que se deben seguir para cambiar el color del cubo son los siguientes:

1. Agregar un objeto prefabricado de botón presionable a la escena
2. Agregar un cubo a la escena
3. Configurar el tipo de evento InteractableOnPressReceiver
4. Configurar el cubo para recibir el evento On Press (Al presionar)
5. Definir la acción que desencadenará el evento On Press (Al presionar)
6. Configurar el cubo para recibir el evento On Release (Al soltar)
7. Definir la acción que desencadenará el evento On Release (Al soltar)
8. Probar el botón mediante la simulación en el editor

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a>1. Agregar un objeto prefabricado de botón presionable a la escena

> [!TIP]
> Un <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">objeto prefabricado</a> es un objeto GameObject preconfigurado almacenado como un recurso de Unity que se puede reutilizar en todo el proyecto.

En la **ventana del proyecto**, busca **PressableButtonHoloLens2** para buscar el objeto prefabricado que usarás en este ejemplo:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-1.png)

En el resultado de la **búsqueda**, selecciona el objeto prefabricado **PressableButtonHoloLens2** y **arrástralo** a la ventana **Hierarchy** (Jerarquía) para agregarlo a la escena:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> Para mostrar la escena tal y como se muestra en la imagen siguiente, haz doble clic en el objeto PressableButtonHoloLens2 en la ventana Hierarchy (Jerarquía) para ponerlo en el foco y, a continuación, usa el <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">gizmo de escena</a>, situado en la esquina superior derecha de la ventana Scene (Escena) para ajustar el ángulo de visualización a lo largo del eje Z.

Con el objeto **PressableButtonHoloLens2** todavía seleccionado, en la ventana **Inspector**:

* Cambia su **posición** de transformación para que se coloque delante de la cámara, que está situada en el origen; por ejemplo, x = 0, y = 0 y z = 0,5.

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> En general, 1 unidad de posición en Unity equivale, aproximadamente, a 1 metro en el mundo físico. Sin embargo, existen excepciones; por ejemplo, cuando los objetos son elementos secundarios de los objetos con escala.

### <a name="2-add-a-cube-to-the-scene"></a>2. Agregar un cubo a la escena

Haz clic con el botón derecho en una zona vacía dentro de la ventana Hierarchy (Jerarquía) y selecciona **3D Object** > **Cube** (Objeto 3D > Cubo) para agregar un cubo a la escena:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-1.png)

Con el objeto **Cube** todavía seleccionado, en la ventana **Inspector**:

* Cambia su **posición** de transformación para que esté cerca del botón que se pueda presionar, pero no se solape con él; por ejemplo, x = 0, y = 0,04 y z = 0,5
* Cambia su **escala** de transformación a un tamaño adecuado; por ejemplo, x = 0,02, y = 0,02 y z = 0,02.

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a>3. Configurar el tipo de evento InteractableOnPressReceiver

En la ventana Hierarchy (Jerarquía), selecciona el objeto **PressableButtonHoloLens2** y, a continuación, en la ventana **Inspector**, en el **menú de hamburguesa**, selecciona **Collapse All Components** (Contraer todos los componentes) para obtener una visión general de todos los componentes de este objeto:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-1.png)

Expande el componente **Interactable (Script)** (Interactuable [script]) y, a continuación, busca y expande la sección **Events** > **Receivers** (Eventos > Receptores):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-2.png)

Haz clic en el botón **Add Event** (Agregar evento) para crear un nuevo receptor de eventos del tipo **InteractableOnPressReceiver**:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> El tipo de receptor de eventos InteractableOnPressReceiver permite que el botón responda a un evento presionado cuando una mano con seguimiento presiona el botón.

En el caso del receptor de eventos recién creado, cambia **Interaction Filter** (Filtro de interacción) a **Near and Far** (Cerca y lejos):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step3-4.png)

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a>4. Configurar el cubo para recibir el evento On Press (Al presionar)

En la ventana Hierarchy (Jerarquía), **haz clic y arrastra** **Cube** (Cubo) al campo de objeto **Event Properties** (Propiedades de evento) para el evento **On Press ()** (Al presionar []) para asignar el cubo como receptor del evento On Press () (Al presionar []):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a>5. Definir la acción que desencadenará el evento On Press (Al presionar)

Haz clic en la lista desplegable de acción, asignada actualmente a **No Function** (Ninguna función) y selecciona **MeshRenderer** > **Material** para establecer la propiedad de material del cubo que se cambiará cuando se desencadene el evento On Press () (Al presionar []):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-1.png)

Haz clic en el pequeño icono de **círculo** situado junto al campo de material, actualmente con el valor**None (Material)** Ninguno (material), para abrir la ventana Select Material (Seleccionar material):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-2.png)

En la ventana Select Material (Seleccionar material), **busca** **MRTK_Standard** y selecciona un material adecuado; por ejemplo, **MRTK_Standard_Cyan** para que el color del cubo cambie a cian al presionar el botón:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a>6. Configurar el cubo para recibir el evento On Release (Al soltar)

**Repite** el paso 4 para el evento On Release (Al soltar) para asignar el **cubo** como receptor del evento **On Release ()** (Al soltar []).

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a>7. Definir la acción que desencadenará el evento On Release (Al soltar)

**Repite** el paso 5 para el evento On Release (Al soltar), pero elige el material **MRTK_Standard_LightGray** para que el color del cubo vuelva a su gris claro original al soltar el botón:

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a>8. Probar el botón mediante la simulación en el editor

Presiona el botón **Play** (Jugar) para entrar en el modo de juego y usa la simulación de entrada del editor para probar el botón que acabas de configurar.

Botón sin presionar (barra espaciadora + rueda hacia atrás del ratón):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-1.png)

Botón presionado (barra espaciadora + rueda hacia adelante del ratón):

![mrlearning-base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> Para obtener información sobre cómo usar la simulación de entrada del editor, puedes consultar la guía [Uso de la simulación de entrada de mano en el editor para probar una escena](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) del [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>Creación de un panel de botones con la colección de objetos de cuadrícula de MRTK

En esta sección, aprenderás a alinear automáticamente varios botones en una interfaz de usuario nueva mediante la herramienta GridObjectCollection de MRTK.

En este ejemplo concreto se muestra cómo crear un panel con cinco botones alineados horizontalmente. Sin embargo, puedes seguir estos mismos principios para crear diseños.

Los principales pasos que debes seguir para lograrlo son:

1. Asignar los objetos de botón a un objeto principal
2. Agregar y configurar el componente Grid Object Collection (Script) (Colección de objetos de cuadrícula [script])
3. Probar los botones mediante la simulación en el editor

### <a name="1-parent-the-button-objects-to-a-parent-object"></a>1. Asignar los objetos de botón a un objeto principal

Haz clic con el botón derecho en una zona vacía dentro de la ventana Hierarchy (Jerarquía) y selecciona **Create Empty** (Crear objeto vacío):

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-1.png)

Haz clic con el botón derecho en el objeto que acabas de crear, selecciona **Rename** (Cambiar nombre) y asígnale un nombre adecuado; por ejemplo, **ButtonCollection**:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-2.png)

Selecciona el objeto **PressableButtonHoloLens2** y **arrástralo** encima del objeto **ButtonCollection** para convertirlo en un elemento secundario de este objeto:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-3.png)

Haz clic con el botón derecho en el objeto **PressableButtonHoloLens2** y selecciona **Duplicar** para crear una copia de este:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step1-4.png)

**Repite** este paso cuatro veces más hasta que tengas un total de cinco objetos PressableButtonHoloLens2.

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2. Agregar y configurar el componente Grid Object Collection (Script) (Colección de objetos de cuadrícula [script])

Con el objeto ButtonCollection seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, haz clic en el botón **Add Component** (Agregar componente) y, a continuación, busca y selecciona **Grid Object Collection** (Colección de objetos de cuadrícula) para agregar un componente Grid Object Collection (Script) (Colección de objetos de cuadrícula [script]) al objeto ButtonCollection:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-1.png)

Configura el componente Grid Object Collection (Script) (Colección de objetos de cuadrícula [script]) como se indica a continuación:

* Cambia **Num Rows** (Número de filas) a 1 para que todos los botones estén alineados en una sola fila.
* Cambia **Cell Width** (Ancho de celda) a 0,05 para espaciar los botones dentro de la fila.

A continuación, haz clic en el botón **Actualizar colección** para aplicar la nueva configuración:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> Los cambios de configuración que acabas de aplicar representan los cambios mínimos necesarios para lograr el objetivo de colocar los botones en una sola fila. Sin embargo, en proyectos futuros, en función de factores como, por ejemplo, la orientación de los objetos principales y secundarios, es posible que necesites ajustar otras opciones de configuración, como, por ejemplo, el tipo de orientación. Para obtener más información sobre la colección de objetos de cuadrícula de MRTK, puedes visitar la guía de [scripts de colección de objetos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) del [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

Con el objeto ButtonCollection aún seleccionado en la ventana Hierarchy (Jerarquía), en la ventana Inspector, cambia la **posición** de transformación del objeto ButtonCollection para que los objetos de botón secundarios se sitúen delante de la cámara, que se encuentra en el origen; por ejemplo, x = 0, y = 0 y z = 0,5:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> La primera vez que se agregó el objeto prefabricado PressableButtonHoloLens2 a la escena en la sección [Botones de interacción y gestos de seguimiento de la mano](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) anterior, lo colocaste delante de la cámara. Sin embargo, dado que la colección de objetos de cuadrícula controla la posición de sus objetos secundarios inmediatos, la posición Z de los objetos secundarios de PressableButtonHoloLens2 se restableció a 0 de acuerdo con la distancia predeterminada de la colección de objetos de cuadrícula del valor principal de 0. Por este motivo, y para mantener organizada la relación de posición entre el objeto principal y el secundario, hemos movido la posición del objeto ButtonCollection hacia adelante en lugar de configurar la distancia del valor principal para que mueva los objetos secundarios de PressableButtonHoloLens2 hacia adelante.

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a>3. Probar los botones mediante la simulación en el editor

Presiona el botón Play (Jugar) para entrar en el modo de juego y usa la simulación de entrada del editor para probar cada uno de los botones del panel de botones que acabas de crear:

![mrlearning-base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> Actualmente, cuando se presiona cualquiera de los cinco botones, el color del cubo cambia a cian. Para que la experiencia sea más interesante, usa lo que acabas de aprender para configurar cada botón y cambiar el cubo a otro color.

## <a name="adding-text-into-your-scene"></a>Adición de texto a la escena

En esta sección, aprenderás a agregar texto a tus experiencias de realidad mixta con TextMesh Pro de Unity, que preparaste en la sección [Importación de recursos esenciales de TextMesh Pro](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) del tutorial anterior.

En este ejemplo concreto, agregarás una etiqueta sencilla bajo la colección de botones que creaste en la sección anterior.

Haz clic con el botón derecho en el objeto ButtonCollection y selecciona **3D Object** > **Text - TextMeshPro** (Objeto 3D > Texto - TextMeshPro) para crear un objeto TextMeshPro como elemento secundario del objeto ButtonCollection:

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-1.png)

Con el objeto TextMeshPro que acabas de crear, denominado Text (TMP), aún seleccionado, en la ventana Inspector, cambia su posición y tamaño para que la etiqueta se coloque estratégicamente bajo la colección de botones; por ejemplo:

* Cambia el valor de **Pos Y** de transformación de rectángulo a 0,0425.
* Cambia el valor **Width** (Ancho) de transformación de rectángulo a 0,24.
* Cambia el valor **Height** (Altura) de transformación de rectángulo a 0,024.

A continuación, actualiza el texto para que refleje el propósito de la etiqueta y elige las propiedades de la fuente para que el texto se ajuste a la etiqueta; por ejemplo:

* Cambia el valor **Text** (Texto) de Text Mesh Pro (Script) a Button Collection (Colección de botones).
* Cambia el valor **Font Style** (Estilo de fuente) de Text Mesh Pro (Script) a Bold (Negrita).
* Cambia el valor **Font Size** (Tamaño de fuente) de Text Mesh Pro (Script) a 0,2.
* Cambia el valor **Alignment** (Alineación) de Text Mesh Pro (Script) a Center and Middle (Centro y medio).

![mrlearning-base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a>Enhorabuena

En este tutorial, has aprendido a clonar, personalizar y configurar las opciones de un perfil de MRTK. También has aprendido a interactuar con botones para desencadenar eventos mediante el seguimiento de manos en HoloLens 2. Por último, has aprendido a crear una sencilla interfaz de usuario mediante el componente de colección de objetos de cuadrícula de MRTK y Text Mesh Pro de Unity.

[Tutorial siguiente: 4. Colocación del contenido dinámico y uso de solucionadores](mrlearning-base-ch3.md)
