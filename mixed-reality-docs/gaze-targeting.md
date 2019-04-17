---
title: Mirada destinadas a
description: Todas las interacciones se basan en la capacidad de un usuario para el elemento que desean interactuar, independientemente de la modalidad de entrada de destino.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Mixto en realidad, mirada, mirada como destino, interacción, diseñar
ms.openlocfilehash: c3225e27331f8afcda65469eb84fe5470bf6ee8c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600678"
---
# <a name="gaze-targeting"></a>Mirada destinadas a

Todas las interacciones se basan en la capacidad de un usuario para el elemento que desean interactuar, independientemente de la modalidad de entrada de destino. En Windows Mixed Reality, por lo general esto se hace mediante la mirada del usuario.

Para que los usuarios puedan trabajar con una experiencia correctamente, debe alinear comprensión calculado del sistema de la intención del usuario y la intención del usuario real, como lo máximo posible. En la medida que el sistema interpreta las acciones del usuario previsto correctamente, aumenta la satisfacción y el rendimiento mejora.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Característica</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (gen 1)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td> Mirada destinadas a</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;">✔️ </td>
</tr><tr>
<td> Destinatarios de ojo</td><td style="text-align: center;"></td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

> [!NOTE]
> Obtener información más específica de HoloLens 2 [próximamente](index.md#news-and-notes).

## <a name="target-sizing-and-feedback"></a>Comentarios y ajuste de tamaño de destino

El vector mirada demostraron varias veces que se pueda usar para dirigirse a correcto, pero a menudo funciona mejor para brutos destinatarios (al adquirir un poco mayores destinos). Tamaños de destino mínimo de 1 a 1,5 grados deben permitir acciones de usuario correctamente en la mayoría de los escenarios, aunque los destinos de grados de 3 a menudo permiten mayor velocidad. Tenga en cuenta que el tamaño que los destinos de usuario es realmente un área 2D incluso para los elementos 3D--cualquier proyección está orientado a ellos debe ser el área de destino. Que proporciona alguna indicación más destacada que un elemento es "activo" (que el usuario está destinado a él) es extremadamente útil, esto puede incluir tratamientos como efectos visible "desplazar el puntero", información destacada de audio o hace clic en, o desactive la alineación de un cursor con un elemento.

![Tamaño de destino óptimo a distancia de medidor 2](images/gazetargeting-size-1000px.jpg)<br>
*Tamaño de destino óptimo a distancia de medidor 2*

![Un ejemplo de resaltado de un objeto de destino de mirada](images/gazetargeting-highlighting-640px.jpg)<br>
*Un ejemplo de resaltado de un objeto de destino de mirada*

## <a name="target-placement"></a>Selección de ubicación de destino

Los usuarios a menudo producirá un error buscar elementos de interfaz de usuario que se colocan muy alto o muy baja en su campo de visión, centrándose en la mayoría de su atención en las áreas en torno a su enfoque principal (normalmente más o menos el nivel de ojo). Puede ayudar colocar la mayoría de los destinos en algunos banda razonable en torno a nivel de los ojos. Dada la tendencia de los usuarios para centrarse en un área visual relativamente pequeña en cualquier momento (attentional cono de visión es aproximadamente 10 grados), agrupar los elementos de interfaz de usuario para el grado que están relacionadas conceptualmente puede aprovechar los comportamientos de encadenamiento de atención de un elemento a otro como un usuario se mueve a su mirada a través de un área. Al diseñar la interfaz de usuario, tenga en cuenta los posibles grandes variaciones en el campo de visión entre HoloLens e inmersivos.

![Un ejemplo de los elementos de interfaz de usuario agrupados para mirada más fácil seleccionar como destino en el Explorador de Galaxy](images/gazetargeting-grouping-1000px.jpg)<br>
*Un ejemplo de los elementos de interfaz de usuario agrupados para mirada más fácil seleccionar como destino en el Explorador de Galaxy*

## <a name="improving-targeting-behaviors"></a>Mejora de los comportamientos de destinatarios

Si intención del usuario para tener como destino algo puede ser determinado (o estrechamente de forma aproximada), puede ser muy útil aceptar intentos "near miss" en la interacción como si se destinen a correctamente. Hay una serie de métodos correctas que se pueden incorporar en las experiencias de realidad mixta:

### <a name="gaze-stabilization-gravity-wells"></a>Mirada estabilización ("wells gravedad")

Esto debe activarse la mayor parte o todo el tiempo. Esta técnica quita el a las vibraciones head/cuello natural que los usuarios pueden tener. También movimiento debido a los comportamientos de búsqueda de términos.

### <a name="closest-link-algorithms"></a>Algoritmos más cercano de vínculo

Estos funcionan mejor en áreas con dispersa contenido interactivo. Si hay una alta probabilidad de que puede determinar lo que un usuario intentó interactuar con, puede complementar sus capacidades de destinatarios, simplemente suponiendo cierto nivel de calidad.

### <a name="backdatingpostdating-actions"></a>Acciones backdating/postdating

Este mecanismo es útil en las tareas que requieren velocidad. Cuando un usuario está moviendo a través de una serie de maniobras/activación como destino a la velocidad, puede resultar útil supone algunos intención y permitir *perdió pasos* para actuar en los destinos que el usuario tenía foco ligeramente antes o ligeramente después el (tap) 50 ms antes o después estuvo en vigor en las primeras pruebas).

### <a name="smoothing"></a>Suavizado

Este mecanismo es útil para los movimientos de rutas, lo que reduce la vibración/oscilante pequeña debido a las características de movimiento natural. Cuando el suavizado de los movimientos de rutas, smooth por distancia/tamaño de los movimientos en lugar de con el tiempo

### <a name="magnetism"></a>Magnética

Este mecanismo puede considerarse como una versión más general de algoritmos de "Vínculo más cercano": dibujar un cursor hacia un destino, o simplemente incrementar hitboxes (ya sea visible o no) como destinos es probable que aproximan a los usuarios, uso de cierto conocimiento del diseño interactivo a intención del usuario de un mejor enfoque. Esto puede ser especialmente eficaz para los destinos pequeño.

### <a name="focus-stickiness"></a>Permanencia de foco

Al determinar qué cercanas a elementos interactivos para dar el foco a, proporcionar un sesgo en el elemento que se centra actualmente. Esto ayudará a reducir el enfoque errático conmutación comportamientos cuando flota en un punto medio entre dos elementos con ruido natural.

## <a name="see-also"></a>Vea también
* [Gestos](gestures.md)
* [Diseño de voz](voice-design.md)
* [Cursores](cursors.md)
