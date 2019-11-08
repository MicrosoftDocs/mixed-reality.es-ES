---
title: Control con los ojos y permanencia
description: Introducción al modelo de entrada de control con los ojos y permanencia
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
ms.localizationpriority: high
keywords: Seguimiento de los ojos, Mixed Reality, Entrada, Control con los ojos, Enfoque con los ojos, HoloLens 2, Selección basada en los ojos, Permanencia
ms.openlocfilehash: 5130fd3c1ecd551788f61f8abb8d02cdedeb4181
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437811"
---
# <a name="eye-gaze-and-dwell"></a>Control con los ojos y permanencia

El modelo de interacción de _"control con los ojos y permanencia"_ es un caso especial del modelo de interacción de [control con los ojos y confirmación](gaze-and-commit.md):
1. Solo tienes que buscar el destino y 
2. Para confirmar tu intención de seleccionar el objetivo, realiza una entrada explícita secundaria: _simplemente sigue mirando el objetivo que quieras seleccionar_.

## <a name="advantages-of-the-eye-gaze-and-dwell-interaction-model"></a>Ventajas del modelo de interacción de "control con los ojos y permanencia" 
Cuando tengas las manos ocupadas en una tarea o en herramientas, quizá no puedas usarlas para interactuar con los hologramas.
Una alternativa de interacción sin manos para la selección de hologramas es el "control con los ojos y permanencia", es decir: _"mirar y fijar la mirada"_ . La ventaja de este enfoque es que incluso los usuarios con movimiento limitado, que no pueden girar completamente su cabeza o cuerpo, pueden interactuar con los hologramas (por ejemplo, en un entorno de trabajo muy reducido).
El usuario simplemente sigue mirando el objetivo que desea seleccionar y se muestra un informe de permanencia diferente para indicar el proceso.


## <a name="challenges-of-the-eye-gaze-and-dwell-interaction-model"></a>Desafíos del modelo de interacción de "control con los ojos y permanencia"
En general, solo se recomienda usar las activaciones basadas en permanencias como última opción, si no están disponibles la entrada de voz ni la entrada de mano. El motivo es que la opción de tiempo de permanencia puede ser bastante complicada. A los usuarios inexpertos no les importan los tiempos de permanencia más largos, pero los usuarios expertos quieren navegar de forma rápida y eficaz por sus experiencias. Esto conduce al desafío de ajustar el tiempo de permanencia a las necesidades específicas de un usuario.
Si el tiempo de permanencia es demasiado corto: El usuario puede sentirse abrumado por tener que volver a mirar los hologramas todo el tiempo. Si el tiempo de permanencia es demasiado largo: La experiencia puede percibirse como demasiado lenta y disruptiva, ya que el usuario tiene que mantener la mirada en los objetivos durante mucho tiempo.

## <a name="design-recommendations"></a>Recomendaciones de diseño
Se recomienda usar un enfoque de dos estados para los informes de permanencia:
1. *Retraso del inicio*: cuando el usuario empieza a mirar un objetivo, no se debe producir nada inmediatamente, ya que podría generar una experiencia de usuario desagradable y abrumadora. En su lugar, se inicia un temporizador para detectar si el usuario está mirando intencionadamente el objetivo o simplemente pasa la mirada sobre él.
2. *Inicio de los informes de permanencia:* después de asegurarse de que el usuario mira intencionadamente el objetivo, empezamos a mostrar informes de permanencia para comunicar al usuario que se está iniciando la activación de la permanencia. Se recomienda un tiempo de inicio de 150 a 250 ms en una proximidad determinada (lo que significa que el usuario se está fijando en un objetivo grande en lugar mirar a su alrededor).  
3. *Informes continuos:* Mientras el usuario sigue mirando el objetivo, se muestra un indicador de progreso continuo para que sepa que tiene que seguir mirando el objetivo. En particular, en el caso de entrada de control con los ojos, se recomienda _llamar la atención visual del usuario_ mostrando un círculo o esfera más grande que se contrae en una versión más pequeña. Mostrar un indicador para el estado final (círculo pequeño) ayuda a comunicar al usuario de cuándo terminará la permanencia. A continuación, se muestra una ilustración de ejemplo. 
4. *Finalizar:* Si el usuario sigue fijando el objetivo (durante otros 650 a 850 ms), se completa la activación de permanencia y se selecciona el objetivo que se ha mirado.

![Estados de permanencia](images/eyes_dwellstate_recommendation.png)<br>

## <a name="see-also"></a>Consulte también
* [Seguimiento de los ojos](eye-tracking.md)
* [Control con los ojos y confirmación](gaze-and-commit-eyes.md)
* [Mirada y confirmación](gaze-and-commit.md)
* [Mirada y permanencia](gaze-and-dwell.md)
* [Entrada de voz](voice-design.md)
