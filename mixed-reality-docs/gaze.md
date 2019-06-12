---
title: Mirada
description: Mirada es el primer formulario de entrada y un formulario principal de destino es en realidad mixta.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Mixed reality, mirada, interacción, diseñar
ms.openlocfilehash: e0c1a925f6faeb37ec35e511cef36f9c06672c8a
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829741"
---
# <a name="gaze"></a>Mirada

**Observación** es el primer formulario de entrada y es un formulario principal de destino es en realidad mixta. Mirada indica que el usuario está buscando en el mundo y permite determinar su intención. En el mundo real, normalmente obtendrá información en un objeto que se va a interactuar con. Esto es lo mismo con la mirada.

Auriculares de realidad mixta utilizar la posición y orientación de head del usuario para determinar su vector mirada principal. De este vector se puede considerar como un puntero láser recta desde directamente entre la vista del usuario. Como el usuario busca en torno a la sala de reuniones, la aplicación puede forman una intersección con este ray, con su propio hologramas tanto con el [asignación espacial](spatial-mapping.md) malla para determinar qué objeto reales o virtual que esté mirando el usuario.

En 2 HoloLens, interacciones mirada de principal del usuario, mirada ojo pueden tener como destino o a través de cerca o mucho entregar las interacciones.
En HoloLens (gen 1), por lo general deben derivar las interacciones de sus destinatarios de mirada principal del usuario, en lugar de intentar para representar o interactuar directamente en la ubicación de la mano. Una vez que se ha iniciado una interacción, movimientos relativos de la mano pueden utilizarse para controlar la [gesto](gestures.md), igual que con el [manipulación o navegación](gestures.md#composite-gestures) gesto. Con inmersivos, puede tener como destino con una mirada principal o señalando capaz [motion controladores](motion-controllers.md).

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
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (gen 1)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></td>
    </tr>
     <tr>
        <td>Mirada HEAD</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Mirada ojo</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

> [!NOTE]
> Obtener información más específica de HoloLens 2 [próximamente](index.md#news-and-notes).


## <a name="uses-of-gaze"></a>Usos de mirada

Como desarrollador de realidad mixta, puede hacer muchas cosas con mirada head u ojos:
* La aplicación puede intersectar mirada con el hologramas en su escena para determinar dónde se encuentra la atención del usuario.
* La aplicación puede tener como destino los gestos y pulsaciones de controlador según mirada del usuario, que permite que el usuario seleccione, activar, tomar, desplácese o interactuar con sus hologramas de otro modo.
* La aplicación puede permitir que el usuario coloque hologramas en superficies del mundo real, mediante la intersección de su ray mirada a la malla de asignación espacial.
* La aplicación puede saber cuando el usuario es *no* buscando en la dirección de un objeto importante, lo que puede provocar que la aplicación para proporcionar indicaciones visuales y de audio para activar hacia ese objeto.

## <a name="cursor"></a>Cursor

Para la mirada principal, debe usar la mayoría de las aplicaciones una [cursor](cursors.md) (u otra indicación visual de auditorio /) para proporcionar a la confianza de los usuarios en lo que va a interactuar con. Normalmente, se coloque este cursor en el mundo donde su ray mirada principal primero forma una intersección con un objeto, que puede ser un holograma o una superficie del mundo real.

![Un cursor visual de ejemplo para mostrar la mirada](images/cursor.jpg)<br>
*Un cursor visual de ejemplo para mostrar la mirada*

Para la mirada ojo, generalmente recomendamos *no* para mostrar un cursor, como esto puede volverse rápidamente que distraen y molesta para el usuario. En su lugar sutilmente resaltar destinos visuales o utilizar un cursor de ojos muy débil para proporcionar confiabilidad sobre cuál es el usuario a interactuar con. Para obtener más información, consulte nuestra [instrucciones de diseño para la entrada de ojo](eye-tracking.md) en HoloLens 2.

## <a name="giving-action-to-the-users-gaze"></a>Acción de la concesión en mirada del usuario

Una vez que el usuario destina un holograma o un objeto del mundo real mediante su mirada, su siguiente paso es realizar la acción en ese objeto. Las formas principales de un usuario para tomar medidas son a través de [gestos](gestures.md), [controladores de movimiento](motion-controllers.md) y [voz](voice-input.md).

## <a name="see-also"></a>Vea también
* [MR Input 210: Mirada HEAD](holograms-210.md)
* [Control con la cabeza y los ojos de DirectX](gaze-in-directx.md)
* [Mirada HEAD en Unity](gaze-in-unity.md)
* [Ojo de seguimiento en 2 HoloLens](eye-tracking.md)
* [Efecto de ojos mirada en Unity mediante el Kit de herramientas de realidad mixta](https://aka.ms/mrtk-eyes)
