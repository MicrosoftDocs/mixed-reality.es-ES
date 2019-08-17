---
title: Usar HoloLens en nuevos espacios
description: HoloLens aprende qué aspecto tiene un espacio a lo largo del tiempo. Los usuarios pueden facilitar este proceso moviendo el HoloLens de ciertas maneras a través del espacio.
author: dorreneb
ms.author: dobrown
ms.date: 08/16/2019
ms.topic: article
keywords: Windows Mixed Reality, diseño, asignación espacial, HoloLens, reconstrucción expuesta, malla, seguimiento de cabezales, asignación
ms.openlocfilehash: a6a83dfc2c883723e4cd79c0dc46a9cd78f1f604
ms.sourcegitcommit: 60f73ca23023c17c1da833c83d2a02f4dcc4d17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566024"
---
# <a name="use-hololens-in-new-spaces"></a>Usar HoloLens en nuevos espacios

HoloLens *asigna*o aprende información sobre el entorno a medida que el usuario se desplaza por un espacio. Con el tiempo, HoloLens crea un *mapa espacial* de todas las partes del entorno que se han observado. HoloLens actualiza el mapa a medida que se observan los cambios en el entorno. Este examen se conservará automáticamente entre los lanzamientos de la aplicación.

HoloLens creará y actualizará asignaciones siempre que el dispositivo esté encendido y un usuario haya iniciado sesión. Si mantiene presionado el dispositivo con las cámaras que apuntan a un espacio, el dispositivo intentará asignar el área. Aunque HoloLens aprenderá un espacio de forma natural a lo largo del tiempo, hay sugerencias y trucos disponibles para asignar el espacio de manera más rápida y eficaz. 

Si HoloLens no puede asignar espacio o está fuera de la calibración, puede entrar en modo limitado. En el modo limitado, no podrá colocar hologramas en su entorno.

## <a name="tips-and-tricks-for-mapping-spaces"></a>Sugerencias y trucos para la asignación de espacios

### <a name="make-sure-the-space-is-set-up-for-mixed-reality"></a>Asegúrese de que el espacio está configurado para la realidad mixta

Las características de un entorno pueden dificultar que HoloLens interprete un espacio. Los niveles de luz, los materiales del espacio, el diseño de los objetos, etc. pueden afectar a la forma en que HoloLens asigna un área.

Puede encontrar sugerencias para configurar el espacio de HoloLens y otros dispositivos de realidad mixta en [consideraciones de entorno para hololens](environment-considerations-for-hololens.md).

### <a name="understand-the-scenarios-for-the-area"></a>Comprender los escenarios del área

Es importante dedicar el tiempo más en el que vaya a usar HoloLens para que el mapa sea relevante y completo. 

Por ejemplo, si un escenario de usuario de HoloLens implica pasar del punto a al punto B, desplazarse por la ruta de acceso dos a tres veces, buscando en todas las direcciones mientras se mueven. 

### <a name="walk-slowly-around-the-space"></a>Recorrer lentamente el espacio

Si recorre demasiado rápidamente el área, es probable que HoloLens pierda las áreas de asignación. Desplácese lentamente alrededor del espacio, deteniéndose cada 5-8 metros para buscar en todo el entorno.

Los movimientos suaves también ayudan a la asignación de HoloLens más effeciently.

### <a name="look-in-all-directions"></a>Buscar en todas las direcciones

Al mirar el espacio, se proporciona a HoloLens más datos sobre dónde se relacionan entre sí los puntos. 

Si no busca, por ejemplo, es posible que HoloLens no sepa dónde está el límite superior de una habitación. 

No olvide mirar el suelo mientras asigna el espacio.

### <a name="cover-key-areas-multiple-times"></a>Portadas varias veces de las áreas clave

Desplazarse por un área varias veces le ayudará a recoger características que puede que haya perdido en el primer tutorial. Intente recorrer un área dos o tres veces para crear un mapa ideal.

Si es posible, mientras se repiten estos movimientos, dedique tiempo a recorrer un área en una dirección y, a continuación, desactive y recorra la forma en que lo hizo.

### <a name="take-your-time-mapping-the-area"></a>Dedique su tiempo a asignar el área

Puede tardar entre 15 y 20 minutos para que HoloLens se asigne completamente y se ajuste a su entorno. Si tiene un espacio en el que piensa usar una HoloLens con frecuencia, tardará ese tiempo en realizarse por adelantado para asignar el espacio puede evitar problemas más adelante. 

## <a name="possible-errors-in-the-spatial-map"></a>Posibles errores en el mapa espacial

Los errores en los datos de asignación espacial se dividen en una de estas tres categorías:

* *Agujeros*: Faltan las superficies del mundo real en los datos de asignación espacial.
* *Hallucinations*: Existen superficies en los datos de asignación espacial que no existen en el mundo real.
* *Túneles espaciales*: La parte de HoloLens ' pierde ' del mapa espacial al pensar que está en una parte diferente del mapa que realmente es.
* *Bias*: Las superficies en los datos de asignación espacial se alinean imperfectamente con las superficies del mundo real, ya sean insertadas o extraídas.

Muchos de estos errores se pueden mitigar si se [eliminan los hologramas](environment-considerations-for-hololens.md) y se vuelve a asignar el espacio.