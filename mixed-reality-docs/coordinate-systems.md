---
title: Sistemas de coordenadas
description: Los sistemas de coordenadas espaciales que se usan para compilar experiencias de realidad mixta colocada, permanente, de escala de sala y de gran escala.
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: sistema de coordenadas, sistema de coordenadas espaciales, solo orientación, escalado colocado, escalado permanente, escalado de habitación, escala mundial, grado de 360, colocado, permanente, de habitación, mundo, escala, posición, orientación, estacionaria, conectado, fase, delimitador, delimitador espacial, bloque mundial, bloqueo mundial, bloqueo de cuerpo, bloqueo de cuerpo, límites, persistencia, uso compartido, pérdida de seguimiento, delimitador espacial en la nube
ms.openlocfilehash: 228f46f1962c39012571234da47ccec07aa67118
ms.sourcegitcommit: 0a1af2224c9cbb34591b6cb01159b60b37dfff0c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2020
ms.locfileid: "79375642"
---
# <a name="coordinate-systems"></a>Sistemas de coordenadas

En su núcleo, las aplicaciones de realidad mixta colocan [hologramas](hologram.md) en su mundo que buscan y suenan como objetos reales. Esto implica el posicionamiento y la orientación precisos de esos hologramas en lugares del mundo que son significativos para el usuario, tanto si el mundo es su habitación física como si es un dominio virtual que ha creado. Cuando se trata sobre la posición y la orientación de los hologramas, o de cualquier otra geometría como [el rayo o](gaze-and-commit.md) las [posiciones de mano](hands-and-tools.md), Windows proporciona varios sistemas de coordenadas del mundo real en los que se puede expresar la geometría, conocido como **sistemas de coordenadas espaciales**.

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/TneGSeqVAXQ" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="40%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    </colgroup>
    <tr>
        <td><strong>Ofrecen</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens (1.ª generación)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td><a href="coordinate-systems.md#stationary-frame-of-reference">Marco estacionario de referencia</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="coordinate-systems.md#attached-frame-of-reference">Marco de referencia asociado</a></td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="coordinate-systems.md#stage-frame-of-reference">Marco de la fase de referencia</a></td>
        <td>Todavía no se admite</td>
        <td>Todavía no se admite</td>
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
    <tr>
        <td><a href="scene-understanding.md">Descripción de escenas</a></td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="mixed-reality-experience-scales"></a>Escalas de experiencia de realidad mixta

Las aplicaciones de realidad mixta pueden diseñar una amplia gama de experiencias de usuario, desde visores de vídeo de 360 grados que solo necesitan la orientación del casco, hasta aplicaciones y juegos de escala mundial completos, que necesitan asignación espacial y anclaje espacial:
<br>

