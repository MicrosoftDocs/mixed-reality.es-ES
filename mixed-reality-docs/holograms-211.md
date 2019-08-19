---
title: Entrada MR 211-gesto
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para obtener información detallada sobre los conceptos de gestos.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, Academy, tutorial, gesto
ms.openlocfilehash: 76d2b4c0ac3d0a3783b091f7dc8c39548a18b548
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522460"
---
>[!NOTE]
>Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.  Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

# <a name="mr-input-211-gesture"></a>Entrada MR 211: Gesto

Los [gestos](gestures.md) convierten la intención del usuario en acción. Con los gestos, los usuarios pueden interactuar con los hologramas. En este curso, aprenderá a realizar un seguimiento de las manos del usuario, a responder a la entrada del usuario y a enviar comentarios al usuario en función del estado y la ubicación de la mano.

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

En los [conceptos básicos de MR 101](holograms-101.md), usamos un sencillo gesto de TAP de aire para interactuar con los hologramas. Ahora, pasaremos más allá del gesto de TAP de aire y exploraremos los nuevos conceptos para:

* Detecta cuándo se realiza el seguimiento de la mano del usuario y proporciona comentarios al usuario.
* Use un gesto de navegación para rotar los hologramas.
* Proporcione comentarios cuando el usuario esté a punto de salir de la vista.
* Use los eventos de manipulación para permitir que los usuarios muevan hologramas con sus manos.

En este curso, volveremos a visitar el explorador de **modelos**de proyectos de Unity, que hemos creado en la [entrada Mr 210](holograms-210.md). Nuestro amigo Astronaut está de regreso para ayudarnos en nuestra exploración de estos nuevos conceptos de gestos.

>[!IMPORTANT]
>Los vídeos insertados en cada uno de los capítulos siguientes se grabaron con una versión anterior de Unity y el kit de herramientas de realidad mixta. Aunque las instrucciones paso a paso son precisas y actuales, es posible que vea scripts y objetos visuales en los vídeos correspondientes que no están actualizados. Los vídeos permanecen incluidos para posterity y porque todavía se aplican los conceptos descritos.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td>Entrada MR 211: Gesto</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de comenzar

### <a name="prerequisites"></a>Requisitos previos

* Un equipo con Windows 10 configurado con las [herramientas](install-the-tools.md)correctas instaladas.
* Funcionalidad básica C# de programación.
* Debe haber completado los [principios básicos 101](holograms-101.md).
* Debe haber completado la [entrada MR 210](holograms-210.md).
* Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Archivos de proyecto

* Descargue los [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) requeridos por el proyecto. Requiere Unity 2017,2 o posterior.
* Elimine el archivo de los archivos en el escritorio o en otra ubicación de fácil acceso.

>[!NOTE]
>Si desea examinar el código fuente antes de la descarga, está [disponible en github](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).

### <a name="errata-and-notes"></a>Erratas y notas

* "Habilitar Solo mi código" debe estar deshabilitado *(* desactivado) en Visual Studio en herramientas-> opciones-> depuración para alcanzar puntos de interrupción en el código.

## <a name="chapter-0---unity-setup"></a>Capítulo 0: configuración de Unity

### <a name="instructions"></a>Instrucciones

1. Inicia Unity.
2. Seleccione **abrir**.
3. Navegue hasta la carpeta de gestos que ha eliminado previamente.
4. Busque y seleccione la carpeta de **Inicio**/del**Explorador de modelos** .
5. Haga clic en el botón **Seleccionar carpeta** .
6. En el panel **proyecto** , expanda la carpeta **escenas** .
7. Haga doble clic en **ModelExplorer** Scene para cargarlo en Unity.

### <a name="building"></a>Compilación

1. En Unity, seleccione **archivo > configuración de compilación**.
2. Si **Scenes/ModelExplorer** no aparece en **escenas en la compilación**, haga clic en **Agregar escenas abiertas** para agregar la escena.
3. Si está desarrollando específicamente para HoloLens, establezca el **dispositivo de destino** en **hololens**. De lo contrario, déjelo en **cualquier dispositivo**.
4. Asegúrese de que el **tipo de compilación** está establecido en **D3D** y que el **SDK** está establecido en la **versión más reciente instalada** (que debe ser SDK 16299 o posterior).
5. Haz clic en **Compilación**.
6. Cree una **nueva carpeta** denominada "app".
7. Haga clic en la carpeta de la **aplicación** .
8. Presione **Seleccionar carpeta** y Unity comenzará a compilar el proyecto para Visual Studio.

