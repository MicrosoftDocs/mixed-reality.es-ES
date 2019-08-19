---
title: Sr Basics 101-proyecto completo con dispositivo
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para aprender los aspectos básicos de Windows Mixed Reality.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: realidad mixta, Windows Mixed Reality, HoloLens, holograma, Academy, tutorial
ms.openlocfilehash: 043ffac8f30a4e29586478b5dca6ecccc2b5afd3
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63524029"
---
>[!NOTE]
>Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.  Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se publicarán en el futuro que mostrarán cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se publiquen.

<br>

# <a name="mr-basics-101-complete-project-with-device"></a>Principios básicos 101: Completar proyecto con dispositivo

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

Este tutorial le guiará a través de un proyecto completo, integrado en Unity, que muestra características básicas de Windows Mixed Reality en HoloLens, como [miradas](gaze.md), [gestos](gestures.md), [entrada de voz](voice-input.md), [sonido espacial](spatial-sound.md) y [asignación espacial](spatial-mapping.md).

El tutorial tardará aproximadamente 1 hora en completarse.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td>Principios básicos 101: Completar proyecto con dispositivo</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de comenzar

### <a name="prerequisites"></a>Requisitos previos

* Un equipo con Windows 10 configurado con las [herramientas](install-the-tools.md)correctas instaladas.
* Un dispositivo HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Archivos de proyecto

* Descargue los [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) requeridos por el proyecto. Requiere Unity 2017,2 o posterior.
  * Si sigue necesitando compatibilidad con Unity 5,6, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).
  * Si sigue necesitando compatibilidad con Unity 5,5, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).
  * Si sigue necesitando compatibilidad con Unity 5,4, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).
* Elimine el archivo de los archivos en el escritorio o en otra ubicación de fácil acceso. Mantenga el nombre de la carpeta como **origami**.

>[!NOTE]
>Si desea examinar el código fuente antes de la descarga, está [disponible en github](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).

## <a name="chapter-1---holo-world"></a>Capítulo 1: mundo "Hololens"

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

En este capítulo, se configurará el primer proyecto de Unity y se recorrerá el proceso de compilación e implementación.

### <a name="objectives"></a>Objetivos

* Configure Unity para el desarrollo holográfica.
* Cree un holograma.
* Vea un holograma que haya realizado.

### <a name="instructions"></a>Instrucciones

* Inicia Unity.
* Seleccione **abrir**.
* Escriba ubicación como la carpeta **origami** que ha eliminado previamente.
* Seleccione **origami** y haga clic en **Seleccionar carpeta**.
* Dado que el proyecto **origami** no contiene una escena, guarde la escena predeterminada vacía en un archivo nuevo mediante:Archivo / :**Guardar escena como**.
* Asigne a la nueva escena el nombre **origami** y haga clic en el botón **Guardar** .

#### <a name="setup-the-main-virtual-camera"></a>Configuración de la cámara virtual principal

* En el **Panel jerarquía**, seleccione **cámara principal**.
* En el **Inspector** , establezca su posición de transformación en **0, 0,0**.
* Busque la propiedad **Borrar marcas** y cambie la lista desplegable de **SKYBOX** a **color sólido**.
* Haga clic en el campo **fondo** para abrir un selector de colores.
* Establezca **R, G, B y** a en **0**.

#### <a name="setup-the-scene"></a>Configuración de la escena

* En el **Panel jerarquía**, haga clic en **crear** y **crear vacío**.
* Haga clic con el botón derecho en el nuevo **GameObject** y seleccione Cambiar nombre. Cambie el nombre de GameObject a **OrigamiCollection**.
* En la carpeta hologramas del panel Proyecto (expanda activos y seleccione hologramas o haga doble clic en la carpeta hologramas en el panel Proyecto):
  * Arrastre **Stage** hasta la jerarquía para que sea un elemento secundario de **OrigamiCollection**.
  * Arrastre **Sphere1** a la jerarquía de para que sea un elemento secundario de **OrigamiCollection**.
  * Arrastre **Sphere2** a la jerarquía de para que sea un elemento secundario de **OrigamiCollection**.
