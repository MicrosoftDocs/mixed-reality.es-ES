---
title: Tipografía
description: El texto es un elemento importante para entregar información en la experiencia de la aplicación.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, diseño, estilo, fuente, tipografía, UI, UX
ms.openlocfilehash: cc8e25e9cd7ba41bed179328fe7198e935e65d76
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66830015"
---
# <a name="typography"></a>Tipografía

El texto es un elemento importante para entregar información en la experiencia de la aplicación. Al igual que la tipografía en pantallas 2D, el objetivo es ser claro y legible. Con el aspecto tridimensional de la realidad mixta, existe la posibilidad de afectar al texto y a la experiencia global del usuario de una manera incluso mayor.

![Ejemplo de tipografía en HoloLens](images/typography-cover.png)<br>
*Ejemplo de tipografía en HoloLens*

Cuando hablemos sobre el tipo en 3D, se tiende a pensar en el texto 3D extruido. A excepción de algunos diseños de logotipo y otras aplicaciones limitadas, el texto extruido tiende a degradar la legibilidad del texto. Aunque estamos diseñando experiencias para 3D, usamos 2D para el tipo porque es más legible y más fácil de leer.

En HoloLens, el tipo se construye con hologramas que usan la luz basada en el sistema de colores aditivo. Al igual que otros hologramas, el tipo se puede colocar en el entorno real, donde se puede bloquear y observar en cualquier ángulo. El efecto de [Parallax](https://en.wikipedia.org/wiki/Parallax) entre el tipo y el entorno también agrega profundidad a la experiencia.

## <a name="typography-in-mixed-reality"></a>Tipografía en realidad mixta

Las reglas tipográficas de realidad mixta no son diferentes de cualquier otra cosa. El texto del mundo físico y del mundo virtual debe ser legible y legible. El texto podría estar en un muro o superpuesto en un objeto físico. Podría ser flotante junto con una interfaz de usuario digital. Independientemente del contexto, se aplican las mismas reglas tipográficas para lectura y reconocimiento.

### <a name="create-clear-hierarchy"></a>Crear una jerarquía clara

Cree el contraste y la jerarquía mediante el uso de diferentes tamaños y pesos de tipos. La definición de una rampa de tipos y su continuación a lo largo de la experiencia de la aplicación proporcionará una excelente experiencia de usuario con una jerarquía de información coherente.

![Ejemplos de rampa de tipos](images/typography-ramp-1000px.jpg)<br>
*Definir la rampa de tipos y seguirla a lo largo de la experiencia de la aplicación*

### <a name="limit-your-fonts"></a>Limitar las fuentes

Evite usar más de dos familias de fuentes diferentes en un único contexto. Esto interrumpirá la armonía y la coherencia de su experiencia y dificultará el consumo de información. En HoloLens, dado que la información se superpone en el entorno físico, el uso de demasiados estilos de fuente degradará la experiencia. Segoe UI es la fuente de todos los diseños digitales de Microsoft. Se usa de forma coherente en el shell de Windows Mixed Reality. Puede descargar el archivo de fuente de Segoe UI desde la [página del kit de herramientas de diseño de Windows](https://docs.microsoft.com/windows/uwp/design-downloads/).

[Más información sobre el Segoe UI tipo de letra](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a>Evitar los pesos de fuente finos

Evite usar pesos de fuentes ligeras o semiligeras para tamaños de tipos en fuente, ya que los trazos verticales finos vibrarán y disminuirán la legibilidad. Las fuentes modernas con un grosor de trazo suficiente funcionan bien. Por ejemplo, Helvetica y Arial son muy legibles en HoloLens con pesos normales o en negrita.

### <a name="color"></a>Color

En HoloLens, dado que los hologramas se construyen con un sistema de luz aditiva, el texto en blanco es muy legible. Puede encontrar ejemplos de texto en blanco en el menú Inicio y en la barra de la aplicación. Aunque el texto en blanco funciona bien sin una placa trasera en HoloLens, un fondo físico complejo podría dificultar la lectura del tipo. Para mejorar el foco del usuario y minimizar la distracción desde un fondo físico, se recomienda usar texto en blanco en una plancha de fondo oscuro o de color.

<br>


![Se recomienda usar texto en blanco en una plancha de fondo oscuro o de color. *Ejemplos de texto en blanco en una plancha de fondo oscuro o de color.* ](images/typography-whiteonblack2-1000px.jpg)

<br>

Para usar texto oscuro, debe usar una placa trasera brillante para que sea legible. En los sistemas de color aditivos, el color negro se muestra como transparente. Esto significa que no podrá ver el texto en negro sin una plancha de fondo de color.

![Ejemplos de texto en negro](images/typography-whiteonblack.png)
<br>*Ejemplos de blanco hacia atrás y negros en texto en blanco*


![Ejemplos de texto en negro](images/640px-typography-blackonwhite.jpg)
<br>*Ejemplos de texto en negro en las aplicaciones del sistema: tienda y configuración*

## <a name="recommended-font-size"></a>Tamaño de fuente recomendado

Como cabe esperar, los tamaños de tipo que usamos en un equipo o un dispositivo de tableta (normalmente entre 12 – 32pt.) son bastante pequeños a una distancia de 2 metros. Depende de las características de cada fuente, pero, en general, el ángulo de visualización mínimo recomendado y el alto de la fuente para la legibilidad son alrededor de 0.35 °-0,4 °/12.21-13.97mm según nuestros estudios de investigación de usuarios. Es aproximadamente 35-40pt con el factor de escala introducido en la página de [texto en Unity](text-in-unity.md) . 

En el caso de la interacción cercana en 0.45 m (45CM), el ángulo de visualización de la fuente mínima legible y el alto son 0,4 °-0,5 °/3.14 – 3,9 mm. Es aproximadamente 9-12 PTO con el factor de escala introducido en el [texto en Unity](text-in-unity.md).

![Contenido del intervalo](images/typography-distance-1000px.jpg)
de interacción Near y Far*en el intervalo de interacción Near y Far*

### <a name="the-minimum-legible-font-size"></a>El tamaño mínimo de fuente legible
| posición | Ángulo de visualización | Alto de texto | Tamaño de fuente * * |
|---------|---------|---------|---------|
| 45CM (distancia de manipulación directa) | 0,4 °-0,5 ° | 3.14:3,9 mm | 8.9:11.13 pt |
| 2m | 0.35 °-0,4 ° | 12.21 – 13.97 mm | 34.63-39.58 PT |


### <a name="the-comfortably-legible-font-size"></a>Tamaño de fuente cómodamente legible
| posición | Ángulo de visualización | Alto de texto | Tamaño de fuente * * |
|---------|---------|---------|---------|
| 45CM (distancia de manipulación directa) | 0,65 °-0,8 ° | 5.1-6.3 mm | 14.47-17.8 pt |
| 2m | 0,6 °-0,75 ° | 20.9-26.2 mm | 59.4-74.2 PT |


Segoe UI (la fuente predeterminada para Windows) funciona bien en la mayoría de los casos. Sin embargo, evite usar familias de fuentes ligeras o semiligeras con un tamaño reducido, ya que los trazos verticales finos vibrarán y disminuirán la legibilidad. Las fuentes modernas con un grosor de trazo suficiente funcionan bien. Por ejemplo, Helvetica y Arial parecen magníficas y son muy legibles en HoloLens con pesos normales o en negrita.

\* * Para obtener información más detallada sobre el cálculo del tamaño de texto en Unity, consulte el [texto de la página en Unity](text-in-unity.md) .

![Visualización del](images/Text_In_Unity_ViewingAngle.jpg)
ángulo de*visualización de la distancia, el ángulo y el alto del texto*

## <a name="resources"></a>Recursos
* [Fuentes Segoe](http://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)
* [Fuente de HoloLens](http://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)

![La fuente HoloLens proporciona los glifos de símbolos usados en Windows Mixed Reality.](images/300px-hololensmdl2symbols.jpg)
<br>*La fuente HoloLens proporciona los glifos de símbolos usados en Windows Mixed Reality.*

## <a name="see-also"></a>Vea también
* [Texto en Unity](text-in-unity.md)
* [Color, luz y materiales](color,-light-and-materials.md)
