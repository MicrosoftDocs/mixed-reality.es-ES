---
title: Holographic Remoting Player
description: Holographic Remoting Player es una aplicación complementaria que se conecta a aplicaciones y juegos de equipos que admiten la comunicación remota holográfica. Holographic Remoting transmite contenido holográfica desde un equipo a Microsoft HoloLens en tiempo real mediante una conexión Wi-Fi.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota de Holographic
ms.openlocfilehash: 8b1d58b2c2ce8f379a87059bb5add0f85f507259
ms.sourcegitcommit: fef42e2908e49822f2d13b05d2f9260bf0d72158
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2020
ms.locfileid: "86061138"
---
# <a name="holographic-remoting-player"></a>Holographic Remoting Player

>[!IMPORTANT]
>Holographic Remoting para HoloLens 2 es un cambio de versión principal. [Las aplicaciones remotas para **hololens (1ª generación)** ](add-holographic-remoting.md) deben usar el paquete NuGet versión **1. x.** x y [las aplicaciones remotas para **hololens 2** ](holographic-remoting-create-host.md) deben usar **2. x**. x. Esto implica que las aplicaciones remotas escritas para HoloLens 2 no son compatibles con HoloLens (1º gen) y viceversa.

[Holographic Remoting Player](https://www.microsoft.com/p/holographic-remoting-player/9nblggh4sv40) es una aplicación complementaria que se conecta a aplicaciones y juegos de equipos que admiten la comunicación remota holográfica. Holographic Remoting transmite contenido holográfica desde un equipo a Microsoft HoloLens en tiempo real mediante una conexión Wi-Fi.

El reproductor de comunicación remota holográfica solo se puede usar con aplicaciones de PC diseñadas específicamente para admitir la comunicación remota holográfica.

El reproductor de comunicación remota holográfica está disponible para HoloLens (1ª generación) y HoloLens 2.  Las aplicaciones de PC que admiten la comunicación remota holográfica con HoloLens deben actualizarse para admitir la comunicación remota holográfica con HoloLens 2. Póngase en contacto con su proveedor de aplicaciones si tiene preguntas sobre qué versiones se admiten.

>[!TIP]
>A partir de la versión [2.2.0](holographic-remoting-version-history.md#v2.2.0) , el reproductor de comunicación remota holográfica también está disponible para equipos Windows que ejecutan [Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md).

## <a name="connecting-to-the-holographic-remoting-player"></a>Conexión al reproductor de acceso remoto holográfica

Siga las instrucciones de la aplicación para conectarse al reproductor de acceso remoto holográfica. Deberá escribir la dirección IP del dispositivo HoloLens, que puede ver en la pantalla principal del reproductor de comunicación remota, como se indica a continuación:

![Holographic Remoting Player](images/holographicremotingplayer.png)

Siempre que vea la pantalla principal, sabrá que no tiene una aplicación conectada.

Tenga en cuenta que la conexión de Holographic Remoting **no está cifrada**. Siempre debe usar la comunicación remota holográfica a través de una conexión Wi-Fi segura en la que confíe.

## <a name="quality-and-performance"></a>Calidad y rendimiento

La calidad y el rendimiento de su experiencia variarán en función de tres factores:
* **La experiencia holográfica que está ejecutando: las** aplicaciones que presentan contenido de alta resolución o muy detallado pueden requerir un equipo más rápido o una conexión inalámbrica más rápida.
* **El hardware del equipo** : su PC debe ser capaz de ejecutar y codificar la experiencia holográfica en 60 fotogramas por segundo. En el caso de una tarjeta gráfica, generalmente se recomienda una GeForce GTX 970 o AMD Radeon R9 290 o superior. Una vez más, su experiencia en particular puede requerir una tarjeta superior o inferior.
* **La conexión Wi-Fi** : su experiencia con Holographic se transmite a través de Wi-Fi. Use una red rápida con poca congestión para maximizar la calidad. El uso de un equipo conectado a través de un cable Ethernet, en lugar de Wi-Fi, también puede mejorar la calidad.

## <a name="diagnostics"></a>Diagnóstico

Para medir la calidad de la conexión, indique **"habilitar diagnósticos"** mientras se está en la pantalla principal del reproductor de comunicación remota holográfica. Cuando se habilitan los diagnósticos, en **HoloLens (1ª generación)** , la aplicación le mostrará:

* **Fps** : el número medio de fotogramas representados que el reproductor remoto recibe y representa por segundo. El ideal es 60 FPS.
* **Latencia** : la cantidad de tiempo promedio que tarda un fotograma en pasar de su equipo a HoloLens. Cuanto menor es el mejor. Esto depende en gran medida de la red Wi-Fi.

En **HoloLens 2** , la aplicación le mostrará:

![Diagnóstico del reproductor remoto Holographic](images/holographicremotingplayer-diag.png)

* **Render** : el número de marcos que el reproductor remoto representa en el último segundo. Tenga en cuenta que esto es independiente del número de fotogramas que llegaron a través de la red (consulte **fotogramas de vídeo**). Además, se muestra el tiempo de Delta de representación promedio/máximo en milisegundos en el último segundo entre los fotogramas representados.

* **Fotogramas de vídeo** : el primer número que se muestra es los fotogramas de vídeo omitidos, el segundo es fotogramas de vídeo reutilizados y el tercero recibe fotogramas de vídeo. Todos los números representan el recuento en el último segundo.
    * ```Received frames```es el número de fotogramas de vídeo que llegaron en el último segundo. En condiciones normales, debe ser 60 pero, si no es así, es un indicador de que los fotogramas se han quitado debido a problemas de red o a que el lado remoto o remoto no produce fotogramas con la tasa esperada.
    * ```Reused frames```es el número de fotogramas de vídeo usados más de una vez en el último segundo. Por ejemplo, si los fotogramas de vídeo llegan tarde, el bucle de representación del reproductor todavía representa un fotograma, pero debe *volver a usar* el fotograma de vídeo que ya ha usado para el fotograma anterior.
    * ```Skipped frames```es el recuento de fotogramas de vídeo que no ha usado el bucle de representación del reproductor. Por ejemplo, la vibración de red puede tener el efecto de que los fotogramas de vídeo que llegan ya no se distribuyen uniformemente. Por ejemplo, si algunas están atrasadas y otras llegan en el tiempo con el resultado de que no tienen una diferencia de 16,66 milisegundos al ejecutarse en 60Hz. Puede ocurrir que más de un fotograma llegue entre dos TICs del bucle de representación del reproductor. En este caso, el jugador *omite* uno o varios fotogramas, ya que se supone que siempre muestra el fotograma de vídeo recibido más recientemente.

    >[!NOTE]
    >Cuando se enfrenta a la vibración de la red, los fotogramas omitidos y reutilizados suelen ser los mismos. Por el contrario, si solo ve Marcos omitidos, es un indicador de que el reproductor no alcanza la velocidad de fotogramas de destino. En este caso, debe seguir observando el tiempo de la diferencia máxima de representación al diagnosticar problemas.

* **Fotogramas de vídeo Delta** : diferencia mínima/máxima entre fotogramas de vídeo recibidos en el último segundo. Este número normalmente se correlaciona con los marcos omitidos o reutilizados en caso de problemas causados por la vibración de la red.
* **Latencia** : el plazo medio en milisegundos durante el último segundo. El intervalo de tiempo en este contexto hace referencia a la hora de enviar datos de representadores/sensores desde HoloLens al lado remoto/remoto hasta que se muestre el fotograma de vídeo para los datos de representación y telemetría en la pantalla de HoloLens.
* **Fotogramas de vídeo descartados** : el número de fotogramas de vídeo descartados en el último segundo y dado que se ha establecido una conexión. La causa principal de los fotogramas de vídeo descartados es cuando un fotograma de vídeo no llega por orden y, por ese motivo, se debe descartar porque ya hay una versión más reciente. Esto es similar a los *fotogramas descartados* , pero la causa está en un nivel inferior de la pila de comunicación remota. Los fotogramas de vídeo descartados solo se esperan en condiciones de red bastante incorrectas.



En la pantalla principal, puede decir **"deshabilitar diagnósticos"** para desactivar los diagnósticos.

## <a name="pc-system-requirements"></a>Requisitos del sistema de PC
* El equipo **debe** ejecutar la actualización de aniversario de Windows 10 o una versión más reciente.
* Se recomienda una tarjeta de gráficos GeForce GTX 970 o AMD Radeon R9 290 o superior.
* Se recomienda conectar el equipo a la red a través de Ethernet para reducir el número de saltos inalámbricos.

## <a name="see-also"></a>Consulte también
* [HoloLens (1ª generación): agregar la comunicación remota holográfica](add-holographic-remoting.md)
* [HoloLens 2: escritura de una aplicación remota Holographic Remoting](holographic-remoting-create-host.md)
* [Términos de licencia del software de control remoto de holografías](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
