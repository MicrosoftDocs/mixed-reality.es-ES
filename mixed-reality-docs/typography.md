---
title: Tipografía
description: Texto es un elemento importante para la entrega de información en su experiencia de aplicación.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, diseño, estilo, fuente, tipografía, interfaz de usuario, experiencia de usuario
ms.openlocfilehash: cc8e25e9cd7ba41bed179328fe7198e935e65d76
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66830015"
---
# <a name="typography"></a>Tipografía

Texto es un elemento importante para la entrega de información en su experiencia de aplicación. Tipografía en pantallas 2D, como el objetivo es tener claras y legibles. Con el aspecto tridimensional de realidad mixta, hay una oportunidad para influir en el texto y el usuario general experiencia de una manera incluso mayor.

![Ejemplo de tipografía en HoloLens](images/typography-cover.png)<br>
*Ejemplo de tipografía en HoloLens*

Cuando hablamos sobre el tipo de 3D, tendemos a pensar extruido, volumétrico texto 3D. Excepto en algunos diseños de logotipo y algunas otras aplicaciones limitadas, texto extruido tiende a disminuir la legibilidad del texto. Aunque estamos diseñando las experiencias para 3D, usamos 2D para el tipo porque es más legible y fácil de leer.

En HoloLens, el tipo se construye con hologramas mediante luz en función del sistema de color aditivos. Al igual que otros hologramas, tipo puede colocarse en el entorno real donde puede ser mundo bloqueado y observa desde cualquier ángulo. El [paralaje](https://en.wikipedia.org/wiki/Parallax) efecto entre el tipo y el entorno también agrega profundidad a la experiencia.

## <a name="typography-in-mixed-reality"></a>Tipografía en realidad mixta

Reglas tipográficas en mixed reality no son distintas de cualquier otro lugar. Texto en el mundo físico y el mundo virtual debe ser legible y legible. Texto podría ser en una pared o superpuesto a un objeto físico. Podría ser flotante junto con una interfaz de usuario digital. Independientemente del contexto, aplicamos las mismas reglas tipográficas para lectura y el reconocimiento.

### <a name="create-clear-hierarchy"></a>Crear jerarquía clara

Compilar contraste y jerarquía usando las ponderaciones y los tamaños de tipo diferente. Definir una rampa de tipos y que hay a continuación a lo largo de la experiencia de aplicación ofrecerá una experiencia de usuario excelente con jerarquía información coherente.

![Ejemplos de rampa de tipos](images/typography-ramp-1000px.jpg)<br>
*Definir su rampa de tipos y seguirlo a lo largo de la experiencia de aplicación*

### <a name="limit-your-fonts"></a>Limitar las fuentes

Evite el uso de más de dos familias de fuentes diferentes en un contexto único. Esto rompería la armonía y la coherencia de la experiencia y que sea más difícil consumir información. En HoloLens, puesto que se superpone a la información del entorno físico, con demasiados estilos de fuente se degradará la experiencia. Segoe UI es la fuente para todos los diseños digitales de Microsoft. Se usa de forma coherente en el shell de Windows Mixed Reality. Puede descargar el archivo de la fuente Segoe UI desde la [página del Kit de herramientas de diseño de Windows](https://docs.microsoft.com/windows/uwp/design-downloads/).

[Para obtener más información sobre el tipo de letra Segoe UI](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a>Evitar los pesos de fuente fina

Evite el uso de pesos de la fuente de luz o semilight para los tamaños de tipo en 42pt porque finos trazos verticales se Vibrar y degradar la legibilidad. Las fuentes modernas con suficiente grosor del trazo funcionan bien. Por ejemplo, Helvetica y Arial son muy legibles en HoloLens mediante valores ponderados normales o en negrita.

### <a name="color"></a>Color

En HoloLens, puesto que el hologramas se construyen con un sistema claro aditivo, texto en blanco es muy legible. Puede encontrar ejemplos de texto en blanco en el menú Inicio y la barra de la aplicación. Aunque texto blanco funciona bien sin un plato de back-en HoloLens, un fondo físico compleja podría realizar el tipo difícil de leer. Para mejorar el enfoque del usuario y minimizar la distracción del fondo de la física, se recomienda usar texto en blanco en un plato oscuro o nuevo color.

<br>


![Se recomienda usar texto en blanco en un plato de back-oscuro o de color. ](images/typography-whiteonblack2-1000px.jpg)
 *Ejemplos de texto en blanco en un plato de back-oscuro o de color.*
<br>

Para usar texto oscuro, debe usar un plato de back-brillante para que sea legible. En los sistemas de color aditivos, negro se muestra como transparente. Esto significa que no podrá ver el texto negro sin un color hacer una copia de la placa.

![Ejemplos de texto en negro](images/typography-whiteonblack.png)
<br>*Ejemplos de blanco en back y negro en texto en blanco*


![Ejemplos de texto en negro](images/640px-typography-blackonwhite.jpg)
<br>*Ejemplos de texto de color negro en las aplicaciones del sistema - Store y configuración*

## <a name="recommended-font-size"></a>Tamaño de fuente recomendado

Como puede esperar, los tamaños de tipo que se usan en un equipo o un dispositivo de tableta gráfica (normalmente entre 12 – 32pt) busque bastante pequeños a una distancia de 2 metros. Depende de las características de cada fuente, pero en general son los requisitos mínimos de visualización de ángulo y el alto de fuente para mejorar la legibilidad en torno a 0.35°-0.4°/12.21-13.97mm según nuestros estudios de investigación de usuario. Se trata de 35 40pt con el factor de escala que se introdujo en [texto en Unity](text-in-unity.md) página. 

Para la interacción casi en 0.45m(45cm), ángulo de visión de la fuente legible mínimo y el alto son 0,4 °-0,5 ° / mediana empresa 3.14 – 3.9. Se trata de 9-12 pt con el factor de escala que se introdujo en [texto en Unity](text-in-unity.md).

![NEAR y far intervalo interacción](images/typography-distance-1000px.jpg)
*intervalo lejos y contenido en cerca de la interacción*

### <a name="the-minimum-legible-font-size"></a>El tamaño mínimo de fuente legible
| distancia | Ángulo de visión | Alto del texto | Tamaño de fuente ** |
|---------|---------|---------|---------|
| 45cm (distancia manipulación directa) | 0.4°-0.5° | 3.14 – 3.9 mm | 8.9–11.13pt |
| 2m | 0.35°-0.4° | 12.21 – 13.97 mm | 34.63-39.58pt |


### <a name="the-comfortably-legible-font-size"></a>El tamaño de fuente cómodamente legibles
| distancia | Ángulo de visión | Alto del texto | Tamaño de fuente ** |
|---------|---------|---------|---------|
| 45cm (distancia manipulación directa) | 0.65°-0.8° | 5.1-6.3 mm | 14.47-17.8pt |
| 2m | 0.6°-0.75° | 20,9-26,2 mm | 59.4-74.2pt |


Segoe UI (la fuente predeterminada para Windows) funciona bien en la mayoría de los casos. Sin embargo, evite usar light o semi familias de fuentes de luz en tamaño pequeño, puesto que se vibran finos trazos verticales y reducirá la legibilidad. Las fuentes modernas con suficiente grosor del trazo funcionan bien. Por ejemplo, Helvetica y Arial buscar magníficos y son muy legibles en HoloLens con pesos normales o en negrita.

** Para obtener más información acerca del cálculo de tamaño de texto en Unity, consulte la página [texto en Unity](text-in-unity.md)

![Ángulo de visión](images/Text_In_Unity_ViewingAngle.jpg)
*ver alto de distancia, angulares y texto*

## <a name="resources"></a>Recursos
* [Fuentes de Segoe](http://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)
* [Fuente de HoloLens](http://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)

![La fuente de HoloLens le ofrece los glifos de símbolos utilizados en Windows Mixed Reality](images/300px-hololensmdl2symbols.jpg)
<br>*La fuente de HoloLens le ofrece los glifos de símbolos utilizados en Windows Mixed Reality.*

## <a name="see-also"></a>Vea también
* [Texto en Unity](text-in-unity.md)
* [Color, luz y materiales](color,-light-and-materials.md)
