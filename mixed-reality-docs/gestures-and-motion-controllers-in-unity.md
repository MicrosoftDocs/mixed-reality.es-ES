---
title: Los gestos y controladores de movimiento en Unity
description: Hay dos formas de realizar acciones en su mirada en Unity, gestos de mano y los controladores de movimiento.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: los gestos, los controladores de movimiento, unity, mirada, de entrada
ms.openlocfilehash: d98590f9a6c40336a13cb75e8050e13edfaa2a6c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597657"
---
# <a name="gestures-and-motion-controllers-in-unity"></a>Los gestos y controladores de movimiento en Unity

Hay dos formas de realizar acciones en su [que mirar en Unity](gaze-in-unity.md), [gestos de mano](gestures.md) y [motion controladores](motion-controllers.md). Tener acceso a los datos de ambos orígenes de entrada espacial a través de las mismas API de Unity.

Unity proporciona dos métodos principales para tener acceso a los datos espaciales de entrada para Windows Mixed Reality, común *Input.GetButton/Input.GetAxis* API que funcionan a través de varios SDK XR de Unity, y un *InteractionManager / GestureRecognizer* API específica de Windows Mixed Reality que expone el conjunto completo de datos espaciales de entrada disponibles.

## <a name="unity-buttonaxis-mapping-table"></a>Tabla de asignación de botón o eje de Unity

Los identificadores de botón y de los ejes en la tabla siguiente se admiten en Administrador de entradas de Unity para los controladores de Windows Mixed Reality movimiento a través de la *Input.GetButton/GetAxis* API, mientras que la columna de "MR Windows específicos" hace referencia a propiedades disponible fuera de la *InteractionSourceState* tipo. Cada una de estas API se describen en detalle en las secciones siguientes.

Las asignaciones de identificador de botón o eje para Windows Mixed Reality coinciden con el botón Oculus/eje identificadores.

Las asignaciones de identificador de botón o eje para Windows Mixed Reality se diferencian de las asignaciones de OpenVR de dos maneras:
1. La asignación usa identificadores de panel táctil que son distintos de tecla de navegación, para admitir controladores con sticks analógicos y touchpads.
2. La asignación evita sobrecargar los identificadores para los botones de menú, dejarlos disponibles para los botones ABXY físicos de botón A y X.

<table>
<tr>
<th rowspan="2">Entrada </th><th colspan="2"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">API de Unity comunes</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2"><a href="gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xr.wsa.input">API de entrada específica de Windows MR</a><br />(XR.WSA.Input)</th>
</tr><tr>
<th> Parte izquierda </th><th> Mano derecha</th>
</tr><tr>
<td> Selección del desencadenador presionado </td><td> 9 = 1.0 de eje </td><td> Eje 10 = 1.0 </td><td> selectPressed</td>
</tr><tr>
<td> Seleccionar valor analógico de desencadenador </td><td> Eje 9 </td><td> Eje 10 </td><td> selectPressedAmount</td>
</tr><tr>
<td> Selección del desencadenador parcialmente presionado </td><td> Botón 14 <i>(compatibilidad de controlador para juegos)</i> </td><td> Botón 15 <i>(compatibilidad de controlador para juegos)</i> </td><td> selectPressedAmount &gt; 0.0</td>
</tr><tr>
<td> Botón de menú presionado </td><td> Botón 6 * </td><td> Botón 7 * </td><td> menuPressed</td>
</tr><tr>
<td> Botón de control presionado </td><td> Eje 11 = 1.0 (sin valores analógicos)<br />Botón 4 <i>(compatibilidad de controlador para juegos)</i> </td><td> Eje 12 = 1.0 (sin valores analógicos)<br />Botón 5 <i>(compatibilidad de controlador para juegos)</i> </td><td> entendido todo</td>
</tr><tr>
<td> Tecla de navegación X <i>(izquierdo: -1,0, correcto: 1.0)</i> </td><td> Eje 1 </td><td> Eje 4 </td><td> thumbstickPosition.x</td>
</tr><tr>
<td> Tecla de navegación Y <i>(parte superior: de -1,0, inferior: 1.0)</i> </td><td> Eje 2 </td><td> Eje 5 </td><td> thumbstickPosition.y</td>
</tr><tr>
<td> Presiona la tecla de navegación </td><td> Botón 8 </td><td> Botón 9 </td><td> thumbstickPressed</td>
</tr><tr>
<td> Panel táctil X <i>(izquierdo: -1,0, correcto: 1.0)</i> </td><td> Axis 17* </td><td> Axis 19* </td><td> touchpadPosition.x</td>
</tr><tr>
<td> Panel táctil Y <i>(parte superior: de -1,0, inferior: 1.0)</i> </td><td> Axis 18* </td><td> Eje 20 * </td><td> touchpadPosition.y</td>
</tr><tr>
<td> Panel táctil tocada </td><td> Botón 18 * </td><td> Botón 19 * </td><td> touchpadTouched</td>
</tr><tr>
<td> Panel táctil presionada </td><td> Botón 16 * </td><td> Botón 17 * </td><td> touchpadPressed</td>
</tr><tr>
<td> 6GDL postura de control o la postura de puntero </td><td colspan="2"> <i>Control</i> suponer solo: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></td><td> Pasar <i>control</i> o <i>puntero</i> como argumento: sourceState.sourcePose.TryGetPosition<br />sourceState.sourcePose.TryGetRotation<br /></td>
</tr><tr>
<td> Estado de seguimiento </td><td colspan="2"> <i>Posición precisión y el origen de riesgo de pérdida solo está disponible a través de API específica MR</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>Estos identificadores de botón o eje difieren de los identificadores que usa Unity para OpenVR debido a conflictos en las asignaciones de la configuración de los controles, Oculus táctil y OpenVR.

