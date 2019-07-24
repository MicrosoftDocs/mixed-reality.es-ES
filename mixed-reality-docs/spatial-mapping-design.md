---
title: Diseño de asignación espacial
description: El uso eficaz de la asignación espacial en HoloLens requiere una consideración cuidadosa de muchos factores.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, diseño, asignación espacial, HoloLens, reconstrucción superficial, malla
ms.openlocfilehash: 451213a79e1d482d64725ce750065611830beec3
ms.sourcegitcommit: 17f86fed532d7a4e91bd95baca05930c4a5c68c5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2019
ms.locfileid: "66829959"
---
# <a name="spatial-mapping-design"></a>Diseño de asignación espacial

El uso eficaz de la asignación espacial en HoloLens requiere una consideración cuidadosa de muchos factores.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><strong>Característica</strong></td>
        <td><a href="hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="immersive-headset-hardware-details.md"><strong>Cascos envolventes</strong></a></td>
    </tr>
     <tr>
        <td>Diseño de asignación espacial</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="why-is-spatial-mapping-important"></a>¿Por qué es importante la asignación espacial?

La asignación espacial permite colocar objetos en superficies reales. Esto ayuda a anclar objetos en el mundo del usuario y saca partido de las pilas reales del mundo. Occluding los hologramas basados en otros hologramas y los objetos del mundo real ayudan a convencer al usuario de que estos hologramas están realmente en su espacio. Los hologramas flotan en el espacio o se mueven con el usuario no se verán como reales. Cuando sea posible, coloque los elementos para mayor comodidad.

Visualizar las superficies al colocar o mover hologramas (usar una cuadrícula proyectada simple). Esto le ayudará al usuario a saber dónde pueden colocar mejor sus hologramas y muestra al usuario si el lugar en el que intentan colocar el holograma todavía no se ha asignado. Puede "elementos de la cartelera" hacia el usuario si acaba en demasiados de un ángulo.

## <a name="what-influences-spatial-mapping-quality"></a>¿Qué influye en la calidad de la asignación espacial?

Con el fin de proporcionar la mejor experiencia de usuario, es importante comprender los factores que afectan a la calidad de los datos de asignación espacial recopilados por HoloLens.

Los errores en los datos de asignación espacial se dividen en una de estas tres categorías:
* **Agujeros**: Faltan las superficies del mundo real en los datos de asignación espacial.
* **Hallucinations**: Existen superficies en los datos de asignación espacial que no existen en el mundo real.
* **Bias**: Las superficies en los datos de asignación espacial se alinean imperfectamente con las superficies del mundo real, ya sean insertadas o extraídas.

Varios factores pueden afectar a la frecuencia y la gravedad de estos errores:

* **Movimiento de usuarios**
   * La forma en que el usuario se mueve a través de su entorno determina en qué medida se examinará el entorno, por lo que el usuario puede requerir orientación para lograr un buen examen.
   * La cámara utilizada para el análisis proporciona datos dentro de un cono de 70 grados, desde un mínimo de 0,8 metros hasta un máximo de 3,1 metros de distancia desde la cámara. Las superficies del mundo real solo se examinarán dentro de este campo de vista. Tenga en cuenta que estos valores están sujetos a cambios en versiones futuras.
   * Si el usuario nunca obtiene en 3,1 metros de un objeto, no se examinará.
   * Si el usuario solo ve un objeto a partir de una distancia inferior a 0,8 metros, no se examinará (Esto evitará el examen de las manos del usuario).
   * Si el usuario no busca nunca (que es bastante normal), es probable que el límite superior no se analice.
   * Si un usuario no busca nunca en el mobiliario o en una pared, no se examinarán los objetos que ocluidos.
   * Las superficies tienden a analizarse con una calidad más alta cuando se ven como cabezales y no en un ángulo superficial.
   * Si se produce un error en el sistema de seguimiento de los cabezales de HoloLens momentáneamente (lo que puede suceder debido a un movimiento de usuario rápido, una iluminación deficiente, paredes sin características o las cámaras que se están analizando), esto puede introducir errores en los datos de asignación espacial. Estos errores se corregirán con el tiempo a medida que el usuario siga desplazando y examinando el entorno.

