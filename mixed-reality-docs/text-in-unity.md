---
title: Texto en Unity
description: Para mostrar texto en Unity, hay dos tipos de componentes de texto que puede utilizar, el texto de la interfaz de usuario y el texto 3D de malla.
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality, diseño, controles, fuentes, tipografía, interfaz de usuario, experiencia de usuario
ms.openlocfilehash: 7d40db2e0571e835e28e444c7921e1a086800936
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829974"
---
# <a name="text-in-unity"></a>Texto en Unity

Texto es uno de los componentes más importantes en las aplicaciones holográficas. Para mostrar texto en Unity, hay tres tipos de componentes de texto que puede utilizar, el texto de la interfaz de usuario, texto 3D de malla y texto de la malla Pro. De forma predeterminada el texto de la interfaz de usuario y el texto 3D de malla aparecen borrosos y son demasiado grandes. Deberá ajustar algunas variables para obtener texto sharp y de alta calidad que tiene un tamaño administrable en HoloLens. Al aplicar el factor de escala para obtener las dimensiones adecuadas cuando se usa el texto de la interfaz de usuario y los componentes de texto de la malla 3D, puede lograr una mejor calidad de representación.

![Cómo obtener el texto nítido y atractivo](images/hug-text-02-640px.png)<br>
*Texto predeterminado borrosos en Unity*

## <a name="working-with-unitys-3d-texttext-mesh-and-ui-text"></a>Trabajar con texto 3D (texto malla) y el texto de la interfaz de usuario de Unity

Unity se da por supuesto que todos los elementos nuevos que se agregan a una escena son 1 unidad de Unity en el tamaño o la escala de transformación de 100%, lo que se traduce a aproximadamente 1 metro en HoloLens. En el caso de las fuentes, el cuadro de límite para un TextMesh 3D resulta en aproximadamente 1 metro en el alto de forma predeterminada.

![Trabajar con fuentes en Unity](images/640px-hug-text-03.png)<br>
*Texto 3D de Unity predeterminado (texto de la malla) ocupa 1 unidad de Unity que es de 1 metro*

<br>
La mayoría de los diseñadores visuales utilizan puntos para definir tamaños de fuente en el mundo real. Hay aproximadamente 2835 (2,834.645666399962) puntos de 1 metro. En función de la conversión del sistema de punto de 1 metro y predeterminado de la malla texto tamaño de fuente 13 Unity, la expresión matemática simple de 13 dividida por igual 2835 0.0046 (0.004586111116 para ser exactos) proporciona una buena escala estándar para comenzar (algunos que desee redondear en 0,005). Escalar el objeto de texto o el contenedor a estos valores no sólo permitirá la conversión de 1:1 de fuente cambia el tamaño de un programa de diseño, pero también proporciona un estándar para que pueda mantener la coherencia a lo largo de su experiencia.

![Unity Mesh texto 3D con distintos tamaños de fuente](images/Text_In_Unity_Measurements1.png)<br>
*Valores de escalado para el texto 3D de Unity y el texto de la interfaz de usuario*

![Unity Mesh texto 3D con distintos tamaños de fuente](images/hug-text-05-1000px.png)<br>
*Unity Mesh texto 3D con valores optimizados*

<br>
Al agregar un elemento de texto en función de la interfaz de usuario o de lienzo a una escena, aún es mayor la disparidad de tamaño. Las diferencias en los dos tamaños es aproximadamente 1000%, lo que podría poner el factor de escala para los componentes de texto en función de la interfaz de usuario a 0.00046 (0.0004586111116 para ser exactos) o 0,0005 para el valor redondeado.

![Texto de la interfaz de usuario de Unity con diferentes píxeles dinámicas por valores de unidad](images/hug-text-04-1000px.png)<br>
*Texto de la interfaz de usuario de Unity con valores optimizados*

<br>

>[!NOTE]
>El valor predeterminado de cualquier fuente puede verse afectado por el tamaño de textura de esa fuente o cómo se importó la fuente en Unity. Estas pruebas se realizaron en función de la fuente Arial de forma predeterminada en Unity, así como otras fuentes importados.

## <a name="working-with-text-mesh-pro"></a>Trabajar con texto de la malla Pro

