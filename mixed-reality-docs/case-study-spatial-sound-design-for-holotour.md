---
title: 'Caso práctico: diseño de sonido espacial para HoloTour'
description: Para crear un paseo virtual 3D realmente envolvente para Microsoft HoloLens, los vídeos panorámicos y los escenarios holográficas solo forman parte de la fórmula.
author: JSyltebo
ms.author: jsylte
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, HoloTour, sonido espacial, caso práctico
ms.openlocfilehash: f2dd704089d9c76b7ba175a4a1ad5cebf9ec6c68
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181930"
---
# <a name="case-study-spatial-sound-design-for-holotour"></a>Caso práctico: diseño de sonido espacial para HoloTour

Los vídeos panorámicos y los escenarios holográficas solo forman parte de la fórmula de un paseo por Microsoft HoloLens virtual realmente envolvente. En este artículo se describe cómo se usó el sonido para que se parezca que realmente está en cada ubicación de HoloTour.

## <a name="the-tech"></a>La tecnología

Las atractivas imágenes y escenas holográficas que se ven en HoloTour son solo una parte de una experiencia de realidad mixta increíble. Aunque los hologramas solo pueden aparecer visualmente delante de un usuario, el [sonido espacial](spatial-sound.md) que HoloLens envía desde todas las direcciones proporciona una experiencia organoléptica más completa.

El sonido espacial proporciona indicaciones para indicar una dirección que debe activar el usuario o para que el usuario sepa que hay más hologramas para ver dentro de su espacio. También se puede adjuntar un sonido directamente a un holograma y actualizar continuamente la dirección y la distancia que el holograma proviene del usuario. Esta técnica hace que parezca que el sonido proviene directamente de ese objeto.

En el caso de HoloTour, queríamos aprovechar las capacidades de sonido espacial de HoloLens para crear un entorno ambiente de 360 grados que esté sincronizado con el vídeo para mostrar los resaltados de Sonic de ubicaciones específicas.

## <a name="behind-the-scenes"></a>En segundo plano

Creamos experiencias de HoloTour de dos ubicaciones diferentes: Roma y Machu Picchu. Para que estos paseos se sientan auténticos y atractivos, queríamos capturar audio de las ubicaciones donde se filmó en lugar de usar sonidos genéricos.

### <a name="capture-the-audio"></a>Captura del audio

En nuestro [caso práctico sobre la captura del contenido visual para HoloTour](case-study-capturing-and-creating-content-for-holotour.md), hablamos del diseño de la plataforma de la cámara. Constaba de 14 cámaras GoPro en una carcasa impresa en 3D diseñada para adaptarse al trípode. Para capturar audio, agregamos una matriz de micrófono cuádruple debajo de las cámaras. El sonido se ha alimentado en una unidad de grabación de cuatro canales compacta en la base del trípode. Hemos elegido los micrófonos que se han realizado bien pero que eran lo suficientemente pequeños como para evitar interferir con las cámaras.

![de la cámara personalizada y la plataforma de micrófono](images/camera-rig-microphones-300px.png)<br>
*Plataforma de micrófono y de cámara personalizada*

Esta configuración captura sonido en cuatro direcciones. Hemos grabado suficiente información para volver a crear una panorámica 3D aural de sonido espacial, que posteriormente podría sincronizar con el vídeo de 360 grados.

Uno de los desafíos del audio de la matriz de cámara es que está a la velocidad de los sonidos fuera de la cámara, como Sirens, aviones o altas vueltas. Para asegurarse de que teníamos todos los elementos de sonido que necesitábamos, también usamos grabadores móviles estéreo y mono para capturar sonidos de ambiente asincrónicos en puntos de interés específicos de cada ubicación. Estas grabaciones proporcionan al diseñador de sonido el contenido limpio para agregar interés y mejorar la direccionalidad en la producción posterior.

Cada día de captura genera muchos archivos. Por lo tanto, era importante desarrollar un sistema para realizar un seguimiento de qué archivos corresponden a una determinada ubicación o cámara. La unidad de grabación se configuró para asignar nombres automáticamente a los archivos por fecha y "Take". Hemos realizado copias de seguridad de los archivos en unidades externas al final de cada día. También encontramos que es importante empezar de cero a las grabaciones de audio. Esta precaución permite una sencilla identificación contextual del contenido en caso de que se produzcan problemas con el nombre de archivo. También era importante ver la captura de la plataforma de la cámara, ya que el vídeo y el audio se grabaron como medios independientes y debían sincronizarse durante el postproducción.

### <a name="edit-the-audio"></a>Edición del audio

En el estudio después del viaje de captura, el primer paso para ensamblar una experiencia de aural direccional y envolvente es revisar todo el audio capturado para una ubicación. Seleccionamos las mejores tomas e identificamos los resaltados que se pueden aplicar durante la integración. Después, el audio se edita y se limpia. Por ejemplo, una bocina de coche que dura un segundo, o lo que se repite varias veces, se puede reemplazar por un audio ambiente más silencioso de la misma sesión de captura.

