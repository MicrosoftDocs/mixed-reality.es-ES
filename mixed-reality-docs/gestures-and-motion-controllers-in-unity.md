---
title: Gestos y controladores de movimiento en Unity
description: Hay dos formas clave de tomar medidas en su mirada en Unity, gestos de mano y controladores de movimiento.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: gestos, controladores de movimiento, Unity, mirados, entrada
ms.openlocfilehash: a85797bfb443f33147c116e90a02c88abda63c67
ms.sourcegitcommit: 2cf3f19146d6a7ba71bbc4697a59064b4822b539
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2019
ms.locfileid: "73926570"
---
# <a name="gestures-and-motion-controllers-in-unity"></a>Gestos y controladores de movimiento en Unity

Hay dos formas clave de tomar medidas en su [mirada en Unity](gaze-in-unity.md), [gestos de mano](gaze-and-commit.md#composite-gestures) y [controladores de movimiento](motion-controllers.md) en HoloLens y HMDs envolventes. Puede tener acceso a los datos de los dos orígenes de entrada espacial a través de las mismas API en Unity.

Unity proporciona dos formas principales de acceder a los datos de entrada espacial para Windows Mixed Reality, las API de *Input. GetButton/Input. GetAxis* comunes que funcionan en varios SDK de Unity XR y una API de *InteractionManager/GestureRecognizer* específica de Windows Mixed Reality que expone el conjunto completo de datos de entrada espaciales disponibles.

## <a name="unity-buttonaxis-mapping-table"></a>Tabla de asignación de ejes y botones de Unity

Los identificadores de botón y de eje de la tabla siguiente se admiten en el administrador de entrada de Unity para controladores de movimiento de Windows Mixed Reality a través de las API *Input. GetButton/GetAxis* , mientras que la columna "específico de Windows Mr" hace referencia a las propiedades disponibles del tipo *InteractionSourceState* . Cada una de estas API se describe en detalle en las secciones siguientes.

Las asignaciones de identificador de botón/eje para Windows Mixed Reality suelen coincidir con los identificadores del botón o del eje Oculus.

Las asignaciones de identificador de botón/eje para Windows Mixed Reality difieren de las asignaciones de OpenVR de dos maneras:
1. La asignación usa identificadores de Touchpad distintos del stick analógico para admitir controladores con thumbsticks y Touchpad.
2. La asignación evita la sobrecarga de los identificadores de botón A y X de los botones de menú, para dejarlos disponibles para los botones de ABXY físicos.

<table>
<tr>
<th rowspan="2">Entrada </th><th colspan="2"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">API de Unity comunes</a><br />(Input. GetButton/GetAxis) </th><th rowspan="2"><a href="gestures-and-motion-controllers-in-unity.md#">API de entrada específica de Windows MR</a><br />XR. WSA. Entradas</th>
</tr><tr>
<th> Mano izquierda </th><th> Mano derecha</th>
</tr><tr>
<td> Seleccionar desencadenador presionado </td><td> Eje 9 = 1,0 </td><td> Eje 10 = 1,0 </td><td> selectPressed</td>
</tr><tr>
<td> Seleccionar desencadenador de valor analógico </td><td> Eje 9 </td><td> Eje 10 </td><td> selectPressedAmount</td>
</tr><tr>
<td> Seleccionar desencadenador parcialmente presionado </td><td> Botón 14 <i>(compatibilidad con el controlador de juegos)</i> </td><td> Botón 15 <i>(compatibilidad con el controlador de juegos)</i> </td><td> selectPressedAmount &gt; 0,0</td>
</tr><tr>
<td> Botón de menú presionado </td><td> Botón 6 * </td><td> Botón 7 * </td><td> menuPressed</td>
</tr><tr>
<td> Botón de control presionado </td><td> Eje 11 = 1,0 (sin valores analógicos)<br />Botón 4 <i>(compatibilidad con el controlador de juegos)</i> </td><td> Eje 12 = 1,0 (sin valores analógicos)<br />Botón 5 <i>(compatibilidad con el controlador de juegos)</i> </td><td> entendido</td>
</tr><tr>
<td> Stick analógico X <i>(izquierda:-1,0, derecha: 1,0)</i> </td><td> Eje 1 </td><td> Eje 4 </td><td> thumbstickPosition. x</td>
</tr><tr>
<td> Stickr Y <i>(superior:-1,0, inferior: 1,0)</i> </td><td> Eje 2 </td><td> Eje 5 </td><td> thumbstickPosition. y</td>
</tr><tr>
<td> Stick analógico presionado </td><td> Botón 8 </td><td> Botón 9 </td><td> thumbstickPressed</td>
</tr><tr>
<td> Touchpad X <i>(izquierda:-1,0, derecha: 1,0)</i> </td><td> Eje 17 * </td><td> Eje 19 * </td><td> touchpadPosition. x</td>
</tr><tr>
<td> Touchpad Y <i>(superior:-1,0, inferior: 1,0)</i> </td><td> Eje 18 * </td><td> Eje 20 * </td><td> touchpadPosition. y</td>
</tr><tr>
<td> Touchpad tocado </td><td> Botón 18 * </td><td> Botón 19 * </td><td> touchpadTouched</td>
</tr><tr>
<td> Touchpad presionado </td><td> Botón 16 * </td><td> Botón 17 * </td><td> touchpadPressed</td>
</tr><tr>
<td> replanteamiento de control de 6DoF o de puntero </td><td colspan="2"> El <i>puño</i> solo representa: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. InputTracking. GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. InputTracking.GetLocalRotation</a></td><td> Pase el <i>control</i> o el <i>puntero</i> como argumento: SourceState. sourcePose. TryGetPosition<br />sourceState.sourcePose.TryGetRotation<br /></td>
</tr><tr>
<td> Estado de seguimiento </td><td colspan="2"> <i>La precisión de la posición y el riesgo de pérdida de origen solo están disponibles a través de la API específica de MR</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState. properties. sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>Estos ID. de botón o eje difieren de los identificadores que usa Unity para OpenVR debido a colisiones en las asignaciones que usan los controladores de juegos, Oculus Touch y OpenVR.

## <a name="grip-pose-vs-pointing-pose"></a>Replanteamiento de control frente a pose de puntero

Windows Mixed Reality admite controladores de movimiento en diversos factores de forma, con el diseño de cada controlador diferente en su relación entre la posición del usuario y la dirección de "avance" natural que deben usar las aplicaciones para apuntar al representar el módem.

Para representar mejor estos controladores, hay dos tipos de supuestos que puede investigar para cada origen de interacción, la representación del **control** y la representación del **puntero**. Las coordenadas de reposición de control y de posición de puntero se expresan en todas las API de Unity en coordenadas globales de Unity.

### <a name="grip-pose"></a>Replanteamiento de control

El **puño** representa la ubicación de la palma de una mano detectada por una HoloLens o la palma que contiene un controlador de movimiento.

En los auriculares envolventes, la representación del puño es la que mejor se usa para representar **la mano del usuario** o **un objeto que se mantiene en la mano del usuario**, como un arma o un cañón. La representación de control también se usa al visualizar un controlador de movimiento, ya que el **modelo representable** proporcionado por Windows para un controlador de movimiento utiliza la representación del puño como su origen y el centro de rotación.

La pose de control se define específicamente de la siguiente manera:
* La **posición del puño**: Palm centroide cuando mantiene el controlador de forma natural, se ajusta hacia la izquierda o derecha para centrar la posición dentro del control. En el controlador de movimiento de Windows Mixed Reality, esta posición generalmente se alinea con el botón de agarre.
* **Eje derecho de la orientación del puño**: cuando se abre por completo la mano para formar una postura plana de 5 dedos, el rayo perpendicular a la palma (hacia delante de la mano izquierda y hacia atrás desde la mano derecha)
* El **eje hacia delante de la orientación del puño**: al cerrar la mano (como si contiene el controlador), el rayo que señala "reenviar" a través del tubo formado por los dedos no Thumb.
* **Eje hacia arriba de la orientación del puño**: el eje hacia arriba implícito por las definiciones derecha y hacia delante.

Puede acceder a la representación del puño a través de la API de entrada entre proveedores (XR) de Unity *[. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) o a través de la API específica de Windows Mr (*SourceState. SourcePose. TryGetPosition/Rotation*, que solicita los datos de pose para el nodo de **control** ).

### <a name="pointer-pose"></a>Representar puntero

La **pose de puntero** representa la punta del controlador que señala hacia delante.

La representación de puntero proporcionada por el sistema se usa mejor para Raycast cuando se **representa el propio modelo de controlador**. Si está representando algún otro objeto virtual en lugar del controlador, como un cañón virtual, debe apuntar con un rayo más natural para ese objeto virtual, como un rayo que viaja a lo largo del barril del modelo de pistola definido por la aplicación. Dado que los usuarios pueden ver el objeto virtual y no el controlador físico, es probable que apunte con el objeto virtual sea más natural para los que usan su aplicación.

Actualmente, la pose de puntero solo está disponible en Unity a través de la API específica de Windows MR, *sourceState. sourcePose. TryGetPosition/Rotation*, pasando *InteractionSourceNode. Pointer* como argumento.

## <a name="controller-tracking-state"></a>Estado de seguimiento del controlador

Al igual que los auriculares, el controlador de movimiento de Windows Mixed Reality no requiere la configuración de sensores de seguimiento externos. En su lugar, el seguimiento de los controladores se realiza mediante sensores en el propio casco.

Si el usuario mueve los controladores fuera del campo de vista del casco, en la mayoría de los casos Windows seguirá inferencia de las posiciones del controlador y las proporcionará a la aplicación. Cuando el controlador ha perdido el seguimiento visual durante el tiempo suficiente, las posiciones del controlador se quitarán de las posiciones de precisión aproximada.

En este punto, el sistema bloqueará el controlador al usuario, realizará un seguimiento de la posición del usuario a medida que se mueven, mientras se expone la verdadera orientación del controlador mediante sus sensores de orientación internos. Muchas aplicaciones que usan Controladores para apuntar a los elementos de la interfaz de usuario y activarlos pueden funcionar con normalidad mientras tienen una precisión aproximada sin que el usuario lo note.

La mejor manera de hacerse una idea es probarlo. Consulte este vídeo con ejemplos de contenido envolvente que funciona con controladores de movimiento en varios Estados de seguimiento:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a>Razonamiento sobre el estado de seguimiento explícitamente

Las aplicaciones que quieren tratar las posiciones de manera diferente según el estado de seguimiento pueden ir más allá e inspeccionar las propiedades en el estado del controlador, como *SourceLossRisk* y *PositionAccuracy*:

<table>
<tr>
<th> Estado de seguimiento </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td>   de <b>alta precisión</b></td><td style="background-color: green; color: white"> &lt; 1,0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Alta precisión (riesgo de pérdida)</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Precisión aproximada</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: orange"> Aproximado </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Ninguna posición</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: orange"> Aproximado </td><td style="background-color: orange"> falso</td>
</tr>
</table>

Estos Estados de seguimiento del controlador de movimiento se definen de la siguiente manera:
* **Alta precisión:** Aunque el controlador de movimiento está en el campo de vista del casco, normalmente proporcionará posiciones de alta precisión en función del seguimiento visual. Tenga en cuenta que un controlador de movimiento que deja momentáneamente el campo de vista o que se oculta momentáneamente de los sensores de auriculares (por ejemplo, por la otra mano del usuario) seguirá devolviendo supuestos de alta precisión durante un breve período de tiempo, en función del seguimiento inerte del controlador. propio.
* **Alta precisión (riesgo de pérdida):** Cuando el usuario mueve el controlador de movimiento más allá del borde del campo de vista del casco, el casco pronto no podrá realizar un seguimiento visual de la posición del controlador. La aplicación sabe cuándo el controlador ha alcanzado este límite de hiperapartados; para ello, vea el **SourceLossRisk** Reach 1,0. En ese momento, la aplicación puede optar por pausar los gestos del controlador que requieren un flujo estable de planteamientos de alta calidad.
* **Precisión aproximada:** Cuando el controlador ha perdido el seguimiento visual durante el tiempo suficiente, las posiciones del controlador se quitarán de las posiciones de precisión aproximada. En este punto, el sistema bloqueará el controlador al usuario, realizará un seguimiento de la posición del usuario a medida que se mueven, mientras se expone la verdadera orientación del controlador mediante sus sensores de orientación internos. Muchas aplicaciones que usan Controladores para apuntar a los elementos de la interfaz de usuario y activarlos pueden funcionar de la manera normal, pero con una precisión aproximada sin que los usuarios lo noten. Las aplicaciones con requisitos de entrada más pesados pueden optar por detectar este descenso de **alta** precisión a una precisión **aproximada** mediante la inspección de la propiedad **PositionAccuracy** , por ejemplo, para proporcionar al usuario una hitbox más amplia en los destinos de la pantalla durante este tiempo.
* **Ninguna posición:** Aunque el controlador puede funcionar con una precisión aproximada durante mucho tiempo, a veces el sistema sabe que incluso una posición bloqueada por el cuerpo no es significativa en este momento. Por ejemplo, un controlador que se acaba de activar puede que nunca se haya observado visualmente, o que un usuario pueda poner un controlador que recoja otro usuario. En ese momento, el sistema no proporcionará ninguna posición a la aplicación y *TryGetPosition* devolverá FALSE.

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>API de Unity comunes (Input. GetButton/GetAxis)

**Espacio de nombres:** *UnityEngine*, *UnityEngine. XR*<br>
**Types**: *Input*, *XR. InputTracking*

Unity usa actualmente sus API de *entrada general. GetButton/Input. GetAxis* para exponer la entrada para [el SDK de Oculus](https://docs.unity3d.com/Manual/OculusControllers.html), [el SDK de OpenVR](https://docs.unity3d.com/Manual/OpenVRControllers.html) y Windows Mixed Reality, incluidas las manos y los controladores de movimiento. Si la aplicación usa estas API para la entrada, puede admitir fácilmente controladores de movimiento en varios SDK de XR, incluido Windows Mixed Reality.

### <a name="getting-a-logical-buttons-pressed-state"></a>Obtener el estado presionado de un botón lógico

Para usar las API de entrada de Unity generales, normalmente se empieza por conectar botones y ejes a nombres lógicos en el [Administrador de entrada de Unity](https://docs.unity3d.com/Manual/ConventionalGameInput.html), enlazando un botón o ID. de eje a cada nombre. Después, puede escribir código que haga referencia a ese botón o nombre de eje lógico.

Por ejemplo, para asignar el botón de desencadenador del controlador de movimiento izquierdo a la acción de envío, vaya a **editar > configuración del proyecto > entrada** en Unity y expanda las propiedades de la sección enviar en ejes. Cambie el botón **positivo** o la propiedad del **botón positivo alternativo** para leer el **botón 14 del joystick**, de la siguiente manera:

](images/unity-input-manager.png) InputManager de ![Unity<br>
*InputManager de Unity*

Después, el script puede comprobar la acción de envío mediante *Input. GetButton*:

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
Puede agregar más botones lógicos cambiando la propiedad **tamaño** en **ejes**.

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>Obtener el estado presionado del botón físico directamente

También puede tener acceso a los botones manualmente por su nombre completo, mediante *Input. GetKey*:

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>Obtención de un controlador de movimiento o mando a mano

Puede tener acceso a la posición y la rotación del controlador mediante *XR. InputTracking*:

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

Tenga en cuenta que esto representa la representación del puño del controlador (donde el usuario mantiene el controlador), lo que resulta útil para representar un arma o un cañón en la mano del usuario, o un modelo del propio controlador.

Tenga en cuenta que la relación entre esta postura de control y el representador de puntero (donde está señalando la punta del controlador) puede diferir entre los controladores. En este momento, el acceso a la pose de puntero del controlador solo es posible a través de la API de entrada específica de MR, que se describe en las secciones siguientes.

## <a name="windows-specific-apis-xrwsainput"></a>API específicas de Windows (XR. WSA. Entradas

**Espacio de nombres:** *UnityEngine. XR. WSA. Input*<br>
**Tipos**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*

Para obtener información más detallada sobre la entrada de mano de Windows Mixed Reality (para HoloLens) y los controladores de movimiento, puede optar por usar las API de entrada espacial específicas de Windows en el espacio de nombres *UnityEngine. XR. WSA. Input* . Esto le permite tener acceso a información adicional, como la precisión de la posición o el tipo de origen, lo que permite indicar a las manos y los controladores.

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>Sondeo del estado de los controladores de manos y de movimiento

Puede sondear el estado de este fotograma para cada origen de interacción (controlador de movimiento o mano) mediante el método *GetCurrentReading* .

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

Cada *InteractionSourceState* que recibe representa un origen de interacción en el momento actual. *InteractionSourceState* expone información como:
* Qué [tipos de pulsaciones](motion-controllers.md) se están produciendo (Select/menu/agarre/Touchpad/Stick)

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* Otros datos específicos de los controladores de movimiento, tales como las coordenadas XY y/o el estado de tocado del Stick.

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* InteractionSourceKind para saber si el origen es una mano o un controlador de movimiento

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>Sondeo de representación de representación de predicción de reenvío

* Cuando se realiza un sondeo de los datos de origen de interacción de las manos y los controladores, las supuestos que obtiene son supuestos predichos en el momento en que las fotos de este fotograma llegarán a los ojos del usuario.  Estas supuestos predichos se utilizan mejor para **representar** el controlador o un objeto mantenido en cada fotograma.  Si el destino es una determinada pulsación o versión con el controlador, será más preciso si usa las API de eventos históricos que se describen a continuación.

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* También puede obtener el representa el encabezado de predicción hacia delante para este marco actual.  Al igual que en el caso de la representación de origen, esto resulta útil para **representar** un cursor, aunque el destino de una determinada pulsación o versión será más preciso si usa las API de eventos históricos que se describen a continuación.

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a>Control de eventos de origen de interacción

Para controlar los eventos de entrada a medida que se producen con sus datos de pose históricos precisos, puede controlar los eventos de origen de interacción en lugar de realizar un sondeo.

Para controlar los eventos de origen de interacción:
* Regístrese para un evento de entrada *InteractionManager* . Para cada tipo de evento de interacción que le interese, necesita suscribirse a él.

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* Controle el evento. Una vez que se haya suscrito a un evento de interacción, recibirá la devolución de llamada cuando sea necesario. En el ejemplo *SourcePressed* , será una vez detectado el origen y antes de que se libere o se pierda.

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;
       
       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a>Cómo detener el control de un evento

Debe dejar de controlar un evento cuando ya no le interese en el evento o si está destruyendo el objeto que se ha suscrito al evento. Para dejar de controlar el evento, cancele la suscripción del evento.

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>Lista de eventos de origen de interacción

Los eventos de origen de interacción disponibles son:
* *InteractionSourceDetected* (el origen se activa)
* *InteractionSourceLost* (se convierte en inactivo)
* *InteractionSourcePressed* (TAP, presionar botón o "seleccionar")
* *InteractionSourceReleased* (final de una pulsación, botón liberado o final de "Select")
* *InteractionSourceUpdated* (se mueve o cambia cualquier estado)

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>Los eventos de destinatarios históricos suponen que coinciden con más precisión con una prensa o una versión

Las API de sondeo descritas anteriormente proporcionan a la aplicación las supuestos predecidas.  Aunque los planteamientos predichos son idóneos para representar el controlador o un objeto de dispositivo de mano virtual, los planteamientos futuros no son óptimos para el destino, por dos motivos clave:
* Cuando el usuario presiona un botón en un controlador, puede haber 20 ms de la latencia inalámbrica a través de Bluetooth antes de que el sistema reciba la prensa.
* A continuación, si usa una pose de predicción, se aplicarían otros 10 20 ms de predicción hacia delante para dirigirse a la hora en que las fotos del fotograma actual llegarán a los ojos del usuario.

Esto significa que el sondeo le proporciona una postura de origen o un representador de cabezales de 30 40 ms hacia delante desde donde se reenvían el encabezado del usuario y las manecillas al presionar o soltar.  Para la entrada de la mano de HoloLens, aunque no hay ningún retraso de la transmisión inalámbrica, hay un retraso de procesamiento similar para detectar la prensa.

Para establecer como destino con precisión en función de la intención original del usuario de una mano o de un controlador, debe usar la representación de origen histórica o la representación del encabezado de ese evento de entrada *InteractionSourcePressed* o *InteractionSourceReleased* .

Puede tener como destino una imprenta o una versión con datos de pose históricos del encabezado del usuario o del controlador:
* El encabezado se representa en el momento en que se produjo un gesto o un pulsador del controlador, que se puede usar para determinar el **destino** en el que se [Gazing](gaze-and-commit.md) el usuario:

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* La suposición de origen en el momento en que se produce una acción del controlador de movimiento, que se puede usar para determinar el **destino** del controlador.  Este será el estado del controlador que experimentó la pulsación.  Si está representando el propio controlador, puede solicitar la representación del puntero en lugar de la representación del control para captar el rayo de destino de lo que el usuario considerará la punta natural de ese controlador representado:

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a>Ejemplo de controladores de eventos

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is 
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point. 
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>API de gesto compuesto de alto nivel (GestureRecognizer)

**Espacio de nombres:** *UnityEngine. XR. WSA. Input*<br>
**Tipos**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*

La aplicación también puede reconocer gestos compuestos de nivel superior para orígenes de entrada espaciales, puntear, retener, manipular y gestos de navegación. Puede reconocer estos gestos compuestos a través de las [manos](gaze-and-commit.md#composite-gestures) y [los controladores de movimiento](motion-controllers.md) mediante GestureRecognizer.

Cada evento de gesto en el GestureRecognizer proporciona el SourceKind para la entrada, así como el rayo del cabezal de destino en el momento del evento. Algunos eventos proporcionan información adicional específica del contexto.

Solo se requieren algunos pasos para capturar gestos mediante un reconocedor de gestos:
1. Crear un nuevo reconocedor de gestos
2. Especificar los gestos que se van a inspeccionar
3. Suscripción a eventos para esos gestos
4. Iniciar la captura de gestos

### <a name="create-a-new-gesture-recognizer"></a>Crear un nuevo reconocedor de gestos

Para usar *GestureRecognizer*, debe haber creado un *GestureRecognizer*:

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>Especificar los gestos que se van a inspeccionar

Especifique qué gestos le interesan a través de *SetRecognizableGestures ()* :

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>Suscripción a eventos para esos gestos

Suscríbase a eventos de los gestos que le interesen.

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
>Los gestos de navegación y manipulación se excluyen mutuamente en una instancia de un *GestureRecognizer*.

### <a name="start-capturing-gestures"></a>Iniciar la captura de gestos

De forma predeterminada, un *GestureRecognizer* no supervisa la entrada hasta que se llama a *StartCapturingGestures ()* . Es posible que se genere un evento de gesto después de que se llame a *StopCapturingGestures ()* si la entrada se realizó antes que el marco en el que se procesó *StopCapturingGestures ()* . El *GestureRecognizer* recordará si está activado o desactivado durante el fotograma anterior en el que se ha producido realmente el gesto y, por tanto, es confiable iniciar y detener la supervisión de gestos según el destino de la mirada a este fotograma.

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>Detener captura de movimientos

Para detener el reconocimiento de gestos:

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>Quitar un reconocedor de gestos

Recuerde cancelar la suscripción a los eventos suscritos antes de destruir un objeto *GestureRecognizer* .

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>Representación del modelo de controlador de movimiento en Unity

![modelo de controlador de movimiento y teleportabilidad](images/motioncontrollertest-teleport-1000px.png)<br>
*Modelo de controlador de movimiento y teleportabilidad*

Para representar los controladores de movimiento en la aplicación que coincidan con las controladoras físicas que están manteniendo los usuarios y articular a medida que se presionan varios botones, puede usar **MotionController recurso prefabricado** en el [Kit de herramientas de realidad mixta](https://github.com/Microsoft/MixedRealityToolkit-Unity/).  Este recurso prefabricado carga dinámicamente el modelo de glTF correcto en tiempo de ejecución desde el controlador de controlador de movimiento instalado del sistema.  Es importante cargar estos modelos dinámicamente en lugar de importarlos manualmente en el editor, de modo que la aplicación muestre modelos 3D físicamente precisos para cualquier controlador actual y futuro que puedan tener los usuarios.

1. Siga las instrucciones [Introducción](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) para descargar el kit de herramientas de realidad mixta y agréguelo al proyecto de Unity.
2. Si ha reemplazado la cámara con el recurso prefabricado de *MixedRealityCameraParent* como parte de los pasos introducción, está listo para empezar.  Ese recurso prefabricado incluye la representación del controlador de movimiento.  En caso contrario, agregue *assets/HoloToolkit/INPUT/Prefabs/MotionControllers. recurso prefabricado* a la escena desde el panel Proyecto.  Querrá agregar ese recurso prefabricado como elemento secundario del objeto primario que usa para mover la cámara cuando el usuario teletransporta dentro de la escena, de modo que los controladores entren junto con el usuario.  Si la aplicación no implica teleportabilidad, solo tiene que agregar el recurso prefabricado en la raíz de la escena.

## <a name="throwing-objects"></a>Producir objetos

La generación de objetos en realidad es un problema más difícil, por lo que puede parecer al principio. Al igual que con la mayoría de las interacciones basadas físicamente, al iniciar el juego funciona de forma inesperada, es evidente de inmediato e interrumpe la inmersión. Hemos dedicado mucho tiempo a pensar en el modo de representar un comportamiento de lanzamiento que se ha corregido físicamente y han llegado unas cuantas instrucciones, habilitadas a través de las actualizaciones de nuestra plataforma, que nos gustaría compartir con usted.

Puede encontrar un ejemplo de cómo se recomienda implementar el lanzamiento [aquí](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage). Este ejemplo sigue estas cuatro instrucciones:
* **Use la *velocidad* del controlador en lugar de la posición**. En la actualización de noviembre de Windows, se presentó un cambio de comportamiento en el [Estado de seguimiento posicional ' ' aproximado](motion-controllers.md#controller-tracking-state)' '. Cuando se encuentra en este estado, se seguirá informando de la información de velocidad de la controladora mientras creemos que es de alta precisión, lo que suele ser más largo que la posición.
* **Incorpore la *velocidad angular* del controlador**. Esta lógica está contenida en el archivo `throwing.cs` en el `GetThrownObjectVelAngVel` método estático, dentro del paquete vinculado anteriormente:
   1. A medida que se conserva la velocidad angular, el objeto iniciado debe mantener la misma velocidad angular que tenía en el momento de la iniciación: `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. Dado que es probable que el centro de la masa del objeto iniciado no sea el origen de la representación del puño, es probable que tenga una velocidad diferente a la del controlador en el marco de referencia del usuario. La parte de la velocidad del objeto aportada de esta manera es la velocidad tangencial instantánea del centro de la masa del objeto producido en torno al origen del controlador. Esta velocidad tangencial es el producto cruzado de la velocidad angular del controlador con el vector que representa la distancia entre el origen del controlador y el centro de la masa del objeto iniciado.
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. La velocidad total del objeto generado es, por lo tanto, la suma de la velocidad del controlador y esta velocidad tangencial: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **Preste mucha atención a la *hora* a la que se aplica la velocidad**. Cuando se presiona un botón, puede tardar hasta 20 ms para ese evento a pasar a través de Bluetooth al sistema operativo. Esto significa que, si sondea un cambio de estado del controlador de presionado a no presionado, o viceversa, el controlador de la información de la que se obtiene se obtiene en realidad de este cambio en el estado. Además, la causa del controlador presentada por nuestra API de sondeo se prevé para reflejar una posible suposición en el momento en que se muestra el fotograma, lo que podría ser más 20 MS en el futuro. Esto es adecuado para la *representación* de objetos retenidos, pero proporciona un problema de tiempo para el *objetivo* del objeto a medida que calculamos la trayectoria en el momento en que el usuario lanzó su lanzamiento. Afortunadamente, con la actualización de noviembre, cuando se envía un evento de Unity, como *InteractionSourcePressed* o *InteractionSourceReleased* , el estado incluye los datos del representador histórico cuando el botón se ha presionado o liberado realmente.  Para obtener la representación del controlador y el destino del controlador más precisos durante las throws, debe usar correctamente el sondeo y los eventos, según corresponda:
   * Para que el **controlador presente** cada fotograma, la aplicación debe colocar el *GameObject* del controlador en la representación del controlador de predicción para la hora de Photon del marco actual.  Estos datos se obtienen de las API de sondeo de Unity como *[XR. InputTracking. GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* o *[XR. WSA. Input. InteractionManager. GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)* .
   * En el caso de que el **controlador se dirija** a una imprenta o una versión, la aplicación debe Raycast y calcular las trayectorias en función de la suposición del controlador histórico para ese evento Press o Release.  Estos datos se obtienen de las API de eventos de Unity, como *[InteractionManager. InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* .
* **Utilice la postura de control**. La velocidad y la velocidad de angular se registran en relación con la pose de control, no con la función de puntero.

El lanzamiento continuará mejorando con futuras actualizaciones de Windows y puede esperar encontrar más información aquí.

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a>Gestos y controladores de movimiento en MRTK V2

Puede tener acceso al gesto y al controlador de movimiento desde el administrador de entrada. 
* [Gesto en MRTK V2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [Controlador de movimiento en MRTK V2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a>Siga los tutoriales.

Los tutoriales paso a paso, con ejemplos de personalización más detallados, están disponibles en la Academia de realidad mixta:

- [Entrada MR 211: gesto](holograms-211.md)
- [Entrada MR 213: Controladores de movimiento](mixed-reality-213.md)

[Entrada MR ![213-controlador de movimiento](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)<br>
*Entrada MR 213-controlador de movimiento*

## <a name="see-also"></a>Consulte también

* [Mirada-cabeza y confirmación](gaze-and-commit.md)
* [Controladores de movimiento](motion-controllers.md)


