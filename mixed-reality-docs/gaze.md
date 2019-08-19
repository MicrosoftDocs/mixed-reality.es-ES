---
title: Mirada
description: Miramos la primera forma de entrada y es una forma principal de establecer como destino dentro de la realidad mixta.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Realidad mixta, mira, interacción, diseño
ms.openlocfilehash: 7e65d26d3e9edabbd01d35a887ffc8622a3c6337
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414367"
---
# <a name="gaze"></a>Mirada

**Miramos** la primera forma de entrada y es una forma principal de establecer como destino dentro de la realidad mixta. Le indica dónde está buscando el usuario en el mundo y le permite determinar su intención. En el mundo real, normalmente observará un objeto con el que desea interactuar. Este es el mismo con miras.

Los auriculares de realidad mixta usan la posición y la orientación del encabezado del usuario para determinar su vector de miras hacia abajo. Puede considerar este vector como un puntero láser directo directamente desde los ojos del usuario. A medida que el usuario mira el salón, la aplicación puede crear una intersección con este rayo, tanto con sus propios hologramas como con la malla de [asignación espacial](spatial-mapping.md) , para determinar qué objeto virtual o del mundo real puede estar mirando el usuario.

En HoloLens 2, las interacciones pueden tener como destino las interacciones de la cabeza del usuario, el ojo o la intersección de la mano.
En HoloLens (1ª generación), las interacciones generalmente deben derivar sus destinatarios del encabezado del usuario, en lugar de intentar representarlas o interactuar directamente en la ubicación de la mano. Una vez que se ha iniciado una interacción, se pueden usar movimientos relativos de la mano para controlar el [gesto](gestures.md), al igual que con la [manipulación o](gestures.md#composite-gestures) el gesto de navegación. Con auriculares envolventes, puede dirigirse a través de [los controladores de movimiento](motion-controllers.md)de mira hacia abajo o con capacidad de puntero.

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Característica</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Mira hacia abajo</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Ojo mirado</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

> [!NOTE]
> [Próximamente](index.md#news-and-notes) se ofrecerá orientación específica para HoloLens 2.


## <a name="uses-of-gaze"></a>Usos de fijamente

Como desarrollador de realidad mixta, puede hacer muchas cosas con miras hacia arriba o hacia abajo:
* La aplicación puede intersectar con los hologramas de la escena para determinar dónde está la atención del usuario.
* La aplicación puede tener como destino gestos y pulsaciones del controlador en función de la mirada del usuario, lo que permite que el usuario seleccione, active, grabe, desplace o interactúe con sus hologramas.
* La aplicación puede permitir que el usuario coloque hologramas en superficies del mundo real, intersectando su rayo con la malla de asignación espacial.
* La aplicación puede saber si el usuario *no* está buscando la dirección de un objeto importante, lo que puede conducir a que la aplicación proporcione indicaciones visuales y de audio para activar dicho objeto.

## <a name="cursor"></a>Cursor

En el caso de la mirada, la mayoría de las aplicaciones deben usar un [cursor](cursors.md) (u otra indicación visual o de auditoría) para dar a la confianza del usuario en qué está a punto de interactuar. Normalmente, este cursor se coloca en el mundo en el que su rayo de miras hacia abajo intersecta primero con un objeto, que puede ser un holograma o una superficie del mundo real.

![Un cursor visual de ejemplo para mostrar la mirada](images/cursor.jpg)<br>
*Un cursor visual de ejemplo para mostrar la mirada*

En general, se recomienda *no* mostrar un cursor, ya que esto puede resultar más rápido y molesto para el usuario. En su lugar, resalte los destinos visuales de forma sutilmente o use un cursor de ojo muy débil para proporcionar confianza sobre lo que el usuario está a punto de interactuar. Para obtener más información, consulte nuestra [Guía de diseño para la entrada basada en ojo](eye-tracking.md) en HoloLens 2.

## <a name="giving-action-to-the-users-gaze"></a>Realizar una acción en la mirada del usuario

Una vez que el usuario ha dirigido un holograma o un objeto del mundo real con su mirada, el siguiente paso es tomar medidas en ese objeto. Las principales formas de que un usuario tome medidas a través de [gestos](gestures.md), [controladores de movimiento](motion-controllers.md) y [voz](voice-input.md).

## <a name="see-also"></a>Vea también
* [MR Input 210: Mira hacia abajo](holograms-210.md)
* [Control con la cabeza y los ojos de DirectX](gaze-in-directx.md)
* [Mira hacia abajo en Unity](gaze-in-unity.md)
* [Miras a la vista de HoloLens 2](eye-tracking.md)
* [Mira fijamente en Unity con el kit de herramientas de realidad mixta](https://aka.ms/mrtk-eyes)
