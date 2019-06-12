---
title: Sistemas de coordenadas
description: Los sistemas de coordenadas espaciales utilizados para generar su asiento, permanente, sala de escalado y escalado del mundo mixto realidad experiencias.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: del sistema de coordenadas, del sistema de coordenadas espacial, sólo orientación, sentado a escala, escala permanente, sala de escala, escala mundial, colocada de 360 grados, permanente, sala, mundo, escala, posición, orientación, inmóvil, adjunta, fase, delimitador, delimitador espacial, bloqueado por el mundo, mundo de bloqueo, bloqueada por el cuerpo, cuerpo de bloqueo, los límites indicados, persistencia, compartir, seguimiento de la pérdida, en la nube delimitador espacial
ms.openlocfilehash: f4b945a3ffb83b9ac0a94e0d793a19939aece3bb
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829862"
---
# <a name="coordinate-systems"></a>Sistemas de coordenadas

En su núcleo, mixto en lugar de las aplicaciones de realidad [hologramas](hologram.md) en el mundo que buscar y parecer objetos reales. Esto implica colocar con precisión y orientar esos hologramas en lugares del mundo que son significativas para el usuario, si el mundo es su espacio físico o un dominio virtual que ha creado. Al establecer el razonamiento sobre la posición y orientación de las hologramas o cualquier otra geometría como los [que mirar](gaze.md) ray o [entregar posiciones](gestures.md), Windows proporciona diversos sistemas de coordenadas del mundo real en la que se puede expresar Geometry, conocido como **sistemas de coordenadas espaciales**.

<br>

