---
title: Reproductor de Remoting holográfica
description: El Reproductor holográfica de comunicación remota es una aplicación complementaria que se conecta a aplicaciones de PC y juegos que admiten la comunicación remota holográfica. Remoting holográfica transmite holográfica contenido desde un equipo a su Microsoft HoloLens en tiempo real, mediante una conexión Wi-Fi.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Comunicación remota de HoloLens, comunicación remota, holográfica
ms.openlocfilehash: 16add6c72b594822cacbef6c92ce196ab9b13429
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605764"
---
# <a name="holographic-remoting-player"></a>Reproductor de Remoting holográfica

El Reproductor holográfica de comunicación remota es una aplicación complementaria que se conecta a aplicaciones de PC y juegos que admiten la comunicación remota holográfica. Remoting holográfica transmite holográfica contenido desde un equipo a su Microsoft HoloLens en tiempo real, mediante una conexión Wi-Fi.

El Reproductor de Remoting holográfica sólo puede utilizarse con aplicaciones de PC que están específicamente diseñadas para admitir la comunicación remota holográfica.

> [!NOTE]
> Obtener información más específica de HoloLens 2 [próximamente](index.md#news-and-notes).

## <a name="connecting-to-the-holographic-remoting-player"></a>Conectar con el Reproductor de Remoting holográfica

Siga las instrucciones de la aplicación para conectar con el Reproductor de Remoting holográfica. Deberá especificar la dirección IP del dispositivo HoloLens, que puede ver en la pantalla principal del jugador de comunicación remota como sigue:

![Reproductor de Remoting holográfica](images/holographicremotingplayer.png)

Siempre que vea la pantalla principal, sabrá que no tiene una aplicación conectada.

Tenga en cuenta que la conexión de remoting holográfica **no cifrados**. Siempre debe utilizar Remoting holográfica a través de una conexión segura de Wi-Fi que confíe.

## <a name="quality-and-performance"></a>Calidad y el rendimiento

La calidad y el rendimiento de la experiencia variará en función de tres factores:
* **La experiencia holográfica ejecutas** -aplicaciones que representan el contenido de alta resolución o muy detallada pueden requerir un PC más rápido o conexión inalámbrica con mayor rapidez.
* **Hardware de su PC** -el equipo debe ser capaz de ejecutar y codificar su experiencia holográfica a 60 fotogramas por segundo. Para una tarjeta gráfica, por lo general se recomienda un GeForce GTX 970 o AMD Radeon R9 290 o superior. De nuevo, su experiencia concreta puede requerir una tarjeta superior o inferiores.
* **La conexión Wi-Fi** -su experiencia holográfica se transmite a través de Wi-Fi. Usar una red rápida con baja congestión para aumentar la calidad. Usa un equipo que está conectado a través de un cable Ethernet, en lugar de Wi-Fi, es posible que también mejorar la calidad.

## <a name="diagnostics"></a>Diagnóstico

Para medir la calidad de la conexión, por ejemplo **"Habilitar los diagnósticos"** mientras que en la pantalla principal del Reproductor Remoting holográfica. Cuando se habilitan los diagnósticos, le mostrará la aplicación:
* **FPS** : el número medio de fotogramas representados el Reproductor de comunicación remota es recibir y procesar por segundo. Lo más conveniente es 60 FPS.
* **Latencia** -la cantidad media de tiempo que tarda un marco ir desde su equipo a la HoloLens. Cuanto menor sea el mejor. Esto depende en gran medida su red Wi-Fi.

Mientras se encuentra en la pantalla principal, puede decir **"Deshabilitar los diagnósticos"** para desactivar el diagnóstico.

## <a name="pc-system-requirements"></a>Requisitos del sistema del equipo
* Su PC **debe** estar ejecutando Windows 10 Anniversary Update.
* Se recomienda un GeForce GTX 970 o AMD Radeon R9 290 o mejor tarjeta gráfica.
* Se recomienda que conectar el equipo a la red a través de ethernet para reducir el número de saltos inalámbrica.

## <a name="see-also"></a>Vea también
* [Términos de licencia del software de comunicación remota holográfica](microsoft-holographic-remoting-software-license-terms.md)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
