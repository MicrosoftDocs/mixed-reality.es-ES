---
title: Reproductor remoto holográfica
description: Holographic Remoting Player es una aplicación complementaria que se conecta a aplicaciones y juegos de equipos que admiten la comunicación remota holográfica. Holographic Remoting transmite contenido holográfica desde un equipo a Microsoft HoloLens en tiempo real mediante una conexión Wi-Fi.
author: JonMLyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota de Holographic
ms.openlocfilehash: b8354295f9752e73cc9b34c1769254e49808b63f
ms.sourcegitcommit: c6b59f532a9c5818d9b25c355a174a231f5fa943
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2019
ms.locfileid: "66813721"
---
# <a name="holographic-remoting-player"></a>Reproductor remoto holográfica

Holographic Remoting Player es una aplicación complementaria que se conecta a aplicaciones y juegos de equipos que admiten la comunicación remota holográfica. Holographic Remoting transmite contenido holográfica desde un equipo a Microsoft HoloLens en tiempo real mediante una conexión Wi-Fi.

El reproductor de comunicación remota holográfica solo se puede usar con aplicaciones de PC diseñadas específicamente para admitir la comunicación remota holográfica.

El reproductor de comunicación remota holográfica está disponible tanto para HoloLens como para HoloLens 2.  Las aplicaciones de PC que admiten la comunicación remota holográfica con HoloLens deben actualizarse para admitir Holographic Remtoing con HoloLens 2.  Póngase en contacto con su proveedor de aplicaciones si tiene preguntas sobre qué versiones se admiten.

## <a name="connecting-to-the-holographic-remoting-player"></a>Conexión al reproductor de acceso remoto holográfica

Siga las instrucciones de la aplicación para conectarse al reproductor de acceso remoto holográfica. Tendrá que escribir la dirección IP del dispositivo HoloLens, que puede ver en la pantalla principal del reproductor de comunicación remota de la siguiente manera:

![Reproductor remoto holográfica](images/holographicremotingplayer.png)

Siempre que vea la pantalla principal, sabrá que no tiene una aplicación conectada.

Tenga en cuenta que la conexión de Holographic Remoting **no**está cifrada. Siempre debe usar la comunicación remota holográfica a través de una conexión Wi-Fi segura en la que confíe.

## <a name="quality-and-performance"></a>Calidad y rendimiento

La calidad y el rendimiento de su experiencia variarán en función de tres factores:
* **La experiencia holográfica que está ejecutando: las** aplicaciones que presentan contenido de alta resolución o muy detallado pueden requerir un equipo más rápido o una conexión inalámbrica más rápida.
* **El hardware del equipo** : su PC debe ser capaz de ejecutar y codificar la experiencia holográfica en 60 fotogramas por segundo. En el caso de una tarjeta gráfica, generalmente se recomienda una GeForce GTX 970 o AMD Radeon R9 290 o superior. Una vez más, su experiencia en particular puede requerir una tarjeta superior o inferior.
* **La conexión Wi-Fi** : su experiencia con Holographic se transmite a través de Wi-Fi. Use una red rápida con poca congestión para maximizar la calidad. El uso de un equipo conectado a través de un cable Ethernet, en lugar de Wi-Fi, también puede mejorar la calidad.

## <a name="diagnostics"></a>Diagnóstico

Para medir la calidad de la conexión, indique **"habilitar diagnósticos"** mientras se está en la pantalla principal del reproductor de comunicación remota holográfica. Cuando se habilitan los diagnósticos, la aplicación le mostrará:
* **Fps** : el número medio de fotogramas representados que el reproductor remoto recibe y representa por segundo. El ideal es 60 FPS.
* **Latencia** : la cantidad de tiempo promedio que tarda un fotograma en pasar de su equipo a HoloLens. Cuanto menor es el mejor. Esto depende en gran medida de la red Wi-Fi.

En la pantalla principal, puede decir **"deshabilitar diagnósticos"** para desactivar los diagnósticos.

## <a name="pc-system-requirements"></a>Requisitos del sistema de PC
* El equipo **debe** ejecutar la actualización de aniversario de Windows 10 o una versión más reciente.
* Se recomienda una tarjeta de gráficos GeForce GTX 970 o AMD Radeon R9 290 o superior.
* Se recomienda conectar el equipo a la red a través de Ethernet para reducir el número de saltos inalámbricos.

## <a name="see-also"></a>Vea también
* [Términos de licencia del software de reproducción remota de holografías](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
