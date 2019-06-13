---
title: Delimitadores espaciales
description: Procedimientos recomendados de uso de delimitadores espaciales para representar hologramas estables.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: coordinate system, spatial coordinate system, world-scale, world, scale, position, orientation, anchor, spatial anchor, world-locked, world-locking, persistence, sharing
ms.openlocfilehash: 16165194d040ad22f7885897eddcc65cf9dcaec3
ms.sourcegitcommit: f20beea6a539d04e1d1fc98116f7601137eebebe
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "65730859"
---
# <a name="spatial-anchors"></a>Delimitadores espaciales

Un delimitador espacial representa un punto importante en el mundo del cual el sistema debe realizar un seguimiento a lo largo del tiempo. Cada delimitador tiene un [sistema de coordenadas](coordinate-systems.md) que se ajusta según sea necesario en función de otros delimitadores o marcos de referencia para garantizar que los hologramas delimitados permanecen exactamente en su sitio.  Representar un holograma en un sistema de coordenadas de un delimitador proporciona la posición más precisa de ese holograma en cualquier momento. Esto supone tener que realizar pequeños ajustes con el tiempo en la posición del holograma, ya que el sistema lo devuelve continuamente a su posición con relación al mundo real.

También permite conservar y compartir los delimitadores espaciales en sesiones de aplicación y en todos los dispositivos:
* Al guardar los delimitadores espaciales locales en el disco y volverlos a cargar más tarde, la aplicación puede detectar la misma ubicación en el mundo real en varias sesiones de aplicación en un único dispositivo HoloLens.
* Mediante el uso de <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> para crear un delimitador en la nube, la aplicación puede compartir un delimitador espacial entre varios dispositivos HoloLens, iOS y Android. Con la representación de un holograma mediante el mismo delimitador espacial en cada dispositivo, los usuarios verán el holograma aparecer en el mismo lugar en el mundo real.  Esto permite compartir experiencias en tiempo real.
* También se puede usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> para la persistencia de hologramas asincrónicos en dispositivos Android, iOS y HoloLens.  Al compartir un delimitador espacial en la nube duradera, varios dispositivos pueden observar el mismo holograma persistente a lo largo del tiempo, aunque los dispositivos no estén presentes juntos simultáneamente.

