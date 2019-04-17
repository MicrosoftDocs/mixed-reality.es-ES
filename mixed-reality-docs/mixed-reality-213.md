---
title: Entrada MR 213
description: Siga este tutorial de programación con Unity, Visual Studio e inmersivos para conocer los detalles de los controladores de movimiento.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, unity mixedrealitytoolkit, envolvente, controlador, academy, tutorial de movimiento
ms.openlocfilehash: 85449795a4fb3d182101cb5b4c4ce3fe85b009c0
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605704"
---
>[!NOTE]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.  Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.  Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.

<br>

# <a name="mr-input-213-motion-controllers"></a>Entrada MR 213: Controladores de movimiento

Controladores de movimiento en el mundo de realidad mixta agregan otro nivel de interactividad. Con [controladores de movimiento](motion-controllers.md), podemos interactuar con objetos de una manera más natural, similar a nuestras interacciones físicas en la vida real, aumentar inmersión directamente y Deleite a su experiencia de aplicación.

En MR 213 de entrada, exploraremos los eventos de entrada del controlador de movimiento mediante la creación de una experiencia simple pintura espacial. Con esta aplicación, los usuarios pueden pintar en un espacio tridimensional con diversos tipos de pinceles y colores.

## <a name="topics-covered-in-this-tutorial"></a>Temas tratados en este tutorial

