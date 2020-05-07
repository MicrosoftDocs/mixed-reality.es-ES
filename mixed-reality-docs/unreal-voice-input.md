---
title: Entrada de voz
description: Explica cómo usar la entrada de voz
author: AndreyChistyakov
ms.author: anchisty
ms.date: 04/08/2020
ms.topic: article
keywords: Windows Mixed Reality, HoloLens
ms.openlocfilehash: d61a9f9d40c76c8872ff0a1b39d65f95ae88d2b7
ms.sourcegitcommit: ba4c8c2a19bd6a9a181b2cec3cb8e0402f8cac62
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82835331"
---
# <a name="voice-input"></a>Entrada de voz

Para habilitar el reconocimiento de voz en HoloLens, el desarrollador debe habilitar "micrófono" en el editor desareal en configuración del proyecto > Platform > HoloLens > funcionalidades. El dispositivo también debe tener habilitado el reconocimiento de voz en configuración > privacidad > voz y usar el idioma inglés.

![Configuración del reconocimiento de voz de Windows](images/unreal/speech-recognition-settings.png)

Se recomienda habilitar también el reconocimiento de voz en línea para obtener la mejor calidad posible del servicio. [Aquí](voice-input.md) encontrará detalles técnicos para el reconocimiento de voz en HoloLens

Después, el usuario verá un cuadro de diálogo que le permitirá habilitar el micrófono cuando se inicie la aplicación por primera vez. Si un usuario selecciona Sí, la aplicación comenzará a obtener entrada de voz.

La entrada de voz no requiere una API especial de Windows Mixed Reality y, en su lugar, se basa en la API de asignación de entrada de Engine 4 existente. [Aquí](https://docs.unrealengine.com/en-US/Gameplay/Input/index.html) encontrará información detallada sobre cómo usar la API de entrada

Se han agregado las asignaciones de voz a la sección de enlaces de la entrada del motor, que se encuentra debajo de las asignaciones de acciones y ejes. 

![Información de entrada del motor de UE4](images/unreal/engine-input.png)
 
Este es un ejemplo de supervisión agregada para el mundo "salto". Se puede usar cualquier palabra o frase en inglés. 

Después de agregar una asignación de voz a través de la configuración del proyecto, un desarrollador puede usar la lógica no real estándar para controlar la entrada, como en el ejemplo siguiente: 
 
![Acción simple para voz](images/unreal/input-action-bp.png)
