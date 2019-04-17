---
title: Conceptos básicos de MR 101E - proyecto completo con el emulador
description: Siga este tutorial con Unity, Visual Studio y el emulador de HoloLens para obtener información sobre los conceptos básicos de una aplicación holográfica de codificación.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: realidad mixta, Windows Mixed Reality, HoloLens, holograma, emulador tutorial, academy,
ms.openlocfilehash: 77f7d497396937bf471a69fa514cef84ab0b699d
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59599407"
---
>[!NOTE]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.  Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.  Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.

<br>

# <a name="mr-basics-101e-complete-project-with-emulator"></a>Conceptos básicos de MR 101E: Proyecto completo con el emulador

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

Este tutorial le guiará a través de un proyecto completo, compilado en Unity, que muestra las características de Windows Mixed Reality principales en incluidos HoloLens [que mirar](gaze.md), [gestos](gestures.md), [deentradadevoz](voice-input.md), [sonido espacial](spatial-sound.md) y [asignación espacial](spatial-mapping.md). El tutorial tardará aproximadamente una hora en completarse.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td>Conceptos básicos de MR 101E: Proyecto completo con el emulador</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de empezar

### <a name="prerequisites"></a>Requisitos previos

* Un equipo con Windows 10 configurado con el valor correcto [herramientas instaladas](install-the-tools.md).

### <a name="project-files"></a>Archivos de proyecto

* Descargue el [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) requerida por el proyecto. Requiere Unity 2017.2 o posterior.
  * Si necesita compatibilidad con Unity 5.6, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).
  * Si necesita compatibilidad con Unity 5.5, utilice [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).
  * Si necesita compatibilidad con Unity 5.4, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).
* Extraer del archivo los archivos en el escritorio o en otros más fáciles de alcanzar la ubicación. Mantenga el nombre de carpeta **Origami**.

>[!NOTE]
>Si desea buscar en el código de origen antes de descargar, tiene [disponible en GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).

## <a name="chapter-1---holo-world"></a>Capítulo 1: "Holo" world

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

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
* Guarde la nueva escena: **Archivo** / **Guardar escena como**.
* Nombre de la escena **Origami** y presione la **guardar** botón.

#### <a name="setup-the-main-camera"></a>Programa de instalación de la cámara principal

* En el **jerarquía Panel**, seleccione **cámara principal**.
* En el **Inspector** establecer su posición de la transformación a **0,0,0**.
* Buscar el **borrar las marcas** propiedad y cambie la lista desplegable de **Skybox** a **color sólido**.
* Haga clic en el **en segundo plano** campo para abrir un selector de colores.
* Establecer **R, G, B y A** a **0**.

#### <a name="setup-the-scene"></a>Programa de instalación de la escena

* En el **jerarquía Panel**, haga clic en **crear** y **crear vacío**.
* Haga clic en el nuevo **GameObject** y seleccione Cambiar nombre. Cambiar el nombre de la GameObject a **OrigamiCollection**.
* Desde el **hologramas** carpeta en el **Panel proyecto**:
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
* Seleccione **Windows Store** en el **plataforma** lista y haga clic en **Cambiar plataforma**.
* Establecer **SDK** a **10 Universal** y **tipo de compilación** a **D3D**.
* Comprobar **Unity C# proyectos**.
* Haga clic en **agregar escenas abierto** para agregar la escena.
* Haga clic en **configuración del Reproductor...** .
* En, seleccione el Panel Inspector el **logotipo de Windows Store**. A continuación, seleccione **configuración de publicación**.
* En el **capacidades** sección, seleccione el **micrófono** y **SpatialPerception** capacidades.
* En la ventana de configuración de compilación, haga clic en **compilar**.
* Crear un **nueva carpeta** denominada "Aplicación".
* Solo haga clic en el **carpeta aplicación**.
* Presione **Seleccionar carpeta**.
* Cuando se realiza a Unity, aparecerá una ventana del explorador de archivos.
* Abra el **aplicación** carpeta.
* Abra el **solución de Visual Studio Origami**.
* Uso de la barra de herramientas superior en Visual Studio, cambiar el destino de depuración a **versión** y de ARM para **X86**.
  * Haga clic en la flecha situada junto al botón del dispositivo y seleccione **emulador de HoloLens**.
  * Haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**.
  * Más tarde el emulador se inicia con el proyecto Origami. Cuando se inicia en primer lugar el [emulador](using-the-hololens-emulator.md), puede tardar hasta 15 minutos para iniciar el emulador. Una vez se inicia, no lo cierre.

## <a name="chapter-2---gaze"></a>Capítulo 2: mirada

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

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

            // Move thecursor to the point where the raycast hit.
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
* Vuelva a la solución de Visual Studio que anteriormente se usa para implementar en el emulador.
* Seleccione "Volver a cargar todo" cuando se le solicite.
* Haga clic en **Depurar -> Iniciar sin depurar** o presione **Ctrl + F5**.
* Usar el controlador de Xbox para buscar en torno a la escena. Tenga en cuenta cómo interactúa el cursor con la forma de objetos.

## <a name="chapter-3---gestures"></a>Capítulo 3: gestos

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

En este capítulo, se agregará compatibilidad para [gestos](gestures.md). Cuando el usuario selecciona una esfera de papel, nos aseguraremos de hacer la esfera se dividen activando gravedad mediante el motor de leyes físicas de Unity.

