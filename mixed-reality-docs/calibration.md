---
title: Curva
description: La calibración de IPD (Interpupillary Distance) puede mejorar la calidad de los objetos visuales. Tanto HoloLens como Windows Mixed Reality con micrófonos que se incluyen en la realidad ofrecen maneras de personalizar IPD.
author: xerxesb85
ms.author: xerxesb
ms.date: 02/24/2019
ms.topic: article
keywords: calibración, confort, objetos visuales, calidad, IPD
ms.openlocfilehash: 5f8e6aef1df0efe4c64c807e627f69c7949363f2
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974801"
---
# <a name="improve-visual-quality-and-comfort"></a>Mejore la calidad visual y la comodidad
HoloLens, HoloLens 2 y Windows Mixed Reality con auriculares de gran rendimiento ofrecen diferentes maneras de mejorar la calidad de la experiencia visual. 

## <a name="hololens"></a>HoloLens

La calibración de IPD (Interpupillary Distance) puede mejorar la calidad de los objetos visuales.

### <a name="during-setup"></a>Durante la instalación

![Pantalla de alineación con el dedo de IPD en el segundo paso](images/ipd-finger-alignment-300px.jpg)<br>

*Pantalla de alineación con el dedo de IPD en el segundo paso*

En HoloLens, se le pedirá que calibre los objetos visuales durante la instalación. Esto permite que el dispositivo ajuste la presentación del holograma según la [distancia de Interpupillary](https://en.wikipedia.org/wiki/Interpupillary_distance) del usuario (IPD). Con un IPD incorrecto, los hologramas pueden aparecer inestables o en una distancia incorrecta.

Una vez que Cortana se introduce a sí mismo, el primer paso de configuración es la calibración. Se recomienda completar el paso de calibración durante esta fase de configuración, pero se puede omitir esperando a que Cortana le pida que indique "SKIP" para continuar.

A los usuarios se les pide que alineen su dedo con una serie de seis destinos por ojo. A través de este proceso, HoloLens establece el IPD correcto para el usuario. Si la calibración debe actualizarse o ajustarse para un nuevo usuario, se puede ejecutar fuera de la instalación mediante la aplicación de calibración.

### <a name="calibration-app"></a>Aplicación de calibración

La calibración puede realizarse en cualquier momento a través de la aplicación de calibración. La aplicación de calibración se instala de manera predeterminada y se puede acceder a ella desde el menú Inicio o a través de la aplicación de configuración. Se recomienda la calibración si desea mejorar la calidad de los objetos visuales o para calibrar los objetos visuales para un nuevo usuario.

**Iniciar la aplicación desde el inicio**
1. Use la [floración](gestures.md#bloom) para ir al [menú Inicio](navigating-the-windows-mixed-reality-home.md#start-menu).
2. Seleccione **+** esta información para ver todas las aplicaciones.
3. **Calibración**de inicio.

![Acceso a la aplicación de calibración desde el shell](images/calibration-shell.png)

![La aplicación de calibración que se muestra como un cubo activo después de iniciarse](images/calibration-livecube-200px.png)

**Inicio de la aplicación desde la configuración**
1. Use la [floración](gestures.md#bloom) para ir al [menú Inicio](navigating-the-windows-mixed-reality-home.md#start-menu).
2. Seleccione **+** esta opción para ver todas las aplicaciones si la **configuración** no está anclada para iniciarse.
3. **Configuración**de inicio.
4. Vaya a**utilidades** **del sistema** > y seleccione **abrir calibración**.

![Inicio de la aplicación de calibración desde la aplicación de configuración](images/calibration-settings-500px.jpg)

## <a name="hololens-2"></a>HoloLens 2

### <a name="calibration"></a>Curva 

En HoloLens 2, se le pedirá que calibre los objetos visuales durante la configuración del dispositivo. Se pide a los usuarios que examinen el conjunto de destinos de fijación. Esto permite que el dispositivo ajuste la representación del holograma para el usuario con el fin de garantizar un holograma colocado con precisión, una experiencia de visualización 3D más cómoda y una calidad de presentación mejorada. Todos los ajustes se producen sobre la marcha sin necesidad de una optimización manual. 

### <a name="calibration-when-sharing-a-device"></a>Calibración al compartir un dispositivo 

El dispositivo Hololens 2 puede compartirse entre personas, sin necesidad de que cada persona pase a través de la configuración del dispositivo. Hololens 2 le pedirá al usuario que calibre los objetos visuales cuando el dispositivo se coloque en el cabezal, si el usuario es nuevo en el dispositivo. Si el usuario ya ha calibrado los objetos visuales en el dispositivo, la pantalla se ajustará sin problemas para ofrecer una experiencia de visualización óptima y cómoda cuando el usuario coloque el dispositivo en el cabezal.  

### <a name="launching-the-calibration-app-from-settings"></a>Inicio de la aplicación de calibración desde la configuración
1. Use el gesto de inicio para ir al menú Inicio.
2. Seleccione **+** esta opción para ver todas las aplicaciones si la **configuración** no está anclada para iniciarse.
3. **Configuración**de inicio.
4. Vaya a**utilidades** **del sistema** > y seleccione **abrir calibración**.

## <a name="immersive-headsets"></a>Cascos envolventes

Para cambiar IPD dentro de los auriculares, abra la aplicación de configuración y vaya a la**pantalla de casco** de **realidad** > mixta y mueva el control deslizante. Verá los cambios en tiempo real en el casco. Si conoce el IPD, quizás desde una visita a Optometrist, puede escribirlo directamente.

También puede ajustar esta configuración; para ello, vaya a **configuración** > de la**pantalla de casco** de**realidad** > mixta en su PC.

Si el casco no admite la personalización de IPD, se deshabilitará esta configuración.

## <a name="see-also"></a>Vea también
* [Consideraciones acerca del entorno en HoloLens](environment-considerations-for-hololens.md)
