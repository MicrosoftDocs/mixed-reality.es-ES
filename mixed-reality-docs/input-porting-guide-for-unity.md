---
title: Entrada de portabilidad de guía para Unity
description: Obtenga información sobre cómo controlar la entrada para Windows Mixed Reality en Unity.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Input, unity, portabilidad
ms.openlocfilehash: 20e8efa09d20b0a9eaa246015d9c185884f9c216
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59602788"
---
# <a name="input-porting-guide-for-unity"></a>Entrada de portabilidad de guía para Unity

Puede trasladar la lógica de entrada a Windows Mixed Reality mediante uno de estos dos enfoques, API Input.GetButton/GetAxis general de Unity que se distribuyen entre varias plataformas o el XR específicas de Windows. WSA. API de entrada que ofrecen datos enriquecidos específicamente para los controladores de movimiento y HoloLens manos.

## <a name="general-inputgetbuttongetaxis-apis"></a>API de Input.GetButton/GetAxis general

Unity usa actualmente sus API Input.GetButton/Input.GetAxis general para exponer la entrada [Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html) y [OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html). Si las aplicaciones ya usan estas API para la entrada, se trata de la ruta de acceso más fácil para la compatibilidad con controladores de movimiento en Windows Mixed Reality: que deba volver a asignar los botones y los ejes en el Administrador de entrada.

Para obtener más información, consulte el [tabla de asignación de botón o eje Unity](gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) y [información general de las API de Unity comunes](gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis).

## <a name="windows-specific-xrwsainput-apis"></a>XR específicos de Windows. WSA. API de entrada

Si ya basa en la aplicación lógica personalizada de entrada para cada plataforma, puede elegir usar las API de entrada espacial específicas de Windows bajo la **UnityEngine.XR.WSA.Input** espacio de nombres. Esto le permite tener acceso a información adicional, como la precisión de la posición o el tipo de origen, lo que le permite indicar a las manos y los controladores de distancia en HoloLens.

Para obtener más información, consulte el [información general de las APIs UnityEngine.XR.WSA.Input](gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput).

## <a name="grip-pose-vs-pointing-pose"></a>Postura de control frente a la postura señalador

Windows Mixed Reality es compatible con controladores de movimiento en una variedad de factores de forma, con el diseño de cada controlador que se diferencia en su relación entre la posición del usuario mano y natural "Reenviar" dirección de que las aplicaciones debe utilizar para que apunte al representar el controlador.

Para representar mejor estos controladores, hay dos tipos de plantea que puede investigar para cada origen de interacción:

* El **control postura**, que representa la ubicación de la palma de una mano detectada por un HoloLens, o bien la palma que contiene un controlador de movimiento.
    * En inmersivos, esta postura mejor se usa para representar **la mano del usuario** o **mantiene un objeto en la mano del usuario**, como una Espada o filo.
    * El **sujete posición**: El centroide de palm cuando se mantiene el controlador de forma natural, ajustar izquierda o derecha para centrar la posición dentro del control.
    * El **sujete eje derecho de orientación**: Cuando se abre completamente la mano para formar una postura plano 5-dedo, el rayo que es normal que la palma (hacia delante desde la palma de izquierdo, con versiones anteriores desde la palma derecha)
    * El **sujete eje hacia delante de orientación**: Cuando cierre la mano parcialmente (como si mantiene el controlador), el rayo que señala "forward" a través del tubo formado por los dedos no thumb.
    * El **sujete orientación de eje**: El eje vertical implicado en las definiciones de la derecha y hacia delante.
    * Puede tener acceso a la postura de control a través de la API de entrada de cualquier Unity entre proveedores (**[XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/Rotation**) o a través de la API de Windows específicos (**sourceState.sourcePose.TryGetPosition/Rotation**, que solicita la postura de control).
* El **puntero postura**, que representa la punta del controlador que señala hacia delante.
    * Esta postura está concebida para raycast cuando **apuntando a la interfaz de usuario** cuando está representando el propio modelo de controlador.
    * Actualmente, está disponible únicamente a través de la API de Windows específica la postura de puntero (**sourceState.sourcePose.TryGetPosition/Rotation**, que solicita la postura de puntero).

Estos postura las coordenadas se expresan en coordenadas universales de Unity.

## <a name="see-also"></a>Vea también
* [Controladores de movimiento](motion-controllers.md)
* [Los gestos y controladores de movimiento en Unity](gestures-and-motion-controllers-in-unity.md)
* [UnityEngine.XR.WSA.Input](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine.XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [Guías de migración](porting-guides.md)