Cuando se haya realizado Unity, aparecerá una ventana del explorador de archivos.

1. Abra la carpeta de la **aplicación** .
2. Abra la **solución ModelExplorer de Visual Studio**.

Si se implementa en HoloLens:

1. Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x86**.
2. Haga clic en la flecha desplegable situada junto al botón equipo local y seleccione **equipo remoto**.
3. Escriba **la dirección IP del dispositivo HoloLens** y establezca el modo de autenticación en **universal (protocolo sin cifrar)** . Haga clic en **Seleccionar**. Si no conoce la dirección IP del dispositivo, consulte **configuración > redes & Internet > opciones avanzadas**.
4. En la barra de menús superior, haga clic en depurar **-> iniciar sin** depurar o presione **Ctrl + F5**. Si esta es la primera vez que se implementa en el dispositivo, tendrá que [emparejarla con Visual Studio](using-visual-studio.md#pairing-your-device-hololens).
5. Cuando la aplicación se haya implementado, descartará el **Fitbox** con un **gesto de selección**.

Si se implementa en un auricular envolvente:

1. Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x64**.
2. Asegúrese de que el destino de implementación está establecido en **equipo local**.
3. En la barra de menús superior, haga clic en depurar **-> iniciar sin** depurar o presione **Ctrl + F5**.
4. Cuando la aplicación se haya implementado, descarte el **Fitbox** mediante la extracción del desencadenador en un controlador de movimiento.

>[!NOTE]
>Es posible que observe algunos errores rojos en el panel de errores de Visual Studio. Es seguro ignorarlos. Cambie al panel de salida para ver el progreso real de la compilación. Los errores en el panel de salida requerirán que se realice una corrección (la mayoría de las veces se deben a un error en un script).

## <a name="chapter-1---hand-detected-feedback"></a>Capítulo 1: comentarios de la mano detectados

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a>Objetivos

* Suscríbase a los eventos de seguimiento de la mano.
* Use los comentarios del cursor para mostrar a los usuarios Cuándo se realiza el seguimiento de una mano.

### <a name="instructions"></a>Instrucciones

* En el panel **jerarquía** , expanda el objeto **InputManager** .
* Busque y seleccione el objeto **GesturesInput** .

El script **InteractionInputSource.CS** realiza estos pasos:

1. Se suscribe a los eventos InteractionSourceDetected y InteractionSourceLost.
2. Establece el estado de HandDetected.
3. Cancela la suscripción de los eventos InteractionSourceDetected y InteractionSourceLost.

A continuación, actualizaremos el cursor de la [entrada MR 210](holograms-210.md) a uno que muestra comentarios en función de las acciones del usuario.

1. En el panel **jerarquía** , seleccione el objeto **cursor** y elimínelo.
2. En el panel **proyecto** , busque **CursorWithFeedback** y arrástrelo al panel **jerarquía** .
3. Haga clic en **InputManager** en el panel de **jerarquías** y, a continuación, arrastre el objeto **CursorWithFeedback** desde la **jerarquía** al campo **cursor** de **SimpleSinglePointerSelector**de InputManager, situado en la parte inferior de la **Inspector**.
4. Haga clic en **CursorWithFeedback** en la **jerarquía**.
5. En el panel **Inspector** , expanda **datos de estado de cursor** en el script de cursor de **objeto** .

Los **datos de estado del cursor** funcionan de la siguiente manera:

* Cualquier estado **observado** significa que no se detecta ninguna mano y que el usuario simplemente está buscando.
* Cualquier estado de **interacción** significa que se detecta una mano o un controlador.
* Cualquier estado de **mantener el mouse** significa que el usuario está examinando un holograma.

### <a name="build-and-deploy"></a>Compilación e implementación

* En Unity, use la **configuración de compilación de > de archivos** para recompilar la aplicación.
* Abra la carpeta de la **aplicación** .
* Si aún no está abierto, abra la **solución ModelExplorer de Visual Studio**.
  * (Si ya ha creado o implementado este proyecto en Visual Studio durante la configuración, puede abrir esa instancia de VS y hacer clic en "recargar todo" cuando se le solicite).
* En Visual Studio, haga clic en depurar **-> iniciar sin** depurar o presione **Ctrl + F5**.
* Después de que la aplicación se implemente en HoloLens, descartará el fitbox con el gesto de punteo de aire.
* Mueva la mano a la vista y apunte el dedo del índice al cielo para iniciar el seguimiento de la mano.
* Mueva la mano a la izquierda, a la derecha, hacia arriba y hacia abajo.
* Observe cómo cambia el cursor cuando se detecta la mano y, a continuación, se pierde de la vista.
* Si se encuentra en un casco envolvente, tendrá que conectar y desconectar el controlador. Esta información es menos interesante en un dispositivo envolvente, ya que un controlador conectado siempre estará "disponible".

## <a name="chapter-2---navigation"></a>Capítulo 2: navegación

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a>Objetivos

* Use los eventos de gestos de navegación para rotar el Astronaut.

### <a name="instructions"></a>Instrucciones

Para usar los gestos de navegación en nuestra aplicación, vamos a editar **GestureAction.CS** para girar objetos cuando se produce el gesto de navegación. Además, agregaremos comentarios al cursor para que se muestren cuando la navegación esté disponible.

1. En el panel **jerarquía** , expanda **CursorWithFeedback**.
2. En la carpeta hologramas, busque el recurso **ScrollFeedback** .
3. Arrastre y coloque el recurso prefabricado de **ScrollFeedback** en **CursorWithFeedback** GameObject en la **jerarquía**.
4. Haga clic en **CursorWithFeedback**.
5. En el panel **Inspector** , haga clic en el botón **Agregar componente** .
6. En el menú, escriba en el cuadro de búsqueda **CursorFeedback**. Seleccione el resultado de la búsqueda.
7. Arrastre y coloque el objeto **ScrollFeedback** de la **jerarquía** en la propiedad **desplazamiento de objeto de juego detectado** del componente **cursor feedback** en el **Inspector**.
8. En el panel **jerarquía** , seleccione el objeto **AstroMan** .
9. En el panel **Inspector** , haga clic en el botón **Agregar componente** .
10. En el menú, escriba en la acción de **gestos**del cuadro de búsqueda. Seleccione el resultado de la búsqueda.

A continuación, Abra **GestureAction.CS** en Visual Studio. En el ejercicio de codificación 2. c, edite el script para hacer lo siguiente:

1. **Gire el objeto AstroMan** cada vez que se lleve a cabo un gesto de navegación.
2. Calcule el valor de **rotationFactor** para controlar la cantidad de giro aplicada al objeto.
3. **Gire el objeto** alrededor del eje y cuando el usuario mueva su mano a la izquierda o a la derecha.

Complete los ejercicios de codificación 2. c en el script o reemplace el código por la solución completada que aparece a continuación:

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

Observará que los demás eventos de navegación ya se han rellenado con cierta información. La GameObject se envía a la pila modal InputSystem's del kit de herramientas, por lo que el usuario no tiene que mantener el foco en el Astronaut una vez que se ha iniciado la rotación. En consecuencia, se extrae el GameObject de la pila una vez que se completa el gesto.

### <a name="build-and-deploy"></a>Compilación e implementación

1. Vuelva a compilar la aplicación en Unity y, después, compile e implemente desde Visual Studio para ejecutarla en HoloLens.
2. Mira el Astronaut, dos flechas deben aparecer a cada lado del cursor. Este nuevo visual indica que el Astronaut se puede girar.
3. Coloque la mano en la posición listo (el dedo índice apunta hacia el cielo) para que HoloLens empiece a realizar un seguimiento de la mano.
4. Para girar el Astronaut, baje el dedo del índice a una posición de pinch y, a continuación, mueva la mano hacia la izquierda o hacia la derecha para desencadenar el gesto de NavigationX.

## <a name="chapter-3---hand-guidance"></a>Capítulo 3: orientación a mano

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a>Objetivos

* Use la puntuación de la **Guía de mano** para ayudar a predecir cuándo se perderá el seguimiento de manos.
* Proporcione **comentarios sobre el cursor** para mostrar Cuándo el usuario está cerca del borde de la cámara de la vista.

### <a name="instructions"></a>Instrucciones

1. En el panel **jerarquía** , seleccione el objeto **CursorWithFeedback** .
2. En el panel **Inspector** , haga clic en el botón **Agregar componente** .
3. En el menú, escriba en la guía de **mano**del cuadro de búsqueda. Seleccione el resultado de la búsqueda.
4. En la carpeta **hologramas** del panel de **proyecto** , busque el recurso **HandGuidanceFeedback** .
5. Arrastre y coloque el recurso **HandGuidanceFeedback** en la propiedad **indicador de orientación a mano** del panel **Inspector** .

### <a name="build-and-deploy"></a>Compilación e implementación

* Vuelva a compilar la aplicación en Unity y, después, compile e implemente desde Visual Studio para experimentar la aplicación en HoloLens.
* Traiga su mano a la vista y eleve el dedo del índice para realizar el seguimiento.
* Empiece a girar Astronaut con el gesto de navegación (acerque el dedo del índice y Thumb juntos).
* Mueva la mano a la izquierda, a la derecha, hacia arriba y hacia abajo.
* A medida que su mano esté cerca del borde del marco de gestos, debe aparecer una flecha junto al cursor para avisarle de que se perderá el seguimiento de la mano. La flecha indica la dirección a la que debe DESPLACESE para evitar que se pierda el seguimiento.

## <a name="chapter-4---manipulation"></a>Capítulo 4: manipulación

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a>Objetivos

* Use los eventos de manipulación para trasladar el Astronaut con las manos.
* Proporcione comentarios sobre el cursor para que el usuario sepa cuándo se puede usar la manipulación.

### <a name="instructions"></a>Instrucciones

GestureManager.cs y AstronautManager.cs nos permiten hacer lo siguiente:

1. Use la palabra clave de voz "**Move Astronaut**" para habilitar los gestos de **manipulación** y "**rotar Astronaut**" para deshabilitarlos.
2. Cambie a responder al reconocedor de gestos de **manipulación**.

Empecemos.

1. En el panel **jerarquía** , cree un nuevo GameObject vacío. Asígnele el nombre "**AstronautManager**".
2. En el panel **Inspector** , haga clic en el botón **Agregar componente** .
3. En el menú, escriba en el cuadro de búsqueda **Astronaut Manager**. Seleccione el resultado de la búsqueda.
4. En el panel **Inspector** , haga clic en el botón **Agregar componente** .
5. En el menú, escriba en el cuadro de búsqueda **origen de entrada de voz**. Seleccione el resultado de la búsqueda.

Ahora agregaremos los comandos de voz necesarios para controlar el estado de interacción de Astronaut.

1. Expanda la sección **palabras clave** en el **Inspector**.
2. Haga clic **+** en el lado derecho para agregar una nueva palabra clave.
3. Escriba la palabra clave como **Move Astronaut**. Si lo desea, no dude en agregar un método abreviado de teclado.
4. Haga clic **+** en el lado derecho para agregar una nueva palabra clave.
5. Escriba la palabra clave como **rotar Astronaut**. Si lo desea, no dude en agregar un método abreviado de teclado.
6. El código de controlador correspondiente se puede encontrar en **GestureAction.CS**, en el controlador **ISpeechHandler. OnSpeechKeywordRecognized** .

![Cómo configurar el origen de entrada de voz para el capítulo 4](images/holograms211-speech.png)

A continuación, configuraremos los comentarios de manipulación en el cursor.

1. En la carpeta **hologramas** del panel de **proyecto** , busque el recurso **PathingFeedback** .
2. Arrastre y coloque el recurso prefabricado **PathingFeedback** en el objeto **CursorWithFeedback** de la **jerarquía**.
3. En el panel **jerarquía** , haga clic en **CursorWithFeedback**.
4. Arrastre y coloque el objeto **PathingFeedback** de la **jerarquía** en la propiedad del **objeto de juego Thing detectado** del componente **cursor feedback** del **Inspector**.

Ahora debemos agregar código a **GestureAction.CS** para habilitar lo siguiente:

1. Agregue código a la función **IManipulationHandler. OnManipulationUpdated** , que moverá el Astronaut cuando se detecte un gesto de **manipulación** .
2. Calcule el **Vector de movimiento** para determinar dónde se debe mover el Astronaut en función de la posición de la mano.
3. **Mueva** el Astronaut a la nueva posición.

Complete la codificación ejercicio 4. a en **GestureAction.CS**o use nuestra solución completada a continuación:

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a>Compilación e implementación

* Recompile en Unity y, después, compile e implemente desde Visual Studio para ejecutar la aplicación en HoloLens.
* Mueva la mano hacia delante de HoloLens y eleve el dedo del índice para que se pueda realizar el seguimiento.
* Centre el cursor sobre el Astronaut.
* Por ejemplo, "Move Astronaut" para trasladar Astronaut con un gesto de manipulación.
* Deben aparecer cuatro flechas alrededor del cursor para indicar que el programa responderá ahora a los eventos de manipulación.
* Baje el dedo del índice hasta el pulgar y manténgalos reducidos juntos.
* A medida que mueve la mano, el Astronaut se moverá también (esta es la manipulación).
* Eleve el dedo del índice para dejar de manipular el Astronaut.
* Nota: Si no se indica "mover Astronaut" antes de mover la mano, se usará en su lugar el gesto de navegación.
* Por ejemplo, "rotar Astronaut" para volver al estado Rotatable.

## <a name="chapter-5---model-expansion"></a>Capítulo 5: expansión del modelo

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a>Objetivos

* Expanda el modelo Astronaut en varias partes más pequeñas con las que el usuario pueda interactuar.
* Mueva cada pieza individualmente mediante gestos de navegación y manipulación.

### <a name="instructions"></a>Instrucciones

En esta sección, se realizarán las siguientes tareas:

1. Agregue una nueva palabra clave "**Expand Model**" para expandir el modelo Astronaut.
2. Agregue una nueva palabra clave "**RESET Model**" para devolver el modelo a su forma original.

Haremos esto agregando dos palabras clave más al origen de entrada de voz del capítulo anterior. También mostraremos otra manera de controlar los eventos de reconocimiento.

1. Haga clic en atrás en **AstronautManager** en el **Inspector** y expanda la sección **palabras clave** en el **Inspector**.
2. Haga clic **+** en el lado derecho para agregar una nueva palabra clave.
3. Escriba la palabra clave como **modelo de expansión**. Si lo desea, no dude en agregar un método abreviado de teclado.
4. Haga clic **+** en el lado derecho para agregar una nueva palabra clave.
5. Escriba la palabra clave como **restablecer modelo**. Si lo desea, no dude en agregar un método abreviado de teclado.
6. En el panel **Inspector** , haga clic en el botón **Agregar componente** .
7. En el menú, escriba en el cuadro de búsqueda **controlador de entrada de voz**. Seleccione el resultado de la búsqueda.
8. Check **es el agente de escucha global**, ya que queremos que estos comandos funcionen independientemente de la GameObject a la que nos centramos.
9. Haga clic **+** en el botón y seleccione **expandir modelo** en la lista desplegable palabra clave.
10. Haga clic en en respuesta y arrastre el **AstronautManager** desde la **jerarquía** hasta el campo **ninguno (objeto).** **+**
11. Ahora, haga clic en la lista desplegable **no función** , seleccione **AstronautManager**y **ExpandModelCommand**.
12. Haga clic en el botón del **+** controlador de entrada de voz y seleccione **restablecer modelo** en la lista desplegable palabra clave.
13. Haga clic en en respuesta y arrastre el **AstronautManager** desde la **jerarquía** hasta el campo **ninguno (objeto).** **+**
14. Ahora, haga clic en la lista desplegable **no función** , seleccione **AstronautManager**y **ResetModelCommand**.

![Cómo configurar el origen y el controlador de entrada de voz para el capítulo 5](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a>Compilación e implementación

* Pruébalo. Compile e implemente la aplicación en HoloLens.
* Por ejemplo, **expanda modelo** para ver el modelo Astronaut expandido.
* Use la **navegación** para girar partes individuales del palo de Astronaut.
* Por ejemplo, **mueva Astronaut** y, a continuación, use la **manipulación** para desplace partes individuales del palo de Astronaut.
* Por ejemplo, **gire Astronaut** para volver a girar las piezas.
* Por ejemplo, **restablezca el modelo** para devolver el Astronaut a su forma original.

## <a name="the-end"></a>Fin

¡Enhorabuena! Ya ha completado **la entrada Mr 211: Movimiento**.

* Sabe cómo detectar y responder a los eventos de seguimiento, navegación y manipulación.
* Comprende la diferencia entre los gestos de navegación y manipulación.
* Sabe cómo cambiar el cursor para proporcionar comentarios visuales sobre cuándo se detecta una mano, Cuándo se va a perder una mano y cuándo un objeto admite distintas interacciones (navegación frente a manipulación).
