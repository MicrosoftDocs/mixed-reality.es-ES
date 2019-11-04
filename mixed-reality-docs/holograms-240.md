---
title: MR Sharing 240-varios dispositivos HoloLens
description: Siga este tutorial de codificación con Unity, Visual Studio y HoloLens para obtener información detallada sobre el uso compartido de hologramas.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-Unity, uso compartido, redes, Academia, tutorial
ms.openlocfilehash: 0d8e8f4484546d82caadf162623a6f4059eb2f00
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73434567"
---
>[!NOTE]
>Los tutoriales de la Academia de realidad mixta se han diseñado con HoloLens (1º generación) y con auriculares de realidad mixta en mente.  Como tal, creemos que es importante dejar estos tutoriales en vigor para los desarrolladores que sigan buscando instrucciones para el desarrollo de esos dispositivos.  Estos tutoriales **_no_** se actualizarán con los conjuntos de herramientas o las interacciones más recientes que se usan para HoloLens 2.  Se mantendrán para seguir trabajando en los dispositivos compatibles. Se ha publicado [una nueva serie de tutoriales](mrlearning-base.md) para HoloLens 2.

<br>

# <a name="mr-sharing-240-multiple-hololens-devices"></a>MR Sharing 240: varios dispositivos HoloLens

Los hologramas reciben la presencia en nuestro mundo a medida que avanzamos en el espacio. HoloLens mantiene los hologramas en su lugar mediante el uso de varios [sistemas de coordenadas](coordinate-systems.md) para realizar un seguimiento de la ubicación y la orientación de los objetos. Cuando compartimos estos sistemas de coordenadas entre dispositivos, podemos crear una experiencia compartida que nos permita participar en un mundo holográfica compartido.

En este tutorial, haremos lo siguiente:

* Configurar una red para una experiencia compartida.
* Compartir hologramas en dispositivos HoloLens.
* Descubra otras personas en nuestro mundo holográfica compartido.
* Cree una experiencia interactiva compartida donde pueda dirigirse a otros reproductores e iniciar proyectiles en ellos.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Recurso</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Cascos envolventes</a></th>
</tr><tr>
<td>MR Sharing 240: varios dispositivos HoloLens</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de empezar

### <a name="prerequisites"></a>Requisitos previos

* Un equipo con Windows 10 configurado con las [herramientas correctas instaladas](install-the-tools.md) con acceso a Internet.
* Al menos dos dispositivos HoloLens [configurados para el desarrollo](using-visual-studio.md#enabling-developer-mode).

### <a name="project-files"></a>Archivos de proyecto

* Descargue los [archivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) requeridos por el proyecto. Requiere Unity 2017,2 o posterior.
  * Si sigue necesitando compatibilidad con Unity 5,6, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).
  * Si sigue necesitando compatibilidad con Unity 5,5, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).
  * Si sigue necesitando compatibilidad con Unity 5,4, use [esta versión](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).
* Elimine el archivo de los archivos en el escritorio o en otra ubicación de fácil acceso. Mantenga el nombre de la carpeta como **SharedHolograms**.

>[!NOTE]
>Si desea examinar el código fuente antes de la descarga, está [disponible en github](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).

## <a name="chapter-1---holo-world"></a>Capítulo 1: Hololens World

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

En este capítulo, se configurará el primer proyecto de Unity y se recorrerá el proceso de compilación e implementación.

### <a name="objectives"></a>Objetivos

* Configure Unity para desarrollar aplicaciones holográficas.
* Vea su holograma.

### <a name="instructions"></a>Instrucciones

