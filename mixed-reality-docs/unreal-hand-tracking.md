---
title: Seguimiento de manos en inreal
description: Explica cómo usar el seguimiento de manos en inreal
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, seguimiento de mano
ms.openlocfilehash: 3f7f4dd1eb62cb707eaaf8632a2ba3c280a4ac31
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835448"
---
# <a name="hand-tracking"></a>Seguimiento de mano

El sistema de seguimiento de mano usa las palmeras y los dedos de una persona como entrada en el mundo real. Un desarrollador puede obtener la posición y la rotación de cada dedo, toda la palma e incluso gestos de mano para usar en su propio código. 

## <a name="hand-pose"></a>Postura de mano

Mediante la pose de mano, los desarrolladores pueden realizar un seguimiento de las manos y los dedos del usuario activo como entrada. Este sistema se expone a través de Blueprints y C++. Los detalles técnicos se encuentran en la clase WinRT correspondiente [Windows. Perception. people. HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) esta API no real proporciona los datos en el formato del sistema de coordenadas no real y los tics se sincronizan con el motor inreal.

### <a name="enum"></a>Enum

EWMRHandKeypoint describe la jerarquía del hueso de la mano. 

Blueprint

![Mano keypoint BP](images/unreal/hand-keypoint-bp.png)
 
C++:
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

![Esqueleto manual](images/hand-skeleton.png)

Los valores numéricos se pueden encontrar en la tabla [Windows. Perception. people. HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind)
 
### <a name="functions"></a>Functions

Para usar las funciones de seguimiento de manos en blueprints, abra "seguimiento de manos/Windows Mixed Reality".

![Seguimiento de mano BP](images/unreal/hand-tracking-bp.png)

En el caso de las funciones de C++, incluya "WindowsMixedRealityHandTrackingFunctionLibrary. h"

BP

![Admite el seguimiento de manos BP](images/unreal/supports-hand-tracking-bp.png)
 
C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

Devuelve true si el seguimiento de mano es compatible con el dispositivo, false si el seguimiento de manos no está disponible.

BP

![Obtener transformación Unión a mano](images/unreal/get-hand-joint-transform.png)
 
C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

Esta función devuelve datos espaciales de la mano. Los datos se actualizan cada fotograma, dentro de un marco, los valores devueltos se almacenan en caché. No se recomienda tener una lógica pesada en esta función por motivos de rendimiento. 

* **Manos del** usuario, puede ser la izquierda o la derecha
* **Keypoint** : el hueso de la mano. 
* **Transformación** : coordenadas y orientación de la base del hueso. Para obtener los datos de transformación para el final de un hueso, se debe solicitar la base del siguiente hueso. Un hueso de la sugerencia especial proporciona el final de distal. 
* **Radio** : radio de la base del hueso.
* **Valor devuelto** : true si se realiza un seguimiento del hueso de este fotograma, false si no se realiza el seguimiento del hueso.

## <a name="hand-live-link-animation"></a>Animación de vínculo activo a mano
Los planteamientos de mano se exponen a la animación mediante el complemento de vínculo dinámico. La documentación del complemento está [aquí](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html)

Si los complementos de Windows Mixed Reality y Live Link están habilitados, vaya a la **ventana > vínculo dinámico** para abrir la ventana del editor de vínculos activos. Haga clic en el **botón + origen** y habilite el origen de seguimiento de la mano mixta de Windows

![Origen de vínculo activo](images/unreal/live-link-source.png)
 
Después de habilitar el origen y abrir cualquier recurso de animación, la pestaña vista previa de la escena de la animación tendrá las siguientes opciones adicionales (los detalles se encuentran en la documentación de Live link que no es real), ya que el complemento está en versión beta, el proceso puede cambiar más adelante.

![Animación de vínculos dinámicos](images/unreal/live-link-animation.png)
 
La jerarquía de animaciones a mano es la misma que en EWMRHandKeypoint. La animación se puede redestinar mediante WindowsMixedRealityHandTrackingLiveLinkRemapAsset. 

![Animación de vínculos en directo 2](images/unreal/live-link-animation2.png)
 
Se puede subclaser en el editor

![Reasignación de vínculos en directo](images/unreal/live-link-remap.png)
 
## <a name="hand-mesh"></a>Malla de mano
Malla que representa las manos del usuario. 

![Malla de mano](images/unreal/hand-mesh.png)
 
### <a name="how-to-enable-and-configure"></a>Cómo habilitar y configurar

Los desarrolladores pueden obtener acceso directo a las mallas manuales para sus propios fines. Este acceso debe estar habilitado en ARSessionConfig: configuración de AR-> asignación de mundo-> generar datos de malla a partir de la geometría sometida a seguimiento. 

Estos son los parámetros predeterminados para las mallas:

1.  Usar datos de malla para la oclusión
2.  Generar colisión para datos de malla
3.  Generar malla de navegación para datos de malla
4.  Representar datos de malla en el parámetro de trama: Debug que muestra la malla generada

