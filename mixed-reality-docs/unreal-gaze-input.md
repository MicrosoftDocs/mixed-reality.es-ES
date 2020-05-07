---
title: Mira fijamente inrealmente
description: Explica cómo usar la entrada de fijamente en el modo inreal.
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality, hologramas, HoloLens, seguimiento ocular
ms.openlocfilehash: 7387bb3f25cdbdfac32f508c173fbd098f844e84
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835633"
---
# <a name="gaze-input"></a>Entrada de mira

El complemento de Windows Mixed Reality no proporciona ninguna función especial para la entrada de mirada. Todo funciona a través de la API no real estándar.

[Cabezal mira API](https://docs.unrealengine.com/en-US/BlueprintAPI/Input/HeadMountedDisplay/index.html)

## <a name="eye-tracking"></a>Seguimiento de los ojos

Para usar la API de seguimiento ocular, los desarrolladores deben habilitar la funcionalidad de "entrada de Miración" en la configuración del proyecto de HoloLens. Cuando se inicia la aplicación, el usuario verá la siguiente solicitud de consentimiento.

![Permisos de entrada ocular](images/unreal/eye-input-permissions.png)
 
Si el usuario da su permiso, la aplicación recibirá una entrada de mirada. 

La API de seguimiento de ojos no real está documentada [aquí](https://docs.unrealengine.com/en-US/BlueprintAPI/EyeTracking/index.html)

[Aquí](eye-tracking.md) se muestran los detalles técnicos del seguimiento ocular

Tenga en cuenta que, en concreto, el seguimiento de la vista de HoloLens no es real con un solo rayo para ambos ojos. HoloLens no proporciona seguimiento Stereoscopic ocular.
