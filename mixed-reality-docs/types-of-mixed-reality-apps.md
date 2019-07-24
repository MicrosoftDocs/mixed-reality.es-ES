---
title: Tipos de aplicaciones de realidad mixta
description: Una de las ventajas de desarrollar aplicaciones para Windows Mixed Reality es que hay un amplio abanico de experiencias que la plataforma puede admitir desde entornos virtuales completamente definados para obtener una capa de información en el entorno actual de un usuario.
author: rwinj
ms.author: willyang
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño y patrones de aplicaciones
ms.openlocfilehash: 97f8039dcd9bbf8ee3d6c7be926db16b60a76b97
ms.sourcegitcommit: 915d3cc63a5571ba22ac4608589f3eca8da1bc81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "63549121"
---
# <a name="types-of-mixed-reality-apps"></a>Tipos de aplicaciones de realidad mixta

Una de las ventajas de desarrollar aplicaciones para Windows Mixed Reality es que hay un abanico de experiencias que la plataforma puede admitir. Desde entornos virtuales totalmente envolventes, para reducir la distribución de la información en el entorno actual de un usuario, Windows Mixed Reality proporciona un sólido conjunto de herramientas para llevar a la vida. Es importante que un creador de aplicaciones entienda pronto en su proceso de desarrollo en cuanto a la ubicación de este espectro. Esta decisión afectará en última instancia a la composición del diseño de la aplicación y a la ruta tecnológica para el desarrollo.

## <a name="enhanced-environment-apps-hololens-only"></a>Aplicaciones de entorno mejoradas (solo HoloLens)

Una de las formas más eficaces en que la realidad mixta puede aportar valor a los usuarios es facilitar la selección de ubicación de la información digital o el contenido en el entorno actual de un usuario. Se trata de una aplicación de entorno mejorada. Este enfoque es popular en el caso de las aplicaciones en las que la ubicación contextual del contenido digital del mundo real es primordial y/o el mantenimiento del entorno real del usuario "presente" durante su experiencia es clave. Este enfoque también permite a los usuarios cambiar fácilmente de las tareas del mundo real a las tareas digitales y volver fácilmente, con lo que se presta más credibilidad para comprometer que las aplicaciones de realidad mixta que ve el usuario realmente forman parte de su entorno.

![Aplicaciones de entorno mejoradas](images/enhancedenvironmentapps-640px.jpg)<br>
*Aplicaciones de entorno mejoradas*

**Ejemplo se usa**
* Una aplicación de estilo de Bloc de notas de realidad mixta que permite a los usuarios crear y colocar notas en torno a su entorno
* Una aplicación de televisión de realidad mixta colocada en un lugar cómodo para ver
* Una aplicación de cocina de realidad mixta colocada sobre la isla de cocina para ayudar en una tarea de cocina
* Una aplicación de realidad mixta que ofrece a los usuarios la sensación de "x-Ray Vision" (es decir, un holograma colocado encima de y imita un objeto del mundo real, a la vez que permite al usuario ver "dentro de ti" de manera holográfica)
* Anotaciones de realidad mixta colocadas en una fábrica para proporcionar la información necesaria del trabajador
* Wayfinding de realidad mixta en un espacio de Office
* Experiencias de sobremesa de realidad mixta (es decir, experiencias de estilo de juego de tablero)
* Aplicaciones de comunicación de realidad mixta como Skype

## <a name="blended-environment-apps"></a>Aplicaciones de entorno mixtas

Dada la capacidad de Windows mixed reality de reconocer y asignar el entorno del usuario, es capaz de crear una capa digital que se puede superponer completamente en el espacio del usuario. El nivel fino respeta la forma y los límites del entorno del usuario, pero la aplicación puede optar por transformar determinados elementos que mejor se adapten para sumergir al usuario en la aplicación. Esto se denomina aplicación de entorno combinada. A diferencia de una aplicación de entorno mejorada, las aplicaciones de entorno combinadas solo pueden ser suficientes para el entorno para usar mejor su composición con el fin de animar el comportamiento de un usuario específico (por ejemplo, para fomentar el movimiento o la exploración) o mediante la sustitución de elementos con cambios (una cocina Counter está prácticamente desollada para mostrar un patrón de mosaico diferente). Este tipo de experiencia puede incluso transformar un elemento en un objeto totalmente diferente, pero conservar las dimensiones aproximadas del objeto como su base (una isla de cocina se transforma en un contenedor para un juego de un atacante de delitos).

![Aplicaciones de entorno mixtas](images/blendedenvironmentapps-640px.jpg)<br>
*Aplicaciones de entorno mixtas*

**Ejemplo se usa**
* Una aplicación de diseño interior de realidad mixta que puede pintar paredes, contrapartes o plantas en diferentes colores y patrones
* Una aplicación de realidad mixta que permite a un diseñador de automóviles crear capas de nuevas iteraciones de diseño para una próxima actualización del automóvil sobre un automóvil existente
* Una cama está "estudiada" y se reemplaza por un stand de realidad mixta del juego de niños
* Un servicio de escritorio está "Tratado" y se reemplaza por un contenedor de realidad mixta en un juego de un emocionante delito
* Una linterna colgante está "tratada" y se reemplaza por el indicador con la misma forma y dimensión.
* Una aplicación que permite a los usuarios sacudir agujeros en sus muros mundiales reales o envolventes, lo que revela un mundo mágico.

## <a name="immersive-environment-apps"></a>Aplicaciones de entorno inmersivo

Las aplicaciones de entorno inmersivo se centran en torno a un entorno que cambia completamente el mundo del usuario y puede colocarlas en un espacio y una hora distintos. Estos entornos pueden parecer muy reales y crear experiencias envolventes y emocionantes que solo están limitadas por la imaginación del creador de la aplicación. A diferencia de las aplicaciones de entorno mixtas, una vez que Windows Mixed Reality identifica el espacio del usuario, una aplicación de entorno inmersivo puede descartar completamente el entorno actual del usuario y reemplazar las existencias por una sola. Estas experiencias también pueden separar completamente el tiempo y el espacio, lo que significa que un usuario podría recorrer las calles de Roma en una experiencia envolvente, mientras que el resto del espacio real todavía está en su espacio real. Es posible que el contexto del entorno real no sea importante para una aplicación de entorno envolvente.

![Aplicaciones de entorno inmersivo](images/windows-mixed-reality-640px.jpg)<br>
*Aplicaciones de entorno inmersivo*

**Ejemplo se usa**
* Una aplicación envolvente que permite a un usuario retrasar un espacio completamente independiente de su propia (es decir, guiar por un famoso edificio, Museo, ciudad popular)
* Una aplicación envolvente que organiza un evento o escenario alrededor del usuario (es decir, una batalla o un rendimiento)

## <a name="see-also"></a>Vea también
* [Introducción al desarrollo](development-overview.md)
* [Modelo de aplicaciones](app-model.md)
* [Vistas de aplicación](app-views.md)
