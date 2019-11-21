---
title: Controladores de manos y movimiento en DirectX
description: Guía del desarrollador para usar el seguimiento de mano y los controladores de movimiento en aplicaciones DirectX nativas.
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/30/2019
ms.topic: article
keywords: manos, controladores de movimiento, DirectX, entrada, hologramas
ms.openlocfilehash: 54eaacc3f0dccf728b5438c020a5efd7e0788251
ms.sourcegitcommit: 4081dc2356fec0ea3625f1d989689cfbbb3fcf5f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74203336"
---
# <a name="hands-and-motion-controllers-in-directx"></a>Controladores de manos y movimiento en DirectX

En Windows Mixed Reality, la entrada de [controlador de movimiento](motion-controllers.md) y la mano se administra a través de las API de entrada espaciales, que se encuentran en el espacio de nombres [Windows. UI. Input. Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) . Esto le permite controlar fácilmente acciones comunes, como **selecciones** , de la misma manera en los controladores de manos y de movimiento.

## <a name="getting-started"></a>Tareas iniciales

Para tener acceso a la entrada espacial en Windows Mixed Reality, empiece con la interfaz SpatialInteractionManager.  Puede tener acceso a esta interfaz mediante una llamada a [SpatialInteractionManager:: GetForCurrentView](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getforcurrentview), normalmente durante el inicio de la aplicación.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

SpatialInteractionManager interactionManager = SpatialInteractionManager::GetForCurrentView();
```

El trabajo de SpatialInteractionManager es proporcionar acceso a [SpatialInteractionSources](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource), que representa un origen de entrada.  Hay tres tipos de SpatialInteractionSources disponibles en el sistema.
* **Hand** representa la mano detectada de un usuario. Los orígenes de mano ofrecen diferentes características basadas en el dispositivo, que abarcan desde gestos básicos de HoloLens hasta un seguimiento completo de la mano en HoloLens 2. 
* **Controller** representa un controlador de movimiento emparejado. Los controladores de movimiento pueden ofrecer una variedad de funcionalidades.  Por ejemplo: seleccione desencadenadores, botones de menú, botones de agarre, Touchpad y thumbsticks.
* **Voice** representa las palabras clave detectadas por el sistema de habla de voz del usuario. Por ejemplo, este origen insertará una imprenta SELECT y Release siempre que el usuario diga "Select".

Los datos por fotograma para un origen se representan mediante la interfaz [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) . Hay dos maneras diferentes de acceder a estos datos, en función de si desea usar un modelo basado en eventos o en el sondeo en la aplicación.

### <a name="event-driven-input"></a>Entrada controlada por eventos
SpatialInteractionManager proporciona varios eventos para los que puede escuchar la aplicación.  Algunos ejemplos son [SourcePressed](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [SourceReleased](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) y [SourceUpdated](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated).

Por ejemplo, el código siguiente enlaza un controlador de eventos denominado MyApp:: OnSourcePressed al evento SourcePressed.  Esto permite que la aplicación detecte presiones en cualquier tipo de origen de interacción.

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
interactionManager.SourcePressed({ this, &MyApp::OnSourcePressed });

```

Este evento presionado se envía a la aplicación de forma asincrónica, junto con el SpatialInteractionSourceState correspondiente en el momento en que se produjo el error. Es posible que la aplicación o el motor de juegos quiera realizar algún procesamiento de inmediato o que desee poner en cola los datos de eventos en la rutina de procesamiento de entrada. Esta es una función de controlador de eventos para el evento SourcePressed, que muestra cómo comprobar si se presionó el botón seleccionar.

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

El código anterior solo comprueba la acción "Select", que corresponde a la acción primaria en el dispositivo. Entre los ejemplos se incluye la realización de una AirTap en HoloLens o la extracción del desencadenador en un controlador de movimiento.  Las presiones de "Select" representan la intención del usuario de activar el holograma al que están destinadas.  El evento SourcePressed se activará para varios botones y gestos diferentes, y puede inspeccionar otras propiedades en el SpatialInteractionSource para comprobar dichos casos.

