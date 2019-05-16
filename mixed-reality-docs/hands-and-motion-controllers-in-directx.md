---
title: Las manos y los controladores de movimiento de DirectX
description: Guía del desarrollador para usar el seguimiento de la mano y controladores de movimiento en las aplicaciones nativas de DirectX.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/30/2019
ms.topic: article
keywords: las manos, controladores de movimiento, directx, entrada, hologramas
ms.openlocfilehash: 08666c8c26cd4851c0c003a96a9e96d7a90228ac
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629648"
---
# <a name="hands-and-motion-controllers-in-directx"></a>Las manos y los controladores de movimiento de DirectX

En Windows Mixed Reality, tanto a mano y [controlador de movimiento](motion-controllers.md) entrada se controla a través de la entrada espacial API, se encuentra en la [Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) espacio de nombres. Esto le permite controlar fácilmente acciones comunes como **seleccione** presiona la misma manera a través de las manos y los controladores de movimiento.

## <a name="getting-started"></a>Introducción

Espaciales del acceso de entrada en Windows Mixed Reality, comience con la interfaz SpatialInteractionManager.  Puede tener acceso a esta interfaz mediante una llamada a [SpatialInteractionManager::GetForCurrentView](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getforcurrentview), normalmente, en ocasiones, durante el inicio de la aplicación.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

SpatialInteractionManager interactionManager = SpatialInteractionManager::GetForCurrentView();
```

Trabajo del SpatialInteractionManager es proporcionar acceso a [SpatialInteractionSources](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource), que representan un origen de entrada.  Hay tres tipos de SpatialInteractionSources disponibles en el sistema.
* **Mano** representa mano detectadas de un usuario. Orígenes de mano ofrecen diferentes características según el dispositivo, que van desde los gestos básicos en HoloLens a mano totalmente articulados y seguimiento en HoloLens 2. 
* **Controlador** representa un controlador de movimiento emparejado. Los controladores de movimiento pueden ofrecer una variedad de capacidades.  Por ejemplo: Seleccione los desencadenadores, los botones de menú, botones de comprensión, touchpads y sticks analógicos.
* **Voz** representa la voz del usuario hablando palabras clave del sistema detectado. Por ejemplo, este origen se inyectar presionar una selección y versión cada vez que el usuario dice "Select".

Datos por marco para un origen es representado por la [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) interfaz. Hay dos maneras diferentes para tener acceso a estos datos, según si quiere usar un modelo orientado a eventos o basados en sondeos en la aplicación.

### <a name="event-driven-input"></a>Controlado por eventos de entrada
El SpatialInteractionManager proporciona una serie de eventos que puede escuchar la aplicación.  Algunos ejemplos son [SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) y [SourceUpdated](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated).

Por ejemplo, el código siguiente enlaza un controlador de eventos llamado MyApp::OnSourcePressed para el evento SourcePressed.  Esto permite a detectar las presiones de cualquier tipo de origen de la interacción de la aplicación.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
interactionManager.SourcePressed({ this, &MyApp::OnSourcePressed });

```

Este evento presionado se envía a la aplicación de forma asincrónica, junto con el SpatialInteractionSourceState correspondiente en el momento en que se produjo la prensa. La aplicación o el motor de juego que desee realizar el procesamiento inmediatamente o puede que desee poner en cola los datos del evento en su rutina de procesamiento de entrada. Aquí es una función de controlador de eventos para el evento SourcePressed, que se muestra cómo comprobar si se presionó el botón de selección.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