Con texto de la malla Pro del Unity, puede proteger la calidad de representación de texto. Admite el esquema de texto claro la distancia con independencia de la [SDF (campo de distancia Signed)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) técnica. Con el mismo método de cálculo que se ha usado anteriormente para el texto 3D de malla y el texto de la interfaz de usuario, podemos encontrar los valores de escalado adecuados usar punto tipográfico convencional. Puesto que la fuente predeterminada de Pro de texto de la malla 3D con el tamaño de 36 muestra el rectángulo de selección de 2,5 Unit(2.5m) de Unity, podemos usar el valor de escala 0,005 para usar el tamaño de punto. El texto de la malla Pro en el menú de la interfaz de usuario tiene el valor predeterminado límite de tamaño de 25 Unit(25m) de Unity. Esto nos da 0,0005 para el valor de escala.

![Unity Mesh texto 3D con distintos tamaños de fuente](images/Text_In_Unity_Measurements2.png)<br>
*Valores de escalado para el texto 3D de Unity y el texto de la interfaz de usuario*

## <a name="recommended-text-size"></a>Tamaño de texto recomendado
Como puede esperar, los tamaños de tipo que se usan en un equipo o un dispositivo de tableta gráfica (normalmente entre 12 – 32pt) busque bastante pequeños a una distancia de 2 metros. Depende de las características de cada fuente, pero en general son los requisitos mínimos de visualización de ángulo y el alto de fuente para mejorar la legibilidad en torno a 0.35°-0.4°/12.21-13.97mm según nuestros estudios de investigación de usuario. Se trata de 35 40pt con el factor de escala descrito anteriormente. 

Para la interacción casi en 0.45m(45cm), ángulo de visión de la fuente legible mínimo y el alto son 0,4 °-0,5 ° / mediana empresa 3.14 – 3.9. 9-12 pt se trata con el factor de escala descrito anteriormente.

![NEAR y far intervalo interacción](images/typography-distance-1000px.jpg)
*intervalo lejos y contenido en cerca de la interacción*

### <a name="the-minimum-legible-font-size"></a>El tamaño mínimo de fuente legible
| distancia | Ángulo de visión | Alto del texto | Tamaño de fuente |
|---------|---------|---------|---------|
| 45cm (distancia manipulación directa) | 0.4°-0.5° | 3.14 – 3.9 mm | 8.9–11.13pt |
| 2m | 0.35°-0.4° | 12.21 – 13.97 mm | 34.63-39.58pt |


### <a name="the-comfortably-legible-font-size"></a>El tamaño de fuente cómodamente legibles
| distancia | Ángulo de visión | Alto del texto | Tamaño de fuente |
|---------|---------|---------|---------|
| 45cm (distancia manipulación directa) | 0.65°-0.8° | 5.1-6.3 mm | 14.47-17.8pt |
| 2m | 0.6°-0.75° | 20,9-26,2 mm | 59.4-74.2pt |

Segoe UI (la fuente predeterminada para Windows) funciona bien en la mayoría de los casos. Sin embargo, evite usar light o semi familias de fuentes de luz en tamaño pequeño, puesto que se vibran finos trazos verticales y reducirá la legibilidad. Las fuentes modernas con suficiente grosor del trazo funcionan bien. Por ejemplo, Helvetica y Arial buscar magníficos y son muy legibles en HoloLens con pesos normales o en negrita.


![Ángulo de visión](images/Text_In_Unity_ViewingAngle.jpg)
*ver alto de distancia, angulares y texto*

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a>Nítida calidad de representación de texto con dimensión adecuada

En función de estos factores de escala, hemos creado [prefabricados texto con texto de la interfaz de usuario y el texto 3D de malla](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text). Los desarrolladores pueden usar estas prefabricados obtener nítida de texto y el tamaño de fuente coherente.

![Nítida calidad de representación de texto con dimensión adecuada](images/hug-text-06-1000px.png)<br>
*Nítida calidad de representación de texto con dimensión adecuada*

## <a name="shader-with-occlusion-support"></a>Sombreador de soporte técnico de oclusión

Material de fuente predeterminado de Unity no es compatible con la oclusión. Por este motivo, se mostrará el texto detrás de los objetos de forma predeterminada. Hemos incluido una sencilla [sombreador que admita la ocultación de](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit/StandardAssets/Shaders/Text3DShader.shader). La imagen siguiente muestra el texto con el material de fuente predeterminado (izquierda) y el texto con oclusión adecuado (derecha).

![Sombreador de soporte técnico de oclusión](images/hug-text-07-1000px.png)<br>
*Sombreador de soporte técnico de oclusión*


## <a name="see-also"></a>Vea también
* [Recurso prefabricado de texto en el MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text)
* [Tipografía](typography.md)

 
