---
title: Destinar la mirada
description: Todas las interacciones se basan en la capacidad de un usuario de establecer como destino el elemento con el que desea interactuar, independientemente de la modalidad de entrada.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Realidad mixta, Miración de miración, interacción, diseño
ms.openlocfilehash: eddc832456b2ba0c6bc8955157d2c8e1a268e893
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829839"
---
# <a name="gaze-and-dwell"></a>Mira fijamente y viviendas
Hay muchas maneras de confirmar una _confirmación_ como la combinación de gestos de _voz_ o de _mano_.
Sin embargo, hay varios escenarios de usuario, en los que las manos de los usuarios pueden estar ocupadas o no se puede realizar su seguimiento (por ejemplo, los trabajadores de la factoría con guantes de aranceles elevados). También es posible que la entrada de voz no esté disponible debido a las preferencias del usuario, el contexto social o los entornos de alto volumen.
Como solución de reserva, otra opción para realizar una _confirmación_ es simplemente seguir el tiempo en un elemento de la interfaz de usuario al que se hace referencia como _vivienda_.
Una _vivienda_ puede realizarse con la mirada hacia arriba o hacia abajo. La idea es sencilla y se puede desglosar en las siguientes fases: 
1. El usuario inicia Gazing en un botón holográfica

2. Después de un breve retraso de inicio (por ejemplo, 150 ms), se inicia una animación de comentarios visuales. El retraso de la aparición se usa para evitar abrumar al usuario mediante la acumulación inmediata de comentarios en todo momento.
    - En el _ojo_de la mirada, recomendamos lo siguiente para el diseño de los comentarios de la vivienda visual:
      - **Blend**: Mezcle sin problemas en los comentarios desde apenas visible al principio hasta totalmente opaco. Esto hace que los comentarios menos distraigan y overwhleming y se alineen perfectamente con la confianza de que el sistema tiene que el usuario realmente desea interactuar con este botón.
      - **Extráigalo en**: Cree un comentario visual que disminuya de tamaño y se desplace hacia el centro del destino, lo que permite obtener la atención visual del usuario. 

3. Después de una duración de permanencia predefinida (por ejemplo, 800 MS), se completa la permanencia y se desencadena un evento asociado.
    - Proporcione algunas finalización de la auditoría o los comentarios visuales para traer realmente su hogar que el elemento ha seleccionado ahora.

![Estados de permanencia](images/eyes_dwellstate_recommendation.png)


# <a name="gaze-targeting"></a>Destinar la mirada

Todas las interacciones se basan en la capacidad de un usuario de establecer como destino el elemento con el que desea interactuar, independientemente de la modalidad de entrada. En Windows Mixed Reality, esto se hace mediante la mirada del usuario por lo general.

Para que los usuarios puedan trabajar con una experiencia correctamente, la comprensión de la intención del usuario calculada por el sistema y la intención real del usuario deben estar lo más alineadas como sea posible. En la medida que el sistema interpreta las intenciones del usuario correctamente, la satisfacción aumenta y el rendimiento mejora.

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
        <td>Destinar la mirada</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Destino de los ojos</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

> [!NOTE]
> [Próximamente](index.md) se ofrecerá orientación específica para HoloLens 2.

## <a name="target-sizing-and-feedback"></a>Ajuste de tamaño del destino y comentarios

Se ha demostrado repetidamente que el vector de mirada se puede usar para establecer el destino de forma precisa, pero suele funcionar mejor para destinos de mayor tamaño (adquisición de destinos algo mayores). Los destinos con un tamaño mínimo de entre 1 y 1,5 grados deberían permitir acciones de usuario correctas en la mayoría de los escenarios, aunque los destinos de 3 grados suelen permitir mayor velocidad. Tenga en cuenta que el tamaño que el usuario establece como destino es realmente un área 2D incluso para los elementos 3D (cualquier proyección de ellos debe ser un área potencial de destino). Resulta muy útil proporcionar alguna indicación destacada de que un elemento está "activo" (que el usuario lo está estableciendo como destino). Esto puede incluir tratamientos como los efectos visibles de "mantener el puntero", señales auditivas o clics, o la alineación clara de un cursor con un elemento.

![Tamaño de destino óptimo a una distancia de 2 metros](images/gazetargeting-size-1000px.jpg)<br>
*Tamaño de objetivo óptimo a una distancia de 2 metros*

