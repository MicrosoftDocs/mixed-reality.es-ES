---
title: Movimiento de inicio
description: Iniciar el gesto para llamar al menú Inicio.
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Realidad mixta, gestos, interacción, diseño
ms.openlocfilehash: 84088156d0c9cdacc421985b922d5e9370f6a87e
ms.sourcegitcommit: fd606e87e3c4785d3ca2a26632be3bb580e39afb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/28/2020
ms.locfileid: "84152511"
---
# <a name="start-gesture"></a>Movimiento de inicio

El gesto de inicio es un gesto de mano que se usa para invocar el menú Inicio. Es el equivalente de presionar la tecla Windows en el teclado, el botón Xbox en un controlador Xbox o el botón Windows en el controlador de movimiento de auriculares envolvente. Es importante comprender qué gestos están reservados para el sistema en cada dispositivo de realidad mixta para evitar conflictos al diseñar las interacciones.

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
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Eclosión</td>
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

## <a name="bloom"></a>Eclosión
Para abrir el menú Inicio en HoloLens (1ª generación), hemos diseñado "floración", que es un gesto simbólico que imita el Blossom de la flor. Es distintivo para la interacción con Surefooted, fácil de realizar y rápida recuperación. Para llevar a cabo el gesto de floración en HoloLens (1ª generación), mantenga su mano con su mano y cerca de la mano y, a continuación, abra la mano mediante la distribución de los dedos.

:::row:::
    :::column:::
        ![Cierre del floración](images/bloom-close.png)<br>
        **Paso 1: Palm con las manos**<br>
    :::column-end:::
    :::column:::
        ![Floración abierto](images/bloom-open.png)<br>
        **Paso 2: Palm up con la mano**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a>Movimiento de inicio
En HoloLens 2, reemplazamos el gesto de floración con un botón de muñeca virtual que permite más interacciones de instinctual que no requieren ninguna enseñanza adicional. Al mostrar a los usuarios el botón de la muñeca, pueden ponerse en contacto de forma intuitiva y presionarlo con la mano.

:::row:::
    :::column:::
        ![Botón de pulsera listo](images/wrist-button-ready.png)<br>
        **Paso 1: Palm para mostrar el botón de muñeca**<br>
    :::column-end:::
    :::column:::
        ![Presionar el botón de muñeca](images/wrist-button-press.png)<br>
        **Paso 2: presionar el botón de muñeca**<br>
    :::column-end:::
:::row-end:::

<br>

---


## <a name="one-handed-start-gesture"></a>Gesto de inicio con una sola mano

> [!IMPORTANT]
> Para que funcione el gesto de inicio con una sola mano:
>
> 1. Debe actualizar a la actualización de noviembre de 2019 (compilación 18363,1039) o posterior.
> 1. Los ojos deben calibrarse en el dispositivo para que el seguimiento ocular funcione correctamente. Si no ve puntos en órbita alrededor del icono de inicio al mirarlo, los ojos no se calibrarán en el dispositivo.

También puede realizar el gesto de inicio con una sola mano. Para ello, mantenga su mano con la palma y mire el **icono de inicio** en su muñeca interna. **Mientras mantiene el ojo del icono**, acerque el dedo y el dedo del índice.<br>
:::row:::
    :::column:::
        ![Botón de pulsera listo](images/wrist-button-ready.png)<br>
        **Paso 1: Palm para mostrar el botón de muñeca**<br>
    :::column-end:::
    :::column:::
        ![Botón de muñeca](images/wrist-button-pinch.png)<br>
        **Paso 2: mira fijamente en el botón y luego en Pinch**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>Consulte también

* [Interacciones instintivas](interaction-fundamentals.md)
* [Control con los ojos](eye-tracking.md)
* [Entrada de voz](voice-input.md)
