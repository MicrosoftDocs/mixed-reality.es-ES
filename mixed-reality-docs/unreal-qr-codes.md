---
title: Códigos QR en Unreal
description: Guía para el uso de códigos QR en Unreal
author: hferrone
ms.author: v-haferr
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, qr codes
ms.openlocfilehash: 90a51227ae455389168fb3262e83f34b64a7bfb5
ms.sourcegitcommit: ee7f04148d3608b0284c59e33b394a67f0934255
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2020
ms.locfileid: "84428749"
---
# <a name="qr-codes-in-unreal"></a>Códigos QR en Unreal

## <a name="overview"></a>Introducción

HoloLens 2 puede ver los códigos QR en el espacio del mundo real a través de la cámara web, que los representa como hologramas empleando un sistema de coordenadas en la posición del mundo real de cada código.  Además de los códigos QR únicos, HoloLens 2 también puede representar hologramas en la misma ubicación en varios dispositivos para crear una experiencia compartida. Asegúrese de seguir estos procedimientos recomendados para agregar códigos QR a las aplicaciones:

- Zonas tranquilas
- Iluminación y fondo
- Tamaño, distancia y posición angular

Preste especial atención a las [consideraciones del ambiente](environment-considerations-for-hololens.md) al colocar códigos QR en la aplicación. Puede encontrar más información sobre cada uno de estos temas e instrucciones sobre cómo descargar el paquete de NuGet necesario en el documento principal de [seguimiento de código QR](qr-code-tracking.md). 

## <a name="enabling-qr-detection"></a>Habilitación de la detección de QR
Como HoloLens 2 necesita usar la cámara web para ver los códigos QR, deberá habilitarla en la configuración del proyecto:
- Abra **Editar > Configuración del proyecto**, desplácese hasta la sección **Plataformas** y pulse en **HoloLens**.
    + Expanda la sección **Funcionalidades** y marque **Cámara web**.  

También deberá participar en el seguimiento del código QR mediante la [adición de un activo ARSessionConfig](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).

## <a name="setting-up-a-tracked-image"></a>Configuración de una imagen con seguimiento

Los códigos QR aparecen en el sistema de geometría con seguimiento de AR de Unreal como una imagen con seguimiento. Para que esto funcione, deberá hacer lo siguiente:
1. Cree un plano técnico y agregue un componente **ARTrackableNotify**.

![Notificación de seguimiento de AR de QR](images/unreal-spatialmapping-artrackablenotify.PNG)

2. Seleccione **ARTrackableNotify** y expanda la sección **Eventos** en el panel **Detalles**. 

![Eventos con QR](images/unreal-spatialmapping-events.PNG)

3. Haga clic en **+** junto a **On Add Tracked Geometry** (Al agregar geometría con seguimiento) para agregar el nodo al gráfico de eventos.
    - Puede encontrar la lista completa de eventos en la API de componente [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html). 

![Ejemplo de representación de QR](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-image"></a>Uso de una imagen con seguimiento
El gráfico de eventos de la siguiente imagen muestra el evento **OnUpdateTrackedImage** que se usa para representar un punto en el centro de un código QR e imprimir sus datos. 

![Ejemplo de representación de QR](images/unreal-qr-render.PNG)

Esto es lo que sucede:
1. En primer lugar, convierte la imagen con seguimiento en un elemento **ARTrackedQRCode** para comprobar que la imagen actualizada actual es un código QR.  
2. Los datos codificados se recuperan de la variable **QRCode**. Puede obtener la parte superior izquierda del código QR en la ubicación de **GetLocalToWorldTransform** y las dimensiones con **GetEstimateSize**. 

También puede [obtener el sistema de coordenadas para un código QR](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) en el código.

## <a name="finding-the-unique-id"></a>Búsqueda del identificador único
Cada código QR tiene un id. de GUID único, que puede buscar:
- Arrastrando y colocando el marcador **As ARTracked QRCode** (Como QRCode ARTracked) y buscando **Get Unique ID** (Obtener id. único).

![GUID de QR](images/unreal-qr-guid.PNG)

Ocurren muchas cosas en segundo plano con los códigos QR, por lo que esto no es todo. Asegúrese de consultar los siguientes vínculos para obtener más detalles sobre ellos.

## <a name="see-also"></a>Consulta también
* [Asignación espacial](spatial-mapping.md)
* [Hologramas](hologram.md)
* [Sistemas de coordenadas](coordinate-systems.md)