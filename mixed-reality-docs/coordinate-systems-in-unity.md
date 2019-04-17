---
title: Sistemas de coordenadas en Unity
description: Aprenda a crear su asiento permanente, sala de escalado y escalado del mundo mixto realidad experiencias en Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema de coordenadas, del sistema de coordenadas espacial, sólo orientación, sentado a escala, escala permanente, sala-escala, escala mundial, colocada de 360 grados, permanente, sala, mundo, escala, posición, orientación, Unity, delimitador, delimitador espacial, delimitador del mundo, bloqueado contra el mundo, mundo de bloqueo, bloqueado de cuerpo, cuerpo de bloqueo, seguimiento de pérdida, locatability, los límites indicados, centrar
ms.openlocfilehash: 36d74488b23587e5c89b40faf97921a10be7473b
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605774"
---
# <a name="coordinate-systems-in-unity"></a>Sistemas de coordenadas en Unity

Windows Mixed Reality es compatible con aplicaciones en una amplia gama de [experimentar escalas](coordinate-systems.md), desde aplicaciones sólo orientación y asentada de escala de seguridad a través de aplicaciones de escala de la sala. En HoloLens, puede avanzar y compilar aplicaciones a escala mundial que permiten a los usuarios recorrer más allá de 5 metros, exploración de toda una planta de un edificio y versiones posteriores.

Es el primer paso para crear una experiencia de realidad mixta en Unity determinar qué [experimentar escala](coordinate-systems.md) destino de la aplicación.

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>Creación de una experiencia sólo orientación o asentada de escala

**Namespace:** *UnityEngine.XR*<br>
**Tipo:** *XRDevice*

