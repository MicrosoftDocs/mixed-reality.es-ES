---
title: 'Tutoriales de introducción: 5. Interacción con objetos 3D'
description: Obtén información sobre el contenido 3D básico y las experiencias de usuario, como la organización de objetos 3D y cuadros de límite para la manipulación básica.
author: jessemcculloch
ms.author: jemccull
ms.date: 05/02/2019
ms.topic: article
keywords: mixed reality, unity, tutorial, hololens
ms.localizationpriority: high
ms.openlocfilehash: 419b381c1240b2cc10708eab03245ed3aabfa859
ms.sourcegitcommit: 61291e83536c8cb2e8401a8e66060128ede35922
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416137"
---
# <a name="5-interacting-with-3d-objects"></a>5. Interacción con objetos 3D

En este tutorial, obtendrás información sobre el contenido 3D básico y la experiencia del usuario; por ejemplo, la organización de objetos 3D como parte de una colección, cuadros de límite para la manipulación básica, interacción próxima y lejana, y gestos de tocar y agarrar con seguimiento de manos.

## <a name="objectives"></a>Objetivos

* Crear un panel de objetos 3D que se usará para otros objetivos de aprendizaje
* Implementar rectángulos de selección
* Configurar objetos 3D para la manipulación básica, como mover, girar y escalar
* Explorar la interacción próxima y lejana
* Más información sobre otros gestos de seguimiento de manos, como agarrar y tocar

## <a name="importing-the-tutorial-assets"></a>Importación de los activos del tutorial

Descarga e importa el paquete personalizado de Unity:

* [MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.2/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.2.unitypackage)

Después de importar los recursos del tutorial, la ventana del proyecto debería tener un aspecto similar al siguiente:

![mrlearning-base](images/mrlearning-base/tutorial4-section1-step1-1.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo importar un paquete personalizado de Unity, consulta [Importación de Mixed Reality Toolkit](mrlearning-base-ch1.md#import-the-mixed-reality-toolkit).

## <a name="decluttering-the-scene-view"></a>Limpieza de la vista de escena

Para que resulte más fácil trabajar con la escena, define la **visibilidad de la escena** para los objetos **Cube** y **ButtonCollection** como desactivada haciendo clic en el icono de **ojo** situado a la izquierda de los objetos. Esto oculta el objeto en la ventana Scene (Escena) sin cambiar su visibilidad en el juego:

![mrlearning-base](images/mrlearning-base/tutorial4-section2-step1-1.png)

> [!TIP]
> Para obtener más información sobre los controles de visibilidad de la escena y cómo puedes usarlos para optimizar la vista de la escena y el flujo de trabajo, visita la documentación sobre la <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">visibilidad de la escena </a> de Unity.

## <a name="organizing-3d-objects-in-a-collection"></a>Organización de los objetos 3D de una colección

En esta sección, crearás un panel de objetos 3D que usarás al explorar varias formas de interactuar con objetos 3D en las siguientes secciones de este tutorial. En concreto, configurarás los objetos 3D para que se coloquen en una cuadrícula de 3 x 3.

Del mismo modo que cuando [creaste un panel de botones](mrlearning-base-ch2.md#creating-a-panel-of-buttons-using-mrtks-grid-object-collection), los principales pasos que debes seguir para lograrlo son:

1. Asignar los objetos 3D a un objeto principal
2. Agregar y configurar el componente Grid Object Collection (Script) (Colección de objetos de cuadrícula [script])

### <a name="1-parent-the-3d-objects-to-a-parent-object"></a>1. Asignar los objetos 3D a un objeto principal

En la ventana Hierarchy (Jerarquía), **crea un objeto vacío**, asígnale un nombre adecuado; por ejemplo, **3DObjectCollection** y colócalo en una ubicación adecuada, como X = 0, Y = -0,2, Z = 2.

En la ventana Project (Proyecto), ve a **Assets** (Recursos) > **MRTK.Tutorials.GettingStarted** > **Prefabs** (Objetos prefabricados) y, a continuación, **asigna** los siguientes objetos prefabricados a la colección **3DObjectCollection** principal:

* Cheese
* CoffeeCup
* EarthCore
* Octa
* Platonic
* TheModule

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-1.png)

En la ventana Hierarchy (Jerarquía), **crea tres cubos** como objetos secundarios de **3DObjectCollection** y define su **escala** de transformación como X = 0,15, Y = 0,15, Z = 0,15:

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-2.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo realizar los pasos indicados anteriormente, consulta el tutorial [Crear la interfaz de usuario y configurar Mixed Reality Toolkit](mrlearning-base-ch2.md).

Cambia la posición de los cubos para poder verlos todos:

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-3.png)

En la ventana Project (Proyecto), desplázate hasta **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > **Materials** (Recursos > MixedRealityToolkit.SDK > StandardAssets > Materials) para ver los materiales proporcionados con MRTK.

**Haz clic y arrastra** un material adecuado a la propiedad 0 del elemento **Materials** (Materiales) del representador de malla de cada cubo; por ejemplo:

* MRTK_Standard_GlowingCyan
* MRTK_Standard_GlowingOrange
* MRTK_Standard_Green

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step1-4.png)

