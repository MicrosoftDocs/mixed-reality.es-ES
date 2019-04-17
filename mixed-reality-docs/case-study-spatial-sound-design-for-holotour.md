---
title: 'Caso práctico: diseño espacial de sonido para HoloTour'
description: Para crear una visita virtual 3D envolvente realmente para Microsoft HoloLens, los vídeos panorámicas y holográfica paisajes son solo una parte de la fórmula.
author: JSyltebo
ms.author: jsylte
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, HoloLens, HoloTour, estudio de sonido, case espacial
ms.openlocfilehash: eca675534dba12dd65a20fb9d85e4df57f725288
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605463"
---
# <a name="case-study---spatial-sound-design-for-holotour"></a>Caso práctico: diseño espacial de sonido para HoloTour

Para crear una visita virtual 3D envolvente realmente para Microsoft HoloLens, los vídeos panorámicas y holográfica paisajes son solo una parte de la fórmula. Diseñador de audio que Jason Syltebo habla acerca de cómo sonido se capturan y procesan para hacerla sentir como que está realmente en cada una de las ubicaciones en HoloTour.

## <a name="the-tech"></a>La tecnología

Las imágenes bonitas y holográficas escenas que ve en HoloTour son solo una parte de la creación de una experiencia de realidad mixta solo. Aunque solo pueden aparecer hologramas visualmente delante de un usuario, el [sonido espacial](spatial-sound.md) característica de HoloLens permite audio proceder de todas las direcciones, que proporciona al usuario una experiencia más completa sensorial.

Sonido espacial nos permite proporcionar pistas de sonido para indicar una dirección en la que el usuario debe activar o permitir que el usuario sabe que hay más hologramas para que vean dentro de su espacio. Podemos adjuntar también un sonido directamente a un holograma y actualizar continuamente la dirección y la distancia que del holograma es de un usuario para hacer parecer como si el sonido procede directamente de ese objeto.

Con HoloTour, queríamos aprovechar las ventajas de las funciones espaciales sonidas de HoloLens para crear un entorno de ambiente de 360 grados, sincronizado con el vídeo para revelar los aspectos destacados sonic de ubicaciones específicas.

## <a name="behind-the-scenes"></a>En segundo plano

Creamos experiencias HoloTour de dos ubicaciones diferentes: Roma y Machu Pichu. Para que estos paseos sienta auténticos y atractivas queríamos evitar el uso de genéricos sonidos y en su lugar, capturar audio directamente desde las ubicaciones donde nos estábamos grabación.

### <a name="capturing-the-audio"></a>Captura de audio

En nuestro [caso práctico acerca de cómo capturar el contenido visual para HoloTour](case-study-capturing-and-creating-content-for-holotour.md), hablamos sobre el diseño personalizado de nuestra plataforma de cámara. Constaba de 14 cámaras GoPro contenidas en una carcasa impresa en 3D, diseñado para las dimensiones específicas de la trípode. Para capturar audio desde esta plataforma de pruebas, hemos agregado una matriz de cuatro micrófono debajo de las cámaras, que se introducen en una unidad de grabación de 4 canales compact sat en la base de la trípode. Elegimos micrófonos que no sólo realizan y, al tiempo que suponía una superficie muy pequeña, con el fin de no occlude la vista de la cámara.

![Plataforma de cámara y micrófono personalizado](images/camera-rig-microphones-300px.png)<br>
*Plataforma de cámara y micrófono personalizado*

Esta configuración captura los sonidos de cuatro direcciones de la ubicación exacta de la cámara, que nos da información suficiente para volver a crear una panorámica auditiva 3D con sonido espacial, que nos podríamos sincronizar más adelante en el vídeo de 360 grados.

Uno de los desafíos con el audio de la matriz de cámara es que está a merced de lo que está registrado en el momento de captura. Incluso si la captura de vídeo es correcta, la captura de sonido puede resultar problemática debido a los sonidos de desactivar cámara como sirenas, aviones o vientos alta. Para asegurarse de que teníamos todos los elementos que necesitamos, hemos usado una serie de unidades de grabación móviles estéreo y mono para obtener elementos de ambientales, asincrónicos en puntos específicos de interés en cada ubicación. Esta captura es importante ya que proporciona al diseñador de sonido, la capacidad para buscar contenido limpio y utilizable que puede usarse en posteriores a la producción para crear interés y permite agregar más direccionalidad.

Cualquier día dado captura generaría un gran número de archivos. Era importante desarrollar un sistema para realizar un seguimiento de los archivos que corresponden a una ubicación determinada o una cámara captura. Nuestra unidad de grabación está establecido en archivos de nombre automático por fecha y número de take y se podrían realizar estas copias al final del día a las unidades externas. Como mínimo, verbalmente slating el principio de grabaciones de audio era importante, ya que esto permite facilitar su identificación contextual del contenido de los nombres de archivo deben convertirse en un problema. También era importante para nosotros Pizarra visualmente la captura de cámara plataforma como el vídeo y audio se registran como medios independientes y es necesario que se sincronizan durante la publicación.

### <a name="editing-the-audio"></a>Edición de audio

Volver al studio después de la captura de ida y vuelta, el primer paso para ensamblar una experiencia auditiva de dirección y envolvente es para revisar todos para una ubicación, la mejor toma de selección e identificar cualquier información destacada que se pueden aplicar de forma creativa durante la captura de audio integración. El audio, a continuación, se puede editar y limpia. Por ejemplo, un cuerno de automóvil alto que duran un segundo o algo así y repetir varias veces, se puede reemplazar y van a unir con secciones de audio silenciosa, ambiente de la misma captura.

