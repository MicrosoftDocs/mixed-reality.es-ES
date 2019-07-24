---
title: Delimitadores espaciales compartidos en DirectX
description: Explica cómo sincronizar dos dispositivos HoloLens compartiendo los delimitadores espaciales.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens, sincronizar, delimitador espacial, transferencia, multijugador, vista, escenario, tutorial, código de ejemplo, Azure, delimitadores espaciales de Azure, ASA
ms.openlocfilehash: 190d3dfb3eec3fd1a57d2713850a7778a4a71de9
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63516872"
---
# <a name="shared-experiences-in-directx"></a>Experiencias compartidas en DirectX

Una experiencia compartida es aquella en la que varios usuarios, cada uno con sus propios dispositivos HoloLens, iOS o Android, ven colectivamente e interactúan con el mismo holograma que se coloca en un punto fijo en el espacio. Esto se logra mediante el uso compartido del delimitador espacial.

## <a name="azure-spatial-anchors"></a>Anclas espaciales de Azure

Puede usar delimitadores espaciales de <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure</a> para crear delimitadores espaciales con respaldo en la nube duraderos, que la aplicación puede encontrar en varios dispositivos HoloLens, iOS y Android.  Al compartir un delimitador espacial común en varios dispositivos, cada usuario puede ver el contenido representado en relación con ese delimitador en la misma ubicación física.  Esto permite compartir experiencias en tiempo real.

También se puede usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> para la persistencia de hologramas asincrónicos en dispositivos Android, iOS y HoloLens.  Al compartir un delimitador espacial en la nube duradera, varios dispositivos pueden observar el mismo holograma persistente a lo largo del tiempo, aunque los dispositivos no estén presentes juntos simultáneamente.

Para empezar a crear experiencias compartidas en la aplicación de HoloLens, pruebe la guía de <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Inicio rápido de hololens</a>de 5 minutos de delimitadores espaciales de Azure.

Una vez que esté en funcionamiento con los anclajes espaciales de Azure, puede <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">crear y buscar delimitadores en HoloLens</a>.  También hay tutoriales disponibles para <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android e iOS</a> , lo que le permite compartir los mismos delimitadores en todos los dispositivos.

## <a name="local-anchor-transfers"></a>Transferencias de delimitadores locales

En situaciones en las que no se pueden usar delimitadores espaciales de Azure, las transferencias de delimitadores [locales](local-anchor-transfers-in-directx.md) permiten que un dispositivo hololens exporte un delimitador para que lo importe un segundo dispositivo hololens.  Tenga en cuenta que este enfoque proporciona una recuperación de delimitador menos sólida que los delimitadores espaciales de Azure, y los dispositivos iOS y Android no son compatibles con este enfoque.

## <a name="see-also"></a>Vea también
* [Experiencias compartidas en realidad mixta](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">SDK de anclajes espaciales de Azure para HoloLens</a>