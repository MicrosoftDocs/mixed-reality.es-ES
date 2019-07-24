---
title: 'Caso práctico: diseño de sonido espacial para HoloTour'
description: Para crear un paseo virtual 3D realmente envolvente para Microsoft HoloLens, los vídeos panorámicos y los escenarios holográficas solo forman parte de la fórmula.
author: JSyltebo
ms.author: jsylte
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, HoloTour, sonido espacial, caso práctico
ms.openlocfilehash: eca675534dba12dd65a20fb9d85e4df57f725288
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63522448"
---
# <a name="case-study---spatial-sound-design-for-holotour"></a>Caso práctico: diseño de sonido espacial para HoloTour

Para crear un paseo virtual 3D realmente envolvente para Microsoft HoloLens, los vídeos panorámicos y los escenarios holográficas solo forman parte de la fórmula. El diseñador de audio Jason Syltebo habla sobre el modo en que se capturó y procesó el sonido para que se parezca que realmente está en cada una de las ubicaciones de HoloTour.

## <a name="the-tech"></a>La tecnología

Las atractivas imágenes y escenas holográficas que se ven en HoloTour son solo una parte de la creación de una experiencia de realidad mixta. Aunque los hologramas solo pueden aparecer visualmente delante de un usuario, la característica de [sonido espacial](spatial-sound.md) de HoloLens permite que el audio proviene de todas las direcciones, lo que proporciona al usuario una experiencia organoléptica más completa.

El sonido espacial nos permite proporcionar indicaciones de audio para indicar una dirección en la que el usuario debe activar, o para que el usuario sepa que hay más hologramas para que puedan verlos dentro de su espacio. También se puede adjuntar un sonido directamente a un holograma y actualizar continuamente la dirección y la distancia que el holograma es de un usuario para que parezca que el sonido proviene directamente de ese objeto.

Con HoloTour, queríamos aprovechar las capacidades de sonido espacial de HoloLens para crear un entorno ambiente de 360 grados, sincronizado con el vídeo para mostrar los resaltados de Sonic de ubicaciones específicas.

## <a name="behind-the-scenes"></a>En segundo plano

Creamos experiencias de HoloTour de dos ubicaciones diferentes: Roma y Machu Picchu. Para que estos paseos se sientan auténticos y atractivos, queríamos evitar el uso de sonidos genéricos y, en su lugar, captar audio directamente desde las ubicaciones en las que estábamos filmando.

### <a name="capturing-the-audio"></a>Captura del audio

En nuestro [caso práctico sobre la captura del contenido visual para HoloTour](case-study-capturing-and-creating-content-for-holotour.md), hablamos del diseño personalizado de la plataforma de la cámara. Constaba de 14 cámaras GoPro contenidas en una carcasa impresa en 3D, diseñada para las dimensiones específicas del trípode. Para capturar audio desde esta plataforma de pruebas, agregamos una matriz de micrófono cuádruple bajo las cámaras, que se incorporaron a una unidad de grabación de 4 canales compacta que se encuentra en la base del trípode. Hemos elegido los micrófonos que no solo se han realizado correctamente, pero que tenían una superficie muy pequeña, de modo que no tapaba la vista de la cámara.

![Plataforma de micrófono y de cámara personalizada](images/camera-rig-microphones-300px.png)<br>
*Plataforma de micrófono y de cámara personalizada*

Este programa de instalación capturó un sonido en cuatro direcciones desde la ubicación precisa de nuestra cámara, lo que nos proporciona información suficiente para volver a crear una panorámica aural 3D mediante el sonido espacial, que podríamos sincronizar posteriormente con el vídeo de 360 grados.

Uno de los desafíos del audio de la matriz de cámara es que depende de lo que se grabó en el momento de la captura. Incluso si la captura de vídeo es buena, la captura de sonido puede resultar problemática debido a los sonidos fuera de la cámara, como Sirens, aviones o altas vueltas. Para asegurarnos de que teníamos todos los elementos que necesitamos, usamos una serie de unidades de grabación móviles estéreo y mono para obtener elementos de ambiente asincrónicos en puntos de interés específicos en cada ubicación. Esta captura es importante, ya que proporciona al diseñador de sonido la capacidad de buscar contenido limpio y utilizable que se puede usar en la producción posterior para elaborar interés y agregar más direccionalidad.

Cualquier día de captura determinado generaría un gran número de archivos. Era importante desarrollar un sistema para realizar un seguimiento de qué archivos corresponden a una determinada ubicación o cámara. Nuestra unidad de grabación se configuró para asignar nombres a los archivos automáticamente por fecha y tomar el número, y realizaremos las copias de seguridad al final del día en las unidades externas. Como mínimo, es importante exponer el principio de las grabaciones de audio, ya que esto permite una sencilla identificación contextual del contenido en caso de que los nombres de archivo se conviertan en un problema. También era importante que nos pongamos en contacto visualmente con la captura de la plataforma de la cámara, ya que el vídeo y el audio se grabaron como medios independientes y debían sincronizarse durante la publicación.

### <a name="editing-the-audio"></a>Edición del audio

En el estudio después del viaje de captura, el primer paso en la creación de una experiencia de aural direccional y envolvente consiste en revisar toda la captura de audio de una ubicación, tomar las mejores tomas e identificar los resaltados que podrían aplicarse de forma creativa durante integrar. Después, el audio se edita y se limpia. Por ejemplo, una bocina de coche alto dura un segundo, o lo que se repite varias veces, se puede reemplazar y unir en secciones de audio de ambiente silencioso de la misma captura.