Una vez que se ha establecido la edición de vídeo para una ubicación del Diseñador de sonido puede sincronizar el audio correspondiente. En este momento, hemos trabajado con captura de la plataforma de pruebas de cámara y captura móvil para decidir qué elementos o combinación de ellos, que funcionará para crear una escena de sonido envolvente. Una técnica que se han encontrado útiles consistió en Agregar todos los elementos de sonido en un audio editor y compilación rápida lineal ficticios SAI (UPS) para experimentar con ideas de combinación diferente. Esto nos dio mejor formados ideas cuando llegó el momento de compilar las escenas HoloTour reales.

### <a name="assembling-the-scene"></a>Montaje de la escena

El primer paso para crear una escena 3D ambiente es crear una cama de ambiente sonidos bucle general en segundo plano que será compatible con otras características y los elementos interactivos de sonido en una escena. En este modo, se tomó un enfoque integral hacia técnicas de implementación diferente según las necesidades específicas y los criterios de diseño de cualquier escena concreta. Algunos escenas podrían indizar hacia el uso de la captura de cámara sincronizado, mientras que otros pueden requerir un enfoque más elaborado que usa más de forma discreta coloca sonidos, elementos interactivos y música y efectos de sonido durante los momentos más cinematográficas en HoloTour.

Al realizar la indización en el uso de la captura de audio de cámara, hemos colocado espaciales habilitada sonido ambientales audio emisores correspondientes a las coordenadas de la orientación de la cámara direccionales tal que la vista de la cámara Norte reproduce audio del micrófono Norte igualmente, para las direcciones cardinales. Estos emisores son world-bloqueado, lo que significa que el usuario puede activar libremente su cabeza en relación con estos emisores y el sonido cambiará en consecuencia, modelado de forma eficaz el sonido del pie en esa ubicación. Escuchar Piazza Navona o el de Pantheon para obtener ejemplos de segundo plano que usan una combinación válida de audio de captura de cámara.

Un enfoque diferente implicada reproducción de un bucle ambiente estéreo junto con los emisores de sonido espaciales a alrededor de la escena de reproducción de sonidos de uso único que son aleatorios en términos de frecuencia de volumen, el cabeceo y el desencadenador. Esto crea un ambiente con una mayor sensación de direccionalidad. Por ejemplo, en Aguas Calientes, puede escuchar cómo cada cuadrante del panorama tiene emisores específicos que intencionadamente resaltan áreas específicas de la geografía, pero funcionan conjuntamente para crear un ambiente general envolvente.

## <a name="tips-and-tricks"></a>Sugerencias y trucos

Cuando va a colocar juntos audio de una escena, hay algunos métodos adicionales que puede usar para resaltar aún más la direccionalidad e inmersión, hacer un gran uso de las capacidades de sonido espaciales de HoloLens. Hemos proporcionado una lista de algunas, a continuación, escuchar la próxima vez que intente HoloTour.
* **Buscar destinos**: Estos son los sonidos que desencadenen solo cuando se encuentre ante un objeto específico o un área del marco holográfico. Por ejemplo, la busca en la dirección de la calle lado café en Piazza Navona del Roma sutilmente desencadenará los sonidos de un restaurante ocupado.
* **Visión local**: El recorrido aunque HoloTour contiene ciertas pulsaciones que guía el paseo, programe hologramas, explorará un tema en profundidad. Por ejemplo, la fachada de la Pantheon fundidos para revelar el oculus, paso audio con reverberación coloca como un emisor desde el interior de la Pantheon 3D fomenta el usuario para explorar el modelo interior.
* **Mejorado direccionalidad**: En muchos de los bastidores, se colocan sonidos de varias maneras para agregar a la direccionalidad. Por ejemplo, en la escena de Pantheon, se colocó el sonido de la fuente lo más cerca de un emisor independiente lo suficiente como para el usuario, por lo que podría hacerse una idea de 'sonic paralaje' como guiaba en todo el espacio de juego. En la escena de Salinas de Maras de Perú, se colocó la perspectiva de algunas de las secuencias poco individual como emisores independientes para crear un entorno más amplias de ambiente, que rodea el usuario con los sonidos auténticos de esa ubicación.
* **Emisor de spline**: Mueve este emisor sonido espacial especial en el espacio 3D en relación con la posición del objeto que está conectado a visual. Un ejemplo de esto fue el tren en Machu Pichu, donde se usa un emisor de spline para dar una sensación de movimiento y la direccionalidad distinta.
* **Música y SFX**: Ciertos aspectos de HoloTour que representan un enfoque más estilizado o cinematográfico utilizan música y efectos de sonido a fin de aumentar el impacto. En la batalla gladiator al final del paseo Roma, efectos especiales, como whooshes o stingers se usaron para ayudar a reforzar el efecto de las etiquetas que aparecen en segundo plano.

## <a name="about-the-author"></a>Acerca del autor

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Jason Syltebo" width="60" height="60" src="images/syltebo.png"></td>
<td style="border-style: none"><b>Jason Syltebo</b><br>Diseñador de audio @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>Vea también
* [Sonido espacial](spatial-sound.md)
* [Diseño espacial de sonido](spatial-sound-design.md)
* [Sonido espacial en Unity](spatial-sound-in-unity.md)
* [MR 220 espacial](holograms-220.md)
* [Vídeo: Microsoft HoloLens: HoloTour](https://www.youtube.com/watch?v=pLd9WPlaMpY)

 