* Inicia Unity.
* Seleccione **abrir**.
* Escriba Location como la carpeta **SharedHolograms** que ha desarchivado anteriormente.
* Seleccione **nombre del proyecto** y haga clic en **Seleccionar carpeta**.
* En la **jerarquía**, haga clic con el botón secundario en la **cámara principal** y seleccione **eliminar**.
* En la carpeta **HoloToolkit-Sharing-240/Prefabs/cámara** , busque la **cámara principal** recurso prefabricado.
* Arrastre y coloque la **cámara principal** en la **jerarquía**.
* En la **jerarquía**, haga clic en **crear** y **crear vacío**.
* Haga clic con el botón derecho en el nuevo **GameObject** y seleccione **cambiar nombre**.
* Cambie el nombre de GameObject a **HologramCollection**.
* Seleccione el objeto **HologramCollection** en la **jerarquía**.
* En el **Inspector** , establezca la posición de la **transformación** en: **X: 0, y:-0,25, Z: 2**.
* En la carpeta **hologramas** del **panel Proyecto**, busque el recurso **EnergyHub** .
* Arrastre y coloque el objeto **EnergyHub** desde el **panel Proyecto** hasta la **jerarquía** como **elemento secundario de HologramCollection**.
* Seleccione el **archivo > guardar la escena como...**
* Asigne a la escena el nombre **SharedHolograms** y haga clic en **Guardar**.
* Presione el botón **reproducir** en Unity para obtener una vista previa de los hologramas.
* Presione **reproducir** una segunda vez para detener el modo de vista previa.

**Exportar el proyecto de Unity a Visual Studio**

* En Unity, seleccione **archivo > configuración de compilación**.
* Haga clic en **Agregar escenas abiertas** para agregar la escena.
* Seleccione **plataforma universal de Windows** en la lista **plataforma** y haga clic en **cambiar plataforma**.
* Establezca **SDK** en **universal 10**.
* Establezca **el dispositivo de destino** en **HoloLens** y el tipo de **compilación de UWP** en **D3D**.
* Compruebe **los C# proyectos de Unity**.
* Haz clic en **Compilación**.
* En la ventana del explorador de archivos que aparece, cree una **nueva carpeta** denominada "app".
* Haga clic en la carpeta de la **aplicación** .
* Presione **Seleccionar carpeta**.
* Cuando se haya realizado Unity, aparecerá una ventana del explorador de archivos.
* Abra la carpeta de la **aplicación** .
* Abra **SharedHolograms. sln** para iniciar Visual Studio.
* Con la barra de herramientas superior de Visual Studio, cambie el destino de Debug a **Release** y de ARM a **x86**.
* Haga clic en la flecha desplegable situada junto a equipo local y seleccione **dispositivo remoto**.
    * Establezca la **Dirección** en el nombre o la dirección IP de HoloLens. Si no conoce la dirección IP del dispositivo, consulte **configuración > redes & Internet > opciones avanzadas** o pregunte a Cortana **, ¿cuál es mi dirección IP? "** .
    * Deje el **modo de autenticación** establecido en **universal**.
    * Haga clic en **seleccionar**
