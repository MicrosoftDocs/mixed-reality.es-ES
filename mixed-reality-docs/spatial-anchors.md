---
title: Delimitadores espaciales
description: Procedimientos recomendados para usar delimitadores espaciales para representar hologramas estables.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: del sistema de coordenadas, del sistema de coordenadas espacial, escala mundial, mundo, escala, posición, orientación, delimitador, delimitador espacial, bloqueado por el mundo, el mundo de bloqueo, persistencia, uso compartido
ms.openlocfilehash: 16165194d040ad22f7885897eddcc65cf9dcaec3
ms.sourcegitcommit: 1c0fbee8fa887525af6ed92174edc42c05b25f90
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2019
ms.locfileid: "65730859"
---
# <a name="spatial-anchors"></a>Delimitadores espaciales

Un anclaje espacial representa un punto importante en el mundo que el sistema debe realizar un seguimiento de con el tiempo. Cada delimitador tiene un [del sistema de coordenadas](coordinate-systems.md) que ajusta según sea necesario, en relación con otros delimitadores o coloque marcos de referencia, con el fin de garantizar que permanezcan con precisión en hologramas anclados.  Representar un holograma en sistema de coordenadas de un delimitador le proporciona la posición más precisos para esa holograma en un momento dado. Esto incluye a costa de pequeños ajustes con el tiempo a la posición del holograma, como el sistema continuamente cambiará en su lugar en relación con el mundo real.

También puede conservar y compartir los anclajes espaciales entre sesiones de aplicación y en todos los dispositivos:
* Guardando delimitadores espaciales locales en el disco y carga de nuevo más tarde, la aplicación puede analizar la misma ubicación en el mundo real en varias sesiones de aplicación en un único dispositivo HoloLens.
* Mediante el uso de <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure espacial delimitadores</a> para crear un anclaje en la nube, la aplicación puede compartir un anclaje espacial entre varios HoloLens, dispositivos iOS y Android. Al tener cada dispositivo representar un holograma utilizando el mismo delimitador espacial, todos los usuarios verán el holograma aparecen en el mismo lugar en el mundo real.  Esto permite experiencias compartidas en tiempo real.
* También puede usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure espacial delimitadores</a> para la persistencia holograma asincrónica a través de dispositivos Android, iOS y HoloLens.  Al compartir un anclaje espacial en la nube duraderas, varios dispositivos pueden observar el mismo holograma persistente con el tiempo, incluso si esos dispositivos no están presentes entre sí al mismo tiempo.

