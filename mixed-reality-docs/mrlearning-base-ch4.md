---
title: 'Tutoriales de introducción: 5. Interactuar con objetos 3D'
description: ''
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.openlocfilehash: a1b26d56b4693ef23f2d77ba53e0961693489a3a
ms.sourcegitcommit: cc61f7ac08f9ac2f2f04e8525c3260ea073e04a7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77130286"
---
# <a name="5-interacting-with-3d-objects"></a>5. interactuar con objetos 3D

En este tutorial, obtendrá información sobre el contenido 3D básico y la experiencia del usuario, como la organización de objetos 3D como parte de una colección, los cuadros de límite para la manipulación básica, la interacción aproximada y lejana, y los gestos táctiles y de agarre con seguimiento manual.

## <a name="objectives"></a>Objetivos

* Crear un panel de objetos 3D que se usará para los otros objetivos de aprendizaje
* Implementar rectángulos de selección
* Configurar objetos 3D para la manipulación básica, como movimiento, rotación y escala
* Explorar la interacción próxima y lejana
* Más información acerca de los gestos de seguimiento de la mano, como captar y tocar

## <a name="importing-the-tutorial-assets"></a>Importar los activos del tutorial

Descargue e importe el paquete personalizado de Unity:

* [MRTK. HoloLens2. Unity. tutoriales. assets. GettingStarted. 2.2.0.0. unitypackage Tools](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.2.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.2.0.0.unitypackage)

Después de haber importado los recursos del tutorial, la ventana del proyecto debería tener un aspecto similar al siguiente:

