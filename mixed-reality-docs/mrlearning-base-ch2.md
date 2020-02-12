---
title: 'Tutoriales de introducción: 3. Crear la interfaz de usuario y configurar el kit de herramientas de realidad mixta'
description: Haz este curso para aprender a implementar Azure Face Recognition dentro de una aplicación de realidad mixta.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: 067832a130f130ffbaa8d455007b8e77e1b13671
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77130720"
---
# <a name="3-creating-user-interface-and-configure-mixed-reality-toolkit"></a>3. crear la interfaz de usuario y configurar el kit de herramientas de realidad mixta
<!-- TODO: Consider renaming to 'Configuring Mixed Reality Toolkit profiles and creating user interfaces' -->

En el tutorial anterior, aprendió sobre algunas de las funcionalidades que el kit de herramientas de realidad mixta (MRTK) tiene que ofrecer al iniciar su primera aplicación para HoloLens 2. En este tutorial aprenderá a crear y organizar botones junto con paneles de texto de la interfaz de usuario y a usar interacción predeterminada (Touch) para interactuar con cada botón. También explorarás la incorporación de acciones y efectos sencillos, como cambiar el tamaño, el sonido y color de los objetos. Este módulo presentará conceptos básicos sobre la modificación de perfiles de MRTK, empezando por desactivar la visualización de la malla de [asignación espacial](spatial-mapping.md) .

## <a name="objectives"></a>Objetivos

* Personalizar y configurar los perfiles de Mixed Reality Toolkit
* Interacción con hologramas mediante elementos y botones de la interfaz de usuario
* Entrada e interacciones básicas del seguimiento de la mano

## <a name="how-to-configure-the-mixed-reality-toolkit-profiles-change-spatial-awareness-display-option"></a>Configuración de los perfiles de kit de herramientas de realidad mixta (cambiar la opción de visualización de reconocimiento espacial)
<!-- TODO: Consider renaming to 'How to customize the MRTK profiles' -->

En esta sección, aprenderá a personalizar y configurar los perfiles predeterminados de MRTK.

En este ejemplo concreto se muestra cómo ocultar la malla de reconocimiento espacial cambiando la configuración del observador de la malla espacial. Sin embargo, puede seguir estos mismos principios para personalizar cualquier configuración o valor en los perfiles de MRTK.

Los principales pasos que se deben seguir para ocultar la malla de reconocimiento espacial son:

1. Clonar el perfil de configuración predeterminado
2. Habilitación del sistema de reconocimiento espacial
3. Clonar el perfil del sistema de reconocimiento espacial predeterminado
4. Clonar el perfil de observador de la malla de reconocimiento espacial predeterminado
5. Cambiar la visibilidad de la malla de reconocimiento espacial

> [!NOTE]
> De forma predeterminada, los perfiles de MRTK no son editables. Estas son las plantillas de perfil predeterminadas que se deben clonar antes de que se puedan editar. Hay varias capas anidadas de perfiles. Por lo tanto, es habitual clonar y editar varios perfiles al configurar uno o varios valores.

### <a name="1-clone-the-default-configuration-profile"></a>1. clonar el perfil de configuración predeterminado

> [!NOTE]
> El perfil de configuración es el perfil de nivel superior. Por lo tanto, para poder editar cualquier otro perfil, primero debe clonar el perfil de configuración.

Con el objeto **MixedRealityToolkit** seleccionado en la ventana jerarquía, en la ventana del inspector, haga clic en el botón **copiar & personalizar** para abrir la ventana Perfil de clonación:

![mrlearning: base](images/mrlearning-base/tutorial2-section1-step1-1.png)

En la ventana clonar perfil, haga clic en el botón **clonar** para crear una copia modificable de la **DefaultHololens2ConfigurationProfile**:

![mrlearning: base](images/mrlearning-base/tutorial2-section1-step1-2.png)

El perfil de configuración recién creado se asigna ahora como el perfil de configuración de la escena:

![mrlearning: base](images/mrlearning-base/tutorial2-section1-step1-3.png)

En el menú de Unity, seleccione **archivo** > **Guardar** para guardar la escena.

> [!TIP]
> Recuerde guardar el trabajo en el tutorial.

### <a name="2-enable-the-spatial-awareness-system"></a>2. habilitar el sistema de reconocimiento espacial