* Haga clic en **Depurar > iniciar sin depurar** o presione **Ctrl + F5**. Si esta es la primera vez que se implementa en el dispositivo, tendrá que [emparejarla con Visual Studio](using-visual-studio.md#pairing-your-device).
* Pon en tu HoloLens y busca el holograma de EnergyHub.

## <a name="chapter-2---interaction"></a>Capítulo 2: interacción

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

En este capítulo, Interactuaremos con los hologramas. En primer lugar, vamos a agregar un cursor para visualizar nuestra [mirada](gaze-and-commit.md). Después, agregaremos [gestos](gaze-and-commit.md#composite-gestures) y usaremos nuestra mano para colocar los hologramas en el espacio.

### <a name="objectives"></a>Objetivos

* Use la entrada de fijamente para controlar un cursor.
* Use la entrada de gestos para interactuar con los hologramas.

### <a name="instructions"></a>Instrucciones

**Gaze**

* En el **Panel jerarquía** , seleccione el objeto **HologramCollection** .
* En el **panel Inspector** , haga clic en el botón **Agregar componente** .
* En el menú, escriba en el cuadro de búsqueda, **mira el administrador**. Seleccione el resultado de la búsqueda.
* En la carpeta **HoloToolkit-Sharing-240\Prefabs\Input** , busque el recurso **cursor** .
* Arrastre y coloque el activo del **cursor** en la **jerarquía**.

**Hacia**

* En el **Panel jerarquía** , seleccione el objeto **HologramCollection** .
* Haga clic en **Agregar componente** y escriba **Administrador de gestos** en el campo de búsqueda. Seleccione el resultado de la búsqueda.
* En el **Panel jerarquía**, expanda **HologramCollection**.
* Seleccione el objeto **EnergyHub** secundario.
* En el **panel Inspector** , haga clic en el botón **Agregar componente** .
* En el menú, escriba en la ubicación del **holograma**del cuadro de búsqueda. Seleccione el resultado de la búsqueda.
* Guarde la escena seleccionando **archivo > guardar escena**.

**Implementación y disfrute**

* Cree e implemente en HoloLens con las instrucciones del capítulo anterior.
* Una vez que la aplicación se inicie en HoloLens, mueva el dedo y observe cómo el EnergyHub sigue su mirada.
* Observe cómo aparece el cursor cuando mira el holograma y cambia a una luz puntual cuando no se Gazing en un holograma.
* Realice una derivación aérea para colocar el holograma. En este momento, en nuestro proyecto, solo puede colocar el holograma una vez (vuelva a implementarlo para intentarlo de nuevo).

## <a name="chapter-3---shared-coordinates"></a>Capítulo 3: coordenadas compartidas

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

Es divertido ver los hologramas e interactuar con ellos, pero vamos a continuar. Configuraremos nuestra primera experiencia compartida: un holograma todo el mundo puede ver juntos.

### <a name="objectives"></a>Objetivos

* Configurar una red para una experiencia compartida.
* Establezca un punto de referencia común.
* Compartir sistemas de coordenadas entre dispositivos.
* Todos ven el mismo holograma.

>[!NOTE]
>Las funcionalidades **InternetClientServer** y **PrivateNetworkClientServer** se deben declarar para que una aplicación se conecte al servidor de uso compartido. Esto ya se hace en los hologramas 240, pero tenga esto en cuenta para sus propios proyectos.

>1. En el editor de Unity, vaya a la configuración del reproductor en "Editar > configuración del proyecto > Player".
>2. Haga clic en la pestaña "tienda Windows"
>3. En la sección "configuración de publicación > funcionalidades", Compruebe la funcionalidad de **InternetClientServer** y la capacidad de **PrivateNetworkClientServer**

### <a name="instructions"></a>Instrucciones

* En el **panel Proyecto** , vaya a la carpeta **HoloToolkit-Sharing-240\Prefabs\Sharing** .
* Arrastre y coloque el recurso prefabricado de **uso compartido** en el **Panel jerarquía**.

A continuación, es necesario iniciar el servicio de uso compartido. Solo **un equipo** en la experiencia compartida debe realizar este paso.

* En Unity: en el menú de la parte superior, seleccione el **menú HoloToolkit-Sharing-240**.
* Seleccione el elemento **servicio de uso compartido de inicio** en la lista desplegable.
* Active la opción **red privada** y haga clic en **permitir el acceso** cuando aparezca el mensaje del firewall.
* Anote la dirección IPv4 que se muestra en la ventana de la consola del servicio de uso compartido. Se trata de la misma dirección IP que el equipo en el que se ejecuta el servicio.

Siga el resto de las instrucciones en **todos los equipos** que se unirán a la experiencia compartida.

* En la **jerarquía**, seleccione el objeto de **uso compartido** .
* En el **Inspector**, en el componente de la **fase de uso compartido** , cambie la **dirección del servidor** de "localhost" a la dirección IPv4 del equipo que ejecuta SharingService. exe.
* En la **jerarquía** , seleccione el objeto **HologramCollection** .
* En el **Inspector** , haga clic en el botón **Agregar componente** .
* En el cuadro de búsqueda, escriba **Import Export Anchor Manager**. Seleccione el resultado de la búsqueda.
* En el **panel Proyecto** , vaya a la carpeta **scripts** .
* Haga doble clic en el script **HologramPlacement** para abrirlo en Visual Studio.
* Reemplace el contenido por el código siguiente.

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

* De nuevo en Unity, seleccione el **HologramCollection** en el **Panel de jerarquías**.
* En el **panel Inspector** , haga clic en el botón **Agregar componente** .
* En el menú, escriba en el cuadro de búsqueda **App State Manager**. Seleccione el resultado de la búsqueda.

**Implementación y disfrute**

* Compile el proyecto para los dispositivos HoloLens.
* Designe un HoloLens en el que implementar primero. Tendrá que esperar a que el delimitador se cargue en el servicio antes de poder colocar el EnergyHub (esto puede tardar ~ 30-60 segundos). Hasta que se realice la carga, se omitirán los gestos de TAP.
* Una vez colocada la EnergyHub, su ubicación se cargará en el servicio y, a continuación, podrá implementar en todos los demás dispositivos HoloLens.
* Cuando un nuevo HoloLens se une por primera vez a la sesión, es posible que la ubicación de EnergyHub no sea correcta en ese dispositivo. Sin embargo, en cuanto se hayan descargado las ubicaciones de delimitador y EnergyHub desde el servicio, el EnergyHub debe saltar a la nueva ubicación compartida. Si esto no ocurre en menos de 30-60 segundos, desplácese a la ubicación donde se encontraba HoloLens original al establecer el delimitador para recopilar más pistas de entorno. Si la ubicación sigue sin bloquearse, vuelva a realizar la implementación en el dispositivo.
* Cuando todos los dispositivos estén listos y ejecuten la aplicación, busque EnergyHub. ¿Puede estar de acuerdo con la ubicación del holograma y la dirección en la que el texto está enfrente?

## <a name="chapter-4---discovery"></a>Capítulo 4: detección

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

Ahora todo el mundo puede ver el mismo holograma. Ahora, vamos a ver a todos los demás conectados a nuestro mundo holográfica compartido. En este capítulo, se tomará la ubicación principal y la rotación de todos los demás dispositivos HoloLens en la misma sesión de uso compartido.

### <a name="objectives"></a>Objetivos

* Descubra entre sí en nuestra experiencia compartida.
* Elegir y compartir un avatar de reproductor.
* Adjunte el avatar del jugador junto a los cabezales de todos.

### <a name="instructions"></a>Instrucciones

* En el **panel Proyecto** , vaya a la carpeta **hologramas** .
* Arrastre y coloque **PlayerAvatarStore** en la **jerarquía**.
* En el **panel Proyecto** , vaya a la carpeta **scripts** .
* Haga doble clic en el script **AvatarSelector** para abrirlo en Visual Studio.
* Reemplace el contenido por el código siguiente.

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

* En la **jerarquía** , seleccione el objeto **HologramCollection** .
* En el **Inspector** , haga clic en **Agregar componente**.
* En el cuadro de búsqueda, escriba **Administrador del reproductor local**. Seleccione el resultado de la búsqueda.
* En la **jerarquía** , seleccione el objeto **HologramCollection** .
* En el **Inspector** , haga clic en **Agregar componente**.
* En el cuadro de búsqueda, escriba **Administrador de reproductores remotos**. Seleccione el resultado de la búsqueda.
* Abra el script **HologramPlacement** en Visual Studio.
* Reemplace el contenido por el código siguiente.

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

* Abra el script **AppStateManager** en Visual Studio.
* Reemplace el contenido por el código siguiente.

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

**Implementación y disfrute**

* Compile e implemente el proyecto en sus dispositivos HoloLens.
* Cuando escuche un sonido de ping, busque el menú de selección de Avatar y seleccione un avatar con el gesto de punteo de aire.
* Si no está mirando ningún holograma, la luz puntual alrededor del cursor girará un color diferente cuando HoloLens se comunique con el servicio: inicializando (púrpura oscuro), descargando el delimitador (verde), importando/exportando datos de ubicación (amarillo), cargar el delimitador (azul). Si la luz de punto alrededor del cursor es el color predeterminado (púrpura claro), está listo para interactuar con otros jugadores en la sesión.
* Mire otras personas conectadas a su espacio: en este caso, habrá un robot holográfica que se flota por encima de su hombro y imitando sus movimientos de cabeza.

## <a name="chapter-5---placement"></a>Capítulo 5: selección de ubicación

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

En este capítulo, haremos que el anclaje sea capaz de colocarse en superficies del mundo real. Usaremos coordenadas compartidas para colocar ese delimitador en el punto intermedio entre todos los usuarios conectados a la experiencia compartida.

### <a name="objectives"></a>Objetivos

* Coloque los hologramas en la malla de asignación espacial basada en la posición principal de los jugadores.

### <a name="instructions"></a>Instrucciones

* En el **panel Proyecto** , vaya a la carpeta **hologramas** .
* Arrastre y coloque el recurso prefabricado de **CustomSpatialMapping** en la **jerarquía**.
* En el **panel Proyecto** , vaya a la carpeta **scripts** .
* Haga doble clic en el script **AppStateManager** para abrirlo en Visual Studio.
* Reemplace el contenido por el código siguiente.

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

* En el **panel Proyecto** , vaya a la carpeta **scripts** .
* Haga doble clic en el script **HologramPlacement** para abrirlo en Visual Studio.
* Reemplace el contenido por el código siguiente.

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

**Implementación y disfrute**

* Compile e implemente el proyecto en sus dispositivos HoloLens.
* Cuando la aplicación esté lista, destaque un círculo y observe cómo aparece EnergyHub en el centro de todos.
* Puntee para colocar el EnergyHub.
* Pruebe el comando de voz "restablecer destino" para elegir la copia de seguridad de EnergyHub y trabajar conjuntamente como un grupo para trasladar el holograma a una nueva ubicación.

## <a name="chapter-6---real-world-physics"></a>Capítulo 6: física del mundo real

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

En este capítulo, vamos a agregar hologramas que rebotan las superficies del mundo real. Vea el espacio lleno con proyectos que usted y sus amigos han lanzado.

### <a name="objectives"></a>Objetivos

* Inicie los proyectiles que rebotan las superficies del mundo real.
* Comparta los proyectiles para que otros jugadores puedan verlos.

### <a name="instructions"></a>Instrucciones

* En la **jerarquía** , seleccione el objeto **HologramCollection** .
* En el **Inspector** , haga clic en **Agregar componente**.
* En el cuadro de búsqueda, escriba **selector de proyectil**. Seleccione el resultado de la búsqueda.

**Implementación y disfrute**

* Cree e implemente en sus dispositivos HoloLens.
* Cuando la aplicación se ejecuta en todos los dispositivos, realice una derivación aérea para lanzar el proyectil en las superficies del mundo real.
* Vea lo que sucede cuando el proyectil entra en conflicto con el avatar de otro jugador.

## <a name="chapter-7---grand-finale"></a>Capítulo 7: final general

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

En este capítulo, se descubrirá un portal que solo se puede detectar con colaboración.

### <a name="objectives"></a>Objetivos

* Trabaje de forma conjunta para iniciar suficientes proyectiles en el anclaje para descubrir un portal secreto.

### <a name="instructions"></a>Instrucciones

* En el **panel Proyecto** , vaya a la carpeta **hologramas** .
* Arrastre y coloque el activo de **submundo** como **elemento secundario de HologramCollection**.
* Con **HologramCollection** seleccionado, haga clic en el botón **Agregar componente** en el **Inspector**.
* En el menú, escriba en el cuadro de búsqueda **ExplodeTarget**. Seleccione el resultado de la búsqueda.
* Con **HologramCollection** seleccionado, en la **jerarquía** , arrastre el objeto **EnergyHub** hasta el campo de **destino** en el **Inspector**.
* Con **HologramCollection** seleccionado, en la **jerarquía** , arrastre el objeto de **submundo** al campo de **submundo** del **Inspector**.

**Implementación y disfrute**

* Cree e implemente en sus dispositivos HoloLens.
* Cuando se haya iniciado la aplicación, colabore con el fin de lanzar proyectiles en el EnergyHub.
* Cuando aparezca el submundo, inicie los proyectiles en el mundo de los robots (golpee un robot tres veces para obtener una diversión adicional).
