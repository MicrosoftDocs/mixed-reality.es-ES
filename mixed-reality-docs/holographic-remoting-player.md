---
title: Reproductor remoto holográfica
description: Holographic Remoting Player es una aplicación complementaria que se conecta a aplicaciones y juegos de equipos que admiten la comunicación remota holográfica. Holographic Remoting transmite contenido holográfica desde un equipo a Microsoft HoloLens en tiempo real mediante una conexión Wi-Fi.
author: JonMLyons
ms.author: jlyons
ms.date: 08/01/2019
ms.topic: article
keywords: HoloLens, comunicación remota, comunicación remota de Holographic
ms.openlocfilehash: c3e31cdb5acf35ecc3101d3cf359e40771cc8cbd
ms.sourcegitcommit: ff330a7e36e5ff7ae0e9a08c0e99eb7f3f81361f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2019
ms.locfileid: "70122075"
---
# <a name="holographic-remoting-player"></a>Reproductor remoto holográfica

>[!IMPORTANT]
>Holographic Remoting para HoloLens 2 es un cambio de versión principal. [Las aplicaciones host para **hololens (1ª generación)** ](add-holographic-remoting.md) deben usar el paquete NuGet versión **1. x.** x y [las aplicaciones host para **hololens 2** ](holographic-remoting-create-host.md) deben usar **2. x**. x. Esto implica que las aplicaciones host escritas para HoloLens 2 no son compatibles con HoloLens 1 y viceversa.

Holographic Remoting Player es una aplicación complementaria que se conecta a aplicaciones y juegos de equipos que admiten la comunicación remota holográfica. Holographic Remoting transmite contenido holográfica desde un equipo a Microsoft HoloLens en tiempo real mediante una conexión Wi-Fi.

El reproductor de comunicación remota holográfica solo se puede usar con aplicaciones de PC diseñadas específicamente para admitir la comunicación remota holográfica.

El reproductor de comunicación remota holográfica está disponible tanto para HoloLens como para HoloLens 2.  Las aplicaciones de PC que admiten la comunicación remota holográfica con HoloLens deben actualizarse para admitir la comunicación remota holográfica con HoloLens 2. Póngase en contacto con su proveedor de aplicaciones si tiene preguntas sobre qué versiones se admiten.

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

Para medir la calidad de la conexión, indique **"habilitar diagnósticos"** mientras se está en la pantalla principal del reproductor de comunicación remota holográfica. Cuando se habilitan los diagnósticos, en **HoloLens (1ª generación)** , la aplicación le mostrará:

* **Fps** : el número medio de fotogramas representados que el reproductor remoto recibe y representa por segundo. El ideal es 60 FPS.
* **Latencia** : la cantidad de tiempo promedio que tarda un fotograma en pasar de su equipo a HoloLens. Cuanto menor es el mejor. Esto depende en gran medida de la red Wi-Fi.

En **HoloLens 2** , la aplicación le mostrará:

![Diagnóstico del reproductor remoto Holographic](images/holographicremotingplayer-diag.png)

* **Render** : el número de marcos que el reproductor remoto representa en el último segundo. Tenga en cuenta que esto es independiente del número de fotogramas que llegaron a través de la red (consulte fotogramas de **vídeo**). Además, se muestra el tiempo de Delta de representación promedio/máximo en milisegundos en el último segundo entre los fotogramas representados.

* Fotogramas de **vídeo** : el primer número que se muestra es los fotogramas de vídeo omitidos, el segundo es fotogramas de vídeo reutilizados y el tercero recibe fotogramas de vídeo. Todos los números representan el recuento en el último segundo.
    * ```Received frames```es el número de fotogramas de vídeo que llegaron en el último segundo. En condiciones normales, debe ser 60 pero, si no es así, es un indicador de que los fotogramas se han quitado debido a problemas de red o a que el lado remoto o host no produce fotogramas con la tasa esperada.
    * ```Reused frames```es el número de fotogramas de vídeo que se han usado más de una vez en el último segundo. Por ejemplo, si los fotogramas de vídeo llegan tarde el bucle de representación del reproductor todavía representa un fotograma , pero necesita reutilizar el fotograma de vídeo que ya ha usado para el fotograma anterior.
    * ```Skipped frames```es el recuento de fotogramas de vídeo que no ha usado el bucle de representación del reproductor. Por ejemplo, la vibración de red puede tener el efecto de que los fotogramas de vídeo que llegan no se distribuyen uniformemente, supongamos que algunos están en espera y otros llegan en el tiempo con el resultado de que no tienen un delta de 16,66 milisegundos cuando se ejecutan en 60Hz. Si lo hace, se puede producir que más de un fotograma llegue entre dos TICs del bucle de representación del reproductor. En este caso, el jugador *omite* uno o varios fotogramas, ya que se supone que se muestra siempre el fotograma de vídeo recibido más recientemente.

    >[!NOTE]
    >Cuando la vibración de red está orientada, normalmente se omite y los fotogramas reutilizados son aproximadamente iguales. Por el contrario, si solo ve Marcos omitidos, es un indicador de que el reproductor no alcanza su velocidad de fotogramas de destino. En este caso, debe tener un vistazo al tiempo máximo de la presentación para el diagnóstico de problemas.

* Fotogramas de **vídeo Delta** : diferencia mínima/máxima entre fotogramas de vídeo recibidos en el último segundo. Este número normalmente se correlaciona con los marcos omitidos o reutilizados en caso de problemas causados por la vibración de la red.
* **Latencia** : el plazo medio en milisegundos durante el último segundo. El intervalo de tiempo en este contexto significa que el tiempo se envía desde el envío de datos de representadores/sensores desde HoloLens hasta el lado remoto/host hasta que se muestra el fotograma de vídeo para los datos de la presentación o la telemetría en la pantalla de HoloLens.
* Fotogramas de **vídeo** descartados: el número de fotogramas de vídeo descartados en el último segundo y dado que se ha establecido una conexión. La causa principal de los fotogramas de vídeo descartados es cuando un fotograma de vídeo no llega por orden y, por ese motivo, se debe descartar porque ya hay una versión más reciente. Esto es similar a los fotogramas descartados, pero la causa está en un nivel inferior de la pila de comunicación remota. Los fotogramas de vídeo descartados solo se esperan en condiciones de red bastante incorrectas.



En la pantalla principal, puede decir **"deshabilitar diagnósticos"** para desactivar los diagnósticos.

## <a name="pc-system-requirements"></a>Requisitos del sistema de PC
* El equipo **debe** ejecutar la actualización de aniversario de Windows 10 o una versión más reciente.
* Se recomienda una tarjeta de gráficos GeForce GTX 970 o AMD Radeon R9 290 o superior.
* Se recomienda conectar el equipo a la red a través de Ethernet para reducir el número de saltos inalámbricos.

## <a name="see-also"></a>Vea también
* [HoloLens (1ª generación): Incorporación de Holographic Remoting](add-holographic-remoting.md)
* [HoloLens 2: Escritura de una aplicación de host de Holographic Remoting](holographic-remoting-create-host.md)
* [Términos de licencia del software de control remoto de holografías](https://docs.microsoft.com/en-us/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Declaración de privacidad de Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
