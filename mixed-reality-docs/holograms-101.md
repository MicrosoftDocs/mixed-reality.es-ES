---
title: Conceptos básicos de MR 101 - proyecto completo con el dispositivo
description: Siga este tutorial de programación con Unity, Visual Studio y HoloLens para obtener información sobre los conceptos básicos de Windows Mixed Reality.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: la realidad, Windows Mixed Reality, HoloLens, mixta holograma, academy, tutorial
ms.openlocfilehash: 043ffac8f30a4e29586478b5dca6ecccc2b5afd3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599358"
---
>[!NOTE]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.  Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.  Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.

<br>

# <a name="mr-basics-101-complete-project-with-device"></a>Conceptos básicos de MR 101: Proyecto completo con el dispositivo

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

Este tutorial le guiará a través de un proyecto completo, compilado en Unity, que muestra las características de Windows Mixed Reality principales en incluidos HoloLens [que mirar](gaze.md), [gestos](gestures.md), [deentradadevoz](voice-input.md), [sonido espacial](spatial-sound.md) y [asignación espacial](spatial-mapping.md).

El tutorial tardará aproximadamente una hora en completarse.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td>Conceptos básicos de MR 101: Proyecto completo con el dispositivo</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de empezar

### <a name="prerequisites"></a>Requisitos previos

* Un equipo con Windows 10 configurado con el valor correcto [herramientas instaladas](install-the-tools.md).
* Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Archivos de proyecto

* Descargue el [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) requerida por el proyecto. Requiere Unity 2017.2 o posterior.
  * Si necesita compatibilidad con Unity 5.6, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).
  * Si necesita compatibilidad con Unity 5.5, utilice [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).
  * Si necesita compatibilidad con Unity 5.4, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).
* Extraer del archivo los archivos en el escritorio o en otros más fáciles de alcanzar la ubicación. Mantenga el nombre de carpeta **Origami**.

>[!NOTE]
>Si desea buscar en el código de origen antes de descargar, tiene [disponible en GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).

## <a name="chapter-1---holo-world"></a>Capítulo 1: "Holo" world

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

En este capítulo, crearemos nuestro primer proyecto de Unity y paso a través de la compilación de la instalación y proceso de implementación.

### <a name="objectives"></a>Objetivos

* Configuración de Unity para desarrollo holográfica.
* Realice un holograma.
* Vea un holograma que haya realizado.

### <a name="instructions"></a>Instrucciones

* Inicie Unity.
* Seleccione **abierto**.
* Escriba la ubicación que el **Origami** carpeta que anteriormente no archivados.
* Seleccione **Origami** y haga clic en **seleccionar la carpeta**.
* Puesto que la **Origami** proyecto no contiene una escena, guarde la escena vacía de forma predeterminada un nuevo archivo con: **Archivo** / **Guardar escena como**.
* Nombre de la nueva escena **Origami** y presione la **guardar** botón.

#### <a name="setup-the-main-virtual-camera"></a>Programa de instalación de la cámara virtual principal

* En el **jerarquía Panel**, seleccione **cámara principal**.
* En el **Inspector** establecer su posición de la transformación a **0,0,0**.
* Buscar el **borrar las marcas** propiedad y cambie la lista desplegable de **Skybox** a **color sólido**.
* Haga clic en el **en segundo plano** campo para abrir un selector de colores.
* Establecer **R, G, B y A** a **0**.

#### <a name="setup-the-scene"></a>Programa de instalación de la escena

* En el **jerarquía Panel**, haga clic en **crear** y **crear vacío**.
* Haga clic en el nuevo **GameObject** y seleccione Cambiar nombre. Cambiar el nombre de la GameObject a **OrigamiCollection**.
* Desde el **hologramas** carpeta en el Panel de proyecto (expanda activos y seleccione hologramas o haga doble clic en la carpeta hologramas en el Panel de proyecto):
  * Arrastre **fase** en la jerarquía sea un elemento secundario de **OrigamiCollection**.
  * Arrastre **Sphere1** en la jerarquía sea un elemento secundario de **OrigamiCollection**.
  * Arrastre **Sphere2** en la jerarquía sea un elemento secundario de **OrigamiCollection**.
* Haga clic en el **luz direccional** objeto en el **jerarquía Panel** y seleccione **eliminar**.
* Desde el **hologramas** carpeta, arrastre **luces** en la raíz de la **jerarquía Panel**.
* En el **jerarquía**, seleccione el **OrigamiCollection**.
* En el **Inspector**, establezca la posición de la transformación en **0, -0,5, 2.0**.
* Presione el **reproducir** en Unity para obtener una vista previa de sus hologramas botón.
* Debería ver los objetos de Origami en la ventana Vista previa.
* Presione **reproducir** una segunda vez para detener el modo de vista previa.