* Haga clic con el botón secundario en el objeto de **luz direccional** en el **Panel jerarquía** y seleccione **eliminar**.
* En la carpeta hologramas, arrastre **Lights** hasta la raíz del **Panel de jerarquía**.
* En la **jerarquía**, seleccione el **OrigamiCollection**.
* En el **Inspector**, establezca la posición de la transformación en **0,-0,5, 2,0**.
* Presione el botón **reproducir** en Unity para obtener una vista previa de los hologramas.
* Debería ver los objetos origami en la ventana de vista previa.
* Presione **reproducir** una segunda vez para detener el modo de vista previa.

#### <a name="export-the-project-from-unity-to-visual-studio"></a>Exportar el proyecto de Unity a Visual Studio

* En Unity, seleccione **archivo > configuración de compilación**.
* Seleccione **plataforma universal de Windows** en la lista **plataforma** y haga clic en **cambiar plataforma**.
* Establezca **SDK** en **universal 10** y **tipo de compilación** en **D3D**.
* Compruebe **los C# proyectos de Unity**.
* Haga clic en **Agregar escenas abiertas** para agregar la escena.
* Haz clic en **Compilación**.
* En la ventana del explorador de archivos que aparece, cree una **nueva carpeta** denominada "app".
* Haga clic en la carpeta de la **aplicación**.
* Presione **Seleccionar carpeta**.
* Cuando se haya realizado Unity, aparecerá una ventana del explorador de archivos.
* Abra la carpeta de la **aplicación** .
* Abra (doble clic) **origami. sln**.
* Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x86**.
* Haga clic en la flecha situada junto al botón dispositivo y seleccione **equipo remoto** para implementar a través de Wi-Fi.
  * Establezca la **Dirección** en el nombre o la dirección IP de HoloLens. Si no conoce la dirección IP del dispositivo, consulte **configuración > redes & Internet > opciones avanzadas** o pregunte a Cortana **, ¿cuál es mi dirección IP? "** .
  * Si HoloLens está conectado a través de USB, puede seleccionar **dispositivo** para implementar a través de USB.
  * Deje el **modo de autenticación** establecido en **universal**.
  * Haga clic en **seleccionar**