Una vez que se ha establecido la edición de vídeo de una ubicación, el diseñador de sonido puede sincronizar el audio correspondiente. En este punto, trabajamos con la captura de la plataforma de cámara y la captura móvil para decidir qué elementos, o combinarlos, funcionarán para crear una escena de audio envolvente. Una técnica que encontramos útil era agregar todos los elementos de sonido en un editor de audio y crear una maqueta de simulacros lineal rápida para experimentar con distintas ideas de combinación. Esto nos brindó mejores ideas en el momento de crear las escenas HoloTours reales.

### <a name="assembling-the-scene"></a>Montaje de la escena

El primer paso para crear una escena ambiente 3D es crear una cama de sonidos de bucle de ambiente de fondo generales que admitan otras características y elementos de sonido interactivos en una escena. Al hacerlo, se tomó un enfoque holístico hacia las distintas técnicas de implementación que se determinan según las necesidades específicas y los criterios de diseño de una determinada escena. Algunas escenas pueden indexar hacia el uso de la captura de cámara sincronizada, mientras que otras pueden requerir un enfoque más seleccionada que use sonidos colocados más discretos, elementos interactivos y música y efectos sonoros para los momentos más cinematográficos de HoloTour.

Al indexar sobre el uso del audio de captura de cámara, colocamos emisores de audio ambiente habilitados para sonido espacial que corresponden a las coordenadas direccionales de la orientación de la cámara, de modo que la vista de cámara norte Reproduce audio desde el micrófono norte y también para las demás direcciones cardinales. Estos emisores están bloqueados en todo el mundo, lo que significa que el usuario puede activar libremente el cabezal con respecto a estos emisores y el sonido cambiará en consecuencia, con lo que se modelará de forma eficaz el sonido de la posición en esa ubicación. Escuche Piazza Navona o Pantheon para ver ejemplos de escenas que usan una buena combinación de audio capturado de cámara.

Un enfoque diferente implicaba la reproducción de un ambiente estéreo de bucle en conjunción con los emisores de sonido espacial colocados en torno a la escena en la reproducción de sonidos de un solo uso aleatorios en términos de volumen, tono y frecuencia del desencadenador. Esto crea un ambiente con un sentido mejorado de direccionalidad. En aguas calientes, por ejemplo, puede escuchar cómo cada cuadrante de la panorámica tiene emisores específicos que resaltan intencionadamente áreas específicas de la geografía, pero colaboran para crear un ambiente envolvente general.

## <a name="tips-and-tricks"></a>Sugerencias y trucos

Al reunir audio para una escena, hay algunos métodos adicionales que puede usar para resaltar más la direccionalidad y la inmersión, lo que hace un uso completo de las capacidades de sonido espacial de HoloLens. Se proporciona una lista de algunos de los siguientes, que se escuchan la próxima vez que se intenta HoloTour.
* **Buscar destinos**: Estos son sonidos que solo se desencadenan cuando se está mirando un objeto o área específica del marco holográfica. Por ejemplo, si mira la dirección del café de la calle del Piazza Navona de Roma, se desencadenarán sutilmente los sonidos de un restaurante ocupado.
* **Visión local**: El viaje a través de HoloTour contiene ciertas pulsaciones en las que su guía de paseo, asistida por hologramas, explorará un tema en profundidad. Por ejemplo, a medida que la fachada del Pantheon se resuelve para mostrar el Oculus, la reverberación de audio colocada como un emisor 3D desde el interior de la Pantheon anima al usuario a explorar el modelo interior.
* **Direccionalidad mejorada**: En muchas escenas, colocamos sonidos de varias maneras para agregarlos a la direccionalidad. En la escena de Pantheon, por ejemplo, el sonido de la fuente se colocó como una emisora independiente lo suficientemente cerca del usuario para que pudiera tener una idea de "Sonic Parallax", ya que recorren el espacio de la reproducción. En la escena de Salinas de Maras, la perspectiva individual de algunos de los pocos flujos se colocaba como emisores independientes para crear un entorno ambiente más envolvente, lo que rodea al usuario con los sonidos auténticos de esa ubicación.
* **Emisor de spline**: Este emisor de sonido espacial especial se mueve en el espacio 3D con respecto a la posición visual del objeto al que está asociado. Un ejemplo de esto era el tren en Machu Picchu, donde usamos un emisor de spline para dar una sensación distintiva de direccionalidad y movimiento.
* **Música y SFX**: Algunos aspectos de HoloTour que representan un enfoque más estilizado o cinematográfico usan música y efectos sonoros para aumentar el impacto emocional. En la batalla de Gladiator al final del paseo de Roma, se usaron efectos especiales como whooshes o los separadores para ayudar a fortalecer el efecto de las etiquetas que aparecen en segundo plano.

## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Jason Syltebo" width="60" height="60" src="images/syltebo.png"></td>
<td style="border-style: none"><b>Jason Syltebo</b><br>Diseñador de audio@Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vea también
* [Sonido espacial](spatial-sound.md)
* [Diseño de sonido espacial](spatial-sound-design.md)
* [Sonido espacial en Unity](spatial-sound-in-unity.md)
* [MR espacial 220](holograms-220.md)
* [Vídeo: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)

 