* **Materiales de superficie**
   * Los materiales que se encuentran en las superficies del mundo real varían en gran medida. Estos afectan a la calidad de los datos de asignación espacial porque afectan al modo en que se refleja la luz de infrarrojos.
   * Es posible que las superficies oscuras no digitalicen hasta que estén más cerca de la cámara, ya que reflejan menos luz.
   * Algunas superficies pueden ser tan oscuras que reflejan demasiado poca luz para su análisis desde cualquier distancia, por lo que introducirán errores de orificio en la ubicación de la superficie y, en ocasiones, también detrás de la superficie.
   * Las superficies especialmente brillantes solo pueden escanear cuando se ve el cabezal y no cuando se ven desde un ángulo superficial.
   * Reflejos, ya que crean reflexiones de illusory de espacios y superficies reales, pueden producir errores de orificio y errores de Hallucination.

* **Movimiento de la escena**
   * La asignación espacial se adapta rápidamente a los cambios en el entorno, como mover personas o abrir y cerrar puertas.
   * Sin embargo, la asignación espacial solo puede adaptarse a los cambios en un área cuando esa área está claramente visible para la cámara que se usa para el examen.
   * Por este motivo, es posible que esta adaptación se retrase con la realidad, lo que puede provocar errores de orificio o Hallucination.
   * Por ejemplo, un usuario examina un amigo y luego se enciende mientras el amigo deja la habitación. Una representación "fantasma" del amigo (un error de Hallucination) se conservará en los datos de asignación espacial, hasta que el usuario vuelva a examinar el espacio en el que estaba el amigo.

* **Interferencia de iluminación**
   * La luz de infrarrojos ambiente de la escena puede interferir con el análisis, por ejemplo, una luz solar fuerte que llega a través de una ventana.
   * Las superficies especialmente brillantes pueden interferir con el análisis de las superficies cercanas, la luz que los rebotan causan errores de sesgo.
   * Las superficies brillantes que reflejen la luz directamente en la cámara pueden interferir con el espacio cercano, ya sea provocando hallucinations de aire flotante o retrasando la adaptación al movimiento de la escena.
   * Dos dispositivos HoloLens en la misma habitación no deberían interferir entre sí, pero la presencia de más de cinco dispositivos HoloLens puede producir interferencias.

Puede que sea posible evitar o corregir algunos de estos errores. Sin embargo, debe diseñar la aplicación para que el usuario pueda alcanzar sus objetivos incluso en presencia de errores en los datos de asignación espacial.

## <a name="the-environment-scanning-experience"></a>La experiencia de análisis del entorno

HoloLens aprende las superficies de su entorno a medida que el usuario las examina. Con el tiempo, HoloLens crea un examen de todas las partes del entorno que se han observado. También actualiza el análisis a medida que se observan los cambios en el entorno. Este examen se conservará automáticamente entre los lanzamientos de la aplicación.

Cada aplicación que utiliza la asignación espacial debe considerar la posibilidad de proporcionar una experiencia de exploración. el proceso a través del cual la aplicación guía al usuario para que examine las superficies necesarias para que la aplicación funcione correctamente.

![Ejemplo de análisis](images/sr-mixedworld-140429-8pm-00068-1000px.png)<br>
*Ejemplo de análisis*

La naturaleza de esta experiencia de análisis puede variar en gran medida en función de las necesidades de cada aplicación, pero dos principios principales deben guiar su diseño.

En primer lugar, **la comunicación clara con el usuario es la principal preocupación**. El usuario siempre debe tener en cuenta si se cumplen los requisitos de la aplicación. Cuando no se cumplan, se debe aclarar inmediatamente al usuario por qué es así y se debe llevar a cabo rápidamente para realizar la acción adecuada.

En segundo lugar, **las aplicaciones deben intentar lograr un equilibrio entre la eficacia y la confiabilidad**. Cuando sea posible hacerlo de manera **confiable**, las aplicaciones deben analizar automáticamente los datos de asignación espacial para ahorrar tiempo al usuario. Cuando no es posible hacerlo de manera confiable, las aplicaciones deben permitir que el usuario proporcione rápidamente la aplicación con la información adicional que requiere.

Para ayudar a diseñar la experiencia de examen adecuada, tenga en cuenta cuál de las siguientes posibilidades es aplicable a su aplicación:

