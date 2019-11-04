---
title: Criterios de calidad de la aplicación
description: En este documento se describen los principales factores que afectan a la calidad de las aplicaciones de realidad mixta.
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: Criterios de calidad de la aplicación, realidad mixta, aplicación de realidad mixta
ms.openlocfilehash: f98111ebe9aacc30778e86501be41e6ac5f6d165
ms.sourcegitcommit: 6bc6757b9b273a63f260f1716c944603dfa51151
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/01/2019
ms.locfileid: "73437049"
---
# <a name="app-quality-criteria"></a>Criterios de calidad de la aplicación

En este documento se describen los principales factores que afectan a la calidad de las aplicaciones de realidad mixta. Para cada factor se proporciona la siguiente información:
* Información general: breve descripción del factor de calidad y por qué es importante.
* Impacto en el dispositivo: Qué tipo de dispositivo de realidad mixta de ventana se ve afectado.
* Criterios de calidad: Cómo evaluar el factor de calidad.
* Cómo medir: métodos para medir (o experimentar) el problema.
* Recomendaciones: Resumen de los enfoques para proporcionar una mejor experiencia de usuario.
* Recursos: recursos de desarrollador y diseño relevantes que son útiles para crear mejores experiencias de la aplicación.

## <a name="frame-rate"></a>Velocidad de fotogramas

La velocidad de fotogramas es el primer pilar de estabilidad del holograma y la comodidad del usuario. La velocidad de fotogramas por debajo de los objetivos recomendados puede hacer que los hologramas parezcan vibrantes, lo que afecta negativamente a la increíble potencia de la experiencia y, potencialmente, a la fatiga ocular. La velocidad de fotogramas de destino para su experiencia en los auriculares de la realidad mixta de Windows será de 60Hz o 90Hz, según los equipos compatibles con Windows Mixed Reality que desee admitir. Para HoloLens, la velocidad de fotogramas de destino es 60 Hz.

### <a name="device-impact"></a>Impacto del dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Rendimiento  |  Reúne |  Puedan |
--- | --- | ---
| La aplicación cumple de forma coherente el objetivo de fotogramas por segundo (FPS) para el dispositivo de destino: 60fps en HoloLens; 90fps en ultra PCs; y 60fps en equipos estándar. | La aplicación tiene caídas de fotogramas intermitentes que no impiden la experiencia básica; o FPS es constantemente inferior al objetivo deseado, pero no impide la experiencia de la aplicación. | La aplicación está experimentando una caída en la velocidad de fotogramas como promedio cada diez segundos o menos. |

### <a name="how-to-measure"></a>Cómo medir