Para crear un **sólo orientación** o **escala asentada experiencia**, debe establecer Unity en el diseño de fondo el tipo de espacio de seguimiento. Esto establece el sistema de coordenadas de Unity para realizar un seguimiento el [marco estático de referencia](coordinate-systems.md#spatial-coordinate-systems). En el modo de seguimiento inmóvil, se coloca el contenido en el editor justo delante de la ubicación predeterminada de la cámara (hacia delante es -Z) aparecerá delante del usuario cuando se inicia la aplicación.

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**Namespace:** *UnityEngine.XR*<br>
**Tipo:** *InputTracking*

Para una pura **experiencia sólo orientación** como un visor de vídeo de 360 grados (donde posicionales actualizaciones principales serían dañen la ilusión), a continuación, puede establecer [XR. InputTracking.disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) en true:

```cs
InputTracking.disablePositionalTracking = true;
```

Para un **escala asentada experiencia**, para permitir al usuario más adelante centrar el origen de su asiento, puede llamar a la [XR. InputTracking.Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) método:

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a>Creación de una experiencia de escala permanente o sala de escala

**Namespace:** *UnityEngine.XR*<br>
**Tipo:** *XRDevice*

Para un **permanente escala** o **experiencia sala escala**, deberá colocar contenido en relación con el límite inferior. Razonar el usuario floor utilizando el  **[fase espacial](coordinate-systems.md#spatial-coordinate-systems)**, que representa el usuario definidas por el origen del nivel del suelo y límite de espacio opcional, configurar durante la primera ejecución.

Para asegurarse de que Unity está funcionando con su sistema de coordenadas universales a nivel del suelo, puede establecer si Unity para el tipo de espacio de seguimiento de RoomScale y asegúrese de que el conjunto correctamente:

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```
* Si SetTrackingSpaceType devuelve true, Unity ha cambiado correctamente su sistema de coordenadas universales para realizar un seguimiento el [fase marco de referencia](coordinate-systems.md#spatial-coordinate-systems).
* Si devuelve false SetTrackingSpaceType, Unity no pudo cambiar a fase marco de referencia, probablemente porque el usuario no ha configurado incluso un piso en su entorno. Esto no es habitual, pero puede ocurrir si el escenario se ha configurado en una sala diferente y el dispositivo se ha movido a la sala actual sin que el usuario que configura una nueva fase.

Una vez que la aplicación establece correctamente el tipo de espacio, contenido colocado en la y de seguimiento de RoomScale = 0 plano aparecerá en el suelo. El origen en (0, 0, 0) será la ubicación específica en el suelo donde puede levantar el usuario durante la instalación de la sala, con -Z que representa la dirección de avance que se enfrentan durante la instalación.

**Namespace:** *UnityEngine.Experimental.XR*<br>
**Tipo:** *Límite*

En el código de script, puede, a continuación, llame al método TryGetGeometry para usted es el tipo de UnityEngine.Experimental.XR.Boundary para obtener un polígono límites, especificar un tipo de límite de TrackedArea. Si el usuario ha definido un límite (obtener una lista de vértices), sabrá que es segura entregar un **experiencia sala escala** al usuario, donde puede guían por la escena crear.

Tenga en cuenta que el sistema automáticamente se representará el límite cuando el usuario se aproxima a él. La aplicación no necesita usar este polígono para representar el límite de sí mismo. Sin embargo, puede elegir disponer de los objetos de la escena con este polígono límites, para asegurarse de que el usuario físicamente puede llegar a esos objetos sin teleporting:

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a>Creación de una experiencia del mundo a escala

**Namespace:** *UnityEngine.XR.WSA*<br>
**Tipo:** *WorldAnchor*

Para true **experiencias del mundo a escala** en HoloLens que permiten a los usuarios consultar más allá de 5 metros, necesitará nuevas técnicas más allá de los que se usan para experiencias de escala de la sala. Es una técnica clave que se va a usar crear un [delimitador espacial](coordinate-systems.md#spatial-anchors) para bloquear un clúster de hologramas exactamente en lugar del mundo físico, independientemente de cuánto ha trasladado el usuario y, a continuación, [encontrar esos hologramas nuevo en versiones posteriores sesiones](coordinate-systems.md#spatial-anchor-persistence).

En Unity, cree un anclaje espacial agregando el **WorldAnchor** componente Unity a un GameObject.

### <a name="adding-a-world-anchor"></a>Agregar un anclaje del mundo

Para agregar un anclaje del mundo, llame AddComponent<WorldAnchor>() en el objeto de juego con la transformación que desean fijar en el mundo real.

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

Ya está. Este objeto de juego ahora se anclará a su ubicación actual en el mundo físico, puede ver sus coordenadas universales de Unity ajustar ligeramente con el tiempo para asegurarse de que alineación físico. Use [persistencia](persistence-in-unity.md) encontrarlo delimitados ubicación nuevo en una sesión de la aplicación en un futuro.

### <a name="removing-a-world-anchor"></a>Eliminación de un anclaje del mundo

Si ya no desea que el GameObject bloqueado en una ubicación del mundo físico y no tiene intención de moverlo este marco, simplemente puede llamar Destroy en el componente de anclaje del mundo.

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

Si desea mover el GameObject este marco, deberá llamar a DestroyImmediate en su lugar.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>Mover un mundo anclada GameObject

No se pueden mover del GameObject mientras un anclaje del mundo está en ella. Si necesita mover el GameObject este marco, es preciso:
1. El componente de anclaje del mundo DestroyImmediate
2. Mover el GameObject
3. Agregue un nuevo componente de anclaje del mundo para el GameObject.

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Gestionar los cambios de Locatability

Un WorldAnchor puede no ser localizable en el mundo físico en un momento dado. Si esto sucede, Unity no va a actualizar la transformación del objeto anclado. Esto también puede cambiar mientras se ejecuta una aplicación. Error al controlar el cambio en locatability hará que el objeto que no aparezca en la ubicación física adecuada en el mundo.

Para recibir notificaciones sobre cambios locatability:
1. Suscribirse al evento OnTrackingChanged
2. Controlar el evento

El **OnTrackingChanged** evento se llamará siempre que el delimitador espacial subyacente cambia entre un estado de ser localizable frente a no ser localizable.

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

A continuación, controlar el evento:

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

A veces los delimitadores se encuentran inmediatamente. En este caso, se establecerá en true cuando esta propiedad isLocated del delimitador de AddComponent<WorldAnchor>() devuelve. Como resultado, no se desencadenará el evento OnTrackingChanged. Un modelo limpio sería llamar a su controlador OnTrackingChanged con el estado inicial de IsLocated después de adjuntar un delimitador.

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a>Uso compartido de los anclajes en todos los dispositivos

Puede usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure espacial delimitadores</a> para crear un anclaje en la nube duraderas desde un WorldAnchor local, que, a continuación, puede localizar su aplicación a través de varios HoloLens, dispositivos iOS y Android.  Al compartir un anclaje espacial comunes en varios dispositivos, cada usuario puede ver el contenido representado en relación con ese delimitador en la misma ubicación física.  Esto permite experiencias compartidas en tiempo real.

Para empezar a crear experiencias compartidas en Unity, pruebe el minuto 5 <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">guías de inicio rápido de Azure espacial delimitadores Unity</a>.

Una vez que esté en marcha con delimitadores espacial de Azure, a continuación, puede <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">crear y localizar los anclajes en Unity</a>.

## <a name="see-also"></a>Vea también
* [Escalas de la experiencia](coordinate-systems.md#mixed-reality-experience-scales)
* [Fase espacial](coordinate-systems.md#stage-frame-of-reference)
* [Seguimiento de la pérdida en Unity](tracking-loss-in-unity.md)
* [Delimitadores espaciales](spatial-anchors.md)
* [Persistencia en Unity](persistence-in-unity.md)
* [Experiencias compartidas en Unity](shared-experiences-in-unity.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure delimitadores espaciales</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Delimitadores espaciales Azure SDK para Unity</a>