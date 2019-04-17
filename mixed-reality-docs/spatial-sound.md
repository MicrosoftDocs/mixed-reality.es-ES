---
title: Sonido espacial
description: Usar sonido espacial en una aplicación de realidad mixta permite colocar convincingly sonidos en un espacio 3D.
author: hak0n
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: sonido espacial, el sonido envolvente, audio 3d, audio de sonido, espacial 3d
ms.openlocfilehash: ccb236a8b53e757ba632a1c7c6cb2d4f07735910
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59600837"
---
# <a name="spatial-sound"></a>Sonido espacial

Cuando los objetos están fuera de la línea de visión, una de las maneras en que podemos percibimos qué está ocurriendo en torno a nosotros es a través de sonido. En Windows Mixed Reality, el motor de audio proporciona el componente de la experiencia de realidad mixta auditiva mediante la simulación de sonido en 3D con simulaciones del entorno, la distancia y dirección. Usar sonido espacial en una aplicación permite a los desarrolladores colocar convincingly sonidos en un espacio dimensional 3 (esfera) en todo el usuario. Los sonidos, a continuación, le resultará como si provinieran objetos físicos real o la hologramas realidad mixta en el entorno del usuario. Dado que [hologramas](hologram.md) están formados por objetos de luz y sonido a veces, el componente de sonido le ayuda a tierra hologramas hacerlos más solo y la creación de una experiencia más inmersiva.

Aunque hologramas solo pueden aparecer visualmente que señala la mirada del usuario, el sonido de la aplicación puede proceder de todas las direcciones; anteriormente, a continuación, subyacente, al lado, etcetera. Puede usar esta característica para llamar la atención sobre un objeto que no esté actualmente en la vista del usuario. Un usuario puede percibir sonidos para ser procedentes de un origen en el mundo de realidad mixta. Por ejemplo, el usuario que se aproxime a un objeto o el objeto que se aproxime a ellos, aumenta el volumen. De forma similar, como los objetos se mueven en torno a un usuario, o viceversa, sonidos espaciales sensación que sonidos proceden directamente desde el objeto.

<br>

>[!VIDEO https://www.youtube.com/embed/PTPvx7mDon4]

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Característica</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (gen 1)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"><a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>

<td> Sonido espacial</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️ (con auriculares)</td>

</tr>
</table>

## <a name="simulating-the-perceived-location-and-distance-of-sounds"></a>Simulación de la ubicación percibido y la distancia de sonidos

Analizando cómo sonido alcanza ambos nuestros oídos, nuestro cerebro determina la distancia y dirección del objeto emite el sonido. Un HRTF (o una función de transferencia de Head relacionados) simula esta interacción al modelar la respuesta espectral que caracteriza cómo un auricular recibe sonido desde un punto en el espacio. El motor de audio espacial usa HRTFs personalizadas para ampliar la experiencia de realidad mixta y simular los sonidos que proceden de varias instrucciones y las distancias.

<br>

>[!VIDEO https://www.youtube.com/embed/aB3TDjYklmo]

Pistas de audio izquierdo o derecho (azimuth) proceden de las diferencias en el tiempo de sonido llega a cada dispositivo de escucha. Subir y Bajar indicaciones proceden de espectrales cambios producidos por la forma de outer ear (pinnae). Mediante la designación de donde proviene audio, el sistema puede simular la experiencia de sonido que llegan en distintos momentos a nuestros oídos. Tenga en cuenta que en HoloLens, mientras spatialization azimuth personalizada, la simulación de elevación se basa en un conjunto de anthropometrics promedio. Por lo tanto, precisión de elevación puede ser menos precisa que la precisión azimuth.

Las características de sonidos también cambian según el entorno en que se encuentran. Por ejemplo, gritar en una Cueva hará que su voz rebote de las paredes, pisos y los límites máximos, y crear un efecto de eco. La configuración del modelo de sala de sonido espacial reproduce estas reflexiones para colocar los sonidos en un entorno concreto de audio. Puede usar esta opción para que coincida con la ubicación del usuario real para la simulación de sonidos en dicho espacio para crear una experiencia más inmersiva de audio.

## <a name="integrating-spatial-sound"></a>La integración de sonido espacial

Dado que es el principio general de la realidad mixta masa [hologramas](hologram.md) en el mundo físico al usuario o el entorno virtual, deben ser spatialized mayoría sonidos desde hologramas. En HoloLens, hay naturalmente CPU y memoria consideraciones de presupuesto, pero puede usar 10-12 espaciales sonidas voces existe durante el uso de menos de ~ 12% de la CPU (aproximadamente un 70% de uno de los cuatro núcleos). Uso recomendado de voces de sonido espaciales incluyen:
* Observación Mixing (resaltado en objetos, especialmente cuando fuera de la vista). Cuando un holograma necesita atención del usuario, reproducir un sonido en ese holograma (por ejemplo, tener una corteza perro virtual). Esto ayuda al usuario a encontrar el holograma cuando no está en la vista.
* Audio Haptics (audio reactiva para las interacciones sin roces). Por ejemplo, reproducir un sonido cuando el controlador del usuario mano o movimiento entra y sale del marco de movimiento. O bien, reproducir un sonido cuando el usuario selecciona un holograma.
* Inmersión (sonido de ambiente que rodean el usuario).

También es importante tener en cuenta que aunque fusión sonido espacial de sonido estéreo estándar puede ser eficaz para crear entornos reales, el sonido estéreo debe ser relativamente silencioso dejar espacio para los aspectos sutiles de sonido espacial, como reflejos ( las indicaciones de distancia) que puede ser difícil escuchar en un entorno ruidoso.

Motor de sonido espacial de Windows solo admite una velocidad de muestreo 48 k para la reproducción. La mayoría middleware, como Unity, automáticamente convertir archivos de sonido en el formato compatible, pero al utilizar directamente las API de Audio de Windows coincide con el formato del contenido en el formato admitido por el efecto.

## <a name="see-also"></a>Vea también
* [MR 220 espacial](holograms-220.md)
* [Sonido espacial en Unity](spatial-sound-in-unity.md)
* [Sonido espacial en DirectX](spatial-sound-in-directx.md)
* [Diseño espacial de sonido](spatial-sound-design.md)
