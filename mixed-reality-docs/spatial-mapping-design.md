---
title: Diseño de la asignación espacial
description: Un uso eficaz de asignación espacial dentro de HoloLens requiere una consideración cuidadosa de muchos factores.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Asignación de Windows Mixed Reality, diseño, espacial, HoloLens, surface reconstrucción, malla
ms.openlocfilehash: d2ddcbf9458769a60cd3ed2871c5f3405c75f10c
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/12/2019
ms.locfileid: "59597887"
---
# <a name="spatial-mapping-design"></a>Diseño de la asignación espacial

Un uso eficaz de asignación espacial dentro de HoloLens requiere una consideración cuidadosa de muchos factores.

## <a name="device-support"></a>Compatibilidad con dispositivos

<table>
<tr>
<th>Característica</th><th style="width:150px"> <a href="hololens-hardware-details.md">HoloLens</a></th><th style="width:150px"> <a href="immersive-headset-hardware-details.md">Inmersivos</a></th>
</tr><tr>
<td> Asignación espacial</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

## <a name="why-is-spatial-mapping-important"></a>¿Por qué es importante la asignación espacial?

Asignación espacial permite colocar objetos en superficies real. Esto ayuda a los objetos de anclaje en el mundo del usuario y aprovecha las ventajas de las indicaciones de profundidad del mundo real. Occluding sus hologramas según otros hologramas y objetos del mundo real le ayuda a convencer al usuario que estos hologramas realmente están en su espacio. Hologramas flotando en el espacio o mover con el usuario no se sentirá como real. Cuando sea posible, elementos de contexto para su comodidad.

Visualice las superficies al colocar o mover hologramas (usar una cuadrícula simple prevista). Esto le ayudará al usuario saber dónde puede colocar mejor sus hologramas y muestra al usuario si la zona que se están intentando colocar el holograma aún no se ha asignado todavía. Se pueden "cartelera elementos" hacia el usuario si terminan en una cantidad excesiva de un ángulo.

## <a name="what-influences-spatial-mapping-quality"></a>¿Qué influye en la calidad de la asignación espacial?

Con el fin de ofrecer la mejor experiencia de usuario, es importante comprender los factores que afectan a la calidad de datos de asignación espacial recopilados por HoloLens.

Errores en los datos de asignación espacial se dividen en tres categorías:
* **Agujeros**: Faltan las superficies del mundo real de los datos de asignación espacial.
* **Alucinaciones**: Las superficies existen en los datos de asignación espacial que no existen en el mundo real.
* **Sesgo**: Las superficies de los datos de asignación espacial no entienden bien se alinean con superficies del mundo real, pulsado o extraerse.

Varios factores pueden afectar a la frecuencia y la gravedad de estos errores:

* **Movimiento de usuario**
   * Cómo el usuario se mueve a través de su entorno de determina cómo se examinará el entorno, por lo que el usuario puede requerir una guía para lograr un buen examen.
   * La cámara que se usa para el análisis proporciona los datos dentro de un cono 70 grados, entre un mínimo de 0,8 metros a un máximo de 3,1 metros de distancia de la cámara. Solo se examinarán las superficies del mundo real dentro de este campo de visión. Tenga en cuenta que estos valores están sujetos a cambios en versiones futuras.
   * Si el usuario nunca recibe dentro de los medidores 3.1 de un objeto, a continuación, no se examinarán.
   * Si el usuario solo ve un objeto de una distancia de menos de 0,8 metros, no se examinarán (Esto evita la exploración de las manos del usuario).
   * Si el usuario nunca se ve hacia arriba (que es bastante normal), a continuación, el límite superior es probable que no se examinarán.
   * Si un usuario se ve nunca detrás de muebles o una pared no se examinarán los objetos que se ocluyeron en ellos.
   * Las superficies tienden a analizarse con una calidad superior cuando se ven toro por las astas en lugar de un ángulo superficial.
   * Si el sistema de seguimiento de la cabeza de la HoloLens momentáneamente falla (que puede ocurrir debido al movimiento rápido de usuario, iluminación, paredes sin características o las cámaras de convertirse en cubierto), esto puede producir errores en los datos de asignación espacial. Alguno de estos errores se corregirán con el tiempo a medida que el usuario desplazarse y examinar su entorno.