| Escala de experiencia | Requisitos | Experiencia de ejemplo | 
|----------|----------|----------|
|  **Solo orientación** |  **Orientación de auriculares** (con alineación de gravedad) |  visor de vídeo de 360 ° | 
|  **Escalado colocado** |  Por encima, más la **posición del casco** en relación con la posición cero |  Juego de carreras o simulador de espacio | 
|  **Escalado permanente** |  Por encima, más el **origen del piso de fase** |  Juego de acciones en el que se coloca el pato y se sobreexpone  | 
|  **Escala de sala** |  Anterior, más los **límites de fase de polígono** |  Juego puzzle donde se recorre el rompecabezas | 
|  **Escala mundial** |  **Delimitadores espaciales** (y normalmente [asignación espacial](spatial-mapping.md)) |  Juego con enemigos procedentes de sus paredes reales, como [RoboRaid](https://www.microsoft.com/p/roboraid/9nblggh5fv3j) | 

Estas escalas de experiencia siguen un modelo de "muñecas de anidamiento". El principio de diseño clave aquí para Windows Mixed Reality es que un casco determinado admite aplicaciones creadas para una escala de experiencia de destino, así como todas las escalas inferiores:
<br>

| seguimiento de 6DOF | Piso definido | seguimiento de 360 ° | Límites definidos | Delimitadores espaciales | Experiencia máxima | 
|----------|----------|----------|----------|----------|----------|
|  No |  - |  - |  - |  - |  **Solo orientación** | 
|  **Sí** |  No |  - |  - |  - |  **Sentada** | 
|  **Sí** |  **Sí** |  No |  - |  - |  **Hacia delante** | 
|  **Sí** |  **Sí** |  **Sí** |  No |  - |  **Permanente: 360 °** | 
|  **Sí** |  **Sí** |  **Sí** |  **Sí** |  No |  **Misma** | 
|  **Sí** |  **Sí** |  **Sí** |  **Sí** |  **Sí** |  **WWPN** | 

Tenga en cuenta que el marco de fase de referencia todavía no se admite en HoloLens. Actualmente, una aplicación de escala de habitación de HoloLens debe usar la [asignación espacial](spatial-mapping.md) o la [comprensión de escenas](scene-understanding.md) para buscar el piso y las paredes del usuario.

## <a name="spatial-coordinate-systems"></a>Sistemas de coordenadas espaciales

Todas las aplicaciones de gráficos 3D usan [sistemas de coordenadas cartesianos](https://docs.microsoft.com/windows/uwp/graphics-concepts/coordinate-systems) para motivar las posiciones y las orientaciones de los objetos en los mundos virtuales que representan. Estos sistemas de coordenadas establecen tres ejes perpendiculares para colocar los objetos: un eje X, Y y Z.

En [realidad](mixed-reality.md), las aplicaciones tendrán en común los sistemas de coordenadas virtuales y físicos. Windows llama a un sistema de coordenadas que tiene un significado real en el mundo físico, un **sistema de coordenadas espaciales**.

Los sistemas de coordenadas espaciales expresan sus valores de coordenadas en metros. Esto significa que los objetos colocados en 2 unidades separadas en el eje X, Y o Z aparecerán 2 metros de distancia entre sí cuando se representen en realidad mixta. Esto le permite representar fácilmente objetos y entornos a escala real.

En general, los sistemas de coordenadas cartesianos pueden ser zurdos o zurdos. Los sistemas de coordenadas espaciales en Windows siempre son zurdos, lo que significa que el eje X positivo apunta hacia la derecha, el eje Y positivo apunta hacia arriba (alineado con gravedad) y el eje Z positivo apunta hacia usted.

En ambos tipos de sistemas de coordenadas, el eje X positivo apunta a la derecha y el eje Y positivo apunta hacia arriba. La diferencia radica en el hecho de que el eje Z positivo apunte hacia delante o fuera. Puede recordar en qué dirección apunta el eje Z positivo apuntando los dedos de la mano izquierda o derecha en la dirección X positiva y enrollándose a la dirección Y positiva. La dirección en la que se encuentra el punto de control, ya sea hacia delante o fuera, es la dirección en la que apunta el eje Z positivo para ese sistema de coordenadas.

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>Creación de una experiencia de solo orientación o de escalado

La clave para la [representación](rendering.md) holográfica es cambiar la vista de la aplicación de sus hologramas cada fotograma a medida que el usuario se desplaza, para que coincida con el movimiento de cabeza previsto. Puede crear **experiencias de escalado colocadas** que respeten los cambios en la posición principal y la orientación del encabezado del usuario mediante un **marco estacionario de referencia**.

Algunos contenidos deben omitir las actualizaciones de la posición principal, que permanecen fijas en el encabezado y la distancia elegidos del usuario en todo momento. El ejemplo principal es el vídeo de 360 grados: dado que el vídeo se captura desde una sola perspectiva fija, estropearía la ilusión de que la posición de la vista se desplazará en relación con el contenido, aunque la orientación de la vista deba cambiar cuando el usuario se desplace. Puede compilar estas **experiencias solo de orientación** mediante un **marco de referencia asociado**.

### <a name="stationary-frame-of-reference"></a>Marco estacionario de referencia

El sistema de coordenadas proporcionado por un marco estacionario de referencia funciona para mantener las posiciones de los objetos cerca del usuario tan estables como sea posible en relación con el mundo, al tiempo que se respetan los cambios en la posición principal del usuario.

En el caso de las experiencias de escalado sentado en un motor de juegos como [Unity](https://unity3d.com/), un marco de referencia es lo que define el "origen mundial" del motor. Los objetos que se colocan en una coordenada del mundo específica usan el marco estacionario de referencia para definir su posición en el mundo real con las mismas coordenadas. El contenido que se mantiene en todo el mundo, incluso cuando el usuario se recorre, se conoce como contenido de **bloque mundial** .

Normalmente, una aplicación creará un marco estacionario de referencia en el inicio y usará su sistema de coordenadas a lo largo de la duración de la aplicación. Como desarrollador de aplicaciones en Unity, simplemente puede empezar a colocar contenido en relación con el origen, que estará en la posición y la orientación iniciales del usuario. Si el usuario se mueve a una nueva ubicación y desea continuar su experiencia de escalado, puede recentrar el origen mundial en esa ubicación.

Con el tiempo, a medida que el sistema aprende más sobre el entorno del usuario, puede determinar que las distancias entre los distintos puntos del mundo real son más cortas o más largas que el sistema que se consideró anteriormente. Si representa hologramas en un marco estacionario de referencia para una aplicación en HoloLens en la que los usuarios van más allá de un área de alrededor de 5 metros de ancho, es posible que la aplicación Observe el desplazamiento en la ubicación observada de esos hologramas. Si su experiencia tiene usuarios que van más allá de 5 metros, está creando una [experiencia de escala mundial](#building-a-world-scale-experience), que requerirá técnicas adicionales para mantener los hologramas estables, como se describe a continuación.

### <a name="attached-frame-of-reference"></a>Marco de referencia asociado

Un marco de referencia conectado se mueve con el usuario a medida que se recorren, con un encabezado fijo definido cuando la aplicación crea el fotograma por primera vez. Esto permite al usuario buscar de forma cómoda el contenido colocado dentro de ese marco de referencia. El contenido representado en esta manera relativa al usuario se denomina contenido **bloqueado por el cuerpo** .

Cuando el casco no puede averiguar dónde se encuentra en el mundo, un marco de referencia asociado proporciona el único sistema de coordenadas que se puede usar para representar hologramas. Esto hace que sea ideal para mostrar la interfaz de usuario de reserva para indicar al usuario que su dispositivo no puede encontrarlos en el mundo. Las aplicaciones que están colocadas en escala o superior deben incluir una reserva de solo orientación para ayudar al usuario a volver a empezar, con una interfaz de usuario similar a la que se muestra en la [Página principal de la realidad mixta](navigating-the-windows-mixed-reality-home.md).

## <a name="building-a-standing-scale-or-room-scale-experience"></a>Creación de una experiencia de escalado permanente o a escala de habitación

Para ir más allá de la escala colocada en un casco inmersivo y crear una **experiencia de escalado permanente**, puede usar el **marco de ensayo de referencia**.

Para proporcionar una **experiencia de escalado a sala**, lo que permite a los usuarios desplazarse por el límite de 5 metros que están predefinidos, puede comprobar también los límites de la **fase** .

### <a name="stage-frame-of-reference"></a>Marco de la fase de referencia

Cuando se configura por primera vez un auricular envolvente, el usuario define una **fase**, que representa el salón en el que experimentará una realidad mixta. La fase define mínimamente un **origen**de la fase, un sistema de coordenadas espaciales centrado en la posición y orientación hacia delante elegidos por el usuario en el que pretenden usar el dispositivo. Al colocar el contenido en este sistema de coordenadas de fase en el plano Y = 0, puede asegurarse de que los hologramas aparecen de forma cómoda en el suelo cuando el usuario está de pie, lo que proporciona a los usuarios una **experiencia de escalado permanente**.

### <a name="stage-bounds"></a>Límites de fase

Opcionalmente, el usuario también puede definir **límites de fase**, un área dentro de la habitación en la que han borrado el mobiliario en el que pretenden desplazarse por la realidad mixta. Si es así, la aplicación puede crear una **experiencia de escalado de habitación**y usar estos límites para asegurarse de que los hologramas siempre se colocan donde el usuario puede tener acceso a ellos.

Dado que el marco de la fase de referencia proporciona un único sistema de coordenadas fijo en el que colocar el contenido relativo al suelo, es la ruta más sencilla para portar aplicaciones de escalado permanente y a escala de sala desarrolladas para auriculares de realidad virtual. Sin embargo, al igual que con esas plataformas de VR, un único sistema de coordenadas solo puede estabilizar el contenido en un diámetro de 5 metros (16 pies), antes de que los efectos de la palanca de la maneta hagan que el contenido alejado del centro se desplace de forma notable a medida que el sistema se ajuste. Para ir más allá de 5 metros, se necesitan delimitadores espaciales.

## <a name="building-a-world-scale-experience"></a>Creación de una experiencia de escala mundial

HoloLens permite verdaderas **experiencias de escala mundial** que permiten a los usuarios ir más allá de 5 metros. Para compilar una aplicación de escala mundial, necesitará nuevas técnicas más allá de las que se usan para las experiencias a escala de habitación.

### <a name="why-a-single-rigid-coordinate-system-cannot-be-used-beyond-5-meters"></a>Por qué no se puede usar un único sistema de coordenadas rígidos más allá de 5 metros

En la actualidad, al escribir juegos, aplicaciones de visualización de datos o aplicaciones de realidad virtual, el enfoque típico consiste en establecer un sistema de coordenadas universal absoluta en el que todas las demás coordenadas puedan volver a asignarse de forma confiable. En ese entorno, siempre puede encontrar una transformación estable que define una relación entre dos objetos cualesquiera de ese mundo. Si no ha movido esos objetos, sus transformaciones relativas siempre permanecerán iguales. Este tipo de sistema de coordenadas global funciona bien cuando se representa un mundo puramente virtual en el que se conoce toda la geometría de antemano. Hoy en día, las aplicaciones de la aplicación de la escala de sala establecen este tipo de sistema de coordenadas de escala de sala absoluta con su origen en el piso.

Por el contrario, un dispositivo de realidad mixta untethered, como HoloLens, tiene un conocimiento dinámico basado en sensor del mundo, ajustando continuamente su conocimiento a lo largo del tiempo del entorno del usuario, ya que recorren muchos medidores en todo el piso de un edificio. En una experiencia de escala mundial, si colocó todos los hologramas en un único sistema rígido de coordenadas, esos hologramas se desplazarían necesariamente con el tiempo, con relación al mundo o entre sí.

Por ejemplo, en la actualidad, los auriculares pueden creer que dos ubicaciones del mundo van separados por 4 metros y, posteriormente, refinan esa información, aprendiendo que las ubicaciones están en realidad 3,9 metros de distancia. Si esos hologramas se hubieran colocado inicialmente a 4 metros de distancia en un único sistema rígido de coordenadas, uno de ellos mostraría siempre 0,1 metros del mundo real.

### <a name="spatial-anchors"></a>Delimitadores espaciales

Windows Mixed Reality soluciona el problema descrito en la sección anterior, ya que permite crear [anclajes espaciales](spatial-anchors.md) para marcar puntos importantes del mundo en los que el usuario ha colocado hologramas. Un delimitador espacial representa un punto importante en el mundo del cual el sistema debe realizar un seguimiento a lo largo del tiempo.

A medida que el dispositivo aprende sobre el mundo, estos delimitadores espaciales pueden ajustar su posición en relación con el otro según sea necesario para asegurarse de que cada delimitador se mantiene exactamente donde se colocó en relación con el mundo real. Al colocar un delimitador espacial en la ubicación donde el usuario coloca un holograma y, a continuación, colocar ese holograma en relación con su delimitador espacial, puede asegurarse de que el holograma mantiene la estabilidad óptima, incluso cuando el usuario se mueve en decenas de metros.

Este ajuste continuo de los delimitadores espaciales relacionados entre sí es la diferencia clave entre los sistemas de coordenadas de los delimitadores espaciales y los marcos de referencia:

* Los hologramas colocados en el marco estacionario de referencia mantienen una relación rígida entre sí. Sin embargo, a medida que el usuario recorra largas distancias, el sistema de coordenadas del marco puede desplazarse en relación con el mundo para asegurarse de que los hologramas junto al usuario parezcan estables.

* Los hologramas colocados en el marco de la fase de referencia también mantienen una relación rígida entre sí. A diferencia del marco estacionario, el marco de la fase siempre permanece fijo en su lugar con respecto a su origen físico definido. Sin embargo, el contenido representado en el sistema de coordenadas de la fase más allá de su límite de 5 medidos solo aparecerá estable mientras el usuario esté de acuerdo con ese límite.

* Los hologramas colocados con un delimitador espacial pueden desplazarse con respecto a los hologramas colocados mediante otro delimitador espacial. Esto permite a Windows mejorar su comprensión de la posición de cada delimitador espacial, incluso si, por ejemplo, un delimitador tiene que ajustarse a la izquierda y otro delimitador debe ajustarse a la derecha.

A diferencia de un marco estacionario de referencia, que siempre optimiza la estabilidad cerca del usuario, el marco de fase de referencia y los delimitadores espaciales garantizan la estabilidad cerca de sus orígenes. Esto ayuda a que estos hologramas se mantengan con precisión en el tiempo, pero también significa que los hologramas que se representen demasiado lejos del origen del sistema de coordenadas experimentarán efectos cada vez más graves. Esto se debe a que los pequeños ajustes en la posición y la orientación de la fase o el delimitador se amplían proporcionalmente a la distancia desde ese anclaje. 

Una buena regla general es asegurarse de que todo lo que se represente en función de un sistema de coordenadas del delimitador espacial distante esté dentro de unos 3 metros de su origen. En el caso de un origen de fase cercano, la representación de contenido distante es correcta, ya que el aumento de los errores posicionales solo afectará a los hologramas pequeños que no se desplazarán mucho en la vista del usuario.

### <a name="spatial-anchor-persistence"></a>Persistencia del delimitador espacial

Los delimitadores espaciales también pueden permitir que la aplicación recuerde una ubicación importante incluso después de que la aplicación se suspenda o se apague el dispositivo.

Puede guardar en el disco los delimitadores espaciales que crea la aplicación y, a continuación, volver a cargarlos más adelante, si los conserva en el **almacén de delimitadores espaciales**de la aplicación. Al guardar o cargar un delimitador, debe proporcionar una clave de cadena que sea significativa para la aplicación, con el fin de identificar el delimitador más adelante. Considere esta clave como el nombre de archivo del delimitador. Si desea asociar otros datos con ese delimitador, como un modelo 3D que el usuario colocó en esa ubicación, guárdelo en el almacenamiento local de la aplicación y asócielo con la clave que eligió.

Al conservar los delimitadores en el almacén, los usuarios pueden colocar hologramas individuales o colocar un área de trabajo en torno a la cual una aplicación colocará sus distintos hologramas y, después, buscar esos hologramas más adelante donde los esperan, en muchos usos de la aplicación.

También se puede usar <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> para la persistencia de hologramas asincrónicos en dispositivos Android, iOS y HoloLens.  Al compartir un delimitador espacial en la nube duradera, varios dispositivos pueden observar el mismo holograma persistente a lo largo del tiempo, aunque los dispositivos no estén presentes juntos simultáneamente.

### <a name="spatial-anchor-sharing"></a>Uso compartido del delimitador espacial

La aplicación también puede compartir un delimitador espacial en tiempo real con otros dispositivos, lo que permite experiencias compartidas en tiempo real.

Mediante el uso de <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">anclajes espaciales de Azure</a>, la aplicación puede compartir un anclaje espacial en varios dispositivos HoloLens, iOS y Android. Con la representación de un holograma mediante el mismo delimitador espacial en cada dispositivo, los usuarios verán el holograma aparecer en el mismo lugar en el mundo real.

## <a name="avoid-head-locked-content"></a>Evitar el contenido bloqueado de encabezado

Se desaconseja encarecidamente la representación de contenido bloqueado por cabeza, que permanece en un punto fijo de la pantalla (por ejemplo, un HUD). En general, el contenido con bloqueo de encabezado es incómodo para los usuarios y no se siente como una parte natural de su mundo.

Normalmente, el contenido bloqueado por el encabezado se debe reemplazar por los hologramas que se adjuntan al usuario o se colocan en el propio mundo. Por ejemplo, los [cursores](cursors.md) generalmente se deben insertar en el mundo, escalar de forma natural para reflejar la posición y la distancia del objeto en la mirada del usuario.

## <a name="handling-tracking-errors"></a>Control de errores de seguimiento

En algunos entornos, como los vestíbulos oscuros, es posible que no sea posible que haya un casco que use el seguimiento interno para buscarse correctamente en el mundo. Esto puede hacer que los hologramas no se muestren o aparezcan en lugares incorrectos si no se tratan correctamente. Ahora se describen las condiciones en las que esto puede suceder, su impacto en la experiencia del usuario y sugerencias para administrar mejor esta situación.

### <a name="headset-cannot-track-due-to-insufficient-sensor-data"></a>El casco no puede realizar el seguimiento debido a que no hay suficientes datos de sensor

A veces, los sensores del casco no pueden averiguar dónde está el casco. Esto puede ocurrir si el salón es oscuro, o si los sensores están tapados por pelo o manos, o si el entorno no tiene una textura suficiente.

Cuando esto sucede, el casco no podrá realizar un seguimiento de su posición con suficiente precisión para representar hologramas de bloque mundial. No podrá averiguar dónde se encuentra un anclaje espacial, un fotograma estacionario o un marco de la fase en relación con el dispositivo, pero puede seguir representando el contenido bloqueado por el cuerpo en el marco de referencia asociado.

La aplicación debe indicar al usuario Cómo volver a realizar el seguimiento posicional y representar algún contenido bloqueado por el cuerpo de reserva que describa algunas sugerencias, como la detección de los sensores y la activación de más luces.

### <a name="headset-tracks-incorrectly-due-to-dynamic-changes-in-the-environment"></a>El casco realiza un seguimiento incorrecto debido a cambios dinámicos en el entorno

A veces, el dispositivo no puede realizar un seguimiento adecuado si hay muchos cambios dinámicos en el entorno, por ejemplo, muchas personas que desplazan por la habitación. En este caso, es posible que los hologramas parezcan saltar o desplazarse cuando el dispositivo intente realizar un seguimiento en este entorno dinámico. Se recomienda usar el dispositivo en un entorno menos dinámico si se alcanza este escenario.

### <a name="headset-tracks-incorrectly-because-the-environment-has-changed-significantly-over-time"></a>El casco realiza un seguimiento incorrecto porque el entorno ha cambiado significativamente con el tiempo

A veces, al empezar a usar un casco en un entorno que ha sufrido muchos cambios (por ejemplo, un movimiento significativo de mobiliario, bloqueos de pared, etc.), es posible que algunos hologramas aparezcan desplazados desde sus ubicaciones originales. Los hologramas anteriores también pueden saltar a medida que el usuario se desplaza por este nuevo espacio. Esto se debe a que la comprensión del espacio del sistema ya no contiene e intenta reasignar el entorno al intentar reconciliar las características de la sala. En este escenario, se recomienda a los usuarios que vuelvan a colocar los hologramas anclados en el mundo si no aparecen donde se esperaba.

### <a name="headset-tracks-incorrectly-due-to-identical-spaces-in-an-environment"></a>El casco realiza un seguimiento incorrecto debido a espacios idénticos en un entorno

A veces, un hogar u otro espacio puede tener dos áreas idénticas. Por ejemplo, dos salones de conferencia idénticos, dos áreas de esquina idénticas, dos pósteres idénticos de gran tamaño que cubren el campo de vista del dispositivo. En estos escenarios, el dispositivo puede, en ocasiones, confundirse entre las partes idénticas y marcarlas como las mismas en su representación interna. Esto puede hacer que los hologramas de algunas áreas aparezcan en otras ubicaciones. Es posible que el dispositivo empiece a perder el seguimiento con frecuencia, ya que la representación interna del entorno está dañada. En este caso, se recomienda restablecer el conocimiento medioambiental del sistema. Tenga en cuenta que al restablecer el mapa, se pierden todas las ubicaciones de anclaje espacial. Esto hará que los auriculares realicen el seguimiento bien en las áreas únicas del entorno. Sin embargo, el problema puede volver a producirse si el dispositivo se vuelve a confundir entre las mismas áreas.

## <a name="see-also"></a>Vea también
* [Presentación de GDC 2017 en sistemas de coordenadas espaciales y representación holográfica](https://channel9.msdn.com/events/GDC/GDC-2017/GDC2017-008)
* [Sistemas de coordenadas de Unity](coordinate-systems-in-unity.md)
* [Sistemas de coordenadas de DirectX](coordinate-systems-in-directx.md)
* [Delimitadores espaciales](spatial-anchors.md)
* [Experiencias compartidas en realidad mixta](shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [Case study - Looking through holes in your reality](case-study-looking-through-holes-in-your-reality.md) (Caso práctico: mirar por un agujero en tu realidad)
