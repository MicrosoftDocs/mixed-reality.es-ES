---
title: MR compartir 240 - varios dispositivos HoloLens
description: Siga este tutorial con Unity, Visual Studio y HoloLens para conocer los detalles de uso compartido hologramas de codificación.
author: keveleigh
ms.author: kurtie
ms.date: 03/21/2018
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit unity, compartir, redes, academy, tutorial
ms.openlocfilehash: 70a39a739d360a5032bc8df76b6f0bd57521d9ec
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59601388"
---
>[!NOTE]
>Los tutoriales de Mixed Reality Academy se diseñaron con HoloLens (gen 1) y Mixed Reality Inmersivos en mente.  Por lo tanto, creemos que es importante dejar estos tutoriales en su lugar para los desarrolladores que todavía están buscando orientación en el desarrollo para esos dispositivos.  Estos tutoriales le **_no_** actualizarse con las interacciones que se usan para HoloLens 2 o los conjuntos de herramientas más recientes.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Habrá una nueva serie de tutoriales que se registrará en el futuro que demostrará cómo desarrollar para HoloLens 2.  Este aviso se actualizará con un vínculo a esos tutoriales cuando se hayan registrado.

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a>MR 240 de uso compartido: Varios dispositivos HoloLens

Hologramas tienen presencia en nuestro mundo al permanecer en su lugar conforme se mueve en el espacio. HoloLens mantiene hologramas en su lugar utilizando varios [sistemas de coordenadas](coordinate-systems.md) para realizar un seguimiento de la ubicación y la orientación de objetos. Cuando se comparten entre los dispositivos de estos sistemas de coordenadas, podemos crear una experiencia compartida que nos permite tomar parte en un mundo holográfico compartido.

En este tutorial, se hará lo siguiente:

* Configurar una red para una experiencia compartida.
* Compartir hologramas en todos los dispositivos HoloLens.
* Descubra otras personas de nuestro mundo holográfica compartido.
* Cree una experiencia interactiva compartida donde puede tener como destino otros jugadores - e iniciar los proyectiles a ellos.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td>MR 240 de uso compartido: Varios dispositivos HoloLens</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de empezar

### <a name="prerequisites"></a>Requisitos previos

* Un equipo con Windows 10 configurado con el valor correcto [herramientas instaladas](install-the-tools.md) con acceso a Internet.
* Al menos dos dispositivos HoloLens [configurado para el desarrollo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Archivos de proyecto

* Descargue el [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) requerida por el proyecto. Requiere Unity 2017.2 o posterior.
  * Si necesita compatibilidad con Unity 5.6, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).
  * Si necesita compatibilidad con Unity 5.5, utilice [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).
  * Si necesita compatibilidad con Unity 5.4, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).
* Extraer del archivo los archivos en el escritorio o en otros más fáciles de alcanzar la ubicación. Mantenga el nombre de carpeta **SharedHolograms**.

>[!NOTE]
>Si desea buscar en el código de origen antes de descargar, tiene [disponible en GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).

## <a name="chapter-1---holo-world"></a>Capítulo 1: Holo World

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

En este capítulo, crearemos nuestro primer proyecto de Unity y paso a través de la compilación de la instalación y proceso de implementación.

### <a name="objectives"></a>Objetivos

* La instalación de Unity para desarrollar aplicaciones holográficas.
* ¡Vea su holograma!

### <a name="instructions"></a>Instrucciones