* **Sin experiencia de exploración**
   * Una aplicación puede funcionar perfectamente sin ninguna experiencia de exploración guiada; obtendrá información sobre las superficies observadas en el transcurso del movimiento natural de usuarios.
   * Por ejemplo, una aplicación que permite al usuario dibujar en superficies con Holographic SprayPaint requiere conocer solo las superficies visibles actualmente para el usuario.
   * El entorno se puede examinar por completo ya si es uno en el que el usuario ya ha pasado mucho tiempo mediante HoloLens.
   * Sin embargo, tenga en cuenta que la cámara usada por la asignación espacial solo puede ver 3.1 m delante del usuario, por lo que la asignación espacial no conocerá las superficies más lejanas a menos que el usuario las haya observado desde una distancia más cercana en el pasado.
   * Por lo tanto, el usuario entiende qué superficies se han examinado, la aplicación debe proporcionar comentarios visuales a este efecto; por ejemplo, la conversión de sombras virtuales en superficies digitalizadas puede ayudar al usuario a colocar hologramas en esas superficies.
   * En este caso, los volúmenes de límite del observador de la superficie espacial deben actualizarse cada fotograma a un [sistema de coordenadas espaciales](coordinate-systems.md)bloqueado por el cuerpo para que sigan el usuario.

* **Buscar una ubicación adecuada**
   * Una aplicación puede estar diseñada para su uso en una ubicación con requisitos específicos.
   * Por ejemplo, la aplicación puede requerir un área vacía alrededor del usuario para que pueda practicar con seguridad Holographic Kung.
   * Las aplicaciones deben comunicar cualquier requisito específico al usuario por adelantado y reforzarlos con comentarios visuales claros.
   * En este ejemplo, la aplicación debe visualizar el alcance del área vacía necesaria y resaltar visualmente la presencia de cualquier objeto no deseado dentro de esta zona.
   * En este caso, los volúmenes de límite del observador de superficie espacial deben usar un sistema de [coordenadas espaciales](coordinate-systems.md) de bloque mundial en la ubicación elegida.

* **Buscar una configuración adecuada de surfaces**
   * Una aplicación puede requerir una configuración específica de superficies, por ejemplo dos paredes grandes, planas y opuestas para crear un salón de reflejos.
   * En tales casos, la aplicación tendrá que analizar las superficies proporcionadas por la asignación espacial para detectar las superficies adecuadas y dirigir al usuario hacia ellas.
   * El usuario debe tener una opción de reserva si el análisis de la superficie de la aplicación no es totalmente confiable. Por ejemplo, si la aplicación identifica incorrectamente una puerta como una pared plana, el usuario necesita una forma sencilla de corregir este error.

* **Examinar parte del entorno**
   * Una aplicación puede querer capturar solo parte del entorno, tal como la dirige el usuario.
   * Por ejemplo, la aplicación examina parte de una habitación para que el usuario pueda publicar un anuncio de la clasificación holográfica para el mobiliario que desea vender.
   * En este caso, la aplicación debe capturar los datos de asignación espacial dentro de las regiones observadas por el usuario durante el examen.