![Ejemplo de resaltado de un objeto establecido como destino de la mirada](images/gazetargeting-highlighting-640px.jpg)<br>
*Ejemplo de resaltado de un objeto establecido como destino de la mirada*

## <a name="target-placement"></a>Situación del destino

Con frecuencia, los usuarios no podrán encontrar elementos de la interfaz de usuario que estén situados muy arriba o muy abajo en su campo de visión, y centrarán la mayoría de su atención en las áreas en torno al foco principal (normalmente al nivel de los ojos aproximadamente). Quizás resulte útil colocar la mayoría de los destinos en una banda razonable a la altura de los ojos. Dada la tendencia de los usuarios de centrarse en un área visual relativamente pequeña en todo momento (el cono de atención de la visión es de 10 grados aproximadamente), agrupar los elementos de la interfaz de usuario según su relación conceptual puede producir comportamientos de llamada de atención de un elemento a otro, ya que un usuario mueve su mirada dentro de un área. Al diseñar la interfaz de usuario, se deben tener en cuenta las posibles grandes variaciones en el campo de visión entre HoloLens y los cascos envolventes.

![Ejemplo de elementos de la interfaz de usuario agrupados para facilitar el establecimiento del destino con la mirada en Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)<br>
*Ejemplo de elementos de la interfaz de usuario agrupados para facilitar el establecimiento del destino con la mirada en Galaxy Explorer*

## <a name="improving-targeting-behaviors"></a>Mejora de los comportamientos de establecimiento de destino

Si se puede determinar (o aproximar) la intención del usuario de establecer algo como destino, puede ser muy útil aceptar intentos "casi incorrectos" en la interacción como si se hubiesen establecido correctamente. Hay una serie de métodos correctos que se pueden incorporar en las experiencias de realidad mixta:

### <a name="gaze-stabilization-gravity-wells"></a>Estabilización de la mirada ("pocillos de gravedad")

Debería estar activada la mayor parte o todo el tiempo. Esta técnica elimina las vibraciones naturales del cuello o la cabeza que los usuarios puedan tener. También existe un movimiento debido a los comportamientos de la mirada o el habla.

### <a name="closest-link-algorithms"></a>Algoritmos de vínculo más cercano

Funcionan mejor en áreas con un contenido interactivo disperso. Si hay una alta probabilidad de poder determinar con qué intentaba interactuar un usuario, sus habilidades de establecimiento de destino se pueden complementar simplemente suponiendo cierto nivel de intención.

### <a name="backdatingpostdating-actions"></a>Anticipar y posponer acciones

Este mecanismo es útil en las tareas que requieren velocidad. Cuando un usuario está pasando por una serie de maniobras de destino y activación a velocidad, puede ser útil asumir algún intento y permitir que *los pasos perdidos* actúen en los destinos en los que el usuario tenía el foco ligeramente antes o ligeramente después de la pulsación (50 ms antes/después). eficaz en las primeras pruebas).

### <a name="smoothing"></a>Suavizado

Este mecanismo es útil para el trazado de movimientos y reduce la vibración u oscilación debidas a las características de los movimientos naturales de la cabeza. En el suavizado del trazado de movimientos, se debe realizar un suavizado en función del tamaño o la distancia de los movimientos y no en función del tiempo.

### <a name="magnetism"></a>Magnetismo

Este mecanismo puede considerarse como una versión más general de los algoritmos de "vínculo más cercano": dibujar un cursor hacia un destino o simplemente aumentar los indicadores de acierto (visibles o no) a medida que los usuarios se aproximan a los destinos usando conocimientos sobre el diseño interactivo para aproximar mejor la intención del usuario. Esto puede resultar especialmente eficaz para destinos pequeños.

### <a name="focus-stickiness"></a>Permanencia del foco

Al determinar a qué elementos interactivos cercanos se dará el foco, se produce un sesgo hacia el elemento que está actualmente en el foco. Esto ayudará a reducir comportamientos de cambio errático del foco cuando se flota en un punto intermedio entre dos elementos con ruido natural.

## <a name="see-also"></a>Vea también
* [Gestos](gestures.md)
* [Comandos de voz](voice-design.md)
* [Cursores](cursors.md)