### <a name="2-add-and-configure-the-grid-object-collection-script-component"></a>2. Agregar y configurar el componente Grid Object Collection (Script) (Colección de objetos de cuadrícula [script])

Agrega un componente **Grid Object Collection (Script)** (Colección de objetos de cuadrícula [script]) al objeto **3DObjectCollection** y configúralo de la siguiente manera:

* Cambia el valor de **Sort Type** (Tipo de orden) a **Child Order** (Orden secundario) para asegurarte de que los objetos secundarios se ordenan en el orden en el que los coloques bajo el objeto principal.

A continuación, haz clic en el botón **Actualizar colección** para aplicar la nueva configuración:

![mrlearning-base](images/mrlearning-base/tutorial4-section3-step2-1.png)

## <a name="manipulating-3d-objects"></a>Manipulación de objetos 3D

En esta sección, agregarás la capacidad de manipular todos los objetos 3D del panel que creaste en la sección anterior. Además, en el caso de los objetos prefabricados, permitirás que los usuarios accedan a los objetos y los agarren con el seguimiento de manos. A continuación, explorarás algunos comportamientos de manipulación que puedes aplicar a los objetos.

Los principales pasos que debes seguir para lograrlo son:

1. Agregar el componente Manipulation Handler (Script) (Controlador de manipulación [script]) a todos los objetos
2. Agregar el componente Near Interaction Grabbable (Script) (Interacción próxima de agarre [script]) a los objetos prefabricados
3. Configurar el componente Manipulation Handler (Script) (Controlador de manipulación [script])

> [!IMPORTANT]
> Para poder **manipular un objeto**, el objeto debe tener los siguientes componentes:
>
> * Componente **Collider**; por ejemplo, un colisionador de cuadro
> * Componente **Manipulation Handler (Script)** (Controlador de manipulación [script])
>
> Para poder **manipular** y **agarrar un objeto con seguimiento de manos**, el objeto debe tener los componentes siguientes:
>
> * Componente **Collider**; por ejemplo, un colisionador de cuadro
> * Componente **Manipulation Handler (Script)** (Controlador de manipulación [script])
> * Componente **Near Interaction Grabbable (Script)** (Interacción próxima de agarre [script])

### <a name="1-add-the-manipulation-handler-script-component-to-all-the-objects"></a>1. Agregar el componente Manipulation Handler (Script) (Controlador de manipulación [script]) a todos los objetos

En la ventana Hierarchy (Jerarquía), selecciona el objeto **Cheese**, mantén presionada la tecla **Mayús** y, a continuación, selecciona el objeto **Cube () 2** y agrega el componente **Manipulation Handler (Script)** (Controlador de manipulación [script]) a todos los objetos:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step1-1.png)

