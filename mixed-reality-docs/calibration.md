---
title: Calibración
description: Calibrar la IPD (distancia interpupillary) puede mejorar la calidad de los objetos visuales. HoloLens y Windows Mixed Reality inmersivos ofrecen formas de personalizar IPD.
author: xerxesb85
ms.author: xerxesb
ms.date: 02/24/2019
ms.topic: article
keywords: calibración, comodidad, los objetos visuales, calidad, ipd
ms.openlocfilehash: 91af069bc4ae5e49d9eb9c529f0d0db7b1567fc8
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605722"
---
# <a name="calibration"></a>Calibración

Calibrar la IPD (distancia interpupillary) puede mejorar la calidad de los objetos visuales. HoloLens y Windows Mixed Reality inmersivos ofrecen formas de personalizar IPD.

## <a name="hololens"></a>HoloLens

### <a name="during-setup"></a>Durante la instalación

![Pantalla IPD alineación del dedo en el segundo paso](images/ipd-finger-alignment-300px.jpg)<br>

*Pantalla IPD alineación del dedo en el segundo paso*

En HoloLens, se le pedirá a calibrar los objetos visuales durante la instalación. Esto permite que el dispositivo ajustar pantalla holograma según el usuario [interpupillary distancia](https://en.wikipedia.org/wiki/Interpupillary_distance) (IPD). Con un IPD incorrecta, pueden aparecer hologramas inestable o a una distancia incorrecta.

Después de que Cortana presenta a sí mismo, el primer paso de instalación es calibración. Se recomienda que complete el paso de calibración durante esta fase de instalación, pero puede omitirse mediante la espera hasta que Cortana le pedirá que diga "Omitir" para continuar.

Se piden a los usuarios para alinear sus dedos con una serie de seis destinos por efecto de ojos. Mediante este proceso, HoloLens establece la IPD correcta para el usuario. Si la calibración deba actualizarse o ajustado para un nuevo usuario, se puede ejecutar fuera de la instalación mediante la aplicación de calibración.

### <a name="calibration-app"></a>Aplicación de calibración

Calibración se puede realizar en cualquier momento a través de la aplicación de calibración. La aplicación de calibración se instala de forma predeterminada y puede obtenerse acceso desde el menú Inicio o a través de la aplicación de configuración. Se recomienda la calibración si desea mejorar la calidad de los objetos visuales o calibrar los objetos visuales de un nuevo usuario.

**Iniciar la aplicación de inicio**
1. Use [bloom](gestures.md#bloom) para llegar a [menú Inicio](navigating-the-windows-mixed-reality-home.md#start-menu).
2. Seleccione **+** para ver todas las aplicaciones.
3. Iniciar **calibración**.

![Acceso a la aplicación de calibración desde el shell](images/calibration-shell.png)

![La aplicación de calibración aparece como un cubo Live después de que se inicia](images/calibration-livecube-200px.png)

**Iniciar la aplicación de configuración**
1. Use [bloom](gestures.md#bloom) para llegar a [menú Inicio](navigating-the-windows-mixed-reality-home.md#start-menu).
2. Seleccione **+** para ver todas las aplicaciones si **configuración** no está anclado al inicio.
3. Iniciar **configuración**.
4. Vaya a **sistema** > **utilidades** y seleccione **calibración abierto**.

![Iniciar la aplicación de calibración de la aplicación de configuración](images/calibration-settings-500px.jpg)

## <a name="hololens-2"></a>HoloLens 2

> [!NOTE]
> Obtener información más específica de HoloLens 2 [próximamente](index.md#news-and-notes).

## <a name="immersive-headsets"></a>Inmersivos

Para cambiar IPD dentro de los auriculares, abra la aplicación de configuración y vaya a **la realidad mixta** > **mostrar auriculares** y mueva el control deslizante. Verá los cambios en tiempo real en los auriculares. Si conoce la IPD, quizás de una visita a la optometrista, puede escribirla directamente también.

También puede ajustar esta configuración, vaya a **configuración** > **la realidad mixta** > **mostrar auriculares** en su PC.

Si los auriculares no admiten la personalización de IPD, esta opción se deshabilitará.

## <a name="see-also"></a>Vea también
* [Consideraciones sobre el entorno de HoloLens](environment-considerations-for-hololens.md)
