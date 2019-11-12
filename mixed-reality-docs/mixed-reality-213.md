---
title: Entrada MR 213
description: Siga este tutorial de codificación con Unity, Visual Studio y auriculares envolventes para aprender los detalles de los controladores de movimiento.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, inmersivo, controlador de movimiento, Academia, tutorial
ms.openlocfilehash: 273d1bf384d588ab24bfe29e30f299b7a41fe541
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926817"
---
>[!NOTE]
>Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.  Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Se ha publicado [una nueva serie de tutoriales](mrlearning-base.md) para HoloLens 2.

<br>

# <a name="mr-input-213-motion-controllers"></a>Entrada MR 213: Controladores de movimiento

Los controladores de movimiento del mundo de la realidad mixta agregan otro nivel de interactividad. Con [los controladores de movimiento](motion-controllers.md), podemos interactuar directamente con los objetos de una manera más natural, de forma similar a las interacciones físicas en la vida real, lo que aumenta la inmersión y la alegría en la experiencia de la aplicación.

En la entrada MR 213, exploraremos los eventos de entrada del controlador de movimiento mediante la creación de una sencilla experiencia de dibujo espacial. Con esta aplicación, los usuarios pueden pintar en un espacio tridimensional con varios tipos de pinceles y colores.

## <a name="topics-covered-in-this-tutorial"></a>Temas tratados en este tutorial

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|**Visualización del controlador**|**Eventos de entrada del controlador**|**Controlador y interfaz de usuario personalizados**|
|Aprenda a representar los modelos de control de movimiento en el modo de juego y el tiempo de ejecución de Unity.|Comprenda los distintos tipos de eventos de botón y sus aplicaciones.|Obtenga información sobre cómo superponer los elementos de la interfaz de usuario sobre el controlador o personalizarlos totalmente.|

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td>Entrada MR 213: Controladores de movimiento</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de empezar

### <a name="prerequisites"></a>Requisitos previos

Consulte la lista de comprobación de instalación para los auriculares que se envolverán en [esta página](install-the-tools.md).

* En este tutorial se requiere [Unity 2017.2.1 P2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)

### <a name="project-files"></a>Archivos de proyecto