* Inicie Unity.
* Seleccione **abierto**.
* Escriba la ubicación que el **SharedHolograms** carpetas que anteriormente sin archivar.
* Seleccione **nombre del proyecto** y haga clic en **seleccionar la carpeta**.
* En el **jerarquía**, haga clic en el **cámara principal** y seleccione **eliminar**.
* En el **HoloToolkit-uso compartido-240/prefabricados/cámara** carpeta, busque la **cámara principal** prefabricado.
* Arrastre y coloque el **cámara principal** en el **jerarquía**.
* En el **jerarquía**, haga clic en **crear** y **crear vacío**.
* Haga clic en el nuevo **GameObject** y seleccione **cambiar el nombre**.
* Cambiar el nombre de la GameObject a **HologramCollection**.
* Seleccione el **HologramCollection** objeto en el **jerarquía**.
* En el **Inspector** establecer el **transformar posición** para: **X: 0, Y: -0.25, Z: 2**.
* En el **hologramas** carpeta en el **panel proyecto**, busque el **EnergyHub** activo.
* Arrastre y coloque el **EnergyHub** objeto desde el **panel proyecto** a la **jerarquía** como un **secundarios de HologramCollection**.
* Seleccione **archivo > Guardar escena como...**
* Nombre de la escena **SharedHolograms** y haga clic en **guardar**.
* Presione el **reproducir** en Unity para obtener una vista previa de sus hologramas botón.
* Presione **reproducir** una segunda vez para detener el modo de vista previa.

**Exporta el proyecto de Unity a Visual Studio**
* En Seleccione Unity **archivo > configuración de compilación**.
* Haga clic en **agregar escenas abierto** para agregar la escena.
* Seleccione **Universal Windows Platform** en el **plataforma** lista y haga clic en **Cambiar plataforma**.
* Establecer **SDK** a **10 Universal**.
* Establecer **dispositivo de destino** a **HoloLens** y **el tipo de compilación UWP** a **D3D**.
* Comprobar **Unity C# proyectos**.
* Haz clic en **Compilación**.
* En la ventana del explorador de archivos que aparece, cree un **nueva carpeta** denominada "Aplicación".
* Solo haga clic en el **aplicación** carpeta.
* Presione **Seleccionar carpeta**.
* Cuando se realiza a Unity, aparecerá una ventana del explorador de archivos.
* Abra el **aplicación** carpeta.
* Abra **SharedHolograms.sln** para iniciar Visual Studio.
* Uso de la barra de herramientas superior en Visual Studio, cambiar el destino de depuración a **versión** y de ARM para **X86**.
* Haga clic en la flecha desplegable situada junto a la máquina Local y seleccione **dispositivo remoto**.
    * Establecer el **dirección** en el nombre o dirección IP de su HoloLens. Si no conoce la dirección IP del dispositivo, busque en **configuración > red e Internet > Opciones avanzadas** o solicitar a Cortana **"Hola Cortana, ¿cuál es mi dirección IP?"**
    * Deje el **modo de autenticación** establecido en **Universal**.
    * Haga clic en **seleccionar**
