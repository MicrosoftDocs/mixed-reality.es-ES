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
# <a name="hand-tracking"></a><span data-ttu-id="732cb-104">Seguimiento de mano</span><span class="sxs-lookup"><span data-stu-id="732cb-104">Hand Tracking</span></span>

<span data-ttu-id="732cb-105">El sistema de seguimiento de mano usa las palmeras y los dedos de una persona como entrada en el mundo real.</span><span class="sxs-lookup"><span data-stu-id="732cb-105">The hand tracking system uses a person’s palms and fingers as input to Unreal.</span></span> <span data-ttu-id="732cb-106">Un desarrollador puede obtener la posición y la rotación de cada dedo, toda la palma e incluso gestos de mano para usar en su propio código.</span><span class="sxs-lookup"><span data-stu-id="732cb-106">A developer can get every finger’s position and rotation, the entire palm, and even hand gestures to use in their own code.</span></span> 

## <a name="hand-pose"></a><span data-ttu-id="732cb-107">Postura de mano</span><span class="sxs-lookup"><span data-stu-id="732cb-107">Hand Pose</span></span>

<span data-ttu-id="732cb-108">Mediante la pose de mano, los desarrolladores pueden realizar un seguimiento de las manos y los dedos del usuario activo como entrada.</span><span class="sxs-lookup"><span data-stu-id="732cb-108">Using the hand pose, developers can track the hands and fingers of the active user as input.</span></span> <span data-ttu-id="732cb-109">Este sistema se expone a través de Blueprints y C++.</span><span class="sxs-lookup"><span data-stu-id="732cb-109">This system is exposed through both Blueprints and C++.</span></span> <span data-ttu-id="732cb-110">Los detalles técnicos se encuentran en la clase WinRT correspondiente [Windows. Perception. people. HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) esta API no real proporciona los datos en el formato del sistema de coordenadas no real y los tics se sincronizan con el motor inreal.</span><span class="sxs-lookup"><span data-stu-id="732cb-110">Technical details are in the corresponding WinRT class [Windows.Perception.People.HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) This Unreal API provides the data in the format of Unreal’s coordinate system and ticks are synchronised with the Unreal Engine.</span></span>

### <a name="enum"></a><span data-ttu-id="732cb-111">Enum</span><span class="sxs-lookup"><span data-stu-id="732cb-111">Enum</span></span>

<span data-ttu-id="732cb-112">EWMRHandKeypoint describe la jerarquía del hueso de la mano.</span><span class="sxs-lookup"><span data-stu-id="732cb-112">EWMRHandKeypoint describes the Hand’s bone hierarchy.</span></span> 

<span data-ttu-id="732cb-113">Blueprint</span><span class="sxs-lookup"><span data-stu-id="732cb-113">Blueprint:</span></span>

![Mano keypoint BP](images/unreal/hand-keypoint-bp.png)
 
<span data-ttu-id="732cb-115">C++:</span><span class="sxs-lookup"><span data-stu-id="732cb-115">C++:</span></span>
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

<span data-ttu-id="732cb-117">Los valores numéricos se pueden encontrar en la tabla [Windows. Perception. people. HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind)</span><span class="sxs-lookup"><span data-stu-id="732cb-117">The numerical values can be found in the table [Windows.Perception.People.HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind)</span></span>
 
### <a name="functions"></a><span data-ttu-id="732cb-118">Functions</span><span class="sxs-lookup"><span data-stu-id="732cb-118">Functions</span></span>

<span data-ttu-id="732cb-119">Para usar las funciones de seguimiento de manos en blueprints, abra "seguimiento de manos/Windows Mixed Reality".</span><span class="sxs-lookup"><span data-stu-id="732cb-119">To use hand tracking functions in Blueprints, open "Hand Tracking/Windows Mixed Reality"</span></span>

![Seguimiento de mano BP](images/unreal/hand-tracking-bp.png)

<span data-ttu-id="732cb-121">En el caso de las funciones de C++, incluya "WindowsMixedRealityHandTrackingFunctionLibrary. h"</span><span class="sxs-lookup"><span data-stu-id="732cb-121">For C++ functions, include "WindowsMixedRealityHandTrackingFunctionLibrary.h"</span></span>

<span data-ttu-id="732cb-122">BP</span><span class="sxs-lookup"><span data-stu-id="732cb-122">BP:</span></span>

