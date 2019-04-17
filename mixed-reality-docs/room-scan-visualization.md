---
title: Visualización de análisis de sala
description: Las aplicaciones que requieren datos de asignación espacial se basan en el dispositivo para recopilar estos datos automáticamente con el tiempo y en las sesiones como el usuario explora su entorno con el dispositivo activo.
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, patrones de aplicaciones, diseño, HoloLens, examen de sala, espacial de asignación, superficie reconstrucción, Live mesh
ms.openlocfilehash: 8ffde9d476e25016f986321377dce8125ee3a596
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605693"
---
# <a name="room-scan-visualization"></a>Visualización de análisis de sala

Las aplicaciones que requieren datos de asignación espacial se basan en el dispositivo para recopilar estos datos automáticamente con el tiempo y en las sesiones como el usuario explora su entorno con el dispositivo activo. La integridad y la calidad de los datos depende de varios factores como la cantidad de exploración, el usuario ha hecho, ¿cuánto tiempo ha transcurrido desde la exploración y si objetos como muebles y puertas movido desde que el dispositivo había analizado el área.

Para asegurarse de datos de asignación espacial útiles, los desarrolladores de aplicaciones tienen varias opciones:
* Se basan en lo que es posible que ya se han recopilado. Estos datos pueden estar incompletos inicialmente.
* Pida al usuario usar el gesto de bloom para llegar a Windows Mixed Reality principal y, a continuación, explore el área que desean usar para la experiencia. Pulsar en el aire pueden usar para confirmar que se conoce toda el área es necesario para el dispositivo.
* Crear una experiencia de exploración personalizada en su propia aplicación.

Tenga en cuenta que en todos estos casos se almacenan los datos reales recopilados durante la exploración por el sistema y la aplicación no necesita hacerlo.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Característica</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td> Visualización de análisis de sala</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>



## <a name="building-a-custom-scanning-experience"></a>Creación de una experiencia de exploración personalizada

Pueden decidir analizar los datos de asignación espacial al principio de la experiencia para decidir si desean que el usuario realice pasos adicionales para mejorar su integridad y la calidad de las aplicaciones. Si el análisis indica que se debe mejorar la calidad, los desarrolladores deben proporcionar una visualización a superponer en el mundo para indicar:
* ¿Cuánto volumen total, en la proximidad de los usuarios debe formar parte de la experiencia
* Donde el usuario debe ir para mejorar los datos

Los usuarios no saben lo que hace que un examen "bueno". Deben mostrarse o dijo lo que se debe buscar si le pide que evaluar un examen: aplanamiento, distancia de las paredes reales, etcetera. El desarrollador debe implementar un bucle de comentarios que incluye la actualización de los datos de asignación espacial durante la fase de análisis o exploración.

En muchos casos, puede ser mejor indicar que el usuario lo que necesitan (por ejemplo, examine el límite superior, busque detrás de muebles), con el fin de obtener la calidad del análisis necesarios.

## <a name="cached-versus-continuous-spatial-mapping"></a>En la caché frente a asignación espacial continua

Los datos de asignación espacial están el peso más pesado pueden consumir las aplicaciones del origen de datos. Para evitar problemas de rendimiento, como fotogramas eliminados o repetir, consumo de los datos debe realizarse con cuidado.

Análisis activo durante una experiencia pueden ser beneficioso o perjudicial y el desarrollador tendrá que decidir qué método utilizar según la experiencia.

### <a name="cached-spatial-mapping"></a>Asignación espacial en caché

En el caso de asignación espacial en caché, la aplicación normalmente toma una instantánea de los datos de asignación espacial y utiliza esta instantánea para la duración de la experiencia.

**Ventajas**
* Reducción de la sobrecarga en el sistema mientras la experiencia ejecuta líder a potencia espectacular, térmico y mejoras de rendimiento de cpu.
* Una implementación más sencilla de la experiencia principal, ya que no se interrumpa por los cambios en los datos espaciales.
* Una sola una vez costo en cualquier procesamiento posterior de los datos espaciales de leyes físicas, gráficos y otros fines.

**Inconvenientes**
* El movimiento de objetos del mundo real o personas no se refleja en los datos en caché. P. ej. la aplicación podría considerar una puerta abierta cuando en realidad está cerrado ahora.
* Potencialmente más memoria de la aplicación para mantener la versión en caché de los datos.

Un buen caso de este método es un juego de la tabla superior o de un entorno controlado.

### <a name="continuous-spatial-mapping"></a>Asignación espacial continua

Algunas aplicaciones pueden confiar en continúa analizando para actualizar los datos de asignación espacial.

**Ventajas**
* No es necesario que se compilarán en una independiente análisis de exploración experiencia o por adelantado en la aplicación.
* El movimiento de objetos del mundo real puede reflejarse en el juego, aunque con cierto retraso.

**Inconvenientes**
* Una mayor complejidad en la implementación de la experiencia del principal.
* Sobrecarga potencial del procesamiento adicional para el gráfico o físicas, como los cambios deben ser ingeridos incrementalmente estos sistemas.
* Mayor capacidad, térmico y el impacto en la CPU.

Un buen caso de este método es uno donde se esperan hologramas para interactuar con el movimiento de objetos, por ejemplo, un automóvil holográfico que las unidades en el suelo pueden toparse con una puerta dependiendo de si es abierto o cerrado correctamente.

## <a name="see-also"></a>Vea también
* [Diseño de la asignación espacial](spatial-mapping-design.md)
* [Sistemas de coordenadas](coordinate-systems.md)
* [Diseño espacial de sonido](spatial-sound-design.md)