En el caso de los proyectos de realidad mixta, estos valores de parámetro se usarán como malla de asignación espacial y valores predeterminados de malla de mano. Los desarrolladores pueden cambiarlos en BP o en el código de cualquier malla determinada.

### <a name="c-api-reference"></a>Referencia de la API de C++ 
```cpp
enum class EARObjectClassification : uint8
{
// other types 
    HandMesh,
};
```

Este valor es la malla de mano entre todos los objetos sometidos a seguimiento.

```cpp
class FARSupportInterface 
{
public:
// other params 
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

Se llama a estos delegados cuando el sistema detecta cualquier objeto sometido a seguimiento, incluida una malla de mano. 
```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```
Los controladores para los delegados deben tener la siguiente firma:
```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

Puede tener acceso a los datos de malla`UARTrackedGeometry::GetUnderlyingMesh`

### <a name="blueprint-api-reference"></a>Referencia de la API de Blueprint

Los desarrolladores deben agregar un componente de notificación supervisable AR a un actor Blueprint.

![Notificación de ARTrackable](images/unreal/ar-trackable-notify.png)
 
A continuación, vaya a los detalles del componente 

![ARTrackable notificar 2](images/unreal/ar-trackable-notify2.png)
 
Y sobrescriba en agregar, actualizar o quitar geometría sometida a seguimiento con código como el siguiente:

![On ARTrackable Notify](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a>Rayos de mano

Los desarrolladores pueden usar un rayo de mano como dispositivo señalador. El sistema está disponible en C++ y Blueprint. Técnicamente, expone [Windows. UI. Input. Spatial. SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose)

Es importante mencionar que, dado que los resultados de todas las funciones cambian cada fotograma, todos ellos se pueden llamar. Para obtener más información sobre las funciones puras e impuras o Invocables [, vea](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)

Para Blueprint, abra "Windows Mixed Reality HMD"

![Rayos de mano BP](images/unreal/hand-rays-bp.png)
 
Para C++, incluya "WindowsMixedRealityFunctionLibrary. h"

### <a name="enum"></a>Enum

![Botones del controlador de entrada](images/unreal/input-controller-buttons.png)
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```
* **Select** : evento de selección desencadenada por el usuario, que se puede desencadenar en HoloLens 2 por airtap o fijamente y commit. Otra manera de desencadenar este evento es decir "Select". 
* **Agarre** : evento de agarre desencadenado por el usuario, que se desencadena en HoloLens 2 cerrando los dedos del usuario en un holograma. 
```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```
* **NotTracked** : la mano no es visible
* **Seguimiento** : se realiza un seguimiento completo de la mano

### <a name="struct"></a>Estructura

![El puntero representa la información BP](images/unreal/pointer-pose-info-bp.png)
```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```
* **Origin** : origen de la mano
* **Dirección** : dirección de la mano
* **Vertical** : Vector de la mano
* **Orientación** : cuaternión de orientación 
* **Estado de seguimiento** : estado de seguimiento actual

### <a name="functions"></a>Functions

Todas las funciones deben ser Invocables en cada fotograma para una supervisión continua. 

![Obtener información de la repostura de puntero](images/unreal/get-pointer-pose-info.png)
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```
La función devuelve la información completa sobre la dirección del rayo en este marco. 

![Se ha captado BP](images/unreal/is-grasped-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
Devuelve true si la mano se capta en este marco. 

![Seleccione BP presionado](images/unreal/is-select-pressed-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```
Devuelve true si el usuario desencadenó SELECT en este marco.

![Clic en el botón BP](images/unreal/is-button-clicked-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```
Devuelve true si el evento/botón se desencadena en este marco.

![Obtiene el estado de seguimiento del controlador BP](images/unreal/get-controller-tracking-status-bp.png)
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
Devuelve el estado de seguimiento de este marco.

## <a name="gestures"></a>Gestos

Hololens 2 puede realizar el seguimiento de gestos espaciales. Los detalles sobre estos gestos están [aquí](https://docs.microsoft.com/hololens/hololens2-basic-usage) un desarrollador puede capturarlos como entrada para su aplicación de realidad mixta. 

La función de C++ está en "WindowsMixedRealitySpatialInputFunctionLibrary. h"

La función Blueprint está en entrada espacial de Windows Mixed Reality

![Capturar movimientos](images/unreal/capture-gestures.png)

### <a name="enum"></a>Enum

![Tipo de gesto](images/unreal/gesture-type.png)
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```
Esta enumeración describe los gestos del eje espacial. Puede leer sobre ellos [aquí](holograms-211.md)

### <a name="function"></a>Función

![Movimientos de captura BP](images/unreal/capture-gestures-bp.png)
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```
La función habilita y deshabilita la captura de gestos. Los gestos habilitados activan los eventos de entrada. Devuelve true si la habilitación de la captura de gestos se realizó correctamente y false si se produce un error.
Eventos clave

![Eventos clave](images/unreal/key-events.png)

![Eventos clave 2](images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```
Si el gesto está habilitado, los eventos inician la activación. 