### <a name="objectives"></a>Objetivos

* Controlar las hologramas con el gesto de Select.

### <a name="instructions"></a>Instrucciones

Comenzaremos por crear una secuencia de comandos que puede detectar el gesto de Select.

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
    void Start()
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

* Exportar, compilar e implementar la aplicación en el emulador de HoloLens.
* Mire en torno a la escena y centrar en uno de los ámbitos.
* Presione el **A** situado en el controlador de Xbox o presione la barra espaciadora para simular el gesto de Select.

## <a name="chapter-4---voice"></a>Capítulo 4 - voz

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

En este capítulo, se agregará compatibilidad para dos [comandos de voz](voice-input.md): "Restablecer world" para devuelve las esferas colocarlo en su ubicación original y "Colocar sphere" para realizar la esfera se encuentran.

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

* Exportar, compilar e implementar la aplicación en el emulador de HoloLens.
* El emulador admitirá micrófono de su PC y responder a su voz: ajustar la vista de modo que el cursor está en uno de los ámbitos y diga "Drop esfera".
* Por ejemplo "**restablecer World**" para llevarlas nuevamente a sus posiciones iniciales.

## <a name="chapter-5---spatial-sound"></a>Capítulo 5: sonido espacial

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

En este capítulo, se deberá agregar música a la aplicación y, a continuación, desencadenar efectos de sonido en determinadas acciones. Vamos a usar [sonido espacial](spatial-sound.md) para proporcionar a los sonidos de una ubicación específica en un espacio 3D.

### <a name="objectives"></a>Objetivos

* Escuche hologramas en el mundo.

### <a name="instructions"></a>Instrucciones

* En el, en el menú superior seleccione Unity **Editar > configuración del proyecto > Audio**
* Buscar el **espacial complemento** configuración y seleccione **MS HRTF Spatializer**.
* Desde el **hologramas** carpeta, arrastre el **ambiente** objeto en el **OrigamiCollection** objeto en el Panel de la jerarquía.
* Seleccione **OrigamiCollection** y busque el **origen Audio** componente. Cambiar estas propiedades:
  * Compruebe el **Spatialize** propiedad.
  * Compruebe el **reproducir en activo**.
  * Cambio **Blend espacial** a **3D** arrastrando el control deslizante totalmente hacia la derecha.
  * Compruebe el **bucle** propiedad.
  * Expanda **configuración sonido 3D**y escriba **0,1** para **nivel Doppler**.
  * Establecer **volumen atenuación** a **atenuación logarítmica**.
  * Establecer **distancia máxima** a **20**.
* En el **Scripts** carpeta, cree un script denominado **SphereSounds**.
* Arrastre **SphereSounds** a la **Sphere1** y **Sphere2** objetos de la jerarquía.
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
* Exportar, compilar e implementar la aplicación en el emulador de HoloLens.
* Utilizar auriculares para obtener el efecto completo y mover más cercana y nada más lejos de la fase oír el sonido a cambiar.

## <a name="chapter-6---spatial-mapping"></a>Asignación de capítulo 6: espacial

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

Ahora vamos a usar [asignación espacial](spatial-mapping.md) para colocar el tablero de juego en un objeto real en el mundo real.

### <a name="objectives"></a>Objetivos

* Ponga el mundo real en el mundo virtual.
* Coloque sus hologramas donde más le interesen.

### <a name="instructions"></a>Instrucciones

* Haga clic en el **hologramas** carpeta en el panel de proyecto.
* Arrastre el **asignación espacial** activo en la raíz de la **jerarquía**.
* Haga clic en el **asignación espacial** objeto en la jerarquía.
* En el **panel Inspector**, cambie las siguientes propiedades:
  * Compruebe el **dibujar mallas Visual** cuadro.
  * Busque **dibujar Material** y haga clic en el círculo de la derecha. Tipo de "**tramas de alambres**" en el campo de búsqueda en la parte superior. Haga clic en el resultado y, a continuación, cierre la ventana.
* Exportar, compilar e implementar la aplicación en el emulador de HoloLens.
* Cuando se ejecuta la aplicación, se representará una malla de una sala de estar previamente digitalizada reales en tramas de alambres.
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
* Ahora ahora podrá colocar el juego en una ubicación específica mediante gazing en él, mediante el gesto de Select (**A** o la barra espaciadora) y, a continuación, pasar a una nueva ubicación y volver a usar el gesto de Select.

## <a name="the-end"></a>Fin

Y es el final de este tutorial.

Ha aprendido conceptos:

* Cómo crear una aplicación holográfica en Unity.
* Cómo hacer que el uso de mirada, gestos, voz, sonidos y asignación espacial.
* Cómo compilar e implementar una aplicación mediante Visual Studio.

Ahora está listo para comenzar a crear sus propias aplicaciones holográficas.

## <a name="see-also"></a>Vea también

* [Conceptos básicos de MR 101: Proyecto completo con el dispositivo](holograms-101.md)
* [Gaze](gaze.md)
* [Gestos](gestures.md)
* [Entrada de voz](voice-input.md)
* [Sonido espacial](spatial-sound.md)
* [Asignación espacial](spatial-mapping.md)
