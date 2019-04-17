---
title: Tipos de aplicaciones de realidad mixta
description: Una de las ventajas del desarrollo de aplicaciones para Windows Mixed Reality es que hay una amplia gama de experiencias que puede admitir la plataforma de entornos virtuales completamente envolventes, a disposición en capas información clara sobre environmentl actual de un usuario.
author: rwinj
ms.author: willyang
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, patrones de aplicaciones
ms.openlocfilehash: 97f8039dcd9bbf8ee3d6c7be926db16b60a76b97
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59598707"
---
# <a name="types-of-mixed-reality-apps"></a>Tipos de aplicaciones de realidad mixta

Una de las ventajas del desarrollo de aplicaciones para Windows Mixed Reality es que hay una amplia gama de experiencias que puede admitir la plataforma. Desde entornos completamente envolventes, virtuales, a información clara sobre el entorno actual de un usuario, la creación de capas Windows Mixed Reality proporciona un sólido conjunto de herramientas para que cualquier experiencia cobren vida. Es importante para comprender al principio de su proceso de desarrollo como para que este espectro se encuentra su experiencia un creador de la aplicación. Esta decisión afectará en última instancia, la composición de diseño de la aplicación y la ruta para el desarrollo tecnológica.

## <a name="enhanced-environment-apps-hololens-only"></a>Aplicaciones del entorno mejorada (solo para HoloLens)

Una de las maneras más eficaces que la realidad mixta puede aportar valor a los usuarios es al facilitar la selección de ubicación de la información digital o el contenido en el entorno actual de un usuario. Se trata de una aplicación de un entorno mejorado. Este enfoque es popular para aplicaciones donde la ubicación contextual de contenido digital en el mundo real es primordial o mantener el entorno de usuario reales "present" durante su experiencia es clave. Este enfoque también permite a los usuarios fácilmente mover desde las tareas del mundo real a tareas digitales y realizar una copia fácilmente, incluso más credibilidad para prometen las aplicaciones de realidad mixta, que el usuario ve realmente forman parte de su entorno de préstamos.

![Aplicaciones del entorno mejorada](images/enhancedenvironmentapps-640px.jpg)<br>
*Aplicaciones del entorno mejorada*

**El ejemplo se usa**
* Una aplicación de estilo de Bloc de notas de la realidad mixta que permite a los usuarios crear y colocar notas en torno a su entorno
* Una aplicación de televisión de realidad mixta situar en una ubicación cómoda para su visualización
* Realidad mixta cocinar la aplicación se coloca encima de la isla de cocina para ayudar en una tarea de cocina
* Una aplicación de realidad mixta que ofrece a los usuarios la sensación de "visión de rayos x" (es decir, un holograma coloca en la parte superior de e imita un objeto del mundo real, al tiempo que permite al usuario ver holographically "dentro de él")
* Las anotaciones de realidad mixta se colocan a lo largo de una fábrica para proporcionar la información necesaria del trabajador
* Realidad mixta wayfinding en un espacio de office
* Experiencias teóricos de simulación de realidad mixta (es decir, experiencias de juego de mesa estilo)
* Aplicaciones de comunicación de realidad mixta como Skype

## <a name="blended-environment-apps"></a>Aplicaciones del entorno combinado

Tiene la capacidad de Windows Mixed Reality reconocer y asignar el entorno del usuario, es capaz de crear una capa digital que se puede superponer completamente en el espacio del usuario. Capa delgada respeta la forma y los límites del entorno de usuario, pero la aplicación puede optar por transformar ciertos elementos que se presta mejor para Sumergir el usuario en la aplicación. Esto se denomina una aplicación de entorno combinado. A diferencia de una aplicación de un entorno mejorado, las aplicaciones del entorno combinado, es posible que solo lo suficientemente la atención sobre el entorno para ofrecer la mejor usar su composición para fomentar comportamiento específico del usuario (por ejemplo, fomentar el movimiento o exploración) o si se reemplaza los elementos con cambios (una cocina contador es prácticamente distintas máscaras para mostrar un patrón de mosaico diferentes). Este tipo de experiencia puede incluso transformar un elemento en un objeto completamente diferente, pero conservan las dimensiones del objeto como base aproximadas (una isla de cocina se transforma en un contenedor para un juego de intriga crime).

![Aplicaciones del entorno combinado](images/blendedenvironmentapps-640px.jpg)<br>
*Aplicaciones del entorno combinado*

**El ejemplo se usa**
* Una aplicación de diseño de interiores de realidad mixta que puede pintar paredes, mostradores o suelos en distintos colores y patrones
* Una aplicación de realidad mixta que permite que un diseñador automotriz capa nueva las iteraciones del diseño para la actualización de un automóvil próximas encima de un automóvil existente
* Una cama se "cubierta" y se reemplaza por un stand de fruta de realidad mixta en el juego de niños
* Un departamento de soporte técnico se "cubierto" y se reemplaza con la realidad mixta contenedor en un juego de intriga crime
* Un farol francesa es "cubierto" y se reemplazan con Poste indicador con aproximadamente la misma forma y dimensión
* Una aplicación que permite a los usuarios de carencias sacudida en sus paredes del mundo real o envolventes, que revelar un mundo mágico

## <a name="immersive-environment-apps"></a>Aplicaciones envolventes de entorno

Las aplicaciones envolventes de entorno están centradas en un entorno que cambia completamente el mundo del usuario y colocan en una hora diferente y un espacio. Estos entornos pueden ser muy reales, crear experiencias envolventes y emocionante que solo se ven limitadas por la imaginación del creador de la aplicación. A diferencia de las aplicaciones del entorno combinado, una vez que Windows Mixed Reality identifica el espacio del usuario, una aplicación de entorno envolventes puede totalmente pasar por alto el entorno del usuario actual y reemplazar todo existencias con uno propio. Estas experiencias completamente también pueden separar tiempo y espacio, lo que significa que un usuario puede recorrer las calles de Roma en una experiencia realmente cautivadora, mientras sigue siendo relativamente aún en su espacio del mundo real. Contexto del entorno del mundo real no puede ser importante para una aplicación de entorno envolventes.

![Aplicaciones envolventes de entorno](images/windows-mixed-reality-640px.jpg)<br>
*Aplicaciones envolventes de entorno*

**El ejemplo se usa**
* Una aplicación envolvente que permite a un usuario visita guiada por un espacio completamente independiente de su propio (es decir, se guiará a través de un edificio famoso, museo, ciudad popular)
* Una aplicación envolvente que organiza un evento o un escenario de usuario (es decir, una batalla o un rendimiento)

## <a name="see-also"></a>Vea también
* [Información general sobre desarrollo](development-overview.md)
* [Modelo de aplicaciones](app-model.md)
* [Vistas de aplicación](app-views.md)
