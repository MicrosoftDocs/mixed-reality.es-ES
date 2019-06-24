---
title: Texto en Unity
description: Para mostrar texto en Unity, hay dos tipos de componentes de texto que puede utilizar, el texto de la interfaz de usuario y el texto 3D de malla.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, controles, fuentes, tipografía, interfaz de usuario, experiencia de usuario
ms.openlocfilehash: 45037f27f68a19478fd56a6edc940fbe45ae7671
ms.sourcegitcommit: 30246ab9b9be44a3c707061753e53d4bf401eb6b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2019
ms.locfileid: "67326301"
---
# <a name="text-in-unity"></a>Texto en Unity

Texto es uno de los componentes más importantes en las aplicaciones holográficas. Para mostrar texto en Unity, hay dos tipos de componentes de texto que puede utilizar, el texto de la interfaz de usuario y el texto 3D de malla. De forma predeterminada, se ve borroso y son demasiado grandes. Deberá ajustar algunas variables para obtener texto sharp y de alta calidad que tiene un tamaño administrable en HoloLens. Al aplicar el factor de escala para obtener las dimensiones adecuadas cuando se usa el texto de la interfaz de usuario y los componentes de texto de la malla 3D, puede lograr una mejor calidad de representación.

![Cómo obtener el texto nítido y atractivo](images/hug-text-02-640px.png)<br>
*Texto predeterminado borrosos en Unity*

## <a name="working-with-fonts-in-unity"></a>Trabajar con fuentes en Unity

Unity se da por supuesto que todos los elementos nuevos que se agregan a una escena son 1 unidad de Unity en el tamaño o la escala de transformación de 100%, lo que se traduce a aproximadamente 1 metro en HoloLens. En el caso de las fuentes, el cuadro de límite para un TextMesh 3D resulta en aproximadamente 1 metro en el alto de forma predeterminada.

![Trabajar con fuentes en Unity](images/640px-hug-text-03.png)<br>
*Texto de Unity predeterminado ocupa 1 unidad de Unity que es de 1 metro*

<br>
La mayoría de los diseñadores visuales utilizan puntos para definir tamaños de fuente en el mundo real. Hay aproximadamente 2835 (2,834.645666399962) puntos de 1 metro. En función de la conversión del sistema de punto de 1 metro y predeterminado de la malla texto tamaño de fuente 13 Unity, la expresión matemática simple de 13 dividida por igual 2835 0.0046 (0.004586111116 para ser exactos) proporciona una buena escala estándar para comenzar (algunos que desee redondear en 0,005). Escalar el objeto de texto o el contenedor a estos valores no sólo permitirá la conversión de 1:1 de fuente cambia el tamaño de un programa de diseño, pero también proporciona un estándar para que pueda mantener la coherencia en toda la aplicación o juego.

![Unity Mesh texto 3D con distintos tamaños de fuente](images/hug-text-05-1000px.png)<br>
*Unity Mesh texto 3D con valores optimizados*

<br>
Al agregar un elemento de texto en función de la interfaz de usuario o de lienzo a una escena, aún es mayor la disparidad de tamaño. Las diferencias en los dos tamaños es aproximadamente 1000%, lo que podría poner el factor de escala para los componentes de texto en función de la interfaz de usuario a 0.00046 (0.0004586111116 para ser exactos) o 0,0005 para el valor redondeado.

![Texto de la interfaz de usuario de Unity con diferentes píxeles dinámicas por valores de unidad](images/hug-text-04-1000px.png)<br>
*Texto de la interfaz de usuario de Unity con valores optimizados*

<br>

>[!NOTE]
>El valor predeterminado de cualquier fuente puede verse afectado por el tamaño de textura de esa fuente o cómo se importó la fuente en Unity. Estas pruebas se realizaron en función de la fuente Arial de forma predeterminada en Unity, así como otras fuentes importados.

## <a name="sharp-text-rendering-quality-with-proper-dimension"></a>Nítida calidad de representación de texto con dimensión adecuada

En función de estos factores de escala, hemos creado [prefabricados texto con texto de la interfaz de usuario y el texto 3D de malla](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MixedRealityToolkit.SDK/StandardAssets/Prefabs/Text). Los desarrolladores pueden usar estas prefabricados obtener nítida de texto y el tamaño de fuente coherente.

![Nítida calidad de representación de texto con dimensión adecuada](images/hug-text-06-1000px.png)<br>
*Nítida calidad de representación de texto con dimensión adecuada*

## <a name="shader-with-occlusion-support"></a>Sombreador de soporte técnico de oclusión

Material de fuente predeterminado de Unity no es compatible con la oclusión. Por este motivo, se mostrará el texto detrás de los objetos de forma predeterminada. Hemos incluido una sencilla [sombreador que admita la ocultación de](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Shaders). La imagen siguiente muestra el texto con el material de fuente predeterminado (izquierda) y el texto con oclusión adecuado (derecha).

![Sombreador de soporte técnico de oclusión](images/hug-text-07-1000px.png)<br>
*Sombreador de soporte técnico de oclusión*

## <a name="recommended-type-size"></a>Tamaño de tipo recomendado

Como puede esperar, los tamaños de tipo que se usan en un equipo o un dispositivo de tableta gráfica (normalmente entre 12 – 32pt) busque bastante pequeños a una distancia de 2 metros. Depende de las características de cada fuente, pero en general es el tamaño de tipo mínima recomendada para mejorar la legibilidad sin vibración trazo alrededor de 30pt, según el factor de escala descrito anteriormente. Si se supone que la aplicación para se puede usar en una distancia de más de cerca, podrían usar los tamaños más pequeños de tipo. Para la selección de la fuente Segoe UI (la fuente predeterminada para Windows) funciona bien en la mayoría de los casos. Sin embargo, evite utilizar light o semi fuentes de luz para los tamaños de tipo en 42pt porque se vibran finos trazos verticales y reducirá la legibilidad. Las fuentes modernas con suficiente grosor del trazo funcionan bien. Por ejemplo, Helvetica y Arial buscar magníficos y son muy legibles en HoloLens con pesos normales o en negrita.

![Tamaño de tipo recomendado](images/hug-text-08-1000px.png)<br>
*Ejemplo de rampa de tipo*

## <a name="see-also"></a>Vea también

* [Recurso prefabricado de texto en el MixedRealityToolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/UX/Prefabs)
* [Escena y el diseño de texto de ejemplo prefabricado](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX/Scenes)
* [Tipografía](typography.md)

 