* **Materiales de superficie**
   * Los materiales que se encuentra en superficies reales varían en gran medida. Afectan a la calidad de datos, ya que afectan a la luz infrarroja cómo se reflejan de asignación espacial.
   * No pueden detectar superficies oscuras hasta que vuelvan más cerca de la cámara, porque reflejan menos claro.
   * Algunas superficies pueden ser tan oscuras que reflejan la luz demasiado pequeño para ser examinado desde cualquier distancia, por lo que presentará errores hueco en la ubicación de la superficie y, a veces también detrás de la superficie.
   * Solo pueden escanear superficies especialmente brillantes cuando se ve toro por las astas y no cuando se ve desde un ángulo superficial.
   * Reflejos, porque crean reflejos illusory de espacios real y superficies, pueden provocar errores de agujero y errores hallucination.

* **Movimiento de escena**
   * Asignación espacial rápidamente se adapta a los cambios en el entorno, como mover usuarios o de apertura y cierre de las puertas.
   * Sin embargo, asignación espacial solo puede adaptar a los cambios en un área cuando dicha área es claramente visible a la cámara que se usa para el análisis.
   * Por este motivo, es posible que esta adaptación a la zaga en realidad, lo que puede causar errores agujero o hallucination.
   * Por ejemplo, un usuario examina a un amigo y Revuelve, a continuación, mientras que la confianza deja la sala. Una representación de "fantasma" de la función friend (error hallucination) se conservará en los datos de asignación espacial, hasta que el usuario da la vuelta y volver a examina el espacio donde estaba de pie friend.

* **Interferencia de iluminación**
   * Luz infrarroja ambiente de la escena puede interferir con la exploración, por ejemplo, estará disponible a través de una ventana de la luz solar segura.
   * Las superficies especialmente brillantes pueden interferir con el análisis de superficies cercanas, la luz el rebote fuera de ellos que causan errores de sesgo.
   * Shiny superficies que reflejan la luz directamente a la cámara pueden interferir con espacio cercano, haciendo que flotante alucinaciones vuelo o al retrasar la adaptación al movimiento de la escena.
   * Dos dispositivos HoloLens en la misma sala no deben interferir entre sí, pero la presencia de más de cinco dispositivos HoloLens puede causar interferencias.

Es posible evitar o corregir algunos de estos errores. Sin embargo, debe diseñar la aplicación para que el usuario es capaz de alcanzar sus objetivos, incluso en presencia de errores en los datos de asignación espacial.

## <a name="the-environment-scanning-experience"></a>El entorno de experiencia de exploración

HoloLens aprende sobre las superficies en su entorno, como el usuario busca en ellos. Con el tiempo, el HoloLens se acumula un examen de todas las partes del entorno que se han observado. También actualiza el examen tal como se observan los cambios en el entorno. Este examen se conservará automáticamente entre los lanzamientos de la aplicación.

Cada aplicación que utiliza la asignación espacial debe tener en cuenta que proporciona una "experiencia de análisis;' el proceso a través del cual la aplicación guía al usuario para examinar las superficies que son necesarias para la aplicación funcione correctamente.

![Ejemplo de análisis](images/sr-mixedworld-140429-8pm-00068-1000px.png)<br>
*Ejemplo de análisis*

La naturaleza de esta experiencia de análisis puede variar enormemente según las necesidades de cada aplicación, pero dos principios principales deberían guiar su diseño.

En primer lugar, **clara la comunicación con el usuario es la principal preocupación**. El usuario siempre debe tener en cuenta si se están cumpliendo los requisitos de la aplicación. Cuando no se se cumplen, debe quedar claro inmediatamente al usuario por qué esto es así y debe llegar rápidamente a realice la acción apropiada.

En segundo lugar, **las aplicaciones deberían intentar lograr un equilibrio entre eficacia y fiabilidad**. Cuando es posible hacerlo **confiable**, las aplicaciones deben analizar automáticamente los datos de asignación espacial para ahorrar el tiempo de usuario. Cuando no es posible hacerlo de forma confiable, las aplicaciones en su lugar, deben habilitar al usuario que proporcione rápidamente la aplicación con la información adicional que requiere.

Para ayudar a la derecha en la experiencia de análisis de diseño, tenga en cuenta que las posibilidades siguientes son aplicables a su aplicación:

* **Ninguna experiencia de exploración**
   * Una aplicación puede funcionar perfectamente sin ninguna experiencia guiada de análisis; conocerá las superficies que se observan en el transcurso de movimiento de usuario natural.
   * Por ejemplo, una aplicación que permite al usuario dibujar en superficies con spraypaint holográfica requiere un conocimiento solo de las superficies actualmente visibles para el usuario.
   * El entorno puede completamente analizarse ya si se trata de uno en el que el usuario ya ha pasado mucho tiempo con el HoloLens.
   * Tenga en cuenta sin embargo que la cámara empleada por asignación espacial solo puede ver 3,1 m delante del usuario, por lo que la asignación espacial no sabrá acerca de los más lejanos superficies, a menos que el usuario ha observado ellos desde una distancia de más de cerca en el pasado.
   * Por lo que el usuario entienda las superficies que se han examinado, la aplicación debe proporcionar comentarios visuales al respecto, por ejemplo, conversión virtuales sombras en superficies digitalizadas puede ayudar al usuario coloque hologramas en dichas superficies.
   * En este caso, deben ser volúmenes delimitador del observador superficie espacial actualizado cada fotograma a un cuerpo bloqueado [del sistema de coordenadas espacial](coordinate-systems.md), de modo que siguen al usuario.

* **Buscar una ubicación adecuada**
   * Una aplicación puede estar diseñada para su uso en una ubicación con requisitos específicos.
   * Por ejemplo, la aplicación puede requerir un área vacía en el usuario, por lo que pueden practicar con seguridad kung-fu holográfico.
   * Las aplicaciones deben comunicar los requisitos específicos para el usuario por adelantado y reforzarlos comentarios visual clara.
   * En este ejemplo, la aplicación debe visualizar la medida del área vacía necesario y resaltar visualmente la presencia de todos los objetos no deseados dentro de esta zona.
   * En este caso, deben usar volúmenes delimitador del observador superficie espacial bloqueado mundo [del sistema de coordenadas espacial](coordinate-systems.md) en la ubicación elegida.

* **Buscar una configuración adecuada de superficies**
   * Una aplicación puede requerir una configuración específica de superficies, por ejemplo dos grandes, plana, opuestas paredes para crear un salón de reflejos holográfica.
   * En tales casos, la aplicación deberá analizar las superficies proporcionadas por la asignación espacial para detectar las superficies adecuadas y dirigir al usuario hacia ellos.
   * El usuario debe tener una opción de reserva si el análisis de la superficie de la aplicación no está totalmente confiables. Por ejemplo, si la aplicación identifica incorrectamente una puerta de entrada como una pared plana, el usuario necesita una manera sencilla para corregir este error.

* **Parte del entorno de análisis**
   * Una aplicación que desee capturar solo parte del entorno, según lo indicado por el usuario.
   * Por ejemplo, la aplicación examina la parte de una sala de por lo que el usuario puede publicar un anuncio clasificado holográfico para muebles que deseen vender.
   * En este caso, la aplicación debe capturar datos de asignación espacial dentro de las regiones observadas por el usuario durante su análisis.

