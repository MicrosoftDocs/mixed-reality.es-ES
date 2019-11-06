---
title: Audio en realidad mixta
description: El audio en realidad mixta puede aumentar la confianza de los usuarios en las interacciones de la interfaz de usuario y sumergir a los usuarios en la experiencia.
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: sonido espacial, sonido envolvente, audio 3D, sonido 3D, audio espacial
ms.openlocfilehash: 1930017903439aee3ac53b6c4be344fdc44c356f
ms.sourcegitcommit: 2e54d0aff91dc31aa0020c865dada3ae57ae0ffc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2019
ms.locfileid: "73641116"
---
# <a name="audio-in-mixed-reality"></a>Audio en realidad mixta
El audio es una parte esencial del diseño y la productividad en la realidad mixta y puede:
* Aumentar la confianza del usuario en las interacciones basadas en gestos y en voz
* Guiar a los usuarios a pasos siguientes
* Combinar objetos virtuales de forma eficaz con el mundo real

El seguimiento de los cabezales de baja latencia de los auriculares de realidad mixta, incluido HoloLens, permite el uso de la espacialización basada en HRTF de alta calidad. La espacialización del audio en la aplicación puede:
* Llamar la atención sobre los elementos visuales
* Ayudar a los usuarios a mantener el conocimiento de su entorno del mundo real

La adición de acústicas conecta con mayor profundidad los hologramas al mundo mixto y puede proporcionar indicaciones sobre el entorno y el estado del objeto.

Para obtener ejemplos más detallados de diseño con audio, consulte [diseño de sonido](spatial-sound-design.md).

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
        <td><strong>Ofrecen</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></td>
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

## <a name="using-sounds-in-mixed-reality"></a>Usar sonidos en realidad mixta
El [uso de sonidos en la realidad mixta](spatial-sound-design.md) puede requerir un enfoque diferente que en las aplicaciones táctiles y de teclado y de mouse. Entre las decisiones clave de diseño sólido se incluyen los sonidos que se deben espaciales y las interacciones que se van a sonify. Estas decisiones pueden tener un efecto fuerte en la confianza de los usuarios, la productividad y la curva de aprendizaje.

### <a name="case-studies"></a>Casos prácticos
HoloTour virtualmente lleva a los usuarios a sitios turísticos e históricos en todo el mundo. En el siguiente caso práctico se describe el diseño de sonido de HoloTour: [diseño de sonido para HoloTour](case-study-spatial-sound-design-for-holotour.md). Se usó un micrófono y una configuración de representación especiales para capturar los espacios de asunto.

RoboRaid es un Reactivador de alta energía para HoloLens. En el caso práctico siguiente se describen las opciones de diseño que se han realizado para garantizar que el audio espacial se ha usado para obtener el máximo efecto drástico: [diseño de sonido para RoboRaid](case-study-using-spatial-sound-in-roboraid.md).

## <a name="spatialization"></a>Espacialización
La espacialización es el componente direccional del audio espacial. Cuando se usa una instalación de 7,1 Home Theater, la espacialización es tan sencilla como la panorámica entre altavoces de alta intensidad. Pero con los auriculares en realidad mixta es fundamental usar una tecnología basada en HRTF para obtener precisión y comodidad. Windows ofrece la espacialización basada en HRTF y esta compatibilidad se acelera mediante hardware en HoloLens 2.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a>¿Se debe Spatial?
Muchos sonidos en aplicaciones de realidad mixta se benefician de la espacialización, lo que saca un sonido del encabezado del agente de escucha y lo coloca en el mundo. Consulte [diseño de sonido espacial](spatial-sound-design.md) para obtener sugerencias sobre los usos más efectivos de la espacialización en la aplicación.

### <a name="spatializer-personalization"></a>Personalización de Spatializer
HRTFs manipulan las diferencias de nivel y fase entre los oídos en el espectro de frecuencias. Se basan en modelos físicos y medidas de las formas de cabeza humana, torso y EAR (pinnae). Nuestro cerebro responde a estas diferencias para dar lugar a una percepción de la dirección en sonido. 

Cada persona tiene una forma de lengüeta única, el tamaño del cabezal y la posición del oído, por lo que los mejores HRTFs son los que se ajustan a usted. HoloLens aumenta la precisión de la espacialización mediante el uso de la distancia entre pupilary (IPD) del casco que se muestra para ajustar el HRTFs para el tamaño de la cabeza.

### <a name="spatializer-platform-support"></a>Compatibilidad con la plataforma Spatializer
Windows ofrece la espacialización, incluido HRTFs, a través de la [API de ISpatialAudioClient](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound). Esta API expone la aceleración de hardware de HoloLens 2 HRTF a las aplicaciones.

### <a name="spatializer-middleware-support"></a>Compatibilidad con middleware de Spatializer
La compatibilidad con Windows ' HRTFs está disponible para algunos motores de audio de terceros:
* Un complemento del [motor de audio de Unity](spatial-sound-in-unity.md) llama a la HRTF XAPO
* Un [complemento de Wwise Audio Engine](https://www.audiokinetic.com/products/plug-ins/msspatial/) llama a la API ISpatialAudioClient

## <a name="acoustics"></a>Acústicas
El audio espacial puede ser más que una dirección. Otras dimensiones, como oclusión, obstrucción, reverberación, agrupación en el portal y modelos de origen, se conocen colectivamente como ' acústicas '. Sin acústica, los sonidos espaciales carecen de una distancia percibida.

El tratamiento acústico puede oscilar entre simple y muy complejo. Mediante el uso de una reverberación simple, como la que se admite en cualquier motor de audio, se pueden introducir sonidos espaciales en el entorno que rodea al agente de escucha. Los sistemas acústicos, como los [acústicos del proyecto](https://aka.ms/acoustics), ofrecen un tratamiento acústico más completo y atractivo. La acústica del proyecto puede modelar el efecto de las paredes, las puertas y otras geometrías de la escena en un sonido, y es una opción eficaz para los casos en los que se conoce la geometría de la escena correspondiente en tiempo de desarrollo.