Con el objeto **MixedRealityToolkit** todavía seleccionado en la ventana jerarquía, en la ventana inspector, seleccione la pestaña **reconocimiento espacial** y active la casilla **Habilitar sistema de reconocimiento espacial** :

![mrlearning: base](images/mrlearning-base/tutorial2-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a>3. clonar el perfil del sistema de reconocimiento espacial predeterminado

En la pestaña **reconocimiento espacial** , haga clic en el botón **clonar** para abrir la ventana Perfil de clonación:

![mrlearning: base](images/mrlearning-base/tutorial2-section1-step3-1.png)

En la ventana clonar perfil, haga clic en el botón **clonar** para crear una copia modificable de la **DefaultMixedRealitySpatialAwarenessSystemProfile**:

![mrlearning: base](images/mrlearning-base/tutorial2-section1-step3-2.png)

Ahora el perfil del sistema de reconocimiento espacial recién creado se asigna automáticamente al perfil de configuración:

![mrlearning: base](images/mrlearning-base/tutorial2-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a>4. clonar el perfil de observador de la malla de reconocimiento espacial predeterminado

Con la pestaña **reconocimiento espacial** todavía seleccionada, expanda la sección observador de la **malla espacial de Windows Mixed Reality** y haga clic en el botón **clonar** para abrir la ventana Perfil de clonación:

![mrlearning: base](images/mrlearning-base/tutorial2-section1-step4-1.png)

En la ventana clonar perfil, haga clic en el botón **clonar** para crear una copia modificable de la **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:

![mrlearning: base](images/mrlearning-base/tutorial2-section1-step4-2.png)

El perfil de observador de la malla de reconocimiento espacial recién creado se asigna automáticamente al perfil del sistema de reconocimiento espacial:

![mrlearning: base](images/mrlearning-base/tutorial2-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a>5. cambiar la visibilidad de la malla de reconocimiento espacial

En la **configuración del observador de la malla espacial**, cambie la **opción de visualización** a **oclusión** para que la malla de asignación espacial sea invisible mientras sigue funcionando:

![mrlearning: base](images/mrlearning-base/tutorial2-section1-step5-1.png)

> [!NOTE]
> Aunque la malla de asignación espacial no es visible, sigue estando presente y funcional. Por ejemplo, los hologramas detrás de la malla de asignación espacial, como un holograma detrás de un muro física, no estarán visibles.

Acabas de aprender a modificar una configuración en el perfil de MRTK. Como puede ver, para personalizar la configuración de MRTK, primero debe crear copias de los perfiles predeterminados. Dado que los perfiles predeterminados no son editables, siempre tendrá como referencia si desea revertir a la configuración predeterminada. Para obtener más información acerca de los perfiles de MRTK y su arquitectura, puede visitar la guía de configuración del perfil de el [Kit de herramientas de realidad mixta](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="hand-tracking-gestures-and-interactable-buttons"></a>Gestos de seguimiento de mano y botones interactivos

En esta sección, aprenderá a usar el seguimiento de manos para presionar un botón y desencadenar eventos para producir una acción cuando se presiona el botón.

En este ejemplo concreto se muestra cómo cambiar el color de un cubo cuando se presiona el botón y cambiarlo a su color original cuando se suelta el botón. Sin embargo, puede seguir estos mismos principios para crear otros eventos.

Los principales pasos que se deben seguir para cambiar el color del cubo son:

1. Agregar un botón que se pueda presionar recurso prefabricado a la escena
2. Agregar un cubo a la escena
3. Configurar el tipo de evento InteractableOnPressReceiver
4. Configurar el cubo para recibir el evento on press
5. Definir la acción que va a desencadenar el evento on press
6. Configurar el cubo para recibir el evento on Release
7. Definir la acción que va a desencadenar el evento on Release
8. Probar el botón mediante la simulación en el editor

### <a name="1-add-a-pressable-button-prefab-to-the-scene"></a>1. agregar un botón que se pueda presionar recurso prefabricado a la escena

> [!TIP]
> Un <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">recurso prefabricado</a> es un GameObject preconfigurado que se almacena como un recurso de Unity y se puede reutilizar en todo el proyecto.

En la **ventana de proyecto**, busque **PressableButtonHoloLens2** para buscar el recurso prefabricado que va a usar en este ejemplo:

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step1-1.png)

En el resultado de la **búsqueda** , seleccione **PressableButtonHoloLens2** recurso prefabricado y **arrástrelo** a la ventana de la **jerarquía** para agregarlo a la escena:

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step1-2.png)

> [!TIP]
> Para mostrar la escena tal como se muestra en la imagen siguiente, haga doble clic en el objeto PressableButtonHoloLens2 en la ventana de jerarquía para ponerlo en el foco y, a continuación, use el Gizmo de la <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">escena</a>, situado en la esquina superior derecha de la ventana de la escena, para ajustar el ángulo de visualización a lo largo del eje Z hacia delante.

Con el objeto PressableButtonHoloLens2 aún seleccionado, en la ventana del **Inspector** :

* Cambiar su **posición** de transformación para colocarla delante de la cámara, que se coloca en el origen, por ejemplo, x = 0, y = 0 y z = 0,5

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step1-3.png)

> [!NOTE]
> En general, 1 unidad de posición en Unity es aproximadamente equivalente a 1 metro en el mundo físico. Sin embargo, hay excepciones para esto, por ejemplo, cuando los objetos son elementos secundarios de objetos escalados.

### <a name="2-add-a-cube-to-the-scene"></a>2. agregar un cubo a la escena

Haga clic con el botón secundario en una zona vacía dentro de la ventana de jerarquía y seleccione **objeto 3d** > **cubo** para agregar un cubo a la escena:

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step2-1.png)