* **Análisis de la sala de toda**
   * Una aplicación puede requerir un examen de todas las superficies en la sala actual, los detrás del usuario incluidos.
   * Por ejemplo, un juego puede agregar el usuario al rol de Gulliver, bajo siege entre cientos de tiny Lilliputians acerca de todas las direcciones.
   * En tales casos, la aplicación debe determinar cuántas de las superficies de actual de la sala ya se han examinado y dirigir la mirada del usuario para rellenar los huecos significativo.
   * La clave para este proceso es proporcionar comentarios visuales que deje claro al usuario aún no se han examinado las superficies que. Por ejemplo podría usar la aplicación [niebla basada en la distancia](https://msdn.microsoft.com/library/windows/desktop/bb173401%28v=vs.85%29.aspx) para resaltar visualmente las regiones que no están cubiertas por las superficies de asignación espacial.

* **Realice una instantánea inicial del entorno**
   * Una aplicación que desee omitir todos los cambios en el entorno después de tomar una 'instantánea' inicial.
   * Esto puede ser adecuado para evitar la interrupción de datos creada por el usuario que está estrechamente al estado inicial del entorno.
   * En este caso, la aplicación debe hacer una copia de los datos de asignación espacial en su estado inicial una vez completado el examen.
   * Las aplicaciones deben seguir recibiendo actualizaciones de datos de asignación espacial si hologramas son todavía se ocluyeron correctamente en el entorno.
   * Actualizaciones continuas a los datos de asignación espacial también permiten visualizar los cambios que se han producido, aclarar al usuario las diferencias entre los estados anteriores y presentes del entorno.

* **Tomar instantáneas iniciadas por el usuario del entorno**
   * Una aplicación que solo desee responder a cambios en el entorno cuando se lo indique el usuario.
   * Por ejemplo, el usuario podría crear varios 3D 'vivientes' de un amigo al capturar su plantea en momentos diferentes.

* **Permitir al usuario cambiar el entorno**
   * Una aplicación puede diseñarse para responder en tiempo real a los cambios realizados en el entorno del usuario.
   * Por ejemplo, el usuario dibujar una cortina podría desencadenar "cambio de escena' para un juego holográfico lleva a cabo en el otro lado.

* **Guía del usuario para evitar errores en los datos de asignación espacial**
   * Una aplicación que quiera proporcionar orientación al usuario mientras está examinando su entorno.
   * Esto puede ayudar al usuario para evitar ciertos tipos de [errores en los datos de asignación espacial](spatial-mapping-design.md#what-influences-spatial-mapping-quality), por ejemplo, al mantenerse fuera de windows través o reflejos.

Un detalle adicional para tener en cuenta es que la 'range' de datos de asignación espacial no es ilimitado. Mientras que la asignación espacial compilar una base de datos permanente de espacios de gran tamaño, solo resulta que los datos disponibles para las aplicaciones en una "burbuja' tamaño limitado en el usuario. Por lo tanto si inicia al principio de un corredor de largo y recorrido de la distancia suficiente el inicio y, después, finalmente desaparecerán las superficies espaciales al principio. Por supuesto, puede mitigar esto almacenando en caché las superficies de la aplicación una vez que han desaparecido de los datos de asignación espacial disponibles.

## <a name="mesh-processing"></a>Procesamiento de malla

Puede ser útil para detectar tipos de errores comunes en las superficies y filtrar, quitar o modificar los datos de asignación espacial según corresponda.

Tenga en cuenta que esa asignación espacial datos está pensados para ser tan fiel como sea posible a las superficies del mundo real, procesamiento para los aplicar los riesgos que desplazar las superficies más lejos de la realidad' '.

Estos son algunos ejemplos de diferentes tipos de procesamiento de la malla que pueden resultarle útiles:

* **Rellenar agujeros**
   * Si no se puede analizar un pequeño objeto de un material oscuro, dejará un hueco en la superficie que lo rodea.
   * Agujeros afectan a la oclusión: pueden verse hologramas 'a' un hueco en una superficie reales supuestamente opaco.
   * Agujeros afectan a raycasts: Si usas raycasts para ayudar a los usuarios interactuar con superficies, puede no ser deseable para estos rayos pasar a través de agujeros. Una solución consiste en utilizar una agrupación de varios raycasts que cubre una región de tamaño adecuado. Esto le permitirá filtrar los resultados de "valor atípico", por lo que incluso si uno raycast pasa a través de un pequeño orificio, el resultado agregado todavía será válido. Sin embargo, tenga en cuenta que este enfoque tiene un costo computacional.
   * Agujeros afectan a conflictos de leyes físicas: un objeto que se controla mediante la simulación física puede quitar a través de una vulnerabilidad en el suelo y se pierden.
   * Es posible rellenar de forma algorítmica esas carencias en la malla de superficie. Sin embargo, deberá ajustar el algoritmo para que no se rellenan agujeros real, como windows y puertas. Puede resultar difícil diferenciar confiable 'agujeros real' desde 'agujeros imaginarios', por lo que tendrá que experimentar con diferentes heurística, como 'tamaño' y 'forma límite'.

* **Eliminación de hallucination**
   * Reflexiones, luces brillantes y objetos en movimiento pueden dejar pequeño persistentes 'alucinaciones' flotante en vuelo.
   * Alucinaciones afectan a la oclusión: alucinaciones es posible que se hacen visibles como formas oscuras moverse delante de y occluding otros hologramas.
   * Alucinaciones afectan a raycasts: Si usas raycasts para ayudar a los usuarios interactuar con superficies, estos rayos podrían detectar un hallucination en lugar de la superficie subyacente. Al igual que con los marcadores, una solución consiste en usar muchos raycasts en lugar de una sola raycast, pero nuevamente, esto se tratarán en un costo computacional.
   * Alucinaciones efecto física colisiones: un objeto controlado por simulación física puede bloquearse con un hallucination y que no puede moverse a través de un área de espacio aparentemente no cifrado.
   * Es posible filtrar dichas alucinaciones de la malla de superficie. Sin embargo, al igual que con los marcadores, deberá ajustar el algoritmo para que real pequeños objetos como lamp significa y no se quitan los identificadores de puerta.

* **Suavizado**
   * Asignación espacial puede devolver las superficies que parecen ser ruidoso en comparación con sus homólogos reales o aproximada.
   * Suavidad afecta a conflictos de leyes físicas: si el límite inferior es una aproximación, una pelota de golf físicamente simulado puede no roll sin problemas a través de él en una línea recta.
   * Suavidad afecta a la representación: si una superficie se visualiza directamente, normales de superficie aproximadas pueden afectar a su apariencia y se interrumpe un aspecto "limpio". Es posible mitigar esta situación mediante el uso de iluminación adecuado y texturas en el sombreador que se usa para representar la superficie.
   * Es posible suavizar rugosidad en una malla de superficie. Sin embargo, esto puede insertar la superficie aún más lejos de la superficie del mundo real correspondiente. Es importante para generar la oclusión holograma precisos y para permitir que los usuarios a lograr las interacciones precisas y predecibles con superficies holográficas mantener una correspondencia de cierre.
   * Si solo es necesario un cambio de cosmético, puede ser suficiente suavizar las normales de vértice sin cambiar las posiciones de vértice.

* **Buscar plano**
   * Hay muchas formas de análisis que una aplicación que desee realizar en las superficies de asignación espacial.
   * Un ejemplo sencillo es 'plano de búsqueda'; identificar regiones limitadas, principalmente plana de superficies.
   * Planares regiones pueden usarse como holográficas-superficies de trabajo, las regiones donde holográfica contenido se puede colocar automáticamente por la aplicación.
   * Planares regiones pueden restringir la interfaz de usuario, para guiar a los usuarios interactuar con las superficies que mejor se adapten a sus necesidades.
   * Planares regiones pueden usarse como se muestra en el mundo real, para holográficas equivalentes para los objetos de función, como las pantallas LCD, tablas o pizarras.
   * Planares regiones pueden definir las áreas de juegos, que forman la base de los niveles de videojuegos.
   * Planares regiones pueden ayudar a los agentes virtuales para navegar por el mundo real, mediante la identificación de las áreas de piso que personas reales las que están probables que guiará en.

## <a name="prototyping-and-debugging"></a>Creación de prototipos y la depuración

### <a name="useful-tools"></a>Herramientas útiles
* El [emulador de HoloLens](using-the-hololens-emulator.md) se puede usar para desarrollar aplicaciones con asignación espacial sin acceso a un HoloLens físico. Permite simular una sesión activa en un HoloLens en un entorno realista, con todos los datos de la aplicación normalmente consumiría, incluidos HoloLens movimiento, sistemas de coordenadas espaciales y las mallas de asignación espacial. Esto puede usarse para proporcionar datos confiables, repetibles, lo que pueden ser útil para depurar los problemas y evaluar los cambios de código.
* Para reproducir un escenarios, capturar datos de asignación espacial en la red desde un HoloLens en vivo, a continuación, guarde en disco y volver a usarla en las siguientes sesiones de depuración.
* El [vista 3D portal del dispositivo Windows](using-the-windows-device-portal.md#3d-view) proporciona una manera de ver todas las superficies espaciales está disponibles a través del sistema de asignación espacial. Esto proporciona una base de comparación para las superficies espaciales dentro de la aplicación; Por ejemplo se puede saber fácilmente si ninguna superficie espacial faltan o que se muestran en el lugar incorrecto.

### <a name="general-prototyping-guidance"></a>Guía de creación de prototipos general
* Dado que [errores](spatial-mapping-design.md#what-influences-spatial-mapping-quality) en la asignación espacial datos fuertemente pueden afectar a la experiencia del usuario, se recomienda que pruebe su aplicación en una amplia variedad de entornos.
* Obtener no intercepta el hábito de pruebas siempre en la misma ubicación, por ejemplo, en su escritorio. No olvide probar en distintas superficies de distintas posiciones, formas, tamaños y materiales.
* De forma similar, mientras que los datos sintéticos o grabados pueden ser útiles para la depuración, no se convierte en demasiado depende de la mismos pocos casos de prueba. Esto puede demorar buscar problemas importantes que más variados pruebas habría detectado anteriormente.
* Es una buena idea para realizar pruebas con usuarios reales (y lo ideal es que no sean dirigidos), porque no pueden usar el HoloLens o la aplicación en exactamente del mismo modo que lo hace. De hecho, podría sorprenderle comportamiento cómo divergente popular, pueden ser el conocimiento y las suposiciones!

## <a name="see-also"></a>Vea también
* [Visualización de análisis de sala](room-scan-visualization.md)
* [Diseño espacial de sonido](spatial-sound-design.md)
* [Persistencia en Unity](persistence-in-unity.md)
