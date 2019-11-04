---
title: Acerca de la cartelera y la etiqueta
description: Los objetos con la cartelera siempre se orientan a sí mismos para que se enfrente al usuario.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, la cartelera, el etiquetado
ms.openlocfilehash: 032e665d94a73b94b59f693e452874af0b45f021
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437001"
---
# <a name="billboarding-and-tag-along"></a>Acerca de la cartelera y la etiqueta

<br>

<img src="images/billboarding-fragments.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">

La cartelera es un concepto de comportamiento que se puede aplicar a los objetos de realidad mixta. Los objetos con la cartelera siempre se orientan a sí mismos para que se enfrente al usuario. Esto es especialmente útil en el caso de los sistemas de texto y de menús en los que los objetos estáticos que se colocan en el entorno del usuario (con bloqueo mundial) quedarían ocultos o ilegibles si el usuario se desplazara.

Los objetos con la cartelera habilitada pueden girar libremente en el entorno del usuario. También se pueden restringir a un único eje en función de las consideraciones de diseño. Tenga en cuenta que los objetos con recortes se pueden recortar o tapaba si se colocan demasiado cerca de otros objetos, o en HoloLens, hay demasiadas cerrar superficies digitalizadas. Para evitar esto, piense en la superficie total que un objeto puede producir cuando se gira en el eje habilitado para la cartelera.

## <a name="what-is-a-tag-along"></a>¿Qué es una etiqueta?

La etiqueta es un concepto de comportamiento que se puede Agregar a hologramas, incluidos los objetos de la cartelera. Esta interacción es una forma más natural y cómoda de lograr el efecto del contenido bloqueado por el cabezal. Una etiqueta a lo largo de un objeto intenta no salir nunca de la vista del usuario. Esto permite al usuario interactuar libremente con lo que se encuentra delante de ellos, a la vez que sigue viendo los hologramas fuera de su vista directa.

![el panel de PIN de HoloLens es un buen ejemplo de cómo se comparan las etiquetas en el](images/tagalong-1000px.jpg)<br>
*El menú Inicio de HoloLens es un buen ejemplo de comportamiento de etiqueta.*

Los objetos de etiqueta incluyen parámetros que pueden ajustarse de la forma en que se comportan. El contenido puede estar dentro o fuera de la línea de visión del usuario mientras se desee mientras el usuario se mueve por su entorno. A medida que el usuario se mueve, el contenido intentará permanecer dentro del perímetro del usuario desplazándose hacia el borde de la vista, en función de la rapidez con la que se mueva el usuario puede dejar el contenido temporalmente fuera de la vista. Cuando el usuario mira hacia el objeto de etiqueta, resulta más completo ver. Piense que el contenido siempre es "un vistazo", por lo que los usuarios nunca olvidan en qué dirección se encuentra el contenido.

Los parámetros adicionales pueden hacer que la etiqueta a lo largo del objeto se adjunte al encabezado del usuario mediante una banda elástica. La amortiguación de aceleración o desaceleración da peso al objeto, lo que hace que se sienta más físicamente presente. Este comportamiento del muelle es una prestación que ayuda al usuario a crear un modelo mental exacto de cómo funciona la etiqueta. Audio le ayuda a proporcionar prestaciones adicionales para cuando los usuarios tienen objetos en el modo de etiqueta. El audio debe reforzar la velocidad de movimiento; un cambio de cabeza rápido debe proporcionar un efecto de sonido más perceptible mientras el recorrido de una velocidad natural debe tener un audio mínimo si se produce algún efecto.

Al igual que el contenido bloqueado realmente por el encabezado, los objetos de etiquetas pueden resultar abrumadores o nauseating si se mueven de forma desigual o muelle demasiado en la vista del usuario. A medida que un usuario busca y luego se detiene rápidamente, sus sentidos les indica que se han detenido. Su saldo les informa de que su cabeza ha dejado de activar y su visión ve que el mundo deja de activar. Sin embargo, si la etiqueta se mantiene en movimiento cuando el usuario se detiene, puede confundir sus sentidos.

## <a name="see-also"></a>Consulta también
* [Cursores](cursors.md)
* [Interacciones instintivas](interaction-fundamentals.md)
* [Comodidad](comfort.md)