### <a name="polling-based-input"></a>Entrada basada en sondeo
También puede usar SpatialInteractionManager para sondear el estado actual de la entrada de cada fotograma.  Para ello, basta con llamar a [GetDetectedSourcesAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) en cada fotograma.  Esta función devuelve una matriz que contiene un [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) para cada [SpatialInteractionSource](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource)activo. Esto significa que una para cada controlador de movimiento activo, uno para cada mano a la que se ha realizado un seguimiento y otro para la voz si se ha creado recientemente un comando "Select". Después, puede inspeccionar las propiedades de cada SpatialInteractionSourceState para dirigir la entrada a la aplicación. 

Este es un ejemplo de cómo buscar la acción "Select" mediante el método de sondeo. Tenga en cuenta que la variable de *predicción* representa un objeto [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction) , que se puede obtener a partir de [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe).

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

Cada SpatialInteractionSource tiene un identificador, que se puede usar para identificar nuevos orígenes y correlacionar los orígenes existentes entre fotogramas y fotogramas.  A las manos se les asigna un nuevo ID. cada vez que salen y entran en el hiperusuario, pero los identificadores de controlador siguen siendo estáticos mientras dure la sesión.  Puede usar los eventos de SpatialInteractionManager, como [SourceDetected](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcedetected) y [SourceLost](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcelost), para reaccionar cuando las manos entran o salen de la vista del dispositivo, o cuando los controladores de movimiento se activan o desactivan o se emparejan o desemparejan.

### <a name="predicted-vs-historical-poses"></a>Supuestos previstos frente a supuestos históricos
Tenga en cuenta que GetDetectedSourcesAtTimestamp tiene un parámetro timestamp. Esto le permite solicitar el estado y presentar datos que sean predecidos o históricos, lo que le permitirá poner en correlación las interacciones espaciales con otros orígenes de entrada. Por ejemplo, al representar la posición de la mano en el fotograma actual, puede pasar la marca de tiempo de predicción proporcionada por [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe). Esto permite que el sistema avance y prediga la posición de la mano para que se alinee con la salida del fotograma representado, lo que minimiza la latencia percibida.

Sin embargo, una pose de predicción de este tipo no produce un rayo apuntador ideal para el destino con un origen de interacción. Por ejemplo, cuando se presiona un botón de controlador de movimiento, puede tardar hasta 20 ms para que ese evento se propague a través de Bluetooth al sistema operativo. Del mismo modo, después de que un usuario realice un gesto de mano, es posible que haya transcurrido un período de tiempo antes de que el sistema detecte el movimiento y la aplicación lo sondeará. En el momento en que la aplicación sondea un cambio de estado, el encabezado y la mano se usan para dirigirse realmente a esa interacción en el pasado. Si tiene como destino el paso de la marca de tiempo de su HolographicFrame actual a GetDetectedSourcesAtTimestamp, la pose se predice en su lugar al rayo de destino en el momento en que se mostrará el fotograma, lo que podría ser superior a 20 MS en el futuro. Este planteamiento futuro es adecuado para *representar* el origen de la interacción, pero constituye un problema de tiempo para *dirigirse* a la interacción, ya que los destinatarios del usuario se produjeron en el pasado.

Afortunadamente, los eventos [SourcePressed](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed), [SourceReleased](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) y [SourceUpdated](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated) proporcionan el [Estado](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) histórico asociado a cada evento de entrada.  Esto incluye directamente el encabezado histórico y las manos disponibles a través de [TryGetPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose), junto con una [marca](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.timestamp) de tiempo histórica que puede pasar a otras API para correlacionar con este evento.