void MyApp::OnSourcePressed(SpatialInteractionManager const& sender, SpatialInteractionSourceEventArgs const& args)
{
    if (args.PressKind() == SpatialInteractionPressKind::Select)
    {
        // Select button was pressed, update app state
    }
}
```

El código anterior sólo se comprueba si la acción de presionar 'Select', que corresponde a la acción primaria en el dispositivo. Por ejemplo, realizando un AirTap en HoloLens o extraer el desencadenador en un controlador de movimiento.  'Select' pulsaciones representan la intención del usuario para activar el holograma que como destino.  Desencadenará el evento SourcePressed para un número de botones diferentes y los gestos, y puede inspeccionar otras propiedades en el SpatialInteractionSource para los casos de prueba.

### <a name="polling-based-input"></a>Entrada basados en sondeos
También puede usar SpatialInteractionManager para sondear el estado actual de la entrada de cada fotograma.  Para ello, basta con llamar a [GetDetectedSourcesAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) cada fotograma.  Esta función devuelve una matriz que contiene uno [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) para cada activo [SpatialInteractionSource](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource). Esto significa, uno para cada controlador de movimiento activo, uno para cada manecilla sometidas a seguimiento y otro para voz si recientemente se dijeron un comando 'select'. A continuación, puede inspeccionar las propiedades en cada SpatialInteractionSourceState a la entrada de la unidad en la aplicación. 

Este es un ejemplo de cómo comprobar la acción 'select' con el método de sondeo. Tenga en cuenta que el *predicción* variable representa un [HolographicFramePrediction](https://docs.microsoft.com/en-us/uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) objeto, que puede obtenerse a partir del [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe).

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
auto sourceStates = m_spatialInteractionManager.GetDetectedSourcesAtTimestamp(prediction.Timestamp());

for (auto& sourceState : sourceStates)
{
    if (sourceState.IsSelectPressed())
    {
        // Select button is down, update app state
    }
}
```

Cada SpatialInteractionSource tiene un identificador, que puede usar para identificar nuevas fuentes y correlacionar los orígenes existentes desde un fotograma a fotograma.  Las manos se asignan a un nuevo identificador de cada vez deje y especifique el campo visual, pero los identificadores de controlador siguen siendo estáticos para la duración de la sesión.  Puede usar los eventos, como en SpatialInteractionManager [SourceDetected](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcedetected) y [SourceLost](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcelost), vista reaccionar cuando manos entren o salgan del dispositivo, o cuando los controladores de movimiento se activan activado/desactivado o no estén empareja/no emparejados.

### <a name="predicted-vs-historical-poses"></a>Predice frente a plantea histórico
Tenga en cuenta que GetDetectedSourcesAtTimestamp tiene un parámetro de marca de tiempo. Esto le permite solicitar el estado y presentan los datos que se predijeron bien o históricos, permitiéndole correlacionar espaciales interacciones con otros orígenes de entrada. Por ejemplo, al representar la posición de la mano en el marco actual, puede pasar en la marca de tiempo de predicción proporcionado por el [HolographicFrame](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe). Esto permite al sistema a la posición de la mano para alinear estrechamente con la salida de fotograma representado, minimiza la latencia percibida de avance predecir.

Sin embargo, este tipo una postura predicho generan un rayo señalador ideal para dirigirse a con un origen de interacción. Por ejemplo, cuando se presiona un botón de controlador de movimiento, puede tardar hasta 20 ms para ese evento se propagan a través de Bluetooth en el sistema operativo. De forma similar, una vez que un usuario realiza un gesto de mano, puede pasar cierta cantidad de tiempo antes de que el sistema detecta el movimiento y la aplicación, a continuación, sondea para él. Cuando la aplicación sondea si hay un cambio de estado, el principal y mano puede causar utilizado al destino que ha sucedido realmente interacción en el pasado. Si su objetivo al pasar la marca de tiempo de su HolographicFrame actual a GetDetectedSourcesAtTimestamp, la postura en su lugar se adelante predecirá a destinatarios rayo en el momento en que se mostrará el marco, que podría ser más de 20 ms en el futuro. Este futuro postura es bueno para *representación* el origen de la interacción, pero nuestro problema de tiempo para los compuestos *destinatarios* la interacción, como el usuario de destino se produjo en el pasado.

Afortunadamente, la [SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) y [SourceUpdated](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated) eventos proporcionan el histórico [estado](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) asociado cada evento de entrada.  Esto incluye directamente el histórico head y mano puede causar disponibles a través de [TryGetPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose), junto con un históricos [Timestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.timestamp) que puede pasar a otras API para correlacionar con este evento.

