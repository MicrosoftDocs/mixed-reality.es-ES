---
title: Mirada con los ojos y confirmación
description: Introducción al modelo de entrada de mirada con los ojos y confirmación
author: sostel
ms.author: sostel
ms.date: 05/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Seguimiento de los ojos, Mixed Reality, Entrada, Mirada con los ojos, Enfoque con los ojos, HoloLens 2, Selección basada en la mirada con los ojos
ms.openlocfilehash: 9cc27f24e1275223f33becd1ff0ec6bdf5b43a57
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "66455091"
---
# <a name="eye-gaze-and-commit"></a>Mirada con los ojos y confirmación
Con HoloLens 2 se nos presenta la gran oportunidad de mirar y confirmar de manera más rápida y cómoda mediante la mirada con los ojos en lugar de la mirada con la cabeza. Esto permite ampliar el modelo de interacción habitual de [mirada con la cabeza y confirmación](gaze-and-commit.md): 
1. Solo tienes que buscar el destino y 
2. Para confirmar tu intención de seleccionar el destino, realiza una entrada explícita secundaria como:  
   - Un gesto con la mano (por ejemplo, pulsar en el aire)
   - Presionar un botón (por ejemplo, en un teclado Bluetooth o un dispositivo de clic)
   - Un comando de voz (por ejemplo, "Seleccionar")
   - Manteniendo la mirada (es decir, el usuario simplemente se mantiene mirando al destino para seleccionarlo)

No obstante, la mirada con los ojos se comporta de manera muy diferente a la mirada con la cabeza en determinados aspectos y, por tanto, presenta una serie de desafíos específicos. En las [Directrices para el diseño de mirada con los ojos](eye-tracking.md), se resumen las ventajas generales y los desafíos a tener en cuenta al usar el seguimiento de los ojos como modelo de entrada en la aplicación holográfica. En esta sección, vamos a centrarnos en las consideraciones de diseño específicas de la función de mirada con los ojos y confirmación.
En primer lugar, los ojos se mueven a una velocidad increíblemente rápida y, por tanto, son estupendos para fijar rápidamente un destino en la vista. Esto hace que la mirada con los ojos resulte idónea para realizar acciones de mirada y confirmación especialmente cuando se combina con confirmaciones rápidas mediante una pulsación en el aire o presión de un botón.
   
A continuación, se abordarán las directrices de diseño a la hora de emplear la mirada con los ojos para este tipo de interacción y se analizarán las diferencias que debe tener en cuenta entre la mirada con los ojos y la mirada con la cabeza.

## <a name="design-guidelines-for-eye-gaze-and-commit"></a>Directrices de diseño para la mirada con los ojos y la confirmación

**No aparece ningún cursor**: Aunque es casi imposible interactuar sin un cursor cuando se usa la mirada con la cabeza, este resulta molesto cuando se usa la mirada con los ojos. En lugar de confiar en un cursor para avisar al usuario de si el seguimiento con la mirada funciona y ha detectado correctamente el destino al que se está mirando actualmente, usa otros resaltes visuales más sutiles (más información a continuación).

**Busca señales más sutiles de la información sobre el gesto de mantener pulsado**: La información visual que puede parecer estupenda para la mirada con la cabeza puede resultar en experiencias muy negativas en la mirada con los ojos. Recuerda que los ojos son extremadamente rápidos y capaces de fijar la mirada rápidamente en muchos puntos del campo de visión. Los cambios súbitos y rápidos de resaltado (activación o desactivación) pueden provocar un parpadeo al mirar alrededor. Por lo tanto, para proporcionar información sobre el gesto de mantener pulsado, es recomendable utilizar un resaltado con fundido de entrada suave (o fundido de salida al dejar de mirar). Esto significa que al principio apenas te darías cuenta de la información al mirar a un destino. En el transcurso de 500-1000 ms el resaltado aumentaría en intensidad. Aunque puede que los usuarios inexpertos mantengan la mirada en el destino para asegurarse de que el sistema ha determinado correctamente el destino enfocado, los usuarios expertos miran y confirman rápidamente sin necesidad de esperar a que los comentarios alcancen su mayor intensidad. Además, también se recomienda usar un fundido de salida que atenúe la información al mantener el puntero. La investigación ha demostrado que los movimientos rápidos y los cambios de contraste son muy notorios en la visión periférica (es decir, el área del campo visual a la que no estás mirando directamente). El fundido de salida no tiene que ser tan lento como el de entrada. Esto solo es importante si dispones de cambios rápidos de contraste o color en el resaltado. Si la información sobre el gesto de mantener pulsado es lo suficientemente sutil para empezar, posiblemente no observarás ninguna diferencia.

**Busca señales de sincronización de la mirada y confirmación**: La sincronización de las señales de entrada es un desafío menor para la mirada con los ojos y la confirmación sencillas, así que, no te preocupes. Es algo a tener en cuenta en caso de que desees usar acciones de confirmación más complicadas aunque puede que eso implique comandos de voz largos o complicados gestos con las manos. Imagina que miras a un destino y dices un comando de voz largo. Teniendo en cuenta el tiempo necesario para pronunciar el comando y el tiempo que tarda el sistema en detectar lo que has dicho, la mirada con los ojos se habrá dirigido a un nuevo destino del escenario. Por tanto, debes explicar a los usuarios que deben fijar la mirada en un destino hasta que se haya reconocido el comando o controlar la entrada de forma que se determine el comienzo del comando y lo que el usuario había estado mirando en ese momento.

## <a name="see-also"></a>Consulte también
* [Mirada-cabeza y confirmación](gaze-and-commit.md)
* [Gestos con la mano](gestures.md)
* [Entrada de voz](voice-design.md)
* [Controladores de movimiento](motion-controllers.md)
