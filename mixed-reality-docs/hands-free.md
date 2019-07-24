---
title: Manos libres
description: Optimización de la aplicación para manos libres
author: liamar
ms.author: liamar
ms.date: 04/20/2019
ms.topic: article
keywords: Realidad mixta, manos libres, miradas por mirados, interacción, diseño
ms.openlocfilehash: 7942192f644a7133335f089cfaaccfaebdd9292e
ms.sourcegitcommit: d8700260f349a09c53948e519bd6d8ed6f9bc4b4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/27/2019
ms.locfileid: "67414394"
---
# <a name="hands-free"></a>Manos libres



## <a name="scenarios"></a>Escenarios

Como se describe en [información general sobre el modelo de interacción](interaction-fundamentals.md), una vez que haya identificado los usuarios y sus objetivos, pregúntese qué desafíos ambientales o de situaciones pueden enfrentarse a medida que trabajan para llevar a cabo sus tareas. Por ejemplo, muchos usuarios necesitan usar sus manos para lograr sus objetivos del mundo real y tendrán dificultades para interactuar con una interfaz basada en manos y controladores. 

Algunos escenarios específicos pueden ser: 
* Se le guiará a través de una tarea, mientras que las manos están ocupadas.
* Referencia a materiales mientras sus manos están ocupados
* Fatiga manual
* Guantes en los que no se puede realizar un seguimiento
* Llevar algo


## <a name="hands-free-modalities"></a>Modalidades de manos libres

### <a name="voice-commandingvoice-designmd"></a>[Comandos de voz](voice-design.md)

El uso de la voz para el comando y el control de una interfaz no solo permite al usuario operar Handsfree, sino que también puede omitir varios pasos. El uso de esta modalidad puede abarcar desde permitir al usuario simplemente leer el nombre de cualquier botón en voz alta para activarlo, como en el caso de "ver-ti", para conversar con un agente que puede realizar tareas por usted.



### <a name="head-gaze-and-dwellgaze-and-dwellmd"></a>[Control con la cabeza y permanencia](gaze-and-dwell.md)

En algunas situaciones sin experiencia, el uso de la voz no es lo ideal o incluso posible. Los entornos de fábrica, la privacidad o las normas sociales de alta carga pueden ser restricciones. El modelo de miras y de la vivienda permite al usuario navegar por la aplicación mediante el vector de encabezado para apuntar, mientras que la permanencia o la vivienda en un botón, se activará después de un período de tiempo determinado, normalmente aproximadamente en un segundo. 


## <a name="transitioning-in-and-out-of-hands-free"></a>Transición dentro y fuera de manos libres

En estos casos, la liberación de las manos de la interacción con los hologramas para la navegación y los comandos puede abarcar de ser un requisito absoluto para el funcionamiento de la aplicación, de un extremo a otro, a una mayor comodidad en la que el usuario puede realizar la transición en cualquier tiempo. 

Si el requisito de la aplicación es que siempre se usará de forma gratuita, ya sea mediante la permanencia, comandos de voz o el único comando de voz, "seleccionar", asegúrese de hacer las adaptaciones adecuadas en la interfaz de usuario. 

Si el usuario de destino debe ser capaz de cambiar de manos libres a su discreción, es importante tener en cuenta los siguientes principios.

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>Supongamos que el usuario ya está en el modo al que desea cambiar
Por ejemplo, si el usuario está en la fábrica, viendo una referencia de vídeo en su Hololens y decide tomar una llave para empezar a trabajar, lo más probable es que empiece a trabajar en Handsfree sin tener que dejar la llave inglesa para presionar un botón. Debe ser capaz de invocar una sesión de voz con un comando de voz, hospedar en una interfaz de usuario ya visible para comenzar la permanencia o decir la palabra "seleccionar".

El usuario debe tener la capacidad de: 
* Cambiar a manos libres sin manos libres
* Cambiar a manos con las manos
* Cambiar al controlador mediante un controlador 

### <a name="create-redundant-ways-to-switch-modes"></a>Crear formas redundantes de cambiar de modo
Aunque el primer principio es acerca del acceso, el segundo es acerca de la disponibilidad. No debe haber una única manera de pasar de un modo a otro. 

Algunos ejemplos serían: 
* Un botón para iniciar las interacciones de voz
* Un comando de voz para realizar la transición al uso de fijamente + viviendas

### <a name="add-a-dash-of-drama"></a>Agregar un guion de series
Un modificador de modo es un gran negocio, es importante que cuando estas transiciones sucedan que son un conmutador explícito, incluso drástico, para que el usuario sepa lo que ha sucedido. 


## <a name="usability-checklist"></a>Lista de comprobación de usabilidad

**¿Puede el usuario hacer todo lo posible y todo lo que sea gratuito?**
* Cada interactúable debe ser accesible sin complicaciones
* Asegúrese de que hay un reemplazo para todos los gestos personalizados, como el cambio de tamaño, la colocación, los deslizamientos, los grifos, etc.
* Asegúrese de que el usuario tiene el control seguro de la presencia de la interfaz de usuario, la ubicación y el nivel de detalle en todo momento.
    * Sacar la interfaz de usuario del camino
    * Interfaz de usuario de direccionamiento fuera del campo de vista (campo de campo)
    * ¿Cuánto veo, dónde?

**¿La mecánica de la interacción se enseña y se refuerza con las prestaciones adecuadas?**

¿Entiende el usuario...
* ... ¿En qué modo se encuentran?
* ... ¿Qué pueden hacer en este modo?
* ... ¿Cuál es el estado actual?
* ... ¿Cómo pueden realizar la transición?
    
**¿La interfaz de usuario está optimizada para manos libres?**   

* Ejemplo: Las prestaciones de permanencia no están integradas en los patrones 2D típicos
* Ejemplo: El destino de la voz es mejor con el resaltado de objetos
* Ejemplo: Las interacciones de voz son mejores con títulos que se deben activar


## <a name="see-also"></a>Vea también
* [Mirada-cabeza y confirmación](gaze-and-commit.md)
* [Manipulación directa con las manos](direct-manipulation.md)
* [Apuntar y confirmar con las manos](point-and-commit.md)
