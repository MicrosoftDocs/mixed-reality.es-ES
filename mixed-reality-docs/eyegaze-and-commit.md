---
title: Mirada y confirmación
description: Información general sobre el modelo de entrada de mirada y confirmación
author: sostel
ms.author: sostel
ms.date: 05/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Seguimiento de los ojos, mixto en realidad, entrada, ojo mirada, destinadas a ojos, HoloLens 2, selección basada en el efecto de ojos
ms.openlocfilehash: 9cc27f24e1275223f33becd1ff0ec6bdf5b43a57
ms.sourcegitcommit: 60060386305eabfac2758a2c861a43c36286b151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66455091"
---
# <a name="eye-gaze-and-commit"></a>Mirada y confirmación
Con el 2 de HoloLens, tenemos la gran oportunidad para realizar mirada & confirmación más rápido y más cómodo con efecto de ojos mirada en lugar de mirada principal. Esto permite ampliar el común [mirada de encabezado y confirmación](gaze-and-commit.md) modelo de interacción: 
1. Solo hay que buscar en un destino y 
2. Para confirmar su intención de seleccionar el destino, realice una base de datos secundaria explícita de entrada como de r:  
   - Gesto (por ejemplo, un aire pulse)
   - Presionar el botón (por ejemplo, en un teclado Bluetooth o clicker)
   - Comando de voz (p. ej., "Select")
   - Reposo (es decir, el usuario simplemente mantiene mirando el destino para seleccionar)

Sin embargo, la mirada ojo se comporta de forma muy distinta a principal mirada en ciertos aspectos y, por tanto, incluye una serie de desafíos únicos. En el [directrices de diseño que mirar ojo](eye-tracking.md), se resumen las ventajas generales y los desafíos a tener en cuenta al usar ocular seguimiento como una entrada en la aplicación holográfica. En esta sección, nos centramos en las consideraciones de diseño específicas para mirada & confirmación.
En primer lugar, los ojos mover increíblemente rápido y, por tanto, son una excelentes destino rápidamente en la vista. Esto hace que ojo que mirar ideal para acciones de mirada y confirmación rápidas, especialmente cuando se combina con confirmaciones rápidas como un botón o pulsar en el aire press.
   
A continuación, nos referiremos a instrucciones de diseño cuando utiliza ojo que mirar para este tipo de interacción y se describen las diferencias entre head y ocular mirada que debe tener en cuenta.

## <a name="design-guidelines-for-eye-gaze-and-commit"></a>Instrucciones para la confirmación y la mirada de diseño

**No mostrar un cursor**: Aunque es casi imposible interactuar sin un cursor cuando se usa el encabezado que mirar, el cursor se vuelve rápidamente que distraen y molestos cuando se usa la mirada de ojos. En lugar de depender de un cursor para informar al usuario detecta la actualmente buscar si rastreo ocular funciona y tiene correctamente en el destino, use sutiles visual resalta (más detalles a continuación).

**Para enviar comentarios al mantener el mouse combinada sutiles se esfuerzan por**: Lo que parece excelentes comentarios visuales para mirada principal puede dar lugar a experiencias terribles abrumadores mediante mirada ojos. Recuerde que los ojos son extremadamente rápidos, darting rápidamente entre los puntos en el campo de la vista. Cambios de resaltado repentino rápido (activar/desactivar) pueden dar lugar flickery comentarios cuando echando un vistazo. Por lo tanto, al proporcionar comentarios al mantener el mouse, se recomienda usar un área resaltada de mezcla sin problemas (y blended horizontal comparada ausente). Esto significa que al principio apenas observaría los comentarios en un destino. En el transcurso de 500-1000 ms el resaltado aumentaría en intensidad. Mientras que los usuarios inexpertos podrían seguir buscando en el destino para asegurarse de que el sistema ha determinado correctamente el destino centrado, usuarios expertos rápidamente podrían observación & se confirman sin esperar a que los comentarios son en su máxima intensidad. Además, también se recomienda usar una mezcla de salida cuando se atenúa, los comentarios al mantener el mouse. Investigación ha demostrado que los cambios rápidos de movimiento y el contraste son muy notables en su visión periférico (por lo tanto, el área de campo visual donde no desea). El fundido de salida no tiene que ser tan lenta como en blend. Esto solo es importante cuando disponga de contraste alto o cambios de color para el resaltado. Si los comentarios al mantener el mouse eran bastante sutil para empezar, probablemente no notará ninguna diferencia.

**Busque señales mirada y confirmar la sincronización**: La sincronización de señales de entrada puede ser menor de un desafío para simple mirada & confirmación, por lo tanto, no se preocupe! Es algo a tener en cuenta en caso de que desea usar acciones de confirmación más complicadas aunque puede implicar a los comandos de voz larga o gestos de mano complicada. Imagine que mire diana y emitido un comando de voz largo. Tenga en cuenta el tiempo que necesita para hablar y el momento en que el sistema necesita para detectar lo que dicho, su mirada ojo normalmente larga cambió a algún nuevo destino de la escena. Por lo tanto, puede hacer que los usuarios tener en cuenta que es posible que deba seguir buscando en un destino hasta que se le ha reconocido el comando o controlar la entrada en una forma de determinar desde el principio del comando y lo que el usuario había estado viendo entonces.

## <a name="see-also"></a>Vea también
* [Mirada-cabeza y confirmación](gaze-and-commit.md)
* [Gestos de mano](gestures.md)
* [Entrada de voz](voice-design.md)
* [Controladores de movimiento](motion-controllers.md)
