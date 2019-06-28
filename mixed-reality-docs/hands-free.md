---
title: Manos libres
description: Optimizar la aplicación para la configuración manos libres
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: La realidad mixta, manos libres, que mirar, mirar como destino, interacción, diseño
ms.openlocfilehash: 7942192f644a7133335f089cfaaccfaebdd9292e
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414394"
---
# <a name="hands-free"></a>Manos libres



## <a name="scenarios"></a>Escenarios

Como se describe en el [información general del modelo de interacción](interaction-fundamentals.md), una vez identificados los usuarios y sus objetivos, pregúntese qué desafíos del entorno o conocimiento produzcan mientras trabajan para realizar sus tareas. Por ejemplo, muchos usuarios necesitan utilizar sus manos para lograr sus objetivos reales y tendrá dificultades para interactuar con una interfaz basada en las manos y controladores. 

Podrían ser algunos escenarios concretos: 
* Se le guiará a través de una tarea, mientras que las manos están ocupadas
* Hacer referencia a materiales mientras están ocupadas sus manos
* Fatiga de la mano
* Guantes que no se puede realizar el seguimiento
* Llevar a algo


## <a name="hands-free-modalities"></a>Modalidades de manos libres

### <a name="voice-commandingvoice-designmd"></a>[Comandos de voz](voice-design.md)

Uso de la voz para comando y control de que una interfaz puede no sólo permite al usuario manos libres de funcionar, pero también omitir varios pasos. El uso de esta modalidad puede oscilar entre lo que permite al usuario simplemente leer el nombre de cualquier botón en voz alta para activarlo, al igual que en vea-it-say-it, para conversar con un agente que puede realizar las tareas por usted.



### <a name="head-gaze-and-dwellgaze-and-dwellmd"></a>[Control con la cabeza y permanencia](gaze-and-dwell.md)

En algunas situaciones en las manos libres, uso de la voz no es ideal o posible. Entornos de fábrica fuerte, privacidad o normas sociales pueden ser restricciones. El encabezado que mirar + profundizaré modelo permite al usuario navegar por la aplicación mediante el uso de su vector principal para que apunte al persistentes, o reposo en un botón se activarán después de una cierta cantidad de tiempo, normalmente aproximadamente 1 segundo o lo. 


## <a name="transitioning-in-and-out-of-hands-free"></a>Transición dentro y fuera de manos libres

Para estos escenarios, liberar las manos de interactuar con hologramas para navegación y comandos puede ser desde un requisito absoluto a la aplicación,-to-end, para una mayor comodidad en la que el usuario puede realizar dentro y fuera de la transición a cualquiera de funcionamiento hora. 

Si el requisito de la aplicación es que siempre se usará con manos libres, ya sea a través de permanencia, comandos de voz o el comando de voz única, "select", asegúrese de realizar el alojamiento adecuado en la interfaz de usuario. 

Si el usuario de destino debe ser capaz de cambiar de manos a manos libres a su discreción, es importante tener los siguientes principios en cuenta.

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>Suponga que el usuario ya está en el modo en que desea cambiar a
Por ejemplo, si el usuario está en la fábrica, siguiendo una referencia de vídeo en su Hololens y decide recoger una llave inglesa para empezar a trabajar, más probable es que podría empezar a trabajar en manos libres sin tener que dejar la llave inglesa que presionar un botón. Debería poder llamar a una sesión de voz con un comando de voz, profundizaré en una interfaz de usuario ya visible para comenzar la permanencia o decir que la palabra "select".

El usuario debe tener la capacidad de: 
* Cambiar a manos libres mientras manos libres
* Cambiar a manos con sus manos
* Cambiar al controlador mediante un controlador 

### <a name="create-redundant-ways-to-switch-modes"></a>Crear redundancia de maneras de cambiar los modos de
Aunque el primer principio es acerca del acceso, la segunda es sobre la disponibilidad. Simplemente no debe haber una manera de transición dentro y fuera de un modo única. 

Algunos ejemplos serían: 
* Un botón para iniciar interacciones de voz
* Un comando de voz para realizar la transición al uso de mirada + permanencia

### <a name="add-a-dash-of-drama"></a>Agregar un guión de drama
Un modificador de modo es muy interesante, es importante que cuando producen estas transiciones que sea un modificador explícito, incluso espectacular, para permitir al usuario saber qué ha ocurrido. 


## <a name="usability-checklist"></a>Lista de comprobación de facilidad de uso

**¿Puede hacer el usuario todo y cualquier otra cosa manos libres, to-end?**
* Cada interactible debe ser accesible con manos libres
* Asegúrese de que hay un reemplazo para todos los gestos personalizados, como el tamaño, colocación, deslizamientos, derivaciones, etcetera.
* Asegúrese de que el usuario tiene control seguro de presencia, colocación y nivel de detalle de la interfaz de usuario en todo momento
    * Introducción de la interfaz de usuario
    * Direccionamiento de la interfaz de usuario que está fuera del campo de visión (FOV)
    * ¿Cuánto tiempo puedo ver, donde cuando

**¿Son la mecánica de la interacción que se va a impartidos y reforzó de manera regular con la factibilidad derecha?**

¿¿Entiende el usuario...
* ... ¿Qué modo se encuentran en?
* ... ¿Qué puede hacer en este modo?
* ... ¿Qué es el estado actual?
* ... ¿Cómo puede realizar la transición fuera?
    
**¿La interfaz de usuario optimizada para manos libres?**   

* Por ejemplo: Prestaciones de permanencia no están integradas en los patrones típicos de 2D
* Por ejemplo: Destinatarios de voz están mejor con el objeto resaltado
* Por ejemplo: Interacciones de voz son mejores con subtítulos que tienen que estar activado


## <a name="see-also"></a>Vea también
* [Mirada-cabeza y confirmación](gaze-and-commit.md)
* [Manipulación directa con las manos](direct-manipulation.md)
* [Apuntar y confirmar con las manos](point-and-commit.md)