* Haga clic en **Depurar > Iniciar sin depurar** o presione **Ctrl + F5**. Si se trata de la primera vez que la implementación en el dispositivo, deberá [emparejarlo con Visual Studio](using-visual-studio.md#pairing-your-device-hololens).
* Colocar en su HoloLens y busque el holograma EnergyHub.

## <a name="chapter-2---interaction"></a>Capítulo 2: interacción

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

En este capítulo, interactuamos con nuestros hologramas. En primer lugar, vamos a agregar un cursor para visualizar nuestro [que mirar](gaze.md). A continuación, agregaremos [gestos](gestures.md) y use nuestra mano para colocar nuestros hologramas en el espacio.

### <a name="objectives"></a>Objetivos

* Utilice la mirada de entrada para controlar un cursor.
* Utilice el gesto de entrada para interactuar con hologramas.

### <a name="instructions"></a>Instrucciones

**Gaze**
* En el **panel jerarquía** seleccione la **HologramCollection** objeto.
* En el **panel Inspector** haga clic en el **Agregar componente** botón.
* En el menú, escriba en el cuadro de búsqueda **que mirar Manager**. Seleccione el resultado de búsqueda.
* En el **240\Prefabs\Input compartir HoloToolkit** carpeta, busque la **Cursor** activo.
* Arrastre y coloque el **Cursor** activo hasta la **jerarquía**.

**Gesto**
* En el **panel jerarquía** seleccione la **HologramCollection** objeto.
* Haga clic en **Agregar componente** y tipo **gesto Manager** en el campo de búsqueda. Seleccione el resultado de búsqueda.
* En el **panel jerarquía**, expanda **HologramCollection**.
* Seleccione el elemento secundario **EnergyHub** objeto.
* En el **panel Inspector** haga clic en el **Agregar componente** botón.
* En el menú, escriba en el cuadro de búsqueda **holograma colocación**. Seleccione el resultado de búsqueda.
* Guarde la escena seleccionando **archivo > Guardar escena**.

**Implementar y disfrute**
* Compilar e implementar en su HoloLens, siguiendo las instrucciones del capítulo anterior.
* Una vez que inicie la aplicación en su HoloLens, mover la cabeza y observe cómo la EnergyHub sigue a su mirada.
* Observe cómo el cursor aparece cuando visita el holograma y cambia a una luz puntual cuando no gazing en un holograma.
* Realizar una derivación de aire para colocar el holograma. En este momento en el proyecto, puede colocar solo una vez el holograma (vuelva a intentarlo).

## <a name="chapter-3---shared-coordinates"></a>Coordina el capítulo 3: compartidos

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

Es divertido ver e interactuar con hologramas, pero vayamos más lejos. Configuraremos nuestra primera experiencia compartido - un holograma todos pueden ver juntos.

### <a name="objectives"></a>Objetivos

* Configurar una red para una experiencia compartida.
* Establecer un punto de referencia común.
* Compartir sistemas de coordenadas en los dispositivos.
* ¡Todos los usuarios ven el mismo holograma!

>[!NOTE]
>El **InternetClientServer** y **PrivateNetworkClientServer** capacidades se deben declarar para que una aplicación se conecte al servidor de uso compartido. Esto se hace por usted ya hologramas 240, pero Téngalo en cuenta para sus propios proyectos.
>1. En el Editor de Unity, vaya a la configuración del Reproductor, vaya a "Editar > proyecto configuración > Player"
>2. Haga clic en la pestaña "Windows Store"
>3. En la sección "Funcionalidades de publicación configuración >", compruebe el **InternetClientServer** capacidad y la **PrivateNetworkClientServer** capacidad

### <a name="instructions"></a>Instrucciones

* En el **panel proyecto** vaya a la **240\Prefabs\Sharing compartir HoloToolkit** carpeta.
* Arrastre y coloque el **compartir** prefabricado en el **panel jerarquía**.

A continuación, se debe iniciar el servicio de uso compartido. Solo **un PC** en el recurso compartido experimentar debe realizar este paso.
* En Unity: en el menú de la mano de la parte superior, seleccione el **240 compartir HoloToolkit menú**.
* Seleccione el **iniciar el servicio de uso compartido** elemento en la lista desplegable.
* Compruebe el **red privada** opción y haga clic en **permitir el acceso a** cuando aparezca el símbolo del sistema del servidor de seguridad.
* Anote la dirección IPv4 que se muestran en la ventana de consola de servicio de uso compartido. Se trata de la misma dirección IP que la máquina que se ejecuta en el servicio.

Siga el resto de las instrucciones **todos los equipos** que unirá la experiencia compartida.
* En el **jerarquía**, seleccione el **compartir** objeto.
* En el **Inspector**, en el **compartir fase** componente, cambie la **dirección del servidor** desde 'localhost' a la dirección IPv4 de la máquina que ejecuta SharingService.exe.
* En el **jerarquía** seleccione la **HologramCollection** objeto.
* En el **Inspector** haga clic en el **Agregar componente** botón.
* En el cuadro de búsqueda, escriba **Administrador de anclaje de exportación de importación**. Seleccione el resultado de búsqueda.
* En el **panel proyecto** vaya a la **Scripts** carpeta.
* Haga doble clic en el **HologramPlacement** script para abrirlo en Visual Studio.
* Reemplace el contenido con el código siguiente.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;
        
        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* En Unity, seleccione el **HologramCollection** en el **panel jerarquía**.
* En el **panel Inspector** haga clic en el **Agregar componente** botón.
* En el menú, escriba en el cuadro de búsqueda **Administrador de estado de la aplicación**. Seleccione el resultado de búsqueda.

**Implementar y disfrute**
* Compile el proyecto para los dispositivos HoloLens.
* Designar uno HoloLens para implementar en primer lugar. Deberá esperar el delimitador que se cargará en el servicio para poder poner el EnergyHub (este proceso puede tardar aproximadamente entre 30 y 60 segundos). Hasta que se realiza la carga, se omitirán los gestos de tap.
* Después de que se ha colocado el EnergyHub, su ubicación se cargarán en el servicio y, a continuación, puede implementar en todos los demás dispositivos HoloLens.
* Cuando un nuevo HoloLens en primer lugar une a la sesión, la ubicación de la EnergyHub no sea correcta en ese dispositivo. Sin embargo, tan pronto como el delimitador y EnergyHub ubicaciones se han descargado desde el servicio, el EnergyHub debería saltar a la nueva ubicación compartida. Si esto no sucede dentro de ~ 30 y 60 segundos, recorrer en la que se encontraba el HoloLens original cuando se establece el delimitador para recopilar más pistas de entorno. Si no bloquea la ubicación todavía, volver a implementar en el dispositivo.
* Cuando los dispositivos están listos y ejecuta la aplicación, busque el EnergyHub. ¿Puede que todos acuerden ubicación del holograma y en qué dirección mira el texto?

## <a name="chapter-4---discovery"></a>Capítulo 4: detección

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

¡Ahora todo el mundo puede ver el mismo holograma! Ahora vamos a ver todos los usuarios conectados else en nuestro mundo holográfica compartido. En este capítulo, se tomará la ubicación principal y la rotación de todos los demás dispositivos HoloLens en la misma sesión de uso compartida.

### <a name="objectives"></a>Objetivos

* Descubrirse entre ellos en nuestra experiencia compartida.
* Seleccionar y compartir un avatar del Reproductor.
* Adjunte el avatar del Reproductor junto a la mente de todos.

### <a name="instructions"></a>Instrucciones

* En el **panel proyecto** vaya a la **hologramas** carpeta.
* Arrastre y coloque el **PlayerAvatarStore** en el **jerarquía**.
* En el **panel proyecto** vaya a la **Scripts** carpeta.
* Haga doble clic en el **AvatarSelector** script para abrirlo en Visual Studio.
* Reemplace el contenido con el código siguiente.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);        
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* En el **jerarquía** seleccione la **HologramCollection** objeto.
* En el **Inspector** haga clic en **Agregar componente**.
* En el cuadro de búsqueda, escriba **Local Reproductor Manager**. Seleccione el resultado de búsqueda.
* En el **jerarquía** seleccione la **HologramCollection** objeto.
* En el **Inspector** haga clic en **Agregar componente**.
* En el cuadro de búsqueda, escriba **remoto Reproductor Manager**. Seleccione el resultado de búsqueda.
* Abra el **HologramPlacement** script en Visual Studio.
* Reemplace el contenido con el código siguiente.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* Abra el **AppStateManager** script en Visual Studio.
* Reemplace el contenido con el código siguiente.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

