---
title: Guía de portabilidad de entrada para Unity
description: Obtenga información sobre cómo controlar la entrada de Windows Mixed Reality en Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: entrada, Unity, portabilidad
ms.openlocfilehash: 20e8efa09d20b0a9eaa246015d9c185884f9c216
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63515495"
---
# <a name="input-porting-guide-for-unity"></a>Guía de portabilidad de entrada para Unity

Puede trasladar la lógica de entrada a Windows Mixed Reality mediante uno de estos dos enfoques: la entrada general de Unity. GetButton/GetAxis API que abarcan varias plataformas, o el XR específico de Windows. WSA. API de entrada que ofrecen datos más completos específicamente para los controladores de movimiento y las manos de HoloLens.

## <a name="general-inputgetbuttongetaxis-apis"></a>API de entrada general. GetButton/GetAxis

Unity usa actualmente sus API de entrada general. GetButton/Input. GetAxis para exponer la entrada para [el SDK de Oculus](https://docs.unity3d.com/Manual/OculusControllers.html) y [el SDK de OpenVR](https://docs.unity3d.com/Manual/OpenVRControllers.html). Si las aplicaciones ya usan estas API para la entrada, esta es la ruta más sencilla para admitir controladores de movimiento en Windows Mixed Reality: solo debe reasignar botones y ejes en el administrador de entrada.

Para obtener más información, consulte la [tabla de asignación de ejes y botones de Unity](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) y la [información general de las API comunes de Unity](gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis).

## <a name="windows-specific-xrwsainput-apis"></a>XR específico de Windows. WSA. API de entrada

Si la aplicación ya compila la lógica de entrada personalizada para cada plataforma, puede optar por usar las API de entrada espacial específicas de Windows en el espacio de nombres **UnityEngine. XR. WSA. Input** . Esto le permite tener acceso a información adicional, como la precisión de la posición o el tipo de origen, lo que permite indicar a las manos y controladores de HoloLens.

Para obtener más información, vea la información [General de las API de UnityEngine. XR. WSA. Input](gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput).

## <a name="grip-pose-vs-pointing-pose"></a>Replanteamiento de control frente a pose de puntero

Windows Mixed Reality admite controladores de movimiento en diversos factores de forma, con el diseño de cada controlador diferente en su relación entre la posición del usuario y la dirección de "avance" natural que deben usar las aplicaciones para apuntar al representar el módem.

Para representar mejor estos controladores, hay dos tipos de supuestos que puede investigar para cada origen de interacción:

* La representación del **control**, que representa la ubicación de la palma de una mano detectada por un HoloLens o la palma que contiene un controlador de movimiento.
    * En los auriculares más envolventes, este planteamiento se usa mejor para presentar **la mano del usuario** o **un objeto mantenido en la mano del usuario**, como un arma o una pistola.
    * La **posición del puño**: La palma de centroide cuando mantiene el controlador de forma natural, se ajusta a la izquierda o a la derecha para centrar la posición dentro del control.
    * **Eje derecho de la orientación del puño**: Cuando abre por completo la mano para formar una postura plana de 5 dedos, el rayo perpendicular a la palma (hacia delante de la mano izquierda, hacia atrás desde la mano derecha)
    * **Eje hacia delante de la orientación del puño**: Cuando cierre parcialmente la mano (como si contiene el controlador), el rayo que señala "reenviar" a través del tubo formado por los dedos no Thumb.
    * **Eje hacia arriba de la orientación del puño**: El eje hacia arriba implícito por las definiciones derecha y hacia delante.
    * Puede acceder a la representación del puño a través de la API de entrada entre proveedores (XR) de Unity **[. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation**) o a través de la API específica de Windows (**SourceState. SourcePose. TryGetPosition/Rotation**, que solicita la pose de control).
* Representación del **puntero**que representa la punta del controlador que señala hacia delante.
    * Esta representación se usa mejor para Raycast cuando se **señala a la interfaz de usuario** cuando se representa el propio modelo del controlador.
    * Actualmente, la pose de puntero solo está disponible a través de la API específica de Windows (**sourceState. sourcePose. TryGetPosition/Rotation**, lo que solicita la pose de puntero).

Estas coordenadas de pose se expresan en coordenadas universales de Unity.

## <a name="see-also"></a>Vea también
* [Controladores de movimiento](motion-controllers.md)
* [Gestos y controladores de movimiento en Unity](gestures-and-motion-controllers-in-unity.md)
* [UnityEngine. XR. WSA. Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Guías de portabilidad](porting-guides.md)