#### <a name="export-the-project-from-unity-to-visual-studio"></a>Exporta el proyecto de Unity a Visual Studio

* En Seleccione Unity **archivo > configuración de compilación**.
* Seleccione **Universal Windows Platform** en el **plataforma** lista y haga clic en **Cambiar plataforma**.
* Establecer **SDK** a **10 Universal** y **tipo de compilación** a **D3D**.
* Comprobar **Unity C# proyectos**.
* Haga clic en **agregar escenas abierto** para agregar la escena.
* Haz clic en **Compilación**.
* En la ventana del explorador de archivos que aparece, cree un **nueva carpeta** denominada "Aplicación".
* Solo haga clic en el **carpeta aplicación**.
* Presione **Seleccionar carpeta**.
* Cuando se realiza a Unity, aparecerá una ventana del explorador de archivos.
* Abra el **aplicación** carpeta.
* Abrir (hacer doble clic) **Origami.sln**.
* Uso de la barra de herramientas superior en Visual Studio, cambiar el destino de depuración a **versión** y de ARM para **X86**.
* Haga clic en la flecha situada junto al botón del dispositivo y seleccione **máquina remota** para implementar a través de Wi-Fi.
  * Establecer el **dirección** en el nombre o dirección IP de su HoloLens. Si no conoce la dirección IP del dispositivo, busque en **configuración > red e Internet > Opciones avanzadas** o solicitar a Cortana **"Hola Cortana, ¿cuál es mi dirección IP?"**
  * Si el HoloLens está conectado a través de USB, puede seleccionar en su lugar **dispositivo** para implementar a través de USB.
  * Deje el **modo de autenticación** establecido en **Universal**.
  * Haga clic en **seleccionar**

