---
title: Compartir experiencias en realidad mixta
description: Holográficas aplicaciones pueden compartir espaciales delimitadores de uno HoloLens a otro, permitiendo a los usuarios representar un holograma en el mismo lugar en el mundo real en varios dispositivos.
author: thetuvix
ms.author: grbury
ms.date: 02/10/2019
ms.topic: article
keywords: experiencia compartida, mixto en realidad, holograma, delimitador espacial, multiusuario, varios
ms.openlocfilehash: b27da1e73c927a26e33746cd2db08e67c6f70acc
ms.sourcegitcommit: f7fc9afdf4632dd9e59bd5493e974e4fec412fc4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2019
ms.locfileid: "59605790"
---
# <a name="shared-experiences-in-mixed-reality"></a>Compartir experiencias en realidad mixta

Hologramas no deben permanecer privada a un solo usuario. Pueden compartir aplicaciones holográficas [delimitadores espaciales](coordinate-systems.md) desde uno HoloLens, iOS o Android dispositivo a otro, permitiendo a los usuarios representar un holograma en el mismo lugar en el mundo real en varios dispositivos.

## <a name="six-questions-to-define-shared-scenarios"></a>Seis preguntas para definir escenarios compartidos

Antes de comenzar el diseño de experiencias compartidas, es importante definir los escenarios de destino. Estos escenarios ayudar a aclarar lo que está diseñando y establecer un vocabulario común para ayudar a comparar y contrastar las características necesarias en su experiencia. Comprender el problema principal y las vías distintas para las soluciones, es clave para descubrir oportunidades inherentes a este medio nuevo.

A través de prototipos internos y exploraciones de nuestros organismos de asociado de HoloLens, hemos creado seis preguntas para ayudar a definir escenarios compartidos. Estas preguntas forman un marco de trabajo, no pretende ser exhaustivo, para ayudar a refinar los atributos importantes de los escenarios.

### <a name="1-how-are-they-sharing"></a>1. ¿Cómo están compartiendo?

Una presentación podría ser impartida por un único usuario virtual, mientras que varios usuarios pueden colaborar o un profesor podría proporcionar instrucciones a los alumnos virtuales trabajar con materiales virtuales, la complejidad de los aumentos de experiencias basadas en el nivel de un usuario tiene la Agencia o puede haber en un escenario.

![Hombre y mujer con holograph en la tabla](images/man-and-women-with-holograph-on-table-500px.png)

Hay muchas formas de compartir, pero hemos observado que la mayoría de ellos se dividen en tres categorías:
* **Presentación**: Cuando se muestra el mismo contenido a varios usuarios. Por ejemplo: Profesor es proporcionar una charla a varios alumnos con el mismo material holográfico que se presenta a todos los usuarios. Sin embargo el profesor podría tener sus propias sugerencias y notas de la que pueden no estar visibles para otros usuarios.
* **Colaboración**: Cuando las personas trabajan en conjunto para lograr algunos objetivos comunes. Por ejemplo: El profesor repartió de un proyecto para obtener información acerca de cómo realizar una cirugía de corazón. Los estudiantes empareje y crean una experiencia de laboratorio de conocimientos compartidos que permite a los estudiantes de medicina colaborar en el modelo de núcleo y aprender.
* **Orientación**: Cuando una persona está ayudando a alguien a solucionar un problema en una interacción de estilo más uno. Por ejemplo: El profesor que ofrecen orientación a un alumno al que está realizando el laboratorio de habilidades de cirugía corazón en la experiencia compartida.

### <a name="2-what-is-the-group-size"></a>2. ¿Cuál es el tamaño de grupo?