Una vez establecida la edición de vídeo de una ubicación, el diseñador de sonido puede sincronizar el audio correspondiente. En este punto, evaluaremos las capturas de sonido móvil y de la plataforma de cámara para decidir qué elementos funcionarían para crear una escena de audio envolvente. Encontramos útil colocar todos los elementos de sonido en un editor de audio y crear simuladores lineales rápidos para experimentar con distintas ideas de combinación. Este paso nos ha proporcionado mejores ideas sobre Cuándo llegó el momento de crear las escenas HoloTours reales.

### <a name="assemble-the-scene"></a>Ensamble de la escena

El primer paso para crear una escena ambiente 3D es crear una cama de sonidos de bucle de ambiente de fondo generales que admitan otras características y elementos de sonido interactivos en una escena. Tomamos un enfoque holístico de la implementación según lo determinen los criterios de diseño de cualquier escena determinada. Algunas escenas pueden indexar hacia el uso de la captura de cámara sincronizada. Un momento más "cinematográfico" podría requerir un enfoque seleccionada que se basa en sonidos, elementos interactivos y música colocados discretamente.

Cuando se indexa en el audio de captura de cámara, colocamos emisores de audio ambiente de ambiente habilitados para sonido espacial que se corresponden con la orientación direccional de las cámaras. La vista de cámara norte Reproduce audio desde el micrófono norte y, de forma similar, para las otras direcciones cardinales. Estos emisores están bloqueados mundialmente, lo que significa que, cuando el usuario cambie su cabezal con respecto a ellos, el sonido cambiará. Esta técnica modela de forma eficaz el sonido de la posición en esa ubicación. Escuche Piazza Navona o Pantheon para ver ejemplos de escenas que usan una buena combinación de audio capturado por cámara.

En un enfoque diferente, a veces se reproduce ambiente estéreo en bucle junto con los emisores de sonido espacial que se colocan alrededor de la escena. Estos emisores juegan un sonido único de volumen aleatorio, tono y frecuencia del desencadenador. Esta técnica crea ambiente que tiene un sentido mejorado de direccionalidad. En aguas Alienates, por ejemplo, puede oír cómo cada cuadrante de la panorámica tiene emisores específicos que resaltan áreas específicas de la geografía pero colaboran para crear un ambiente envolvente general.

## <a name="tips-and-tricks"></a>Sugerencias y trucos

Hay algunas maneras adicionales de resaltar la direccionalización y mejorar la inmersión para hacer un uso completo de las capacidades de sonido espacial de HoloLens. Hemos proporcionado una lista aquí. Escuche estos efectos la próxima vez que intente HoloTour.
* **Buscar destinos:** Estos sonidos se desencadenan cuando se observa un objeto o área específica del marco holográfica. Por ejemplo, mire hacia el café de la calle del Navona de Piazza de Roma para desencadenar sutilmente los sonidos de los restaurantes ocupados.
* **Visión local:** El viaje a través de HoloTour contiene ciertas "pulsaciones" en las que la guía del paseo, asistida por hologramas, explora un tema en profundidad. Por ejemplo, a medida que la fachada del Pantheon se resuelve para mostrar el Oculus, la reverberación de audio que se colocó como un emisor 3D desde dentro de la Pantheon anima al usuario a explorar el interior.
* **Direccionalidad mejorada:** En muchas escenas, colocamos sonidos de varias maneras para agregarlos a la direccionalidad. En la escena de Pantheon, por ejemplo, el sonido de la fuente se colocó como una emisora independiente lo suficientemente cerca del usuario que podía tener una idea de "Sonic Parallax" a medida que recorren el espacio de juego. En la escena de Salinas de Maras de Perú, los sonidos de los pocos flujos individuales se colocaban como emisores independientes para compilar un entorno ambiente más envolvente, lo que rodea al usuario con los sonidos auténticos de esa ubicación.
* **Emisor de Spline:** Estos emisores se mueven en el espacio 3D en relación con la posición visual del objeto al que están asociados. Un ejemplo es el tren en Machu Picchu, donde usamos un emisor de spline para dar una sensación distintiva de direccionalidad y movimiento.
* **Música y SFX:** Algunos aspectos de HoloTour que representan un enfoque más estilizado o cinematográfico usan música y efectos sonoros para aumentar el impacto emocional. En el combate Gladiator al final del paseo por la Roma, por ejemplo, los efectos especiales como whooshes y los separadores ayudan a fortalecer el efecto de las etiquetas que aparecen en segundo plano.

## <a name="see-also"></a>Consulta también
* [Sonido espacial](spatial-sound.md)
* [Diseño de sonido espacial](spatial-sound-design.md)
* [Sonido espacial en Unity](spatial-sound-in-unity.md)
* [Vídeo: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)