* [Descargue los archivos](https://github.com/Microsoft/MixedReality213/archive/master.zip) requeridos por el proyecto y extraiga los archivos en el escritorio.

>[!NOTE]
>Si desea examinar el código fuente antes de la descarga, está [disponible en github](https://github.com/Microsoft/MixedReality213).

## <a name="unity-setup"></a>Configuración de Unity

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a>Objetivos

* Optimizar el desarrollo de Unity para Windows Mixed Reality
* Configuración de una cámara de realidad mixta
* Entorno de instalación

### <a name="instructions"></a>Instrucciones

* Inicia Unity.
* Seleccione **abrir**.
* Navegue hasta el escritorio y busque la carpeta **MixedReality213-Master** que ha desarchivado anteriormente.
* Haga clic en **Seleccionar carpeta**.
* Una vez que Unity termine de cargar los archivos de proyecto, podrá ver el editor de Unity.
* En Unity, seleccione **archivo > configuración de compilación**.

    ![MR213_BuildSettings](images/mr213-buildsettings-450px.png)

* Seleccione **plataforma universal de Windows** en la lista **plataforma** y haga clic en el botón **cambiar plataforma** .
* Establecimiento del dispositivo de destino en **cualquier dispositivo**
* Establecer el tipo de compilación en **D3D**
* Establecer SDK en la **versión más reciente instalada**
* Comprobación **de C# proyectos de Unity**
    * Esto permite modificar archivos de script en el proyecto de Visual Studio sin volver a generar el proyecto de Unity.
* Haga clic en **configuración del reproductor**.
* En el panel **Inspector** , desplácese hacia abajo hasta la parte inferior.
* En configuración de XR, Active **realidad compatible**
* En SDK de realidad virtual, seleccione **Windows Mixed Reality** .

    ![MR213_XRSettings](images/mr213-xrsettings-500px.png)

* Cierre la ventana de **configuración de compilación** .

### <a name="project-structure"></a>Estructura del proyecto

En este tutorial se usa **[Mixed Reality Toolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** . Puede encontrar las versiones en [esta página](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).

![ProjectStructure](images/mr213-projectstructure-650px.png)

**Escenas completadas para su referencia**

* Encontrará dos escenas de Unity completadas en la carpeta **Scenes** .
    * **MixedReality213**: escena completada con un solo pincel
    * **MixedReality213Advanced**: escena completada para diseño avanzado con varios pinceles

**Nueva configuración de escenas para el tutorial**

* En Unity, haga clic en **archivo > nueva escena** .
* Eliminar la **cámara principal** y la **luz direccional**
* En el **panel Proyecto**, busque y arrastre el siguiente Prefabs al panel **jerarquía** :
    * Assets/HoloToolkit/INPUT/Prefabs/**MixedRealityCamera**
    * Activos/AppPrefabs/**entorno**

    ![Cámara y entorno](images/mr213-cameraenvironment-300px.jpg)

* Hay dos Prefabs de cámara en el kit de herramientas de realidad mixta:
    * **MixedRealityCamera. recurso prefabricado**: solo cámara
    * **MixedRealityCameraParent. recurso prefabricado**: cámara + teleportabilidad + límite
    * En este tutorial, usaremos **MixedRealityCamera** sin la característica de teleportabilidad. Por este motivo, hemos agregado recurso prefabricado de **entorno** sencillo, que contiene una planta básica para que el usuario sienta.
    * Para obtener más información acerca de la teleportabilidad con **MixedRealityCameraParent**, consulte el artículo sobre el [diseño avanzado: teleportabilidad y Locomotion](#advanced-design---teleportation-and-locomotion)

**Configuración de SKYBOX**

* Haga clic en **ventana > iluminación > configuración**
* Haga clic en el círculo en el lado derecho del **campo material de SKYBOX**
* Escriba "Gray" y seleccione **SkyboxGray** (assets/AppPrefabs/support/Materials/SkyboxGray. MAT)

    ![Establecer SKYBOX](images/mr123-skyboxsetting-400px.jpg)

* Active la opción **SKYBOX** para poder ver el degradado gris asignado SKYBOX

    ![Alternar opción SKYBOX](images/mr213-skyboxcheck-400px.jpg)

* La escena con MixedRealityCamera, entorno y gris SKYBOX tendrá el siguiente aspecto.

    ![Entorno de MixedReality213](images/mr213-environment-600px.jpg)

* Haga clic en **archivo > guardar escena como**
* **Guardar** la escena en la carpeta Scenes con cualquier nombre

## <a name="chapter-1---controller-visualization"></a>Capítulo 1: visualización del controlador

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a>Objetivos

* Aprenda a representar modelos de controlador de movimiento en el modo de juego de Unity y en tiempo de ejecución.

Windows Mixed Reality proporciona un modelo de controlador animado para la visualización del controlador. Hay varios enfoques que puede realizar para la visualización del controlador en la aplicación:

* Predeterminado: uso del controlador predeterminado sin modificación
* Híbrido: uso del controlador predeterminado, pero personalización de algunos de sus elementos o de la superposición de componentes de interfaz de usuario
* Reemplazo: usar su propio modelo 3D personalizado para el controlador

En este capítulo, veremos los ejemplos de estas personalizaciones del controlador.

### <a name="instructions"></a>Instrucciones

* En el panel **proyecto** , escriba **MotionControllers** en el cuadro de búsqueda. También puede encontrarlo en assets/HoloToolkit/INPUT/Prefabs/.
* Arrastre **MotionControllers** recurso prefabricado en el panel **jerarquía** .
* Haga clic en **MotionControllers** recurso prefabricado en el panel **jerarquía** .

**MotionControllers recurso prefabricado**

**MotionControllers** recurso prefabricado tiene un script **MotionControllerVisualizer** que proporciona las ranuras para los modelos de controladores alternativos. Si asigna sus propios modelos 3D personalizados, como una mano o un valor de espada, y activa la casilla "usar siempre el modelo alternativo de la izquierda o la derecha", se verán en lugar del modelo predeterminado. Usaremos esta ranura en el capítulo 4 para reemplazar el modelo de controlador por un pincel.

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

**Las**

* En el panel **Inspector** , haga doble clic en **MotionControllerVisualizer** script para ver el código en Visual Studio

**Script MotionControllerVisualizer**

Las clases **MotionControllerVisualizer** y **MotionControllerInfo** proporcionan los medios para tener acceso a & modificar los modelos de controlador predeterminados. **MotionControllerVisualizer** se suscribe al evento **InteractionSourceDetected** de Unity y crea automáticamente instancias de los modelos de controlador cuando se encuentran.

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

Los modelos de controlador se entregan según [la especificación glTF](https://github.com/KhronosGroup/glTF). Este formato se ha creado para proporcionar un formato común, a la vez que mejora el proceso que subyace a la transmisión y desempaquetado de recursos 3D. En este caso, es necesario recuperar y cargar los modelos de controlador en tiempo de ejecución, ya que queremos que la experiencia del usuario sea lo más fluida posible y no se garantice qué versión de los controladores de movimiento puede estar usando el usuario. Este curso, a través del kit de herramientas de la realidad mixta, usa una versión del [proyecto UnityGLTF](https://github.com/KhronosGroup/UnityGLTF)del Grupo Khronos.

Una vez que se ha entregado el controlador, los scripts pueden usar **MotionControllerInfo** para buscar las transformaciones de elementos de controlador específicos para que puedan colocarse correctamente.

En un capítulo posterior, se aprenderá a usar estos scripts para adjuntar elementos de interfaz de usuario a los controladores.

*En algunos scripts, encontrará bloques de código con **#if. UNITY_EDITOR** o **UNITY_WSA**. Estos bloques de código solo se ejecutan en el tiempo de ejecución de UWP al implementar en Windows. Esto se debe a que el conjunto de API que usa el editor de Unity y el tiempo de ejecución de la aplicación para UWP son diferentes.*

* **Guarde** la escena y haga clic en el botón **reproducir** .

Podrá ver la escena con controladores de movimiento en el casco. Puede ver animaciones detalladas para los clics de botón, el movimiento del stick analógico y el resaltado táctil de Touchpad.

![MR213_Controller valor predeterminado de visualización](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a>Capítulo 2: adjuntar elementos de la interfaz de usuario al controlador

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a>Objetivos

* Más información sobre los elementos de los controladores de movimiento
* Obtenga información acerca de cómo adjuntar objetos a partes específicas de los controladores

En este capítulo, aprenderá a agregar elementos de la interfaz de usuario al controlador, al que el usuario puede acceder y manipular fácilmente en cualquier momento. También aprenderá a agregar una interfaz de usuario del selector de colores simple mediante la entrada del panel táctil.

### <a name="instructions"></a>Instrucciones

* En el panel **proyecto** , busque el script **MotionControllerInfo** .
* En el resultado de la búsqueda, haga doble clic en **MotionControllerInfo** script para ver el código en Visual Studio.

**Script MotionControllerInfo**

El primer paso es elegir a qué elemento del controlador desea asociar la interfaz de usuario. Estos elementos se definen en **ControllerElementEnum** en **MotionControllerInfo.CS**.

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)

* **Inicio**
* **MENU**
* **Visión**
* **Palanca**
* **No**
* **Panel táctil**
* **Pose de puntero** : este elemento representa la punta de la dirección de reenvío hacia delante del controlador.

**Las**

* En el panel **proyecto** , busque el script **AttachToController** .
* En el resultado de la búsqueda, haga doble clic en **AttachToController** script para ver el código en Visual Studio.

**Script AttachToController**

El script **AttachToController** proporciona una manera sencilla de adjuntar cualquier objeto a un elemento y una manecilla de controlador especificados.

En **AttachElementToController ()** ,

* Comprobar la mano mediante **MotionControllerInfo. Handl**
* Obtiene un elemento específico del controlador mediante **MotionControllerInfo. TryGetElement ()**
* Después de recuperar la transformación del elemento del modelo del controlador, el objeto primario que se encuentra en él y establecer la posición local del objeto & la rotación en cero.

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type " + element + " under controller " + newController.ControllerParent.name + "; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

La manera más sencilla de usar el script **AttachToController** es heredar de él, como hemos hecho en el caso de **ColorPickerWheel.** Simplemente invalide las funciones **OnAttachToController** y **OnDetachFromController** para realizar la instalación o el desglose cuando el controlador se detecta o se desconecta.

**Las**

* En el panel **proyecto** , escriba en el cuadro de búsqueda **ColorPickerWheel**. También puede encontrarlo en assets/AppPrefabs/.
* Arrastre **ColorPickerWheel** recurso prefabricado en el panel **jerarquía** .
* Haga clic en **ColorPickerWheel** recurso prefabricado en el panel **jerarquía** .
* En el panel **Inspector** , haga doble clic en **ColorPickerWheel** script para ver el código en Visual Studio.

![ColorPickerWheel recurso prefabricado](images/mr213-colorpickerwheel-1000px.jpg)

**Script ColorPickerWheel**

Dado que **ColorPickerWheel** hereda **AttachToController**, muestra la **mano** y el **elemento** en el panel del **Inspector** . Vamos a asociar la interfaz de usuario al elemento Touchpad del controlador izquierdo.

![Script ColorPickerWheel](images/mr213-attachtocontroller-300px.jpg)

**ColorPickerWheel** invalida **OnAttachToController** y **OnDetachFromController** para suscribirse al evento de entrada que se usará en el capítulo siguiente para la selección de color con entrada de Touchpad.

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```

* **Guarde** la escena y haga clic en el botón **reproducir** .

**Método alternativo para adjuntar objetos a los controladores**

Se recomienda que los scripts hereden de **AttachToController** e invalide **OnAttachToController**. Sin embargo, esto no siempre es posible. Una alternativa es usarla como componente independiente. Esto puede ser útil si desea adjuntar un recurso prefabricado existente a un controlador sin refactorizar los scripts. Basta con que la clase espere a que Isattached (se establezca en true antes de realizar la instalación. La manera más sencilla de hacerlo es usar una corutina para ' Start '.

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a>Capítulo 3: trabajar con la entrada de Touchpad

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a>Objetivos

* Obtenga información sobre cómo obtener eventos de datos de entrada de Touchpad
* Aprenda a usar la información de posición del eje Touchpad para la experiencia de la aplicación

### <a name="instructions"></a>Instrucciones

* En el panel **jerarquía** , haga clic en **ColorPickerWheel**
* En el panel **Inspector** , en **animación**, haga doble clic en **ColorPickerWheelController**
* Podrá ver la pestaña **animador** abierta

**Mostrar u ocultar la interfaz de usuario con el controlador de animación de Unity**

Para mostrar y ocultar la interfaz de usuario de **ColorPickerWheel** con la animación, usamos el [sistema de animación de Unity](https://docs.unity3d.com/Manual/AnimationOverview.html). Si se establece la propiedad **visible** de **ColorPickerWheel**en los desencadenadores true o false, se **muestran** y **ocultan** los desencadenadores de animación. Los parámetros de **Mostrar** y **ocultar** se definen en el controlador de animación **ColorPickerWheelController** .

![Controlador de animación de Unity](images/mr123-animationcontroller-550px.jpg)

**Las**

* En el panel **jerarquía** , seleccione **ColorPickerWheel** recurso prefabricado
* En el panel **Inspector** , haga doble clic en **ColorPickerWheel** script para ver el código en Visual Studio

**Script ColorPickerWheel**

**ColorPickerWheel** se suscribe al evento **InteractionSourceUpdated** de Unity para escuchar eventos Touchpad.

En **InteractionSourceUpdated ()** , el script primero comprueba para asegurarse de que:

* es realmente un evento Touchpad (obj. state. **touchpadTouched**)
* se origina desde el controlador izquierdo (obj. state. Source). **zurdo**)

Si ambos son true, la posición del panel táctil (obj. state. **touchpadPosition**) se asigna a **selectorPosition**.

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

En **Update ()** , en función de la propiedad **visible** , desencadena los desencadenadores Mostrar y ocultar animación en el componente de animación del selector de colores.

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

En **Update ()** , **selectorPosition** se usa para convertir un rayo en el Colisionador de malla de la rueda de colores, que devuelve una posición UV. Esta posición se puede usar para buscar la coordenada de píxeles y el valor de color de la textura de la rueda de colores. Este valor es accesible para otros scripts a través de la propiedad **SelectedColor** .

![Rueda del selector de colores raycasting](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a>Capítulo 4: invalidación del modelo de controlador

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a>Objetivos

* Obtenga información sobre cómo invalidar el modelo de controlador con un modelo 3D personalizado.

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a>Instrucciones

* Haga clic en **MotionControllers** en el panel **jerarquía** .
* Haga clic en el círculo en el lado derecho del campo **alternativo de controlador derecho** .
* Escriba **"BrushController**" y seleccione recurso prefabricado en el resultado. Puede encontrarlo en assets/AppPrefabs/**BrushController**.
* Comprobar **usar siempre el modelo derecho alternativo**

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

No es necesario que **BrushController** recurso prefabricado esté incluido en el panel de **jerarquías** . Sin embargo, para desproteger sus componentes secundarios:

* En el panel **proyecto** , escriba **BrushController** y arrastre **BrushController** recurso prefabricado al panel **jerarquía** .

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

Encontrará el componente de **información** en **BrushController**. Usaremos su transformación para iniciar o detener las líneas de dibujo.

* Elimine el **BrushController** en el panel de **jerarquías** .
* **Guarde** la escena y haga clic en el botón **reproducir** . Podrá ver el modelo de pincel reemplazado por el controlador de movimiento de la derecha.

## <a name="chapter-5---painting-with-select-input"></a>Capítulo 5: pintar con seleccionar entrada

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a>Objetivos

* Obtenga información sobre cómo usar el evento de botón Seleccionar para iniciar y detener un dibujo de línea

### <a name="instructions"></a>Instrucciones

* Busque **BrushController** recurso prefabricado en el panel **proyecto** .
* En el panel **Inspector** , haga doble clic en **BrushController** script para ver el código en Visual Studio

**Script BrushController**

**BrushController** se suscribe a los eventos **InteractionSourcePressed** y **InteractionSourceReleased** de InteractionManager. Cuando se desencadena el evento **InteractionSourcePressed** , la propiedad **Draw** del pincel se establece en true. Cuando se desencadena el evento **InteractionSourceReleased** , la propiedad **Draw** del pincel se establece en false.

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

Mientras **Draw** está establecido en true, el pincel generará puntos en una instancia de Unity **LineRenderer**. Se mantiene una referencia a este recurso prefabricado en el campo **Stroke recurso prefabricado** del pincel.

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

Para usar el color seleccionado actualmente en la interfaz de usuario de la rueda del selector de colores, **BrushController** debe tener una referencia al objeto **ColorPickerWheel** . Dado que se crea una instancia de recurso prefabricado de **BrushController** en tiempo de ejecución como controlador de reemplazo, cualquier referencia a los objetos de la escena tendrá que establecerse en tiempo de ejecución. En este caso, usamos **GameObject. FindObjectOfType** para encontrar **ColorPickerWheel**:

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```

* **Guarde** la escena y haga clic en el botón **reproducir** . Podrá dibujar las líneas y pintar con el botón seleccionar del controlador de la derecha.

## <a name="chapter-6---object-spawning-with-select-input"></a>Capítulo 6: generación de objetos con selección de entrada

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a>Objetivos

* Obtenga información sobre cómo usar los eventos de entrada del botón seleccionar y agarre
* Obtener información sobre cómo crear instancias de objetos

### <a name="instructions"></a>Instrucciones

* En el panel **proyecto** , escriba **ObjectSpawner** en el cuadro de búsqueda. También puede encontrarlo en assets/AppPrefabs/
* Arrastre **ObjectSpawner** recurso prefabricado en el panel **jerarquía** .
* Haga clic en **ObjectSpawner** en el panel **jerarquía** .
* **ObjectSpawner** tiene un campo denominado **origen de color**.
* En el panel **jerarquía** , arrastre la referencia **ColorPickerWheel** a este campo.

    ![Inspector de generación de objetos](images/mr213-objectspawnercolorpickerwheel-650px.jpg)

* Haga clic en **ObjectSpawner** recurso prefabricado en el panel **jerarquía** .
* En el panel **Inspector** , haga doble clic en **ObjectSpawner** script para ver el código en Visual Studio.

**Script ObjectSpawner**

El **ObjectSpawner** crea instancias de las copias de una malla primitiva (cubo, esfera, cilindro) en el espacio. Cuando se detecta un **InteractionSourcePressed** , comprueba la mano y si se trata de un evento **InteractionSourcePressType. agarre** o **InteractionSourcePressType. Select** .

Para un evento de **agarre** , incrementa el índice del tipo de malla actual (esfera, Cube, cylinder)

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

En el caso de un evento **Select** , en **SpawnObject ()** , se crea una instancia de un nuevo objeto, no primario y se publica en el mundo.

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detach the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

**ObjectSpawner** usa **ColorPickerWheel** para establecer el color del material del objeto de presentación. A los objetos generados se les asigna una instancia de este material para conservar su color.

* **Guarde** la escena y haga clic en el botón **reproducir** .

Podrá cambiar los objetos con el botón de agarre y generar objetos con el botón seleccionar.

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a>Creación e implementación de una aplicación en el portal de realidad mixta

* En Unity, seleccione **archivo > configuración de compilación**.
* Haga clic en **Agregar escenas abiertas** para agregar la escena actual a las **escenas de la compilación**.
* Haz clic en **Compilación**.
* Cree una **nueva carpeta** denominada "app".
* Haga clic en la carpeta de la **aplicación** .
* Haga clic en **Seleccionar carpeta**.
* Cuando se haya realizado Unity, aparecerá una ventana del explorador de archivos.
* Abra la carpeta de la **aplicación** .
* Haga doble clic en el archivo de solución de Visual Studio **YourSceneName. sln** .
* Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x64**.
* Haga clic en la flecha desplegable situada junto al botón dispositivo y seleccione **equipo local**.
* Haga clic en **depurar-> iniciar sin depurar** en el menú o presione **Ctrl + F5**.

Ahora la aplicación se crea e instala en el portal de realidad mixta. Puede volver a iniciarlo a través del menú Inicio en el portal de realidad mixta.

## <a name="advanced-design---brush-tools-with-radial-layout"></a>Herramientas de pincel de diseño avanzadas con diseño radial

![MixedReality213 Main](images/mr213-main-600px.jpg)

En este capítulo, obtendrá información sobre cómo reemplazar el modelo de controlador de movimiento predeterminado con una colección de herramientas de pincel personalizada. Como referencia, puede encontrar la escena completada **MixedReality213Advanced** en la carpeta **Scenes** .

### <a name="instructions"></a>Instrucciones

* En el panel **proyecto** , escriba **BrushSelector** en el cuadro de búsqueda. También puede encontrarlo en assets/AppPrefabs/
* Arrastre **BrushSelector** recurso prefabricado en el panel **jerarquía** .
* Para la organización, cree un GameObject vacío denominado **brushes** .
* Arrastre los siguientes Prefabs desde el panel **proyecto** a los **pinceles**
    * Assets/AppPrefabs/**BrushFat**
    * Assets/AppPrefabs/**BrushThin**
    * Activos/AppPrefabs/**borrador**
    * Assets/AppPrefabs/**MarkerFat**
    * Assets/AppPrefabs/**MarkerThin**
    * Activos/AppPrefabs/**lápiz**

    ![Pinceles](images/mixedreality213-brushes-250px.png)

* Haga clic en **MotionControllers** recurso prefabricado en el panel **jerarquía** .
* En el panel **Inspector** , desactive **usar modelo de derecho alternativo siempre** en el **visualizador de controlador de movimiento**
* En el panel **jerarquía** , haga clic en **BrushSelector**
* **BrushSelector** tiene un campo denominado **ColorPicker**
* En el panel **jerarquía** , arrastre el campo **ColorPickerWheel** al **ColorPicker** en el panel **Inspector** .

    ![Asignar ColorPickerWheel al selector de pincel](images/mr213-brushselector-500px.jpg)

* En el panel **jerarquía** , en **BrushSelector** recurso prefabricado, seleccione el objeto de **menú** .
* En el panel **Inspector** , en el componente **LineObjectCollection** , abra la lista desplegable de la matriz de **objetos** . Verá 6 ranuras vacías.
* En el panel **jerarquía** , arrastre cada uno de los Prefabs primarios bajo los **pinceles** GameObject a estas ranuras en cualquier orden. (Asegúrese de que está arrastrando el Prefabs de la escena, no el Prefabs en la carpeta del proyecto).

![Selector de pincel](images/mr213-brushselectorbrushes-700px.jpg)

**BrushSelector recurso prefabricado**

Dado que **BrushSelector** hereda **AttachToController**, muestra las opciones de la **mano** y el **elemento** en el panel del **Inspector** . Hemos seleccionado **right** y **Pointing** para adjuntar herramientas de pincel al controlador de la derecha con dirección hacia delante.

El **BrushSelector** hace uso de dos utilidades:

* **Ellipse**: se usa para generar puntos en el espacio a lo largo de una forma de elipse.
* **LineObjectCollection**: distribuye objetos usando los puntos generados por cualquier clase de línea (por ejemplo, elipse). Esto es lo que vamos a usar para colocar los pinceles a lo largo de la forma de elipse.

Cuando se combinan, estas utilidades se pueden usar para crear un menú radial.

**Script LineObjectCollection**

**LineObjectCollection** tiene controles para el tamaño, la posición y la rotación de objetos distribuidos a lo largo de su línea. Esto resulta útil para crear menús radiales como el selector de pincel. Para crear la apariencia de los pinceles que se escalan verticalmente desde cero a medida que se aproximan a la posición seleccionada del centro, los picos de la curva **ObjectScale** en el centro y en las cintas se desconectan en los bordes.

**Script BrushSelector**

En el caso de **BrushSelector**, hemos elegido usar la animación de procedimientos. En primer lugar, el script **LineObjectCollection** distribuye los modelos de pincel en una elipse. Después, cada pincel es responsable de mantener su posición en la mano del usuario en función de su valor de **DisplayMode** , que cambia en función de la selección. Elegimos un enfoque de procedimiento debido a la alta probabilidad de que las transiciones de posición del pincel se interrumpan cuando el usuario selecciona pinceles. Las animaciones Mecanim pueden controlar las interrupciones correctamente, pero suelen ser más complicadas que una sencilla operación lerp.

**BrushSelector** usa una combinación de ambos. Cuando se detecta la entrada del panel táctil, las opciones de pincel se vuelven visibles y se escalan verticalmente a lo largo del menú radial. Después de un período de tiempo de espera (que indica que el usuario ha realizado una selección), las opciones de pincel se vuelven a reducir de nuevo y solo se mantiene el pincel seleccionado.

**Visualización de la entrada del panel táctil**

Incluso en los casos en los que el modelo de controlador se ha reemplazado por completo, puede resultar útil Mostrar la entrada en las entradas del modelo original. Esto ayuda a realizar las acciones del usuario en realidad. En el caso de **BrushSelector** , hemos optado por hacer que el Touchpad esté brevemente visible cuando se recibe la entrada. Para ello, se recupera el elemento Touchpad del controlador, se sustituye su material por un material personalizado y, después, se aplica un degradado al color de ese material en función de la última vez que se recibió la entrada Touchpad.

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }

    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

**Selección de la herramienta pincel con entrada Touchpad**

Cuando el selector de pincel detecta la entrada presionada del Touchpad, comprueba la posición de la entrada para determinar si estaba a la izquierda o a la derecha.

**Grosor del trazo con selectPressedAmount**

En lugar del evento **InteractionSourcePressType. Select** en **InteractionSourcePressed ()** , puede obtener el valor analógico de la cantidad presionada a través de **selectPressedAmount**. Este valor se puede recuperar en **InteractionSourceUpdated ()** .

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

**Script de borrador**

El **borrador** es un tipo especial de pincel que reemplaza la función **DrawOverTime ()** del **pincel**base. Mientras que Draw es true, el borrador comprueba si su sugerencia se corta con cualquier trazo de pincel existente. Si lo hace, se agregan a una cola para que se reduzcan y se eliminen.

## <a name="advanced-design---teleportation-and-locomotion"></a>Diseño avanzado: teleportabilidad y Locomotion

Si desea permitir que el usuario se mueva por la escena con la teleportabilidad mediante el Stick, use **MixedRealityCameraParent** en lugar de **MixedRealityCamera**. También debe agregar **InputManager** y **DefaultCursor**. Dado que **MixedRealityCameraParent** ya incluye **MotionControllers** y el **límite** como componentes secundarios, debe quitar **MotionControllers** y recurso prefabricado de **entorno** existentes.

### <a name="instructions"></a>Instrucciones

* En el panel **jerarquía** , elimine **MixedRealityCamera**, **Environment** y **MotionControllers**
* En el **panel Proyecto**, busque y arrastre el siguiente Prefabs al panel **jerarquía** :
    * Assets/AppPrefabs/INPUT/Prefabs/**MixedRealityCameraParent**
    * Assets/AppPrefabs/INPUT/Prefabs/**InputManager**
    * Assets/AppPrefabs/INPUT/Prefabs/cursor/**DefaultCursor**

    ![Cámara principal de realidad mixta](images/mr213-cameraparent-300px.png)

* En el panel **jerarquía** , haga clic en **Administrador de entrada** .
* En el panel **Inspector** , desplácese hacia abajo hasta la sección **selector simple de puntero único** .
* En el panel **jerarquía** , arrastre **DefaultCursor** al campo **cursor** .

    ![Asignación de DefaultCursor](images/mr213-defaultcursor-500px.png)

* **Guarde** la escena y haga clic en el botón **reproducir** . Podrá usar el stick analógico para girar izquierda/derecha o teletranspórtate.

## <a name="the-end"></a>Fin

Y este es el final de este tutorial. Aprendió:

* Cómo trabajar con modelos de controlador de movimiento en el modo de juego y el tiempo de ejecución de Unity.
* Cómo usar diferentes tipos de eventos de botón y sus aplicaciones.
* Cómo superponer los elementos de la interfaz de usuario en la parte superior del controlador o personalizarlos totalmente.

Ya está listo para empezar a crear su propia experiencia envolvente con los controladores de movimiento.

## <a name="completed-scenes"></a>Escenas completadas

* En el panel del **proyecto** de Unity, haga clic en la carpeta **Scenes** .
* Encontrará dos escenas de Unity **MixedReality213** y **MixedReality213Advanced**.
    * **MixedReality213**: escena completada con un solo pincel
    * **MixedReality213Advanced**: escena completada con varios pinceles en el ejemplo de la cantidad de imprenta del botón seleccionar

## <a name="see-also"></a>Consulta también

* [MR 213 archivos de proyecto de entrada](https://github.com/Microsoft/MixedReality213)
* [Kit de herramientas de realidad mixta: escena de prueba de controlador de movimiento](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [Kit de herramientas de realidad mixta: mecánica de captación](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [Instrucciones de desarrollo de controlador de movimiento](motion-controllers.md)
