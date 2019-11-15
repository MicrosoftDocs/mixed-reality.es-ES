---
title: Acerca de la cartelera y la etiqueta
description: Los objetos con la cartelera siempre se orientan a sí mismos para que se enfrente al usuario.
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, la cartelera, el etiquetado
ms.openlocfilehash: 06cd1c6f67f8aa2dd94173d4089adbdbd0765211
ms.sourcegitcommit: 781e47db2ca2f2c792c95e76ac309b44b3535555
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2019
ms.locfileid: "74105737"
---
# <a name="billboarding-and-tag-along"></a>Acerca de la cartelera y la etiqueta

<br>

<img src="images/UX/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a>¿Qué es la cartelera?

La cartelera es un concepto de comportamiento que se puede aplicar a los objetos de realidad mixta. Los objetos con la cartelera siempre se orientan a sí mismos para que se enfrente al usuario. Esto es especialmente útil en el caso de los sistemas de texto y de menús en los que los objetos estáticos que se colocan en el entorno del usuario (con bloqueo mundial) quedarían ocultos o ilegibles si el usuario se desplazara.

Los objetos con la cartelera habilitada pueden girar libremente en el entorno del usuario. También se pueden restringir a un único eje en función de las consideraciones de diseño. Tenga en cuenta que los objetos con recortes se pueden recortar o tapaba si se colocan demasiado cerca de otros objetos, o en HoloLens, hay demasiadas cerrar superficies digitalizadas. Para evitar esto, piense en la superficie total que un objeto puede producir cuando se gira en el eje habilitado para la cartelera.

<br>

---
## <a name="what-is-a-tag-along"></a>¿Qué es una etiqueta?

La etiqueta es un concepto de comportamiento que se puede Agregar a los hologramas. Una etiqueta a lo largo del objeto intenta permanecer en un intervalo que permite al usuario interactuar de forma cómoda.

![el panel de PIN de HoloLens es un buen ejemplo de cómo se comparan las etiquetas en el](images/tagalong-1000px.jpg)<br>
*El menú Inicio de HoloLens es un buen ejemplo de comportamiento de etiqueta.*

Los objetos de etiqueta incluyen parámetros que pueden ajustarse de la forma en que se comportan. El contenido puede estar dentro o fuera de la línea de visión del usuario mientras se desee mientras el usuario se mueve por su entorno. A medida que el usuario se mueve, el contenido intentará permanecer dentro del perímetro del usuario desplazándose hacia el borde de la vista, en función de la rapidez con la que se mueva el usuario puede dejar el contenido temporalmente fuera de la vista. Cuando el usuario mira hacia el objeto de etiqueta, resulta más completo ver. Piense que el contenido siempre es "un vistazo", por lo que los usuarios nunca olvidan en qué dirección se encuentra el contenido.

Los parámetros adicionales pueden hacer que la etiqueta a lo largo del objeto se adjunte al encabezado del usuario mediante una banda elástica. La amortiguación de aceleración o desaceleración da peso al objeto, lo que hace que se sienta más físicamente presente. Este comportamiento del muelle es una prestación que ayuda al usuario a crear un modelo mental exacto de cómo funciona la etiqueta. Audio le ayuda a proporcionar prestaciones adicionales para cuando los usuarios tienen objetos en el modo de etiqueta. El audio debe reforzar la velocidad de movimiento; un cambio de cabeza rápido debe proporcionar un efecto de sonido más perceptible mientras el recorrido de una velocidad natural debe tener un audio mínimo si se produce algún efecto.

Al igual que el contenido bloqueado realmente por el encabezado, los objetos de etiquetas pueden resultar abrumadores o nauseating si se mueven de forma desigual o muelle demasiado en la vista del usuario. A medida que un usuario busca y luego se detiene rápidamente, sus sentidos les indica que se han detenido. Su saldo les informa de que su cabeza ha dejado de activar y su visión ve que el mundo deja de activar. Sin embargo, si la etiqueta se mantiene en movimiento cuando el usuario se detiene, puede confundir sus sentidos.

<br>

---

## <a name="billboarding-and-tag-along-in-mrtkmixed-reality-toolkit-for-unity"></a>La cartelera y la etiqueta en MRTK (kit de herramientas de realidad mixta) para Unity
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** proporciona scripts para el comportamiento de la cartelera y la etiqueta. Simplemente asigne el script Billboard.cs a cualquier objeto para agregar el comportamiento de la cartelera y hacer que el objeto siempre se enfrente a usted. Para agregar el comportamiento de etiqueta, use el script RadialView.cs. Puede ajustar varias opciones, como lerping Time, Distance y degree.

* [MRTK: Solver de vista radial](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html#radialview)
* [MRTK: script de la cartelera](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a>Consulta también

* [Cursores](cursors.md)
* [Rayo de mano](point-and-commit.md)
* [Button](button.md)
* [Objeto con el que se puede interactuar](interactable-object.md)
* [Cuadro de límite y barra de la aplicación](app-bar-and-bounding-box.md)
* [Manipula](direct-manipulation.md)
* [Menú Mano](hand-menu.md)
* [Menú Near](near-menu.md)
* [Colección de objetos](object-collection.md)
* [Comando de voz](voice-input.md)
* [Teclado](keyboard.md)
* [Herramienta](tooltip.md)
* [Tabletas](slate.md)
* [Control deslizante](slider.md)
* [Etiquetado y vista frontal continua](billboarding-and-tag-along.md)
* [Indicación del progreso](progress.md)
* [Magnetismo de superficie](surface-magnetism.md)