![Admite el seguimiento de manos BP](images/unreal/supports-hand-tracking-bp.png)
 
<span data-ttu-id="732cb-124">C++:</span><span class="sxs-lookup"><span data-stu-id="732cb-124">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

<span data-ttu-id="732cb-125">Devuelve true si el seguimiento de mano es compatible con el dispositivo, false si el seguimiento de manos no está disponible.</span><span class="sxs-lookup"><span data-stu-id="732cb-125">Returns true if hand tracking is supported on the device, false if hand tracking is not available.</span></span>

<span data-ttu-id="732cb-126">BP</span><span class="sxs-lookup"><span data-stu-id="732cb-126">BP:</span></span>

![Obtener transformación Unión a mano](images/unreal/get-hand-joint-transform.png)
 
<span data-ttu-id="732cb-128">C++:</span><span class="sxs-lookup"><span data-stu-id="732cb-128">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="732cb-129">Esta función devuelve datos espaciales de la mano.</span><span class="sxs-lookup"><span data-stu-id="732cb-129">This function returns spatial data of the hand.</span></span> <span data-ttu-id="732cb-130">Los datos se actualizan cada fotograma, dentro de un marco, los valores devueltos se almacenan en caché.</span><span class="sxs-lookup"><span data-stu-id="732cb-130">The data updates every frame, inside a frame the returned values are cached.</span></span> <span data-ttu-id="732cb-131">No se recomienda tener una lógica pesada en esta función por motivos de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="732cb-131">It is not recommended to have heavy logic on this function for performance reasons.</span></span> 

* <span data-ttu-id="732cb-132">**Manos del** usuario, puede ser la izquierda o la derecha</span><span class="sxs-lookup"><span data-stu-id="732cb-132">**Hand** – hand of the user, may be left or right</span></span>
* <span data-ttu-id="732cb-133">**Keypoint** : el hueso de la mano.</span><span class="sxs-lookup"><span data-stu-id="732cb-133">**Keypoint** – the bone of the hand.</span></span> 
* <span data-ttu-id="732cb-134">**Transformación** : coordenadas y orientación de la base del hueso.</span><span class="sxs-lookup"><span data-stu-id="732cb-134">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="732cb-135">Para obtener los datos de transformación para el final de un hueso, se debe solicitar la base del siguiente hueso.</span><span class="sxs-lookup"><span data-stu-id="732cb-135">To get the transform data for the end of a bone, the base of the next bone should be requested.</span></span> <span data-ttu-id="732cb-136">Un hueso de la sugerencia especial proporciona el final de distal.</span><span class="sxs-lookup"><span data-stu-id="732cb-136">A special Tip bone gives end of distal.</span></span> 
* <span data-ttu-id="732cb-137">**Radio** : radio de la base del hueso.</span><span class="sxs-lookup"><span data-stu-id="732cb-137">**Radius** — radius of the base of the bone.</span></span>
* <span data-ttu-id="732cb-138">**Valor devuelto** : true si se realiza un seguimiento del hueso de este fotograma, false si no se realiza el seguimiento del hueso.</span><span class="sxs-lookup"><span data-stu-id="732cb-138">**Return Value** — true if the bone is tracked this frame, false if the bone is not tracked.</span></span>

