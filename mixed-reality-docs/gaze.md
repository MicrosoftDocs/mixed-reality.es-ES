---
title: Mirada
description: Mirada es el primer formulario de entrada y un formulario principal de destino es en realidad mixta.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Realidad mixta, mirada, interacción, diseñar
ms.openlocfilehash: 738ba9063a5d00f3bbedce989d93076d56ad1a44
ms.sourcegitcommit: 45676da11ebe33a2aa3dccec0e8ad7d714420853
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65629105"
---
# <a name="gaze"></a>Mirada

**Observación** es el primer formulario de entrada y es un formulario principal de destino es en realidad mixta. Mirada indica que el usuario está buscando en el mundo y permite determinar su intención. En el mundo real, normalmente obtendrá información en un objeto que se va a interactuar con. Esto es lo mismo con la mirada.

Auriculares de realidad mixta utilizar la posición y orientación de head del usuario para determinar su vector mirada principal. De este vector se puede considerar como un puntero láser recta desde directamente entre la vista del usuario. Como el usuario busca en torno a la sala de reuniones, la aplicación puede forman una intersección con este ray, con su propio hologramas tanto con el [asignación espacial](spatial-mapping.md) malla para determinar qué objeto reales o virtual que esté mirando el usuario.

En HoloLens 2, interacciones mirada principal del usuario pueden tener como destino o a través de cerca o mucho entregar las interacciones.  En HoloLens (gen 1), por lo general deben derivar las interacciones de sus destinatarios de mirada principal del usuario, en lugar de intentar para representar o interactuar directamente en la ubicación de la mano. Una vez que se ha iniciado una interacción, movimientos relativos de la mano pueden utilizarse para controlar la [gesto](gestures.md), igual que con el [manipulación o navegación](gestures.md#composite-gestures) gesto. Con inmersivos, puede tener como destino con una mirada o señalando capaz [motion controladores](motion-controllers.md).

<br>

>[!VIDEO https://www.youtube.com/embed/zCPiZlWdVws]

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Característica</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (gen 1)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td> Mirada HEAD</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr><tr>
<td> Mirada ojo</td><td></td><td style="text-align: center;">✔️</td><td></td>
</tr>
</table>

> [!NOTE]
> Obtener información más específica de HoloLens 2 [próximamente](index.md#news-and-notes).


## <a name="uses-of-gaze"></a>Usos de mirada

Como desarrollador de realidad mixta, puede hacer muchas cosas con mirada:
* La aplicación puede intersectar mirada con el hologramas en su escena para determinar dónde se encuentra la atención del usuario.
* La aplicación puede tener como destino los gestos y pulsaciones de controlador según mirada del usuario, que permite que el usuario seleccione, activar, tomar, desplácese o interactuar con sus hologramas de otro modo.
* La aplicación puede permitir que el usuario coloque hologramas en superficies del mundo real, mediante la intersección de su ray mirada a la malla de asignación espacial.
* La aplicación puede saber cuando el usuario es *no* buscando en la dirección de un objeto importante, lo que puede provocar que la aplicación para proporcionar indicaciones visuales y de audio para activar hacia ese objeto.

## <a name="cursor"></a>Cursor

La mayoría de las aplicaciones debe usar un [cursor](cursors.md) (u otra indicación visual de auditorio /) para proporcionar a la confianza de los usuarios en lo que va a interactuar con. Normalmente, se coloque este cursor en el mundo donde su mirada ray interactúa primero un objeto, que puede ser un holograma o una superficie del mundo real.

![Un cursor visual de ejemplo para mostrar la mirada](images/cursor.jpg)<br>
*Un cursor visual de ejemplo para mostrar la mirada*

## <a name="giving-action-to-the-users-gaze"></a>Acción de la concesión en mirada del usuario

Una vez que el usuario destina un holograma o un objeto del mundo real mediante su mirada, su siguiente paso es realizar la acción en ese objeto. Las formas principales de un usuario para tomar medidas son a través de [gestos](gestures.md), [controladores de movimiento](motion-controllers.md) y [voz](voice-input.md).

## <a name="see-also"></a>Vea también
* [MR Input 210: mirada](holograms-210.md)
* [Mirada principal y de ojo de DirectX](gaze-in-directx.md)
* [Mirada en Unity](gaze-in-unity.md)