**Implementar y disfrute**
* Compilar e implementar el proyecto a los dispositivos HoloLens.
* Cuando oye un sonido haciendo ping, el menú de selección de avatar de buscar y seleccionar un avatar con el gesto de pulsar en el aire.
* Si no ve ningún hologramas, el punto de luz en torno al cursor activará un color diferente cuando su HoloLens se comunican con el servicio: Inicializando (violeta oscuro), que descarga el delimitador (verde), importar o exportar datos de ubicación (amarillo), Cargando el delimitador (azul). Si el punto de luz en torno a su cursor es el color predeterminado (púrpura claro), a continuación, está listo para interactuar con otros jugadores en la sesión.
* Mirar otras personas conectadas a su espacio - habrá un robot holográfico flotando encima de su hombro y mediante la imitación de sus movimientos principales!

## <a name="chapter-5---placement"></a>Capítulo 5: selección de ubicación

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

En este capítulo, nos aseguraremos de hacer el delimitador que se pueden colocar en superficies del mundo real. Vamos a usar coordenadas compartidas para colocar ese delimitador en el punto medio entre todos los usuarios conectados a la experiencia compartida.

### <a name="objectives"></a>Objetivos

* Colocar hologramas en el mapa espacial en función de posición principales de jugadores.

### <a name="instructions"></a>Instrucciones

