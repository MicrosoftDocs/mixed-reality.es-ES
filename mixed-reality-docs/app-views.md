---
title: Vistas de aplicación
description: Los dos tipos de vistas de las aplicaciones de Windows Mixed Reality son vistas envolventes y vistas 2D.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: vista envolvente, vista 2D, pizarra, aplicación
ms.openlocfilehash: a5b50df5be31d66a866e691d9e059bcf38672064
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437033"
---
# <a name="app-views"></a>Vistas de aplicación

Las aplicaciones de Windows pueden contener dos tipos de vistas: vistas **envolventes** y **vistas 2D**. Las aplicaciones pueden cambiar entre las distintas vistas de envolvente y las vistas 2D, mostrando sus vistas 2D en un monitor como una ventana o en un casco como pizarra. Las aplicaciones que tienen al menos una vista envolvente se clasifican como **aplicaciones de realidad mixta**. Las aplicaciones que nunca tienen una vista envolvente son **aplicaciones 2D**.

## <a name="immersive-views"></a>Vistas envolventes

Una vista envolvente ofrece a la aplicación la posibilidad de crear hologramas en el mundo o sumergir al usuario en un entorno virtual. Cuando una aplicación está dibujando en la vista envolvente, ninguna otra aplicación está dibujando al mismo tiempo&mdash;los hologramas de varias aplicaciones no se componen juntos. Al ajustar continuamente la perspectiva desde la que la [aplicación representa](rendering.md) su escena para que coincida con los movimientos principales del usuario, la aplicación puede representar hologramas [de bloque mundial](coordinate-systems.md) que permanecen en un punto fijo del mundo real o puede representar un mundo virtual que contiene su posición cuando un usuario se mueve dentro de ella.

![cuando se encuentra en una vista envolvente, los hologramas se pueden colocar en todo el mundo.](images/designoverview-940px.jpg)<br>
*Cuando se encuentra en una vista envolvente, los hologramas se pueden colocar en todo el mundo*

En [HoloLens](hololens-hardware-details.md), la aplicación representa sus hologramas sobre el entorno real del usuario. En un [casco con Windows Mixed Reality](immersive-headset-hardware-details.md), el usuario no puede ver el mundo real y, por tanto, la aplicación debe representar todo lo que verá el usuario.

La [Página principal de Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md) (incluido el menú Inicio y los hologramas que ha colocado en torno al entorno) no se representa en una vista envolvente. En HoloLens, las notificaciones del sistema que se producen mientras se muestra una vista envolvente se retransmiten de forma audible por Cortana y el usuario puede responder con la entrada de voz.

En una vista envolvente, la aplicación también es responsable de controlar todas las entradas. La entrada en Windows Mixed Reality se compone de [los controladores](motion-controllers.md) de [mirados](gaze-and-commit.md), [gestos](gaze-and-commit.md#composite-gestures) (solo HoloLens), [voz](voice-input.md) y movimiento (solo auriculares inmersivo).

## <a name="2d-views"></a>vistas 2D

![varias vistas 2D diseñadas en torno a la Página principal de Windows Mixed Reality](images/teleportation-940px.png)<br>
*Varias aplicaciones con una vista 2D colocada en torno a la Página principal de Windows Mixed Reality*

Una aplicación con una vista 2D aparece en la [Página principal de Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md) (a veces denominada "Shell") como una pizarra virtual, representada junto con los iniciadores de aplicaciones y otros hologramas que el usuario ha colocado en su mundo. El usuario puede ajustar esta pizarra para moverla y escalarla, aunque permanece en una resolución fija, independientemente de su tamaño. Si la primera vista de la aplicación es una vista 2D, el contenido 2D rellenará la misma pizarra que se usa para iniciar la aplicación.

En un casco de escritorio, puede ejecutar cualquier aplicación Plataforma universal de Windows (UWP) que se ejecute en el monitor de escritorio hoy mismo. Estas aplicaciones ya representan vistas en 2D, y su contenido aparecerá automáticamente en una pizarra en el mundo del usuario cuando se inicie. las aplicaciones para UWP en 2D pueden tener como destino la familia de dispositivos **Windows. universal** para ejecutarse en auriculares de escritorio y en HoloLens como pizarras.

Un uso clave de las vistas 2D es mostrar un formulario de entrada de texto que puede hacer uso del teclado del sistema. Dado que el shell no se puede representar en la parte superior de una vista envolvente, la aplicación debe cambiar a una vista 2D para mostrar el teclado del sistema. Las aplicaciones que quieren aceptar la entrada de texto pueden cambiar a una vista 2D con un cuadro de texto. Mientras el cuadro de texto tenga el foco, el sistema mostrará el teclado del sistema, lo que permite al usuario escribir texto.

Tenga en cuenta que, en un equipo de escritorio, una aplicación puede tener vistas 2D en el monitor de escritorio y en un casco conectado. Por ejemplo, puede examinar el borde en el monitor de escritorio usando su vista de 2D principal para buscar un vídeo de 360 grados. Al reproducir ese vídeo, Edge iniciará una vista envolvente secundaria dentro de los auriculares para mostrar el contenido de vídeo envolvente.

## <a name="see-also"></a>Consulta también

* [Modelo de aplicaciones](app-model.md)
* [Actualización de aplicaciones para UWP bidimensionales para la realidad mixta](building-2d-apps.md)
* [Obtención de HolographicSpace](getting-a-holographicspace.md)
* [Desplazamiento por la página principal de Windows Mixed Reality](navigating-the-windows-mixed-reality-home.md)
* [Tipos de aplicaciones de realidad mixta](types-of-mixed-reality-apps.md)