* **Examinar toda la habitación**
   * Una aplicación puede requerir un examen de todas las superficies de la habitación actual, incluidas las que están detrás del usuario.
   * Por ejemplo, un juego puede poner al usuario en el rol de Gulliver, en Siege desde cientos de pequeñas Lilliputianss que se aproximan desde todas las direcciones.
   * En tales casos, la aplicación necesitará determinar cuántas de las superficies de la habitación actual ya se han analizado y dirigir la mirada del usuario para rellenar los huecos significativos.
   * La clave de este proceso consiste en proporcionar comentarios visuales que le permitan aclarar al usuario qué superficies todavía no se han analizado. Por ejemplo, la aplicación podría usar la [niebla basada en distancia](https://msdn.microsoft.com/library/windows/desktop/bb173401%28v=vs.85%29.aspx) para resaltar visualmente las regiones que no están tratadas por superficies de asignación espacial.

* **Tomar una instantánea inicial del entorno**
   * Una aplicación puede querer omitir todos los cambios en el entorno después de tomar una "instantánea" inicial.
   * Esto puede ser adecuado para evitar la interrupción de los datos creados por el usuario que están estrechamente acoplados al estado inicial del entorno.
   * En este caso, la aplicación debe realizar una copia de los datos de asignación espacial en su estado inicial una vez completado el examen.
   * Las aplicaciones deben seguir recibiendo actualizaciones de los datos de asignación espacial si el entorno sigue ocluidos correctamente.
   * Las actualizaciones continuas de los datos de asignación espacial también permiten visualizar cualquier cambio que se haya producido, con lo que se aclara al usuario las diferencias entre los Estados anterior y actual del entorno.

* **Realizar instantáneas iniciadas por el usuario del entorno**
   * Una aplicación solo puede querer responder a los cambios del entorno cuando lo indique el usuario.
   * Por ejemplo, el usuario podría crear varios "statues" de un amigo al capturar sus supuestos en momentos diferentes.

* **Permitir al usuario cambiar el entorno**
   * Una aplicación puede estar diseñada para responder en tiempo real a los cambios realizados en el entorno del usuario.
   * Por ejemplo, el usuario que dibuja una cortina podría desencadenar ' cambio de escena ' para una reproducción holográfica en el otro lado.

* **Guiar al usuario para evitar errores en los datos de asignación espacial**
   * Una aplicación puede querer proporcionar orientación al usuario mientras examina su entorno.
   * Esto puede ayudar al usuario a evitar ciertos tipos de [errores en los datos de la asignación espacial](spatial-mapping-design.md#what-influences-spatial-mapping-quality), por ejemplo, alejándose de las ventanas o los reflejos de sunlit.

Un detalle adicional que se debe tener en cuenta es que el "intervalo" de datos de asignación espacial no es ilimitado. Mientras que la asignación espacial crea una base de datos permanente de espacios grandes, solo hace que los datos estén disponibles para las aplicaciones en una "burbuja" de tamaño limitado alrededor del usuario. Por lo tanto, si comienza al principio de un corredor largo y se aleja de la partida, las superficies espaciales de vuelta al principio desaparecerán. Por supuesto, puede mitigar esto si almacena en caché esas superficies en la aplicación después de que hayan desaparecido de los datos de asignación espacial disponibles.

## <a name="mesh-processing"></a>Procesamiento de mallas

Puede ayudar a detectar tipos comunes de errores en las superficies y filtrar, quitar o modificar los datos de asignación espacial según corresponda.

Tenga en cuenta que los datos de la asignación espacial están diseñados para ser lo más fieles posible a las superficies del mundo real, por lo que cualquier procesamiento que aplique a los riesgos que desplacen las superficies más allá de la "verdad".

Estos son algunos ejemplos de los diferentes tipos de procesamiento de mallas que puede encontrar útiles:

* **Relleno de huecos**
   * Si se produce un error al digitalizar un pequeño objeto de un material oscuro, dejará un hueco en la superficie circundante.
   * Los huecos afectan a la oclusión: los hologramas se pueden visualizar "a" en una superficie real supuestamente opaca.
   * Los huecos afectan a raycasts: Si usa raycasts para ayudar a los usuarios a interactuar con las superficies, puede que no sea deseable que estos rayos pasen por los huecos. Una mitigación consiste en usar una agrupación de varios raycasts que cubran una región de tamaño adecuado. Esto le permitirá filtrar los resultados de ' atípico ', de modo que incluso si un Raycast pasa a través de un orificio pequeño, el resultado del agregado seguirá siendo válido. Sin embargo, tenga en cuenta que este enfoque se refiere a un costo computacional.
   * Los huecos afectan a las colisiones físicas: un objeto controlado por la simulación física puede desplazarse a través de un orificio en el suelo y perderse.
   * Es posible rellenar de forma algorítmica estos huecos en la malla de superficie. Sin embargo, tendrá que ajustar el algoritmo para que no se rellenen "agujeros reales", como ventanas y puertas. Puede ser difícil diferenciar de ' agujeros reales ' de ' agujeros imaginarios ' de forma confiable, por lo que tendrá que experimentar con distintas heurísticas, como ' tamaño ' y ' forma límite '.

* **Eliminación de Hallucination**
   * Las reflexiones, las luces brillantes y los objetos móviles pueden dejar un pequeño "hallucinations" flotante en el aire medio.
   * Hallucinations afectar a la oclusión: Hallucinations puede ser visible como formas oscuras que se mueven delante y occluding otros hologramas.
   * Hallucinations afectan a raycasts: Si está usando raycasts para ayudar a los usuarios a interactuar con las superficies, estos rayos podrían alcanzar un Hallucination en lugar de la superficie detrás. Al igual que con los huecos, una mitigación consiste en usar muchos raycasts en lugar de un único Raycast, pero de nuevo esto supondrá un costo computacional.
   * Hallucinations afectan a las colisiones físicas: un objeto controlado por la simulación física puede quedar atascado contra un Hallucination y no puede desplazarse por un área de espacio aparentemente despejada.
   * Es posible filtrar este hallucinations de la malla de superficie. Sin embargo, al igual que con los huecos, tendrá que ajustar el algoritmo para que no se eliminen los objetos pequeños, como los soportes y los controladores de las puertas.

* **Suavizado**
   * La asignación espacial puede devolver superficies que parezcan aproximadas o ' ruidoso ' en comparación con sus homólogos del mundo real.
   * La suavidad afecta a las colisiones físicas: Si el piso es rugoso, es posible que una bola de golf simulada físicamente no se revierta sin problemas en una línea recta.
   * La suavidad afecta a la representación: Si una superficie se visualiza directamente, las normales de superficie rugosa pueden afectar a su apariencia e interrumpir el aspecto "limpio". Es posible mitigarlo mediante la iluminación y las texturas adecuadas en el sombreador que se usa para representar la superficie.
   * Es posible suavizar la rugosidad en una malla de superficie. Sin embargo, esto puede extender la superficie fuera de la superficie del mundo real correspondiente. Es importante mantener una correspondencia estrecha para producir una oclusión de holograma precisa y permitir a los usuarios lograr interacciones precisas y predecibles con las superficies holográficas.
   * Si solo se requiere un cambio cosmético, puede ser suficiente para suavizar las normales de vértices sin cambiar las posiciones de los vértices.

* **Búsqueda de planos**
   * Hay muchas formas de análisis que una aplicación puede querer realizar en las superficies proporcionadas por la asignación espacial.
   * Un ejemplo sencillo es ' búsqueda de planos '; identificación de regiones de superficies limitadas y delimitadas.
   * Las regiones planas se pueden usar como superficies de trabajo holográficas, regiones en las que la aplicación puede colocar automáticamente el contenido holográfica.
   * Las regiones planas pueden restringir la interfaz de usuario para guiar a los usuarios para que interactúen con las superficies que mejor se adapten a sus necesidades.
   * Las regiones planas se pueden usar como en el mundo real, para homólogos holográficas a objetos funcionales como pantallas LCD, tablas o pizarras.
   * Las regiones planas pueden definir áreas de reproducción, formando la base de los niveles de Videogame.
   * Las regiones planas pueden ayudar a los agentes virtuales a navegar por el mundo real, mediante la identificación de las áreas de piso en las que es probable que los usuarios reales realicen un recorrido.

## <a name="prototyping-and-debugging"></a>Prototipos y depuración

### <a name="useful-tools"></a>Herramientas útiles
* El [emulador de hololens](using-the-hololens-emulator.md) se puede usar para desarrollar aplicaciones mediante la asignación espacial sin acceso a una HoloLens física. Le permite simular una sesión activa en una HoloLens en un entorno realista, con todos los datos que utilizará normalmente la aplicación, como el movimiento de HoloLens, los sistemas de coordenadas espaciales y las mallas de asignación espacial. Se puede usar para proporcionar una entrada repetible y confiable, que puede ser útil para depurar problemas y evaluar los cambios en el código.
* Para reproducir escenarios, Capture los datos de asignación espacial a través de la red desde una HoloLens en vivo y, luego, guárdelos en el disco y vuelva a usarlo en sesiones de depuración posteriores.
* La [vista 3D del portal de dispositivos de Windows](using-the-windows-device-portal.md#3d-view) proporciona una manera de ver todas las superficies espaciales disponibles actualmente a través del sistema de asignación espacial. Esto proporciona una base de comparación para las superficies espaciales dentro de la aplicación; por ejemplo, puede saber fácilmente si faltan superficies espaciales o si se muestran en el lugar equivocado.

### <a name="general-prototyping-guidance"></a>Instrucciones generales de prototipos
* Dado que los [errores](spatial-mapping-design.md#what-influences-spatial-mapping-quality) en los datos de asignación espacial pueden afectar seriamente a la experiencia del usuario, se recomienda probar la aplicación en una amplia variedad de entornos.
* No se preocupe en el hábito de probar siempre en la misma ubicación, por ejemplo, en el escritorio. Asegúrese de probar varias superficies de diferentes posiciones, formas, tamaños y materiales.
* Del mismo modo, aunque los datos sintéticos o grabados pueden ser útiles para la depuración, no se vuelven demasiado a depender de los mismos casos de prueba. Esto puede retrasar la búsqueda de problemas importantes que se habrían detectado con anterioridad.
* Es una buena idea realizar pruebas con usuarios reales (y idealmente no dirigidos), ya que es posible que no usen HoloLens o su aplicación exactamente del mismo modo que lo hace. De hecho, puede sorprenderle de qué grado de comportamiento, conocimiento y suposiciones de las personas pueden ser divergentes.

## <a name="see-also"></a>Vea también
* [Visualización de la exploración de la sala](room-scan-visualization.md)
* [Diseño de sonido espacial](spatial-sound-design.md)
* [Persistencia en Unity](persistence-in-unity.md)