Para experiencias de escala permanente o sala de escala para auriculares escritorio anclado a red que permanecerán dentro de un diámetro de 5 metros, generalmente sólo se pueden usar el [fase marco de referencia](coordinate-systems.md#stage-frame-of-reference) en lugar de los anclajes de espaciales, que proporciona un único sistema de coordenadas en el que se va a representar todo el contenido. Sin embargo, si la aplicación se va a permitir que los usuarios consultar más allá de 5 metros en HoloLens, quizás funcionando a lo largo de toda una planta de un edificio, necesitará espaciales delimitadores para mantener estable de contenido.

Mientras que los anclajes espaciales son excelentes para hologramas que deben permanecer fijos en el mundo, una vez que se coloca un delimitador, no se puede mover. Existen alternativas a los delimitadores que son más apropiadas para hologramas dinámicos que se deben etiquetar junto con el usuario. Es mejor colocar hologramas dinámicas mediante un marco estático de referencia (la base de las coordenadas del mundo de Unity) o un marco de referencia adjunta.

## <a name="best-practices"></a>Procedimiento recomendado

Estas directrices de anclaje espacial le ayudarán a representar hologramas estables que realizar un seguimiento preciso del mundo real.

### <a name="create-spatial-anchors-where-users-place-them"></a>Crear delimitadores espaciales donde los usuarios colocarlos

La mayoría de los casos, los usuarios deben ser las explícitamente colocar delimitadores espaciales.

Por ejemplo, en HoloLens, una aplicación puede forman una intersección con el usuario [que mirar](gaze.md) de trazado de rayos con el [asignación espacial](spatial-mapping.md) malla para permitir al usuario decidir dónde colocar un holograma. Cuando el usuario puntea para colocar ese holograma, cree un anclaje espacial en el punto de intersección y, a continuación, coloque el holograma en el origen del sistema de coordenadas del anclaje.

Delimitadores espaciales locales son fáciles y eficaces para crear y el sistema consolidarán sus datos internos si varios delimitadores pueden compartir sus datos de sensor subyacente. Normalmente, debe crear un nuevo anclaje de espacial local para cada holograma que un usuario coloca explícitamente, excepto en los casos descritos a continuación, como grupos rígidos de hologramas.

### <a name="always-render-anchored-holograms-within-3-meters-of-their-anchor"></a>Procesar siempre hologramas delimitados dentro de 3 metros de su delimitador

Delimitadores espaciales estabilización su sistema de coordenadas cerca de origen del anclaje. Si representa más de 3 metros desde ese origen hologramas, esos hologramas pueden experimentar errores de posicionales apreciables en proporción a su distancia desde ese origen debido a efectos de la palanca arm. Esto funciona si el usuario es el acrónimo casi el delimitador, puesto que el holograma está lejos del usuario, lo que significa que el error de la holograma distante angular será pequeño. Sin embargo, si el usuario dirige a esa holograma distante, a continuación, será grande en su visión, hacer que los efectos de la palanca arm desde el origen de anclaje lejana bastante obvio.

### <a name="group-holograms-that-should-form-a-rigid-cluster"></a>Hologramas de grupo que deben formar un clúster rígido

Hologramas varios pueden compartir el mismo delimitador espacial si la aplicación espera que esas hologramas mantener relaciones fijas entre sí.

Por ejemplo, si está animando un sistema solar holográfico en una sala, es mejor asociar todos los objetos del sistema solar a un único delimitador en el centro, por lo que se muevan sin problemas entre sí. En este caso, es el sistema solar como un todo que está anclado, aunque sus partes componentes son mover dinámicamente en el delimitador.

La clave observación para mantener la estabilidad holograma es seguir la regla de 3 metros de longitud anterior.

### <a name="render-highly-dynamic-holograms-using-the-stationary-frame-of-reference-instead-of-a-local-spatial-anchor"></a>Representar hologramas altamente dinámicos mediante el marco estático de referencia en lugar de un anclaje espacial local

Si tiene un holograma altamente dinámico, como un carácter de caminar alrededor de la sala o una interfaz de usuario flotante que sigue a lo largo de la pared cerca del usuario, es mejor omitir delimitadores espaciales locales y procesar esos hologramas directamente en el sistema de coordenadas proporcionado por el [</C0>marcoestáticodereferencia<spanclass="notranslate">](coordinate-systems.md#stationary-frame-of-reference) (es decir, en Unity, lograr esto colocando hologramas directamente en coordenadas universales sin un WorldAnchor).</span> Hologramas en un marco estático de referencia pueden experimentar desfase cuando el usuario está lejos de ser el holograma, pero esto es menos probable que sean evidentes para hologramas dinámicas: el holograma es mover constantemente de todos modos, o su movimiento mantiene constantemente cerca del usuario , donde se minimizará el desfase.

Un caso interesante de hologramas dinámicos es un objeto que se anima desde un sistema de coordenadas anclado a otro. Por ejemplo, podría tener dos castillos 10 metros, y cada uno en su propio delimitador espacial, con un castillo desencadenando una bala de cañón en el castillo otro. En este momento que se desencadena la bala de cañón, se puede representar en la ubicación adecuada en el marco estático de referencia, con el fin de coincidir con el cañón en sistema de coordenadas anclado del castillo primer. A continuación, puede seguir su trayectoria en el marco estático de referencia que desaparecerá 10 metros a través del aire. Como el bala de cañón alcanza lo otro castillo, decide mover en el castillo segundo anclado para permitir cálculos con cuerpos rígidos de que castle física del sistema de coordenadas.

Si va a compartir un holograma altamente dinámico en todos los dispositivos, deberá elegir algún delimitador espacial de la nube para que actúe como su elemento primario, como estático marcos de referencia no se pueden compartir entre dispositivos.  Sin embargo, en este caso, debe asegurarse de que ya sea el holograma dinámico o los dispositivos de visualización permanecen dentro de radius de 3 metros del anclaje, para garantizar que el holograma aparece estable en todos los dispositivos.

### <a name="avoid-creating-a-grid-of-spatial-anchors"></a>Evitar la creación de una cuadrícula de delimitadores espaciales

Es posible que vea tentado a que la aplicación se coloque una cuadrícula normal de delimitadores espaciales cuando el usuario, realizar la transición objetos dinámicos de anclaje anclaje a medida que se mueven. Sin embargo, esto implica una gran cantidad de administración para su aplicación, sin la ventaja de los datos del sensor profundo que el propio sistema mantiene internamente. En estos casos, normalmente obtendrá mejores resultados con menos esfuerzo colocando sus hologramas en el marco estático de referencia, como se describe en la sección anterior.

Al colocar previamente un conjunto de delimitadores espacial de la nube en torno a un espacio estático, considere la posibilidad de colocar los delimitadores espaciales en las ubicaciones de la claves hologramas se encontrará con el usuario por el principio anterior, en lugar de crear una cuadrícula de delimitadores arbitraria.  Esto garantiza que obtendrá máxima estabilidad para esos hologramas claves.

### <a name="release-local-spatial-anchors-you-no-longer-need"></a>Versión locales delimitadores espaciales que ya no necesita

Mientras un anclaje espacial local está activo, el sistema dará prioridad a mantener en torno a los datos de sensor que está a punto de anclaje. Si ya no usa un delimitador espacial, stop, obtener acceso a su sistema de coordenadas. Esto permitirá que los datos de sensor subyacentes va a quitar según sea necesario.

Esto es especialmente importante para delimitadores locales que se haya guardado en el almacén de anclaje espacial. Los datos del sensor detrás de estos delimitadores se mantienen en torno a permanentemente para permitir que la aplicación buscar en futuras sesiones de aplicación, lo que reducirán el espacio disponible para realizar el seguimiento de otros delimitadores de anclaje. Conservar solo los delimitadores locales que deba buscar de nuevo en futuras sesiones y quitarlos de la tienda cuando ya no son significativos para el usuario.

Para delimitadores espacial de la nube, puede escalar el almacenamiento según su escenario requiere.  Puede almacenar tantos delimitadores de la nube según sea necesario y liberarlas solo cuando sepa que los usuarios no necesitarán buscar hologramas en dicho delimitador nuevo.

## <a name="see-also"></a>Vea también
* [Sistemas de coordenadas](coordinate-systems.md)
* [Experiencias compartidas en realidad mixta](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [Persistencia en Unity](persistence-in-unity.md)
* [Delimitadores espaciales en DirectX](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-spatial-anchors)
* [Caso práctico: examinar los huecos en la realidad](case-study-looking-through-holes-in-your-reality.md)