## <a name="grip-pose-vs-pointing-pose"></a>Postura de control frente a la postura señalador

Windows Mixed Reality es compatible con controladores de movimiento en una variedad de factores de forma, con el diseño de cada controlador que se diferencia en su relación entre la posición del usuario mano y natural "Reenviar" dirección de que las aplicaciones debe utilizar para que apunte al representar el controlador.

Para representar mejor estos controladores, hay dos tipos de plantea puede investigar para cada origen de interacción, el **control postura** y el **puntero postura**. Tanto el control postura y puntero postura las coordenadas se expresan por todas las API de Unity en coordenadas globales de mundo de Unity.

### <a name="grip-pose"></a>Postura de control

El **control postura** representa la ubicación de la palma de una mano detectada por un HoloLens, o bien la palma que contiene un controlador de movimiento.

En inmersivos, la postura de control se utiliza mejor para representar **la mano del usuario** o **mantiene un objeto en la mano del usuario**, como una Espada o filo. La postura de control también se utiliza al visualizar un controlador de movimiento, como el **modelo representable** proporcionados por Windows para un movimiento controlador utiliza la postura de control como su origen y el centro de rotación.

La postura de control se define específicamente como sigue:
* El **sujete posición**: El centroide de palm cuando se mantiene el controlador de forma natural, ajustar izquierda o derecha para centrar la posición dentro del control. En el controlador de movimiento Windows Mixed Reality, esta posición generalmente se alinea con el botón de entender.
* El **sujete eje derecho de orientación**: Cuando se abre completamente la mano para formar una postura plano 5-dedo, el rayo que es normal que la palma (hacia delante desde la palma de izquierdo, con versiones anteriores desde la palma derecha)
* El **sujete eje hacia delante de orientación**: Cuando cierre la mano parcialmente (como si mantiene el controlador), el rayo que señala "forward" a través del tubo formado por los dedos no thumb.
* El **sujete orientación de eje**: El eje vertical implicado en las definiciones de la derecha y hacia delante.

