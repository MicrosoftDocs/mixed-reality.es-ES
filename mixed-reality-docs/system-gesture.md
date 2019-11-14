---
title: Gestos del sistema
description: Gesto del sistema para llamar al menú Inicio.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Realidad mixta, gestos, interacción, diseño
ms.openlocfilehash: 417811fff9d98e459dc0047d46ea065acfced4ef
ms.sourcegitcommit: f2b7c6381006fab6d0472fcaa680ff7fb79954d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/14/2019
ms.locfileid: "74064238"
---
# <a name="system-gesture"></a>Gestos del sistema

El gesto del sistema es un gesto de mano que se usa para invocar el menú Inicio. Es el equivalente de presionar la tecla Windows en el teclado, el botón Xbox en un controlador Xbox o el botón Windows en el controlador de movimiento de auriculares envolvente. Es importante comprender qué gestos están reservados para el sistema en cada dispositivo de realidad mixta para evitar conflictos al diseñar las interacciones.

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
        <td>Flores</td>
        <td>✔️</td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td>Botón de muñeca</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
    <tr>
        <td>Mira fijamente y contacto con Palm up</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a>Flores
Para abrir el menú Inicio en HoloLens (1ª generación), hemos diseñado "floración", que es un gesto simbólico que imita el Blossom de la flor. Es distintivo para la interacción con Surefooted, fácil de realizar y rápida recuperación. Para llevar a cabo el gesto de floración en HoloLens (1ª generación), mantenga su mano con su mano y cerca de la mano y, a continuación, abra la mano mediante la distribución de los dedos.

:::row:::
    :::column:::
        ](images/bloom-close.png) de cierre de ![floración<br>
        **Paso 1: Palm con las manos**<br>
    :::column-end:::
    :::column:::
        ![abierto con floración](images/bloom-open.png)<br>
        **Paso 2: Palm up con la mano**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="wrist-button"></a>Botón de muñeca
En HoloLens 2, reemplazamos el gesto de floración con un botón de muñeca virtual que permite más interacciones de instinctual que no requieren ninguna enseñanza adicional. Al mostrar a los usuarios el botón de la muñeca, pueden ponerse en contacto de forma intuitiva y presionarlo con la mano.

:::row:::
    :::column:::
        ![botón de muñeca listo](images/wrist-button-ready.png)<br>
        **Paso 1: Palm para mostrar el botón de muñeca**<br>
    :::column-end:::
    :::column:::
        ![presionar el botón de muñeca](images/wrist-button-press.png)<br>
        **Paso 2: presionar el botón de muñeca**<br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="eye-gaze-and-palm-up-pinch"></a>Mira fijamente y contacto con Palm up
También hemos diseñado una solución de una sola mano para facilitar el acceso en HoloLens 2. Este gesto requiere que los usuarios miren el botón de la muñeca y, a continuación, usar la misma mano para realizar un toque de mano con el dedo y el dedo del índice.<br>
:::row:::
    :::column:::
        ![botón de muñeca listo](images/wrist-button-ready.png)<br>
        **Paso 1: Palm para mostrar el botón de muñeca**<br>
    :::column-end:::
    :::column:::
        ![botón de la muñeca](images/wrist-button-pinch.png)<br>
        **Paso 2: mira fijamente en el botón y luego en Pinch**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>Consulta también

* [Interacciones instintivas](interaction-fundamentals.md)
* [Control con los ojos](eye-tracking.md)
* [Entrada de voz](voice-input.md)