Esto conduce a las siguientes prácticas recomendadas al representar y destinar a manos y controladores cada fotograma:
* En cuanto a la **representación manual o del controlador** en cada fotograma, la aplicación debe **sondear** la suposición de **predicción de reenvío** de cada origen de interacción en el momento de Photon del fotograma actual.  Puede sondear todos los orígenes de interacción llamando a [GetDetectedSourcesAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) cada fotograma, pasando la marca de tiempo de predicción proporcionada por [HolographicFrame:: CurrentPrediction](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.currentprediction).
* En el caso de los **destinatarios** de la mano o del controlador, en una imprenta o en una versión, la aplicación debe controlar **los eventos**presionados o liberados, raycasting basándose **en el encabezado** o la pose de la mano del evento. Para obtener este rayo de destino, puede controlar el evento [SourcePressed](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed) o [SourceReleased](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) , obtener la propiedad [State](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) de los argumentos de evento y, a continuación, llamar a su método [TryGetPointerPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) .

## <a name="cross-device-input-properties"></a>Propiedades de entrada entre dispositivos
La API de SpatialInteractionSource admite controladores y sistemas de seguimiento de mano con una amplia gama de funcionalidades. Una serie de estas funcionalidades son comunes entre los tipos de dispositivo. Por ejemplo, el seguimiento de mano y los controladores de movimiento proporcionan una acción "Select" y una posición 3D. Siempre que sea posible, la API asigna estas funciones comunes a las mismas propiedades en el SpatialInteractionSource.  Esto permite a las aplicaciones admitir más fácilmente una amplia gama de tipos de entrada. En la tabla siguiente se describen las propiedades que se admiten y cómo se comparan entre los tipos de entrada.

