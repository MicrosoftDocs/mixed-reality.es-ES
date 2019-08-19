---
title: Sonido espacial
description: El uso de sonido espacial en una aplicación de realidad mixta permite colocar sonidos de forma convincente en un espacio 3D.
author: hak0n
ms.author: hakons
ms.date: 03/21/2018
ms.topic: article
keywords: sonido espacial, sonido envolvente, audio 3D, sonido 3D, audio espacial
ms.openlocfilehash: a30a484c4e47593556fbd1786158262551e11d22
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829917"
---
# <a name="spatial-sound"></a>Sonido espacial

Cuando los objetos se encuentran fuera de nuestra línea de visión, una de las formas en las que podemos percibir qué está ocurriendo en torno a nosotros es el sonido. En Windows Mixed Reality, el motor de audio proporciona el componente aural de la experiencia de realidad mixta mediante la simulación de un sonido 3D mediante simulaciones de dirección, distancia y entorno. El uso de un sonido espacial en una aplicación permite a los desarrolladores colocar los sonidos de forma convincente en un espacio tridimensional (esfera) alrededor del usuario. Después, esos sonidos parecerán como si provinieran de objetos físicos reales o los hologramas de realidad mixta en el entorno del usuario. Dado que los [hologramas](hologram.md) son objetos que se componen de luz y a veces sonido, el componente de sonido ayuda a los hologramas de la base y a crear una experiencia más envolvente.

Aunque los hologramas solo pueden aparecer visualmente donde apunta la mirada del usuario, el sonido de la aplicación puede proviene de todas las direcciones. por encima, por debajo, en segundo plano, etc. Puede usar esta característica para atraer la atención a un objeto que no esté actualmente en la vista del usuario. Un usuario puede percibir sonidos para que procedan de un origen en el mundo de la realidad mixta. Por ejemplo, a medida que el usuario se acerca a un objeto o el objeto se acerca a ellos, aumenta el volumen. Del mismo modo, a medida que los objetos se mueven por un usuario, o viceversa, los sonidos espaciales proporcionan la ilusión de que los sonidos provienen directamente del objeto.

<br>

>[!VIDEO https://www.youtube.com/embed/PTPvx7mDon4]

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Característica</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Sonido espacial</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (con auriculares)</td>
    </tr>
</table>

## <a name="simulating-the-perceived-location-and-distance-of-sounds"></a>Simulación de la ubicación percibida y la distancia de los sonidos

Mediante el análisis de cómo llega el sonido a nuestros oídos, nuestro cerebro determina la distancia y la dirección del objeto que emite el sonido. Un HRTF (o una función de transferencia relacionada con el encabezado) simula esta interacción mediante el modelado de la respuesta espectral que caracteriza el modo en que una lengüeta recibe sonido de un punto en el espacio. El motor de audio espacial usa HRTFs personalizados para expandir la experiencia de realidad mixta y simular sonidos que provienen de varias direcciones y distancias.

<br>

>[!VIDEO https://www.youtube.com/embed/aB3TDjYklmo]

Las señales de audio izquierda o derecha (Azimuth) proceden de las diferencias en el momento en que llega el sonido en cada oído. Las pilas de arriba y abajo se originan a partir de los cambios espectrales generados por la forma auricular externa (pinnae). Al designar desde dónde proviene el audio, el sistema puede simular la experiencia de sonido que llega en diferentes momentos a nuestros oídos. Tenga en cuenta que en HoloLens, aunque la espacialización Azimuth está personalizada, la simulación de elevación se basa en un conjunto medio de anthropometrics. Por lo tanto, la precisión de la elevación puede ser menos precisa que la precisión de Azimuth.

Las características de los sonidos también cambian en función del entorno en el que existen. Por ejemplo, Shouting en un Cave hará que la voz rebote las paredes, suelos y techos, lo que crea un efecto de eco. La configuración del modelo Room de sonido espacial reproduce estos reflejos para colocar sonidos en un entorno de audio determinado. Puede usar esta opción para hacer coincidir la ubicación real del usuario con la simulación de sonidos en ese espacio para crear una experiencia de audio más envolvente.

## <a name="integrating-spatial-sound"></a>Integración de sonido espacial

Dado que el principio general de la realidad mixta es el [holograma](hologram.md) en el mundo físico o el entorno virtual del usuario, la mayoría de los sonidos de los hologramas deben estar espaciales. En HoloLens, existen consideraciones de uso natural de la CPU y de la memoria, pero puede usar las voces de sonido espacial 10-12 allí mientras usa menos del 12% de la CPU (~ 70% de uno de los cuatro núcleos). El uso recomendado para las voces de sonido espacial incluye:
* Combinación de comiras (objetos, especialmente cuando está fuera de la vista). Cuando un holograma necesita la atención de un usuario, reproducir un sonido en dicho holograma (por ejemplo, tener una corteza de perro virtual). Esto ayuda al usuario a encontrar el holograma cuando no está en la vista.
* Audio hápticos (audio reactivo para interacciones sin tocar). Por ejemplo, reproducir un sonido cuando el controlador de movimiento o la mano del usuario entra y sale del marco de gestos. O bien, reproducir un sonido cuando el usuario selecciona un holograma.
* Inmersión (sonido ambiente alrededor del usuario).

También es importante tener en cuenta que, aunque la combinación de sonidos estéreo estándar con sonido espacial puede ser eficaz en la creación de entornos realistas, los sonidos estéreo deben ser relativamente tranquilos para dejar espacio para los sutiles aspectos del sonido espacial, como reflexiones ( indicaciones de distancia) que pueden ser difíciles de oír en un entorno ruidoso.

El motor de sonido espacial de Windows solo admite una velocidad de muestreo de 48k para la reproducción. La mayoría de middleware, como Unity, convertirá automáticamente los archivos de sonido en el formato admitido, pero cuando use las API de audio de Windows directamente, haga coincidir el formato del contenido con el formato admitido por el efecto.

## <a name="see-also"></a>Vea también
* [MR espacial 220](holograms-220.md)
* [Sonido espacial en Unity](spatial-sound-in-unity.md)
* [Sonido espacial en DirectX](spatial-sound-in-directx.md)
* [Diseño de sonido espacial](spatial-sound-design.md)
