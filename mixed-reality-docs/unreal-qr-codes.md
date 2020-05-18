---
title: Códigos QR en Unreal
description: Guía para el uso de códigos QR en Unreal
author: sw5813
ms.author: jacksonf
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, development, features, documentation, guides, holograms, qr codes
ms.openlocfilehash: 67a3a8092ab908cba6768e92ed6a0e7bd2737275
ms.sourcegitcommit: 5b802078090700e06630c8fc665fedeaa0a16eb7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/13/2020
ms.locfileid: "83342663"
---
# <a name="qr-codes-in-unreal"></a>Códigos QR en Unreal

HoloLens puede colocar códigos QR en un área del mundo para representar hologramas en posiciones conocidas del mundo real.  También se puede usar para representar hologramas en varios dispositivos en la misma ubicación para crear una experiencia compartida. 

Para habilitar la detección de QR en HoloLens, asegúrate de que la funcionalidad "Webcam" esté activada en el editor de Unreal en Project Settings > Platform > HoloLens > Capabilities (Configuración del proyecto > Plataforma > HoloLens > Funcionalidades).  

Para participar en el seguimiento de códigos QR en Unreal, inicia una sesión ARSession mediante la función StartARSession. 

Los códigos QR se muestran en el sistema de geometría supervisado de AR de Unreal como imagen con seguimiento.  Para usar esta característica, agrega un componente AR Trackable Notify (Notificación de seguimiento de AR) a un actor de Blueprint: 

![Notificación de seguimiento de AR de QR](images/unreal-spatialmapping-artrackablenotify.PNG)

A continuación, ve a los detalles del componente y haz clic en el botón verde "+" de los eventos que se van a supervisar.  

![Eventos con QR](images/unreal-spatialmapping-events.PNG)

Aquí, nos hemos suscrito a OnUpdateTrackedImage para representar un punto en el centro de un código QR e imprimir los datos codificados del código QR. 

![Ejemplo de representación de QR](images/unreal-qr-render.PNG)

En primer lugar, convierte la imagen de la que se realiza el seguimiento en ARTrackedQRCode para comprobar que la imagen actualizada actual es un código QR.  Después, los datos codificados se pueden recuperar con la variable QRCode.  La parte superior izquierda del código QR se puede recuperar desde la ubicación de GetLocalToWorldTransform.  Las dimensiones se pueden recuperar con GetEstimateSize. 

Cada código QR también tiene un identificador GUID único: 

![GUID de QR](images/unreal-qr-guid.PNG)

## <a name="see-also"></a>Consulta también
* [Seguimiento de códigos QR](qr-code-tracking.md)