| Propiedad | Descripción | Gestos de HoloLens (primera generación) | Controladores de movimiento | Manos articuladas|
|--- |--- |--- |--- |--- |
| [SpatialInteractionSource::**Handl**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource.handedness) | Mano derecha o izquierda/controlador. | No se admite | Se admite | Se admite |
| [SpatialInteractionSourceState::**IsSelectPressed**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isselectpressed) | Estado actual del botón principal. | TAP del aire | Desencadenador | Pulsación aérea relajada (bajo contacto vertical) |
| [SpatialInteractionSourceState::**IsGrasped**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isgrasped) | Estado actual del botón de arrastre. | No se admite | Botón de arrastre | Alejar o cerrar mano |
| [SpatialInteractionSourceState::**IsMenuPressed**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.ismenupressed) | Estado actual del botón de menú.    | No se admite | Botón de menú | No se admite |
| [SpatialInteractionSourceLocation::**Position**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.position) | Ubicación XYZ de la mano o posición del puño en el controlador. | Ubicación de Palm | Posición de la postura de control | Ubicación de Palm |
| [SpatialInteractionSourceLocation::**Orientation**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.orientation) | Cuaternión que representa la orientación de la mano o del puño en el controlador. | No se admite | Orientación de la pose de puño | Orientación de Palm |
| [SpatialPointerInteractionSourcePose::**Position**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.position#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_Position) | Origen del rayo señalador. | No se admite | Se admite | Se admite |
| [SpatialPointerInteractionSourcePose::**ForwardDirection**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.forwarddirection#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_ForwardDirection) | Dirección del rayo señalador. | No se admite | Se admite | Se admite |

Algunas de las propiedades anteriores no están disponibles en todos los dispositivos y la API proporciona un medio para probar esto. Por ejemplo, puede inspeccionar la propiedad [SpatialInteractionSource:: IsGraspSupported](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource.isgraspsupported) para determinar si el origen proporciona una acción de agarre.

### <a name="grip-pose-vs-pointing-pose"></a>Replanteamiento de control frente a pose de puntero

Windows Mixed Reality admite controladores de movimiento en diversos factores de forma.  También admite sistemas de seguimiento de mano articulados.  Todos estos sistemas tienen relaciones diferentes entre la posición de la mano y la dirección de "avance" natural que las aplicaciones deben usar para señalar o representar objetos en la mano del usuario.  Para admitir todo esto, se proporcionan dos tipos de supuestos 3D para el seguimiento y los controladores de movimiento de la mano.  La primera es la postura de control, que representa la posición del usuario.  La segunda es el representador que señala, que representa un rayo señalador que se origina desde la mano o el controlador del usuario. Por lo tanto, si desea presentar **la mano del usuario** o **un objeto mantenido en la mano del usuario**, por ejemplo, un arma o un cañón, utilice la postura de control. Si desea Raycast del controlador o de la mano, por ejemplo, cuando el usuario **apunta a la interfaz** de usuario, use la pose de puntero.

Puede tener acceso a la **pose de control** a través de [SpatialInteractionSourceState::P ropiedades:: TryGetLocation (...)](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties.trygetlocation#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_).  Se define de la siguiente manera:
* La **posición del puño**: Palm centroide cuando mantiene el controlador de forma natural, se ajusta hacia la izquierda o derecha para centrar la posición dentro del control.
* **Eje derecho de la orientación del puño**: cuando se abre por completo la mano para formar una postura plana de 5 dedos, el rayo perpendicular a la palma (hacia delante de la mano izquierda y hacia atrás desde la mano derecha)
* El **eje hacia delante de la orientación del puño**: al cerrar la mano (como si contiene el controlador), el rayo que señala "reenviar" a través del tubo formado por los dedos no Thumb.
* **Eje hacia arriba de la orientación del puño**: el eje hacia arriba implícito por las definiciones derecha y hacia delante.

Puede tener acceso al **replanteamiento del puntero** a través de [SpatialInteractionSourceState::P ropiedades:: TryGetLocation (...):: SourcePointerPose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose) o [SpatialInteractionSourceState:: TryGetPointerPose (...):: TryGetInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_).

## <a name="controller-specific-input-properties"></a>Propiedades de entrada específicas del controlador
En el caso de los controladores, SpatialInteractionSource tiene una propiedad de controlador con capacidades adicionales.
* **HasThumbstick:** Si es true, el controlador tiene un stick. Inspeccione la propiedad [ControllerProperties](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) de SpatialInteractionSourceState para adquirir los valores x e y del stick analógico (ThumbstickX y ThumbstickY), así como el estado presionado (IsThumbstickPressed).
* **HasTouchpad:** Si es true, el controlador tiene un touchpad. Inspeccione la propiedad ControllerProperties de SpatialInteractionSourceState para adquirir los valores x e y de Touchpad (TouchpadX y Touchpad) y para saber si el usuario está tocando el panel (IsTouchpadTouched) y si está presionando el panel táctil ( IsTouchpadPressed).
* **SimpleHapticsController:** La API de SimpleHapticsController para el controlador permite inspeccionar las capacidades de hápticos del controlador y también permite controlar los comentarios de hápticos.

Tenga en cuenta que el intervalo para Touchpad y el Stick es-1 a 1 para ambos ejes (de abajo a arriba y de izquierda a derecha). El intervalo del desencadenador analógico, al que se tiene acceso mediante la propiedad SpatialInteractionSourceState:: SelectPressedValue, tiene un intervalo de 0 a 1. Un valor de 1 se correlaciona con IsSelectPressed igual a true; cualquier otro valor corresponde a IsSelectPressed siendo igual a false.

## <a name="articulated-hand-tracking"></a>Seguimiento de mano articulado
La API de Windows Mixed Reality proporciona compatibilidad total para el seguimiento de mano articulado, por ejemplo, en HoloLens 2. El seguimiento manual articulado se puede usar para implementar la manipulación directa y los modelos de entrada de punto y confirmación en las aplicaciones. También se puede usar para crear interacciones completamente personalizadas.

### <a name="hand-skeleton"></a>Esqueleto manual
El seguimiento de mano articulado proporciona un conjunto de 25 esqueleto que permite muchos tipos diferentes de interacciones.  El esqueleto proporciona 5 uniones para los dedos de índice/intermedio/anillo/pequeño, 4 uniones para el pulgar y 1 conjunto de muñecas.  La Unión de muñecas actúa como la base de la jerarquía. En la imagen siguiente se muestra el diseño del esqueleto.

![Esqueleto manual](images/hand-skeleton.png)

En la mayoría de los casos, cada conjunto se denomina basándose en el hueso que representa.  Dado que hay dos huesos en cada conjunto, usamos una Convención de nomenclatura de cada unión basada en el hueso secundario en esa ubicación.  El hueso secundario se define como el hueso más allá de la muñeca.  Por ejemplo, la Unión "index proximal" contiene la posición inicial del proximal de índice y la orientación de dicho hueso.  No contiene la posición final del hueso.  Si lo necesita, lo obtendría de la Unión siguiente en la jerarquía, la Unión "índice intermedio".

Además de las 25 uniones jerárquicas, el sistema proporciona una Unión de Palm.  La palma normalmente no se considera parte de la estructura del esqueleto.  Solo se proporciona como una manera cómoda de obtener la posición y orientación generales de la mano.

La siguiente información se proporciona para cada conjunto:

| Nombre | Descripción |
|--- |--- |
|Posición | posición 3D de la Unión, disponible en cualquier sistema de coordenadas solicitado. |
|Orientación | orientación 3D del hueso, disponible en cualquier sistema de coordenadas solicitado. |
|Radio | Distancia a superficie de la piel en la posición de la Unión. Resulta útil para optimizar interacciones directas o visualizaciones que se basan en el ancho del dedo. |
|Precisión | Proporciona una sugerencia sobre el grado de confianza del sistema con respecto a la información de la Unión. |

Puede tener acceso a los datos del esqueleto de mano a través de una función en [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).  La función se denomina [TryGetHandPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygethandpose#Windows_UI_Input_Spatial_SpatialInteractionSourceState_TryGetHandPose)y devuelve un objeto denominado [HandPose](https://docs.microsoft.com//uwp/api/windows.perception.people.handpose).  Si el origen no admite manos articuladas, esta función devolverá null.  Una vez que tenga un HandPose, puede obtener datos conjuntos actuales llamando a [TryGetJoint](https://docs.microsoft.com//uwp/api/windows.perception.people.handpose.trygetjoint#Windows_Perception_People_HandPose_TryGetJoint_Windows_Perception_Spatial_SpatialCoordinateSystem_Windows_Perception_People_HandJointKind_Windows_Perception_People_JointPose__), con el nombre de la Unión en la que está interesado.  Los datos se devuelven como una estructura [JointPose](https://docs.microsoft.com//uwp/api/windows.perception.people.jointpose) .  En el código siguiente se obtiene la posición de la sugerencia de índice. La variable *CurrentState* representa una instancia de [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).

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

La API de seguimiento de mano articulada permite una malla de mano de triángulo totalmente deformable.  Esta malla puede deformarse en tiempo real junto con el esqueleto manual y resulta útil para la visualización, así como técnicas de física avanzadas.  Para acceder a la malla de mano, primero debe crear un objeto [HandMeshObserver](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshobserver) llamando a [TryCreateHandMeshObserverAsync](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync) en [SpatialInteractionSource](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource).  Esto solo debe realizarse una vez por origen, normalmente la primera vez que lo ve.  Esto significa que se llamará a esta función para crear un objeto HandMeshObserver siempre que una mano entre en el subobjeto.  Tenga en cuenta que se trata de una función asincrónica, por lo que tendrá que tratar un poco de simultaneidad aquí.  Una vez disponible, puede solicitar al objeto HandMeshObserver el búfer de índice de triángulo llamando a [GetTriangleIndices](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshobserver.gettriangleindices#Windows_Perception_People_HandMeshObserver_GetTriangleIndices_System_UInt16___).  Los índices no cambian el marco sobre el marco, de modo que puede obtenerlos una vez y almacenarlos en memoria caché durante el tiempo de vida del origen.  Los índices se proporcionan en el orden de bobinado hacia la derecha.

El siguiente código pone en marcha un STD:: Thread separado para crear el observador de la malla y extrae el búfer de índice una vez que el observador de la malla esté disponible.  Se inicia a partir de una variable denominada *CurrentState*, que es una instancia de [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) que representa una mano a la que se ha realizado un seguimiento.

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
Iniciar un subproceso desasociado es solo una opción para controlar las llamadas asincrónicas.  Como alternativa, puede usar la nueva funcionalidad de [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) compatible con C++/WinRT.

Una vez que tenga un objeto HandMeshObserver, debe mantenerlo durante el tiempo que su SpatialInteractionSource correspondiente esté activo.  A continuación, cada fotograma, puede solicitarle el búfer de vértices más reciente que representa la mano llamando a [GetVertexStateForPose](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshobserver.getvertexstateforpose) y pasando una instancia de [HandPose](https://docs.microsoft.com//uwp/api/windows.perception.people.handpose) que representa el supuesto para el que desea los vértices.  Cada vértice del búfer tiene una posición y un normal.  Este es un ejemplo de cómo obtener el conjunto actual de vértices para una malla de mano.  Al igual que antes, la variable *CurrentState* representa una instancia de [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate).

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

A diferencia de las uniones de esqueleto, la API de malla de mano no permite especificar un sistema de coordenadas para los vértices.  En su lugar, [HandMeshVertexState](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshvertexstate) especifica el sistema de coordenadas en el que se proporcionan los vértices.  Después, puede obtener una transformación de malla llamando a [TryGetTransformTo](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem.trygettransformto#Windows_Perception_Spatial_SpatialCoordinateSystem_TryGetTransformTo_Windows_Perception_Spatial_SpatialCoordinateSystem_) y especificando el sistema de coordenadas deseado.  Tendrá que usar esta transformación de malla siempre que trabaje con los vértices.  Este enfoque reduce la sobrecarga de la CPU, especialmente si solo usa la malla para fines de representación.

## <a name="gaze-and-commit-composite-gestures"></a>Miras y confirmaciones de gestos compuestos
En el caso de las aplicaciones que usan el modelo de entrada de la opción de mira y confirmación, especialmente en HoloLens (First gen), la API de entrada espacial proporciona un [SpatialGestureRecognizer](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx) opcional que se puede usar para habilitar los gestos compuestos basados en el evento "Select".  Al enrutar las interacciones desde el SpatialInteractionManager al SpatialGestureRecognizer de un holograma, las aplicaciones pueden detectar los eventos de punteo, retención, manipulación y navegación uniformemente a través de los dispositivos de entrada de manos, voz y espaciales, sin tener que controlar las pulsaciones y las versiones de forma manual.

SpatialGestureRecognizer solo realiza la desambiguación mínima entre el conjunto de gestos que solicite. Por ejemplo, si solicita simplemente TAP, el usuario puede mantener el dedo hacia abajo siempre que quiera y se siga produciendo una pulsación. Si solicita el toque y el mantenimiento, después de que se mantenga presionado el dedo, el gesto promoverá a una suspensión y ya no se producirá una derivación.

Para usar SpatialGestureRecognizer, controle el evento [InteractionDetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) de SpatialInteractionManager y capte el SpatialPointerPose expuesto allí. Use el rayo principal del usuario de esta postura para formar una intersección con los hologramas y las mallas de superficie en el entorno del usuario, con el fin de determinar con qué está intentando interactuar el usuario. A continuación, enrute el SpatialInteraction de los argumentos de evento al SpatialGestureRecognizer del holograma de destino, mediante su método [CaptureInteraction](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) . Esto comienza a interpretar esa interacción según el valor de [SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings) establecido en el reconocedor en el momento de la creación, o en [TrySetGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings).

En HoloLens (primera generación), las interacciones y gestos generalmente deben derivar sus destinatarios del encabezado del usuario, en lugar de intentar representar o interactuar directamente en la ubicación de la mano. Una vez que se ha iniciado una interacción, se pueden usar movimientos relativos de la mano para controlar el gesto, al igual que con la manipulación o el gesto de navegación.

## <a name="see-also"></a>Consulte también
* [Control con la cabeza y los ojos de DirectX](gaze-in-directx.md)
* [Modelo de entrada de manipulación directa](direct-manipulation.md)
* [Modelo de entrada de punto y confirmación](point-and-commit.md)
* [Miran y confirman el modelo de entrada](gaze-and-commit.md)
* [Controladores de movimiento](motion-controllers.md)
