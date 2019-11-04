---
title: Mirada con la cabeza y confirmación
description: Introducción al modelo de entrada de mirada con la cabeza y confirmación
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Mixed Reality, gaze, gaze targeting, interaction, design
ms.openlocfilehash: 5fef778dde6852222e098aeb1cbb41fe04e0b744
ms.sourcegitcommit: a5dc182da237f63f0487d40a2e11894027208b6c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/02/2019
ms.locfileid: "73441091"
---
# <a name="head-gaze-and-commit"></a>Mirada con la cabeza y confirmación
_Encabezado y confirmación_ es un caso especial del modelo de entrada de [mira y de confirmación](gaze-and-commit.md) que implica el destino de un objeto con la dirección del encabezado hacia delante (dirección del encabezado) y, a continuación, la actuación con una entrada secundaria, como el movimiento de la mano. Pulse o el comando de voz "seleccionar". 

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Modelo de entrada</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Mirada con la cabeza y confirmación</td>
        <td>✔️ Se recomienda</td>
        <td>✔️ Recomendado (tercera opción: <a href="interaction-fundamentals.md">Ver las demás opciones</a>)</td>
        <td>➕ Opción alternativa</td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a>Ajuste de tamaño del destino y comentarios
El vector de miras hacia abajo se ha mostrado varias veces para que se pueda usar para lograr objetivos más precisos, pero a menudo funciona mejor para la segmentación bruta: adquisición de destinos algo más grandes. Los tamaños mínimos de destino de 1 a 1,5 grados permiten acciones de usuario correctas en la mayoría de los escenarios, aunque los destinos de 3 grados a menudo permiten una mayor velocidad. Tenga en cuenta que el tamaño que el usuario establece como destino es realmente un área 2D incluso para los elementos 3D (cualquier proyección de ellos debe ser un área potencial de destino). Proporcionar alguna indicación destacada de que un elemento está "activo" (que el usuario tiene como destino) es muy útil. Esto puede incluir tratamientos como efectos visibles de "mantener el mouse", resaltados de audio o clics o alineación clara de un cursor con un elemento.

![Tamaño de objetivo óptimo a una distancia de 2 metros](images/gazetargeting-size-1000px.jpg)<br>
*Tamaño de objetivo óptimo a una distancia de 2 metros*

<br>

![Ejemplo de resaltado de un objeto establecido como destino de la mirada](images/gazetargeting-highlighting-940px.jpg)<br>
*Ejemplo de resaltado de un objeto establecido como destino de la mirada*

## <a name="target-placement"></a>Situación del destino
A menudo, los usuarios no pueden encontrar los elementos de la interfaz de usuario que están colocados muy altos o muy bajos en su campo de vista, centrándose en la mayor parte de su atención en áreas en torno a su enfoque principal, que es aproximadamente en el nivel de ojo. Quizás resulte útil colocar la mayoría de los destinos en una banda razonable a la altura de los ojos. Dada la tendencia de los usuarios de centrarse en un área visual relativamente pequeña en todo momento (el cono de atención de la visión es de 10 grados aproximadamente), agrupar los elementos de la interfaz de usuario según su relación conceptual puede producir comportamientos de llamada de atención de un elemento a otro, ya que un usuario mueve su mirada dentro de un área. Al diseñar la interfaz de usuario, se deben tener en cuenta las posibles grandes variaciones en el campo de visión entre HoloLens y los cascos envolventes.

![Ejemplo de elementos de la interfaz de usuario agrupados para facilitar el establecimiento del destino con la mirada en Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)<br>
*Ejemplo de elementos de la interfaz de usuario agrupados para facilitar el establecimiento del destino con la mirada en Galaxy Explorer*

## <a name="improving-targeting-behaviors"></a>Mejora de los comportamientos de establecimiento de destino
Si la intención del usuario de destinar algo puede determinarse (o aproximarse de cerca), puede resultar muy útil aceptar los intentos de pérdida en la interacción como si estuviesen dirigidos correctamente. Estos son algunos de los métodos correctos que se pueden incorporar en experiencias de realidad mixta:

### <a name="head-gaze-stabilization-gravity-wells"></a>Estabilización de la mirada con la cabeza ("pozos de gravedad")
Esto se debe activar la mayoría o la totalidad del tiempo. Esta técnica elimina las vibraciones de cabeza natural y cuello que los usuarios podrían tener como movimiento debido a comportamientos de mirar y hablar.

### <a name="closest-link-algorithms"></a>Algoritmos de vínculo más cercano
Funcionan mejor en áreas con un contenido interactivo disperso. Si hay una probabilidad alta de que pueda determinar con qué un usuario estaba intentando interactuar, puede complementar sus capacidades de destino suponiendo cierto nivel de intento.

### <a name="backdating-and-postdating-actions"></a>Acciones de la
Este mecanismo es útil en las tareas que requieren velocidad. Cuando un usuario pasa por una serie de maniobras de destino y activación a velocidad, resulta útil asumir algún intento y permitir que los pasos perdidos actúen en los destinos en los que el usuario tenía el foco ligeramente antes o ligeramente después de la pulsación (50 ms antes/después era efectiva en EA pruebas de RLY).

### <a name="smoothing"></a>Suavizado
Este mecanismo es útil para los movimientos de las acciones, lo que reduce la ligera vibración y Wobble debido a las características de movimiento de cabeza natural. Al suavizar los movimientos de las acciones, smoothándose por el tamaño y la distancia de los movimientos en lugar de a lo largo del tiempo.

### <a name="magnetism"></a>Magnetismo
Este mecanismo puede considerarse como una versión más general de los algoritmos de vínculo más cercanos: dibujar un cursor hacia un destino o simplemente aumentar hitboxes, ya sea visible o no, a medida que los usuarios se aproximan a los objetivos probables mediante el uso de algún conocimiento del diseño interactivo para mejorar enfoque del intento del usuario. Esto puede resultar especialmente eficaz para destinos pequeños.

### <a name="focus-stickiness"></a>Permanencia del foco
Al determinar los elementos interactivos cercanos en los que se va a dar el foco, el ajuste de enfoque proporciona una inclinación al elemento que está enfocado actualmente. Esto ayuda a reducir los comportamientos de cambio de foco errático al flotar en un punto medio entre dos elementos con ruido natural.


## <a name="see-also"></a>Consulta también
* [Interacción basada en ojos](eye-gaze-interaction.md)
* [Mirada y permanencia](gaze-and-dwell.md)
* [Manipulación práctica directa](direct-manipulation.md)
* [Gestos prácticos](gaze-and-commit.md#composite-gestures)
* [Manos y confirmación](point-and-commit.md)
* [Interacciones instintivas](interaction-fundamentals.md)
* [Entrada de voz](voice-input.md)



