---
title: Experiencias compartidas en Unity
description: Compartir el mismos hologramas entre varios usuarios en una aplicación de Unity.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: Uso compartido, delimitador, WorldAnchor, MR compartir 250, WorldAnchorTransferBatch, SpatialPerception, Azure, Azure delimitadores espaciales, ASA
ms.openlocfilehash: fe755c15d942660b1e16b2335db28d3d7ce72816
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605778"
---
# <a name="shared-experiences-in-unity"></a>Experiencias compartidas en Unity

Una experiencia compartida es uno donde varios usuarios, cada uno con sus propios HoloLens, dispositivo iOS o Android, colectivamente ver e interactuar con el mismo holograma que se coloca en un punto fijo en el espacio. Esto se logra mediante el uso compartido de anclaje espacial.

## <a name="azure-spatial-anchors"></a>Anclas espaciales de Azure

Puede usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure espacial delimitadores</a> crear duraderos delimitadores espaciales basado en la nube, que, a continuación, puede localizar su aplicación a través de varios HoloLens, dispositivos iOS y Android.  Al compartir un anclaje espacial comunes en varios dispositivos, cada usuario puede ver el contenido representado en relación con ese delimitador en la misma ubicación física.  Esto permite experiencias compartidas en tiempo real.

También puede usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure espacial delimitadores</a> para la persistencia holograma asincrónica a través de dispositivos Android, iOS y HoloLens.  Al compartir un anclaje espacial en la nube duraderas, varios dispositivos pueden observar el mismo holograma persistente con el tiempo, incluso si esos dispositivos no están presentes entre sí al mismo tiempo.

Para empezar a crear experiencias compartidas en Unity, pruebe el minuto 5 <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">guías de inicio rápido de Azure espacial delimitadores Unity</a>.

Una vez que esté en marcha con delimitadores espacial de Azure, a continuación, puede <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">crear y localizar los anclajes en Unity</a>.

## <a name="local-anchor-transfers"></a>Transferencias de anclaje local

En situaciones donde no se puede usar Azure delimitadores espacial, [delimitador local transferencias](local-anchor-transfers-in-unity.md) habilitar un dispositivo HoloLens exportar un delimitador para ser importadas por un segundo dispositivo HoloLens.  Tenga en cuenta que este enfoque proporciona la retirada de delimitador menos sólida que Azure espacial delimitadores y dispositivos iOS y Android no son compatibles con este enfoque.

## <a name="see-also"></a>Vea también
* [Compartir experiencias en realidad mixta](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure delimitadores espaciales</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Delimitadores espaciales Azure SDK para Unity</a>