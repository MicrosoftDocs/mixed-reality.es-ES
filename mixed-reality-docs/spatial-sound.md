---
title: Audio en realidad mixta
description: El audio en realidad mixta puede aumentar la confianza de los usuarios en las interacciones de la interfaz de usuario y sumergir a los usuarios en la experiencia.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: sonido espacial, sonido envolvente, audio 3D, sonido 3D, audio espacial
ms.openlocfilehash: b939433daf80a95a11bc0e1ac2ffd75dfe0cf299
ms.sourcegitcommit: 8bf7f315ba17726c61fb2fa5a079b1b7fb0dd73f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2019
ms.locfileid: "75181985"
---
# <a name="audio-in-mixed-reality"></a>Audio en realidad mixta
El audio es una parte esencial del diseño y la productividad en la realidad mixta. El sonido puede:
* Aumentar la confianza del usuario en las interacciones de gestos y voz.
* Guiar a los usuarios a pasos siguientes.
* Combinar objetos virtuales de forma eficaz con el mundo real.

El seguimiento de los cabezales de baja latencia de los auriculares de realidad mixta, incluido HoloLens, admite la espacialización basada en HRTF de alta calidad. Puede espacialar el audio de la aplicación para:
* Llame la atención a los elementos visuales.
* Ayudar a los usuarios a mantener el conocimiento de su entorno real.

Las acústicas conectan con mayor profundidad los hologramas al mundo de la realidad mixta. Proporciona indicaciones sobre el entorno y el estado de los objetos.

Vea ejemplos detallados [de diseño que usa audio](spatial-sound-design.md).

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

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
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (primera generación)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Espacialización</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Aceleración de hardware de la espacialización</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="use-of-sounds-in-mixed-reality"></a>Uso de sonidos en realidad mixta
El [uso de sonidos en la realidad mixta](spatial-sound-design.md) requiere un enfoque diferente que en aplicaciones táctiles y de teclado y de mouse. Entre las decisiones clave de diseño sólido se incluyen los sonidos que se deben espaciales y las interacciones que se van a sonify. Estas decisiones afectan seriamente a la confianza de los usuarios, la productividad y la curva de aprendizaje.

### <a name="case-studies"></a>Casos prácticos
HoloTour virtualmente lleva a los usuarios a sitios turísticos e históricos en todo el mundo. Vea el caso práctico [de diseño de sonido para HoloTour](case-study-spatial-sound-design-for-holotour.md) . Se usó un micrófono y una configuración de representación especiales para capturar los espacios de asunto.

RoboRaid es un Reactivador de alta energía para HoloLens. En el caso práctico [de diseño de RoboRaid](case-study-using-spatial-sound-in-roboraid.md) , se describen las opciones de diseño que se realizaron para garantizar el uso del audio espacial al efecto más drástico.

## <a name="spatialization"></a>Espacialización
La espacialización es el componente direccional del audio espacial. En el caso de una instalación de 7,1 Home Theater, la espacialización es tan sencilla como la panorámica entre los altavoces. Sin embargo, en el caso de los auriculares mixtos, es fundamental usar una tecnología basada en HRTF para obtener precisión y comodidad. Windows ofrece la espacialización basada en HRTF y esta compatibilidad se acelera mediante hardware en HoloLens 2.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a>¿Se debe Spatial?
La espacialización puede mejorar muchos sonidos en aplicaciones de realidad mixta. La espacialización saca un sonido del encabezado del agente de escucha y lo coloca en el mundo. Para obtener sugerencias sobre el uso eficaz de la espacialización en la aplicación, consulte [diseño de sonido espacial](spatial-sound-design.md).

### <a name="spatializer-personalization"></a>Personalización de Spatializer
HRTFs manipulan las diferencias de nivel y fase entre los oídos en el espectro de frecuencias. Se basan en modelos físicos y medidas de las formas de cabeza humana, torso y EAR (pinnae). Nuestro cerebro responde a estas diferencias para proporcionar una dirección perceptible en el sonido.

Cada persona tiene una forma de EAR única, el tamaño del cabezal y la posición del oído. Por lo tanto, el mejor HRTFs es su utilidad. Para aumentar la precisión de la espacialización, HoloLens usa la distancia entre pupilary (IPD) del casco que se muestra para ajustar el HRTFs para el tamaño de la cabeza.

### <a name="spatializer-platform-support"></a>Compatibilidad con la plataforma Spatializer
Windows ofrece la espacialización, incluido HRTFs, a través de la [API de ISpatialAudioClient](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound). Esta API expone la aceleración de hardware de HoloLens 2 HRTF a las aplicaciones.

### <a name="spatializer-middleware-support"></a>Compatibilidad con middleware de Spatializer
La compatibilidad con Windows ' HRTFs está disponible para los siguientes motores de audio de terceros.
* Un [complemento de motor de audio de Unity](spatial-sound-in-unity.md)
* Un [complemento de Wwise Audio Engine](https://www.audiokinetic.com/products/plug-ins/msspatial/)

## <a name="acoustics"></a>Acústicas
El audio espacial está sobre más que la dirección. Otras dimensiones incluyen las oclusión, los obstáculos, la reverberación, el portal y el modelado de origen. Colectivamente, estas dimensiones se denominan *acústicas*. Sin acústica, los sonidos espaciales carecen de distancia aparente.

Los tratamientos acústicos van desde simple a muy complejo. Puede usar una reverberación simple compatible con cualquier motor de audio para enviar sonidos espaciales en el entorno del agente de escucha. Los sistemas acústicos, como los [acústicos del proyecto](https://aka.ms/acoustics) , proporcionan un tratamiento acústico más rico y atractivo. Los sonidos acústicos del proyecto pueden modelar el efecto de las paredes, las puertas y otras geometrías de la escena en un sonido. Es una opción eficaz para los casos en los que la geometría de la escena pertinente se conoce en tiempo de desarrollo.

## <a name="next-steps"></a>Pasos siguientes
- [Sonido espacial en Unity](spatial-sound-in-unity.md)
- [Cómo usar sonido en aplicaciones de realidad mixta](spatial-sound-design.md)