|![MixedReality213 Topic1](images/mr213-topic1.png)|![Topic2 MixedReality213](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|**Visualización de controlador**|**Eventos de entrada del controlador**|**Interfaz de usuario y dispositivo personalizado**|
|Obtenga información sobre cómo representar modelos de controlador de movimiento en modo de juego de Unity y en tiempo de ejecución.|Comprender los distintos tipos de eventos de botón y sus aplicaciones.|Obtenga información sobre los elementos de interfaz de usuario en la parte superior del controlador de superposición o personalizarlo completamente.|

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td>Entrada MR 213: Controladores de movimiento</td><td style="text-align: center;"> </td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de empezar

### <a name="prerequisites"></a>Requisitos previos

Consulte la lista de comprobación de instalación para inmersivos en [esta página](install-the-tools.md).

* Este tutorial requiere [2017.2.1p2 de Unity](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)

### <a name="project-files"></a>Archivos de proyecto

* [Descargar los archivos](https://github.com/Microsoft/MixedReality213/archive/master.zip) requerida por el proyecto y extraiga los archivos en el escritorio.

>[!NOTE]
>Si desea buscar en el código de origen antes de descargar, tiene [disponible en GitHub](https://github.com/Microsoft/MixedReality213).

## <a name="unity-setup"></a>Programa de instalación de Unity

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a>Objetivos

* Optimizar el desarrollo de Unity para Windows Mixed Reality
* Configuración de la cámara de realidad mixta
* Configuración del entorno

### <a name="instructions"></a>Instrucciones

* Inicie Unity.
* Seleccione **abierto**.
* Vaya al escritorio y buscar el **MixedReality213-master** carpetas que anteriormente sin archivar.
* Haga clic en **Seleccionar carpeta**.
* Una vez que Unity termina de cargar archivos de proyecto, podrá ver el editor de Unity.
* En Unity, seleccione **archivo > configuración de compilación**.

![MR213_BuildSettings](images/mr213-buildsettings-450px.png)
* Seleccione **Universal Windows Platform** en el **plataforma** lista y haga clic en el **Cambiar plataforma** botón.
* Establezca el dispositivo de destino en **cualquier dispositivo**
* Establece el tipo de compilación en **D3D**
* Establece el SDK **instalada más reciente**
* Comprobar **Unity C# proyectos**
    * Esto permite que modificar los archivos de script en el proyecto de Visual Studio sin volver a generar el proyecto de Unity.
* Haga clic en **configuración del Reproductor**.
* En el **Inspector** panel, desplácese hacia abajo hasta la parte inferior
* En la configuración de XR, comprobar **compatibles de realidad Virtual**
* En el SDK de realidad Virtual, seleccione **Windows Mixed Reality**

![MR213_XRSettings](images/mr213-xrsettings-500px.png)
* Cerrar **configuración de compilación** ventana.

### <a name="project-structure"></a>Estructura del proyecto

Este tutorial se usa  **[Kit de herramientas de realidad mixta - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)**. Puede encontrar las versiones en [esta página](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).

![ProjectStructure](images/mr213-projectstructure-650px.png)

**Completado escenas para su referencia**
* Encontrará dos escenas Unity completadas en **escenas** carpeta.
    * **MixedReality213**: Escena completado con el único pincel
    * **MixedReality213Advanced**: Completar la escena para diseño avanzado con varios pinceles

**Nueva configuración de la escena para el tutorial**
* En Unity, haga clic en **archivo > nueva escena**
* Eliminar **cámara principal** y **luz direccional**
* Desde el **panel proyecto**, busque y arrastre el prefabricados siguientes en el **jerarquía** panel:
    * Assets/HoloToolkit/Input/Prefabs/**MixedRealityCamera**
    * Assets/AppPrefabs/**Environment**

![Cámara y entorno](images/mr213-cameraenvironment-300px.jpg)
* Hay dos prefabricados de cámara en el Kit de herramientas de realidad mixta:
    * **MixedRealityCamera.prefab**: Solo la cámara
    * **MixedRealityCameraParent.prefab**: Cámara Teleportation + límites
    * En este tutorial, usaremos **MixedRealityCamera** sin teleportation característica. Por este motivo, hemos agregado simple **entorno** prefabricado que contiene un piso básico para que el usuario sienta toma de tierra.
    * Para obtener más información sobre la teleportation con **MixedRealityCameraParent**, consulte [avanzado diseño - Teleportation y desplazamiento](#advanced-design---teleportation-and-locomotion)

**Programa de instalación skybox**
* Haga clic en **Ventana > iluminación > configuración**
* Haga clic en el círculo en el lado derecho de la **campo Skybox Material**
* Escriba "gray" y seleccione **SkyboxGray**

(Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)

![Establecer skybox](images/mr123-skyboxsetting-400px.jpg)
* Comprobar **Skybox** opción para poder ver asignado skybox degradado gris

![Opción de alternancia skybox](images/mr213-skyboxcheck-400px.jpg)
* La escena con MixedRealityCamera, entorno y skybox gris tendrá un aspecto similar al siguiente.

![Entorno MixedReality213](images/mr213-environment-600px.jpg)
* Haga clic en **archivo > Guardar escena como**
* **Guardar** la escena en la carpeta de escenas con cualquier nombre

## <a name="chapter-1---controller-visualization"></a>Capítulo 1: visualización de controlador

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a>Objetivos

* Obtenga información sobre cómo representar los modelos en modo de juego de Unity y en tiempo de ejecución de controlador de movimiento.

Windows Mixed Reality proporciona un modelo de controlador animado para la visualización del controlador. Hay varios enfoques que puede emplear para la visualización del controlador en la aplicación:
* Valor predeterminado: mediante el controlador predeterminado sin modificaciones
* Hybrid - utilizando el controlador de forma predeterminada, pero personalizar algunas de sus elementos o superposición de componentes de interfaz de usuario
* Reemplazo - mediante su propio personalizar un modelo 3D para el controlador

En este capítulo, aprendemos sobre los ejemplos de estas personalizaciones del controlador.

### <a name="instructions"></a>Instrucciones

* En el **proyecto** del panel, escriba **MotionControllers** en el cuadro de búsqueda. También puede encontrarlo en activos/HoloToolkit/entrada/prefabricados /.
* Arrastre el **MotionControllers** prefabricado en el **jerarquía** panel.
* Haga clic en el **MotionControllers** prefabricado en el **jerarquía** panel.

**MotionControllers prefabricado**

**MotionControllers** prefabricado tiene un **MotionControllerVisualizer** secuencia de comandos que proporciona las ranuras para los modelos de controlador alternativo. Si asigna sus propios modelos 3D personalizados como una mano o un filo y compruebe 'Siempre uso alternativo izquierda/derecha Model', los verá en lugar del modelo de forma predeterminada. Usaremos esta ranura en el capítulo 4 para reemplazar el modelo de controlador con un pincel.

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

**Instrucciones**
* En el **Inspector** del panel, haga doble clic en **MotionControllerVisualizer** secuencia de comandos para ver el código de Visual Studio

**Secuencia de comandos MotionControllerVisualizer**

El **MotionControllerVisualizer** y **MotionControllerInfo** clases proporcionan los medios para tener acceso y modificar los modelos del controlador predeterminado. **MotionControllerVisualizer** se suscribe a Unity **InteractionSourceDetected** eventos y automáticamente crea instancias de los modelos de controlador cuando se encuentran.

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

Los modelos de controlador se entregan según [la especificación glTF](https://github.com/KhronosGroup/glTF). Este formato se ha creado para proporcionar un formato común, al tiempo que mejora el proceso detrás de transmisión y desempaquetar los recursos en 3D. En este caso, se debe recuperar y cargar los modelos de controlador en tiempo de ejecución, como queremos que el usuario experimente lo más fácilmente posible, y no se garantiza la versión de los controladores de movimiento del usuario puede estar usando. Este curso, mediante el Kit de herramientas de realidad mixta, usa una versión del grupo Khronos [UnityGLTF proyecto](https://github.com/KhronosGroup/UnityGLTF).

Una vez que se ha entregado el controlador, pueden utilizar secuencias de comandos **MotionControllerInfo** para buscar las transformaciones de los elementos de un controlador específico, por lo que pueden colocarse correctamente.

En un capítulo posterior, se obtendrá información sobre cómo usar estas secuencias de comandos para asociar elementos de interfaz de usuario a los controladores.

*En algunos scripts, encontrará bloques de código con **#if! UNITY_EDITOR** o **UNITY_WSA**. Estos bloques de código se ejecutan solo en el tiempo de ejecución UWP al implementar en Windows. Esto es porque el conjunto de API usados por el editor de Unity y el tiempo de ejecución de la aplicación para UWP son diferentes.*
* **Guardar** la escena y haga clic en el **reproducir** botón.

Podrá ver la escena con los controladores de movimiento de los auriculares. Puede ver animaciones detalladas para los clics de botón, el movimiento de tecla de navegación y panel táctil táctil resaltado.

![MR213_Controller visualización predeterminada](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a>Capítulo 2: asociar elementos de interfaz de usuario para el controlador

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a>Objetivos

* Obtenga información acerca de los elementos de los controladores de movimiento
* Obtenga información sobre cómo asociar los objetos a partes específicas de los controladores

En este capítulo, obtendrá información sobre cómo agregar elementos de la interfaz de usuario para el controlador que el usuario puede tener acceso fácilmente y manipular en cualquier momento. También aprenderá a agregar un selector de colores simple mediante el panel táctil de entrada de la interfaz de usuario.

### <a name="instructions"></a>Instrucciones

* En el **proyecto** del panel, buscar **MotionControllerInfo** secuencia de comandos.
* Los resultados de búsqueda, haga doble clic en **MotionControllerInfo** secuencia de comandos para ver el código en Visual Studio.

**Secuencia de comandos MotionControllerInfo**

El primer paso es elegir qué elemento del controlador que desee asociar a la interfaz de usuario. Estos elementos se definen en **ControllerElementEnum** en **MotionControllerInfo.cs**.

![MR213 MotionControllerElements](images/mr213-motioncontrollerelements-1000px.jpg)
* **Página principal**
* **Menú**
* **Grasp**
* **Tecla de navegación**
* **Select**
* **Panel táctil**
* **Postura señalador** : este elemento representa la punta del controlador que señala hacia delante.

**Instrucciones**
* En el **proyecto** del panel, buscar **AttachToController** secuencia de comandos.
* Los resultados de búsqueda, haga doble clic en **AttachToController** secuencia de comandos para ver el código en Visual Studio.

**Secuencia de comandos AttachToController**

El **AttachToController** script proporciona una manera sencilla para asociar todos los objetos a un lateralidad del controlador especificado y el elemento.

En **AttachElementToController()**,
* Compruebe con diestro o zurdo **MotionControllerInfo.Handedness**
* Obtener un elemento específico del controlador mediante **MotionControllerInfo.TryGetElement()**
* Después de recuperar el elemento transformar desde el modelo de controlador primario, el objeto situado debajo de él y rotación o la posición local del objeto se establece en cero.

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

La manera más sencilla de usar **AttachToController** script es heredar de él, como hemos hecho en el caso de **ColorPickerWheel.** Simplemente reemplace el **OnAttachToController** y **OnDetatchFromController** funciones para realizar la instalación / desglose cuando el controlador se ha detectado o desconectado.

**Instrucciones**
* En el **proyecto** del panel, escriba en el cuadro de búsqueda **ColorPickerWheel**. También puede encontrarlo en activos/AppPrefabs /.
* Arrastre **ColorPickerWheel** prefabricado en el **jerarquía** panel.
* Haga clic en el **ColorPickerWheel** prefabricado en el **jerarquía** panel.
* En el **Inspector** del panel, haga doble clic en **ColorPickerWheel** secuencia de comandos para ver el código en Visual Studio.

![ColorPickerWheel prefabricado](images/mr213-colorpickerwheel-1000px.jpg)

**Secuencia de comandos ColorPickerWheel**

Puesto que **ColorPickerWheel** hereda **AttachToController**, muestra **diestro o zurdo** y **elemento** en el  **Inspector de** panel. Se adjuntará la interfaz de usuario para el elemento de panel táctil en el controlador de la izquierda.

![Secuencia de comandos ColorPickerWheel](images/mr213-attachtocontroller-300px.jpg)

**ColorPickerWheel** invalida la **OnAttachToController** y **OnDetatchFromController** para suscribirse al evento de entrada que se usará en el capítulo siguiente para la selección de color con panel táctil de entrada.

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
* **Guardar** la escena y haga clic en el **reproducir** botón.

**Método alternativo para asociar los objetos a los controladores**

Se recomienda que las secuencias de comandos heredan **AttachToController** e invalidar **OnAttachToController**. Sin embargo, esto no sea siempre posible. Una alternativa es usarlo como un componente independiente. Esto puede ser útil cuando desee adjuntar un prefabricado existente a un controlador sin refactorizar las secuencias de comandos. Simplemente haga que su clase esperar IsAttached para establecerse en true antes de realizar ninguna configuración. La manera más sencilla de hacerlo es mediante una corrutina de 'Start'.

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a>Capítulo 3: trabajar con la entrada del teclado táctil

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a>Objetivos

* Obtenga información sobre cómo obtener eventos de datos de entrada de teclado táctil
* Aprenda a usar la información de posición del eje de panel táctil para su experiencia de aplicación

### <a name="instructions"></a>Instrucciones

* En el **jerarquía** del panel, haga clic en **ColorPickerWheel**
* En el **Inspector** panel **Animatior**, haga doble clic en **ColorPickerWheelController**
* Podrá ver **animador** pestaña abierto

**Mostrar u ocultar la interfaz de usuario con el controlador de animación de Unity**

Para mostrar y ocultar el **ColorPickerWheel** la interfaz de usuario con la animación, estamos usando [sistema de animación de Unity](https://docs.unity3d.com/Manual/AnimationOverview.html). Establecer el **ColorPickerWheel**del **Visible** propiedad en true o false desencadenadores **mostrar** y **ocultar** desencadenadores de animación. **Mostrar** y **ocultar** parámetros se definen en el **ColorPickerWheelController** controlador de animación.

![Controlador de animación de Unity](images/mr123-animationcontroller-550px.jpg)

**Instrucciones**
* En el **jerarquía** panel, seleccione **ColorPickerWheel** prefabricado
* En el **Inspector** del panel, haga doble clic en **ColorPickerWheel** secuencia de comandos para ver el código de Visual Studio

**Secuencia de comandos ColorPickerWheel**

**ColorPickerWheel** se suscribe a Unity **InteractionSourceUpdated** eventos para escuchar eventos de teclado táctil.

En **InteractionSourceUpdated()**, la secuencia de comandos comprueba primero para asegurarse de que:
* es realmente un evento de teclado táctil (obj.state. **touchpadTouched**)
* se origina desde el controlador izquierdo (obj.state.source. **diestro o zurdo**)

Si se cumplen, coloque el panel táctil (obj.state. **touchpadPosition**) se asigna a **selectorPosition**.

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

En **Update()**, en función de **visible** propiedad, desencadena mostrar y ocultar los desencadenadores de animación en el componente de Animador del selector de colores

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

En **Update()**, **selectorPosition** se utiliza para convertir un rayo en colisionador de malla de la rueda de colores, que devuelve la posición de UV. Esta posición, a continuación, puede usarse para buscar las coordenadas de píxel y el valor de textura de la rueda de colores de color. Este valor es accesible para otros scripts a través de la **SelectedColor** propiedad.

![Detalles de rueda del selector de color](images/mr213-colorpickerwheel-raycast-700px.png)

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

## <a name="chapter-4---overriding-controller-model"></a>Capítulo 4: reemplazar el modelo de controlador

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a>Objetivos

* Obtenga información sobre cómo invalidar el modelo de controlador con un modelo 3D personalizado.

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a>Instrucciones

* Haga clic en **MotionControllers** en el **jerarquía** panel.
* Haga clic en el círculo en el lado derecho de la **alternativo controlador derecho** campo.
* Escriba en **' BrushController**' y seleccione el prefabricado verá en el resultado. Puede encontrarlo en activos/AppPrefabs/**BrushController**.
* Comprobar **Use siempre el modelo adecuado alternativo**

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

El **BrushController** prefabricado no tiene que incluirse en el **jerarquía** panel. Sin embargo, para desproteger sus componentes secundarios:
* En el **proyecto** del panel, escriba en **BrushController** y arrastre **BrushController** prefabricado en el **jerarquía** panel.

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

Encontrará el **sugerencia** componente en **BrushController**. Usaremos su transformación para dibujar líneas de inicio y detención.
* Eliminar el **BrushController** desde el **jerarquía** panel.
* **Guardar** la escena y haga clic en el **reproducir** botón. Podrá ver que el modelo de pincel reemplazado el controlador de movimiento derecho.

## <a name="chapter-5---painting-with-select-input"></a>Capítulo 5: pintar con seleccione entrada

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a>Objetivos

* Obtenga información sobre cómo usar el evento de botón de selección para iniciar y detener un dibujo de línea

### <a name="instructions"></a>Instrucciones

* Búsqueda **BrushController** prefabricado en el **proyecto** panel.
* En el **Inspector** del panel, haga doble clic en **BrushController** secuencia de comandos para ver el código en Visual Studio

**Secuencia de comandos BrushController**

**BrushController** se suscribe a la InteractionManager **InteractionSourcePressed** y **InteractionSourceReleased** eventos. Cuando **InteractionSourcePressed** se desencadena el evento, el pincel **dibujar** propiedad está establecida en true; cuando **InteractionSourceReleased** se desencadena el evento, el pincel **Dibujar** propiedad está establecida en false.

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

Mientras **dibujar** está establecido en true, el pincel que se generan los puntos en un Unity con instancias **LineRenderer**. Una referencia a este recurso prefabricado se mantiene en el pincel **trazo prefabricado** campo.

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

Para usar el color seleccionado actualmente de la rueda de selector de colores de la interfaz de usuario, **BrushController** debe tener una referencia a la **ColorPickerWheel** objeto. Dado que el **BrushController** prefabricado se crea una instancia en tiempo de ejecución como un controlador de reemplazo, tendrán todas las referencias a objetos de la escena debe establecerse en tiempo de ejecución. En este caso usamos **GameObject.FindObjectOfType** para localizar el **ColorPickerWheel**:

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
* **Guardar** la escena y haga clic en el **reproducir** botón. Podrá volver a dibujar las líneas y pintar con el botón de selección en el controlador derecho.

## <a name="chapter-6---object-spawning-with-select-input"></a>Capítulo 6: al generar el objeto con selección de entrada

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a>Objetivos

* Obtenga información sobre cómo usar Select y entender los eventos de entrada de botón
* Obtenga información sobre cómo crear instancias de objetos

### <a name="instructions"></a>Instrucciones

* En el **proyecto** del panel, escriba **ObjectSpawner** en el cuadro de búsqueda. También puede encontrarlo en activos/AppPrefabs /
* Arrastre el **ObjectSpawner** prefabricado en el **jerarquía** panel.
* Haga clic en **ObjectSpawner** en el **jerarquía** panel.
* **ObjectSpawner** tiene un campo denominado **Color origen**.
* Desde el **jerarquía** del panel, arrastre el **ColorPickerWheel** referencia en este campo.

![Objeto Spawner Inspector](images/mr213-objectspawnercolorpickerwheel-650px.jpg)
* Haga clic en el **ObjectSpawner** prefabricado en el **jerarquía** panel.
* En el **Inspector** del panel, haga doble clic en **ObjectSpawner** secuencia de comandos para ver el código en Visual Studio.

**Secuencia de comandos ObjectSpawner**

El **ObjectSpawner** crea una instancia de copias de una malla primitiva (cubo, esfera, cilindro) en el espacio. Cuando un **InteractionSourcePressed** se detecta comprueba la situación y, si es un **InteractionSourcePressType.Grasp** o **InteractionSourcePressType.Select** evento.

Para un **sujete** eventos, incrementa el índice del tipo actual de malla (esfera, cubo, cilindro)

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

Para un **seleccione** eventos, en **SpawnObject()**, un nuevo objeto se ha creado una instancia, sin principal y se lanzan en el mundo.

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detatch the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

El **ObjectSpawner** usa el **ColorPickerWheel** para establecer el color del material del objeto de visualización. Objetos generados se dada una instancia de este material, por lo que conservarán su color.
* **Guardar** la escena y haga clic en el **reproducir** botón.

Podrá cambiar los objetos con el botón de comprensión y generar objetos con el botón de selección.

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a>Compilar e implementar la aplicación portal de realidad mixta
* En Unity, seleccione **archivo > configuración de compilación**.
* Haga clic en **agregar escenas abierto** para agregar la escena actual para el **escenas en compilación**.
* Haz clic en **Compilación**.
* Crear un **nueva carpeta** denominada "Aplicación".
* Solo haga clic en el **aplicación** carpeta.
* Haga clic en **Seleccionar carpeta**.
* Cuando se realiza a Unity, aparecerá una ventana del explorador de archivos.
* Abra el **aplicación** carpeta.
* Haga doble clic en **YourSceneName.sln** el archivo de solución de Visual Studio.
* Uso de la barra de herramientas superior en Visual Studio, cambiar el destino de depuración a **versión** y de ARM para **X64**.
* Haga clic en la flecha desplegable situada junto al botón del dispositivo y seleccione **máquina Local**.
* Haga clic en **Depurar -> Iniciar sin depurar** en el menú o presione **Ctrl + F5**.

Ahora la aplicación se compila e instalada en el Portal de realidad mixta. Puede iniciar otra vez a través del menú Inicio en el Portal de realidad mixta.

## <a name="advanced-design---brush-tools-with-radial-layout"></a>Diseño avanzado - herramientas de pincel con diseño radial

![MixedReality213 principal](images/mr213-main-600px.jpg)

En este capítulo, obtendrá información sobre cómo reemplazar el modelo de controlador de movimiento predeterminado con una colección de la herramienta pincel personalizado. Como referencia, puede encontrar la escena completa **MixedReality213Advanced** en **escenas** carpeta.

### <a name="instructions"></a>Instrucciones

* En el **proyecto** del panel, escriba **BrushSelector** en el cuadro de búsqueda. También puede encontrarlo en activos/AppPrefabs /
* Arrastre el **BrushSelector** prefabricado en el **jerarquía** panel.
* Para la organización, cree un GameObject vacío denominado **pinceles**
* Arrastre las siguientes prefabricados desde el **proyecto** en el panel **pinceles**
    * Assets/AppPrefabs/**BrushFat**
    * Assets/AppPrefabs/**BrushThin**
    * Assets/AppPrefabs/**Eraser**
    * Assets/AppPrefabs/**MarkerFat**
    * Assets/AppPrefabs/**MarkerThin**
    * Assets/AppPrefabs/**Pencil**

![Pinceles](images/mixedreality213-brushes-250px.png)
* Haga clic en **MotionControllers** prefabricado en el **jerarquía** panel.
* En el **Inspector** del panel, desactive la opción **siempre uso alternativo derecha modelo** en el **visualizador del controlador de movimiento**
* En el **jerarquía** del panel, haga clic en **BrushSelector**
* **BrushSelector** tiene un campo denominado **ColorPicker**
* Desde el **jerarquía** del panel, arrastre el **ColorPickerWheel** en **ColorPicker** campo el **Inspector** panel.

![Asignar ColorPickerWheel al Selector de pincel](images/mr213-brushselector-500px.jpg)
* En el **jerarquía** panel **BrushSelector** prefabricado, seleccione el **menú** objeto.
* En el **Inspector** panel, en el **LineObjectCollection** componente, abra el **objetos** lista desplegable de la matriz. Verá 6 ranuras vacías.
* Desde el **jerarquía** del panel, arrastre cada uno de los prefabricados su elemento primarios en el **pinceles** GameObject en estas ranuras en cualquier orden. (Asegúrese de que está arrastrando el prefabricados desde la escena, no el prefabricados en la carpeta del proyecto).

![Selector de pincel](images/mr213-brushselectorbrushes-700px.jpg)

**BrushSelector prefabricado**

Puesto que la **BrushSelector** hereda **AttachToController**, muestra **diestro o zurdo** y **elemento** opciones en el  **Inspector de** panel. Hemos seleccionado **derecha** y **señalando suponer** para adjuntar las herramientas de pincel para el controlador derecho hacia delante.

El **BrushSelector** hace uso de dos utilidades:
* **Elipse**: usado para generar puntos en el espacio a lo largo de una forma de elipse.
* **LineObjectCollection**: distribuye objetos utilizando los puntos de generados por cualquier clase de línea (por ejemplo, la elipse). Esto es lo que vamos a usar para colocar nuestros pinceles a lo largo de la forma de elipse.

Cuando se combinan, estas utilidades se pueden usar para crear un menú radial.

**Secuencia de comandos LineObjectCollection**

**LineObjectCollection** tiene controles para el tamaño, posición y giro de objetos distribuidos a lo largo de su línea. Esto es útil para crear menús radiales, como el selector de pincel. Para crear la apariencia de los pinceles esa escala nada, como se aproximen a la posición central seleccionado, el **ObjectScale** curva picos en el centro y cirios en los bordes.

**Secuencia de comandos BrushSelector**

En el caso de los **BrushSelector**, hemos elegido usar animación procedimientos. En primer lugar, los modelos de pincel se distribuyen en una elipse por la **LineObjectCollection** secuencia de comandos. A continuación, cada pincel es responsable de mantener su posición en la mano del usuario según sus **DisplayMode** valor, que cambia en función de la selección. Nos decidimos por un enfoque de procedimiento porque la probabilidad alta de las transiciones de posición del pincel que se interrumpa, ya que el usuario selecciona pinceles. Mecanim animaciones pueden controlar las interrupciones de forma correcta, pero suele ser más complicado que una simple operación Lerp.

**BrushSelector** usa una combinación de ambos. Cuando se detecte una entrada de teclado táctil, opciones de pincel se hacen visibles y escalar verticalmente a lo largo del menú radial. Tras un período de tiempo de espera (que indica que el usuario ha realizado una selección) el pincel las opciones de escala hacia abajo de nuevo, dejando sólo el pincel seleccionado.

**Visualización de entrada de teclado táctil**

Incluso en casos donde el modelo de controlador se ha reemplazado por completo, puede ser útil mostrar la entrada en las entradas del modelo original. Esto ayuda a hacer que las acciones del usuario en realidad. Para el **BrushSelector** hemos decidido que el panel táctil brevemente visible cuando se recibe la entrada. Para hacerlo, recuperando el elemento de panel táctil desde el controlador, reemplazando su material con un material personalizado, a continuación, aplicar un degradado de color de ese material según el último panel táctil de tiempo se ha recibido la entrada.

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

**Selección de herramientas de pincel con la entrada del teclado táctil**

Cuando el selector de pincel detecta una entrada presionado del teclado táctil, comprueba la posición de la entrada para determinar si fue a la izquierda o derecha.

**Grosor del trazo con selectPressedAmount**

En lugar de la **InteractionSourcePressType.Select** eventos en el **InteractionSourcePressed()**, puede obtener el valor de la cantidad presionado a través de analógico **selectPressedAmount**. Este valor se puede recuperar en **InteractionSourceUpdated()**.

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

**Borrador** es un tipo especial de pincel que invalida la base de **pincel**del **DrawOverTime()** función. Aunque Draw es true, el borrador comprueba si su sugerencia tiene una intersección con los trazos existentes. Si es así, se agregan a una cola se puede reducir hacia abajo y eliminar.

## <a name="advanced-design---teleportation-and-locomotion"></a>Diseño avanzado - Teleportation y desplazamiento

Si desea permitir al usuario moverse por la escena con teleportation mediante la tecla de navegación, utilice **MixedRealityCameraParent** en lugar de **MixedRealityCamera**. También deberá agregar **InputManager** y **DefaultCusor**. Puesto que **MixedRealityCameraParent** ya incluye **MotionControllers** y **límite** como componentes secundarios, debe quitar las existentes  **MotionControllers** y **entorno** prefabricado.

### <a name="instructions"></a>Instrucciones

* En el **jerarquía** del panel, eliminar **MixedRealityCamera**, **entorno** y **MotionControllers**
* Desde el **panel proyecto**, busque y arrastre el prefabricados siguientes en el **jerarquía** panel:
    * Assets/AppPrefabs/Input/Prefabs/**MixedRealityCameraParent**
    * Assets/AppPrefabs/Input/Prefabs/**InputManager**
    * Assets/AppPrefabs/Input/Prefabs/Cursor/**DefaultCursor**

![Realidad mixta cámara primaria](images/mr213-cameraparent-300px.png)
* En el **jerarquía** del panel, haga clic en **Administrador de entrada**
* En el **Inspector** del panel, desplácese hacia abajo hasta la **Selector Simple de puntero único** sección
* Desde el **jerarquía** del panel, arrastre **DefaultCursor** en **Cursor** campo

![Asignación de DefaultCursor](images/mr213-defaultcursor-500px.png)
* **Guardar** la escena y haga clic en el **reproducir** botón. Podrá usar la tecla de navegación para girar izquierda/derecha o teleport.

## <a name="the-end"></a>Fin

Y es el final de este tutorial. Ha aprendido conceptos:
* Cómo trabajar con modelos de controlador de movimiento en el modo de juego Unity y en tiempo de ejecución.
* Cómo usar diferentes tipos de eventos de botón y sus aplicaciones.
* Cómo los elementos de interfaz de usuario en la parte superior del controlador de superposición o personalizarlo completamente.

Ahora está listo para comenzar a crear su propia experiencia envolvente con controladores de movimiento.

## <a name="completed-scenes"></a>Segundo plano completada

* En Unity **proyecto** panel, haga clic en el **escenas** carpeta.
* Encontrará dos sceens Unity **MixedReality213** y **MixedReality213Advanced**.
    * **MixedReality213**: Escena completado con el único pincel
    * **MixedReality213Advanced**: Escena completada con varios pincel con el ejemplo de cantidad presione del botón de selección

## <a name="see-also"></a>Vea también

* [Archivos de proyecto MR 213 de entrada](https://github.com/Microsoft/MixedReality213)
* [Kit de herramientas de realidad mixta - escena de la prueba del controlador de movimiento](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [Kit de herramientas de realidad mixta - mecánica de arrastre](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [Instrucciones de desarrollo del controlador de movimiento](motion-controllers.md)