> [!NOTE]
> Para los fines de este tutorial, los colisionadores ya se han agregado a los objetos prefabricados. En el caso de los elementos primitivos de Unity, como los objetos Cube, el componente Collider se agrega automáticamente al crear el objeto. En la imagen anterior, los colisionadores se representan mediante contornos verdes. Para obtener más información sobre los colisionadores, visita la documentación sobre <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">colisionadores</a> de Unity.

### <a name="2-add-the-near-interaction-grabbable-script-component-to-the-prefab-objects"></a>2. Agregar el componente Near Interaction Grabbable (Script) (Interacción próxima de agarre [script]) a los objetos prefabricados

En la ventana Jerarquía, selecciona el objeto **Cheese**, mantén presionada la tecla **Mayús** y, a continuación, selecciona el objeto **TheModule** y agrega el componente **Near Interaction Grabbable (Script)** (Interacción próxima de agarre [script]) a todos los objetos:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step2-1.png)

### <a name="3-configure-the-manipulation-handler-script-component"></a>3. Configurar el componente Manipulation Handler (Script) (Controlador de manipulación [script])

#### <a name="default-manipulation"></a>Manipulación predeterminada

Para el objeto **Cube**, deja todas las propiedades en el valor predeterminado para experimentar el comportamiento de manipulación predeterminado:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-1.png)

> [!TIP]
> Para restablecer los valores predeterminados de un componente, puedes seleccionar el icono de configuración del componente y seleccionar Restablecer.

#### <a name="restrict-manipulation-to-scale-only"></a>Restringir la manipulación solo a escala

En el caso del objeto **Cube (1)** , cambia **Two Handed Manipulation Type** (Manipulación con dos manos) a **Escala** para que solo el usuario pueda cambiar el tamaño del objeto:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-2.png)

#### <a name="constrain-the-movement-to-a-fixed-distance-from-the-user"></a>Restringir el movimiento a una distancia fija del usuario

En el caso del objeto **Cube (2)** , cambia **Constraint On Movement** (Limitación del movimiento) a **Fix Distance From Head** (Corregir distancia de la cabeza) para que, cuando el objeto se mueva, permanezca a la misma distancia del usuario:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-3.png)

#### <a name="default-grabbable-manipulation"></a>Manipulación de agarre predeterminada

En el caso de los objetos **Cheese**, **CoffeCup** y **EarthCore**, deja todas las propiedades con sus valores predeterminados para experimentar el comportamiento de manipulación de agarre predeterminado:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-4.png)

#### <a name="remove-the-ability-of-far-manipulation"></a>Quitar la capacidad de manipulación remota

En el caso del objeto **Octa**, desactiva la casilla **Allow Far Manipulation** (Permitir manipulación remota) para que el usuario solo pueda interactuar con el objeto directamente mediante el seguimiento de manos:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-5.png)

#### <a name="make-an-object-rotate-around-its-center"></a>Hacer que un objeto gire alrededor de su centro

En el caso del objeto **Platonic**, cambia **One Hand Rotation Mode Near** (Modo de rotación de una mano próximo) y **One Hand Rotation Mode Far** (Modo de rotación de una mano remoto) a **Rotate About Object Center** (Girar alrededor del centro de un objeto) para que, cuando el usuario gire el objeto con una mano, gire alrededor del centro del objeto:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-6.png)

#### <a name="keep-movement-after-object-is-released"></a>Mantener el movimiento después de liberar el objeto

Para el objeto **TheModule**, agrega un componente **Rigidbody** para habilitar la física y, a continuación, desactiva la casilla **Use Gravity** (Usar gravedad) para que el objeto no se vea afectado por la gravedad:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-7.png)

De nuevo en el componente Manipulation Handler (Script) (Controlador de manipulación [script]), comprueba que **Release Behavior** (Comportamiento de liberación) se haya establecido en **Keep Velocity** (Conservar velocidad) y **Keep Angular Velocity** (Conservar velocidad angular) para que, una vez que el objeto se libere de la mano del usuario, siga moviéndose:

![mrlearning-base](images/mrlearning-base/tutorial4-section4-step3-8.png)

Para obtener más información sobre el componente controlador de manipulación y sus propiedades asociadas, consulta la guía del [controlador de manipulación](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html) en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="adding-bounding-boxes"></a>Adición de cuadros de límite

Los cuadros de límite hacen que manipular objetos con una mano sea más sencillo e intuitivo tanto para la interacción próxima como remota, ya que proporcionan controladores que se pueden usar para el escalado y la rotación.

En este ejemplo, agregarás un cuadro de límite al objeto EarthCore, de modo que se podrá interactuar con este objeto mediante la manipulación de objetos configurada en la sección anterior. También se podrá escalar y girar con los controladores de cuadro de límite.

> [!IMPORTANT]
> Para poder usar un **cuadro de límite**, el objeto debe tener los siguientes componentes:
>
> * Componente **Collider**; por ejemplo, un colisionador de cuadro
> * Componente **Bounding Box (Script)** (Cuadro de límite [script])

### <a name="1-add-the-bounding-box-script-component-to-the-earthcore-object"></a>1. Agregar el componenteBounding Box (Script) (Cuadro de límite [script]) al objeto EarthCore

En la ventana Inspector, selecciona el objeto **EarthCore** y agrega el componente **Bounding Box (Script)** (Cuadro de límite [script]) al objeto EarthCore:

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step1-1.png)

> [!NOTE]
> Las visualizaciones del cuadro de límite se crean en tiempo de ejecución y, por tanto, no son visibles antes de entrar en el modo de juego.

### <a name="2-visualize-and-test-the-bounding-box-using-the-in-editor-simulation"></a>2. Visualizar y probar el cuadro de límite mediante la simulación en el editor

Presiona el botón Jugar para acceder al modo de juego. A continuación, mantén presionada la barra espaciadora para que aparezca la mano y usa el ratón para interactuar con el cuadro de límite:

![mrlearning-base](images/mrlearning-base/tutorial4-section5-step2-1.png)

Para obtener más información sobre el componente de cuadro de límite y sus propiedades asociadas, puedes visitar la guía sobre el [cuadro de límite](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) en el [portal de documentación de MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).

## <a name="adding-touch-effects"></a>Adición de efectos táctiles

En este ejemplo, permitirás que se desencadenen eventos al tocar un objeto con la mano. En concreto, configurarás el objeto Octa para que se produzca un efecto sonoro cuando el usuario lo toque.

Los principales pasos que debes seguir para lograrlo son:

1. Agregar un componente de origen de audio al objeto
2. Agregar el componente Near Interaction Touchable (Script) (Interacción próxima táctil [script]) al objeto
3. Agregar el componente Hand Interaction Touch (Script) (Componente de interacción de mano [script]) al objeto
4. Implementar el evento On Touch Started (Iniciado con el tacto)
5. Probar la interacción táctil mediante la simulación en el editor

> [!IMPORTANT]
> Para poder **desencadenar eventos táctiles**, el objeto debe tener los siguientes componentes:
>
> * Componente **Collider** (Colisionador), preferiblemente un colisionador de cuadro
> * Componente **Near Interaction Touchable (Script)** (Interacción próxima táctil [script])
> * Componente **Hand Interaction Touch (Script)** (Interacción con la mano táctil [script])

> [!NOTE]
> El componente Hand Interaction Touch (Script) (Interacción con la mano táctil [script]) no forma parte del MRTK. Se importó con los recursos de este tutorial y, originalmente, formaba parte de los ejemplos de Unity de Mixed Reality Toolkit.

### <a name="1-add-an-audio-source-component-to-the-object"></a>1. Agregar un componente de origen de audio al objeto