Puede tener acceso a la postura de control a través de la API de entrada de cualquier Unity entre proveedores (*[XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation*) o a través de la API de Windows MR específicos (*sourceState.sourcePose.TryGetPosition/Rotation*, solicitando suponen datos para el **control** nodo).

### <a name="pointer-pose"></a>Postura de puntero

El **puntero postura** representa la punta del controlador que señala hacia delante.

La postura de puntero proporcionado por el sistema se utiliza mejor para raycast cuando esté **el propio modelo de controlador de representación**. Si está representando algún otro objeto virtual en lugar del controlador, como un cañón virtual, debe señalar con un radio que es más natural para ese objeto virtual, como un radio que recorre el Cañón del modelo filo definido por la aplicación. Dado que los usuarios pueden ver el objeto virtual y no en el controlador físico, que apunta con el objeto virtual probablemente será más natural para aquellos que usen la aplicación.

Actualmente, está disponible en Unity solo a través de la API de Windows MR específica, la postura de puntero *sourceState.sourcePose.TryGetPosition/Rotation*, pasando *InteractionSourceNode.Pointer* como la argumento.

## <a name="controller-tracking-state"></a>Estado del controlador de seguimiento

Al igual que los auriculares, el controlador de movimiento de Windows Mixed Reality no requiere ninguna configuración de los sensores de seguimiento externas. En su lugar, se realiza un seguimiento de los controladores de sensores en los auriculares en sí mismo.

Si el usuario mueve los controladores de campo de la vista de los auriculares, en la mayoría de los casos Windows seguirá deducir las posiciones de controlador y le proporciona a la aplicación. Cuando el controlador ha perdido un seguimiento visual de tiempo suficiente, se quitarán las posiciones del controlador a las posiciones de precisión aproximado.

En este momento, el sistema las eliminará bloqueo del cuerpo del controlador para el usuario, la posición del usuario de seguimiento a medida que se mueven, mientras se sigue manteniendo la orientación del controlador de true mediante sus sensores de orientación interna. Muchas aplicaciones que usen controladores para apuntar al y activar los elementos de interfaz de usuario pueden funcionar normalmente aunque aproximado con una precisión de sin que el usuario lo advierta.

La mejor forma de hacerse una idea de esto es probarlo usted mismo. Vea este vídeo con ejemplos de contenido envolvente que funciona con los controladores de movimiento a través de varios Estados de seguimiento:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a>Seguimiento del estado de forma explícita el razonamiento

Es posible que vaya más allá e inspeccionar las propiedades en el estado del controlador, como las aplicaciones que desea tratar las posiciones de manera diferente en función de seguimiento del estado de *SourceLossRisk* y *PositionAccuracy*:

<table>
<tr>
<th> Estado de seguimiento </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>Alta precisión</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Alta precisión (corre el riesgo de perder)</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Precisión aproximado</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Aproximado </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Ninguna posición</b> </td><td style="background-color: orange"> == 1.0 </td><td style="background-color: orange"> Aproximado </td><td style="background-color: orange"> falso</td>
</tr>
</table>

Estos Estados de seguimiento del controlador de movimiento se definen como sigue:
* **Alta precisión:** Mientras el controlador de movimiento está dentro de campo de la vista de los auriculares, generalmente entregará las posiciones de alta precisión, en función de seguimiento visual. Tenga en cuenta que un controlador de movimiento que momentáneamente deja el campo de visión o se oculta temporalmente de los sensores de auriculares (por ejemplo, por otro lado del usuario) continuará devolviendo plantea de alta precisión durante un breve período, en función de seguimiento inercial del controlador Sí.
* **Alta precisión (corre el riesgo de perder):** Cuando el usuario mueve el controlador de movimiento más allá del borde de campo de la vista de los auriculares, los auriculares pronto podrá realizar un seguimiento visual de la posición del dispositivo. La aplicación conoce cuando el controlador ha alcanzado este límite FOV viendo el **SourceLossRisk** llegar a 1.0. En ese momento, la aplicación puede optar por pausar los gestos de controlador que requieren un flujo constante de plantea muy alta calidad.
* **Precisión aproximado:** Cuando el controlador ha perdido un seguimiento visual de tiempo suficiente, se quitarán las posiciones del controlador a las posiciones de precisión aproximado. En este momento, el sistema las eliminará bloqueo del cuerpo del controlador para el usuario, la posición del usuario de seguimiento a medida que se mueven, mientras se sigue manteniendo la orientación del controlador de true mediante sus sensores de orientación interna. Muchas aplicaciones que usen controladores para apuntar al y activar los elementos de interfaz de usuario pueden funcionar como while normal con una precisión aproximada de sin que el usuario lo advierta. Pueden elegir sentido esta lista de aplicaciones con requisitos de entrada más **alta** precisión a **aproximado** precisión inspeccionando el **PositionAccuracy** propiedad, para ejemplo para otorgar al usuario un hitbox más generosa en destinos fuera de la pantalla durante este tiempo.
* **Ninguna posición:** Mientras que el controlador puede operar en una precisión aproximada durante mucho tiempo, en ocasiones, el sistema sepa que incluso una posición bloqueada de cuerpo no es significativa en este momento. Por ejemplo, un controlador que ha estado encendido solo es posible que nunca se han observado visualmente, o un usuario puede dejar un controlador que, a continuación, se recoge por otra persona. En esos momentos, el sistema no proporcionará cualquier posición a la aplicación, y *TryGetPosition* devolverá false.

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>API de Unity comunes (Input.GetButton/GetAxis)

**Namespace:** *UnityEngine*, *UnityEngine.XR*<br>
**Tipos**: *Input*, *XR.InputTracking*

Unity usa actualmente su general *Input.GetButton/Input.GetAxis* API para exponer la entrada [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) y Windows Mixed Reality, incluidos las manos y los controladores de movimiento. Si su aplicación usa estas API para la entrada, puede admitir fácilmente controladores de movimiento a través de varios SDK XR, incluidos Windows Mixed Reality.

### <a name="getting-a-logical-buttons-pressed-state"></a>Al obtener el estado presionado de un botón lógico

Para usar la entrada de Unity general API, normalmente empezará por inserción de botones y los ejes a los nombres lógicos en el [Unity entrada Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), enlace un botón o eje identificadores a cada nombre. A continuación, puede escribir código que hace referencia a dicho nombre lógico de botón o eje.

Por ejemplo, para asignar el botón de desencadenador del controlador de movimiento izquierdo a la acción de envío, vaya a **Editar > configuración del proyecto > entrada** dentro de Unity y expanda las propiedades de la sección de envío en los ejes. Cambiar el **botón positivo** o **Alt positivo botón** propiedad que se va a leer **botón joystick 14**, similar al siguiente:

![InputManager de Unity](images/unity-input-manager.png)<br>
*Unity InputManager*

A continuación, puede comprobar el script para la acción de envío mediante *Input.GetButton*:

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
Puede agregar botones más lógicos cambiando el **tamaño** propiedad bajo **ejes**.

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>Obtener estado presionado de un botón físico directamente

También puede acceder botones por su nombre completo nombre, con *Input.GetKey*:

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>Obtener una mano o postura del controlador de movimiento

Puede tener acceso a la posición y rotación del controlador, mediante *XR. InputTracking*:

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

Tenga en cuenta que esto representa la postura de control del controlador (donde el usuario mantiene el controlador), lo que resulta útil para representar una Espada o presión en la mano del usuario o un modelo de la propia controladora.

Tenga en cuenta que puede diferir la relación entre la postura de este control y la postura de puntero (donde está señalando a la punta del controlador) en todos los controladores. En este momento, tener acceso a la postura del puntero del controlador sólo es posible a través de la entrada MR específica API que se describe en las secciones siguientes.

## <a name="windows-specific-apis-xrwsainput"></a>API específicas de Windows (XR. WSA. Entrada)

**Namespace:** *UnityEngine.XR.WSA.Input*<br>
**Tipos**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*

Para obtener información más detallada acerca de la entrada de la mano de Windows Mixed Reality (para HoloLens) y los controladores de movimiento, puede elegir usar las API de entrada espacial específicas de Windows bajo la *UnityEngine.XR.WSA.Input* espacio de nombres. Esto le permite tener acceso a información adicional, como la precisión de la posición o el tipo de origen, lo que le permite indicar a las manos y los controladores de distancia.

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>Sondear el estado de las manos y los controladores de movimiento

Se puede sondear para el estado de este fotograma para cada origen (controlador de mano o movimiento) de interacción con el *GetCurrentReading* método.

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

Cada *InteractionSourceState* obtendrá back representa un origen de interacción en el momento actual. El *InteractionSourceState* expone información como:
* Que [tipos de pulsaciones](motion-controllers.md) se producen (Select/menú/comprensión o panel táctil o tecla de navegación)

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* Otros datos específicos de los controladores de movimiento, tales el panel táctil o de tecla de navegación coordenadas XY y estado modificada

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```
   
* El InteractionSourceKind saber si el origen es una mano o un controlador de movimiento

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>Sondear plantea representación predicho de avance

* Al sondear en busca de datos de origen de la interacción de las manos y los controladores, la puede causar que obtendrá es plantea predicho de avance por el momento en el tiempo cuando photons de este fotograma llegarán a la vista del usuario.  Estos plantea predicho de avance resultan especialmente útiles para **representación** el controlador o un retenidos objeto cada fotograma.  Si están destinadas a la acción de presionar una determinada o versión con el controlador, que será más precisos, si usa el evento histórico API descritas a continuación.

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* También puede obtener la postura principal predicho de avance para este marco actual.  Igual que con la postura de origen, esto es útil para **representación** un cursor, aunque destinado a un determinado presione o versión serán más preciso, si usa el evento histórico API descritas a continuación.

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a>Control de eventos del origen de interacción

Para controlar los eventos de entrada cuando se produzcan con sus datos precisos postura históricos, puede controlar eventos del origen de interacción en lugar de sondeo.

Para controlar los eventos de origen de interacción:
* Registrarse para una *InteractionManager* evento de entrada. Para cada tipo de evento de interacción que le interesen, deberá suscribirse a él.

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```
   
* Controle el evento. Una vez que se ha suscrito a un evento de interacción, obtendrá la devolución de llamada cuando corresponda. En el *SourcePressed* ejemplo, se trata de una vez se ha detectado el origen y antes de que se publicó o se pierde.

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

### <a name="how-to-stop-handling-an-event"></a>Cómo detener un evento de control

Debe dejar de controlar un evento cuando ya no está interesado en el evento o se destruya el objeto que se ha suscrito al evento. Para dejar de controlar el evento, anular la suscripción del evento.

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>Lista de eventos del origen de interacción

Los eventos de origen de la interacción disponible son:
* *InteractionSourceDetected* (origen se convierte en activado)
* *InteractionSourceLost* (pasa a estar inactiva)
* *InteractionSourcePressed* (tap, presionar el botón o "Select" dijeron)
* *InteractionSourceReleased* (final de una derivación, el botón o al final de "Select" dijeron)
* *InteractionSourceUpdated* (mueva o cambie algún estado de lo contrario)

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>Eventos para histórico plantea destinatarios que coinciden con la máxima precisión con una presione o versión

Las API de sondeos que se ha descrito anteriormente, asigne a la aplicación puede causar predicho de avance.  Mientras esos plantea predicho es más adecuada para representar un objeto de dispositivo de mano virtual o el controlador, puede causar futuras no es óptimas para destinatarios por dos razones fundamentales:
* Cuando el usuario presiona un botón en un controlador, puede haber unos 20 ms de latencia inalámbrica a través de Bluetooth antes de que el sistema reciba la prensa.
* A continuación, si está utilizando una postura predicho de avance, existe son aplicables para el tiempo cuando photons del fotograma actual llegará a la vista del usuario de destino otro 10-20ms de predicción hacia delante.

Esto significa que sondeo le ofrece una postura de origen o head suponer que es el 30-40 MS hacia delante desde donde principal y las manos del usuario realmente atrás cuando estaban ha ocurrido la prensa o versión.  Para la entrada de la mano de HoloLens, aunque no hay ningún retraso transmisiones inalámbricas, hay un retraso de procesamiento similares para detectar la prensa.

Identificar con precisión según la intención del usuario original pulsación de una mano o el controlador, debe usar la postura de origen históricos o postura principal desde que *InteractionSourcePressed* o *InteractionSourceReleased* evento de entrada.

Puede tener como destino un presione o liberar con datos históricos postura de head del usuario o su controlador de:
* Se ha producido la postura principal en el momento cuando se presiona un gesto o un controlador, que puede utilizarse para **destinadas a** para determinar cuál fue el usuario [gazing](gaze.md) en:

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

* Se ha producido la postura de origen en el momento cuando se presiona un controlador de movimiento, que puede utilizarse para **destinatarios** para determinar lo que el usuario señalando el controlador en.  Este será el estado del controlador que experimentó la prensa.  Si está representando el propio controlador, puede solicitar la postura de puntero, en lugar de la postura de control, debe grabar el rayo destinatarios de lo que el usuario tendrá en cuenta la punta natural del que representa el controlador:

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

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>Gesto de compuesto de alto nivel API (GestureRecognizer)

**Namespace:** *UnityEngine.XR.WSA.Input*<br>
**Tipos**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*

La aplicación también puede reconocer gestos compuestos de mayor nivel para los gestos de suspensión, la manipulación y la navegación espacial de orígenes de entrada, Tap. Puede reconocer estos gestos compuestos entre ambos [manos](gestures.md) y [controladores de movimiento](motion-controllers.md) utilizando el GestureRecognizer.

Cada evento de gestos en el GestureRecognizer proporciona el SourceKind para la entrada, así como el rayo principal destinatarios en el momento del evento. Algunos eventos proporcionan información específica de contexto adicional.

Hay solo unos pasos necesarios para capturar los gestos de un reconocedor de gestos:
1. Crear un nuevo reconocedor de gestos
2. Especifique qué gestos para inspeccionar
3. Suscripción a eventos de los gestos
4. Iniciar la captura de gestos

### <a name="create-a-new-gesture-recognizer"></a>Crear un nuevo reconocedor de gestos

Para usar el *GestureRecognizer*, debe haber creado un *GestureRecognizer*:

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>Especifique qué gestos para inspeccionar

Especifique qué gestos que esté interesado a través de *SetRecognizableGestures()*:

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>Suscripción a eventos de los gestos

Suscribirse a eventos para los gestos que esté interesado.

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
>Los gestos de navegación y manipulación son mutuamente excluyentes en una instancia de un *GestureRecognizer*.

### <a name="start-capturing-gestures"></a>Iniciar la captura de gestos

De forma predeterminada, un *GestureRecognizer* no supervisa entrada hasta *StartCapturingGestures()* se llama. Es posible que se puede generar un evento de gesto después *StopCapturingGestures()* se llama si la entrada se realizó antes del fotograma donde *StopCapturingGestures()* se procesó. El *GestureRecognizer* recordarán si fue activado o desactivado durante el fotograma anterior en el que el gesto producido realmente y por lo que es confiable para iniciar y Detener supervisión de gesto según mirada de este marco destino.

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>Detener la captura de gestos

Para detener el reconocimiento de gestos:

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>Quitar un reconocedor de movimiento

Recuerde que debe cancelar la suscripción a eventos suscritos antes de destruir un *GestureRecognizer* objeto.

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

![Teleportation y el modelo de controlador de movimiento](images/motioncontrollertest-teleport-1000px.png)<br>
*Teleportation y el modelo de controlador de movimiento*

Para representar los controladores de movimiento en la aplicación que coinciden con los controladores de físicos a los usuarios mantienen y explicar como se presionan los botones distintos, puede usar el **MotionController prefabricado** en el [Kit de herramientas de realidad mixta ](https://github.com/Microsoft/MixedRealityToolkit-Unity/).  Este recurso prefabricado carga dinámicamente el modelo glTF correcto en tiempo de ejecución desde el controlador del controlador de movimiento instalados del sistema.  Es importante cargar estos modelos de forma dinámica en lugar de importarlos de forma manual en el editor, para que la aplicación mostrará modelos 3D físicamente precisos para los controladores actuales y futuros de los usuarios pueden tener.

1. Siga el [Introducción](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instrucciones para descargar el Kit de herramientas de realidad mixta y agregarlo a su proyecto de Unity.
2. Si reemplaza la cámara con la *MixedRealityCameraParent* prefabricado como parte de los pasos de introducción, estará listo para continuar.  Ese recurso prefabricado incluye representación de controlador de movimiento.  De lo contrario, agregue *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* en su escena en el panel de proyecto.  Desea agregar que prefabricado como elemento secundario de cualquier objeto primario se usa para mover la cámara en torno a cuando la teleports usuario dentro de la escena, para que los controladores vienen junto con el usuario.  Si la aplicación no implica teleporting, simplemente agregue el prefabricado verá en la raíz de la escena.

## <a name="throwing-objects"></a>Producir objetos

A continuación, generar objetos en realidad virtual es un problema más difícil al principio pareciera. Al igual que con interacciones más físicamente en función, cuando se lanza en juego actúa de forma inesperada, es evidente de inmediato e inmersión se interrumpe. Hemos pasado algún tiempo a pensar en profundidad acerca de cómo representan un comportamiento produce físicamente correcto y han inventado algunas instrucciones, habilitadas a través de las actualizaciones de nuestra plataforma, que nos gustaría compartir con usted.

Puede encontrar un ejemplo de cómo se recomienda implementar producir [aquí](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage). Este ejemplo sigue estas cuatro directrices:
* **Usar el controlador *velocity* en lugar de posición**. En la actualización de noviembre de Windows, se introdujo un cambio de comportamiento cuando se encuentra en la ['' aproximado '' estado de seguimiento posicionales](motion-controllers.md#controller-tracking-state). En este estado, información de progreso sobre el controlador seguirá notificará siempre que creemos que es de alta precisión, que a menudo es más larga de posición permanece alta precisión.
* **Incorporar la *velocidad angular* del controlador de**. Esta lógica se incluye en el `throwing.cs` de archivos en el `GetThrownObjectVelAngVel` métodos estáticos, dentro del paquete vinculado anteriormente:
   1. Como se conserva la velocidad angular, el objeto iniciado debe mantener la misma velocidad angular que tenía en el momento del lanzamiento: `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. Como es probable no en el origen de la postura de control, es probable que tenga una velocidad diferente, a continuación, el controlador de en el marco de referencia del usuario del centro de masa del objeto iniciado. La parte de la velocidad del objeto que aporta de esta manera es el progreso tangencial instantáneo del centro de masa del objeto se produce en torno al origen de controlador. Esta velocidad tangencial: es el producto cruzado de la velocidad angular del controlador con el vector que representa la distancia entre el origen del controlador y del centro de masa del objeto iniciado.
    
      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```
   
   3. La velocidad total del objeto se produce, por tanto, es la suma de la velocidad del controlador y este progreso tangencial: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **Preste mucha atención a la *tiempo* en el que se aplique la velocidad**. Cuando se presiona un botón, se pueden tardar hasta 20 ms para ese evento se propagan a través de Bluetooth en el sistema operativo. Esto significa que si el sondeo para un cambio de estado del controlador de presionado para no presionado o viceversa, será realmente la información de la postura de controlador que obtiene con él por delante de este cambio de estado. Además, la postura de controlador presentada por nuestra API de sondeo al día se prevé para reflejar una postura es probable que en el momento que se mostrará el marco que podría ser más de 20 ms, a continuación, en el futuro. Esto es bueno para *representación* mantiene los objetos, pero nuestro problema de tiempo para los compuestos *destinatarios* el objeto calculamos la trayectoria para el momento en que el usuario libera su throw. Afortunadamente, con la actualización de noviembre, cuando un evento de Unity como *InteractionSourcePressed* o *InteractionSourceReleased* se envía el estado incluye los datos históricos postura desde nuevo cuando el botón era realmente presionado o publicadas.  Para obtener la representación más precisa de controlador y el controlador destinatarios durante produce, debe usar correctamente sondeo y eventos, según corresponda:
   * Para **representación controlador** cada fotograma, la aplicación debe colocar el controlador *GameObject* en el controlador predicho de avance suponer tiempo de photon del marco actual.  Obtener estos datos desde Unity, como las API de sondeos *[XR. InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* o  *[XR. WSA. Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.
   * Para **controlador destinatarios** tras un presione o versión, la aplicación debe raycast y calcular las trayectorias en función de la postura de controlador históricos para ese evento presione o versión.  Extraer estos datos de eventos de Unity API, como  *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.
* **Utilice la postura de control**. Velocidad angular y la velocidad se notifican en relación con la postura de control, no un puntero postura.

Iniciando seguirá aumentando con futuras actualizaciones de Windows y se puede esperar encontrar más información al respecto aquí.

## <a name="accelerate-development-with-mixed-reality-toolkit"></a>Acelere el desarrollo con el Kit de herramientas de realidad mixta

Hay dos escenas de ejemplo sobre InputManager y MotionController en Unity. A través de estos escenas, pueden aprender cómo usar InputManager del MRTK y tener acceso a datos controlan los eventos de los botones del controlador de movimiento.

- [HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/InputManagerTest.unity)
- [HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/MotionControllerTest.unity)
- [Archivo Léame de los detalles técnicos](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input)

![Segundo plano de ejemplo de entrada en MRTK](images/MRTK_ExampleScene_Input.png)<br>
*Segundo plano de ejemplo de entrada en MRTK*

### <a name="automatic-scene-setup"></a>Programa de instalación automática de escenas

Al importar [MRTK publicar paquetes de Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases) o clonar el proyecto desde el [repositorio de GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity), va a buscar un nuevo menú 'Kit de herramientas de realidad mixta' en Unity. En el menú "Configurar", verá el menú 'Aplicar configuración de escena de Mixed Reality'. Al hacer clic en él, quita la cámara de forma predeterminada y agrega los componentes básicos - [InputManager](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/InputManager.prefab), [MixedRealityCameraParent](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/MixedRealityCameraParent.prefab), y [DefaultCursor](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Prefabs/Cursor/DefaultCursor.prefab).

![Menú MRTK para la instalación de la escena](images/MRTK_Input_Menu.png)<br>
*Menú MRTK para la instalación de la escena*

![Programa de instalación automática de escenas en MRTK](images/MRTK_HowTo_Input1.png)<br>
*Programa de instalación automática de escenas en MRTK*

### <a name="mixedrealitycamera-prefab"></a>MixedRealityCamera prefabricado

Puede agregar también manualmente desde el panel de proyecto. Puede encontrar estos componentes como prefabricados. Al buscar **MixedRealityCamera**, podrá ver dos prefabricados cámara diferente. La diferencia es que **MixedRealityCamera** es la cámara solo prefabricado, mientras que **MixedRealityCameraParent** incluye componentes adicionales para el inmersivos como Teleportation, movimiento Controlador y límites.

![Cámara prefabricados en MRTK](images/MRTK_HowTo_Input2.png)<br>
*Cámara prefabricados en MRTK*

**MixedRealtyCamera** admite HoloLens y auriculares envolventes. Detecta el tipo de dispositivo y optimiza las propiedades como borrar las marcas y Skybox. A continuación, encontrará algunas de las propiedades útiles que puede personalizar como Cursor personalizado, los modelos de controlador de movimiento y el suelo.

![Propiedades para el controlador de movimiento de Cursor y Floor](images/MRTK_HowTo_Input3.png)<br>
*Propiedades para el controlador de movimiento de Cursor y Floor*

## <a name="follow-along-with-tutorials"></a>Seguir tutoriales

Tutoriales paso a paso, con ejemplos de personalización más detallados, están disponibles en la Academia de realidad mixta:

- [Entrada MR 211: Gesto](holograms-211.md)
- [Entrada MR 213: Controladores de movimiento](mixed-reality-213.md)

[![Entrada MR 213 - controlador de movimiento](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)<br>
*Entrada MR 213 - controlador de movimiento*

## <a name="see-also"></a>Vea también

* [Gestos](gestures.md)
* [Controladores de movimiento](motion-controllers.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [InteractionInputSource.cs en MixedRealityToolkit Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/InputSources/InteractionInputSource.cs)