**Uno a uno** compartir experiencias puede proporcionar una sólida línea de base y lo ideal es que se pueden crear sus pruebas de concepto en este nivel. Pero tenga en cuenta que compartir con los grupos de gran tamaño (más allá de 6 personas) puede provocar dificultades desde technical (datos y redes) social (el impacto de estar en una sala con [avatares varias](https://vimeo.com/160704056)). Complejidad aumenta exponencialmente a medida que avance desde **pequeño** a **grandes grupos**.

Hemos descubierto que las necesidades de grupos pueden dividirse en tres categorías de tamaño:
* 1:1
* Pequeño < 7
* Grandes > = 7

Tamaño de grupo hace que para una pregunta importante porque influye en:
* Representaciones de personas en el espacio holográfica
* Escalado de objetos
* Escalado del entorno

### <a name="3-where-is-everyone"></a>3. ¿Dónde está todo el mundo?

La intensidad de la realidad mixta entra en juego cuando una experiencia compartida puede tener lugar en la misma ubicación. La llamamos **colocados**. Por el contrario, cuando se distribuya el grupo y al menos un participante no está en el mismo espacio físico (como suele ocurrir con VR) la llamamos una experiencia remota. A menudo es el caso de que su grupo tiene **ambos** participantes colocados y remotos (por ejemplo, dos grupos en las salas de conferencias).

![Tres personas con holograph en la tabla](images/three-people-with-holograph-on-table-500px.png)

Las categorías siguientes ayudan a transmitir donde los usuarios se encuentran:
* Ubicación compartida: Todos los usuarios estarán en el mismo espacio físico.
* Remoto: Todos los usuarios estarán en espacios físicos independientes.
* Ambos: Los usuarios será una combinación de espacios colocadas y remotos.

Algunas de las razones por qué esta pregunta es fundamental porque influye en:
* ¿Cómo se comunican las personas?
* Por ejemplo: ¿Si deben tener los avatares?
* ¿Qué objetos que vea. ¿Todos los objetos compartidos?
* ¿Si es necesario para adaptarse a su entorno?

### <a name="4-when-are-they-sharing"></a>4. ¿Cuándo están compartiendo?

Se nos ocurre normalmente **sincrónica** experiencias de experiencias compartidas vienen en mente: Todos los hacemos lo juntos. Pero incluye un único elemento virtual que se ha agregado por otra persona y tiene un **asincrónica** escenario. Imagine una nota o una nota de voz, queda en un entorno virtual. ¿Cómo se controlan los 100 recordatorios virtuales restante en el diseño? ¿Qué ocurre si están entre docenas de personas con distintos niveles de privacidad?

Tenga en cuenta sus experiencias como una de estas categorías de tiempo:
* **Sincrónicamente**: Uso compartido de la experiencia holográfica al mismo tiempo. Por ejemplo: Dos de los estudiantes al realizar la práctica de conocimientos al mismo tiempo.
* **Asincrónicamente**: Uso compartido de la experiencia holográfica en momentos diferentes. Por ejemplo: Dos estudiantes al realizar la práctica de habilidades, pero está trabajando en secciones separadas en momentos diferentes.
* **Ambos**: Los usuarios a veces compartirán sincrónicamente, pero otras veces asincrónicamente. Por ejemplo: Profesor de clasificación de la asignación realizada por los alumnos en un momento posterior y dejando las notas de estudiante para el día siguiente.

Algunas de las razones por qué esta pregunta es importante porque influye en:
* Persistencia de objeto y el entorno. Por ejemplo: Almacenar los Estados para que se puedan recuperar.
* Perspectiva del usuario. Por ejemplo: Quizás recordar lo que el usuario había aumentado al salir de notas.

### <a name="5-how-similar-are-their-physical-environments"></a>5. ¿Similitud son sus entornos físicos?

La probabilidad de dos entornos idénticos reales, fuera de experiencias colocados, es delgada a menos que esos entornos se han diseñado para que sean idénticos. Es más probable tener **similar** entornos. Por ejemplo, las salas de conferencias son similares, tiene normalmente una tabla ubicada centralmente rodeada de sillas. Salas de estar, por otro lado, suelen ser **dispares** y puede incluir cualquier número de fragmentos de muebles en una matriz de los diseños de infinita.

![Holograph en la tabla](images/holograph-on-table-500px.png)

Tenga en cuenta sus experiencias de uso compartidos de conexión en una de estas dos categorías:
* **Similar**: Entornos que tienden a tener muebles similar, la luz ambiental y sonido, tamaño del espacio físico. Por ejemplo: Profesor está en el salón de charla A y estudiantes están en la conferencia hall salón de charla B. A podría tener menos sillas que B pero ambos pueden tener un soporte físico para colocar hologramas en.
* **Dispares**: Entornos que son bastante diferentes en la configuración de muebles, tamaño de la sala, consideraciones de luz y sonidas. Por ejemplo: Mientras que los estudiantes son un Hall grande conferencia rellenado con los estudiantes y profesores, es profesor en una sala de foco.

Es importante pensar en el entorno como influirá en:
* Cómo experimentarán las personas a estos objetos. Por ejemplo: Si su experiencia funciona mejor en una tabla y el usuario no tiene ninguna tabla? O en una superficie plana floor pero el usuario no tiene un espacio desordenado.
* Escala de los objetos. Por ejemplo: Colocación de un modelo de 6 pies humano en una tabla puede ser difícil, pero un modelo de núcleo funcionaría bien.

### <a name="6-what-devices-are-they-using"></a>6. ¿Qué dispositivos usan?

Hoy en día a menudo es probable que vea las experiencias compartidas entre dos **dispositivos envolventes** (esos dispositivos pueden diferir ligeramente en cuanto a los botones y la capacidad relativa, pero no en gran medida) o dos **holográficas dispositivos** dada las soluciones que se está dirigidas a estos dispositivos. Pero tenga en cuenta que **dispositivos 2D** (un participante de escritorio o móviles u observador) será una consideración necesaria, especialmente en situaciones de **mixto dispositivos 2D y 3D**. Descripción de los tipos de dispositivos que se va a utilizar sus participantes es importante, no sólo porque proceden con fidelidad diferentes y las restricciones de datos y las oportunidades, pero dado que los usuarios tienen expectativas únicas para cada plataforma.

## <a name="exploring-the-potential-of-shared-experiences"></a>Explorar el potencial de experiencias compartidas

Respuestas a las preguntas anteriores se pueden combinar para comprender mejor el escenario compartido, cristalice los desafíos a medida que amplía la experiencia. El equipo de Microsoft, Esto ayudó a establecer un mapa de carreteras para mejorar las experiencias se usa hoy en día, comprender el matiz de estos problemas complejos y cómo aprovechar las ventajas de experiencias compartidas en realidad mixta.

Por ejemplo, considere la posibilidad de uno de los escenarios de Skype desde el lanzamiento de HoloLens: un usuario que se recorrieron [cómo corregir un conmutador de luz roto](https://www.youtube.com/watch?v=iBfzs3G8BEA) con la Ayuda de un experto en ubicados de forma remota.

![Corrección de un conmutador de la luz con la asistencia a través de Skype para HoloLens](images/fix-a-broken-switch-with-hololens-640px.jpg)

<i>Proporciona un experto <b>1:1</b> guía desde su <b>2D</b>, equipo de escritorio a un usuario de un <b>3D, en realidad mixta</b> dispositivo. El <b>instrucciones</b> es <b>sincrónica</b> y los entornos físicos son <b>dispares</b>.</i>

Una experiencia similar a esto es un cambio de paso de nuestra experiencia actual, aplicar el paradigma de vídeo y voz en un medio de nuevo. Pero Si observamos el futuro, debemos definir la oportunidad de nuestros escenarios mejor y crear experiencias que reflejan la intensidad de la realidad mixta.

Tenga en cuenta la [herramienta de colaboración OnSight](https://www.youtube.com/watch?v=ZOWQp0-Bkkw) desarrollado por el laboratorio de propulsión a chorro de la NASA. Los científicos de trabajar en los datos de las misiones de viajero de Marte pueden colaborar con compañeros en tiempo real dentro de los datos del panorama marciano.

![Colaborar entre compañeros separados de forma remota para planear el trabajo para el Explorador de Marte](images/onsight-nasa-jpl.gif)

<i>Un científico explora un entorno con un <b>3D, en realidad mixta</b> dispositivo con un <b>pequeño</b> grupo de <b>remoto</b> colegas mediante <b>3D y 2D</b> dispositivos. El <b>colaboración</b> es <b>sincrónica</b> (pero puede revisarse de manera asincrónica) y los entornos físicos (prácticamente) son <b>similar</b>.</i>

Experiencias como OnSight presentan nuevas oportunidades para colaborar. De señalar físicamente los elementos en el entorno virtual para compartir su perspectiva tal como explican sus conclusiones y junto a un compañero de trabajo. OnSight usa la lente de inmersión y presencia para reconsiderar las experiencias de uso compartidas en la realidad mixta.

Colaboración intuitivo es la base de la conversación y trabajar juntos y comprender cómo podemos aplicar esta intuición a la complejidad de la realidad mixta es fundamental. Si podemos no sólo volver a crear experiencias de uso compartidas en mixed reality pero aumento del rendimiento de ellos, será un cambio de paradigma para el futuro de trabajo. Diseño de experiencias compartidas en realidad mixta es espacio nuevo y emocionante, y estamos solo al principio.

## <a name="get-started-sharing-experiences"></a>Comience a compartir experiencias

En función de la aplicación y el escenario, habrá distintos requisitos para lograr la experiencia deseada. Algunas de estas incluyen
* Creación de coincidencia: Capacidad de crear sesiones, anunciar la sesión y descubrir e invitar a personas específicas, tanto localmente y remota para unirse a la sesión.
* Delimitar el uso compartido: Capacidad para alinear las coordenadas en varios dispositivos en un espacio local común, por lo que hologramas aparecen en el mismo lugar para todas las personas.
* Redes: Capacidad de tener posiciones, interacciones, y los movimientos de personas y hologramas sincronizan en tiempo real en todos los participantes.
* Almacenamiento de estado: Capacidad para almacenar características holograma y ubicaciones en el espacio para una combinación de la mitad de la sesión, recuerda a una hora posterior y solidez contra los problemas de red.


La clave para experiencias compartidas es varios usuarios ven la mismas hologramas en el mundo en su propio dispositivo, con frecuencia se realiza mediante el uso compartido de delimitadores para alinear las coordenadas en todos los dispositivos.
Para compartir los delimitadores, use el <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure espacial delimitadores</a>:
* En primer lugar, el usuario coloca el holograma.
* Aplicación crea un [delimitador espacial](coordinate-systems.md) para anclar ese holograma exactamente en el mundo.
* Los delimitadores pueden compartirse a HoloLens, iOS y Android dispositivos a través de la <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure espacial delimitadores</a>. 

Con un anclaje espacial compartido, la aplicación en cada dispositivo tiene ahora un sistema de coordenadas comunes en el que puede colocar el contenido. Ahora puede asegurarse de la aplicación para colocar y orientar el holograma en la misma ubicación.
En los dispositivos HoloLens, también puede compartir los anclajes de sin conexión desde un dispositivo a otro.  Use los vínculos siguientes para decidir cuál es mejor para su aplicación.


## <a name="see-also"></a>Vea también
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure delimitadores espaciales</a>
* [Compartido espaciales delimitadores en DirectX](shared-spatial-anchors-in-directx.md)
* [Experiencias compartidas en Unity](shared-experiences-in-unity.md)
* [Vista del espectador](spectator-view.md)