>[!VIDEO https://www.youtube.com/embed/TneGSeqVAXQ]

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="40%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    </colgroup>
    <tr>
        <td><strong>Característica</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (gen 1)</strong></a></td>
        <td><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Inmersivos</strong></a></td>
    </tr>
     <tr>
        <td><a href="coordinate-systems.md#stationary-frame-of-reference">Marco estático de referencia</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="coordinate-systems.md#attached-frame-of-reference">Marco de referencia adjunta</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="coordinate-systems.md#stage-frame-of-reference">Fase de marco de referencia</a></td>
        <td>No se admite aún</td>
        <td>No se admite aún</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="coordinate-systems.md#spatial-anchors">Delimitadores espaciales</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="spatial-mapping.md">Asignación espacial</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="mixed-reality-experience-scales"></a>Escalas de experiencia de realidad mixta

Pueden diseñar aplicaciones de realidad mixta para una amplia gama de experiencias de usuario, desde los visores de vídeo de 360 grados que basta con la orientación de auriculares, para aplicaciones a escala mundial completa y juegos, que necesitan delimitadores espaciales y asignación espacial:
<br>

| Escala de la experiencia | Requisitos | Experiencia de ejemplo | 
|----------|----------|----------|
|  **Sólo orientación** |  **Orientación de auriculares** (gravedad alineado) |  Visor de 360° de vídeo | 
|  **Seated-scale** |  Anteriormente, plus **posición auriculares** en relación con la posición cero |  Simulador de juego o espacio de carreras | 
|  **Standing-scale** |  Anteriormente, plus **fase origen floor** |  Juego de acción donde agacha y dodge en su lugar  | 
|  **Room-scale** |  Anteriormente, plus **polygon de límites de fase** |  Rompecabezas juego donde andar el rompecabezas | 
|  **World-scale** |  **Delimitadores espaciales** (y normalmente [asignación espacial](spatial-mapping.md)) |  Juego con enemigos procedentes de las paredes real, como [RoboRaid](https://www.microsoft.com/p/roboraid/9nblggh5fv3j) | 

Estos experimentan siga escalas de un modelo de "anidar muñecas". El principio de diseño clave aquí para Windows Mixed Reality es que un auricular determinado es compatible con las aplicaciones compiladas para una escala de la experiencia de destino, así como todo menor escala:
<br>

| Seguimiento 6GDL | Floor definido | 360° de seguimiento | Límites definidos | Delimitadores espaciales | Experiencia de máxima | 
|----------|----------|----------|----------|----------|----------|
|  No |  - |  - |  - |  - |  **Sólo orientación** | 
|  **Sí** |  No |  - |  - |  - |  **Seated** | 
|  **Sí** |  **Sí** |  No |  - |  - |  **Permanente - hacia delante** | 
|  **Sí** |  **Sí** |  **Sí** |  No |  - |  **Permanente - 360°** | 
|  **Sí** |  **Sí** |  **Sí** |  **Sí** |  No |  **Room** | 
|  **Sí** |  **Sí** |  **Sí** |  **Sí** |  **Sí** |  **World** | 

Tenga en cuenta que el marco de referencia de la fase no es compatible aún con HoloLens. Necesita usar una aplicación de salón de escala en HoloLens [asignación espacial](spatial-mapping.md) encontrar floor y los planos laterales del usuario.

## <a name="spatial-coordinate-systems"></a>Sistemas de coordenadas espaciales

Usan todas las aplicaciones de gráficos 3D [sistemas de coordenadas cartesiano](https://docs.microsoft.com/windows/uwp/graphics-concepts/coordinate-systems) razonar sobre las posiciones y orientaciones de objetos en los mundos virtuales se representan. Estos sistemas de coordenadas establecer 3 ejes perpendiculares a lo largo del que se va a colocar los objetos: un eje X, Y y Z.

En [la realidad mixta](mixed-reality.md), las aplicaciones se razón sobre los sistemas de coordenadas virtuales y físicos. Windows llama a un sistema de coordenadas que tiene un significado real en el mundo físico un **del sistema de coordenadas espacial**.

Sistemas de coordenadas espaciales expresar sus valores de las coordenadas en metros. Esto significa que los objetos colocan 2 unidades separadas entre sí en la X, eje Y o Z aparecerá 2 metros aparte entre sí cuando se representa en realidad mixta. Esto le permite representar fácilmente objetos y los entornos a escala del mundo real.

En general, los sistemas de coordenadas cartesiano pueden ser diestro o zurdo. Sistemas de coordenadas espaciales en Windows siempre es diestros, lo que significa que el valor positivo eje x apunte a la derecha, el eje y positivo señala hacia arriba (alineados a la gravedad) y el valor positivo z apunta hacia TI.

En ambos tipos de sistemas de coordenadas, el valor positivo eje x apunta a la derecha y el eje y positivo señala hacia arriba. La diferencia es si el eje z positivo apunta hacia o lejos de usted. Puede recordar qué dirección del eje z positivo señala señalando los dedos de cualquiera de la izquierda o derecha en el valor positivo X cURL ellos a la dirección del eje Y positiva y la dirección. La dirección señala el pulgar, acerque o aleje, es la dirección a la que apunta el eje z positivo para ese sistema de coordenadas.

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>Creación de una experiencia sólo orientación o asentada de escala

La clave a holographic [representación](rendering.md) está cambiando la vista de la aplicación de sus hologramas cada marco cuando el usuario se mueve alrededor, para que coincida con su movimiento principal previsto. Puede compilar **escala asentada experiencias** que respeto los cambios en la posición del usuario principal y la orientación principal utilizando una **marco estático de referencia**.

Distancia desde el usuario en todo momento y algún contenido debe tener en cuenta las actualizaciones de posición principal, permanece fijo en un encabezado elegido. El ejemplo principal es vídeo de 360 grados: dado que el vídeo se captura desde una perspectiva fija única, sería dañen la ilusión de la posición de la vista mover en relación con el contenido, aunque debe cambiar la orientación de la vista como el usuario mira alrededor. Puede compilar como **sólo orientación experiencias** mediante un **adjunta el marco de referencia**.

### <a name="stationary-frame-of-reference"></a>Marco estático de referencia

El sistema de coordenadas proporcionado por un marco estático de referencia funciona para mantener las posiciones de los objetos de cerca el usuario lo más estable como sea posible en relación con el mundo, respetando los cambios en la posición del usuario principal.

Para experiencias de escala alojados en un motor de juego como [Unity](https://unity3d.com/), un marco estático de referencia es lo que define "mundo origin" del motor. Los objetos que se colocan en una coordenada del mundo específica usar el marco estático de referencia para definir su posición en el mundo real con las mismas coordenadas. Contenido que permanece colocado en el mundo, incluso cuando el usuario, se conoce como **bloqueado por el mundo** contenido.

Una aplicación normalmente se crea un marco estático de referencia en el inicio y usar su sistema de coordenadas durante el ciclo de vida de la aplicación. Como desarrollador de aplicaciones en Unity, simplemente puede empezar a colocar contenido en relación con el origen, lo que estará en posición principal inicial del usuario y la orientación. Si el usuario se mueve a un nuevo lugar y desea continuar su experiencia de escalado asentado, puede Centrar el origen del mundo en esa ubicación.

Con el tiempo, como el sistema aprende más sobre el entorno del usuario, puede determinar que las distancias entre distintos puntos en el mundo real es menor o mayor que el sistema considera anteriormente. Si representan hologramas en un marco estático de referencia para una aplicación en HoloLens donde los usuarios consultar más allá de un área amplia de aproximadamente 5 metros, la aplicación puede observar el desfase en la ubicación de esos hologramas observada. Si su experiencia tiene usuarios que se adentra más allá de 5 metros, está creando un [experiencia del mundo a escala](#building-a-world-scale-experience), lo que requerirá técnicas adicionales para mantener hologramas estable, tal como se describe a continuación.

### <a name="attached-frame-of-reference"></a>Marco de referencia adjunta

Un marco de referencia adjunta se mueve con el usuario que guían alrededor, con un encabezado fijo definido cuando la aplicación primero crea el marco. Esto permite al usuario consultar cómodamente en torno a contenido que se coloca dentro de ese marco de referencia. Se llama a contenido representado de este modo de usuario relacionados con **bloqueado por el organismo** contenido.

Cuando los auriculares no pueden averiguar dónde se encuentra en el mundo, un marco de referencia adjunta proporciona el único sistema de coordenadas que se puede usar para representar hologramas. Esto resulta ideal para mostrar la interfaz de usuario de reserva para indicar al usuario que su dispositivo no encuentra en el mundo. Las aplicaciones que están sentados a escala o superior deben incluir una reserva sólo orientación para ayudar al usuario comenzar de nuevo, con la interfaz de usuario similar a la que se muestra en el [Mixed Reality doméstica](navigating-the-windows-mixed-reality-home.md).

## <a name="building-a-standing-scale-or-room-scale-experience"></a>Creación de una experiencia de escala permanente o sala de escala

Para ir más allá de la escala alojados en un auricular envolvente y generar un **permanente escala experiencia**, puede usar el **fase marco de referencia**.

Para proporcionar un **experiencia sala escala**, permitiéndole andar con los usuarios dentro del límite de 5 metros se ha definido previamente, puede comprobar para **fase límites** también.

### <a name="stage-frame-of-reference"></a>Fase de marco de referencia

Al configurar primero un auricular envolvente, el usuario define un **fase**, que representa el espacio en el que experimentarán la realidad mixta. La fase se define como mínimo un **fase origen**, un sistema de coordenadas espacial centrado en el usuario del elegido posición piso y orientación hacia delante que va a utilizar el dispositivo. Al colocar contenido en este sistema de coordenadas de la fase en el plano de piso Y = 0, puede garantizar sus hologramas cómodamente aparecen en el suelo cuando el usuario es permanente, ofreciendo a los usuarios con un **permanente escala experiencia**.

### <a name="stage-bounds"></a>Límites de fase

Opcionalmente, también puede definir el usuario **fase límites**, un área dentro de la sala que ha borrado de muebles de donde va a mover en la realidad mixta. Si es así, puede compilar la aplicación un **experiencia sala escala**, utilizando estos límites para asegurarse de que siempre se colocan hologramas, donde el usuario puede comunicarse con ellos.

Dado que el marco de referencia de la fase proporciona que un único se ha corregido el sistema de coordenadas en que se va a colocar el contenido de piso relativo, es la ruta de acceso más fácil para portabilidad permanente de escala y las aplicaciones de escala de la sala desarrolladas para auriculares de realidad virtual. Sin embargo, como con esas plataformas VR, un único sistema de coordenadas sólo puede estabilizar el contenido en sobre un diámetro de 5 metros (16 pies), antes de la palanca arm efectos producir contenido lejos el centro se desplacen considerablemente según el ajusta el sistema. Para ir más allá de 5 metros, se necesitan delimitadores espaciales.

## <a name="building-a-world-scale-experience"></a>Creación de una experiencia del mundo a escala

HoloLens permite true **experiencias del mundo a escala** que permiten a los usuarios consultar más allá de 5 metros. Para compilar una aplicación de escala mundial, necesitará nuevas técnicas más allá de los que se usan para experiencias de escala de la sala.

### <a name="why-a-single-rigid-coordinate-system-cannot-be-used-beyond-5-meters"></a>¿Por qué no se puede usar un único sistema de coordenadas rígido más allá de 5 metros

Hoy en día, al escribir juegos, aplicaciones de visualización de datos o las aplicaciones de realidad virtual, el enfoque típico es establecer un sistema de coordenadas universales absolutas que todas las otras coordenadas confiable pueden asignar al. En ese entorno, siempre puede encontrar una transformación estable que define una relación entre los dos objetos en ese mundo. Si no mueve esos objetos, sus transformaciones relativas siempre permanecen igual. Este tipo de global sistema de coordenadas funciona bien al representar un mundo virtual puramente donde sabe todo de la geometría de antemano. Hoy en día aplicaciones a escala sala VR establecen este tipo de sistema de coordenadas de la sala de escala absoluta con su origen en el suelo.

En cambio, un dispositivo sin restricción de realidad mixta, como HoloLens tiene un conocimiento controlado por el sensor dinámico del mundo, ajuste continuamente sus conocimientos con el tiempo de entorno del usuario que guían a través de toda una planta de un edificio muchas medidas. En una experiencia del mundo a escala, si ha colocado todas sus hologramas en un único sistema de coordenadas rígido, esos hologramas necesariamente se desvíen con el tiempo, en relación con el mundo o entre sí.

Por ejemplo, los auriculares pueden creer actualmente dos ubicaciones del mundo para ser 4 metros de distancia y después refinar más tarde ese conocimiento, que las ubicaciones son en realidad 3.9 metros de distancia de aprendizaje. Si esos hologramas inicialmente se ha establecido los medidores 4 aparte en un único sistema de coordenadas rígido, uno de ellos siempre aparecerán 0,1 metros procedentes del mundo real.

### <a name="spatial-anchors"></a>Delimitadores espaciales

Windows Mixed Reality soluciona el problema descrito en la sección anterior, por lo que le permite crear [delimitadores espaciales](spatial-anchors.md) para marcar puntos importantes del mundo donde el usuario ha colocado hologramas. Un anclaje espacial representa un punto importante en el mundo que el sistema debe realizar un seguimiento de con el tiempo.

Como el dispositivo, aprende sobre el mundo, estos delimitadores espaciales pueden ajustar su posición relativa entre sí, según sea necesario para garantizar que cada delimitador permanece exactamente donde se colocó en relación con el mundo real. Si coloca un anclaje espacial en la ubicación donde el usuario coloca un holograma y, a continuación, colocar ese holograma en relación con su delimitador espacial, puede asegurarse de que el holograma mantiene la estabilidad óptima, incluso cuando el usuario se desplaza entre decenas de metros.

Este ajuste continuo de delimitadores espaciales relativos a otro es la diferencia principal entre coordinate systems desde delimitadores espaciales y estático marcos de referencia:

* Hologramas colocados en el marco estático de referencia todas mantienen una relación rígida entre sí. Sin embargo, cuando el usuario grandes distancias, podría desviarse del sistema de coordenadas del marco en relación con el mundo para asegurarse de que aparezcan estables hologramas junto al usuario.

* Hologramas colocados en el marco de referencia de la fase también mantienen una relación rígida entre sí. A diferencia del marco inmóvil, el marco de la fase siempre permanece fijo en su lugar con respecto a su origen físico definido. Sin embargo, contenido representado en el sistema de coordenadas de la fase más allá de su límite de 5 metros sólo aparecerá estable mientras el usuario es permanente dentro de ese límite.

* Hologramas colocados usando uno podría desviarse del anclaje espacial en relación con hologramas colocan usando otro delimitador espacial. Esto permite que Windows mejorar su comprensión de la posición de cada delimitador espacial, incluso si, por ejemplo, un delimitador debe ajustarse a sí mismo deja y otro delimitador debe ajustar a la derecha.

A diferencia de un marco estático de referencia, que siempre se optimiza para mejorar la estabilidad cerca del usuario, el marco de referencia de fase y delimitadores espaciales garantizan la estabilidad cerca de sus orígenes. Esto ayuda a esos hologramas permanece exactamente con el tiempo, pero también significa que hologramas representados demasiado lejos de origen de su sistema de coordenadas experimentará los efectos de arm de maneta cada vez más graves. Esto es porque se amplía pequeños ajustes en la posición y la orientación de la fase o delimitador proporcional a la distancia de anclaje. 

Una buena regla general es para asegurarse de que nada que representan en función de sistema de coordenadas de un anclaje espacial distantes está dentro de unos 3 metros de origen. Un origen de fase cercanos, representar el contenido distantes está bien, ya cualquier error posicional mayor afectará únicamente pequeñas hologramas que desplazarán mucho en la vista del usuario.

### <a name="spatial-anchor-persistence"></a>Persistencia de anclaje espacial

Delimitadores espaciales también pueden permitir que su aplicación recordar una ubicación importante incluso después de la aplicación se suspende o se apaga el dispositivo.

Puede guardar los anclajes espaciales de la aplicación crea el disco y, a continuación, cargarlos vuelva a intentarlo más tarde, conservando a su aplicación **espacial tienda Premium**. Al guardar o cargar un delimitador, proporcione una clave de cadena que sea significativa para la aplicación, con el fin de identificar el delimitador más adelante. Considere esta clave como el nombre de archivo para el delimitador. Si desea asociar otros datos a dicho delimitador, como un modelo 3D que el usuario se coloca en esa ubicación, guárdela en el almacenamiento local de la aplicación y su asociación con la clave que eligió.

Por conservar delimitadores en el almacén, los usuarios pueden colocar hologramas individuales o coloque un área de trabajo alrededor de los cuales colocar sus diversos hologramas una aplicación y, a continuación, buscar esos hologramas más tarde que esperan, a través de muchos usos de la aplicación.

También puede usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure espacial delimitadores</a> para la persistencia holograma asincrónica a través de dispositivos Android, iOS y HoloLens.  Al compartir un anclaje espacial en la nube duraderas, varios dispositivos pueden observar el mismo holograma persistente con el tiempo, incluso si esos dispositivos no están presentes entre sí al mismo tiempo.

### <a name="spatial-anchor-sharing"></a>Uso compartido de anclaje espacial

La aplicación también puede compartir un anclaje espacial en tiempo real con otros dispositivos, lo que permite en tiempo real comparte experiencias.

Mediante el uso de <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure espacial delimitadores</a>, la aplicación puede compartir un anclaje espacial entre varios HoloLens, dispositivos iOS y Android. Al tener cada dispositivo representar un holograma utilizando el mismo delimitador espacial, todos los usuarios verán el holograma aparecen en el mismo lugar en el mundo real.

## <a name="avoid-head-locked-content"></a>Evitar contenido bloqueado head

Se desaconseja encarecidamente representar contenido bloqueado head, que permanece en un punto fijo en la pantalla (por ejemplo, un HUD). En general, contenido bloqueado head resulta cómodo para los usuarios y no perciben como una parte natural de su mundo.

Contenido bloqueado HEAD normalmente se debe reemplazar con hologramas que se adjuntan al usuario o se colocan en el mundo propio. Por ejemplo, [cursores](cursors.md) deben generalmente enviarse en el mundo, escalar de forma natural para reflejar la posición y la distancia del objeto bajo la mirada del usuario.

## <a name="handling-tracking-errors"></a>Seguimiento de control de errores

En algunos entornos, como los vestíbulos oscuros, puede no ser posible para un auricular con seguimiento por completo para encontrar la propia correctamente en el mundo. Esto puede provocar hologramas no aparecen o aparecen en posiciones incorrectas si se controlan correctamente. Ahora analizaremos las condiciones en que esto puede suceder, su impacto en la experiencia del usuario, y sugerencias para ofrecer la mejor controlan esta situación.

### <a name="headset-cannot-track-due-to-insufficient-sensor-data"></a>No se pueden realizar un seguimiento de los auriculares debido a los datos del sensor insuficiente

A veces, no están posible averiguar dónde está el auricular sensores de auriculares. Esto puede ocurrir si la sala es oscura, si los sensores están cubiertos por pelo o manos o si el entorno no tiene suficiente textura.

Cuando esto sucede, los auriculares no se pueden realizar un seguimiento de su posición con suficiente precisión para representar hologramas bloqueado por el mundo. No podrá averiguar donde es un delimitador espacial, marco parado o fase en relación con el dispositivo, pero todavía puede presentar contenido bloqueado de cuerpo en el marco de referencia adjunta.

La aplicación debe indicar al usuario cómo obtener la posición de seguimiento, representación algún contenido bloqueado por el cuerpo de la reserva que se describe algunas sugerencias, como descubrir los sensores y encender las luces más.

### <a name="headset-tracks-incorrectly-due-to-dynamic-changes-in-the-environment"></a>Realiza un seguimiento de auriculares incorrectamente debido a que los cambios dinámicos en el entorno

A veces, el dispositivo no se puede realizar un seguimiento correctamente si hay una gran cantidad de cambios dinámicos en el entorno, por ejemplo, muchas personas deambulan en la sala. En este caso, pueden parecer la hologramas saltar o variar según el dispositivo intenta realizar un seguimiento de sí mismo en este entorno dinámico. Se recomienda usar el dispositivo en un entorno dinámico menos si se produce esta situación.

### <a name="headset-tracks-incorrectly-because-the-environment-has-changed-significantly-over-time"></a>Auriculares realiza un seguimiento incorrectamente porque el entorno ha cambiado significativamente con el tiempo

A veces, al empezar a usar auriculares en un entorno que ha experimentado muchos cambios (por ejemplo, movimiento importante muebles, para la pared etc.), es posible que algunos hologramas pueden aparecer desplazadas desde sus ubicaciones originales. La anteriores hologramas también pueden ir directamente en torno a cuando el usuario se mueve de este nuevo espacio. Esto es porque ya no contiene la descripción del sistema de su espacio y se intentará volver a asignar el entorno mientras intenta conciliar las características de la sala. En este escenario, se recomienda para animar a los usuarios a volver a colocar hologramas fija en el mundo si no aparecen cuando se esperaba.

### <a name="headset-tracks-incorrectly-due-to-identical-spaces-in-an-environment"></a>Realiza un seguimiento de auriculares incorrectamente debido a que los espacios idéntico en un entorno

A veces, una casa o en otro espacio puede tener dos áreas idénticas. Por ejemplo, dos salas de conferencias idénticos, dos idénticos esquina áreas, dos pósteres idénticos grandes que abarcan campo de la vista del dispositivo en el. En estos escenarios, el dispositivo puede, en ocasiones, confundirse entre las partes idénticas y marcarlos como el mismo en su representación interna. Esto puede provocar la hologramas de algunas áreas que aparezcan en otras ubicaciones. El dispositivo puede empezar a perder el seguimiento a menudo porque está dañado su representación interna del entorno. En este caso, se aconseja para restablecer la comprensión del entorno del sistema. Tenga en cuenta que al restablecer el mapa conlleva una pérdida de todas las ubicaciones de anclaje espacial. Esto hará que los auriculares realizar un seguimiento bien en las áreas del entorno únicas. Sin embargo, el problema vuelve a puede producirse si el dispositivo obtiene confundirse entre las áreas idénticas de nuevo.

## <a name="see-also"></a>Vea también
* [Presentación de 2017 GDC en sistemas de coordenadas espaciales y representación holográfica](https://channel9.msdn.com/events/GDC/GDC-2017/GDC2017-008)
* [Sistemas de coordenadas de Unity](coordinate-systems-in-unity.md)
* [Sistemas de coordenadas de DirectX](coordinate-systems-in-directx.md)
* [Delimitadores espaciales](spatial-anchors.md)
* [Experiencias compartidas en realidad mixta](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [Caso práctico: examinar los huecos en la realidad](case-study-looking-through-holes-in-your-reality.md)
