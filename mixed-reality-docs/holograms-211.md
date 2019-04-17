---
title: Entrada MR 211 - gesto
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para conocer los detalles de los conceptos de gesto.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, academy, tutorial, movimiento
ms.openlocfilehash: 76d2b4c0ac3d0a3783b091f7dc8c39548a18b548
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605399"
---
>[!NOTE]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.  Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.  Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.

# <a name="mr-input-211-gesture"></a>Entrada MR 211: Gesto

[Los gestos](gestures.md) convertir la intención del usuario en acción. Con los gestos, los usuarios pueden interactuar con hologramas. En este curso, se obtendrá información sobre cómo realizar un seguimiento de las manos del usuario, responder a entradas del usuario, y ofrecer comentarios al usuario por lado estado y la ubicación.

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

En [MR Fundamentos 101](holograms-101.md), usamos un gesto de pulsar de aire simple para interactuar con nuestra hologramas. Ahora, podrá ir más allá del gesto de pulsar en el aire y explorar conceptos nuevos que:

* Detectar cuándo se está realizando un seguimiento de la mano del usuario y proporcionar comentarios al usuario.
* Usar un gesto de exploración se va a girar nuestro hologramas.
* Proporcionar comentarios al manual del usuario que se va a dejar fuera de la vista.
* Usar eventos de manipulación para permitir que los usuarios se desplacen hologramas con sus manos.

En este curso, volveremos a proyecto Unity **el Explorador de modelos**, que se basa [MR entrada 210](holograms-210.md). Es nuestro amigo astronautas a ayudarnos en nuestra exploración de estos nuevos conceptos de gesto.

>[!IMPORTANT]
>Los vídeos insertados en cada uno de los siguientes capítulos se guardó usando una versión anterior de Unity y el Kit de herramientas de realidad mixta. Aunque las instrucciones paso a paso son actuales y precisas, puede ver las secuencias de comandos y los objetos visuales en los vídeos correspondientes que no están actualizados. Los vídeos permanecen incluidos para la posterioridad y porque se tratan los conceptos se siguen aplican.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td>Entrada MR 211: Gesto</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de empezar

### <a name="prerequisites"></a>Requisitos previos

* Un equipo con Windows 10 configurado con el valor correcto [herramientas instaladas](install-the-tools.md).
* Básica C# capacidad de programación.
* Debe haber completado [MR Fundamentos 101](holograms-101.md).
* Debe haber completado [MR entrada 210](holograms-210.md).
* Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Archivos de proyecto

* Descargue el [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) requerida por el proyecto. Requiere Unity 2017.2 o posterior.
* Extraer del archivo los archivos en el escritorio o en otros más fáciles de alcanzar la ubicación.

>[!NOTE]
>Si desea buscar en el código de origen antes de descargar, tiene [disponible en GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).

### <a name="errata-and-notes"></a>Erratas y notas

* "Habilitar Solo mi código" debe deshabilitarse (*unchecked*) en Visual Studio en Herramientas -> Opciones -> depuración con el fin de alcanzar los puntos de interrupción en el código.

## <a name="chapter-0---unity-setup"></a>Capítulo 0: instalación de Unity

### <a name="instructions"></a>Instrucciones