![mrlearning: base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, puede consultar las instrucciones para [importar el kit de herramientas de realidad mixta](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit) .

## <a name="decluttering-the-scene-view"></a>Desenredo de la vista de escena

Para que resulte más fácil trabajar con la escena, establezca la visibilidad de la **escena** del cubo y los objetos ButtonCollection en OFF; para ello, haga clic en el icono de **ojo** situado a la izquierda de los objetos. Esto oculta el objeto en la ventana de la escena sin cambiar su visibilidad en el juego:

![mrlearning: base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> Para obtener más información sobre los controles de visibilidad de escenas y cómo puede usarlos para optimizar la vista de escenas y el flujo de trabajo, puede visitar la documentación de visibilidad de la <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">escena</a> de Unity.

## <a name="organizing-3d-objects-in-a-collection"></a>Organizar objetos 3D en una colección

En esta sección, creará un panel de objetos 3D que se utilizará al explorar varias formas de interactuar con objetos 3D en las siguientes secciones de este tutorial. En concreto, configurará los objetos 3D para que se coloquen en una cuadrícula de 3 x 3.

Del mismo modo que cuando se [crea un panel de botones](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), los principales pasos que se deben seguir para lograrlo son:

1. Parent los objetos 3D a un objeto primario
2. Agregar y configurar el componente de colección de objetos de cuadrícula (Script)

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a>1. Parent los objetos 3D a un objeto primario

En la ventana jerarquía, **cree un objeto vacío**, asígnele un nombre adecuado, por ejemplo, **3DObjectCollection**, y colóquelo en una ubicación adecuada, por ejemplo, X = 0, y =-0,2, Z = 2.

En la ventana del proyecto, vaya a **activos** > **MRTK. Tutoriales. GettingStarted** > **Prefabs**y, a continuación, el **elemento primario** del Prefabs siguiente al **3DObjectCollection**:

* Quesos
* CoffeeCup
* EarthCore
* Octa
* Platonic
* Módulo

![mrlearning: base](images/mrlearning-base/tutorial4-section3-step1-1.png)

En la ventana de jerarquía, **cree tres cubos** como objetos secundarios de **3DObjectCollection** y establezca su **escala** de transformación en X = 0,15, y = 0,15, Z = 0,15:

![mrlearning: base](images/mrlearning-base/tutorial4-section3-step1-2.png)

<!-- TODO: Finish -->
> [!TIP]
> Para obtener un recordatorio sobre cómo realizar los pasos indicados anteriormente, puede consultar el tutorial creación de la [interfaz de usuario y configuración del kit de herramientas de realidad mixta](mrlearning-base-ch2.md) .

Cambie la posición de los cubos para que pueda ver cada cubo:

![mrlearning: base](images/mrlearning-base/tutorial4-section3-step1-3.png)

En la ventana del proyecto, vaya a **activos** > **MixedRealityToolkit. SDK** > **StandardAssets** > **material** para ver los materiales proporcionados con el MRTK.

**Haga clic y arrastre** un material adecuado a la propiedad 0 del elemento de **materiales** del representador de la malla del cubo, por ejemplo:

* MRTK_Standard_GlowingCyan
* MRTK_Standard_GlowingOrange
* MRTK_Standard_Green:

![mrlearning: base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2. agregar y configurar el componente de colección de objetos de cuadrícula (Script)

Agregue un componente de la **colección de objetos de cuadrícula (Script)** al objeto 3DObjectCollection y configúrelo de la siguiente manera:

* Cambie **tipo de ordenación** a orden secundario para asegurarse de que los objetos secundarios se ordenan en el orden en el que los colocó en el objeto primario.

A continuación, haga clic en el botón **Actualizar colección** para aplicar la nueva configuración:

![mrlearning: base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a>Manipular objetos 3D

En esta sección, agregará la capacidad de manipular todos los objetos 3D del panel que creó en la sección anterior. Además, en el caso de los objetos recurso prefabricado, permitirá que los usuarios accedan a los objetos y los capten con manos con seguimiento. A continuación, explorará algunos comportamientos de manipulación que puede aplicar a los objetos.

Los principales pasos que se deben seguir para lograrlo son:

1. Agregar el componente de controlador de manipulación (Script) a todos los objetos
2. Agregar el componente de captura de interacción cercana (Script) a los objetos recurso prefabricado
3. Configurar el componente de controlador de manipulación (Script)

> [!IMPORTANT]
> Para poder **manipular un objeto**, el objeto debe tener los siguientes componentes:
>
> * Componente de **Colisionador** , por ejemplo, un Colisionador de caja
> * Componente de **controlador de manipulación (Script)**
>
> Para poder **manipular** y **captar un objeto con manos sometidas a seguimiento**, el objeto debe tener los siguientes componentes:
>
> * Componente de **Colisionador** , por ejemplo, un Colisionador de caja
> * Componente de **controlador de manipulación (Script)**
> * Componente de captura de la **interacción cercana (Script)**

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a>1. Agregue el componente de controlador de manipulación (Script) a todos los objetos.

En la ventana jerarquía, seleccione el objeto **queso** , mantenga presionada la tecla **MAYÚS** y, a continuación, seleccione el objeto **Cube ()** y agregue el componente de **controlador de manipulación (Script)** a todos los objetos:

![mrlearning: base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> En este tutorial, los colisionadores ya se han agregado a Prefabs. En el caso de los primitivos de Unity, como los objetos de cubo, el componente de Colisionador se agrega automáticamente cuando se crea el objeto. En la imagen anterior, los colisionadores se representan mediante los contornos verdes. Para más información sobre los colisionadores, puede visitar la documentación del <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Colisionador</a> de Unity.

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a>2. agregar el componente de captura de interacción cercana (Script) a los objetos recurso prefabricado

En la ventana de jerarquía, seleccione el objeto de **queso** , mantenga presionada la tecla **MAYÚS** y, a continuación, seleccione el objeto **módulo** y agregue el componente de **captura de interacción cercana (Script)** a todos los objetos:

![mrlearning: base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a>3. configurar el componente de controlador de manipulación (Script)

#### <a name="default-manipulation"></a>Manipulación predeterminada

Para el objeto de **cubo** , deje todas las propiedades en el valor predeterminado para experimentar el comportamiento de manipulación predeterminado:

![mrlearning: base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> Para restablecer los valores predeterminados de un componente, puede seleccionar el icono de configuración del componente y seleccionar restablecer.

#### <a name="restrict-manipulation-to-scale-only"></a>Restringir la manipulación solo a escala

En el caso del objeto **Cube (1)** , cambie el **tipo de manipulación dos manos** a escala para permitir solo al usuario cambiar el tamaño del objeto:

![mrlearning: base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a>Restringir el movimiento a una distancia fija del usuario

Para el objeto **Cube (2)** , cambie **Constraint en** Move para corregir la distancia desde Head, de modo que cuando se mueva el objeto se mantenga a la misma distancia del usuario:

![mrlearning: base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a>Manipulación capturable predeterminada

En el caso de los objetos **queso**, **CoffeCup**y **EarthCore** , deje todas las propiedades en el valor predeterminado para experimentar el comportamiento de la manipulación de capturas predeterminada:

![mrlearning: base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a>Eliminación de la capacidad de manipulación lejana

Para el objeto **OCTA** , desactive la casilla **permitir la manipulación lejana** para que el usuario solo pueda interactuar con el objeto directamente mediante las manos controladas:

![mrlearning: base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a>Hacer que un objeto gire alrededor de su centro

En el caso del objeto **Platonic** , cambie el **modo de rotación de una mano cerca** del **modo de rotación de una mano** hacia la gira sobre el centro de objetos para que sea así cuando el usuario gire el objeto con una mano, se rote alrededor del centro del objeto:

![mrlearning: base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="prevent-movement-after-object-is-released"></a>Impedir el movimiento después de liberar el objeto

En el caso del objeto de **módulo** , cambie el comportamiento de la **versión** a nada para que una vez que el objeto se libere de la mano del usuario, no siga moviendo:

![mrlearning: base](images/mrlearning-base/tutorial4-section4-step3-7.png)

Para obtener más información sobre el componente de controlador de manipulación y sus propiedades asociadas, puede visitar la guía de [control de manipulaciones](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="adding-bounding-boxes"></a>Agregar cuadros de límite

Los cuadros de límite facilitan y simplifican la manipulación de objetos con una mano para una interacción cercana y lejana al proporcionar controladores que se pueden usar para el escalado y la rotación.

En este ejemplo, agregará un cuadro de límite al objeto EarthCore, por lo que ahora se puede interactuar con este objeto con la manipulación de objetos configurada en la sección anterior, así como, escalado y girado con los manipuladores del cuadro de límite.

> [!IMPORTANT]
> Para poder utilizar un cuadro de **límite**, el objeto debe tener los siguientes componentes:
>
> * Componente de **Colisionador** , por ejemplo, un Colisionador de caja
> * Componente de **cuadro de límite (Script)**

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a>1. Agregue el componente de cuadro de límite (Script) al objeto EarthCore

En la ventana del inspector, seleccione el objeto **EarthCore** y agregue el componente del **cuadro de límite (Script)** al objeto EarthCore:

![mrlearning: base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> Las visualizaciones del cuadro de límite se crean en tiempo de ejecución y, por tanto, no son visibles antes de entrar en el modo de juego.

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a>2. visualizar y probar el cuadro de límite mediante la simulación en el editor

Presione el botón reproducir para entrar en el modo de juego. A continuación, mantenga presionada la barra espaciadora para abrir la mano y use el mouse para interactuar con el cuadro de límite:

![mrlearning: base](images/mrlearning-base/tutorial4-section5-step2-1.png)

Para obtener más información acerca del componente de cuadro de límite y sus propiedades asociadas, puede visitar la guía del [cuadro de límite](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) en el portal de [documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="adding-touch-effects"></a>Agregar efectos de toque

En este ejemplo, permitirá que los eventos se desencadenen al tocar un objeto con la mano. En concreto, configurará el objeto OCTA para que se produzca un efecto sonoro cuando el usuario lo toque.

Los principales pasos que se deben seguir para lograrlo son:

1. Agregar un componente de origen de audio al objeto
2. Agregar el componente de la interacción táctil (Script) cerca del objeto
3. Agregar el componente de interacción a mano (Script) al objeto
4. Implementar el evento on Touch Started
5. Prueba de la interacción táctil mediante la simulación en el editor

> [!IMPORTANT]
> Para poder **desencadenar eventos táctiles**, el objeto debe tener los siguientes componentes:
>
> * Componente de **Colisionador** , preferiblemente un Colisionador de caja
> * Componente de la **interacción táctil (Script) cercano**
> * Componente de **toque de interacción manual (Script)**

> [!NOTE]
> El componente de interacción manuscrita de mano (Script) no forma parte de MRTK. Se importó con los recursos de este tutorial y parte originalmente de los ejemplos de Unity de MixedReality Toolkit.

### <a name="1-add-an-audio-source-component-to-the-object"></a>1. agregar un componente de origen de audio al objeto

En la ventana de jerarquía, seleccione el objeto **OCTA** , agregue un componente de **origen de audio** al objeto OCTA y, a continuación, cambie la **mezcla espacial** a 1 para habilitar el audio espacial:

![mrlearning: base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a>2. agregar el componente de la interacción táctil (Script) cerca del objeto

Con el objeto **OCTA** aún seleccionado, agregue el componente de **secuencia de comandos táctil (Script) cerca** de la interacción al objeto OCTA y, a continuación, haga clic en los botones **corregir límites** y **centro de corrección** para actualizar el centro local y las propiedades de los límites del elemento táctil de interacción cercana (Script) para que coincida con BoxCollider:

![mrlearning: base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a>3. agregar el componente de toque de interacción de mano (Script) al objeto

Con el objeto **OCTA** aún seleccionado, agregue el componente de **toque de interacción de mano (Script)** al objeto OCTA:

![mrlearning: base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a>4. implementar el evento on Touch Started

En el componente de toque de interacción de mano (Script), haga clic en el icono de **+** pequeño para crear un nuevo evento **on Touch Started ()** . A continuación, configure el objeto **OCTA** para recibir el evento y defina **AudioSource. PlayOneShot** como la acción que se va a desencadenar:

![mrlearning: base](images/mrlearning-base/tutorial4-section6-step4-1.png)

Vaya a **activos** > **MixedRealityToolkit. SDK** > **StandardAssets** > material para ver los clips de audio que se proporcionan con el MRTK y, a continuación, asigne un clip de audio adecuado al campo **clip de audio** , por ejemplo, el clip de audio MRTK_Gem:

![mrlearning: base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo implementar eventos, puede consultar las instrucciones de [gestos de seguimiento de mano e](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons) interactivos.

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a>5. probar la interacción táctil mediante la simulación en el editor

Presione el botón reproducir para entrar en el modo de juego. A continuación, mantenga presionada la barra espaciadora para abrir la mano y use el mouse para tocar el objeto OCTA y desencadenar el efecto de sonido:

![mrlearning: base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> Como vio al probar la interacción táctil y como se muestra en la imagen anterior, el objeto OCTA color pulsated mientras se toca. Este efecto está codificado de forma rígida en el componente de toque de interacción (Script) de mano y no en el resultado de la configuración de eventos completada en los pasos anteriores.
>
> Si desea deshabilitar este efecto, puede, por ejemplo, comentar como comentario o la línea 32 ' TargetRenderer = GetComponentInChildren<Renderer>(); ', lo que dará lugar a que el TargetRenderer quede nulo y el color no sea pulsating.

## <a name="congratulations"></a>Enhorabuena

En este tutorial, aprendió a organizar objetos 3D en una colección de cuadrículas y cómo manipular estos objetos (escalado, rotación y movimiento) mediante la interacción aproximada (captando directamente con manos sometidas a seguimiento) e interacción lejana (mediante rayos de miración o rayos de mano). También ha aprendido cómo colocar los rectángulos de selección alrededor de los objetos 3D, y ha aprendido a usar y personalizar los controladores en los cuadros de límite. Por último, has aprendido a desencadenar eventos al tocar objetos.

[Lección siguiente: 6. explorar opciones de entrada avanzadas](mrlearning-base-ch5.md)