En la ventana Jerarquía, selecciona el objeto **Octa**, agrega un componente de **origen de audio** al objeto Octa y, a continuación, cambia el valor de **Spatial Blend** (Combinación espacial) a 1 para habilitar el audio espacial:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step1-1.png)

### <a name="2-add-the-near-interaction-touchable-script-component-to-the-object"></a>2. Agregar el componente Near Interaction Touchable (Script) (Interacción próxima táctil [script]) al objeto

Con el objeto **Octa** todavía seleccionado, agrega el componente **Near Interaction Touchable (Script)** (Interacción próxima táctil [script]) al objeto Octa y, a continuación, haz clic en los botones **Fix Bounds** (Corregir límites) y **Fix Center** (Corregir centro) para actualizar el centro local y las propiedades de los límites de la interacción próxima táctil (script) para que coincidan con BoxCollider:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step2-1.png)

### <a name="3-add-the-hand-interaction-touch-script-component-to-the-object"></a>3. Agregar el componente Hand Interaction Touch (Script) (Componente de interacción de mano [script]) al objeto

Con el objeto **Octa** aún seleccionado, agrega el componente **Hand Interaction Touch (Script)** (Interacción con la mano táctil [script]) al objeto Octa:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step3-1.png)

### <a name="4-implement-the-on-touch-started-event"></a>4. Implementar el evento On Touch Started (Iniciado con el tacto)

En el componente **Hand Interaction Touch (Script)** (Interacción con la mano táctil [script]), haz clic en el pequeño icono **+** para crear un nuevo evento **On Touch Started ()** (Iniciado con el tacto []). A continuación, configura el objeto **Octa** para recibir el evento y define **AudioSource.PlayOneShot** como la acción que se desencadenará:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-1.png)

Ve a **Assets** > **MixedRealityToolkit.SDK** > **StandardAssets** > Materials (Assets > MixedRealityToolkit.SDK > StandardAssets > Materiales) para ver los clips de audio que se incluyen con el MRTK y asigna un clip de audio adecuado al campo **Clip de audio**; por ejemplo, el clip de audio MRTK_Gem:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step4-2.png)

> [!TIP]
> Para obtener un recordatorio sobre cómo implementar eventos, puedes hacer referencia a las instrucciones sobre [gestos de seguimiento de manos y botones interactuables](mrlearning-base-ch2.md#hand-tracking-gestures-and-interactable-buttons).

### <a name="5-test-the-touch-interaction-using-the-in-editor-simulation"></a>5. Probar la interacción táctil mediante la simulación en el editor

Presiona el botón Jugar para acceder al modo de juego. A continuación, mantén presionada la barra espaciadora para abrir la mano y usa el ratón para tocar el objeto Octa y desencadenar el efecto de sonido:

![mrlearning-base](images/mrlearning-base/tutorial4-section6-step5-1.png)

> [!NOTE]
> Como viste al probar la interacción táctil y como se muestra en la imagen anterior, el color del objeto Octa se contraía al tocarlo. Este efecto está codificado de forma rígida en el componente Hand Interaction Touch (Script) (Componente de interacción de mano [script]) y no como resultado de la configuración de los eventos que completaste en los pasos anteriores.
>
> Si quieres deshabilitar este efecto, puedes, por ejemplo, comentar la línea 32 "TargetRenderer = GetComponentInChildren<Renderer>();", lo que provocará que TargetRenderer siga teniendo un valor null y que el color no se contraiga.

## <a name="congratulations"></a>Enhorabuena

En este tutorial has aprendido a organizar objetos 3D en una colección de cuadrícula y a manipular estos objetos (escalado, giro y movimiento) con interacción próxima (agarrándolos directamente con las manos con seguimiento) y lejana (con el haz de mano o mirada). También has aprendido a colocar cuadros de límite alrededor de objetos 3D, y a usar y personalizar los controladores en los cuadros de límite. Por último, has aprendido a desencadenar eventos al tocar objetos.

[Siguiente lección: 6. Exploración de opciones avanzadas de entrada](mrlearning-base-ch5.md)