* Haga clic en depurar **> iniciar sin** depurar o presione **Ctrl + F5**. Si esta es la primera vez que se implementa en el dispositivo, tendrá que [emparejarla con Visual Studio](using-visual-studio.md#pairing-your-device-hololens-(1st-gen)).

* Ahora se compilará el proyecto origami, se implementará en HoloLens y, a continuación, se ejecutará.
* Pon en tu HoloLens y mira tu vista para ver los nuevos hologramas.

## <a name="chapter-2---gaze"></a>Capítulo 2: mira hacia abajo

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

En este capítulo, vamos a presentar la primera de las tres formas de interactuar con los hologramas: [mirada](gaze.md).

### <a name="objectives"></a>Objetivos

* Visualice la mirada con un cursor de un mundo bloqueado.

### <a name="instructions"></a>Instrucciones

* Vuelva al proyecto de Unity y cierre la ventana de configuración de la compilación si aún está abierta.
* Seleccione la carpeta hologramas en el **panel Proyecto**.
* Arrastre el objeto **cursor** al **Panel jerarquía** en el nivel raíz.
* Haga doble clic en el objeto **cursor** para examinarlo más detenidamente.
* Haga clic con el botón secundario en la carpeta scripts en el panel Proyecto.
* Haga clic en el submenú **crear** .
* Seleccione  **C# script**.
* Asigne al script el nombre **WorldCursor**. Nota: El nombre distingue mayúsculas de minúsculas. No es necesario agregar la extensión. cs.
* Seleccione el objeto **cursor** en el **Panel jerarquía**.
* Arrastre y coloque el script **WorldCursor** en el **panel Inspector**.
* Haga doble clic en el script **WorldCursor** para abrirlo en Visual Studio.
* Copie y pegue este código en **WorldCursor.CS** y **guarde todo**.

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

* Vuelva a compilar la aplicación desde el **archivo > la configuración de compilación**.
* Vuelva a la solución de Visual Studio que se usó anteriormente para implementar en HoloLens.
* Seleccione "recargar todo" cuando se le solicite.
* Haga clic en depurar **-> iniciar sin** depurar o presione **Ctrl + F5**.
* Ahora mire la escena y observe cómo interactúa el cursor con la forma de los objetos.

## <a name="chapter-3---gestures"></a>Capítulo 3: gestos

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

En este capítulo, se agregará compatibilidad con [gestos](gestures.md). Cuando el usuario selecciona una esfera de papel, haremos que la esfera se active al activar la gravedad mediante el motor físico de Unity.

### <a name="objectives"></a>Objetivos

* Controle los hologramas con el gesto de selección.

### <a name="instructions"></a>Instrucciones

Comenzaremos por crear un script y luego puede detectar el gesto de selección.

* En la carpeta scripts, cree un script denominado **GazeGestureManager**.
* Arrastre el script **GazeGestureManager** hasta el objeto **OrigamiCollection** de la jerarquía.
* Abra el script **GazeGestureManager** en Visual Studio y agregue el código siguiente:

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

* Cree otro script en la carpeta scripts, esta vez con el nombre **SphereCommands**.
* Expanda el objeto **OrigamiCollection** en la vista de jerarquía.
* Arrastre el script **SphereCommands** al objeto **Sphere1** en el panel jerarquía.
* Arrastre el script **SphereCommands** al objeto **Sphere2** en el panel jerarquía.
* Abra el script en Visual Studio para editarlo y reemplace el código predeterminado por este:

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

* Exporte, compile e implemente la aplicación en su HoloLens.
* Fíjese en uno de los esferas.
* Realice el gesto seleccionar y observe la esfera que se coloca en la superficie siguiente.

## <a name="chapter-4---voice"></a>Capítulo 4: voz

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

En este capítulo, se agregará compatibilidad con dos [comandos de voz](voice-input.md): "RESET World" para devolver los esferas quitados a su ubicación original y "Drop Sphere" para que la esfera quede.

### <a name="objectives"></a>Objetivos

* Agregue comandos de voz que siempre escuchan en segundo plano.
* Cree un holograma que reaccione a un comando de voz.

### <a name="instructions"></a>Instrucciones

* En la carpeta scripts, cree un script denominado **SpeechManager**.
* Arrastre el script **SpeechManager** hasta el objeto **OrigamiCollection** de la jerarquía.
* Abra el script **SpeechManager** en Visual Studio.
* Copie y pegue este código en **SpeechManager.CS** y **guarde todo**:

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

* Abra el script **SphereCommands** en Visual Studio.
* Actualice el script para que se lea de la siguiente manera:

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

* Exporte, compile e implemente la aplicación en su HoloLens.
* Fíjese en uno de los esferas y en "**colocar esfera**".
* Por ejemplo, "**restablecer mundo**" para volver a colocarlos en sus posiciones iniciales.

## <a name="chapter-5---spatial-sound"></a>Capítulo 5: sonido espacial

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

En este capítulo, agregaremos música a la aplicación y, a continuación, desencadenaremos efectos sonoros en determinadas acciones. Usaremos el [sonido espacial](spatial-sound.md) para proporcionar a los sonidos una ubicación específica en el espacio 3D.

### <a name="objectives"></a>Objetivos

* Escuche los hologramas de su mundo.

### <a name="instructions"></a>Instrucciones

* En Unity, seleccione en el menú superior **editar > configuración del proyecto > audio**
* En el panel Inspector del lado derecho, busque la configuración del **complemento Spatializer** y seleccione **MS HRTF Spatializer**.
* En la carpeta hologramas del panel Proyecto, arrastre el objeto **ambiente** hasta el objeto **OrigamiCollection** en el panel jerarquía.
* Seleccione **OrigamiCollection** y busque el componente **origen de audio** en el panel Inspector. Cambie estas propiedades:
  * Compruebe la propiedad **Spatial** .
  * Active la casilla **reproducir en activo**.
  * Cambie la **mezcla espacial** a **3D** arrastrando el control deslizante hasta la derecha. El valor debe cambiar de 0 a 1 cuando se mueve el control deslizante.
  * Compruebe la propiedad **Loop** .
  * Expanda **configuración de sonido 3D**y escriba **0,1** para el **nivel de Doppler**.
  * Establezca **rolloff de volumen** en **rolloff logarítmica**.
  * Establezca la **distancia máxima** en **20**.
* En la carpeta scripts, cree un script denominado **SphereSounds**.
* Arrastre y coloque **SphereSounds** en los objetos **Sphere1** y **Sphere2** de la jerarquía.
* Abra **SphereSounds** en Visual Studio, actualice el código siguiente y **guarde todo**.

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

* Guarde el script y vuelva a Unity.
* Exporte, compile e implemente la aplicación en su HoloLens.
* Desplácese más cerca y más lejos de la fase y vuelva al lado para oír el cambio de los sonidos.

## <a name="chapter-6---spatial-mapping"></a>Capítulo 6: asignación espacial

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

Ahora vamos a usar la [asignación espacial](spatial-mapping.md) para colocar el tablero de juego en un objeto real del mundo real.

### <a name="objectives"></a>Objetivos

* Traiga su mundo real al mundo virtual.
* Coloque los hologramas donde más le importan.

### <a name="instructions"></a>Instrucciones

* En Unity, haga clic en la carpeta hologramas en el panel Proyecto.
* Arrastre el recurso de **asignación espacial** a la raíz de la **jerarquía**.
* Haga clic en el objeto de **asignación espacial** en la jerarquía.
* En el **panel Inspector**, cambie las siguientes propiedades:
  * Active la casilla **dibujar mallas visuales** .
  * Busque **material de dibujo** y haga clic en el círculo de la derecha. Escriba "**Wireframe**" en el campo de búsqueda de la parte superior. Haga clic en el resultado y, a continuación, cierre la ventana. Al hacerlo, el valor de Draw material debe establecerse en Wireframe.
* Exporte, compile e implemente la aplicación en su HoloLens.
* Cuando se ejecuta la aplicación, una malla de alambres se superpone a su mundo real.
* Vea cómo una esfera gradual se quedará fuera de la fase y en el suelo.

Ahora le mostraremos cómo trasladar el OrigamiCollection a una nueva ubicación:

* En la carpeta scripts, cree un script denominado **TapToPlaceParent**.
* En la **jerarquía**, expanda **OrigamiCollection** y seleccione el objeto **Stage** .
* Arrastre el script **TapToPlaceParent** hasta el objeto Stage.
* Abra el script **TapToPlaceParent** en Visual Studio y actualícelo para que sea el siguiente:

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

* Exportar, compilar e implementar la aplicación.
* Ahora debería poder colocar el juego en una ubicación específica Gazing en él, con el gesto seleccionar y, a continuación, pasar a una nueva ubicación y volver a usar el gesto seleccionar.

## <a name="chapter-7---holographic-fun"></a>Capítulo 7: diversión de holográfica

### <a name="objectives"></a>Objetivos

* Revela la entrada a un mundo holográfica.

### <a name="instructions"></a>Instrucciones

Ahora le mostraremos cómo descubrir el mundo holográfica:

* En la carpeta hologramas del panel Proyecto:
  * Arrastre el submundo a la jerarquía para que sea un elemento secundario de **OrigamiCollection**.
* En la carpeta scripts, cree un script denominado **HitTarget**.
* En la **jerarquía**, expanda **OrigamiCollection**.
* Expanda el objeto **fase** y seleccione el objeto de **destino** (ventilador azul).
* Arrastre el script **HitTarget** al objeto de **destino** .
* Abra el script **HitTarget** en Visual Studio y actualícelo para que sea el siguiente:

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

* En Unity, seleccione el objeto de **destino** .
* Ahora hay dos propiedades públicas visibles en el componente de **destino** de aciertos y necesitan hacer referencia a los objetos de nuestra escena:
  * Arrastre el subámbito del panel **jerarquía** a la propiedad subworld del componente **destino** de la visita.
  * Arrastre **fase** desde el panel **jerarquía** hasta el **objeto para ocultar** la propiedad en el componente de destino de la **visita** .
* Exportar, compilar e implementar la aplicación.
* Coloque la colección origami en el plano inferior y, a continuación, use el gesto seleccionar para hacer una colocación de esfera.
* Cuando la esfera alcanza el destino (ventilador azul), se producirá una explosión. La colección se ocultará y aparecerá un hueco para el mundo.

## <a name="the-end"></a>Fin

Y este es el final de este tutorial.

Aprendió:

* Cómo crear una aplicación holográfica en Unity.
* Cómo hacer uso de fijamente, gestos, voz, sonido y asignación espacial.
* Cómo compilar e implementar una aplicación con Visual Studio.

Ya está listo para empezar a crear su propia experiencia holográfica.

## <a name="see-also"></a>Vea también

* [MR Basics 101E: proyecto completo con emulador](holograms-101e.md)
* [Gaze](gaze.md)
* [Gestos](gestures.md)
* [Entrada de voz](voice-input.md)
* [Sonido espacial](spatial-sound.md)
* [Asignación espacial](spatial-mapping.md)