* El [portal de dispositivos de Windows](using-the-windows-device-portal.md#system-performance) proporciona un gráfico de velocidad de fotogramas en tiempo real en "rendimiento del sistema".
* Para la depuración de desarrollo, agregue un contador de diagnóstico de velocidad de fotogramas a la aplicación. Vea recursos para obtener un contador de ejemplo.
* Las caídas de velocidad de fotogramas se pueden experimentar en el dispositivo mientras la aplicación se está ejecutando moviendo el encabezado de lado a lado. Si el holograma muestra un movimiento de vibración inesperado, es probable que la velocidad de fotogramas baja o el plano de estabilidad sea la causa.

### <a name="recommendations"></a>Recomendaciones

* Agregue un contador de velocidad de fotogramas al principio del trabajo de desarrollo.
* Los cambios que incurren en una caída en la velocidad de fotogramas se deben evaluar y resolver correctamente como un error de rendimiento.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Descripción del rendimiento de la realidad mixta](understanding-performance-for-mixed-reality.md)
* [Estabilidad y velocidad del holograma](hologram-stability.md#frame-rate)
* [Presupuesto de rendimiento de activos](asset-creation-process.md)
* [Recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a>Herramientas y tutoriales

* [MRToolkit, pantalla de contador de FPS](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [MRToolkit, sombreadores](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a>Referencias externas

* [Unity, optimizar aplicaciones móviles](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a>Estabilidad de holograma

Los hologramas estables aumentarán la facilidad de uso y la increíble capacidad de su aplicación, y crearán una experiencia de visualización más cómoda para el usuario. La calidad de la estabilidad del holograma es el resultado de un buen desarrollo de la aplicación y la capacidad del dispositivo para comprender (realizar un seguimiento) de su entorno. Aunque la velocidad de fotogramas es el primer pilar de estabilidad, otros factores pueden afectar a la estabilidad, como:

* Uso del plano de estabilización
* Distancia a los delimitadores espaciales
* Llevar

### <a name="device-impact"></a>Impacto del dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Rendimiento  |  Reúne |  Puedan |
--- | --- | ---
|  Los hologramas aparecen de forma coherente. | El contenido secundario exhibe un movimiento inesperado. o el movimiento inesperado no impide la experiencia general de la aplicación. | El contenido principal del marco exhibe un movimiento inesperado. |

### <a name="how-to-measure"></a>Cómo medir

Con el dispositivo y la visualización de la experiencia:

* Mover el encabezado de lado a lado, si los hologramas muestran un movimiento inesperado, la velocidad de fotogramas baja o la alineación incorrecta del plano de estabilidad al plano focal es la causa probable.
* Desplazarse por los hologramas y el entorno, busque comportamientos como nadar y salto. Este tipo de movimiento probablemente se debe a que el dispositivo no realiza un seguimiento del entorno o a la distancia al delimitador espacial.
* Si hay varios hologramas en el marco, observe el comportamiento de holograma en varias profundidades al mover la posición principal de lado a lado, en caso de que la irregularidad parezca que esto se debe a un plano de estabilización.

### <a name="recomendations"></a>Recomendaciones

* Agregue un contador de velocidad de fotogramas al principio del trabajo de desarrollo.
* Use el plano de estabilización.
* Siempre representa los hologramas anclados dentro de los 3 metros de su delimitador.
* Asegúrese de que el entorno está configurado para el seguimiento adecuado.
* Diseñe su experiencia para evitar los hologramas en diversos niveles de profundidad focal dentro del marco.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Estabilidad y velocidad del holograma](hologram-stability.md#frame-rate)
* [Caso práctico, uso del plano de estabilización](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [Descripción del rendimiento de la realidad mixta](understanding-performance-for-mixed-reality.md)
* [Recomendaciones de rendimiento para Unity](performance-recommendations-for-unity.md)
* [Delimitadores espaciales](spatial-anchors.md)
* [Control de errores de seguimiento](coordinate-systems.md#handling-tracking-errors)
* [Marco estacionario de referencia](coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a>Herramientas y tutoriales

* [Kit complementario MR, Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a>Posición de hologramas en superficies reales

Las alineaciones de los hologramas con objetos físicos (si se prevé que se colocarán en relación con otras) son una indicación clara de la no Unión de los hologramas y del mundo real. La precisión de la selección de ubicación debe ser relativa a las necesidades del escenario; por ejemplo, la selección de ubicación de superficie general puede usar el mapa espacial, pero la selección de ubicación más precisa requerirá el uso de marcadores y calibración.

### <a name="device-impact"></a>Impacto del dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Rendimiento  |  Reúne |  Puedan |
--- | --- | ---
| Los hologramas se alinean a la superficie normalmente en el intervalo de centímetros a pulgadas. Si se requiere más precisión, la aplicación debe proporcionar un medio eficaz para la colaboración dentro de la especificación de la aplicación deseada. | N/A | Los hologramas aparecen sin alinear con el objeto de destino físico, ya que separan el plano de la superficie o parecen flotar fuera de la superficie. Si se requiere precisión, los hologramas deben cumplir las especificaciones de proximidad del escenario. | 

### <a name="how-to-measure"></a>Cómo medir

* Los hologramas que se colocan en el mapa espacial no deben parecer drásticamente por encima o por debajo de la superficie.
* Los hologramas que requieren una ubicación precisa deben tener algún tipo de sistema de marcadores y calibración que sea preciso para el requisito del escenario.

### <a name="recommendations"></a>Recomendaciones

* El mapa espacial resulta útil para colocar objetos en superficies cuando no se requiere precisión.
* Para obtener la mejor precisión, use marcadores o pósteres para establecer los hologramas y un controlador de Xbox (o algún mecanismo de alineación manual) para la calibración final.
* Considere la posibilidad de dividir los hologramas extra grandes en partes lógicas y alinear cada parte en la superficie.
* La Interpupilary distancia establecida correctamente (IPD) también puede afectar a la alineación de los hologramas. Configure siempre HoloLens en el del usuario.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Colocación de asignación espacial](spatial-mapping.md#placement)
* [Proceso de detección de salas](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [Procedimientos recomendados para los anclajes espaciales](spatial-anchors.md#best-practices)
* [Control de errores de seguimiento](coordinate-systems.md#handling-tracking-errors)
* [Asignación espacial en Unity](spatial-mapping-in-unity.md)
* [Información general sobre el desarrollo de Vuforia](vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a>Herramientas y tutoriales

* [MR espacial 230: asignación espacial](holograms-230.md)
* [Kit de herramientas de MR, bibliotecas de asignación espacial](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [Kit complementario MR, ejemplo de calibración de póster](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [Kit complementario MR, Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a>Referencias externas

* [Caso práctico de Lowes, alineación de precisión](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a>Ver la zona de confort

Los desarrolladores de aplicaciones controlan el lugar en el que los usuarios convergen colocando contenido y hologramas a varias profundidades. Los usuarios que contengan HoloLens siempre se acomodarán a 2,0 m para mantener una imagen clara porque las pantallas de HoloLens se fijan a una distancia óptica aproximadamente a 2,0 m del usuario. Una profundidad de contenido incorrecta puede conducir a la molestia visual o a la fatiga.

### <a name="device-impact"></a>Impacto del dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

<table>
<tr>
<td> Rendimiento </td><td><ul>
<li>Coloque el contenido en 2m.</li><li>Cuando los hologramas no se pueden colocar en 2m y no se pueden evitar conflictos entre convergencia y ajuste, la zona óptima para la colocación de hologramas se encuentra entre 1,25 m y 5 m.</li><li>En todos los casos, los diseñadores deben estructurar el contenido para animar a los usuarios a interactuar con 1 + m (por ejemplo, ajustar el tamaño del contenido y los parámetros de ubicación predeterminados).</li><li>A menos que el escenario no requiera específicamente, se debe implementar un plano de recorte con fadeout a partir de 1m.</li><li>En los casos en los que se requiere una observación más detallada de un holograma de motionless, el contenido no debe estar más cerca que 50CM.</li>
</ul></td>
</tr><tr>
<td> Reúne</td><td> El contenido está dentro de la guía de visualización y movimiento, pero se usa inadecuadamente o no se usa el plano de recorte.</td>
</tr><tr>
<td> Puedan </td><td> El contenido se presenta demasiado cerca (normalmente &lt;1,25 m o &lt;50CM para los hologramas estacionales que requieren una observación más detallada).</td>
</tr>
</table>

### <a name="how-to-measure"></a>Cómo medir

* Normalmente, el contenido debe ser de 2 m, pero no más cercano a 1,25 o superior a 5 m.
* Con pocas excepciones, la distancia de representación de recorte de HoloLens debe establecerse en. 85CM con fadeout de contenido que empieza en 1m. Acerque el contenido y observe el efecto del plano de recorte.
* El contenido estacionario no debe estar más cerca de 50CM.

### <a name="recommendations"></a>Recomendaciones

* Diseñe el contenido para obtener la distancia de visualización óptima de 2 m.
* Establezca la distancia de representación de recorte en 85cm con fadeout de contenido a partir de 1m.
* En el caso de los hologramas estacionales que necesitan una visualización más estrecha, el plano de recorte no debe estar más cerca de 30cm y fadeout debe iniciar al menos 10cm fuera del plano de recorte.

### <a name="resources"></a>Recursos

* [Distancia de representación](hologram-stability.md#hologram-render-distances)
* [Punto de enfoque en Unity](focus-point-in-unity.md)
* [Experimentación con escala](scale.md#experimenting-with-scale)
* [Texto, tamaño de fuente recomendado](typography.md#recommended-font-size)

## <a name="depth-switching"></a>Cambio de profundidad

Sin tener en cuenta los problemas de la zona de confort, las demandas del usuario a cambiar con frecuencia o rapidez entre los objetos cercanos y lejanos (incluidos los hologramas y el contenido del mundo real) pueden conducir a la fatiga oculomotor y a la molestia general.

### <a name="device-impact"></a>Impacto del dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Rendimiento  |  Reúne |  Puedan |
--- | --- | ---
|  Cambio de profundidad limitado o natural que no hace que el usuario se recentre sin ningún problema. | Cambio de profundidad abrupta: este es el núcleo y está diseñado en la experiencia de la aplicación, o en el modificador de profundidad abrupta causado por contenido real inesperado. | Conmutador de profundidad coherente o cambio de profundidad brusco que no es necesario ni básico para la experiencia de la aplicación. | 

### <a name="how-to-measure"></a>Cómo medir

* Si la aplicación requiere que el usuario cambie de forma constante y/o repentinamente el foco de profundidad, hay un problema de conmutación de profundidad.

### <a name="recommendations"></a>Recomendaciones

* Mantenga el contenido principal en un plano focal coherente y asegúrese de que el plano de estabilización coincide con el plano focal. Esto evitará la fatiga oculomotor y el movimiento de holograma inesperado.

### <a name="resources"></a>Recursos

* [Distancia de representación](hologram-stability.md#hologram-render-distances)
* [Punto de enfoque en Unity](focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a>Uso de sonido espacial

En Windows Mixed Reality, el motor de audio proporciona el componente aural de la experiencia de realidad mixta mediante la simulación de un sonido 3D mediante simulaciones de dirección, distancia y entorno. El uso de un sonido espacial en una aplicación permite a los desarrolladores colocar los sonidos de forma convincente en un espacio tridimensional (esfera) alrededor del usuario. Después, esos sonidos parecerán como si provinieran de objetos físicos reales o los hologramas de realidad mixta en el entorno del usuario. El sonido espacial es una herramienta eficaz para la inmersión, accesibilidad y diseño de la experiencia del usuario en aplicaciones de realidad mixta.

### <a name="device-impact"></a>Impacto del dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Rendimiento  |  Reúne |  Puedan |
--- | --- | ---
|  El sonido está espacial lógicamente y la experiencia de usuario usa correctamente el sonido para ayudar con la detección de objetos y los comentarios de los usuarios. El sonido es natural y relevante para los objetos y se normaliza en el escenario. | El audio espacial se utiliza de forma adecuada para aumentar la capacidad de respuesta, pero falta como medio para ayudar con los comentarios de los usuarios y la detectabilidad. | El sonido no está espacialmente como se esperaba o falta de sonido para ayudar al usuario dentro de la experiencia de usuario. O el audio espacial no se consideró ni usó en el diseño del escenario. | 

### <a name="how-to-measure"></a>Cómo medir

* En general, los sonidos relevantes deben emitirse desde los hologramas de destino (por ejemplo, el sonido de corteza procedente de holográfica Dog).
* Deben usarse señales sonoras en toda la experiencia del usuario para ayudar al usuario a realizar comentarios o a conocer las acciones que se encuentran fuera del marco holográfica.

### <a name="recommendations"></a>Recomendaciones

* Use el audio espacial para ayudar con la detección de objetos y las interfaces de usuario.
* Los sonidos reales funcionan mejor que la síntesis o el sonido no natural.
* La mayoría de los sonidos deben ser espaciales.
* Evite los emisores invisibles.
* Evite el enmascaramiento espacial.
* Normalizar todos los sonidos.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Sonido espacial](spatial-sound.md)
* [Diseño de sonido espacial](spatial-sound-design.md)
* [Sonido espacial en Unity](spatial-sound-in-unity.md)
* [Caso práctico, sonido espacial para HoloTour](case-study-spatial-sound-design-for-holotour.md)
* [Caso práctico, uso de sonido espacial en RoboRaid](case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a>Herramientas y tutoriales

* [MR espacial 220: sonido espacial](holograms-220.md)
* [MRToolkit, audio espacial](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a>Centrarse en los límites de trama holográfica (hipertema)

Las experiencias de usuario bien diseñadas pueden crear y mantener un contexto útil del entorno virtual que se extiende alrededor de los usuarios. Mitigar el efecto de los límites de los hipertextos implica un diseño minucioso de la escala y el contexto del contenido, el uso de audio espacial, los sistemas de orientación y la posición del usuario. Si se realiza correctamente, el usuario sentirá menos el límite de los límites de los subprocesos, a la vez que tiene una experiencia de aplicación cómoda.

### <a name="device-impact"></a>Impacto del dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Rendimiento  |  Reúne |  Puedan |
--- | --- | ---
|  El usuario nunca pierde el contexto y se siente cómodo. Se proporciona asistencia contextual para objetos grandes. Se proporcionan instrucciones de detección y visualización para los objetos que se encuentran fuera del marco. En general, el diseño de movimiento y la escala de los hologramas son adecuados para una experiencia de visualización cómoda. | El usuario nunca pierde el contexto, pero es posible que se requiera movimiento de cuello adicional en situaciones limitadas. En situaciones limitadas, la escala hace que los hologramas interrumpan el fotograma vertical u horizontal, lo que produce un movimiento de cuello para ver los hologramas. | Es necesario que el usuario pierda el contexto o el movimiento de cuello coherente para ver los hologramas. No hay ninguna guía de contexto para objetos holográficas grandes, el movimiento de objetos es fácil de perder fuera del marco sin ninguna guía de detección, o bien un holograma alto requiere un movimiento de cuello normal para verlo. | 

### <a name="how-to-measure"></a>Cómo medir

* El contexto de un holograma (grande) se pierde o no se entiende debido a que se recortan en los límites.
* La ubicación de los hologramas es difícil de encontrar debido a la falta de directores de atención o al contenido que mueve y sale rápidamente del marco holográfica.
* El escenario requiere un movimiento de cabezal normal y repetitivo hacia arriba y hacia abajo para ver por completo un holograma que dé lugar a una fatiga del cuello.

### <a name="recommendations"></a>Recomendaciones

* Comience la experiencia con objetos pequeños que se ajusten al objeto de subproceso y, a continuación, transición con indicaciones visuales a versiones más grandes.
* Use los directores de audio y atención espaciales para ayudar al usuario a encontrar contenido que está fuera del hipermismo.
* En la medida de lo posible, evite los hologramas que recortan verticalmente el hipernivel.
* Proporcionar al usuario orientación en la aplicación para obtener la mejor ubicación de visualización.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Marco holográfico](holographic-frame.md)
* [Caso práctico, aprendizaje de la interfaz de usuario de HoloStudio y diseño de interacción](case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [Escala de objetos y entornos](scale.md)
* [Cursores, indicaciones visuales](cursors.md#visual-cues)

#### <a name="external-references"></a>Referencias externas

* [Gran cantidad de ADO sobre el visual](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a>El contenido reacciona a la posición del usuario

Los hologramas deben reaccionar a la posición del usuario aproximadamente de la misma manera que lo hacen los objetos "reales". Una consideración de diseño importante son los elementos de la interfaz de usuario que no pueden suponer necesariamente que la posición de un usuario sea estacional y adaptarse al movimiento del usuario. El diseño de una aplicación que se adapta correctamente a la posición del usuario creará una experiencia más increíble y facilitará su uso.

### <a name="device-impact"></a>Impacto del dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

<table>
<tr>
<td> Rendimiento </td><td> El contenido y la interfaz de usuario se adaptan a las posiciones de los usuarios, lo que permite al usuario interactuar de forma natural con el contenido dentro del ámbito de movimiento esperado</td>
</tr><tr>
<td> Reúne </td><td> La interfaz de usuario se adapta a la posición del usuario, pero puede impedir la vista de contenido clave que requiere que el usuario ajuste su posición.</td>
</tr><tr>
<td> Puedan </td><td><ol>
<li>Los elementos de la interfaz de usuario se pierden o se bloquean durante el movimiento, lo que provoca que el usuario vuelva a los controles (o los busque) de una misma.</li><li>Los elementos de la interfaz de usuario limitan la vista del contenido principal.</li><li>El movimiento de la interfaz de usuario no está optimizado para ver la distancia y el momento, especialmente con elementos de interfaz <a href="billboarding-and-tag-along.md">de usuario de etiquetas</a> .</li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a>Cómo medir

* Todas las medidas deben realizarse dentro de un ámbito razonable del escenario. Aunque el movimiento del usuario variará, no intente engañar a la aplicación con un movimiento de usuario extremo.
* En el caso de los elementos de la interfaz de usuario, los controles pertinentes deben estar disponibles independientemente del movimiento del usuario. Por ejemplo, si el usuario está viendo y recorriendo un mapa 3D con zoom, el control de zoom debe estar disponible para el usuario independientemente de la ubicación.

### <a name="recommendations"></a>Recomendaciones

* El usuario es la cámara y controla el movimiento. Dejar que se controlen.
* Considere la posibilidad de mostrar los sistemas de texto y de menú que, de otro modo, podrían quedar bloqueados o desconocidos si un usuario tuviera que desplazarse.
* Use la etiqueta junto con el contenido que debe seguir al usuario y, al mismo tiempo, permitir que el usuario vea lo que hay delante de ellos.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Diseño de interacción](hologram.md)
* [Color, claro y material](color,-light-and-materials.md)
* [Etiquetado y vista frontal continua](billboarding-and-tag-along.md)
* [Interacciones instintivas](interaction-fundamentals.md)
* [Automovimiento y Locomotion de usuario](comfort.md#self-motion-and-user-locomotion)

#### <a name="tools-and-tutorials"></a>Herramientas y tutoriales

* [Entrada MR 210: mirada](holograms-210.md)

## <a name="input-interaction-clarity"></a>Claridad de interacción de entrada

La claridad de la interacción de entrada es fundamental para el uso de una aplicación e incluye la coherencia de entrada, la capacidad de enfoque, la detectabilidad de los métodos de interacción. El usuario debe poder usar las interacciones comunes de toda la plataforma sin tener que reaprender. Si la aplicación tiene una entrada personalizada, debe comunicarse claramente y mostrarse.

### <a name="device-impact"></a>Impacto del dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Rendimiento  |  Reúne |  Puedan |
--- | --- | ---
|  Los métodos de interacción de entrada son coherentes con las [instrucciones](interaction-fundamentals.md)proporcionadas por Windows Mixed Reality. Cualquier entrada personalizada no debe ser redundante con entrada estándar (en lugar de usar la interacción estándar) y se debe comunicar y demostrar claramente al usuario. | Similar a lo mejor, pero las entradas personalizadas son redundantes con los métodos de entrada estándar. El usuario puede seguir logrando el objetivo y el progreso a través de la experiencia de la aplicación. | Es difícil comprender la asignación de botones o métodos de entrada. La entrada está muy personalizada, no es compatible con la entrada estándar, no hay instrucciones o probablemente cause problemas de fatiga y confort. | 

### <a name="how-to-measure"></a>Cómo medir

* La aplicación usa [métodos de entrada estándar](interaction-fundamentals.md) coherentes.
* Si la aplicación tiene una entrada personalizada, se comunica claramente mediante:
* Experiencia de primera ejecución
* Pantallas de introducción
* Información de herramientas
* Autocar manual
* Sección de ayuda
* Voz sobre

### <a name="recommendations"></a>Recomendaciones

* Utilice los métodos de entrada estándar siempre que sea posible.
* Proporcione demostraciones, tutoriales e información sobre herramientas para los métodos de entrada no estándar.
* Use un modelo de interacción coherente en toda la aplicación.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Interacciones instintivas](interaction-fundamentals.md)
* [Objetos interactuables](interactable-object.md)
* [Control con la cabeza y permanencia](gaze-and-dwell.md)
* [Cursores](cursors.md)
* [Confort y mira](comfort.md#gaze-direction)
* [Entrada de voz](voice-input.md)
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

* [Caso práctico: el logro de más informática personal](case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [Estudio de conversión: aprendizaje de la interfaz de usuario de HoloStudio y diseño de interacción](case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [Aplicación de ejemplo: tabla periódica de los elementos](periodic-table-of-the-elements.md)
* [Aplicación de ejemplo: módulo lunar](lunar-module.md)
* [Entrada MR 210: mirada](holograms-210.md)
* [Entrada MR 211: gestos](holograms-211.md)
* [Entrada MR 212: voz](holograms-212.md)

## <a name="interactable-objects"></a>Objetos interactuables

Un botón ha sido una metáfora usada para desencadenar un evento en el mundo abstracto 2D. En el mundo de la realidad mixta de tres dimensiones, ya no es necesario limitarnos a este mundo de la abstracción. Cualquier elemento puede ser un objeto interactuable que desencadene un evento. Un objeto interactuable puede representarse como cualquier cosa, desde una taza de café de la mesa hasta un globo flotante en el aire. Independientemente del formulario, los objetos interactivos deben ser claramente reconocibles por el usuario a través de las indicaciones de audio y visual.

### <a name="device-impact"></a>Impacto del dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Rendimiento  |  Reúne |  Puedan |
--- | --- | ---
|  Independientemente del formulario, los objetos interactuables se pueden reconocer a través de las indicaciones de audio y visual en tres Estados: inactivo, dirigido y seleccionado. "Lo veo, por ejemplo, está claro y se usa de forma coherente en toda la experiencia. Los objetos se escalan y distribuyen para permitir la finalización de errores de forma gratuita. | El usuario puede reconocer objetos como interactivos a través de comentarios de audio o visuales, y puede tener como destino y activar el objeto. | No se proporcionan indicaciones visuales o de audio, el usuario no puede reconocer un objeto interactuable. Las interacciones son propensas a errores debido a la escala de objetos o a la distancia entre los objetos. | 

### <a name="how-to-measure"></a>Cómo medir

* Los objetos interactuables son reconocibles como ' interactuable '; incluir botones, menús y contenido específico de la aplicación. Como regla general, debe haber una indicación visual y de audio cuando el destino es objetos interactivos.

### <a name="recommendations"></a>Recomendaciones

* Use comentarios visuales y de audio para las interacciones.
* Los comentarios visuales deben diferenciarse en cada estado de entrada (inactivo, dirigido, seleccionado)
* Los objetos que se pueden interactuar deben escalarse y colocarse para los destinos sin errores.
* Los objetos interactuables agrupados (por ejemplo, una barra de menús o una lista) deben tener el espaciado adecuado para el destino.
* Los botones y menús que admiten el comando de voz deben proporcionar etiquetas de texto para la palabra clave Command ("vea esto, dígalo")

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Objeto con el que se puede interactuar](interactable-object.md)
* [Texto en Unity](text-in-unity.md)
* [Cuadro de límite y barra de la aplicación](app-bar-and-bounding-box.md)
* [Entrada de voz](voice-input.md)

#### <a name="tools-and-tutorials"></a>Herramientas y tutoriales

* [Kit de herramientas de realidad mixta-UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a>Detección de salas

Las aplicaciones que requieren datos de asignación espacial se basan en el dispositivo para recopilar automáticamente estos datos a lo largo del tiempo y entre sesiones a medida que el usuario explora su entorno con el dispositivo activo. La integridad y la calidad de estos datos dependen de una serie de factores, entre los que se incluye la cantidad de exploración que ha realizado el usuario, cuánto tiempo ha transcurrido desde la exploración y si los objetos como el mobiliario y las puertas se han trasladado desde que el dispositivo examinó la zona. Muchas aplicaciones analizarán los datos de asignación espacial al principio de la experiencia para juzgar si el usuario debe realizar pasos adicionales para mejorar la integridad y la calidad del mapa espacial. Si es necesario que el usuario analice el entorno, debe proporcionar instrucciones claras durante la experiencia de exploración.

### <a name="device-impact"></a>Impacto del dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Rendimiento  |  Reúne |  Puedan |
--- | --- | ---
|  Visualización de la malla espacial indique a los usuarios que el análisis está en curso. El usuario sabe claramente qué hacer y cuándo se inicia y se detiene el examen. | Se proporciona la visualización de la malla espacial, pero es posible que el usuario no sepa claramente qué hacer y que no se proporcione información de progreso. | Ninguna visualización de malla. No se proporciona información de orientación al usuario sobre dónde buscar, o Cuándo se inicia o se detiene el examen. |

### <a name="how-to-measure"></a>Cómo medir

* Durante un examen de habitación necesario, se proporciona orientación visual y de audio que indica dónde buscar y cuándo iniciar y detener el examen.

### <a name="recommendations"></a>Recomendaciones

* Indique la cantidad del volumen total de los usuarios que debe formar parte de la experiencia.
* Comunicarse cuando el examen se inicia y se detiene, como un indicador de progreso.
* Use una visualización de la malla durante el examen.
* Proporcione guías de audio y visual para animar al usuario a buscar y desplazarse por la habitación.
* Informe al usuario de dónde debe ir para mejorar los datos. En muchos casos, puede ser mejor indicar al usuario lo que necesita hacer (por ejemplo, mirar el límite superior, mirar detrás del mobiliario) para obtener la calidad de examen necesaria.

### <a name="resources"></a>Recursos

#### <a name="documentation"></a>Documentación

* [Visualización de la exploración de la sala](room-scan-visualization.md)
* [Caso práctico: ampliación de las funcionalidades de asignación espacial de HoloLens](case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [Caso práctico: diseño de sonido espacial para HoloTour](case-study-spatial-sound-design-for-holotour.md)
* [Caso práctico: creación de una experiencia envolvente en fragmentos](case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a>Herramientas y tutoriales

* [Kit de herramientas de realidad mixta-UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a>Indicadores direccionales

En una aplicación de realidad mixta, el contenido puede estar fuera del campo de vista o ocluidos por objetos del mundo real. Una aplicación bien diseñada facilitará a los usuarios la búsqueda de contenido no visible. Los indicadores direccionales avisan a un usuario de contenido importante y proporcionan orientación sobre el contenido en relación con la posición del usuario. Las instrucciones para el contenido no visible pueden adoptar la forma de emisores de sonido, flechas direccionales o indicaciones visuales directas.

### <a name="device-impact"></a>Impacto del dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Rendimiento  |  Reúne |  Puedan |
--- | --- | ---
|  Las guías de audio y visual guían directamente al usuario al contenido relevante fuera del campo de vista. | Una flecha o algún indicador que apunta al usuario en la dirección general del contenido. | El contenido relevante está fuera del campo de vista y no se proporciona ninguna guía de ubicación para el usuario. | 

### <a name="how-to-measure"></a>Cómo medir

* El contenido relevante fuera del campo de vista de usuario se detecta mediante señales de audio o visual.

### <a name="recommendations"></a>Recomendaciones

* Cuando el contenido pertinente esté fuera del campo de vista del usuario, use indicadores direccionales e indicaciones de audio para guiar al usuario al contenido. En muchos casos, se prefiere una guía visual directa a las flechas direccionales.
* Los indicadores direccionales no se deben integrar en el cursor.

### <a name="resources"></a>Recursos

* [Marco holográfico](holographic-frame.md)

## <a name="data-loading"></a>Carga de datos

Un control de progreso proporciona información al usuario sobre el hecho de que se está llevando a cabo una operación de ejecución larga. Puede significar que el usuario no puede interactuar con la aplicación cuando el indicador de progreso está visible y también puede indicar cuánto tiempo puede ser el tiempo de espera.

### <a name="device-impact"></a>Impacto del dispositivo

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>Criterios de calidad

|  Rendimiento  |  Reúne |  Puedan |
--- | --- | ---
|  Indicador visual animado, en forma de una barra de progreso o un anillo, que muestra el progreso durante cualquier carga o procesamiento de datos. El indicador visual proporciona instrucciones sobre cuánto tiempo puede ser la espera. | Se informa al usuario de que la carga de datos está en curso, pero no hay ninguna indicación de cuánto tiempo podría ser la espera. | No hay ningún indicador de carga de datos o de proceso para que la tarea tarde más de 5 segundos. |

### <a name="how-to-measure"></a>Cómo medir

* Durante la carga de datos, compruebe que no hay ningún estado en blanco durante más de 5 segundos.

### <a name="recommendations"></a>Recomendaciones

* Proporcionar un animador de carga de datos que muestre el progreso en cualquier situación en la que el usuario pueda percibir que esta aplicación se haya detenido o bloqueado. Una regla general razonable es cualquier actividad de "carga" que podría tardar más de 5 segundos.

### <a name="resources"></a>Recursos

* [Indicación del progreso](progress.md)
