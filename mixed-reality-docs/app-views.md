---
title: Vistas de aplicación
description: Los dos tipos de vistas en las aplicaciones de Windows Mixed Reality son vistas envolventes y 2D.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: vista envolvente, ver 2D, tableta táctil, la aplicación
ms.openlocfilehash: 2cf65941616ac6906d40e4b4616311317ac705d3
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605710"
---
# <a name="app-views"></a>Vistas de aplicación

Las aplicaciones de Windows pueden contener dos tipos de vistas, **vistas envolventes** y **vistas 2D**. Pueden cambiar las aplicaciones entre sus diversas vistas envolventes y vistas 2D, que muestra sus vistas 2D en un monitor, como una ventana o en un auricular como una pizarra. Las aplicaciones que tienen al menos una vista envolvente se clasifican como **mixto las aplicaciones de realidad**. Las aplicaciones que nunca tienen una vista envolvente son **aplicaciones 2D**.

## <a name="immersive-views"></a>Vistas envolventes

Una vista envolvente ofrece su aplicación la capacidad de crear hologramas en el mundo que le rodea o Sumergir el usuario en un entorno virtual. Cuando una aplicación dibuja en la vista envolvente, ninguna otra aplicación está dibujando al mismo tiempo&mdash;hologramas desde varias aplicaciones no están compuestos juntos. Ajustando continuamente la perspectiva desde la que su [representaciones de aplicación](rendering.md) su escena para que coincida con los movimientos principal del usuario, la aplicación puede representar [bloqueado por el mundo](coordinate-systems.md) hologramas que permanecen en un punto fijo real mundo, o bien puede representar un mundo virtual que contiene su posición como un usuario se mueve dentro de él.

![Cuando se encuentra en una vista envolvente, hologramas pueden colocarse en el mundo que le rodea.](images/designoverview.jpg)<br>
*Cuando se encuentra en una vista envolvente, hologramas pueden colocarse en el mundo que le rodea*

En [HoloLens](hololens-hardware-details.md), la aplicación presenta sus hologramas sobre el entorno del mundo real del usuario. En un [auriculares envolventes de Windows Mixed Reality](immersive-headset-hardware-details.md), el usuario no puede ver el mundo real, y para que la aplicación debe representar todo lo que el usuario verá.

El [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) (incluido el menú Inicio y hologramas haya colocado respecto del entorno) no se representará mientras se encuentra en un envolventes ver. En HoloLens, las notificaciones del sistema que se producen mientras se muestra una vista envolvente se transmitirá audiblemente cortana, y el usuario puede responder con la entrada de voz.

Mientras está en una vista envolvente, la aplicación también es responsable de controlar todas las entradas. Entrada en Windows Mixed Reality se compone de [que mirar](gaze.md), [gesto](gestures.md) (solo para HoloLens), [voz](voice-input.md) y [motion controladores](motion-controllers.md) (envolventes auriculares solo).

## <a name="2d-views"></a>Vistas de 2D

![Varias vistas 2D disponen en torno a Windows Mixed Reality principal](images/teleportation-640px.png)<br>
*Colocan varias aplicaciones con una vista 2D en torno a Windows Mixed Reality principal*

Una aplicación con una vista 2D aparece en el [Windows Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md) (a veces denominado el "shell") como una pizarra virtual, se procesa junto con los iniciadores de aplicaciones y otros hologramas el usuario ha colocado en su mundo. El usuario puede ajustar este tableta táctil para mover y escalarlo, aunque permanece con una resolución fija independientemente de su tamaño. Si la primera vista de la aplicación es una vista 2D, el contenido 2D rellenará la Pizarra misma usada para iniciar la aplicación.

Auriculares desktop, puede ejecutar las aplicaciones de plataforma Universal de Windows (UWP) que se ejecutan en el monitor de escritorio hoy mismo. Estas aplicaciones ya están representar vistas 2D hoy en día, y su contenido aparecerán automáticamente en una tableta táctil en el mundo del usuario cuando se inicia. Las aplicaciones para UWP 2D pueden tener como destino el **Windows.Universal** familia de dispositivos se ejecute en ambos auriculares de escritorio y en HoloLens como pizarras.

Uno es el uso de claves de 2D vistas mostrar un formulario de entrada de texto que puede hacer que el uso del teclado del sistema. Dado que el shell no se puede representar en una vista envolvente, la aplicación debe pasar a una vista para mostrar el teclado del sistema 2D. Las aplicaciones que desean aceptar la entrada de texto pueden cambiar a una vista 2D con un cuadro de texto. Mientras que ese cuadro de texto tiene el foco, el sistema mostrará el teclado del sistema, lo que permite al usuario escribir texto.

Tenga en cuenta que los equipos de escritorio, una aplicación puede tener vistas 2D en ambos el monitor de escritorio y en un auricular conectado. Por ejemplo, puede examinar Edge en el monitor de escritorio con su vista 2D principal para encontrar un vídeo de 360 grados. Al reproducir ese vídeo, Edge iniciará una vista secundaria envolvente dentro de los auriculares para mostrar el contenido de vídeo envolvente.

## <a name="see-also"></a>Vea también

* [Modelo de aplicaciones](app-model.md)
* [Actualización de aplicaciones UWP 2D de realidad mixta](building-2d-apps.md)
* [Obtener un HolographicSpace](getting-a-holographicspace.md)
* [Navegar por el inicio de Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
* [Tipos de aplicaciones de realidad mixta](types-of-mixed-reality-apps.md)
