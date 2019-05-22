---
title: Criterios de calidad de la aplicación
description: Este documento describe los principales factores que afectan a la calidad de las aplicaciones de realidad mixta.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: criterios de calidad de la aplicación, la realidad mixta mixto de aplicación de realidad
ms.openlocfilehash: 756bc148f290aa3406c9ac8bb7003d463c62772c
ms.sourcegitcommit: c20563b8195c0c374a927b96708d958b127ffc8f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/21/2019
ms.locfileid: "65974747"
---
# <a name="app-quality-criteria"></a>Criterios de calidad de la aplicación

Este documento describe los principales factores que afectan a la calidad de las aplicaciones de realidad mixta. Para cada factor se proporciona la siguiente información
* Información general: una breve descripción de factor de calidad y por qué es importante.
* Impacto de dispositivo: el tipo de dispositivo de realidad mixta de ventana se ve afectado.
* Criterios de calidad: cómo evaluar el factor de calidad.
* Cómo medir: métodos para medir el problema (o experiencia).
* Recomendaciones: resumen de los enfoques para ofrecer una mejor experiencia de usuario.
* Recursos: desarrolladores pertinentes y los recursos de diseño que son útiles para crear mejores experiencias de aplicación.

## <a name="frame-rate"></a>Velocidad de fotogramas

Velocidad de fotogramas es el primer pilar de comodidad de holograma estabilidad y el usuario. Velocidad de fotogramas por debajo de los destinos recomendados puede provocar hologramas aparezcan nerviosos afectan negativamente la believability de la experiencia y que puedan causar fatiga visual. La velocidad de fotogramas de destino para su experiencia en inmersivos Windows Mixed Reality estará bien 60 o 90Hz dependiendo de qué Mixed Reality compatible con equipos con Windows que desea admitir. HoloLens la velocidad de fotogramas de destino es de 60Hz.

### <a name="device-impact"></a>Impacto de dispositivo

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Mejor  |  Cumple |  un error |
--- | --- | ---
| La aplicación cumple siempre fotogramas por segundo (FPS) para el dispositivo de destino: 60fps en HoloLens; 90fps en PCs Ultra; y 60fps en equipos estándar. | La aplicación tiene caídas intermitentes de fotogramas no impide la experiencia principal; o bien FPS es constantemente inferior a objetivo deseado, pero no impida la experiencia de aplicación. | La aplicación está experimentando una disminución en la velocidad de fotogramas en promedio cada diez segundos o menos. |

### <a name="how-to-measure"></a>Cómo medir

