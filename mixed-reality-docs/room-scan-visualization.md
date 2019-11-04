---
title: Visualización del examen de salón
description: Las aplicaciones que requieren datos de asignación espacial se basan en el dispositivo para recopilar automáticamente estos datos a lo largo del tiempo y entre sesiones a medida que el usuario explora su entorno con el dispositivo activo.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, patrones de aplicaciones, diseño, HoloLens, examen de salón, asignación espacial, malla
ms.openlocfilehash: bdb070407f27d04046bd022894c7a8a01b9658d1
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437517"
---
# <a name="room-scan-visualization"></a>Visualización del examen de salón

Las aplicaciones que requieren datos de asignación espacial se basan en el dispositivo para recopilar automáticamente estos datos a lo largo del tiempo y entre sesiones a medida que el usuario explora su entorno con el dispositivo activo. La integridad y la calidad de estos datos dependen de una serie de factores, entre los que se incluye la cantidad de exploración que ha realizado el usuario, cuánto tiempo ha transcurrido desde la exploración y si los objetos como el mobiliario y las puertas se han trasladado desde que el dispositivo examinó la zona.

Para garantizar datos de asignación espacial útiles, los desarrolladores de aplicaciones tienen varias opciones:
* Confíe en lo que ya se ha recopilado. Estos datos pueden estar incompletos inicialmente.
* Pida al usuario que use el gesto de floración para llegar a la Página principal de Windows Mixed Reality y, a continuación, explore el área que desean usar para la experiencia. Pueden utilizar la pulsación aérea para confirmar que el dispositivo conoce todo el área necesaria.
* Cree una experiencia de exploración personalizada en su propia aplicación.

Tenga en cuenta que en todos estos casos los datos reales recopilados durante la exploración se almacenan en el sistema y la aplicación no necesita hacerlo.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Ofrecen</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Visualización del examen de salón</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a>Generar una experiencia de exploración personalizada

Las aplicaciones pueden decidir analizar los datos de asignación espacial al principio de la experiencia para juzgar si desean que el usuario realice pasos adicionales para mejorar su integridad y calidad. Si el análisis indica que se debe mejorar la calidad, los desarrolladores deben proporcionar una visualización de superposición en todo el mundo para indicar:
* La cantidad del volumen total de los usuarios en proximidad debe formar parte de la experiencia
* Dónde debe ir el usuario para mejorar los datos

Los usuarios no saben lo que realiza un análisis "correcto". Es necesario que se muestren o se les indique lo que debe buscar si se les pide que evalúen un análisis, la distancia de las paredes reales, etc. El desarrollador debe implementar un bucle de comentarios que incluya la actualización de los datos de asignación espacial durante la fase de exploración o exploración.

En muchos casos, puede ser mejor indicar al usuario lo que necesita hacer (por ejemplo, mirar el límite superior, mirar detrás del mobiliario) para obtener la calidad de examen necesaria.

## <a name="cached-versus-continuous-spatial-mapping"></a>Asignación espacial en caché y continua

Los datos de asignación espacial son el peso más pesado que pueden consumir las aplicaciones de origen de datos. Para evitar problemas de rendimiento, como fotogramas quitados o intermitencias, el consumo de estos datos debe realizarse con cuidado.

El análisis activo durante una experiencia puede ser beneficioso o perjudicial, y el desarrollador deberá decidir qué método usar en función de la experiencia.

### <a name="cached-spatial-mapping"></a>Asignación espacial almacenada en caché

En el caso de la asignación espacial almacenada en caché, la aplicación normalmente toma una instantánea de los datos de asignación espacial y usa esta instantánea para la duración de la experiencia.

**Ventajas**
* Reducción de la sobrecarga en el sistema mientras se ejecuta la experiencia, lo que supone una mejora considerable en el rendimiento de la CPU, el térmico y la potencia.
* Una implementación más sencilla de la experiencia principal, ya que no se ve interrumpida por los cambios en los datos espaciales.
* Un único costo de tiempo en cualquier procesamiento posterior de los datos espaciales para la física, los gráficos y otros propósitos.

**Desventajas**
* El movimiento de objetos o personas reales no se refleja en los datos almacenados en caché. P. ej. es posible que la aplicación considere una puerta abierta cuando realmente está cerrada.
* Posiblemente más memoria de la aplicación para mantener la versión en caché de los datos.

Un buen caso para este método es un entorno controlado o una tabla principal del juego.

### <a name="continuous-spatial-mapping"></a>Asignación espacial continua

Algunas aplicaciones pueden basarse en el análisis continuo para actualizar los datos de asignación espacial.

**Ventajas**
* No es necesario compilar en una experiencia de exploración o exploración independiente de antemano en la aplicación.
* El movimiento de objetos del mundo real puede reflejarse en el juego, aunque con algún retraso.

**Desventajas**
* Mayor complejidad en la implementación de la experiencia principal.
* Sobrecarga potencial del procesamiento adicional de gráficos o física, ya que estos sistemas deben ingerir los cambios de forma incremental.
* Mayor potencia, térmico y impacto de la CPU.

Un buen caso para este método es aquél en el que se espera que los hologramas interactúen con los objetos de movimiento, por ejemplo, un coche holográfica que las unidades del piso quieran golpear correctamente en una puerta en función de si está abierto o cerrado.

## <a name="see-also"></a>Consulta también
* [Asignación espacial](spatial-mapping.md)
* [Sistemas de coordenadas](coordinate-systems.md)
* [Diseño de sonido espacial](spatial-sound-design.md)
