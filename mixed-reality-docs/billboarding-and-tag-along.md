---
title: Vallas publicitarias y tag-along
description: Los objetos con vallas publicitarias siempre orientación para enfrentar el usuario.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, vallas publicitarias, tag-along
ms.openlocfilehash: 8215b96aff1f3c2d43e959f04ad83d41ffd32b2a
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605345"
---
# <a name="billboarding-and-tag-along"></a>Vallas publicitarias y tag-along

Vallas publicitarias es un concepto de comportamiento que se puede aplicar a objetos en la realidad mixta. Los objetos con vallas publicitarias siempre orientación para enfrentar el usuario. Esto es especialmente útil con texto y sistemas trabajé dónde colocan los objetos estáticos en el entorno del usuario (bloqueado por el mundo) sería en caso contrario, oculta o ilegible si para desplazarse por un usuario.

![HoloLens perspectiva de un sistema de menús que siempre enfrenta el usuario](images/billboarding-fragments.gif)<br>
*HoloLens perspectiva de un sistema de menús que siempre enfrenta el usuario*

Los objetos con vallas publicitarias habilitada pueden girar libremente en el entorno del usuario. También puede estar restringidos a un único eje según las consideraciones de diseño. Tenga en cuenta, objetos billboarded pueden recortar o occlude propios si se colocan demasiado cerca de otros objetos o en HoloLens, analizado demasiado cerca superficies. Para evitar este problema, piense en la superficie total que puede producir un objeto si gira en el eje habilitado para vallas publicitarias.

## <a name="what-is-a-tag-along"></a>¿Qué es un tag-along?

Tag-Along es un concepto de comportamiento que se puede agregar a hologramas, incluidos los objetos billboarded. Esta interacción es una manera más natural y descriptiva de conseguir el efecto de contenido bloqueado a la cabeza. Un objeto tag-along intenta nunca deja la vista del usuario. Esto permite al usuario interactuar libremente con lo que es la parte delantera de ellos al observar el hologramas fuera de su vista directa.

![El panel de HoloLens PIN es un buen ejemplo de cómo se comporta tag-along](images/tagalong-1000px.jpg)<br>
*El menú Inicio de HoloLens es un buen ejemplo de comportamiento tag-along*

Objetos Tag-Along tienen parámetros que pueden ajustar el comportamiento. Contenido puede ser dentro o fuera de línea de visión del usuario según sea necesario mientras el usuario se mueve en torno a su entorno. Cuando el usuario se mueve, el contenido se intentará respetar los periféricos del usuario desplazando hacia el borde de la vista, según qué rapidez se mueve un usuario puede dejar el contenido temporalmente fuera de la vista. Cuando el usuario gazes hacia el objeto tag-along, resulta más completa en la vista. Piense en contenido siempre está "Ausente rápida" por lo que los usuarios nunca olviden qué dirección de su contenido.

Parámetros adicionales pueden hacer que el objeto tag-along sienta adjunto a la cabeza del usuario mediante una banda de goma. Amortiguamiento de aceleración o deceleración da peso al objeto, lo que se sienta más físicamente presente. Este comportamiento spring es una prestación que ayuda al usuario crear un modelo mental preciso de cómo funciona tag-along. Audio ayuda a proporcionar prestaciones adicionales para cuando los usuarios tienen objetos en modo tag-along. Audio debe reforzar la velocidad de movimiento. vuelta rápida principal debe proporcionar un efecto más notable de sonido mientras caminando a una velocidad natural debe tener los efectos de audio si cualquier mínima en absoluto.

Al igual que realmente bloqueado de encabezado de contenido, pueden resultar objetos tag-along sobrecargar o nauseating si se mueven extremadamente o primavera demasiado en la vista del usuario. Cuando un usuario busca en torno a y, a continuación, rápidamente stop, sus sentidos que indican que han dejado. El equilibrio que les informa de que su cabeza ha dejado de activación, así como sus ve vision la detención del mundo activación. Sin embargo, si tag-along en sigue moviendo cuando el usuario se ha detenido, pueden confundir a sus sentidos.

## <a name="see-also"></a>Vea también
* [Cursores](cursors.md)
* [Aspectos básicos de interacción](interaction-fundamentals.md)
* [Comodidad](comfort.md)