Con el objeto de cubo todavía seleccionado, en la ventana del **Inspector** :

* Cambie su **posición** de transformación para que se encuentre cerca del botón que se pueda presionar, pero no se superponga con él, por ejemplo, x = 0, y = 0,04 y z = 0,5
* Cambie la **escala** de transformación a un tamaño adecuado, por ejemplo, x = 0,02, y = 0,02 y z = 0,02

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step2-2.png)

### <a name="3-configure-the-interactableonpressreceiver-event-type"></a>3. configurar el tipo de evento InteractableOnPressReceiver

Con el objeto PressableButtonHoloLens2 seleccionado en la ventana jerarquía, en el **menú**de la ventana del **Inspector** , seleccione **contraer todos los componentes** para obtener una visión general de todos los componentes de este objeto:

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step3-1.png)

Expanda el componente **interactuable (Script)** y, a continuación, busque y expanda la sección **eventos** > **receptores** :

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step3-2.png)

Para el tipo de receptor de eventos **InteractableOnPressReceiver**, cambie el **filtro de interacción** a **Near y Far**:

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step3-3.png)

> [!NOTE]
> El tipo de receptor de eventos denominado InteractableOnPressReceiver permite al botón responder a un evento presionado cuando una mano a la que se hace un seguimiento presiona el botón.

### <a name="4-configure-the-cube-to-receive-the-on-press-event"></a>4. configurar el cubo para recibir el evento on press

En la ventana jerarquía, **haga clic y arrastre** el **cubo** al campo objeto de **propiedades de evento** para el evento **on press ()** para asignar el cubo como receptor del evento on press ():

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step4-1.png)

### <a name="5-define-the-action-to-be-triggered-by-the-on-press-event"></a>5. definir la acción que va a desencadenar el evento on press

Haga clic en la lista desplegable acción, actualmente **no hay ninguna función**asignada y seleccione **MeshRenderer** ** > material material para** establecer la propiedad material del cubo que se cambiará cuando se desencadene el evento on press ():

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step5-1.png)

Haga clic en el icono de **círculo** pequeño situado junto al campo material, actualmente rellenado con **ninguno (material)** , para abrir la ventana Seleccionar material:

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step5-2.png)

En la ventana Seleccionar material, **busque** **MRTK_Standard** y seleccione un material adecuado, por ejemplo, **MRTK_Standard_Cyan** para que el color del cubo cambie a Aguamarina cuando se presione el botón:

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step5-3.png)

### <a name="6-configure-the-cube-to-receive-the-on-release-event"></a>6. configurar el cubo para recibir el evento on Release

**Repetir** Paso 4 para el evento on Release para asignar el cubo como receptor del evento on Release ().

### <a name="7-define-the-action-to-be-triggered-by-the-on-release-event"></a>7. definir la acción que va a desencadenar el evento on Release