1. Inicie Unity.
2. Seleccione **abierto**.
3. Navegue hasta la **gesto** carpeta que anteriormente no archivados.
4. Busque y seleccione el **iniciando**/**el Explorador de modelos** carpeta.
5. Haga clic en el **Seleccionar carpeta** botón.
6. En el **proyecto** del panel, expanda el **escenas** carpeta.
7. Haga doble clic en **ModelExplorer** escena para cargarlo en Unity.

### <a name="building"></a>Compilación

1. En Unity, seleccione **archivo > configuración de compilación**.
2. Si **escenas/ModelExplorer** no aparece en **escenas en compilación**, haga clic en **agregar escenas abierto** para agregar la escena.
3. Si está desarrollando específicamente para HoloLens, establezca **dispositivo de destino** a **HoloLens**. En caso contrario, déjelo en **cualquier dispositivo**.
4. Asegúrese de **tipo Build** está establecido en **D3D** y **SDK** está establecido en **más reciente instalado** (que debe ser SDK 16299 o posterior).
5. Haz clic en **Compilación**.
6. Crear un **nueva carpeta** denominada "Aplicación".
7. Solo haga clic en el **aplicación** carpeta.
8. Presione **seleccionar la carpeta** y Unity empezará a compilar el proyecto de Visual Studio.

Cuando se realiza a Unity, aparecerá una ventana del explorador de archivos.

1. Abra el **aplicación** carpeta.
2. Abra el **ModelExplorer Visual Studio solución**.

Si la implementación en HoloLens:

1. Uso de la barra de herramientas superior en Visual Studio, cambiar el destino de depuración a **versión** y de ARM para **x86**.
2. Haga clic en la flecha de lista desplegable situada junto al botón de la máquina Local y seleccione **máquina remota**.
3. Escriba **su dirección IP del dispositivo HoloLens** y establezca el modo de autenticación en **Universal (protocolo sin cifrar)**. Haga clic en **Seleccionar**. Si no conoce la dirección IP del dispositivo, busque en **configuración > red e Internet > Opciones avanzadas**.
4. En la barra de menús superior, haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**. Si se trata de la primera vez que la implementación en el dispositivo, deberá [emparejarlo con Visual Studio](using-visual-studio.md#pairing-your-device-hololens).
5. Cuando haya implementado la aplicación, descartar los **Fitbox** con un **seleccione gesto**.

Si la implementación en un auricular envolvente:

1. Uso de la barra de herramientas superior en Visual Studio, cambiar el destino de depuración a **versión** y de ARM para **x64**.
2. Asegúrese de que el destino de implementación se establece en **máquina Local**.
3. En la barra de menús superior, haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**.
4. Cuando haya implementado la aplicación, descartar los **Fitbox** extrayendo el desencadenador en un controlador de movimiento.

>[!NOTE]
>Es posible que observe algunos errores rojo en el panel de errores de Visual Studio. Es seguro pasarlos por alto. Progreso de la compilación conmutador al panel de salida para ver los costes reales. Errores en el panel de salida, deberá realizar una corrección (la mayoría suelen deberse a un error en una secuencia de comandos).

## <a name="chapter-1---hand-detected-feedback"></a>Capítulo 1: comentarios de mano detectado

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a>Objetivos

* Suscribirse para entregar eventos de seguimiento.
* Use la información del cursor para mostrar a los usuarios cuando se está realizando un seguimiento de una mano.

### <a name="instructions"></a>Instrucciones

* En el **jerarquía** del panel, expanda el **InputManager** objeto.
* Busque y seleccione el **GesturesInput** objeto.

El **InteractionInputSource.cs** script sigue estos pasos:

1. Se suscribe a los eventos InteractionSourceDetected y InteractionSourceLost.
2. Establece el estado HandDetected.
3. Cancela la suscripción de los eventos InteractionSourceDetected y InteractionSourceLost.

A continuación, se actualizará el cursor de [MR entrada 210](holograms-210.md) en uno que se muestran comentarios dependiendo de las acciones del usuario.

1. En el **jerarquía** panel, seleccione el **Cursor** objeto y elimínelo.
2. En el **proyecto** del panel, busque **CursorWithFeedback** y arrástrelo el **jerarquía** panel.
3. Haga clic en **InputManager** en el **jerarquía** panel, a continuación, arrastre el **CursorWithFeedback** objeto desde el **jerarquía** en el Del InputManager **SimpleSinglePointerSelector**del **Cursor** campo, en la parte inferior de la **Inspector**.
4. Haga clic en el **CursorWithFeedback** en el **jerarquía**.
5. En el **Inspector** del panel, expanda **datos de estado del Cursor** en el **objeto Cursor** secuencia de comandos.

El **datos de estado del Cursor** funciona como esto:

* Cualquier **observación** estado significa que no se detecta ningún mano y el usuario simplemente está mirando.
* Cualquier **Interact** estado significa que se detecte una mano o el controlador.
* Cualquier **mantenga el mouse** estado significa que el usuario está viendo un holograma.

### <a name="build-and-deploy"></a>Compilación e implementación

* En Unity, utilice **archivo > configuración de compilación** para recompilar la aplicación.
* Abra el **aplicación** carpeta.
* Si aún no está abierto, abra el **solución de Visual Studio ModelExplorer**.
  * (Si ya creado o implementado este proyecto en Visual Studio durante la instalación, a continuación, puede abrir esa instancia de VS y haga clic en 'Volver a cargar todo' cuando se le solicite).
* En Visual Studio, haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**.
* Después de la aplicación se implementa en el HoloLens, descarte la fitbox con el gesto de pulsar en el aire.
* Mover la mano en la vista y seleccione el dedo índice el cielo para iniciar el seguimiento de mano.
* Mover la mano izquierda, derecha, arriba y abajo.
* Vea cómo el cursor cambia cuando se detecta y, a continuación, se pierde de vista de la mano.
* Si se encuentra en un auricular envolvente, tendrá que conectar y desconectar el controlador. Estos comentarios se vuelve menos interesantes en un dispositivo envolvente, como un controlador conectado siempre será "disponible".

## <a name="chapter-2---navigation"></a>Capítulo 2: navegación

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a>Objetivos

* Use los eventos de gestos de navegación para rotar a los astronautas.

### <a name="instructions"></a>Instrucciones

Para usar gestos de navegación en nuestra aplicación, vamos a editar **GestureAction.cs** girar objetos cuando se produce el gesto de navegación. Además, vamos a agregar comentarios al cursor para mostrar cuando la navegación está disponible.

1. En el **jerarquía** del panel, expanda **CursorWithFeedback**.
2. En el **hologramas** carpeta, busque la **ScrollFeedback** activo.
3. Arrastre y coloque el **ScrollFeedback** prefabricado hasta el **CursorWithFeedback** GameObject en el **jerarquía**.
4. Haga clic en **CursorWithFeedback**.
5. En el **Inspector** del panel, haga clic en el **Agregar componente** botón.
6. En el menú, escriba en el cuadro de búsqueda **CursorFeedback**. Seleccione el resultado de búsqueda.
7. Arrastrar y colocar el **ScrollFeedback** objeto desde el **jerarquía** en el **objeto de juego de desplazamiento detectado** propiedad en el **comentarios del Cursor**componente en el **Inspector**.
8. En el **jerarquía** panel, seleccione el **AstroMan** objeto.
9. En el **Inspector** del panel, haga clic en el **Agregar componente** botón.
10. En el menú, escriba en el cuadro de búsqueda **acción de gesto**. Seleccione el resultado de búsqueda.

A continuación, abra **GestureAction.cs** en Visual Studio. En la codificación ejercicio 2.c, edite la secuencia de comandos para hacer lo siguiente:

1. **Girar el AstroMan** objeto cada vez que se realiza un gesto de navegación.
2. Calcular la **rotationFactor** para controlar la cantidad de giro que se aplican al objeto.
3. **Girar el objeto** alrededor del eje y cuando el usuario mueve la mano izquierda o derecha.

Codificación completa ejercita 2.c en la secuencia de comandos o reemplace el código con la solución completa a continuación:

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

Observará que los otros eventos de exploración ya se rellenan con alguna información. Insertamos el GameObject en el Kit de herramientas pila modal del InputSystem, por lo que el usuario no tiene que mantener el foco en los astronautas una vez comenzada la rotación. En consecuencia, se extraiga el GameObject la pila una vez completado el gesto.

### <a name="build-and-deploy"></a>Compilación e implementación

1. Vuelva a compilar la aplicación en Unity y, a continuación, compile e implemente desde Visual Studio para ejecutarlo en el HoloLens.
2. Mire los astronautas, dos flechas deben aparecer en cualquier lado del cursor. Este nuevo objeto visual indica que se pueden girar los astronautas.
3. Coloque la mano en la posición lista (dedo de índice apuntado hacia el cielo) por lo que el HoloLens iniciará el seguimiento de su mano.
4. Para rotar a los astronautas, reducir el dedo índice a una posición pinch y, a continuación, mueva la mano izquierda o derecha para desencadenar el gesto NavigationX.

## <a name="chapter-3---hand-guidance"></a>Capítulo 3: Guía de mano

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a>Objetivos

* Use **entregar puntuación orientación** para ayudar a predecir cuándo se perderá mano de seguimiento.
* Proporcionar **comentarios en el cursor** para mostrar cuando se acerque a la perimetral de la cámara de vista de la mano del usuario.

### <a name="instructions"></a>Instrucciones

1. En el **jerarquía** panel, seleccione el **CursorWithFeedback** objeto.
2. En el **Inspector** del panel, haga clic en el **Agregar componente** botón.
3. En el menú, escriba en el cuadro de búsqueda **mano orientación**. Seleccione el resultado de búsqueda.
4. En el **proyecto** panel **hologramas** carpeta, busque la **HandGuidanceFeedback** activo.
5. Arrastre y coloque el **HandGuidanceFeedback** activo en el **mano orientación indicador** propiedad en el **Inspector** panel.

### <a name="build-and-deploy"></a>Compilación e implementación

* Vuelva a compilar la aplicación en Unity y, a continuación, compile e implemente desde Visual Studio para probar la aplicación en HoloLens.
* Trae la mano a la vista y generar el dedo índice que se realiza el seguimiento.
* Iniciar la rotación de los astronautas con los gestos de navegación (acercar el dedo índice y thumb juntos).
* Mover la mano izquierda, derecha, arriba y abajo.
* Como la mano acerque el borde del marco de movimiento, aparecerá una flecha junto al cursor para avisarle de esa mano de seguimiento se perderá. La flecha indica la dirección para mover la mano con el fin de evitar que el seguimiento que se pierdan.

## <a name="chapter-4---manipulation"></a>Capítulo 4: manipulación

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a>Objetivos

* Usar eventos de manipulación para mover a los astronautas con las manos.
* Proporcionar comentarios sobre el cursor para informar al usuario cuando se puede usar la manipulación.

### <a name="instructions"></a>Instrucciones

GestureManager.cs y AstronautManager.cs nos permitirá hacer lo siguiente:

1. Use la palabra clave de voz "**mover astronautas**" para habilitar **manipulación** gestos y "**girar astronautas**" para deshabilitarlos.
2. Se va a responder a la **reconocedor de gestos de manipulación**.

Empecemos.

1. En el **jerarquía** panel, cree un nuevo GameObject vacío. Asígnele el nombre "**AstronautManager**".
2. En el **Inspector** del panel, haga clic en el **Agregar componente** botón.
3. En el menú, escriba en el cuadro de búsqueda **astronautas Manager**. Seleccione el resultado de búsqueda.
4. En el **Inspector** del panel, haga clic en el **Agregar componente** botón.
5. En el menú, escriba en el cuadro de búsqueda **origen de entrada de voz**. Seleccione el resultado de búsqueda.

Ahora vamos a agregar los comandos de voz para controlar el estado de interacción de los astronautas.

1. Expanda el **palabras clave** sección la **Inspector**.
2. Haga clic en el **+** en el lado derecho para agregar una nueva palabra clave.
3. Escriba la palabra clave como **mover astronautas**. No dude en Agregar un acceso directo de la clave si así lo desea.
4. Haga clic en el **+** en el lado derecho para agregar una nueva palabra clave.
5. Escriba la palabra clave como **girar astronautas**. No dude en Agregar un acceso directo de la clave si así lo desea.
6. El código del controlador correspondiente puede encontrarse en **GestureAction.cs**, en el **ISpeechHandler.OnSpeechKeywordRecognized** controlador.

![Cómo configurar el origen de entrada de voz de capítulo 4](images/holograms211-speech.png)

A continuación, configuramos los comentarios de la manipulación en el cursor.

1. En el **proyecto** panel **hologramas** carpeta, busque la **PathingFeedback** activo.
2. Arrastre y coloque el **PathingFeedback** prefabricado hasta el **CursorWithFeedback** objeto en el **jerarquía**.
3. En el **jerarquía** del panel, haga clic en **CursorWithFeedback**.
4. Arrastre y coloque el **PathingFeedback** objeto desde el **jerarquía** en el **objeto de juego detectado rutas** propiedad en el **comentarios del Cursor**componente en el **Inspector**.

Ahora tenemos que agregar código a **GestureAction.cs** para habilitar lo siguiente:

1. Agregue código a la **IManipulationHandler.OnManipulationUpdated** función, lo que se moverá los astronautas cuando un **manipulación** se detecta el gesto.
2. Calcular la **vector de movimiento** determinar dónde se deben mover los astronautas a mano posición basada.
3. **Mover** los astronautas a la nueva posición.

Codificación completa ejercicio 4.a en **GestureAction.cs**, o usar nuestra solución completa a continuación:

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

* Volver a generar en Unity y, a continuación, compile e implemente desde Visual Studio para ejecutar la aplicación en HoloLens.
* Mover la mano delante el HoloLens y generar el dedo índice para que puede realizar un seguimiento.
* Centrar el cursor a través de los astronautas.
* Supongamos que mover astronautas para mover a los astronautas con un gesto de manipulación.
* Deberían aparecer la cuatro flechas alrededor del cursor para indicar que el programa ahora responderán a eventos de manipulación.
* Disminuya el dedo índice hasta el pulgar y mantenerlos pellizcados juntos.
* Al mover la mano alrededor, los astronautas moverá demasiado (es decir, manipulación).
* Elevar el dedo índice para dejar de manipular a los astronautas.
* Nota: Si no dice a 'Mover astronautas' antes de mover la mano, los gestos de navegación se usará en su lugar.
* Supongamos que girar astronautas para volver al estado giratorias.

## <a name="chapter-5---model-expansion"></a>Capítulo 5: expansión de modelo

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a>Objetivos

* Expanda el modelo astronautas en varios, fragmentos más pequeños que el usuario puede interactuar con.
* Mover cada pieza individualmente con gestos de navegación y manipulación.

### <a name="instructions"></a>Instrucciones

En esta sección, se llevará a cabo las siguientes tareas:

1. Agregar una nueva palabra clave "**expanda modelo**" para expandir el modelo astronautas.
2. Agregar una nueva palabra clave "**restablecer modelo**" para devolver el modelo a su forma original.

Haremos esto mediante la adición de dos más palabras clave para el origen de entrada de voz en el capítulo anterior. También le mostraré otra manera de controlar los eventos de reconocimiento.

1. Haga clic en nuevo en **AstronautManager** en el **Inspector** y expanda el **palabras clave** sección la **Inspector**.
2. Haga clic en el **+** en el lado derecho para agregar una nueva palabra clave.
3. Escriba la palabra clave como **expandir modelo**. No dude en Agregar un acceso directo de la clave si así lo desea.
4. Haga clic en el **+** en el lado derecho para agregar una nueva palabra clave.
5. Escriba la palabra clave como **restablecer modelo**. No dude en Agregar un acceso directo de la clave si así lo desea.
6. En el **Inspector** del panel, haga clic en el **Agregar componente** botón.
7. En el menú, escriba en el cuadro de búsqueda **controlador de entrada de voz**. Seleccione el resultado de búsqueda.
8. Comprobar **es Global escucha**, puesto que deseamos que estos comandos para trabajar sin tener en cuenta el GameObject nos centraremos.
9. Haga clic en el **+** y seleccione **expanda modelo** en la lista desplegable de la palabra clave.
10. Haga clic en el **+** en respuesta y arrastre el **AstronautManager** desde el **jerarquía** en el **None (objeto)** campo.
11. Ahora, haga clic en el **sin función** lista desplegable, seleccione **AstronautManager**, a continuación, **ExpandModelCommand**.
12. Haga clic en el controlador de entrada de voz **+** y seleccione **restablecer modelo** en la lista desplegable de la palabra clave.
13. Haga clic en el **+** en respuesta y arrastre el **AstronautManager** desde el **jerarquía** en el **None (objeto)** campo.
14. Ahora, haga clic en el **sin función** lista desplegable, seleccione **AstronautManager**, a continuación, **ResetModelCommand**.

![Cómo configurar el origen de entrada de voz y el controlador de capítulo 5](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a>Compilación e implementación

* Pruébalo. Compilar e implementar la aplicación en el HoloLens.
* Por ejemplo **expanda modelo** para ver el modelo astronautas expandida.
* Use **navegación** para girar las partes individuales del palo astronautas.
* Por ejemplo **mover astronautas** y, a continuación, usar **manipulación** para mover partes individuales del palo astronautas.
* Por ejemplo **girar astronautas** para girar las piezas de nuevo.
* Por ejemplo **restablecer modelo** para devolver los astronautas a su forma original.

## <a name="the-end"></a>Fin

¡Enhorabuena! Ahora ha completado **MR 211 de entrada: Gesto**.

* Sepa cómo detectar y responder a mano los eventos de seguimiento, la navegación y manipulación.
* Comprender la diferencia entre los gestos de navegación y manipulación.
* Saber cómo cambiar el cursor para proporcionar comentarios visuales cuando se detecta una mano, cuando se perderá una mano y cuando un objeto es compatible con diferentes interacciones (manipulación de vs de navegación).