## <a name="hand-live-link-animation"></a><span data-ttu-id="732cb-139">Animación de vínculo activo a mano</span><span class="sxs-lookup"><span data-stu-id="732cb-139">Hand Live Link Animation</span></span>
<span data-ttu-id="732cb-140">Los planteamientos de mano se exponen a la animación mediante el complemento de vínculo dinámico.</span><span class="sxs-lookup"><span data-stu-id="732cb-140">Hand poses are exposed to Animation using the Live Link plugin.</span></span> <span data-ttu-id="732cb-141">La documentación del complemento está [aquí](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html)</span><span class="sxs-lookup"><span data-stu-id="732cb-141">The plugin documentation is [here](https://docs.unrealengine.com/en-US/Engine/Animation/LiveLinkPlugin/index.html)</span></span>

<span data-ttu-id="732cb-142">Si los complementos de Windows Mixed Reality y Live Link están habilitados, vaya a la **ventana > vínculo dinámico** para abrir la ventana del editor de vínculos activos.</span><span class="sxs-lookup"><span data-stu-id="732cb-142">If the Windows Mixed Reality and Live Link plugins are enabled, go to **Window > Live Link** to open the Live Link editor window.</span></span> <span data-ttu-id="732cb-143">Haga clic en el **botón + origen** y habilite el origen de seguimiento de la mano mixta de Windows</span><span class="sxs-lookup"><span data-stu-id="732cb-143">Click the **+ Source button** and enable Windows Mixed Reality Hand Tracking Source</span></span>

![Origen de vínculo activo](images/unreal/live-link-source.png)
 
<span data-ttu-id="732cb-145">Después de habilitar el origen y abrir cualquier recurso de animación, la pestaña vista previa de la escena de la animación tendrá las siguientes opciones adicionales (los detalles se encuentran en la documentación de Live link que no es real), ya que el complemento está en versión beta, el proceso puede cambiar más adelante.</span><span class="sxs-lookup"><span data-stu-id="732cb-145">After you enable the source and open any animation asset, the Preview Scene tab of Animation will have the following additional options (the details are in Unreal’s Live Link documentation- as the plugin is in beta, the process may change later)</span></span>

![Animación de vínculos dinámicos](images/unreal/live-link-animation.png)
 
<span data-ttu-id="732cb-147">La jerarquía de animaciones a mano es la misma que en EWMRHandKeypoint.</span><span class="sxs-lookup"><span data-stu-id="732cb-147">The hand animation hierarchy is the same as in EWMRHandKeypoint.</span></span> <span data-ttu-id="732cb-148">La animación se puede redestinar mediante WindowsMixedRealityHandTrackingLiveLinkRemapAsset.</span><span class="sxs-lookup"><span data-stu-id="732cb-148">Animation can be retargeted using WindowsMixedRealityHandTrackingLiveLinkRemapAsset.</span></span> 

![Animación de vínculos en directo 2](images/unreal/live-link-animation2.png)
 
<span data-ttu-id="732cb-150">Se puede subclaser en el editor</span><span class="sxs-lookup"><span data-stu-id="732cb-150">It can be subclassed in the editor</span></span>

![Reasignación de vínculos en directo](images/unreal/live-link-remap.png)
 
## <a name="hand-mesh"></a><span data-ttu-id="732cb-152">Malla de mano</span><span class="sxs-lookup"><span data-stu-id="732cb-152">Hand Mesh</span></span>
<span data-ttu-id="732cb-153">Malla que representa las manos del usuario.</span><span class="sxs-lookup"><span data-stu-id="732cb-153">Mesh representing the user hands.</span></span> 

![Malla de mano](images/unreal/hand-mesh.png)
 
### <a name="how-to-enable-and-configure"></a><span data-ttu-id="732cb-155">Cómo habilitar y configurar</span><span class="sxs-lookup"><span data-stu-id="732cb-155">How to enable and configure</span></span>

<span data-ttu-id="732cb-156">Los desarrolladores pueden obtener acceso directo a las mallas manuales para sus propios fines.</span><span class="sxs-lookup"><span data-stu-id="732cb-156">Developers can get direct access to hand meshes for their own purposes.</span></span> <span data-ttu-id="732cb-157">Este acceso debe estar habilitado en ARSessionConfig: configuración de AR-> asignación de mundo-> generar datos de malla a partir de la geometría sometida a seguimiento.</span><span class="sxs-lookup"><span data-stu-id="732cb-157">This access must be enabled in ARSessionConfig: AR Settings -> World Mapping -> Generate Mesh Data from Tracked Geometry.</span></span> 

<span data-ttu-id="732cb-158">Estos son los parámetros predeterminados para las mallas:</span><span class="sxs-lookup"><span data-stu-id="732cb-158">Here are the default parameters for meshes:</span></span>

1.  <span data-ttu-id="732cb-159">Usar datos de malla para la oclusión</span><span class="sxs-lookup"><span data-stu-id="732cb-159">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="732cb-160">Generar colisión para datos de malla</span><span class="sxs-lookup"><span data-stu-id="732cb-160">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="732cb-161">Generar malla de navegación para datos de malla</span><span class="sxs-lookup"><span data-stu-id="732cb-161">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="732cb-162">Representar datos de malla en el parámetro de trama: Debug que muestra la malla generada</span><span class="sxs-lookup"><span data-stu-id="732cb-162">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="732cb-163">En el caso de los proyectos de realidad mixta, estos valores de parámetro se usarán como malla de asignación espacial y valores predeterminados de malla de mano.</span><span class="sxs-lookup"><span data-stu-id="732cb-163">For mixed reality projects, these parameter values will be used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="732cb-164">Los desarrolladores pueden cambiarlos en BP o en el código de cualquier malla determinada.</span><span class="sxs-lookup"><span data-stu-id="732cb-164">Developers can change them in BP or code for any particular mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="732cb-165">Referencia de la API de C++</span><span class="sxs-lookup"><span data-stu-id="732cb-165">C++ API Reference</span></span> 
```cpp
enum class EARObjectClassification : uint8
{
// other types 
    HandMesh,
};
```

<span data-ttu-id="732cb-166">Este valor es la malla de mano entre todos los objetos sometidos a seguimiento.</span><span class="sxs-lookup"><span data-stu-id="732cb-166">This value is the hand mesh among all trackable objects.</span></span>

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

<span data-ttu-id="732cb-167">Se llama a estos delegados cuando el sistema detecta cualquier objeto sometido a seguimiento, incluida una malla de mano.</span><span class="sxs-lookup"><span data-stu-id="732cb-167">These delegates are called when the system detects any trackable object, including a hand mesh.</span></span> 
```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```
<span data-ttu-id="732cb-168">Los controladores para los delegados deben tener la siguiente firma:</span><span class="sxs-lookup"><span data-stu-id="732cb-168">Handlers to the delegates should have the following signature:</span></span>
```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

<span data-ttu-id="732cb-169">Puede tener acceso a los datos de malla`UARTrackedGeometry::GetUnderlyingMesh`</span><span class="sxs-lookup"><span data-stu-id="732cb-169">Mesh data can be accessed by `UARTrackedGeometry::GetUnderlyingMesh`</span></span>

### <a name="blueprint-api-reference"></a><span data-ttu-id="732cb-170">Referencia de la API de Blueprint</span><span class="sxs-lookup"><span data-stu-id="732cb-170">Blueprint API Reference</span></span>

<span data-ttu-id="732cb-171">Los desarrolladores deben agregar un componente de notificación supervisable AR a un actor Blueprint.</span><span class="sxs-lookup"><span data-stu-id="732cb-171">Developers should add an AR Trackable Notify Component to a Blueprint actor</span></span>

![Notificación de ARTrackable](images/unreal/ar-trackable-notify.png)
 
<span data-ttu-id="732cb-173">A continuación, vaya a los detalles del componente</span><span class="sxs-lookup"><span data-stu-id="732cb-173">Then go to the component’s details</span></span> 

![ARTrackable notificar 2](images/unreal/ar-trackable-notify2.png)
 
<span data-ttu-id="732cb-175">Y sobrescriba en agregar, actualizar o quitar geometría sometida a seguimiento con código como el siguiente:</span><span class="sxs-lookup"><span data-stu-id="732cb-175">And overwrite On Add/Update/Remove Tracked Geometry with code like the below:</span></span>

![On ARTrackable Notify](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a><span data-ttu-id="732cb-177">Rayos de mano</span><span class="sxs-lookup"><span data-stu-id="732cb-177">Hand Rays</span></span>

<span data-ttu-id="732cb-178">Los desarrolladores pueden usar un rayo de mano como dispositivo señalador.</span><span class="sxs-lookup"><span data-stu-id="732cb-178">Developers can use a hand ray as a pointing device.</span></span> <span data-ttu-id="732cb-179">El sistema está disponible en C++ y Blueprint.</span><span class="sxs-lookup"><span data-stu-id="732cb-179">The system is available in C++ and Blueprint.</span></span> <span data-ttu-id="732cb-180">Técnicamente, expone [Windows. UI. Input. Spatial. SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose)</span><span class="sxs-lookup"><span data-stu-id="732cb-180">Technically it exposes [Windows.UI.Input.Spatial.SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose)</span></span>

<span data-ttu-id="732cb-181">Es importante mencionar que, dado que los resultados de todas las funciones cambian cada fotograma, todos ellos se pueden llamar.</span><span class="sxs-lookup"><span data-stu-id="732cb-181">It’s important to mention that since the results of all the functions changes every frame, they are all made callable.</span></span> <span data-ttu-id="732cb-182">Para obtener más información sobre las funciones puras e impuras o Invocables [, vea](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)</span><span class="sxs-lookup"><span data-stu-id="732cb-182">For more information about pure vs impure or callable functions, see [that](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)</span></span>

<span data-ttu-id="732cb-183">Para Blueprint, abra "Windows Mixed Reality HMD"</span><span class="sxs-lookup"><span data-stu-id="732cb-183">For Blueprint open “Windows Mixed Reality HMD”</span></span>

![Rayos de mano BP](images/unreal/hand-rays-bp.png)
 
<span data-ttu-id="732cb-185">Para C++, incluya "WindowsMixedRealityFunctionLibrary. h"</span><span class="sxs-lookup"><span data-stu-id="732cb-185">For C++ include "WindowsMixedRealityFunctionLibrary.h"</span></span>

### <a name="enum"></a><span data-ttu-id="732cb-186">Enum</span><span class="sxs-lookup"><span data-stu-id="732cb-186">Enum</span></span>

![Botones del controlador de entrada](images/unreal/input-controller-buttons.png)
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```
* <span data-ttu-id="732cb-188">**Select** : evento de selección desencadenada por el usuario, que se puede desencadenar en HoloLens 2 por airtap o fijamente y commit.</span><span class="sxs-lookup"><span data-stu-id="732cb-188">**Select** -– User triggered Select event, which can be triggered in HoloLens 2 by airtap or gaze and commit.</span></span> <span data-ttu-id="732cb-189">Otra manera de desencadenar este evento es decir "Select".</span><span class="sxs-lookup"><span data-stu-id="732cb-189">Another way to trigger this event is to say “Select”.</span></span> 
* <span data-ttu-id="732cb-190">**Agarre** : evento de agarre desencadenado por el usuario, que se desencadena en HoloLens 2 cerrando los dedos del usuario en un holograma.</span><span class="sxs-lookup"><span data-stu-id="732cb-190">**Grasp** -– User triggered Grasp event, which is triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span> 
```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```
* <span data-ttu-id="732cb-191">**NotTracked** : la mano no es visible</span><span class="sxs-lookup"><span data-stu-id="732cb-191">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="732cb-192">**Seguimiento** : se realiza un seguimiento completo de la mano</span><span class="sxs-lookup"><span data-stu-id="732cb-192">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="732cb-193">Estructura</span><span class="sxs-lookup"><span data-stu-id="732cb-193">Struct</span></span>

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
* <span data-ttu-id="732cb-195">**Origin** : origen de la mano</span><span class="sxs-lookup"><span data-stu-id="732cb-195">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="732cb-196">**Dirección** : dirección de la mano</span><span class="sxs-lookup"><span data-stu-id="732cb-196">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="732cb-197">**Vertical** : Vector de la mano</span><span class="sxs-lookup"><span data-stu-id="732cb-197">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="732cb-198">**Orientación** : cuaternión de orientación</span><span class="sxs-lookup"><span data-stu-id="732cb-198">**Orientation** – orientation quaternion</span></span> 
* <span data-ttu-id="732cb-199">**Estado de seguimiento** : estado de seguimiento actual</span><span class="sxs-lookup"><span data-stu-id="732cb-199">**Tracking Status** – current tracking status</span></span>

### <a name="functions"></a><span data-ttu-id="732cb-200">Functions</span><span class="sxs-lookup"><span data-stu-id="732cb-200">Functions</span></span>

<span data-ttu-id="732cb-201">Todas las funciones deben ser Invocables en cada fotograma para una supervisión continua.</span><span class="sxs-lookup"><span data-stu-id="732cb-201">All the functions should be callable on every frame for continuous monitoring.</span></span> 

![Obtener información de la repostura de puntero](images/unreal/get-pointer-pose-info.png)
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```
<span data-ttu-id="732cb-203">La función devuelve la información completa sobre la dirección del rayo en este marco.</span><span class="sxs-lookup"><span data-stu-id="732cb-203">The function returns the full information about the hand ray direction in this frame.</span></span> 

![Se ha captado BP](images/unreal/is-grasped-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
<span data-ttu-id="732cb-205">Devuelve true si la mano se capta en este marco.</span><span class="sxs-lookup"><span data-stu-id="732cb-205">Returns true if the hand is grasped in this frame.</span></span> 

![Seleccione BP presionado](images/unreal/is-select-pressed-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```
<span data-ttu-id="732cb-207">Devuelve true si el usuario desencadenó SELECT en este marco.</span><span class="sxs-lookup"><span data-stu-id="732cb-207">Returns true if the user triggered Select in this frame.</span></span>

![Clic en el botón BP](images/unreal/is-button-clicked-bp.png)
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```
<span data-ttu-id="732cb-209">Devuelve true si el evento/botón se desencadena en este marco.</span><span class="sxs-lookup"><span data-stu-id="732cb-209">Returns true if the event/button is triggered in this frame.</span></span>

![Obtiene el estado de seguimiento del controlador BP](images/unreal/get-controller-tracking-status-bp.png)
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
<span data-ttu-id="732cb-211">Devuelve el estado de seguimiento de este marco.</span><span class="sxs-lookup"><span data-stu-id="732cb-211">Returns the tracking status in this frame.</span></span>

## <a name="gestures"></a><span data-ttu-id="732cb-212">Gestos</span><span class="sxs-lookup"><span data-stu-id="732cb-212">Gestures</span></span>

<span data-ttu-id="732cb-213">Hololens 2 puede realizar el seguimiento de gestos espaciales.</span><span class="sxs-lookup"><span data-stu-id="732cb-213">The Hololens 2 can track spatial gestures.</span></span> <span data-ttu-id="732cb-214">Los detalles sobre estos gestos están [aquí](https://docs.microsoft.com/hololens/hololens2-basic-usage) un desarrollador puede capturarlos como entrada para su aplicación de realidad mixta.</span><span class="sxs-lookup"><span data-stu-id="732cb-214">Details about these gestures are [here](https://docs.microsoft.com/hololens/hololens2-basic-usage) A developer can capture them as input to their mixed reality application.</span></span> 

<span data-ttu-id="732cb-215">La función de C++ está en "WindowsMixedRealitySpatialInputFunctionLibrary. h"</span><span class="sxs-lookup"><span data-stu-id="732cb-215">The C++ function is in "WindowsMixedRealitySpatialInputFunctionLibrary.h"</span></span>

<span data-ttu-id="732cb-216">La función Blueprint está en entrada espacial de Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="732cb-216">The Blueprint function is in Windows Mixed Reality Spatial Input</span></span>

![Capturar movimientos](images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="732cb-218">Enum</span><span class="sxs-lookup"><span data-stu-id="732cb-218">Enum</span></span>

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
<span data-ttu-id="732cb-220">Esta enumeración describe los gestos del eje espacial.</span><span class="sxs-lookup"><span data-stu-id="732cb-220">This enum describes spatial axis gestures.</span></span> <span data-ttu-id="732cb-221">Puede leer sobre ellos [aquí](holograms-211.md)</span><span class="sxs-lookup"><span data-stu-id="732cb-221">You can read about them [here](holograms-211.md)</span></span>

### <a name="function"></a><span data-ttu-id="732cb-222">Función</span><span class="sxs-lookup"><span data-stu-id="732cb-222">Function</span></span>

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
<span data-ttu-id="732cb-224">La función habilita y deshabilita la captura de gestos.</span><span class="sxs-lookup"><span data-stu-id="732cb-224">The function enables and disables capturing of gestures.</span></span> <span data-ttu-id="732cb-225">Los gestos habilitados activan los eventos de entrada.</span><span class="sxs-lookup"><span data-stu-id="732cb-225">The enabled gestures fire input events.</span></span> <span data-ttu-id="732cb-226">Devuelve true si la habilitación de la captura de gestos se realizó correctamente y false si se produce un error.</span><span class="sxs-lookup"><span data-stu-id="732cb-226">It returns true if enabling gesture capture succeeded and false if there's an error.</span></span>
<span data-ttu-id="732cb-227">Eventos clave</span><span class="sxs-lookup"><span data-stu-id="732cb-227">Key Events</span></span>

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
<span data-ttu-id="732cb-230">Si el gesto está habilitado, los eventos inician la activación.</span><span class="sxs-lookup"><span data-stu-id="732cb-230">If the gesture is enabled, the events begin firing.</span></span> 