* En el **panel proyecto** vaya a la **hologramas** carpeta.
* Arrastre y coloque el **CustomSpatialMapping** prefabricado hasta el **jerarquía**.
* En el **panel proyecto** vaya a la **Scripts** carpeta.
* Haga doble clic en el **AppStateManager** script para abrirlo en Visual Studio.
* Reemplace el contenido con el código siguiente.

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to 
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a 
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* En el **panel proyecto** vaya a la **Scripts** carpeta.
* Haga doble clic en el **HologramPlacement** script para abrirlo en Visual Studio.
* Reemplace el contenido con el código siguiente.

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the 
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and 
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

**Implementar y disfrute**
* Compilar e implementar el proyecto a los dispositivos HoloLens.
* Cuando la aplicación esté lista y todo ello en un círculo, tenga en cuenta cómo el EnergyHub aparece en el centro de todo el mundo.
* Pulse para colocar el EnergyHub.
* Pruebe el comando de voz de restablecimiento de destino para seleccionar el EnergyHub copia de seguridad y trabajar juntos como un grupo para mover el holograma a una nueva ubicación.

## <a name="chapter-6---real-world-physics"></a>Capítulo 6: físicas reales

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

En este capítulo, vamos a agregar hologramas que reboten en superficies del mundo real. ¡Ver el espacio se llene con proyectos iniciados por usted y sus amigos!

### <a name="objectives"></a>Objetivos

* Inicie los proyectiles que reboten en superficies del mundo real.
* Comparta los proyectiles para que otros jugadores pueden verlos.

### <a name="instructions"></a>Instrucciones

* En el **jerarquía** seleccione la **HologramCollection** objeto.
* En el **Inspector** haga clic en **Agregar componente**.
* En el cuadro de búsqueda, escriba **proyectil iniciador**. Seleccione el resultado de búsqueda.

**Implementar y disfrute**
* Compilar e implementar en los dispositivos HoloLens.
* Cuando se ejecuta la aplicación en todos los dispositivos, realice una derivación de aire para iniciar proyectil en superficies del mundo real.
* ¡Vea lo que sucede cuando su proyectil entra en conflicto con el avatar del otro reproductor!

## <a name="chapter-7---grand-finale"></a>Capítulo 7 - gran objetivo

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

En este capítulo, se podrá revelar un portal que solo se puede detectar con la colaboración.

### <a name="objectives"></a>Objetivos

* Funcionan conjuntamente para iniciar suficiente proyectiles en el delimitador para revelar un secreto portal!

### <a name="instructions"></a>Instrucciones

* En el **panel proyecto** vaya a la **hologramas** carpeta.
* Arrastre y coloque el **Underword** activo como un **secundarios de HologramCollection**.
* Con **HologramCollection** seleccionado, haga clic en el **Agregar componente** situado en la **Inspector**.
* En el menú, escriba en el cuadro de búsqueda **ExplodeTarget**. Seleccione el resultado de búsqueda.
* Con **HologramCollection** seleccionado desde la **jerarquía** arrastrar el **EnergyHub** de objeto para el **destino** campo el **Inspector**.
* Con **HologramCollection** seleccionado desde la **jerarquía** arrastrar el **Underword** de objeto para el **Underword** campo el  **Inspector de**.

**Implementar y disfrute**
* Compilar e implementar en los dispositivos HoloLens.
* Cuando se inicia la aplicación, colaborar para iniciar los proyectiles a lo EnergyHub.
* Cuando aparezca el Underword, inicie proyectiles a robots Underword (acierto un robot tres veces por diversión adicional).