Esto nos lleva a las siguientes prácticas recomendadas de representación y compatibilidad con las manos y los controladores de cada fotograma:
* Para **representación mano/controlador** cada fotograma, la aplicación debe **sondeo** para el **predicho de avance** suponer de cada origen de interacción en tiempo de photon del marco actual.  Se puede sondear para todos los orígenes de interacción mediante una llamada a [GetDetectedSourcesAtTimestamp](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) cada fotograma, pasando la marca de tiempo de predicción proporcionado por [HolographicFrame::CurrentPrediction](https://docs.microsoft.com/en-us/uwp/api/windows.graphics.holographic.holographicframe.currentprediction).
* Para **destinadas a mano o controlador** tras un presione o versión, la aplicación debe controlar presionado o lanzado **eventos**, detalles según el **históricos** postura head o disponible para ese evento. Obtener esta ray destinatarios controlando el [SourcePressed](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed) o [SourceReleased](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) eventos, obteniendo el [estado](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) propiedad de los argumentos de evento y, a continuación, llamar a su [ TryGetPointerPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) método.

## <a name="cross-device-input-properties"></a>Propiedades de entrada entre dispositivos
La API de SpatialInteractionSource admite los controladores y los sistemas con una amplia gama de capacidades de seguimiento de mano. Un número de estas capacidades es comunes entre los tipos de dispositivo. Por ejemplo, mano movimiento y seguimiento de los controladores de ambos proporcionan una acción 'select' y una posición 3D. Siempre que sea posible, la API asigna estas funcionalidades comunes a las mismas propiedades en el SpatialInteractionSource.  Esto permite que las aplicaciones admitir más fácilmente una amplia gama de tipos de entrada. En la tabla siguiente se describe las propiedades que son compatibles y cómo se comparan entre tipos de entrada.

| Property | Descripción | Gestos de HoloLens | Controladores de movimiento | Manos articuladas|
|--- |--- |--- |--- |--- |
| [SpatialInteractionSource::**Handedness**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.handedness) | Derecha o izquierda o controlador. | No se admite | Se admite | Se admite |
| [SpatialInteractionSourceState::**IsSelectPressed**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isselectpressed) | Estado actual del botón principal. | En el aire | desencadenador | Pulse aire moderada (acercar los dedos vertical) |
| [SpatialInteractionSourceState::**IsGrasped**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isgrasped) | Estado actual del botón de arrastre. | No se admite | Botón de captura | Reducir o cerrado de mano |
| [SpatialInteractionSourceState::**IsMenuPressed**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.ismenupressed) | Estado actual del botón de menú.    | No se admite | Botón de menú | No se admite |
| [SpatialInteractionSourceLocation::**Position**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.position) | Ubicación de XYZ de la posición de mano o control en el controlador. | Ubicación de Palm | Posición de la postura de control | Ubicación de Palm |
| [SpatialInteractionSourceLocation::**Orientation**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.orientation) | Cuaternión que representa la orientación de la postura de mano o control en el controlador. | No se admite | Orientación de la postura de control | Orientación de Palm |
| [SpatialPointerInteractionSourcePose::**Position**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.position#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_Position) | Origen del rayo señalador. | No se admite | Se admite | Se admite |
| [SpatialPointerInteractionSourcePose::**ForwardDirection**](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.forwarddirection#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_ForwardDirection) | Dirección del rayo señalador. | No se admite | Se admite | Se admite |

Algunas de las propiedades anteriores no están disponibles en todos los dispositivos y la API proporciona un medio para probar esto. Por ejemplo, puede inspeccionar el [SpatialInteractionSource::IsGraspSupported](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.isgraspsupported) propiedad para determinar si el origen proporciona una idea de acción.

### <a name="grip-pose-vs-pointing-pose"></a>Postura de control frente a la postura señalador

Windows Mixed Reality es compatible con controladores de movimiento en una variedad de factores de forma.  También admite articulado mano los sistemas de seguimiento.  Todos estos sistemas tienen distintas relaciones entre la posición de la mano y la dirección de "reenvío" natural que las aplicaciones deben usar para los objetos que señala o rendreing en manos del usuario.  Para admitir todo esto, hay dos tipos de 3D puede causar proporcionada para ambos controladores de seguimiento y el movimiento de la mano.  La primera es la postura de control, que representa la posición del usuario manualmente.  El segundo está señalando una postura, que representa un rayo señalador procedentes de mano o el controlador del usuario. Por lo tanto, si quiere representar **la mano del usuario** o **mantiene un objeto en la mano del usuario**, como una Espada o filo, use la postura de control. Si desea raycast desde el controlador o la mano, por ejemplo, cuando el usuario es **apuntando a la interfaz de usuario** , utilice la postura señalador.

Puede tener acceso a la **control postura** a través de [SpatialInteractionSourceState::Properties::TryGetLocation(...) ](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties.trygetlocation#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).  Se define como sigue:
* El **sujete posición**: El centroide de palm cuando se mantiene el controlador de forma natural, ajustar izquierda o derecha para centrar la posición dentro del control.
* El **sujete eje derecho de orientación**: Cuando se abre completamente la mano para formar una postura plano 5-dedo, el rayo que es normal que la palma (hacia delante desde la palma de izquierdo, con versiones anteriores desde la palma derecha)
* El **sujete eje hacia delante de orientación**: Cuando cierre la mano parcialmente (como si mantiene el controlador), el rayo que señala "forward" a través del tubo formado por los dedos no thumb.
* El **sujete orientación de eje**: El eje vertical implicado en las definiciones de la derecha y hacia delante.

Puede tener acceso a la **puntero postura** a través de [SpatialInteractionSourceState::Properties::TryGetLocation (...):: SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) o [SpatialInteractionSourceState:: TryGetPointerPose (...):: TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).

## <a name="controller-specific-input-properties"></a>Propiedades de entrada específicas del controlador
Para los controladores, el SpatialInteractionSource tiene una propiedad de controlador con capacidades adicionales.
* **HasThumbstick:** Si es true, el controlador tiene una tecla de navegación. Inspeccionar el [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) propiedad de la SpatialInteractionSourceState para adquirir la tecla de navegación x y los valores y (ThumbstickX y ThumbstickY), así como su estado presionado (IsThumbstickPressed).
* **HasTouchpad:** Si es true, el controlador tiene un panel táctil. Inspeccionar la propiedad ControllerProperties de la SpatialInteractionSourceState para adquirir el panel táctil x e y valores (TouchpadX y TouchpadY) y para saber si el usuario toca la almohadilla (IsTouchpadTouched) y si presiona el panel táctil hacia abajo () IsTouchpadPressed).
* **SimpleHapticsController:** Para el controlador de la API de SimpleHapticsController le permite inspeccionar las capacidades de haptics del controlador, y también permite controlar comentarios hápticos.

Tenga en cuenta que el intervalo para teclado táctil y la tecla de navegación es -1 y 1 para ambos ejes (de abajo a arriba y de izquierda a derecha). El intervalo para el desencadenador analógico, que se obtiene acceso mediante la propiedad SpatialInteractionSourceState::SelectPressedValue, tiene un intervalo de 0 a 1. Un valor de 1 se correlaciona con IsSelectPressed igual a true. cualquier otro valor se correlaciona con IsSelectPressed igual a false.

## <a name="articulated-hand-tracking"></a>Seguimiento de mano articulado
La API de realidad mixta de Windows proporciona compatibilidad completa para mano articulado seguimiento, por ejemplo, en HoloLens 2. Seguimiento de mano articulado puede utilizarse para implementar los modelos de confirmación de punto de entrada y de manipulación directa en sus aplicaciones. También puede usarse para crear interacciones completamente personalizadas.

### <a name="hand-skeleton"></a>Esqueleto de mano
Mano articulado seguimiento proporciona un esqueleto de 25 común que permite a muchos tipos diferentes de las interacciones.  El esqueleto proporciona 5 articulaciones para los dedos de índice/intermedio/anillo/poco, 4 puntos de unión para el control thumb y 1 muñeca común.  La junta de la muñeca actúa como la base de la jerarquía. La siguiente ilustración muestra el diseño del esqueleto.

![Esqueleto de mano](images/hand-skeleton.png)

En la mayoría de los casos, cada conjunto se denomina según el hueso que representa.  Dado que hay dos huesos en cada unión, usamos una convención de nomenclatura cada junta según el hueso secundario en esa ubicación.  El hueso secundarios se define como el hueso más lejos de la muñeca.  Por ejemplo, el "índice articulaciones próximas" conjunta contiene la posición inicial del hueso articulaciones próximas índice y la orientación de ese ósea.  No contiene la posición final del hueso.  Si necesita, se podría obtener del siguiente común en la jerarquía, el "índice"intermedio común.

Además de las 25 juntas jerárquicas, el sistema proporciona una junta palm.  La palma normalmente no se considera parte de la estructura básica.  Se proporciona sólo como una manera cómoda de obtener la posición y orientación general de la mano.

La siguiente información se proporciona para cada unión:

| Nombre | Descripción |
|--- |--- |
|Posición | Posición 3D de la junta, disponible en cualquier sistema de coordenadas solicitado. |
|Orientación | Orientación 3D del hueso, disponible en ninguna solicitado del sistema de coordenadas. |
|Radio | Distancia a la superficie de la máscara en la posición del conjunta. Resulta útil para la optimización de las interacciones directas o visualizaciones que se basan en el ancho del dedo. |
|Precisión | Proporciona una sugerencia en el nivel de confianza se siente acerca de la información de la unión. |

Puede obtener acceso a los datos de esqueleto de mano a través de una función en el [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).  Se llama a la función [TryGetHandPose](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygethandpose#Windows_UI_Input_Spatial_SpatialInteractionSourceState_TryGetHandPose), y devuelve un objeto denominado [HandPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose).  Si el origen no es compatible con manos articuladas, esta función devolverá null.  Una vez que tenga un HandPose, puede obtener datos del conjuntos actual mediante una llamada a [TryGetJoint](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose.trygetjoint#Windows_Perception_People_HandPose_TryGetJoint_Windows_Perception_Spatial_SpatialCoordinateSystem_Windows_Perception_People_HandJointKind_Windows_Perception_People_JointPose__), con el nombre de la junta de la que está interesado.  Los datos se devuelven como un [JointPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.jointpose) estructura.  El código siguiente obtiene la posición de la punta del dedo índice. La variable *currentState* representa una instancia de [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::Foundation::Numerics;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    JointPose joint;
    if (handPose.TryGetJoint(desiredCoordinateSystem, HandJointKind::IndexTip, joint))
    {
        float3 indexTipPosition = joint.Position;

        // Do something with the index tip position
    }
}
```

### <a name="hand-mesh"></a>Malla de mano

La API de seguimiento de mano articulada permite una malla de triángulo deformable totalmente disponible.  Esta malla puede deform en tiempo real junto con el esqueleto de la mano y es útil para la visualización, así como técnicas avanzadas de leyes físicas.  Para obtener acceso a la malla de mano, debe crear primero un [HandMeshObserver](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver) objeto mediante una llamada a [TryCreateHandMeshObserverAsync](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync) en el [SpatialInteractionSource](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsource).  Esto solo debe realizarse una vez por cada origen, normalmente la primera vez que lo vea.  Esto significa que se llamará a esta función para crear un objeto HandMeshObserver siempre que sea una mano entra en el campo visual.  Tenga en cuenta que esto es una función asincrónica, por lo que tendrá que tratar con un poco de simultaneidad aquí.  Cuando esté disponible, puede pedir el objeto HandMeshObserver el búfer de índice de triángulo mediante una llamada a [GetTriangleIndices](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver.gettriangleindices#Windows_Perception_People_HandMeshObserver_GetTriangleIndices_System_UInt16___).  Índices no cambien marco sobre el marco, por lo que puede obtenerlos de una vez y almacenarlos en memoria caché durante la vigencia del origen.  Los índices se muestran en orden de generación de las agujas del reloj.

El código siguiente se pone en marcha un std::thread desasociada para crear el observador de la malla y extrae el búfer de índice cuando esté disponible el observador de malla.  Se inicia desde una variable denominada *currentState*, que es una instancia de [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) que representa una mano sometidas a seguimiento.

```cpp
using namespace Windows::Perception::People;

std::thread createObserverThread([this, currentState]()
{
    HandMeshObserver newHandMeshObserver = currentState.Source().TryCreateHandMeshObserverAsync().get();
    if (newHandMeshObserver)
    {
        unsigned indexCount = newHandMeshObserver.TriangleIndexCount();
        vector<unsigned short> indices(indexCount);
        newHandMeshObserver.GetTriangleIndices(indices);

        // Save the indices and handMeshObserver for later use - and use a mutex to synchronize access if needed!
     }
});
createObserverThread.detach();
```
Iniciar un subproceso separado es sólo una opción para controlar las llamadas asincrónicas.  Como alternativa, puede usar el nuevo [co_await](https://docs.microsoft.com/en-us/windows/uwp/cpp-and-winrt-apis/concurrency) funcionalidad admitida por C++/WinRT.

Una vez que un objeto HandMeshObserver, debe retener durante el tiempo que su SpatialInteractionSource correspondiente está activo.  A continuación, en cada fotograma, puede pedir para el búfer de vértices más reciente que representa la mano mediante una llamada a [GetVertexStateForPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshobserver.getvertexstateforpose) y pasando un [HandPose](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handpose) instancia que representa la postura que desea que los vértices para.  Cada vértice en el búfer tiene una posición y normal.  Este es un ejemplo de cómo obtener el conjunto actual de los vértices de una malla de mano.  Igual que antes, el *currentState* variable representa una instancia de [SpatialInteractionSourceState](https://docs.microsoft.com/en-us/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).

```cpp
using namespace winrt::Windows::Perception::People;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    std::vector<HandMeshVertex> vertices(handMeshObserver.VertexCount());
    auto vertexState = handMeshObserver.GetVertexStateForPose(handPose);
    vertexState.GetVertices(vertices);

    auto meshTransform = vertexState.CoordinateSystem().TryGetTransformTo(desiredCoordinateSystem);
    if (meshTransform != nullptr)
    {
        // Do something with the vertices and mesh transform, along with the indices that you saved earlier
    }
}
```

A diferencia de uniones de esqueleto, la API de malla de mano no le permiten especificar un sistema de coordenadas de los vértices.  En su lugar, el [HandMeshVertexState](https://docs.microsoft.com/en-us/uwp/api/windows.perception.people.handmeshvertexstate) especifica el sistema de coordenadas que se proporcionan los vértices en.  A continuación, puede obtener una transformación de malla mediante una llamada a [TryGetTransformTo](https://docs.microsoft.com/en-us/uwp/api/windows.perception.spatial.spatialcoordinatesystem.trygettransformto#Windows_Perception_Spatial_SpatialCoordinateSystem_TryGetTransformTo_Windows_Perception_Spatial_SpatialCoordinateSystem_) y especifica el sistema de coordenadas deseado.  Deberá usar esta transformación malla siempre que trabaje con los vértices.  Este enfoque reduce la sobrecarga de CPU, especialmente si se usa solo la malla para fines de representación.

## <a name="gaze-and-commit-composite-gestures"></a>Observación y confirmar los gestos compuestos
Las aplicaciones que usan el modelo de entrada de mirada y confirmación, especialmente en HoloLens (primer uso), la API de entrada espacial proporciona opcional [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) que puede utilizar para habilitar los gestos compuestos creados en la parte superior de la 'select' eventos.  Mediante el enrutamientos interacciones desde el SpatialInteractionManager a SpatialGestureRecognizer de un holograma, las aplicaciones pueden detectar eventos Tap, suspensión, manipulación y navegación uniformemente entre manos, voz y dispositivos de entrada espaciales, sin tener que controlar las pulsaciones y libera manualmente.

SpatialGestureRecognizer realiza solo la anulación de ambigüedades mínimo entre el conjunto de gestos que solicitan. Por ejemplo, si se solicita solo Tap, el usuario puede presionada su dedo como deseen y todavía se producirá una derivación. Si se solicita tanto pulsado, después de aproximadamente un segundo de mantener presionado su dedo, el gesto se promoverá a una suspensión y ya no se producirá un punteo.

Para usar SpatialGestureRecognizer, controlar el SpatialInteractionManager [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) agarre el SpatialPointerPose expuesto allí y eventos. Usar ray de mirada principal del usuario desde esta postura para formar una intersección con el hologramas y superficie mallas en el entorno del usuario, con el fin de determinar lo que va a interactuar con el usuario. A continuación, enrutar la SpatialInteraction en los argumentos de evento SpatialGestureRecognizer del holograma de destino, mediante su [CaptureInteraction](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) método. Esto inicia la interpretación de esa interacción según la [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) establecer en ese módulo de reconocimiento, o en tiempo de creación - [TrySetGestureSettings](http://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).

En HoloLens (gen. primero), por lo general deben derivar las interacciones y los gestos sus destinatarios de mirada principal del usuario, en lugar de intentar para representar o interactuar directamente en la ubicación de la mano. Una vez que se ha iniciado una interacción, los movimientos relativos de la mano pueden utilizarse para controlar el movimiento, al igual que con el gesto de manipulación o exploración.

## <a name="see-also"></a>Vea también
* [Mirada principal y de ojo de DirectX](gaze-in-directx.md)
* [Modelo de entrada de la manipulación directa](direct-manipulation.md)
* [Modelo de entrada de punto y confirmación](point-and-commit.md)
* [Modelo de entrada de mirada y confirmación](gaze-and-commit.md)
* [Controladores de movimiento](motion-controllers.md)
