---
title: Asignación espacial
description: Asignación espacial proporciona una representación detallada de las superficies reales en el entorno en torno a la HoloLens.
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: asignación espacial, HoloLens, realidad mixta, reconstrucción expuesta, malla, sr
ms.openlocfilehash: 31abeca624512f1d5e721dbe879ca2243cf41345
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59605772"
---
# <a name="spatial-mapping"></a>Asignación espacial

Asignación espacial proporciona una representación detallada de las superficies reales en el entorno en torno a la HoloLens, lo que permite a los desarrolladores crear una experiencia convincente de realidad mixta. Mediante la combinación del mundo real con el mundo virtual, una aplicación puede hacer hologramas parezca real. Las aplicaciones también pueden alinear forma más natural con las expectativas del usuario al proporcionar interacciones y familiares comportamientos reales.

<br>

>[!VIDEO https://www.youtube.com/embed/zff2aQ1RaVo]

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Característica</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens (gen 1)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td> Asignación espacial</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>



## <a name="conceptual-overview"></a>Información general conceptual

![Superficies de malla que abarcan una sala](images/SurfaceReconstruction.jpg)<br>
*Un ejemplo de una malla de asignación espacial que abarcan una sala*

Los dos tipos de objeto principal que utiliza para la asignación espacial son 'Espacial observador superficie' y la superficie espacial.

La aplicación proporciona el observador de superficie espacial con uno o más volúmenes de delimitadores para definir las regiones de espacio en el que la aplicación desea recibir datos de asignación espacial. Para cada uno de estos volúmenes, asignación espacial proporcionará la aplicación con un conjunto de superficies espacial.

Estos volúmenes pueden estacionarios (en una ubicación fija con respecto a la vida real) o se pueden vincular a la HoloLens (mueve, pero no giran, con el HoloLens mientras se desplaza a través del entorno). Cada superficie espacial describe superficies del mundo real en un pequeño volumen de espacio, representado como una malla de triángulo que se adjunta a un mundo bloqueado [del sistema de coordenadas espacial](coordinate-systems.md).

Como el HoloLens recopila nuevos datos sobre el entorno y, cuando se producen cambios en el entorno, aparecerán las superficies espaciales, desaparecen y cambiar.

## <a name="common-usage-scenarios"></a>Escenarios de uso comunes

![Ilustraciones de los escenarios de uso comunes de asignación espacial: Selección de ubicación, oclusión, física y navegación](images/sm-concepts-1000px.png)

### <a name="placement"></a>Colocación

Asignación espacial proporciona aplicaciones con la oportunidad de presentar formularios naturales y familiares de interacción para el usuario. ¿Qué podría ser más natural que al colocar el teléfono hacia abajo en el departamento de soporte técnico?

Restringir la colocación de hologramas (o más en general, cualquier selección de ubicaciones espaciales) tiene su origen en superficies proporciona una asignación natural de 3D (punto en el espacio) en 2D (punto de superficie). Esto reduce la cantidad de información que el usuario debe proporcionar a la aplicación y por lo tanto, las interacciones del usuario con mayor rapidez, más fácil y más preciso. Esto es especialmente cierto porque 'distancia' no es algo que nos estamos acostumbrados a comunicar físicamente a otras personas o equipos. Cuando se señala con nuestro dedo, vamos a especificar una dirección, pero no una distancia.

Una advertencia importante aquí es que cuando una aplicación infiere la distancia desde la dirección (por ejemplo mediante la realización de una raycast a lo largo mirada dirección del usuario buscar más cercano superficie espacial), esto debe producir resultados que el usuario puede prever con exactitud. En caso contrario, el usuario perderá su sentido de control y esto puede volverse rápidamente frustrante. Un método que ayuda en esto es realizar varias raycasts en lugar de uno. Los resultados agregados deben ser más suave y más predecible, menos susceptibles a influir de resultados 'valor 'transitorios atípico (como puede deberse a pasar a través de agujeros diminutos o cuándo llegarán pequeños fragmentos de geometría que el usuario no es consciente de los rayos). También se puede realizar la agregación o suavizado con el tiempo; Por ejemplo puede limitar la velocidad máxima a la que un holograma puede variar en la distancia desde el usuario. También puede ayudar simplemente limitando el valor de distancia mínima y máxima, por lo que el holograma que se va a mover repentinamente no Volar ausente en la distancia o bloquearían en frente al usuario.

Las aplicaciones también pueden usar la forma y la dirección de las superficies de la ubicación de holograma guía. Una silla holográfica no debería penetrar a través de las paredes y debería situarse vaciado con el límite inferior, aunque sea ligeramente desigual. Este tipo de funcionalidad probablemente haría confiar en que el uso de conflictos de leyes físicas, en lugar de simplemente raycasts, problemas semejantes pero se aplicarán. Si el holograma colocado tiene muchos polígonos pequeño que seguir, como las piernas en una silla, lo puede que tenga sentido para expandir la representación física de esos polígonos en algo más anchos y más suave para que sean más capaz de deslizar sobre superficies espaciales sin enganche.

Por su parte, proporcionados por el usuario se pueden simplificar fuera por completo y superficies espaciales pueden usarse para realizar la selección de ubicación holograma completamente automático. Por ejemplo, la aplicación podría poner un conmutador de luz holográfico en algún lugar en la pared para que el usuario presione. Doblemente aquí; se aplica la misma salvedad sobre la capacidad de predicción Si el usuario espera control holograma ubicación, pero la aplicación no coloque siempre hologramas donde esperan (si el interruptor de la luz aparece en algún sitio que el usuario no puede llegar a), esto será una experiencia frustrante. En realidad puede ser peor realizar la selección de ubicación automática que requiere corrección usuario algunas veces, de que solo se requiere al usuario realizar siempre la selección de ubicación; Dado que es la correcta colocación automática *espera*, corrección manual se siente como si una carga!

Tenga en cuenta también que la capacidad de una aplicación para usar superficies espaciales para la selección de ubicación depende en gran medida en la aplicación [análisis experiencia](spatial-mapping-design.md#the-environment-scanning-experience). Si no se ha analizado una superficie, a continuación, no se puede usar para la ubicación. Es responsabilidad de la aplicación para aclarar este punto para el usuario, para que puede ayudar a analizar las superficies de nuevo o seleccione una nueva ubicación.

Los comentarios visuales para el usuario son de vital importancia durante la selección. El usuario tiene que saber dónde está el holograma con respecto a la superficie más cercana con [efectos de toma de tierra](spatial-mapping.md#visualization). Debe entender por qué se está restringiendo el movimiento de su holograma (por ejemplo, debido a la colisión con otra cercana superficie). Si un holograma no pueden colocar en la ubicación actual, a continuación, comentarios visuales deben dejar claro por qué no. Por ejemplo, si el usuario intenta colocar un sofá holográfico atascado mitad de camino en la pared, a continuación, las partes del sofá que están detrás de la pared deben pulsan en un color enfadado. O por el contrario, si la aplicación no encuentra una superficie espacial en una ubicación donde el usuario puede ver una superficie del mundo real, a continuación, la aplicación debería aclarar esto. La ausencia de un efecto de toma de tierra en esta área obvia puede lograr este objetivo.

### <a name="occlusion"></a>Oclusión

Uno de los usos principales de las superficies de asignación espacial es simplemente occlude hologramas. Este comportamiento simple tiene un impacto enorme en el realismo percibido de hologramas, lo que ayuda a crear una sensación visceral que realmente ocupan el mismo espacio físico que el usuario.

Oclusión también proporciona información para el usuario. Cuando un holograma parece que se ocluyeron en una superficie del mundo real, esto proporciona información visual adicional que indique la ubicación espacial de ese holograma en el mundo. Por el contrario, puede también útiles oclusión *ocultar* información del usuario; hologramas occluding detrás de las paredes puede reducir el desorden visual de manera intuitiva. Para mostrar u ocultar un holograma, el usuario simplemente tiene que mover su cabeza.

También puede usarse para preparar las expectativas para una interfaz de usuario natural según interacciones físicas familiares; oclusión Si un holograma se ocluyeron en una superficie es ya que se muestran es sólido, por lo que el usuario debe esperar que realizará el holograma *entren en conflicto* con la superficie y no basta con pasar a través de él.

A veces, no es deseable oclusión de hologramas. Si un usuario debe ser capaz de interactuar con un holograma, que necesitan poder verlo - incluso si está detrás de una superficie del mundo real. En tales casos, normalmente tiene sentido para representar tal un holograma diferente al que se ocluyeron (por ejemplo, en lo que reduce el brillo). De este modo, el usuario será capaz de ubicar visualmente el holograma, pero aún será conscientes de que está detrás de algo.

### <a name="physics"></a>Física

El uso de simulación física es otra forma en que la asignación espacial puede usarse para reforzar el *presencia* de hologramas en espacio físico del usuario. Cuando mi pelota de goma holográfica desplazará mi escritorio de manera realista, rebota en el suelo y desaparece en el sofá, podría ser difícil de creer que no es realmente ahí.

Simulación de leyes físicas también ofrece la oportunidad para una aplicación para usar las interacciones basadas en física naturales y familiares. Mover una pieza de muebles holográfica en torno a en el suelo probablemente será más fácil para el usuario si los muebles responde como si lo estaba deslizante en el piso con la inercia adecuado y fricción.

Para generar los comportamientos físicos realistas, es probable que necesite realizar algunas [mesh procesamiento](spatial-mapping.md#mesh-processing) como rellenar agujeros, quitar flotante alucinaciones y suavizado aproximado superficies.

También necesitará tener en cuenta cómo la aplicación [análisis experiencia](spatial-mapping-design.md#the-environment-scanning-experience) influye en su simulación física. En primer lugar, no entren en conflicto falta superficies con nada; ¿Qué ocurre cuando se implemente la pelota de goma desactivar hacia abajo el corredor y fuera del extremo del mundo conocido? En segundo lugar, debe decidir si continuará responder a cambios en el entorno con el tiempo. En algunos casos, desea responder lo más rápidamente posible; Diga si el usuario está utilizando las puertas y muebles como movible señalización de obras de defensa contra un tempest de flechas Roman entrantes. En otros casos, sin embargo, es posible que desee omitir nuevas actualizaciones; impulsar su automóvil deportivo holográfica alrededor de la pista de carreras en el suelo, de repente, no puede ser tan divertido si decide que el perro se colocan en el medio de la pista.

### <a name="navigation"></a>Navegación

Las aplicaciones pueden usar datos de asignación espacial para conceder a la capacidad de navegar por el mundo real de la misma manera que una persona real sería holográfica caracteres (o agentes). Esto puede ayudar a reforzar la presencia de caracteres holográficas restringiendo el mismo conjunto de comportamientos naturales y conocidos como las del usuario y sus amigos.

Funciones de navegación podrían ser útiles para los usuarios también. Una vez que se ha creado un mapa de navegación en un área determinada, se podría compartir para proporcionar instrucciones holográficas para nuevos usuarios familiarizados con esa ubicación. Esta asignación podría diseñarse para ayudar a mantener peatones '' el flujo del tráfico sin problemas, o para evitar los accidentes en ubicaciones peligrosos como sitios de construcción.

Los principales retos técnicos implicados en la implementación de la funcionalidad de navegación será una detección fiable de superficies transitable (los seres humanos no camine en tablas!) y estable adaptación a los cambios en el entorno (los seres humanos no recorra las puertas cerradas!). La malla puede requerir algunos [procesamiento](spatial-mapping.md#mesh-processing) antes de que se puede utilizar para la navegación por un carácter virtual y el diseño de la ruta de acceso. Suavizado de la malla y quitar alucinaciones pueden ayudar a evitar caracteres bloqueados cada vez. También es posible que desee simplificar drásticamente la malla con el fin de acelerar su carácter planeamiento de ruta de acceso y los cálculos de navegación. Estos desafíos han recibido mucha atención en el desarrollo de tecnología de videojuegos, y hay una gran cantidad de literatura de investigación disponibles en estos temas.

Tenga en cuenta que no se puede usar la funcionalidad integrada de NavMesh en Unity con superficies de asignación espacial. Esto es porque no se conocen las superficies de asignación espacial hasta que la aplicación se inicia, mientras que los archivos de datos de NavMesh deben generarse a partir de componentes de origen antes de tiempo. Tenga en cuenta también que, al sistema de asignación espacial no proporcionará [información acerca de las superficies muy lejos](spatial-mapping-design.md#the-environment-scanning-experience) desde la ubicación del usuario actual. Por lo que la aplicación debe 'recordar' superficies Sí si se van a crear un mapa de un área muy grande.

### <a name="visualization"></a>visualización

La mayoría de los casos es adecuado para las superficies espaciales sea invisible; Para minimizar el desorden visual y dejar que el real world hablen por sí mismos. Sin embargo, a veces es útil visualizar las superficies de asignación espacial directamente, a pesar del hecho de que sus equivalentes en el mundo real ya están visibles.

Por ejemplo, cuando el usuario intenta colocar un holograma hasta una superficie (colocación de un archivador holographic en la pared, por ejemplo) puede resultar útil a masa el holograma al convertir una sombra a la superficie. Esto proporciona al usuario una idea mucho más clara de la proximidad física exacta entre el holograma y la superficie. También es un ejemplo de la práctica más general de visualmente 'vista previa de' un cambio antes de que el usuario se confirma en él.

Mediante la visualización de las superficies, la aplicación puede compartir con el usuario, su comprensión del entorno. Por ejemplo, un juego de mesa holográfico pudiera visualizar las superficies horizontales que ha identificado como "tablas", para que el usuario sepa dónde debe ir para interactuar.

Visualización de las superficies de puede ser una manera útil para mostrar al usuario cercanas espacios que están ocultos de la vista. Esto puede proporcionar una manera sencilla de proporcionar al usuario acceso a su cocina (y todos sus contenidos hologramas) de su sala de estar.

Las mallas de superficie proporcionadas por asignación espacial no pueden ser especialmente "limpias". Por lo tanto es importante visualizarlos de manera adecuada. Cálculos de iluminación tradicional pueden resaltar errores en las normales de superficie de una manera visualmente confuso, mientras se proyectan en la superficie de texturas "limpias" pueden ayudar a darle un aspecto más limpio. También es posible realizar [mesh procesamiento](spatial-mapping.md#mesh-processing) para mejorar las propiedades de la malla, antes de que se representan las superficies.

## <a name="using-the-surface-observer"></a>Utilizando el observador de superficie

El punto de partida para la asignación espacial es el observador de superficie. Flujo del programa es como sigue:
* Crear un objeto observador de superficie
   * Proporcionar uno o más volúmenes espaciales, para definir las áreas de interés en el que la aplicación desea recibir datos de asignación espacial. Un volumen espacial es simplemente una forma de definir una región de espacio, como una esfera o cuadro.
   * Usar un volumen espacial con un sistema de coordenadas espacial bloqueado por el mundo para identificar una región del mundo físico fija.
   * Uso de un volumen espacial, actualizado para cada fotograma con un cuerpo bloqueado espacial sistema de coordenadas, para identificar una región de espacio que se mueve (pero no se gira) con el usuario.
   * Estos volúmenes espaciales pueden cambiarse más adelante en cualquier momento, como el estado de la aplicación o el usuario cambia.
* Usar sondeo o notificación para recuperar información acerca de las superficies espaciales
   * Es posible que 'sondea' el observador de superficie para el estado de superficie espacial en cualquier momento. Como alternativa, puede registrarse para eventos del observador expuesta 'superficies cambiado', que notifique a la aplicación cuando han cambiado las superficies espaciales.
   * Para un volumen dinámico espacial, como frustum de vista, o un volumen bloqueado por el cuerpo, las aplicaciones debe sondear en busca de cambios cada fotograma mediante el establecimiento de la región de interés y, a continuación, obtener el conjunto actual de superficies espaciales.
   * Para un volumen estático, como un cubo bloqueado por el mundo que abarcan una habitación individual, pueden registrar las aplicaciones para que el evento 'superficies cambiado' recibir una notificación cuando pueden haber cambiado superficies espaciales dentro de ese volumen.
* Cambios de las superficies de procesos
   * Recorrer en iteración el conjunto proporcionado de superficies espaciales.
   * Clasificar espaciales superficies como se ha agregado, cambiado o quitado.
   * Para cada superficie espacial han agregado o modificado, si es necesario enviar una solicitud asincrónica para recibir la malla actualizada que representa el estado actual de la superficie en el nivel de detalle deseado.
* Procesar la solicitud asincrónica de malla (más detalles en las secciones siguientes).

## <a name="mesh-caching"></a>Almacenamiento en caché de malla

Las superficies espaciales se representan mediante mallas de triangulares densa. Almacenar, procesar y procesar estos mallas pueden consumir importantes recursos de cálculo y almacenamiento. Por lo tanto, cada aplicación debe adoptar una malla de almacenamiento en caché de esquema adecuado para sus necesidades, con el fin de minimizar los recursos utilizados para el almacenamiento y procesamiento de la malla. Este esquema debe determinar que mallas para conservar y cuáles se deben descartar, así como cuándo se debe actualizar la malla para cada superficie espacial.

Muchas de las consideraciones que se ha tratado informará directamente cómo la aplicación debe aproximarse al almacenamiento en caché de malla. Debe considerar cómo el usuario se mueve a través del entorno, se necesitan las superficies que, cuando se observará los diferentes tipos de superficies y cuándo se deben capturar los cambios en el entorno.

Al interpretar el evento 'superficies cambiado' proporcionado por el observador expuesto, la lógica de almacenamiento en caché de malla básica es el siguiente:
* Si la aplicación ve un identificador de superficie espacial que no ha visto antes, debería tratarlo como una nueva superficie espacial.
* Si la aplicación ve una superficie espacial con un identificador conocido, pero con una nueva hora de actualización, debería tratarlo como una superficie espacial actualizada.
* Si la aplicación ya no ve una superficie espacial con un identificador conocido, debería tratarlo como una superficie espacial quitada.

Depende de cada aplicación para, a continuación, realice las siguientes selecciones:
* ¿Para las superficies espaciales nuevo, se debe solicitar malla?
   * Por lo general se debe solicitar malla inmediatamente para nuevas superficies espaciales, que pueden proporcionar información útil de nuevo al usuario.
   * Sin embargo, nuevas superficies espaciales cerca de y delante del usuario deben tener prioridad y se debe solicitar primero su malla.
   * Si no es necesaria la malla nuevo, si por ejemplo la aplicación ha permanente o temporalmente 'inmoviliza' su modelo del entorno, a continuación, debe no ser solicitados.
* ¿Para las superficies espaciales actualizadas, se debe solicitar malla?
   * Superficies espaciales actualizadas cerca de y delante del usuario deben tener prioridad y se debe solicitar primero su malla.
   * También puede ser adecuado dar prioridad a nuevas superficies que al actualizar las superficies, especialmente durante la experiencia de exploración.
   * Para limitar los costos de procesamiento, las aplicaciones que desee limitar la velocidad a la que procesan las actualizaciones de las superficies espaciales.
   * Es posible deducir que son menores, por ejemplo, si los límites de la superficie son pequeños, en cuyo caso la actualización puede no ser lo suficientemente importante como para procesar los cambios realizados en una superficie espacial.
   * Las actualizaciones de las superficies espaciales fuera de la región de interés del usuario actual se pueden omitir por completo, aunque en este caso puede ser más eficaz para modificar los volúmenes de delimitadores espaciales usando el observador de superficie.
* ¿Para las superficies espaciales quitadas, debe descartarse malla?
   * Por lo general malla debe descartarse inmediatamente para las superficies espaciales quitadas, para que permanezca correcta oclusión holograma.
   * Sin embargo, si la aplicación tiene motivos para creer que una superficie espacial volverá a aparecer en breve (quizás basándose en el diseño de la experiencia del usuario), a continuación, puede ser más eficaz para conservarlo que to descartar su malla y crearla de nuevo más tarde.
   * Si la aplicación está creando un modelo a gran escala del entorno de usuario es posible que no quiere descartar las mallas en absoluto. Todavía será necesario limitar el uso de recursos sin embargo, posiblemente mediante mallas de puesta en cola en el disco como superficies espaciales desaparecen.
   * Tenga en cuenta que algunos eventos durante la generación de superficie espacial relativamente poco frecuentes pueden causar espaciales superficies será sustituido por nuevas superficies espaciales en una ubicación similar pero con distintos identificadores. Por lo tanto, las aplicaciones que elija no para descartar una superficie quitada procure no final copia con varios superpuesta altamente espaciales expuestas mallas que abarcan la misma ubicación.
* ¿Debe descartarse malla para otras superficies espaciales?
   * Aunque existe una superficie espacial, si ya no es útil para la experiencia del usuario, a continuación, debe descartarse. Por ejemplo, si la aplicación "reemplaza" la habitación en el otro lado de una puerta de entrada con un espacio virtual alternativo, a continuación, las superficies espaciales en ese espacio ya no importan.

Aquí es una ejemplo malla estrategia almacenamiento en caché, mediante histéresis espaciales y temporales:
* Considere una aplicación que quiera utilizar un volumen en forma de frustum espacial de interés que sigue la mirada del usuario que parezcan y andar.
* Una superficie espacial puede desaparecer temporalmente de este volumen simplemente porque el usuario busca lejos de la superficie o pasos adicionales fuera de él... solo para mirar hacia atrás o se mueve cerca de nuevo más tarde unos instantes. En este caso, descartando y volver a crear la malla para esta superficie representan una gran cantidad de procesamiento de redundante.
* Para reducir el número de cambios procesados, la aplicación usa dos observadores superficies espaciales, uno dentro de la otra. El volumen más grande es esférico y sigue el usuario 'forma diferida;' solo se mueve cuando sea necesario para garantizar que su centro está en 2,0 metros del usuario.
* Siempre se procesan en nuevas y actualizadas mallas de superficie espaciales desde el observador superficie interno más pequeño, pero las mallas se almacenan en caché hasta que éstas desaparecen del observador superficie externo más grande. Esto permite que la aplicación evitar el procesamiento de muchos cambios redundantes debido al movimiento de usuario local.
* Puesto que una superficie espacial también puede desaparecer temporalmente debido a la pérdida de seguimiento, la aplicación también aplaza descartar superficies espaciales quitadas durante el seguimiento de la pérdida.
* En general, una aplicación debe evaluar el equilibrio entre el proceso de actualización menor y mayor uso de memoria para determinar su estrategia de almacenamiento en caché ideal.

## <a name="rendering"></a>Representación

Hay tres formas principales en el que las mallas de asignación espacial tienden a ser utilizadas para la representación:
* Para la visualización de superficie
   * A menudo resulta útil visualizar las superficies espaciales directamente. Por ejemplo, conversión 'shadows' de los objetos en superficies espaciales pueden proporcionar comentarios visuales útiles al usuario mientras coloca en superficies hologramas.
   * Una cosa a tener en cuenta es que las mallas espaciales son diferentes para el tipo de las mallas que podría crear un intérprete en 3D. La topología de triángulo no será tan 'Limpiar' como topología creados por humanos y la malla se verá afectado de [varios errores](spatial-mapping-design.md#what-influences-spatial-mapping-quality).
   * Para crear una estética visual agradable, es posible que, por tanto, desea realizar algunas [mesh procesamiento](spatial-mapping.md#mesh-processing), por ejemplo a vulnerabilidades de relleno o smooth normales de superficie. También es posible que desee usar a un sombreador a las texturas diseñado por el intérprete de proyecto en la malla en lugar de visualizar directamente la topología de malla y las normales.
* Para occluding hologramas tras las superficies del mundo real
   * Superficies espaciales se pueden representar en una fase de profundidad que solo afecta a la [búfer de profundidad](https://msdn.microsoft.com/library/windows/desktop/bb219616(v=vs.85).aspx) y no afecta a los destinos de representación de color.
   * Esto prepara el búfer de profundidad para occlude representan posteriormente hologramas tras las superficies espaciales. Precisa oclusión de hologramas mejora el sentido de que realmente existen hologramas dentro del espacio físico del usuario.
   * Para habilitar la representación sólo profundidad, actualice su estado de mezcla para establecer el [RenderTargetWriteMask](https://msdn.microsoft.com/library/windows/desktop/hh404492(v=vs.85).aspx) en cero para el color de todos los destinos de representación.
* Para modificar la apariencia de hologramas ocluidos en superficies del mundo real
   * Geometría representado normalmente está oculto cuando se es ocluido. Esto se consigue estableciendo la función de profundidad su [estado de la Galería de símbolos de profundidad](https://msdn.microsoft.com/library/windows/desktop/ff476110(v=vs.85).aspx) a "menor o igual", lo que hace que la geometría sea visible sólo cuando sea **más de cerca** a la cámara que todos se representan previamente geometría.
   * Sin embargo, puede ser útil para mantener determinado geometría visible incluso cuando se está ocluido y modificar su apariencia cuando ocluidos como una manera de proporcionar comentarios visuales al usuario. Por ejemplo, esto permite que la aplicación mostrar al usuario la ubicación de un objeto mientras lo que claramente que está detrás de una superficie del mundo real.
   * Para lograr esto, se representan la geometría de una segunda vez con un sombreado diferente que crea la apariencia deseada 'occluded'. Antes de procesar la geometría por segunda vez, realizar dos cambios en su [estado de la Galería de símbolos de profundidad](https://msdn.microsoft.com/library/windows/desktop/ff476110(v=vs.85).aspx). En primer lugar, Establece la función de profundidad en "mayor o igual que" para que la geometría verá sólo cuando sea **más** desde la cámara que toda la geometría procesada anteriormente. En segundo lugar, establezca el DepthWriteMask a cero, por lo que no se modificará el búfer de profundidad (el búfer de profundidad debe continuar representar la profundidad de la geometría **más cercano** a la cámara).

[Rendimiento](understanding-performance-for-mixed-reality.md) es una preocupación importante al representar las mallas de asignación espacial. Estas son algunas técnicas de rendimiento de representación específica para representar las mallas de asignación espacial:
* Ajustar la densidad de triángulo
   * Cuando el solicitante superficie espacial mallas de su superficie observador, solicitar la menor densidad de mallas de triangulares será suficiente para sus necesidades.
   * Puede que tenga sentido para variar la densidad de triángulo en una base de superficie por superficie, dependiendo de la distancia de la superficie del usuario y su importancia para la experiencia del usuario.
   * Recuentos de triángulo que se reducen reducirá el uso de memoria y los costos de procesamiento de vértices en la GPU, aunque no afectará a los costos de procesamiento de píxeles.
* Realizar frustum caras traseras
   * Caras traseras frustum omite los objetos de dibujo que no estén visibles porque están fuera del frustum de visualización actual. Esto reduce los costos de procesamiento de CPU y GPU.
   * Puesto que la selección se realiza en una base por cada malla y superficies espaciales pueden ser grandes, divide cada malla de superficie espacial en fragmentos más pequeños puede producir más eficaz de caras traseras (en que se representan menos triángulos fuera de la pantalla). Hay una desventaja, sin embargo; las mallas más que tiene, las llamadas de dibujo más debe realizar, lo que pueden aumentar los costos de CPU. En casos extremos, la frustum caras traseras cálculos propios incluso podría tener un costo de CPU puede medir.
* Ajustar el orden de procesamiento
   * Las superficies espaciales tienden a ser grandes, ya que representan todo el entorno del usuario a su alrededor. Los costos en la GPU de procesamiento de píxeles, por tanto, pueden ser elevado, especialmente en casos donde hay más de una capa de geometría visible (incluidas las superficies espaciales y otros hologramas). En este caso, la capa más cercana al usuario se se occluding aún más las capas, por lo que se desperdicia GPU el tiempo dedicado a procesar esas capas más lejanos.
   * Para reducir este trabajo redundante en la GPU, ayuda a presentar superficies opacas en orden de delante hacia atrás (los más de cerca en primer lugar, más alejados de los últimos). Por 'opaque' nos referimos a las superficies para el que el DepthWriteMask se establece en uno de sus [estado de la Galería de símbolos de profundidad](https://msdn.microsoft.com/library/windows/desktop/ff476110(v=vs.85).aspx). Cuando se representan las superficies más cercanos, desbloquear el búfer de profundidad para que las superficies más lejanos se omiten eficazmente por el procesador de píxel en la GPU.

## <a name="mesh-processing"></a>Procesamiento de malla

Una aplicación puede realizar [varias operaciones](spatial-mapping.md#mesh-processing) en mallas de superficie espaciales para satisfacer sus necesidades. Los datos de índice y del vértice proporcionados con cada malla de superficie espacial usan el mismo diseño familiar que el [búferes de vértices e índice](https://msdn.microsoft.com/library/windows/desktop/bb147325%28v=vs.85%29.aspx) que se usan para representar las mallas de triangulares en representación moderno todas las API. Sin embargo, un hecho clave a tener en cuenta es que los triángulos asignación espacial tienen un **front-hacia la derecha orden de devanado**. Cada triángulo se representa mediante tres índices de vértices en el búfer de índice de la malla y estos índices identificará los vértices del triángulo en un **hacia la derecha** orden cuando se ve el triángulo de la **front** lado. La parte delantera en paralelo (o exterior) de mallas de superficie espaciales corresponde como cabría esperar a la parte frontal (visible) de las superficies del mundo real.

Las aplicaciones deben realizar solo simplificación de la malla si la densidad de triángulo menos detallada proporcionada por la superficie observador es todavía insuficientemente general - este trabajo es consumen muchos recursos y ya no se realice el tiempo de ejecución para generar los distintos proporciona niveles de detalle.

Dado que cada observador expuesta puede proporcionar varias superficies espaciales desconectadas, algunas aplicaciones que desee recortar estos espacial superficie mallas con cada símbolo de compresión otro, a continuación, ellos juntos. En general, el paso de recorte es necesario que cercanas mallas de superficie espaciales a menudo se superpongan ligeramente.

## <a name="raycasting-and-collision"></a>Detalles y colisión

En orden para una API de leyes físicas (como [Havok](http://www.havok.com/)) para proporcionar una aplicación con funcionalidad de detalles y colisión para superficies espaciales, la aplicación debe proporcionar la superficie espacial mallas a la API de física. Las mallas que se usan con frecuencia para física tienen las siguientes propiedades:
* Contienen solo un número reducido de triángulos. Las operaciones de leyes físicas son más intensivas que las operaciones de representación.
* Son 'agua estrecha'. Las superficies que pretende ser sólido no deberían tener pequeñas orificios; incluso agujeros demasiado pequeños para ser visible pueden causar problemas.
* Se convierten en cáscaras convexas. Cáscaras convexos tienen pocos polígonos y libres de vulnerabilidades, y son computacionalmente mucho más eficaces para procesar de mallas de triángulo sin procesar.

Cuando raycasts rendimiento frente a las superficies espaciales, tenga en cuenta que estas superficies a menudo son complejas, formas desordenadas llenos de detalles poco desorganizados - simplemente como su escritorio! Esto significa que un único raycast a menudo es insuficiente para proporcionar suficiente información sobre la forma de la superficie y la forma del espacio vacío cerca de ella. Normalmente, por tanto, es una buena idea realizar muchos raycasts dentro de un área pequeña y a usar los resultados agregados para derivar un conocimiento más confiable de la superficie. Por ejemplo, utilizando el promedio de 10 raycasts guía holograma ubicación en una superficie producirá un resultado mucho más suave y menos 'nerviosos' que utilizando solo un único raycast.

Sin embargo, tenga en cuenta que cada raycast puede tener un alto costo computacional. Por tanto, según el escenario de uso que debe sacrificar el costo computacional de raycasts adicionales (se realiza cada fotograma) contra el costo computacional de [mesh procesamiento](spatial-mapping.md#mesh-processing) para suavizar y quitar agujeros en superficies espaciales ( realiza cuando se actualizan las mallas espaciales).

## <a name="troubleshooting"></a>Solución de problemas
* Para las mallas expuestas se oriente correctamente, cada GameObject debe estar activo antes de enviarlo a la SurfaceObeserver tener su malla construido. En caso contrario, las mallas se mostrarán en tu espacio, pero se ha girado en ángulos extraños.
* El GameObject que se ejecuta la secuencia de comandos que se comunica con el SurfaceObserver debe establecerse en el origen. De lo contrario, todos GameObjects que crear y enviar a la SurfaceObserver tener sus mallas construidas tendrán un desplazamiento igual que el desplazamiento del objeto de juego primario. Esto puede hacer que su mallas se muestran varios medidores distancia que resulta muy difícil depurar lo que está ocurriendo.

## <a name="see-also"></a>Vea también
* [Sistemas de coordenadas](coordinate-systems.md)
* [Asignación espacial en DirectX](spatial-mapping-in-directx.md)
* [Asignación espacial en Unity](spatial-mapping-in-unity.md)
* [Diseño de la asignación espacial](spatial-mapping-design.md)
* [Caso práctico: examinar los huecos en la realidad](case-study-looking-through-holes-in-your-reality.md)
