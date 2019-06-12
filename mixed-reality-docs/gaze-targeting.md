---
title: Mirada destinadas a
description: Todas las interacciones se basan en la capacidad de un usuario para el elemento que desean interactuar, independientemente de la modalidad de entrada de destino.
author: cre8ivepark
ms.author: jennyk
ms.date: 02/24/2019
ms.topic: article
keywords: Mixto en realidad, mirada, mirada como destino, interacción, diseñar
ms.openlocfilehash: eddc832456b2ba0c6bc8955157d2c8e1a268e893
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829839"
---
# <a name="gaze-and-dwell"></a>Mirada y permanencia
Hay muchas maneras diferentes para confirmar una _confirmación_ , como la combinación mirada con _voz_ o _gestos de mano_.
Hay varios escenarios de usuario sin embargo, en el que manos de los usuarios, o bien pueden estar ocupadas o no se puede realizar el seguimiento (p. ej., los trabajadores de fábrica con guantes pesados demasiado grande). Entrada de voz también no estén disponible debido a las preferencias del usuario, contexto social o entornos de altos.
Como una solución de reserva otra opción para realizar un _confirmación_ es simplemente mantener que comience en un elemento de interfaz de usuario que nos referiremos como _profundizaré_.
Un _profundizaré_ puede realizarse con mirada head o efecto de ojos. La idea es sencilla y puede dividirse en las siguientes fases: 
1. Usuario comienza a gazing en un botón holográfico

2. Después de un retraso breve manifestación (p. ej., 150 ms) se ha iniciado alguna animación comentarios visuales. El retraso de aparición se usa para evitar sobrecargar el usuario haciendo que emerja inmediatamente los comentarios todo el tiempo.
    - Para _mirada ojo_, se recomienda lo siguiente para el diseño del objeto visual profundizaré comentarios:
      - **Blend se**: Blend sin problemas en los comentarios de apenas visible en primer lugar a totalmente opaco. Esto hace que los comentarios a menos que distraen y overwhleming y bien se alinea con la confianza de que el sistema tiene que el usuario realmente desea ponerse en contacto con este botón.
      - **Incorporación de cambios**: Cree un comentarios visuales que disminuye de tamaño y se mueve hacia el centro del destino, dirige la atención del usuario visual. 

3. Después de una duración de permanencia definido previamente (por ejemplo, 800 ms), se completa la permanencia y se desencadena un evento asociado.
    - Proporcionar algunos finalizando auditorio o comentarios visuales poner realmente inicio el elemento tienen seleccionada ahora.

![Profundizaré Estados](images/eyes_dwellstate_recommendation.png)


# <a name="gaze-targeting"></a>Mirada destinadas a

Todas las interacciones se basan en la capacidad de un usuario para el elemento que desean interactuar, independientemente de la modalidad de entrada de destino. En Windows Mixed Reality, por lo general esto se hace mediante la mirada del usuario.

Para que los usuarios puedan trabajar con una experiencia correctamente, debe alinear comprensión calculado del sistema de la intención del usuario y la intención del usuario real, como lo máximo posible. En la medida que el sistema interpreta las acciones del usuario previsto correctamente, aumenta la satisfacción y el rendimiento mejora.

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
        <td>Mirada destinadas a</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Destinatarios de ojo</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

> [!NOTE]
> Obtener información más específica de HoloLens 2 [próximamente](index.md).

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
* [Comandos de voz](voice-design.md)
* [Cursores](cursors.md)