Cuando se permanezca de pie o en una sala con auriculares de escritorio conectados que vayan a permanecer en un diámetro de 5 metros, generalmente basta con usar el [marco del escenario de referencia](coordinate-systems.md#stage-frame-of-reference) en lugar de delimitadores espaciales, siempre que proporcione un sistema de coordenadas donde representar el contenido. Sin embargo, si la aplicación va a permitir que los usuarios se alejen más de 5 metros de HoloLens, como en toda una planta de un edificio, necesitará delimitadores espaciales para mantener el contenido estable.

Aunque los delimitadores espaciales son estupendos para los hologramas que deben permanecer fijos en el mundo, una vez colocados, no se pueden mover. Para los hologramas dinámicos que deben etiquetarse junto con el usuario existen otras alternativas adecuadas. Es mejor colocar hologramas dinámicos mediante un marco estático de referencia (la base de las coordenadas del mundo de Unity) o un marco de referencia adjunto.

## <a name="best-practices"></a>Procedimiento recomendado

Estas directrices de delimitación espacial te ayudarán a representar hologramas estables que realizan un seguimiento preciso del mundo real.

### <a name="create-spatial-anchors-where-users-place-them"></a>Crear delimitadores espaciales donde los usuarios los colocan

En la mayoría de los casos, los usuarios deben ser los que coloquen los delimitadores espaciales explícitamente.

Por ejemplo, en HoloLens, una aplicación forma una intersección con la [mirada](gaze.md) del usuario con la malla de [asignación espacial](spatial-mapping.md) para que este pueda decidir dónde colocar un holograma. Cuando el usuario puntea para colocar ese holograma, debes crear un delimitador espacial en la intersección y colocar el holograma en el origen del sistema de coordenadas del delimitador.

Los delimitadores espaciales locales se crean de manera sencilla y eficaz, y el sistema consolidará sus datos internos en caso de que varios delimitadores compartan datos de sensor subyacentes. En general debes crear un delimitador espacial local para cada holograma que un usuario coloque explícitamente, excepto en los casos descritos a continuación, como los grupos rígidos de hologramas.

### <a name="always-render-anchored-holograms-within-3-meters-of-their-anchor"></a>Procesar siempre hologramas delimitados en un radio de 3 metros a partir del delimitador

Los delimitadores espaciales estabilizan su sistema de coordenadas cerca del origen del delimitador. Si representas hologramas a más de 3 metros del origen, pueden experimentar errores de posición apreciables en proporción a su distancia desde el origen debido al efecto palanca. Esto funciona si el usuario permanece cerca del delimitador, ya que el holograma está también lejos del usuario, lo que significa que el error angular del holograma será reducido. Sin embargo, si el usuario se acerca al holograma, se agrandará a la vista y el efecto palanca del origen lejano del delimitador será bastante evidente.

### <a name="group-holograms-that-should-form-a-rigid-cluster"></a>Agrupar los hologramas que deban formar un clúster rígido

Varios hologramas pueden compartir el mismo delimitador espacial si la aplicación espera que conserven una relación fija entre ellos.

Por ejemplo, si vas a animar un sistema solar holográfico en una sala, es mejor unir todos los objetos de este en un delimitador en el centro de manera que se muevan despacio en relación los unos con los otros. En este caso, el sistema solar es como un todo delimitado, aunque sus componentes se muevan dinámicamente alrededor del delimitador.

El elemento clave para mantener la estabilidad del holograma es seguir la anterior regla de los 3 metros.

### <a name="render-highly-dynamic-holograms-using-the-stationary-frame-of-reference-instead-of-a-local-spatial-anchor"></a>Representar hologramas muy dinámicos mediante el marco estático de referencia en lugar de usar un delimitador espacial local

Si tienes un holograma muy dinámico, como un personaje que pasea por la sala o una IU flotante que sigue al usuario por la pared, lo mejor es pasar de los delimitadores espaciales locales y representar los hologramas directamente en el sistema de coordenadas del [marco estático de referencia](coordinate-systems.md#stationary-frame-of-reference) (por ejemplo, en Unity, esto se consigue al colocar los hologramas directamente en coordenadas reales sin WorldAnchor). Los hologramas en un marco estático de referencia pueden experimentar desfase cuando el usuario está lejos estos, pero se notará menos con los dinámicos: o bien, el holograma se mueve constantemente de todas formas, o bien, su movimiento lo mantiene cerca del usuario y el desfase es mínimo.

Un caso interesante de hologramas dinámicos es un objeto animado desde un sistema de coordenadas delimitado a otro. Por ejemplo, podrías tener dos castillos a una distancia de 10 metros entre sí, cada uno con su propio delimitador espacial, y que uno le disparara un cañonazo al otro. Al disparar el cañón, puedes representarlo en la ubicación correcta en el marco estático de referencia de manera que coincida con el cañón del sistema de coordenadas delimitado del primer castillo. Después, seguirá su trayectoria de 10 metros por el aire en el marco estático de referencia. Cuando la bala alcance el otro castillo, puedes elegir moverla al sistema de coordenadas delimitado del segundo castillo para permitir cálculos físicos con los cuerpos rígidos de allí.

Si vas a compartir un holograma muy dinámico entre dispositivos, deberás elegir algún delimitador espacial de la nube para que actúe como elemento primario, ya que los marcos estáticos de referencia no se pueden compartir entre dispositivos.  Sin embargo, en este caso,para garantizar que el holograma aparece estable en todos los dispositivos, debes asegurarte de que el holograma dinámico o los dispositivos que lo vean permanecen en el radio de 3 metros del delimitador.

### <a name="avoid-creating-a-grid-of-spatial-anchors"></a>Evitar la creación de una cuadrícula de delimitadores espaciales

Quizá te gustaría que la aplicación desplegara una cuadrícula normal de delimitadores espaciales según el usuario deambula para mover los objetos dinámicos de un delimitador a otro a su paso. Sin embargo, esto implica un gran trabajo de administración para la aplicación y se perdería la ventaja de los datos de sensor detallados que el sistema mantiene internamente. En estos casos se suelen obtener mejores resultados con menor esfuerzo si se colocan los hologramas en el marco estático de referencia, tal y como se describe en la sección anterior.

Al colocar previamente un conjunto de delimitadores espaciales de la nube en torno a un espacio estático, debes considerar la posibilidad de colocarlos en las posiciones de los hologramas clave que el usuario se encontrará según el principio anterior, en lugar de crear una cuadrícula de delimitadores arbitraria.  Esto garantiza la máxima estabilidad de esos hologramas clave.

### <a name="release-local-spatial-anchors-you-no-longer-need"></a>Liberar los delimitadores espaciales locales que ya no se necesitan

Mientras un delimitador espacial local esté activo, el sistema dará prioridad a mantener los datos de sensor circundantes. Si ya no usas un delimitador espacial, deja de acceder a su sistema de coordenadas para que los datos de sensor subyacentes se eliminen según proceda.

Esto es especialmente importante para los delimitadores locales que hayas guardado en el almacén de delimitadores espaciales. Los datos de sensor en los que se basan estos delimitadores se mantendrán permanentemente para que la aplicación encuentre el delimitador en futuras sesiones de la aplicación y así reducir el espacio necesario para el seguimiento de otros delimitadores. Conserva solo los delimitadores locales que necesites encontrar en futuras sesiones y elimínalos del almacén cuando ya no tengan sentido para el usuario.

Para los delimitadores espaciales en la nube, el almacenamiento puede escalar según las necesidades del escenario.  Puedes almacenar tantos delimitadores en la nube como necesites y eliminarlos solo cuando sepas que los usuarios ya no los necesitarán para ubicar hologramas en ese delimitador.

## <a name="see-also"></a>Consulte también
* [Sistemas de coordenadas](coordinate-systems.md)
* [Experiencias compartidas en realidad mixta](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [Persistencia en Unity](persistence-in-unity.md)
* [Delimitadores espaciales en DirectX](coordinate-systems-in-directx.md#place-holograms-in-the-world-using-spatial-anchors)
* [Case study - Looking through holes in your reality](case-study-looking-through-holes-in-your-reality.md) (Caso práctico: mirar por un agujero en tu realidad)