* Se proporciona un gráfico de velocidad de fotogramas en tiempo real a través mediante el [Windows Device Portal](using-the-windows-device-portal.md#system-performance) bajo "Rendimiento del sistema".
* Para la depuración de desarrollo, agregar un contador de diagnóstico de velocidad de fotogramas en la aplicación. Consulte los recursos de un contador de ejemplo.
* Caídas de velocidad de fotogramas se pueden experimentar en el dispositivo mientras se ejecuta la aplicación moviendo la cabeza de lado a lado. Si muestra en el holograma movimiento nerviosos inesperado, a continuación, de baja velocidad de fotogramas o el plano de estabilidad es probablemente la causa.

### <a name="recommendations"></a>Recomendaciones

* Agregar un contador de velocidad de fotogramas al principio del trabajo de desarrollo.
* Los cambios que se incurre en un descenso en la velocidad de fotogramas deben ser evaluados y resuelto correctamente como un error de rendimiento.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Análisis de rendimiento de la realidad mixta](understanding-performance-for-mixed-reality.md)
* [Velocidad de fotogramas y la estabilidad de holograma](hologram-stability.md#frame-rate)
* [Presupuesto de rendimiento de activos](asset-creation-process.md)
* [Recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a>Herramientas y tutoriales

* [MRToolkit, para mostrar del contador FPS](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [MRToolkit, sombreadores](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a>Referencias externas

* [Unity, optimización de aplicaciones móviles](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a>Estabilidad holograma

Hologramas estables aumentará la facilidad de uso y believability de la aplicación y crear una experiencia de visualización más cómoda para el usuario. La calidad de estabilidad holograma es el resultado de desarrollo de por sí buena aplicación y la capacidad del dispositivo a comprender (pista) su entorno. Mientras la velocidad de fotogramas es el primer pilar de estabilidad, otros factores pueden afectar estabilidad incluidos:

* Uso de la placa de estabilización
* Distancia delimitadores espacial
* Seguimiento

### <a name="device-impact"></a>Impacto de dispositivo

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Mejor  |  Cumple |  un error |
--- | --- | ---
|  Hologramas aparecen continuamente estables. | Contenido secundario Exhibe movimiento inesperado; o movimiento inesperado impedir la experiencia de aplicación global. | Contenido principal en el marco exhibe un movimiento inesperado. |

### <a name="how-to-measure"></a>Cómo medir

Aunque utilice el dispositivo y la experiencia de visualización:

* Mover la cabeza de lado a lado, si el hologramas muestran el movimiento inesperado, a continuación, de baja velocidad de fotogramas o alineación incorrecta de la placa de estabilidad en el plano focal es la causa probable.
* Moverse por el entorno y hologramas, Buscar comportamientos como nado y jumpiness. Este tipo de movimiento es probable que deba por el dispositivo no hace seguimiento el entorno o la distancia con relación al anclaje espacial.
* Si es grande o varios hologramas están en el marco, observar el comportamiento de holograma en diversos profundidades al mover su posición principal de lado a lado, si aparece de inestabilidad es probable que esto ha provocado por el plano de estabilización.

### <a name="recomendations"></a>Recomendaciones de

* Agregar un contador de velocidad de fotogramas al principio del trabajo de desarrollo.
* Utilice el plano de estabilización.
* Siempre se representan hologramas delimitados dentro de 3 metros de su delimitador.
* Asegúrese de que su entorno está configurado para el seguimiento adecuado.
* Diseñar su experiencia para evitar hologramas en distintos niveles de profundidad focal dentro del marco.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Velocidad de fotogramas y la estabilidad de holograma](hologram-stability.md#frame-rate)
* [Caso práctico, con el plano de estabilización](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [Análisis de rendimiento de la realidad mixta](understanding-performance-for-mixed-reality.md)
* [Recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md)
* [Delimitadores espaciales](spatial-anchors.md)
* [Seguimiento de control de errores](coordinate-systems.md#handling-tracking-errors)
* [Marco estático de referencia](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a>Herramientas y tutoriales

* [El Sr. complementaria Kit, Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a>Posición de hologramas en superficies real

Desajustes de hologramas con objetos físicos (si está diseñado para colocarse en relación con ellas) es una indicación clara de la unión no son de hologramas y reales. Precisión de la selección de ubicación debe ser relativa a las necesidades del escenario; Por ejemplo, colocación de superficie general puede usar la asignación espacial, pero más preciso colocación requerirán algún uso de marcadores y calibración.

### <a name="device-impact"></a>Impacto de dispositivo

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Mejor  |  Cumple |  un error |
--- | --- | ---
| Hologramas alinean a la superficie de normalmente en los centímetros al intervalo pulgadas. Si se requiere mayor precisión, la aplicación debe proporcionar un medio eficaz para la colaboración dentro de la especificación de la aplicación deseada. | N/A | El hologramas aparecen sin alinear con el objeto de destino físico interrumpir el plano de la superficie o que aparecen a float lejos de la superficie. Si se requiere la precisión, hologramas deben cumplir la especificación de la proximidad del escenario. | 

### <a name="how-to-measure"></a>Cómo medir

* No deben aparecer hologramas que se colocan en el mapa espacial drásticamente flotar encima o debajo de la superficie.
* Hologramas que requieren una colocación precisa deben tener algún tipo de marcador y calibración del sistema que es preciso hasta los requisitos del escenario.

### <a name="recommendations"></a>Recomendaciones

* Asignación espacial es útil para colocar objetos en superficies cuando la precisión no es necesaria.
* La mejor precisión, utilizar marcadores o pósters para establecer el hologramas y un controlador Xbox (o algún mecanismo de alineación manual) para la calibración final.
* Considere la posibilidad de dividir hologramas muy grandes en partes lógicas y alinear cada parte a la superficie.
* Incorrectamente conjunto interpupilary distancia (IPD) también puede afectar la alineación holograma. Configure siempre HoloLens en IPD del usuario.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Selección de ubicación de asignación espacial](spatial-mapping.md#placement)
* [Espacio de proceso de detección](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [Prácticas recomendadas de delimitadores espacial](spatial-anchors.md#best-practices)
* [Seguimiento de control de errores](coordinate-systems.md#handling-tracking-errors)
* [Asignación espacial en Unity](spatial-mapping-in-unity.md)
* [Introducción al desarrollo de Vuforia](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a>Herramientas y tutoriales

* [MR Spatial 230: asignación espacial](holograms-230.md)
* [El Sr. Kit de herramientas, bibliotecas de asignación espacial](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [MR complementaria Kit, ejemplo de calibración de póster](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [El Sr. complementaria Kit, Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a>Referencias externas

* [Caso práctico de Lowes, alineación de precisión](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a>Visualización de zona de comodidad

Control de los desarrolladores de aplicaciones donde convergen los ojos de los usuarios mediante la colocación de contenido y hologramas en diversos profundidades. Los usuarios gastando de HoloLens siempre se alojará a m 2.0 para mantener una imagen clara porque muestra de HoloLens se fija en una distancia óptica aproximadamente 2.0m alejándose del usuario. Profundidad de contenido incorrecto puede provocar fatiga ni incomodidad visual.

### <a name="device-impact"></a>Impacto de dispositivo

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

<table>
<tr>
<td> Mejor </td><td><ul>
<li>Colocar contenido en 2 minutos.</li><li>Cuando no se puede colocar hologramas en 2 minutos y no se puede evitar conflictos entre la convergencia y alojamiento, es la zona de colocación holograma óptimo entre 1,25 y 5 millones.</li><li>En todos los casos, los diseñadores deben estructurar el contenido para animar a los usuarios interactúen más de 1 m de distancia (por ejemplo, ajustar el tamaño del contenido y predeterminado de los parámetros de colocación).</li><li>A menos que específicamente no es necesario según el escenario, un plano de recorte debe implementar con fadeout comenzando en 1 millón.</li><li>En casos donde se requiere una observación más cerca de un holograma inmóvil, el contenido no debe ser menor que 50cm.</li>
</ul></td>
</tr><tr>
<td> Cumple</td><td> Está contenido dentro de la Guía de movimiento y de visualización, pero uso incorrecto o no utiliza el plano de recorte.</td>
</tr><tr>
<td> un error </td><td> El contenido se presenta demasiado cerca (normalmente &lt;1.25 m, o &lt;50 cm para estacionarios hologramas que requieren más cerca de observación.)</td>
</tr>
</table>

### <a name="how-to-measure"></a>Cómo medir

* Contenido deberían normalmente tener 2m ausente, pero no más cerca que más de 5m o 1,25.
* Con pocas excepciones, la distancia de representación de recorte de HoloLens debe establecerse en .85CM con fadeout empezando por 1m de contenido. Enfocar el contenido y tenga en cuenta el efecto del plano de recorte.
* Contenido estático no debe estar más cerca que 50cm ausente.

### <a name="recommendations"></a>Recomendaciones

* Diseñar el contenido de la distancia óptima de 2 minutos.
* Establece la distancia de la representación de recorte en 85cm con fadeout empezando por 1m de contenido.
* Para hologramas estacionarios que necesitan más cerca de visualización, el plano de recorte debe ser no menos de 30cm y fadeout debe empezar al menos 10cm fuera del plano de recorte.

### <a name="resources"></a>Recursos

* [Representar distancia](hologram-stability.md#hologram-render-distances)
* [Punto de enfoque en Unity](focus-point-in-unity.md)
* [Experimentar con escala](scale.md#experimenting-with-scale)
* [Texto, tamaño de fuente recomendado](typography.md#recommended-font-size)

## <a name="depth-switching"></a>Cambio de profundidad

Independientemente de la zona de visualización de los problemas de comodidad, exige el usuario puede cambiar con frecuencia o rápidamente entre casi y ahora focal objetos (incluidos hologramas y contenido del mundo real) pueden dar lugar a fatiga oculomotor y malestar general.

### <a name="device-impact"></a>Impacto de dispositivo

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Mejor  |  Cumple |  un error |
--- | --- | ---
|  Profundidad natural o limitada de conmutación no hace que se reenfocar al usuario. | Conmutador de profundidad abrupta es el núcleo y diseñadas en la experiencia de aplicación, o conmutador de profundidad abrupta producida por el contenido real-world inesperado. | Conmutador de profundidad coherente, o cambio brusco profundidad que no es necesario o core a la experiencia de aplicación. | 

### <a name="how-to-measure"></a>Cómo medir

* Si la aplicación requiere que el usuario para constantemente o repentinamente cambiar el foco de profundidad, no hay profundidad cambiar el problema.

### <a name="recommendations"></a>Recomendaciones

* Mantener el contenido principal en un plano focal coherente y asegúrese de que el plano de estabilización coincide con el plano focal. Alivie oculomotor fatiga y movimiento holograma inesperado.

### <a name="resources"></a>Recursos

* [Representar distancia](hologram-stability.md#hologram-render-distances)
* [Punto de enfoque en Unity](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a>Uso de sonido espacial

En Windows Mixed Reality, el motor de audio proporciona el componente de la experiencia de realidad mixta auditiva simulando 3D sonido con simulaciones del entorno, la distancia y dirección. Usar sonido espacial en una aplicación permite a los desarrolladores colocar convincingly sonidos en un espacio dimensional 3 (esfera) en todo el usuario. Los sonidos, a continuación, le resultará como si provinieran objetos físicos real o la hologramas realidad mixta en el entorno del usuario. Sonido espacial es una herramienta eficaz para inmersión, accesibilidad y diseño de la experiencia de usuario en aplicaciones de realidad mixta.

### <a name="device-impact"></a>Impacto de dispositivo

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Mejor  |  Cumple |  un error |
--- | --- | ---
|  Lógicamente es spatialized sonido y la experiencia de usuario adecuadamente usa sonido para ayudar a los comentarios de usuario y la detección de objeto. Sonido es natural y relevantes para los objetos y normalizado en el escenario. | Audio espacial es usado correctamente para believability pero no se encuentra como medio para facilitar la detectabilidad y comentarios del usuario. | No se spatialized sonido según lo esperado, o falta de sonido para ayudar a los usuarios de la experiencia de usuario. O bien, no se considera o se usan en el diseño del escenario de audio espacial. | 

### <a name="how-to-measure"></a>Cómo medir

* En general, deben emitir sonidos relevantes de hologramas de destino (ej., sonido corteza procedentes de perro holográfica.)
* Las indicaciones de sonido deben usarse en toda la experiencia de usuario para ayudar al usuario con comentarios ni el conocimiento de las acciones fuera del marco holográfica.

### <a name="recommendations"></a>Recomendaciones

* Utilice audio espacial para ayudar con interfaces de usuario y la detección del objeto.
* Sonidos real funcionan mejor que síntesis o sonido no natural.
* Debe ser spatialized mayoría de los sonidos.
* Evite los emisores invisibles.
* Evite enmascaramiento espacial.
* Normalizar todos los sonidos.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Sonido espacial](spatial-sound.md)
* [Diseño de sonido espacial](spatial-sound-design.md)
* [Sonido espacial en Unity](spatial-sound-in-unity.md)
* [Caso práctico de sonido para HoloTour espacial](case-study-spatial-sound-design-for-holotour.md)
* [Caso práctico, usar sonido espacial en RoboRaid](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a>Herramientas y tutoriales

* [MR Spatial 220: sonido espacial](holograms-220.md)
* [MRToolkit, Audio espacial](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a>Centrarse en los límites del marco holográfica (FOV)

Experiencias de usuario bien diseñada pueden crear y mantener un contexto útil del entorno virtual que se extiende en torno a los usuarios. Mitigar el efecto de los límites FOV implica un diseño concienzudo de escalado de contenido y el contexto, el uso de audio espacial, sistemas de orientación y la posición del usuario. Si se hace correctamente, el usuario se sentirán como menor afectadas por los límites del campo visual al tiempo que tiene una experiencia de aplicación cómodo.

### <a name="device-impact"></a>Impacto de dispositivo

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Mejor  |  Cumple |  un error |
--- | --- | ---
|  Usuario nunca pierde el contexto y se siente cómodo ver. Se proporciona ayuda contextual para los objetos grandes. Detectabilidad y ver la guía se proporcionan para los objetos fuera del marco. En general, el diseño de movimiento y la escala de la hologramas son adecuados para una experiencia de visualización cómoda. | Usuario nunca pierde el contexto, pero es posible que deban movimiento cuello adicional en ciertas situaciones. En ciertas situaciones escalado hace hologramas para interrumpir en el marco vertical u horizontal, causando ciertos movimientos cuello ver hologramas. | Usuario que puede perder contexto o movimiento cuello coherente se requiere para ver hologramas. Ninguna instrucción de contexto para objetos holográficas grandes, mover objetos fáciles de perder fuera del marco sin instrucciones de detectabilidad ni hologramas altos requiere movimiento cuello regulares para ver. | 

### <a name="how-to-measure"></a>Cómo medir

* Contexto para un holograma (grande) se pierde o no entiende debido a que se recorta por los límites.
* Ubicación de hologramas son difíciles de encontrar debido a la falta de directores de atención o contenido que entra y sale rápidamente el marco holográfico.
* Escenario requiere repetitivas y reducir verticalmente un movimiento principal para ver por completo un holograma resultante en fatiga cuello y regular.

### <a name="recommendations"></a>Recomendaciones

* La experiencia de inicio con objetos pequeños que ajustar el campo visual y, después, realizar la transición con indicaciones visuales a las versiones más grandes.
* Use espaciales directores de audio y atención para la búsqueda de contenido de usuario que está fuera del campo visual.
* Cuando sea posible, evite hologramas que recortar verticalmente el campo visual.
* Proporcionar al usuario con instrucciones de la aplicación para ver la ubicación de mejor.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Marco holográfico](holographic-frame.md)
* [Caso práctico, HoloStudio UI y conocimientos de diseño de interacción](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [Escalado de objetos y entornos](scale.md)
* [Cursores, indicaciones visuales](cursors.md#visual-cues)

#### <a name="external-references"></a>Referencias externas

* [El campo visual con ado](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a>Contenido reacciona a la posición del usuario

Hologramas deben reaccionar ante el usuario coloque en aproximadamente la misma forma que los objetos de "real". Una consideración de diseño importantes es elementos de interfaz de usuario que no se pueden suponer necesariamente la posición de un usuario esté parados y adaptar y movimiento del usuario. Diseñar una aplicación que correctamente se adapta a la posición del usuario creará una experiencia más solo y que sea más fácil de usar.

### <a name="device-impact"></a>Impacto de dispositivo

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

<table>
<tr>
<td> Mejor </td><td> Contenido y la interfaz de usuario se adaptan a las posiciones de usuario que permite usuario interactúen de forma natural con contenido dentro del ámbito de movimiento de usuario esperado.</td>
</tr><tr>
<td> Cumple </td><td> Interfaz de usuario se adapta a la posición del usuario, pero puede impedir la vista de contenido clave pedir al usuario que ajustan su posición.</td>
</tr><tr>
<td> un error </td><td><ol>
<li>Elementos de interfaz de usuario se pierde o se bloquea durante el usuario que causan de movimiento que se vuelva a controles (o busque).</li><li>Elementos de interfaz de usuario limitan la vista de contenido principal.</li><li>Movimiento de la interfaz de usuario no está optimizado para la visualización de distancia y momentum especialmente con <a href="billboarding-and-tag-along.md">tag-along</a> elementos de interfaz de usuario.</li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a>Cómo medir

* Todas las mediciones deben realizarse dentro de un ámbito razonable del escenario. Aunque puede variar el movimiento de usuario, no intente engañar a la aplicación con el movimiento de usuario extreme.
* Para los elementos de interfaz de usuario, los controles relevantes deben estar disponibles, independientemente del movimiento del usuario. Por ejemplo, si el usuario está viendo y caminar alrededor de un mapa 3D con zoom, el control de zoom debe ser estén disponible para el usuario independientemente de la ubicación.

### <a name="recommendations"></a>Recomendaciones

* El usuario es la cámara y controlan el movimiento. Deje que su unidad.
* Considere la posibilidad de vallas publicitarias para texto y sistemas trabajé que de lo contrario serían bloqueado por el mundo u oculta si un usuario tuviera que desplazarse.
* Usar tag-along para el contenido que debe seguir al usuario mientras sigue permitiendo que el usuario ver lo que está delante de ellas.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Diseño de interacción](hologram.md)
* [Color de luz y material](color,-light-and-materials.md)
* [Etiquetado y vista frontal continua](billboarding-and-tag-along.md)
* [Interacciones instintivas](interaction-fundamentals.md)
* [El movimiento y el desplazamiento del usuario](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a>Herramientas y tutoriales

* [MR Input 210: mirada](holograms-210.md)

## <a name="input-interaction-clarity"></a>Claridad de interacción de entrada

Claridad de interacción de entrada es fundamental para la facilidad de uso de una aplicación e incluye la entrada coherencia, innegables, detectabilidad de los métodos de interacción. Usuario debería poder usar las interacciones habituales de toda la plataforma sin volver a aprender. Si la aplicación tiene parámetros de entrada personalizado, se debe claramente comunicar y demostrar.

### <a name="device-impact"></a>Impacto de dispositivo

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Mejor  |  Cumple |  un error |
--- | --- | ---
|  Métodos de entrada de interacción son coherentes con Windows Mixed Reality proporcionado [orientación](interaction-fundamentals.md). Cualquier entrada personalizada no debería ser redundante con la entrada estándar (en su lugar use interacción estándar) y debe claramente comunicar y demostrar al usuario. | Es similar a las entradas mejor, pero personalizadas son redundantes con métodos de entrada estándares. Usuario todavía puede lograr el objetivo y el progreso a través de la experiencia de aplicación. | Difíciles de comprender la asignación de botón o el método de entrada. Input personalizado en gran medida, no es compatible con la entrada estándar, no hay instrucciones, o puede provocar problemas de fatiga y comodidad. | 

### <a name="how-to-measure"></a>Cómo medir

* La aplicación usa coherente [métodos de entrada estándar.](interaction-fundamentals.md)
* Si la aplicación tiene parámetros de entrada personalizados, claramente se comunique a través de:
* Experiencia de primera ejecución
* Pantallas de presentación
* Información sobre herramientas
* Instructora de mano
* Sección de ayuda
* VoiceOver

### <a name="recommendations"></a>Recomendaciones

* Utilice los métodos de entrada estándares siempre que sea posible.
* Proporcionar información sobre herramientas, tutoriales y demostraciones para métodos de entrada no estándares.
* Usar un modelo de interacción coherente en toda la aplicación.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Interacciones instintivas](interaction-fundamentals.md)
* [Objetos interactuable](interactable-object.md)
* [Control con la cabeza y permanencia](gaze-and-dwell.md)
* [Cursores](cursors.md)
* [Comodidad y mirada](comfort.md#gaze-direction)
* [Gestos](gestures.md)
* [Entrada de voz](voice-input.md)
* [Comandos de voz](voice-design.md)
* [Controladores de movimiento](motion-controllers.md)
* [Guía de portabilidad de entrada para Unity](input-porting-guide-for-unity.md)
* [Entrada desde teclado en Unity](keyboard-input-in-unity.md)
* [Mirada en Unity](gaze-in-unity.md)
* [Gestos y controladores de movimiento en Unity](gestures-and-motion-controllers-in-unity.md)
* [Entrada de voz en Unity](voice-input-in-unity.md)
* [Entrada desde teclado, ratón y controlador en DirectX](keyboard,-mouse,-and-controller-input-in-directx.md)
* [Control con la cabeza y los ojos de DirectX](gaze-in-directx.md)
* [Manos y controladores de movimiento en DirectX](hands-and-motion-controllers-in-directx.md)
* [Entrada de voz en DirectX](voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a>Herramientas y tutoriales

* [Caso práctico: La búsqueda de informática más personal](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [Estudio de conversión: HoloStudio UI y conocimientos de diseño de interacción](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [Aplicación de ejemplo: Tabla periódica de los elementos](periodic-table-of-the-elements.md)
* [Aplicación de ejemplo: Módulo lunar](lunar-module.md)
* [MR Input 210: mirada](holograms-210.md)
* [MR Input 211: Gestos](holograms-211.md)
* [MR Input 212: voz](holograms-212.md)

## <a name="interactable-objects"></a>Objetos interactuable

Un botón ha sido una metáfora utilizada para desencadenar un evento en el mundo abstracto 2D. En el mundo tridimensional de realidad mixta, no tenemos que limitarse a este mundo de abstracción ya. Nada puede ser un objeto Interactuable que desencadena un evento. Un objeto interactuable puede representarse como nada una taza de café en la tabla a un globo flotante en el aire. Independientemente del formulario, objetos interactuable deben ser claramente reconocibles por el usuario a través de las pistas de audio y visuales.

### <a name="device-impact"></a>Impacto de dispositivo

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Mejor  |  Cumple |  un error |
--- | --- | ---
|  Independientemente del formulario, objetos interactuable sean reconocibles a través de las indicaciones visuales y de audio a través de tres estados: inactivo, destinado y seleccionada. "Vea, diga" claro y coherente sirve a lo largo de la experiencia. Los objetos se escala y se distribuyen para permitir errores como destino. | Usuario puede reconocer el objeto como interactuable a través de comentarios de audio o el objeto visual y puede tener como destino y activar el objeto. | No dada indicaciones visuales o audio, usuario no puede reconocer un objeto interactuable. Las interacciones son propensas a errores debido a la escala del objeto o la distancia entre los objetos. | 

### <a name="how-to-measure"></a>Cómo medir

* Objetos interactuable son reconocibles como 'interactuable'; incluyendo contenido específico de los botones, menús y la aplicación. Como regla general debería haber una pista de audio y visual cuando tenga como destino objetos interactuable.

### <a name="recommendations"></a>Recomendaciones

* Usar comentarios visuales y de audio para las interacciones.
* Comentarios visuales es diferente para cada entrada de estado (inactivo, destino, seleccionado)
* Deben ser escalar y colocan por error libre como destino objetos interactuable.
* Los objetos agrupados interactuable (por ejemplo, una barra de menús o lista) deben tener espacio adecuado para dirigirse a.
* Los botones y menús que admiten el comando de voz deben proporcionar etiquetas de texto de la palabra clave de comando ("verlo, diga")

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Objeto con el que se puede interactuar](interactable-object.md)
* [Texto en Unity](text-in-unity.md)
* [Barra de la aplicación y cuadro delimitador](app-bar-and-bounding-box.md)
* [Comandos de voz](voice-design.md)

#### <a name="tools-and-tutorials"></a>Herramientas y tutoriales

* [Kit de herramientas de realidad mixta - UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a>Sala de análisis

Las aplicaciones que requieren datos de asignación espacial se basan en el dispositivo para recopilar estos datos automáticamente con el tiempo y en las sesiones como el usuario explora su entorno con el dispositivo activo. La integridad y la calidad de los datos depende de varios factores como la cantidad de exploración, el usuario ha hecho, ¿cuánto tiempo ha transcurrido desde la exploración y si objetos como muebles y puertas movido desde que el dispositivo había analizado el área. Muchas aplicaciones analizará los datos de asignación espacial al principio de la experiencia para juzgar si el usuario debe realizar pasos adicionales para mejorar la integridad y la calidad de la asignación espacial. Si el usuario es necesario para analizar el entorno, desactive le proporcionará instrucciones durante la experiencia de exploración.

### <a name="device-impact"></a>Impacto de dispositivo

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Mejor  |  Cumple |  un error |
--- | --- | ---
|  Visualización de la malla espacial indique a los usuarios análisis está en curso. Usuario claramente sabe qué hacer y cuando se inicia y detiene el análisis. | Se proporciona la visualización de la malla espacial, pero el usuario puede saber con claridad qué hacer y se proporciona ninguna información de progreso. | No hay ninguna visualización de malla. No se proporciona al usuario sobre dónde buscar o cuando el examen se inicia o detiene la información de orientación. |

### <a name="how-to-measure"></a>Cómo medir

* Durante un examen de espacio necesaria, se proporciona orientación de audio y visual que indica dónde buscar y cuándo se debe iniciar y detener análisis.

### <a name="recommendations"></a>Recomendaciones

* Indicar cuánto volumen total, en la proximidad de los usuarios debe formar parte de la experiencia.
* Cuando el examen se inicia y detiene como un indicador de progreso se comunican.
* Usar una visualización de la malla durante el análisis.
* Proporcionar indicaciones visuales y de audio para fomentar que usuario examinar y desplazarse por la habitación.
* Informar al usuario dónde debe ir para mejorar los datos. En muchos casos, puede ser mejor indicar que el usuario lo que necesitan (por ejemplo, examine el límite superior, busque detrás de muebles), con el fin de obtener la calidad del análisis necesarios.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Visualización de la exploración de la sala](room-scan-visualization.md)
* [Caso práctico: Expandir las capacidades de asignación espacial de HoloLens](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [Caso práctico: Diseño espacial de sonido para HoloTour](case-study-spatial-sound-design-for-holotour.md)
* [Caso práctico: Creación de una experiencia realmente cautivadora en fragmentos](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a>Herramientas y tutoriales

* [Kit de herramientas de realidad mixta - UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a>Indicadores direccionales

En una aplicación de realidad mixta, el contenido puede estar fuera del campo de visión u ocluyeron en objetos del mundo real. Una aplicación bien diseñada le resultará más fácil para el usuario buscar el contenido que no sea visible. Indicadores direccionales alertar a un usuario al contenido importante y asesoramiento sobre el contenido en relación con la posición del usuario. Guía de contenido que no sea visible puede adoptar la forma de los emisores de sonido, flechas direccionales o indicaciones visuales directas.

### <a name="device-impact"></a>Impacto de dispositivo

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Mejor  |  Cumple |  un error |
--- | --- | ---
|  Indicaciones visuales y de audio directamente guiar al usuario al contenido pertinente fuera el campo de visión. | Una flecha o algún indicador que señala al usuario en la dirección general del contenido. | Contenido relevante está fuera del campo de visión y deficiente o ninguna Guía de ubicación se proporciona al usuario. | 

### <a name="how-to-measure"></a>Cómo medir

* Contenido relevante fuera del campo de vista de usuario es reconocible a través de las indicaciones visuales o audio.

### <a name="recommendations"></a>Recomendaciones

* Cuando contenido relevante está fuera del campo de visión del usuario, utilice indicadores direccionales y pistas de sonido para guiar al usuario al contenido. En muchos casos, se prefiere una guía visual directa a través de las flechas direccionales.
* Indicadores direccionales no deben generarse en el cursor.

### <a name="resources"></a>Recursos

* [Marco holográfico](holographic-frame.md)

## <a name="data-loading"></a>Carga de datos

Un control de progreso proporciona información al usuario sobre el hecho de que se está llevando a cabo una operación de ejecución larga. Puede significar que el usuario no puede interactuar con la aplicación cuando el indicador de progreso está visible y también puede indicar cuánto podría ser el tiempo de espera.

### <a name="device-impact"></a>Impacto de dispositivo

<table>
<tr>
<th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Mejor  |  Cumple |  un error |
--- | --- | ---
|  Anima el indicador visual, en forma de una barra de progreso o anillo, que muestra el progreso durante cualquier dato cargando o procesando. El indicador visual proporciona orientación sobre cuánto podría ser la espera. | Se informa al usuario que la carga de datos está en curso, pero no hay ninguna indicación de cuánto podría ser la espera. | No hay carga de datos o indicadores de proceso de tarea tarda más de 5 segundos. |

### <a name="how-to-measure"></a>Cómo medir

* Compruebe que no hay ningún estado en blanco durante más de 5 segundos durante la carga de datos.

### <a name="recommendations"></a>Recomendaciones

* Proporcione una animación de la carga de datos muestra el progreso en cualquier situación cuando el usuario puede percibir esta aplicación se ha detenido o se ha bloqueado. Una regla general razonable es cualquier actividad "Cargando" que podría tardar más de 5 segundos.

### <a name="resources"></a>Recursos

* [Indicación del progreso](progress.md)