**Repetir** Paso 5 para el evento on release, pero elija el **MRTK_Standard_LightGray** material para que el color del cubo vuelva a su color gris claro original al soltar el botón:

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step7-1.png)

### <a name="8-test-the-button-using-the-in-editor-simulation"></a>8. probar el botón mediante la simulación en el editor

Presione el botón **reproducir** para entrar en el modo de juego y use la simulación de entrada del editor para probar el botón que acaba de configurar.

Botón no presionado (barra espaciadora + rueda hacia atrás del mouse):

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step8-1.png)

Botón presionado (barra espaciadora + rueda de desplazamiento hacia delante):

![mrlearning: base](images/mrlearning-base/tutorial2-section2-step8-2.png)

> [!TIP]
> Para obtener información sobre cómo usar la simulación de entrada del editor, puede consultar el [uso de la simulación de entrada de la mano del editor para probar una](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guía de escenas en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="creating-a-panel-of-buttons-using-mrtks-grid-object-collection"></a>Creación de un panel de botones con la colección de objetos de cuadrícula de MRTK

En esta sección, aprenderá a alinear automáticamente varios botones en una interfaz de usuario ordenada mediante la herramienta de colección de objetos de cuadrícula de MRTK.

En este ejemplo concreto se muestra cómo crear un panel con cinco botones alineados horizontalmente. Sin embargo, puede seguir estos mismos principios para crear otros diseños.

Los principales pasos que se deben seguir para lograrlo son:

1. Primaria de los objetos de botón en un objeto primario
2. Agregar y configurar el componente de colección de objetos de cuadrícula (Script)
3. Prueba de los botones mediante la simulación en el editor

### <a name="1-parent-the-button-objects-to-a-parent-object"></a>1. primaria de los objetos de botón en un objeto primario

Haga clic con el botón derecho en una zona vacía dentro de la ventana de jerarquía y seleccione **crear vacío**:

![mrlearning: base](images/mrlearning-base/tutorial2-section3-step1-1.png)

Haga clic con el botón derecho en el objeto recién creado, seleccione **cambiar nombre**y asígnele un nombre adecuado, por ejemplo, **ButtonCollection**:

![mrlearning: base](images/mrlearning-base/tutorial2-section3-step1-2.png)

Seleccione el objeto **PressableButtonHoloLens2** y **arrástrelo** sobre el objeto **ButtonCollection** para convertirlo en un elemento secundario del objeto ButtonCollection:

![mrlearning: base](images/mrlearning-base/tutorial2-section3-step1-3.png)

Haga clic con el botón secundario en el objeto **PressableButtonHoloLens2** y seleccione **duplicar** para crear una copia de él:

![mrlearning: base](images/mrlearning-base/tutorial2-section3-step1-4.png)

**Repita** este paso cuatro veces más hasta que tenga un total de cinco objetos PressableButtonHoloLens2.

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2. agregar y configurar el componente de colección de objetos de cuadrícula (Script)

Con el objeto ButtonCollection seleccionado en la ventana jerarquía, en la ventana inspector, haga clic en el botón **Agregar componente** , busque y seleccione **colección de objetos de cuadrícula** para agregar un componente de colección de objetos de cuadrícula (Script) al objeto ButtonCollection:

![mrlearning: base](images/mrlearning-base/tutorial2-section3-step2-1.png)

Configure la colección de objetos de cuadrícula (Script) de la siguiente manera:

* Cambie **NUM Rows** a 1 para que todos los botones estén alineados en una sola fila.
* Cambiar el **ancho de celda** a 0,05 para descartar los botones de la fila

A continuación, haga clic en el botón **Actualizar colección** para aplicar la nueva configuración:

![mrlearning: base](images/mrlearning-base/tutorial2-section3-step2-2.png)

> [!NOTE]
> Los cambios de configuración que acaba de aplicar representan los cambios mínimos necesarios para lograr el objetivo de colocar los botones en una sola fila. Sin embargo, en proyectos futuros, en función de factores como, por ejemplo, la orientación de los objetos primarios y secundarios, es posible que necesite ajustar otras opciones de configuración como, por ejemplo, el tipo de orientación. Para obtener más información sobre la colección de objetos de cuadrícula de MRTK, puede visitar la guía de [scripts de colección de objetos](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectCollection.html#object-collection-scripts) en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

Con el objeto ButtonCollection todavía seleccionado en la ventana de la jerarquía, en la ventana del inspector, cambie la **posición** de transformación del objeto ButtonCollection para que sus objetos de botón secundarios se coloquen delante de la cámara, que se coloca en el origen, por ejemplo, x = 0, y = 0 y z = 0,5:

![mrlearning: base](images/mrlearning-base/tutorial2-section3-step2-3.png)

> [!NOTE]
> La primera vez que se agregó el recurso prefabricado PressableButtonHoloLens2 a la escena en la sección [gestos de seguimiento de mano y botones interactuables](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) anteriores, se coloca delante de la cámara. Sin embargo, dado que la colección de objetos Grid controla su posición de los objetos secundarios inmediatos, la posición Z de los objetos secundarios PressableButtonHoloLens2 se restableció a 0 según la distancia predeterminada de la colección de objetos de cuadrícula del valor 0. Esto, y para mantener la relación posicional de elementos primarios y secundarios organizada, es el motivo por el que se ha movido la posición del objeto primario ButtonCollection hacia delante en lugar de configurar la distancia desde el valor primario para mover los objetos secundarios PressableButtonHoloLens2 hacia delante.

### <a name="3-test-the-buttons-using-the-in-editor-simulation"></a>3. probar los botones mediante la simulación en el editor

Presione el botón reproducir para entrar en el modo de juego y use la simulación de entrada del editor para probar cada uno de los botones de en el panel de botones recién creado:

![mrlearning: base](images/mrlearning-base/tutorial2-section3-step3-1.png)

> [!TIP]
> Actualmente, cuando se presiona cualquiera de los cinco botones, el color del cubo cambia a aguamarina. Para que la experiencia sea más interesante, use lo que acaba de aprender para configurar cada botón y cambiar el cubo a un color diferente.

## <a name="adding-text-into-your-scene"></a>Agregar texto a la escena

En esta sección, aprenderá a agregar texto a sus experiencias de realidad mixta con TextMesh pro de Unity, que preparó en la sección [Import TextMesh Pro Essential Resources](mrlearning-base-ch1.md#import-textmesh-pro-essential-resources) del tutorial anterior.

En este ejemplo concreto, agregará una etiqueta simple debajo de la colección de botones que creó en la sección anterior.

Haga clic con el botón derecho en el objeto ButtonCollection y seleccione **objeto 3d** > **Text-TextMeshPro** para crear un objeto TextMeshPro como elemento secundario del objeto ButtonCollection:

![mrlearning: base](images/mrlearning-base/tutorial2-section4-step1-1.png)

Con el objeto TextMeshPro que se acaba de crear, denominado Text (TMP), aún seleccionado, en la ventana del inspector, cambie su posición y tamaño para que la etiqueta se coloque en el interior de la colección de botones, por ejemplo:

* Cambie la transformación de rectángulo **Y** a-0,0425
* Cambiar el **ancho** de la transformación Rect a 0,24
* Cambiar el **alto** de la transformación Rect a 0,024

A continuación, actualice el texto para que refleje el contenido de la etiqueta y elija Propiedades de fuente para que el texto quepa dentro de la etiqueta, por ejemplo:

* Cambiar el texto de la malla de texto Pro ( **script) a** la colección de botones
* Cambiar el **estilo de fuente** de la malla de texto Pro (Script) a negrita
* Cambiar el **tamaño de fuente** de la malla de texto Pro (Script) a 0,2
* Cambiar la **alineación** de la malla de texto Pro (Script) al centro y el medio

![mrlearning: base](images/mrlearning-base/tutorial2-section4-step1-2.png)

## <a name="congratulations"></a>Enhorabuena

En este tutorial, aprendió a clonar, personalizar y configurar una configuración de Perfil de MRTK. También aprendió a interactuar con los botones para desencadenar eventos mediante las manos del seguimiento en HoloLens 2. Por último, aprendió a crear una interfaz de usuario simple mediante el componente de colección de objetos de cuadrícula de MRTK y el pro de malla de texto de Unity.

[Siguiente tutorial: 4. colocar contenido dinámico y usar solucionadores](mrlearning-base-ch3.md)