* Haga clic en **Depurar > Iniciar sin depurar** o presione **Ctrl + F5**. Si se trata de la primera vez que la implementación en el dispositivo, deberá [emparejarlo con Visual Studio](using-visual-studio.md#pairing-your-device-hololens-(1st-gen)).

* El proyecto Origami ahora crear, implementar en su HoloLens y, a continuación, ejecute.
* Colocar en su HoloLens y mire para ver sus nueva hologramas.

## <a name="chapter-2---gaze"></a>Capítulo 2: mirada

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

En este capítulo, vamos a introducir la primera de estas tres maneras de interactuar con sus hologramas-- [que mirar](gaze.md).

### <a name="objectives"></a>Objetivos

* Visualice a su mirada mediante un cursor bloqueado por el mundo.

### <a name="instructions"></a>Instrucciones

* Vuelva a su proyecto de Unity y cerrar la ventana de configuración de compilación si aún está abierta.
* Seleccione el **hologramas** carpeta en el **panel proyecto**.
* Arrastre el **Cursor** objeto en el **panel jerarquía** en el nivel raíz.
* Haga doble clic en el **Cursor** objeto vistazo más de cerca.
* Haga doble clic en el **Scripts** carpeta en el panel de proyecto.
* Haga clic en el **crear** submenú.
* Seleccione  **C# Script**.
* Nombre de la secuencia de comandos **WorldCursor**. Nota: El nombre distingue mayúsculas de minúsculas. No es necesario agregar la extensión. cs.
* Seleccione el **Cursor** objeto en el **panel jerarquía**.
* Arrastre y coloque el **WorldCursor** de script en el **panel Inspector**.
* Haga doble clic en el **WorldCursor** script para abrirlo en Visual Studio.
* Copie y pegue este código en **WorldCursor.cs** y **guardar todo**.

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move the cursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* Vuelva a compilar la aplicación de **archivo > configuración de compilación**.
* Vuelva a la solución de Visual Studio que anteriormente se usa para implementar en su HoloLens.
* Seleccione "Volver a cargar todo" cuando se le solicite.
* Haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**.
* Ahora mire la escena y observe cómo interactúa el cursor con la forma de objetos.

## <a name="chapter-3---gestures"></a>Capítulo 3: gestos

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

En este capítulo, se agregará compatibilidad para [gestos](gestures.md). Cuando el usuario selecciona una esfera de papel, nos aseguraremos de hacer la esfera se dividen activando gravedad mediante el motor de leyes físicas de Unity.

### <a name="objectives"></a>Objetivos

* Controlar las hologramas con el gesto de Select.

### <a name="instructions"></a>Instrucciones

Se comenzará creando una secuencia de comandos, a continuación, puede detectar el gesto de Select.

* En el **Scripts** carpeta, cree un script denominado **GazeGestureManager**.
* Arrastre el **GazeGestureManager** de script en el **OrigamiCollection** objeto en la jerarquía.
* Abra el **GazeGestureManager** de script en Visual Studio y agregue el código siguiente:

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Awake()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* Cree otra secuencia de comandos en la carpeta de Scripts, esta vez denominada **SphereCommands**.
* Expanda el **OrigamiCollection** objeto en la vista de jerarquía.
* Arrastre el **SphereCommands** de script en el **Sphere1** objeto en el panel de la jerarquía.
* Arrastre el **SphereCommands** de script en el **Sphere2** objeto en el panel de la jerarquía.
* Abra el script en Visual Studio para editar y reemplace el código predeterminado con esto:

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* Exportar, compilar e implementar la aplicación en su HoloLens.
* Examine una de las esferas.
* Realice el gesto de select y observe cómo la esfera de colocar en la superficie de debajo.

## <a name="chapter-4---voice"></a>Capítulo 4 - voz

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

En este capítulo, se agregará compatibilidad para dos [comandos de voz](voice-input.md): "Restablecer world" para devolver las esferas colocarlo en su ubicación original y "Quitar esfera" para realizar la esfera se encuentran.

### <a name="objectives"></a>Objetivos

* Agregar comandos de voz que siempre escuchan en segundo plano.
* Cree un holograma que reacciona a un comando de voz.

### <a name="instructions"></a>Instrucciones

* En el **Scripts** carpeta, cree un script denominado **SpeechManager**.
* Arrastre el **SpeechManager** de script en el **OrigamiCollection** objeto en la jerarquía
* Abra el **SpeechManager** script en Visual Studio.
* Copie y pegue este código en **SpeechManager.cs** y **guardar todo**:

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* Abra el **SphereCommands** script en Visual Studio.
* Actualice el script para que quede como sigue:

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* Exportar, compilar e implementar la aplicación en su HoloLens.
* Examine una de las esferas y diga "**Drop esfera**".
* Por ejemplo "**restablecer World**" para llevarlas nuevamente a sus posiciones iniciales.

## <a name="chapter-5---spatial-sound"></a>Capítulo 5: sonido espacial

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

En este capítulo, se deberá agregar música a la aplicación y, a continuación, desencadenar efectos de sonido en determinadas acciones. Vamos a usar [sonido espacial](spatial-sound.md) para proporcionar a los sonidos de una ubicación específica en un espacio 3D.

### <a name="objectives"></a>Objetivos

* Escuche hologramas en el mundo.

### <a name="instructions"></a>Instrucciones

* En el menú superior, seleccione Unity **Editar > configuración del proyecto > Audio**
* En el Panel de Inspector en el lado derecho, busque el **espacial complemento** configuración y seleccione **MS HRTF Spatializer**.
* Desde el **hologramas** carpeta en el panel proyecto, arrastre el **ambiente** objeto en el **OrigamiCollection** objeto en el Panel de la jerarquía.
* Seleccione **OrigamiCollection** y busque el **origen Audio** componente en el panel del Inspector. Cambiar estas propiedades:
  * Compruebe el **Spatialize** propiedad.
  * Compruebe el **reproducir en activo**.
  * Cambio **Blend espacial** a **3D** arrastrando el control deslizante totalmente hacia la derecha. El valor debe cambiar de 0 a 1 cuando se mueve el control deslizante.
  * Compruebe el **bucle** propiedad.
  * Expanda **configuración sonido 3D**y escriba **0,1** para **nivel Doppler**.
  * Establecer **volumen atenuación** a **atenuación logarítmica**.
  * Establecer **distancia máxima** a **20**.
* En el **Scripts** carpeta, cree un script denominado **SphereSounds**.
* Arrastre y coloque **SphereSounds** a la **Sphere1** y **Sphere2** objetos de la jerarquía.
* Abra **SphereSounds** en Visual Studio, actualice el código siguiente y **guardar todo**.

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* Guarde el script y volver a Unity.
* Exportar, compilar e implementar la aplicación en su HoloLens.
* Mover más cercano y más lejos de la fase y activar lado a lado para que escuche los sonidos cambiar.

## <a name="chapter-6---spatial-mapping"></a>Asignación de capítulo 6: espacial

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

Ahora vamos a usar [asignación espacial](spatial-mapping.md) para colocar el tablero de juego en un objeto real en el mundo real.

### <a name="objectives"></a>Objetivos

* Ponga el mundo real en el mundo virtual.
* Coloque sus hologramas donde más le interesen.

### <a name="instructions"></a>Instrucciones

* En Unity, haga clic en el **hologramas** carpeta en el panel de proyecto.
* Arrastre el **asignación espacial** activo en la raíz de la **jerarquía**.
* Haga clic en el **asignación espacial** objeto en la jerarquía.
* En el **panel Inspector**, cambie las siguientes propiedades:
  * Compruebe el **dibujar mallas Visual** cuadro.
  * Busque **dibujar Material** y haga clic en el círculo de la derecha. Tipo de "**tramas de alambres**" en el campo de búsqueda en la parte superior. Haga clic en el resultado y, a continuación, cierre la ventana. Al hacerlo, debe obtener o establecer el valor de dibujar Material en tramas de alambres.
* Exportar, compilar e implementar la aplicación en su HoloLens.
* Cuando se ejecuta la aplicación, una malla de tramas de alambres superpondrán el mundo real.
* Vea cómo una esfera gradual estarán fuera del escenario y en el suelo.

Ahora vamos a mostrarle cómo mover la OrigamiCollection a una nueva ubicación:

* En el **Scripts** carpeta, cree un script denominado **TapToPlaceParent**.
* En el **jerarquía**, expanda el **OrigamiCollection** y seleccione el **fase** objeto.
* Arrastre el **TapToPlaceParent** script en el objeto de fase.
* Abra el **TapToPlaceParent** de script en Visual Studio y actualizarlo para que sea lo siguiente:

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* Exportar, compile e implemente la aplicación.
* Ahora ya podrá colocar el juego en una ubicación específica mediante gazing en él, con el gesto de Select y, a continuación, mover a una nueva ubicación y volver a usar el gesto de Select.

## <a name="chapter-7---holographic-fun"></a>Capítulo 7 - divertido holográfica

### <a name="objectives"></a>Objetivos

* Mostrar la entrada a un Underword holográfica.

### <a name="instructions"></a>Instrucciones

Ahora vamos a mostrarle cómo descubrir el Underword holográfica:

* Desde el **hologramas** carpeta en el Panel de proyecto:
  * Arrastre **Underword** en la jerarquía sea un elemento secundario de **OrigamiCollection**.
* En el **Scripts** carpeta, cree un script denominado **HitTarget**.
* En el **jerarquía**, expanda el **OrigamiCollection**.
* Expanda el **fase** de objetos y seleccione el **destino** (ventilador azul) del objeto.
* Arrastre el **HitTarget** de script en el **destino** objeto.
* Abra el **HitTarget** de script en Visual Studio y actualizarlo para que sea lo siguiente:

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* En Unity, seleccione el **destino** objeto.
* Dos propiedades públicas son ahora visibles en el **aciertos destino** componente y la necesidad de los objetos de referencia de nuestra escena:
  * Arrastre **Underword** desde el **jerarquía** panel a la **Underword** propiedad en el **aciertos destino** componente.
  * Arrastre **fase** desde el **jerarquía** panel a la **objeto se va a ocultar** propiedad en el **aciertos destino** componente.
* Exportar, compile e implemente la aplicación.
* Coloque la colección de Origami en el suelo y, a continuación, usar el gesto de Select para realizar una esfera drop.
* Cuando la esfera alcanza el destino (ventilador azul), se producirá una explosión. La colección se ocultarán y aparecerá un "agujero" para el Underword.

## <a name="the-end"></a>Fin

Y es el final de este tutorial.

Ha aprendido conceptos:

* Cómo crear una aplicación holográfica en Unity.
* Cómo hacer uso de mirada, gestos, voz, sonido y asignación espacial.
* Cómo compilar e implementar una aplicación mediante Visual Studio.

Ahora está listo para comenzar a crear su propia experiencia holográfica.

## <a name="see-also"></a>Vea también

* [Conceptos básicos de MR 101E: Proyecto completo con el emulador](holograms-101e.md)
* [Gaze](gaze.md)
* [Gestos](gestures.md)
* [Entrada de voz](voice-input.md)
* [Sonido espacial](spatial-sound.md)
* [Asignación espacial](spatial-mapping.md)
